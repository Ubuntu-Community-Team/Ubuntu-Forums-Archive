---
title: "cannot burn 80 minute audio cd"
date: 2009-01-13
forum: Ubuntu Studio
---

### Post by scarf on 2009-01-13
ok i have two machines both running ubuntu 8.10, one is a laptop and the other is a desktop.  on the desktop, i cannot burn an audio cd which is close to 80 minutes.  however, the same project burns just fine on the laptop.  what happens on the desktop is that the burning process stops right towards the end, and k3b produces an error like "cdrecord has no permission to open the device".  all other types of projects (shorter audio cds, dvds, etc.) have so far worked just perfectly in k3b.

more details:

- project: single .wav with cue sheet, totalling 79m 56s
- media: verbatim 80 min cd-r


what is in common on both systems:

- burning application: k3b 1.0.5-1ubuntu6
- default settings (also, 'allow overburning' and 'force unsafe operations' are both unchecked)

what differs between systems:

- architecture: desktop is x86_64 and laptop is i686
- burner: desktop is optiarc ad-5170a and laptop is matshita ujda-755


i figure it is probably the optiarc burner, but i can't accept that just yet ;)



update: i have just experienced the error again in another project that is only 77m 56s

here is the tail end of k3b debugging output, where the error occurs:

```

...<snip>
Track 25: Total bytes read/written: 31718736/31718736 (12957 sectors).
Starting new track at sector: 348631
Track 26:    0 of    4 MB written.
Track 26:    1 of    4 MB written (fifo 100%) [buf 100%]  37.4x.
Track 26:    2 of    4 MB written (fifo 100%) [buf 100%]  36.8x.
Track 26:    3 of    4 MB written (fifo 100%) [buf 100%]  35.8x.
Track 26:    4 of    4 MB written (fifo 100%) [buf 100%]  37.0x.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 05 58 F3 00 00 1A 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 03 00 05 57 1E 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 349982 (valid) 
cmd finished after 0.010s timeout 40s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 4455360 bytes
Writing  time:  176.732s
Average write speed  30.9x.
Min drive buffer fill was 100%
Writing Leadout...
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 05 5A 27 00 00 1A 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.001s timeout 40s
write leadout data: error after 0 bytes
Fixating...
Fixating time:    0.002s
BURN-Free was never needed.
/usr/bin/wodim: fifo had 13503 puts and 13492 gets.
/usr/bin/wodim: fifo was 0 times empty and 6686 times full, min fill was 96%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=48 -raw96r driveropts=burnfree textfile=/tmp/k3bzuqtga.dat -eject -useinfo -audio /tmp/kde-scar/k3b_audio_0_01.inf /tmp/kde-scar/k3b_audio_0_02.inf /tmp/kde-scar/k3b_audio_0_03.inf /tmp/kde-scar/k3b_audio_0_04.inf /tmp/kde-scar/k3b_audio_0_05.inf /tmp/kde-scar/k3b_audio_0_06.inf /tmp/kde-scar/k3b_audio_0_07.inf /tmp/kde-scar/k3b_audio_0_08.inf /tmp/kde-scar/k3b_audio_0_09.inf /tmp/kde-scar/k3b_audio_0_10.inf /tmp/kde-scar/k3b_audio_0_11.inf /tmp/kde-scar/k3b_audio_0_12.inf /tmp/kde-scar/k3b_audio_0_13.inf /tmp/kde-scar/k3b_audio_0_14.inf /tmp/kde-scar/k3b_audio_0_15.inf /tmp/kde-scar/k3b_audio_0_16.inf /tmp/kde-scar/k3b_audio_0_17.inf /tmp/kde-scar/k3b_audio_0_18.inf /tmp/kde-scar/k3b_audio_0_19.inf /tmp/kde-scar/k3b_audio_0_20.inf /tmp/kde-scar/k3b_audio_0_21.inf /tmp/kde-scar/k3b_audio_0_22.inf /tmp/kde-scar/k3b_audio_0_23.inf /tmp/kde-scar/k3b_audio_0_24.inf /tmp/kde-scar/k3b_audio_0_25.inf /tmp/kde-scar/k3b_audio_0_26.inf 


```

---

### Post by scarf on 2009-01-27
:confused:

---

