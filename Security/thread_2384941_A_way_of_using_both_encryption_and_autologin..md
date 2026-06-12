---
title: "A way of using both encryption and autologin."
date: 2018-02-14
forum: Security
---

### Post by kdidkovsky on 2018-02-14
I have written a server software that has to run automatically when a computer boots, including the situation when it restarts after power failure. It has to start even if no user is in the room at the moment (and most of the time there will be no user in the server room). I can use a common autologin via lightdm and start my software either via .profile or via "Startup application" from the graphic menu. Part of the software needs a GUI, so it can not be started from /etc/rc.local before the X server starts.

Now I have to install the software for the end user and protect it (the software) from unauthorized access. There will be another thread about file access permissions, but here I want to discuss the following situation. Let's suppose I've perfectly protected my system via file permissions and the logged in user cannot steal/modify any data or binaries. Unfortunaly, he can take the disk out and connect it to another Linux machine where he has root access rights, thus making my protection useless. That's why I want to encrypt some part of the filesystem so that the data and binaries are only accessible when the system is booted as designed.

I've already found out than neither home folder encryption works with autologin, nor a private folder inside home can be mounted without a user typing in the password. And even truecrypt without a password (with a key file) requires the user to press enter. So my question is: is there any way at all of allowing the system to boot automatically without any interaction with the user, while keeping private data encrypted and thus unaccessible when the disk is connected to an another PC?

---

### Post by deadflowr on 2018-02-14
> So my question is: is there any way at all of allowing the system to boot automatically without any interaction with the user, while keeping private data encrypted and thus unaccessible when the disk is connected to an another PC?
No.
That would defeat the purpose.

---

### Post by kdidkovsky on 2018-02-15
> **deadflowr said:**
> No.
That would defeat the purpose.

Am I right then that every system that starts automatically and does something without interaction with the user (a web server, a database, an industrial automation system, a medical system) can be broken into just by removing the disk and by inserting it into another Linux machine? Of course, there can be another means of protection, such as DB keys, containers etc., but is it true that Linux itself has no means of preventing such access?

---

### Post by ubname on 2018-02-15
Maybe you're trying to make a complicated thing a bit too easy, i'm not a security expert in any way but your setup is flawed i think.
If data is valuable there must be no *power failure* and no physical access must be granted otherwise your security is a joke.
Maybe it is possible to boot a full encrypted disk having the encryption key on an USB flash drive used as boot drive(?), when you remove USB it will not boot
if the HD is stolen/removed it's encrypted so no access to data.

---

### Post by kdidkovsky on 2018-02-15
> **ubname said:**
> Maybe you're trying to make a complicated thing a bit too easy, i'm not a security expert in any way but your setup is flawed i think.
If data is valuable there must be no *power failure* and no physical access must be granted otherwise your security is a joke.
Maybe it is possible to boot a full encrypted disk having the encryption key on an USB flash drive used as boot drive(?), when you remove USB it will not boot
if the HD is stolen/removed it's encrypted so no access to data.

1. The system I'm talking about is used in remote locations where reliable power is a rare treasure. The server rack is backed by an UPS, but there's a chance that the power loss will last more than 4 hours (usual time on UPS in our projects). In this case an unqualified person from the support staff has to press a single button to start the system once the power is back again.

2. The customer _always_ has physical access to the system, otherwise he can't use it. The problem is that the customer is sometimes also a competitor trying to duplicate/reverse engineer the system. I understand that every protection can be broken but don't want to make the task too easy for such people.

---

### Post by ubname on 2018-02-15
Maybe it is possible to boot a full encrypted disk having the encryption  key on an USB flash drive used as boot drive(?), when you remove USB it  will not boot
if the HD is stolen/removed it's encrypted so no access to data.

Another option: a virtual machine on external encrypted usb, you can save the key on the host and on reboot it will auto mount unencrypted, ence usable only on the system with the right key/permission
if plugged on another system it will ask for password.

---

### Post by kdidkovsky on 2018-02-16
> **ubname said:**
> Maybe it is possible to boot a full encrypted disk having the encryption  key on an USB flash drive used as boot drive(?), when you remove USB it  will not boot
if the HD is stolen/removed it's encrypted so no access to data.

Another option: a virtual machine on external encrypted usb, you can save the key on the host and on reboot it will auto mount unencrypted, ence usable only on the system with the right key/permission
if plugged on another system it will ask for password.

All these options require me or another trusted person to be present at the site to reboot the system if it's powered off. This is not acceptable even now, when there are less than a hundred objects with the system installed in different countries. Imagine that you'd have to call a Microsoft guy to power on a windows machine. If the trusted person was present, he could just enter the decryption password, that would be much easier.

I'll dig into USB protection keys topic, but that's another story. I just hoped that Linux native encryption tools would provide another level of protection.

---

