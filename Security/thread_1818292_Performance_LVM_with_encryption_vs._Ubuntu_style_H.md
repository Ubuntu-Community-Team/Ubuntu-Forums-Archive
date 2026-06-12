---
title: "Performance: LVM with encryption vs. Ubuntu style Home encryption"
date: 2011-08-04
forum: Security
---

### Post by ufugu on 2011-08-04
I'm finally getting around to setting up a laptop with proper encryption.  From what I've looked at, either Debian-style LVM with encryption or the /home encryption offered during a standard Ubuntu install will work for me.

Does either one offer a **performance** advantage over the other?

I'm NOT asking which is better or more secure.  Just which one may be less obtrusive during intensive tasks, all other things being equal.  I'm on an i3-2310M FWIW.

Searched, but haven't found this exact comparison.  Sorry if it's a recurring topic and I just can't find it.

---

### Post by bodhi.zazen on 2011-08-04
You would have to benchmark it yourself, using some disk intense activities, such as create and delete 10,000 files in $HOME , but the overhead with either is about 1 % or so, a little less, so any difference you measured is going to be trivial.

I would use an encryption option based on the features you want and not performance.

---

### Post by ufugu on 2011-08-05
Thanks! I'm taking that to mean that the two options are roughly equal in performance.

In any case, ~1% is mighty attractive number.  I'm trying to learn about these options and I'm finding numbers and/or generalizations thrown out all over the map regarding performance impact.

I'm going to try the encrypted LVM first, but I'm still curious to hear if anyone has personally experienced a difference between the two.

---

### Post by nrundy on 2011-08-06
I think you'll only find a difference if you use an old computer. Anything dual-core and the performance hit from encryption is going to be negligible. Like bodhi said, choose based on features.

If you are dealing with a 10 year old single core processor though you might see difference performance wise.

---

### Post by scorp123 on 2011-08-07
> **ufugu said:**
> From what I've looked at, either Debian-style LVM with encryption or the /home encryption offered during a standard Ubuntu install will work for me. I use both. There are only minor performance hits as far as I can tell. And my laptop is almost 7 years old. It's an old Core Duo (= 32-bit only CPU) with 3 GB RAM. And I have no problems with it whatsoever despite using two encryption schemes on top of each other.

---

### Post by tubbygweilo on 2011-08-07
Ufugu, I am using lvm, full disk encryption on 10.04lts - the only slowness I encounter is me entering the long passphrase at boot time. 
I never noticed any difference between lvm, full disk encryption and a non-encrypted install when running everyday tasks including reading + writing Truecrypt files.

2* 2 Duo t8100 @2.1 GHz with 3.9Gib RAM.

---

### Post by ufugu on 2011-08-08
> **tubbygweilo said:**
> ...the only slowness I encounter is me entering the long passphrase at boot time.

:)

Thanks for the responses.  LVM with encryption is working seamlessly and it's good to know that my performance concerns were for nothing (at least so far--I'll fire up Ardour soon and see how it handles recording audio...).

---

### Post by nrundy on 2011-08-10
> **ufugu said:**
> :)

Thanks for the responses.  LVM with encryption is working seamlessly and it's good to know that my performance concerns were for nothing (at least so far--I'll fire up Ardour soon and see how it handles recording audio...).

@ufugu, what version of Ubuntu are you running with the encryption? Are you running full disk encryption?

---

