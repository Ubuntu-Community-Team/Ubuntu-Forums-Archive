---
title: "Unbelievable issues on installing Ubuntu server"
date: 2020-02-06
forum: Server Platforms
---

### Post by weevie56 on 2020-02-06
I am an experienced IT Professional with 20+ years Windows experience
However - LINUX is new to me
So I am trying to install Ubuntu server 18.04 on a Dell 390 PC to run Nagios on
To start with - I am using all of the default settings - but still get "An error occurred during installation"
I have tried several different sources (USB and DVD) - but still get exactly the same error every time
This is such a simple issue - but I cannot find a solution
Looking at the installation log - there is error after error !
Then there's a login problem - after carefully typing in admin and user passwords - neither are accepted by the (half installed) system - "authentication failure"

---

### Post by coffeecat on 2020-02-06
> **weevie56 said:**
> 
So I am trying to install Ubuntu server 12.04 on a Dell 390 PC to run Nagios on

Ubuntu 12.04 has been out of support for nearly three years now. You need to install a currently supported version. More information here:

[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)

---

### Post by CatKiller on 2020-02-06
> **weevie56 said:**
> I am an experienced IT Professional with 20+ years Windows experience 

That's likely to be an impediment rather than an asset; that's 20 years of conditioning in Windows. Unlearning all those habits is *much* harder than simply learning how to use Linux. 

> So I am trying to install Ubuntu server 12.04 

I really hope that's a typo: 12.04 has been unsupported for a very long time. 18.04 LTS or 19.10 are the currently supported releases. 

>  Looking at the installation log - there is error after error !

Telling us what those errors say would be a good start for allowing us to help you. In the meantime, there's a "check for defects" option that you can use to make sure you haven't had a bad download.

---

### Post by weevie56 on 2020-02-06
I meant 18.04 - it shows how much this problem has affected my state of mind !
How do I use the "check for defects " option ?
The download, though is sound - I have created a bootable DVD at home and found exactly the same errors as a bootable USB created at work !
Despite all of the errors - I do have a running txt based system - but it won't let me log in as SU - Telling me that my password is incorrect - which is not correct - I very carefully made sure that I typed it in correctly

---

### Post by slickymaster on 2020-02-06
Thread moved to **Server Platforms** for a better fit

---

### Post by CatKiller on 2020-02-06
> **weevie56 said:**
> How do I use the "check for defects " option ? 

I can't remember exactly what it's called on the server installer, but it's one of the first options; it checks the hash of every file against the hashes stored in a file. 

> Despite all of the errors - I do have a running txt based system 

...That's what an Ubuntu server install is. There's no GUI. If you want a GUI you either need to use the desktop installer or install your choice of desktop environment. 

>  - but it won't let me log in as SU - Telling me that my password is incorrect - which is not correct - I very carefully made sure that I typed it in correctly

Unless you actually called your user "su" you can't "log in" as su, which stands for switch user. You log in as yourself and, occasionally, run commands as root, using your own password, using either sudo (switch user, do) or su (switch user), if you need to run several commands in a row as root. You very very rarely need to run things as root.

---

### Post by TheFu on 2020-02-06
20 yrs with Windows is likely part of the issue.  Most of us went through the re-training to unlearn Windows knowledge that just doesn't apply on Unix systems.  About 20% is similar, the other 80% will lead you down the wrong path.  

Ubuntu doesn't have a root account you log into.  Ubuntu uses sudo to temporarily elevate privileges for users who are members of the sudo group.  Other Linux distros DO USE root logins, but also support sudo.  As a general security stance, my company doesn't allow remote root access. Root can only login on a physical console, never over a network.

As for validating a good download, there was a checksum file at the same place you got the ISO.  Probably multiple checksums.  Those should always be manually validated before using any ISO.  There are Linux tools, sha1sum ; sha256sum ; md5sum used to create the different checksums.  Then manually compare the output with the contents of those *sum files.

Linux servers don't have any GUI.  Sorry. Running a GUI from 12000 miles away sucks.  I live on the US east coast, but maintain a few non-profit Linux servers in east and central Asia.

When doing a first install on new hardware, I always google for "ubuntu 18.04 install {vendor, model}" to see if anyone else had issues and posted specific solutions. **Dell 390 ubuntu 18.04 install**

After you get a feel for the typical HW issues, that won't be needed.  Plus, the server install won't have many GPU drivers or funky network drivers.  If you have an Intel PRO/1000 or newer I21x NICs, those will be included and just work.  Forget about wifi for now.

Users, groups, are managed differently.  Often, I just modify text files to make changes, no tools needed/wanted.

Network sharing is totally different.  There are better/faster methods than samba for example.  Once setup, they behave just like local storage and 99.9% of programs cannot tell the difference.  Also, using NTFS storage will result in poor performance.  Stick with native Linux file systems which have kernel drivers.  If you are familiar with Veritas LVM and FS, do yourself a favor and choose to use LVM at install time.  Storage design and architecture for Linux systems is completely different from Microsoft's stuff.  Otherwise, stay with ext4, especially for backup storage.

Windows skills aren't all bad.  Knowing how to troubleshoot problems and find solutions will be useful.  When first starting out, it is best to ask questions with the final, final, goal shown, since the Windows way is seldom the Unix way.  We see people asking for help with individual steps here all the time, when most of those steps just aren't needed for the real solution.  The question above is NOT that sort. Good job.

Dell systems are usually the most compatible with Linux.  Places where they have issues are when the BIOS settings are wrong or there are 2 GPU devices and one is nvidia.

Anyways, doubt much of my post is all that useful. Perhaps it will help to avoid future issues?

---

### Post by LHammonds on 2020-02-06
> **weevie56 said:**
> I am an experienced IT Professional with 20+ years Windows experience
Take it from another 20+ year Windows guy, that means little other than knowing the high-level view of how things work.  Linux and how it is designed works quite different...so as Yoda once said, "you must unlearn what you have learned"

> **weevie56 said:**
> However - LINUX is new to me
I was right there where you are back around the time Ubuntu 10.04 released.

> **weevie56 said:**
> So I am trying to install Ubuntu server 18.04 on a Dell 390 PC to run Nagios on
You're in luck (mostly) because I have done the very same (mostly).  Most everything I have done has been in virtual environments which means I don't have much experience in bare-metal installs/troubleshooting but once you get the initial hardware out of the way, its pretty-much the same.

Here is my latest tutorial on [installing Nagios on Ubuntu Server 18.04]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=267") but it wasn't quite finished since I have shifted over to other duties...but it should get you most of the way there except for the Windows client.

> **weevie56 said:**
> To start with - I am using all of the default settings - but still get "An error occurred during installation"
I have tried several different sources (USB and DVD) - but still get exactly the same error every time
...
Looking at the installation log - there is error after error !
Not much said here to actually provide any kind of help.  Need those exact error messages placed here (preferably between CODE tags)

LHammonds

---

