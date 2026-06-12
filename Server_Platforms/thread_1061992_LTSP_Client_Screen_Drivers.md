---
title: "LTSP Client Screen Drivers"
date: 2009-02-06
forum: Server Platforms
---

### Post by kwwebb on 2009-02-06
I am running an Ubuntu 8.10 64 bit LTSP server with 32 bit clients.  If I boot up my dell laptop as a client everything works fine.  However, if I boot up on one of the other client machines then the screen is either blank or it comes up in a corrupted black/white sort of screen.

The server has an onboard Intel graphics card.  My laptop has an Nvidia graphics card.  All the clients have ATI cards.  I think one of the following could be the problem:
The display card drivers are not avialable
The resolution/frequency is too high

I have read that LTSP 5 automatically sorts the drivers out somehow.  I'm really not sure, but does anyone know about this problem?  In addition, how would I install ATI drivers on my server/check the drivers on the server.  Also, do you have do re-build the client if the server drivers are updated?

Could someone please help?

Many thanks guys,
Kingsley.

---

### Post by haddog on 2009-02-15
Kingsley. I this is not really a fix but have you tried the Ubuntu 8.04 alternate CD? It comes with an option to install the LTSP server. I have no issues with 8.04. When I did an upgrade to 8.10, thin clents had a hard time connecting or displaying vdeo, if they even connected at all. 

Everything was working fine with 8.04. I even tried a clead install of 8.10. Still no luck. I just went back to 8.04. All the thin clients work from the first boot after install.

---

