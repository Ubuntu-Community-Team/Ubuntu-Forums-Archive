---
title: "Secure laptop from its own user?"
date: 2008-04-11
forum: Security Discussions
---

### Post by garton on 2008-04-11
I'm going to install a not-yet released application on an Ubuntu laptop computer and send it to a potential customer for evaluation. I don't want the customer to be able to do *anything* but run the app the way I intended. The application is written in python and C. Is this possible? Any ideas on how to do this?

---

### Post by netlogic on 2008-04-11
> **garton said:**
> I'm going to install a not-yet released application on an Ubuntu laptop computer and send it to a potential customer for evaluation. I don't want the customer to be able to do *anything* but run the app the way I intended. The application is written in python and C. Is this possible? Any ideas on how to do this?

Research ratpoison window manager, only run windows session, and set to automatically launch your app.

---

### Post by scorp123 on 2008-04-19
> **garton said:**
> I'm going to install a not-yet released application on an Ubuntu laptop computer and send it to a potential customer for evaluation. Hmmm.... I'd rather use something such as Sun's "Secure Global Desktop" and then let the (potential) customer try out the application in that environment. If you physically ship the program installed on a laptop all they have to do is insert a boot CD and they can manipulate everything any way they wish, e.g. even steal your program.

With a remote environment where I only give them access to what I want there is no chance for them to ever do something I don't want them to do. Just an idea.

[http://www.sun.com/software/products/sgd](http://www.sun.com/software/products/sgd)

---

### Post by cornelinux on 2008-04-20
Hi,

if you managed to handle the thing with the license of your not released application you could also build a live-CD. This is rather easy.
Take a look at the "debian live helper".

Kind regards
Cornelius

---

### Post by picopir8 on 2008-04-21
I have been looking into something similar and AFAIK, there is no way to totally lock down an application.  Should someone gain root access they could easily bypass just about any security restrictions you impose.  Gaining root access is as simple as editing the boot parameters so the computer boots into single user (aka recovery) mode, booting with a livecd, or removing the drive and connecting it to a computer where they have root access.

Making your own liveCD would be slightly more secure because all files are compressed using squashfs and so they would not be visible when looking at the CD contents.  The only way to gain access is to boot the CD (preventing someone for using another liveCD to gain root access), or to mount and extract the files manually on a machine where they already have root access.

The later case is impossible to prevent so you need to encrypt your sensitive files. However you would need to include the decryption key in your boot scripts so your program can be executed.  A decryption key placed in a boot script would be easily found. Another option is to put it in a keyring, but every keyring I know of allows someone to view all keys in the keyring so that is pointless.  What would be nice is a write only keyring but I dont know of any.   

The only other option I can think of is a launcher program that would verify that the liveCD is in fact running and not simply extracted and running under a chroot session.  Once the program has verified that the liveCD is in fact running natively (ie kernel check, drive check, etc. and perhaps attempting to issue an "exit" command to exit a potential chroot session) it could decrypt the main program.  However, this too is flawed because someone could open the launcher program in a hex editor and extract the decryption key.

Also, dont forget to modify the kernel to prevent the "single" boot option from being used (or at the very least make sure your launcher checks to ensure that the user is _not_ root.

---

### Post by netlogic on 2008-04-23
Why are you making things so complicated?
Just change your fstab for application partition to be read-only. 
Just take away all console access, set bios, and grub passwords. Also, blacklist your usb mass storage module.

Ratpoision is a simple window manager. It is very easy to set it up to run only one application. Many people use it for MythTV.

---

### Post by scorp123 on 2008-04-23
> **netlogic said:**
>  Just change your fstab for application partition to be read-only. Just take away all console access, set bios, and grub passwords.  That would still not prevent anything. Whoever has the laptop could simply boot another OS (e.g. a live CD) and then do whatever manipulation they want to do, even steal the program. They send the laptop back with a note saying "Thank you but we're not interested ... " and one month later they release the program themselves, claiming that their programmers had "something similar" in mind .... Stuff like that happens all the time everywhere. And OP probably lacks the financial resources to take anyone to court I guess ...?

I'd still suggest to let the customer try out the application in a remote environment, be that a VNC session, a NX session, RDP session, Tarantella, or whatever. As soon as you ship the application on a laptop to the customer you have to depend on their sense of "fair play". Too bad if they don't have any and you only find out when it is too late ...

---

### Post by netlogic on 2008-04-23
> **scorp123 said:**
> That would still not prevent anything. Whoever has the laptop could simply boot another OS (e.g. a live CD) and then do whatever manipulation they want to do, even steal the program. They send the laptop back with a note saying "Thank you but we're not interested ... " and one month later they release the program themselves, claiming that their programmers had "something similar" in mind .... Stuff like that happens all the time everywhere. And OP probably lacks the financial resources to take anyone to court I guess ...?

I'd still suggest to let the customer try out the application in a remote environment, be that a VNC session, a NX session, RDP session, Tarantella, or whatever. As soon as you ship the application on a laptop to the customer you have to depend on their sense of "fair play". Too bad if they don't have any and you only find out when it is too late ...

Turning the app into a live cd environment will work? Have you heard a program called mount and cp? Also, you can debug the session of swap and ram, so it is pointless. NX session is probably only way for the super paranoid. If he wrote with GPL tools, it wouldn't matter. If he hasn't, just patent the tool and sue them if they steal something.

---

### Post by yeleek on 2008-05-08
> **garton said:**
> I'm going to install a not-yet released application on an Ubuntu laptop computer and send it to a potential customer for evaluation. I don't want the customer to be able to do *anything* but run the app the way I intended. The application is written in python and C. Is this possible? Any ideas on how to do this?

If this were a windows app i'd say stick it on a citrix server, you can get developer licenses or even an eval for 90 days whilst your customer tests it.  I work with Citrix and whilst i know there is a unix version, don't know if it would run on linux.

Alternatively - how about hosting it in a virtual machine?  Lock down the vm bios and they shouldn't be able to boot anything other than what you want - i.e. no live cd?  Then lock down ubuntu and send them the vm on a dvd.  You should be good...  *i think - come from windows  background*

---

