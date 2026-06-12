---
title: "How to log on to root directly?"
date: 2016-02-15
forum: Server Platforms
---

### Post by Jake_Simmons on 2016-02-15
Hi,
I know its not the safest to log on directly to root, but for my application to work, that is what i need to do. i can not use the su or sudo -i options, and so i must log on directly for this to work. I have tried setting the root password using ```
passwd
``` whilst logged in to root, and then logging out and trying the username 'root' and the password i set. If anyone could help me out that would be greatly appreciated!
Many thanks,
Jake

---

### Post by sudodus on 2016-02-15
It is against the security policy of Ubuntu to log in as root, so I don't want to tell you how to do it.

If you tell us details about your application, I think someone (I or someone else) can help you solve the problem without logging in as root.

---

### Post by lensman3 on 2016-02-15
> **sudodus said:**
> It is against the security policy of Ubuntu to log in as root, so I don't want to tell you how to do it.

If you tell us details about your application, I think someone (I or someone else) can help you solve the problem without logging in as root.

Just using cross machine backup programs (rsnapshot, rsync) and figuring out which user to do non-root backups is a waste of time!  I've tried to setup a non-root backup using another user (bin, wheel or what-ever) was too frustrating and wasted too much time.  Finally deleted everything and went with root backups.  Once more than two machines are involved not worth the hastle.  Whoever decided to propagate the non-root is best mantra should get the "not invented here" M$ dunce cap.

---

### Post by MAFoElffen on 2016-02-15
Backing up remotely or local? Running or with services shut down? And as sudodus asked, which application or how are you wanting to backup? What do you want to backup?

---

### Post by cariboo on 2016-02-15
Everything you need to know about sudo is available [here.]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Habitual on 2016-02-16
I smell an [xy]("http://xyproblem.info/") problem. :)

---

### Post by Jake_Simmons on 2016-02-16
ok, i have an app that can run commands at the press of a button (you pre-set the command and it runs it when you click the button) it seems like a really good idea, and i want to try it out. Unfortunately, the commands like poweroff that would be quite neat require sudo, and as soon as the app requires a login, i thought that logging into root would allow me to perform poweroff without the need for a second password entry from my account (as root needs verification). The app is called SSH remote, and i have it on ios. If you have a solution, that would be great.

---

### Post by ian-weisser on 2016-02-16
Check your design: You are trying to defeat a deliberate safety verification. What happens when you miskey or typo?

One solution: Edit the sudoers file.
Another solution: Send a dbus message to the Power Manager.

---

