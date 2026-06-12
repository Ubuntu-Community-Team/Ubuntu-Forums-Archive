---
title: "LTSP and nbd_disconnect problem"
date: 2016-09-29
forum: Server Platforms
---

### Post by abix_adam_pl on 2016-09-29
I have DELL R160 server working with xUbuntu 16.04 and LTSP-pnp fat-clients.
From time to time, I have strange situation - on some PC's (pxe
terminals) I see that icons are disappears from desktop, and there is no
connction with home directory served by nbd in server. Ping is ok
beetwen client and server (I have tested). I turned on logging and I see
in syslog:

nbd_server[25520]: Read failed: Connection reset by peer

The clients logs to the server:
Sep 29 14:29:34 PC16 kernel: [ 82.864511] block nbd9: NBD_DISCONNECT
Sep 29 14:29:34 PC16 kernel: [ 82.865905] block nbd9: Receive control
failed (result -32)
Sep 29 14:29:41 PC03 kernel: [ 878.836660] traps: chrome[5939] general
protection ip:7fb8c04fc186 sp:7ffcc9d47490 error:0 in
Sep 29 14:29:42 PC18 kernel: [ 1191.184294] perf interrupt took too long
(5025 > 5000), lowering kernel.perf_event_max_sample_
Sep 29 14:29:49 PC03 kernel: [ 887.110768] traps: chrome[5955] general
protection ip:7efe800fd186 sp:7fff3c423fb0 error:0 in

Does anybody had something like that?

---

