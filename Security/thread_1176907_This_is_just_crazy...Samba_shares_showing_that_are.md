---
title: "This is just crazy...Samba shares showing that are not mine"
date: 2009-06-02
forum: Security
---

### Post by offthegrid2 on 2009-06-02
This is crazy. I'm running 9.04 x86 with ADSL and no router. I started to have smb shares show up that are not mine. They keep the same with one or two being removed or added. 

My question is this a security problem via my ISP? Possibly bots?

Here is a pic.
[http://picasaweb.google.com/lh/photo/ofvZgawiOQP6N_lC5S6UHw?feat=directlink](http://picasaweb.google.com/lh/photo/ofvZgawiOQP6N_lC5S6UHw?feat=directlink)

---

### Post by lensman3 on 2009-06-02
Unless you are running a firewall, such that you don't block ports 135 to 137 and 445 tcp/udp, then samba will see other machines shares.  These shares are probably on your local ISP network (collision domain and network mask).  I would suggest that you block both the incoming and outgoing ports.

That also means that if you are running X11 then ports 6000-6063 are probably being exported.  If you are running NFS then the NFS ports are being exported.  

The ideal firewall block both incoming AND outgoing ports.  Then only turn on those services that you want.

---

### Post by HBBFrum on 2009-06-03
If I didn't know any better, I would say that you are hooked up to an external network and it just isn't forgetting that you leave it.

The 'police' one worried me.

---

### Post by lisati on 2009-06-03
I concur with the advice to check your firewall: if you can see them, then chances are that they can see you!

---

### Post by offthegrid2 on 2009-06-03
Sorry for not knowing how or what to put here. I run shorewall locked down with scans showing my system as stealthily.

I do not even have Samba installed according to synaptic list.

I plugged in a laptop to a friends adsl hardline and it shows the same thing. Only Linux can see it but on windows it is hidden and has to be told to show hidden files.

---

### Post by koenn on 2009-06-03
you have smb client instlled by default, and that's enough to see those shares. I agree with lensman3 that it's most likely windows machines with file sharing turned on (by default) and connected to the internet with no or an extremely permissive firewall. 
Haven't seen this since the nineties, though. I thought people knew by now that filesharing on an internet-connected computer is kinda asking for trouble.

---

### Post by offthegrid2 on 2009-06-03
Thanks to everyone for their replies. 
This just started, the windows shares showing via adsl modem. I have been watching it while refreshing it and new ones appear and old ones disappear only to return in a few minutes.

I live in the boonies and am lucky to even have adsl instead of dial-up, our ISP is only a few years old and small. I give them credit though for knowing what they do not know and doing their best to address security problems,however it seems the average pc user is clueless.

My ISP has disable user accounts ASAP when they detect an infected machine, this however is something entirely new showing up on in the past week or so.

I agree with HBBFrum that the police one concerns me as well, the small township I live a couple of miles from has a very small police department and have been screwed before because of bad security and disconnected for it.

I have been using linux for about 5 years and ubuntu for 3, I still consider myself a newbie. I did the best I could by sending emails with screen shots to my ISP and links to websites dealing with windows OS on how to shut off running services and securing windows machines.

I advise them to buy a butt load of routers and pre-configure them followed by installing them for clients to at the very least attempt to contain the vulnerabilities in windows. Charge them as well.

I'm considering setting up town meetings to address internet security though I am not sure how will it be accepted. I welcome opinions and resource links to help.

They know me as the other OS guy, I'm always harping on how bad windows is.

Thanks again everyone.

---

