---
title: "[Virtual Box with 9.04 Host and 9.04 Client] Client Key Authentication Issue"
date: 2009-06-04
forum: Server Platforms
---

### Post by dave888 on 2009-06-04
Ive installed ubuntu server and virtual box on a host system.  There is a ubuntu server client currently running nothing more then ssh on this host.

VirtualBox NAT Has been configured to forward port X on the host to the clients port 22.

I can connect to both the host and the client though SSH using passwords from a remote box.

The host and the client have been configured to use SSH Key Authentication.  

The key authentication works on the host without issue.  

The key authentication works on the client, ONLY when I have a current open session to it.  To clarify, if I connect to the client using key authentication with no other current sessions, I get prompted for a password. If I connect to the client using key authentication WITH another open session, I successfully connect without any password prompt.

I have tried connecting from a remote PC and from the host to the client itself, and both suffer the above issue.

Im inclined to think its an issue with VirtualBox NAT.  Has anyone has a similar issue, or recomend any potential solutions?

Cheers,
Dave

---

### Post by dave888 on 2009-06-04
An additional piece of information.

If I open an ssh connection to the localhost (from the client, to the client) inside a remote session, using screen. I can then disconnect the remote session (leaving the localhost to localhost connection running inside screen), I can then successfully connect using the key remotely.

Now im not convinced its a NAT issue...

---

