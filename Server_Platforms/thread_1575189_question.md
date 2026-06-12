---
title: "question"
date: 2010-09-15
forum: Server Platforms
---

### Post by Maddjokerz on 2010-09-15
I have  a ubuntu desktop 80gb 878mb, but I want to install another harddrive, is there a way to run the 80gb as a desktop and run the other harddrive as server?

---

### Post by arrrghhh on 2010-09-15
Well they wouldn't be able to run at the same time... but you could dual-boot and have one option for the server edition and one option for the desktop edition...

But that seems kinda silly, especially since you can put all of the regular services on top of a desktop install... Any particular reason you're doing it this way?

---

### Post by Troublegum on 2010-09-15
Or you use virtualization if you have enough resources.

---

### Post by sikander3786 on 2010-09-15
You can surely install server on the second hard drive but only 1 OS can be up and running at the same PC at one time as arrrghhh mentioned above. To run a Virtual Machine with the amount of RAM (878 MB) seems quite difficult to me.

What kind of server do you want to configure? You can say that Ubuntu Desktop is originally Ubuntu Server with an addition i.e, GUI (GNOME, KDE for instance).

---

### Post by prshah on 2010-09-15
> **Maddjokerz said:**
> I have  a ubuntu desktop 80gb 878mb, but I want to install another harddrive, is there a way to run the 80gb as a desktop and run the other harddrive as server?

To run it simultaneously, you have to use virtualization as already mentioned.

A server install (no gui) can be managed with as little as 128MB (256MB recommended). 

Considering your limited memory, you might want to look into KVM/Qemu rather than VirtualBox (though it won't hurt to try VBox initally).

---

### Post by Maddjokerz on 2010-09-16
I was just wondering I love my desktop and want to add another harddrive and more memory, I am pretty new to ubuntu and wanted to learn how to run a server. I was hoping to kill two birds with one stone but looks like I may have to build my own server then.

---

### Post by snowpine on 2010-09-16
> **Maddjokerz said:**
> I was just wondering I love my desktop and want to add another harddrive and more memory, I am pretty new to ubuntu and wanted to learn how to run a server. I was hoping to kill two birds with one stone but looks like I may have to build my own server then.

You can run a server from "regular" Ubuntu just fine.

A good start is to read through this "sticky" thread: [http://ubuntuforums.org/showthread.php?t=1046738](http://ubuntuforums.org/showthread.php?t=1046738)

---

### Post by arrrghhh on 2010-09-16
> **snowpine said:**
> You can run a server from "regular" Ubuntu just fine.

A good start is to read through this "sticky" thread: [http://ubuntuforums.org/showthread.php?t=1046738](http://ubuntuforums.org/showthread.php?t=1046738)

+1 to the OP.  You can run all the server-based applications from a desktop install, NO problem.  Then that extra hdd is pure extra space!

---

### Post by Maddjokerz on 2010-09-17
I think I wll try and run the server applications from my desktop, Thank you for all the help....

---

