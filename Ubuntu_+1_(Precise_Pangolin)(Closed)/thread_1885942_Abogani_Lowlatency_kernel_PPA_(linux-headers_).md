---
title: "Abogani Lowlatency kernel PPA (linux-headers ?)"
date: 2011-11-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zika on 2011-11-24
In [https://launchpad.net/~abogani/+archive/ppa]("https://launchpad.net/%7Eabogani/+archive/ppa") , for quite some time, I'm unable to install linux-headers packages (64-bit, if that does matter)... Anyone with the same problem. It seems that it is some dependency round robin case... It seems that kernel image work fine...
Any suggestion for another (modern enough) lowlatency or real-time kernel PPA, aside from compiling kernel for myself (which I did several times)...?

---

### Post by jfernyhough on 2011-11-24
I'm not sure if this is low-latency enough for you, but have you seen Liquorix?

[http://liquorix.net/](http://liquorix.net/)

It's built for Debian based on the Zen kernel config and patches. [http://zen-kernel.org/](http://zen-kernel.org/)

---

### Post by zika on 2011-11-24
> **jfernyhough said:**
> I'm not sure if this is low-latency enough for you, but have you seen Liquorix?

[http://liquorix.net/](http://liquorix.net/)

It's built for Debian based on the Zen kernel config and patches. [http://zen-kernel.org/](http://zen-kernel.org/)
Yes. I use(d) Liquorix kernel for couple of years, as far as I recall. But Liquorix kernel is, as I see it, the opposite side of the scale where lowlatency (rt) kernel is North and Liquorix is South... Liquorix is optimized for speed.
I'll check it again (in documents) but my experience with music using these two kernels is just as I described above...

---

### Post by christophski on 2012-01-03
have you solved this? I have found that the linux-headers-lowlatency and the linux-lowlatency-headers package depend on each other so you can't install one because they other isn't installed, meaning you can't install either at all.

---

### Post by zika on 2012-01-04
> **christophski said:**
> have you solved this? I have found that the linux-headers-lowlatency and the linux-lowlatency-headers package depend on each other so you can't install one because they other isn't installed, meaning you can't install either at all.I've stopped using lowlatency. But, as long as Ubuntu kernel is properly installed (with both headers files OK) (I think and it worked) the only thing needed is image file for lowlatency (and realtime, from the same author...)...

---

### Post by crazy bird on 2012-01-04
Just some questions:
- what's the advantage of using [such kernel]("https://launchpad.net/~abogani/+archive/ppa")?
- why using such kernel?
- where is it for?

---

### Post by christophski on 2012-01-04
I need the header files to install certain packages such as for Virtualbox and Ironhide, which require using the headers to build dkms packages during install. I have messaged abogani on launchpad and am awaiting a reply.

@crazybird:
Low latency and realtime kernels allow for certain processes to essentially jump to the front of the processing queue so that their job can be done quick enough for whatever application the computer is being used for. 
I use a lowlatency kernel for professional audio and recording, where it is essential that audio is processed quick enough that a delay caused by the computer is not noticeable. For example If I have recorded some drums and then want to record a guitar to it, if the latency (time for the audio to be processed) is too high, when I play back what I have recorded, the guitar will not be in time with the drums.

Other applications include running machinery such as a CNC mill and things such as stock exchange computers where time is money.

---

### Post by christophski on 2012-01-05
I have worked out a way to do it. If you don't particularly understand the ;inux file hierachy I wouldn't recommend this though.

Download the headers package for your processor architecture (32 or 64 bit) from here: [https://launchpad.net/~abogani/+archive/lowlatency/+packages](https://launchpad.net/~abogani/+archive/lowlatency/+packages)

and Download the "All" package from here: [http://packages.ubuntu.com/precise/linux-headers-3.2.0-7](http://packages.ubuntu.com/precise/linux-headers-3.2.0-7)

Now you have to open the deb files in Archive Manager, NOT Ubuntu Software Centre. Extract the contents to somewhere and copy the files to their respective directories, then it should all work.

---

### Post by zika on 2012-01-05
> **christophski said:**
> I have worked out a way to do it. If you don't particularly understand the ;inux file hierachy I wouldn't recommend this though.

Download the headers package for your processor architecture (32 or 64 bit) from here: [https://launchpad.net/~abogani/+archive/lowlatency/+packages]("https://launchpad.net/%7Eabogani/+archive/lowlatency/+packages")

and Download the "All" package from here: [http://packages.ubuntu.com/precise/linux-headers-3.2.0-7](http://packages.ubuntu.com/precise/linux-headers-3.2.0-7)

Now you have to open the deb files in Archive Manager, NOT Ubuntu Software Centre. Extract the contents to somewhere and copy the files to their respective directories, then it should all work.That is exactly what I wrote several messages ago.
> **zika said:**
> I've stopped using lowlatency. But, as long as  Ubuntu kernel is properly installed (with both headers files OK) (I  think and it worked) the only thing needed is image file for lowlatency  (and realtime, from the same author...)...
With &#8222;as long as  Ubuntu kernel is properly installed&#8220; I meant up-to-date... We are in Precise sub-Forum and I presume that You have PP installed...
So, for PP users only image file is necessary...
You did not have to extract them manually, simple &#8222;dpkg -i&#8220; was enough...

---

