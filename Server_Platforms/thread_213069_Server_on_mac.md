---
title: "Server on mac"
date: 2006-07-10
forum: Server Platforms
---

### Post by jordans on 2006-07-10
Is it at all possible to install Ubuntu Server 6.06 on a mac? And do i need a special disk to do it? And once i put it in how would i go about installing it.

---

### Post by Novastorm on 2006-07-10
Ok, yes i believe it's entirely possible to run a server on a MAC. I haven't done this myself, but I can give you a few pointers.

First go to the Ubuntu site, click "download" underneath the server section and then select a local file mirror. Then you need to select the correct ISO depending on your architecture.

If your using an older MAC, ie. PowerPC architecture (G3, G4 etc) then you need ubuntu-6.06-server-powerpc.iso or if your using an Intel MAC, I believe you can just use ubuntu-6.06-server-i386.iso

However if you haven't got previous linux experience you might be better to use the desktop installation instead, it includes all the server packages (can be installed via apt-get/aptitude/synaptic) and a GUI interface. In this case download the ISO specific to your architecture that contains the word "desktop" in it.

---

### Post by venzen on 2006-07-10
It is possible. Go to 

[http://se.releases.ubuntu.com/6.06/](http://se.releases.ubuntu.com/6.06/)

and scroll down to the section 'Server Install CD' then choose the Mac (PowerPC) iso. Download this, burn it to cd (instruct your burning software to make the cd bootable). Put this CD in your Mac, boot up and follow the prompts.

You will have to dedicate your entire hard disk to Ubuntu - you will lose everything on there - so backup before you start ;) 

What kind of Mac do you own? i.e. how much memory, hard drive size and what processor?

---

### Post by jordans on 2006-07-11
It is a G3 with a 10 GB harddrive and 512 MGS of ram but it has worked with breezy for a long time spotlessly. I just don't know how i would boot up then be able to start it. I can't go into command line and try to install it can I?

---

