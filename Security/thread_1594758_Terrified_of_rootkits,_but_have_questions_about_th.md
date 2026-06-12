---
title: "Terrified of rootkits, but have questions about them"
date: 2010-10-12
forum: Security
---

### Post by Fingerfin on 2010-10-12
So... I'm not a very advanced user. In the past I've been even worse, and I know I used to be very lax and negligent about security. Basically, I've been running ubuntu and windows 7 dual boots on 2 computers with absolutely no regard for security for over a year. At this point I've already virus scanned windows and checked ubuntu for rootkits with chkroot and rkhunter. Windows virus scanner found many viruses but no rootkits. I'm sure at least one of my machines can have rootkits on it, at least because it was a bootleg my friend got off some random torrent site.

So this time I want to do a full fresh start with all security measures in place. But I'm still not 100% sure of what to expect from rootkits. Would quick formatting my entire drive guarantee that no traces of a rootkit remain? And I'm not even ruling out that I have some on my linux partitions that evade detection by rkhunter and chkroot (though I trust I'm so unimportant that nobody should bother infecting me with advanced malware). Is it safe to download and burn an OS install image on a compromised machine?

---

### Post by yaroto98 on 2010-10-12
On the Windows side for checking for rootkits:

[http://www.softpedia.com/get/Antivirus/F-Secure-BlackLight-Rootkit-Detection.shtml](http://www.softpedia.com/get/Antivirus/F-Secure-BlackLight-Rootkit-Detection.shtml)

Try Blacklight, it does a good job.

Unfortunately the only way to be COMPLETELY sure there aren't any rootkits, is a complete reformat installing from an uncompromised source.

From my experience Rootkits are very rare if you keep use good security measures.

---

### Post by Fingerfin on 2010-10-12
Well yeah, I guess my initial post was a bit incoherent. I just want to reformat all my drives to be completely sure so I can just sleep tight and run securely. It's a bit irrational, but I'm haunted by the ubuntu updates that I'd put off for months, the windows updates I never got on one install, the other windows install which came with who knows what secretly installed, my daily visits to really shady-looking sites, the times I was logged in as root for no good reason.

 So I guess the two biggest questions I have are:
 1. What would be an uncompromised source?
 2. Is there a way for me to get this source through a potentially compromised system and still be very sure that the source is uncompromised?

---

### Post by uRock on 2010-10-12
> **Fingerfin said:**
> So I guess the two biggest questions I have are:
 1. What would be an uncompromised source?
 2. Is there a way for me to get this source through a potentially compromised system and still be very sure that the source is uncompromised?
Download and burn the latest Ubuntu ISO to disk and use your Windows install disks that came with the machine.

Install Windows first so that you don't have to go back and reinstall the boot loader.

I think you can use the GParted live disk to format the disk drive before installing.

---

### Post by WeAreLinux on 2010-10-13
Just want to add, after downloading the Ubuntu ISO, make sure the md5 is correct:

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you're still feeling uneasy about downloading Ubuntu from your machine, you can request a free CD with Ubuntu's Ship It Program (takes forever though) or buy the latest version from Canonical.

[http://www.ubuntu.com/desktop/get-ubuntu/cds](http://www.ubuntu.com/desktop/get-ubuntu/cds)

[http://shop.canonical.com/](http://shop.canonical.com/)

---

### Post by HermanAB on 2010-10-13
Relax dude.  I've been running UNIX systems since about 1985 and have never seen a real live rootkit.

---

### Post by ehode on 2010-10-13
I can understand the concern about rootkits.  Like they said, best bet would be a format (overwriting the mbr) and install from a fresh and known source.  

Now days running cracked software just isn't worth the hassle IMHO.

---

