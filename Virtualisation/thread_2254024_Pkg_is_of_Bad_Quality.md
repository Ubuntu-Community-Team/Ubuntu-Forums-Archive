---
title: "Pkg is of Bad Quality"
date: 2014-11-24
forum: Virtualisation
---

### Post by Rick St. George on 2014-11-24
Attempting to install VirtualBox 4.3.2 for Ubuntu-Trusty.
First I downloaded the Key, and then DKMS.

Then, when intalling, I got the Error "Pkg. is of Bad Quality", along with the following message;

"Lintian check results for /tmp/virtualbox-4.3_4.3.20-96996~Ubuntu~raring_amd64.deb:
warning: collect info strings about package virtualbox-4.3 failed 
warning: skipping check of binary package virtualbox-4.3"

-----------------------

Here is the system. 
Dell Precision 390, has dual 64 bit core, 1 GB Ram, 250 GB SATA HD.
Sound Card: SB Live CT4780
Video Card: ATI Radeon HD 5450, 1GB (hdmi off)
OS: UbuntuStudio v14.04 64 bit

Following Instructions and Download at - [www.virtualbox.org/wiki/Linux_Downloads]("http://ubuntuforums.org/www.virtualbox.org/wiki/Linux_Downloads") 

Any ideas what happened and what I should do next?

Thanks,
Rick
:popcorn:

---

### Post by ibjsb4 on 2014-11-25
Doesn't look installed.  Check it.
```
apt-cache policy virtualbox-4.3
```

---

### Post by kurt18947 on 2014-11-25
Virtual Box is available in the repositories. I don't know about the version.  You might want to check that virtual box is indeed not installed.  I've gotten similar messages using Ubuntu Software Center but the package was still installed.

---

### Post by ian-weisser on 2014-11-25
kurt18947 is right - use the version from the Ubuntu repositories instead.
The package you downloaded says 4.3.2, and looks like it's for 13.04 (raring). Not a good idea to install on a 14.04 system.
The package in the 14.04 repositories is 4.3.10.

How to install the version in the Ubuntu repositories: Use Software Center.

---

### Post by ibjsb4 on 2014-11-25
That raring thing has popped up on mine too, thus I was wanting verification of availability.  The install in the repository looks to be on 4.3.10 and the site is up to 4.3.20, so not much difference in the two.  I have found updating from the site to be dependable 99% of the time, but when you get hit with that 1%, it usually a real killjoy.  So I don't upgrade often.

---

### Post by Rick St. George on 2014-12-01
Thanks Kurt & Ian, the install was successful from the Ubuntu Software Center.

Case closed.
Rick
;-}

---

