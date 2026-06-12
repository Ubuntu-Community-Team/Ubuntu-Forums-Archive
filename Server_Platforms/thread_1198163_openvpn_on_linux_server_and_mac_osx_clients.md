---
title: "openvpn on linux server and mac osx clients"
date: 2009-06-27
forum: Server Platforms
---

### Post by Linux&amp;Gsus on 2009-06-27
Hi all,
I have a question about how to get OpenVPN over SSL working on Mac clients. What I have so far is the server set up wit OpenVPN and it works perfectly fine with my Linux laptop.

However, I have problems with connecting Macs to it. There seems to be a problem with SSL on the on those Macs, as in no SSL available. To be honest I sort of expected it to be installed and enabled by default. But when I try to connect to the VPN server with [Tunnelblick]("http://code.google.com/p/tunnelblick/") on an OSX 10.4 system I get an error about not being able to connect because of some SSL thing, I have yet to try it with 10.5.

I know that is all a bit vague. Unfortunately I didn't thik of making a screenshot from that error message and I wont have access to a Mac until Monday (which is probably still Sunday for many here).
But I was wondering if there is anything that you folks might now that is a common thing that needs to be done to enable SSL. I searched the web for enabling SSL on Macs but couldn't find any useful info.

Any help is appreciated.
Cheers,
L&G

---

### Post by windependence on 2009-06-27
There's nothing special you have to configure on OS X for SSL, it's already in the OS. You could try a different client. Viscosity is good, but not free, however at $9 I don't think it'll break your bank. I think you have something misconfigured in tunnelblick.

-Tim

---

### Post by Linux&amp;Gsus on 2009-06-27
Thanks for the info. Though I haven't really seen to much config stuff in Tunnelblick but I'll check again. I really only have tried it once on Friday, had very little time.

Just to be on the safe side. Is there any way I can double check that SSL is installed and working? Well, I'm sure there is, so I guess the question is more how can I check that SSL is working correctly.

Cheers,
L&G

---

