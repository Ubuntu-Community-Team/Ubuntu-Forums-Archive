---
title: "ping command: incorrect output bug after routing redirect"
date: 2015-10-31
forum: Virtualisation
---

### Post by Skaperen on 2015-10-31
while testing VPNs (using OpenVPN) between AWS regions. i had the ping command running first between 2 instances in different regions. the EC2 router (in default VPC at 172.31.0.1) sent a routing redirect when it first got its route table entries added.  the ping command got this packet.  when the VPN router instance on each end got its own route table updated to make the new tunnel useable, the ping requests and replies finally came through.  the observed bug was that ping was reporting the router IP address as the reply source.  this was confirmed by killing ping and restarting it after which the address was correct.  so, it appears something inside ping was updated wrong when the redirect was received.  this is not critical because of a simple workaround to (re)start ping afterwards and this being a rare event for most use(r)s.

---

### Post by sudodus on 2015-10-31
Thanks for sharing this information :-)

But the developers seldom visit the Ubuntu Forums. If you want the bug to be squashed, you should write a ***bug report at Launchpad*** and ask someone who understands it to confirm the bug by marking 'affects me too' at your bug report.

---

