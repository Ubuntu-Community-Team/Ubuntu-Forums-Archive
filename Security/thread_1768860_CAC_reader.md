---
title: "CAC reader"
date: 2011-05-27
forum: Security
---

### Post by daniel.cotter on 2011-05-27
When I first bought the system -- my first Linux box in a long time -- it took about 2 days of dabbling (not 2 days straight, just two days of searching before I found all the info I needed) to get my CAC card reader installed and working, and it worked fine on all the sites I need access to.  

That was with 10.10; I have since upgraded to 11.04, and much of what I had installed was gone.  It kept the files and documents I had saved, but  I had to redownload all my programs.  I am trying once again to configure the card reader, but have run into difficulty. (I saved the sites as bookmarks, and have followed the same procedure I used before.)

Firstly, the reader is only recognized intermittently.  When pcsc_scan identifies it, it will get me into some sites, but when it does not, it doesn't function (duh).

Also, coolkey (the package that worked before) will not install properly.  I tried it through synaptic, and it doesn't put the required files where they need to be.  I tried to autoconf, ./configure, make.  Autoconf gives errors about missing elements (I can be more specific if you need the exact errors), configure fails (ditto), and make tells me there is no target.

Another related puzzle is that not every DoD site asks for authentication.  The ones I can get into do, of course, but some don't ask, and give me an automatic authentication error, even at times when I am sure the reader is recognized and working.

I realize I am being extremely vague, but if you get the drift of what I am after and think you can help me, I will supply whatever logs and/or screen dumps that will help.

Thanks in advance, Daniel

---

### Post by ken_23434 on 2011-06-11
The DOD sites that are automatically rejecting you w/out asking for your PIN from your CAC are probably doing that due to past history where you tried that site when the CAC reader wasn't working.

Look for cookies or history files associated w/ those sites and delete them.  Since I don't know what ones would do it (history, cookies, etc...) I would just delete all my internet temp files (not necessarily the best way to do it).

Ken

---

### Post by hellz99 on 2011-06-17
> **ken_23434 said:**
> 

Look for cookies or history files associated w/ those sites and delete them.  Since I don't know what ones would do it (history, cookies, etc...) I would just delete all my internet temp files (not necessarily the best way to do it).


Man, I really hope there's more protection than just setting a cookie to deny.

---

