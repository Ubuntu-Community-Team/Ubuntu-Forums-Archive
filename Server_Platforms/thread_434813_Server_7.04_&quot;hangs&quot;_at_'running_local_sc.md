---
title: "Server 7.04 &quot;hangs&quot; at 'running local scripts'"
date: 2007-05-06
forum: Server Platforms
---

### Post by hbchrist on 2007-05-06
I have an old Compaq P350 running Feisty Fawn 7.04 server. It actually runs very well, and I have been able to convert most server services to it away from a Win2K3 box I was using (DHCP, DNS, Apache, etc).

However, as an experiment, I tried to install gedit as I found vi to be frustrating (nothing against vi, just my personal learning curve issues). Gedit installed, but without the Gnome Desktop, it wouldn't launch, so I completely uninstalled it. So far, so good.

Now, however, when I restart or cold boot the server, everything loads without issue until I see the "Running local scripts /etc/...rc.local" message. At this point, the server does not move to the login prompt, it just holds position on the screen. All of the services I installed *are* working, so the server is still operating at a level I need.

When I press any of the arrow keys, the system then drops to a command prompt. However, sometimes the prompt is all caps, sometimes it isn't. I can then enter commands or make changes as necessary.

I would like to know how I can trace the cause of the "quasi-hangup" and eliminate it. Despite the fact that the server still works, I'm a believer that little idiosyncrasies like this actually indicate potentially bigger issues.

Thanks in advance,
hbchrist

---

### Post by kokoroexchange on 2007-05-07
I'm having the exact same issue except that it started for me from the beginning (after installing the LAMP version of Ubuntu 7.04 for PPC).  I have it running on a Mac XServe PPC G5 Dual 2.3 MHz.  Everything works for me but I keep wondering why it won't advance to the prompt and instead 'sticks' at the 'running local scripts' line??  I always 'push' it forward by pressing return once which brings up the command prompt.

Does anyone have any information about this?

Jason

---

### Post by MetalMusicAddict on 2007-05-07
Hit enter or "Alt" and one of the "F#" keys should get you a prompt.

---

### Post by kokoroexchange on 2007-05-08
Thanks but my problem isn't that I can't get a prompt.  I'm just worried that the 'hanging' at "running local scripts" is indicative of some underlying problem that may cause trouble elsewhere later.  If that isn't the case then I'm fine as I haven't had any operational problems with the server....yet.   Just hoping that I don't have to worry about the 'yet'.  :) 

Jason

---

### Post by lonewolf72 on 2007-05-09
I am also having this issue of Feisty Server "hanging" at "running local scripts".  I have had this issue on two different sets of hardware (installed off of two different sets of media).  Should I be worried?  The desktop install I have done, works beautifully...

---

### Post by OrganicPanda on 2007-05-11
I'm having the same issue, I installed in vmware as part of my research for my uni course and it hangs at that point, the weird thing is that it's a fresh install so there should be no problems right?

---

