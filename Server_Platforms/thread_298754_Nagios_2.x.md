---
title: "Nagios 2.x"
date: 2006-11-13
forum: Server Platforms
---

### Post by nocturn on 2006-11-13
I'm using Nagios from the repos on a Dapper-server install.  But Ubuntu is still using the 1.3 branch while Nagios2 is already at 2.5.

Is there an easy way (preferably deb packages) to move to Nagios2?

---

### Post by digilink on 2006-11-13
I'm certainly know expert when it comes to things like this, but I have been building upgraded packages from source using the following method, this may not work in every situation, but the packages I have done this with so far seem to be working:

Make sure you have source repositories enabled and issue:
sudo apt-get build-dep packagename

Download the source tree and extract it to it's own directory, then compile the package:

sudo ./configure
sudo make 
sudo make install

Again, this may not work in every situation, due to different versions of libraries, new ones etc. but I have built a few packages succesfully this way. 

Hope that helps.

---

### Post by digeratess on 2006-12-15
I'm going to try this this weekend. Would love to know if anyone else already has and any tips.

---

### Post by chrisfay on 2006-12-15
> But Ubuntu is still using the 1.3 branch while Nagios2 is already at 2.5.


Are you saying the Ubuntu 'repos' are using 1.3? I'm fairly positive that I installed my Nagios package via apt-get and its 2.5..:-k

---

### Post by digeratess on 2006-12-15
> **chrisfay said:**
> Are you saying the Ubuntu 'repos' are using 1.3? I'm fairly positive that I installed my Nagios package via apt-get and its 2.5..:-k

I installed the package nagios-text last night via apt-get from the Ubuntu repositories, and it is version 1.3.

Nagios 2 is listed as a package for Fiesty.

---

