---
title: "Is it Possible to do ssh tunelling port 80 without root rights ?"
date: 2006-11-23
forum: Server Platforms
---

### Post by burek on 2006-11-23
> The idea: there is a pc behind a nat that wanna ssh a distant pc listening port 22. We would like it secured. Is there a way ?
Using OpenSSH *is* secure, else it wouldn't be called Secure SHell. If you would still want to tunnel ssh this command creates a tunnel from your local port 80 to a remote server running SSH whose IP address is 10.0.1.1: "ssh -L80:127.0.0.1:22 -t -N -2 10.0.1.1". Once authenticated in another window executing "ssh -p 80 localhost 'hostname -i' " should show the remote servers IP address. Note the local port 80 is just an example since ports below 1024 can only be forwarded by root, so if you're not root try for example 8080. If you work with tunnels a lot then it's no fun running and checking them: automate it using AutoSSH. For more interesting tunnel examples and explanation: [http://souptonuts.sourceforge.net/sshtips.htm](http://souptonuts.sourceforge.net/sshtips.htm).

I tried with putty and with ssh linux, and I got asked about root permissions or m$ saied it cannot forwarsd port. Is it normal ? or routeur sthg wrong ?
> Privileged ports can only be forwarded by root.

Hence, Is it Possible to do ssh tunelling port 80 without root rights ?

thank you !

---

### Post by MJN on 2006-11-24
Eh? I'm not sure I understand your question... (could be my fault entirely!)
 
You've quoted the bit saying 'privilege ports can only be forwarded by root', so isn't that the answer to your question? (port 80 is privileged if that's what you're wondering).
 
Mathew

---

### Post by stickboy2642 on 2006-11-26
Any port below port 1024 is considered "privileged" and requires root permissions to bind and manipulate.

---

