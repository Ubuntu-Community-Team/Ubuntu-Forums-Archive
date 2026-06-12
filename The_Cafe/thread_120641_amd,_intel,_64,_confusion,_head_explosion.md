---
title: "amd, intel, 64, confusion, head explosion"
date: 2006-01-23
forum: The Cafe
---

### Post by towsonu2003 on 2006-01-23
for all my life, i used intel... and learning about a new processor (architecture??) is not like learning to use a new browser...

as the title shows, I'm confused to death. There is this intel thingy (pentium, celeron, whatever), and there is this amd 64 thingy (athlon? don't know)... from intel, I understand a machine like this: [http://www.shopping.hp.com/webapp/shopping/generic_subcategory.do?storeName=computer_store&landing=computers&category=notebooks/hp_pavilion/zd8000_series&subcat1=rts&catLevel=3](http://www.shopping.hp.com/webapp/shopping/generic_subcategory.do?storeName=computer_store&landing=computers&category=notebooks/hp_pavilion/zd8000_series&subcat1=rts&catLevel=3)
for amd64, I understand a machine like this: [http://www.shopping.hp.com/webapp/shopping/product_detail.do?storeName=computer_store&landing=computers&category=notebooks/hp_pavilion/dv8000z_series&subcat1=rts&catLevel=3&product_code=EP407UA%23ABA](http://www.shopping.hp.com/webapp/shopping/product_detail.do?storeName=computer_store&landing=computers&category=notebooks/hp_pavilion/dv8000z_series&subcat1=rts&catLevel=3&product_code=EP407UA%23ABA)

it seems for intel, there is the x86 kernel, and for amd 64, there is the amd 64 kernel. here are my numerous questions:

1. can you run amd64 computer with x86 kernel? 
1.a. if you can, does the x86 kernel slows it down too much?
2. can software compiled for x86 run in amd64? 
2.a. if I download, let's say, firefox, does it make a difference whether I have intel or amd64?
2.b.do the 3 kernels use different repositories in ubuntu for packages?
3. do amd64 users encounter specific problems bc they don't use intel? (as in, I use firefox, so can't get into IE-only sites kinda)
4. are there specific problems amd64 kernel users bc their kernel isn't x86?
5. is there a nice almost objective place to learn about the differences btw intel & amd64? all sites I've found are either amd-fans or too-technical... I'm a true newbie to this complicated processor (and architecture??) thingy.

---

### Post by bloodborne on 2006-01-23
AMD64 is a 64 bit chip that can run 32 bit, x86 instrucitons. That means that you can run the same x86 software on an AMD64 as on an Intel Pentium 4 or whatever. However, since it is 64 bit, you can run native 64 bit apps and os's on it. As for Ubuntu, AMD64 is perfectly capable of running both the x86 and AMD64 versions, howerer, you will see higher performance in the 64 bit environment due to the larger strings of data that the chip can process at once and the more memory it is capable of accessing.

---

### Post by BSDFreak on 2006-01-23
[quote=towsonu2003]for all my life, i used intel... and learning about a new processor (architecture??) is not like learning to use a new browser...

as the title shows, I'm confused to death. There is this intel thingy (pentium, celeron, whatever), and there is this amd 64 thingy (athlon? don't know)... from intel, I understand a machine like this: [http://www.shopping.hp.com/webapp/shopping/generic_subcategory.do?storeName=computer_store&landing=computers&category=notebooks/hp_pavilion/zd8000_series&subcat1=rts&catLevel=3]("http://www.shopping.hp.com/webapp/shopping/generic_subcategory.do?storeName=computer_store&landing=computers&category=notebooks/hp_pavilion/zd8000_series&subcat1=rts&catLevel=3")
for amd64, I understand a machine like this: [http://www.shopping.hp.com/webapp/shopping/product_detail.do?storeName=computer_store&landing=computers&category=notebooks/hp_pavilion/dv8000z_series&subcat1=rts&catLevel=3&product_code=EP407UA%23ABA]("http://www.shopping.hp.com/webapp/shopping/product_detail.do?storeName=computer_store&landing=computers&category=notebooks/hp_pavilion/dv8000z_series&subcat1=rts&catLevel=3&product_code=EP407UA%23ABA")

it seems for intel, there is the x86 kernel, and for amd 64, there is the amd 64 kernel. here are my numerous questions:

1. can you run amd64 computer with x86 kernel? 
1.a. if you can, does the x86 kernel slows it down too much?
2. can software compiled for x86 run in amd64? 
2.a. if I download, let's say, firefox, does it make a difference whether I have intel or amd64?
2.b.do the 3 kernels use different repositories in ubuntu for packages?
3. do amd64 users encounter specific problems bc they don't use intel? (as in, I use firefox, so can't get into IE-only sites kinda)
4. are there specific problems amd64 kernel users bc their kernel isn't x86?
5. is there a nice almost objective place to learn about the differences btw intel & amd64? all sites I've found are either amd-fans or too-technical... I'm a true newbie to this complicated processor (and architecture??) thingy. 

PS. Forum busy **again**, hopefully I'm not submitting this more than once.[/quote]

AMD64 is an x86 CPU with 64 bit extensions.

1. Yes
1a. No, it will run with no slowdown what so ever, it's an x86 CPU.
2. Yes
2a. Depends on which version of Firefox you download, the one compiled for IA32 will run on either, the one compiled for AMD64 will only run on AMD64.
2b. I don't know but any kernel compiled for the Intel 32 bit arch (i386-i686) or AMD 32 (K7) or AMD 64 (K8) will run just fine on an AMD64 CPU.
3. No, generally not, you will be able to run any program compiled for i386-686 or AMD64 on the box but you can't mix 32 bit plugins with 64 bit programs (IE, you can't use 32 bit flash plugin on a 64 bit firefox).
4. No, because it is still as much x86 arch as the P4 is.
5. Most i have seen are very objective, Anandtech has had some good articles on it though, i'd search their article database for it if i were you.

---

### Post by CompShrink on 2006-01-27
I actually started looking into this recently. When you are saying Intel, do you mean 32 bit intel, or 64 bit? Both Intel and AMD have 64 bit systems, and they are very similar (because Intel ripped off AMD and just tweaked a few things).

Intel 64 and AMD 64 aren't 100% compatable, however.

I think most of your questions were well answered above, but I will add this:

I haven't seen any talk of support for Intel 64. You can run the standard 32 bit kernels on it, afaik, but the Ubuntu 64bit kernel is made for AMD64, and probably won't work... but again I've actually not read anything on Intel 64 and Ubuntu, because I haven't seen any...

And as for 4, I'm sorry but I have to disagree with BSDFreak. I have read quite a lot on this forum about how you have to do chroot and other tricks to get 32 bit compiled programs to run if you are using the AMD64 kernel. Yes, there are ways to run every 32 bit program while still running in 64 bit mode, but it sounds like some people are annoyed by the added effort.

You can run the 32 bit kernel on it if you want, and it will still run fast.

---

### Post by poofyhairguy on 2006-01-27
[QUOTE=towsonu2003]
1. can you run amd64 computer with x86 kernel? 
1.a. if you can, does the x86 kernel slows it down too much?
2. can software compiled for x86 run in amd64? [/QUOTE]

I am doing that now and it runs great. 64 bit Ubuntu is kinda hard to use for some.

For more information, the best place to look for this stuff is wikipedia:

[http://en.wikipedia.org/wiki/AMD64](http://en.wikipedia.org/wiki/AMD64)

---

### Post by mstlyevil on 2006-01-27
Intel's current Pentium 4 cpu's use AMD64 instruction sets also. AMD and Intel have a cross licensing agreement that they can use the others new technology on future chips. Intel just renamed the instruction set to EMT64 but it is exactly the same as AMD's. Intel did not rip it off of AMD, they adopted it because it had already become the standard used by Microsoft and consumers. As far as I know, if you get a P4 with EMT64, you can use the AMD64 kernel. If you do not have the need for larger amouts of memory, (More than 4 GB) I would suggest you use the k7 kernel for AMD or the i686 kernel for intel. The reason is that there are still a lot of gaps in software and drivers for the 64bit kernel. AMD is superior and faster than Intel right noe because the memory controler is on die with the cpu allowing the memory to be utilized at it's full bandwith in both directions. Intels memory controller is still on the mobo limiting trafic to one direction at a time and causing a bottlekneck of traffic back and forth between the controler and the CPU. Also the shorter pipelines cause the CPU on AMD to utilze less energy and they produce less heat. These are thse big differences.

---

### Post by towsonu2003 on 2006-01-27
thanks for the answers. it started to make some sense :) I looked at the wiki, even that was too techy for me :)

[QUOTE=CompShrink]When you are saying Intel, do you mean 32 bit intel, or 64 bit? [/QUOTE]
I meant the 32 bit intel, the basic stuff you get when you buy a computer (that's not amd). 

also, let me add another question here: which one would you prefer (32 bit intel, or 64 bit amd) in your linux system? just from your experience (and from a prospective computer buyer's perspective).

---

### Post by bloodborne on 2006-01-27
I have a AMD64 dual core in my main desktop and I'd love to load it up with the AMD64 version of Ubuntu. I know that there is some software incompatabilities and such with the 64-bit version, but I'm not planning on doing anything high end like web or software development.

I guess it all comes down to what you want to do. If there is one must-have app, load up the LiveCD and try it out in the 64-bit environment, or try to get someone else's opinion.

---

### Post by poofyhairguy on 2006-01-27
[QUOTE=towsonu2003]
also, let me add another question here: which one would you prefer (32 bit intel, or 64 bit amd) in your linux system? just from your experience (and from a prospective computer buyer's perspective).[/QUOTE]


Easy because I just did across the board upgrades recently.

For desktops its better to get a 64 bit (dual core if you can) AMD system. Intel isn't worth looking at on desktops.

For laptops you want a 32 bit Intel chip. The Pentium M is awesome.

---

### Post by endersshadow on 2006-01-27
[QUOTE=poofyhairguy]Easy because I just did across the board upgrades recently.

For desktops its better to get a 64 bit (dual core if you can) AMD system. Intel isn't worth looking at on desktops.

For laptops you want a 32 bit Intel chip. The Pentium M is awesome.[/QUOTE]

Depends on the lappy you want, though.  I've got a P4 w/ HTT...but I'd LOVE to have an AMD Sempron system...my buddy's brother just bought him one...it flies...

<3 AMD.

---

### Post by mstlyevil on 2006-01-27
[QUOTE=towsonu2003]thanks for the answers. it started to make some sense :) I looked at the wiki, even that was too techy for me :)


I meant the 32 bit intel, the basic stuff you get when you buy a computer (that's not amd). 

also, let me add another question here: which one would you prefer (32 bit intel, or 64 bit amd) in your linux system? just from your experience (and from a prospective computer buyer's perspective).[/QUOTE]

I am not sure if you can still buy a 32 bit desktop P4 unless it is a outdated system. I would have to say if you want a desktop go with AMD 64. If you want a notebook replacement for your desktop and you will not be traveling with it all the time then go for a AMD 64 laptop. If you travel a lot and need long battery life yet great performance, go with a new Intel Single or Duo mobile processor. If you need a laptop on a buget then you could still get a regular Pentium M laptop probally for much cheaper than the new single or Duo CPU's. Pentium M's and the new Duo and Single mobile processors are the best CPU's Intel makes right now and they are slightly better overall than AMD's mobile processors.

---

