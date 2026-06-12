---
title: "How does swap look like?"
date: 2006-12-28
forum: The Cafe
---

### Post by ltk5 on 2006-12-28
Has anyone seen the inside of a swap space? I mean surely there must be something in it...so, what does it look like? Any ideas:D ? (imagination also)

Personally I view it as a big vulcano, with a crater full of different stuff..

---

### Post by 3rdalbum on 2006-12-28
Here's how to have a look at what's in your swap:

```
cat /proc/swaps
```

Find the device file location listed in there (mine is /dev/sda5) and put it into the next command:

```
sudo cat <device-location-for-the-swap> | less
```
e.g. "sudo cat /dev/sda5 | less"

You can scroll down using the Page Down key. I just found the string "SuSESuSE" in mine, plus all this stuff:

```
server: about do a switch
^@svc_sendreply
^@CALLIT (prog %lu): fork: %m^@-d: debugging mode
^@-t dir: chroot into dir
^@-v: verbose logging
^@-i address: bind to address
^@dt:vi:^@portmap: fork: %s^@portmap^@cannot create udp socket: %m^@cannot bind
udp: %m^@couldn't do udp_create^@cannot create tcp socket: %m^@cannot bind tcp:
%m^@couldn't do tcp_create^@couldn't do chroot^@run_svc returned unexpectedly^@
^@^@p<D5><FF><FF><88><D8><FF><FF><80><D7><FF><FF><E4><D6><FF><FF><86><D6><FF>
<FF><B8><D5><FF><FF>usage: %s [-dv] [-t dir] [-i address]
^@%lu^@connect from %s to %s(%s)%s^@: request not forwarded^@: request from non-local host^@setgroups(0, 0) failed: %m^@setuid(65534) failed: %m^@setgid(65534)
failed: %m^@callit^@dump^@getport^@null^@unset^@^@^@^@: request from unauthorized host^@^@^@^@: request from unprivileged port^@socket^@SIOCGIFCONF^@SIOCGIFFLAGS^@SIOCGIFADDR^@portmap: out of memory^@cannot find any active local network interfaces
.....
Copyright (c) 1990 The Regents of the University of California.
 All rights reserved.

```

Interesting stuff. My swap space does look a bit like a volcano, actually :-)

---

### Post by ltk5 on 2006-12-28
Whoa!!
I can even see some lava in here
```
<89><D0><C3><F7>&#1673;^U^@^@^@^@<BA><FF><FF><FF><FF><EB><ED><89><F6><83><EC>^P<89>|
<89>&#969;&#1097;l$^L<BD>{^@^@^@<89><FA><89>t$^D<89>&#393;<E8><89>^\$S<89><F3>&#832;[=~<FF><FF><FF>
<89><C3>w^U<89><U+060B>t$^D<8B>^\$<8B>|<8B>l$^L<83><C4>^P<C3><F7>&#1737;^]^@^@^@^@<BB>
<FF><FF><FF><FF><EB>&#1805;<B6>^@^@^@^@<8D><BF>^@^@^@^@<8B>D<C7>^@^A^@^@^@1<C0>Ív^@
<8B>D$^DÍt&^@<8D><BC>'^@^@^@^@<8B>D$^D<8B>TÍ<B4>&^@^@^@^@1<C0>Í<B6>^@^@^@^@<8D>
<BC>'^@^@^@^@<83><EC>^D<8B>T<C7>^D$^A^@^@^@<8B>^D$<89>^B<8D>B^D<89>B^D<89>@^D
<83><C4>^D<C3>S<8B>\$^P<8B>T$^L<85><DB>t^L<85><D2><8B>D<89><D9><FF>^S[Ð<8D>t&^@S
<8B>T$^T<8B>\<8B>D$^L<8B>L$^P<83><FA>^Bt^L<83><FA>^Dt^U<83><EA>^At^V[<C3><F0>f^O
<B1>^K[Í<B4>&^@^@^@^@<F0>^O<B1>^K[<C3><F0>^O<B0>^K[Ít&^@<8B>D$^D<8B>@$Ð<8D><B4>&
^@^@^@^@<A1>^@^@^@^@Ív^@<8D><BC>'^@^@^@^@<8B>D$^D<8B>@8%<FF><FF>^O^@Ív^@<8B>D$^D
<8B>@<Ð<8D><B4>&^@^@^@^@<8B>D$^D<8B>@<FC>Ð<8D><B4>&^@^@^@^@<8B>D$^D<8B>@xÐ<8D>
<B4>&^@^@^@^@<8B>T<8B>D$^D<89>PxÍt&^@<8B>D$^D<8B>@^X<C1><E8>^G<83><E0>^AÉ<F6>
<8B>D$^D<F6>@^X^C^O<95><C0>^O<B6><C0>Ð<8B>D$^D<8B>@^TÐ<8D><B4>&^@^@^@^@<8B>D$^D
<8B><8B>@^LÐ<8D>t&^@<A1>^@^@^@^@Ív^@<8D><BC>'^@^@^@^@<8B>D^CD$^D^O<B6>^@^O<B6>
<C0>Ð<8B>D$^D^E^@^@^@@Í<B6>^@^@^@^@<A1>^@^@^@^@Ív^@<8D><BC>'^@^@^@^@<8B>D$^D<83>
<F8>^Kw^G<FF>$<85>^@^@^@^@<B8>^N^@^@^@ø^P^@^@^@<90><8D>t&^@ø^V^@^@^@ø^M^@^@^@
<8D>t&^@ø^E^@^@^@ø9^@^@^@<8D>t&^@ø^L^@^@^@ø^A^@^@^@<8D>t&^@ø^S^@^@^@ø^D^@^@^@
<8D>t&^@ø^@^B^@^@øP^@^@^@<8D>t&^@<C3><EB>^M<90><90><90><90><90><90><90><90><90>
<90><90><90><90><83><EC>^D<8B>T<8B>D$^L<C7>B^D^@^@^@^@<89>^B<C7>^D$^A^@^@^@<8B>
^D$<89><8D>B^L<89>B^L<89>@^D<83><C4>^DÉ<F6><B8>^T^@^@^@Ív^@<8D><BC>'^@^@^@^@<8B>

```
and this one.. i'll call it *clouds*
```

¢·                           X           ÀU‰·        
                                                                                  &#9670;U‰·         U‰·        PT‰·        T‰·        ÀS‰·        °T‰·                            °           0º‰·        D   &#9670;&#65533;&#65533;&#65533;g&#65533;&#65533;K|h¢&#65533;i&#65533;&#65533;&#65533;&#65533;nx&#65533;&#65533;nx&#65533;&#65533;&#5161;&#65533;&#21545;&#65533;&#37929;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#418;&#65533;&#65533;&#65533;&#65533;&#65533;&#35753;&#65533;t&#65533;&#65533;&#843;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;H&#65533; &#13047;&#65533;&#4855;&#65533;©&#65533;&#65533;L&#65533;&#65533;&#65533;©&#65533;T&#65533;&#65533;&#65533;&#65533;©&#65533;&#65533;*&#65533;&#65533;©&#65533;
                                                               &#65533;&#65533;&#65533;&#65533;
                                                                      &#65533;&#65533;P&#65533;&#65533;&#65399;&#1030;&#65399;`&#65533;&#65533;P&#65533;&#65533;0P&#65533;&#65533;\P&#65533;&#65533;&#65533;P&#65533;&#65533;&#65533;P&#65533;&#65533;&#65533;P&#65533;&#65533;&#65533;P&#65533;&#65533;Q&#65533;&#65533;4Q&#65533;
```

btw, is it save doing things like that?:cool:

---

### Post by Bartender on 2006-12-28
Swap is sort of a burnt-sienna brown.  See attachment

Whoops, attachment is too small to get the full sienna-brown effect.  Sorry...

---

### Post by ltk5 on 2006-12-31
Hasn't anybody taken a picture of their swap?

---

### Post by christhemonkey on 2006-12-31
You should of Googled it!

[IMG]http://host.jwcinc.net/2285538/swap5.JPG[/IMG]
[http://images.google.com/images?q=swap+inside&ndsp=18&svnum=10&hl=en&lr=&start=90&sa=N](http://images.google.com/images?q=swap+inside&ndsp=18&svnum=10&hl=en&lr=&start=90&sa=N)

---

### Post by eriqk on 2007-01-01
Here's a part of mine, a few days ago:
[img]http://www.xs4all.nl/~dwaes/images/art/swap-klein.png[/img]

Groet, Erik

---

### Post by Shadow1 on 2007-01-01
What's **really** fun is if you do

```
sudo cat <swap> >> /dev/dsp
```

Sounds like the calming noise of a dialup modem to me.

---

### Post by OldTimeTech on 2007-01-01
This is how I see my swap;

[ATTACH]22007[/ATTACH]

---

