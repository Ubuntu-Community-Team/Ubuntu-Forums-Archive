---
title: "Newbie security doubts about Onedrive linux client"
date: 2020-08-20
forum: Security
---

### Post by dabezt on 2020-08-20
First of all thanks for this superb community, it rocks!

I've a Security related doubt about Onedrive. I'm running latest Ubuntu Desktop 20.04.1 on my desktop computer and also in my laptop. So happy! it's the best linux distro for desktop I've found! I've also Windows 10 in dual boot (grub, etc.)

I'm worried about privacy and security with the Onedrive 'client':

I've found a (free) client to connect my Microsoft Onedrive to Ubuntu. The one that installs with 'sudo apt-get install onedrive' comes from Skillon gihub ([https://github.com/skilion/onedrive](https://github.com/skilion/onedrive)), but it does not work with Ubuntu 20.04.1 (crashes in the permisions url introduction process, more here [https://github.com/skilion/onedrive/issues/511](https://github.com/skilion/onedrive/issues/511)). I've read into Skillon github issues that I should use a newer one (skillon abandoned his fork in 2018), in a new fork: [https://github.com/abraunegg/onedrive](https://github.com/abraunegg/onedrive)
Following the steps in install.md ([https://github.com/abraunegg/onedrive/blob/master/docs/INSTALL.md](https://github.com/abraunegg/onedrive/blob/master/docs/INSTALL.md)), I've added a new PPA from Yannick ([https://launchpad.net/~yann1ck/+archive/ubuntu/onedrive](https://launchpad.net/~yann1ck/+archive/ubuntu/onedrive)). And installed the 'new' abraunegg onedrive client.

Of course, first step is to allow permissions to access from this application to your onedrive account. You have to open a login url in microsoft, and get permissions on to onedrive linux client, etc. It's working, after doing a onedrive --synchronize, I get my onedrive folder replied into ubuntu desktop.

My questions, with all my gratitude and respect to this tool / client developers:

Is it safe? 

I mean, I always try to think in a badway, so is it possible to be 'sending' unconciously to unwanted people my credentials or permissons?

if it's a new version why is not included by default into ubuntu ppa when first installing 'onedrive' like skillon old one?

Thanks a lot! Cheers!

---

### Post by TheFu on 2020-08-20
Don't use any cloudy service if you care about privacy and security. It is common sense, that seems to be uncommon when it comes to using "the cloud".  I don't understand why that is.  Good marketing, I suppose.  Opportunities to make money from your private information and direct access to your data.  They don't thank you for that do they?  

Do you really think they secure the data ... at all?

What is the business model around letting people store data on free storage? How does that earn money for the company?

All "cloudy" services are 1 bad SQL query away from leaking your data to others.  There's no magic "partition" to prevent other people from having access, especially in the non-paid versions. Careless Computing: [https://www.wilderssecurity.com/threads/chromeos-careless-computing-stallman.288904/](https://www.wilderssecurity.com/threads/chromeos-careless-computing-stallman.288904/)

IMHO.

Using some outside software just adds complexity and another team who can create poorly secured code.  Every software developer knows that each line of code is an opportunity to introduce 1-10 bugs.

---

### Post by EuclideanCoffee on 2020-08-20
OneDrive is a good tool. Microsoft, despite their poor reputation in the early security world, has a good reputation for maintaining security today, especially if you pay for it. If you didn't know, Microsoft's cloud infrastructure is powered by Linux. :)

Concerning the application, you will need to do a self-audit before you can determine its trust.

This application will need elevated privilege to install onto your computer via apt. This alone is a risk. Of course you can read the package scripts.

If you cannot read the source, you won't be able to determine if you can trust the source. Even if you can read the source, you will need to check each update before applying to your system.

Another way to is directly install the binary, but then the binary is a compiled piece of software, so anything could be on it. You can't audit the source then!

Then of course you need to send your information to the application own. This has been historically abused. I would not trust it.

Any package from the Universe repository is community supported and shouldn't be considered secure (by default, though there are plenty of good community software). [https://packages.ubuntu.com/bionic/onedrive](https://packages.ubuntu.com/bionic/onedrive)

---

### Post by dabezt on 2020-08-21
Thanks for all the answers! Cheers

---

