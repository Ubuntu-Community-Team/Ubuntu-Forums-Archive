---
title: "where's the gui"
date: 2010-07-14
forum: Server Platforms
---

### Post by jason.rgd on 2010-07-14
I installed ubuntu server but no gui!!! is it removed to give more ram for lamp processing!!! if  want to install gui what should  I do!!1

---

### Post by xoddoza on 2010-07-14
Its not installed since most server tasks can be done CLI.

```
sudo apt-get install ubuntu-desktop
```

then

```
startx
```

If I recall correctly.

---

### Post by sarim on 2010-07-14
or you can use the lxde desktop because it needs less ram so you you get more memory for LAMP.

sudo apt-get install xorg lxde

you can use vnc to connect with that desktop,

for so install a vncserver,

sudo apt-get install tightvncserver

then run this command,

sudo vncserver

then you can use a vnc viewer program to connect with your server desktop. COOL

---

### Post by jason.rgd on 2010-07-15
thanks!! I'll try it out... does this mean I use the above commands for any debian based system like ubuntu or is it ubuntu specific...

---

### Post by CharlesA on 2010-07-15
Please tunnel VNC over SSH or use NXMachine if you need to access a graphical environment on a server.

Also use a very strong password for VNC.

My server doesn't have a GUI, but I forward X over SSH for stuff that needs a gui.

They should work with any debian based OS, but YMMV.

---

### Post by sarim on 2010-07-15
> **CharlesA said:**
> Please tunnel VNC over SSH or use NXMachine if you need to access a graphical environment on a server.

i use vnc in my server.And I dont need ssh tunnel for vnc. I log into my server through ssh. then run the command,

```
vncserver
```

then it show a output like > "new X server in s1.******.com:1"

then i open tighvnc viewer in my desktop pc and give the address "s1.******.com:1" for connecting, then giving vnc password i can view and work on my server's GUI desktop. :)

---

### Post by spynappels on 2010-07-15
> **sarim said:**
> i use vnc in my server.And I dont need ssh tunnel for vnc. I log into my server through ssh. then run the command,

```
vncserver
```

then it show a output like 

then i open tighvnc viewer in my desktop pc and give the address "s1.******.com:1" for connecting, then giving vnc password i can view and work on my server's GUI desktop. :)

Is that not tunnelling over SSH?

---

### Post by moonport on 2010-07-15
> **jason.rgd said:**
> I installed ubuntu server but no gui!!! is it removed to give more ram for lamp processing!!! if  want to install gui what should  I do!!1

You can check this: [https://help.ubuntu.com/community/Installation/LowMemorySystems#Preparing%20for%20Graphical%20Environment](https://help.ubuntu.com/community/Installation/LowMemorySystems#Preparing%20for%20Graphical%20Environment)

It suggests some GUI options.
Regards.

---

### Post by CharlesA on 2010-07-15
> **sarim said:**
> i use vnc in my server.And I dont need ssh tunnel for vnc. I log into my server through ssh. then run the command,

```
vncserver
```

then it show a output like 

then i open tighvnc viewer in my desktop pc and give the address "s1.******.com:1" for connecting, then giving vnc password i can view and work on my server's GUI desktop. :)

That's not tunneling over SSH. you tunnel VNC over SSH for added security, since SSH encrypts everything end-to-end. VNC isn't encrypted at all. Sending keystrokes and screengrabs as unencrypted data is just plain stupid imo.

It might work if you are on a network that you own, but if it's on anything that you don't own, it is best to err on the side of caution.

> **spynappels said:**
> Is that not tunnelling over SSH?

No it isn't. [http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html](http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html)

---

### Post by jason.rgd on 2010-07-19
I finally have gnome and have installed the tight vnc server... thanks for the option... Now one more question... 

what if I want to view my desktop from another computer on the local lan... and switch of the gui once my work is done... What do I do for this purpose.. any ideas... I want to remove the display for the server... Only keep the cpu cabinet... without any other peripheral devices...

 the gnome starts by default... I want it to start only if I need it after I login... since I know some basic commands on linux

does the vnc server start during boot time like the LAMP server

---

### Post by sarim on 2010-07-26
> **jason.rgd said:**
> does the vnc server start during boot time like the LAMP server
I found that the vncserver  doesnot starts after login, every time after boot i need to log in to my server through ssh then run the vncserver command.

---

### Post by arrrghhh on 2010-07-26
Probably easier to use the ubuntu-desktop distro if you want a GUI... Just FYI.

Obviously, you can customize ubuntu-server to have a GUI but that's not really the purpose of ubuntu-server.  It's supposed to run lean and mean - everything can be managed from the CLI, so there's no need of the extra overhead & security issues that come with a GUI.

---

