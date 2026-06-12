---
title: "share tips on how to make ubuntu 10.10 faster"
date: 2010-11-25
forum: The Cafe
---

### Post by nolag on 2010-11-25
List any ways to speed up ubuntu here. If they have known concequences you can list them too :P. There are only a few I have heard.
 
1) move the tmp folder (or at laest the browser's tmp if you use a lot of RAM or have large tmp files) to RAM
 
cons: uses RAM, if you burn DVDs or sometimes CDs tmp is BIG (browser only does not tend to be too much space)
 
2) Disable unneeded services at boot (helps most with boot, but also can keep system running faster)
 
3) concurrent booting (only helps boot speed not as handy)
con: needs multi-core or hyper-threaded CPU (or multiple CPUs :P)
 
4) if you don't use all of your RAM lower swappiness, if you use a lot of RAM but have less increase swappiness
 
5) increase writeback time
con: powerfailures cause more loss
 
Any other tips that people care to share? They can be for newer computers or older computer, 32-bit or 64-bit, what ever system :D.

---

### Post by madjr on 2010-11-25
a popular way right now.

[http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html](http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html)

---

### Post by NightwishFan on 2010-11-25
Ubuntu no longer has a preemptive kernel (though the generic kernel is perfect for most things). Perhaps compile your own kernel with 1000hz. I have seen nothing to recommend full preemption for a simple desktop/laptop though. The default voluntary works fine for me.

---

### Post by Khakilang on 2010-11-25
My Ubuntu is already fast so I don't have any idea how to make it faster but for Window 7 I might have some idea. Recently I found my brother's computer with Window 7 was getting slow when copying some files. So I just give him some tips like defrag the hard disk, check for virus, clean the registery and blah, blah, blah.

---

### Post by czr114 on 2010-11-25
Among the greatest boosts to Ubuntu speed it is installing the system and ~ on an SSD. While that's not a free tweak, the performance improvement is of such magnitude to be worth a mention. On new builds, if it's possible, find a way to work it into the budget.

The modern-day desktop experience is primarily bottlenecked at the disk.

---

### Post by Shining Arcanine on 2010-11-26
> **nolag said:**
> List any ways to speed up ubuntu here. If they have known concequences you can list them too :P. There are only a few I have heard.
 
1) move the tmp folder (or at laest the browser's tmp if you use a lot of RAM or have large tmp files) to RAM
 
cons: uses RAM, if you burn DVDs or sometimes CDs tmp is BIG (browser only does not tend to be too much space)
 
2) Disable unneeded services at boot (helps most with boot, but also can keep system running faster)
 
3) concurrent booting (only helps boot speed not as handy)
con: needs multi-core or hyper-threaded CPU (or multiple CPUs :P)
 
4) if you don't use all of your RAM lower swappiness, if you use a lot of RAM but have less increase swappiness
 
5) increase writeback time
con: powerfailures cause more loss
 
Any other tips that people care to share? They can be for newer computers or older computer, 32-bit or 64-bit, what ever system :D.
You could rewrite the entire graphics stack, including the desktop environment, according to professional development standards. That would make the GUI faster.

---

### Post by inobe on 2010-11-26
> **nolag said:**
> List any ways to speed up ubuntu here. If they have 
Any other tips that people care to share? They can be for newer computers or older computer, 32-bit or 64-bit, what ever system :D.

i think the response issues are solely related to old hardware, i have an ultra heavy kde environment going snappy with a dual core amd with 4 gigs of ram.

consider a new system.

---

### Post by nolag on 2010-11-26
Thank you all for the replys :D, I will try some of them for sure (when I have some free time) and post my results.  If you come up with more feel free to post them.  If I recall the 200 line thing will be in 11.04, so it may be better to wait since my new kernel would no longer be supported (+ I have never compiled a kernel so I would not want to break it).  I would try the script that can increase preformance by doing the same thing in userland.  From what I have been reading, there are some other folders that can be moved to RAM to increase speed as well (that don't take up too much space). /tmp seems like a bad idea for those who burn dvds since it takes too much space :'(.  
 
> **NightwishFan said:**
> Ubuntu no longer has a preemptive kernel (though the generic kernel is perfect for most things). Perhaps compile your own kernel with 1000hz. I have seen nothing to recommend full preemption for a simple desktop/laptop though. The default voluntary works fine for me.
 
How do you set how often it is preemptive?  Also I read somewhere that the linux new kernel are preemptive?
 
> **Shining Arcanine said:**
> You could rewrite the entire graphics stack, including the desktop environment, according to professional development standards. That would make the GUI faster.
 
I don't know how to do that, but I will look it up.  Just to get me started are we talking about like gnome/kde or kernel stuff that integrates with x?  (Also how large a project are we talking, this sounds like it may be more than I can do :P)
 
> **inobe said:**
> i think the response issues are solely related to old hardware, i have an ultra heavy kde environment going snappy with a dual core amd with 4 gigs of ram.
 
consider a new system.
 
I have no speed issues either (core i7 4 cores 4GB RAM), but there is always a way to make things faster, say dvd ripping/burning, browsers, benchmarks, folding at home, and more.

---

### Post by NightwishFan on 2010-11-26
Well technically I worded that poorly. It is certainly preemptive, just you might see more responsiveness (less speed on full preemption and 1000hz) and sorry it requires a kernel build. If I think of anything for you I will bump this thread.

For most machines if you want to avoid touching the disk set swappiness to 20.
```
sudo nano /etc/sysctl.conf
```

Add this to the bottom of the file, and then press ctrl+X to save:
```
vm.swappiness = 20
```

---

### Post by nolag on 2010-11-26
> **NightwishFan said:**
> Well technically I worded that poorly. It is certainly preemptive, just you might see more responsiveness (less speed on full preemption and 1000hz) and sorry it requires a kernel build. If I think of anything for you I will bump this thread.
 
For most machines if you want to avoid touching the disk set swappiness to 20.
```
sudo nano /etc/sysctl.conf
```
 
Add this to the bottom of the file, and then press ctrl+X to save:
```
vm.swappiness = 20
```
 
lol yeah, I was thinking of setting it to 10 (well 0 for me, I have no swap space :D) but 10 on a default disk).
 
Also I am just curious, do you know what the speed is now or where that would be found in the kernel?

---

### Post by NightwishFan on 2010-11-26
```
32-bit 250hz
64-bit 100hz
```

Though I am kind of rambling this really is not a solution. Try installing the package preload, it will load files into memory for faster program starting.

---

### Post by nolag on 2010-11-26
> **NightwishFan said:**
> ```
32-bit 250hz
64-bit 100hz
```
 
Though I am kind of rambling this really is not a solution. Try installing the package preload, it will load files into memory for faster program starting.
 
I was thinking if one increases the rate for preempitveness, then won't there be more system interupts, thus slowing down the actuall running times, but speeding up responsiveness?
 
I have heard mixed reviews about preload.  Some of people say it makes it faster (I understand why), but some people are saying it slows it down a lot.  A lot of people also say they see no difference.  I should look for benchmarks to compare later (or make my own).

---

### Post by NightwishFan on 2010-11-26
Preload seems to help, though to be honest if your applications already start fast there is little need. As for 1000hz and etc.. It is recommended in the kernel documentation but though it wont be magic. Ubuntu has it's kernel set up well for most situations.

---

### Post by jlparsons on 2011-02-26
2nd for preload.  Slows down boot but makes apps start quicker.  On the other hand once you've loaded a program once I believe it'll normally stay in ram until forced out by high memory demand anyway so it'll start like lightening next time until you reboot anyway.  Some argue preload does little, but I like it!

---

### Post by K.Mandla on 2011-02-26
This is very much out of date, but some of it will still apply.

[http://kmandla.wordpress.com/projects/set-up-ubuntu-for-speed/](http://kmandla.wordpress.com/projects/set-up-ubuntu-for-speed/)

---

### Post by ggallozz on 2011-05-21
> **Khakilang said:**
> .....my brother's computer with Window 7 was getting slow when copying some files. So I just give him some tips .....

...and finally switch to Ubuntu !

:-D

---

### Post by ggallozz on 2011-05-21
> **nolag said:**
> List any ways to speed up ubuntu here. ..........

Thank you for the *tips* but the *how to* lacks a lot ....

Sorry, but I'm not yet so geek as you should, so a step by step tutorial will only be useful for me.

---

### Post by skabople on 2011-09-28
> **czr114 said:**
> Among the greatest boosts to Ubuntu speed it is installing the system and ~ on an SSD. While that's not a free tweak, the performance improvement is of such magnitude to be worth a mention. On new builds, if it's possible, find a way to work it into the budget.

The modern-day desktop experience is primarily bottlenecked at the disk.

I do agree on using an Solid State Drive for a Linux system of any sorts. I would like to add that just putting your Linux on an SSD isn't the best thing to do but not exactly the wrong thing to do either. If you do put an SSD on a Linux system then I would strongly recommend reading the ArchWiki's on what they have to say. 

I would also recommend this article for regular platter drives as well... 

[https://wiki.archlinux.org/index.php/SSD](https://wiki.archlinux.org/index.php/SSD)

~Linux All The Way... FTW~

---

