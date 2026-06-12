---
title: "External Permissions and Questions"
date: 2011-04-11
forum: Security
---

### Post by Naater on 2011-04-11
Hello ubuntu users and others! I thought this would be an appropriate place to forward a few questions I have about the default permissions on ubuntu 10.10. I'll say now when I say"External" I really mean anything outside the "File System" or my main hard drive ( So CD/DVD drive would count as external in this case).

     Now, for an example to  go with my  question:
Whenever a self run program so to speak is placed into my main hard drive as well as any read cd it seems the default permissions for it to run as a program are false. This isn't normally a problem because a quick "right-click" and "properties" or a "chmod" command will fix that. However with the case of the cd it is different because the cd won't allow my or even root to edit it. Most cds are "read only" it seems.

     I have found a way around it by copies the contents of the cd and placing it in my main hard drive where I can edit it but I don't want to have to do that.

    Further more this totally ruins the point of having two hard drives because for some reason I can't edit what's not in my main hard drive while at the same time I can't run what's in my other hard drive.

    Can I change this? How can I?

Thanks for your time!

---

### Post by ajgreeny on 2011-04-11
File permissions on a hard drive formatted to a linux filesystem type can always be changed either by opening nautilus with root permissions ```
gksudo nautilus
```or using the command line and **chmod** command.  See ```
man chmod
``` for more info.  Files on a windows formatted disk (fat32, ntfs) will not be able to accept permissions in the same way

It is also to possible change the way the hard disks are mounted at boot time with an edit of the file /etc/fstab, but this is only possible as root with ```
gksudo gedit /etc/fstab
```and you need to get it right, or you will not mount the disk at all.  How is it mounted at the moment?

You are correct about files on a CD which can not be changed in any way to take account of linux file permissions, which windows does not understand, not does it work with permissions in the same way.

---

### Post by Naater on 2011-04-11
How is it mounted? ...hmm I don't know right now to be honest I just have been letting the system detect and mount it automatically and for other things... right click, and press mount. Has been working fine so far.

---

### Post by SeijiSensei on 2011-04-12
> **Naater said:**
> Whenever a self run program so to speak is placed into my main hard drive as well as any read cd it seems the default permissions for it to run as a program are false.

I presume by "self-run program" you're not talking about programs installed from the Ubuntu repositories?  Something downloaded from the Internet perhaps?  That's generally the wrong approach to installing software in Ubuntu for any package that already exists in the repositories.

In general, the approach you describe whereby random downloaded content is not marked as executable is the correct one from a security perspective.  You might find it annoying, but it's a lot safer than automatically running downloaded executable files.  It makes the user think twice before running something whose origins and purpose are unknown to the operating system.

Want to give us an example of the kind of program you're talking about?

If you're talking about [running Windows programs with WINE]("http://wiki.winehq.org/FAQ#head-27c7adc4eef7b58912198d92de654c498f585d86"), there is a problem with optical drives that arose with some recent security enhancements to WINE.  Read that link for solutions.

---

