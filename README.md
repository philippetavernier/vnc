# vnc
## INSTALL


```
sudo apt-get install lightdm
sudo reboot
sudo apt-get install x11vnc

```
Modify X11vnc file
```
sudo nano /lib/systemd/system/x11vnc.service
```
```
[Unit]
Description=x11vnc service
After=display-manager.service network.target syslog.target

[Service]
Type=simple
ExecStart=/usr/bin/x11vnc -forever -display :0 -auth guess -passwd password
ExecStop=/usr/bin/killall x11vnc
Restart=on-failure

[Install]
WantedBy=multi-user.target


sudo systemctl daemon-reload

sudo systemctl enable x11vnc.service

sudo systemctl start x11vnc.service

sudo systemctl status x11vnc.service
```
