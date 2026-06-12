---
title: "Hardy, LTSP and Wyse Winterm"
date: 2008-08-21
forum: The Cafe
---

### Post by Bill259 on 2008-08-21
Hi all,

I notice the tagline for this forum is 'stuff that repeatedly comes up' and I imagine that this might be such stuff.

I set up Hardy with LTSP last night, stunningly simple (*), set my HP laptop (WinXP home on it) to PXE boot, it connected first time, loaded a desktop, allowed me to log in, and everything worked swimmingly.

I've a number of Wyse WinTerm 3150SE machines that I'd like to be able to use.  They're capable of PXE boot and the first one I plugged in connected ok, did the cylon thing briefly, then displayed the ubuntu load screen and the progress bar filling from left to right.  It stopped five blocks from the right.  Nothing else happens.  

Will this ever work and if so what am I doing wrong?  I've seen some forum entries for replacing the WinCE OS on the WinTerm with linux but I thought that PXE pretty much ignored the installed OS and got on with it.  I don't want to go through reflashing the WinTerms.

Any help thankfully received, even if it isn't good news.

TIA,
Bill.

(*) once I'd figured out that the install sets the thin-client network up with 192.168.0.1 as its IP address, which was the same as my Netgear switch.

---

### Post by bodycoach2 on 2008-08-21
I'm going to take a S.W.A.G that is has something to do with the unique embedded processor: 

"AMD Geode GX&#8482; embedded processor with integrated high-speed video"

I'd try the LTSP mailing list to see if anyone has had any success with that processor:

[http://wiki.ltsp.org/twiki/bin/view/Ltsp/Support](http://wiki.ltsp.org/twiki/bin/view/Ltsp/Support)

Let us know if you get it to work.

---

### Post by Dragonbite on 2008-08-21
I would look, like mentioned, that the kernel in the LTSP portion is correct and most of my previous problems came from X which was solved by reducing the color depth (to like 16) and setting a low screen resolution to be tried first.

---

### Post by bodycoach2 on 2008-08-21
Found some more information here:

[http://winterm.gaast.net/main.php/news.html](http://winterm.gaast.net/main.php/news.html)

---

### Post by Bill259 on 2008-08-25
Thanks for the pointers.  I'll post any results back here.

Best,
Bill.

---

