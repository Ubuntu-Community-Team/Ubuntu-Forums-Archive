---
title: "Storageworks RA4100, Emulex LP8000"
date: 2008-05-01
forum: Server Platforms
---

### Post by Ferret-Simpson on 2008-05-01
Ok, I'll admit it - I'm stuck.

I have my Emulex card in the machine and the RA4100 hooked up over optical fibre channel. The status lights all show good - but the problem is that the LP can't seem to see the RA.

Is this a wonderful quirk of SAN tech that I was not forewarned of? Namely that Arrays only work with one HBA?

Or is there a step I'm missing in my assumption of "Install OS, log in, mount /dev/sdb"..?

Thanks

iGraham

---

### Post by Ferret-Simpson on 2008-05-02
```
[   99.304760] Emulex LightPulse Fibre Channel SCSI driver 8.2.2
[   99.304769] Copyright(c) 2004-2007 Emulex.  All rights reserved.
[  108.665574] lpfc 0000:03:06.0: 0:1303 Link Up Event x1 received Data: x1 x1 x0 x0
[  108.667319] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x4 to remote NPORT xfffffe Retried:3 Error:x3/18
[  109.666923] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xef Retried:3 Error:x3/18
[  109.667397] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xe8 Retried:3 Error:x3/18
[  109.667898] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xe4 Retried:3 Error:x3/18
[  109.668365] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xe2 Retried:3 Error:x3/18
[  109.668868] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xe1 Retried:3 Error:x3/18
[  109.669337] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xe0 Retried:3 Error:x3/18
[  109.669839] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xdc Retried:3 Error:x3/18
[  109.670309] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xda Retried:3 Error:x3/18
[  109.670814] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xd9 Retried:3 Error:x3/18
[  109.685325] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xd6 Retried:3 Error:x3/18
[  109.685808] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xd5 Retried:3 Error:x3/18
[  109.686303] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xd4 Retried:3 Error:x3/18
[  109.686775] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xd3 Retried:3 Error:x3/18
[  109.687262] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xd2 Retried:3 Error:x3/18
[  109.687758] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xd1 Retried:3 Error:x3/18
[  109.688225] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xce Retried:3 Error:x3/18
[  109.688711] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xcd Retried:3 Error:x3/18
[  109.689184] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xcc Retried:3 Error:x3/18
[  109.689671] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xcb Retried:3 Error:x3/18
[  109.690146] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xca Retried:3 Error:x3/18
[  109.690637] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xc9 Retried:3 Error:x3/18
[  109.691117] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xc7 Retried:3 Error:x3/18
[  109.691612] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xc6 Retried:3 Error:x3/18
[  109.702773] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xc5 Retried:3 Error:x3/18
[  109.703228] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xc3 Retried:3 Error:x3/18
[  109.703734] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xbc Retried:3 Error:x3/18
[  109.704199] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xba Retried:3 Error:x3/18
[  109.704693] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xb9 Retried:3 Error:x3/18
[  109.705171] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xb6 Retried:3 Error:x3/18
[  109.718577] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xb5 Retried:3 Error:x3/18
[  109.719039] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xb4 Retried:3 Error:x3/18
[  109.719533] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xb3 Retried:3 Error:x3/18
[  109.720007] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xb2 Retried:3 Error:x3/18
[  109.720501] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xb1 Retried:3 Error:x3/18
[  109.720978] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xae Retried:3 Error:x3/18
[  109.721481] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xad Retried:3 Error:x3/18
[  109.721942] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xac Retried:3 Error:x3/18
[  109.722429] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xab Retried:3 Error:x3/18
[  109.722913] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xaa Retried:3 Error:x3/18
[  109.723402] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xa9 Retried:3 Error:x3/18
[  109.723883] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xa7 Retried:3 Error:x3/18
[  109.724396] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xa6 Retried:3 Error:x3/18
[  109.724854] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xa5 Retried:3 Error:x3/18
[  109.725351] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xa3 Retried:3 Error:x3/18
[  109.725883] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x9f Retried:3 Error:x3/18
[  109.726318] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x9e Retried:3 Error:x3/18
[  109.726798] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x9d Retried:3 Error:x3/18
[  109.727303] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x9b Retried:3 Error:x3/18
[  109.727766] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x98 Retried:3 Error:x3/18
[  109.728272] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x97 Retried:3 Error:x3/18
[  109.728733] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x90 Retried:3 Error:x3/18
[  109.732522] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x8f Retried:3 Error:x3/18
[  109.732573] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x88 Retried:3 Error:x3/18
[  109.733028] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x84 Retried:3 Error:x3/18
[  109.733488] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x82 Retried:3 Error:x3/18
[  109.734001] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x81 Retried:3 Error:x3/18
[  109.734473] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x80 Retried:3 Error:x3/18
[  109.734966] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x7c Retried:3 Error:x3/18
[  109.735472] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x7a Retried:3 Error:x3/18
[  109.735933] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x79 Retried:3 Error:x3/18
[  109.736422] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x76 Retried:3 Error:x3/18
[  109.736884] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x75 Retried:3 Error:x3/18
[  109.737358] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x74 Retried:3 Error:x3/18
[  109.737847] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x73 Retried:3 Error:x3/18
**[  109.754908] scsi 0:0:0:0: RAID              COMPAQ   ARRAY CONTROLLER 2.60 PQ: 0 ANSI: 0**
[  110.662978] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x72 Retried:3 Error:x3/18
[  110.663455] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x71 Retried:3 Error:x3/18
[  110.675387] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x6e Retried:3 Error:x3/18
[  110.675866] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x6d Retried:3 Error:x3/18
[  110.676322] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x6c Retried:3 Error:x3/18
[  110.676796] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x6b Retried:3 Error:x3/18
[  110.677260] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x6a Retried:3 Error:x3/18
[  110.678192] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x69 Retried:3 Error:x3/18
[  110.678205] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x67 Retried:3 Error:x3/18
[  110.708743] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x66 Retried:3 Error:x3/18
[  110.709196] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x65 Retried:3 Error:x3/18
[  110.709685] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x63 Retried:3 Error:x3/18
[  110.710158] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x5c Retried:3 Error:x3/18
[  110.710650] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x5a Retried:3 Error:x3/18
[  110.711102] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x59 Retried:3 Error:x3/18
[  110.712035] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x56 Retried:3 Error:x3/18
[  110.712049] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x55 Retried:3 Error:x3/18
[  110.712536] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x54 Retried:3 Error:x3/18
[  110.712993] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x53 Retried:3 Error:x3/18
[  110.713932] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x52 Retried:3 Error:x3/18
[  110.713946] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x51 Retried:3 Error:x3/18
[  110.714871] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x4e Retried:3 Error:x3/18
[  110.714885] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x4d Retried:3 Error:x3/18
[  110.724835] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x4c Retried:3 Error:x3/18
[  110.725330] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x4b Retried:3 Error:x3/18
[  110.725786] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x4a Retried:3 Error:x3/18
[  110.726257] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x49 Retried:3 Error:x3/18
[  110.726728] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x47 Retried:3 Error:x3/18
[  110.727190] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x46 Retried:3 Error:x3/18
[  110.735331] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x45 Retried:3 Error:x3/18
[  110.735795] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x43 Retried:3 Error:x3/18
[  110.736278] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x3c Retried:3 Error:x3/18
[  110.737207] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x3a Retried:3 Error:x3/18
[  110.737219] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x39 Retried:3 Error:x3/18
[  110.737701] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x36 Retried:3 Error:x3/18
[  110.738177] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x35 Retried:3 Error:x3/18
[  110.752613] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x34 Retried:3 Error:x3/18
[  110.753097] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x33 Retried:3 Error:x3/18
[  110.753571] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x32 Retried:3 Error:x3/18
[  110.754022] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x31 Retried:3 Error:x3/18
[  110.754510] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x2e Retried:3 Error:x3/18
[  110.754977] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x2d Retried:3 Error:x3/18
[  110.755915] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x2c Retried:3 Error:x3/18
[  110.755929] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x2b Retried:3 Error:x3/18
[  110.756407] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x2a Retried:3 Error:x3/18
[  110.756864] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x29 Retried:3 Error:x3/18
[  110.757803] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x27 Retried:3 Error:x3/18
[  110.757818] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x26 Retried:3 Error:x3/18
[  110.758295] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x25 Retried:3 Error:x3/18
[  110.758756] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x23 Retried:3 Error:x3/18
[  110.759709] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x1f Retried:3 Error:x3/18
[  110.759733] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x1e Retried:3 Error:x3/18
[  110.765545] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x1d Retried:3 Error:x3/18
[  110.765571] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x1b Retried:3 Error:x3/18
[  110.765584] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x18 Retried:3 Error:x3/18
[  110.765596] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x17 Retried:3 Error:x3/18
[  110.765635] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x10 Retried:3 Error:x3/18
[  110.765648] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT xf Retried:3 Error:x3/18
[  110.766150] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x8 Retried:3 Error:x3/18
[  110.766611] lpfc 0000:03:06.0: 0:(0):0108 No retry ELS command x3 to remote NPORT x4 Retried:3 Error:x3/18

```

Ok, so that's the relevant output from my latest boot dmesg.

Status lights are all good on both devices: 

RA4100 reads TX and RX active. 
LP8000 reads Link Up.

Nothing interesting is in /dev/ - i.e. no StorageWorks access.

---

### Post by Ferret-Simpson on 2008-05-02
Well, since the RA is recognised by the lpfc driver (Hundreds of errors notwithstanding) I'm trying to install the HP Array controller drivers. At the very leat it;ll give me control and monitoring for my onboard RAID, and may help with the External RAID.

Does no-one really have any idea about the HBA incompat question!?

Anyway. I get an error on trying:

gas001@DJun-Keep:~$ hpacucli 
touch: cannot touch `/opt/compaq/cpqacuxe/bld/locks/CPQACU_MUTEX': Permission denied
/opt/compaq/hpacucli/bld/.hpacucli: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

Suggestions?

---

### Post by rustybronco on 2008-05-02
Have you tried installing the fibreutils.rpm (there may be a deb for it) ? 
[http://people.debian.org/~osamu/pub/getwiki/wiki/all-popcon-results.txt](http://people.debian.org/~osamu/pub/getwiki/wiki/all-popcon-results.txt)
> Package: fibreutils    0     0     0     2

---

### Post by Ferret-Simpson on 2008-05-02
Fibreutils is primarily a driver for the Qlogic Compaq HBA's. I'm using the LP8000.

My current theory (Since the LP is able to at least see the existence of the RA) is that the RA is set to FC_AL whereas the lpfc driver seems to force it into FC_p2p.

When I changed the Emulex BIOS plugin from P2P to Arbitrated Loop, I was able to see not only the RA but also a LUN from within the BIOS. Unfortunately, the BIOS setting is ignored by lpfc.

I also tried changing the /etc/modules/options file to force FC_AL but the driver seems to have ignored it. :(

Am I editing a config file that isn't looked at? Where should I enter my options?

---

### Post by rustybronco on 2008-05-03
> **Ferret-Simpson said:**
> 
I have my Emulex card in the machine and the RA4100 hooked up over optical fibre channel. The status lights all show good - but the problem is that the LP can't seem to see the RA.

Is this a wonderful quirk of SAN tech that I was not forewarned of? Namely that Arrays only work with one HBA?
iGrahamWell it very well may be that your LP7800 can not work with the RA4100 [http://forums12.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1209819951171+28353475&threadId=218250](http://forums12.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1209819951171+28353475&threadId=218250)

you can try getting and loading different drivers for the LP7800 and give it a go, but it will require a lot of time on your part.

or just get a hca that is known to work with the RA4100.

I wish I could help more than that.

---

### Post by Ferret-Simpson on 2008-05-03
Thanks for the link - it just proved my point.

I don't WANT to reconfigure the array. If I need to, I'll boot into Windows/ReactOS and go from there.

All I want to do is access the currently configured LUNs. And in that post, he clearly states he could DO that on Windows, just like I can do it in the Emulex BIOS.

I just need to know how to switch the Emulex lpfc drivers from FC_P2P to FC_AL

It's like hooking a econet connector into an ethernet port - they're both networks, but they can't understand each other.

My Array has a Fibre Channel Arbitrated Loop port.

My HBA has a DUAL MODE port - that Linux is forcing into NODE (N) (Port 2 Port) mode. I JUST need to switch it to AL. Sod the configuration of the thing! I can do that by serial port!

---

### Post by Ferret-Simpson on 2008-05-03
Sorry. Just re-read my post and realised how exasperated I sounded! :oops:

But ignoring how irritated this simple problem is making me - thats the face of it. One configuration option that I'm having difficulty solving. Once I can get that changed, I can read and write to the array - which is good enough for now.

---

### Post by Ferret-Simpson on 2008-05-19
Well, there's something to be said for experimentation - I HAVE MY LUN!!!!!!!!!

I still can't access it though. :/

Ok - I took the advice of a friend (Really dumb thing I should have done myself:)

sudo modprobe -vr lpfc
sudo modprobe -v lpfc lpfc_topology=0x4

As it turns out, my problem was that I had entered 0x04 instead of 0x4 into /etc/modprobe.d/options - so now that it's corrected, I still get a fistload of "NPORT" errors, BUT:

[ XXXX.XXXXXX] scsi 3:0:0:0: Attached scsi generic sg1 type 12

A little googling revealed the "sg3-utils" package, from which I ran:

sudo sg_map

Outputting:

/dev/sg0 /dev/scd0
/dev/sg1 

Because obviously the first is me ide-scsi (Or possibly pure scsi, who knows!?) CD-ROM drive. After that, there is no script on how to deal with /dev/sg1 (Not a block device, needs to be mapped first) so it sits there. I need to know how to map a "scsi generic" device, to a block device. Anyone know?

If I work it out, I'll post it in - this sounds like fun, high level UNIX learning. :)

---

### Post by Ferret-Simpson on 2008-05-19
Now I see the main problem!

Which also leaves me temporarily stumped. :/

My sg1, should be accompanied by an sg 2,3,4 for each LUN - as in - a controller scsi ID ("LUN 0") plus one for each LUN. Which means that all the configuration on the RAID Array has been wiped, and my LUN in the bios was the all encompassing, absolutely unuseable LUN0.

It's also impossible to get hold of the RA4100 manual, so it looks like I'll be installing a Windows OS on one of my machines (Obviously not the Xserve) and since I've just got the server running so at all, I'll leave that one for now (Though I do plan on reinstalling to bring myself back to original OS specs, then do the basics from there.)

I'll keep you posted.

---

### Post by Ferret-Simpson on 2008-05-20
DO NOT TAKE ME FOR SOME CONJURER OF CHEAP TRICKS!

Ok, so: I wiped the system and rebuilt to use a 10GB Hardy partition, a 2GB Swap partition, and installed Windows on the remaining 6GB. (RAID 1+0, 2x18.2GB)

Then installed all Windows 2000 compliant drivers for the LP8000 from Emulex.com.

Then installed the Compaq Array Configuration Utility from ftp.compaq.com.

Then updated the LP8000 to the latest firmware and boot code....

Viola! The LP8000 and CPQ Array Config Utility worked perfectly together (LP8000 using scsiport miniport drivers) and I could do an autoconfig of two nice big juicy 52GB LUN's (Which I can later replace if need be with bigger ones from bigger hard disks. :) )

Ladies and gentlemen, I present my server. :D

---

