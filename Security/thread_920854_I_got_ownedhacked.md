---
title: "I got owned/hacked"
date: 2008-09-15
forum: Security
---

### Post by Pete89 on 2008-09-15
Hello,

I am running postfix 2.3 on Debian 4.0 and I got hacked. I can see multiple attempts to connect to gmail and visi.com for some reason. I htough I was pretty good about doing updates and keeping up on patches.

I have the box blocked off now but what I want to do is forensically find out what happened. Can anyone give me some tips on how to tackle this?

I have checked the history command and see nothing that I have not done so I dont think it was rooted. One thing odd is clamav has the cpu pegged at 98% but that is not too odd since this is an NSLUS (SLUG) running Debian.

Being owned sucks...

Thanks,

Pete

---

### Post by rogeriopvl on 2008-09-15
Check for rootkits (install rkhunter) and check in detail every log. If you were hacked and noticed in time, you might have some trails that the attacker left unclean.

---

### Post by Pete89 on 2008-09-15
A little more information. RKhunter found gave me one warning:

 Scanning for hidden files...                               [ Warning! ]
---------------
/etc/.pwd.lock /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools 

Please inspect:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory) 

But I looked around and this seems to be a common false positive for Debian.

The little bugger has now stopped trying to send traffic out on port 25 and has switched to UDP 123 which I did have open outbound at one point. This box is in a DMZ which is now allowing nothing in or out.

---

### Post by brian_p on 2008-09-15
> **Pete89 said:**
> Hello,

I am running postfix 2.3 on Debian 4.0 and I got hacked. I can see multiple attempts to connect to gmail and visi.com for some reason.

Check your postfix configuration. Assuming these are incoming connections it is an attempt to relay mail through your machine. You, of course, have set up postfix to disallow this so it will fail. Perfectly normal. No hacking.

> I have the box blocked off now but what I want to do is forensically find out what happened. Can anyone give me some tips on how to tackle this?

The postfix logs are your first port of call.

---

### Post by Pete89 on 2008-09-16
> **brian_p said:**
> Check your postfix configuration. Assuming these are incoming connections it is an attempt to relay mail through your machine. You, of course, have set up postfix to disallow this so it will fail. Perfectly normal. No hacking.

No these are active outbound connections from the mail server to the world. First I see a boat load of DNS lookups and then a whole lot attempts to connect via tcp 25 to many google and visi servers. This is then followed by attempts to connect to other bots over port udp 123.

---

### Post by brian_p on 2008-09-16
> **Pete89 said:**
> No these are active outbound connections from the mail server to the world. First I see a boat load of DNS lookups and then a whole lot attempts to connect via tcp 25 to many google and visi servers. This is then followed by attempts to connect to other bots over port udp 123.

So not a postfix problem after all.

---

### Post by FakeOutdoorsman on 2008-09-16
These are interesting reads and might give you some insight:
[Hacked Linux Checklist]("http://blog.gnist.org/article.php?story=HollidayCracking")
[Dead Linux Machines do Tell Tales]("http://www.giac.org/practical/GCFA/James_Fung_GCFA.pdf") [link to pdf]

Once the investigation is done I highly recommend wiping the drive, reinstalling the OS, and reading the [Securing Debian Manual]("http://www.debian.org/doc/manuals/securing-debian-howto/").

---

### Post by hyper_ch on 2008-09-17
> **Pete89 said:**
> I am running postfix 2.3 on Debian 4.0 and I got hacked. I can see multiple attempts to connect to gmail and visi.com for some reason. I htough I was pretty good about doing updates and keeping up on patches.

Are you sure that you didn't just run an open relay mailserver?

---

