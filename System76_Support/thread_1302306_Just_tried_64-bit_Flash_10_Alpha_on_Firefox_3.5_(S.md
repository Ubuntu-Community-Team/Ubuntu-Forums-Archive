---
title: "Just tried 64-bit Flash 10 Alpha on Firefox 3.5 (Shiretoko) -- still no joy"
date: 2009-10-26
forum: System76 Support
---

### Post by samalex on 2009-10-26
Hi Everyone,

Over the weekend I noticed that Ubuntu had Firefox 3.5 available to download in the repositories so I downloaded it.  Thus far everything works as it did in 3.0 which was nice to see since I had some custom settings with Shockwave working through Wine and Sun Java in stead of that IcedTea that comes with Ubuntu.

So with Firefox 3.5 installed I decided to try 64-bit Flash 10 Alpha from Adobe once more to see if it would like Firefox 3.5.  Following the instructions posted here by the S76 folks I uninstalled Flash and the wrapper, downloaded 64-bit Flash 10 from Adobe's site, and fired up Firefox 3.5 where it actually loaded faster!  I then went to YouTube and I got excited when a flash movie started to play.  

After about 3 minutes I decided to check out ustream.tv, and 5 seconds after the site loaded Firefox crashed with only the Segmentation Fault error i used to see in FF 3.0 when I tried 64-bit Flash 10 Alpha.  So I opened it back up, went to Hulu, and opening page's Flash intro started playing but 3-4 seconds later FF 3.5 crashed again with the same error.

So I guess either something else on my system isn't liking Flash 10 so I removed it and reinstalled Flash 10 from the Ubuntu repositories with the wrapper which got things back on track.

Anywhoo, just thought I'd share.

Thanks,

Sam

---

### Post by HotShotDJ on 2009-10-27
> **samalex said:**
> After about 3 minutes I decided to check out ustream.tv, and 5 seconds after the site loaded Firefox crashed with only the Segmentation Fault error i used to see in FF 3.0 when I tried 64-bit Flash 10 Alpha.  So I opened it back up, went to Hulu, and opening page's Flash intro started playing but 3-4 seconds later FF 3.5 crashed again with the same error.Hi Samalex --

I'm using the 64 bit flash in Karmic.  I checked out ustream.tv and was unable to replicate the issue you are having with firefox 3.5.  I'm wondering if it might be a configuration problem in firefox.  Try renaming your ~/.mozilla folder to ~/.mozilla.bak and then restart firefox 3.5.  This will give you a clean profile to test.  See if the problem persists.

---

