---
title: "Good Idea?"
date: 2006-06-22
forum: The Cafe
---

### Post by Kimm on 2006-06-22
I have recently aquired an Old laptop.

Its a P3 850 MHz with 256 mb RAM (dont know the other specs).
The battery is completely dead, and the OS (win2k) has broken down completely...

I'm thinking about making an SSH server out of it... I'll put Xubuntu on it and have it compile things when I need a program from source, and perhaps use it to store files when I reinstall.

Is this a good idea?
I'm a novice at making servers so I'm woundering how I would go about moving files to and from the server? Should I have an FTP server on it?

And is there any way to not make it available for the general public? (i.e. just in a local network)

---

### Post by Virogenesis on 2006-06-22
[QUOTE=Kimm]I have recently aquired an Old laptop.

Its a P3 850 MHz with 256 mb RAM (dont know the other specs).
The battery is completely dead, and the OS (win2k) has broken down completely...

I'm thinking about making an SSH server out of it... I'll put Xubuntu on it and have it compile things when I need a program from source, and perhaps use it to store files when I reinstall.

Is this a good idea?
I'm a novice at making servers so I'm woundering how I would go about moving files to and from the server? Should I have an FTP server on it?

And is there any way to not make it available for the general public? (i.e. just in a local network)[/QUOTE]
Well I can answer one of your questions relating to the FTP yes you can make an ftp and ban all outside traffic from logging in you can do this.
two ways block the port using a ip table rule or within the ftpd itself.

---

### Post by Kimm on 2006-06-23
Ah, that sounds like a good idea... using a whitelist and block everyone but me...
Sounds like an idea! ^^

---

