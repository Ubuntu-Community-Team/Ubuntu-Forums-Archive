---
title: "SlingPlayer Worked - now Doesn't!"
date: 2009-06-23
forum: Wine
---

### Post by RMOP on 2009-06-23
Months ago, I followed the standard install directions for SlingPlayer (SP) under Unbuntu. It worked fine the first time. Great. But, after some months of disuse, and with a probable Kernel upgrade (or two) in there somewhere, I attempted to run SP again. No joy. Forget THOSE error messages...as I uninstalled/reinstalled SlingBox then Wine multiple times. now I'm left with the following:

"Unable to load local resource. Please reinstall the product."

wine-1.0.1
2.6.27-14-generic

I was so annoyed that I PURCHASED the SymbianOS version of SP -- which works fine, BTW. I'm stuck on how to get SP working again under Ubuntu.

I've avoided posting the verbose output from the terminal from which SP is launched.

Can anyone suggest possibe solutions based upon their own success w this?

Many thanks.

---

### Post by NightMKoder on 2009-06-23
A few suggestions - 

1. update to the latest wine (1.1.24)
2. start with a fresh prefix (rm -rf ~/.wine)
3. reinstall and enjoy if all is well.

---

### Post by RMOP on 2009-07-03
Thanks for the suggestion. I'd already tried that by the time I read your post. Didn't work.

***Did you actually try your own suggestion and find it to work?*** No fault if you didn't, but if you did and it worked, that would be useful information. Since trying later versions of Wine and meeting no success, I've gathered that SlingPlayer doesn't tend to install or run with versions later than 1.1.16.

I ended up installing Wine version 1.1.16 and still meeting no success. Then I decided to try the install script at

[http://www.slingcommunity.com/group/discussion/26840/Slingplayer-Linux-Install-Script-1.0xb/?page=8](http://www.slingcommunity.com/group/discussion/26840/Slingplayer-Linux-Install-Script-1.0xb/?page=8)

***That worked first try.*** I subsequently noted at least on person acheived the same success using Wine 1.1.19. Not really sure what is the latest version of Wine that might work with Andy's script. Or if updating Wine after a successful install of SlingPlay would break things.

But, I'm up and running with a stable version of SP on my eeePC, and am happy enough about it to leave it alone. For now.


> **NightMKoder said:**
> A few suggestions - 

1. update to the latest wine (1.1.24)
2. start with a fresh prefix (rm -rf ~/.wine)
3. reinstall and enjoy if all is well.

---

