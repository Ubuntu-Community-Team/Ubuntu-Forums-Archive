---
title: "Kernel crashes related to nvidia [thread restart]"
date: 2012-04-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by NHclimber on 2012-04-16
[B]Original post by shadowfirebird

Any other Nvidia users having crashes?[/B]             
                                                                I'm getting at  least one crash a day.  Kernel crashes (flashing keyboard lights, total  hang) and X crashes (suddenly being bounced back to login).

I've just seen something in kern.log that suggests Nvidia may be to blame for at least some of this behaviour (emphasis mine):


     ```
Apr 16 12:22:10 blake kernel: [11127.936825] sd 4:0:0:0: [sdb] 31116288 512-byte logical blocks: (15.9 GB/14.8 GiB) 
Apr 16 12:22:10 blake kernel: [11127.938812] sd 4:0:0:0: [sdb] No Caching mode page present 
Apr 16 12:22:10 blake kernel: [11127.938824] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Apr 16 12:22:10 blake kernel: [11127.942811] sd 4:0:0:0: [sdb] No Caching mode page present 
Apr 16 12:22:10 blake kernel: [11127.942822] sd 4:0:0:0: [sdb] Assuming drive cache: write through 
Apr 16 12:22:10 blake kernel: [11127.947834]  sdb: sdb1 
**Apr 16 12:39:12 blake kernel: [12149.628762] NVRM: GPU at 0000:02:00.0 has fallen off the bus. **
Apr 16 12:39:12 blake kernel: [12149.628771] NVRM: os_pci_init_handle: invalid context! 
Apr 16 12:39:12 blake kernel: [12149.628773] NVRM: os_pci_init_handle: invalid context! 

```Anyone else getting this?
I can see two different Nvidia drivers in "additional drivers": the  recommended one, and one with "(post-release updates)(version-current  updates)".   Can anyone tell me about the differences?  

I've just switched back to the earlier, recommended driver.  Will let you know if this appears to make a difference.


**Update:**
It doesn't stop the X crashes, certainly.  I've just had two.  syslog shows:

     
     ```
Apr 16 15:29:33 blake kernel: [ 6987.760289] NVRM: Xid (0000:02:00): 6, PE0001  
Apr 16 15:29:33 blake gnome-session[4862]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.#012 
Apr 16 15:29:34 blake acpid: client 4653[0:0] has disconnected Apr 16 15:29:34 blake acpid: client 4653[0:0] has disconnected 
Apr 16 15:29:34 blake acpid: client connected from 5771[0:0] Apr 16 15:29:34 blake acpid: 1 client rule loaded 
Apr 16 15:29:34 blake acpid: client connected from 5771[0:0] Apr 16 15:29:34 blake acpid: 1 client rule loaded 
```**Update #2:**
The older driver seems worse.  I've had five crashes in the last hour.
                                                                                                                                    *                                              Last edited by shadowfirebird; 2 Hours Ago at 01:21 PM..                                                           *

---

### Post by NHclimber on 2012-04-16
> **NHclimber said:**
> **Any other Nvidia users having crashes?**             
                                                                I'm getting at  least one crash a day.  Kernel crashes (flashing keyboard lights, total  hang)
[...]
Anyone else getting this?

Yes. [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/978342]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/978342")

I think it's related to 3.2.0-22+ kernel + nvidia drivers as well but  have yet to capture the panic.  Doesn't happen for me at all with  nouveau driver.

---

### Post by NHclimber on 2012-04-16
Original post by shadowfirebird

> [I]Yes. [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/978342]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/978342")

I think it's related to 3.2.0-22+ kernel + nvidia drivers as well but  have yet to capture the panic.  Doesn't happen for me at all with  nouveau driver.[/I]
                                 
No, I can't catch the panic, either.  Presumably I should append my logs, as above, to 'your' bug?

---

### Post by NHclimber on 2012-04-16
>  	 	 		 			 				 					Originally Posted by **shadowfirebird** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11848313#post11848313") 				
 				*No, I can't catch the panic, either.  Presumably I should append my logs, as above, to 'your' bug?*
 			 		 	 	 


What kernel ('uname -a') are you on?

I wouldn't yet append your logs -- might just obfuscate the problem when I do finally grab the panic on the debug console.

---

### Post by NHclimber on 2012-04-16
Original post by shadowfirebird
>                                                                       Originally Posted by **NHclimber**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11848374#post11848374")                 
                 [I]What kernel ('uname -a') are you on?

I wouldn't yet append your logs -- might just obfuscate the problem when I do finally grab the panic on the debug console.[/I]
                                 
Damn, too late.  Sorry.  I'd decided it was a stupid question.  Obviously not.  

I'm on 3.2.0-23-generic.

---

### Post by shadowfirebird on 2012-04-17
So now we have >1 restarts of the merged thread.  "LOL", as my daughter would no doubt say.  

Since you managed to get the original posts onto a new thread somehow, I guess I'll post here.

I've been running without Compiz -- in Ubuntu 2D, and now Openbox -- since last night.  No crashes, and I'm still using the proprietary Nvidia drivers.  Worth a try?

---

### Post by NHclimber on 2012-04-17
> **shadowfirebird said:**
> So now we have >1 restarts of the merged thread.  "LOL", as my daughter would no doubt say.  
I saw that.  PITA but bodhi meant well though.

> **shadowfirebird said:**
> Since you managed to get the original posts onto a new thread somehow, I guess I'll post here.

I've been running without Compiz -- in Ubuntu 2D, and now Openbox -- since last night.  No crashes, and I'm still using the proprietary Nvidia drivers.  Worth a try?
I'm going to try to reproduce it today running a firewire console so I can do a memory dump of the kernel log even with unavailable cpu cores. This should be interesting...

---

### Post by Frogs Hair on 2012-04-17
No crashes with kernel 3.3.0.23 , Nvidia Current driver 295.40, and 8 series video card .

---

### Post by mc4man on 2012-04-17
> I can see two different Nvidia drivers in "additional drivers": the recommended one, and one with "(post-release updates)(version-current updates)". Can anyone tell me about the differences? 
Exact same driver source, slightly different .diff applied. Should be no difference between the 2 atm (pre-release

users of the updates version would be informed of  updated non security driver & security packages while the users of the current package would only receive notice of security updates.

---

### Post by shadowfirebird on 2012-04-17
> **mc4man said:**
> Exact same driver source, slightly different .diff applied. Should be no difference between the 2 atm (pre-release

users of the updates version would be informed of  updated non security driver & security packages while the users of the current package would only receive notice of security updates.

That's interesting.  I certainly thought I got a lot more crashes on the 'recommended' driver, but of course that's not exactly scientific.  Thank you.

---

### Post by shadowfirebird on 2012-04-17
> **Frogs Hair said:**
> No crashes with kernel 3.3.0.23 , Nvidia Current driver 295.40, and 8 series video card .

Damn.  Thank you.  That rather suggests it's not something as simple as old nvidia card plus new kernel.

I take it you are running Unity 3D?

---

### Post by IanW on 2012-04-17
Nvidia have acknowledged a bug involving driver 295.40 & older (series 6,7 & 8 cards).
[Linky]("http://www.nvnews.net/vbulletin/showpost.php?p=2546510&postcount=1")

---

### Post by NHclimber on 2012-04-17
> **IanW said:**
> Nvidia have acknowledged a bug involving driver 295.40 & older (series 6,7 & 8 cards).
[Linky]("http://www.nvnews.net/vbulletin/showpost.php?p=2546510&postcount=1")

Thanks for the link. Unfortunately for me, it doesn't apply as I still have 295.33 without the security patch on dual G84s (Quadro FX 570).

---

### Post by shadowfirebird on 2012-04-18
I haven't had a crash for nearly 48 hours now.  I just stopped trying to use window managers that had Compiz.

Whether this would work for anyone else, or whether it actually constitutes a valid workaround, I don't know.   It's sort of like giving up, after all.

(I've actually gone back to Openbox.  The one thing I miss about Unity is the Dash.  But, Openbox certainly would not work on my netbook...)

---

### Post by Ender985 on 2012-04-18
Nvidia user here. I too had random logouts (X crashes judging from your OP) with the proprietary driver jockey recommended me. I am using a standard pangolin Ubuntu install with the default unity, 3.2.0-23-generic kernel, and some compiz settings enabled. Since I'm using this box in a working environment (I know I know xD) I just got rid of the proprietary drivers, and since then everything worked fine in the graphics department. So +1 here for it being a bug on their end.

---

### Post by NHclimber on 2012-04-18
> **shadowfirebird said:**
> I haven't had a crash for nearly 48 hours now.  I just stopped trying to use window managers that had Compiz.

Whether this would work for anyone else, or whether it actually constitutes a valid workaround, I don't know.   It's sort of like giving up, after all.

(I've actually gone back to Openbox.  The one thing I miss about Unity is the Dash.  But, Openbox certainly would not work on my netbook...)

I'm still working on it.

I finally have firewire setup so that I can capture the kernel log after  the machine has died, so now I'm just waiting for the crash.

Unfortunately, I wasn't as careful as I should have been and used jockey  to switch back to nvidia-current from nouveau -- this took the install  up to 295.40. Whoops! So I downgraded to 295.33 from /var/cache, but I'm not sure that the machine is in its original state anymore (besides the firewire-related stuff).

Anyway, after a week with nouveau, I thought it was superior in many respects.  The VT switch is way-fast, it has its own FB driver, and the redraw from suspend isn't broken. Perf-wise though, I have no idea if there's a substantial difference anymore though.

I'm only continuing to work on this, not to improve the nvidia driver, but to make sure that the crash isn't from something else.

---

### Post by cknight725 on 2012-04-24
Same issue here, 5+ crashes this evening trying to watch movies in VLC.  Tried both drivers in Jockey (295.something & 280.13)

Ubuntu 11.10 Oneiric
Kernel: 3.0.0.17-generic
lspci: nVidia Corporation GT216 [GeForce GT 220] (rev a2)

I dunno -- almost seems like it happens more with heating, but its so frequent its nearly impossible to nail down.

---

