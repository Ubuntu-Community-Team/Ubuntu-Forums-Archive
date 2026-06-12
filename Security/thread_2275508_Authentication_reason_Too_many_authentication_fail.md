---
title: "Authentication reason: Too many authentication failures"
date: 2015-04-26
forum: Security
---

### Post by Finschken on 2015-04-26
Hello!
I have for a while now, received the error "Authentication reason: Too many authentication failures" when I am trying to login into my Ubuntu server via tightVNC.
I do have to restart the server every time I need to enter it, I am afraid that someone is trying to hack my server. 

Is there any way to fix this problem? Thanks!

Btw, I do have googled it and did not find anything useful!

---

### Post by TheFu on 2015-04-26
VNC isn't secure.  I wouldn't open VNC on any internet-facing NIC. If you must have VNC, use either an openVPN or ssh tunnel to connect to the host and tunnel the VNC connection through that.  There are how-tos for this ... [http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html](http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html) is one.

Or you can use NX if you must have a remote desktop. **x2go** is the best implementation - there is a client for most desktop OSes and a server for Linux, plus it can use ssh-keys for authentication, so nobody will hack that provided you don't use passwords and run **fail2ban** (or something similar).  Over the long run, most server admins use plain ssh with keys for all the management of their linux servers (assuming they aren't using ansible or puppet).  X2go instructions: [http://wiki.x2go.org/doku.php/doc:installation:x2goserver](http://wiki.x2go.org/doku.php/doc:installation:x2goserver) - it feels 2-3x faster than VNC or RDP.  The only reason I know not to only use x2go is if you must, must, have an android client and access over the internet. There isn't any NX client for android.

---

### Post by Finschken on 2015-04-27
> **TheFu said:**
> VNC isn't secure.  I wouldn't open VNC on any internet-facing NIC. If you must have VNC, use either an openVPN or ssh tunnel to connect to the host and tunnel the VNC connection through that.  There are how-tos for this ... [http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html](http://www.cyberciti.biz/tips/tunneling-vnc-connections-over-ssh-howto.html) is one.

Or you can use NX if you must have a remote desktop. **x2go** is the best implementation - there is a client for most desktop OSes and a server for Linux, plus it can use ssh-keys for authentication, so nobody will hack that provided you don't use passwords and run **fail2ban** (or something similar).  Over the long run, most server admins use plain ssh with keys for all the management of their linux servers (assuming they aren't using ansible or puppet).  X2go instructions: [http://wiki.x2go.org/doku.php/doc:installation:x2goserver](http://wiki.x2go.org/doku.php/doc:installation:x2goserver) - it feels 2-3x faster than VNC or RDP.  The only reason I know not to only use x2go is if you must, must, have an android client and access over the internet. There isn't any NX client for android.

Thank you for your answer!
I did try the first one and it did say "bind: Address already in use". Otherwise, it's not a local server. I do rent a server in another country.
And I am not that good with ubuntu, just started. So x2go is pretty much like RDP?

---

