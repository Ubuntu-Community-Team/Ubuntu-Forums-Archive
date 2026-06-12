---
title: "Of NICs and Drivers"
date: 2009-05-01
forum: Server Platforms
---

### Post by cyberian22 on 2009-05-01
Hi,

I have a problem. My machine has 2 Intel 82541GI Gigabit NICs, which are run using the e1000 driver. I want to run one of these NICs with the e1000 driver, and the other with another driver (I'm experimenting with different drivers).

Is there anyway to specify different drivers to load for each of the NICs? Currently, when I install and use a driver, it defaults to being used for both the NICs. 

I've tried writing UDEV rules, but they don't seem to be considered upon booting.

Any pointers would be much appreciated. Thanks!

---

### Post by disabledaccount01 on 2009-05-02
Message removed by author.

---

### Post by cyberian22 on 2009-05-13
I tried editing the modprobe config without much success. However, fiddling around with the devfs did work. Link: [http://lwn.net/Articles/143397/](http://lwn.net/Articles/143397/)

---

