---
title: "How to make ISO from 7.10 download?"
date: 2007-10-20
forum: The Cafe
---

### Post by roseen on 2007-10-20
I downloaded 7.10 and received 5456 files for a total of 4.2 GB. A total of 10 files are visible, including directories and files.  Now what?
How do I turn these files into an ISO image that I can burn to a DVD.

Does this seem right?  The only command that work is extract, but it doesn't seem to do anything.  
Any suggestions?  Thanks

---

### Post by jfinkels on 2007-10-20
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by -grubby on 2007-10-20
It's supposed to download as an ISO file, where did you download it from.

---

### Post by reyfer on 2007-10-20
Where did you download from? I understand that when you download, you get the ISO image, so I don't understand why you get the file structure.

---

### Post by Spike-X on 2007-10-20
What burning program do you use? I know GnomeBaker and Nero (for Windows) both have a "burn to image" function.

Or I guess you could just burn all the files you downloaded to a data disc.

---

### Post by Spike-X on 2007-10-20
> **reyfer said:**
> Where did you download from? I understand that when you download, you get the ISO image, so I don't understand why you get the file structure.
This happened to a friend of mine as well. We never could figure out how/why it happened.

---

### Post by lyndaj70 on 2007-10-20
Unless you are experienced in creating bootable disks, I would attempt to download again.  It's "supposed" to be downloaded as an ISO already, so you may not have all of the files, or even worse, those files could be hacked.

Take care,
~L

---

### Post by Sofie on 2007-10-20
I downloaded the ISO and want to burn it on a dvd. 

I am currently using Ubuntu 7.04, and cant find a program to burn the dvd (rw)? 

Is there such?

I want to make a new installation, because I am new and explored to careless, so much are ****** up...  And I dont know what I did and to what... So Im starting over with the new Ubuntu.

---

### Post by popch on 2007-10-20
> **Sofie said:**
> I downloaded the ISO and want to burn it on a dvd. 

I am currently using Ubuntu 7.04, and cant find a program to burn the dvd (rw)? 

Is there such?.

I right-clicked the ISO which I had downloaded, then selected the command to write the image to a CD. There was not more to it.

---

### Post by zerosystem on 2007-10-20
> **roseen said:**
> I downloaded 7.10 and received 5456 files for a total of 4.2 GB. A total of 10 files are visible, including directories and files.  Now what?
How do I turn these files into an ISO image that I can burn to a DVD.

Does this seem right?  The only command that work is extract, but it doesn't seem to do anything.  
Any suggestions?  Thanks

I know I know what's wrong. You see the command extract because winzip/winrar by default is set to open .iso files. You probably have visible file extensions turned off. To turn them on, in any open directory window, go to Tools>Folder Options>View, and uncheck "Hide extensions for known file types".

Now, when you look at the file you downloaded (and with every other file on your system as well) the file will have a three letter extension. You should now see the '.iso'.

Don't extract it. Instead, use a program like Nero, or the free program known as 'ISO Recorder'. With Nero, just look for an option like 'burn image' or something similar. If you're going to use ISO Recorder, just install it and then right click on it and select burn/write or something similar.

---

