---
title: "Server install and wireless"
date: 2008-04-23
forum: Server Platforms
---

### Post by Oak37 on 2008-04-23
Hi all,
I've installed the release candidate 8.04 on one of my servers. Previously I had been using the desktop versions of Ubuntu but wanted to give the server version a go to save on system resources etc.
My problem is getting the wireless card enabled. It was recognised straight away on the desktop edition since 7.04 I believe but isn't on the server edition. Does anyone have any ideas on where to start solving this?
I've tried pinging one of my other servers but the network is unreachable, I copied and pasted my /etc/network/interfaces file over from my other server (which has the same card) but still nothing.

Thanks for any help you can provide!

---

### Post by bluefrog on 2008-04-23
is your card recognized?

lspci | grep -i "network\|ethernet"

or at least lspci and check if you see your card.

What card is it? is it using restricted drivers with you other ubuntu?

---

### Post by Oak37 on 2008-04-23
Thanks for the reply!
lspci | grep returns what I think is the Wireless card:

Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

My other computer is using restricted drivers specifically "Atheros Hardware Access Layer (HAL)"
Is there a way I can enable this?

---

### Post by bluefrog on 2008-04-23
you need to find what package gives you the restricted driver and install it on your server.

---

### Post by Oak37 on 2008-04-23
I found the linux-restricted-modules package for the kernel version but it doesn't seem to want to load up at start up. This could be because I installed the generic version and I need the server version but there appears to be no server version.
After reading around it seems a common problem trying to use restricted devices on the server kernel as they don't seem to be supported, I'll keep looking around to see if I find anything.
Thanks bluefrog for your help :)

---

### Post by honeydew on 2008-04-23
maybe try 
```
apt-get install linux-restricted-modules-`uname -r`
```

the  ` is the one on the left next to the number 1.

---

### Post by Oak37 on 2008-04-24
I think I've found out the package I want (Package: linux-restricted-modules-2.6.24-16-server), it isn't on the install cd but it is available online. I'll use the ethernet on the server to download and install it so hopefully that will do the trick! I'll report back with my findings ;)

---

### Post by Oak37 on 2008-04-25
I was able to get the wireless card working by compiling the madwifi drivers myself but couldn't get my head around the WPA_supplicant program. For the sake of reference and for anybody that might find themselves in this situation I've included my steps below:
[LIST]
[*]I followed the installation steps found [here]("https://help.ubuntu.com/community/Router/Madwifi").
[*]This [page]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo") was invaluable in adding on to the previous link as well as providing information on various types of encryption.
[/LIST]

As for my own solution I decided to install a minimal graphical environment consisting of xorg and ICEwm and then used wicd for setting up my network configuration. Worked well for me, hope this helps anybody else in a similar situation :)

---

