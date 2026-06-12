---
title: "do we really need to enter our password for everything?"
date: 2009-04-05
forum: The Cafe
---

### Post by mamamia88 on 2009-04-05
i was just wondering why do we need to enter our passwords for everything?  i can see doing it for something that might break the system like deleting an important file but why do we have to do it for installing from the repository which ubuntu declares as safe?

---

### Post by swoll1980 on 2009-04-05
Having to enter a password to install software makes me feel all warm, and fuzzy inside.

---

### Post by SomeGuyDude on 2009-04-05
Because a user only has permissions to alter the /home folder. So anything you do, anything, that touches another folder will require permission to do so.

---

### Post by majamba on 2009-04-05
because that's the way works if login as root you can do anything

but usually a regular user has only limited aceess he modify only his home and not install but by entering your password you became like superuser you can install if just let be every account be like superuser the system will be very vulnerable, that's why windows is so easily effect and they tried implementing that system into vista.

you do the samething for osx

---

### Post by MikeTheC on 2009-04-05
> **mamamia88 said:**
> i was just wondering why do we need to enter our passwords for everything?  i can see doing it for something that might break the system like deleting an important file but why do we have to do it for installing from the repository which ubuntu declares as safe?

Ok, think about it like this:

You bought and paid for the computer. It's yours. Heck, you may be the only human who touches it.

*However*

Linux, like UNIX, is a multi-user operating system at it's core. So, when you boot up and get to the desktop and are doing things, even though you are the "owner" (legal sense), at that moment you're just a "user" (account sense). This is a deliberate design choice by the Linux community. Heck, even other UNIX variants, such as Mac OS X, do this. Consider...

How is the operating system supposed to know that it's really you who wants to install a given app, or do a given update, regardless of how innocuous said activity might be?

---

### Post by pbpersson on 2009-04-05
> **mamamia88 said:**
> why do we have to do it for installing from the repository which ubuntu declares as safe?

Have you ever been on a Windows machine where you did not have admin rights and could not install anything?  Linux is that way by default.  When you enter the password you are becoming "super user" and you can trash your system.

The repositories are not safe.  No one has been able to test each package in combination with every other package on every type of hardware on the planet.

There are bugs in all software and by installing anything you could change your computer.

Is there anything like a restore point in Ubuntu?

The repositories are relatively safe

---

### Post by aysiu on 2009-04-05
In answer to your question, no, we don't really need to enter our password for everything. We enter our passwords only to modify system files.

That shouldn't happen very often. Why are you modifying system files all the time? I don't get it. My primary applications are Firefox and Thunderbird. What are yours? Synaptic Package Manager, Hardware Drivers and Login Window?

And Ubuntu even has a 15-minute timeout so that you don't have to enter your password again immediately even if you're using multiple applications modifying system files. In Mac OS X there is no sudo timeout, so you need to enter your password *every single time*.

---

### Post by schauerlich on 2009-04-05
> **aysiu said:**
> In Mac OS X there is no sudo timeout, so you need to enter your password *every single time*.

No.

From the sudoers manpage:

```
       timestamp_timeout
                   Number of minutes that can elapse before sudo will ask for
                   a passwd again.  The default is 5.  Set this to 0 to always
                   prompt for a password.  If set to a value less than 0 the
                   user's timestamp will never expire. 
```

---

### Post by JK3mp on 2009-04-05
Well..was gonna post, but others got it covered. So...i guess im covering the pointless post part of this. xD

---

### Post by yabbadabbadont on 2009-04-05
> **aysiu said:**
> And Ubuntu even has a 15-minute timeout so that you don't have to enter your password again immediately even if you're using multiple applications modifying system files. In Mac OS X there is no sudo timeout, so you need to enter your password *every single time*.

I actually prefer not to have the timeout... just in case.  One of the first things that I do upon installing a system that uses sudo is to visudo and add "timestamp_timout=0" to the default options.

(I go through a lot of tin foil too...)

Edit: DOH!  Too slow.

---

### Post by Kareeser on 2009-04-05
This feature is there to protect the user from him or herself :)

t'is a good feature, I'd say.

---

### Post by aysiu on 2009-04-05
> **EDavidBurg said:**
> No.

From the sudoers manpage:

```
       timestamp_timeout
                   Number of minutes that can elapse before sudo will ask for
                   a passwd again.  The default is 5.  Set this to 0 to always
                   prompt for a password.  If set to a value less than 0 the
                   user's timestamp will never expire. 
```

In any case, the Ubuntu timeout is longer. I just tested it, and it's longer than 5 minutes in Ubuntu.

---

### Post by pbpersson on 2009-04-05
> **aysiu said:**
> In any case, the Ubuntu timeout is longer. I just tested it, and it's longer than 5 minutes in Ubuntu.

I always thought it was 15

It is no big deal for me.  I don't use sudo that much.

Also, I do everything with a sudo version of Nautilus when I need to modify system files and I think after I start the session it will not time out

Just gotta be sure to close it when my sudo tasks are done ;)

---

### Post by mamamia88 on 2009-04-05
my problem is not entering password to modify system files but it is entering a password everytime i try to install from syaptic or add/remove.  by being in syanapic or add/remove ubuntu developers have declared these programs safe to install and entering a password to install them seems sily

---

### Post by gnomeuser on 2009-04-05
This is the exact thing PolicyKit was designed to handle. Learn it, Love it, Port applications to using it.

---

### Post by 3rdalbum on 2009-04-05
Synaptic doesn't just install programs, it can remove them too. If you remove the wrong thing, your system breaks.

Also, some programs can open up possible security holes when they are installed. I'm sure that some programs can break your system by being installed in tandum with other things - for instance, if you installed "grub" and "lilo" simultaneously?

Besides, the practical reason why Synaptic requires a password is because only root processes can modify the root filesystem, and in order to elevate to root you need to authenticate, either with a password or with PAM.

---

### Post by Kareeser on 2009-04-05
I'm sure that there's a software based keylogger that's on the repositories accessed by the synaptic package manager.

You wouldn't exactly want someone to install THAT on your computer without your password, would you?

---

### Post by schauerlich on 2009-04-05
> **aysiu said:**
> In any case, the Ubuntu timeout is longer. I just tested it, and it's longer than 5 minutes in Ubuntu.

It's 15. Should one wish to change either timeout, it's just a visudo away.

---

