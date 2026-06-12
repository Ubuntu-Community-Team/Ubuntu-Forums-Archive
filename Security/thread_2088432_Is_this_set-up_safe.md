---
title: "Is this set-up safe?"
date: 2012-11-26
forum: Security
---

### Post by mythic97 on 2012-11-26
I am using Ubuntu 12.04 LTS 32bit basic firewall no anti virus to keep speed up always have internet connection and only install from trusted sites and software centre and never use credit card orders on my laptop ever do I need Anti virus or can I throw caution to the wind and keep on going like I am now?

---

### Post by sammiev on 2012-11-26
[Hers's]("http://ubuntuforums.org/showthread.php?t=510812") a great read on security.

---

### Post by coldraven on 2012-11-26
I've read that a good reason to run anti-virus in Linux is to scan things that your Windows friends give you. So, for example,  you could spread a virus on a USB stick that you shared. You would not get infected but they would.
I sometime use Clam to do that but so far I've had no detections

---

### Post by Ms. Daisy on 2012-11-26
All your questions are answered here:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by Shuudoushi on 2012-11-26
Most of the time when a virus hits Linux it is patched to the point the virus is useless. So anti-virus is mostly just from spreading the cold so to speak.

---

### Post by DukeOfMixture on 2012-11-26
As always, the last line of defense between an OS and any malware is the user.

That being said, here are the steps I take.

**1.** I edit my hosts file.

[http://winhelp2002.mvps.org/hosts.htm](http://winhelp2002.mvps.org/hosts.htm)

This will block sites that use "drive by" methods of inserting malware onto your computer. (*For a while, it included a line that disabled some godaddy images. You may want to check for that if you run into any problems with a regularly used site that might appear on the list.*)

**2.** If you use Firefox, use the NoScript add on.

**3.** Here is my ufw status:

Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
1:19/tcp                   DENY OUT    Anywhere
1:19/udp                   DENY OUT    Anywhere
22:52/tcp                  DENY OUT    Anywhere
22:52/udp                  DENY OUT    Anywhere
54:79/tcp                  DENY OUT    Anywhere
54:79/udp                  DENY OUT    Anywhere
81:122/tcp                 DENY OUT    Anywhere
81:122/udp                 DENY OUT    Anywhere
124:442/tcp                DENY OUT    Anywhere
124:442/udp                DENY OUT    Anywhere
444:65535/tcp              DENY OUT    Anywhere
444:65535/udp              DENY OUT    Anywhere
1:19/tcp                   DENY OUT    Anywhere (v6)
1:19/udp                   DENY OUT    Anywhere (v6)
22:52/tcp                  DENY OUT    Anywhere (v6)
22:52/udp                  DENY OUT    Anywhere (v6)
54:79/tcp                  DENY OUT    Anywhere (v6)
54:79/udp                  DENY OUT    Anywhere (v6)
81:122/tcp                 DENY OUT    Anywhere (v6)
81:122/udp                 DENY OUT    Anywhere (v6)
124:442/tcp                DENY OUT    Anywhere (v6)
124:442/udp                DENY OUT    Anywhere (v6)
444:65535/tcp              DENY OUT    Anywhere (v6)
444:65535/udp              DENY OUT    Anywhere (v6)

**Please note,** however, that in order to use certain tools such as whois or utorrent, you may have to adjust or temporarily disable these rules.

Here is how I applied the rules from the terminal:

```
sudo ufw deny out 1:19/tcp
sudo ufw deny out 1:19/udp
sudo ufw deny out 22:52/tcp
sudo ufw deny out 22:52/udp
sudo ufw deny out 54:79/tcp
sudo ufw deny out 54:79/udp
sudo ufw deny out 81:122/tcp
sudo ufw deny out 81:122/udp
sudo ufw deny out 124:442/tcp
sudo ufw deny out 124:442/udp
sudo ufw deny out 444:65535/tcp
sudo ufw deny out 444:65535/udp
```I don't socialize at all if I can help it, and am very certain (knock on wood) with regards to files that I download from the Internet.

But if you are concerned, ClamAv is a good idea as aforementioned in other posts. There is also a portable version for USB.

---

### Post by Ms. Daisy on 2012-11-26
> **Shuudoushi said:**
> Most of the time when a virus hits Linux it is patched to the point the virus is useless. So anti-virus is mostly just from spreading the cold so to speak. There aren't any viruses in the wild for Linux.  There are root kits and other browser-based attacks that would work in Linux, but anti-virus doesn't protect against those regardless.  

Your best bet is to follow the recommendations in the basic security wiki and the sticky threads in this forum.

---

### Post by Shuudoushi on 2012-11-27
> **Ms. Daisy said:**
> There aren't any viruses in the wild for Linux.  There are root kits and other browser-based attacks that would work in Linux, but anti-virus doesn't protect against those regardless.  

Your best bet is to follow the recommendations in the basic security wiki and the sticky threads in this forum.

I am aware of this. The bit about spreading the "cold" was about un-knowingly spreading viruses to people you know on windows.

---

### Post by Ms. Daisy on 2012-11-27
I agree with this bit: Antivirus on Linux can be used so you don't pass Windows viruses on to your contacts that run Windows.

However...

> **Shuudoushi said:**
> Most of the time when a virus hits Linux it is patched to the point the virus is useless.  See I'm kind of a stickler for details so I can't let this bit go quite yet.  There are no Linux viruses in the real world, therefore, no viruses are hitting Linux.  Vulnerabilities in Linux are continuously found and patched, just as with every other operating system. But none of those patches have anything to do with Windows viruses.

If you meant when a WINDOWS virus hits Linux, then the virus will be useless because it will only execute on a Windows box (unless you take the extra steps to make it executable on your Linux box which would just be daft). Patching has nothing to do with it in this case either.

Patching vulnerabilities is an excellent idea for every operating system and software.  Patches fix vulnerabilities that could potentially be exploited by attackers.  The Linux vulnerabilities just aren't being exploited by **viruses** at the moment.  

All viruses are exploits but not all exploits are viruses.

---

### Post by Shuudoushi on 2012-11-27
> **Ms. Daisy said:**
> I agree with this bit: Antivirus on Linux can be used so you don't pass Windows viruses on to your contacts that run Windows.

However...

 See I'm kind of a stickler for details so I can't let this bit go quite yet.  There are no Linux viruses in the real world, therefore, no viruses are hitting Linux.  Vulnerabilities in Linux are continuously found and patched, just as with every other operating system. But none of those patches have anything to do with Windows viruses.

If you meant when a WINDOWS virus hits Linux, then the virus will be useless because it will only execute on a Windows box (unless you take the extra steps to make it executable on your Linux box which would just be daft). Patching has nothing to do with it in this case either.

Patching vulnerabilities is an excellent idea for every operating system and software.  Patches fix vulnerabilities that could potentially be exploited by attackers.  The Linux vulnerabilities just aren't being exploited by **viruses** at the moment.  

All viruses are exploits but not all exploits are viruses.

Very true and good points. I was just stating that if someone did take the time to make a Linux virus it would be fruitless, do to the fact of how often Linux distros get patched to avoid such things.

---

