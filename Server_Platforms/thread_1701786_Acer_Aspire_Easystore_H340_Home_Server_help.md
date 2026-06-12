---
title: "Acer Aspire Easystore H340 Home Server help"
date: 2011-03-06
forum: Server Platforms
---

### Post by ReginaldPerrin3 on 2011-03-06
I must confess to being a bit of a noob when it comes to servers and  things. I have an H340 Home Server, and I really want to eliminate any  Windows on it.
Having read what people have written here, I installed Ubuntu Server  10.10 on an empty drive via an existing machine. Then I removed the  supplied 1 TB drive with Windows Server on it from the H340, inserted  the new Ubuntu server drive.
Now I can power up the machine, the lights come on, the network light flickers with activity, and...
Well, I am at a bit of a loss at what to "do" now.

The H340 is connected to a router, just like my existing machine, so it gets an IP address from the DHCP server in the router.
How do I actually connect to the H340? I really don't know. Do I go  "Places->Network"? or "Places->Connect to Server"? Or do I do a  remote desktop connection?
When it is powered up, how does it start without a user doing a login?
There is no keyboard, screen, etc. Only the network cable.

I would appreciate some help here.
I hope I don't come across as silly and useless, I have simply never had  to deal with a Server before, so I need some hand holding for a while. I  have Ubuntu desktop and Windows 7 dual boot.

Thanks

---

### Post by excogitation on 2011-03-17
[H340 thread]("http://ubuntuforums.org/showthread.php?t=1193348")

basically you need to pull the drive again,
insert it in a box with screen, keyboard,
install opnessh-server,
put it back in the H340 and
just connect to it through "ssh IPofH340".

Use your google skills for "ssh" and also "x over ssh" if you
want to have your desktop environment to play with the H340.

---

