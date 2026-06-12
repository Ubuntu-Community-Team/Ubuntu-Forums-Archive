---
title: "File transfer from Mac OS X to Starling"
date: 2009-09-21
forum: System76 Support
---

### Post by macabrem on 2009-09-21
I was researching how to best transfer files, securely, from my Mac with OS X to my Starling (once I actually receive the Starling).  

I came across this article:  [http://labs.iamkoa.net/2007/10/27/networking-ubuntu-mac-os-x-fugu-it/](http://labs.iamkoa.net/2007/10/27/networking-ubuntu-mac-os-x-fugu-it/)

Does this seem like a good option and/or the best way?

Also, I'm wondering if I plug in an external USB hard drive if it could/would be recognized by both OS's - and just transfer files by copying them to the USB hard drive from one computer then plugging it into the other and dragging the files off?

---

### Post by jml on 2009-09-21
Fugu should be a good solution for you for secure transfers over a distance.  But you never mentioned how far separated the computers are.  If they are in the same room, and you have admin access to both of them, another solution would be to run either a crossover cable or a standard network cable between them and set up networking.  Normally, you have to use a crossover cable, but Mac OSX can tell the difference between the two and "rewire" its network connection to accomodate either type of cable.  If you only have a limited number of files to transfer, another way is to upload the files from the Mac to a large enough thumb drive and then download them to the Starling.  That is how I transfer files from my Mac to my Starling.

Joe

---

### Post by macabrem on 2009-09-21
> **jml said:**
> Fugu should be a good solution for you for secure transfers over a distance.  But you never mentioned how far separated the computers are.  If they are in the same room, and you have admin access to both of them, another solution would be to run either a crossover cable or a standard network cable between them and set up networking.  Normally, you have to use a crossover cable, but Mac OSX can tell the difference between the two and "rewire" its network connection to accomodate either type of cable.  If you only have a limited number of files to transfer, another way is to upload the files from the Mac to a large enough thumb drive and then download them to the Starling.  That is how I transfer files from my Mac to my Starling.

Joe

Well, when I get the Starling, I can put it right next to my Mac.  It's been so long since I've had to hook two computers together with a network cable, I guess I'll have to see if I can figure out how to do that between two different OS's.

Will an external hard drive work the same as a Thumb drive since they are both USB?  Does the external have to be formatted a certain way to be recognized by both Mac OS and Ubuntu?

---

### Post by thomasaaron on 2009-09-21
> Well, when I get the Starling, I can put it right next to my Mac. It's been so long since I've had to hook two computers together with a network cable, I guess I'll have to see if I can figure out how to do that between two different OS's.

I would not recommend that. I would set up openssh on on the Starling, and one of these...
[http://www.openssh.com/macos.html](http://www.openssh.com/macos.html)
...on the Mac.

Then you can use an SSH tunnel to transfer files between the machines.

> Will an external hard drive work the same as a Thumb drive since they are both USB? Does the external have to be formatted a certain way to be recognized by both Mac OS and Ubuntu?

A USB drive would work great. That's probably the easiest way to accomplish your task.

---

