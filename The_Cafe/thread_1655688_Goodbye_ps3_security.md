---
title: "Goodbye ps3 security"
date: 2010-12-30
forum: The Cafe
---

### Post by orlox on 2010-12-30
[http://www.engadget.com/2010/12/29/hackers-obtain-ps3-private-cryptography-key-due-to-epic-programm/](http://www.engadget.com/2010/12/29/hackers-obtain-ps3-private-cryptography-key-due-to-epic-programm/)

Seems we will be seeing linux back again on the ps3, and this time not only on fat models with old firmwares, and not with a hypervisor restricting access to the GPU :D

yay homebrew also!

---

### Post by asifnaz on 2010-12-30
> **orlox said:**
> [http://www.engadget.com/2010/12/29/hackers-obtain-ps3-private-cryptography-key-due-to-epic-programm/](http://www.engadget.com/2010/12/29/hackers-obtain-ps3-private-cryptography-key-due-to-epic-programm/)

Seems we will be seeing linux back again on the ps3, and this time not only on fat models with old firmwares, and not with a hypervisor restricting access to the GPU :D

yay homebrew also!

I ll love to use Linux and hombrew on my ps3 but they just presented a theory not proof

---

### Post by orlox on 2010-12-30
> **asifnaz said:**
> I ll love to use Linux and hombrew on my ps3 but they just presented a theory not proof

They say it's not a theory, and that they would run a demo tomorrow. Wouldn't think they lie with such short time to make it true.

---

### Post by handy on 2010-12-30
I look forward to seeing what tomorrow brings.

Don't Sony just have to truly generate something akin to a random number to seed their cryptography to solve this problem?

---

### Post by orlox on 2010-12-30
> **handy said:**
> I look forward to seeing what tomorrow brings.

Don't Sony just have to truly generate something akin to a random number to seed their cryptography to solve this problem?

Don't really know much about cryptography, but from what I have seen so far, the fact that the random number generator was actually constant allowed them to find out how to create valid keys for applications. The (supposedly) random number generator does not live in the ps3, its used by sony to create keys to authenticate applications.

So basically, sony can't do a thing without screwing up all older applications, since we could create signed applications that will seem as legal (legal in the sony way) as anything downloaded from the psn. Unless they make a giant whitelist for all accepted applications, but even that seems useless, since they seem to have got complete access to the ps3, which would allow to easily remove or modify any kind of whitelist.

---

### Post by handy on 2010-12-30
I expect that Sony will quite quickly nullify this security breach by changing the way they create their encryption & if it must be so clumsy, then they will create a white list. Though I expect they employ brains big enough to streamline the process beyond that.

It will be interesting to see if this lot comes to anything.

---

### Post by MisterGaribaldi on 2010-12-30
And, in other news, my PC runs Ubuntu perfectly. :p

---

### Post by asifnaz on 2010-12-30
If this is true it can't be fixed. Patching this by changing the private key would require a change in the hardware which would also nullify any existing software and game released since the PS3's launch. If Sony were to do that, they'd screw over every person that owns a PS3 as the existing private key would be useless on a new console.

Sony really screwed up. Now there will be apps for cheating in every single online game. Not to mention that it blows the door open for piracy.

Can't wait for the homebrew to start coming out.

---

### Post by handy on 2010-12-30
> **MisterGaribaldi said:**
> And, in other news, my PC runs Ubuntu perfectly. :p

You are obviously not a gamer that requires more than GNU/Linux distros or the same running Wine can handle.

> **asifnaz said:**
> If this is true it can't be fixed. Patching this by changing the private key would require a change in the hardware which would also nullify any existing software and game released since the PS3's launch. If Sony were to do that, they'd screw over every person that owns a PS3 as the existing private key would be useless on a new console.

Sony really screwed up. Now there will be apps for cheating in every single online game. Not to mention that it blows the door open for piracy.

Can't wait for the homebrew to start coming out.

Perhaps you are right? 

Though I still tend to think that Sony will find a way to plug the hole. Perhaps they will only be able to plug it for future games in their worst case scenario.

Personally, I hope that they can't plug the hole it is just that I expect that with the resources at their disposal they will find a way that we haven't thought of.

It will be interesting to see if all of a sudden (at last) there will become pirate copies of PS3 games available on the net.

---

### Post by orlox on 2010-12-30
Torrents have been around for a while now. For some months now it has been possible to dump games and run copies from the hdd, enabling also running pirate (harharhar) copies. I bought one of these dongles to run my games from the hdd, got some very appreciable boosts in loading times, but without online gaming it wasn't worth it.

Hopefully now I can return to that, without having to waste a usb port of my slim in a dongle :D.

---

### Post by handy on 2010-12-30
> **orlox said:**
> Torrents have been around for a while now. For some months now it has been possible to dump games and run copies from the hdd, enabling also running pirate (harharhar) copies. I bought one of these dongles to run my games from the hdd, got some very appreciable boosts in loading times, but without online gaming it wasn't worth it.

Hopefully now I can return to that, without having to waste a usb port of my slim in a dongle :D.

Thanks, good to hear. (Be careful here on the topic though.)

I have a USB cable going from my PS3 to my Samsung SyncMaster 2443 monitor, which gives me 2 USB ports on my desktop. If nothing else it makes it more convenient to have the PS3 away from my desk. :)

Have you tried using a USB hub?

---

### Post by asifnaz on 2010-12-30
> **orlox said:**
> Torrents have been around for a while now. For some months now it has been possible to dump games and run copies from the hdd, enabling also running pirate (harharhar) copies. I bought one of these dongles to run my games from the hdd, got some very appreciable boosts in loading times, but without online gaming it wasn't worth it.

Hopefully now I can return to that, without having to waste a usb port of my slim in a dongle :D.

If you are talking about psjailbreak or psdowngrade they are patched by sony . so , nomore work

---

### Post by Dr. C on 2010-12-30
Well here it is GNU / Linux running on the PS3 **slim** [http://www.youtube.com/watch?v=lGI0EnNQ5GE]("http://www.youtube.com/watch?v=lGI0EnNQ5GE").

---

### Post by handy on 2010-12-30
I wonder who's head will roll at Sony corp. for this?

---

### Post by mips on 2011-01-04
> **asifnaz said:**
> If you are talking about psjailbreak or psdowngrade they are patched by sony . so , nomore work

With the encryption keys out in the wild who cares. This is x100 better and opens up way more possibilities like using a file system that supports sizes bigger than 4GB, playing MKV movies, running games off your HDD, running any emulator you want to play old games.

There is nothing Sony can do about this, patches or firmware updates won't work as it will affect every single ps3 out there. The keys are store in hardware. The only thing they can do is make changes in future manufactured consoles but that could cause issues with backward compatibility, your old ps3 games will no longer work.

And it's not like the system was hacked either, the keys were presented in memory. So just like AACS and CSS etc it shows you the more DRM you try and apply the more people are going to want to eliminate it.

Wonder what Sony is going to have to say about this :D

---

### Post by asifnaz on 2011-01-04
If Sony haven't bothered removing the OtherOS in the first place, this  wouldn't have happened. Now, there's not a damn thing that they could do  about it. It also screws up the chance for PS3 BC in PS4.

---

### Post by handy on 2011-01-04
"BC" meaning backward compatibility I take it?

---

### Post by mips on 2011-01-04
> **handy said:**
> "BC" meaning backward compatibility I take it?

Yip. Even if they modified new production PS3s it would create problems with previously modified games. So the same would hold true for a PS4 wanting PS3 BC. Essentially they screwed themselves over with their own security scheme :biggrin:

Unless it's possible to run dual keys for old and new stuff?

---

### Post by handy on 2011-01-04
> **mips said:**
> Yip. Even if they modified new production PS3s it would create problems with previously modified games. So the same would hold true for a PS4 wanting PS3 BC. Essentially they screwed themselves over with their own security scheme :biggrin:

Unless it's possible to run dual keys for old and new stuff?

They really have had their software locked up big time for the PS3 all along.

The ability for users to use Linux on the skinny PS3 is going to open up previously closed possibilities, which is great.

It will be interesting to see the implications of this breakthrough in the coming months.

---

### Post by asifnaz on 2011-01-04
> **handy said:**
> They really have had their software locked up big time for the PS3 all along.

The ability for users to use Linux on the skinny PS3 is going to open up previously closed possibilities, which is great.

It will be interesting to see the implications of this breakthrough in the coming months.

Hopefully Playstation franchise is not killed in the cross-fire

---

### Post by mips on 2011-01-05
[http://psx-scene.com/forums/f6/psp-now-also-open-console-developers-74290/](http://psx-scene.com/forums/f6/psp-now-also-open-console-developers-74290/)

The PSP keys were found in the PS3, obviously for inter action between the devices.

So now the PSP is also wide open.

---

