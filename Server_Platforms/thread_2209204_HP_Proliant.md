---
title: "HP Proliant"
date: 2014-03-04
forum: Server Platforms
---

### Post by Saoud on 2014-03-04
Hello,

I'm thinking of buying a old server instead of building one by myself but u have a few questions.
I will be buying the Proliant ML350 G5, will i be able to install ubuntu server on it? And in the specification[http://h18004.www1.hp.com/products/quickspecs/12475_div/12475_div.PDF](http://h18004.www1.hp.com/products/quickspecs/12475_div/12475_div.PDF)
it says that i can put hdd of max 500GB. Will i havet installing freenas use larger hdd?

and are there any other things i should now about? i want to use raid6 (software of hardware)

---

### Post by TheFu on 2014-03-04
Some older Proliant hardware does not work with 12.04 and later Ubuntu releases.  Do your homework. Search the forums. There is an issue with DL380-something, for example. The problem model WAS in the supported hardware list from Canonical for older releases, but didn't work on newer ones. I don't recall anything about the ML350, but ... google a bunch and be careful.

[http://www.ubuntu.com/certification/make/HP/?query=ml350&category=Desktop&category=Laptop&category=Server&release=12.04+LTS&level=Any](http://www.ubuntu.com/certification/make/HP/?query=ml350&category=Desktop&category=Laptop&category=Server&release=12.04+LTS&level=Any) - that specific model is NOT certified under 12.04. Could be many reasons - just being old means there isn't much incentive for HP to attempt certification. It was certified under 10.04, but things changed vastly after that release.

Many older servers are 
* VERY loud
* not very energy efficient
* not as fast as a current-gen desktop systems
Be careful in your choice, but have fun too!

---

### Post by Saoud on 2014-03-05
thank you very much for your help

---

### Post by nerdtron on 2014-03-05
If you're buying something that old maybe a desktop with i5 or i7 can have better performance, less space, less noise and less power consumption. You can always buy a RAID card if you want or setup software RAID if you want to have protection for hard drive failure.

---

### Post by Saoud on 2014-03-05
Ok. instead of making a new thread I will ask it here.
my second option was to make a sever. I want to keep the cost as low as possible so could someone tell me if the hardware will enough to run as a server

Case:Fractal Design Node 304
motherboard: ASRock E350M1
memory: G.Skill Ripjaws 4GB
power supply: Be quiet! System power 7 300W

the total cost will be around &#8364;200

---

### Post by nerdtron on 2014-03-05
What is the processor and what application would you run on it?
If you are going to make it a file server, I say it is good enough.

---

### Post by Saoud on 2014-03-05
it has a onboard [COLOR=#4D4D4D][FONT=helvetica]AMD E-350 APU (1.6GHz, Dual-Core)

i want to use it as a fileserver and install owncloud and if possible install plex[/FONT][/COLOR]

---

### Post by TheFu on 2014-03-05
Ok - so I own an AMD E-350 APU.  It is sorta slow, but for a pure storage server or simple web server, that doesn't matter too much.  For anything more, get a Core i3 or better CPU. It will run Plex, but doesn't have enough power to transcode for different client device needs.

BTW - that APU sips power - less than 26W for the entire system here with a spinning HDD and XBMC running. I'm using a silent pico-PSU happily.

If you want a server than can handle transcoding or almost any storage ... look up the FreeNAS suggested hardware - most will push a SuperMicro MB.
If you want a server to handle virtualization - Core i5 plus lots-o-RAM; 8-32G is needed.

---

