---
title: "Trying to set up an EC2 instance for remote use"
date: 2014-03-07
forum: Server Platforms
---

### Post by Pigmeat_Papa on 2014-03-07
I have sunk 16 hours over the last two days trying to set up an EC2 ubuntu instance to use as a virtual desktop. The use-case is personal computing--I'd want to connect via something like Nomachine 4 from an Android tablet. Sure, Nomachine Android is still in Alpha, but since I have yet to get the server end running with *anything*, I'm not yet concerned about that. Heck, I haven't even gotten far enough along to bring the tablet into play--I'm using a laptop running 13.04.

I'm no wiz at this, but I can (usually) follow directions. I'd swear I've followed all of the extant directions to the letter. For instance, using [these instructions]("http://xmodulo.com/2013/06/how-to-set-up-ubuntu-desktop-vm-on-amazon-ec2.html") on xmodulo (these are the most up-to-date instructions anywhere that I can find), I manage to connect with vncviewer via ssh *only long enough* to see the desktop and *start* to launch some better remote desktop app--one that requires a graphical interface (such as TeamViewer). After that, it disconnects me and I can't connect again without rebooting the instance. It's likely something wrong with how I've got vncserver set up: when I try to kill the process it says there's no such thing, but then when I try to relaunch it it says it's already running. But I might just be confused (it seemed to work the first time I tried it, from a micro instance--but not a medium or large).

For the life of me, I have been unable to get any alternative to vncserver to work at *all. *I tried xrdp, x2go, and freenx, but obviously don't really know what I'm doing. For all I know, the x2go and freenx servers were running fine and I couldn't figure out how to connect to them.

My question is just: does anyone have an easier way of doing this? Surely I can't be the only non-developer who likes using Ubuntu and thought to himself, "Gee, I wish I could connect to a cloud instance of my favorite distro from this tablet."

---

### Post by TheFu on 2014-03-07
First, 13.04 is unsupported. Either switch to 12.04 or 13.10 if you will update in April to 14.04.

NoMachine v4 clients **only** work with NoMachine servers.  I've been using NoMachine 3.5.x clients to connect to FreeNX for years ... literally. Clients are on Windows7 x64 and Ubuntu 12.04 x32. No Android client exists.

I'm typing this reply on an NX virtual desktop running from a different machine.  that machine is 2ft away, but I routinely use it from across town or across the globe (Nepal, Seoul, Singapore, Thailand, South Africa, Amsterdam, or around the USA). This is my default desktop mode. The virtual desktop runs under KVM (Ubuntu 12.04 server) with an Ubuntu 12.04 Server+LXDE client VM.  No reason this shouldn't work from EC2 as well - though I haven't tried it.

FreeNX is non-trivial to get working, it seems.  I've helped a few people here get it going, but it was always painful - for some reason.  OTOH, I was able to follow the instructions and within 15 minutes, was up and connected. Haven't touched those settings since. It has been reproducible too - 5 minutes to setup now. Also have set this up at work for remote desktops for a few key people - running Ubuntu 12.04 Server + LXDE.

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) - follow the instructions carefully. There are multiple manual steps AFTER the **sudo aptitude install** parts.  Creating a cert, installing that cert inside every client ... read carefully. If you use the default cert, then everyone in the world can access your NX server. 

BTW, I resume sessions all-the-time ... like every day, so that note is not accurate for everyone. I've been unable to get NoMachine NX client v4.x working anywhere. On Android, the alpha client starts, blanks the screen and dies. I'd love to travel with a tablet instead of a $250 netbook, but having a real OS is helpful to troubleshoot hotel filters. The [Acer C720]("http://www.amazon.com/Acer-C720-Chromebook-11-6-Inch-2GB/dp/B00FNPD1VW") looks impressive (re-loaded with Ubuntu) ... I may get one. I'll miss the wired ethernet port and 500G HDD greatly.  My current netbook, Asus Eee, is only 600p and about 12x slower, so something more capable, higher resolution, with a longer battery life (8+hrs) would be good.  I just convinced myself - need to order a 100G compatible SSD to go with it.

I think mixing virtual desktops can be confusing, so I don't do it. VNC and RDP performance suck compared to NX anyway.  KVM uses VNC for the "console" - it is painfully slow - and that is being nice.  Normal VNC is 20x faster than the KVM built-in crap.  Don't know about Xen (which is what Amazon uses). Never used the built-in VNC when I ran Xen VMs.

So ... if you have an Ubuntu 12.04 box on your LAN, get FreeNX working on it, practice, understand, then try to get it working on EC2. That's my advice.

---

