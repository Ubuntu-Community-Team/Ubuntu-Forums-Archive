---
title: "gksudo Ubuntu 16.04 Server"
date: 2019-01-09
forum: Server Platforms
---

### Post by gevensen on 2019-01-09
I installed wireshark and it says i have to run it on terminal using gksudo
If I install gksudo will it turn my whole system into a gui or can i exit it for normal terminal work

---

### Post by slickymaster on 2019-01-09
Thread moved to **Server Platforms** for a better fit

---

### Post by QIII on 2019-01-09
Hello!

gksudo has very specific use cases, and one of its uses is to open graphical apps without fear of giving root ownership of your user directory and files.

If you have no GUI (typical for a server), just use sudo.

---

### Post by gevensen on 2019-01-09
I cant i get the following errors

QXcbConnection: Could not connect to display
Aborted (core dumped)

---

### Post by QIII on 2019-01-09
Would you please post the command you are entering and the results in their entirety?

---

### Post by volkswagner on 2019-01-09
I would consider a different way of doing things.

I'm not sure you really "need" Wireshark installed on your headless server.
You can create pcap files using tcpdump. Then analyze the file with a 
workstation with Wireshark installed (vs the server itself). I haven't tried it, but
you can also [view a live capture running on your server]("https://www.comparitech.com/net-admin/tcpdump-capture-wireshark/").

You if Wireshark is in fact installed on the server you can access it with ssh -X (x-forwarding).

---

### Post by gevensen on 2019-01-10
command /usr/bin/wiresharkresponse 


QXcbConnection: Could not connect to display
Aborted (core dumped)

---

### Post by gevensen on 2019-01-10
I am trying to track down repeated lines in my UFW log so I installed wireshark to review the packets

Jan  6 07:11:13 mail kernel: [1347540.590637] [UFW BLOCK] IN=eno1 OUT= MAC=01:00:5e:00:00:01:60:38:e0:cd:74:18:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=33340 PROTO=2

---

