---
title: "Severe security breach over three months- need Linux-experienced eyes to help"
date: 2013-09-09
forum: Security
---

### Post by jon20 on 2013-09-09
Please forgive me if this doesn't belong here- I do run Ubuntu/Kubuntu as my primary daily OS, so I feel a bit at home here to ask this....

I'd appreciate any help in sorting all of this out... I've gotten way too far into the forest to be objective at this point. Normally I'm someone who has multiple purpose-built machines running at any given time of day. Now I've been cut off at the knees by this malware/hacking problem to the extent that for three months I've had zero functional systems. Here is the deal: 


It started out with a rootkit. Noticed some strange activity during a benchmark run on a clean install with all possible windows services turned off, right down to the CD driver. Nuked the drive and still there. Reflashes BIOS and all firmware, still there. Spent three months now trying to erraticate it from the hardware, but it's there no matter what. Not sure if it's bios or firmware or ?, but it's somewhere in non-volatile memory aside from the drives in any OS environment. Strange, but okay.


Next came the Android part. My tablet started having unusual generic icons show up on the desktop, which were for programs I didn't recognize. The read-me and license files were all filled with scripts to keylog and steal photos, video and audio from the microphone. Couldn't clear it off without rooting it, so just tossed it since it was an econo tablet to start with. Then it got really good. My cellphone, my NON-smartphone cellphone got hacked. SMS texts were being intercepted and altered or blocked. Phone calls to the other party at the time would go to voicemail. This may have even carried over to the home phone which is on the same coaxial line as my interenet, but that may be an incorrect charge. 


Next I replaced the cell with a Galaxy, which was promptly infected with the Android virus AND had the same treatment as the previous phone. Didn't ever connect to the home network or even use the wifi period. Exchanged this twice now. Should mention I've also exchanged my own router for two different modem/router combo units from the cable co during this time. Whatever is going on, it's getting into EVERYTHING with an RF capability in my home and it's not easy to put the f' in it's place. 


Not sure it's related since it's an old house, but there is a distinct, new humming in the computing room from the walls. Could be something far out there like LAN over Powerline I'd suspect, as the outlets in the room are clearly magnetically charged too now? (wtf??)


I'm thinking there are four different scenarios that are likely here.


1) Simply still this insane rootkit at work, propagating itself up to the router where it's then trying to breach anything within range. This seems possible, since everything involved has SOME capacity for wifi networking. 


2) Neighborhood had a punk kid who enjoys hacking move in with a hidden network. Assume based on some odd router activity (DNS set to 192.168.1.1) that it could be someone rerouting my traffic elsewhere from the computers. Not sure about the phone aspect; perhaps unrelated to the big picture? 


3) Recent ex is having her new boyfriend hack into my stuff. Not really interested in laying out specifics, but there is some motive there and I have no idea if he'd be someone who could do something like this. Can see the scenario where he's simply cloned my SIM card and used my cell to keep screwing with my gear though. Strange activity definitely centers around any contact with her, and she is defensive when I mention the idea beyond what I'd expect. 


4) I suppose it'd be naive to ignore the obvious idea that this could be official business, in which case I'm not going to object too loudly except it's been choking off basic computing tasks. Not someone who has anything criminal to observe, so would have thought this would have passed by now if it's this. Am politically active, so could have painted a target, but this feels way too malicious and not purposeful. 


What I need help with is:


1) How would you go about setting up a network with a new router in this mess of a scenario? Obviously [COLOR=#000000][FONT=verdana]cryptographic [/FONT][/COLOR]strength access codes for the router but what else? Manual port forwarding, static addressing, or ? Would appreciate a link to a tool I could use to create valid IP's for static- the subnet thing isn't super comfortable for me. 


2) Would you guess this is a Who or a What that I'm fight against? Local or remote? 


3) Would you imagine there is a PC configuration, possibly using firewalls and a virtualbox I'd guess, that could survive being leaned on this badly if I cannot trace the source? Was thinking about setting up Kubuntu and Win 7 inside a Kubuntu host and seeing if that keeps a new machine clean. Second option was trying a chromebook for now since the BIOS is not standard and I could run Chr Ubuntu on it. 


4) Anything I'm missing or that you think could help.


Thanks guys, I need whatever I can get.

*edit* know there are certainly some spelling and auto correct errors in there- please forgive them, don't have a actual PC to even post this from and am working with what I've got here.

---

### Post by tgalati4 on 2013-09-09
I would take a roll of tinfoil and fashion a hat to wear at all time.

Seriously, if you are a surveillance target by a national agency, there is not much you can do except move or unplug completely from the grid.

From the amount and variety of intrusions, I would suspect your router/cable modem.  I would get a netgear linux-compatible router and install tomato or dd-wrt and watch your router traffic. 

I would run a Live session of linux (any distro) from a commercially-pressed CD, and install etherape and some other monitor tools and be vigilent.

Then report back what is working and not working.

---

### Post by RavenLX on 2013-09-09
It could be that whatever-it-is is infecting itself on one or more of your devices so that whenever you change out one, if another goes online it automatically infects the new device. A no-win situation. 

1. Unplug everything and wipe out and reconstruct all devices (including updating the firmware - be sure you can do this offline first).

2. Connect the router and only ONE device (not all). Go with tgalati4's suggestions above and watch for any odd activity. 

3. If that doesn't work, contact your ISP and see if something is happening upstream that is sending it to your machine/modem for whatever reason.

4. If #3 doesn't work, then the worst case would be to replace ALL devices with new ones (yes even a new router) and hook up ONLY the new devices and computers. Don't use the same SSID and password for your network. Maybe mirror someone else's SSID that looks like a number and append a "2" to it or something. NEVER hook any of the old (possibly infected) computers/devices to your network ever again. If this is still going on after all new devices, then something definitely is going awry there.

If #4 is unaffordable, I'm not sure what could be done past #3. I hope you won't have to get that far.

---

### Post by coldraven on 2013-09-10
Check your router for open ports, my one had Telnet and FTP open by default! Why?
If in doubt do as tgaliti4 says and buy a new one.
Go here to check: [https://www.grc.com](https://www.grc.com)

---

### Post by tgalati4 on 2013-09-10
[http://www.dd-wrt.com/site/index](http://www.dd-wrt.com/site/index)

[http://www.polarcloud.com/tomato](http://www.polarcloud.com/tomato)

Track the geographic locations of your IP traffic.  If they go to a country that you have not visited, nor intend to visit, then take note and set up some firewall blocking for those IP subnets.  

You need to collect data and narrow down exactly what is going on.  With so many devices and a lot of odd behavior on each, it's difficult to track down what is going on.

---

### Post by ventrical on 2013-09-12
1. How do you know it was a rootkit?
2. What did you do before you noticed this *rootkit*. (ie. did you update the BIOS previously?)

Regards.

---

### Post by jon20 on 2013-09-12
Thanks for the input guys. Anything further would be appreciated as well. 

First thing's first- I've been labeling it a rootkit based on behavior as it was observed. If you are hinting it could be a reoccuring instance of someone from outside the system breaching it, I'd have to think back on that paradigm, but it certainly is not a typical file system virus. It persists across full DBan/KillDisk reformats of SSD or HDD, even inside live environments with old clean discs being used and no hard drive connected whatsoever. It has morphed from simply having DCOM and svchost apps running in the background upon initial startup forward inside windows and "KDev"/"Init" and a mysterious "pulse audio" cloned duplicate service inside Ubuntu to now having the ENTIRE system running inside a virtualbox from boot. Yeah, that's true as crazy as it sounds. Am now only able to install an OS using drivers that fit with a virtualbox, not the actual hardware drivers. 

I'm sure I flashed the BIOS with updates dozens of times after this on each system, but leading up to I most likely had as well. It's just part of the nature of the OC/benchmark hobby that I spent a LOT of time inside the BIOS settings on a regular basis and would even run different versions dependent on what a given benchmark favored for scores, so there was some backward/downgrade flashing along the was as well. I suppose I could have got a file infected from the OS's normal virus and then flashed that infection to BIOS, rather than having had the rootkit move itself there by design? Thinking outloud here. 

Does anyone know if there is a soundcard/driver firmware virus/rootkit out there? Because this definitely knocks down the audio service on any platform 100% of the time, and is running listed as Pulse_Audio on ubuntu, which has me thinking...

Really wish I could piece together where the mobile and wireless/pc components are meshing. I am thinking the android/linux platform has something to do with it. Found notes for a remote access tool in the android phone's help files along with an apache server.

---

### Post by jdog1907 on 2013-09-13
I have simular problems mine started when i was runing win 7 i figured out it came fron a porn package i got threw utorent its a viris /program but also it is operated by a person or people 
i figured out it was a security program to protect children from acessing stuff they didnt need to but it is a little more now it is verry nasty pece of software now i wish i had writen down what i found out because i cant rember the websight i found with the info there are solutions out there one is if u can replace hard drive will temp fix until it gets reinfected ther is a script that will fix it i will let u know once i find more info it is hard with this virus on my back it bitdefender anti mallware software is suposta be able to detect it i dont know for sure i havent got it my self when i tried online the virus/person blocked me so i think it works

---

### Post by ventrical on 2013-09-13
> **jon20 said:**
> Thanks for the input guys. Anything further would be appreciated as well. 

I'm sure I flashed the BIOS with updates dozens of times after this on each system, but leading up to I most likely had as well. It's just part of the nature of the OC/benchmark hobby that I spent a LOT of time inside the BIOS settings on a regular basis and would even run different versions dependent on what a given benchmark favored for scores, so there was some backward/downgrade flashing along the was as well. I suppose I could have got a file infected from the OS's normal virus and then flashed that infection to BIOS, rather than having had the rootkit move itself there by design? Thinking outloud here. 

First rule about updating BIOS. If it is working - DON'T upgrade BIOS! I too am a fellow overclocker. The moment I start to adjust my <jumper free config> I am basically leaving my system open to get pretty well carfunkled .

 
> 
Does anyone know if there is a soundcard/driver firmware virus/rootkit out there? Because this definitely knocks down the audio service on any platform 100% of the time, and is running listed as Pulse_Audio on ubuntu, which has me thinking...

There are some malware removal techniques (can't remember offhand) that will remove embedded firmware malware short of flashng or re-flashing. Sometimes (if this is actually your case) certain PCI cards or components in the chipset will lock the malicious code in.

My suggestions are (for your desktop only) 1. Turn off PC-unplug.. 2. Remove CMOS battery. 3. Remove all adapter cards from slots. (Check also to see if any cards have 'creeped' out of their slots.) 4. Reassemble system.

If you decide to re-flash the BIOS do it with the onboard video without any other PCI/AGP cards installed. Also no hdd.. etc. *note that some hardware failures can and will emulate behaviour that is typical of malware* I had this happen to me with an ATi PCI graphics adapter. Days upon days of malware removal. Changed the card and malware was gone !!

> 
Really wish I could piece together where the mobile and wireless/pc components are meshing. I am thinking the android/linux platform has something to do with it. Found notes for a remote access tool in the android phone's help files along with an apache server.

This sounds more like an anomolous bug and is not related to the prob with your desktop.  

What type of hardware are you using as your desktop?

Regards..

---

