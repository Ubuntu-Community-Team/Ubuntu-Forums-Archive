---
title: "Adding new hard drive [setup]"
date: 2008-05-28
forum: Server Platforms
---

### Post by Dr Small on 2008-05-28
I have had this 80 GB hard drive setting in my server, ever since I began the thing, and the hard drive had another copy of ubuntu loaded on it. Well, I just reformatted the entire drive to ext3 as hdd1

My current setup is /dev/hdc1 mounted as / at bootup. I want to have /dev/hdd1 mounted as /home at bootup, and eliminate /home which is is hdc1.

So basically my entire system would reside on hdc, and my files (for my fileserver) would reside on hdd.

How can I safely accomplish this?

Dr Small

---

### Post by Dr Small on 2008-05-28
Ok, so what if I mount hdd1 (temporarilly) and copy the structure of /home over to it, rename /home on hdc1 to /home_bak, and add the following to /etc/mtab:
```
/dev/hdd1 /home ext3 rw,errors=remount-ro 0 0
```

I am meerly blindly stumbling around, and hoping that would work. Will it work?

Dr Small

---

### Post by hyper_ch on 2008-05-29
[http://www.psychocats.net](http://www.psychocats.net) 

there's a howto on how you make a seperate home later on. You can apply this 1 : 1. The only difference is you don't partition your disk first but you just mount a new drive there ;)

---

