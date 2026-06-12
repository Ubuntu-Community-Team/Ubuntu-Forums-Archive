---
title: "Ubuntu In Small Businesses"
date: 2009-09-21
forum: The Cafe
---

### Post by marsdend on 2009-09-21
Hi all,

If a small business was to use Ubuntu as its main OS, is there any solutions to syncronise users files over the network? eg. If a user loggs onto PC-A and creates test.doc, when they log onto PC-B test.doc will also be there.

Thanks in advance,
Dan

---

### Post by stwschool on 2009-09-21
Ubuntu One is one way, and with karmic (next release) it'll be pretty tightly integrated.

---

### Post by marsdend on 2009-09-21
> **stwschool said:**
> Ubuntu One is one way, and with karmic (next release) it'll be pretty tightly integrated.

Thanks, would i have to create an Ubuntu One account for each user though? I think it might actually work. Ill have to do some research on that.

---

### Post by diablo75 on 2009-09-21
Another way is if you have one computer designated to function as a server for multiple clients to connect to and store files.  I wouldn't be surprised if you could go so far as to have an entire home folder for each user stored on the server so the client PC's would function like dummy-terminal-hybrids.  It might take a few seconds longer for them to log into their account, but everything would be stored in a central location.

Though right now, I'm using [Dropbox]("http://www.getdropbox.com") to sync a folder between multiple PCs over the Internet.  It's free (as long as the amount of data in the shared folder doesn't exceed 2GB at any given time) and is ***very*** easy to setup.  You create an account in a few seconds, then use the same username/password to sync future installs on other computers.  Or you could have people create their own accounts for their own 2GB folder and then create a folder in your own dropbox to invite them to have access to, and vice-versa.  I should also add that the thing I like about Dropbox more than Ubuntu One is that it's cross-platform friendly.  It works on Linux, Mac and Windows.

---

### Post by ChrT on 2009-09-21
Or, you could just use rsync or something like svn, localy, without resorting to the Cloud Allmighty...I seriously don't understand why a company would want to share their business secrets with whoever owns the servers in the "cloud".

---

### Post by scrooge_74 on 2009-09-21
You could have a box acting as server and you could nfs a folder in that server so all PCs when they log they mount that share, then your users could just put stuff there.

Or you can create users in the server then you can let them mount their own shared folder when they log into any of the other PCs (each user has his own desktop config so you can get them to use their own shared folder only)

---

### Post by marsdend on 2009-09-21
> **diablo75 said:**
> Another way is if you have one computer designated to function as a server for multiple clients to connect to and store files.  I wouldn't be surprised if you could go so far as to have an entire home folder for each user stored on the server so the client PC's would function like dummy-terminal-hybrids.  It might take a few seconds longer for them to log into their account, but everything would be stored in a central location.

Though right now, I'm using [Dropbox]("http://www.getdropbox.com") to sync a folder between multiple PCs over the Internet.  It's free (as long as the amount of data in the shared folder doesn't exceed 2GB at any given time) and is ***very*** easy to setup.  You create an account in a few seconds, then use the same username/password to sync future installs on other computers.  Or you could have people create their own accounts for their own 2GB folder and then create a folder in your own dropbox to invite them to have access to, and vice-versa.  I should also add that the thing I like about Dropbox more than Ubuntu One is that it's cross-platform friendly.  It works on Linux, Mac and Windows.

Thanks for the reply, I have been looking at dropbox and it seems a good idea, I have also been looking at LTSP server and using thin clients, do you have any experience with this?

Dan

---

### Post by LowSky on 2009-09-21
> **scrooge_74 said:**
> You could have a box acting as server and you could nfs a folder in that server so all PCs when they log they mount that share, then your users could just put stuff there.

Or you can create users in the server then you can let them mount their own shared folder when they log into any of the other PCs (each user has his own desktop config so you can get them to use their own shared folder only)

Best option is this idea.

---

### Post by chefbodini on 2009-09-21
I'd suggest a central server for data file storage.  This simplifies storage management and data backup solutions.  NFS is bundled and free to use.  It's easy to set up and maintain.

---

### Post by Dragonbite on 2009-09-21
> **scrooge_74 said:**
> You could have a box acting as server and you could nfs a folder in that server so all PCs when they log they mount that share, then your users could just put stuff there.

Or you can create users in the server then you can let them mount their own shared folder when they log into any of the other PCs (each user has his own desktop config so you can get them to use their own shared folder only)

Oooh.. I think I'm going to set this up for my home network to make it easy for everybody to have a shared location (and easy to back-up!)

---

### Post by marsdend on 2009-09-21
> **LowSky said:**
> Best option is this idea.

Thanks, how do i go about creating users in a server though? Would this be similar to using active directory in windows?

Cheers,
Dan

---

### Post by koenn on 2009-09-21
> **marsdend said:**
> Thanks, how do i go about creating users in a server though? Would this be similar to using active directory in windows?

Cheers,
Dan
```
adduser 
```


and no, it has nothing to do with active directory.

---

### Post by koenn on 2009-09-21
> **marsdend said:**
> Hi all,

If a small business was to use Ubuntu as its main OS, is there any solutions to syncronise users files over the network? eg. If a user loggs onto PC-A and creates test.doc, when they log onto PC-B test.doc will also be there.

Thanks in advance,
Dan

I agreee with those that said you 'd set up a file server for this sort of thing. What and how will depend on whether this small business is going to run Ubuntu on its server(s), its desktops, or both.

---

### Post by marsdend on 2009-09-21
> **koenn said:**
> I agreee with those that said you 'd set up a file server for this sort of thing. What and how will depend on whether this small business is going to run Ubuntu on its server(s), its desktops, or both.

I am looking for a complete ubuntu solution.

---

### Post by ChrT on 2009-09-21
> **marsdend said:**
> I am looking for a complete ubuntu solution.

Ubuntu Server with ssh and rsync for the fileserver(s), and whatever flavour of regular Ubuntu for the desktops/workstations.

---

### Post by koenn on 2009-09-21
wouldn't simply having a server with nfs exports for home directories and shared files be sufficient ?

---

### Post by AlexanderDGreat on 2009-10-11
I would definitely go for LTSP Server.

---

