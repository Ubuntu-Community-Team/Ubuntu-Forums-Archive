---
title: "Do ATI or NVIDIA's official drivers work for you in Ubuntu 6.06(Dapper)"
date: 2006-10-16
forum: The Cafe
---

### Post by TLE on 2006-10-16
[SIZE="3"]Do ATI or NVIDIA's official drivers work for you in Ubuntu 6.06(Dapper)[/SIZE]


[SIZE="2"]Hey everybody.
*Utilizing the 3D acceleration* on those fancy graphics cards people have seems to be one of the things that give 
people a *lot of trouble*, and therefore is also enveloped in a lot of rumors about what works and what don't. The *purpose of this poll is* to try to shed some light on this through *statistics*.

In order to make this as *fair and useable a result* as possible, please try to conform to the following guidelines

[LIST=1]
[*]Vote only if your situation accurately fits one of the options.


[*]**( * NOTE from poll options * )** When you evaluate how fast the acceleration work please remember, that if you are running games designed for Windows through Wine or Cedega, you are in fact running a "translation" layer in between the game and your system, that is bound to use some resources and therefore you cannot necessarily expect the same speed as you get with the same system and the same game in Windows. Furthermore, if the 3D acceleration is very slow, giving real low (depending on your hardware of course) frame rates in `glxgears -printfps`, then your 3D rendering is probably not hardware accelerated at all and you should choose the "...DO NOT..." option instead of the "...DO give me 3D acceleration. It is slower..." option.


[*]If you reply "...DO NOT..." please be as sure as you can that it is not the application you use (Wine/Cedega or various games) but in fact the graphics drivers that are to blame. This can be investigated by gathering info on whether that particular application works for other people and if you did what you could to set it up right.


[*]The poll options do not include any info on how easy or difficult it was to make it work. This is on purpose, as it would make it far to complicated to include all the different permutations of that also. In short, ease of installation might be the subject of another poll but not this one.
[/LIST]


This poll of for Ubuntu 6.06(Dapper) only. The reason for doing it now (right before Ubuntu 6.06(Dapper)'s successor is released) is that now everybody has had a chance to try and make it work, and in fact, if you have been working on it since the release of Ubuntu 6.06(Dapper) and it still doesn't work, then it probably won't at all ;)

I will make more of these polls in the future, regularly right before every release to track the development of this issue. If sufficiently many people vote in order for it to be a sound statistical base (say ~100), I'll forward the result to NVIDIA and ATI for them to use as they see fit.

Please also make a post describing you experience with these official drivers.

Let's keep those votes coming
Regards TLE[/SIZE]

[SIZE="1"]PS: Regarding the formulation of the options. There are, off course, a lot of ways to define the categories for this poll. I have done everything that I can, to ensure that these categories are as clear and unambiguous as possible. I have additionally discussed the formulation with several other people (Thank you AskHL, Genrij, tseliot) before posting to try and ensure this. Therefore, if you have questions about the boundaries in the definitions, please post in this thread, but if you think they are inconsistent, please PM me instead since formulation-discussions, whether the critique is valid or not, tend to kill polls very quickly.

PPS: There are a lot of subjects related to this one that often initiate discussion: "How Wine works, what Wine is and is not", "ideological discussions about Wine vs. Cedega". Please make those discussion elsewhere and keep the posts here related to the subject.
[/SIZE]

[SIZE="4"][EDIT][/SIZE]
[SIZE="2"]Thanks for voting everyone. I got the 100 votes i was aiming at.

When I get around to it (I'll probably install edgy first) I'll make a wiki page containing the result of this poll and post a link to it here. Later on when we change distro again I'll make another poll and update the wiki-page with some statistics.

Regards TLE[/SIZE]

---

### Post by Perfect Storm on 2006-10-22
sticky for four days.

---

### Post by PatrickMay16 on 2006-10-22
Cockin' downhill at speeds in excess of 500,000 kilometers per hour.
I recently got an Nvidia GeForce 6200 because I was interested in playing N64 games using an emulator. It works very well for me, and I haven't had any problems with it.

---

### Post by chaosgeisterchen on 2006-10-22
The ATI drivers really suck, especially now that they stopped supporting my X300.

I have to take the R300 open source drives which do not really offer satisfying graphical power. I will switch to nVidia, as they at least offer good drivers even for Linux.

---

### Post by maniacmusician on 2006-10-22
I get a functioning system, but no 3d graphics. If i'm not getting those, then really, I might as well go with the open source "ati" driver (and i am, in fact). 

i've heard a few things floating around, and will try and post here to see if they're true. well, it's one thing really.

but i've heard that ATI cards for the laptop are *very* well supported? this will be pretty influential in my upcoming laptop purchase. After the debaucle with my ati chipset, i swore never to get ATI anything again. but now i'm hearing that ati supports onboard laptop cards very well...so what's the final word on this? or is there one? just want to make an informed purchase.

---

### Post by Juzz on 2006-10-22
Nopes - ATi more or less sucks overall...

If you have the opportunity for getting a NVidia based laptop - go for it.

BTW: I voted ATi off. DO NOT work for me - I get screen tearing and blinking when the system is working on something.

---

### Post by TLE on 2006-10-22
> **Juzz said:**
> Nopes - ATi more or less sucks overall...

If you have the opportunity for getting a NVidia...

Yeah that was actually one of the "rumours" I wanted to test. So far it looks like that's pretty much the current state of things.

---

### Post by qamelian on 2006-10-22
The official ATI drivers don't work with my laptop even though they explicitly list my card as supported. This is common for every distro I have tried.

My desktop has an Nvidia Geforce FX 5600, and the official Nvidia drivers work flawlessly. 

I doubt I'll ever purchase another PC or laptop that uses an ATI GPU.

---

### Post by user1397 on 2006-10-22
the fglrx ati driver from the repositories works flawlessly for me.  i have a sapphire radeon x1600 pro 512mb agp card.  its the last agp card ati's gonna make i think, after this, only PCI-E.  i've played the linux native version of america's army with this graphics card in ubuntu 6.06, with absolutely no problems at all.

---

### Post by Juzz on 2006-10-23
> **erik1397 said:**
> the fglrx ati driver from the repositories works flawlessly for me.  i have a sapphire radeon x1600 pro 512mb agp card.  its the last agp card ati's gonna make i think, after this, only PCI-E.  i've played the linux native version of america's army with this graphics card in ubuntu 6.06, with absolutely no problems at all.
Sorry to say it, but then you are using the community drivers...

But have you run anything else than Americas Army and WoW on it?

I used to have a Radeon 9800 Pro, and those were practically the only games I could run out of those I own. Morrorwind did run, but extremely poorly, GTA had about 1-2 fps and a whole bunch of others didn't run.
So this spring I exchanged it for a GeForce 6600GT and WOW what a difference.

---

### Post by TLE on 2006-10-23
> **Juzz said:**
> Sorry to say it, but then you are using the community drivers...

The poll refers to the drivers that NVIDIA and ATI produce, no matter if you download them directly from their homepage or install the community versions.

I certainly don't hope that it is the common belief that I was only refering to the ones you actually download from their homepage. Because then I'll have to reformulate the post to make that clear.

---

### Post by Rumor on 2006-10-23
I am currently running an eVGA 6800GT card using the drivers downloaded from nvidia's website. Games like Quake 3 or Neverwinter Nights run very smoothly with good frame rates.

---

### Post by chewitts on 2006-10-23
ATI's off. drivers DO give me 3D-acc. It is slower(*) than I would expect"

PCI.E X800 GT gcard.

---

### Post by Rhubarb on 2006-10-23
Have a laptop with PCIe nVidia go 7400, using the drivers from the repositories.
UT2004 (openGL) works beautifully - same fps as windows (Direct X) - with all of the qualities and details turned up ~ 40 FPS
Quake 3 also runs very fast (and so it should).
I do have one problem with the nVidia drivers, in that when I shut down Dapper, the screen goes blank rather than displaying the Ubuntu shutdown splash.

---

### Post by warlorddagaz on 2006-10-23
They do work, although it took me ages - I would recommend "envy" to anyone who is trying to install the nvidia driver, as it does the whole process for you - I had been trying to install the driver, and getting errors at every point: x-server, then kernel problems which needed a c compiler - as I am new to linux, envy was very helpful.

---

### Post by user1397 on 2006-10-23
> **Juzz said:**
> Sorry to say it, but then you are using the community drivers...as you have probably already read the OP's post about this, i dont feel a need to reply to this statement.

> **Juzz said:**
> But have you run anything else than Americas Army and WoW on it?i do not own WoW, and never will, as i don't like it at all.  but other than america's army, i have only run little arcade style games, like super tux and such, and i have run xgl/compiz in the past with this setup (though not anymore, i have since removed it.)

> **Juzz said:**
> I used to have a Radeon 9800 Pro, and those were practically the only games I could run out of those I own. Morrorwind did run, but extremely poorly, GTA had about 1-2 fps and a whole bunch of others didn't run.
So this spring I exchanged it for a GeForce 6600GT and WOW what a difference.hmmm well i also had a radeon 9800 pro, but it over heated because the thing holding the fan to the GPU like melted off, so i had to get a new card.  i don't really game on linux, america's army was more of a test for me than anything.  that's all ubuntu is for me nowadays, sorry to say:  a testing ground.  my default OS for work and play is windows, though i do not like it very much.:-k

---

### Post by jpkotta on 2006-10-24
I have a laptop with ATI and desktop with NVidia.  NVidia has worked flawlessly for me ever since I found out about it (ca. 6 months after I installed Linux, long before installing Ubuntu).  

ATI was a PITA until they finally got their act together and made a nice installer.  Their drivers are still unstable and slower, and don't work with Composite.  But, I know how to make them crash and more importantly how to not make them crash (don't start extra X servers and don't run Celestia), and suspend works with them, so it's OK.

I voted for NVidia works flawlessly and fast.  I also would have voted for ATI works, but slow.

---

### Post by rocknrolf77 on 2006-10-24
I can say I actually hate my ati card. Never got it working properly. Nvidia at least continues to support their older cards to. The problem is I like Amd. Din't like that fusion. Getting the 7600 GT in a 14 days time. What a relief. This was my last ati card. No more money from me to them.

---

### Post by Placenta Juan on 2006-10-24
ATI's official 8.28.8 drivers work fine on my radeon 9600xt
i get between 80-100fps in SuperTux and Planet Penguin Racer.:)

---

### Post by Buddha443556 on 2006-10-25
I was using the official nVidia driver but switched back to nv after encountering a bug that crashed x. Bug involved long lines of text in certain programs (Firebug and Regexxer). 3D acceleration seemed fine however I only used it for the screen saver. :oops:

---

### Post by TLE on 2006-10-27
Thanks for voting everyone. I got the 100 votes i was aiming at.

When I get around to it (I'll probably install edgy first) I'll make a wiki page containing the result of this poll and post a link to it here. Later on when we change distro again I'll make another poll and update the wiki-page with some statistics.

Regards TLE

---

