---
title: "Cyber Defense student using MacBook Pro 2012 for Linux, MacOs and Windows"
date: 2020-11-16
forum: The Cafe
---

### Post by bigwookiez on 2020-11-16
I have been a "PC" all of my life. I am now a 2nd year student studying in a Cyber Defense program. My old PC laptop was dying so I picked up an older MacBook Pro for school. It has 16 GB of RAM so I can run VirtualBox with no issues. I am learning Linux and realizing how powerful the program can be. Ideally, I would like this laptop to be able to use MacOS, Windows, and Linux. Is running Ubuntu in VirtualBox the best option for this machine or should I look into a dualboot option or running off a USB thumbdrive instead. I mainly want to learn Linux and get familiar with using terminal commands. 

Or should I wipe the old PC laptop and make it a Linux machine only? Its an old Dell that had came with Windows 7 initially, and it did not like running Windows 10 that put on it which caused the issues. The hardware is still good. I am thinking that could make it a Linux server of sorts to try and connect with my Mac and other devices.

I want to be able to learn about connecting all types of devices and be able to troubleshoot the different OS's since this will be required when working in an office setting.

Sorry for the rambling discussion post. I'm going to go back and read other people's posts to keep learning. I appreciate any insight if you have some. Thanks.

---

### Post by DuckHook on 2020-11-16
Welcome to the forums, bigwookiez,

Your questions are very welcome but rather open&#8209;ended.
> **bigwookiez said:**
> I mainly want to learn Linux and get familiar with using terminal commands.
Given that you just want to get your feet wet in the CLI, I assume that you are not intending to use this in a production capacity. More specifically, you won't be using it in a resource&#8209;intensive way that requires access to the bare metal. If this is the case, then it makes sense to run Linux within a VM so that you have the comfort of a known OS as your base. You can then tinker with and explore Linux to your heart's content.

A further considerable advantage to VMs is that you can roll back to a known good snapshot whenever you gum things up. When starting out as a novice, such missteps are likely to happen. All in all, I would highly recommend starting off with Linux installed in a VM.

> &#8230;should I wipe the old PC laptop and make it a Linux machine only? Its an old Dell that had came with Windows 7 initially, and it did not like running Windows 10 that put on it which caused the issues. The hardware is still good. I am thinking that could make it a Linux server of sorts to try and connect with my Mac and other devices.

This is an entirely separate project. It's a worthy learning exercise, but has nothing to do with your main machine or your immediate goal.

I would not recommend embarking upon this project until you have more comfort with Linux under your belt. At that point, learning Linux server admin would stand you in good stead. But don't bite off more than you can chew right away. Even an elephant can eventually be consumed one bite at a time.

> I want to be able to learn about connecting all types of devices and be able to troubleshoot the different OS's since this will be required when working in an office setting.
This is very forward&#8209;thinking of you. Just tackle things one step at a time and you will get there.

> Sorry for the rambling discussion post. I'm going to go back and read other people's posts to keep learning. I appreciate any insight if you have some. Thanks.
Nothing to apologize for. We welcome enthusiastic new users to the fold. It's refreshing actually. However, because this is not really a technical help request, I have moved it to the Cafe. That's the subforum where we hang out to shoot the breeze and discuss non-technical stuff.

I'm sure that others will be happy to chime in and give you their tuppence.

Good Luck and Happy Ubuntu-ing!

---

### Post by EuclideanCoffee on 2020-11-16
I installed Ubuntu on a 2012 Macbook. The batteries swelled. I'm not sure if Linux was the cause, but the PC overheated. This was long before I had several years of Linux experience. I would say, if this is your first year and you're not committed to a deep dive, use a virtual machine. It will save you time as you will likely rebuild your OS. Ubuntu is very stable, but you'll likely want to try new versions and see what Ubuntu has to offer outside of whatever release you use. Best wishes on your education.

Dual booting is not a good use of your time in my opinion. It is prone to error, causing you to rebuild your PC time after time. If that actually sounds appealing to you, you may want to consider dual booting. Haha. Personally it drives me nuts when my stable workstation stops functioning. Stability is very important to me.

---

### Post by mastablasta on 2020-11-18
> **bigwookiez said:**
>  I I mainly want to learn Linux and get familiar with using terminal commands. 


virtualbox is perfect for that. it is easy to use and you can run many server at once. best thing about is is you can take a snapshot, ruin the OS with strange commands and tests and then restore OS to previous state with the snapshot in a couple of seconds.

but in the end, use what works best for you.

---

