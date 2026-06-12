---
title: "Best Video Card?"
date: 2007-05-12
forum: The Cafe
---

### Post by ArtificialSynapse on 2007-05-12
I'm getting a new job soon, and before I move out to Chicago, I want to enjoy the fact I don't have to be completely responsible with my money. . .sooooo....I'm buying a new video card along with another stick of RAM, I'm looking to spend about 150 - 200 on the video card ; what do you think would work best with Ubuntu. I've got a PCI Express expansion slot with 1gb of system RAM.

---

### Post by prizrak on 2007-05-12
Hard to say really. Now that AMD has announced that they will open up driver for their video cards you might want to get a Radeon. On the other hand they haven't done it yet so you might be better with an nVidia.

---

### Post by RTrev on 2007-05-12
> **ArtificialSynapse said:**
> I'm getting a new job soon, and before I move out to Chicago, I want to enjoy the fact I don't have to be completely responsible with my money. . .sooooo....I'm buying a new video card along with another stick of RAM, I'm looking to spend about 150 - 200 on the video card ; what do you think would work best with Ubuntu. I've got a PCI Express expansion slot with 1gb of system RAM.

First, the RAM.  I just found this page that you might be interested in:

[http://blogs.zdnet.com/Ou/?p=488](http://blogs.zdnet.com/Ou/?p=488)

About the video card, I think it depends on what you want to do with it.  I don't think you can go wrong with Nvidia, and I picked up an XFX Nvidia GeForce 7300 GT with dual digital outputs and 512M of DDR2 for about $100.  It's running in a 16x PCI-Express slot.  I'm not a gamer, so can't comment on how it would do there, but it does just fine for normal work and for watching DVD movies, etc.  Nvidia makes it very easy to run multiple monitors, with their Twinview technology.  I don't know how good a benchmark this really is, but I usually use glxgears -info to measure the speed, and with Twinview enabled and dual flat panel displays, I get a value of 6500 frames/second with this card.

Nvidia is one of the only cards I don't here complaints about from the Linux community, so apparently most people don't have much trouble getting them running right.

HTH,
Bob

---

### Post by trak87 on 2007-05-12
While the news of ATI (via AMD) going in the open source direction is really good, it may be a while before you can get great drivers for ATI cards. In my experience, NVidia cards have been better for me because there's less fiddling around trying to get glx (high speed graphics) working.

---

### Post by maniacmusician on 2007-05-12
eVGA GeForece 7600 GT

---

### Post by Enverex on 2007-05-12
> **ArtificialSynapse said:**
> I'm getting a new job soon, and before I move out to Chicago, I want to enjoy the fact I don't have to be completely responsible with my money. . .sooooo....I'm buying a new video card along with another stick of RAM, I'm looking to spend about 150 - 200 on the video card ; what do you think would work best with Ubuntu. I've got a PCI Express expansion slot with 1gb of system RAM.

The graphics card front is simple. Buy the best nVidia card that you can afford.

> **prizrak said:**
> ...Now that AMD has announced that they will open up driver for their video cards....

Erm, when did this happen and sources please?

---

### Post by eks on 2007-05-19
**Don't get an ATI**, it's certainly trouble. Their drivers are terrible. They might improve if the rumors of opening the drivers are true, but even if the rumors become true it will take quite some time for new versions to be available and better supported. Until then you might already be ready for a new upgrade. **So, definitely, go with nVidia.**

eks
PS: yes, I own an ATI and I regret it. I will actually sell it the following weeks and buy a nVidia.

---

### Post by jariku on 2007-05-20
> **Enverex said:**
> Erm, when did this happen and sources please?
[http://ubuntuforums.org/showthread.php?t=440767](http://ubuntuforums.org/showthread.php?t=440767)

---

### Post by Outrunner on 2007-05-20
Well, a 7600 GT as suggested above would be your best choice, and more than enough if you don't play games(or newer games, at least). Make sure you have a good PSU(good brand and somewhere around 350W whould be enough, generally)

---

### Post by PrimoTurbo on 2007-05-20
I don't recommend ATI because I have an ATI card and the performance under Linux is not on par to Windows in native games. Only time will tell if ATI's open source drivers will be good or even if they are what they say they are.

For now I suggest an Nvidia card under Linux, also consider the fact that ATI's drivers will take a while to be released anyways and good drivers will only come after a while also.

---

### Post by jamieplucinski on 2007-05-20
Don't hold your breath for AMD/ATI to open everything up, same with the Vista drivers, what they provide, they do to support some corporate customers, and shun the rest. My 200m is deliberately ignored during hardware detection in ATI's Vista installer, despite being packaged with a perfectly good 200m driver. Why? Because two bytes in my firmware list it as a HP chipset, so it's ignored, and HP always want me to upgrade, so I am stuck with not getting the updates ATI are releasing... nice. It worked and was detected before, just not now in their new and improve drivers. Good job Microsoft actually ship a good and I mean 30-40 FPS in World of Warcraft in Windowed mode on Vista with Glass turned on and all WoW graphics options at the max good.

For Windows, ATI, for Linux Nvidia, if you are experimenting with Ubuntu, I'd go ATI, because I've been trying to move to Ubuntu for over a year now but as much as the builds keep getting better, there are always show-stoppers and I end up installing Windows again so I can actually use my laptop... :(

---

### Post by Enverex on 2007-05-20
> **jamieplucinski said:**
> Don't hold your breath for AMD/ATI to open everything up, same with the Vista drivers, what they provide, they do to support some corporate customers, and shun the rest. My 200m is deliberately ignored during hardware detection in ATI's Vista installer, despite being packaged with a perfectly good 200m driver. Why? Because two bytes in my firmware list it as a HP chipset, so it's ignored, and HP always want me to upgrade, so I am stuck with not getting the updates ATI are releasing... nice. It worked and was detected before, just not now in their new and improve drivers. Good job Microsoft actually ship a good and I mean 30-40 FPS in World of Warcraft in Windowed mode on Vista with Glass turned on and all WoW graphics options at the max good.

For Windows, ATI, for Linux Nvidia, if you are experimenting with Ubuntu, I'd go ATI, because I've been trying to move to Ubuntu for over a year now but as much as the builds keep getting better, there are always show-stoppers and I end up installing Windows again so I can actually use my laptop... :(

Please don't ever recommend ATi for anyone that intends to use Linux at all, you're condemning them to a nightmare and nVidia works perfectly well under Windows so that's no excuse.

---

### Post by Lux Perpetua on 2007-05-20
Yes, AMD has announced that they will release open-source drivers, but would you really bet $200 that they'll keep their promise in a timely manner?

---

### Post by maniacmusician on 2007-05-20
> **Lux Perpetua said:**
> Yes, AMD has announced that they will release open-source drivers, but would you really bet $200 that they'll keep their promise in a timely manner?
well it would take a long time to release open source drivers anyways, since they would have to replace propritetary 3rd party bits with their own source, but that's not really the issue.

In all likelihood, they'll not keep their promise at all. and I would wager some money on that statement.

Besides, the issue is not them providing open source drivers. Just because they let us see the source for the drivers doesn't mean that the drivers will be good. The issue is them providing **open specifications** for their video cards, so that after they release their crappy open source drivers, we can look at the specifications and fix all the bugs in their horrible coding.

Considering the work they did on the fglrx drivers, this will probably be the case.

---

### Post by ArtificialSynapse on 2007-05-20
Alright, thanks for your input, I'd have gone with Nvidia anyways, since that's always what I've gotten, and I really don't even want any possibility of my card not working up to par with Nvidia.

So now what nvidia card should I get?

---

### Post by maniacmusician on 2007-05-20
As I said before, eVGA nVidia 7600GT. It's in your price range and it packs a lot of punch for that price.

or the other option is, buy the RAM first, and then decide how much money you really want to spend on a video card. If you can afford something better than the 7600GT, go for it.

---

### Post by jamieplucinski on 2007-05-20
> **Enverex said:**
> Please don't ever recommend ATi for anyone that intends to use Linux at all, you're condemning them to a nightmare and nVidia works perfectly well under Windows so that's no excuse.

I agree that ATI used to be a nightmare, but they're getting better with every build, and not everyone has the extra cash to shell out on an Nvidia, I know I don't for sure. My 200m works fine with the restricted modules enabled, sure the laptop overheats and shuts down, but that's due to ACPI being bugged.

If you have the money for an Nvidia, go for it, ATI is just a cheaper alternative for those with very little money to spend. Nvidia are also more power hungry than ATI, so depending on what graphics card you go for, you might have to get a new PSU... again it just comes down to cashflow.

---

### Post by PatrickMay16 on 2007-05-20
Don't buy an ATI card yet; wait until they deliver on their promise of open drivers. Until then, get an nvidia card.

---

### Post by Babbage on 2007-05-20
I just built a new computer and I got the  NVIDIA GeForce 7100 GS 128MB Turbo Cache PCI-E Card. I realise it's an entry level card with 128 Mb memory, but I was disappointed with it's performance under Ubuntu Fiesty. The LCD monitor I'm using is a few years old so that may be an issue; although 1024 x 768 at 50 Hz refresh rate is way below what I was expecting. I got better performance on the same screen with my old PC and a 64Mb nVidia card using Ubuntu Dapper.

Forgot to mention I'm using the nVidia restricted drivers in both cases.
Anyway I like nVidia cards so I'd recommend them, liked them when I used Windows and they seem to be best choice for Ubuntu as well.

---

### Post by Polygon on 2007-05-20
I have an ATI radeon 9800 and its worked fine for me so far. the fglrx drivers also work perfectly and i can play games like doom3 and unreal tournament 2004 without any slowdowns (except a bit on doom3)

but i have heard that nvidia cards have better support.

---

### Post by Enverex on 2007-05-20
> **Babbage said:**
> I just built a new computer and I got the  NVIDIA GeForce 7100 GS 128MB Turbo Cache PCI-E Card. I realise it's an entry level card with 128 Mb memory, but I was disappointed with it's performance under Ubuntu Fiesty. The LCD monitor I'm using is a few years old so that may be an issue; although 1024 x 768 at 50 Hz refresh rate is way below what I was expecting. I got better performance on the same screen with my old PC and a 64Mb nVidia card using Ubuntu Dapper.

Forgot to mention I'm using the nVidia restricted drivers in both cases.
Anyway I like nVidia cards so I'd recommend them, liked them when I used Windows and they seem to be best choice for Ubuntu as well.

It's not really running at 50Hz, it's just an illusion caused by nVidia's TwinView XOrg option.

---

### Post by Babbage on 2007-05-20
Thanks for the reply Enverex, maybe it's not so bad after all.

---

