---
title: "VNC Support With 11.10"
date: 2012-03-31
forum: Server Platforms
---

### Post by brandontravis on 2012-03-31
Hey all, as you can imagine I (like others) am new-ish to Linux, and very new to Ubuntu.

I am trying to replace my Windows Home Server with Ubuntu Server that acts primarily as a media server to the multiple entertainment locations in my house.

Installation of Ubuntu Server 11.10 goes off without a hitch, get SSH setup for access from my MacBook Air running OS 10.7 and have no issues accessing everything locally.

I decided that having a desktop environment available wouldn't be a terrible ideas, as this is the first time I have used any Ubuntu variant and I haven't used any linux flavor in several years.  I installed Gnome as it is what I am familiar with.

Here is where the trouble begins.  The first VNC Server I installed was vnc4server, got it up and running properly with no issues, connected just fine from my Mac on my local network with no issues.  I can interact with the desktop just fine (create new files / folders, etc) but I cannot see the menu bars / side bar for the life of me.  I thought that I would try x11vnc, so I removed vnc4server, removed local files that I had edited to get gnome working (found that solution on a post on these forums), and installed x11vnc.  With this, I can SEE everything, but cannot interact with anything.  No keyboard or mouse support at all.

I'm sure I am just doing something stupid, but does anyone have any suggestions?

I would be happy to provide any additional information needed to get this fixed.

Thanks in advance!

---

### Post by coffeecat on 2012-04-02
*Thread moved to **Server Platforms**.*

---

### Post by CharlesA on 2012-04-02
Check out FreeNX, it goes over SSH and is way more secure than VNC.

---

### Post by arrrghhh on 2012-04-02
IMHO you should install the Desktop Edition if you want a full blown DE.  The server edition doesn't come with a DE, and most people seem to just apt-get install ubuntu-desktop - which basically defeats the whole purpose of going for the server installation!

Plus, the desktop edition has a form of VNC/remote desktop built in.  I think it uses the VNC protocol, I think it's called 'Vino'?  I haven't run the desktop version in a while, sorry.

With all that said, I also vote heavily that you give the server side a shot w/o the use of a DE.  Between web interfaces and a few CLI commands, I find myself perfectly happy running a server w/o a DE.  I know it's scary, but I swear once you get used to it you'll love it.  At least I do :p.

I'm sure that's not the answer you're looking for, but the one above mine is probably the best you're going to get.  FreeNX is worlds ahead of VNC...

---

### Post by CharlesA on 2012-04-02
> **arrrghhh said:**
> IMHO you should install the Desktop Edition if you want a full blown DE.  The server edition doesn't come with a DE, and most people seem to just apt-get install ubuntu-desktop - which basically defeats the whole purpose of going for the server installation!

Plus, the desktop edition has a form of VNC/remote desktop built in.  I think it uses the VNC protocol, I think it's called 'Vino'?  I haven't run the desktop version in a while, sorry.

It's easier to just install Ubuntu desktop anyhow. I think that's what the VNC server is called but I haven't run the newer versions of Ubuntu. It's not the best VNC server, but it gets the job done.

> With all that said, I also vote heavily that you give the server side a shot w/o the use of a DE.  Between web interfaces and a few CLI commands, I find myself perfectly happy running a server w/o a DE.  I know it's scary, but I swear once you get used to it you'll love it.  At least I do :p.

I think the only thing I use a web interface for is virtualbox, but that's only cuz I am lazy and it's easier than SSHing in and setting up a VM that way.

---

### Post by HermanAB on 2012-04-03
BTW, VNC is the favourite way to get your machine hacked.  These forums are full of tales of VNC woe.  Rather read the snailbook and use SSH.

---

### Post by eabel on 2012-04-05
i have x11vnc running on ubuntu 11.10 on my laptop through oracle vbox 4.1.12 via a win7 host.  I can access the desktop as long as i login via unity 2d or gnome classic.  I got x11vnc working using the following upstart script:
cat share/x11vnc.conf                                                                  &#9472;&#9496;
start on login-session-start
 script
 x11vnc  -rfbauth /home/eddie/.vnc/passwd -ncache_cr -xkb -noxdamage -norepeat -noxrecord -noxfixes -display :0 -auth /var/run/lightdm/root/:0 -forever -bg -o /var/log/x11vnc.log
 end script

Put the file in /etc/init and start x11vnc.  From my netbook i access the ubuntu desktop via ssh and ultraVNC.  i used ssvnc_windows (free download)  and changed the default vncviewer to ultra rather than real.  works great.  the x11vnc faq was very helpful in T/Sing issues that i ran into.  Good Luck,

Ed  ;)

---

