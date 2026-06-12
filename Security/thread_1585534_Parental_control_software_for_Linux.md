---
title: "Parental control software for Linux"
date: 2010-09-30
forum: Security
---

### Post by erngab on 2010-09-30
I hope I'm in a good section
Which program you know to protection from porn on the net, parental control software.
I try Webcleaner filtering HTTP proxy but I stack. I do not know how to go further.

>  p, li { white-space: pre-wrap; } [FONT=Sans Serif]jsprf.c: In function 'BuildArgArray':[/FONT]
 [FONT=Sans Serif]jsprf.c:644: error: incompatible types when assigning to type 'va_list' from type 'struct __va_list_tag *'[/FONT]
 [FONT=Sans Serif]make[4]: *** [jsprf.lo] Error 1[/FONT]
 [FONT=Sans Serif]make[4]: Leaving directory `/media/sdb5/Ernest/erngab/Desktop Linux/SECURITY/webcleaner-2.41/libjs'[/FONT]
 [FONT=Sans Serif]make[3]: *** [all-recursive] Error 1[/FONT]
 [FONT=Sans Serif]make[3]: Leaving directory `/media/sdb5/Ernest/erngab/Desktop Linux/SECURITY/webcleaner-2.41/libjs'[/FONT]
 [FONT=Sans Serif]make[2]: *** [all] Error 2[/FONT]
 [FONT=Sans Serif]make[2]: Leaving directory `/media/sdb5/Ernest/erngab/Desktop Linux/SECURITY/webcleaner-2.41/libjs'[/FONT]
 [FONT=Sans Serif]make[1]: *** [all-recursive] Error 1[/FONT]
 [FONT=Sans Serif]make[1]: Leaving directory `/media/sdb5/Ernest/erngab/Desktop Linux/SECURITY/webcleaner-2.41'[/FONT]
 [FONT=Sans Serif]make: *** [all] Error 2[/FONT]


Any ideas would be welcome.
Thanks

---

### Post by sikander3786 on 2010-09-30
I'll recommend [dansguardian]("http://dansguardian.org/").

Even you may want to give Ubuntu CE a go, it has all that protection built-in.

[http://ubuntuce.com/](http://ubuntuce.com/)

---

### Post by bodhi.zazen on 2010-09-30
The best parental control is you.

In terms of proxy services I like the combination of

NoScript + Privoxy + Dansguardian

See : [http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)

---

### Post by alphaamanitin on 2010-10-01
It is not really an Ubuntu solution but you can go to OpenDNS, use their DNS servers.  Then you register your network with OpenDNS, and they can do lots of filtering.  What I don't like about it is that they record every where you go and you can view the histoy.  So it depends on if you are like me and want more anonomous internet usage.  It is free for non commercial uses.

AlphaA

---

### Post by tumelo on 2011-03-08
If you go with dansguardian be sure to add google.com/images to your blacklist. You or your kids can see anything and everything in google images without dansguardian blocking it. So make sure it's on your blacklist and just use bing images if you need to.

---

### Post by wacky_sung on 2011-03-09
Actually those filtering can be bypass if your children is smart enough to connect through a VPN.

---

### Post by bodhi.zazen on 2011-03-09
> **wacky_sung said:**
> Actually those filtering can be bypass if your children is smart enough to connect through a VPN.

Yes, there are several methods children can bypass such things.

Parental control software does not replace supervision or parental responsibilities.

---

