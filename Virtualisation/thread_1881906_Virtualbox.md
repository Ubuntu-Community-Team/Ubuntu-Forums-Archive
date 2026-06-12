---
title: "Virtualbox ?"
date: 2011-11-16
forum: Virtualisation
---

### Post by rmp5s on 2011-11-16
I have a couple quick questions regarding Virtualbox.  I'm running Ubuntu 11.10 as the host and Win7 Ultimate as the guest.  

When I go to install the guest additions, it says it can't find the ISO.  Then it offers to download it but fails due to being "unable to connect to the server"...:

```
Failed to download the VirtualBox Guest Additions CD image from http://dlc.sun.com.edgesuite.net/virtualbox/4.1.2_Ubuntu/VBoxGuestAdditions_4.1.2_Ubuntu.iso.

Error downloading http://dlc.sun.com.edgesuite.net/virtualbox/4.1.2_Ubuntu/VBoxGuestAdditions_4.1.2_Ubuntu.iso - server replied: Not Found
```

I've never had this happen and I'm a bit unsure as to how to fix it.  It's kind of important to me because I'm trying to test the viability of running Ubuntu full time and just using the VM for gaming and windows specific things.  Installing the additions may even be rather irrelevant but I don't know.  Every Win7 guest I've set up, regardless of host, was unable to utilize the graphics hardware of the host.  Is there any way around this?  I can't even get transparent windows in my guests!...let alone actual gaming graphics!

And, would setting up Ubuntu Server using the Kernel Virtualisation Module help this?  I know that this is one of the least-overhead ways of running VMs and I'm a bit reluctant to go through the hassle of implementing it if it's not going to do what I want it to do.

For now, I guess I'll just have a Windows 7 partition and use Wine...

---

### Post by WasMeHere on 2011-11-16
Hi rmp5s,

I think that, as long as you want to play games 'needing graphics performance' you should keep your dual boot setup and run the windows games in Windows. Unless of course, you love to tweak your computer ;-)

The guest additions make it a nicer experience to run Virtualbox, so I suggest that you download it. Your problem might be that the internet connection is not yet working from your virtual machine. (It might also be some temporary problem at the Virtualbox web site.)

It was several years ago that I set up my Virtualbox (in Ubuntu 8.04, now upgraded to 10.04) so I don't remember the details, but I don't remember any big problems with it. I think you can get advice from someone around here, who has more recent experience. Nota bene, I use a wired internet connection.

Have fun finding out about Ubuntu :-)
Olle

---

### Post by rmp5s on 2011-11-16
Yea...that's the thing:  I LOVE tinkering with puters.  I already have a solution to the "problem" (it isn't even REALLY a problem since I created the situation...) by dual booting...I'm just trying to learn, tinker and find new trick ways of doing things.  

Plus, I would LOVE to get rid of windows all together.  I do lots of music recording so I'll never 100% leave windows, but to be able to run Ubuntu (or it's brother Mint, which I might even like a little bit more than Ubuntu 11.10) 95% of the time would be awesome.  I really like Linux as an OS and I really like what Ubuntu stands for so being able to even mostly switch would be awesome!

---

### Post by andrew.46 on 2011-11-16
You are using the repository version? There is a newer version + guest additions + extension pack here:

[http://download.virtualbox.org/virtualbox/4.1.6/](http://download.virtualbox.org/virtualbox/4.1.6/)

The extension pack has a more limited license than Virtualbox itself and amongst other things allows access to usb devices. Some [details here]("http://en.wikipedia.org/wiki/VirtualBox#Licensing"). Alternative if you wish to stick to the repository version simply change the repository mirror you are using and try again :).

---

### Post by rmp5s on 2011-11-19
I downloaded that one you linked, uninstalled the current one and reinstalled the new one and it works fine now.  Thank you!

---

### Post by andrew.46 on 2011-11-19
Great news :).

---

### Post by uRock on 2011-11-19
Moved to the *Virtualization* sub-forum.

---

### Post by sup on 2011-11-20
Alternatively, install  virtualbox-guest-additions-iso package - then virtualbox will not need to download anything.

---

### Post by rmp5s on 2011-11-21
Oh wow...didn't even see the sub forum.  Thanks for all the help!!

---

### Post by nowtejas on 2011-12-14
SWEET..!!!

Thank you very much..!

I have my Windows7 installation going on in the virtualbox 4.1.2 and as soon as it's done, my virtual machine gets a kick upto 4.1.6 :)

Hope the Guest Additions will work then! :)

---

### Post by AlastairG on 2012-02-27
I had the same problem but instead, I used this repository to get the latest version: [https://launchpad.net/~debfx/+archive/virtualbox](https://launchpad.net/~debfx/+archive/virtualbox)

Afterwards, I checked their site and they have an official repo: [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by shakma on 2012-03-28
> **sup said:**
> Alternatively, install  virtualbox-guest-additions-iso package - then virtualbox will not need to download anything.


This is really the best answer.  Thanks!

BTW, what he's saying is go to Synaptic (or Ubuntu Software Center, or use "apt-get" on the commandline) and install the following package:
virtualbox-guest-additions-iso

This should really be marked for download by default when you install VirtualBox...

Peace.

---

### Post by mwkeeler on 2012-03-29
> **sup said:**
> Alternatively, install  virtualbox-guest-additions-iso package - then virtualbox will not need to download anything.

I am so new to Ubuntu.  I am trying to figure out how to install packages after you download them.  Any suggestions? 

I installed Virtualbox and tried to set up guest additions.  I ran into the same problem that initiated this thread.  I downloaded the guest additions iso package and am trying to figure out the installation procedure.  I installed Ubuntu last week and this is all new.  What a different world inside Linux.  This is really cool!

---

