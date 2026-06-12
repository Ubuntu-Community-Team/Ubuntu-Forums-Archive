---
title: "mysterious problem, packets disappear"
date: 2009-06-18
forum: Security
---

### Post by firsttimeuser on 2009-06-18
I am running an application which "captures" the incoming netflow on a defined port on my 64bit 8.10 server.

Everything is set up correctly, but no matter what I try, the application is not able to see the data at all.

I double checked iptables, and there is no rule defined. 

I ran tcpdump on that specific port and saw the packet coming. 

I hooked up my laptop, which also runs ubuntu, using exactly same application and same syntax and i get the flow data without any problem. 

Someone suggested SELinux might be running, but a quick grep in dmesg result shows SELinux is disabled.

What else could be wrong and what else should I check? I am pulling my hairs off now...

thanks!

---

### Post by munky99999 on 2009-06-18
> defined port on my 64bit 8.10 server.
> I hooked up my laptop, which also runs ubuntu, using exactly same application and same syntax and i get the flow data without any problem.
laptop is running desktop and not server?

Im quite inexperienced with server but afaik server is setup such that basically only dns-dhcp is the only open listening port.

You might have the firewall on the server box shutting that specific port down.

---

### Post by iponeverything on 2009-06-18
use netcat to try to capture the flow and sent to file just to verify that the issue is not with your application.

---

### Post by wirelessmonkey on 2009-06-18
If tcpdump is seeing it, then there is a problem with your application on that machine.

---

