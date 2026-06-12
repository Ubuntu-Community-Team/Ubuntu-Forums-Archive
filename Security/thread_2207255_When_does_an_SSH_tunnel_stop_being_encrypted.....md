---
title: "When does an SSH tunnel stop being encrypted...."
date: 2014-02-22
forum: Security
---

### Post by SchnappiJedi on 2014-02-22
Say you are at work and you setup a dynamic SSH tunnel using putty to your SSH server at home and visit google.com. Does the tunnel stop being encrypted when it leaves your home network from the SSH server? Or does it stay encrypted all the way to google.com?

---

### Post by CharlesA on 2014-02-22
It is encrypted to your end point (the ssh server).

---

### Post by SchnappiJedi on 2014-03-07
What about dynamic tunneling?

How does creating a local tunnel to google.com and connecting to localhost,port differ from connecting to google through a dynamic tunnel in terms of what is encrypted?

From my understanding a dynamic tunnel is encrypted to the SSH server (and back to the client connection), while the SSH server sends clear text packets to google.com. However a localhost tunnel to google.com infers that that the connection all the way to google.com and back is encrypted.

---

### Post by CharlesA on 2014-03-07
What do you mean? The same thing would apply if you are connected to a (remote) ssh server via a local tunnel and connect to a site with localhost. A) You'll get SSL error B) The connection is only encrypted to the SSH server.

---

### Post by SchnappiJedi on 2014-03-07
With a dynamic tunnel data travels to google.com from the SSH server unencrypted (only the tunnel to/from the SSH server from your client is encrypted). 

With a local tunnel you are encrypting the data all the way to google.com and back to the SSH server.

Is this correct?

The SSL error isn't an issue as one can just accept the server mismatch. But SSL isn't really necessary over a local tunnel...although I agree google.com would force it.

---

### Post by CharlesA on 2014-03-07
In either case, the encryption stops at the SSH server.

See here:
[http://chamibuddhika.wordpress.com/2012/03/21/ssh-tunnelling-explained/](http://chamibuddhika.wordpress.com/2012/03/21/ssh-tunnelling-explained/)

---

### Post by SchnappiJedi on 2014-03-08
I had seen this article again but reading it again a second time was helpful.

If you tunnel a VNC or RDP session over the internet the session is 100% encrypted only if the SSH server is running on the same computer you RDP or VNC' into. Correct?

---

### Post by CharlesA on 2014-03-08
> **schnappi2 said:**
> I had seen this article again but reading it again a second time was helpful.

If you tunnel a VNC or RDP session over the internet the session is 100% encrypted only if the SSH server is running on the same computer you RDP or VNC' into. Correct?

Yes, otherwise it hits the SSH "endpoint" and goes out to whatever machine you are trying to connect to unencrypted.

---

### Post by SeijiSensei on 2014-03-09
Unless you are sending HTTPS requests over the tunnel, of course.  But in that case, there really is no need for the tunnel.

---

