---
title: "Problems with qjackctl / Bitwig"
date: 2016-02-11
forum: Ubuntu Studio
---

### Post by Hyenaz on 2016-02-11
Hello,

I was wondering if anyone has any advice for me. I am running Ubuntu Studio 15.10.

I have a Lenovo B580 and an RME Babyface.

When I run qjackctl and try and use the application Bitwig, after some moments, the Bitwig audio engine crashes.

I would think this was the fault of Bitwig, except for the fact that when I start jackd from the terminal with the following command:

    /usr/bin/jackd -P79 -t2000 -dalsa -dhw:Babyface2326740 -r88200 -p256 -n2 -s


it doesn't crash.

Here is my qjackctl config for the Babyface:

[ATTACH=CONFIG]267232[/ATTACH]

Is there, based on the terminal input, some setting I should change in qjackctl that could stop this crashing?

Thanks!

Adrienne

---

