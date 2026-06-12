---
title: "No way to download folders from Ubuntu One website?"
date: 2014-04-09
forum: Ubuntu One (CLOSED)
---

### Post by I.Bun.Tu on 2014-04-09
I'm having some trouble getting the Ubuntu One client to connect to my account and download files from one of the machines I'm trying to use. This problem occurs about once or twice a month on all of my Ubuntu 13.10 machines at various different times (for example, I'm connected on my laptop [pcname: rogue] and just uploaded some music that I'm trying to get on my desktop [pcname: peacefactory], so Ubuntu One is connected fine on rogue, but on peacefactory, although the client appears to be working on peacefactory it will not sync and download files; this happens on all my machines for a day or so at different times throughout the month, usually only one machine at a time).

So until it works tomorrow I wanted to go to the website and download the folders. Then I didn't see any options in the web client and googled to find this:

[http://askubuntu.com/questions/269694/how-to-download-entire-shared-folder-on-ubuntu-one](http://askubuntu.com/questions/269694/how-to-download-entire-shared-folder-on-ubuntu-one)

So is this not possible or am I just not seeing how to do it?

Also if this is NOT possible, it should be made possible for situations like this where people cannot access the client.

Thanks.

---

### Post by bapoumba on 2014-04-09
Moved to Ubuntu One.

No, it is not possible to download a folder from the web interface. It has to be done file by file. The only way to get a folder is via the client.

Are you aware that Ubuntu One file storage is going to end by June (files still accessible til the end of July) ?
[http://ubuntuforums.org/showthread.php?t=2214632](http://ubuntuforums.org/showthread.php?t=2214632)

---

### Post by dhh915 on 2014-04-09
> **bapoumba said:**
> Moved to Ubuntu One.

No, it is not possible to download a folder from the web interface. It has to be done file by file. The only way to get a folder is via the client.

Are you aware that Ubuntu One file storage is going to end by June (files still accessible til the end of July) ?
[http://ubuntuforums.org/showthread.php?t=2214632](http://ubuntuforums.org/showthread.php?t=2214632)


There's the rub.  Ubuntu has already removed the Ubuntu One App. from the Ubuntu Software Center. S in my case, I just recently had to rebuild my machine from the ground up.  Now without having a copy of Ubuntu One app. on my rebuilt machine my files are "stranded"

---

### Post by bapoumba on 2014-04-09
Can you still access them from the other computer ? Files from last sync should be in the Ubuntu One folder in your home.

---

### Post by dhh915 on 2014-04-09
> **bapoumba said:**
> Can you still access them from the other computer ? Files from last sync should be in the Ubuntu One folder in your home.

In my case I only have it on one computer.

---

### Post by bapoumba on 2014-04-10
> **dhh915 said:**
> In my case I only have it on one computer.

Yes, I understood that. You are left with only two options :
- get the files one by one from the web interface
- go to the /<your_user_home>/Ubuntu One folder on the "rogue" labeled computer and copy from there, transfer to the other one over some removable media, usb thumb drive or CD or other cloud service (dropbox comes to mind, but there are other alternatives).

Quite sorry about the situation.

---

### Post by I.Bun.Tu on 2014-04-14
> **bapoumba said:**
> Yes, I understood that. You are left with only two options :
- get the files one by one from the web interface
- go to the /<your_user_home>/Ubuntu One folder on the "rogue"  labeled computer and copy from there, transfer to the other one over  some removable media, usb thumb drive or CD or other cloud service  (dropbox comes to mind, but there are other alternatives).

Quite sorry about the situation.

"rogue" was one of my machines, I think you might have mixed up posts.

> **bapoumba said:**
> Moved to Ubuntu One.

No, it is not possible to download a folder from the web interface. It has to be done file by file. The only way to get a folder is via the client.

Are you aware that Ubuntu One file storage is going to end by June (files still accessible til the end of July) ?
[http://ubuntuforums.org/showthread.php?t=2214632](http://ubuntuforums.org/showthread.php?t=2214632)

I did notice that email a day or two after I posted this thread. Normally I would advocate for adding this feature to the web interface but seeing as Ubuntu One is shutting down, I have nothing further to query or discuss on the subject. Thank you for the reply. I will mark this thread as solved.

---

### Post by bapoumba on 2014-04-14
> **I.Bun.Tu said:**
> "rogue" was one of my machines, I think you might have mixed up posts.
Quite possible, I guess you got the idea though. What I did is copy everything from my own /home/Ubuntu One folder to a separate /storage partition on the same machine and share from another cloud service the files i wanted to share. Of course, I had a limited amount of files of a limited size to share so that worked out OK for me. I understand this may not be a viable solution if you have a large number of files or if some of them are large. Thus the removable media suggestion.

> **I.Bun.Tu said:**
> 
I did notice that email a day or two after I posted this thread. Normally I would advocate for adding this feature to the web interface but seeing as Ubuntu One is shutting down, I have nothing further to query or discuss on the subject. Thank you for the reply. I will mark this thread as solved.
Thanks for doing the homework :)

---

### Post by thnewguy on 2014-04-14
You could use something like u1ftp, it is a program that connects to Ubuntu One using your login credentials and provides access to your files over a local FTP port. I've used it a couple of times to transfer files between Ubuntu One and a server installation.

---

### Post by bapoumba on 2014-04-14
> **thnewguy said:**
> You could use something like u1ftp, it is a program that connects to Ubuntu One using your login credentials and provides access to your files over a local FTP port. I've used it a couple of times to transfer files between Ubuntu One and a server installation.
I did not know that. Thanks for the info :)

---

### Post by Jon Hanna on 2014-05-01
There's now an option on the site to download all your files as a zip, which would be handy for some, though less handy than u1ftp if you don't want to pull all the files to the same place.

---

