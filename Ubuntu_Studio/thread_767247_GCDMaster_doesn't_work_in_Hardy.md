---
title: "GCDMaster doesn't work in Hardy"
date: 2008-04-25
forum: Ubuntu Studio
---

### Post by Dingbats on 2008-04-25
I have just installed Hardy Heron, and now gcdmaster doesn't work.  When I run *sudo gcdmaster project.toc*, I get this over and over (you have to run it as root):

```
Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
```

When I run it with gksudo, it opens fine.  It only recognizes the burner the first time I try it after logging in.  Then when I try to burn the CD, the burning process dialog opens and after a few seconds it says that it aborted with error.

After a failed attempt at burning, Ubuntu won't recognize the disk drive at all.  If I insert a CD (empty/burned/music) nothing happens.

gcdmaster also takes abnormally long to open.  It used to work just fine in Gutsy.

Please please tell me there is a way around this!

---

### Post by Dingbats on 2008-04-28
No one..?  :(

---

### Post by billd42 on 2008-05-17
No help here, but I get the same error.  I'm just getting started on the project of ripping a substantial vinyl collection to digital, so I've no idea whether this worked under Gutsy.

---

### Post by Stochastic on 2008-05-19
Actually I get the same error for about 10 consecutive times, then it changes to /dev/hda for about 30 times (each error takes a full second, obviously) but then the app loads.  It seems to be able to play files and add songs.  I didn't attempt to open any .toc files, save a project, or burn a CD, so if anyone wants to give that a shot and report back...

I ran an strace and it looks like there's lots of bad requests going on, though I'm only beginning to be able to read those files.

Here's a launchpad bug that describes the issue: [https://bugs.launchpad.net/ubuntu/+source/cdrdao/+bug/2765](https://bugs.launchpad.net/ubuntu/+source/cdrdao/+bug/2765) that seems to have been around for the past two and a half years.  There's a supposed fix linked to in the comments, but nothing has been acted on (from what I see) to get the fix into the repos (despite the fix being posted back in 2006 and the bug being on the top of the "Ubuntu Burning Team" list of four bugs).  Though I've yet to try the fix myself for confirmation.
---Calling all devs, someone please take action---

The long and short of this is that the app looks promising, but I would never use an app with this many VISIBLE errors in any mastering process.

---

### Post by andrew.46 on 2008-05-19
Hi,

I seem to have perhaps a variation of this problem. The cdrdao command works fine:

```
andrew@skamandros:~$ sudo cdrdao scanbus
Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check http://cdrdao.sourceforge.net/drives.html#dt for current driver tables.

Using libscg version 'ubuntu-0.8ubuntu1'

1,0,0 : Optiarc , DVD+-RW AD-5560A, DD11

```

But the program gcdmaster does not work at all. Not a big problem for me as I prefer the command line version :-).

     Andrew

---

### Post by andrew.46 on 2008-05-19
Hi,

There may be a way:

> **Dingbats said:**
> Please please tell me there is a way around this!

gcdmaster is simply a front for cdrdao. Have a look at:

[http://ubuntuforums.org/showthread.php?t=795181](http://ubuntuforums.org/showthread.php?t=795181)

which I wrote a couple of days ago and see if this works where gcdmaster fails.

           Andrew

---

### Post by Stochastic on 2008-05-19
> **andrew.46 said:**
> Have a look at:

[http://ubuntuforums.org/showthread.php?t=795181](http://ubuntuforums.org/showthread.php?t=795181)

which I wrote a couple of days ago and see if this works where gcdmaster fails.

Um, that's only for copying CDs, gcdmaster is not intended for simply copying CDs.

---

### Post by andrew.46 on 2008-05-20
Hi,

> **Stochastic said:**
> Um, that's only for copying CDs, gcdmaster is not intended for simply copying CDs.

cdrdao will do everything that gcdmaster does (gcdmaster being only a front-end) and unlike gcdmaster it *works* under Hardy Heron. The guide does not deal explicitly with more complex material as it is intended only as a beginning.

       Andrew

---

### Post by tmndz on 2008-07-18
Well, today the problem reached me: GCDMaster starts extremely slow and finds no devices, cdrdao can't scan devices.
What happens is that GCDMaster on startup as well as "cdrdao scanbus" attempts to open all available character devices /dev/sg0, /dev/sg1, and so on.
On my system, /dev/sg0 is related to my harddrive /dev/sda and belongs to the group "disk", whereas /dev/sg1 is for the CDROM drive and belongs to the "cdrom" group.
So, as quick'n'dirty workaround, I added myself to the group "disk" and everything now is working as it should.

---

### Post by dannyboy79 on 2010-01-10
this is not working for me for some reason. I just installed karmic to a usb casper-rw image and its awesome but now I am having issues with creating a dvd, most likely a cd also. Here's my /dev/ list of cd and dvd devices:

ls -la /dev/ | grep cd
lrwxrwxrwx   1 root   root           9 2010-01-10 08:39 cdrom -> /dev/scd1
lrwxrwxrwx   1 root   root           3 2010-01-08 23:18 cdrom2 -> sr0
lrwxrwxrwx   1 root   root           3 2010-01-08 23:19 cdrom3 -> sr1
lrwxrwxrwx   1 root   root           3 2010-01-08 23:18 cdrw2 -> sr0
lrwxrwxrwx   1 root   root           3 2010-01-08 23:19 cdrw3 -> sr1
drwxr-xr-x   2 root   root          60 2010-01-08 23:16 pktcdvd
lrwxrwxrwx   1 root   root           3 2010-01-08 23:16 scd0 -> sr0
lrwxrwxrwx   1 root   root           3 2010-01-08 23:16 scd1 -> sr1
crw-rw----   1 root   cdrom    21,   0 2010-01-08 23:16 sg0
crw-rw----   1 root   cdrom    21,   1 2010-01-08 23:16 sg1
brw-rw----+  1 root   cdrom    11,   0 2010-01-08 23:16 sr0
brw-rw----+  1 root   cdrom    11,   1 2010-01-08 23:16 sr1

and dvd devices:
ls -la /dev/ | grep dvd
lrwxrwxrwx   1 root   root           3 2010-01-08 23:18 dvd2 -> sr0
lrwxrwxrwx   1 root   root           3 2010-01-08 23:19 dvd3 -> sr1
lrwxrwxrwx   1 root   root           3 2010-01-08 23:18 dvdrw2 -> sr0
lrwxrwxrwx   1 root   root           3 2010-01-08 23:19 dvdrw3 -> sr1
drwxr-xr-x   2 root   root          60 2010-01-08 23:16 pktcdvd

so I made sure I am in the cdrom group. see here:
daniel adm dialout fax cdrom tape audio dip video plugdev fuse lpadmin netdev admin sambashare mythtv

when i issue cdrdao scanbus either as with sudo or not, i get this:
sudo cdrdao scanbus
Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check [http://cdrdao.sourceforge.net/drives.html#dt](http://cdrdao.sourceforge.net/drives.html#dt) for current driver tables.

Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.

here's my fstab entries if that matters:
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

and the mount directories do exist:
drwxr-xr-x  2 root   root   2048 2010-01-10 08:26 cdrom0
drwxr-xr-x  2 root   root   2048 2010-01-10 08:26 cdrom1

so I am at a loss of what I need to do to be able to burn dvd's or cd's.

---

### Post by dannyboy79 on 2010-01-10
making permission for cdrdao and wodim to look like this had solved it.

-rws--x---    1 root     cdrom      512680 19. Jan 12:29 cdrdao


before i couldn't even issue cdrdao scanbus, it would return the error about accessing device exclusively blah blah,

nope, nevermind. i tried to burn a dvd structure iso file using k3b and this is what it rrturns:

[http://pastebin.com/f4748b2d4](http://pastebin.com/f4748b2d4)



and also I tried again:

[http://pastebin.com/f7520fec8](http://pastebin.com/f7520fec8)



also here is the tail end of dmesg

sr 0:0:1:0: [sr1] Unhandled sense code
[ 3404.771821] sr 0:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3404.771826] sr 0:0:1:0: [sr1] Sense Key : Hardware Error [current] 
[ 3404.771831] sr 0:0:1:0: [sr1] Add. Sense: Timeout on logical unit
[ 3404.771837] end_request: I/O error, dev sr1, sector 0
[ 3404.771843] Buffer I/O error on device sr1, logical block 0
[ 3404.771850] Buffer I/O error on device sr1, logical block 1
[ 3404.771853] Buffer I/O error on device sr1, logical block 2
[ 3404.771856] Buffer I/O error on device sr1, logical block 3
[ 3404.771859] Buffer I/O error on device sr1, logical block 4
[ 3404.771862] Buffer I/O error on device sr1, logical block 5
[ 3404.771865] Buffer I/O error on device sr1, logical block 6
[ 3404.771868] Buffer I/O error on device sr1, logical block 7
[ 3404.771871] Buffer I/O error on device sr1, logical block 8
[ 3411.610001] sr 0:0:1:0: [sr1] Unhandled sense code
[ 3411.610006] sr 0:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3411.610010] sr 0:0:1:0: [sr1] Sense Key : Hardware Error [current] 
[ 3411.610015] sr 0:0:1:0: [sr1] Add. Sense: Timeout on logical unit
[ 3411.610022] end_request: I/O error, dev sr1, sector 0
[ 3411.610027] __ratelimit: 23 callbacks suppressed
[ 3411.610031] Buffer I/O error on device sr1, logical block 0
[ 3432.125011] sr 0:0:1:0: [sr1] Unhandled sense code
[ 3432.125016] sr 0:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3432.125020] sr 0:0:1:0: [sr1] Sense Key : Hardware Error [current] 
[ 3432.125025] sr 0:0:1:0: [sr1] Add. Sense: Timeout on logical unit
[ 3432.125032] end_request: I/O error, dev sr1, sector 0
[ 3432.125037] Buffer I/O error on device sr1, logical block 0
[ 3432.125044] Buffer I/O error on device sr1, logical block 1
[ 3432.125047] Buffer I/O error on device sr1, logical block 2
[ 3432.125051] Buffer I/O error on device sr1, logical block 3
[ 3445.781853] sr 0:0:1:0: [sr1] Unhandled sense code
[ 3445.781857] sr 0:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3445.781862] sr 0:0:1:0: [sr1] Sense Key : Hardware Error [current] 
[ 3445.781867] sr 0:0:1:0: [sr1] Add. Sense: Timeout on logical unit
[ 3445.781874] end_request: I/O error, dev sr1, sector 0
[ 3445.781880] Buffer I/O error on device sr1, logical block 0
[ 3459.438738] sr 0:0:1:0: [sr1] Unhandled sense code
[ 3459.438742] sr 0:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3459.438747] sr 0:0:1:0: [sr1] Sense Key : Hardware Error [current] 
[ 3459.438752] sr 0:0:1:0: [sr1] Add. Sense: Timeout on logical unit
[ 3459.438758] end_request: I/O error, dev sr1, sector 0
[ 3459.438764] Buffer I/O error on device sr1, logical block 0
[ 3792.004352] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 3792.004369] ata3.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[ 3792.004371]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 3792.004374] ata3.00: status: { DRDY }
[ 3797.016751] ata3: link is slow to respond, please be patient (ready=0)
[ 3802.016587] ata3: soft resetting link
[ 3805.432445] ata3.00: configured for UDMA/133
[ 3805.432467] ata3: EH complete
[ 5461.228649] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5461.228656] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 5461.228661] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 5461.228668] end_request: I/O error, dev sr0, sector 0
[ 5461.228672] Buffer I/O error on device sr0, logical block 0
[ 5461.229582] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5461.229586] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 5461.229591] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 5461.229596] end_request: I/O error, dev sr0, sector 0
[ 5461.229600] Buffer I/O error on device sr0, logical block 0
[ 5461.393059] cdrom: This disc doesn't have any tracks I recognize!
[ 5716.704845] warning: `growisofs' uses 32-bit capabilities (legacy support in use)
[ 5832.236035] end_request: I/O error, dev fd0, sector 0
[ 5832.326143] UDF-fs: No anchor found
[ 5832.326147] UDF-fs: Rescanning with blocksize 2048
[ 5832.467535] UDF-fs: No anchor found
[ 5832.467540] UDF-fs: No partition found (1)
[ 5832.500342] ISOFS: Unable to identify CD-ROM format.
[ 6867.062925] aufs au_plink_append:280:dpkg[18296]: unexpectedly many pseudo links, 101
[ 6876.543972] aufs au_plink_append:280:dpkg[18296]: unexpectedly many pseudo links, 357
[ 6878.993052] aufs au_plink_append:280:dpkg[18296]: unexpectedly many pseudo links, 613
[ 6886.361586] aufs au_plink_append:280:dpkg[18296]: unexpectedly many pseudo links, 869
[ 7950.316372] sr 0:0:1:0: [sr1] Unhandled sense code
[ 7950.316377] sr 0:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7950.316381] sr 0:0:1:0: [sr1] Sense Key : Hardware Error [current] 
[ 7950.316386] sr 0:0:1:0: [sr1] Add. Sense: Timeout on logical unit
[ 7950.316393] end_request: I/O error, dev sr1, sector 0
[ 7950.316398] Buffer I/O error on device sr1, logical block 0
[ 8405.410901] sr 0:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8405.410908] sr 0:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[ 8405.410913] sr 0:0:1:0: [sr1] Add. Sense: Logical block address out of range
[ 8405.410919] end_request: I/O error, dev sr1, sector 0
[ 8405.410924] Buffer I/O error on device sr1, logical block 0
[ 8405.418034] sr 0:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8405.418039] sr 0:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[ 8405.418044] sr 0:0:1:0: [sr1] Add. Sense: Logical block address out of range
[ 8405.418050] end_request: I/O error, dev sr1, sector 0
[ 8405.418056] Buffer I/O error on device sr1, logical block 0
[ 8405.444280] cdrom: This disc doesn't have any tracks I recognize!

dont know if this matters but this is karmic koala installed into a casper-rw (4g in size) running from a 16gb verbatim usb stick

---

### Post by dannyboy79 on 2010-01-24
bump, pleae help. i can't burn any dvd iso's and i am trying to figure out if this is media problem or hardware problem. thank you

turns out to maybe a media / linux tools problem (dvdrecord, wodim, cdrdao, k3b, brasero). i can't burn any dvd iso's in linux when using these generic dynex dvd-r discs on either a 

NEC AD-7170A

or 

DVDRW IDE 16X A091

dvd burners, every error is the same, power calibration error or other various errors.

but if I go over to my windows 7 box and use poweriso to burn that same dvd iso file onto the same media using a 

NEC DVDRW ND-2510A

it burns just fine.

---

