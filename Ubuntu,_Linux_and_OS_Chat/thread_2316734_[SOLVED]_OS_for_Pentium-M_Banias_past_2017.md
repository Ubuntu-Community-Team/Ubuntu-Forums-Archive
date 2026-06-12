---
title: "[SOLVED] OS for Pentium-M Banias past 2017?"
date: 2016-03-10
forum: Ubuntu, Linux and OS Chat
---

### Post by MoebusNet on 2016-03-10
It appears many distributions are dropping support for nonpae processors; some even propose dropping 32-bit altogether. Any recommendations for a distro supporting 32-bit nonpae kernels beyond 2017?

---

### Post by sudodus on 2016-03-10
Most Pentium M and Celeron M processors have PAE capability but lack the PAE flag. They can run a PAE kernel, if you use the boot option **forcepae**. See this link.

[Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

I have an IBM Thinkpad T42 with such a Pentium M processor, and I can run the next version, Xenial Xerus, to be released as 16.04 LTS. So have no fear, you will be able to run Lubuntu at least for another three years :-)

If you absolutely want a non-pae kernel, you can install Debian Jessie or ToriOS (the version based on Debian Jessie).

---

### Post by MoebusNet on 2016-03-10
@sodus - Thank you! I've been reading about Debian 8.x, AntiX and even Puppy and if I understood correctly the current versions didn't support nonpae kernels. I used  *forcepae* to install Lubuntu 14.04 and it's working well. It's just that I could not find anything specifically that confirmed nonpae support in any of those I mentioned for current/future versions. Because I run an *buntu OS, I was most concerned with the ability to clean install the new *buntu LTS (being based on Debian); you've assuaged my fears.

---

### Post by MoebusNet on 2016-03-10
@sodus - I read the link, which for Pentium-M instructed to install from the original 15.10 iso which uses a nonpae kernel, and not to install from the 'point' releases which apparently do not. Do we have anything that states that 16.04 will be available with nonpae kernels or the ability to use *forcepae*?

---

### Post by sudodus on 2016-03-10
All Ubuntu flavours of 14.04 LTS and 15.10 have only pae kernels. I am iso testing Lubuntu Xenial (to become 16.04 LTS), and I *know* that the forcepae boot option is there and that it works in my computer with Pentium M. There will be no non-pae kernel in the Ubuntu flavours of 16.04 LTS.

The official documents are not published yet for 16.04 LTS, but you can check with the ***xenial beta1*** and ***xenial daily*** iso files at the testing tracker:

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

I also know that there is a non-pae kernel of Debian Jessie. There is also a PAE kernel (and of course also a 64-bit kernel) of Debian Jessie. ToriOS is using the non-pae kernel of Debian Jessie (in its Debian version).

---

### Post by MoebusNet on 2016-03-10
@sodus - Thank you again!

---

