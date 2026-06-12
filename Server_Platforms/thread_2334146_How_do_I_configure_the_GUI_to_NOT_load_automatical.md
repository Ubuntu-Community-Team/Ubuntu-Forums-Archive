---
title: "How do I configure the GUI to NOT load automatically on startup. (Ubuntu Serv. 16.04)"
date: 2016-08-16
forum: Server Platforms
---

### Post by fromwin2lin on 2016-08-16
I don't want the GUI to load automatically on startup. I am using Ubuntu 16.04.1 Server with the Lubuntu GUI installed. Lubuntu-desktop is the lightest I could find. Does anybody know how to configure the GUI to not start automatically and if I wanted to load I just type in the command: "startx"?

---

### Post by ian-weisser on 2016-08-16
There's an explanation of exactly how to do it at [http://linux.m2osw.com/boot-command-line-console-ubuntu-1604](http://linux.m2osw.com/boot-command-line-console-ubuntu-1604)
It's a systemd setting.

---

### Post by MAFoElffen on 2016-08-17
Please read what you are linking to...You are correct, but it is not a systemd setting. It is just appending "text" to the kernel boot line as a kernel boot option. (via the grub2 /etc/default/grub file)

The problem with loading a full desktop environment with the login manager, is that it add's hooks into the lgraphical login manager. When you start the XSession and try to exit it, it gets a little lost. Because you don't want to shutdown a server, nor retrun to a graphical login... just get back to the console prompt. 

The way I get around that is to not use shutdown, but rather open a terminal and get the PID's of the DM and of Xorg... Then kill them. It will cleanly get back to the console prompt.

Another way is to remove the graphical login manager, but that sometime boinks the Desktop Environment/ Window Manager..

For more details, look at my Graphics Resoltuion Sticky linked in my sigline... or search on my posts here. For server, think console.. if an XSession is wanted, then think just a minimal instance that you can remove all trace of when not needed. IMHO- That should be the goal.

---

### Post by springshades on 2016-08-17
I'm not sure if this will work for your particular expectations, but what about just adding the following lines to /etc/rc.local before the exit line:

```
systemctl start multi-user.target
sleep 3
chvt 1
```

and then running the command:

```
sudo systemctl enable rc-local.service
```

to enable the script.

The upside is that this is a pretty simple option. The downside is that it requires root permissions to start the GUI, and it actually boots to a GUI *first* and then shuts it down. You would have to start the GUI with the command:

```
sudo systemctl start graphical.target
```

---

### Post by mastablasta on 2016-08-17
> **fromwin2lin said:**
>  Server with the Lubuntu GUI installed. Lubuntu-desktop is the lightest I could find.

lightest windowed one would actually be jwm, however i consider IceWM to be a bit easier to setup and understand.

there are also a few tiled Windows options available such as i3 or awesomewm etc.

there is no need for a GUI on a server, but you could also use a webgui if needed (have a look at Ajenti for example)

---

### Post by MAFoElffen on 2016-08-18
+1 with MastaBlasta.

I have a minimum X (instance-load) installed on some of my servers for admin tools on those specific servers, but I use OpenBox (with no logon manager). That is the lightest that I am using. No frills. Very little overhead. And like I mentioned, just does an instance load of X, when required. That specific server has a GUI RAID utility for it's hard RAID, that if not accessible, alternately would require bringing down that server offline to maintain. So I can see both sides, within reason.

To the poster that mentioned loading X as "root":
.. One thing that root cannot and should not do is load an XSession. First root does no have XAuthority to start an XSession. You can force it, by tricking it, but that has problems when you "force that." It is also not a good idea security-wise, to open up that rabbit hole, especially on a server.

---

