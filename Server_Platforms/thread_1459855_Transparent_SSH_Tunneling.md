---
title: "Transparent SSH Tunneling"
date: 2010-04-21
forum: Server Platforms
---

### Post by jersak on 2010-04-21
Is it possible to make SSH tunneling transparent?
Normally, when you connect to something through a tunnel, the IP of the client is shown as the tunnel server's IP.

I would like to make the tunnel show the real client IP instead of the server's IP.

---

### Post by jersak on 2010-04-21
Transparent SSH Tunneling
Is it possible to make SSH tunneling transparent?
Normally, when you connect to something through a tunnel, the IP of the client is shown as the tunnel server's IP.

I would like to make the tunnel show the real client IP instead of the server's IP.

---

### Post by drs305 on 2010-04-22
Duplicate posts are discouraged on the Ubuntu forums. The second post originally placed in the Networking forum has been removed.

---

### Post by HermanAB on 2010-04-22
No, the return packets have to go back to the tunnel machine.

---

### Post by Brandon Williams on 2010-04-22
There might be some way for you to communicate the real client IP to the application server at the application layer. At the TCP/IP level, it must be the address and port of the tunnel server in order to ensure that return traffic goes back to the tunnel server. This is analagous to the client side connection, where you must tell the client to communicate with the local machine's address and port number.

If you have the necessary access rights on the SSH tunnel server, you might be able to [set up an SSH VPN](https://help.ubuntu.com/community/SSH_VPN). This would give your local machine a unique address on the remote network.

---

