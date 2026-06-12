---
title: "SAMBA - Not autostarting anymore"
date: 2011-04-14
forum: Server Platforms
---

### Post by rentarou on 2011-04-14
Hello,

Since yesterday I've been experiencing some problems with Samba, more specificaly smbd not starting automatically anymore. Running "Sudo service smbd start" starts it manually, stop and restart also work after starting it. If I try running it using /etc/init.d/smbd start I get an error along with the usual information about it being an upstart service now. The error being:

```
start: Rejected send message, 1 matched rules; type="method_call",  sender=":1.39" (uid=1000 pid=2262 comm="start)  interface="com.ubuntu.Upstart0_6.Job" member="Start" error  name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0  pid=1 comm="/sbin/init"))
```

Up until yesterday everything was working just perfectly, today was the day the server was suposed to go in use, and this happens. The only thing I can remember that has changed since last reboot yesterday when everything was still working is :
1. We did some updates (ubuntu update manager).
2. Server changed locations (from at my desk to the server rack).

I've been googling for this problem but haven't found much in a ways of a solution.

Some extra info: using Ubuntu 10.10 Maverick Meerkat, Gnome 2.32.0
Shares are authenticated to a Windows Server 2003 domain, using LikeWise.

---

### Post by falko on 2011-04-14
Can you try
```
insserv smbd
```
? This should create the necessary system startup links.

---

### Post by rentarou on 2011-04-14
That didn't seem to work.
The command returned me with  a few pages worth of text, a small snippet of it:

> insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'smbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `smbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `smbd'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dmesg' missing LSB tags and overridesRebooted afterwards and nothing had changed.

I've also checked the SMBD log file, and found this, I'm guessing this is pretty relevant, but have no idea what to do to fix it.

> [2011/04/14 10:10:46.824196,  0] lib/interface.c:519(load_interfaces)
  ERROR: Could not determine network interfaces, you must use a interfaces config line

I've tried adding a line to my samba config:
> interfaces = eth0 10.0.0.48
This seems to solve the problem, smbd is starting up together with the system again.
I'm guessing this problem was caused by a network interface coming up too late, however I would like someone to confirm this.

I'm also getting another error in my SMBD log now:

> [2011/04/14 10:47:53.647917,  0] smbd/server.c:500(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use

The solution of adding the interface line in the smb.conf seems like a workaround, I'd prefer a cleaner fix if anyone has one.

---

