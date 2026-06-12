---
title: "Boot your Ubuntu in 7sec??? TexasFlood Boot System"
date: 2008-10-11
forum: The Cafe
---

### Post by RRFarFar on 2008-10-11
This is the first place to ask, isnt. it?

So I am asking - has anyone heard of TexasFlood Boot System which claims to start KDE-based Resulinux in 7 seconds? Can in it be installed and used in Hardy to make boot process faster??

Here is an ftp with the deb package -  [ftp://neacm.fe.up.pt/pub/resulinux/debs/](ftp://neacm.fe.up.pt/pub/resulinux/debs/)
Also see what distrowatch tells us about Resulinux - [http://distrowatch.com/table.php?distribution=resulinux](http://distrowatch.com/table.php?distribution=resulinux)
I am not an expert in a boot process but as to the year 2007 (post in various forums are dated 2007) TexasFllod was unable to work with pardon for my illiteracy 'upstream' system like ubuntu. Upstream probably means that Ubuntu uses some kind of upstream technology to boot itself. Nevertheless you may video on youtube - [http://www.resulinux.forumdebian.com.br/texasfloodweb/](http://www.resulinux.forumdebian.com.br/texasfloodweb/) , which shows how this system works. 

Honestly saying I am willing to experiment, but I need an advice.How???
As it is shown TexasFlood works on Debian, so why can't it work in Ubuntu??
There is also an interesting discussion here - [http://www.murga-linux.com/puppy/viewtopic.php?t=22563](http://www.murga-linux.com/puppy/viewtopic.php?t=22563) 
IDEAS???????????

---

### Post by RRFarFar on 2008-10-12
No a single person? Nobody heard of it??

---

### Post by cilkay on 2008-10-12
That figure of seven seconds is not true. The video shows the original system booting in 51.7 seconds and the modified system booting in 39 seconds for a difference of 12.7 seconds.

The term "upstream" in Ubuntu refers to Debian, not to the boot system. Ubuntu uses [upstart]("http://upstart.ubuntu.com/") for its boot system. Switching to a different one is a significant amount of work that requires a deep understanding of the boot process.

---

### Post by RRFarFar on 2008-10-12
> **cilkay said:**
> That figure of seven seconds is not true. The video shows the original system booting in 51.7 seconds and the modified system booting in 39 seconds for a difference of 12.7 seconds.

The term "upstream" in Ubuntu refers to Debian, not to the boot system. Ubuntu uses [upstart]("http://upstart.ubuntu.com/") for its boot system. Switching to a different one is a significant amount of work that requires a deep understanding of the boot process.

Ok, ok - let it be upstart, not upstream. But anyway 12 seconds sounds better that 52 or 39, while mine is around 1.5 min. 
I thought people who know a lot about debian/ubuntu could give an advise, or maybe somebody is already testing this.
My opinion, is that it is far better to experiment with new boot system, then to install Interpid beta for example or even worse Alpha))))))))

---

### Post by cilkay on 2008-10-13
> **RRFarFar said:**
> But anyway 12 seconds sounds better that 52 or 39, while mine is around 1.5 min.

Where do you get 12 second boot times? TexasFlood allegedly boots in 39 seconds, not 12 seconds.

As for why your system is taking 90 seconds to boot, it could be any number of things causing that. You don't mention anything about your hardware or what daemons you have have enabled. If you have something that is dependent on DNS and you have a slow DNS server, that could cause long boot times. It seems to me that the more profitable option for you is to figure out why your particular machine takes so long to boot rather than do a rip-and-replace of the init system.

---

### Post by cilkay on 2008-10-14
I just stumbled upon [TIP: Improve bootup speed by reprofiling bootup]("http://ubuntuforums.org/showthread.php?t=254263"). Might be useful.

---

### Post by Sef on 2008-10-14
moved to community cafe.

---

### Post by derekr44 on 2008-10-14
90 second bootup?

Shoot, my Arch box is up in about 20-30.

---

