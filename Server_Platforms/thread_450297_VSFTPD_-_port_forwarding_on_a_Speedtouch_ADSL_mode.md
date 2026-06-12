---
title: "VSFTPD - port forwarding on a Speedtouch ADSL modem?"
date: 2007-05-21
forum: Server Platforms
---

### Post by fyl2u on 2007-05-21
Hi.

I've got my Ubuntu machine working perfectly as an FTP server on my local area network and via loopback, and I've setup the port-forwarding how I thought it was supposed to be, but when I try to login by typing in the external IP address in a browser address bar, it gives me the login window but then says Access Denied.

I'm using VSFTPD, and the port forwarding rules I put in are as follows:
o
protocol: any (also tried it on TCP)
port range: 20-20
translate to: 20-20
trigger protocol: -
trigger port: -

protocol: any (also tried it on TCP)
port range: 21-21
translate to: 21-21
trigger protocol: -
trigger port: -

Any idea what I'm doing wrong?

Thanks in advance.

---

### Post by fyl2u on 2007-05-21
Nevermind - got it sorted... I was being an idiot.

---

