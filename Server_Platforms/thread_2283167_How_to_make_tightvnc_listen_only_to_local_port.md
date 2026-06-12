---
title: "How to make tightvnc listen only to local port"
date: 2015-06-19
forum: Server Platforms
---

### Post by ndnd on 2015-06-19
Hello,
I have Ubuntu 12.XX Server on which I installed the tightvnc package. I have been able to connect fine from my laptop into the server through TightVNC (SSH Tunneling) as well as without SSH.  

As an added safety I wish to disallow any user to connect to the server without SSH tunnel. How can I stop the tightvnc from listening to the ports 5901-5910 and only listen to the local port 127.0.0.1. This way users can only access tightvnc through the tunnel. 

I am new to tightvnc so details would be helpful (if there is a specific file I need to modify the location of the file and the specific syntax that needs to be modified). 

Thanks in advance for your help!

---

### Post by TheFu on 2015-06-19
Use **iptables** to block non-local connections to those ports.
Use the --localhost option on the vncserver startup. [https://askubuntu.com/questions/476583/vnc-server-security](https://askubuntu.com/questions/476583/vnc-server-security)

Or you could check out **x2go** - which feels about 2x-3x faster because it uses NX. NX includes ssh. There is no option NOT to use ssh. Everyone who tries x2go is amazed, but it isn't for every situation.

---

