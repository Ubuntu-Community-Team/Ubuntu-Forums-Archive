---
title: "This is what I want to do. How do I do it?"
date: 2009-02-07
forum: Server Platforms
---

### Post by MannyL on 2009-02-07
Please explain this to me like I'm an idiot.

Currently I have a home network consisting of

two wired XP Pro system
one wired 2003 server as a domain controller (NFR from prior employer)
one wireless XP Pro System
one wireless Visa System (can not access domains)
one XUBUNTU server (uname -a Linux dumpster 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux)
One Linksys Router with 2 POTS ports for VOIP
One Linksys WiFi Router.

One 10/100/1000 switch with each device on it's own port. The Linksys with the POTS is the router between my cable modem and network

I want to be able to from outside my house access my network and retrieve files from the XUBUNTU and 2003 server. I also want to be able to use VNC to control any of the computers.

Currently I have achieved goal 2 by using vnc on mutiple ports and using the router to forward to the port I want. But I was thinking if I can make my remote system appear on the local network I could then just run VNC directly.

The remote system will usually be the  Vista system.

---

### Post by gombadi on 2009-02-07
By the sounds of things you are looking for a VPN - [http://www.openvpn.org]("http://www.openvpn.org") is your best bet.

You can configure the ubuntu server in server mode and the vista laptop as a client, open one port (udp 1194) on your router and then connect from the laptop to any of the machines in your network. Ubuntu has packages for it and the openvpn site has windows client packages.

It is not the easiest thing to setup so the Networking forum may be a better place for some openvpn config help.

---

### Post by MannyL on 2009-02-07
Thank you. I will browse that forum

---

### Post by hyper_ch on 2009-02-08
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by jimv on 2009-02-08
> See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Wow, I think it might mean that you've been posting too much when you start referencing the policies by number, lol!

:D

---

### Post by windependence on 2009-02-08
> **jimv said:**
> Wow, I think it might mean that you've been posting too much when you start referencing the policies by number, lol!

:D

Nope, it means he's right.

For the OP, I would suggest using NoMachine instead of VNC. It's much more secure and tons faster. FreeNX is here:

[http://freenx.berlios.de/](http://freenx.berlios.de/)

Paid variety (free client) here:

[http://www.nomachine.com/](http://www.nomachine.com/)

-Tim

---

