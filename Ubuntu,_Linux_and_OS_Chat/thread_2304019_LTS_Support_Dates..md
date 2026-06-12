---
title: "LTS Support Dates."
date: 2015-11-23
forum: Ubuntu, Linux and OS Chat
---

### Post by poorguy on 2015-11-23
hello,

i have always read that ubuntu 14.04 LTS is supported until 04/2019.
i wonder what is up with these dates and how accurate this link.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

perhaps i am not reading this right as it seams ubuntu 14.04.2 LTS  & ubuntu 14.04.3 LTS supported until 08/2016
i am confused can someone explain.

thanks.

---

### Post by sammiev on 2015-11-23
They look correct and much the same [here]("http://www.ubuntu.com/info/release-end-of-life").

---

### Post by deadflowr on 2015-11-23
> **poorguy said:**
> 
perhaps i am not reading this right as it seams ubuntu 14.04.2 LTS  & ubuntu 14.04.3 LTS supported until 08/2016
i am confused can someone explain.

thanks.

It's part of the whole hwe Ubuntu implements for LTS releases.
since 14.04.2,.3,and.4 are based on the kernels/hardware stacks from 14.10, 15.04 and 15.10 respectively, those will need to be upgraded after 16.04 comes out to the 16.04 hardware stack.
See:[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
and an as explained for 12.04: [https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

As 12.04 was the first to do this, it'll be interesting to see what happens with 14.04.
Hopefully they've learned a few things about how to implement it better.
(Quite a few users/posters here did not realize they needed to upgrade the stack)
It's confusing, to say the least.

---

### Post by poorguy on 2015-11-23
it is confusing.
i am always learning something new about ubuntu from this thread.

alright it makes a little bit more sense now as the links help.

thanks for the info and links.

life is good.
the poorguy

---

### Post by grahammechanical on 2015-11-23
The logic seems to be this:

The Linux kernels in Ubuntu 14.10, 15.04 & 15.10 will only get 9 months support because those releases only get 9 months support. So, those same kernels in Ubuntu 14.04.2; 14.04.3 & 14.04.4 will also get the same length of support and no more.

Regards.

---

### Post by poorguy on 2015-11-23
hello,

ok so if i understand it is new release point and new kernel.

would that be correct.

---

### Post by mikodo on 2015-11-23
> **poorguy said:**
> hello,

ok so if i understand it is new release point and new kernel.

would that be correct.

Well kinda. By that I mean, usually that is the case. Case where it is not the case, is like the situation I decided to follow with my new install to 14.04 after leaving 12.04. I had the choice to install 14.04; 14.04.1 or 14.04.2 at the time. I choose 14.04.1 because I had read that kernel would be supported for 5 years by Ubuntu. If I had chosen 14.04.2 it would have upgraded to 14.04.3 and then 14.04.4 and so on in 9 month increments, until it was no longer supported. Very confusing I know and that is what me made look at your thread. I had already had HWE explained to me but, see that it is escaping me now. So I looked to see where I am at to be sure. I ran:


mikodo@mikodo:~$  uname -r
3.13.0-68-generic
mikodo@mikodo:~$ 

and checked [against this]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack"). See the "Update Kernel Release Schedule". 

There are decisions that need to made with LTS, that are not as clear as a new point releases only. Most are only supported for 9 months but, with the cases of 14.04 and 14.04.1 they have the 5 year support, (or the remainder of the 5 year support). I can only assume, that is what is expected for 16.04.x's.

Addendum: The reason I chose 14.04.1 is, that I expected that kernel would support my older hardware. I even checked it with the live cd first and my hardware worked well with it. The .1 release of 14.04 was to enable the hardware enablement for 14.04 and with the newer point releases updates throughout the life span of 14.04. With that, I could reasonably expect that I could have support for my hardware. Also, it would update itself with HWE with that kernel and I would not have do anything myself for that to happen while still supporting my older hardware. So, if I had added newer hardware, I would also have the newest available HWE with it too.

I hope I haven't made things more difficult to understand.

---

### Post by poorguy on 2015-11-23
hey mikodo,

 it seems the 14.04 / 14.04.1 is the real LTS where the 14.04.2 / 14.04.3 are the ones that get the 9 month support and different kernel.
now the  14.04.2 / 14.04.3  will update themselves to the next kernel on its own is that right.

i always wondered when i noticed the kernel change in the info pages and graphs and it is making more sense.

thanks for the info and explaining in detail and yes this can be confusing. 

as stated earlier i am always learning something new from this forum.

thanks.
the poorguy

---

### Post by poorguy on 2015-11-23
hello,

even though this is about LTS one thing i don't understand is why some people choose the "NON LTS" distro over the LTS distro.
i myself prefer the stable LTS and the fact that i wouldn't have do a new install every 9 months.

i have also notice that some ubuntu flavors are LTS but only supported for 3 years so what is up with that.


the poorguy

---

### Post by sammiev on 2015-11-23
> **poorguy said:**
> hello,

even though this is about LTS one thing i don't understand is why some people choose the "NON LTS" distro over the LTS distro.
i myself prefer the stable LTS and the fact that i wouldn't have do a new install every 9 months.

i have also notice that some ubuntu flavors are LTS but only supported for 3 years so what is up with that.


the poorguy

Some people need the latest drivers for their equipment.

---

### Post by poorguy on 2015-11-24
hello sammiev,

i was wondering why and drivers would be a good reason.
do you have to install every 9 months or can you do an upgrade.

the poorguy

---

### Post by sammiev on 2015-11-24
Yes you can upgrade, always back up your data first.

If everything is working and your happy, no need to upgrade unless you reach EOL. :)

---

### Post by poorguy on 2015-11-24
hello sammiev,

do you get a notice saying support is ended and does the upgrade process run smoothly.

---

### Post by sammiev on 2015-11-24
> **poorguy said:**
> hello sammiev,

do you get a notice saying support is ended and does the upgrade process run smoothly.

I usually update a head of time for testing.

I spend most of my time on the Ubuntu Development Release.

---

### Post by poorguy on 2015-11-24
hey everyone,

thanks for all the input and info. 

also HAPPY THANKSGIVING life is good.

the poorguy

---

### Post by flocculant on 2015-11-24
>  i have also notice that some ubuntu flavors are LTS but only supported for 3 years so what is up with that.well, simply - ubuntu has all of canonical to sort it's stuff out - flavours don't :) so it's a people thing, nothing more

---

### Post by poorguy on 2015-11-24
> **flocculant said:**
> well, simply - ubuntu has all of canonical to sort it's stuff out - flavours don't :) so it's a people thing, nothing more

hey flocculant,

thanks.

i often wondered about that and now i know,

thanks again.

---

