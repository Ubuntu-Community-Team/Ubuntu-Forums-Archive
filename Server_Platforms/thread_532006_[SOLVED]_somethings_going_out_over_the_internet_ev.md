---
title: "[SOLVED] somethings going out over the internet everytime I open up terminal at least"
date: 2007-08-22
forum: Server Platforms
---

### Post by nowshining on 2007-08-22
I just installed ethereal and I noticed everytime I open up terminal (yes I have dialup) it sends a message out to the internet thru my service provider thru the DNS protocol

0000   00 04 02 00 00 00 00 00 00 00 00 00 00 00 08 00  ................
0010   45 00 00 3a f9 3a 40 00 40 11 79 ef 04 f5 65 94  E..:.:@.@.y...e.
0020   40 88 1c 78 04 8f 00 35 00 26 1d 73 90 ff 01 00  @..x...5.&.s....
0030   00 01 00 00 00 00 00 00 0c 42 4f 54 31 4e 45 54  .........BOT1NET
0040   31 47 4f 44 31 00 00 1c 00 01                    1GOD1.....


........

Yes i am the BOT1NET1GOD1 so I am wondering what's up because I never saw this stuff in windows xp when I had it...


and another one

0000   00 00 02 00 00 00 00 00 00 00 00 00 00 00 08 00  ................
0010   45 00 00 1c ec 7c 00 00 01 02 05 7a d1 f7 15 f1  E....|.....z....
0020   e0 00 00 01 11 64 ee 9b 00 00 00 00              .....d......


.........

I don't read that stuff so anyone know here know what it means, the second one I just restarted the capture and it changed what was being sent out, however I do now know firefox is sending crud out to bloglines, etc.. automatically.lolz :P anyway and NO I DO NOT use the rss feader at all..


EDIT: they change each and everytime sometimes I get one sometimes I get 2 now I got 4 this one stands out tho (there udp tho)

0000   00 00 02 00 00 00 00 00 00 00 00 00 00 00 08 00  ................
0010   45 00 01 16 00 00 40 00 37 11 7b 4e 40 88 1c 78  E.....@.7.{N@..x
0020   04 f5 65 94 00 35 04 96 01 02 7e 39 e2 37 85 80  ..e..5....~9.7..
0030   00 01 00 01 00 03 00 03 0c 42 4f 54 31 4e 45 54  .........BOT1NET
0040   31 47 4f 44 31 00 00 01 00 01 c0 0c 00 01 00 01  1GOD1...........
0050   00 00 02 58 00 04 40 88 1d be c0 0c 00 02 00 01  ...X..@.........
0060   00 00 02 58 00 15 06 61 75 74 68 6e 73 03 6c 61  ...X...authns.la
0070   78 04 75 6e 74 64 03 63 6f 6d 00 c0 0c 00 02 00  x.untd.com......
0080   01 00 00 02 58 00 15 06 61 75 74 68 6e 73 03 64  ....X...authns.d
0090   63 61 04 75 6e 74 64 03 63 6f 6d 00 c0 0c 00 02  ca.untd.com.....
00a0   00 01 00 00 02 58 00 15 06 61 75 74 68 6e 73 03  .....X...authns.
00b0   69 61 64 04 75 6e 74 64 03 63 6f 6d 00 06 61 75  iad.untd.com..au
00c0   74 68 6e 73 03 6c 61 78 04 75 6e 74 64 03 63 6f  thns.lax.untd.co
00d0   6d 00 00 01 00 01 00 00 02 58 00 04 40 88 1c 15  m........X..@...
00e0   06 61 75 74 68 6e 73 03 64 63 61 04 75 6e 74 64  .authns.dca.untd
00f0   03 63 6f 6d 00 00 01 00 01 00 00 02 58 00 04 40  .com........X..@
0100   88 2c 73 06 61 75 74 68 6e 73 03 69 61 64 04 75  .,s.authns.iad.u
0110   6e 74 64 03 63 6f 6d 00 00 01 00 01 00 00 02 58  ntd.com........X
0120   00 04 40 88 23 91                                ..@.#.


edit again: now even more:

A screenshot is below the BLUE ones are the ones I am talking about - the IGMP is normal from JUNO UNTD...

---

### Post by Mr. C. on 2007-08-22
This is multicast group membership communication.  It's normal.  Run:
```
netstat -rn

```
and you'll see the 224.0.0.1 multicast address configured.  A multicast address allows networking packets to be addressed to any number of computers at once.  Each client computer registers itself using IGMP so that routers know on which networks multicast packets should be forwarded.

You can disable multicast and IGMP on your router and system if you want.

MrC

---

### Post by nowshining on 2007-08-23
hmm somehow I got no email on this one, - i was waiting, anyway well windows Don't sent out IGMP or multicast just by opening a program not only does terminal do it, the Calculator does it and so does many others.. Can you explain to me how to sTOP this.. I do NOT LIKE IGMP nor multicast at all and I have no router...

edit: if your going to say to disable some services and stuff like that, THEY ARE ALREADY DISABLED - all that I can see anyway and it network tools it says multi cast disabled.

edit2: n/m on pp0 it's enabled somehow

edit3: found out how to do it, went into root terminal and did this

ifconfig ppp0 -multicast

then

ifconfig ppp0 -allmulti


as the last command kept giving me this warning

Warning: Interface ppp0 still in ALLMULTI mode.

but the first command when ran first fixed this up, lolz it took a bit but this page helped me a lot

[http://linux.die.net/man/8/ifconfig](http://linux.die.net/man/8/ifconfig)

yep thanks to that page it helped me...

---

### Post by Mr. C. on 2007-08-23
Good, sounds like you have it resolved.  But leave the Well Windows Doesn't Do It mentality.  You're dealing with an entirely different OS, utilities and behaviors.  You simple cannot compare the two this way.

Best of luck,
MrC

---

### Post by nowshining on 2007-08-24
no actually I sort of don't I found out that the Ifconfig -multicast only TEMP disables the ppp0 and it just comes right BACK after i dial out and back in however it did permanently remove the all multi but still unfortunately multicast is enabled all the time.. can it be removed impermanently ???


edit: found a way to disable it on each dialup but something still goes out to the net.  :frustrated: and yes I updated my how to on disabling multicast for ppp0 users...

---

