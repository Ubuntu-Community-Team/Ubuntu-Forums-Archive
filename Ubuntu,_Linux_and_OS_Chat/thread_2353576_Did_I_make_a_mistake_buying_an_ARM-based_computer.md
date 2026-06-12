---
title: "Did I make a mistake buying an ARM-based computer?"
date: 2017-02-23
forum: Ubuntu, Linux and OS Chat
---

### Post by ge96 on 2017-02-23
I like Linux/use it as my primary os primarily because my computers have been garbage so the decrease in resource use. I started out using Linux Mint then Debian, now Ubuntu primarily due to Ubuntu having better support on missing drivers so on installation I don't have to find for example a network driver.

Anyway, I bought this Chromebook which I thought wasn't a bad buy for like $100 with 4GB (I find even 8GB is almost not enough, I used to have 16GB on a desktop), an octa-core processor (what?), and a 1080p screen.

After I bought it I realized it was ARM-based, like "Oh noooo...." after reading how many programs are not "compiled?" for ARM.

What I don't understand, for example Raspberry Pi you can install a LAMP server which is something I have on all of my computers as I am a web developer(using this particular stack).

So this ARM-computer the programs I'm interested in using:

Chromium
Visual Studio Code/Atom (already looked may not be happening)
LAMP web server
Filezilla (I think there is something for this)
pcmanfm (file manager)
gedit (text pad of some kind)
putty (ssh client)
libre office (word/excel)

Also hopefully getting ubuntu on there I can  use i3 the window tiling manager.

I don't know, again I'm hoping I didn't make a mistake on that.

Thanks for any help.

edit: I realize too that I could just search each of these programs and see if they're ARM-supported.

I'm just wondering if there is a work around or something in case. I would feel bad that I just wasted money buying this ARM-computer which aside from the potential lack of software, the bad performance though I realize it's optimized for energy saving not performance.

---

### Post by wildmanne39 on 2017-02-23
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by ge96 on 2017-02-23
Thanks

---

### Post by Olav on 2017-02-23
I am not sure what your question is, exactly.

To determine whether or not it is possible to install Ubuntu/ARM64 on your computer I think you need to mention the brand and type/model. Or if it is one of those brandless Chinese products, you need to be as precise as possible about its specifications.

If installation is at all possible it is unlikely that you will have any problem with availability of software. As far as I know everything in the Ubuntu repositories is available for ARM also. Certainly all the programs you mentioned.

You can check here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

For instance your window manager: [http://packages.ubuntu.com/xenial/arm64/i3/download](http://packages.ubuntu.com/xenial/arm64/i3/download)

---

### Post by ge96 on 2017-02-24
Thanks for your response.

I didn't even think about 'different arm' I just assumed "arm" in general.

It's a Samsung Chromebook 2, I've seen people put Crouton on it and I don't know, I just happened to come across people mentioning ARM and software incompatibility. Had me concerned, thanks. I actually received it in the mail so will be checking it out.

Thanks for the links.

---

### Post by mikewhatever on 2017-02-25
Most of what you want is available in the Ubuntu repositories, if you can manage to install Ubuntu on that particular device. ARM ecosystem is not like Intel's x86, there is no unified platform, every vendor does its own, and the result is many partly compatible or incompatible vendor specific platforms/implementations. That makes it difficult for distros to provide support for multiple ARM devices, as each requires its own custom made image. One reason old Chromebooks are so cheap is the lack of support.

On top of that, kernels updates is a sore point. The Ubuntu provided kernels usually don't work on ARM devices, so the user is stuck with whatever custom kernel is provided by the vendor. And vendors are notoriously indifferent when it comes to provide security updates for their custom kernels. 

Anyway, good luck with that, and keep us posted.

---

### Post by ge96 on 2017-03-04
Hey,

I did come back here just to report pretty much 100% positive news.

I did not decide to install Ubuntu, I was following a tutorial on how to install crouton and went with trusty/xfce4 (primarily because of i3). I didn't even think to install Ubuntu (not preference just followed word for word on the tutorial)

Everything I wanted is installed except Visual Studio code, that one did say in the terminal something along the lines of (ARM not supported).

I also setup a LAMP server on a raspberry pi zero haha (which is also ARM) pretty cool. I was also amazed this version uses less ram (as I was not aware the pi zero only had 512 MB of ram) so it was interesting to see mysql use less than usual.

Anyway, that is too bad about the security update/kernel. I get what you mean with vendor specific, this applies to phones as well where Android itself gets updated but the phone manufacture it's up to them to update the particular device.

I was also not sure, on ChromeBook from my experience/understanding the "terminal" is "part of the browser?" eg. you keep a tab open with the shell-terminal-like window. That's where you start the crouton and then use the commands for me it's like ctrl+alt+shift+back arrow to switch between chrome OS and "linux" (both are linux technically right?)

What I was trying to say was that although I enabled power management, I'm not sure if it's TLP, PowerTop, or PowerStat... but anyway I did enable it, but when you switch to the chrome side I wonder if it keeps running... or does not apply to the chrome os side. I am not sure people said they get 8 hours on this chromebook while the manufacturer claims 8.5... it is somewhat of an older chromebook (2014) with the die size like 48nm I think something relatively high (older). I haven't really measured on my end and I'm trying to be good to the battery by keeping its use between 40-80% the calculator/battery on Chrome OS usually says something like 4 hours left where I rarely charge it to 100%. Usually it does last me a day but I don't use it as often as my desktop.

I do like the 13.3" size laptops, good size. Eventually I think I'll get a Macbook Air but at the moment I am broke haha. A $600+ laptop for me is not an easy buy, I like the ~$100 replaceable computers...

Thanks for the help.

---

