---
title: "Will ubuntu fill my server needs?"
date: 2008-08-31
forum: Server Platforms
---

### Post by elmo541992 on 2008-08-31
I need to get a somewhat old computer to share files over a small home network of windows machines, and also have access to these files from a remote computer over the internet.  

Will ubuntu be able to do this? and if so, what will I need to do/setup for it to work?  If not, what will?

~max

---

### Post by hrod beraht on 2008-08-31
It'll do both.
During install, choose Samba File Server for sharing files with Windows computers over your LAN and OpenSSH Server for accessing the server remotely over the internet.

Are you accessing the server over the internet with a linux machine or a windows machine? With linux, you can easily connect via SSH to have the server show up as just another drive. Or, with Windows you can use something like WinSCP to transfer files back and forth (assuming that's what you are wanting to do).

Are you familiar with Samba or SSH?

Bob

---

### Post by elmo541992 on 2008-09-01
ill be accessing files from windows machines.  Is there a way I could set up a password protected ftp server or something else that will let me access them through firefox or something?  Will i be able to access the files through explorer in windows on the lan network?

thatnks for the help so far!

~max

---

### Post by cdtech on 2008-09-01
Sure, I use proftp, command line ssh from my server.

---

### Post by mellowd on 2008-09-01
You'll be able to do what you want, plus about 1000 things more

---

### Post by Kolipoki on 2008-09-02
> **elmo541992 said:**
> ill be accessing files from windows machines.  Is there a way I could set up a password protected ftp server or something else that will let me access them through firefox or something?  Will i be able to access the files through explorer in windows on the lan network?

thatnks for the help so far!

~max
With WinSCP you won't need FTP, but it doesn't use a browser (IE, Firefox, etc.), though its interface can be set to look like the Windows Explorer. You might want to give it a try.

---

