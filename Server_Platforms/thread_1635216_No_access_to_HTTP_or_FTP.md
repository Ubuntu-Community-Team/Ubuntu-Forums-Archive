---
title: "No access to HTTP or FTP"
date: 2010-12-01
forum: Server Platforms
---

### Post by akromm on 2010-12-01
So here is my problem.  I have recently set up a server with Ubuntu Server 10.10.

In my router configuration i have forwarded ports FTP, HTTP, and SSH.

From within my LAN I can access the webpages on the server (running apache2) and i can access ftp.

But from outside of my LAN i can only access SSH.  FTP and HTTP dont work.

Whether i try connecting from within my lan or outside of my lan I'm using a web address (eg adam.server.org (Not the actual address)) which is the IP address of my router (im using no-ip services.)

So, anyone know why i cant access HTTP or FTP from outside of my LAN??

Thanks.
Adam

---

### Post by pricetech on 2010-12-01
Just to make sure I understand;  Are you trying to use your internal domain name externally ??

If you use your external IP and port forwarding is set up in your router, it should just plain work.

---

### Post by akromm on 2010-12-01
No, I'm trying to use my external IP address.  Using my external IP when outside of my LAN I have access to ssh but not http or ftp, even though all 3 ports are forwarded.  Using my external IP when inside of my LAN i have access to all 3.

-Adam.

---

### Post by SeijiSensei on 2010-12-02
The ports may be blocked by your provider.  Try using a couple of ports above 1024 on your router and forwarding them back to the server.  Use, say, 30080 and 30021 and forward them back to 80 and 21 respectively.  If that works (e.g., http://192.168.1.1:30080/), but 80 and 21 do not, the ISP is likely blocking them.

Do your ISP's terms of service forbid servers?  If so, they make enforce the policy by blocking inbound FTP and HTTP connections.

---

### Post by akromm on 2010-12-02
You where right, they are blocking those ports.  Thanks.

---

