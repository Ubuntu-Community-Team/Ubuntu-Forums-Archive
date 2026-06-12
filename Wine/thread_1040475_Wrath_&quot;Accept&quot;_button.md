---
title: "Wrath &quot;Accept&quot; button"
date: 2009-01-15
forum: Wine
---

### Post by chips.4.u on 2009-01-15
I had this installed once, due to a drive failure... you get the point.

So what I have tried so far is this:
-Installing from the (correctly) mounted DVD
-Installing from files copied over to the Hard drive
-Installing from the Blizzard download installer

All 3 tries resulted in the "Accept" button not activating.
I'm currently using Wine 1.0.1, so I upgraded to the 1.1.12 build and tried all 3 over again, still with no luck.

I have even gone to the extent of using a fresh install of intrepid (after updates) then wine, and then Wrath but that accept button will not activate for me at all.

Others have had luck with the online installer, but its still a no go with me.

I actually solved this not long after posting (sorry didn't need to post).
After a complete wipe of wine. I installed 1.0.1 configured it with 'winecfg' then upgraded to 1.1.12. when I used 'wineprefixcreate' I noticed it disabled gecko html rendering. I used 'wine iexplore [http://www.winehq.org](http://www.winehq.org)' answered yes to install it again. After that Wrath 'Accept' button (with the online installer) was active without scrolling to the bottom of the EULA.

---

### Post by Napoleon85 on 2009-04-28
Thank you so much for this.  I had tried a myriad of other fixes but this was the only one that worked for me.  

I found the information on [this site]("http://www.winehq.org/download/deb") [winehq.org] to be very useful in installing the dev version mentioned above.

---

