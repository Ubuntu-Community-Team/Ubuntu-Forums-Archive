---
title: "simple file server"
date: 2006-06-27
forum: Server Platforms
---

### Post by zeusdo on 2006-06-27
Can someone help me setup a simple file server. I'm looking for a step by step tutorial because I have never worked witha server before.

---

### Post by harisund on 2006-06-27
What exactly are you looking for? 

If all you are looking for is the ability to trasnfer files, you can install a FTP server. A better choice however would be to install SSH server, since you get the advantages of remotely being able to login and execute commands, and transfer files all through the same port. 

The package "openssh-server" gets you that.

---

### Post by Iowan on 2006-06-27
[http://www.howtoforge.com/]("http://www.howtoforge.com/")
There's a couple of articles on setting up a server. There may be some how-to's in one of the other forums (appropriately named **HOWTOs, Tips & Tricks**).

---

### Post by jimcooncat on 2006-06-27
For a linux server, I prefer SSH over Samba or NFS. I set up sshd with Blowfish as the default encryption, and turn compression on for those machines outside the building.

For a linux client for SSH, I use gFTP, though I've been trying SSHFS with great results these past few days. Nice thing with that is that the remote directory looks like a local directory to the machine, so I can use any file management tool or even the command line. I use keychain to hold my private keys.

For a Windows client for SSH, I use WinSCP. Excellent program, and I hope they will finish cloning all it's functionality into gFTP. I use Pageant to hold my private keys.

For a Windows server, I share folders and use Samba for a Linux client. I'd like to find an SSH server for Windows (outside of a full Cygwin install) but haven't had time to research yet.

You should be able to look up any of the jargon here at wikipedia.org and get lots of links to helpful documents.

I realize you said "simple", and SSH looks very complex. While it takes a little while to learn, it's actually simpler to use -- much simpler to maintain and tweak. Like many things, "It's easy when you know how."

---

### Post by harisund on 2006-06-27
I agree with jimcooncat. SSH pretty much does everything you can dream of. 

Of course you could still install the rest for 'legacy' purposes, but SSH can do both file sharing and remote administration in one shot and is accessible independant of the client operating system you are using.

---

### Post by GOwin on 2006-06-27
It's not an Ubuntu solution but it might be something you should check out: [www.openfiler.com](www.openfiler.com)

---

### Post by zeusdo on 2006-06-28
Thanks to everyone for your input.

---

