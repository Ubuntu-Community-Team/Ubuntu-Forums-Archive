---
title: "Can't Add CD in Synaptic"
date: 2006-10-22
forum: Repositories &amp; Backports
---

### Post by bart_simpson on 2006-10-22
Hey everyone, I recently upgraded my Ubuntu Dapper Drake to Ubuntu Edgy Eft Beta Release two weeks ago, and everything was handy dandy until my wireless internet stopped working. I decided to wait for the Release Candidate to attempt to upgrade in hopes that it would solve my internet issues. I downloaded the Live CD to the Release Candidate, but everytime I go into Synaptic Add CD, it'll automatically unmount it and ask me again if I want to add another CD, which if I say yes, it'll jus mount it, then unmount it and ask me again if I want to add another cd. I tried going into a terminal and putting in:
sudo apt-cdrom add
sudo apt-get update
sudo apt-get upgrade

but after all is said and done, it says 0 new packages have been installed/upgraded and I'm left where I was to begin with. Any help would be great, thanks.

---

### Post by az on 2006-10-22
You cannot upgrade from the live cd.  It is not a big fat repository like the old install cds or the alternate cd.

---

### Post by bart_simpson on 2006-10-22
Ah, okay, thanks, any tips though on how I can get my Edgy Eft beta  release to Edgy Eft Release Candidate, because I cannot get my wirelss internet working in this beta release to upgrade.

---

### Post by az on 2006-10-22
> **bart_simpson said:**
> Ah, okay, thanks, any tips though on how I can get my Edgy Eft beta  release to Edgy Eft Release Candidate, because I cannot get my wirelss internet working in this beta release to upgrade.

Use the alternate cd.

What wireles card do you have and what method did you use to get it to work originally?

---

### Post by bart_simpson on 2006-10-22
I have a Wireless-G USB Network Adapter (Model Number: WUSB54G version 4) and it worked the first time with rausb0, but I don't know, it just wouldn't connect again after the first time I lost the connection. After fooling around with rausb0, I decided to install ndiswrapper, since it worked so well in Dapper Drake, and that also worked for a while, but after I lost my connection the first time, I go into Systemp->Preferences->Networking to see that it says it's not configured, I configure it, close it out, it still won't work, go back into Networking and it'll once again say it's not configured. I made sure I installed ndiswrapper-1.8 and have linked it and everything, but it still will not allow me to configure it in Wireless Networking.

---

### Post by bart_simpson on 2006-10-22
I'm downloading the Alternate Install CD now by the way to see if that will allow me to upgrade and hopefully solve my network problems.

---

