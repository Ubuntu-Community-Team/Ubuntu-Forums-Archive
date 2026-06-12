---
title: "Bigger Swap File Needed"
date: 2018-10-18
forum: Virtualisation
---

### Post by PatK100 on 2018-10-18
Hi

I have installed VMWare 15 on Ubuntu 18.04 - every time I create a new VM machine I get the message that a swap file of at least 2.6GB is needed and you only have a swap file of 2.0GB - I cannot find a swap file or indeed any method of increasing the size.

I am fairly new to Linux so I would appreciate any help you could give.

I am also experiencing poor performance - could this be the source of that poor performance ?


Many thanks


Pat

---

### Post by sp40140 on 2018-10-18
What are the hardware specification of the host machine? what are the resources you are trying to allocate to guest? What os/version is host and guest?

---

### Post by PatK100 on 2018-10-19
Host I5 8250 with 8GB RAM VM,s Windows 10 with 4GB RAM

---

### Post by sp40140 on 2018-10-19
This is highly unusual. VMWare doesn't usually care about the size of swapfile.
Maybe you should monitor the ram usage over some time for the host os and see if it goes above 4 gig for significant amount of time. Maybe that might make vmware throw that message.
Having said that, check out this page to tweak the swapfile size:

[https://askubuntu.com/questions/927854/how-do-i-increase-the-size-of-swapfile-without-removing-it-in-the-terminal](https://askubuntu.com/questions/927854/how-do-i-increase-the-size-of-swapfile-without-removing-it-in-the-terminal)

---

