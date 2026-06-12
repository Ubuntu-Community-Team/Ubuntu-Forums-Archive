---
title: "Automatic File Synchronization"
date: 2009-02-24
forum: Server Platforms
---

### Post by Evil_Network on 2009-02-24
I am looking to put together an Ubuntu based file server for my home studio. I would like to be able to automatically synchronize a small directory tree between my Windows workstation and the server. I am looking for a method beyond simple file sharing thru Samba obviously.

Any input one could offer would be appreciated.

Thanks!

--Joe

---

### Post by dajasc on 2009-02-24
I had a similar desire.  See this: [http://ubuntuforums.org/showthread.php?t=1078677](http://ubuntuforums.org/showthread.php?t=1078677)

---

### Post by Evil_Network on 2009-02-24
I should have been more explicit...

I am not wanting this for backups. I do video editing, graphics design, DVD Authoring, etc. So one thing I can't do is utilize a network drive. A network is good for 25mb DV files with the right switch. But it's not ok for HD. So here is what I would like to accomplish.

I have a storage raid in the workstation. I keep a directory for all client files, shoots, etc. It is that directory tree that I would like to have synch with a file server running Ubuntu and a mirrored storage device. Using simple tools in Windows is not the answer because it wants to copy everything, not just incremental new files. At least that is my understanding.

It was mentioned to me by a colleague that he felt there was a Linux utility that could reach out to a shared drive and do what I wanted. This is what I was hoping for. 

--Joe

---

### Post by freerkkalsbeek on 2009-02-24
Is rsync possible? Works great between *nix systems, but I have no idea if it's running on Windows.

Freerk

---

### Post by dajasc on 2009-02-24
There is an easy to use windows implementation of rsync, DeltaCopy, it uses the rsync algorithm and therefore supports incremental copying.  It can run as a scheduled service.

---

