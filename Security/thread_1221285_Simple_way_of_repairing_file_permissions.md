---
title: "Simple way of repairing file permissions"
date: 2009-07-23
forum: Security
---

### Post by confuciusquinn on 2009-07-23
os x has a utility: 
[http://en.wikipedia.org/wiki/Repair_permissions](http://en.wikipedia.org/wiki/Repair_permissions) 
that helps you fix file permissions that could have become insecure on your system. For example, a system file that is supposed to be only writable by owner, but for some reason is writable by group and other. Does a similar utility exist for ubuntu? I'm thinking about running

```
 sudo chmod -R o-w / 
```

could this break anything? I'd also like to know which files should not be other / group readable. Basically I want a clean and simple way of sandboxing new users on my system.

---

### Post by bodhi.zazen on 2009-07-23
There is not easy way of fixing your system if you run that command and it breaks.

I would not change ownership or permissions system wide in that way if I were you.

What is it about the default permissions you do not like ? By default regular users can not edit system files.

---

### Post by cybertoast on 2009-07-23
confusciusquinn,
first you should go to vegetarian paradise in chinatown. yes in nyc.

But more importantly, the repair permissions on osx does not seem to change system file permissions:

> 
Does Disk Utility check permissions on all files?

No. Files that aren't installed as part of an Apple-originated installer package are not listed in a receipt and therefore are not checked. For example, if you install an application using a non-Apple installer application, or by copying it from a disk image, network volume, or other disk instead of installing it via Installer, a receipt file isn't created. This is expected. Some applications are designed to be installed in one of those ways.
 (from [http://support.apple.com/kb/HT1452](http://support.apple.com/kb/HT1452))

The umask option in linux is usually what handles this sort of thing for new users/files/folders (often the user default umask is 022: [http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html](http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html)).

I would actually think that what you're proposing
```
 sudo chmod -R o-w /
```
*would* cause all sorts of problems. For example, /var/lib files need to be writeable be non-owner and non-group processes often. And /var/log files are pretty much mostly written to by non-owner/group processes.

What specific system file(s) are you worried about being writable by unauthorized users?

Sandboxing users can also be done by setting up a [chroot jail]("https://help.ubuntu.com/community/BasicChroot"). Not sure if this is what you want to do, so not putting more details here until you tell me more.

enjoy

---

### Post by confuciusquinn on 2009-07-23
i'll check it out. went to Decibel, awesome vibe. 

Basically, I want to keep a user to their HOME directory, and maybe one or two other directories that I give them access to, and nothing else. can chroot do this, or is chroot just for applications?

---

### Post by bodhi.zazen on 2009-07-23
> **confuciusquinn said:**
> i'll check it out. went to Decibel, awesome vibe. 

Basically, I want to keep a user to their HOME directory, and maybe one or two other directories that I give them access to, and nothing else. can chroot do this, or is chroot just for applications?

If you stop and think about it, that is pretty much the default settings.

What you propose is not really practical. A user needs at least read access as well as r-x access to many many locations */bin */sbin /tmp etc, etc, etc.

Perhaps if you describe what it is you are wanting to do I can give you better advice. I can not tell if you are wanting a kiosk, chroot for a ftp user, or what really. You might want to look at selinux or apparmor as well.

---

### Post by confuciusquinn on 2009-07-23
hm, I guess you're right. I don't know that much about ubuntu and I guess I wanted someone to confirm that for me. thanks. 

Here is the situation: I have a server where I host multiple websites, and I'd like to subcontract developers and limit their access to only the specific projects they are working on. I think I will make a group for each project, assign the users to their respective project groups, and configure the read/write/ex permissions on the project files accordingly.

---

### Post by bodhi.zazen on 2009-07-23
Put their (www) root directories in $HOME

Give them access with vsftp, chroot home with vsftp (see the config file)

[http://ubuntuforums.org/showpost.php?p=7629250&postcount=6](http://ubuntuforums.org/showpost.php?p=7629250&postcount=6)

---

