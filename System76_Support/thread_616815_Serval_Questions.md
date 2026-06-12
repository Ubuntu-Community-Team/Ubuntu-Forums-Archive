---
title: "Serval Questions"
date: 2007-11-18
forum: System76 Support
---

### Post by DomIncollingo on 2007-11-18
Hi,

I'm planning to buy a laptop with Linux pre-installed.  I've looked at the System 76 Serval and the Inspiron from Dell, but I'm very much leaning toward the Serval because it seems like a higher quality product.  Could someone who has used a Serval answer a few questions?

1) Does everything pretty much work out-of-the-box?  Are there any major gotchas?

2) When I create a user Id for myself, is there an easy way to give that user sudo privileges?  I know that ubuntu normally gives sudo privileges to the first user that is created, but I would imagine that System 76 creates that first user.

3) I've read that System 76 tweaks the OS so that it will work properly with the hardware.  Can you install the periodic updates / fixes from the ubuntu repositories (via the online updater) even though the OS has been tweaked?

4) Has anyone used the Medibuntu packages (specifically Google Earth) with this laptop?

Thanks very much for any input regarding the Serval!

Dom

---

### Post by Beaucephus on 2007-11-18
For number 3

Tweaked is probably not the right word. They *configure* it so the hardware functions.

---

### Post by jpkotta on 2007-11-19
2)  
```
sudo adduser jpkotta
sudo adduser jpkotta admin
```
or to use the GUI
```
sudo users-admin
```
The GUI is also available somewhere in the menu.

I've never even heard of Serval, so I can't answer the other questions.

---

### Post by palintheus on 2007-11-19
Sys76 doesn't add any user, they use the OEM install so on the first boot, you set the time zone, your user info, and a couple other things iirc.

---

### Post by rmemm on 2007-11-19
I don't have the model you're interest in, but I do have a Gazelle 2300 I purchased a couple of years ago.  I've been very happy with this the overall experience and would use them again.  I'm also still using Dapper 606 LTS version which was installed by System 76 at the time.

Answers to your questions:

*  Repositories - that's how it works.  Pretty much all of the stuff that System76 uses comes from the prepositores.  So yes custom install but nothing that modifies Ubuntu too much I think.  I think more recently they have the System76 driver package which may indeed be an addon -- so I don't know how it works.

*  Sudo permission.  My experiemince the System>Administration>Users and Groups gnome tool is used to modify a whole range of permissions, one is admin access via sudo - so it's all in the gui mostly -- by this I mean this and many other things.

Regarding out of the box -- my personal experience was that not 100% of everything was supported at that time -- but I was still very happy with my choice in general.  I think they have worked on this with the System76 driver and perhaps other things -- and more or maybe everything now is supported.  My experience with them was that they seem pretty open so I think you could probably just ask them directly about this for the exact model your going to buy.  

The other thing I would say about out of the box.  I had a few bumps in the road -- meaning a couple of things that perhaps should have been configured a little differently -- probably because I was customer number 1 or 2 during the transition to Dapper -- but they were right there with their email support -- very fast turn around even on weekends.  I suspect they were small at the time and in early startup mode -- so don't know what it's like today -- but at the time -- I was very happy with that.  I rememger thing -- do they ever go home.

I'd be interested in what other think -- but as of now I'm pretty positive.

Rob

---

### Post by thomasaaron on 2007-11-19
Nice work, guys. I love how the community is growing and contributing. And I DEFINITELY appreciate the help!

This is the way to start a Monday!

---

### Post by jml on 2007-11-19
I own a first gen Darter, not a Serval so some of my answers may not apply.  I'll try to answer them in the order you list them.

1.  On my Darter, yes, everything worked out of the box.  On some of the newer laptops according to posts on this forum, some advanced features do not work yet, finger print scanners, web cams etc.  You may want to e-mail System 76 at their support address.  They can answer specific questions about feature status.

2.  System 76 does what is called an OEM install, (similar to what other computer manufacturers do.).  So the first time the customer turns on the computer, it creates the admin (sudo) account. So you do not have to give sudo privleges to any other accounts.  From a security point of view I would only have one account with admin privliges on a machine any way.

3.  Actually, System 76 starts with a plain vanilla copy of the most current version of Ubuntu and then adds custom drivers to support the functionality Ubuntu does not support out of the box.  So, yes, you can do periodic updates to both Ubuntu and to the System 76 drivers when needed.

4.  Since I don't have access to a Serval, I can't answer this question.  Again, an e-mail to support at System 76 should yield an answer for you.


I was in contact with them a lot via e-mail before I made my purchase from them.  They usually answer e-mails very quickly and seem to go the extra mile to be helpful, both before and after the sail.  And, no, I do not own stock in the company, nor am I an employee.  I'm just a very satisfied customer.

Joe

---

### Post by farruinn on 2007-11-19
> **jml said:**
> 3.  Actually, System 76 starts with a plain vanilla copy of the most current version of Ubuntu and then adds custom drivers to support the functionality Ubuntu does not support out of the box.  So, yes, you can do periodic updates to both Ubuntu and to the System 76 drivers when needed.

Do they have their own repository for this driver package so it can be updated via apt?

---

### Post by palintheus on 2007-11-19
> **farruinn said:**
> Do they have their own repository for this driver package so it can be updated via apt?

Yes

---

### Post by DomIncollingo on 2007-11-19
Thanks very much for the replies and for the very useful information!  I appreciate it.

---

### Post by asmiller-ke6seh on 2007-11-21
I own a Serval Performance laptop - I've had it for about 9 months. I LOVE IT. Also, the folks at System76, and the community - they are great.

I looked at the Dell laptop with Ubuntu pre-installed AFTER I had already bought and had been using my Serval for a couple of months, and pricing out a similar spec'd system, I figure I got a better deal with System76 ... including a higher resolution display and a faster hard drive for a little lower cost.

Only two things ... I am patiently waiting for System76 to figure out how to support the built-in webcamera and the internal fingerprint reader - but I know they will get these working (they promised) and I know that I will have this laptop for quite a while, so one day I will get the word that when I run the latest version of the System76 Driver that these two items will be activated.

Until then, I stand behind the wonderful performance and solid design of the Serval Performance (which is really a Compal HEL/80 ... a really solid box).

---

