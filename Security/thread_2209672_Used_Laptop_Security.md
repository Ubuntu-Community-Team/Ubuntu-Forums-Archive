---
title: "Used Laptop Security?"
date: 2014-03-06
forum: Security
---

### Post by Adam's AI on 2014-03-06
I just bought a used laptop from a shop. I am of course going to be wiping Windows and installing Ubuntu, but I am wondering if I at that point I can trust the computer?

Are there any additional security checks I can do? Should I try to re-load firmware/BIOS, is there a way to verify the hardware is trust-worthy? If you bought a used laptop, would you do banking on it (for example)?


Edit: Also, I'm not sure if the laptop's parts are all original or not...

---

### Post by Elastic_Potential on 2014-03-06
I assume your question is more along the lines of, "if this computer had viruses on Windows, will those viruses transfer to Linux?"  If you wipe Windows (wipe the entire partition table) and use Ubuntu, you should be okay.  You may want to skim through this section of the forums for additional security methods, as Linux isn't totally infallible.

As for hardware integrity/trustworthiness, the best way to find out is by using it; I'm curious to know what hardware could be considered "untrustworthy."

---

### Post by coldraven on 2014-03-07
The likes of the NSA could in theory have changed the firmware of the hard drive but it would be expecting Windows to do the connection to it's servers.
In other words, it probably won't be a problem under Linux.
But check to see if there is a BIOS update, it will not hurt to have the latest version.

---

### Post by ankspo71 on 2014-03-07
The laptop I'm using now was given to me used so I decided to wipe the entire hard drive a couple of times to destroy any traces of recoverable data, including the broken and non-repairable Windows installation itself. Wiping can take a very long time, especially if the drive is wiped using random data, and/or using multiple passes, though. I do this each time I get (or get rid of) a used computer or hard drive. Simply formatting a drive doesn't securely destroy any data, instead it recreates the partition table and marks the data as read so it can be eventually overwritten later on with normal computer use.

If I would have wanted to keep Windows (if it had worked) then I would have used the recovery media/partition to reinstall windows, and then used some Windows program to wipe the unused free-space instead (which would include that recoverable data marked as read). Then I would do the same after installing Linux with a Linux application. 

> If you bought a used laptop, would you do banking on it (for example)?

I had several used computers over the years, and I've done things like shopping on all of them.

I can't comment on the possibilities of any hardware security issues.  I'm sure there would be much less concern for older hardware though.

---

### Post by bashiergui on 2014-03-09
> **coldraven said:**
> The likes of the NSA could in theory have changed the firmware of the hard drive but it would be expecting Windows to do the connection to it's servers.
In other words, it probably won't be a problem under Linux.
But check to see if there is a BIOS update, it will not hurt to have the latest version.
LOL. No. You're not going to trick the NSA by using Linux. If the NSA wants it, they've already got it.

I do agree to look for a firmware update, always a good idea with a new device. 

If you wipe the drive by writing zeros or random data over the entire drive once, that will be more than sufficient to trust the computer.

---

### Post by monkeybrain20122 on 2014-03-09
> **ankspo71 said:**
> The laptop I'm using now was given to me used so I decided to wipe the entire hard drive a couple of times to destroy any traces of recoverable data, including the broken and non-repairable Windows installation itself. Wiping can take a very long time, especially if the drive is wiped using random data, and/or using multiple passes, though. I do this each time I get (or get rid of) a used computer or hard drive. Simply formatting a drive doesn't securely destroy any data, instead it recreates the partition table and marks the data as read so it can be eventually overwritten later on with normal computer use.
.

A bit paranoid? I just got a used laptop and sold mine. I just reformatted the hd and installed several Linux distros and that was it.

---

### Post by monkeybrain20122 on 2014-03-09
> **bashiergui said:**
> LOL. No. You're not going to trick the NSA by using Linux. If the NSA wants it, they've already got it.

I do agree to look for a firmware update, always a good idea with a new device. 

If you wipe the drive by writing zeros or random data over the entire drive once, that will be more than sufficient to trust the computer.

I don't know why the NSA would be interested in me. I lead a boring life :)

---

### Post by open2reason on 2014-03-09
As did Douglas Quail in "**We Can Remember It for You Wholesale**" written by an author with a family name the forum software replaces with ****, you should be OK.

---

### Post by ankspo71 on 2014-03-09
> **monkeybrain20122 said:**
> A bit paranoid? I just got a used laptop and sold mine. I just reformatted the hd and installed several Linux distros and that was it.

No, not really, I just think it's good practice to do. That part about the multiple passes and random data was a just a reminder that they can take a very long time.

---

