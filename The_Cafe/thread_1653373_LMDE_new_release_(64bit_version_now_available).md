---
title: "LMDE new release (64bit version now available)"
date: 2010-12-26
forum: The Cafe
---

### Post by PC_load_letter on 2010-12-26
Sorry if it has been posted here before. A new release of Linux Mint Debian Edition was out on 12/24. I'm downloading it right now, plan on installing it later tonight. This is awesome!

**EDIT: **Here is a link: [http://blog.linuxmint.com/?p=1604](http://blog.linuxmint.com/?p=1604)

---

### Post by K.Mandla on 2010-12-26
Thanks, I somehow overlooked this in the run-up to Christmas. Cheers!

---

### Post by shuttleworthwannabe on 2010-12-27
can we have some feedback on how well it works? hardware support, and if the "[known issues]("http://www.linuxmint.com/rel_debian.php")" were addressed? e.g. installer hangs during installation if you select format partition...

I am also going to download it now. Thanks for the notice.

S

---

### Post by kaldor on 2010-12-27
If you have NVIDIA cards (ATI/AMD reported some issues too) you must disable the Nouveau driver in GRUB before booting or else you will get a black screen at GDM.

---

### Post by shuttleworthwannabe on 2010-12-27
downloaded and checked integrity and then burned the dvd--booted from dvd and it hangs immediately after start liveDVD...on text screen saying ready...
 Does this on 2 machines--Acer 6292 intel integrated Chip and Dell vostro 3700 nvidia graphics.

I had same problem with the earlier release in Oct as well. Bummer, I was really looking forward to testing this distro.

S

---

### Post by Dobbie03 on 2010-12-27
I have installed it no worries at all.  Everything works fine, only one problem, I have no idea how to install Audacious 2.4 :(

---

### Post by RainPhantom on 2010-12-27
Installed 64bit on ATI and nvidia computers and had no issues also have the 32bit on an intel computer this was installed on 10/09/10 and is fully updated and works with no issues.
If Gnome is your preference then this is the best distro.

---

### Post by PC_load_letter on 2010-12-27
> **RainPhantom said:**
> Installed 64bit on ATI and nvidia computers and had no issues also have the 32bit on an intel computer this was installed on 10/09/10 and is fully updated and works with no issues.
If Gnome is your preference then this is the best distro.


I downloaded the CD iso, used the latest Unetbootin to make a live usb drive, then I installed it on my Dell Vostro w/ Nvidia card. Installation went smoothly, no problems at all, well, here is what I ran into.

- After I installed the proprietary nvidia driver, and updated, the login boot screen had this nasty Ubuntu 10.10 (in large text) instead of the new branding Ubuntu. I followed the instructions [here]("http://theopenhelp.com/2010/09/how-to-fix-ugly-plymouth-logo-on-ubuntu.html") and the problem was fixed. 

- Although I disabled all the sounds, there was a VERY loud beep coming out of the laptop speaker when I logged out or shut down the session. Couldn't figure out what to do here. 

- Unfortunately, several of the software that I use on daily basis is not available in the repos, and/or the developers only have the Ubuntu versions which I'm not sure they could be used on a Debian distro, e.g. sagemath from sagemath.org

Anyway, I think it's awesome distro and I'll keep an eye on it, but the fact remains, Ubuntu has made me spoiled till rot :D

---

### Post by mips on 2010-12-27
[http://mentors.debian.net/cgi-bin/sponsor-pkglist?action=details;package=audacious](http://mentors.debian.net/cgi-bin/sponsor-pkglist?action=details;package=audacious)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=597179](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=597179)
[http://www.linuxnov.com/audacious-2-4-0-released-gtk2-audio-player/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+Linuxnov+(LinuxNov](http://www.linuxnov.com/audacious-2-4-0-released-gtk2-audio-player/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+Linuxnov+(LinuxNov))

---

### Post by Dobbie03 on 2010-12-27
> **mips said:**
> [http://mentors.debian.net/cgi-bin/sponsor-pkglist?action=details;package=audacious](http://mentors.debian.net/cgi-bin/sponsor-pkglist?action=details;package=audacious)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=597179](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=597179)
[http://www.linuxnov.com/audacious-2-4-0-released-gtk2-audio-player/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+Linuxnov+(LinuxNov](http://www.linuxnov.com/audacious-2-4-0-released-gtk2-audio-player/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+Linuxnov+(LinuxNov))

So are those sites telling me its not yet packaged for Debian?

---

### Post by mips on 2010-12-28
> **MattDobson said:**
> So are those sites telling me its not yet packaged for Debian?

Does not look like it but you can get the tar.gz from here [http://mentors.debian.net/debian/pool/main/a/audacious/](http://mentors.debian.net/debian/pool/main/a/audacious/)

---

