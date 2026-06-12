---
title: "No updates in wily for a week"
date: 2015-09-07
forum: Ubuntu Development Version
---

### Post by wgarcia on 2015-09-07
I've upgraded to wily in two systems about one week ago, and I haven't received any updates since then. I don't have the "proposed" repository enabled. Is this normal? I usually receive zillions of updates in development versions.

---

### Post by dino99 on 2015-09-07
yes its normal, the packages landing into 'proposed' first can be very instable or even be a show stopper, like network-manager 1.0.4 actually which let you without network. So be patient and wait for stable packages in 'main'. But if you like troubles to dig around, then 'proposed' can give you some :D

---

### Post by wgarcia on 2015-09-07
OK, so it must be related to the big changes happening in "proposed" as commented in other threads, because as I said even without "proposed" enabled my experience is to receive numerous updates each week in development versions, so everything must be held there for the time being...

---

### Post by rrnbtter on 2015-09-07
Greetings,
I've been manually installing proposed, leaving out the network-manager 1.0.4 . So far everything is working fine. It's a testing version, but I have yet to get the network-manager to work even though all of the dependencies are installed and working with 0.9.10 .

---

### Post by grahammechanical on 2015-09-07
You might find when using apt-get update/upgrade that there is a lot of stuff being held back. It is held back for a reason. And stuff slowly comes down. It noticed this a couple of weeks ago. I got fed up with waiting and ran apt-get dist-upgrade and crossed my fingers. Nothing broke. I am not saying it will not break your system.

I did notice one little thing regarding Network Manager. I can get an Internet connection if I use ethernet or WiFi but not if both types of connection are up. I saw this problem during Vivid development and it went away at the beginning of Wily development but it is now back.

Regards.

---

### Post by sgage on 2015-09-07
I have been getting updates to Wily every day, using Synaptic, without the proposed repos being enabled. I'm using Ubuntu Gnome, so some of the updates are Gnome-specific, but far from all of them.

---

### Post by PaulW2U on 2015-09-07
I must admit I've been a little confused by some of the posts on this thread. I have two laptops running Ubuntu 15.10. Both are receiving updates on an almost daily basis, i.e. very little at weekends.

Today I've received updates re lightdm and cups on both of them. And just to clarify -proposed has **not** been enabled on either laptop.

---

### Post by sgage on 2015-09-07
> **PaulW2U said:**
> I must admit I've been a little confused by some of the posts on this thread. I have two laptops running Ubuntu 15.10. Both are receiving updates on an almost daily basis, i.e. very little at weekends.

Today I've received updates re lightdm and cups on both of them. And just to clarify -proposed has **not** been enabled on either laptop.

I got a bunch of cups updates today, and also gstreamer stuff.

---

### Post by wgarcia on 2015-09-07
Correct, I checked one of the systems where I was not getting upgrades, and I noticed that /etc/cron.daily/apt was not executable. I remembered after the last two posts that this had happened to me in the past also after a distribution upgrade, this file is unmarked as executable. I will review if I had reported an error. After "sudo apt-get update", "sudo apt-get upgrade" I also got a lot of updates, and the partial upgrades I get are the normal ones related to kernel and such.

---

### Post by wgarcia on 2015-09-07
The error report is :
[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/390319](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/390319)

At the end you see that it is said that if the upgrade aborts the /etc/cron.daily/apt file may loose its executable flag. In both systems I mentioned the upgrade aborted because of some problem with the phone related files (modemmanager and other unity8 related things) and I had to finish the upgrade manually. So that may explain it.

---

### Post by ventrical on 2015-09-08
> **PaulW2U said:**
> I must admit I've been a little confused by some of the posts on this thread. I have two laptops running Ubuntu 15.10. Both are receiving updates on an almost daily basis, i.e. very little at weekends.

Today I've received updates re lightdm and cups on both of them. And just to clarify -proposed has **not** been enabled on either laptop.

No proposed here either and I am getting tons of updates daily. I have Ubuntu-Desktop (unity), MATE,ubuntu-gnome, xubuntu, lubuntu, snappy, ubuntu-next .. etc.. all at varying degrees of development across 8 seperate towers with all three different intel/nvidia and ati video hardware. This cycle has been rather uneventful with minimum interruptions and almost zero showstoppers. mac4man found some interesting bugs (synaptic history for one) but I would opine to say that this has been one of the smoothest of the rolling releases since the concepts' inception . Schools back in - expect more development, updates and likewse and I expect that there will be a zero break in the action after the final release of wily into the next release of 'xzany xylaphone' :)

Regards..

---

