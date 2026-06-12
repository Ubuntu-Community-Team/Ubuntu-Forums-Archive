---
title: "vmware server configuration"
date: 2007-04-29
forum: Server Platforms
---

### Post by cacharreo on 2007-04-29
I get VMWare server working on ubuntu 7.04, but I need to configure it using ***sudo /usr/bin/vmware-config.pl*** each time that I start up my computer (It forgets the configuration).
Some idea abot this one?
Thanks...

---

### Post by Brazen on 2007-04-29
Are you sure it's not just happening after a kernel upgrade?

---

### Post by veloce on 2007-05-01
> **cacharreo said:**
> I get VMWare server working on ubuntu 7.04, but I need to configure it using ***sudo /usr/bin/vmware-config.pl*** each time that I start up my computer (It forgets the configuration).
Some idea abot this one?
Thanks...

What happens if you don't? (what error do you get?)

---

### Post by cacharreo on 2007-05-01
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.     :confused:

---

### Post by veloce on 2007-05-01
I've not had this issue but I have seen it discussed in this forum.  Can't think what the title was but do some digging.  I seem to remember that the solution involved running "sudo vmware" but care was needed or you would always need to run vmware as root.

---

### Post by gaiterodezona on 2007-11-11
I tryed this [workaround]("http%3A%2F%2Fblog.solutionperspectivemedia.co.uk%2Farchives%2F6-VMware-need-to-re-run-vmware-config.pl-every-reboot-on-linux.html&title=VMware%20need%20to%20re-run%20vmware-config.pl%20every%20reboot%20on%20linux")
Until now it's working fine...
good luck

---

### Post by doanut on 2007-11-11
Just put that command into you startup. rc.local.

See if that helps.

---

