---
title: "Personal VPN"
date: 2009-01-22
forum: Security
---

### Post by maclarke on 2009-01-22
I used JiWire SpotLock in Windows. On its website its described as* Using powerful IPSec encryption technology, the gold standard for corporate virtual private networks (VPNs), JiWire SpotLock creates a secure "tunnel" that protects your inbound and outbound Wi-Fi communications (Email, Web, IM, VOIP calls, FTP, etc.) at any Wi-Fi hotspot*.

Is there a Linux equivalent?

---

### Post by tribaal on 2009-01-22
Well depending on exactly what you wish to do, there are several options available in linux (as usual).

The two obvious answers on top of my head would be:

1. Install OpenVPN on your server machine. NetworkManager comes with a client that installs easily and conveniently lets you connect to your VPN (all GUI based).

2. If you need encrypted tunneling / port forwarding for web browsing for example (over an untrusted network), you can already set up a very good VPN-like solution using only ssh: 
```
ssh <username>@<server> -D <a local open port number>
```
Leave the terminal open (that's your tunnel), then in Firefox settings, set your proxy to be a "SOCKS v5 proxy", with your local IP address (not the server's!), and the port you set in SSH's "-D" parameter. This will forward all your web traffic to the server over SSH. That is, from the outside world, you'll be browsing the web from your server's IP address.

Hope this helps, let me know if you need further advise!

- Trib'

---

