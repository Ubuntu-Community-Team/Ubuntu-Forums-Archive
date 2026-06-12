---
title: "Setting up finger"
date: 2010-04-18
forum: Server Platforms
---

### Post by WitchCraft on 2010-04-18
Question: When I do finger @kernel.org, I get the below output.

How do I have to configure finger to produce similar output for doing finger @mydomain.com ?

```

root@IS1300:~# finger @kernel.org
[kernel.org]
The latest linux-next version of the Linux kernel is:         next-20100415
The latest snapshot 2.6 version of the Linux kernel is:       2.6.34-rc4-git6
The latest mainline 2.6 version of the Linux kernel is:       2.6.34-rc4
The latest stable 2.6.33 version of the Linux kernel is:      2.6.33.2  
The latest stable 2.6.32 version of the Linux kernel is:      2.6.32.11 
The latest stable 2.6.31 version of the Linux kernel is:      2.6.31.13 
The latest stable 2.6.30 version of the Linux kernel is:      2.6.30.10 
The latest stable 2.6.27 version of the Linux kernel is:      2.6.27.46 
The latest stable 2.4.37 version of the Linux kernel is:      2.4.37.9  
root@IS1300:~# 


```

---

### Post by samosamo on 2010-04-18
Finger is a little before my time so I can't help you but I imagine configuring it is as easy as a google or two.  I did want to ask though: what is the reason you need this?  Finger seems to be available for legacy purposes and in some cases, such as the example you give on kernel.org, it seems to be for vanity purposes as well.

---

