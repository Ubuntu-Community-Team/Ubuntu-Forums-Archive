---
title: "[SOLVED] PPTPD fails to start"
date: 2008-10-24
forum: Server Platforms
---

### Post by ricmitch on 2008-10-24
Hi everyone.

I am running an 8.04, 2.6.24-19-server with Webmin and a few other services. On the same network I am running an identical distro as a file server. Both PCs are x86.

I have been trying to get pptpd to work on the first computer having successfully configured it on the latter as a temporary measure.

Having followed identical steps in installing and configuring PPTPD using the console (and checking the variables aside from IPs etc. match through Webmin), I find that the service completely fails to start on one of the PCs, but not the other.

Even with debugging enabled, starting the server daemon using "/etc/init.d/pptpd start" or "pptpd" doesn't launch the process, doesn't create a pid file (except perhaps momentarily) and doesn't leave any messages in /var/log/messages or /var/log/debug.

Anyone got any ideas on how I can find out why the process isn't launching?

Thanks in advance.

---

### Post by ricmitch on 2008-10-24
After checking my configuration files, I noticed a typo in the pptpd.conf file of the problematic server. I had accidentally set the remoteip variable to extend beyond 255.

Given that this fails silently, despite verbosity being cranked up and debugging messages being switched on, should it be reported as a bug?

---

### Post by RayVad on 2008-12-24
Same problem fixed here. Also due to an error somewhere in the config file.

---

