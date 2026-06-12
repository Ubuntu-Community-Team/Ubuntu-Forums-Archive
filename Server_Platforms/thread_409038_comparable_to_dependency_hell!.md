---
title: "comparable to dependency hell!"
date: 2007-04-14
forum: Server Platforms
---

### Post by feekies on 2007-04-14
G'day all

been reading the forums on and off for a quite a few months now. I have recently purchased a dedicated server.

AMD sempron 2600
512mb ram
80GB IDE HDD

I got it with Ubuntu server (6.06?) installed. first job was to install a GUI.

```
aptitude install ubuntu-desktop
```
```

```
5 - 10 mins later its finished. Righteo, time to insert some VNC to see the pretty GUI. Following this guide (to the 't'):

[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

read pages 1 - 6 then pages 27 - 29

Steps i took:
```
sudo apt-get install vncserver xinetd
```

```
sudo vncpasswd /root/.vncpasswd
```

```
sudo vi /etc/xinetd.d/Xvnc
```

added this to /etc/xinetd.d/Xvnc
```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5901
}
```


```
sudo /etc/init.d/xinetd stop
sudo killall Xvnc
sudo /etc/init.d/xinetd start
```

so i try to connect. No luck, no connection to server. so i keep reading...

Tried this.
```
sudo Xvnc :2 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
```


i put the details into UltraVNC (i had to use the port 5902 for some reason), then prompts me for the password. success!! it connects! yay!!! but its the boring gray background with the black X.

keep going reading through the discussion. I find out that the ubuntu server needs to be restarted. so i restart the server. then i try to connect, now i cant even get though. Then i was being prompted for a password but wouldnt connect saying mention DSM. I was using MSRC4Plugin.dsm. No where did i tell vnc to use encryption or even how it got a key... 

i removed vncserver, xinetd

i'm going to start again! anyone have any insight into this?

---

### Post by huygens on 2007-04-14
I would be willing to help, but I'm not sure where you want to go.

What I understood is that you have a PC, you have install ubuntu server edition, and as there was no GUI, you installed ubuntu-desktop.

Now for my point of view, you have a "desktop" version with Gnome on which you can log in and that has some potential services running like file sharing, web or file server, etc.
So if you start your machine, you should have a graphical login, and after successful login, you have a desktop environment.

Now from there, where do you want to go?

---

