---
title: "Anti-Virus and Encryption"
date: 2016-02-04
forum: Security
---

### Post by incurablegeek on 2016-02-04
Please excuse the double question.

1) On my Window 7 computers (now migrating all 6 computers to Kubuntu), I use Avast Free Antivirus. Is there something more suitable to Kubuntu 14.04

2) The last time I communicated with Bruce Schneier (quite a while ago so his position may have changed), he said that TrueCrypt, though no longer supported, was still he best in that no "back door" was known. Would TC still be the best choice for Kubuntu?

Please understand that I am hesitant to rely on any encryption built into the OS, whether it be Windows or Linux.

Note: This link does refer but is not thorough or detailed: [http://ubuntuforums.org/showthread.php?t=2312389&highlight=Anti-Virus+Encryption](http://ubuntuforums.org/showthread.php?t=2312389&highlight=Anti-Virus+Encryption)

Thanks!

---

### Post by Habitual on 2016-02-04
in 15 years, I have never seen a Linux virus on a Linux host.
And I don't use, or recommend any AV,
and I have truecrypt-7.1a and not afraid to use it.

---

### Post by pfeiffep on 2016-02-04
> **incurablegeek said:**
> Please excuse the double question.

1) On my Window 7 computers (now migrating all 6 computers to Kubuntu), I use Avast Free Antivirus. Is there something more suitable to Kubuntu 14.04
<snip>
Thanks!I don't use antivirus programs on my Ubuntu installs. 
If you plan to communicate with Windows PCs **and** you want to insure that you don't inadvertently share a virus with Windows you might consider using [ClamAV]("http://www.unixmen.com/installing-scanning-clamav-ubuntu-14-04-linux/")

---

### Post by incurablegeek on 2016-02-04
The only reason I will ever need to communicate with Windows computers is to pull files off of them, install Kubutu on another and so on down the line.

So I will look into Clam AV.

Btw, I have a pfSense firewall. Will that be adequate?

---

### Post by 1clue on 2016-02-04
While Linux-based systems are not prone to viruses, they are as susceptible to other forms of malware as Windows is.

The system can be hardened, but much of this depends on users not being stupid.  Also note that Canonical does not simply release an insecure operating system, but as always there is a fine line between ease of use and security.

There is no easy solution here. With ANY computer, the best defense is between your ears.

You might start here:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)
[http://www.ubuntu.com/usn/](http://www.ubuntu.com/usn/)

Most of that is distribution-independent, meaning it applies pretty much to any type of Linux.  The last link is specific to Ubuntu-based distros.

---

### Post by pfeiffep on 2016-02-04
> **incurablegeek said:**
> The only reason I will ever need to communicate with Windows computers is to pull files off of them, install Kubutu on another and so on down the line.

So I will look into Clam AV.

Btw, I have a pfSense firewall. Will that be adequate? +1 for 1clue > There is no easy solution here. With ANY computer, the best defense is between your ears.and I might add the other users also!
If you don't plan on sharing to Windows then I wouldn't waste time with ClamAV

---

### Post by 1clue on 2016-02-04
pfSense is a FreeBSD-based firewall.  It's as good as many commercial offerings, and in fact there is a paid support plan with them so they can be considered a commercial offering.

I would point out that a typical wireless router appliance is notoriously insecure.  pfSense and/or Linux-based firewalls can be much better, based on the care and knowledge of the administrator.

Personally I consider defense in depth to be important, so even though you have pfSense I would still lock down each computer as much as possible.  Especially if you have WIFI on the inside.

So that brings up another thing.  If WIFI connects to your lan, then that lan is insecure.  If you have 3+ interfaces on your pfSense box, you might consider a dual firewall, one from the Internet and one from the WIFI.

---

### Post by incurablegeek on 2016-02-04
> Especially if you have WIFI

Rest assured, gentlemen, I **never use WiFi**. Those routers are porous. I even heavily criticized Cisco routers as being potentially insecure despite "layered security". 

Also my passwords are so complex I cannot remember them (been using LastPass)

Thank you so much for the helpful links. I would assume that what is recommended for Ubuntu would also be good for Kubuntu, since only the GUI is different.

---

### Post by 1clue on 2016-02-04
Kubuntu is using the same repository as ubuntu. You can technically switch from one to the other post-install.

The usn site will distinguish between them if necessary.

---

### Post by incurablegeek on 2016-02-04
I kind of knew the answer, but was just hoping for reassurance and possibly a pat on the head.  ):P

I would even venture to say (quite tenuously) that what works in Unix would probably be at least adaptable to Linux, Fedora, etc.

In conclusion, I would really like to thank you folks for taking time with me. This is a most unusual forum in that it is welcoming, helpful and well-mannered. 

Whenever I encounter trolls on a forum, I leave that forum. I just don't need the anxiety. For what it's worth one of my partners in India said he has experienced really awful people on some forums there, and he himself leaves them for the same reasons.

Thanks again!

[CENTER][SIZE=3]**Ubuntu is the Future!**[/SIZE]
[/CENTER]

---

### Post by 1clue on 2016-02-04
Have you considered nested firewalls? Or ids/ips like snort or suricata?

I'm trying to get some of this going.

Trolls here get banned. They're third class occupants here, don't let them chase you off.

Linux vs UNIX: generally speaking they're very similar. You will find that the open source versions of the standard tools is usually much better. Vim vs vi, or less vs more. I've found that in some cases it is reversed though, I've seen Solaris do some pretty good stuff. Not sure if it was the os or a really good sys admin.

---

