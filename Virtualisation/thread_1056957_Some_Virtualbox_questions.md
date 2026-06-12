---
title: "Some Virtualbox questions"
date: 2009-02-01
forum: Virtualisation
---

### Post by tagrat on 2009-02-01
I'm thinking of building a machine from the ground up for use with virtualbox. Been reading through the threads and user manual. Had some questions/ need some confirmations. 

Base system - intel dual core - 4 gig - probably DDR2. 
Video card - Not sure who's writing the best linux drivers these days  - opinions needed. 

Thought I'd use Ubuntu 64bit as the host OS. Does it make more sense to use a lightweight desktop like Xfce desktop - want to try operating out of 2 guest instances on XP one Ubuntu. I realize a guest install of Ubuntu under Ubuntu doesn't make a ton of sense - but I have plans to use this guest for testing.  

Guest OS's would be XP 32bit and Ubuntu 32bit. 

Anything I'm not thinking of? Flawed logic?

---

### Post by dkev on 2009-02-02
Are you going to be keeping both guest OS's up and running all the time?

---

### Post by tagrat on 2009-02-11
Generally no. one at a time

---

### Post by Perryg on 2009-02-12
Good day Tagrat,

I have Vista business 32 bit as host and run Ubuntu 8.04 LAMP & Ubuntu 8.10 as client 24/7 in a test enviornment.  The setup you specified should support all that you need to do.  I have also done this using Ubuntu as the Host but was having timing issues running (2) guests as above.  Since Virtual Box is going to use its own video driver you can go mad with the card you use on the Host.  I have a Nvidia GeForce 8600 512 meg card.  Also remember if you use M$ Windows as the host you are not going to get more than 3.5 gig of memory to work in the 32 bit version.

---

### Post by niteshifter on 2009-02-12
Hi,

See attached screenshot. That's Ibex and XP (seamless mode) Guests running on a 32 bit install of Gutsy (Host) with 2GB RAM. The XP VM has 1GB RAM, the Ibex VM 512MB. True, I'm bumping against my physical RAM limit, but experience tells me I can go to around 1GB into swap before things get weird.

I don't think you'll have any problems with 4GB / 64 bit ;)

---

