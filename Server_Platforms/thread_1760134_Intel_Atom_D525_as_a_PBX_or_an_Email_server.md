---
title: "Intel Atom D525 as a PBX or an Email server?"
date: 2011-05-16
forum: Server Platforms
---

### Post by Ron Jones on 2011-05-16
I've got a hankering to upgrade my home PBX from Trixbox on CentOS to SipXecs on Ubuntu 10.04 LTS. 

The current Trixbox setup is running on a Gigabyte G33M-S2 with 2.2 GHz Intel Core 2 duo (There ain't no kill, like overkill). My needs are... ahem... modest, to say the least. The user base is currently five (5) people (all family members)... and would never grow beyond 10.

So, the Intel Atom D525 looks like I could cut down on power consumption. I'm thinking of going with the Gigabyte version found here [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128452](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128452) 

If it works out well, I'm thinking of moving my email server (currently  on Qmail, and showing its age) to a D525 board, and switching to  Postfix.

Has anyone had any thoughts, experiences (good or bad), and/or "gotchas" with the Atom boards as a server (no gui).

Thanks,

---

### Post by spynappels on 2011-05-16
No personal experience with the Atom, but a general rule of thumb I apply to all my Asterisk boxes is max out the RAM as it is cheap. I tend to run at least 4GB RAM on my PBX boxes, but the Atom MoBo can handle 4GB so no worries there.

I've not seen the PBX you are talking about, must have a look at it.

---

### Post by cherva on 2011-05-16
I have configured some PBX servers with asterisk and from my experience that this motherboard with this cpu and 1 gb of ram will be more than enough if you go ubuntu server (no gui) + asterisk. Plus if for some reason it is not ok you can always add + 1GB of RAM :) Also you can run your e-mail server with no problem along with asterisk.

---

### Post by druhboruch on 2011-05-16
It is a nice board, but I would look for one with passive cooling.
Currently I run mail server on Acer H340 and it performs just great.

---

### Post by Ron Jones on 2011-05-17
That is good news!

I've been running Trixbox for about 3 years now on the same box, and whenever I run 'top,' it remains a stead 0.0 across the board (but for the occasional 0.01). 

SipXecs ([http://www.sipfoundry.org]("http://www.sipfoundry.org/")) was the first PBX I tried. Unfortunately, back in early 2008 they didn't have a B2BUA, so it would have meant yet another piece of equipment. Since then, they've added one, so I can migrate now.

I like their interface better than Trixbox. It's cleaner, and easier for me to figure out (or maybe I'm just a little thick lol).

When we moved into our current house, I built a little (100 sq ft) closet so that the server rack, the provider POP, and my reloading equipment remains safe from little hands (I got a good deal on a modular 14U rack from StarCase.com, and some D-200 2U cases from iStarUSA). It's well insulated, so I don't mind a little noise, but I'm really hoping that I can move to more energy-efficient hardware (assuming the payoff is less than the life of the equipment).

If the PBX load remains low, I'll try it with my email server. And if that works out well, I may go whole hog and migrate the web server to an Atom board as well.

---

### Post by elico on 2011-05-17
it's all question of the server load...
how many users on the PBX?and on the MAIL server?some bandwidth statistics of the current system.
also as long your PBX wont use any Hardware features such as ISDN or PRI the ATOM D4XX + sould do the work with no problem.
you will might want to use a more powerful hardware that will give you more options with a little more power consumption.

---

