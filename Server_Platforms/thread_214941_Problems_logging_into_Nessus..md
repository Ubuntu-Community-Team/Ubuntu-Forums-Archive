---
title: "Problems logging into Nessus."
date: 2006-07-13
forum: Server Platforms
---

### Post by A2A on 2006-07-13
Hi all.  I have nessus installed but cant get it to work.  When I open it (Applications -> Internet -> Nessus) I get a "Nessus Setup" window.  After entering my password and clicking "Login"  I get a error popup saying "Could not open a connection to localhost".
I also tried using my IP in the "Nessusd Host" field to no avail.  The default port is set to 1241.
Any help would be much appreciated.

Thanks

---

### Post by rbalfour on 2006-07-13
You need to start the server part

$sudo /etc/init.d/nessusd start

the GUI is just a client to the server....

gl

---

### Post by A2A on 2006-07-13
Thanks rbalfour.  
I realized I had only the GUI part installed and the daemon was missing.  I installed it and configured it (sudo nessus-adduser, etc).  Got it running and performed a scan.  Worked like a charm.
Perhaps you (or someone else) can help me with the following output that listed under general/tcp:
> 
admin.cgi was detected on this server
Shoutcast server installs a version that is vulnerable to a buffer overflow.
** Note that Nessus did not try to exploit the flaw, so this might be a false alert.
Solution: Upgrade Shoutcast to the latest version.
Risk Factor: High
CVE : CVE-2002-0199
BID : 3934
 
So how do I update and or remove Shoutcast?  As far as I recall, I never installed it to begin with :-(
Much appreciated :p

---

