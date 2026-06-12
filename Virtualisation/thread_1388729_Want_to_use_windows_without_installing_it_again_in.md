---
title: "Want to use windows without installing it again in a VM"
date: 2010-01-23
forum: Virtualisation
---

### Post by Adbekunkus on 2010-01-23
Hi all. I have Ubuntu KarmicKoala 9.10 installed on my laptop as well as Windows XP Pro in another partition of my hard drive. My question is (I think) very simple: I want to use a Virtual Machine to access my windows system without rebooting AND without installing it anew in a virtual machine. Does anyone know how to do that?

---

### Post by ttoilleb on 2010-01-23
According to page 150 of the Virtualbox 3.1.2 Users Guide - *9.12 Using a raw host hard disk from a guest* - you can do this, with a few caveats.

If you don't already have Virtualbox installed, or do not have the Users Guide, visit [http://www.virtualbox.org/](http://www.virtualbox.org/) and begin exploring.

---

### Post by daltore on 2010-01-24
Is there any way to mount a physical partition as an image?  I'd rather not create an image if I can just treat the partition as one, but is there a way to make an image that links to the partition?

---

### Post by Thomas Garman on 2010-01-24
I spent several days researching this topic because I very much wanted to do the same thing you describe.  "Hey, if the operating system is just sitting there on a partition then why can't I use it in a virtual machine?"  

IF you got it to work, you would have to re-authenticate your copy of windows every time you booted into one or the other machine, virtual or actual, because every time you boot up there is a little windows configuration file that detects the hardware associated with the install and if you try to boot the OS into two different machines then it won't let you and you will end up having to call a Microsoft hotline to reactivate.  The virtual machine has a different hardware configuration than the version that is actually installed on the hard drive.  Hence, two machines.

There are a couple of sites you can find easily/google-find where bloggers claim to have succeeded in doing what you describe but the write-ups are so vague that I doubt it.  Or else it is similar to getting Snow Leopard installed in a Virtualbox... not the kind of thing a mere mortal could ever hope to do if it has ever even been done.

Just plunk down a hundred bucks and go get yourself an OEM copy of XP home basic and install that in your virtualbox.  It takes almost no effort or time.  I assume that you don't consider your time to be worthless. The math is clear:

spend 50 hours testing out different configurations and reading posts in forums and trying and retrying installations to get Virtualbox to load an existing partition OR ELSE just go buy a copy of XP and be done with it.

This whole virtualization thing is a little bit of a fad really.

---

### Post by Mistrblank on 2010-01-27
> **Thomas Garman said:**
> 
This whole virtualization thing is a little bit of a fad really.

Clarification, it's a fad for the home user.  Virtualization itself isn't going anywhere.  I can run 10 independent hosts on a 1U server, it's great.  I can run an entire test environment on my workstation.  I can prototype new roll outs in minutes rather than hours.  

At home, I've used it successfully for a handful of applications, but really at home I don't want to manage more OSes and I don't have the ability (or desire) to build an entire enterprise management setup.  Another OS is another headache to worry about backing up.  I want it to work and to be easy at home.  Right now, the extent I use it for is a locked down OS to remote into my work desktop without any cross contamination from my home OSes and I have another that runs a stripped down OS for centralizing GNUCash and Redmine.

---

