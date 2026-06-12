---
title: "Work Computer"
date: 2010-11-29
forum: Virtualisation
---

### Post by kpayton on 2010-11-29
Im considering Loading up my Laptop (Lenovo SL510) with Ubuntu 10.10, and DLing Virtual Box to Support Windows Environment.

The question I have is has anyone done this before?  Any Draw backs?  I'm in IT so if I break it I fix it, but Im curious.  Any noticeable difference running Ubuntu as Host as opposed to Windows?

---

### Post by reiki on 2010-11-29
> **kpayton said:**
> Im considering Loading up my Laptop (Lenovo SL510) with Ubuntu 10.10, and DLing Virtual Box to Support Windows Environment.

The question I have is has anyone done this before?  Any Draw backs?  I'm in IT so if I break it I fix it, but Im curious.  Any noticeable difference running Ubuntu as Host as opposed to Windows?

Your ram will be a determining factor in how well windows performs in a VM. I have a Dell Zino HD with 8gigs of memory. I run Ubuntu as host and often have an XP and Win7 VM running as well for various reasons. No issues at all. 

First make sure your SL510 is supported as far as drivers for all of the various hardware. Sound, touchpad, etc. You can usually get a decent indication of this simply by booting an Ubuntu LiveCD.

Once you establish that your laptop is supported to your satisfaction, you can decide about either dual booting or virtualizing. I have both (because I have a 750GB hard drive). I shrank my factory Win7 partition to 100GB so I could boot to win7 native in case I need technical support from Dell. I could have made it considerably smaller. The rest is Ubuntu. I boot to Ubuntu by default. I start a VM of XP or Win7 (or OSX) as needed, when needed and because of the 8GB of memory I have no performance issues at all.

Added benefit: Once you have a Windows VM installed and updated, you can snapshot it and if it gets hosed up with virus/malware/spyware you just revert to known good snapshot.

---

### Post by kpayton on 2010-11-29
> **reiki said:**
> Your ram will be a determining factor in how well windows performs in a VM. I have a Dell Zino HD with 8gigs of memory. I run Ubuntu as host and often have an XP and Win7 VM running as well for various reasons. No issues at all. 

First make sure your SL510 is supported as far as drivers for all of the various hardware. Sound, touchpad, etc. You can usually get a decent indication of this simply by booting an Ubuntu LiveCD.

Once you establish that your laptop is supported to your satisfaction, you can decide about either dual booting or virtualizing. I have both (because I have a 750GB hard drive). I shrank my factory Win7 partition to 100GB so I could boot to win7 native in case I need technical support from Dell. I could have made it considerably smaller. The rest is Ubuntu. I boot to Ubuntu by default. I start a VM of XP or Win7 (or OSX) as needed, when needed and because of the 8GB of memory I have no performance issues at all.

Added benefit: Once you have a Windows VM installed and updated, you can snapshot it and if it gets hosed up with virus/malware/spyware you just revert to known good snapshot.

Sadly I only have 2 Gigs of memory in this machine so thats the biggest factor and thats why I wanted to do Ubuntu as the Host because running Windows 7 and Ubuntu as a Gues is UGLY!  

I would love to take this laptop to 8 Gig but lets face it.  Convincing Management to up me to 8 Gig for purposes of Ubuntu is next to impossible :)

---

### Post by ebasa on 2010-11-29
Would be better to dual boot IMO.

---

### Post by cgb on 2010-11-29
I have Maverick running on a Dell E6400 with 2 GB ram and use virtualbox quite a bit to support windows users as well as run some apps that do not run properly through wine.  If you start to get to much going on you will notice the limitation due to the shortage of RAM but it actually runs quite smoothly.  No real other drawbacks except having to boot a second operating system but with how fast ubuntu loads it makes very little difference on boot time.

---

### Post by HermanAB on 2010-11-30
2 Gig RAM is enough for 3 simultaneous instances of XP of 500MB each.

BTW, if you are in IT, then you should probably use VMware Player - VMware experience will look better on your CV, since that is what all IT systems use.

---

### Post by kpayton on 2010-11-30
> **HermanAB said:**
> 2 Gig RAM is enough for 3 simultaneous instances of XP of 500MB each.

BTW, if you are in IT, then you should probably use VMware Player - VMware experience will look better on your CV, since that is what all IT systems use.

I doubt I'd run 3 at one time but it would probably be an instance of Server and Ubuntu and or Windows XP.  

BTW Ive been reading what are these "Tiny" versions of XP and 7 Im hearing about?  are they just stripped versions or?

I agree on my resume/CV it looks better for VMWare but I get the impression VMWare is money hungry.  almost $200 for VM Workstation?  Don't get me wrong its a great product but the cost ia bit rich in my opinion.  Virtual Box does the same exact thing and for Free, its just not a popular in the USA as it is over in the UK.  Ive also messed around with VM Player which is a great product as well I just thought VB was much faster for some weird reason and you could do snap shots of it?

---

### Post by cgb on 2010-11-30
Yes, "Tiny" versions are just stripped down versions without a lot of extras.  I do believe their is a free version of VMware Player for personal use.  I have used both and for the most part Virtualbox has worked smoother for me although it has been a while since I have used VMware so I may give it another try.

---

### Post by kpayton on 2010-11-30
> **cgb said:**
> Yes, "Tiny" versions are just stripped down versions without a lot of extras.  I do believe their is a free version of VMware Player for personal use.  I have used both and for the most part Virtualbox has worked smoother for me although it has been a while since I have used VMware so I may give it another try.

Correct VM Player is Free, however you cannot do Snap Shots, so if you are testing things VM Player isn't a good idea.  IF you are looking to just play and see different OS's it's a great idea.  You also can't create Network Fences in VM Player which I think Virtual Box may lack as well.  Could be wrong on that one though.

VM Player just seems much slower to me for some reason.

---

### Post by pricetech on 2010-11-30
I'd use VirtualBox.  I'm running it now on a Dell with 2 gigs of RAM, giving XP 1 gig.  Ubuntu is my host and XP my guest.  Works well enough.

You might just ask for more RAM.  It's cheap enough now they might just spring for it.

---

### Post by kpayton on 2010-11-30
> **pricetech said:**
> I'd use VirtualBox.  I'm running it now on a Dell with 2 gigs of RAM, giving XP 1 gig.  Ubuntu is my host and XP my guest.  Works well enough.

You might just ask for more RAM.  It's cheap enough now they might just spring for it.

How does VPN connectivity work on it?  Good Bad?  Just curious.  I love Virtual Box while I agree VM looks better because everyone knows what it is.

---

### Post by TBABill on 2010-11-30
My concern beyond memory and dual boot is why you would use 10.10 on a work computer? if you rely on it for business, 10.04 is safer, more proven and certainly more stable for lots of users. Being a LTS I would think you would be safer entrusting your work to something with a bit more stability....but just my $0.02. :)

---

### Post by kpayton on 2010-11-30
> **TBABill said:**
> My concern beyond memory and dual boot is why you would use 10.10 on a work computer? if you rely on it for business, 10.04 is safer, more proven and certainly more stable for lots of users. Being a LTS I would think you would be safer entrusting your work to something with a bit more stability....but just my $0.02. :)

I haven't had bad luck with 10.10, I just worry about functionality.  Obviously the HOST OS needs as much resource as possible and slapping WinBlows on it is like putting a Ford Escort Motor in a Lambo :)  

Dumb Question but LTS = Limited Tech SupporT?

---

### Post by tgm4883 on 2010-11-30
> **kpayton said:**
> I haven't had bad luck with 10.10, I just worry about functionality.  Obviously the HOST OS needs as much resource as possible and slapping WinBlows on it is like putting a Ford Escort Motor in a Lambo :)  

Dumb Question but LTS = Limited Tech SupporT?

Long term support.

I use 10.10 on my test box, (Dell optiplex 960 with 8GB ram) and I can run quite a few VM's on this box. I work with others who use Windows as their host OS (same machines) and they seem to have RAM issues with 2-3 VM's at a time. 

When I had my older test box with 2GB ram I could run ~5 XP vm's at a time (although they were set to low amounts of ram and even that was pushing it). The same machine running Windows Server 2003 only was able to do 1 comfortably.

---

