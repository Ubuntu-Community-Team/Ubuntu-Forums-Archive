---
title: "Need Free/OpenSource Disk Imaging Software"
date: 2006-09-02
forum: The Cafe
---

### Post by clparker on 2006-09-02
Hi All,

I need the name of a prefered free and/or opensource Disk Imaging program, something allong the lines of norton ghost or powerquest imaging software.

I am a student at the University of New Mexico here in Albuquerque. I'm in charge of maintaining a computer lab with 12 Dell PCs with windows on them. We want to start developing images of these machines so if they have some kind of trouble, we can just re-image them and have them up in a matter of minutes rather than hours. It would also help with consistency, and building images is something to keep us out of trouble.

Please Help. Google's not helping, beleive a team of three guys is going nowhere. This dept. at the University is pretty straped for cash.

Again, we just need some kind of free or open source Disk Imaging system to deploy windows images to these Dell GX170L and GX 240 Desktops.

-Thanks in Advance,;)

CLParker

---

### Post by mips on 2006-09-02
There is always the **dd** command to image drives with. dd command is very powerfull and there is lots of documentation on how to image drives and other media with it.

Should work from most live cd's but have a look for a security/forensic based live cd. The linux version has one minor shortcoming, something about drives with uneven sectors or something of the kind, don't have time to check now. The BSD version does not have this shortcoming.

I would look for some right now but don't have the time. Maybe later.
Do a search for Forensic CD and/or dd image

[http://www.rajeevnet.com/hacks_hints/os_clone/os_cloning.html](http://www.rajeevnet.com/hacks_hints/os_clone/os_cloning.html)
[http://www.freesbie.org/](http://www.freesbie.org/)
[http://www.e-fense.com/helix/](http://www.e-fense.com/helix/)
[http://www.linux-forensics.com/](http://www.linux-forensics.com/)

---

### Post by clparker on 2006-09-02
Not exactly what I was lookin for...
Need somekind of Program similar to ghost and\or some other imaging system so we can get one machine up and running and use that image for all of them.
There's gotta be some freeware windows apps that will do this simple task. A fullblown ghost like product in Linux will do.
Idealy we'd like to upload images to a computer we could use as a server and then boot to a CD and download these images over the server.
We simply just cant afford Norton Ghost @ $79.99 a liscence.
Somebody's Gotta have an idea...

---

### Post by milehigh on 2006-09-02
This might be what you're looking for:
[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

---

### Post by mips on 2006-09-02
[http://www.thefreecountry.com/utilities/backupandimage.shtml](http://www.thefreecountry.com/utilities/backupandimage.shtml)
[http://www.cs.utah.edu/flux/papers/frisbee-usenix03-base.html](http://www.cs.utah.edu/flux/papers/frisbee-usenix03-base.html)

---

### Post by clparker on 2006-09-02
Perfect!!! 
Thank You Soooooo Much!

-CLParker!!!

---

### Post by SoundMachine on 2006-09-02
dd is exellent, with it an bzip2 i can basically put an entire install on a cd.

---

### Post by slougi on 2006-09-02
Another vote for dd + bzip2/gzip.

---

### Post by UbuWu on 2006-09-02
Another option would be making them thin clients.

*** edit: I didn't see they are windows pc's, hmmm... ***

---

### Post by clparker on 2006-09-02
Yeah, any other ideas? It's 12 Windows PCs that I want identical images on, and price and consistancy are very important.

Thanks again for all your guy's help.

---

### Post by teet on 2006-09-03
I think you would only have to buy norton ghost once.  Why would you need 12 different copies of it?  The 12 computers are identical right?

If I was at the computer shop I used to work at I would just:

1.  get one computer set up exactly the way I wanted it (you'll have to do some special stuff to setup the preinstall environment in XP...b/c of activation)
2.  grab the harddrive out of another machine, disconnect the cdrom from the machine I just setup, and hook up the second harddrive to the cdrom's ide channel (or just plug the hdd into another SATA port if that's what I was using).
3.  boot up norton ghost from a 1.44" floppy disk (the whole program fits on one floppy) and do a 'disk-to-disk' copy of disk1 to disk2 (this process only takes 5-10 minutes).
4.  shutdown, disconnect, and repeat process until you get all the harddrives imaged.

-teet

---

### Post by jonzep on 2006-09-03
sounds like partimage would work well for what you want to do.

[http://www.partimage.org/](http://www.partimage.org/)

```
apt-get install partimage
```

if you have internet access you can do it using the ubuntu live cd and save the master image to a server, where you can later acces it and restore your boxes to the master state.

alternatively if the machines will not be able to access the net (and therefore no apt-get) you could always remaster an ubuntu disc or find a small distro that has recovery tools such as partimage included by default.

(btw ntfs support is "expirimental" in partimage however i have found it to work flawlessly)

---

### Post by clparker on 2006-09-03
> **teet said:**
> I think you would only have to buy norton ghost once.  Why would you need 12 different copies of it?  The 12 computers are identical right?

Wait, so we'd only need ONE liscence 1 x ($69.99) to image these machienes legally. Not 12 x ($69.99)???

I was under the impression we'd need some kind of bulk liscense to legally copy images from one machiene to dozens more.

I have several different types of images, I'd like to build. 
One for the Dells in the computer lab, and the employee systems.

---

### Post by mips on 2006-09-03
I thought you needed a free/opensource package ?

Just buy ghost and be done with it.

---

### Post by teet on 2006-09-03
> **clparker said:**
> Wait, so we'd only need ONE liscence 1 x ($69.99) to image these machienes legally. Not 12 x ($69.99)???

I was under the impression we'd need some kind of bulk liscense to legally copy images from one machiene to dozens more.

I have several different types of images, I'd like to build. 
One for the Dells in the computer lab, and the employee systems.

I think you would only need 1 license to do what I was saying.  Note that my method wasn't actually creating images...it was just cloning one harddrive to another one.  Also, it wasn't really using the full norton ghost program.  My method only required the version that fits on one 1.44" floppy.

Honestly, I'm not familiar enough with the norton ghost program to tell you if you would need 12 copies to make the images...we always used PQDI (powerquest drive image) to create and restore images at the shop.


Finally, as I mentioned before, if you're really wanting to image these machines you're going to have to setup the preinstall environment correctly.  See the link below for details.
[http://download.microsoft.com/download/E/B/A/EBA1050F-A31D-436B-9281-92CDFEAE4B45/OPK-preinstall-intro.doc](http://download.microsoft.com/download/E/B/A/EBA1050F-A31D-436B-9281-92CDFEAE4B45/OPK-preinstall-intro.doc)

-teet

---

### Post by clparker on 2006-09-03
When I worked in another dept. we built images for machines, and I know how to build an image, my problem is this dept. Has no money, no money as in zero dollars.

---

### Post by jdong on 2006-09-03
partimage is the most feature-filled and appropriate for your case. Also see SystemRescueCD for a simple, small LiveCD from which you can use partimage. Knoppix and Kanotix both have partimage installed, too, I believe.

---

### Post by frrobert on 2006-09-03
If you would like a windows solution.

I would recommend creating a PE Builder Cd with DriveImage XML on it.  Before I went to Ubuntu I used it all the time for imaging Windows and other issues.


The link for PE Builder is 

[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

The link for Drive Image XML is

[http://www.runtime.org/dixml.htm](http://www.runtime.org/dixml.htm)

---

### Post by phersotty on 2006-09-03
There is an article in the September 2006 edition of Linux Pro Magazine that shows how to create an image with tar.  It looks straight forward enough, but I don't know how well it would work for a Windows image.  If you need multiple Windows configurations then why bother with images?  You might as well do separate installations on each machine unless they are going to all be identical.

---

### Post by clparker on 2006-09-04
> **phersotty said:**
> If you need multiple Windows configurations then why bother with images?

We have 12 Opiplex GX 170Ls that act as Lab computers and About that many GX 240s that act as office computers, then we have bout six GX 270s.

Image deployment systems allow us to get a computer up and running in a matter of minutes, not hours.

Images are also something that allows us more consistency in our deployment. It lets us fix known problems much faster.

---

### Post by ago on 2006-09-04
If you do not like dd you can try partimage.

[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

For differences between partimage and dd see the FAQ

***edit: ops did not notice it had already been mentioned

---

### Post by clparker on 2006-09-04
Part Image Looks pretty good, Anybody know of any freeware windows apps that will do this?

---

### Post by ago on 2006-09-04
> **clparker said:**
> Part Image Looks pretty good, Anybody know of any freeware windows apps that will do this?

Why do you need a windows app to do that? What can it really add to dd\partimage? Once you learn them they are easy to use and they work well.

---

### Post by clparker on 2006-09-04
> **ago said:**
> Why do you need a windows app to do that? What can it really add to dd\partimage? Once you learn them they are easy to use and they work well.

I just dont wanna have to set up dual boot and then have to boot to linux just to upload and/or download images and/or set up a separate linux image server.

Anybody know of any freeware windows imaging software?

---

