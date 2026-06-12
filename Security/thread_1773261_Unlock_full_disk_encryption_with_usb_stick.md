---
title: "Unlock full disk encryption with usb stick?"
date: 2011-06-01
forum: Security
---

### Post by sweep16 on 2011-06-01
I want to set up full disk encryption with a pass phrase and was wondering if there was a way to use a usb stick to automaticly unlock the encryption. Im sure ive seen it done before but cant find anything on it now.
Thanks.

---

### Post by tubbygweilo on 2011-06-02
I have a 10.04 with full disk encryption and a live 10.04 usb memory stick and when booting with the live usb stick I can not access my fully encrypted disk. 

If you get other results then I and a few other users of this forum would love to know how you did it.

---

### Post by crispy_420 on 2011-06-07
Isn't that a similar method that BitLocker uses with the TPM chip? Not sure of a Linux method so I am also curious.

---

### Post by Ranko Kohime on 2013-02-26
Although this is an old thread, the question is still relevant, so I'll answer for the sake of Googlers.

The Luks encryption used by Ubuntu has the option of using a keyfile.  This keyfile can be anything, as long as it's secret from everyone else.  It could be a movie file, audio file, ODT document, or even just random data from /dev/urandom or /dev/random.

This [tutorial]("http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile") explains the process.

---

