---
title: "I made a stupid mistake and found a new way to blow it up."
date: 2012-01-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by JRV on 2012-01-27
I accidentally started Ubuntu Tweak's system cleaner while in the middle of an upgrade.

Oh well, nothing lost, just a test system.

---

### Post by Megaptera on 2012-01-27
ooops!

... what's next on your "Interesting Experiments" list?

I sympathise though, I had a nasty experience the first time I flirted with Bleachbit!!

---

### Post by satanselbow on 2012-01-27
Gotta say Good work :popcorn:

I try and reserve that sort of breakage to mission critical machines only ;)

---

### Post by ventrical on 2012-01-27
> **JRV said:**
> I accidentally started Ubuntu Tweak's system cleaner while in the middle of an upgrade.

Oh well, nothing lost, just a test system.

Nice work!!  We become stronger and wiser when we rip an install. It's the true grit that beta testers are made of .. :)

---

### Post by AlanR8 on 2012-01-27
That takes a special talent!!

Well done and good work. Just the sort of thing I'd do!!!!

---

### Post by jfernyhough on 2012-01-27
My favourite so far was to add Debian Sid repos to my sources.list, forget about pinning, then dist-upgrade.

The process itself completed. Not much worked properly afterwards though. :D

---

### Post by effenberg0x0 on 2012-01-27
> **JRV said:**
> I accidentally started Ubuntu Tweak's system cleaner while in the middle of an upgrade.

Oh well, nothing lost, just a test system.

A killer one :)

With much less style: I had two PC cases side by side. Both are black, same model, and have hotswap HDD drawers. 
One was running Precise and dd to copy one HDD to another. 
The other was installing Precise. 

DD copy ended and I had to remove the hotswap HDD. No need to say more :)

One thing I can tell you after this: The installer is not ready to deal with the removal of /dev/sda during the install to /dev/sda :)

Regards,
Effenberg

---

### Post by kansasnoob on 2012-01-27
When I did this:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

That's exactly why I did everything via CLI :)

Adding a GUI to the top only provides one more way to hose things.

---

### Post by arpanaut on 2012-01-27
> **effenberg0x0 said:**
> One thing I can tell you after this: The installer is not ready to deal with the removal of /dev/sda during the install to /dev/sda :)

Sounds like a bug in Ubiquity.
Did you report it?  :mrgreen:

j/k

---

### Post by kansasnoob on 2012-01-27
> **effenberg0x0 said:**
> A killer one :)

With much less style: I had two PC cases side by side. Both are black, same model, and have hotswap HDD drawers. 
One was running Precise and dd to copy one HDD to another. 
The other was installing Precise. 

DD copy ended and I had to remove the hotswap HDD. No need to say more :)

One thing I can tell you after this: The installer is not ready to deal with the removal of /dev/sda during the install to /dev/sda :)

Regards,
Effenberg

If you remove a drive during installation what would you expect to have happen?

---

### Post by effenberg0x0 on 2012-01-27
> **kansasnoob said:**
> If you remove a drive during installation what would you expect to have happen?

One of these:
- Maybe it would install PP to the BIOS? 
- Maybe the circle or friends would materialise in a tron-matrix way, rip of a pointy piece of PCB and carve machine language to the interior of the case?

(I was just joking...)

Regards,
Effenberg

---

### Post by EchoTech on 2012-01-28
The FIRST time is a learning experience,  the SECOND time is a mistake.

---

### Post by Double.J on 2012-01-28
My sympathies!

While we're comfessing our sins, one of my more stupid slip up's was a multi point attack on Open SUSE;

Whilst installing gentoo from inside ubuntu (I'd done it a couple of times before and got complacent) I'd set up my stage 3 tarball, and gone to bed, the next day I powered on, mounted the gentoo / partition, installed portage, chrooted in, noticed something wasn't right, but couldn't be bothered to work out what - I'd done it over night, thought I'd missed something, so decided to just start over - I re-downloaded the stage 3 and portage tarballs, used the infamous "rm -rf" to clear out whatever I'd borked and start again... rattled on through, got the base system set up and restarted... It was actually a couple of hours before I realised that I'd had my SUSE partition mounted at the time:oops:
> SUSE meet portage...SUSE meet oblivion

The helpful comment from my flatmate - "you know just deleting it would have been quicker"

Live and learn, learn and backup ;)

---

