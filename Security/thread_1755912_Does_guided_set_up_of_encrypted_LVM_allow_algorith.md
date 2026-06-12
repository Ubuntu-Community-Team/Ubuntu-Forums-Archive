---
title: "Does guided set up of encrypted LVM allow algorithm XTS choice?"
date: 2011-05-11
forum: Security
---

### Post by nrundy on 2011-05-11
When using the Alternate CD to install Natty, if I select "Guided - use entire disk and set up encrypted LVM," am I allowed to select settings like AES, 256, XTS?

or are these settings auto-selected and I'm not given a choice?

A friend told me I should avoid the IV Algorithm "CBC" and use "XTS" instead because XTS is more modern and offers better security. How do I select XTS?

---

### Post by rookcifer on 2011-05-11
> **nrundy said:**
> When using the Alternate CD to install Natty, if I select "Guided - use entire disk and set up encrypted LVM," am I allowed to select settings like AES, 256, XTS?

or are these settings auto-selected and I'm not given a choice?

A friend told me I should avoid the IV Algorithm "CBC" and use "XTS" instead because XTS is more modern and offers better security. How do I select XTS?

The installation CD does not give the option of XTS even though LUKS does support it now.  If you want to use XTS, you will have to setup the partitions manually and then unlock them before installation.  That's not something you probably want to fool around with.

As for CBC-ESSIV, it is perfectly secure.  There's no reason not to use it.

---

### Post by nrundy on 2011-05-11
> **rookcifer said:**
> The installation CD does not give the option of XTS even though LUKS does support it now.  If you want to use XTS, you will have to setup the partitions manually and then unlock them before installation.  That's not something you probably want to fool around with.

As for CBC-ESSIV, it is perfectly secure.  There's no reason not to use it.

I was told CBC doesn't protect against watermarking. That I should use XTS. It's all over my head.

Most folk use CBC here with Ubuntu? no concerns with not using XTS?

---

### Post by rookcifer on 2011-05-12
> **nrundy said:**
> I was told CBC doesn't protect against watermarking. That I should use XTS. It's all over my head.

CBC with a predictable initialization vector is susceptible to watermarking attacks, but with [ESSIV]("http://en.wikipedia.org/wiki/XTS_mode#ESSIV"), it's not.  Thus, there are no known weaknesses in CBC-ESSIV (which is the default in LUKS on Ubuntu.)

> Most folk use CBC here with Ubuntu? no concerns with not using XTS?

No concerns.  XTS is newer and was just recently (last year) standardized by NIST for drive encryption, but CBC-ESSIV is older and probably better tested.  

I have had this same discussion with cryptographers, most of whom say they still use CBC-ESSIV.  There's nothing wrong with XTS, but it hasn't quite made its mark as the default cipher-mode in most crypto applications.

---

### Post by nrundy on 2011-05-12
> **rookcifer said:**
> CBC with a predictable initialization vector is susceptible to watermarking attacks, but with [ESSIV]("http://en.wikipedia.org/wiki/XTS_mode#ESSIV"), it's not.  Thus, there are no known weaknesses in CBC-ESSIV (which is the default in LUKS on Ubuntu.)



No concerns.  XTS is newer and was just recently (last year) standardized by NIST for drive encryption, but CBC-ESSIV is older and probably better tested.  

I have had this same discussion with cryptographers, most of whom say they still use CBC-ESSIV.  There's nothing wrong with XTS, but it hasn't quite made its mark as the default cipher-mode in most crypto applications.

rookcipher, I really appreciate you taking the time to educate me about this. Thanks so much!

So if I use the Alternate CD and select "Guided - use entire disk and set up encrypted LVM," will I automatically by default get AES 256 with CBC-ESSIV? Or do I need to look out during installation/setup to select these settings?

---

### Post by rookcifer on 2011-05-12
> **nrundy said:**
> rookcipher, I really appreciate you taking the time to educate me about this. Thanks so much!

So if I use the Alternate CD and select "Guided - use entire disk and set up encrypted LVM," will I automatically by default get AES 256 with CBC-ESSIV? Or do I need to look out during installation/setup to select these settings?

Yes, AES-256 with CBC-ESSIV is the default.

---

