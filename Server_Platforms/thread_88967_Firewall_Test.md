---
title: "Firewall Test"
date: 2005-11-11
forum: Server Platforms
---

### Post by fordp on 2005-11-11
[http://www.auditmypc.com/freescan/scanoptions.asp]("http://www.auditmypc.com/freescan/scanoptions.asp")

The web site above has a firewall test and I have just tried it on my Athlon XP Breezy PC running Firefox, and it could find some things about me I did not expect.

I have a broadband router and run NAT, the website above could sho my private (Nat'ed) IP address.

My brother thinks this is down to Java passing this info on to the website.

What do people on this forum think of this.

Is it a security risk ?

I realise that one of the main aims of the above site is to sell software for windoze that you should not need!

I look forward to reading what people think.

---

### Post by Kyral on 2005-11-11
GRC.com's Shields UP! is much better IMO (Not for profit either :D)

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by LordHunter317 on 2005-11-11
The test in the OP is a known POS test.  Ignore it.

---

### Post by paddyg on 2005-11-11
fordp, if you've got firestarter installed and correctly setup, that doesn't happen.

I've just tested it.

(That's just in case you don't want to ignore things you don't like ;) )

---

### Post by fordp on 2005-11-11
I just installed Firestarter and it did not help.

The Website still showed my correct private IP address.

---

### Post by Spudgun on 2005-11-11
So what? Every website you visit knows your IP address.

---

### Post by Kyral on 2005-11-11
If you connect to anything it knows your IP address. How else would it know where to shoot the data?

---

### Post by LordHunter317 on 2005-11-11
He means the IP address behind his NAT router, which the public Internet cannot see, normally.  But that site doesn't figure it out via external means, either, so it's not a fair test.

I really, really meant it when I said that site is a POS.  Just don't even think about it, it means nothing.

---

### Post by paddyg on 2005-11-12
i've studied the issue a bit more carefully...

LordHunter317 and fordp's brother were quite right: it's only a childish trick performed by using java via the browser port---if we disable java--and javascript-- just as a test, the trick's gone...

The info about the internal ip is quite useless if the machine is invisible to the net (stealth).

I don't even know why i'm writing this post, this "issue" really means less than nothing.

---

### Post by jdong on 2005-11-12
Yes, it's a cheap Java trick attained by simply listing all bindable addresses via a Java applet. No security breach, since Java sandboxes applets from any serious privacy breaches, and the exposed internal IP is unreachable.

---

