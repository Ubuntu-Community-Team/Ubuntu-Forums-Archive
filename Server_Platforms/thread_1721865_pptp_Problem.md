---
title: "pptp Problem"
date: 2011-04-05
forum: Server Platforms
---

### Post by drewsmith71 on 2011-04-05
I have managed to configure the server and it accepts connections from our network but not offsite.

Here the log for an accepted connection:

Apr  5 07:21:21 kayfoam pppd[18027]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Apr  5 07:21:21 kayfoam pppd[18027]: pppd 2.4.5 started by root, uid 0
Apr  5 07:21:21 kayfoam pppd[18027]: Using interface ppp0
Apr  5 07:21:21 kayfoam pppd[18027]: Connect: ppp0 <--> /dev/pts/1
Apr  5 07:21:24 kayfoam pppd[18027]: MPPE 128-bit stateless compression enabled
Apr  5 07:21:24 kayfoam pppd[18027]: local  IP address 192.168.0.1
Apr  5 07:21:24 kayfoam pppd[18027]: remote IP address 192.168.6.234

Heres the log for when it fails from external net:

Apr  5 07:23:03 kayfoam pppd[19911]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Apr  5 07:23:03 kayfoam pppd[19911]: pppd 2.4.5 started by root, uid 0
Apr  5 07:23:03 kayfoam pppd[19911]: Using interface ppp0
Apr  5 07:23:03 kayfoam pppd[19911]: Connect: ppp0 <--> /dev/pts/1
Apr  5 07:23:03 kayfoam kernel: [54438.008002] Inbound IN=eth0 OUT= MAC=00:19:99:17:b2:3e:00:1e:2a:48:07:c9:08:00 SRC=109.180.148.156 DST=192.168.1.3 LEN=60 TOS=0x00 PREC=0x00 TTL=227 ID=7549 PROTO=47 
Apr  5 07:23:06 kayfoam kernel: [54440.724312] Inbound IN=eth0 OUT= MAC=00:19:99:17:b2:3e:00:1e:2a:48:07:c9:08:00 SRC=109.180.148.156 DST=192.168.1.3 LEN=32 TOS=0x00 PREC=0x00 TTL=228 ID=3689 PROTO=47 
Apr  5 07:23:06 kayfoam kernel: [54440.765534] Inbound IN=eth0 OUT= MAC=00:19:99:17:b2:3e:00:1e:2a:48:07:c9:08:00 SRC=109.180.148.156 DST=192.168.1.3 LEN=65 TOS=0x00 PREC=0x00 TTL=228 ID=46353 PROTO=47 
Apr  5 07:23:06 kayfoam kernel: [54440.960604] Inbound IN=eth0 OUT= MAC=00:19:99:17:b2:3e:00:1e:2a:48:07:c9:08:00 SRC=109.180.148.156 DST=192.168.1.3 LEN=60 TOS=0x00 PREC=0x00 TTL=228 ID=31575 PROTO=47 
Apr  5 07:23:09 kayfoam kernel: [54443.724546] Inbound IN=eth0 OUT= MAC=00:19:99:17:b2:3e:00:1e:2a:48:07:c9:08:00 SRC=109.180.148.156 DST=192.168.1.3 LEN=32 TOS=0x00 PREC=0x00 TTL=228 ID=50046 PROTO=47 
Apr  5 07:23:09 kayfoam kernel: [54443.763889] Inbound IN=eth0 OUT= MAC=00:19:99:17:b2:3e:00:1e:2a:48:07:c9:08:00 SRC=109.180.148.156 DST=192.168.1.3 LEN=65 TOS=0x00 PREC=0x00 TTL=228 ID=39991 PROTO=47 
Apr  5 07:23:09 kayfoam kernel: [54443.964943] Inbound IN=eth0 OUT= MAC=00:19:99:17:b2:3e:00:1e:2a:48:07:c9:08:00 SRC=109.180.148.156 DST=192.168.1.3 LEN=60 TOS=0x00 PREC=0x00 TTL=228 ID=825 PROTO=47 
Apr  5 07:23:12 kayfoam kernel: [54446.722734] Inbound IN=eth0 OUT= MAC=00:19:99:17:b2:3e:00:1e:2a:48:07:c9:08:00 SRC=109.180.148.156 DST=192.168.1.3 LEN=65 TOS=0x00 PREC=0x00 TTL=228 ID=7039 PROTO=47 
Apr  5 07:23:12 kayfoam kernel: [54446.971291] Inbound IN=eth0 OUT= MAC=00:19:99:17:b2:3e:00:1e:2a:48:07:c9:08:00 SRC=109.180.148.156 DST=192.168.1.3 LEN=60 TOS=0x00 PREC=0x00 TTL=228 ID=50201 PROTO=47 
Apr  5 07:23:15 kayfoam kernel: [54449.766571] Inbound IN=eth0 OUT= MAC=00:19:99:17:b2:3e:00:1e:2a:48:07:c9:08:00 SRC=109.180.148.156 DST=192.168.1.3 LEN=65 TOS=0x00 PREC=0x00 TTL=228 ID=51304 PROTO=47 
Apr  5 07:23:15 kayfoam kernel: [54449.967550] Inbound IN=eth0 OUT= MAC=00:19:99:17:b2:3e:00:1e:2a:48:07:c9:08:00 SRC=109.180.148.156 DST=192.168.1.3 LEN=60 TOS=0x00 PREC=0x00 TTL=228 ID=50038 PROTO=47 
Apr  5 07:23:18 kayfoam kernel: [54452.766897] Inbound IN=eth0 OUT= MAC=00:19:99:17:b2:3e:00:1e:2a:48:07:c9:08:00 SRC=109.180.148.156 DST=192.168.1.3 LEN=65 TOS=0x00 PREC=0x00 TTL=228 ID=44305 PROTO=47 
Apr  5 07:23:18 kayfoam kernel: [54452.966191] Inbound IN=eth0 OUT= MAC=00:19:99:17:b2:3e:00:1e:2a:48:07:c9:08:00 SRC=109.180.148.156 DST=192.168.1.3 LEN=60 TOS=0x00 PREC=0x00 TTL=228 ID=11080 PROTO=47 
Apr  5 07:23:21 kayfoam kernel: [54455.763345] Inbound IN=eth0 OUT= MAC=00:19:99:17:b2:3e:00:1e:2a:48:07:c9:08:00 SRC=109.180.148.156 DST=192.168.1.3 LEN=65 TOS=0x00 PREC=0x00 TTL=228 ID=34133 PROTO=47 
Apr  5 07:23:21 kayfoam kernel: [54455.964278] Inbound IN=eth0 OUT= MAC=00:19:99:17:b2:3e:00:1e:2a:48:07:c9:08:00 SRC=109.180.148.156 DST=192.168.1.3 LEN=60 TOS=0x00 PREC=0x00 TTL=228 ID=63341 PROTO=47 
Apr  5 07:23:24 kayfoam kernel: [54458.730206] Inbound IN=eth0 OUT= MAC=00:19:99:17:b2:3e:00:1e:2a:48:07:c9:08:00 SRC=109.180.148.156 DST=192.168.1.3 LEN=65 TOS=0x00 PREC=0x00 TTL=228 ID=12904 PROTO=47 
Apr  5 07:23:24 kayfoam kernel: [54458.968821] Inbound IN=eth0 OUT= MAC=00:19:99:17:b2:3e:00:1e:2a:48:07:c9:08:00 SRC=109.180.148.156 DST=192.168.1.3 LEN=60 TOS=0x00 PREC=0x00 TTL=228 ID=5651 PROTO=47 
Apr  5 07:23:27 kayfoam kernel: [54461.765989] Inbound IN=eth0 OUT= MAC=00:19:99:17:b2:3e:00:1e:2a:48:07:c9:08:00 SRC=109.180.148.156 DST=192.168.1.3 LEN=65 TOS=0x00 PREC=0x00 TTL=228 ID=22643 PROTO=47 
Apr  5 07:23:27 kayfoam kernel: [54461.967106] Inbound IN=eth0 OUT= MAC=00:19:99:17:b2:3e:00:1e:2a:48:07:c9:08:00 SRC=109.180.148.156 DST=192.168.1.3 LEN=60 TOS=0x00 PREC=0x00 TTL=228 ID=58183 PROTO=47 
Apr  5 07:23:30 kayfoam kernel: [54464.768251] Inbound IN=eth0 OUT= MAC=00:19:99:17:b2:3e:00:1e:2a:48:07:c9:08:00 SRC=109.180.148.156 DST=192.168.1.3 LEN=65 TOS=0x00 PREC=0x00 TTL=228 ID=43310 PROTO=47 
Apr  5 07:23:30 kayfoam kernel: [54464.969359] Inbound IN=eth0 OUT= MAC=00:19:99:17:b2:3e:00:1e:2a:48:07:c9:08:00 SRC=109.180.148.156 DST=192.168.1.3 LEN=60 TOS=0x00 PREC=0x00 TTL=228 ID=1554 PROTO=47 
Apr  5 07:23:33 kayfoam pppd[19911]: LCP: timeout sending Config-Requests
Apr  5 07:23:33 kayfoam pppd[19911]: Connection terminated.
Apr  5 07:23:33 kayfoam pppd[19911]: Modem hangup
Apr  5 07:23:33 kayfoam pppd[19911]: Exit.
Apr  5 07:23:39 kayfoam kernel: [54473.314923] Inbound IN=eth0 OUT= MAC=00:19:99:17:b2:3e:00:1e:2a:48:07:c9:08:00 SRC=192.168.1.1 DST=192.168.1.3 LEN=29 TOS=0x00 PREC=0x00 TTL=64 ID=2 DF PROTO=UDP SPT=1432 DPT=7 LEN=9 


Any help would be great.

---

