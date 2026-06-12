---
title: "Which kernel for HP DL580 G2 ?"
date: 2010-04-02
forum: Server Platforms
---

### Post by dtushing on 2010-04-02
Hi, 

I have a HP DL580 G2 server with 4 x Intel Zeon 2.8ghz and 8gig of RAM. 

Can I run a 64bit kernel and recognize the full 8gig of RAM ?

I've tried a 32bit kernel but I don't think it's seeing past 4gig of  RAM. 

The standard 64bit kernel install give me an error "Kernel requires  x86_64 CPU but only detected i686 CPU"

Thanks in advance for your help.

D

---

### Post by Bachstelze on 2010-04-02
What is the exact Xeon model in the machine? Apparently it is not 64bit, you can use the PAE 32bit kernel to be able to use your 8G of RAM.

---

### Post by dtushing on 2010-04-02
Hi Bachstelze, 

Thanks for your reply. 

I have 4 x Intel Xeon Processor MP at 2.80 GHz \ 2 MB cache. 

I _think_ it's a Paxville MP version.

[http://en.wikipedia.org/wiki/Xeon#7000-series_.22Paxville_MP.22](http://en.wikipedia.org/wiki/Xeon#7000-series_.22Paxville_MP.22)

It does look like it's an only x86 instruction set - and not x86_64, if that's the case 
can my machine address more than 4gig of RAM  ?

Thanks

---

### Post by cascade9 on 2010-04-02
Seems to be not the Paxville (pity, as the Paxville is 64bit capable). I think its actually a Foster MP/Gallatin Xeon in there (@ 2.8 Ghz, you have the Gallatin) 

[http://en.wikipedia.org/wiki/List_of_Intel_Xeon_microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_Xeon_microprocessors)

You will just have to use the PAE kernel to address more than 4Gb. From what I recall, its not that hard to install the PAE kernel. 

BTW, nice sever there ;)

---

### Post by Bachstelze on 2010-04-02
> **cascade9 said:**
> 
You will just have to use the PAE kernel to address more than 4Gb. From what I recall, its not that hard to install the PAE kernel. 

Aye, just

```
sudo apt-get install linux-generic-pae
```

It might even be installed by default on Ubuntu Server.

---

### Post by dtushing on 2010-04-02
Great stuff guys - thanks for your help. Appreciate it. 


D

---

### Post by cascade9 on 2010-04-02
No problems dtushing :) 

> **Bachstelze said:**
> Aye, just

```
sudo apt-get install linux-generic-pae
```It might even be installed by default on Ubuntu Server.

I _think_ it is.

---

