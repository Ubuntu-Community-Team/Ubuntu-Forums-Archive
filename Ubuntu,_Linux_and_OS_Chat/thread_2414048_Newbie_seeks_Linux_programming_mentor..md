---
title: "Newbie seeks Linux programming mentor."
date: 2019-03-05
forum: Ubuntu, Linux and OS Chat
---

### Post by donniedureau on 2019-03-05
Hi all,

I am teacher who would like to use my Linux OS instead of Windows or Mac.
The only thing holding me back is being able to print.
The school uses a print server (I hope my terminology is right) called Uni-flow made by NTware for Canon. 
But a Linux version doesn't exist.
I have been quoted $325-625AUD for a solution. Crikey.

But I thought that if I had access to the apple version of the app, and can read/access the script, could I try to write a linux version based on it?
I have no knowledge of programming, but am interested in seeing if it is possible, and learning along the way.
I'm also happy to ditch the idea, if more experienced people here tell me it's a waste of time.

So I guess my first question is: Is it possible to write a linux app based on an apple one?

Thanks for reading.

---

### Post by coffeecat on 2019-03-05
Hi and welcome to the forum. You posted to a section of the forum (Ubuntu Dev Link Forum) that is so neglected I had to clear a path through the cobwebs to move your post. :wink: It wasn't really the best place anyway. I've moved this to ***Ubuntu, Linux & OS Chat*** where forum members should be able to address your general questions about transitioning to a Linux-based OS, preferably Ubuntu!

As this is a chat area, it's really for discussing general points. If, as a result of discussion, you have some specific technical questions to ask, please do start a support thread in a support area of the forum.

Good luck!

---

### Post by mastablasta on 2019-03-05
> **donniedureau said:**
> Hi all,

I am teacher who would like to use my Linux OS instead of Windows or Mac.
The only thing holding me back is being able to print.
The school uses a print server (I hope my terminology is right) called Uni-flow made by NTware for Canon. 
But a Linux version doesn't exist.
I have been quoted $325-625AUD for a solution. Crikey.

But I thought that if I had access to the apple version of the app, and can read/access the script, could I try to write a linux version based on it?
I have no knowledge of programming, but am interested in seeing if it is possible, and learning along the way.
I'm also happy to ditch the idea, if more experienced people here tell me it's a waste of time.

So I guess my first question is: Is it possible to write a linux app based on an apple one?

Thanks for reading.

it's a waste of time. what you need are linux drivers for the printer. 

you would have to write them form scratch and reverse engineer them. MacOS is not linux. it is also not based on linux. perhaps the closes to MacOS is BSD or more accurately the DarwinOS. even if you could get access to mac driver, they would likely be in binary code which means you don't have the source code to do any changes on it.

1. options would be get a cannon driver and connect to printer directly over the network.
2. if that is no possible use windows in virtualbox or similar to do the printing.
3. if that is ridiculous, then consider the environment and don't print.

---

### Post by SeijiSensei on 2019-03-05
There might be ways to connect to it over the network and not need a driver.  Does it support Postscript, for instance?  What happens if you visit [http://localhost:631/](http://localhost:631/) and choose Administration > Find New Printers?  Does it see the device?

---

### Post by oldfred on 2019-03-05
This says it has Linux & network print drivers.
[https://canyonfalls.net/wp-content/uploads/2018/06/intsol_uniFLOW_2018LTS_Brochure.pdf](https://canyonfalls.net/wp-content/uploads/2018/06/intsol_uniFLOW_2018LTS_Brochure.pdf)

---

### Post by Geoffrey_Arndt on 2019-03-07
You might be able to easily setup printing via Google Cloud Print from the Chrome Browser.

---

### Post by him610 on 2019-03-09
You might be able to configure CUPS to use a generic PCL driver, or a Windows printer via Samba.

Here is a link written in German on Uniflow Linux Installation CUPS 1/ 6
[https://www.zid.tuwien.ac.at/fileadmin_z/files_zserv/student/druckservice/driver/uniFLOW_LinuxCUPS_Installationsanleitung.pdf]("https://www.zid.tuwien.ac.at/fileadmin_z/files_zserv/student/druckservice/driver/uniFLOW_LinuxCUPS_Installationsanleitung.pdf")

Google has a translation utility that will translate it to English.

---

### Post by donniedureau on 2019-03-10
Thanks to all for these suggestions! Very much appreciated.
Am going to forget about creating an app from scratch and try the cloud option.
Again, thanks to all.

---

