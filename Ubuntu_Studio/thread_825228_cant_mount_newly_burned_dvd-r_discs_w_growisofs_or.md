---
title: "cant mount newly burned dvd-r discs w/ growisofs or k3b"
date: 2008-06-10
forum: Ubuntu Studio
---

### Post by mowgliee on 2008-06-10
first, my symptoms/history:

i've been burning dvd data files using same drive & OS & PC for 6+ months now.  2 weeks ago i added some sessions to a dvd-r using growisofs from cmd line.  no issues, readable on all drives.  (wouldnt it be great if the story ended there?)  today i tried to use same method to burn a new dvd-r using:

growisofs -Z /dev/cdrw -v -v -l -R -J -joliet-long file.name

to which the result was it takes a long time as though it is really burning the disc and even says:
Executing 'genisoimage -v -v -l -R -J -joliet-long 030308jupiter.BWUSA.tar.bz2 030308jupiter.tar.bz2 | builtin_dd of=/dev/cdrw obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage 1.1.2 (Linux)
  28   550 
Cache hit for '/..'
      31   881010 030308jupiter.BWUSA.tar.bz2
  881011   881138 030308jupiter.tar.bz2
Writing:   Initial Padblock                        Start Block 0
Done with: Initial Padblock                        Block(s)    16
Writing:   Primary Volume Descriptor               Start Block 16
Done with: Primary Volume Descriptor               Block(s)    1
Writing:   Joliet Volume Descriptor                Start Block 17
Done with: Joliet Volume Descriptor                Block(s)    1
Writing:   End Volume Descriptor                   Start Block 18
Done with: End Volume Descriptor                   Block(s)    1
Writing:   Version block                           Start Block 19
Done with: Version block                           Block(s)    1
Writing:   Path table                              Start Block 20
Done with: Path table                              Block(s)    4
Writing:   Joliet path table                       Start Block 24
Done with: Joliet path table                       Block(s)    4
Writing:   Directory tree                          Start Block 28
Done with: Directory tree                          Block(s)    1
Writing:   Joliet directory tree                   Start Block 29
Done with: Joliet directory tree                   Block(s)    1
Writing:   Directory tree cleanup                  Start Block 30
Done with: Directory tree cleanup                  Block(s)    0
Writing:   Extension record                        Start Block 30
Done with: Extension record                        Block(s)    1
Writing:   The File(s)                             Start Block 31
Total extents scheduled to be written = 881289
/dev/cdrw: "Current Write Speed" is 4.1x1352KBps.
:-[ WRITE@LBA=10h failed with SK=5h/ASC=21h/ACQ=02h]: Invalid argument
:-( write failed: Invalid argument
/dev/cdrw: flushing cache
/dev/cdrw: updating RMA
/dev/cdrw: closing session

but if i try to mount that newly burned disc:
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

& dmesg | tail says:
attempt to access beyond end of device
sr0: rw=0, want=68, limit=4
isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

if i use same growisofs cmd on the now hopefully multisession dvd-r disc to add sessions, the result was:
:-[ WRITE@LBA=0h failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
:-( media is not formatted or unsupported.
:-( write failed: Wrong medium type

but its the same media, drive, pc, method i used to add sessions previously.  the original session (aka original burn) on the successful multi-session dvd-r discs was created using k3b.  so i started up gdm & k3b and this is where it gets really weird!  when i load a blank dvd-r, system mounts it and asks if i want to create a data dvd using gnome-baker (i assume since thats the default).  i say no and run k3b.  on first run, k3b recognizes the device but "no media present."  so i close k3b.  its still mounted.  restart k3b, now no device found!!!!  cant manually add it either!  AND when i close k3b, the disc is no longer mounted AND i cant eject it (pushing eject button or using eject /dev/scd0 from cmd line).

if i reboot, everything is normal (device found, mounts blanks fine) but the whole process repeats.

system info:  ubuntu feisty w/ auto daily aptitude updates from all repos, dvd burner = LG 4040B, media = verbatim dvd-r, pc = dell poweredge 400sc w/ 1 gb DDRAM.

some other info:

dvd+rw-mediainfo /dev/scd0 w/o disc loaded (note that dvd dvdrw cdrom cdrw are just symlinks to scd0):
INQUIRY:                [HL-DT-ST][DVDRAM GSA-4040B][A304]
GET [CURRENT] CONFIGURATION:
:-( no media mounted, exiting...

dvd+rw-mediainfo /dev/scd0 w/ blank dvd-r loaded:
INQUIRY:                [HL-DT-ST][DVDRAM GSA-4040B][A304]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         11h, DVD-R Sequential
 Media ID:              MCC 02RG20  
 Current Write Speed:   4.0x1385=5540KB/s
 Write Speed #0:        4.0x1385=5540KB/s
 Write Speed #1:        2.0x1385=2770KB/s
GET [CURRENT] PERFORMANCE:
 Write Performance:     4.0x1385=5540KB/s@[0 -> 2298495]
 Speed Descriptor#0:    02/2298495 R@3.3x1385=4584KB/s W@4.0x1385=5540KB/s
 Speed Descriptor#1:    02/2298495 R@3.3x1385=4584KB/s W@2.0x1385=2770KB/s
READ DVD STRUCTURE[#0h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Legacy lead-out at:    2298496*2KB=4707319808
READ DISC INFORMATION:
 Disc status:           blank
 Number of Sessions:    1
 State of Last Session: empty
 "Next" Track:          1
 Number of Tracks:      1
READ TRACK INFORMATION[#1]:
 Track State:           invisible incremental
 Track Start Address:   0*2KB
 Next Writable Address: 0*2KB
 Free Blocks:           2297888*2KB
 Track Size:            2297888*2KB
READ CAPACITY:          0*2048=0

if i do dvd+rw-mediainfo /dev/scd0 w/ the attempted burned disc which i cannot mount:
INQUIRY:                [HL-DT-ST][DVDRAM GSA-4040B][A304]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         11h, DVD-R Sequential
 Media ID:              MCC 02RG20  
 Current Write Speed:   4.0x1385=5540KB/s
 Write Speed #0:        4.0x1385=5540KB/s
 Write Speed #1:        2.0x1385=2770KB/s
GET [CURRENT] PERFORMANCE:
 Write Performance:     4.0x1385=5540KB/s@[0 -> 2298495]
 Speed Descriptor#0:    02/2298495 R@3.3x1385=4584KB/s W@4.0x1385=5540KB/s
 Speed Descriptor#1:    02/2298495 R@3.3x1385=4584KB/s W@2.0x1385=2770KB/s
READ DVD STRUCTURE[#10h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Legacy lead-out at:    16*2KB=32768
READ DVD STRUCTURE[#0h]:
 Media Book Type:       25h, DVD-R book [revision 5]
 Last border-out at:    2045*2KB=4188160
READ DISC INFORMATION:
 Disc status:           appendable
 Number of Sessions:    2
 State of Last Session: empty
 "Next" Track:          2
 Number of Tracks:      2
READ TRACK INFORMATION[#1]:
 Track State:           complete incremental
 Track Start Address:   0*2KB
 Free Blocks:           0*2KB
 Track Size:            65264*2KB
 Last Recorded Address: 15*2KB
READ TRACK INFORMATION[#2]:
 Track State:           invisible incremental
 Track Start Address:   93952*2KB
 Next Writable Address: 93952*2KB
 Free Blocks:           2203936*2KB
 Track Size:            2203936*2KB
FABRICATED TOC:
 Track#1  :             14@0
 Track#AA :             14@16
 Multi-session Info:    #1@0
READ CAPACITY:          16*2048=32768

so its clearly burning something.  there are more sessions and tracks and data on the output of the post burn disc.  and the disc even looks burned in the right amount.

so what the heck is going on?  is this related to firmware and k3b?  how can that be when it worked to burn additional sessions w/ cmd line growisofs in the recent past?  and it worked to burn initial sessions w/ k3b in the recent past?  why cant i mount it on any dvd drive?  or even on the dvd burner drive which made it?  why does k3b fail to see the media for a fresh new blank dvd-r and then kill the device?  why does the system not even recognize the device after k3b is killed?  why dont our votes really count in any federal election?

pls help b/c, frankly, i just dont need this many coasters!!!

i dont even know where to begin troubleshooting :(  PLEASE HELP!!!

---

