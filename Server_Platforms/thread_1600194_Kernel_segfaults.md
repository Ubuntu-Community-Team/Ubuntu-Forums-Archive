---
title: "Kernel segfaults"
date: 2010-10-18
forum: Server Platforms
---

### Post by jiriki on 2010-10-18
Hello,

I wonder what's the correct place to report this issue. Maybe Linux kernel mailing lists? Basically I'm running stock ubuntu kernel and I get segfaults if I renice my gaming server threads. Currently I use chrt only to get better priorities and no segfaults. Its running 64-bit ubuntu but the game server binaries are 32-bit. It happens both for HL1 and HL2 servers. I think I had this problem before with CK kernel aswell. I haven't got any segfaults even with higher loads without renicing.

This only happens if the game servers are crowded.

```
[487475.181119] srcds_i486[22147]: segfault at 0 ip 00000000f5a13f41 sp 00000000ff989070 error 4 in matchmaking_ds_i486.so[f59e7000+76000]
[489113.152060] srcds_i486[29128]: segfault at 0 ip 00000000f595bf41 sp 00000000ffeb47a0 error 4 in matchmaking_ds_i486.so[f592f000+76000]
[489356.535774] srcds_i486[30377]: segfault at 0 ip 00000000f59d4f41 sp 00000000ffda5690 error 4 in matchmaking_ds_i486.so[f59a8000+76000]
[489858.366696] srcds_i486[32732]: segfault at 0 ip 00000000f5977f41 sp 00000000ffc7f450 error 4 in matchmaking_ds_i486.so[f594b000+76000]
[490106.364405] srcds_linux[1344]: segfault at 4b459089 ip 00000000f4d4ed4f sp 00000000ffad3750 error 4 in vphysics.so[f4c67000+29e000]
[490126.056718] srcds_i486[1480]: segfault at 0 ip 00000000f59a8f41 sp 00000000ffdc5dd0 error 4 in matchmaking_ds_i486.so[f597c000+76000]
[490277.981658] srcds_i486[2193]: segfault at 0 ip 00000000f598af41 sp 00000000fff62bc0 error 4 in matchmaking_ds_i486.so[f595e000+76000]
[490521.989283] srcds_i486[3075]: segfault at 0 ip 00000000f5a07f41 sp 00000000ffb97450 error 4 in matchmaking_ds_i486.so[f59db000+76000]
[490681.197642] srcds_i486[3732]: segfault at 0 ip 00000000f59fef41 sp 00000000ffbde180 error 4 in matchmaking_ds_i486.so[f59d2000+76000]
[491027.464585] hlds_i686[20979]: segfault at 1ac ip 00000000f4e0c966 sp 00000000ffc653d0 error 4 in ns_i386.so[f4c53000+2f7000]
[491093.567429] srcds_i486[6517]: segfault at 0 ip 00000000f5972f41 sp 00000000ff807620 error 4 in matchmaking_ds_i486.so[f5946000+76000]
[491367.640835] srcds_i486[7967]: segfault at 0 ip 00000000f59a2f41 sp 00000000ffd0c7a0 error 4 in matchmaking_ds_i486.so[f5976000+76000]
[491490.954751] srcds_i486[8689]: segfault at 0 ip 00000000f59c8f41 sp 00000000ff823bc0 error 4 in matchmaking_ds_i486.so[f599c000+76000]
[491615.730137] srcds_i486[9347]: segfault at 0 ip 00000000f5a0df41 sp 00000000ffcc48a0 error 4 in matchmaking_ds_i486.so[f59e1000+76000]
[491984.217915] srcds_i486[11389]: segfault at 0 ip 00000000f597ef41 sp 00000000fffba600 error 4 in matchmaking_ds_i486.so[f5952000+76000]
[492090.771309] srcds_linux[12045]: segfault at ca064015 ip 00000000f4d84d4f sp 00000000ff917ba0 error 4 in vphysics.so[f4c9d000+29e000]
[492091.951560] srcds_linux[12064]: segfault at 0 ip 00000000f6cc9de2 sp 00000000ff9172d0 error 6 in engine.so[f6b79000+258000]
[492220.395323] srcds_i486[12673]: segfault at 0 ip 00000000f597af41 sp 00000000ff82db40 error 4 in matchmaking_ds_i486.so[f594e000+76000]
[493884.078503] srcds_i486[19701]: segfault at 0 ip 00000000f5931f41 sp 00000000ff80ede0 error 4 in matchmaking_ds_i486.so[f5905000+76000]
[495549.070993] srcds_i486[25901]: segfault at 0 ip 00000000f5981f41 sp 00000000ff901f30 error 4 in matchmaking_ds_i486.so[f5955000+76000]
[495827.127060] srcds_i486[27141]: segfault at 0 ip 00000000f59fcf41 sp 00000000ffd174b0 error 4 in matchmaking_ds_i486.so[f59d0000+76000]
[499094.666198] srcds_i486[18475]: segfault at 0 ip 00000000f5938f41 sp 00000000ffee7800 error 4 in matchmaking_ds_i486.so[f590c000+76000]
```

Also if someone can clarify if there's actually any advantage of renicing if one is using chrt, I'd be glad to know.

---

