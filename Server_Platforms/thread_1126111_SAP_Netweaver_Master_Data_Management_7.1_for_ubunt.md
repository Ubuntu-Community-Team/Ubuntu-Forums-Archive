---
title: "SAP Netweaver Master Data Management 7.1 for ubuntu server 8.04 LTS?"
date: 2009-04-15
forum: Server Platforms
---

### Post by klcom on 2009-04-15
Hi, we are finding a documentation or some info for develop one Ubuntu server 8.04.1 LTS with SAP Netweaver Master Data Management 7.1, this software suport RedHat Enterprise, Suse and Solaris. But we want run it over Ubuntu? that is posible? and recomendable?

Thanks a lot of!

:guitar:

---

### Post by ikonia on 2009-04-15
if your library sets meet the requirments of the application it should be possible

eg: if you package requires 

glibc2.X
pango2.X
gtk2.2.X

and your ubuntu vesion has glibc2.X, pango2.X and gtk2.2.X (just using these as examples) then you should be fine in terms of it actually running, what may be a problem is 

a.) support - if SAP don't support it on ubuntu based systems, it will cost an arm and a leg to get support or they may flat refuse

b.) updates if ubuntu updates a package to a version that is not compatible with the product - it will be break and due to point a.) you're stuck in a jam

c.) the packaging - I'm not sure what format the install comes in, but if it's an rpm or a sun package you'll need to extract it and manually drop the files in place and maintain this, which may cause issues with your package manager dependencies later down the line, depending on what's included in the package.

the short answer is - products like SAP are enterprise class and expensive to run this sort of product on an unsupported and non-packaged platform is not a great idea, it may not be a popular response, but run it on, and develop it for platforms that are supported, if you want it packaged for ubuntu - lobby SAP.

---

