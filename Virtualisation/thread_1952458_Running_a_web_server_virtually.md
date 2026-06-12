---
title: "Running a web server virtually"
date: 2012-04-04
forum: Virtualisation
---

### Post by OliverHaslam on 2012-04-04
Hi.

I'm absolutely new to the idea of virtualization, but it intrigues me to say the least.

I also happen to need to install Ubuntu 64-bit to access my new 8GB of RAM. With the current install hosting a web site, I'm wondering whether it is possible (read, easy) to run a web server as a virtual machine. I'm thinking that I could clone the machine as it is, and then move it into the virtual world, behind the new Ubuntu 64-bit installation.

I assume this is entirely possible, but I am unsure about how port forwarding would work. How does everything know to push port 80 to the VM and not the host machine? I presume I cannot run Apache on both VM and host, either?

If I can save having to reinstall Apache and my site after the change to 64-bit, and get to play with virtualization at the same time, then I'm in!

Anyone care to help a quick learning n00b?

Cheers :)

---

### Post by haqking on 2012-04-04
> **OliverHaslam said:**
> Hi.

I'm absolutely new to the idea of virtualization, but it intrigues me to say the least.

I also happen to need to install Ubuntu 64-bit to access my new 8GB of RAM. With the current install hosting a web site, I'm wondering whether it is possible (read, easy) to run a web server as a virtual machine. I'm thinking that I could clone the machine as it is, and then move it into the virtual world, behind the new Ubuntu 64-bit installation.

I assume this is entirely possible, but I am unsure about how port forwarding would work. How does everything know to push port 80 to the VM and not the host machine? I presume I cannot run Apache on both VM and host, either?

If I can save having to reinstall Apache and my site after the change to 64-bit, and get to play with virtualization at the same time, then I'm in!

Anyone care to help a quick learning n00b?

Cheers :)

Yes it will work.

Yes you can clone your existing install to a image and back into a VM

The VM should have its own IP on the lan through bridged networking so port forwarding is required on the router to forward web requests to that machine as normal except to the VM IP and not the host.

And x64 bit is not required to access 8Gb as PAE will do so, however if you have x64 hardware then i would recommend x64 anyways.

Peace

---

### Post by OliverHaslam on 2012-04-04
> **haqking said:**
> Yes it will work.

Yes you can clone your existing install to a image and back into a VM

The VM should have its own IP on the lan through bridged networking so port forwarding is required on the router to forward web requests to that machine as normal except to the VM IP and not the host.

And x64 bit is not required to access 8Gb as PAE will do so, however if you have x64 hardware then i would recommend x64 anyways.

Peace

Ahhhh, it has it's own IP. That makes sense. 

I'm trying to get PAE to work but the new Kernel won't boot.

---

### Post by haqking on 2012-04-04
> **OliverHaslam said:**
> Ahhhh, it has it's own IP. That makes sense. 

I'm trying to get PAE to work but the new Kernel won't boot.

well it will have its own IP via NAT by default, i would switch it to bridged (so it acts like a real machine on the LAN) and assign its own static IP for your LAN.

---

### Post by OliverHaslam on 2012-04-04
> **haqking said:**
> well it will have its own IP via NAT by default, i would switch it to bridged (so it acts like a real machine on the LAN) and assign its own static IP for your LAN.

Which software would you recommend?

---

### Post by haqking on 2012-04-04
> **OliverHaslam said:**
> Which software would you recommend?

personally i prefer and use virtual box. (make sure you install extension pack) and enable guest additions in the VM for USB support as well as add your user account to the vboxusers group.

vmware works well also.

There are others.

---

### Post by OliverHaslam on 2012-04-04
> **haqking said:**
> personally i prefer and use virtual box. (make sure you install extension pack) and enable guest additions in the VM for USB support as well as add your user account to the vboxusers group.

vmware works well also.

There are others.

VB will do the job then? I'd been told VMware Viewer was better at bridging networks.

---

### Post by haqking on 2012-04-04
> **OliverHaslam said:**
> VB will do the job then? I'd been told VMware Viewer was better at bridging networks.

better in what way ?

if it works it works.

Virtualbox has never given me any problems, though i know what im doing ;-)

It is a just a simple drop down box in the VM settings for NAT to Bridged and then giving a static or DHCP assigned address as usual.

For your reference [http://www.virtualbox.org/manual/](http://www.virtualbox.org/manual/)

install both and see which you prefer

---

### Post by OliverHaslam on 2012-04-04
> **haqking said:**
> better in what way ?

if it works it works.

Virtualbox has never given me any problems, though i know what im doing ;-)

It is a just a simple drop down box in the VM settings for NAT to Bridged and then giving a static or DHCP assigned address as usual.

For your reference [http://www.virtualbox.org/manual/](http://www.virtualbox.org/manual/)

install both and see which you prefer



Thanks.

Final question - what's the best way of getting this install into a VM? Looking at Clonezilla but not getting far.

---

### Post by haqking on 2012-04-04
> **OliverHaslam said:**
> Thanks.

Final question - what's the best way of getting this install into a VM? Looking at Clonezilla but not getting far.

yes clonezilla is what i use.

Take an image and then boot a VM to the clonezilla cd or iso and clone the image back into the VM

---

### Post by OliverHaslam on 2012-04-04
> **haqking said:**
> yes clonezilla is what i use.

Take an image and then boot a VM to the clonezilla cd or iso and clone the image back into the VM

Struggling with the restore part.  I've got a VM ready, but Clonezilla didn't give me an ISO as I expected, and I'm not sure how to point Clonezilla or the VM at it for the restore.

Any tips as to the next step? Google's not helping and Clonezilla itself isn't great.

Cheers.

---

### Post by haqking on 2012-04-04
> **OliverHaslam said:**
> Struggling with the restore part.  I've got a VM ready, but Clonezilla didn't give me an ISO as I expected, and I'm not sure how to point Clonezilla or the VM at it for the restore.

Any tips as to the next step? Google's not helping and Clonezilla itself isn't great.

Cheers.

its not supposed to give you a .iso, it will be a tar.gz file image.

Set your VM to boot from CD (clonezilla CD) or a clonezilla CD .iso and it will boot into clonezilla like it did when you took an image.

Then choose restore from image file to the VM virtual hard drive.

---

### Post by OliverHaslam on 2012-04-04
> **haqking said:**
> its not supposed to give you a .iso, it will be a tar.gz file image.

Set your VM to boot from CD (clonezilla CD) or a clonezilla CD .iso and it will boot into clonezilla like it did when you took an image.

Then choose restore from image file to the VM virtual hard drive.

Cheers. That's what I thought I did, but Clonezilla complains there are no mounted drives.

---

### Post by haqking on 2012-04-04
> **OliverHaslam said:**
> Cheers. That's what I thought I did, but Clonezilla complains there are no mounted drives.

well have you set up a virtual hard drive for that VM ?

and you are booting that VM to the CD right ?

---

### Post by OliverHaslam on 2012-04-04
> **haqking said:**
> well have you set up a virtual hard drive for that VM ?

and you are booting that VM to the CD right ?

Yeah, done all that. When Clonezilla asks where to pull the image from, what am I telling it? There are no drives mounted other than the one it's going to write to.

The files I have from the clone are attached.

---

### Post by haqking on 2012-04-04
> **OliverHaslam said:**
> Yeah, done all that. When Clonezilla asks where to pull the image from, what am I telling it? There are no drives mounted other than the one it's going to write to.

The files I have from the clone are attached.

I dont know, where did you put the image ? ;-)

you need to make sure the image is accessible for restore be it on USB or wherever.

---

### Post by OliverHaslam on 2012-04-04
> **haqking said:**
> I dont know, where did you put the image ? ;-)

you need to make sure the image is accessible for restore be it on USB or wherever.

It's on a local drive. I've set it as shared in VirtualBox but I assume that's not it?

---

### Post by haqking on 2012-04-04
> **OliverHaslam said:**
> It's on a local drive. I've set it as shared in VirtualBox but I assume that's not it?

that wont be any good as shared folders is something you access via the guest OS which you dont have yet.

Stick it on a drive you can access in VB such as a USB drive which is easiest

---

### Post by OliverHaslam on 2012-04-04
This is as far as I get. (attached)

---

### Post by OliverHaslam on 2012-04-04
> **haqking said:**
> that wont be any good as shared folders is something you access via the guest OS which you dont have yet.

Stick it on a drive you can access in VB such as a USB drive which is easiest

Argh, I don't have a spare :(

---

### Post by haqking on 2012-04-04
> **OliverHaslam said:**
> Argh, I don't have a spare :(

;-)

well you can use a network location like in the list, clonezilla supports it as long as you know the parameters and location, or if not then you will need a USB device.

Even then, i presume you have made the virtual hard disk at least the size or larger than the source image.

You may also experience a little configuration issue such as static IP with it being a server etc.

most of the time it is an easy thing to remedy if problems exist after cloning.

Cheera

---

### Post by OliverHaslam on 2012-04-04
> **haqking said:**
> ;-)

well you can use a network location like in the list, clonezilla supports it as long as you know the parameters and location, or if not then you will need a USB device.

Even then, i presume you have made the virtual hard disk at least the size or larger than the source image.

You may also experience a little configuration issue such as static IP with it being a server etc.

most of the time it is an easy thing to remedy if problems exist after cloning.

Cheera

I'll try the network approach then. I assume I just use my normal IP/SSH settings?

Did that list of files look right?

---

### Post by haqking on 2012-04-04
> **OliverHaslam said:**
> I'll try the network approach then. I assume I just use my normal IP/SSH settings?

Did that list of files look right?

well yeah but you will have to configure networking for clonezilla to do that.

I cant tell you what those settings will be.

Yes looks right, it is just the one that is highlighted

---

### Post by OliverHaslam on 2012-04-04
Right, works over SSH but after finding the files I'm taken straight to a screen that wants to turn a partition into another image....

Does the VM drive need to be a big as the old one, or as big as the data that's going on it?

---

### Post by haqking on 2012-04-04
> **OliverHaslam said:**
> Right, works over SSH but after finding the files I'm taken straight to a screen that wants to turn a partition into another image....

Does the VM drive need to be a big as the old one, or as big as the data that's going on it?

then you made the wrong choice you need to restore from image to local.

as for the size, i always make the HDD file the same size or larger than the source drive

---

### Post by OliverHaslam on 2012-04-04
> **haqking said:**
> then you made the wrong choice you need to restore from image to local.

as for the size, i always make the HDD file the same size or larger than the source drive

I never get an option for that...

There's either use an image to restore or back up to, or use a disk-disk. That's it.

---

### Post by haqking on 2012-04-04
> **OliverHaslam said:**
> I never get an option for that...

There's either use an image to restore or back up to, or use a disk-disk. That's it.

well yeah use an image to restore is same thing i cant remember the wording as i havent done it for a while and am not looking at it.

are you following the documentation ;-)

---

### Post by OliverHaslam on 2012-04-04
> **haqking said:**
> well yeah use an image to restore is same thing i cant remember the wording as i havent done it for a while and am not looking at it.

are you following the documentation ;-)

You mean the documentation that says I should see this: [http://clonezilla.org/clonezilla-live/doc/02_Restore_disk_image/images/ocs-08-restoredisk.png](http://clonezilla.org/clonezilla-live/doc/02_Restore_disk_image/images/ocs-08-restoredisk.png) and I actually see the screen that I've attached?

After selecting the image to use via SSH, and then hitting Advanced, I get to this screen that wants to create a new image.

---

### Post by haqking on 2012-04-04
> **OliverHaslam said:**
> You mean the documentation that says I should see this: [http://clonezilla.org/clonezilla-live/doc/02_Restore_disk_image/images/ocs-08-restoredisk.png](http://clonezilla.org/clonezilla-live/doc/02_Restore_disk_image/images/ocs-08-restoredisk.png) and I actually see the screen that I've attached?

After selecting the image to use via SSH, and then hitting Advanced, I get to this screen that wants to create a new image.

I am afraid i dont know why you are getting that as i am not there to see the steps taken or look at your configuration.

I have never had any issues with clonezilla, i am guessing it is a option choice somewhere or issue with networking.


You will need to play around and read all the steps throughly and make the right choices.

Cheers

---

### Post by OliverHaslam on 2012-04-04
> **haqking said:**
> I am afraid i dont know why you are getting that as i am not there to see the steps taken or look at your configuration.

I have never had any issues with clonezilla, i am guessing it is a option choice somewhere or issue with networking.


You will need to play around and read all the steps throughly and make the right choices.

Cheers

There's obviously something wrong with the clone.

Anything other than clonezilla?

---

### Post by haqking on 2012-04-04
> **OliverHaslam said:**
> There's obviously something wrong with the clone.

Anything other than clonezilla?

[http://alternativeto.net/software/clonezilla/?platform=linux](http://alternativeto.net/software/clonezilla/?platform=linux)

i think remastersys may do it aswell but i have never used it.

I only ever use clonezilla and it works, i am guessing there is something you are doing or not doing along the way.

peace

---

### Post by CharlesA on 2012-04-04
> **OliverHaslam said:**
> There's obviously something wrong with the clone.

Anything other than clonezilla?
I use clonezilla as well and the drive you want to restore the image to must be at least as big as the source drive.

Make sure the location the images are stored is mounting correctly - I ran into that problem when trying to clone an image over the network and the box the image was on had problems with the network.

Are you using SSH or Samba?

---

### Post by OliverHaslam on 2012-04-05
> **CharlesA said:**
> I use clonezilla as well and the drive you want to restore the image to must be at least as big as the source drive.
 
Make sure the location the images are stored is mounting correctly - I ran into that problem when trying to clone an image over the network and the box the image was on had problems with the network.
 
Are you using SSH or Samba?
 
Hi,
 
I was using SSH, and it was connecting fine.
 
In the end I decided to give myself an sql test and just installed a clean version of Ubuntu and set everything up afresh. Just the Time Machine / Apple shares to sort now.
 
Cheers, I'd love to know why it wasn't mounting properly.

---

### Post by CharlesA on 2012-04-05
Strange. I haven't tried the ssh option, but if you were able to connect ok, and gave it the correct path, it should have been ok.

Anyhow, glad you got it set up and working.

---

