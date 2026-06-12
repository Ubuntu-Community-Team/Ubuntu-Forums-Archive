---
title: "3Gb of RAM instead of 4 ??"
date: 2009-04-15
forum: System76 Support
---

### Post by formol on 2009-04-15
hello

I've a strange problem.  in the system monitor in my pangolin, it claim that I have 3Gb of RAM.  But I've 2x2Gb (4093Mb in the bios)

I'm running 9.04 beta now but I tryed with a 8.04.2 live cd and got the same result. 

so, what is that?

thank you

---

### Post by fballem on 2009-04-15
> **formol said:**
> hello

I've a strange problem.  in the system monitor in my pangolin, it claim that I have 3Gb of RAM.  But I've 2x2Gb (4093Mb in the bios)

I'm running 9.04 beta now but I tryed with a 8.04.2 live cd and got the same result. 

so, what is that?

thank you

A couple of questions:

1/ Are you running a 32-bit version of ubuntu. If you are, then 3Gb is the maximum address space that can be handled?

2/ Is your video graphics adapter card using shared memory, in which case, this will reduce the amount of RAM.

Hope this helps,

---

### Post by formol on 2009-04-15
1/ yes, 32 bit version, but, correct me if I'm wrong, but the 3Gb limit is only in windows, in linux, the limit for 32bit is 4GB i think

2/ No, video card have is own memory (nvidia 9200 i think, with 512mb)

but, it strange, I booted a 64bit version of Ubuntu 8.10 with a live-cd and now it's 3.9 Gb...

my research over the internet tend to confirm that the 32bit architecture limit is 4Gb, so if I'm not wrong, I don't know what to think (and to do) about that.

---

### Post by theozzlives on 2009-04-15
So use the 64 bit version....

---

### Post by Vaphell on 2009-04-15
thing is that video adapter memory is in a shared 4GB (2^32) address space iirc. there is not enough addresses to cover both ram and devices. If you want to see whole ram, simply use 64bit version (2^64 -> much greater address space).

---

### Post by damis648 on 2009-04-15
A 32-bit arch supports 4GB *total*, which includes video memory, that reserved for the kernel, etc. so for you it comes out to about 3GB.

---

### Post by formol on 2009-04-15
yeah, it seems so...

and my main computer apparently have the same problem with the 32bit version : 2,5Gb instead 3Gb     (6 x 512 + 512mg in my video pci-x card)

on my file/printer server, running 64bit Ubuntu, the full 3Gb (1x3) is present.

so I guest here is the solution. thanks to all who reply for helping me. 

(the reason why I use 32bit is because it's more simple to use Wine and Flash with 32bit version, but, I will find how to make this stuff work in 64bit...)

---

### Post by fballem on 2009-04-16
> **formol said:**
> yeah, it seems so...

and my main computer apparently have the same problem with the 32bit version : 2,5Gb instead 3Gb     (6 x 512 + 512mg in my video pci-x card)

on my file/printer server, running 64bit Ubuntu, the full 3Gb (1x3) is present.

so I guest here is the solution. thanks to all who reply for helping me. 

(the reason why I use 32bit is because it's more simple to use Wine and Flash with 32bit version, but, I will find how to make this stuff work in 64bit...)

I have been testing 64-bit Jaunty and it's working very well - including Flash and Wine. You may want to look at changing to 9.04 when it's released, although the beta is out now. From past experience, I have been better off with a clean installation when I change versions, but others may have different opinions.

Glad we could help,

---

### Post by jdb on 2009-04-16
> **formol said:**
> 1/ yes, 32 bit version, but, correct me if I'm wrong, but the 3Gb limit is only in windows, in linux, the limit for 32bit is 4GB i think

2/ No, video card have is own memory (nvidia 9200 i think, with 512mb)

but, it strange, I booted a 64bit version of Ubuntu 8.10 with a live-cd and now it's 3.9 Gb...

my research over the internet tend to confirm that the 32bit architecture limit is 4Gb, so if I'm not wrong, I don't know what to think (and to do) about that.

32 bit systems can address 4G but about 1G of that range is reserved for hardware.
A 64 bit system can remap that range above 4G & use it.

jdb

---

### Post by thinman1189 on 2009-04-16
> **formol said:**
> yeah, it seems so...

and my main computer apparently have the same problem with the 32bit version : 2,5Gb instead 3Gb     (6 x 512 + 512mg in my video pci-x card)

on my file/printer server, running 64bit Ubuntu, the full 3Gb (1x3) is present.

so I guest here is the solution. thanks to all who reply for helping me. 

(the reason why I use 32bit is because it's more simple to use Wine and Flash with 32bit version, but, I will find how to make this stuff work in 64bit...)
Flash generally works for me on 64bit. Occasionally I'll have to restart Firefox to get certain things to work, but that may also be attributed to the various script and flash blocking addons that I use. 

Wine, and occasionally native releases, can be a bit of a pain in 64bit but there's plenty of help sites to deal with that. I found that [http://www.64bitjungle.com/tag/workbench/](http://www.64bitjungle.com/tag/workbench/) was very helpful when getting MySQL workbench installed for school. 64bitjungle is usually very good.

---

### Post by 3Miro on 2009-04-16
I have had no problem with wine, just go to their web page (winehq) and add their repository. I am playing a number of 32-bit windows games on my 64-bit Linux Desktop and from what I hear I might be having less trouble than if I was using 64-bit windows.

---

### Post by formol on 2009-04-16
thank you all for your answer.

---

