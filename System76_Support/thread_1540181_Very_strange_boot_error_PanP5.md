---
title: "Very strange boot error: PanP5"
date: 2010-07-27
forum: System76 Support
---

### Post by gamerchick02 on 2010-07-27
I have a PanP5 from June 2009.

I left my computer on and went to lunch (nothing different; I do this all the time) and came back.  My computer seemed to shut down, or reboot or something (I didn't initiate it).

I'm getting a very long bootup time and when it does boot, I get this error (on a white-text-on-black terminal):

Intel UNDI, PXE-2.1 (build 082)
Copyright (C) 1997-2000 Intel Corporation

For Realtek RTL8111B/8111C Gigabit Ethernet Controller v2.0 (071105)

Client MAC ADDR: 00 90 F5 91 CC FC GUID: 0090F591-CCFC-000-000-000000000000
PXE-E53: No boot filename received

PXE-M0F: Exiting PXE ROM.
Operating System not found

So, it's something to do with my ethernet?  Or is it something to do with Ubuntu?

For the record, I have Ubuntu 10.04 and Win7 on this computer, and both were working just fine up til a half hour ago.

Amy

---

### Post by gamerchick02 on 2010-07-27
Update:

Booted into a liveCD, and my system hard drive is not detected at all.

Any thoughts?

I've never had a hard drive do this before.

Amy

---

### Post by gamerchick02 on 2010-07-27
Another update:

My hard drive is clicking.  Sounds like it died.

I got this replaced last year in November.

So, I guess I need a new hard drive?

Amy

---

### Post by marshmallow1304 on 2010-07-27
Sounds like it.  From the first post, it looks like the BIOS was trying to initiate a [PXE]("http://en.wikipedia.org/wiki/Preboot_Execution_Environment") boot, which could happen if PXE was after hard drive in the boot order and the hard drive was not found, which would happen if it had died.

---

### Post by gamerchick02 on 2010-07-27
Yeah, sounds about right.  I have a drive my brother gave me, but it's only 200 gb.  Will suffice for now.

I'd really like Tom or isantop to respond.  See what they can do; if they can ship a new HD to me or whatever.

Amy

---

### Post by isantop on 2010-07-28
Hi Amy.

Please email us at support...at...system76...dot...com

---

### Post by gamerchick02 on 2010-07-28
Thanks. I'll send out an email this afternoon.

Amy

---

