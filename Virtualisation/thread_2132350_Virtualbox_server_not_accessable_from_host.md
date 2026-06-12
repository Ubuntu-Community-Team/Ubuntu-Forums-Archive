---
title: "Virtualbox server not accessable from host"
date: 2013-04-04
forum: Virtualisation
---

### Post by umfunix on 2013-04-04
I've installed Ubuntu lamp server on a Virtualbox.  The host is Ubuntu 12.04.  The virtualbox server has access to internet and can ping router and host IP while getting a DHCP IP, although subnet mask is weird.
host:
10.0.0.21 255.255.0.0 gateway 10.0.0.2

virtualbox server from dhcp:
10.0.2.15 255.255.255.0 10.0.0.2

As I said, although the subnet mask is not the same, access and pinging is fine.  Network settings are set on NAT.

BUT, when I try to access the lamp server from the host ([http://10.0.2.15](http://10.0.2.15)), I do not get access (it works from within the virtualbox, so setup and config is working).

I tried to change virtualbox server's IP to static (10.0.0.1 255.255.0.0 gateway 10.0.0.2) with NO access to and from nowhere.  No router, no host, or the other way round.

Can someone tell me what I should do to get the virtualbox server (10.0.2.15) web accessable from host (10.0.0.21)?  I need to configure a web app on the virtualbox server from the host.

---

### Post by lmarmisa on 2013-04-05
I recommend to switch network settings to Bridged Adapter.

---

### Post by Hexxus on 2013-04-05
I agree with lmarmisa - I was going to say your NAT might be to blame with this.

---

### Post by umfunix on 2013-04-08
Thanks, but still no ping rely.  Can ping the virtual box server's own IP but not the host.:(

---

### Post by SeijiSensei on 2013-04-08
If you run ifconfig on the guest, is its IP address in the same subnet as the host, which it should be if you are using bridging.  If the guest still has a 10.x IP address, chances are good it is still running in NAT mode.

You did shut down the guest before changing modes, right?  You cannot change from NAT to bridged on a running guest VM.

---

### Post by umfunix on 2013-04-13
thanks, I did not shutdwon and restart.

---

