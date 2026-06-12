---
title: "Am I doomed to run Ubuntu 7.10 forever?"
date: 2008-07-18
forum: The Cafe
---

### Post by Exershio on 2008-07-18
The problem is my ATI Radeon 9550 AGP video card. Remember back in 7.10, before FGLRX was supported in the FGLRX drivers? Well, my video card refuses to play nice with any drivers compatible with Ubuntu 8.04. I thought I'd be slick and download the old ATI drivers and install them manually in 8.04, but guess what? They don't work with the new Linux kernel.

With the newer ATI drivers (catalyst 7.11 and newer), my video is just plain choppy and unbearable with any OpenGL application that does 3d rendering.

So, I'm back to Ubuntu 7.10. It's nice having working 3d so I can play a few games, but I'm also doomed to run out of date software.

Though, if I look at it this way, I don't have many options:
1) Run Ubuntu 7.10. Everything works good, though the software is old.
2) Run Ubuntu 8.04. Newer software (yay), but can't play 3d games (boo)
3) Run Windows Vista. Video card drivers simply stop responding and crash anytime I play a 3d games.
4) Run Windows XP. Old stable OS, new programs, working games, but isn't exciting. I can't tweak it anymore, nothing new to really learn. It's not Linux, and I'm just plain bored with it.

Is there any other options for me? I just want new up to date software with the old ATI drivers, but it seems everything is just incompatible with each other.

I was thinking of installing Arch Linux (I love that distro), and taking on the adventurous task of compiling an older kernel, installing old ATI drivers, and then installing all new software. Could that work?

I just can't wait until ATI finally releases drivers that work for everybody. Then I won't have a problem. :D

Ah, who knows. If you all have any input or suggestions, please let me know. I'd appreciate it greatly. :)

---

### Post by zmjjmz on 2008-07-18
> **Exershio said:**
> The problem is my ATI Radeon 9550 AGP video card. [...]
Ah, who knows. If you all have any input or suggestions, please let me know. I'd appreciate it greatly. :)

Wait until Ubuntu 8.10?

---

### Post by loell on 2008-07-18
or wait till 9.04? :biggrin:

gutsy updates would have stop some time in that release.

---

### Post by SunnyRabbiera on 2008-07-18
Try other distributions, like mandriva, linux mint, Mepis...never know what might work.

---

### Post by Lster on 2008-07-18
[QUOTE=Exershio]Try other distributions, like mandriva, linux mint, Mepis...never know what might work.[/QUOTE]

+1. You can always come back to Ubuntu. Perhaps OpenSUSE?

---

### Post by Miguel on 2008-07-18
I'm not sure I get your problem. I fear the OSS driver doesn't cut it for you, does it? Because latest radeon GIT is wonderful with EXA and doesn't have any kind of video tearing. It's also pretty stable but... don't expect any decent 3D performance until Gallium comes and the mesa driver gets any kind of memory manager.

You can also try the latest fglrx in Ubuntu Gutsy (the ubuntu I hate the most) before upgrading to hardy, just remember to blacklist fglrx in /etc/default/linux-restricted-modules-common (this will disable the repository version).

In any case, what you want to do for Arch Linux should work, and should also work for Ubuntu. The bad bad thing is that you would have to keep track of security vulnerabilities by yourself, and then patch them yourself, and then recompile your kernel again. Or forget security updates. What the heck! You could also run the gutsy kernel within hardy and, if you keep the gutsy repositories, you would still get security updates for the kernel until April 2009,

---

### Post by PrimoTurbo on 2008-07-18
Try arch linux.

---

### Post by Yannick Le Saint kyncani on 2008-07-18
> **zmjjmz said:**
> Wait until Ubuntu 8.10?

Yeah, ubuntu getting a new release out every six months, you don't have too much an out-of-date system if you skip one version (maybe two even).

Look, the next version is only three months ahead :)
Now, Windows XP was out in October 2001, vista in January 2007.

---

### Post by Exershio on 2008-07-18
The only problem with waiting is I don't know if ATI will ever fix their drivers, and currently none of the new drivers work with my card. That is why I need to use an old Ubuntu. I need an old Linux kernel that works with the old ATI drivers.

If I try to install the old ATI drivers on the current linux kernel version, it says failed to install because the kernel is not supported.

---

### Post by gn2 on 2008-07-18
Why not just buy a cheap Nvidia card?

In the UK you can get one for under £20.

---

### Post by Exershio on 2008-07-18
buying a new video card is out of the question. my current power supply is 175w. I'm surprised my current video card is working fine with this computer. Any other video card would probably just not work on such a lower power supply.

And if I want to upgrade my power supply, I'd need a new motherboard and a new case, because guess what? My power supply only has 14 PINS! it's an odd one alright.

But yeah, as you can see, new video card is pretty much out of the question.

---

### Post by gn2 on 2008-07-18
> **Exershio said:**
> buying a new video card is out of the question. my current power supply is 175w. 

A similar Nvidia card will be fine.
e.g: [http://www.ebuyer.com/product/119723](http://www.ebuyer.com/product/119723)

---

### Post by Daveski on 2008-07-18
> **Exershio said:**
> I'm surprised my current video card is working fine with this computer. 

Well clearly it isn't.

---

### Post by Exershio on 2008-07-18
> **Daveski said:**
> Well clearly it isn't.
It works very well in Windows XP, so clearly my computer and video card work fine together.

It's my video card and Linux that don't work fine.

---

### Post by RiceMonster on 2008-07-18
#include<stdio.h>

int main (void) {
  while (1) {
    printf("Try some more Linux distributions. "); 
  }
}

---

### Post by bruce89 on 2008-07-18
> **RiceMonster said:**
> #include<stdio.h>

int main (void) {
  while (1) {
    printf("Try some more Linux distributions. "); 
  }
}

You forgot to return 0.

---

### Post by RiceMonster on 2008-07-18
Aww! how could I forget that! Regardless, the program should still compile and run.

---

### Post by loell on 2008-07-18
> **RiceMonster said:**
>  Regardless, the program should still compile and run.
heheh

bad, bad C  practices [-(

---

### Post by PrimoTurbo on 2008-07-18
Get a new power supply, you can get a generic 450W for $20 USD. Get a nvidia card for $50.

---

### Post by bruce89 on 2008-07-18
> **loell said:**
> heheh

bad, bad C  practices [-(

Don't get me started on the braces.

---

### Post by RiceMonster on 2008-07-18
I assume you wanted me to indent, which got unformated when I posted it, and that you wanted me to put the braces like this:

int main (void) 
{

etc.

---

### Post by Exershio on 2008-07-18
I don't mean to be rude, but you guys are going way off topic. And a lot of you aren't even reading what I'm typing.

I can't just go out and get a 450w power supply because I have yet to find a dealer that sells 14 pin power supplies. It's always 20 pin or 24 pin.

---

### Post by JT9161 on 2008-07-19
Id say this gives you  a reason to try some other distros.

---

### Post by zachtib on 2008-07-19
*have* you tried the radeon driver? it worked great on my Radeon 9000...

---

### Post by Daveski on 2008-07-20
> **Exershio said:**
> It works very well in Windows XP, so clearly my computer and video card work fine together.

It's my video card and Linux that don't work fine.

Ah, but if you use Linux, then the card is not working for you.  - Sorry, I understand what you mean though, but think of all those people who want to upgrade to Vista from XP on their machines (I'm sure there MUST be some who do). They'll say that their old video card isn't supported in Vista so they'll have to get another card. (Or be doomed to run XP forever...)

---

### Post by Zero Prime on 2008-07-20
I just have to ask, did you try Envy?

---

### Post by Exershio on 2008-07-20
Yeah, I've tried just about everything mentioned in this thread short of buying a new card.

Though I'm quite disappointed. Ubuntu 7.10 didn't work like it used to. Maybe my card is just dying. Meh, still works in Windows, so I'll just go back to dual booting I suppose.

Guess I should start saving for a new computer. Being 17 without a job and no source of monetary income, I'm **** out of luck.

---

### Post by Washer on 2008-07-20
I'm guessing hardy won't work with some old kernel?

---

### Post by poofyhairguy on 2008-07-20
> **Exershio said:**
> Yeah, I've tried just about everything mentioned in this thread short of buying a new card.

Though I'm quite disappointed. Ubuntu 7.10 didn't work like it used to. Maybe my card is just dying. Meh, still works in Windows, so I'll just go back to dual booting I suppose.

Guess I should start saving for a new computer. Being 17 without a job and no source of monetary income, I'm **** out of luck.

Seriously, the open source Radeon driver build into the newest Ubuntu by default is not that bad. It can do Compiz and has decent GL performance. IT has come a long way in a little ammount of time for r300 hardware like yours. It is the only thing on use on my system with a x850 XT.

---

### Post by Dr Small on 2008-07-20
> **primoturbo said:**
> try Arch Linux.
+1

---

### Post by tdrusk on 2008-07-20
I'm just throwing this out there. Try running 8.04 and installing fluxbox. See if the lighter environment makes things smoother. 7.10 was lighter than 8.04. XP is lighter than 8.04.. Maybe the driver is using a lot of resources.

Then again it may not work.

Maybe try debian testing and load the driver you are currently using.

---

### Post by Exershio on 2008-07-22
> **poofyhairguy said:**
> Seriously, the open source Radeon driver build into the newest Ubuntu by default is not that bad. It can do Compiz and has decent GL performance. IT has come a long way in a little ammount of time for r300 hardware like yours. It is the only thing on use on my system with a x850 XT.
The open source driver doesnt work on my system at all. Any 3d rendering instantly kills my computer, locks it up, and requires a reboot via the power button.

---

### Post by hessiess on 2008-07-22
just stick with 7.10 for now, or try some other dists.

---

### Post by Canis familiaris on 2008-07-22
What's wrong staying with 7.10?

---

### Post by Saint Angeles on 2008-07-22
i wrote a little tutorial for how i got my fglrx driver working... theres a lot of attributes in there that may help...
[http://ubuntuforums.org/showpost.php?p=4749740&postcount=12](http://ubuntuforums.org/showpost.php?p=4749740&postcount=12)

---

### Post by Canis familiaris on 2008-07-22
@Saint Angeles
Do you know anyway to stop flickering of OpenGL apps like Celestia, Google Earth when using Compiz in an ATI card?

---

### Post by Iceni on 2008-07-22
A little ot but why not, it's the cafè:) Hardy was such a mess for me, I could never get my ide hard drive to work and my keyboard would randomly stop working. Now running 8.10 a2 and a lot more stable than hardy ever was for me:)

---

### Post by GOfree on 2008-07-24
I wish I could help.

I have the same problem, and I will be sticking with 7.10. I like it.

Don't worry. Somebody will figure it out. Ubuntu is not going to leave us poor ATI guys behind...I hope.

---

### Post by Saint Angeles on 2008-08-21
> **Anurag_panda said:**
> @Saint Angeles
Do you know anyway to stop flickering of OpenGL apps like Celestia, Google Earth when using Compiz in an ATI card?
actually i don't...

i usually switch to metacity when i need to use apps like that. the fusion-icon makes it super simple to switch back and forth.

i have found that when watching videos, switching to x11 (as opposed to xv) makes it run great under compiz... even wobbly windows looks great with videos.

---

### Post by ghindo on 2008-08-21
> **anurag_panda said:**
> what's wrong staying with 7.10?+1

---

### Post by waapwoop1 on 2008-08-21
> **Exershio said:**
> The problem is my ATI Radeon 9550 AGP video card. Remember back in 7.10, before FGLRX was supported in the FGLRX drivers? Well, my video card refuses to play nice with any drivers compatible with Ubuntu 8.04. I thought I'd be slick and download the old ATI drivers and install them manually in 8.04, but guess what? They don't work with the new Linux kernel.

With the newer ATI drivers (catalyst 7.11 and newer), my video is just plain choppy and unbearable with any OpenGL application that does 3d rendering.

So, I'm back to Ubuntu 7.10. It's nice having working 3d so I can play a few games, but I'm also doomed to run out of date software.

Though, if I look at it this way, I don't have many options:
1) Run Ubuntu 7.10. Everything works good, though the software is old.
2) Run Ubuntu 8.04. Newer software (yay), but can't play 3d games (boo)
3) Run Windows Vista. Video card drivers simply stop responding and crash anytime I play a 3d games.
4) Run Windows XP. Old stable OS, new programs, working games, but isn't exciting. I can't tweak it anymore, nothing new to really learn. It's not Linux, and I'm just plain bored with it.

Is there any other options for me? I just want new up to date software with the old ATI drivers, but it seems everything is just incompatible with each other.

I was thinking of installing Arch Linux (I love that distro), and taking on the adventurous task of compiling an older kernel, installing old ATI drivers, and then installing all new software. Could that work?

I just can't wait until ATI finally releases drivers that work for everybody. Then I won't have a problem. :D

Ah, who knows. If you all have any input or suggestions, please let me know. I'd appreciate it greatly. :)


Yes forever

---

