---
title: "x11vnc disconnects after 1 or 2 mins | receives stop command (caught signal: 15)"
date: 2020-05-18
forum: Ubuntu, Linux and OS Chat
---

### Post by karthik-mrk on 2020-05-18
Hi,

I am trying to run a x11vnc server on Ubuntu 20.04. I followed [this]("https://www.youtube.com/watch?v=bLGLwGToFCg") tutorial and created a systemd service for x11vnc. Looks like at first everything works fine, but the x11vnc is receiving a signal (**caught signal: 15**) to stop i guess and on the client side the session ends unexpectedly. Who issues this signal to x11vnc?

[B]The log says:
[/B]
caught signal: 15
18/05/2020 22:13:32 deleted 60 tile_row polling images.
18/05/2020 22:13:32 passing arg to libvncserver: -rfbport
18/05/2020 22:13:32 passing arg to libvncserver: 5900
18/05/2020 22:13:32 passing arg to libvncserver: -passwd

[Here]("https://ubuntuforums.org/showthread.php?t=1612704&page=2&p=10082455#post10082455") it says to use -noxrecord option, but that is also not working. Can someone please tell me what I am missing here?

Below is what I have in systemd service file in /lib/systemd/system/x11vnc.service:

[Unit]
Description=x11vnc service
Requires=display-manager.service
After=display-manager.service network.target syslog.target


[Service]
Type=forking
ExecStart=/usr/bin/x11vnc -forever -display :0 -auth /var/run/lightdm/root/:0 -rfbport 5900 -oa /home/karthik/x11vnc.log -noxdamage -noxrecord -passwd 1234
ExecStop=/usr/bin/killall x11vnc
Restart=on-failure


[Install]
WantedBy=multi-user.target

By the way, I am new to Linux environment. I freshly installed Ubuntu 20.04 in my station.

Thanks in advance.

---

