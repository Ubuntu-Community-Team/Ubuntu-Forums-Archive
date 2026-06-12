---
title: "Got XDMCP working, no sound"
date: 2010-12-25
forum: Server Platforms
---

### Post by afonteijn on 2010-12-25
I have been working on setting up XDMCP on my ubuntu 10.10 media computer for too many hours. And so I thought to explain how to set it up and then ask two questions.

The first problem I encountered is that XDMCP is broken in ubuntu 10.04 and 10.10. However, it should be fixed in the upcoming release. To solve this, a different display manager needs to be installed. Instead of using GNOME's GDM I used KDM
```
sudo apt-get install KDM
```
During the installation a blue screen will appear with the question which display manager to choose. You guessed right, choose KDM.

After the installation two files need to be edited: kdmrc and Xaccess. Both are located in /etc/kde4/kdm
```
gksudo gedit /etc/kde4/kdm/kdmrc
```
find [Xdmcp] and add
```
Enable=true
```
Save and close gedit
```
gksudo gedit /etc/kde4/kdm/Xaccess
```
find the line
```
#*					#any host can get a login window
```
and "*" (without quotes) below it
If you would like to add some safety, you can add the ip address of the client instead of "*".

I also opened the ports udp 177 and tcp 6000, because I use ufw. I don't know if it is needed if you don't use ufw. In case you want to try. Enable ufw:
```
sudo ufw enable
```
open port udp 177
```
sudo ufw allow 177
```
open port tcp 6000 for specific client ip address
```
sudo ufw allow proto tcp from 192.168.x.xxx to any port 6000
```

To access the "server" through XDMCP I logged out of the GUI of my Ubuntu client by the command:
[INDENT]Ctrl+Alt+F2[/INDENT]

I killed the running gdm
```
sudo stop gdm
```

And started the session by typing
```
X :2 -query 192.168.x.xxx
```
The ip address is that of the server.

I encountered a weird bug, that showed all the text on the screen mirrored and backwards. I solved the problem by turning of compiz. It might be a problem related to the proprietary NVIDIA drivers or it could be a compiz specific bug.

I hope this will be helpful to someone, as it has taken me quite a bit of time to figure out.

Now my two questions:
1. Is there an easy way to export the sound from the "server" to the client? I read some articles about esound, but that seems to be outdated. I also read that this must be possible with pulseaudio. Is there a guide on this?

2. I would like the client to login with XDMCP automatically. Is there a minimalistic Ubuntu (or Debian derivative) that automatically lets a user login?

---

