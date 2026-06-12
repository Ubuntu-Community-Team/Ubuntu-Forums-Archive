---
title: "Installing Ubuntu Server on Xseries 232"
date: 2012-10-03
forum: Server Platforms
---

### Post by Phaze08 on 2012-10-03
So we're installing Ubuntu Server 12.04 on an old server at work....I'm wondering if maybe the server is too old for this release? Its last use was in 1999, but would that matter too much? Ubuntu is pretty light and runs well on older machines. Anyway, it boots from live cd (Sorta) and after a while this error pops up. [https://www.dropbox.com/s/xchexldzo9fuzbb/IMG_20121003_154646.jpg](https://www.dropbox.com/s/xchexldzo9fuzbb/IMG_20121003_154646.jpg)
Anyone know whats with that? Do I need an older version? Is there another problem with the hardware?

---

### Post by hasan.akgoz on 2012-10-04
may be is hardware problem. Try again with CentOS live cd .

---

### Post by jerrrys on 2012-10-04
My googling indicates that machine is running p3 processor(s).  It may not have pae support.

[http://askubuntu.com/questions/117744/how-can-i-install-12-04-on-a-non-pae-cpu-error-kernel-requires-features-not-p](http://askubuntu.com/questions/117744/how-can-i-install-12-04-on-a-non-pae-cpu-error-kernel-requires-features-not-p)

---

### Post by Phaze08 on 2012-10-04
You're right it is a P3. It has two actually lol. So it wouldnt have support for ubuntu at all?

Edit: Never mind, I read the link you gave, thanks. :D

---

### Post by Phaze08 on 2012-10-04
> **hasan.akgoz said:**
> may be is hardware problem. Try again with CentOS live cd .

I've never heard of this, enlighten me?

---

### Post by Phaze08 on 2012-10-04
Ok.....we got Ubuntu 10.10 to install ok but for some reason the lan wont work...Ive never come across this issue before on ubuntu. It could be that the lan just doesnt work on this machine, it was an old server we salvaged but it has 3 lan plugs so Id hope one of them worked lol. I also thought maybe since 10.10 was a little unstable that could be the problem. Since Ive never used xubuntu I thought I'd install the latest version and maybe my lan would work with 2 years worth of updates lol. Weird thing is, when I put in the CD, it just boots Ubuntu and doesnt even try to boot from the live cd. 
I have the machine set to boot from cd first priority.

---

### Post by jerrrys on 2012-10-04
10.10 has reached EOL.  Whether you choose ubuntu or xubuntu go with either 10.04 or 11.10 as suggested in the above link.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Phaze08 on 2012-10-05
Hmmm ok that makes sense thanks lol. 
Ill give it a shot

---

### Post by PyroSamurai on 2012-10-10
As far as your LAN port goes, I had a similar problems with my Dell PowerEdge 2400 when I tried out Mageia 2 on it. I fixed that by installing the the non-free drivers repository. Could be a similar issue?

By the way, I use Lubuntu 10.04 on my server.

---

### Post by Phaze08 on 2012-10-22
Well, it turns out our lan port was bad. (All of 3 of them. Used machines :/ ) But, we had a few laying around and popped one in and its good to go. Unfortunately its 32 bit so we can't build Android on it like we hoped to lol.

---

