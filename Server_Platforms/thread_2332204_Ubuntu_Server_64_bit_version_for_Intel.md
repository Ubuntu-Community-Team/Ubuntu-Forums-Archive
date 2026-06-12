---
title: "Ubuntu Server 64 bit version for Intel"
date: 2016-07-29
forum: Server Platforms
---

### Post by ravi20 on 2016-07-29
Hi

We were evaluating the latest 16.04 Ubuntu Server 64 bit OS in a machine with 4 GB RAM and noticed that after installing the Software version displayed as 32 bit OS. 

My question.

If we install in a hardware with more than 4 GB, will it automatically show as 64 bit OS. 

I use this ubuntu-16.04.1-server-amd64.iso on a Intel Server.

Thanks.

---

### Post by slickymaster on 2016-07-29
*Thread moved to **Server Platforms**.*

---

### Post by nikefalcon on 2016-07-29
Welcome to Ubuntu Forums!

> **ravi20 said:**
> 
We were evaluating the latest 16.04 Ubuntu Server 64 bit OS in a machine with 4 GB RAM and noticed that after installing the Software version displayed as 32 bit OS. 

Which "software version" are you referring to? How did you ascertain it? Any command/s that you used or a screenshot would help us understand what exactly you are talking about.

> **ravi20 said:**
> 
My question.

If we install in a hardware with more than 4 GB, will it automatically show as 64 bit OS. 

I use this ubuntu-16.04.1-server-amd64.iso on a Intel Server. 

Well..the instruction length supported by the hardware(32/64bit) is dependent on the processor architecture, and in no way depends on the capacity of the RAM you have installed. I think you might have gotten a few things mixed up...so I'l make no more comments regarding your question until I have more details and understand your situation properly.

Cheers!

---

### Post by PaulW2U on 2016-07-29
> **ravi20 said:**
> If we install in a hardware with more than 4 GB, will it automatically show as 64 bit OS. 

I use this ubuntu-16.04.1-server-amd64.iso on a Intel Server.
ravi20, if you install a 32-bit OS then that is what you will have. Likewise, a 64-bit OS. Please show us the output of:
```
uname -a
```
That will tell us whether you have a 32 or 64-bit OS.

---

### Post by cariboo on 2016-07-29
You need to download and install the AMD64 version. Due to AMD supporting 64bit processors first, the version was named for them but will work on most 64-bit processors. 

```
 inxi -C
CPU:       Dual core Pentium E5400 (-MCP-) cache: 2048 KB
           clock speeds: max: 2700 MHz 1: 2003 MHz 2: 2003 MHz
```

```
uname -a
Linux willy 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by ravi20 on 2016-07-30
Here below the information. We are trying the " ubuntu-16.04.1-server-amd64.iso" in a HP Desktop machine with 4 GB RAM and Intel Core 2 Duo CPU (around 8 years old machine). 

uname - a 

Linux erp 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:06:14 UTC 2016 i686 i686 i686 GNU/Linux




inxi -C
CPU:       Dual core Intel Core2 Duo E8300 (-MCP-) cache: 6144 KB 
              clock speeds: max: 2833 MHz 1: 1998 MHz 2: 1998 MHz

But we would be soon installing this in a Lenovo x3650 M5, Xeon 6C E5-2620v3 2.4GHz Server. 

We need to make this a 64 bit OS Server installation in the new machine.

Appreciate your clarification that when we install the AMD 16.04 version, it will see my CPU capacity and make it a 64 bit OS.

Thanks much for your help in clarifying. Rgds.

---

### Post by nikefalcon on 2016-07-30
> **ravi20 said:**
> Here below the information. We are trying the "  ubuntu-16.04.1-server-amd64.iso" in a HP Desktop machine with 4 GB RAM  and Intel Core 2 Duo CPU (around 8 years old machine). 

uname - a 

Linux erp 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:06:14 UTC 2016 i686 i686 i686 GNU/Linux

Seems like you are running 32-bit linux right now; I wonder how..since you used the amd64 image. :-k

Anyways, if you are interested, you can check if your processor is 64-bit capable with the following:
```
 lshw|grep "\-cpu" -A 9|grep width 
```

---

