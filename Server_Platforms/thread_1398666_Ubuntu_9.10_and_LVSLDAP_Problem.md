---
title: "Ubuntu 9.10 and LVS/LDAP Problem"
date: 2010-02-04
forum: Server Platforms
---

### Post by dankwaldmb on 2010-02-04
Hello Ubuntu Forum,

I'm working on a Ubuntu 9.10 AMD64 server project with LVS and am seeing a serious problem.  

I have an LVS server, with all the ip_vs modules plugged that load balances two reverse proxy servers that are load balancing applications.  We also have two LDAP servers that are load balanced through LVS so the applications authenticate through LVS.  This setup was working on 8.04 but we migrated to 9.10 because of hardware problems and now LVS no longer works for LDAP.

The problem we're seeing is that an application that authenticates against LDAP, it will authenticate correctly through LVS once, but once you log out, it won't authenticate anymore.  If I point the application directly to the LDAP though, I don't see this problem at all, so I don't think it's an LDAP or an application problem.

I've watched the packets when requests are made using tshark and the only thing strange I see are TCP Out Of Order's related to the LDAP requests and unbind.  I don't know if this is a sign of the problem, or normal though.  I see these TCP OOO's as well when watching requests to the Reverse Proxy machines that LVS also load balances, but LVS seems to pass those requests correctly, or at least the TCP OOO's don't effect it the same way... if they're related to this problem at all.

I'm working with kernel 2.6.31-14-server but have also tried it with 2.6.31-17-server and see the same problem unfortunately.  All of my configurations are the same as I had on 8.04, so I don't think it's a configuration problem either... at least not an obvious one.  LDAP is on the standard port, and isn't using SSL, all routing is done with Direct Routing and the SED scheduler.

Like I said, I didn't see this problem at all on 8.04, but returning to 8.04 comes with other issues and so isn't an option right now.  The only difference between 8.04 and 9.10 is that on 8.04 I compiled the ip_vs options into the kernel, but I don't think that plugging the modules would cause this problem.  

Please provide any advice you can asap... time is of the essence.

Thanks everyone for your time and effort in advance,

Dave

---

