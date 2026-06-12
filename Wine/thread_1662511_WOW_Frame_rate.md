---
title: "WOW Frame rate"
date: 2011-01-08
forum: Wine
---

### Post by rosco232 on 2011-01-08
I am desperately tryin (so far to much avail) to increase my framerate in WOW using wine.  My pc is no hoss, but it isn't bottom of the line either. I cant seem to get above 28fps.  I feel like I should be pullin about 50 fps, but I may be terribly wrong.  Please help!!

AMD Athlon 64 x2 Dual Core 5000+
NVIDIA Geforce 8400gs
2gb RAM

Ubuntu 10.10 32bit
Wine 1.2.2
-Edited WTF file with (SET gxApi "opengl") script (it actually runs about 2fps faster with this deleted, but for now, I have it in)
-Added the HKEY_CURRENT_USER\Software\Wine\ registry addition......that didn't seem to do anything.
-Tried adding other WTF file scripts (SET ffxDeath "0",
SET ffxGlow "0", and SET M2UseShaders "0") this didnt seem to do anything at all.  I thankfully didn't have any graphic errors to start with, just tried to see.......so they are no longer in WTF file.

-Running WOW at 1920x1080 (my screen resolution) both windowed and fullscreen without much of an increase.  Also tried lower resolutions.
-Have video settings to lowest or fair with only view distance at high. Vertical Sync is OFF. All heavy load stuff is off or low.
-I use SKYPE for chat, so in-game voice chat is off.



Please help......28 fps isn't horrible, but i really don't want to think about what this is going to do in a raid.

---

### Post by gradinaruvasile on 2011-01-08
The 8400 gs is a low end card. It has low-speed 64-bit memory bandwidth. While this is not that visible in lower-end games, in heavy 3d games it shows and becomes the performance bottleneck. I would recommend a 128-bit (at least) card for gaming.

Other than that you can try upgrading to the latest wine version - 1.3.10 now and the latest nvidia driver - 260.19.29.

Edit:

Other thing to try is to install directx 9 full (not just the base dlls) with winetricks. It really helps in general in increasing 3d compatibility and fps.

---

### Post by rosco232 on 2011-01-08
Ok, Thanks!  

My problem is my motherboard on this one.  It only has pci express 16x.....not 2.0 or 2.1.....otherwise i would have a much different card. :( 
-Any suggestions on cards? Did a quick search and found only ATI cards, and they are min 80 bucks......That seems awfully high for an interface that is obsolete, and a 5yr old game....(only running original game at the moment until I get it running the way I want).
-My experience with ATI in the past has been pretty negative. I was hoping to get acquainted with NVIDIA more.  Had Raedeon 9200 and 9800 pro in past. 
-Also havent seen much in the way of ATI and WOW really working well with wine....I'm seriously not trying to just ATI bash here, but if I'm going to have to spend 80 minimum, I might as well get a new motherboard too.....this is destroying the point of keeping alive this older computer.

I am currently running driver 260.19.29. Ran an older version too and I like the functionality of the newer better.  No speed difference between the two.

Thank you for the directx suggestion. I will definitely try that!!!!

---

### Post by cwwilson721 on 2011-01-08
2.0 cards work in a 1.0 x16 slot. If I were you, I'd get (min) an Nvidia 9600GT or higher (EXCEPT a 210/220)(Forget ATi, the drivers STILL need work, and have had issues lately AGAIN.

Check [this link to see the hierarchy of video cards]("http://www.tomshardware.com/reviews/gaming-graphics-card-recommendation-upgrade,2803-7.html")

Closer to the top is better. If you have questions if it is OK or not, check the specs:
MORE than 64bit memory bandwidth
MORE than 36 Cuda cores.
More memory (example: 2GB vs 1GB) doesn't matter as much as Bandwith/cores. Memory amount is more important when you try to use Anti-Aliasing.

If you keep this in mind, you should be fine for WoW/wine. 

For example, I use a Nvidia 9600GSO w/768mb ram, 192bit memory bandwidth, and 48 Cuda cores (Note: Some 9600GSO's have less bandwidth or Cuda cores. Just watch the specs).

Good luck

---

### Post by rosco232 on 2011-01-11
Thanks for the help folks.  Luckily I had only purchased the card a few days before hand and due to my new knowledge that a 2.0 card will work until I opt to change mobo and proc (thanks cwwilson721) I took it back and bought a GTS 250 and an upgrade on ram too.

So, for the WOW news in wine.....

Plugged card in, plugged ram, booted, opened wow.....

30fps now. Well, not bad, but still expected more. And only one option in video settings opened that didnt allow me to do before hand.

Downloaded and installed directx......no difference.

Bit the bullet, formatted, dual boot install of Maverick and Windows XP.

In windows it works MUCH better (well duh......)
Im talkin a very solid 40 fps with EVERYTHING maxed. 60 to 70 on fair to good settings.

Thanks again for the help everyone. Ill still use wine, but probably only when in questing solo or with a group under 4. Everything else, on xp. Did learn a bunch and walked away with a positive experience and a better running machine than I could have dreamed of with this old thing.

Next will be win 7 64 dual boot with Maverick 64 if I can get a student copy......

---

### Post by mdshann on 2011-01-11
When I played WOW I was locked at 60 fps (max refresh on my LCD) on a Core i7 with 6 GB of RAM and a GTX 275... if you can get 50 fps on a dual core with 2 GB of RAM and an 8400 GS / GTS 250 then I should just have burned all that cash...

My brother has a similar system to yours with a Core 2 Duo and 4 GB of RAM. He just got one of the newer GTX 460 cards and it plays games every bit as good as mine. He payed about the same as I did for my 275 so it seems to me that $200-ish is the sweet spot where you get the best bang for your buck. My computer loads levels faster but graphics seem to be about the same. A friend of mine has 2 GTX 480's in SLI ($600 a piece!) and to tell you the truth while he gets more frames it's really not that much more playable than my 275 or my bro's 460.

---

### Post by rosco232 on 2011-01-11
nah, i upgraded ram too man

running 4gb

ya, i have learned to not spend lots of money on comp stuff

---

### Post by _outlawed_ on 2011-01-11
> **mdshann said:**
> A friend of mine has 2 GTX 480's in SLI ($600 a piece!) and to tell you the truth while he gets more frames it's really not that much more playable than my 275 or my bro's 460.

Quite a waste of money, considering the max frame rate that humans can see is 45 fps. Anything more than 45 is undetectable by our eyes.

---

### Post by cwwilson721 on 2011-01-11
> **_outlawed_ said:**
> Quite a waste of money, considering the max frame rate that humans can see is 45 fps. Anything more than 45 is undetectable by our eyes.You obviously don't play WoW.
Higher FPS=better DPS/Tanking/Heals in raids and PvP. The reason is that you aren't waiting on the graphics to change to do 'whatever'. And things like riding in one of the "propeller driven" mounts at <45 and then >60 is DEFINITELY discernible.

I'm running a 9600GSO/768MB and 4GB ram on a  AMD dual-core 5200+. And my FPS is 45-70 depending on where I am. (On an LCD. If you want better FPS, unlock it from the refresh in Video Settings. It will help)

---

### Post by _outlawed_ on 2011-01-12
> **cwwilson721 said:**
> You obviously don't play WoW.
Higher FPS=better DPS/Tanking/Heals in raids and PvP. The reason is that you aren't waiting on the graphics to change to do 'whatever'. And things like riding in one of the "propeller driven" mounts at <45 and then >60 is DEFINITELY discernible.

I'm running a 9600GSO/768MB and 4GB ram on a  AMD dual-core 5200+. And my FPS is 45-70 depending on where I am. (On an LCD. If you want better FPS, unlock it from the refresh in Video Settings. It will help)

Yes, because I've played WoW since beta. I was just saying in general human eyes can't detect FPS past 45.

And my point remains, 2x $600 video cards to play an ancient game that hasn't had a graphics engine update in forever? But whatever, thats his choice.

---

### Post by cwwilson721 on 2011-01-12
> **_outlawed_ said:**
> Yes, because I've played WoW since beta. I was just saying in general human eyes can't detect FPS past 45.

And my point remains, 2x $600 video cards to play an ancient game that hasn't had a graphics engine update in forever? But whatever, thats his choice.Maybe they play other games that need it.
Maybe they have more money that they have to spend it all.

Either way, I have a Linux box with 3-way SLI and 3 NV9800GTX+ cards in it. Why? Because of games for Windows, and now dual-booted for Linux. It's there. And I 'ocassionally' play WoW on it. It's nice to turn all up to max, and still be able to play. Then boot into W7-64bit and REALLY max it out.

Not needed, but nice to know it's there.

Like a car that can do 160MPH. Speed limits in US doesn't go above 80MPH anywhere.
But I CAN.

---

### Post by mdshann on 2011-01-12
> **cwwilson721 said:**
> Maybe they play other games that need it.
Maybe they have more money that they have to spend it all.

Either way, I have a Linux box with 3-way SLI and 3 NV9800GTX+ cards in it. Why? Because of games for Windows, and now dual-booted for Linux. It's there. And I 'ocassionally' play WoW on it. It's nice to turn all up to max, and still be able to play. Then boot into W7-64bit and REALLY max it out.

Not needed, but nice to know it's there.

Like a car that can do 160MPH. Speed limits in US doesn't go above 80MPH anywhere.
But I CAN.

Exactly. If I had the money I also would have bought 2 480's. Unfortunately things like rent, food, and getting to work take precedence over entertainment.

---

### Post by cwwilson721 on 2011-01-12
But not sleep!!!

Wow rulez our dreams!

---

### Post by khelben1979 on 2011-01-25
> **_outlawed_ said:**
> Quite a waste of money, considering the max frame rate that humans can see is 45 fps. Anything more than 45 is undetectable by our eyes.

Where is your source of that statement? I read through [this]("http://whisper.ausgamers.com/wiki/index.php/How_many_FPS_human_eye_can_see"), and that is not a valid statement. It seems a little more complicated than that.

Also keep in mind that if a game reports 40, 45 or 50 fps, I wouldn't be too naive to believe that the measurement is correct as well. I'm a bit sceptic about it.

---

### Post by Halzen on 2011-01-25
> **_outlawed_ said:**
> I was just saying in general human eyes can't detect FPS past 45.

Congrats - you either have bad eyes, a bad monitor, or both. The average human can easily detect the differences between 45 FPS and higher. Whether that difference actually shows to begin with depends on your display's refresh rate. For example, a monitor with 60hz refresh rate will allow you to see the "smoothness" up to 60FPS, but anything higher than that will still look like 60FPS.

Oh, and to the OP: running WoW in OpenGL mode can drastically improve your framerate in Wine, at the cost of some visual eye candy. I get over 40 FPS in Orgrimmar and other crowded places, and upwards of 70-140 FPS elsewhere, at high settings with 2x multisampling. Unfortunately, I can't crank up the shadow or water quality due to the OpenGL rendering limitations.

---

### Post by Nekralikos on 2011-01-25
> **cwwilson721 said:**
> 2.0 cards work in a 1.0 x16 slot. If I were you, I'd get (min) an Nvidia 9600GT or higher (EXCEPT a 210/220)(Forget ATi, the drivers STILL need work, and have had issues lately AGAIN.

Check [this link to see the hierarchy of video cards]("http://www.tomshardware.com/reviews/gaming-graphics-card-recommendation-upgrade,2803-7.html")

Closer to the top is better. If you have questions if it is OK or not, check the specs:
MORE than 64bit memory bandwidth
MORE than 36 Cuda cores.
More memory (example: 2GB vs 1GB) doesn't matter as much as Bandwith/cores. Memory amount is more important when you try to use Anti-Aliasing.

If you keep this in mind, you should be fine for WoW/wine. 

For example, I use a Nvidia 9600GSO w/768mb ram, 192bit memory bandwidth, and 48 Cuda cores (Note: Some 9600GSO's have less bandwidth or Cuda cores. Just watch the specs).

Good luck
ATI Mobility Radeon HD 5870 is a pretty dope card~

---

