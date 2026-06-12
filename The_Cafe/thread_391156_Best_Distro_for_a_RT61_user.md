---
title: "Best Distro for a RT61 user?"
date: 2007-03-22
forum: The Cafe
---

### Post by Frak on 2007-03-22
I'm currently using a Linksys WMP54G wireless chipset and am bound by my Wireless card, unfortunately Ubuntu Dapper doesn't boot, Kubuntu works "sometimes", and as we all know Edgy's RT61 Drivers are damaged, and I've tried feisty, and it recognizes, tries, but never connects. 

Can anybody here suggest a distribution that works out of the box with RT61 Chipsets?  And yes I've tried compiling drivers for my card, and it doesn't even recognize my card even after compilation, besides that Ubuntu not allowing the Ralink Driver sufficient permissions, even though compilation of the driver invoked by me as super user to create the correct directories for installation.  Besides that, I would have to *re*compile it every time I updated my kernel.

Thanks for any suggestions. :guitar:

---

### Post by AndyCooll on 2007-03-22
Although I understand your frustration, I'm not really sure where you're coming from in suggesting conclusively that the RT61 chipset doesn't work. My Belkin PCMCIA card uses the RT61 chipset. True, it is a pain to set up. However, once setup it _isn't_ damaged, it works very well.

:cool:

---

### Post by Frak on 2007-03-22
> **AndyCooll said:**
> Although I understand your frustration, I'm not really sure where you're coming from in suggesting conclusively that the RT61 chipset doesn't work. My Belkin PCMCIA card uses the RT61 chipset. True, it is a pain to set up. However, once setup it _isn't_ damaged, it works very well.

:cool:
Mine isn't damaged either, the drivers corrupted when they were included in edgy.  Seriously though, if you know a distribution, please suggest it, I **can't** get the driver working, and that is the developers work, not mine.

P.S. I am using the v4.1 revision of the WMP54G Wireless card.

---

### Post by skotreed on 2007-04-12
Before you try a new distro!!  

I'm currently running Feisty with a linksys wireless card (RT61).  At first i had the same problem, the card was working according to the system but i could not connect.  The way i got it working was to restart the init.d/networking file.  To do this enter

sudo /etc/init.d/networking restart

into the terminal

it will take a second to run the process but in the end it shout state an IP address.  Once the procedure is done, cclose the console.  Makek sure your network is setup coorectly as far as SSID and WEP are concerned and try to connect to the internet.

Hopefully this should fix the problem.

<<<note>>> I am having to run this process every time i restart the system.

---

### Post by Frak on 2007-04-12
Oh I don't need anymore help, sorry.  I created a script that compiles the driver and installs it manually.

---

