---
title: "Still required to enter keyring"
date: 2006-12-14
forum: System76 Support
---

### Post by eg-maverick on 2006-12-14
I'm having a problem with my system and wifi and keyring. When I use my wifi connection, i am asked to enter my keyring password twice. My understanding was that the issue of entering keyring for network manager was resolved in Edgy and the newest NM. However, I've taken a step back in that I have to enter it twice. I had a problem with NM and my laptop that was fixed in thread [http://www.ubuntuforums.org/showthread.php?t=243229](http://www.ubuntuforums.org/showthread.php?t=243229) but that change is still in the file /etc/network:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp
#wireless-essid EG Duramax
#wireless-key 463f4e2160

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

Any ideas how I can resolve this problem?
Thanks,
Craig

---

### Post by crichell on 2006-12-14
The first portion of this How To looks promissing:

[http://www.ubuntuforums.org/showthread.php?t=316927&highlight=network+manager+keyring](http://www.ubuntuforums.org/showthread.php?t=316927&highlight=network+manager+keyring)

We're going to test it this afternoon.

---

### Post by newlinux on 2006-12-14
I have this problem as well on my laptop, but I've just lived with it... would be nice to fix. Looking forward to seeing if the how-to fixes it...

---

### Post by EriK76 on 2006-12-14
The how to listed  worked.

[http://www.ubuntuforums.org/showthread.php?t=316927&highlight=network+manager+keyring](http://www.ubuntuforums.org/showthread.php?t=316927&highlight=network+manager+keyring)

My keyring password and my login password are the same so I only followed steps 1 thru 3 of Part 1.  

I did not have to do Part 2 but I wasn't having the multiple keyring pop-up issue.

---

### Post by newlinux on 2006-12-14
I think I'll give it a try this weekend. My login password and keyring password aren't the same so we'll see...

---

### Post by frainbart on 2006-12-14
I use the pam-keyring that others have cited above successfully. It works like a charm on my 12" Gazelle Value.

---

### Post by newlinux on 2006-12-19
worked for me too. I still have a problem where sometimes network manager doesn't "see" my home network unless I turn the networking off and on. I don't quite know what this is. kismet always sees my network, so it's probably not the hardware... It always sees my neighbor's wireless network and loves to connect to that (and it's unsecured). But I'm no longer asked for 2 passwords... or even one when it finally does recognize it.

---

### Post by eg-maverick on 2006-12-20
Well, now I only have to enter the keyring password once each time I power up or go to a new wifi spot. Weird.

---

### Post by eg-maverick on 2006-12-21
I just went through the massive update requested from auto-update and now I have to enter my keyring password twice again. Argh. I'm going to try the previous fix again and see if I can get it back to one request, at least.
Craig

---

### Post by michaeljb2005 on 2007-01-05
> **eg-maverick said:**
> I just went through the massive update requested from auto-update and now I have to enter my keyring password twice again. Argh. I'm going to try the previous fix again and see if I can get it back to one request, at least.
Craig

Might I recommend trying wifi-radar for dynamic wireless networking and netapplet for switching between local and wireless networking.  

Wifi-radar works in the background you just have to open it to configure secure networks requiring passwords.  After that it will automatically choose networks already configured or connect to networks that are not password protected if it can't find anything else to connect to.  

Netapplet sits there on your gnome-panel and you just click on it when you want to change back and forth.  Once you install it, just run it using netapplet and if you want it to run on startup just put netapplet in your list of startup commands.  

Just so you know, in feisty they're supposed to be updating network manager to also work with static addresses as well as dynamic and making wireless networking more hassle free.  Perhaps that will be the all in one solution on the next release.

Thanks.

---

### Post by crichell on 2007-01-05
> Perhaps that will be the all in one solution on the next release.

That's the impression I'm getting too.  System > Administration > Networking will be revamped as well - no more wiping out network-manager-gnome.

---

### Post by eg-maverick on 2007-01-06
> **michaeljb2005 said:**
> Might I recommend trying wifi-radar for dynamic wireless networking and netapplet for switching between local and wireless networking.  

Wifi-radar works in the background you just have to open it to configure secure networks requiring passwords.  After that it will automatically choose networks already configured or connect to networks that are not password protected if it can't find anything else to connect to.  

Netapplet sits there on your gnome-panel and you just click on it when you want to change back and forth.  Once you install it, just run it using netapplet and if you want it to run on startup just put netapplet in your list of startup commands.  

Just so you know, in feisty they're supposed to be updating network manager to also work with static addresses as well as dynamic and making wireless networking more hassle free.  Perhaps that will be the all in one solution on the next release.

Thanks.

This sounds like what I've been looking for on both fronts: a solution that works and a system release that does what Windows did years ago (sorry - I just don't get why Linux makes portable networking so hard). Anyway, Thanks for the really good news. I'll give wifi-radar a try and let you know how I get along. Regards,
Craig

---

### Post by eg-maverick on 2007-04-24
> **crichell said:**
> That's the impression I'm getting too.  System > Administration > Networking will be revamped as well - no more wiping out network-manager-gnome.

Carl,
I seem to have the same results since upgrading to Feisty, i.e. I have to enter the keyring password each time. Now I haven't uncommented the network interface file or uninstalled NM applet. If I do both of those things will wireless work right?
Thanks,
Craig

---

### Post by thomasaaron on 2007-04-24
If you uncommented the network interfaces file and shut down the applet, you could set your internet connections with System > Admin > Networking.  If I remember correctly from my dapper days, it should connect automatically to whatever your last AP was (??).

And you should no longer get the keyring.

---

### Post by eg-maverick on 2007-04-25
> **michaeljb2005 said:**
> Might I recommend trying wifi-radar for dynamic wireless networking and netapplet for switching between local and wireless networking.  

Wifi-radar works in the background you just have to open it to configure secure networks requiring passwords.  After that it will automatically choose networks already configured or connect to networks that are not password protected if it can't find anything else to connect to.  

Netapplet sits there on your gnome-panel and you just click on it when you want to change back and forth.  Once you install it, just run it using netapplet and if you want it to run on startup just put netapplet in your list of startup commands.  

Just so you know, in feisty they're supposed to be updating network manager to also work with static addresses as well as dynamic and making wireless networking more hassle free.  Perhaps that will be the all in one solution on the next release.

Thanks.

I tried wifi=radar and couldn't get it to work. Still looking for a solution running under 7.04.

---

### Post by DynaWerx on 2007-05-01
Here's what worked for me.

Append the following to the end of /etc/pam.d/gdm:
```
@include common-pamkeyring
```

I found this in the comments section at [http://johnny.chadda.se/2007/02/21/unlock-the-gnome-keyring-upon-login/](http://johnny.chadda.se/2007/02/21/unlock-the-gnome-keyring-upon-login/)

---

### Post by eg-maverick on 2007-05-02
> **DynaWerx said:**
> Here's what worked for me.

Append the following to the end of /etc/pam.d/gdm:
```
@include common-pamkeyring
```

I found this in the comments section at [http://johnny.chadda.se/2007/02/21/unlock-the-gnome-keyring-upon-login/](http://johnny.chadda.se/2007/02/21/unlock-the-gnome-keyring-upon-login/)

Thanks for the suggestion. However, it's already in the gdm. My login and keyring password are different. I would be willing to change it (the keyring) if I knew how.

---

