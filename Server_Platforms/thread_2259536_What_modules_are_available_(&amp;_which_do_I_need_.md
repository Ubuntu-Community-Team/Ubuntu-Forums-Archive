---
title: "What modules are available (&amp; which do I need for RAID): /etc/initramfs-tools/modules"
date: 2015-01-05
forum: Server Platforms
---

### Post by DiagonalArg on 2015-01-05
Hi all.  I've had to do some disk preparation before an install, and discovered that to get the system as I wanted it configured to boot, I had to add some modules to /etc/initramfs-tools/modules ([COLOR=#000000]dm-crypt, aes, xts, sha512) [/COLOR]and update the initramfs.[COLOR=#000000]  

Now I want to install another system with RAID and will need to add the modules for that.  Where do I look up the list of available modules?  How do I figure out which ones I need?  Poking around it seems that dm-raid and raid1 might be it; but I see a lot more possibilities, so I'm not sure.

Any thoughts?

Thanks
/D[/COLOR]

---

### Post by gordintoronto on 2015-01-05
Providing more information would make it a lot easier for people to help you. What computer? What RAID? What OS?

---

### Post by TheFu on 2015-01-06
HW-RAID, SW-RAID or Fake-RAID would be helpful to know.  IMHO, there really isn't any reason to use Fake-RAID - why limit the OS to specific hardware when the performance won't be any better than SW-RAID?  SW-RAID is much, much, much more flexible, if it meets the performance needs for the system.

---

### Post by DiagonalArg on 2015-01-11
@[COLOR=#000000]gordonintoranto - It's software raid under Ubuntu 14.04.  

Still, the question is also general.  Where do I find a list of initramfs modules & how do I identify which ones are to be used for any particular application?  In this case, the application is RAID.

Thanks,
/DA.[/COLOR]

---

### Post by MAFoElffen on 2015-01-11
I guess I can translate...

Sounding like you have an Ubuntu Server Edition installation disk, are installing and you don't see any options in the partitioner there for RAID yet... Right? In the Server Install Disk > Partinioner Section... That will do that all for you, if you follow the following instructions.

You have to select the "manual" option from the main menu of that too and create some partitions first, before an option to create an mdadm RAID will appear in the menu... Depending on what RAID type you want to use, will leverage how many partitions you need to create. Another stumbling block for some is that when you are selecting members, initially select only those you want to use as active members... If you want to use a spare, if there is another free partition, it will ask you for that in another panel...

If you have questions, feel free to ask... Or if you already have a system and you want to add RAID,I'll explain how to do that from the CLI...

"mdadm" is complicated to explain in just one sentence. It is "Linux Software Raid,"(§) It is very powerful and flexible. It is the current standard for Linux systems. It is what Ubuntu uses as it's Linux Software RAID becauase of that. Installing and going through mdadm will install and manage the pieces allot easier than trying to decide what individual pieces goes where, how to tie them together and be able manage that under the microscope, from those individual pieces. Grub2 and Linux kernel support working with mdadm. 

Are you trying to create your own flavor of that from scratch? If so, I could always use some help on my opensource project.

If you are not trying to re-invent the wheel, then maybe you should learn more about mdadm. You don't need to learn about how it works under the hood to use it. Trust that it works and learn to work with it. My opensource project is to try to develop something with hooks to mdadm, that is intended to make that process easier to implement and manage.
___
MAFoElffen
mdadm-gui Project Lead

(footnote- § dmraid went away after loosing support a few years ago)

---

### Post by DiagonalArg on 2015-01-11
@MAFoElffen - I really appreciate your reply.  Thing is, perhaps everyone's reading far too much into my question.  I understand cryptsetup and mdadm pretty well.  What I'm doing is preparing my disk before-hand using the live CD, then installing Ubuntu into that disk, and finally making the mods that are needed to get a bootable system.  With an encrypted disk, I have to do things like change /etc/crypttab and /etc/fstab, along with adding the modules described above [COLOR=#000000]([/COLOR][COLOR=#000000][COLOR=#000000]dm-crypt, aes, xts, sha512) to /etc/initramfs-tools/modules.  Then I chroot into the modified system, update-initramfs, and reboot.  All is good.  I want to do the same with LUKS + RAID.  So:

(1) What modules do I need in /etc/initramfs-tools/modules for RAID
(2) More generally, where do I find a list of initramfs modules & how do I figure out which ones are necessary for a particular application.

Thanks again,
/DA.

*Edit - PS.  & yes, I really need to do it this way.  :)[/COLOR][/COLOR]

---

### Post by MAFoElffen on 2015-01-12
So you are looking for something like this?
[http://blog.joelweinberger.us/2013/12/setting-up-full-disk-encrypted-lvm-on.html](http://blog.joelweinberger.us/2013/12/setting-up-full-disk-encrypted-lvm-on.html)

and the files for mdadm get installed like this:
```

/etc/cron.d/mdadm
/etc/cron.daily/mdadm
/etc/default/grub.d/dmraid2mdadm.cfg
/etc/init.d/mdadm
/etc/init.d/mdadm-waitidle
/etc/logcheck/ignore.d.server/mdadm
/etc/logcheck/violations.d/mdadm
/lib/udev/rules.d/64-md-raid.rules
/sbin/mdadm
/sbin/mdmon
/usr/share/apport/package-hooks/source_mdadm.py
/usr/share/bug/mdadm/script
/usr/share/doc-base/mdadm-faq
/usr/share/doc-base/mdadm-jd-rebuild-raid
/usr/share/doc-base/mdadm-md-txt
/usr/share/doc-base/mdadm-raid5-vs-10
/usr/share/doc-base/mdadm-readme-recipes
/usr/share/doc-base/mdadm-superblock-formats
/usr/share/doc/mdadm/FAQ.gz
/usr/share/doc/mdadm/NEWS.Debian.gz
/usr/share/doc/mdadm/RAID5_versus_RAID10.txt.gz
/usr/share/doc/mdadm/README.Debian.gz
/usr/share/doc/mdadm/README.checkarray
/usr/share/doc/mdadm/README.recipes.gz
/usr/share/doc/mdadm/TODO.Debian
/usr/share/doc/mdadm/TODO.gz
/usr/share/doc/mdadm/changelog.Debian.gz
/usr/share/doc/mdadm/copyright
/usr/share/doc/mdadm/examples/mdadd.sh
/usr/share/doc/mdadm/examples/mdadm.conf-example
/usr/share/doc/mdadm/examples/syslog-events
/usr/share/doc/mdadm/md.txt.gz
/usr/share/doc/mdadm/md_superblock_formats.txt.gz
/usr/share/doc/mdadm/rebuilding-raid.html
/usr/share/initramfs-tools/hooks/mdadm
/usr/share/initramfs-tools/scripts/init-premount/mdadm
/usr/share/initramfs-tools/scripts/mdadm-functions
/usr/share/lintian/overrides/mdadm
/usr/share/man/man4/md.4.gz
/usr/share/man/man5/mdadm.conf.5.gz
/usr/share/man/man8/mdadm.8.gz
/usr/share/man/man8/mdmon.8.gz
/usr/share/mdadm/checkarray
/usr/share/mdadm/mkconf

```

---

### Post by DiagonalArg on 2015-01-12
[COLOR=#000000]@MAFoElffen - Yes, you're on the right track, that's basically what I'm doing.  Thing is, I do my disk-prep a little bit differently, and so the install doesn't figure out that it needs the crypt & RAID modules.  Therefore I have to tell it by hand, by including them in /etc/initramfs-tools/modules.

I already know which initramfs modules are relevant to cryptsetup, so I need to know which modules are relevant to mdadm.  And more generally, I'd like to know about all of them (all of the initramfs modules).

Thanks
/DA[/COLOR]

---

### Post by DiagonalArg on 2015-01-12
Ok, here is a description of the issue of getting modules into the initramfs: [https://wiki.ubuntu.com/Initramfs](https://wiki.ubuntu.com/Initramfs)  (Just search for the word "modules" in that page.)

I think I've worked out that all kernel modues can be used in the initramfs, and lists can be obtained as described here: [https://help.ubuntu.com/community/Loadable_Modules](https://help.ubuntu.com/community/Loadable_Modules)

Now, how do I identify the modules that are relevant for a particular application?  Someone helped me out to get that list for cryptsetup, but I don't know where it came from, and I don't know which are necessary for mdadm.

/DA

---

