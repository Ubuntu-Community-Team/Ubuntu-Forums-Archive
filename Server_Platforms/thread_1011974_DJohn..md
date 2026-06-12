---
title: "DJohn."
date: 2008-12-15
forum: Server Platforms
---

### Post by Ferret-Simpson on 2008-12-15
Has anybody ever tried using djohn - Distributed John?

Here's the story: I have a (Physical) Security server, which is an SGI Indy. My aim for it is to have it take periodic photos of my living room, compress them into moderate PNG and upload them both to my internal file server (A Windows 2003 Server) and to my external file service. (Actually an Apple MobileMe account - Webdav on OS X Server in Cupertino.)

This part is all nice and easy thanks to the simplicity of IRIX. Unfortunately, when I got the machine, I was never provided with a password. Soooo. I ran john for 7 minutes and cracked it. Unfortunately, I then decided that 7 minutes was too short for my liking, maxed out all the security settings and immediately forgot the password. 16 days on a Core 2 Duo and I still don't have the damn thing. Obviously this is running on a single core, when my laptop is on. I also have a whole ruddy rack of HP Proliant DL360 G2's with Dual P3's and Hardy (For some reason, Intrepid's version of Grub isn't found by the BIOS. *shrug*) So, I have a look round and find djohn!

My question, basically: Has any body used it, is it easy to compile (Unlike for example... AcerHK) and does it work efficiently?

G-Man.

---

### Post by MJN on 2008-12-15
What password are you trying to crack? And what is it protecting?
 
If it's a user password, and there's no encryption, just replace the password (in /etc/passwd|shadow) with root access.
 
Apologies if I missed the answers these questions in your text - I'm not familiar with the exact setup you describe.
 
Mathew
 
[Edit: A Google search for 'SGI Indy password' finds [this]("http://unix.derkeiler.com/Newsgroups/comp.sys.sgi.admin/2005-02/0048.html") as the first result. Given how easy the solution appears to be I guess I am missing the complications in your case?]

---

### Post by Ferret-Simpson on 2008-12-15
```
gman@NS0:~/INDY$ john -restore
Loaded 1 password (Standard DES [48/64 4K])
guesses: 0  time: 16:22:31:08 (3)  c/s: 244414  trying: iwz6wdj - rx1z4mh

```

Alas! The indy has no built in media reader, just a scsi port and I have no external scsi media readers! The firmware password I reset a long time ago - only the system internal password remains. Unfortunately, SASH (Stand Alone SHell) the firmware interface can read but not write files. So I managed to cat the contents of the passwd and shadow files, but I have no way to overwrite them!

Thus: john.

---

