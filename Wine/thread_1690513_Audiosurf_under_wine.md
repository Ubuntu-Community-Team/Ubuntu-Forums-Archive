---
title: "Audiosurf under wine"
date: 2011-02-18
forum: Wine
---

### Post by d3lug3 on 2011-02-18
Hi there, after a few days worth of forum reading, trying various doubtful solutions and more forum reading, I've come to the conclusion that I either need to start my own thread on this or simply run it on a virtual windows under ubuntu (which is like cheating to me!).

My problem is a game called Audiosurf. I've tried running it both with and without steam, but I run in to more or less the same issue which I haven't been able to find anyone else connect to Audiosurf, so I would be very happy if someone could sheath some light on this issue!

Here's my terminal when running it without steam:
> fixme:win:EnumDisplayDevicesW ((null),0,0xdae27c,0x00000000), stub!
fixme:d3d:query_init Unhandled query type 0x4.
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg0: Permission denied
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 1.
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg0: Permission denied
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 1.
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1f1f58,0x1f1e58): stub
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)


I'm running ubuntu 10.04 lucid with an Nvidia GeForce GT 220M and wine version 1.2.2

Please don't hesitate to ask for more information if it's needed.

-D3lug3

---

### Post by Jonessen on 2011-05-30
I had the same problem because i started Audiosurf from an NTFS.
I get less errrors when it's in the programs directory of wine. It actualy does't work, but there are ne permission errors anymore.
Copy it into this folder, and then, if you get other errors, ask somebody who really is good in that things :D

---

