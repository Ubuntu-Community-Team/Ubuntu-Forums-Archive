---
title: "Can't Get VPN To Work"
date: 2018-04-18
forum: Server Platforms
---

### Post by open4epl on 2018-04-18
I'm back on 16.4 but I can't seem to get the VPN to work. I go to> [https://www.vpnbook.com/freevpn](https://www.vpnbook.com/freevpn) input the VPN Gateway & PW and it won't connect. Please help.

---

### Post by wildmanne39 on 2018-04-18
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by delfiler on 2018-04-19
i am gone sound very basic and beginner here but let me ask a few questions first:
has anything changed between the 16.4 and the version you were on before?
do you have any scripts running on the previous version?
if there is a script did you adjust it? (if there are no scripts skip this question)
are the interfaces still called the same?
did you try to update or upgrade before? (as in typing the command 'apt-get update' or 'apt-get upgrade'?)
well these are my questions and i hope you can answer them

---

### Post by open4epl on 2018-04-19
Sorry but I found my solution here> [https://www.youtube.com/watch?v=tcx2-EkYYDg&list=PLR_EhJ0E23PY3F_LsGONEIDSe_b9iprA3&t=0s&index=2](https://www.youtube.com/watch?v=tcx2-EkYYDg&list=PLR_EhJ0E23PY3F_LsGONEIDSe_b9iprA3&t=0s&index=2) 
And I got the VPN to work w/ OpenVPN.

---

### Post by open4epl on 2018-04-19
Btw, is there a limit to how many VPN's that can be stored on Ubuntu?

---

### Post by TheFu on 2018-04-19
> **open4epl said:**
> Btw, is there a limit to how many VPN's that can be stored on Ubuntu?

Yes, but I doubt you'd ever hit any.  There are limits for different views of "vpn."  There is the file system limit. There is the RAM limit, there is the CPU limit, there are openvpn limits and there is the GUI tool display limit.  

I have about 60 ovpn files that all work fine. Don't see any reason that 50,000 can't be there and used one at a time.  Running 2 VPNs concurrently, is non-trivial.

As for running multiple different VPN services for others, I'd done a few concurrently to support listening on different ports with different settings.

---

