---
title: "Best Linux OS for a portable USB drive"
date: 2016-11-18
forum: Ubuntu/Debian BASED
---

### Post by laggger164 on 2016-11-18
I made a bootable Ubuntu USB stick (32GB) with an encrypted home folder. I really like it as I am using it right now on my main PC just to get used to it.
But problems popped up when using a different PC, which is what I meant to use it for.

Before I go into detail, I know many of you dont have the time to read all the things: I need an OS suitable to game lightly (Modded minecraft, Light steam games), usable for web browsing, text editing, programming, other not really demanding work and storing my files on an encrypted partition or a /home folder, while being portable to any classic computer.

So here is what happened in detail:

My brother has an AMD GPU inside of his laptop, he was trying to run Modded Minecraft on his Kali distro, he couldnt do it, so he tried my Ubuntu stick. It worked there!
Then he gave the USB stick back to me and when I plugged it into my main PC it wouldnt start up. I dont know if he was installing any drivers on his laptop, I gotta ask him about that. I looked into the log file which Ubuntu graciously provided me with and saw that there was the word RADEON at the end of the log many times, I am guessing that (EE) meant error.

Since I have an old AMD GPU in my system (HD7750) AND a new Nvidia GTX 960 because I was running 2 something like Linus from LinusTechTips did - 2 Gamers 1 CPU. I had 2 GPUs for that. I thought that one was causing the problem. And it was. I removed it. Booted into Ubuntu no problem, it uploaded the log to the developers (although I highly doubt they will know what actually happened), shut it down, inserted the HD7750 back in where it was and it booted just fine.

Since I have only done this once, I will do more testing before going to another OS or doing some other major changes that you provide me with. (hopefully)

---

### Post by sudodus on 2016-11-18
***Backup*** is always important, particularly for systems in USB drives and encrypted systems.

You are doing quite well with Ubuntu :-)

But if you want to run your system in older computers too, you can consider a community flavour with a lighter desktop environment, *Lubuntu*, *Ubuntu MATE* or *Xubuntu*. Feel free to try some of the major linux distros, that you find at [http://distrowatch.com/](http://distrowatch.com/). There might be problems to get support for minor distros.

You can get some tips from this link (and links from it),

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by laggger164 on 2016-11-18
> **sudodus said:**
> ***Backup*** is always important, particularly for systems in USB drives and encrypted systems.

You are doing quite well with Ubuntu :-)

But if you want to run your system in older computers too, you can consider a community flavour with a lighter desktop environment, *Lubuntu*, *Ubuntu MATE* or *Xubuntu*. Feel free to try some of the major linux distros, that you find at [http://distrowatch.com/](http://distrowatch.com/). There might be problems to get support for minor distros.

You can get some tips from this link (and links from it),

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("https://ubuntuforums.org/showthread.php?t=2230389")
Thank you so much for the reply!

Wow... there are a LOT more distros than I thought...

I knew there were lots of them, but I havent even imagined THAT many would exist. And I am guessing the number of them is only rising. Holy cow.

So those lighter versions of Linux would run better on weaker hardware. Which makes sense. But I am mostly talking about driver support.
Are there any Linux distros that have an advantage in native driver support? Or just driver support in general?

I know that I should google it. And I did, but I cannot figure out how to search for it. And there is no way I am going over every Linux distro trying them out. Even the major ones.
If there are none that you can think of, then I will either stick to Ubuntu or find another distribution and play with that.

---

### Post by sudodus on 2016-11-18
There are some differences, but most modern distros have the same linux kernel series, and with them the same drivers. The methods to install proprietary drivers for graphics, wifi, printer etc might vary, as well as the policy to provide closed source code.

I think the Ubuntu family (standard Ubuntu and the community flavours) is one of the best to support drivers and to be user friendly.

If you have problems with some driver, you can come back and ask specifically about that problem.

-o-

Try the other linux distros at or near the top of the list. You can create live-only USB boot drives quite easily with the cloning method, because these distros provide hybrid iso files (that work as cloned both from DVD and USB (and memory card, if the computer can boot from cards). You can install [mkusb](https://help.ubuntu.com/community/mkusb) into Ubuntu and use it to create these USB boot drives (easy and safe). Of course you can re-use the same pendrive and try the linux distros one after another.

---

### Post by C.S.Cameron on 2016-11-19
Puppy Tahr is worth looking at, it was made from the start to run off CD's and Flash drives.
Runs in RAM, is only 200MB and is based on Ubuntu, (14.04). fast as lightning and very light.

---

### Post by laggger164 on 2016-11-21
> **sudodus said:**
> There are some differences, but most modern distros have the same linux kernel series, and with them the same drivers. The methods to install proprietary drivers for graphics, wifi, printer etc might vary, as well as the policy to provide closed source code.

I think the Ubuntu family (standard Ubuntu and the community flavours) is one of the best to support drivers and to be user friendly.

If you have problems with some driver, you can come back and ask specifically about that problem.

-o-

Try the other linux distros at or near the top of the list. You can create live-only USB boot drives quite easily with the cloning method, because these distros provide hybrid iso files (that work as cloned both from DVD and USB (and memory card, if the computer can boot from cards). You can install [mkusb](https://help.ubuntu.com/community/mkusb) into Ubuntu and use it to create these USB boot drives (easy and safe). Of course you can re-use the same pendrive and try the linux distros one after another.

> **C.S.Cameron said:**
> Puppy Tahr is worth looking at, it was made from the start to run off CD's and Flash drives.
Runs in RAM, is only 200MB and is based on Ubuntu, (14.04). fast as lightning and very light.

So I have installed Xubuntu after trying it and Kubuntu in a VM (Virtualbox FTW!) 

Xubuntu is supposed to have good driver support, it is lighter on the system and comes with XCFE (or however it is spelled) desktop layout.

I have modified it to my liking, now just to install all the things that I want.

Puppy Linux doesn't seem bad, but also doesn't seem like a good option for me. It isn't that pretty or feature packed as Ubuntu and derivatives (which might be the point of that OS though) and I couldn't find any information about making it persistent. Live CDs are on almost all Linux distros...

---

### Post by sudodus on 2016-11-21
Are you happy with what you have now (Xubuntu and Kubuntu), or do you want help to make Puppy persistent?

If you feel that the problem of your first post is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

If you have some other problem or question, it is better to create a new thread with a good descriptive title and more details in the first post. That way you will get the attention of people who are interested in that problem, and who can give good advice.

---

### Post by C.S.Cameron on 2016-11-21
Puppy has an option to automatically add persistence the first time you shut down.
 There is no limit to persistence size other than disc size, you can even specify that persistence be stored on your internal hard drive or second USB.

Puppy does not use a casper-rw file like Ubuntu does so you can make a dual boot flash drive and have both O/S's persistent.

I think Puppy comes with at least as many aps as Ubuntu, but you are right they are mostly light aps like Abiword rather than Write and a much lighter browser, (Firefox is getting a little bloated). 

If you worry about wearing out your pendrive with too many writes, (I don't), note that Puppy only writes to disk at the end of a session or when asked.

It also comes with a built in remaster system so you can add and remove aps and then make a custom bootable iso.

---

