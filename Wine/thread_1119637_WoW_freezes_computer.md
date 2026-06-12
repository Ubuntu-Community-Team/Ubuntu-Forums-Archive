---
title: "WoW freezes computer"
date: 2009-04-08
forum: Wine
---

### Post by Clopin on 2009-04-08
Hello there.

I'm kinda new to Ubuntu, but I've messed around with it before. Well, I installed Wine 1.1.18 and then installed WoW. The installation worked perfectly, but when I play, my computer sometimes freezes (is that what you call "stuttering"?), first time it's for a period of 10-20 seconds, next time it's totally freezed, and I have to reboot.

I've tried various stuff like registry fix, config.wtf editing, disable compiz and a lot more, but no success at all.

I've check the terminal output, but it does not give any errors after I've had the freeze, which I think is weird.

My graphic card is 8800GT and I'm using nVidia 180.44, which I think is the latest. And I'm on 32 bit Ubuntu 8.10

I'm hoping for an explanation.

Thanks
Clopin

EDIT:
My terminal output when running WoW (Before freeze and after freeze, nothing changes).
> moller@moller-desktop:~$ wine "C:\Program Files\World of Warcraft\Wow.exe" -opengl
fixme:advapi:SetSecurityInfo stub
archive Data\enGB\patch-enGB.MPQ opened
archive Data\patch.MPQ opened
archive Data\enGB\patch-enGB-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
archive Data\enGB\expansion-locale-enGB.MPQ opened
archive Data\enGB\lichking-locale-enGB.MPQ opened
archive Data\enGB\expansion-speech-enGB.MPQ opened
archive Data\enGB\lichking-speech-enGB.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39edbc,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x39ebe0,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x39f0b8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f434,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f59c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f150,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df1c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df44,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x37404084) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmReleaseContext (0x30028, 0x134b60): stub
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x39dae4,0x00000000), stub!

---

### Post by billfreeboy on 2009-04-08
Hmm. I don't know about this, but it might need tweaking to make it work right. This chart for example:
[IMG]http://upload.wikimedia.org/wikipedia/commons/7/7c/History_Of_WineAppDB.gif[/IMG]
See the details here: [http://en.wikipedia.org/wiki/Wine_(software)#Functionality]("http://en.wikipedia.org/wiki/Wine_(software)#Functionality")

---

### Post by Clopin on 2009-04-08
> **billfreeboy said:**
> Hmm. I don't know about this, but it might need tweaking to make it work right. This chart for example:
[IMG]http://upload.wikimedia.org/wikipedia/commons/7/7c/History_Of_WineAppDB.gif[/IMG]
See the details here: [http://en.wikipedia.org/wiki/Wine_(software)#Functionality]("http://en.wikipedia.org/wiki/Wine_(software)#Functionality")

Well if that was the case, I'm pretty sure a lot others would have the same problem, but I can't seem to find anybody else with the same problem as me.

---

### Post by Clopin on 2009-04-09
Okay, so I've just tried to uninstall Wine & WoW, and then install again. It was no success, as it freezed once again, but this time it took a long time before it froze.

---

### Post by asdfoo on 2009-04-09
> **Clopin said:**
> Okay, so I've just tried to uninstall Wine & WoW, and then install again. It was no success, as it freezed once again, but this time it took a long time before it froze.

does it still freeze if you start it correctly?

you need to cd into the install directory and then run the main executable

---

### Post by Clopin on 2009-04-09
> **asdfoo said:**
> does it still freeze if you start it correctly?

you need to cd into the install directory and then run the main executable

I've made a shortcut for doing so:
wine "C:\Program Files\World of Warcraft\WoW.exe" -opengl

But I've also tried doing it manually using terminal, no success as well.

---

### Post by Clopin on 2009-04-12
This might be considered as a bump, but I'm really desperate. Im tired of playing on my WinXP laptop.

I've tried looking at my GPU heat while playing WoW, and I'm having an idea, that whenever my GPU goes above 69 celcius (70, 71...) it starts freezing. Could this be correct?
Whenever I start Ubuntu it's on 51 celcius, and when I start playing, it goes very fast to 64-65celcius. And while playing, it goes up to the 70 celcius.
Could this be correct, 'cause I do not think 70 celcius is a lot for a GPU.

---

### Post by asdfoo on 2009-04-12
> **Clopin said:**
> This might be considered as a bump, but I'm really desperate. Im tired of playing on my WinXP laptop.

I've tried looking at my GPU heat while playing WoW, and I'm having an idea, that whenever my GPU goes above 69 celcius (70, 71...) it starts freezing. Could this be correct?
Whenever I start Ubuntu it's on 51 celcius, and when I start playing, it goes very fast to 64-65celcius. And while playing, it goes up to the 70 celcius.
Could this be correct, 'cause I do not think 70 celcius is a lot for a GPU.


this could be it... I don't play WoW but I do l4d or bf1942 and the thermal monitor for my 8800GTS sits around 60-61 from memory

---

### Post by hikaricore on 2009-04-12
Have you checked the heatsync/fan on your video card?
If it's overheating that much it could be clogged with dust.
Lockups could be the least of your worries if you kill your card.

Also you aren't overclocking or anything silly like that are ya?

---

### Post by Clopin on 2009-04-12
> **hikaricore said:**
> Have you checked the heatsync/fan on your video card?
If it's overheating that much it could be clogged with dust.
Lockups could be the least of your worries if you kill your card.

Also you aren't overclocking or anything silly like that are ya?

I've never messed with the BIOS and overclocking. But when I was on Windows XP, the driver had some kind of automatic overclocking utility, but it shouldn't be enabled as I've removed WinXP completely.

---

### Post by hikaricore on 2009-04-12
I meant your video card...

Did you check for dust bunnies?

---

### Post by Clopin on 2009-04-12
> **hikaricore said:**
> I meant your video card...

Did you check for dust bunnies?

Nope, Im not overclocking, as I dunno how to overclock a graphic card. Haven't checkde for dust yet, but I'm sure I just need a better air circulation.
I've ordered a new power supply and case for my computer. I'm sure it will improve it a lot.

---

### Post by hikaricore on 2009-04-12
If you really want to do it right, get a can of compressed air and spray the hell out of everything when you rebuild.
You also might want to consider removing the screws that hold your cpu and gpu fans to their heat-syncs.
These are two major dust clog areas on modern PCs, as the fans and heat spreaders have gotten bigger and have more surface area to hold dust.

Best of luck and let us know how it goes.

---

### Post by Clopin on 2009-04-12
> **hikaricore said:**
> If you really want to do it right, get a can of compressed air and spray the hell out of everything when you rebuild.
You also might want to consider removing the screws that hold your cpu and gpu fans to their heat-syncs.
These are two major dust clog areas on modern PCs, as the fans and heat spreaders have gotten bigger and have more surface area to hold dust.

Best of luck and let us know how it goes.

Thanks for the ideas, I'll see what I can do with it. I'm afraid I have to wait until Tuesday, because of holidays.

---

### Post by hikaricore on 2009-04-12
Btw I just meant to remove those screws temporarily while you clean.  ^_^
I re-read what I posted and didn't want anyone to get any silly ideas.
Always be sure to reassemble things properly. :p

<< Should have slept more last night.

---

### Post by Clopin on 2009-04-13
> **hikaricore said:**
> Btw I just meant to remove those screws temporarily while you clean.  ^_^
I re-read what I posted and didn't want anyone to get any silly ideas.
Always be sure to reassemble things properly. :p

<< Should have slept more last night.

Of course ;). Thanks for your all your replies. When I get my new hardware, should be on Wednesday, I'll write a new reply.

---

### Post by Clopin on 2009-04-18
Okay, so good news:
I bought a new chassi, Aztec Sonata III 500 with a 500 watt power supply. And bought 2x 2gb Kingston Ram.

It now works perfect! :)

---

### Post by hikaricore on 2009-04-18
Fantastic!  Glad to hear you got it all going.

---

