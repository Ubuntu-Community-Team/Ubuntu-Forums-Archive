---
title: "Designing a server farm"
date: 2007-06-15
forum: Server Platforms
---

### Post by brooksbp on 2007-06-15
Hey this is a fairly basic question about designing/building a server farm.

We're planning on scaling horizontally (multiple cheap machines) for our web application and I am starting to look over the hardware side of scaling.  We would need roughly 5-9 machines to start off with and could definetly use more 20+ in the future--we are seeing/predicting increased growth.  It would most likely be wise to purchase rack or blade servers.

With that decision, how do you go about accessing video and input to those rack servers?  I understand that once you have applications up and running and connections set that you can just leave all the rack servers without any input devices (mouse, keyboard) and a monitor.  But, what if you need to access the rack servers--each machine individually--fairly often and can't VPN or SSH or virtualize into it?  Are you litterally stuck with a huge rack server infrastructure and forced to buy a couple monitors and keyboards and mice to hook up to the rack servers??  You have to do it that way to get the servers up and running anyways, right?

Thanks for your input.

---

### Post by rickyjones on 2007-06-15
This all depends on the final hardware that you install. For instance, if you install multiple x86 servers (i.e. HP DL380 G3s...) then you can use a standard KVM switch - preferably an IP-based one to allow access over the network. If you are going with Blades then I'm pretty sure that it comes with a special USB cord that gives you KB/Video/Mouse that you can move between blades. Else there is alway the iLO port on them, but that also requires network connectivity.

Hope it helps!

-Richard

---

### Post by brooksbp on 2007-06-15
Ohhhh I see. So you can use either a KVM switch or iLO? What is iLO?  Also, is there any other convenient ways of doing this besides a KVM switch or iLO? or are you just stuck with being forced to remote login--which would be the easiest I presume...

---

### Post by Icidic on 2007-06-16
iLO is a form of remote 'Lights Out' management, particularly useful for Blade servers and what not.  It's generally just a ethernet port that you plug into and can give you Telnet\Console access to the server, possibly more.  I'm not to savvy with it myself really.

VNC and RDP might be worth looking into as well, preferably the latter.  IP-KVM would be your best bet, aside from iLO though.

---

### Post by rickyjones on 2007-06-16
Let me give you an example from where I work: We have racks of HP Blades and HP DL380s (various generations). All our HP servers have the remote iLO ports, just in case we need them. Basically you assign it an IP address and using your web browser it allows you console access just like using VNC. For the DL380s (and similar) we hook everything up to a KVM switch. I'm replacing all ours with Avocent DSR2035s (IP-based KVM switch) so that we have access at the rack and our desks.

Hope that clears it up for you!

-Richard

---

### Post by PilotJLR on 2007-06-16
Also keep in mind most vendors (HP included) requrie a license purchase to enable Remote Console (Desktop) via iLo. This applies to normal rack servers...
For example, if you get a DL380, its iLo card will support only SNMP monitoring and "virtual power" until you give it a license for Remote Deskop.

Blades come with iLo Blade Edition, which has remote console by default. Although a local dongle is possible, iLo is all you ever need for out of band management.

---

### Post by elst on 2007-06-17
If you haven't got it already, get a copy of "The Practice of Systems and Network Administration" by Limoncelli and Hogan. It isn't specifically about server farms, but provides good advice about running a network without losing your sanity, including a section on server rooms.

---

### Post by brooksbp on 2007-06-17
Ah alright. Thanks a ton for all of your responses.  I work as a sole web application developer in a non-tech company.  Also a fulltime student; so trying to learn this on my own--which is super cool, but tiring.  The 'small' web app that I need to scale would require around 5 servers and could scale larger in the future so I guess it's time to learn about server farms and all of that--not to say that learning how to scale web applications (software/hardware) is daunting enough.  

Real world experience coupled with self educating + smart people around you is soooooooo much more interesting and fast-pace than undergraduate life!! Thanks!

---

