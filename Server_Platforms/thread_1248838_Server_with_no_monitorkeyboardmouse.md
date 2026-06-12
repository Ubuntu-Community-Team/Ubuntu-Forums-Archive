---
title: "Server with no monitor/keyboard/mouse"
date: 2009-08-24
forum: Server Platforms
---

### Post by Cheetah05 on 2009-08-24
Hi there,

Setting up my first file server and have a few questions.

My server is setting on an Intel atom 330 board with 2GB of RAM and 2 1TB sata drives. This is connected via a 1Gb connection to my Apple Airport Exreme router. My ONLY client is a MacBook which is connected via Wireless-N 300Mbps to my router and is usually around 1m from my router so has a decent quality signal.

I have got Ubuntu 9.0.4 installed (all up-to-date).

I want my server to have no monitor, keyboard or mouse so that I can connect to it remotely via my MacBook. I have managed to connect to Ubuntu from my Macbook using the inbuilt vnc client on my Mac. It can be quite laggy at times and I was wondering if there was any settings on the Ubuntu side that I could change to speed it up at all?

Only problem with the VNC is that I can't seem to connect to the server when it has booted without the monitor, when I plug the monitor in it says something about low graphics mode...how do I fix that?

I have managed to setup Apple Filing Protocal (AFP) which is working quite well and also means that I can use Time Machine aswell which is great.

Because I have already setup first hard drive and got all the files on it already how do I setup a RAID 1 to mirror the drive onto the second drive without screwing up anything on the first hard drive? I don't mind if it just backs up my shared files as that's all I need backed up.

Thanks for reading and any responses.

**EDIT:**
I was hoping to have it WOL when accessed too...for the files.

---

### Post by ibutho on 2009-08-24
Can't help with the VNC issue because its not something I use very often. I have a headless server that I administer through ssh. You can enable X forwarding, so that graphical apps running on your server will show on your client when using ssh. If you use a mac, this [article]("http://developer.apple.com/Darwin/runningX11.html") may help.

---

### Post by HermanAB on 2009-08-24
Install SSH Server.  It is much easier to get to work than VNC and it is secure.  Install Gnome but do not run X, leave the server in runlevel 3. Then simply do from the Apple:
$ ssh -X -C -c blowfish user@server gnome-panel

---

### Post by scorp123 on 2009-08-24
> **HermanAB said:**
>  Install Gnome but do not run X, leave the server in runlevel 3.  I was under the impression that Ubuntu, just like Debian, is imitating FreeBSD and puts everything into one runlevel, namely runlevel 2 ... ?

Taken from one of my systems:
```
> runlevel
N 2
```

[http://ubuntuforums.org/showpost.php?p=1159446&postcount=2](http://ubuntuforums.org/showpost.php?p=1159446&postcount=2)
[http://ubuntuforums.org/showpost.php?p=1165306&postcount=3](http://ubuntuforums.org/showpost.php?p=1165306&postcount=3)

---

### Post by ibutho on 2009-08-24
> **scorp123 said:**
> I was under the impression that Ubuntu, just like Debian, is imitating FreeBSD and puts everything into one runlevel, namely runlevel 2 ... ?

Taken from one of my systems:
```
> runlevel
N 2
```

[http://ubuntuforums.org/showpost.php?p=1159446&postcount=2](http://ubuntuforums.org/showpost.php?p=1159446&postcount=2)
[http://ubuntuforums.org/showpost.php?p=1165306&postcount=3](http://ubuntuforums.org/showpost.php?p=1165306&postcount=3)

Thats correct. To disable X running automatically, you'd have to disable the login manager service e.g.
```
sudo update-rc.d -f remove gdm
```

---

### Post by Cheetah05 on 2009-08-25
Forgive my ignorance, but what is the difference between ssh and vnc. I have been doing a bit of googling and by the looks of it ssh looks alot more complicated.

Also, you keep talking about levels and "X" - I don't know what these are.

It has come to my attention that the problem with the "low-graphics-mode" when you VNC into ubuntu is a common problem and possibly a bug - is this true?

I've managed to setup WOL on my computer via magic packet sending. Is there anyway to have the server wake whenever it is accessed by my Macbook so I don't have to do the magic packet sending first.

Also when I wake the computer it comes to a locked user screen, how can I get it to boot straight into a session.

Thanks for the responses.

**EDIT:**
Also, after waking from LAN I seem to have to connect to my Server via the Ip address rather than the hostname - why is this and can it be fixed?

---

### Post by scorp123 on 2009-08-25
> **Cheetah05 said:**
> Forgive my ignorance, but what is the difference between ssh and vnc. 

How about trying Wikipedia?

VNC:
[http://en.wikipedia.org/wiki/Vnc](http://en.wikipedia.org/wiki/Vnc)
> " ... In computing, Virtual Network Computing (VNC) is a graphical desktop sharing system ... "


SSH:
[http://en.wikipedia.org/wiki/Ssh](http://en.wikipedia.org/wiki/Ssh)
>  " ... Secure Shell or SSH is a network protocol that allows data to be exchanged using a secure channel between two networked devices. [1] Used primarily on Linux and Unix based systems to access shell accounts ... "


> **Cheetah05 said:**
>  I have been doing a bit of googling and by the looks of it ssh looks alot more complicated. Life is full of challenges, so that we may embrace them and grow in wisdom and experience. ;)

The thread title suggests you're running a server with no keyboard, monitor or mouse. Therefore SSH _definitely_ is what you should learn. It makes very little sense to use VNC in this scenario here.

> **Cheetah05 said:**
>  Also, you keep talking about levels 
[http://en.wikipedia.org/wiki/Runlevel](http://en.wikipedia.org/wiki/Runlevel)

> **Cheetah05 said:**
>  and "X" 
[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)


> **Cheetah05 said:**
>  It has come to my attention that the problem with the "low-graphics-mode" when you VNC into ubuntu is a common problem and possibly a bug - is this true?   I don't use VNC in such a way and I don't have that problem. "worksforme" as they call it on the Ubuntu IRC channel.

> **Cheetah05 said:**
>  I've managed to setup WOL on my computer via magic packet sending. Is there anyway to have the server wake whenever it is accessed by my Macbook so I don't have to do the magic packet sending first.  And it will wake-up ... how? I am not aware of such a possibility. That's the very reason why you need that "magic" packet or else nothing will happen.


> **Cheetah05 said:**
>  Also when I wake the computer it comes to a locked user screen, how can I get it to boot straight into a session. I don't recommend that. Really. It's a big gaping security hole waiting to be exploited if you do that.

> **Cheetah05 said:**
>  Also, after waking from LAN I seem to have to connect to my Server via the Ip address rather than the hostname - why is this and can it be fixed? I guess that depends on your DNS, router, firewall or whatever is responsible for the name resolution in your network? You could add static host entries to **/etc/hosts** (or whatever the equivalent is on your Mac) so that your server's hostname is always resolvable. Please see the manual for the details:
```
man hosts
```

---

### Post by scorp123 on 2009-08-25
I just checked an on-line copy of Apple's man pages ... and they suck quite frankly?? I thought BSD's man pages were supposed to be soooo much better than Linux ones?

Apple's man page on "hosts":
[http://developer.apple.com/documentation/Darwin/Reference/ManPages/man5/hosts.5.html](http://developer.apple.com/documentation/Darwin/Reference/ManPages/man5/hosts.5.html)

... it doesn't really explain a lot.


So here's Ubuntu's on-line version of the same manual page. It also contains examples on how host entries shoud look like. I think this one is of better use:

[http://manpages.ubuntu.com/manpages/jaunty/en/man5/hosts.5.html](http://manpages.ubuntu.com/manpages/jaunty/en/man5/hosts.5.html)

---

### Post by Dragonbite on 2009-08-25
You have a full-blown Ubuntu installation, or Ubuntu Server?

Ubuntu Server does not give you Gnome or a GUI by default, but you can add it after installation fairly easily.

---

### Post by scorp123 on 2009-08-25
> **Dragonbite said:**
> Ubuntu Server does not give you Gnome or a GUI by default, but you can add it after installation fairly easily. True, if it's really the server edition he could do e.g.
```
sudo apt-get install ubuntu-desktop
``` ... and that would add all the GUI stuff from the desktop release on top.

But: the thread title says that there is no keyboard, no mouse and no screen attached to that computer. So I don't really see the point in installing a GUI there. If that system is used as a server then running GUI stuff is a waste of CPU time and I/O cycles, aside from the potential security risks that you get into.

That's why various people suggested to keep e.g. GNOME turned off (and how we got to talk about runlevels and such).

But OK, it absolutely is a possibility to install GNOME (or KDE; or XFCE; or any of the smaller environments such as fluxbox, blackbox, etc.) and such on a "Ubuntu Server" installation ...

---

### Post by ugm6hr on 2009-08-25
I realise you have now set everything up with Ubuntu, but I can't help but recommend FreeNAS as a much simpler alternative for a Home Server.

I haven't got a Mac, but according to the FreeNAS website, AFP is supported.  Mac's also support NFS (I believe), which works flawlessly on my FreeNAS box (with Ubuntu).

The important thing is that it is designed to not have a keyboard, mouse or monitor (after initial installation).  In fact, you *can* install it with none of those things if your network router / gateway has a 192.168.1.x ip address.

If you want to have a look at how straightforward it is to install to a USB to try it out (without having to write anything to the HD), see the link in my signature below.

---

### Post by Cheetah05 on 2009-08-26
I remember that there was a reason I didn't want to use FreeNAS.

I believe it was something to do with WOL not working, but i'll give it another go.

---

### Post by dragos2 on 2009-08-26
X forwarding over SSH, but is slow.
Free NX Server -  great.

---

### Post by Knight-Server on 2009-09-11
This is what I did to fix this problem: 

In Terminal: 
gksudo gedit /etc/X11/xorg.conf

At the bottom of the file it looks like this: 
```

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```

Change it so it says:
```

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
SubSection "Display"
    Depth 24
    Virtual    1280 800
EndSubSection
EndSection

```

1280 x 800 is the resolution I like on my screen, so whatever screen resolution you want replace your values on the "Virtual" line.  They need to be multiples of 8 or 16, and some systems require 32.  

Hope this helps.

---

### Post by Cardale on 2009-09-11
This might sound stupid, but use your lan ip and not a external ip.  Oh and I use tightVNC works great.

---

