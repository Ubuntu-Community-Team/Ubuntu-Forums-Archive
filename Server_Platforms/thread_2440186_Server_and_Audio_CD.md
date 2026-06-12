---
title: "Server and Audio CD"
date: 2020-04-07
forum: Server Platforms
---

### Post by maurocn on 2020-04-07
I put an audio CD and it's impossible to mount it

It returns this:
```

[COLOR=#454545][FONT=&quot][    2.944473] sr 2:0:0:0: [sr0] tag#12 Sense Key : Illegal Request [current] [/FONT][/COLOR]
[COLOR=#454545][FONT=&quot][    2.944883] sr 2:0:0:0: [sr0] tag#12 Add. Sense: Illegal mode for this track[/FONT][/COLOR]
[COLOR=#454545][FONT=&quot][    2.945258] sr 2:0:0:0: [sr0] tag#12 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00[/FONT][/COLOR]
[COLOR=#454545][FONT=&quot][    2.945620] blk_update_request: I/O error, dev sr0, sector 0[/FONT][/COLOR]
[COLOR=#454545][FONT=&quot][    2.956043] sr 2:0:0:0: [sr0] tag#13 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE[/FONT][/COLOR]
[COLOR=#454545][FONT=&quot][    2.956406] sr 2:0:0:0: [sr0] tag#13 Sense Key : Illegal Request [current] [/FONT][/COLOR]
[COLOR=#454545][FONT=&quot][    2.956751] sr 2:0:0:0: [sr0] tag#13 Add. Sense: Illegal mode for this track[/FONT][/COLOR]
[COLOR=#454545][FONT=&quot][    2.957085] sr 2:0:0:0: [sr0] tag#13 CDB: Read(10) 28 00 00 00 00 00 00 00 01 00[/FONT][/COLOR]
[COLOR=#454545][FONT=&quot][    2.957417] blk_update_request: I/O error, dev sr0, sector 0[/FONT][/COLOR]
[COLOR=#454545][FONT=&quot][    2.957758] Buffer I/O error on dev sr0, logical block 0, async page read[/FONT][/COLOR]
[COLOR=#454545][FONT=&quot][    2.968042] sr 2:0:0:0: [sr0] tag#15 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE[/FONT][/COLOR]

```

Just to clarify the Ubuntu Server 16.04 runs as VM on a ESXi 6.5 Server.
If I link the CD to a Windows VM it works.

Any suggestion?
Thnx
M.

---

### Post by LHammonds on 2020-04-07
[https://askubuntu.com/questions/102406/how-to-find-mount-point-for-audio-cd-dvd](https://askubuntu.com/questions/102406/how-to-find-mount-point-for-audio-cd-dvd)

---

### Post by maurocn on 2020-04-07
Basically I didn&#8217;t realised that Audio CDs has no file system.
Even the errors (that at this point they&#8217;re not an error) just launch cdparanoia and the tracks are recognised.

thank you

---

