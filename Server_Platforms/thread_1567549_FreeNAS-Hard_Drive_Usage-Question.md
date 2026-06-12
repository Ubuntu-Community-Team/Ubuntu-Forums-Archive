---
title: "FreeNAS-Hard Drive Usage-Question"
date: 2010-09-03
forum: Server Platforms
---

### Post by rcayea on 2010-09-03
Hey Everyone,

I have a question about NAS. I hope, since I know just about nothing about it, other than what I been researching for the last 30 minutes, that this question doesn't sound too, o, rediculous.

I have three hard drives hooked to the same motherboard. My goal is to make a server-type device out of one of my hard drives and since I don't have the funds to buy any computer components at the moment I was wondering if I could utilize one of my hard drives with NAS. I would like to for example, be on my computer with Ubuntu, but let my wife still have access to the other Hard drive from her Vista computer. Is this something FreeNAS might help me with?


I know that I can't use one of my hard drives installed with Ubuntu Server because the server has to always be on and when I am on my other hard drive that limits the use of the server hard drive. 

My question is, can I install FreeNAS or similar product on one of my hard drives and have it accessable by my wife's computer even though I am running my ubuntu desktop hard drive, which is hooked to the same mobo?


Thanks,
Randy

---

### Post by ayenack on 2010-09-03
Hello rcayea.

No FreeNAS is it's own OS and run independently of other OS's. You could run it in a virtual machine but I would suggest using file sharing on the spare drive.

Take a look at this how to.

[http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/](http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/)

This is for 10.04

[http://macpablodesigns.wordpress.com/2010/05/01/enable-personal-file-sharing-in-ubuntu-10-04/](http://macpablodesigns.wordpress.com/2010/05/01/enable-personal-file-sharing-in-ubuntu-10-04/)

Best thing to do is create a folder on the drive put all the file you want in it and share that.

---

### Post by rcayea on 2010-09-04
Thanks for the feedback. I'll have a look at those links.

---

### Post by ayenack on 2010-09-04
No problem.

---

