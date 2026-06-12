---
title: "Gnucash"
date: 2008-06-23
forum: System76 Support
---

### Post by riseringseeker on 2008-06-23
I am wondering, why does the System76 driver also install gnucash?

I would like to get gnucash **and** have it do online banking, which of course the version in the repositories won't do because of licensing restrictions/problems.

Can anyone answer the first question, and give me help with getting online banking going in gnucash?

---

### Post by thomasaaron on 2008-06-23
When we first started this business, there were a ton of requests for gnucash. So, since our customer base seemed to want it, we installed it.

As for getting online banking to work, the instructions are here, on their wiki...

[http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2#Ubuntu](http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2#Ubuntu)

However, it may be more trouble than it is worth to get it going in Hardy. This is from the above link...

> Debian

Debian does not package aqofxconnect because of a license incompatibility. You will need to follow the instructions in Installing GnuCash on Debian in order to:

    * recompile gnucash (to include HBCI support)
    * create the package libaqbanking-ofx0 (which has aqofxconnect). 

[edit] Ubuntu

The same as in Debian applies. The Debian guide for enabling HBCI/OFX support can be equally used for Ubuntu Edgy 6.10 and GnuCash 2.0.x.

    The Ubuntu distribution does not have these options enabled by default in repositories, as when using apt-get, aptitude or the Synaptic Package Manager. This is due to a dependency on one piece of non-GPL software (the OpenSSL package, used for SSL communication). 



I've heard that this is supposed to be remedied in a month or two from our Sales Manager, who uses GnuCash for everything.

---

### Post by riseringseeker on 2008-06-23
> **thomasaaron said:**
> When we first started this business, there were a ton of requests for gnucash. So, since our customer base seemed to want it, we installed it.

As for getting online banking to work, the instructions are here, on their wiki...

[http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2#Ubuntu](http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2#Ubuntu)

However, it may be more trouble than it is worth to get it going in Hardy. This is from the above link...



I've heard that this is supposed to be remedied in a month or two from our Sales Manager, who uses GnuCash for everything.

Having it easier to get gnucash work with online banking would be a wonderful thing!  Is that what you are saying here, that the Sales Manager is going to remedy getting gnucash working with online banking, and at least make it easy to get going with it enabled?

---

### Post by thomasaaron on 2008-06-23
No, sorry, I wasn't clear.

The Sales Manager is not going to remedy anything. He uses GnuCash and keeps himself informed about various features on it. There is supposed to be either a new version of GnuCash or a new version of the library that allows online banking. It should come down through the repos soon.

---

### Post by riseringseeker on 2008-06-23
> **thomasaaron said:**
> No, sorry, I wasn't clear.

The Sales Manager is not going to remedy anything. He uses GnuCash and keeps himself informed about various features on it. There is supposed to be either a new version of GnuCash or a new version of the library that allows online banking. It should come down through the repos soon.

That would be great, please keep me posted.

---

### Post by thomasaaron on 2008-06-23
OK. Just found out that the package that is supposed to fix this is already being tested by Debian. I just don't know what that means for an ETA of the fix into Ubuntu.

---

### Post by undadecor on 2008-07-14
> **riseringseeker said:**
> give me help with getting online banking going in gnucash?

Try this out:  [http://ubuntuforums.org/showthread.php?t=854770](http://ubuntuforums.org/showthread.php?t=854770)

---

### Post by riseringseeker on 2008-07-20
> **undadecor said:**
> Try this out:  [http://ubuntuforums.org/showthread.php?t=854770](http://ubuntuforums.org/showthread.php?t=854770)

May have to make several changes, that seems to be a howto for fiesty 32 bit, am running hardy 64 bit, but will check into it.

---

### Post by riseringseeker on 2008-08-28
> **thomasaaron said:**
> OK. Just found out that the package that is supposed to fix this is already being tested by Debian. I just don't know what that means for an ETA of the fix into Ubuntu.

Any word on it yet?

---

### Post by thomasaaron on 2008-08-28
Hey, thanks for bumping this one. I'd forgotten all about it.

Looks like it is fixed in Intrepid. See...
[https://launchpad.net/ubuntu/intrepid/+source/gnucash/2.2.6-1ubuntu1](https://launchpad.net/ubuntu/intrepid/+source/gnucash/2.2.6-1ubuntu1)

Look at the changelog for 2.2.4-2 at the bottom.
Hardy uses 2.2.4-1, I believe.

---

