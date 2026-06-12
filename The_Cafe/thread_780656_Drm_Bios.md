---
title: "Drm Bios"
date: 2008-05-03
forum: The Cafe
---

### Post by Craftycorner on 2008-05-03
I just found out that manufacturers like Phoenix are getting in bed with Microsoft and the AA's to put DRM in the BIO'S of the computer.  

How will this effect the running of the computer and running of non-DRM files or systems like Linux?  As we've learned from the Sony fiasco, DRM rootkits did far more than fart with music/video files.

---

### Post by Nem1976 on 2008-05-03
I did a google search and only found articles that were from 2003/2004.  
Can you post the article you read if it's more recent?

---

### Post by Craftycorner on 2008-05-03
I also got a lot of hits on something called Palladium and 'Trusted Computing'.  I don't mind things securing me, but I don't want doggie tags on my crap and or gizmos telling me what I can or can't do with my stuff!  :confused:

[http://search.techrepublic.com.com/search/digital+media+and+digital+rights+management+(drm)+and+hardware+and+security.html](http://search.techrepublic.com.com/search/digital+media+and+digital+rights+management+(drm)+and+hardware+and+security.html)
[http://www.zdnet.com.au/tag/copyright-drm-trust.htm](http://www.zdnet.com.au/tag/copyright-drm-trust.htm)

---

### Post by p_quarles on 2008-05-03
Not a support question, so moved to the Community Cafe.

---

### Post by zmjjmz on 2008-05-03
I found this a while ago:
[http://www.cl.cam.ac.uk/~rja14/tcpa-faq.html](http://www.cl.cam.ac.uk/~rja14/tcpa-faq.html)
TC looks pretty scary.
Very scary.

---

### Post by SunnyRabbiera on 2008-05-03
well there will probably be a way around it, TC is no threat considering the very cleaver linux community.

---

### Post by SuperSon!c on 2008-05-03
considering all of those articles are pretty old, i'd imagine they've jumped ship on that idea.  manufacturers would be complete idiots to back something like that.

---

### Post by PoopyTheJ on 2008-05-04
Still going strong unfortunately. Palladium and all the craziness associated with it has been pushed back for the next MS Os release but a LOT of the ideas and technologies associated with it are included in Vista already. It will potentially have a very detrimental effect on the Linux community. This is a very enlightening article here, [http://www.cs.auckland.ac.nz/~pgut001/pubs/vista_cost.html](http://www.cs.auckland.ac.nz/~pgut001/pubs/vista_cost.html), the Vista pimps like to attack this guy and call him unprofessional etc, but he's right about an awful lot. Unfortunately I see it regularly at my job.

---

### Post by Vadi on 2008-05-04
My laptop has a Phoenix BIOS, but it doesn't seem to have the fuzzy bed feeling you've been descripting. Pity.

Anyway, there is some restricted module mentioned in the bios that I remember, but it's been **disabled by default**, and I've never really bothered about it.

---

### Post by Craftycorner on 2008-05-04
Finding more current articles on Trusted Computing is like pulling teeth, but I found a 2005 article.... 
:lolflag:

[http://www.schneier.com/blog/archives/2005/08/trusted_computi.html](http://www.schneier.com/blog/archives/2005/08/trusted_computi.html)

---

### Post by tw3k on 2008-05-04
The quote below is from my bios. Been meaning to switch to [coreboot]("http://coreboot.org/").

> 
Calibrating delay loop... 304M loops per second. OK.
No LinuxBIOS table found.
Found chipset "VT8237", enabling flash write... OK.
Probing for Am29F040B, 512 KB
probe_29f040b: id1 0x49, id2 0x4d
Probing for Am29LV040B, 512 KB
probe_29f040b: id1 0x49, id2 0x4d
Probing for Am29F016D, 2048 KB
probe_29f040b: id1 0xff, id2 0xff
Probing for AE49F2008, 256 KB
probe_jedec: id1 0x26, id2 0xd4
Probing for At29C040A, 512 KB
probe_jedec: id1 0x49, id2 0x4d
Probing for At29C020, 256 KB
probe_jedec: id1 0x26, id2 0xd4
Probing for MBM29F400TC, 512 KB
probe_m29f400bt: id1 0x49, id2 0x44
Probing for MX29F002, 256 KB
probe_29f002: id1 0x26, id2 0xd4
Probing for MX25L4005, 512 KB
generic_spi_command called, but no SPI chipset detected
Probing for SST29EE020A, 256 KB
probe_jedec: id1 0x26, id2 0xd4
Probing for SST28SF040A, 512 KB
probe_28sf040: id1 0x49, id2 0x4d
Probing for SST39SF010A, 128 KB
probe_jedec: id1 0x0, id2 0x0
Probing for SST39SF020A, 256 KB
probe_jedec: id1 0x26, id2 0xd4
Probing for SST39SF040, 512 KB
probe_jedec: id1 0x49, id2 0x4d
Probing for SST39VF020, 256 KB
probe_jedec: id1 0x26, id2 0xd4
Probing for SST49LF040B, 512 KB
probe_jedec: id1 0x49, id2 0x4d
Probing for SST49LF040, 512 KB
probe_jedec: id1 0x49, id2 0x4d
Probing for SST49LF020A, 256 KB
probe_jedec: id1 0x26, id2 0xd4
Probing for SST49LF080A, 1024 KB
probe_jedec: id1 0xff, id2 0xff
Probing for SST49LF002A/B, 256 KB
probe_jedec: id1 0x26, id2 0xd4
Probing for SST49LF003A/B, 384 KB
probe_jedec: id1 0x5e, id2 0xcf
Probing for SST49LF004A/B, 512 KB
probe_jedec: id1 0x49, id2 0x4d
Probing for SST49LF008A, 1024 KB
probe_jedec: id1 0xff, id2 0xff
Probing for SST49LF004C, 512 KB
probe_49lfxxxc: id1 0x49, id2 0x4d
Probing for SST49LF008C, 1024 KB
probe_49lfxxxc: id1 0xff, id2 0xff
Probing for SST49LF016C, 2048 KB
probe_49lfxxxc: id1 0xff, id2 0xff
Probing for SST49LF160C, 2048 KB
probe_49lfxxxc: id1 0xff, id2 0xff
Probing for Pm49FL002, 256 KB
probe_jedec: id1 0x26, id2 0xd4
Probing for Pm49FL004, 512 KB
probe_jedec: id1 0x49, id2 0x4d
Probing for W29C011, 128 KB
probe_jedec: id1 0x0, id2 0x0
Probing for W29C040P, 512 KB
probe_jedec: id1 0x49, id2 0x4d
Probing for W29C020C, 256 KB
probe_jedec: id1 0x26, id2 0xd4
Probing for W29EE011, 128 KB
probe_w29ee011: id1 0x0, id2 0x0
Probing for W49F002U, 256 KB
probe_jedec: id1 0x26, id2 0xd4
Probing for W49V002A, 256 KB
probe_jedec: id1 0x26, id2 0xd4
Probing for W49V002FA, 256 KB
probe_jedec: id1 0x26, id2 0xd4
Probing for W39V040FA, 512 KB
probe_jedec: id1 0x49, id2 0x4d
Probing for W39V040A, 512 KB
probe_jedec: id1 0x49, id2 0x4d
Probing for W39V040B, 512 KB
probe_jedec: id1 0x49, id2 0x4d
Probing for W39V080A, 1024 KB
probe_jedec: id1 0xff, id2 0xff
Probing for M29F002B, 256 KB
probe_jedec: id1 0x26, id2 0xd4
Probing for M50FW040, 512 KB
probe_jedec: id1 0x49, id2 0x4d
Probing for M29W040B, 512 KB
probe_jedec: id1 0x49, id2 0x4d
Probing for M29F002T/NT, 256 KB
probe_jedec: id1 0x26, id2 0xd4
Probing for M29F400BT, 512 KB
probe_m29f400bt: id1 0x49, id2 0x44
Probing for M50FLW040A, 512 KB
probe_jedec: id1 0x49, id2 0x4d
Probing for M50FLW040B, 512 KB
probe_jedec: id1 0x49, id2 0x4d
Probing for M50FLW080A, 1024 KB
probe_jedec: id1 0xff, id2 0xff
Probing for M50FLW080B, 1024 KB
probe_jedec: id1 0xff, id2 0xff
Probing for M50FW080, 1024 KB
probe_jedec: id1 0xff, id2 0xff
Probing for M50FW016, 2048 KB
probe_jedec: id1 0xff, id2 0xff
Probing for M50LPW116, 2048 KB
probe_jedec: id1 0xff, id2 0xff
Probing for M29W010B, 128 KB
probe_jedec: id1 0x0, id2 0x0
Probing for M29F040B, 512 KB
probe_29f040b: id1 0x49, id2 0x4d
Probing for 82802ab, 512 KB
probe_82802ab: id1 0x49, id2 0x4d
Probing for 82802ac, 1024 KB
probe_82802ab: id1 0xff, id2 0xff
Probing for F49B002UA, 256 KB
probe_jedec: id1 0x26, id2 0xd4
Probing for LHF00L04, 1024 KB
probe_lhf00l04: id1 0xff, id2 0xff
Probing for S29C51001T, 128 KB
probe_jedec: id1 0x0, id2 0x0
Probing for S29C51002T, 256 KB
probe_jedec: id1 0x26, id2 0xd4
Probing for S29C51004T, 512 KB
probe_jedec: id1 0x49, id2 0x4d
Probing for S29C31004T, 512 KB
probe_jedec: id1 0x49, id2 0x4d
No EEPROM/flash device found.




> 
superiotool r2986
Probing for ALi Super I/O at 0x3f0...
  Failed. Returned data: id=0xffff, rev=0xff
Probing for ALi Super I/O at 0x370...
  Failed. Returned data: id=0xffff, rev=0xff
Probing for Fintek Super I/O at 0x2e...
  Failed. Returned data: vid=0xffff, id=0xffff
Probing for Fintek Super I/O at 0x4e...
  Failed. Returned data: vid=0xffff, id=0xffff
Probing for ITE Super I/O (init=0x87,0x01,0x55,0x55/0xaa) at 0x2e...
Found ITE IT8712F (id=0x8712, rev=0x8) at 0x2e
Register dump:
idx 07 20 21 22 23 24 2b
val 0a 87 12 08 10 1e 00
def NA 87 12 08 00 00 00
LDN 0x00 (Floppy)
idx 30 60 61 70 74 f0 f1
val 01 03 f0 06 02 00 80
def 00 03 f0 06 02 00 00
LDN 0x01 (COM1)
idx 30 60 61 70 f0 f1 f2 f3
val 01 03 f8 04 00 50 00 7f
def 00 03 f8 04 00 50 00 7f
LDN 0x02 (COM2)
idx 30 60 61 70 f0 f1 f2 f3
val 01 02 f8 03 00 50 00 7f
def 00 02 f8 03 00 50 00 7f
LDN 0x03 (Parallel port)
idx 30 60 61 62 63 70 74 f0
val 01 03 78 00 00 07 04 08
def 00 03 78 07 78 07 03 03
LDN 0x04 (Environment controller)
idx 30 60 61 62 63 70 f0 f1  f2 f3 f4 f5 f6
val 01 02 90 00 00 00 80 80  0a 00 80 00 ff
def 00 02 90 02 30 09 00 00  00 00 00 NA NA
LDN 0x05 (Keyboard)
idx 30 60 61 62 63 70 71 f0
val 00 00 60 00 64 00 02 48
def 01 00 60 00 64 01 02 08
LDN 0x06 (Mouse)
idx 30 70 71 f0
val 00 0c 02 00
def 00 0c 02 00
LDN 0x07 (GPIO)
idx 25 26 27 28 29 2a 2c 60  61 62 63 64 65 70 71 72  73 74 b0 b1 b2 b3 b4 b5  b8 b9 ba bb bc bd c0 c1  c2 c3 c4 c8 c9 ca cb cc  e0 e1 e2 e3 e4 f0 f1 f2  f3 f4 f5 f6 f7 f8 f9 fa  fb fc fd
val 00 00 00 00 01 80 1f 00  00 08 00 08 20 00 01 00  38 00 00 00 00 00 01 00  60 08 00 00 00 00 00 00  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  00 00 00 28 00 00 00 00  00 00 00
def 01 00 00 40 00 00 00 00  00 00 00 00 00 00 00 00  c0 00 00 00 00 00 00 00  00 00 00 00 00 00 01 00  00 40 00 01 00 00 40 00  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  00 NA 00
LDN 0x08 (MIDI port)
idx 30 60 61 70 f0
val 00 03 00 0a 00
def 00 03 00 0a 00
LDN 0x09 (Game port)
idx 30 60 61
val 00 02 01
def 00 02 01
LDN 0x0a (Consumer IR)
idx 30 60 61 70 f0
val 00 03 10 0b 06
def 00 03 10 0b 00
Probing for ITE Super I/O (init=0x87,0x87) at 0x2e...
  Failed. Returned data: id=0xffff, rev=0xf
Probing for ITE Super I/O (init=0x87,0x01,0x55,0x55/0xaa) at 0x4e...
  Failed. Returned data: id=0xffff, rev=0xf
Probing for ITE Super I/O (init=0x87,0x87) at 0x4e...
  Failed. Returned data: id=0xffff, rev=0xf
Probing for NSC Super I/O at 0x2e...
  Failed. Returned data: port=0xff, port+1=0xff
Probing for NSC Super I/O at 0x4e...
  Failed. Returned data: port=0xff, port+1=0xff
Probing for SMSC Super I/O (idregs=0x20/0x21) at 0x2e...
  Failed. Returned data: id=0xff, rev=0xff
Probing for SMSC Super I/O (idregs=0x0d/0x0e) at 0x2e...
  Failed. Returned data: id=0xff, rev=0xff
Probing for SMSC Super I/O (idregs=0x20/0x21) at 0x4e...
  Failed. Returned data: id=0xff, rev=0xff
Probing for SMSC Super I/O (idregs=0x0d/0x0e) at 0x4e...
  Failed. Returned data: id=0xff, rev=0xff
Probing for SMSC Super I/O (idregs=0x20/0x21) at 0x162e...
  Failed. Returned data: id=0xff, rev=0xff
Probing for SMSC Super I/O (idregs=0x0d/0x0e) at 0x162e...
  Failed. Returned data: id=0xff, rev=0xff
Probing for SMSC Super I/O (idregs=0x20/0x21) at 0x164e...
  Failed. Returned data: id=0xff, rev=0xff
Probing for SMSC Super I/O (idregs=0x0d/0x0e) at 0x164e...
  Failed. Returned data: id=0xff, rev=0xff
Probing for SMSC Super I/O (idregs=0x20/0x21) at 0x3f0...
  Failed. Returned data: id=0xff, rev=0xff
Probing for SMSC Super I/O (idregs=0x0d/0x0e) at 0x3f0...
  Failed. Returned data: id=0xff, rev=0xff
Probing for SMSC Super I/O (idregs=0x20/0x21) at 0x370...
  Failed. Returned data: id=0xff, rev=0xff
Probing for SMSC Super I/O (idregs=0x0d/0x0e) at 0x370...
  Failed. Returned data: id=0xff, rev=0xff
Probing for Winbond Super I/O (init=0x88) at 0x2e...
  Failed. Returned data: id/oldid=0xff/0x0f, rev=0xff
Probing for Winbond Super I/O (init=0x89) at 0x2e...
  Failed. Returned data: id/oldid=0xff/0x0f, rev=0xff
Probing for Winbond Super I/O (init=0x86,0x86) at 0x2e...
  Failed. Returned data: id/oldid=0xff/0x0f, rev=0xff
Probing for Winbond Super I/O (init=0x87,0x87) at 0x2e...
  Failed. Returned data: id/oldid=0xff/0x0f, rev=0xff
Probing for Winbond Super I/O (init=0x88) at 0x4e...
  Failed. Returned data: id/oldid=0xff/0x0f, rev=0xff
Probing for Winbond Super I/O (init=0x89) at 0x4e...
  Failed. Returned data: id/oldid=0xff/0x0f, rev=0xff
Probing for Winbond Super I/O (init=0x86,0x86) at 0x4e...
  Failed. Returned data: id/oldid=0xff/0x0f, rev=0xff
Probing for Winbond Super I/O (init=0x87,0x87) at 0x4e...
  Failed. Returned data: id/oldid=0xff/0x0f, rev=0xff
Probing for Winbond Super I/O (init=0x88) at 0x3f0...
  Failed. Returned data: id/oldid=0xff/0x0f, rev=0xff
Probing for Winbond Super I/O (init=0x89) at 0x3f0...
  Failed. Returned data: id/oldid=0xff/0x0f, rev=0xff
Probing for Winbond Super I/O (init=0x86,0x86) at 0x3f0...
  Failed. Returned data: id/oldid=0xff/0x0f, rev=0xff
Probing for Winbond Super I/O (init=0x87,0x87) at 0x3f0...
  Failed. Returned data: id/oldid=0xff/0x0f, rev=0xff
Probing for Winbond Super I/O (init=0x88) at 0x370...
  Failed. Returned data: id/oldid=0xff/0x0f, rev=0xff
Probing for Winbond Super I/O (init=0x89) at 0x370...
  Failed. Returned data: id/oldid=0xff/0x0f, rev=0xff
Probing for Winbond Super I/O (init=0x86,0x86) at 0x370...
  Failed. Returned data: id/oldid=0xff/0x0f, rev=0xff
Probing for Winbond Super I/O (init=0x87,0x87) at 0x370...
  Failed. Returned data: id/oldid=0xff/0x0f, rev=0xff
Probing for Winbond Super I/O (init=0x88) at 0x250...
  Failed. Returned data: id/oldid=0xff/0x0f, rev=0xff
Probing for Winbond Super I/O (init=0x89) at 0x250...
  Failed. Returned data: id/oldid=0xff/0x0f, rev=0xff
Probing for Winbond Super I/O (init=0x86,0x86) at 0x250...
  Failed. Returned data: id/oldid=0xff/0x0f, rev=0xff
Probing for Winbond Super I/O (init=0x87,0x87) at 0x250...
  Failed. Returned data: id/oldid=0xff/0x0f, rev=0xff



---

### Post by SunnyRabbiera on 2008-05-04
the thing is that I dont think trusted computing will ever effect linux, after all most of those on the list for it are linux supporters (mainly HP and even intel these days)
I dont think this will place linux anywhere

---

### Post by unknown03 on 2008-05-04
[http://ubuntuforums.org/showthread.php?t=738405]("http://ubuntuforums.org/showthread.php?t=738405")

It may be time to switch to Linux BIOS *when* that happens

---

### Post by zmjjmz on 2008-05-04
AFAIK the TC part will be built into the processor's architecture or something.
I may be wrong and tired.

---

### Post by SunnyRabbiera on 2008-05-04
however it wont make things windows only for sure, you can bet that if TC limits linux a lot of folks are going to be mad.
and there comes the revolution.

---

### Post by Craftycorner on 2008-05-04
> **SunnyRabbiera said:**
> however it wont make things windows only for sure, you can bet that if TC limits linux a lot of folks are going to be mad.
and there comes the revolution.

What gives me the shivers is all the memories of the Sony rootkit and what it did to all the legally purchased CD's when played on computers.  This Trusted Computing and built In Bios sounds an awful lot like a Sony Rootkit on steroids.

Admittedly, the supersized hard drives can be formatted to delete all the DRM for holding multiple Operating Systems.  This sounds like a move to kick Linux out of the box.  

What kind of work is being done to the Linux kernel to reside in such a BIOS?:(

---

### Post by samjh on 2008-05-04
> **Craftycorner said:**
> What kind of work is being done to the Linux kernel to reside in such a BIOS?:(

The kernel doesn't reside in a BIOS.  But it must work with the BIOS for input and output operations.

The Linux kernel has supported TCM for some time.  Since 2.6.12 I think.

IBM is also working on enlarging TCM support for Linux:
[http://www.linuxelectrons.com/news/linux/15574/ibm-brings-trusted-computing-linux](http://www.linuxelectrons.com/news/linux/15574/ibm-brings-trusted-computing-linux)

The potential for problems arises when TCM triggers files or software to be wiped or fail to run/open because of lack of authentication.  There are also economic and political negatives, such as vendor lock-in and the potential for malevolent governments (and other organisations and individuals) to censor materials they don't want made public.

---

### Post by helliewm on 2008-05-04
Isn't there a Linux BIOS too?

Helen

---

### Post by samjh on 2008-05-04
> **helliewm said:**
> Isn't there a Linux BIOS too?

Indeed there is: [http://www.coreboot.org/Welcome_to_coreboot](http://www.coreboot.org/Welcome_to_coreboot)

:)

---

### Post by drascus on 2008-05-04
> I also got a lot of hits on something called Palladium and 'Trusted Computing'. I don't mind things securing me

First of all "Trusted Computing" (I call it Treacherous computing) is not a means fo securing you. If you have heard this it is just propeganda. The only function these technologies have is for your computer to disobey you and obey somone else. They are a direct attack on the user an therefore cannot be looked at as securing the user. It really just secures the content providers ability to hurt the person should they choose. 

Second there is Free Bios now adays. They won't go on all chipsets but you can just buy a motherboard which you can install Free Bios on. So I think that we will ultimately be OK if they should lock down BIOS. I just think that it will make it much harder to install Gnu/Linux on a computer in the future. 

read this article for more: [http://http://www.gnu.org/philosophy/can-you-trust.html]("http://http://www.gnu.org/philosophy/can-you-trust.html")

---

### Post by original_jamingrit on 2008-05-04
Here's a video for those who need a quick explanation.  It talks about the original intention of Trusted Computing, and why it's no longer intended to be in your hands.

[http://www.youtube.com/watch?v=XgFbqSYdNK4](http://www.youtube.com/watch?v=XgFbqSYdNK4)

---

### Post by Craftycorner on 2008-05-04
OK, Trusted computing is one rotten #####.  How can you make sure, how can the Linux community be sure that future computers (older ones will age and become scarce after a while) will be usable and free of this funk?

---

### Post by zmjjmz on 2008-05-04
Spread those videos.

---

