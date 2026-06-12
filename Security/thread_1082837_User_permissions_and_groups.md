---
title: "User permissions and groups"
date: 2009-02-28
forum: Security
---

### Post by e24ohm on 2009-02-28
I remember reading an article some where that mentioned that you should create a user with none-root rights to safe guard against malicious code install, and other sort of nasties. I am new to Linux and need some help with creating a user with the correct level of rights. I found the utility that allows you to create a user, but what rights should I give this user?

For a standard user, who I do not want to be able to install apps, or change “anything” what do you folks recommend setting the user's rights at, and any tips you can offer.

thank you
E

---

### Post by insineratehymn on 2009-02-28
There are various tutorials/guides/how-to's to beef up the security of your new shiny Ubuntu box.

This one is a really good guide, and also goes into alot of detail of hot just how, but **why** you would want to secure your linux box. (and theres even a pretty good joke about viruses on linux).

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)


Start there, read it all, follow the links, and be enlightened. =)

---

### Post by e24ohm on 2009-02-28
> **insineratehymn said:**
> There are various tutorials/guides/how-to's to beef up the security of your new shiny Ubuntu box.

This one is a really good guide, and also goes into alot of detail of hot just how, but **why** you would want to secure your linux box. (and theres even a pretty good joke about viruses on linux).

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)


Start there, read it all, follow the links, and be enlightened. =)Hey mate, thanks for the link, and the article. this looks really nice. Thanks again....

Cheers!!!

---

### Post by e24ohm on 2009-03-03
Folks,
I have been reading about user rights, and groups in my Linux+ study material. I am at an lost, so please go slow with me, in the fact that I am coming from a windows point of view/mind set. When i create groups, is it a best practice to have a the user in which profile group: administrator, desktop user, unprivileged? 

I am worried that scripts would get installed, but i do not want to disable scripts because I need Flash to load for pages my users use.

Also, the user ID, is that just a random number, that is associated with a username?

Thank you,
E

---

### Post by bodhi.zazen on 2009-03-03
In general one gives users as few privileges as possible. There is no reason to give all users administrative access in either windows or linux.

If a user needs limited access, to say part of the system, that is what sudo is for.

see : [RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

and if you wish more info, look at these pages :

[http://www.sudo.ws/sudo/man/sudoers.html](http://www.sudo.ws/sudo/man/sudoers.html)

[http://www.sudo.ws/sudo/man/sudo.html](http://www.sudo.ws/sudo/man/sudo.html)

See also

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)

Note every distro starts user numbers at a different #. Ubuntu uses 1000 , rpm based systems often use 500.

The system recognizes users by number , not name.

See /etc/passwd and /etc/groups

---

