---
title: "Error When Trying to Install Windows on PanP7"
date: 2010-05-14
forum: System76 Support
---

### Post by SuperZero on 2010-05-14
Hi all!

I got my PanP7 today and am overjoyed with it. Unfortunately, however, I planned to do a lot of Autodesk work on it, which meant I had to install Windows 7. I started following the instructions here [http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine) but when it comes to reinstalling grub2, I get the error: 

grub-setup: warn: This msdos-style partition label has no post-MBR gap; embedding won't be possible!
grub-setup: warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists.
            However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: If you really want blocklists, use --force.

Any advice on what to do? I googled a bit, and apparently this error has something to do with not having some sort of gap before the first partition? I'm pretty vague. I don't want to ruin my brand new machine, so I'm here asking for help =)

---

### Post by SuperZero on 2010-05-14
I figured this out myself. I opened up GParted via LiveCD and scooted partition 1 over a couple megabytes. That created a small unallocated space before the first partition. I then tried to install grub2 again and it worked perfectly.

---

### Post by HotShotDJ on 2010-05-16
The PanP7 looks like a great machine!  I'm wondering if you might have been better off installing Windows 7 using VirtualBox rather than dual booting.  I'm not familiar with Autodesk, but did see SGI Open Inventor ([http://oss.sgi.com/projects/inventor/](http://oss.sgi.com/projects/inventor/)) -- I don't know if it is relevant to your work or not... but at least something to look at in the F/OSS community.  I'm also pretty sure there are several AutoCAD type packages that runs on Linux.  Perhaps one of them might meet your needs.

---

