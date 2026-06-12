---
title: "Ubuntu (with desktop) now works on HP stream 7"
date: 2016-07-11
forum: Ubuntu Phone and Tablet
---

### Post by huwwevans on 2016-07-11
Hi all, There was a thread on this a while back:  [http://ubuntuforums.org/showthread.php?t=2261294](http://ubuntuforums.org/showthread.php?t=2261294)

I now have the os working.  And it works pretty well.  

The RPMB issue has been fixed in the latest kernels.  And grub config detects the uefi and forces it to load in a legacy manner.  

I achieved this by installing the 32 bit server iso, booting it using the fedlet efi file.  

Then after 3 days or so of patiently typing into the root console in recovery mode I managed to install the ubuntu-desktop packages.  

With the touch screen and battery indicator working it was then a simple matter to add the hadess driver for the wifi.  

Unfortunately hadess driver slows the tablet right down, however it is perfectly usable.  

only two things not working are sound and cameras.  

Let me know if you need further details of how to reproduce this.

Update,  My test model crashed and won't restart.  I don't think this is an ubuntu issue though.  Most likely the ssd is corrupted by the number of times it crashed or ran out of battery during install.

---

