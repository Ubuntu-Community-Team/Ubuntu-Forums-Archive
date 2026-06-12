---
title: "VirtualBox 3.0 good/bad/indifferent?"
date: 2009-07-10
forum: Virtualisation
---

### Post by maflynn on 2009-07-10
I'm looking to for information regarding how well (or not so well) virtualbox 3.0 is on jaunty.  I tried the prior version a little while ago but thought the performance was a tad sluggish in comparison to vmware (it could have been that I failed to tweak the settings or it really was slower - not sure which).

Anybody has any suggestions regarding virtualbox 3.0 versus vmware.  I have vmware reinstalled on ubuntu but I've not created any guest OSs yet.  If I'm going to make the jump nows the time and while I do plan on trying both out, I'd like to see what people here have to save about virtualbox and vmware.

I've been searching, and I've read both stickies.  It seems that there's a line of thought by bodhi.zazen that people are moving towards virtualbox and away from vmware

> 
Personally, at this piont, I have no need to run VMWare, KVM and Virtualbox both better integrate into Ubuntu and both seem to work better (for me) then VMWare.

Personally, I do not like the direction VMWar Server 2.0 is moving, 1.x is for me a much better product.

Becasue of those issues I am guessing community members are slowy moving away from VMWare, although I sure there are some very knowledgable people using VMWare.


Anyone care to elaborate on this further. 

As for background information I'm running 32bit version of Ubuntu 9.04 on my MacBook Pro with 4 gig of ram.

Thanks in advance

---

### Post by Murdock on 2009-07-10
I to dislike the new ways of VMware Server 2.x and changed to virtualbox(now 3.0) and i have never been happier. i didn't notice much or for that fact any performance issues when i changed and i could also use my VMware hdd on Virtualbox so that where another +.

i can't say i have anything negative to report about the change.

just to clear out what i'm running. 

MSI laptop with Celeron-M 1.7Ghz 2Gb Ram and running Ubuntu 9.04 32bit

Virtualbox is running WinXP

---

### Post by maflynn on 2009-07-11
I'm trying it now and so far the setup/install of virtual box is better then vmware server and accessing the environment is as well.

The performance appears to be good as well. I'm giving it more time but so far virtual box appears to be a good choice

---

### Post by kixome on 2009-07-11
it is absolutely excellent

---

### Post by IQRules on 2009-07-11
What tool to convert Vista partition /dev/sda1 over for Virtualbox?
I have 8.10 64-bit version. Anyone tries out 64-bit.
I dislike VMware 2.0 server, more issue to deal with.

---

### Post by tacantara on 2009-07-11
> **maflynn said:**
> 
As for background information I'm running 32bit version of Ubuntu 9.04 on my MacBook Pro with 4 gig of ram.

Thanks in advance

I've been using VB about as long as I've been an Ubuntu user (almost 6 months now).  My Dell XPS has half the RAM your MacBook has, and I find VB to run quite well.  In addition to Windows XP, I am also running the alpha version of Kubuntu Karmic Koala.  Both run smoothly for me (although I never run both VMs simultaneously).

---

### Post by happ on 2009-07-11
> **tacantara said:**
> I've been using VB about as long as I've been an Ubuntu user (almost 6 months now).  My Dell XPS has half the RAM your MacBook has, and I find VB to run quite well.  In addition to Windows XP, I am also running the alpha version of Kubuntu Karmic Koala.  Both run smoothly for me (although I never run both VMs simultaneously).

I am running VB 3.0.2 on Linux Mint 7_64 host. Have problem with copy paste function between host and guest. Guest additions installed.

---

### Post by Perryg on 2009-07-11
@happ,
I had this problem and updated to Version 3.0.2 an found that the problem had not been fixed, or I thought it had not.  The problem was I needed to remove the 3.0.0. Guest additions and then install the 3.0.2 Guest additions.  Must have been some kind of artifact left over.  Also a reboot of the Host and the Guest cleaned it all up.  I do not have this problem any longer.  Maybe this will help you as well.  By the way even though VBox does not require it any longer I also removed the previous VBox (3.0.0) from the host before I installed the new version.  (old fashioned about this I guess) but it did in fact take care of the problem.

---

### Post by maflynn on 2009-07-11
Unless I run into any issues I do have to say that VB has won me over. I don't need an windows environment too often but when I do, VirtualBox is more then up to the task
The ease of install and configuration are clearly superior then VMware.  Of course since I'm using vmware server the UI is geared towards running the guest OSs in a server environment where multiple guest OSs run. I only need one maybe two OSs.

Since Ubuntu has replaced my need (and desire) to run windows, there's only rare occasions that I'll need to fire up windows (for those odd programs that are windows only and no Linux variant found)

---

