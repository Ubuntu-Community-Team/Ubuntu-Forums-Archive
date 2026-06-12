---
title: "What would be the result of a &quot;sudo rm -r /&quot;?"
date: 2013-05-27
forum: Ubuntu, Linux and OS Chat
---

### Post by caltosax on 2013-05-27
Hey, so I have a question just out of curiosity.  I have a dual-booted laptop, running Windows 7 and Ubuntu 12.04.  What would happen if I entered the command "sudo rm -r /"?  Obviously my whole Linux system would be gone.  But, would this affect my Windows partition at all?  Would the boot loader still be there?  If not, would it be easy to reinstall the windows boot loader?  Overall, is this overall just a horrible idea, or is it an option for wiping my Linux partition?

---

### Post by cariboo on 2013-05-28
I wouldn't suggest trying it. Probably the easiest and quickest way to wipe a Linux partition is to use [gparted]("http://gparted.sourceforge.net/") to do what you need.

---

### Post by buzzingrobot on 2013-05-28
"rm -r /" will remove all the files and directories in the "/" directory. It will not remove the partition.

Using gparted or any other partition editor to remove the partition will do just that, of course.

---

### Post by jpeddicord on 2013-05-28
Running it as-is will give you a notice saying you need "--no-preserve-root" (**but don't try that anyway, typos are dangerous**).

If your Windows partition (or any other) is mounted, it will be erased as well, since `rm` operates down the file tree and doesn't care about filesystem boundaries. I know someone who took a backup of their system and ran "rm -rf /" on it while the backup drive was still mounted. :P

tl;dr: don't do it

---

### Post by CosmicFlux on 2013-05-30
I love the fact that Linux allows you the freedom to wipe your entire system with such a simple command. Linux assumes you're smart and you know what you are doing. As said above you could potentially wipe out all data on all partitions if you have everything mounted into the directory tree. If that were the case, then the result would be a shed load of tears... :)


Cosmic

---

### Post by montag dp on 2013-05-30
> **jpeddicord said:**
> Running it as-is will give you a notice saying you need "--no-preserve-root" (**but don't try that anyway, typos are dangerous**).

If your Windows partition (or any other) is mounted, it will be erased as well, since `rm` operates down the file tree and doesn't care about filesystem boundaries. I know someone who took a backup of their system and ran "rm -rf /" on it while the backup drive was still mounted. :P

tl;dr: don't do itOh snap!  Ha ha, that's terrible.

---

### Post by Irihapeti on 2013-05-30
A few years back, there was a rash of booby-trapped deb packages with "cool themes" for you to install. Except they had no theme files in them &#8211; and had a post-install script containing "rm -rf /"...

---

