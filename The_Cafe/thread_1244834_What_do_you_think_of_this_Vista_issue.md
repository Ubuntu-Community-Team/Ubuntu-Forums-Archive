---
title: "What do you think of this Vista issue?"
date: 2009-08-19
forum: The Cafe
---

### Post by billdotson on 2009-08-19
[http://support.microsoft.com/kb/971204/](http://support.microsoft.com/kb/971204/)

How does Vista, which is not going to be mounted, have any clue if you cloned it or not? Isn't the MBR and everything cloned? Even more so, I haven't even done anything to this new HP I bought. It has the main partition and the recovery partition. I heard someone on another site talking about how HP also had a Tattoo or something, is that a special hardware DRM for HP computers? Regardless I cannot install Vista SP2 on this brand new HP computer I spent a whole lot of money for. Did Microsoft design it so you couldn't, you know, actually BACK UP your install in case something happened to it, or is this just a bug on their part?

This is absolutely infuriating, a service pack should not be this difficult. This probably will not work as it most likely references specific hardware components but could I find system files for a Vista x64 SP2 and copy them over and then run the SP2 installer or would that just royally botch things?

Oh, and here is another article: [http://news.softpedia.com/news/Vista-SP2-Fails-to-Install-on-PCs-with-Cloned-Disks-or-Partitions-111761.shtml](http://news.softpedia.com/news/Vista-SP2-Fails-to-Install-on-PCs-with-Cloned-Disks-or-Partitions-111761.shtml)

Seriously, this is absurd. Did Microsoft make it so you couldn't have PARTITIONS? Dear lord, is this some scheme to keep people from copying Vista or using any other operating system or god forbid a DATA partition? 

Does any of this have to do with GPT? I really have only heard about it today but I guess it is the replacement for the (well-aged; only four primary partitions, come on?!) MBR.

---

### Post by billdotson on 2009-08-19
I found a fix that worked for me off of another site. Type mmc in the DOS command prompt. Load the computer management snap-in. Then do go to storage > disk management. Right click on the C: drive and mark the partition as active. Note: this worked for me but my rant still stands as the partition and cloning thing still affects a lot of people and it is still absurd.

---

### Post by SoftwareExplorer on 2009-08-19
That could definitely get annoying!

---

### Post by billdotson on 2009-08-20
Seriously, not allowing people with partitions to install a service pack? Intentional or huge error? I vote intentional.

How would Vista know it was being cloned? That doesn't make sense to me. Even more so, would it be able to detect cloning if dd or g4u (ghost 4 unix) did it? They copy at the lowest level possible don't they? On the g4u site it says you can just write empty zeros to the unused space on the partition or drive and then the size would be about the same as the actual data usage when compressed. Is Vista "awake" even when the drive isn't mounted? I bet there are tiny little Microsoft nano-soldiers watching everything and reporting back. Don't believe me? You'll see.

---

### Post by blur xc on 2009-08-20
hmm...  maybe not the same thing, but I have Vista  installed on a partition (dual boot) and in a virtual machine via. virtual box.  Same install dvds, activation number, but receive updates just fine.  It's maybe not 100% kosher, but it is only still installed on my pc (isn't is one license per cpu anyway?)

BM

---

### Post by billdotson on 2009-08-21
It is probably one license per breath you take while using it... :P

---

### Post by Daveski on 2009-08-21
"third-party disk management tools"

Hahahaha ...
<wipes tear from eye>

---

### Post by SoftwareExplorer on 2009-08-21
> **billdotson said:**
> It is probably one license per breath you take while using it... :P
Or so Microsoft wishes. It's a good thing people find way around activation and such, otherwise, I think Microsoft would charge more. (Of course, in a way, one of the ways around activation is Linux)

---

### Post by billdotson on 2009-08-21
Yeah, "third-party tools" is a joke. Shows you how paranoid Microsoft is about you using anything that isn't theirs. Well, unless of course they can bully company "x" into doing what they want. Really, aside from the available applications and the amount of drivers available for Windows (because of how widespread it is) is there really any reason why anyone would prefer it over another operating system? 

Obviously driver support and application choice are hugely important but as far as stability, ease of use, customization options, etc. why would someone choose Windows? Yeah, they make installing programs rather effortless with the *.exe files but as far as I know Apple really markets OS X as an OS where you don't really have to know much to make it run. Ease of use is great if you need to get something done fast but I prefer operating systems that have options. Have ease of use for when you have to finish something fast and have more advanced stuff under the hood you can work with (I don't think batch scripting counts here; as far as I know the bash shell is lot more robust than cmd.exe).

---

### Post by HoKaze on 2009-08-22
Back when I was using Vista (it came pre-installed I'm afraid) I couldn't install SP2 either. It would install then in stage 3 took 16 hours to install (laptop has 4GB RAM and is pretty new o.O') and then when it rebooted it would start again...and again...and again...until we finally got through to a login screen 3 days later and the damn thing was still on SP1.
Needless, to say, I ditched Vista. Microsoft really did screw up with it, it seems.

---

### Post by cascade9 on 2009-08-22
Oh dear, thats a major issue. At first I thought that it might have been aimed at vLite, but apparently no. 

> **billdotson said:**
> Yeah, "third-party tools" is a joke. Shows you how paranoid Microsoft is about you using anything that isn't theirs. Well, unless of course they can bully company "x" into doing what they want. Really, aside from the available applications and the amount of drivers available for Windows (because of how widespread it is) is there really any reason why anyone would prefer it over another operating system? 

Yep, 'me too' people who want to use what everyone else they know uses.

---

### Post by Sidewinder1 on 2009-08-22
Was doing my research on Vista back in 2007 and discovered some of the things that you have mentioned and was appalled! I got very concerned that the next computer I would purchase would have mandatory Vista on it. NFW!  Started looking around; discovered Ubuntu; installed; never looked back.  :-)
Side

---

