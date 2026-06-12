---
title: "Trying to fully switch to Linux, need info please!"
date: 2021-04-27
forum: Ubuntu, Linux and OS Chat
---

### Post by gordan-vrbanec-vepar on 2021-04-27
Hello!

I'm hoping i can get some info on the programs and hardware i use, and how they work on Linux.
I'd like to run everything i need on Linux, but my previous attempts weren't as successful.
Those were years ago, and i know Linux has gone a long way since then, especially with gaming, so i'm hoping maybe i can get everything else to work.

I'm mainly concerned with how music making software works on Linux.

I use Reaper and plugins like virtual amplifiers and the like for music recording. I have a Focusrite Scarlett 2i4 2nd gen audio interface.
Is it possible to use those on Linux? Most of what i have is written as a VST plugin either for windows or Mac. Is there a way to use those on Linux somehow?
Or would i need to run a Virtual Machine with Windows to use a DAW? And how would that impact latency?
I don't mind doing that btw, i can set up a VM for just music production, it's fine. I'm just worried about latency or stuttering. It's kind of hard to record and mix when you can't hear the mix properly...

Other programs i use are Photoshop, Illustrator, After effects and simmilar. 
I plan on getting Affinity Photo and the rest of their software. Has anyone been able to make those run?

Lastly, i play only one game (Guild Wars 2) and i know it can run on Linux pretty well. So for gaming, i'm not concerned much, there's tons of helpful software that basically automate the process now, and even Steam has Proton now so gaming on Linux was never easier than it is now.
And of course, multimedia on Linux is effortless (web, movies, music), i always liked that. 

My main concern is with music production software.

Thank you for reading, i'm looking forward to hearing what can be done!

---

### Post by CatKiller on 2021-04-27
> **gordan-vrbanec-vepar said:**
> I'm hoping i can get some info on the programs and hardware i use, and how they work on Linux. 

Fire up a live USB and try it. 

>  I use Reaper and plugins like virtual amplifiers and the like for music recording. I have a Focusrite Scarlett 2i4 2nd gen audio interface.
Is it possible to use those on Linux? Most of what i have is written as a VST plugin either for windows or Mac. Is there a way to use those on Linux somehow? 

The DAC will be fine. There is DAW software available that can handle VST plugins, but I've not tried it. Ardour and Muse, I think? 

For low latency audio you'll want to use JACK (to be replaced by PipeWire at some point soon); it's extremely flexible and not especially new-user-friendly. Anticipate needing to take some time to get up to speed. 

> Other programs i use are Photoshop, Illustrator, After effects and simmilar. 
I plan on getting Affinity Photo and the rest of their software. Has anyone been able to make those run? 

Adobe ignore the existence of Linux. I don't believe their software works in Wine.

There is ample software available to do the tasks that you're interested in, but not the specific software that you've listed. Even if you ultimately prefer the software that's available on Linux, you'll have a productivity hit while you learn a new workflow, and there's every chance that you *won't* prefer the software that's available. 

Find some time to have a play. Have a hobby project - rather than something with a deadline - to give your experimentation some structure. The skills you know are mostly transferable; specific knowledge of particular tools is not, really. Your own particular balance between the two is something that you'll have to discover for yourself.

---

### Post by gordan-vrbanec-vepar on 2021-04-27
> **CatKiller said:**
> Fire up a live USB and try it. 

 

The DAC will be fine. There is DAW software available that can handle VST plugins, but I've not tried it. Ardour and Muse, I think? 

For low latency audio you'll want to use JACK (to be replaced by PipeWire at some point soon); it's extremely flexible and not especially new-user-friendly. Anticipate needing to take some time to get up to speed. 

 

Adobe ignore the existence of Linux. I don't believe their software works in Wine.

There is ample software available to do the tasks that you're interested in, but not the specific software that you've listed. Even if you ultimately prefer the software that's available on Linux, you'll have a productivity hit while you learn a new workflow, and there's every chance that you *won't* prefer the software that's available. 

Find some time to have a play. Have a hobby project - rather than something with a deadline - to give your experimentation some structure. The skills you know are mostly transferable; specific knowledge of particular tools is not, really. Your own particular balance between the two is something that you'll have to discover for yourself.

Yeah, i guess i can test it live, though, i always thought that's kind of the bare bones of what the OS can do, not sure i'll be able to test everything, but i'll try it, thanks!

Good to know about VSTs! Thank you, gives me hope! :)

About Adobe, yeah, i'm not married to that software and i'd rather use anything else, but a lot of people use it so i have to as well. If i can use Affinity Photo and Affinity Designer on Linux somehow, that would be great.
The only "adobe specific" program that i can't find a real replacement for is After Effects. 

As for the workflow, i'm adaptable, that's not really a problem for me, as long as the programs have all the tools i need.

---

### Post by ajgreeny on 2021-04-27
I have used musescore in the past successfully, but not being a musician I do everything manually and very slowly.
It does, apparently, work very well with midi keyboards so that me be worth investigating further.

Musescore, if you haven't heard of it, is similar I believe to Sibelius, but I have never seen Sibelius so don't know how they differ.

---

### Post by scorp123 on 2021-04-27
> **gordan-vrbanec-vepar said:**
>  The only "adobe specific" program that i can't find a real replacement for is After Effects. 

DaVinci Resolve maybe? Their Red Hat Linux "RPM" packages can be converted for Ubuntu's "DEB" package format. It's not free software, but compared to what Adobe is charging these days it's dirt-cheap in comparison.

---

### Post by TheFu on 2021-04-27
[https://alternativeto.net/](https://alternativeto.net/) tries to show alternatives based on the name of another program.

Make a list of programs and features that you use. Prioritize them.  Then work through the available native Linux tools, list the features and prioritize them. 

You've made compromises when using the programs on Windows/OSX already - perhaps you didn't realize that because there wasn't any choice in your mind at the time.  Now that you know more, when you look at the Linux options, it is doubtful there is a 1-for-1 replacement.  Also, Linux users will make custom little programs using scripts to extend many of these tools, so it could be that things which required 10 steps before can be automated into 1 step now, thanks to scripting.

Just have the idea of scripting in your mind as you look at the tools.

---

### Post by webaake on 2021-04-27
You should definately go for Reaper! Since a couple of versions ago it has support for LV2 plugins. It has had good support for VST2 and VST3 native plugins for a long while. If you have some Win VST's there are solutions including Wine and some other intermediary plugins. I had Ardour for long while but I find the Reaper community more alive and vibrating and that Reaper have very active developers.

Focusrite 2i4 works very well indeed. Drivers built in the kernel.

Reaper: [https://www.reaper.fm/](https://www.reaper.fm/)

---

### Post by CatKiller on 2021-04-27
> **gordan-vrbanec-vepar said:**
> Yeah, i guess i can test it live, though, i always thought that's kind of the bare bones of what the OS can do, not sure i'll be able to test everything, but i'll try it, thanks!
Just so you're aware, the live installer environment is exactly the same as the one you'll have after you've fresh installed, with a couple of wrinkles: load times will be slower because everything needs to be decompressed before it can be used; it can't use the proprietary Nvidia driver, since then it wouldn't work on non-Nvidia hardware; and you can install whatever applications you want, but they won't persist because the install medium is read-only. There's a way to set it up with persistence, but I've never tried it. Other than that, it's exactly the same.

---

### Post by gordan-vrbanec-vepar on 2021-04-27
> **ajgreeny said:**
> I have used musescore in the past successfully, but not being a musician I do everything manually and very slowly.
It does, apparently, work very well with midi keyboards so that me be worth investigating further.

Musescore, if you haven't heard of it, is similar I believe to Sibelius, but I have never seen Sibelius so don't know how they differ.

Yeah, Musescore is a music notation software like Sibelius. I personally use Guitar Pro, but i'm sure there's alternatives that work. 

I'm more concerend about music recording and production software and plugins.

> **scorp123][COLOR=#000000]DaVinci Resolve maybe? Their Red Hat Linux "RPM" packages can be converted for Ubuntu's "DEB" package format. It's not free software, but compared to what Adobe is charging these days it's dirt-cheap in comparison.[/COLOR][/QUOTE]

Ah yes, Resolve is pretty nice! I didn't try the full version so i don't know how it compares to After Effects, but the free version is basically a 100 times better Adobe Premiere without the crashing! :) 


[QUOTE=TheFu][https://alternativeto.net/](https://alternativeto.net/)[COLOR=#000000] tries to show alternatives based on the name of another program.[/COLOR]

[COLOR=#000000]Make a list of programs and features that you use. Prioritize them. Then work through the available native Linux tools, list the features and prioritize them.[/COLOR]

[COLOR=#000000]You've made compromises when using the programs on Windows/OSX already - perhaps you didn't realize that because there wasn't any choice in your mind at the time. Now that you know more, when you look at the Linux options, it is doubtful there is a 1-for-1 replacement. Also, Linux users will make custom little programs using scripts to extend many of these tools, so it could be that things which required 10 steps before can be automated into 1 step now, thanks to scripting.[/COLOR]

[COLOR=#000000]Just have the idea of scripting in your mind as you look at the tools.[/COLOR][/QUOTE]

I did try some of the alternatives, but unfortunately, when it comes to audio, most plugins are written for windows and there's no real alternative here...
But i'll check it out nonetheless, maybe there's something i missed.

[QUOTE=webaake][COLOR=#000000]You should definately go for Reaper! Since a couple of versions ago it has support for LV2 plugins. It has had good support for VST2 and VST3 native plugins for a long while. If you have some Win VST's there are solutions including Wine and some other intermediary plugins. I had Ardour for long while but I find the Reaper community more alive and vibrating and that Reaper have very active developers.[/COLOR]

[COLOR=#000000]Focusrite 2i4 works very well indeed. Drivers built in the kernel.[/COLOR]

[COLOR=#000000]Reaper: [/COLOR][https://www.reaper.fm/](https://www.reaper.fm/)[/QUOTE]

I'm using Reaper on Windows too, it's awesome! I know it has a native version, but is there a way to use the windows plugins on the linux version as well? Like, some translation layer or whatever? Cause if i can make that work, then i'm all for it!
And awesome info about Focusrite! Good to know it will work in linux! Makes me so happy! :)

[Quote=CatKiller][COLOR=#000000]Just so you're aware, the live installer environment is exactly the same as the one you'll have after you've fresh installed, with a couple of wrinkles: load times will be slower because everything needs to be decompressed before it can be used said:**
> 

Yes, i'm aware, thanks for the heads up! I did try persistence once, and it's ok, but still, not as responsive and as good as having it installed obviously. 

One question though (not directly quoting anyone here, just in general). 
Currently, i'm using my mobile phone usb tethering to connect to wireless (since my wireless is busted). In the meantime until i get a new antenna, is this going to work on Ubuntu? Do i have to install something specific or enable something? 
Cause i can't really get on the internet without it...

---

### Post by scorp123 on 2021-04-27
> **gordan-vrbanec-vepar said:**
>  Currently, i'm using my mobile phone usb tethering to connect to wireless (since my wireless is busted). In the meantime until i get a new antenna, is this going to work on Ubuntu? 

That's something you could test with an Ubuntu Live-USB stick or Live-CD/DVD. While the live session is running, plug-in the USB cable that is attached to your phone (which should be set to USB-tethering) into the computer and then open a terminal and type in this command:

```
sudo dmesg
```

You should see some kind of reaction, e.g. your system telling you that it can see a new network device on the USB port.

When I do that here with my Samsung Galaxy phone (set to USB tethering) and an Ubuntu 20.04 installation I get this:

```

[ 2408.360953] usb 2-1: new high-speed USB device number 5 using ehci-pci
[ 2408.524369] usb 2-1: New USB device found, idVendor=04e8, idProduct=6860, bcdDevice= c.00
[ 2408.524377] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2408.524382] usb 2-1: **[COLOR="#FF0000"]Product: SAMSUNG_Android[/COLOR]**
[ 2408.524387] usb 2-1: [COLOR="#FF0000"]**Manufacturer: SAMSUNG**[/COLOR]
[ 2408.524392] usb 2-1: SerialNumber: xxxxxxxxxxx
[ 2411.285817] usb 2-1: USB disconnect, device number 5
[ 2411.809001] usb 2-1: new high-speed USB device number 6 using ehci-pci
[ 2411.967593] usb 2-1: New USB device found, idVendor=04e8, idProduct=6863, bcdDevice= c.00
[ 2411.967602] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2411.967607] usb 2-1: [COLOR="#FF0000"]**Product: SAMSUNG_Android**[/COLOR]
[ 2411.967612] usb 2-1: Manufacturer: SAMSUNG
[ 2411.967616] usb 2-1: SerialNumber: xxxxxxxxxxxxx
[ 2412.033043] [COLOR="#FF0000"]**usbcore: registered new interface driver cdc_ether**[/COLOR]
[ 2412.038880] rndis_host 2-1:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, xx:xx:xx:xx:xx:xx
[ 2412.045373] [COLOR="#FF0000"]**usbcore: registered new interface driver rndis_host**[/COLOR]

```

In that very moment my desktop's top panel also showed a new "Ethernet" network icon. So there definitely was a reaction and it worked.

So that's something you should definitely be able to test in a Live session too.

---

### Post by gordan-vrbanec-vepar on 2021-04-28
> **scorp123 said:**
> That's something you could test with an Ubuntu Live-USB stick or Live-CD/DVD. While the live session is running, plug-in the USB cable that is attached to your phone (which should be set to USB-tethering) into the computer and then open a terminal and type in this command:

```
sudo dmesg
```

You should see some kind of reaction, e.g. your system telling you that it can see a new network device on the USB port.

When I do that here with my Samsung Galaxy phone (set to USB tethering) and an Ubuntu 20.04 installation I get this:

```

[ 2408.360953] usb 2-1: new high-speed USB device number 5 using ehci-pci
[ 2408.524369] usb 2-1: New USB device found, idVendor=04e8, idProduct=6860, bcdDevice= c.00
[ 2408.524377] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2408.524382] usb 2-1: **[COLOR=#FF0000]Product: SAMSUNG_Android[/COLOR]**
[ 2408.524387] usb 2-1: [COLOR=#FF0000]**Manufacturer: SAMSUNG**[/COLOR]
[ 2408.524392] usb 2-1: SerialNumber: xxxxxxxxxxx
[ 2411.285817] usb 2-1: USB disconnect, device number 5
[ 2411.809001] usb 2-1: new high-speed USB device number 6 using ehci-pci
[ 2411.967593] usb 2-1: New USB device found, idVendor=04e8, idProduct=6863, bcdDevice= c.00
[ 2411.967602] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2411.967607] usb 2-1: [COLOR=#FF0000]**Product: SAMSUNG_Android**[/COLOR]
[ 2411.967612] usb 2-1: Manufacturer: SAMSUNG
[ 2411.967616] usb 2-1: SerialNumber: xxxxxxxxxxxxx
[ 2412.033043] [COLOR=#FF0000]**usbcore: registered new interface driver cdc_ether**[/COLOR]
[ 2412.038880] rndis_host 2-1:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, xx:xx:xx:xx:xx:xx
[ 2412.045373] [COLOR=#FF0000]**usbcore: registered new interface driver rndis_host**[/COLOR]

```

In that very moment my desktop's top panel also showed a new "Ethernet" network icon. So there definitely was a reaction and it worked.

So that's something you should definitely be able to test in a Live session too.

Thank you! I'll try that! :)

---

### Post by mlocik97 on 2021-04-28
99% of software from Windows is not problem to run on Linux thanks to WineHQ... but well, Adobe's products are so ******, that are in 1% of "hardly" working on Windows, and it will not work on Linux...
Well, but I think there are alternatives to a lot of software, that support adobe's file format. You can search on [https://alternativeto.net/](https://alternativeto.net/) if your software doesn't run on Linux.

For gaming there is project called "Lutris" that can run a lot of games, ofc Fortnite is one as well ****** software, that doesn't run under WineHQ. But I had no problem with other games.

Music production software should not be problem, and there are a lot of alternatives, if yes, but I still believe You will be able to run Your apps under WineHQ.

---

### Post by gordan-vrbanec-vepar on 2021-04-28
Just ran the Live USB. As soon as i enabled USB sharing on my phone  Ubuntu recognized the device and connected me to the internet!
I then tried youtube and my audio interface works without a problem!

Off to a great start! :) 


> **mlocik97 said:**
> 99% of software from Windows is not problem to run on Linux thanks to WineHQ... but well, Adobe's products are so ******, that are in 1% of "hardly" working on Windows, and it will not work on Linux...
Well, but I think there are alternatives to a lot of software, that support adobe's file format. You can search on [https://alternativeto.net/](https://alternativeto.net/) if your software doesn't run on Linux.

For gaming there is project called "Lutris" that can run a lot of games, ofc Fortnite is one as well ****** software, that doesn't run under WineHQ. But I had no problem with other games.

Music production software should not be problem, and there are a lot of alternatives, if yes, but I still believe You will be able to run Your apps under WineHQ.

Yeah, i'll search for alternatives. If nothing else, i'll run them in a virtual machine, it should be good enough for that.
Luckily i don't care about Fortnite, i mostly only play Guild Wars 2 and nothing else, and that game works so no problems with that. And yes, Lutris has an installer for it. Weirldy, it works even better on linux with DXVK than native windows hahaha! Vulkan is awesome!

I'm hoping one day Affinity can make their software for linux as well, but if not native, i just hope it can work with WIne. If they manage that, that's all i need. I'd like to be rid of adobe sooner or later, not because it's bad software, but because i dislike their subscription model.

---

### Post by Tadaen_Sylvermane on 2021-04-30
I tried to do away with Windows a number of years ago. Did well for awhile. At the end though I accepted that one needs the proper tool for the job. Can everything you want realistically be done on Linux? Yes most likely. Is some of it more trouble than it should be? Yes in some cases. For me I use Linux for almost everything and I keep a pci passthrough vm available on my desktop for games via Windows. I never had much success with Wine + it's frontends. 

I really believe this is the solid answer for me is the pairing of the two. The raw stability of the underlying linux system on lvm with the availability of Windows software natively (for all purposes). It's a win win.

---

