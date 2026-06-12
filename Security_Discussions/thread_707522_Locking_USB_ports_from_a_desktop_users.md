---
title: "Locking USB ports from a desktop users"
date: 2008-02-25
forum: Security Discussions
---

### Post by Alt69 on 2008-02-25
Hi, I am exploring options that will prevent my desktop users from inserting a USB key and either copying files to the drive, or removing files from the drive.   And while seraching them for USBs sticks might be fun :), i am hoping there are other options.

Is there a way to lock down the USB ports for a person who logs on as a desktop user, yet still allow full access for the administrator?

thanks,

---

### Post by ruy_lopez on 2008-02-25
System-->Administration-->Users and Groups. Choose a user and select "properties". Under the "User Privileges" tab, you can disable access to "external storage", "CD drives", "floppy drives", "Scanners", "Modems" etc. Disabling some of these should prevent a user doing most of the things that USB is used for.

---

### Post by Alt69 on 2008-02-25
thanks, will do some testing.

---

### Post by Alt69 on 2008-02-25
Hi, I have done some testing and it does not seem to work.

1) I created a brand new user on the server to test things out. I removed every check from the "user Privlidges" tab. I Used the gui to create the new user.

2) Log in with the user and pluged in a 250G Simple USB external hard and had full access to it. I could see all files, read from it, create files, etc.

Am I doing something wrong or am I missing something?


thanks.

---

