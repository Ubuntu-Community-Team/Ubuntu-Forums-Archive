---
title: "Processor constantly at max"
date: 2011-06-02
forum: Server Platforms
---

### Post by Leon D on 2011-06-02
Hi folks,

I recently installed both Ubuntu server and the desktop environment onto an old Dell 2350 with a 1.7 Intel Celeron, 512 Ram and a newly installed 160GB seagate HD.

I added the desktop for the GUI as I have no idea about command line and whenever I use it it usually takes me several days of trawling sites to get the machine to do what I'm wanting!

I have a problem though, the processor is regularly overheating and is on at 100% time, is this because the hardware is not up to the task or something else?

All I wanted is to add an extra level of security for the home network as both my parents work from home on windows machines, they seem to always get viruses (which I'm fed up of trying to fix!), so having the ability to route all internet traffic through a linux box would be great as I know the security/reliability with Linux is numero uno!

Cheers,

Leon

---

### Post by Joe of loath on 2011-06-02
The GUI you're running, is it Unity? Because that's quite heavy on resources. Try logging into the classic Gnome desktop.

Also, having the box as a router/firewall won't completely stop the Windows boxes getting viruses.

---

### Post by Leon D on 2011-06-02
Hi Joe,

I did get a pop up advising to run the desktop in classic, which I've done.  I still have the same problem re: the processor though.

Oh, will it provide any level of extra security or is it not worth it?

Cheers

---

### Post by JohnBonne on 2011-06-02
Joe, hey,
Had the same problem on my HP until I got the Xorg graphics for my Intel GPU.

---

### Post by Joe of loath on 2011-06-02
A decent firewall distro like smoothwall will be better, and easier, than setting up a Ubuntu box to do the same job. You could also use a lower end box, and use less power, since smoothwall is very light.

---

### Post by Leon D on 2011-06-02
Cheers Joe,

That looks like a cracking idea, thanks for the heads up :D

---

### Post by ruffEdgz on 2011-06-02
> **Joe of loath said:**
> A decent firewall distro like smoothwall will be better, and easier, than setting up a Ubuntu box to do the same job. You could also use a lower end box, and use less power, since smoothwall is very light.

+1 for this suggestion.

Whenever someone is interested in a server based machine to help with firewalls or something, I would always recommend CLI only with no GUI support to make sure the purpose of the box uses all of its resources on the task at hand. Not for the GUI frontend.

I helped a friend set this up at his place and its a very good product:

[http://www.smoothwall.org/](http://www.smoothwall.org/)

---

### Post by JohnBonne on 2011-06-02
> **Leon D said:**
> Hi Joe,

I did get a pop up advising to run the desktop in classic, which I've done.  I still have the same problem re: the processor though.

Oh, will it provide any level of extra security or is it not worth it?

Cheers

I meant Leon, hey.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

[https://help.ubuntu.com/community/InstallingUbuntuOnADellLatitudeX1](https://help.ubuntu.com/community/InstallingUbuntuOnADellLatitudeX1)

---

### Post by Leon D on 2011-06-02
Cheers guys, I'm downloading Smoothwall now!

And thanks John, I'll remember that tip for the next time I get to try and play with Ubuntu ;)

---

### Post by JPorter on 2011-06-08
Smoothwall (the free version) is fine for many situations, but "out of the box" it lacks some advanced features that may be needed in the future, like multi-WAN, VLAN trunking, IPsec VPN, etc.

Another (free) alternative is pfSense. It's a high performance, highly secure router/firewall distribution based on FreeBSD. The feature list is quite a bit longer by default than smoothwall, pfSense offers a range of features that are typically only found on commercial firewalls or commercial firewall distributions (at significant expense).

We use pfSense in production here and we've been pleased with it. It is very stable, and maintains high throughput even on relatively low-spec hardware. It may not fit your current needs, but it's worth filing away for future reference.  [http://www.pfsense.org/](http://www.pfsense.org/)

---

