---
title: "Firefox by far the best browser especially in a Virtual Machine."
date: 2017-04-30
forum: Ubuntu, Linux and OS Chat
---

### Post by lammert-nijhof on 2017-04-30
I have been using the Chrome browser since approx. 2010. Recently I switched to Firefox, because I detected that on 720p YouTube video, Chrome did drop a considerable amount of frames, while Firefox did not drop any frame. That has been the main reason to drop Chrome and start using Firefox. Nowadays I have detected more reasons.

Firefox has always been one of the top browsers, but a new beta feature with respect to the use of HW acceleration will beat the competition by a factor 2. I run my distros, also my main OS as a VM in Virtualbox 5.1.18. I have a AMD Phenom II X2 processor that runs at 3.4GHz with a 6MB cache and my video card is an old 1GB Geforce 8400GS. 

In a VM it could display 720p YouTube videos, but the CPU occupation would run up to 80%-90%. I detected, the not yet by default supported, HW acceleration in Firefox and used it for my host and most of my Guest OSes. In my Guest OSes the CPU load drops to 40%-50% and on some occasions it even dips for minutes below 40%. In the mean time I see my Geforce 8400GS run at max GPU and VRAM frequencies (520MHz and 600MHz).  Firefox is not perfect yet, because the main Firefox window hides all other menus and sub-windows from being displayed, but I expect, that is a relative simple issue to solve. 

My main message is however, that the HW acceleration support in Firefox halves your CPU load in my case to 40%-50% and that beats Opera and Chrome both needing 85%-95%. Note that both browsers have enabled HW acceleration by default. Chrome often produces a pure black screen and I have to abort the VM afterwards. If looking at the nerd statistics provided by YouTube, Firefox did not drop any frame, while both other browsers did drop 10%-25% of the frames running at 720p. I notice the same type of difference using my real HW and will try to give some more details in the coming days.

Good that the open source community beats again the big multinational, probably because they concentrate their effort on the main engine instead of on gimmicks and bling-bling.

---

### Post by LastDino on 2017-04-30
I didn't knew about all this but I prefer firefox as well, mostly because I tend to keep open dozens of tabs over sessions and FF loads/renders each tab separately (As you click on it) and not all at one time like chrome, which makes it start faster than Chrome. Especially if you have slower connection, however, I also like to use Chromium as my 2nd browser. Just like the feel of it.

---

### Post by speedwell68 on 2017-04-30
Interesting.  I used to be a Firefox guy, but I find the interface clunky in comparison with Chrome.

---

### Post by Skaperen on 2017-04-30
what about 1080p and 4k videos?  what about outside a VM?  what about in the cloud?  what about over a VNC connection?

---

### Post by lammert-nijhof on 2017-04-30
@Skaperen: I would say try it, if you want to know. I would be more interested how those browsers would behave using an i5, i7, R5 or R7 processor with a modern graphics card like the GeForce 1060 or the Radeon RX570 or so. They will run the videos without any load problem, but I'm curious how reliable they perform in Virtualbox. I can't try it, because I don't have that equipment. My HW is 8 years old. So I can forget about 4k, my monitor is just able to display 1080p or to be completely honest the limit of my old Fujitsu-Siemens vga display of 22" is 1680x1050 at 60Hz. I don't see much difference between 720p and 1080p, probably because in the past I looked too often at the black and white PAL TV system of 576i at 50Hz. 

I tried 1080p and the Vbox guests will run at that resolution, but I don't remember the CPU load in virtualbox. On my real HW; firefox with 1080p30 runs at 40%-55% CPU load and the video card is maxed out. On 1080p60 the CPU load increases with 20% and it starts dropping frames, probably because my Internet can't cope anymore. On 720p30 the CPU runs at a CPU load of 30%-35% and the video card toggles between 400MHz and 600MHz.
> Measured on Phenom B59 X2 at 3.4GHz, 1GB GeForce 8400GS and Ubuntu 16.04
                    [FONT=fixedsys]Browsers 720p      1080p
Firefox                  33%               50%
Chrome                 53%              68%[/FONT]

 In general Chrome requires 15%-20% more CPU time than Firefox for those YouTube videos.

---

