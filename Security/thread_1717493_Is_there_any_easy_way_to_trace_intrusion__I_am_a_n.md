---
title: "Is there any easy way to trace intrusion ? I am a newbie !"
date: 2011-03-29
forum: Security
---

### Post by Abhihemu on 2011-03-29
Hi all :)
[LEFT]i am a new linux user, yesterday my one friend scanned my pc from his city and told me about the webpages i opened. He told me that i have 58 open ports. I was scared, he suggested me to use Live CD for surfing.:shock:
[/LEFT]

 Actually i don't know anything about these things but i want to remain safe,I read the snort tutorial which seems tough for me to do!  isn't there any easy to use graphical software for Ubuntu which can show me any intrusion ? and which i can stop it using graphical buttons?:confused:

---

### Post by collisionystm on 2011-03-29
All you need to do is enable a firewall on your computer. Just remember the most basic firewall works like this:

all outbound traffic from your computer is allowed
all inbound is blocked

HOWEVER, whenever you access a webpage or a program on your computer runs, it goes out of your firewall and in turn, opens a port in it. that port is now open for traffic to flow back and forth until you close the program or webpage. so just install a firewall. i would use gufw . When you are done on a web page, or on a page you dont really trust. close it.

---

### Post by cariboo on 2011-03-29
If you have a default install, you have nothing to worry about. Problems start when you install services without securing them. The most common two services that lead to problems are ssh and remote-desktop sharing secured by weak passwords.

If you are behind a router, and you have no ports forwarded, you won't have any problems with people trying to crack your system, just make sure you have uPNP turned off, as there are a few programs that will use uPNP for port-forwarding.

There are a lot of people that believe in the belt and suspenders approach, they have a firewall on their computer as well as a router, but I've been behind a router since 2002, and haven't had a system cracked **yet**.

---

### Post by Abhihemu on 2011-03-30
Thanks
@[collisionystm]("http://ubuntuforums.org/member.php?u=1249225") as u said i installed Firewall gufw and have enabled it. :)

@cariboo907 i have unchecked remote desktop in the start up application list. My modem says it's ADSL2+Router i know nothing more. I use Transmission Torrent client for ISO downloads, how to turn off uPNP ?
Thanks for your replies :)

---

### Post by cariboo on 2011-03-30
I use my web browser to acces the management console on my Linksys 310N. If you know your gateway address, just type:

```
http://<gateway_address>
```

enter the user name and password, that you used to set it up, then change the settings.

---

