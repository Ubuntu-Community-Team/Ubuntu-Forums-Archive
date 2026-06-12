---
title: "SSH &amp; VNC connections being dropped, then rejected"
date: 2008-08-13
forum: Server Platforms
---

### Post by Emjx on 2008-08-13
We have an issue with a Ubuntu 7.10 server where SSH sessions are dropped with a message *connection reset by peer* and then any subsquent sessions are rejected with a message *connection refused*. Usually after a few minutes the connection can be re-established but again, only for a few minutes.

I have tried the following to fix the issue:
[LIST]
[*]Checked hosts allow & deny files - allow allows all, deny is empty
[*]Ran sudo apt-get update to ensure latest patches
[*]Tried installation of 8.10 LTS instead
[*]Replaced the network switch in between workstation & server
[*]Replaced network cables with tested, brand new cables
[*]Re-installed SSH (originally installed via apt-get install ssh, reinstalled that, then uninstalled that and installed openssh-server
[*]No network or other errors in system log
[*]Tried repeating ping to & from server and even during a SSH connection drop, no other network service was lost (HTTP still available, ping still fine (no increased TTL, etc))
[/LIST]

After scouring many forums and not realling finding much, we came upon the conclusion that the server had a fault NIC, so, phoned HP and the next-day had a brand new system board fitted (onboard NIC's). Unfortunately this did not solve the issue.

We have three identical servers (HP DL360 G5, 2x Quad Core Xeon, 4GB RAM) - two servers (one running 7.10 and the other running 8.04 LTS (upgraded from 7.10)) are absolutely fine, the third as described above, is not.

If anyone can give some ideas, then I would be absolutely delighted to hear them!!! Many thanks!

---

### Post by windependence on 2008-08-13
Looks like the ssh server is getting hit by tons of requests from somewhere and after so many attempts it will refuse connections for a set period of time. This is default behavior and is a good thing. What is in your /var/log/auth.log?

-Tim

---

### Post by Emjx on 2008-08-13
I had a look in that file yesterday and there was nothing that appeared unusual - no lots of attempts at access. I haven't checked today - but will check again in the morning (am away from the server at the moment).

I am not expecting to see much in that log as the server is on an internal private LAN, in a secured lab with no NAT'd external IP address to it so if there was something hammering the server, it would have to be internal...!

---

### Post by windependence on 2008-08-13
Well it was worth a shot. :) I have seen this many times, but you pretty well rules that one out. ;)

-Tim

---

