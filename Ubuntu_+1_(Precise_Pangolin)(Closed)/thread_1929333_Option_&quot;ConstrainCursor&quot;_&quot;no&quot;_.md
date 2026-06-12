---
title: "Option &quot;ConstrainCursor&quot; &quot;no&quot;  Auto hid Launcher"
date: 2012-02-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Johnny3 on 2012-02-21
My Launcher want come out with auto hid on. DBO said a fix was to put Option "ConstrainCursor" "no"
in your xorg.conf for nvidia users will fix this issue. The only place I can find xorg.conf is ect\x11 and it has this in it. 

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

Is this the file I want to change? If so where do I put
"ConstrainCursor" "no" . Would this be right?

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
        Option "ConstrainCursor" "no"
EndSection

I think I will have to log on as root with gksu nautilus. Do you all think this is right.
Thanks and God Bless Johnny3 65++

---

### Post by Johnny3 on 2012-02-21
Never mind I just did it. By dumb luck it worked. It only is a problem with the n video cards.
Thanks and God Bless johnny3 65++

---

### Post by VMC on 2012-02-21
I read about fixing the launcher with xorg fix, but actually does this do? Is launcher hid until you press against right wall?

---

### Post by mc4man on 2012-02-21
> **VMC said:**
> I read about fixing the launcher with xorg fix, but actually does this do? Is launcher hid until you press against right wall?

The issue with nvidia ..20 & the reveal is supposedly fixed in the new xserver-xorg-core upgrade (1.11.4-0ubuntu4

(haven't tried here yet, I'm back on the ..10 for a bit to see if nvidia is behind or related what I'd term acquired restart/shutdown failure syndrome

---

### Post by Johnny3 on 2012-02-21
> **VMC said:**
> I read about fixing the launcher with xorg fix, but actually does this do? Is launcher hid until you press against right wall?

It fixed it for me. You have to press against the left side. I think it is only a problem with the nVidia drivers. By defalt is is always off you can turn on hid in stting appearance then behavior. Hope you can under stand what I am saying I don't explain thing very well. 12.4 64 bit is working well for me. This was the bigest problem for me because I would eather have to hit the for lack of a better word window's key or leave it showing all the time. 
Good Luck and God Bless Johnny3 65+++

---

