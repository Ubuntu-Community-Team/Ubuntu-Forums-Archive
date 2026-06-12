---
title: "Sad departure from Ubuntu Land..."
date: 2007-01-23
forum: The Cafe
---

### Post by wylie348 on 2007-01-23
Well, after several years using Linux (mostly Ubuntu) I have had to return to windoze.  I was very disappointed to have to make the switch, but I thought I would post my rationale, in the hopes that I can return to Ubuntu Land when I purchase my next laptop.
It all boiled down to hardware support.  Even with the awesome support of the forums, my laptop, Fujitsu T4210 Lifebook, simply has too many hardware features that were unsupported, and I found that even tweaking did not bring the battery performance up to par with windoze.
So I guess it was all my fault for not being more careful with my tablet purchase, so to make this a useful post other than a rant, can anyone provide me with a suggestion for a great tablet that actually supports Linux more than windoze?  Any suggestions appreciated, although it will now have to wait for the next hardware upgrade cycle.
Thanks again Community!
:(

---

### Post by timpino on 2007-01-23
IBM usually have decent linux-support and they have a tablet I think it's X60t but not really sure... :)

---

### Post by Kateikyoushi on 2007-01-23
I guess recommending it now does not make much sense, so ask it again and look around when you are about to buy it.
Recently we are also looking for new notebooks and there seem to be lot of new features on them which might not be supported in linux, it makes me wonder as well what are my chances for using linux on a Vaio UX or type G.

---

### Post by The Noble on 2007-01-23
Good luck in your travels and thank you for being patient! When you decide to buy a new laptop, tablet hardware detection will improve...

---

### Post by 23meg on 2007-01-23
[QUOTE=wylie348]can anyone provide me with a suggestion for a great tablet that actually supports Linux more than windoze? [/QUOTE]Everything except suspend works as default with my Toshiba Tecra M4, and battery life is generally better in Ubuntu than Windows. Some people also report success with getting suspend working.

---

### Post by smitty5533 on 2007-01-23
I'll second the toshiba
a week ago i thought that i was going to go back to m$ for sure, but  it has been very easy to find solutions for tablet problems for my toshiba r15

---

### Post by Johnsie on 2007-01-23
Ubuntu falls shot of many users requirements.... It also causes many laptops to overheat. That's a danger in itself (fire hazard). I'm not just making that up. Search these forums. I actually had to put a laptop on a cold kitchen floor to prevent a computer from shutting down while running apt-get.

---

### Post by Daveski on 2007-01-24
> **Johnsie said:**
> Ubuntu falls shot of many users requirements.... It also causes many laptops to overheat. That's a danger in itself (fire hazard).

No, that's called badly designed hardware. What about all those people who run serious crunching applications that run the CPU at full-tilt? Or those who run grid computing clients that keep the CPU at 100%? Or even those who might run DOS, which wont run any of the power saving stuff? If a laptop bursts into flames, or simply shuts down when running at 100%, then the laptop has been seriously poorly designed, or has gathered too much goo in the cooling ducts, and really needs a good clean.

---

### Post by wylie348 on 2007-01-24
Well I am finding it really hard to stick with Windows...!  I think I just used Linux too long and fell in love with Ubuntu and the Forums.  Now - how to effectively plan my way back.  I am getting new batteries sent to me under warranty, and I want to ensure that it is not Ubuntu that is reducing their effectiveness and that it was probably just poor batteries...
Is there any DANGER to running my Fujitsu hardware under Ubuntu...?
Thanks again for help, and yes - I only lasted 1 week under windoze power - but I am happy to start the re-install process with Ubuntu!
:)

---

### Post by The Noble on 2007-01-25
There is no danger with using another operating system with 99.9 percent of the hardware out there. The only way for Linux to permanently damage something would be through extremely poor system design or the Fuhitsu BIOS says "OH TEh NOeS! It'S TEh H@xxoR LInuX! SElF ImpLoSioN ActiVaTE!" So in reality, no problems should arise. Just watch out for the heat issue for extended periods of time. My Dell laptop has some heating issues (around 52 Celsius idle), but it has a class action lawsuit against it so whataver...

---

### Post by prizrak on 2007-01-25
I got Feisty on TravelMate C310 (tablet) battery life is about the same (10 mins more in Windows). Tablet part works but I can't flip the screen, tho according to the plans for Feisty final and Feisty+1 that won't be a problem when XRANDR replaces XORG.CONF completely. Wacom-tools are also improving quite fast. Hotkeys are working as well with the acerhk module, hopefully the Ubuntu team will integrate them (I opened a bug about it). My biggest hurdle right now is Bluetooth, I'm pretty sure that BlueZ driver has support for it but something is preventing it from working.

---

### Post by gvoima on 2007-02-20
My battery life dropped a little bit because i have a nvidia graphic card and the drivers don't support powermizer yet, so it runs on full speed all the time :P
NVClock is a good option too, but it would be better to have native support from manufacturer and a slider to set the levels for the gpu/mem.
If I drop the graphic card clocks enough (approximately to the same as in windows) I get more battery life than I did on windows with maximum powersaving.

> **prizrak said:**
> I got Feisty on TravelMate C310 (tablet)...hotkeys are working as well with the acerhk module...
I wasn't aware of this module, I too have Travelmate C310 and have strugled with the hotkeys above the keyboard, I even tried to compile the acer_acpi to get wlan/bluetooth button working with no success.
This saved my day, thank you so much :)

BTW, how did you get suspend working? I have NVIDIA card on mine and it's giving me a hard time with suspend, it takes ages for it to wake up.

---

### Post by Erunno on 2007-02-20
One thing that really annoys me on my Kubuntu notebook is the strange CPU cooling behaviour. Instead of letting the fan run for a longer period to bring the temperature down to a level a good deal below where additional cooling is needed the OS turns the fan on and off repeatedly for a couple of seconds which is far more distracting than a constant hum in the background. I hope Feisty will continue to improve laptop support as many people own one and being seen with Ubuntu is free advertisement.

---

### Post by prizrak on 2007-02-20
> **gvoima said:**
> My battery life dropped a little bit because i have a nvidia graphic card and the drivers don't support powermizer yet, so it runs on full speed all the time :P
NVClock is a good option too, but it would be better to have native support from manufacturer and a slider to set the levels for the gpu/mem.
If I drop the graphic card clocks enough (approximately to the same as in windows) I get more battery life than I did on windows with maximum powersaving.


I wasn't aware of this module, I too have Travelmate C310 and have strugled with the hotkeys above the keyboard, I even tried to compile the acer_acpi to get wlan/bluetooth button working with no success.
This saved my day, thank you so much :)

BTW, how did you get suspend working? I have NVIDIA card on mine and it's giving me a hard time with suspend, it takes ages for it to wake up.

Just for the sake of other people benefitting since I already responded to you on PM. Also I would like to offer a public thank you for the BT tip, I was going to ditch Windows when Feisty went final anyway but that was definetly icing on the cake. You should write up a how-to on getting BT to work. 

Never got suspend working in Feisty it worked in Dapper but took alot of time. Never tried Edgy. There are reports of the binary driver screwing with suspend. As far as battery life goes in my tests Ubuntu (Feisty + Beryl) drops me by 10 minutes compared to Windows. Seeing as how the C310 can handle dual batteries it never seemed like a big problem to me ;)

---

### Post by darrenn on 2007-02-20
Have you tried microsoft virtual pc 2007?

 It is free and it seems to work great with linux. No hassle download, no need for a cdkey. I had linux running within five minutes of downloading it. I am using dsl right now, but I am going to switch too ubuntu soon. This is a godsend for people with hardware problems. 

Now you have no excuse not to use linux. 

[http://www.microsoft.com/windows/products/winfamily/virtualpc/default.mspx](http://www.microsoft.com/windows/products/winfamily/virtualpc/default.mspx)

---

### Post by RAV TUX on 2007-02-20
> **wylie348 said:**
> Well, after several years using Linux (mostly Ubuntu) I have had to return to windoze.  I was very disappointed to have to make the switch, but I thought I would post my rationale, in the hopes that I can return to Ubuntu Land when I purchase my next laptop.
It all boiled down to hardware support.  Even with the awesome support of the forums, my laptop, Fujitsu T4210 Lifebook, simply has too many hardware features that were unsupported, and I found that even tweaking did not bring the battery performance up to par with windoze.
So I guess it was all my fault for not being more careful with my tablet purchase, so to make this a useful post other than a rant, can anyone provide me with a suggestion for a great tablet that actually supports Linux more than windoze?  Any suggestions appreciated, although it will now have to wait for the next hardware upgrade cycle.
Thanks again Community!
:(

Highly surprised that you post any problems with your Fujitsu and Linux....

I actually installed a dual-boot system to Ubuntu on exactely the same computer you mention on a friends computer....everything just worked, with the exception of some tweaking on the wacom....

I would say the Fujitsu's in my experience make the most Linux compatible computers that I have ever come across...

My wife has the Fujitsu LifeBook T4215 which we will be dual booting to Linux soon also...

I am really not sure what your talking about....

please post your specific problems so others can help you and provide links to all threads that you have posted looking for specific help on....

---

