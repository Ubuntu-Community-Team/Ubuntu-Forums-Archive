---
title: "port existing disk image to different hardware i.e. raspberry pi"
date: 2016-06-17
forum: Server Platforms
---

### Post by Dana_Carter on 2016-06-17
I honestly don't know how stupid this question is....
I have an appliance that is on x86 hardware and running Ubuntu Server...
Is it possible to backup or image this system and move it 'as is' to a raspberry pi running ubuntu server?
Basically I would like to not have to redo all the myriad steps to deploy every app and script on the new box,  I would like to cut down the steps.

Can you, perhaps, just change out the kernel used in the image?  Or only back up all files except the kernel (including permissions etc.) and move it to the rpi?

Thanks for indulging me..

---

### Post by howefield on 2016-06-17
Thread moved to the "*Server Platforms*" forum.

---

### Post by coldraven on 2016-06-17
Hey Dana, I'm probably not the person who can answer your query but I'm interested to find out the solution. AFAIK any software running on the RPi has to be compiled for the ARM architecture. So your version of, say, Apache that's running on x86 will not run on the RPi.
You don't say what your appliance is so it's difficult to diagnose. You may be able to migrate all the config and database files and everything will be sweet. No doubt someone will tell us how that will work out :)
More info please.

---

