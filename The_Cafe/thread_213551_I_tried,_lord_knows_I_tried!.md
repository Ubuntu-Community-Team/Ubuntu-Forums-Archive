---
title: "I tried, lord knows I tried!"
date: 2006-07-11
forum: The Cafe
---

### Post by Zodiac on 2006-07-11
Well, I am posting this using my HP 6230... running windows.

I tried everything to get my Broadcom NetXtreme BCM5751 Gigabit Ethernet to work, all to no avail. I have searched the internet high and low for answers and have discovered there are none.

I have said it before, and I will say it again, drivers are the single biggest issue facing Linux going forward. Manufacturers have to be convinced to release them...

Sigh. :( 

And it goes on, and on, and on…

---

### Post by tseliot on 2006-07-11
did you read this?

[http://www.linuxquestions.org/questions/showthread.php?t=403644](http://www.linuxquestions.org/questions/showthread.php?t=403644)

---

### Post by tseliot on 2006-07-11
And if that doesn't work you might try Fedora Core 5 which seems to handle ti just fine as it's reported here:

[http://www.phoronix.com/lch/?k=entry&l=85&t=Tyan](http://www.phoronix.com/lch/?k=entry&l=85&t=Tyan)

---

### Post by Adamant1988 on 2006-07-11
Zodiac, there are lots of nifty work arounds... and you could always replace the card with something that does work...
If you're serious about Linux and Ubuntu a single card shouldn't stop you.

---

### Post by Compucore on 2006-07-11
I'll be trying Fedora 5 soon. I had gotten a DVD version of it with a magazine from the UK that talks about Linux and had a version of Red hat. $12 Canadian prices. Its worth it for a magazine that comes with an OS and some featured stuff thatcan take up a DVD sized format. It'll be fun to learn that too after I get my kicks with Ubuntu on my Aptiva. I know one bypass to get around with the IRQ's since I was having problems with a current kernel for my Aptiva. So it is easily fixe with a added command for it. I find it fun learning linux over here on my spare time and to use it to its full potential.

Compucore


> **tseliot said:**
> And if that doesn't work you might try Fedora Core 5 which seems to handle ti just fine as it's reported here:

[http://www.phoronix.com/lch/?k=entry&l=85&t=Tyan](http://www.phoronix.com/lch/?k=entry&l=85&t=Tyan)

---

### Post by Zodiac on 2006-07-11
I have tried all of this, none of it worked.

Fedora didn't work, the windows drivers didn't work... and its a laptop so I can't just "swap the card".

What else can a man do???

---

### Post by tseliot on 2006-07-11
> **Zodiac said:**
> the windows drivers didn't work...
Doesn't work in Windows???

---

### Post by Compucore on 2006-07-11
What else have you not tried. If the gigabit eithernet that is built in. Have you tried checking with the chipset manufacturer of the networking card. maybe they might have a set of drivers. Or if its embeded with the mtherboard itself.

Compucore

---

### Post by Zodiac on 2006-07-11
I believe it is part of the mobo... and I mean the windows drivers didn't work in Ubuntu...

The manufacturers website was of no help neither was HP's.

I am at wits end.

---

### Post by DoctorMO on 2006-07-11
Sometimes devices such as these don't work because ubuntu will pick out a nice module for that hardware and it will conflict with other modules you try and probe.

One of the ethernet cards I had to get working required me to remove almost all the modules on the computer and then modprobe the sujested one. as soon as I recognised which other module was trying to load I removed it and blacklisted it in modprobe confs.

---

### Post by drizek on 2006-07-11
> **Zodiac said:**
> I believe it is part of the mobo... and I mean the windows drivers didn't work in Ubuntu...

The manufacturers website was of no help neither was HP's.

I am at wits end.

Maybe its time to get a wireless router?

---

### Post by Compucore on 2006-07-11
Maybe he could do it that way as well come to think of it. You may be onto something there. And it just might work. Is there a general list when you did a modprob and it suggested X driver instead of Y driver. Would it be a viable solution to his problem in order to dig deaper into this. I know it might be a long shot but it just might work. Like what you mention you were able to to tell modprob go here to this one insead of the otherone instead. It would be somthing similar to like add/remove hardware in windows. *(Okay not exactly like windows. But the general idea. Shivers at the thought of doing it in windows so many times.)* sometimes you can tell like you said if you knew what to look for.

Compucore

> **DoctorMO said:**
> Sometimes devices such as these don't work because ubuntu will pick out a nice module for that hardware and it will conflict with other modules you try and probe.

One of the ethernet cards I had to get working required me to remove almost all the modules on the computer and then modprobe the sujested one. as soon as I recognised which other module was trying to load I removed it and blacklisted it in modprobe confs.

---

### Post by Swab on 2006-07-11
Just buy a cheap PCMCIA ethernet card...

---

### Post by Zodiac on 2006-07-11
Sorry guys... this is getting to whacked out for me... I don't have the l33t skillz to be the one forging the path for these linux unfriendly drivers...

I am going to go back to Windows for this laptop, but I will keep lurking, waiting for proper drivers to be included.

Mark my words, I'll be back.

P.S. - HP and Broadcom have both gotten nasty letters from me in regards to this issue. It's BS that I can't use the OS of my choice without having to jumps through hoops.

Thanks anyways guys!

---

