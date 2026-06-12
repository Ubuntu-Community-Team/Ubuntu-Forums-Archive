---
title: "Blind user starting Edubuntu and Macintosh  lab needs help with setting up all system"
date: 2007-12-27
forum: Server Platforms
---

### Post by ASquared21 on 2007-12-27
Please read this page as I have posted a few different questions on this thread.
Thanks,
From: education pagesBlind user starting Edubuntu and Macintosh lab
Hi,
I want to start a Edubuntu lab with sixteen machines. I am new to Ubuntu and need all the advice I can get. Does anyone have any ideas?
Required for the lab"
16 Cases
2 8-port switches
1 router wit 4-port switch
16 floppy drives
16 ps2 keyboards
1 or 2 ps2 mouses
15 normal speed network cards
1 GB network card
15 sticks of 32 MB ram
1 or two sticks of ram equaling minimum 2 GB
1 monitor
16 power units
1 cd and or dvd drive
16 power cables
1 onboard fan
1 USB 1.0 or 2. card
1 Macintosh computer
1 80 GB hard drive
20 network ethernet cables
16 sound cards with headphones
Thanks,
AWEBSIGHT administrator
AWEBSIGHT web team
________________
Re: Blind user starting Edubuntu and Macintosh lab
Hi,
I plan to use this lab to train blind and visually impaired students in keyboarding and computing.
Thanks,
AWEBSIGHT administrator
AWEBSIGHT web team
__________________
 Re: Blind user starting Edubuntu and Macintosh lab
Hi,
I want to run a web server on a NetVista 2200 (8363). How can I load Gusty on the unit? Also, how can I boot from an LTSP server using another setup of the NetVista?

Any help will be appreciated.
Thanks,
__________________

---

### Post by kesomir on 2007-12-30
You're better off using fewer switches -> ie: a single 24 port gigabit switch rather than 2 x eight port and 1 x four port switches. This will give you the best throughput.

Additionally, Edubuntu sets up best for a new administrator on a server with two network cards in it. It does so as it expects an internet and external card (for bridging to the rest of the network). Later on when things work nicely, you could play with combining the cards on the internal interface to double your bandwidth. (Not really an issue depending on what you're going to be running for visually impaired students).

- I have no experience working with macintosh machines and ubuntu. However LTSP should work with anything that can PXE boot from a network card - if the mac can do this, that's all you need <IF> you can sort out an architecture build on the LTSP server -> might be easiest with seperate network interfaces? -> Read up on the LTSP pages to get a good idea and subscribe to the edubuntu mailing list - links can be found in searches of these forums.

Best of luck.

---

### Post by ASquared21 on 2007-12-30
Hi,
I wasn't aware that a 24-port switch was on the market. Does anyone know how much one would cost and where I could obtain one?

I'm not sure if I was clear about the purpose of the Macintosh desktops, but they are to provide the desktop enviornment, aplications and things of that nature.
Thanks,

---

