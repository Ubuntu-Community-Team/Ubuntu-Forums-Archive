---
title: "Wubi 8.04 testing"
date: 2008-02-27
forum: Ubuntu Dev Link Forum
---

### Post by ago on 2008-02-27
Wubi 8.04 is now released on the Ubuntu CD and in stand-alone mode. If you do not know what wubi is, please have a look at [http://wubi-installer.org](http://wubi-installer.org). This is the first "official" Wubi release, so it requires some hammering on your side. You need windows (wubi is a windows-side installer) and 5GB free.

You can find the development version of wubi here: [http://wubi-installer.org/devel/minefield/](http://wubi-installer.org/devel/minefield/)

Try it out, and pls report any bug on the wubi forum ([http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)) or in launchpad [https://bugs.launchpad.net/wubi/](https://bugs.launchpad.net/wubi/) 

If you have troubles try first chkdsk /r from windows within the drive where you installed wubi, if you have boot issues, press esc at the countdown and select one of the other options. For anything else, boot in verbose mode, and ask in the Wubi forum.

Windows logs are in your temp folder (type %temp% in windows explorer)
Boot logs are /casper.log + /tmp/*log
Relevant ubiquity logs are/var/log/syslog + /var/log/installer/*


Thanks in advance,

Ago

---

### Post by Huss on 2008-03-25
Great idea. will test it when I get the chance. Do I need to backup the files on a windows system?

---

### Post by TomMK on 2008-03-26
Installed and running flawlessly on an HP NC6400 laptop withwindows xp. Very impressed.

---

### Post by plun on 2008-03-27
> **ago said:**
> 
If you have troubles try first chkdsk /r from windows within the drive where you installed wubi, if you have boot issues, press esc at the countdown and select one of the other options. For anything else, boot in verbose mode, and ask in the Wubi forum.



Hi Ago

Thanks for your work with Wubu, great !

About Error checking and also Defrag, mostly all Windows PCs looks like a big mess and a few maybe knows about these tools...:)

A Vista disk is often totally messed up with small index files everywhere, just to check it with for example O&O defrag.

[http://support.microsoft.com/?scid=kb%3Ben-us%3B315265&x=11&y=16](http://support.microsoft.com/?scid=kb%3Ben-us%3B315265&x=11&y=16)

[http://support.microsoft.com/?scid=kb%3Ben-us%3B314848&x=17&y=12](http://support.microsoft.com/?scid=kb%3Ben-us%3B314848&x=17&y=12)

These tools can easily be linked to Wubis GUI.

This takes some time but in the end Wubi will be more sucessful.

Thanks !

---

### Post by ago on 2008-03-27
plun,

We considered to use jkdefrag and chkdsk but at the moment we are in feature freeze and UI freeze.
Also running both on fairly large disks (which are quite common today), takes a loooong time and neither provides an easy way to be incorporated into a plugin.

---

### Post by plun on 2008-03-27
> **ago said:**
> plun,

We considered to use jkdefrag and chkdsk but at the moment we are in feature freeze and UI freeze.
Also running both on fairly large disks (which are quite common today), takes a loooong time and neither provides an easy way to be incorporated into a plugin.

OK...

Well, I will recommend (if someone asks) to just run error check and defrag, also using Windows GUI for both (not using cmd).

I read OpenSuse manual for Dual-Boot installs and they also
recommends this.

Its the same "****" with NTFS auto mounts with a partition with errors.
Windows often just run... also external USB disks.

Mostly all Windows users also are overfilled with temporarily junk files and I always recommends CCleaner to get rid of this mess.
After that error check and defrag.

And it takes time but with Windows and Redmonds ideas its maybe is worth it...:)

Wubi looks great anyway...Thanks !

---

