---
title: "Occasional screen flicker in Lemur"
date: 2010-07-17
forum: System76 Support
---

### Post by msrinath80 on 2010-07-17
Hi all,

I've been facing this problem since the very beginning on the Lemur. It became more annoying only after I changed to a dark theme. Basically, every few minutes there's this screen flickering that takes place (usually at the bottom of the screen). I did some googling to find that this seems to be a "Lucid Lynx" problem associated with the GMA 4500MHD. Check this[1] link for more information.

For the present, I have added the "i915.powersave=0" to the kernel as suggested in that link. So far I've not seen the flicker. But I'll be sure to report if it relapses. Perhaps the S76 devs should consider including this switch as part of the S76 driver for the Lemur (at least until this bug gets fixed in the intel drivers).

References:
[1] [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/538648?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/538648?comments=all)

---

### Post by thomasaaron on 2010-07-19
I'm doubting it is software related. We've not seen this on any other Lemurs.

If it recurs, though, you might go ahead and contact support...at...system76...dot...com.

---

### Post by msrinath80 on 2010-07-19
Thanks Tom. Since I added that switch, I am yet to see the flicker reproduce. From my end it does look like a software issue :-k I will post again if I see it once more. Let me know if adding that switch is a bad idea?

---

### Post by koenigjm on 2010-07-21
For the record, I am having this issue on my Lemur as well.  

Going to try the fix suggested by msrinath80.

---

### Post by koenigjm on 2010-07-21
Screen flicker has seemingly gone away with the fix referred to by msrinath80!

---

### Post by msrinath80 on 2010-07-21
> **koenigjm said:**
> Screen flicker has seemingly gone away with the fix referred to by msrinath80!

Thanks for confirming the issue koenigjm :) Since adding that switch, I am yet to see any flickers either (fingers crossed).

---

### Post by isantop on 2010-07-22
We also had another customer with this issue over the phone. I recommended it to her, and so far I've yet to hear back with any problems.

---

### Post by h.thomas on 2010-07-31
Hi!

I have had what seems to be the same issue (on my Lemur, which began when I started upgraded to Lucid).  Could someone provide a slightly more detailed description of how to implement the fix described above?  Thanks a lot!

cheers

Hugh

---

### Post by h.thomas on 2010-07-31
Oh, I think I figured it out for myself.  You just add 'i915.powersave=0' after 'GRUB_CMDLINE_LINUX_DEFAULT="quiet splash'
in /etc/default/grub and then run 'sudo update-grub' from the terminal, right?  

cheers

Hugh

---

### Post by msrinath80 on 2010-08-06
Once again, it seems like the problem is Ubuntu-centric. There is no issue with screen flicker in Debian (squeeze).

---

### Post by isantop on 2010-08-06
> **h.thomas said:**
> Oh, I think I figured it out for myself.  You just add 'i915.powersave=0' after 'GRUB_CMDLINE_LINUX_DEFAULT="quiet splash'
in /etc/default/grub and then run 'sudo update-grub' from the terminal, right?  

cheers

Hugh
Yes, that correct, but be sure to add it on the same line, and inside of the quotation marks, so that that line reads:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.powersave=0"
```
exactly.

---

