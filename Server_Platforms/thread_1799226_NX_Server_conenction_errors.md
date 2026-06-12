---
title: "NX Server conenction errors"
date: 2011-07-07
forum: Server Platforms
---

### Post by afd on 2011-07-07
Hi guys and girls,

I'm trying to set up an instance of NX Server remotely (via SSH) on a client's server just as I have with one that is working in my office.

Both have been setup the same way but I have done one in front of the machine and the other remotely.

The one in my office has no connection issues and after forwarding a port on the router we can access this instance from outside of the LAN.

The other server we cannot connect to via NX Client although we have the ssh working ok.

Both servers are running ubuntu server 10.04 but have ubuntu-desktop installed.

I am using NX Server 3.4 (not FreeNX) as stated here: [https://help.ubuntu.com/community/NomachineNX]("https://help.ubuntu.com/community/NomachineNX")

I have checked the logs on the server which is not working and here is the info for the session that did not connect: [http://pastebin.com/ZiWkf4HT]("http://pastebin.com/ZiWkf4HT")

I've a hunch it may be to do with ownership or permissions but I'm not entirely sure.

Any help greatly appreciated.

Thanks.

---

### Post by afd on 2011-07-07
Actually I found the solution in another thread:

```
rm .Xauthority*
```

---

