---
title: "Fixed Starling Wireless Issue"
date: 2011-01-10
forum: System76 Support
---

### Post by macabrem on 2011-01-10
For those of us on here that want to use a System 76 Starling with the rtl8187 wireless driver issue (Star 1 for sure) with another OS (since the System 76 driver can't be run on another OS), I found a solution.

I posted a question to damentz, the guy involved with the Liquorix Kernel over at the Tech Patterns forum.  I wasn't sure if there was anything on the kernal side that could be done to fix this since I was pretty sure my driver worked under an old kernel.
   Here's what he suggested: > 
You might want to try building the wireless driver from the newest bleeding edge archive of compat-wireless: [http://wireless.kernel.org/en/users/Download#Where_to_download_bleeding_edge](http://wireless.kernel.org/en/users/Download#Where_to_download_bleeding_edge)
I use this for my wireless card since the version in the stable kernels typically doesn't work or work well enough to let me do anything useful. Let me know if this works for you.

This solution worked perfectly.  I'm more intermediate than advanced with Linux, and I had no problems building the wireless driver.

I can now use my Starling with another OS and get terrific range with my wireless (at least across the street if not further).

Use at your own risk.  I just wanted to point this out.  I love my Starling, and I appreciate what System 76 does for the Linux community.  I just chose not to stick with Ubuntu and I thought others might appreciate this solution.

---

