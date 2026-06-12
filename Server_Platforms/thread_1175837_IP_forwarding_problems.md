---
title: "IP forwarding problems"
date: 2009-06-01
forum: Server Platforms
---

### Post by IbuildDW on 2009-06-01
I have what I think is an issue with IP forwarding.

Machine 1
eth0 192.168.1.1 gw 192.168.1.254
eth1 192.168.2.1

Machine 2
eth0   192.168.1.2
eth0:0 192.168.2.2 gw 192.168.2.1

I need to be able to get to the Internet (Machine 1's gw) from Machine 2.  

I have on Machine 1:
```

~# cat /proc/sys/net/ipv4/ip_forward
1

```

I can ping other machines on the 192.168.1.0 network and the 192.168.2.0 network from Machine 2, but can't get to any other addresses from Machine 2.

Please let me know if you have ANY ideas, I've been trying to get this working for several days and haven't made any progress.  From all I've read, I should only need ip forwarding enabled.  I have that, but it doesn't appear to be working.

TIA

---

### Post by hvc123 on 2009-06-01
i dont know how but u need to set up nat on the 1st machine..

try [http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

should get u going

---

### Post by IbuildDW on 2009-06-01
> **hvc123 said:**
> i dont know how but u need to set up nat on the 1st machine..


 THANKS!  That helped.  Now I can see other networks from Machine 2!!

Last issue to solve.

  Any idea why I can't ssh into the 192.168.1.2 address from another network?

Office is on a 192.168.3.0 network with a VPN to the 192.168.1.0 network.
I can ping the machine at 192.168.1.2 but if I try to SSH or bring up a Web page it just kinda hangs.

If I'm physically on a machine that is on the 192.168.1.0 network I have no trouble.

---

