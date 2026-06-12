---
title: "problem installing Ubuntu Server 8.04"
date: 2008-04-25
forum: Server Platforms
---

### Post by Data-Base on 2008-04-25
Hello,

we have a VMware ESX 3.5

I tried installing Ubuntu Server 8.04 64Bit (I choose in VMware 65Bit Ubuntu) and it did not work , Ubuntu instillation program gave me a massage telling me that the hardware is not 64Bit !!!


now the other main thing is:

I used the 32Bit CD , change the settings of the guest to use 32bit CPU and everything went OK till I get the step where I can chose the services that I can install so I choose LAMP and SSH Server then when when I go to the next step I get an error message with Red background

> [!!] Select and install software

Installation step failed

..............................
...........................
..................

<Continue>


so what should I do or what did I do wrong ?

check the attached image


Thank you all

---

### Post by FreakerBeaker on 2008-04-27
I ran into this too.  I found that if you burn the cd at too high of a rate, it will fail.  For my own curiosity, I burned the image at 16x.  I would try burning the image using a low speed around 16x and if that fails, one more step below.  If that doesn't solve it, it may be the burning utilitiy.

---

### Post by Data-Base on 2008-04-27
hello,

thank you for your reply, but

I did not burn the image I used it direct in VMware !!

i'll try it with VMware Fusion on my Mac


Thanks

---

### Post by Data-Base on 2008-04-29
Hello

I was able to install the 64Bit :guitar:

I had to go in the servers bios and make enable the Intel Virtualization function in the CPU, so now VMware ESX is able to run 64Bit Guests.

:popcorn:

---

### Post by mkaibear on 2008-05-15
Cheers, Data-Base - solved this problem for me, too.

Blooming Intel and not enabling this automagically :)

---

### Post by Data-Base on 2008-05-15
Glad it helped you too :-)

---

