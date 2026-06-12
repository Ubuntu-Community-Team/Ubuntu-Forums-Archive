---
title: "Rosegarden/Ardour/Jack Transport"
date: 2011-05-14
forum: Ubuntu Studio
---

### Post by stagekraft on 2011-05-14
Hey All,

I'm sure this has been covered somewhere on the forum, but a search did not bring up what I think I'm looking for.....

I recently installed Rosegarden, and I'm having trouble getting the transport to connect to the transport in Ardour, I know it must be a Jack thing but I'm not sure what connects to what in Jack.

In Jack/connections/alsa tab, I see;

output ports;                              
Ardour
0:control
1:mcu
2:seq

Rosegarden
1:sync out
2: external controller
3:gen midi device

input ports;
Ardour
0:control
1:mcu
2: seq

Rosegarden
1:rec in
2:external controller


So, what connects to what to link the transports?
am I missing something obvious??

Regards,
John

---

### Post by Pablo_F on 2011-05-14
Hi,

You don't have to make any connection via qjackctl. You just have to tell both programs to use the jack transport.

In Rosegarden, Edit, Preferences, General.

In Ardour, top of the Editor window, drop down menu near the clocks.

Cheers, Pablo

---

### Post by stagekraft on 2011-05-17
Thanks Pablo,

Yep, something obvious, right before my eyes.

I was expecting some command line configuration or something, and here it was just a click of a couple buttons.......

Regards, 
John

---

