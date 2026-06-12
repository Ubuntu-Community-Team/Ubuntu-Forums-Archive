---
title: "web server hardware (motherboards in particular)"
date: 2007-10-16
forum: Server Platforms
---

### Post by ae+ on 2007-10-16
hello all

i'm about to setup a web / dns server which will mainly be used for development (housing dev versions of client sites etc.). it will be fairly low traffic.

is there anything i should bear in mind in regards to motherboards?
the rest of the box i should be fine with, however i feel a bit clueless when it comes to motherboards...  especially MB's and servers (hence why I am asking here and not hardware). also, we dont want to spend a lot of money either, so no Xeon nonsense  - it doesn't need to be a powerhouse of a machine.

any suggestions would be appreciated. at this stage i am tending towards  the following MB/processor combo based on good desktop reviews (and price). 

CPU AM2 5600+ X2
Motherboard Asus M2N32-SLI deluxe

THANKS!

andrew

---

### Post by James79 on 2007-10-16
If you're going to be using commodity hardware, there really isn't any special consideration required for motherboards. Make sure it has enough SATA/IDE ports for your needs, as well I find onboard lan/video helps a lot towards simplifying things.

More to the point is the nature of the sites you will be hosting. Even an old P2 can be used without incident to house low traffic static html websites, as there is very little overhead. 

Will your site be running php as well (or other scripting languages)? Will the scripts be doing anything cpu intensive (like picture resizing, etc)? Will you be running a large database on the server as well?

If you answered no to most of these questions, then you can probably save yourself some money by getting an even more modest (less power hungry, quieter, etc) system.

I personally use an old celeron 550mhz laptop with a busted screen as my LAMP/ssh server, and it works wonderfully!

---

