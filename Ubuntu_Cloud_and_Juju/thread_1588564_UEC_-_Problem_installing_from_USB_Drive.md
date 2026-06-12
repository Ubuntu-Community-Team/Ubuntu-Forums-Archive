---
title: "UEC - Problem installing from USB Drive?"
date: 2010-10-05
forum: Ubuntu Cloud and Juju
---

### Post by deviprasad_k on 2010-10-05
Hi,
 
I tried installing Ubuntu Enterprise Cloud (ver UEC 10.04.1).
 
I had installed the Cloud Controller, Cluster Controller, Storage Controller and Walrus on a server.
 
When I tried installing Node Controller on a VMWare Server it doesn't seem to work.
 
So, I had managed to get a DELL PE 1955 Server with VT extensions enabled.
 
I created a USB Drive using the **Universal USB Installer **software (downloaded from Ubuntu site). But, when I try to boot the server from the USB Drive, I **don't **get the **"Install Ubuntu Enterprise Cloud" **option.
 
Have anyone installed UEC from USB Drive?
Is there a problem installing UEC from a USB Drive?
 
Should i try installing it from a CD by creating a CD from the ISO image?
 
Kindly advice.
 
Regards,
Deviprasad

---

### Post by marrusl on 2010-10-07
It should work fine.  I have installed UEC from a USB drive a number of times without problem.

By "Universal USB Installer" do you mean "Startup Disk Creator" from the SYSTEM > ADMINISTRATION menu?  That's what I used to create the USB key installer from ISO.

What do you see when you startup the server?  Is it exactly the same except that particular line is missing?

---

### Post by deviprasad_k on 2010-10-08
I used the "Burn your CD or create a USB drive" option in [http://www.ubuntu.com/server/get-ubuntu/download](http://www.ubuntu.com/server/get-ubuntu/download) and downloaded the software for creating a USB Drive.
 
I get the "Install Ubuntu Server" and "Rescue a Broken System" options only. I don't get the "Install Ubuntu Enterprise Cloud" option as mentioned in the Installation Document.
 
Any comments...am i doing anything wrong here...

---

### Post by marrusl on 2010-10-08
No I don't think you are, I suspect the Universal USB Installer on windows mucks with the grub entries and does a poor job and removes the grub entry for the UEC install.

The best option, which I can confirm works great is to build the ISO on USB drive from within Ubuntu desktop.

Good luck with your UEC testing!

Mark

---

### Post by deviprasad_k on 2010-10-13
I burnt the iso on to a CD and it works!!
 
Next step is to build image and run the instances...
 
Wish me Good Luck !! :)

---

### Post by marrusl on 2010-10-15
Glad to hear it, Deviprasad.

Let us know how things go!

---

