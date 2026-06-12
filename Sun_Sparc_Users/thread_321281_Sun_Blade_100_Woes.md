---
title: "Sun Blade 100 Woes"
date: 2006-12-18
forum: Sun Sparc Users
---

### Post by g1zmo on 2006-12-18
OK.  I've read all of the threads about installing onto a Sun Blade 100 - I've even [[COLOR="Blue"]chimed in[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=210630") on a [[COLOR="Blue"]few[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=209831") of  [[COLOR="Blue"]them[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=228447") before - but I'm still unable to get past the [[COLOR="Blue"]Stack Underflow[/COLOR]]("http://www.ubuntuforums.org/showpost.php?p=1433999&postcount=3") error when booting from the installation CD.

My OBP is the latest (4.17.1).  I've tried booting with ide=nodma.  I've tried juggling memory sticks around in all possible combinations while specifying mem=xxx and waving a dead chicken over the motherboard and chanting the [[COLOR="Blue"]Free Software Song[/COLOR]]("http://www.gnu.org/music/free-software-song.html").  I don't know what else to do.  BTW, I get the same exact error with 6.06 as well as 6.10.

So, one more time, am I just SOL?

---

### Post by Delta_Farce on 2006-12-19
Hi g1zmo,

How much RAM have you got? I'm guessing it's 2x512Mb sticks, in which case it might be worth removing one of the sticks and trying to install it that way.

---

### Post by shawnerz on 2006-12-22
G1zmo,
I'm running Ubunto on a Sublade 100 with 256 MB of RAM.  I had some initial problems with the display, but everything else seems to be running fine.
Let me know if you need some system info.

BTW, I'm running Open Boot 4.5 and SILO 1.4.10.
-Shawn

---

### Post by g1zmo on 2007-01-03
> **Delta_Farce said:**
> Hi g1zmo,

How much RAM have you got? I'm guessing it's 2x512Mb sticks, in which case it might be worth removing one of the sticks and trying to install it that way.

It has one 256MB stick and two 128MB sticks.  Like I said before, I've tried all permutations of memory sticks and slots to no avail.

---

### Post by Delta_Farce on 2007-02-12
g1zmo, 

Apologies for the delay in my response and thanks for the extra info. My advice would be to try an install with just the single 256mb stick of RAM for the time being. 

What speed did you burn the ISO at too? I had some problems with discs that were burned at high speed. Try burning at 4x or slower.

I did get this error with some distro cds that I was trying, but I assumed it was an issue with SILO. Are you able to boot anything else (Gentoo, FreeBSD, OpenBSD). If you can try another distro (particularly Gentoo as that uses SILO as well) then we can try to isolate the issue (ie is it Ubuntu's problem, or a hardware problem).

Cheers,

Mark

---

### Post by cac on 2007-02-13
I would try booting Gentoo's LiveCD; I would bet you'd be able to boot.  I have Gentoo running on Sunblade 100/150's with 1GB of RAM (4x256MB), using latest OBP 4.17.1, and Gentoo's 2.6.17 flavored kernel, but Gentoo's latest LiveCD (2006.1) uses SILO 1.4.13.  I remember having fast data access MMU Miss errors as well as your stack underflow error when I used anything less than 1.4.13.  It also had something to do with the kernel version, as I remember having to use their 2.6.16 kernel on the LiveCD to boot.

There's been considerable discussion on the Gentoo forums regarding this, but no definite root causes have been found; at least last time I looked into it.

However I thinking of switching to Ubuntu as it would be easier to manage.  It takes too long to compile packages on these machines to be useful as a workstation in a production environment.  But if Ubuntu's having problems, I might hold off; at least I have usable systems...

Regards,
-chris

---

### Post by g1zmo on 2007-02-16
I've tried using just the 256 stick - that's what's in there now.  I don't remember what speed the disc was burned at - I'm sure it was the max for my burner.  But I've used that same disc to install Ubuntu on a few other systems including an Ultra2, an E4000, and an E250.  I don't see a Sparc version of Gentoo's LiveCD, but I'm downloading the minimal install disc for Sparc and will let you know how it goes.

---

### Post by g1zmo on 2007-02-16
Using a [Gentoo Minimal/Install CD for Sparc64]("http://www.gentoo.org/main/en/where.xml") (burned at 4x), I get the same Stack Underflow error whether I choose 2616 or 2617 (again, with the single 256M mem stick installed).  I guess I've got flaky hardware?  Solaris is rock-solid on this machine.  Hmmmph.  If there's something else I can do to try and troubleshoot, I'm open to any suggestions.

---

### Post by Delta_Farce on 2007-02-17
Hmm...it has been a while since I installed Gentoo on my Sunblade (at least 6 months) but I remember it installing a 2.4 kernel. I know this because I compiled a 2.6 kernel for it before killing the system and switching to Ubuntu.

Have you tried to install with one of the 128 sticks? My machine is running 512, but with a single stick. When I got this error it seemed to be related to my OBP version, but seeing that you're running 4.17 I'm can't see why you're still getting this error.

Cheers,

Mark

---

### Post by Delta_Farce on 2007-02-19
Just a thought g1zmo, but have you tried a netboot? Seems that a few users have successfully installed Ubuntu using this method...

[Have a look here.]("http://www.ubuntuforums.org/showpost.php?p=1488452")

---

### Post by g1zmo on 2007-02-20
I don't really have anything I can set up as a boot server, unfortunately.  I'll see if an older (2.4 kernel) Gentoo might work.  And I've tried all of this with 128M, 256M, 384M, and 512M in various memory slots.

---

