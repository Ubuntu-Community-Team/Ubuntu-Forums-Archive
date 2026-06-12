---
title: "Is rootkit hunter only for servers?"
date: 2011-03-03
forum: Security
---

### Post by nrundy on 2011-03-03
Should I (can I) user Rootkit Hunter to help secure my Desktop install of Ubuntu? Or is this only operable (intended) for Servers? The literature I read on it seems to always be referring to servers and not Desktops.

---

### Post by uRock on 2011-03-03
I would recommend reading all of the threads full of false positives before bothering with rkhunter. I wouldn't bother with rkhunter, unless you have been installing 3rd party software or running web based applications as root.

---

### Post by bodhi.zazen on 2011-03-03
> **nrundy said:**
> Should I (can I) user Rootkit Hunter to help secure my Desktop install of Ubuntu? Or is this only operable (intended) for Servers? The literature I read on it seems to always be referring to servers and not Desktops.

Linux is not window and you should only use rkhunter (or any security tool really) if you are willing to read the documentation and google search the results.

---

### Post by nrundy on 2011-03-03
> **bodhi.zazen said:**
> Linux is not window and you should only use rkhunter (or any security tool really) if you are willing to read the documentation and google search the results.

I said in my post that I was reading the literature (= documentation).

---

### Post by nrundy on 2011-03-03
> **uRock said:**
> I would recommend reading all of the threads full of false positives before bothering with rkhunter. I wouldn't bother with rkhunter, unless you have been installing 3rd party software or running web based applications as root.

Thanks for the info. 

I've only installed from the "default" Ubuntu repositories with one exception. I downloaded and installed TrueCrypt from the website.

---

### Post by nrundy on 2011-03-03
Is the reason TrueCrypt is not in the ubuntu repository because it's not full GPL?

---

### Post by bodhi.zazen on 2011-03-03
> **nrundy said:**
> Is the reason TrueCrypt is not in the ubuntu repository because it's not full GPL?

Yes.

The opens source alternate is LUKS which can be used in Windows as well.

Personally I use LUKS rather then Truecrypt.

---

### Post by nrundy on 2011-03-04
I looked for LUKS in synaptic but nothing showed up called LUKS. Is LUKS available in the repo? Am I looking for the right name?

I'd like to switch to LUKS.

---

### Post by bodhi.zazen on 2011-03-04
dm-crypt

[http://www.hermann-uwe.de/blog/howto-disk-encryption-with-dm-crypt-luks-and-debian](http://www.hermann-uwe.de/blog/howto-disk-encryption-with-dm-crypt-luks-and-debian)

Most how-to's describe how to install the entire system into a LUKS crypt with LVM.

BUT you do not need to do that, you can have a separate crypt you use for data. See the link I gave you.

---

