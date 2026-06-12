---
title: "Lost virtual machines"
date: 2013-04-25
forum: Virtualisation
---

### Post by gnugen on 2013-04-25
Hello
In Virtualbox I have recently got this error message. All hard drives and external media are mounted and I still get this message. Why?

 > One or more virtual hard disks, CD/DVD or floppy media are not currently accessible. As a result, you will not be able to operate virtual machines that use these media until they become accessible later.

 Press Check to open the Virtual Media Manager window and see what media are inaccessible, or press Ignore to ignore this message.


---

### Post by TheFu on 2013-04-25
> **gnugen said:**
> Hello
In Virtualbox I have recently got this error message. All hard drives and external media are mounted and I still get this message. Why?

I've only seen this message when
a) the file system isn't mounted
b) the file system is mounted read-only
c) the virtualbox config file is corrupt
d) the files ownership/permissions have been changed

So, those are the places that I'd start my research.
Being "mounted" is NOT the same as "viewing in Nautilus."

Anyway, check those things and check the log files in /var/log/ for extra information.

---

### Post by gwm on 2013-04-28
Hi,
I too am having problems.
I look at TheFu's list of points and he says **Being "mounted" is NOT the same as "viewing in Nautilus."**
That throws me completely and now I don't understand points **a** and **b** like I thought I did.
It is very unlikely that an upgrade process is going to change the ownership / permissions, which leaves the possibility of some "corruption" (incompatibility) of the configuration. To handle that, I moved the .vdi file to another folder and deleted the Vitrualbox VMs directory that used to contain it.

Next I went looking for a release on the Oracle website. They don't have a 13.04 version. That means we are trying to make the older one work with an unsupported kernel. To recompile the kernel, we need the correct header files and they don't exist. Unless someone actually knows better and can tell us what to do, I guess we now have to be patient and wait for Oracle to catch up with this release.

Next I went to the Ubuntu Software Center and installed their version of VirtualBox. As I understand it, this is the OSE version (which I guess probably means something like Open Source Edition) - I read somewhere in the forums that Oracle don't support it.

I started this version and created a new virtual machine without a hard drive. This recreated the directory that I had earlier deleted and I moved the .vdi file into it. Finally, under the settings for my new virtual machine, I added an exisiting hard drive and pointed it to the .vdi file.

Now it all is well in the jungle!!

:guitar:

---

### Post by ibjsb4 on 2013-04-28
Ubuntu 13.04 ("Raring Ringtail") [ i386]("http://download.virtualbox.org/virtualbox/4.2.12/virtualbox-4.2_4.2.12-84980%7EUbuntu%7Eraring_i386.deb") | [ AMD64]("http://download.virtualbox.org/virtualbox/4.2.12/virtualbox-4.2_4.2.12-84980%7EUbuntu%7Eraring_amd64.deb")

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

