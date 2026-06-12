---
title: "call to socket() errors"
date: 2009-03-31
forum: Ubuntu Dev Link Forum
---

### Post by gonzo1948 on 2009-03-31
Hi,

I have 2 applications linked with the same libpcap library. The first 
one is just a sanity app that makes a few calls to libpcap, including 
pcap_lookupdevs().  The second app is a bit more extensive but also 
calls pcap_lookupdevs() upon initialization.

If I run the 1st app with user myself, I get the typical message "no 
suitable device found" from pcap_lookupdevs().  If I run the 1st app as 
root, then it runs just fine, as expected.

When I run the 2nd app, pcap_lookupdevs() always fails with "no suitable 
device found" regardless of whether I run the app as myself or as root.

I have traced the failure to the system call socket() in live_open_new() 
(in the pcap-linux.c file). I print out both the user ID and the 
effective user ID before and after the call to socket(). 

When I run the 1st app, the debugging printfs in live_open_new() print 
out as expected. That is, when the 1st app is run as myself, both the 
user ID and the effective user ID are me, and the call to socket() fails 
with an "Operation not permitted" error.

When I run the 2nd app as root, the debugging printfs in live_open_new() 
print out that the user ID is root (0) and the effective user ID is also 
root (0), but the call to socket() still fails with the "Operation not 
permitted" error.

Again, the same libpcap library is linked into both apps. I have tried 
the most recent version of libpcap as well as several older 
versions--all with the same results.  I can run  both apps from the same 
root shell, yet the socket() call always fails in the 2nd app.  I do not 
think the problem is in this 2nd app, because, it runs fine on other 
systems. It is just on my system that the socket() call fails in the 2nd 
app.

I am running Ubuntu 8.04 and all my other network related apps that use 
libpcap work just fine if I run them with sudo or as root. But in this 
app, the pcap_lookupdevs() always fails EVEN WHEN RUN AS ROOT.

Any ideas on what could be causing socket() to fail (with Operation not 
permitted) in the pcap routine live_open_new() even when running as root?

Thanks,

-Andres

---

