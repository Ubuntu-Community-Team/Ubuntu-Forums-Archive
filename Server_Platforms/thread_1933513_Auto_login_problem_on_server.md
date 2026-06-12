---
title: "Auto login problem on server"
date: 2012-02-29
forum: Server Platforms
---

### Post by Tiganjero on 2012-02-29
I have a server that doesn't have a gpu, meaning i cannot connect it to a display. I've put an HDD into my laptop and installed Ubuntu 10.04 LTS. I've set everything up the way I need it, including X11VNC and added everything to the Start-up applications. I've also set the administrator account to auto login. Everything works flawlessly until I try it on the server. I can connect to it via ssh and when I run *who -u -b* I can only see myself logged in over the network (there isn't a user on :0 which is where VNC tries to get the feed from). I'm unsure whether it could be falling back to a command line environment when it detects the lack of a gpu. The worst thing is, I can't see what it's doing.

Thanks,
George

---

### Post by TeoBigusGeekus on 2012-03-01
No idea about what's happening mate; perhaps you'll have better luck [here]("http://ubuntuforums.org/forumdisplay.php?f=339").

---

### Post by howefield on 2012-03-01
Thread moved to "*Server Platforms*" forum.

---

### Post by drdos2006 on 2012-03-01
Use Webmin to visually control your server.
Uses a browser pointed to [https://Your_server_IP_address:10000](https://Your_server_IP_address:10000) to edit files, create shares, startup shutdown daemons etc..

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb
Install with :
sudo dpkg -i webmin_1.570_all.deb

Add extra libraries with :
sudo apt-get -f install

```


regards

---

### Post by CharlesA on 2012-03-01
The GUI probably isn't starting due to the lack of a video card.

Is vnc running?

Sidenote: I would recommend using something like FreeNX instead of VNC as it is more secure.

---

### Post by Tiganjero on 2012-03-02
> **CharlesA said:**
> The GUI probably isn't starting due to the lack of a video card.

That was my first guess. What I'd like to know though, is whether I can force the gui to load no matter what.


> **CharlesA said:**
> Is vnc running?

No, it's not. I've tried detecting it with ***ps -e | grep x11*** but, it returns nothing. Which is why I've tried starting it manually. Here's the output:

```
root@administrator:~# x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800
02/03/2012 18:09:58 passing arg to libvncserver: -httpport
02/03/2012 18:09:58 passing arg to libvncserver: 5800
02/03/2012 18:09:58 -usepw: found /root/.vnc/passwd
02/03/2012 18:09:58 x11vnc version: 0.9.9 lastmod: 2009-12-21  pid: 1392
02/03/2012 18:09:58 XOpenDisplay("") failed.
02/03/2012 18:09:58 Trying again with XAUTHLOCALHOSTNAME=localhost ...
02/03/2012 18:09:58
02/03/2012 18:09:58 *** XOpenDisplay failed. No -display or DISPLAY.
02/03/2012 18:09:58 *** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
02/03/2012 18:09:58 *** 1 2 ^C
```

qBittorrent also isn't running, although it should, since it's too in Startup Applications. Output:

```
root@administrator:~# qbittorrent
qbittorrent: cannot connect to X server

```

I think that the only solution here would be to either find a workaround for gpu detection or to force the gui to start.

Thanks,
George

---

### Post by Tiganjero on 2012-03-02
Ok, so I finally remembered to check Xorg logs and the lack of a gpu _**is**_ what's causing this issue since X can't find a display. My first (and only) idea was to fool Xorg into thinking it has a display connected and move along as it would normally. So I disabled KMS and started fiddling with /etc/X11/xorg.conf. Unfortunately, none of the setting I've tried worked, hence all of them displayed this error on load.
_*[SIZE="1"]Xorg.0.log:[/SIZE]*_
```
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 2.3.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 6.0
(II) VESA: driver for VESA chipsets: vesa
(WW) Falling back to old probe method for vesa
(EE) No devices detected.

Fatal server error:
no screens found

```

I'll keep messing about the config files. Any help greatly appreciated!

Cheers,
George

---

### Post by Tiganjero on 2012-03-03
I've installed the tightvncserver package and edited the xorg.conf file a bit so it works now. I start the server, connect via ssh to it and run vncserver so it creates a virtual display :1 and points vnc to it. I'll automatize it so it's automatically run on boot. Hope this helps anyone with a similar problem.

Cheers,
George

---

