---
title: "close all open ports on ubuntu"
date: 2011-08-12
forum: Security
---

### Post by invader.sushil on 2011-08-12
i checked with sysv-rc-conf the service **samba, cups and ssh** and all these are set to **off** for all **levels 12345**. however when i check with **nmap,** the ports are **open** for these services. i tried stopping these services manually with the following command :
 
**sudo service cups stop**
**sudo service smbd stop**
**sudo service ssh stop**
 
now on checking with nmap, the ports for these services are closed. my concern is that if i restart ubuntu then these services again start which i donot want them to.how do i this??

---

### Post by FuturePilot on 2011-08-12
CUPS only listens on the localhost so there's really nothing to worry about with that. As for smbd and ssh, do you need them? If you don't use them, uninstall them.

---

### Post by Dangertux on 2011-08-12
Also something to keep in mind, if you are scanning locally ie: running nmap on the machine you are scanning.  The results will look very different than what an outside scanner would see. This is because of a default iptables' loopback policy.

Also if you are still having the services start on reboot you can try this command it might help.

```

sudo update-rc.d -f servicename remove

```

Hope that helps.

---

### Post by iisjman07 on 2011-08-12
Try using > sudo chkconfig ssh disable

---

### Post by doas777 on 2011-08-12
@op: a tip on open ports:

there are many ports open on a system that are only accessible to that host, and are used by processes that want to share data with eachother (called InterProcess Communication).
you can determine which ports are locally 'filtered'  by running
```
netstat -ntlup
```
and looking at the ports open on local address '127.0.0.1'. these are only accessible internally. 
ports listening on the lan IP are usually services that have been configured for access by the local lan only, but be sure to evaluate each independently, as it is up to the service as to how to determine its local listening address.
ports listening on 0.0.0.0 are accessible from anywhere that can reach them, so those are your highest priority to profile.

---

### Post by invader.sushil on 2011-08-13
i donot want to uninsatll the services samba and ssh, as i might require those. my concern is that i want to start them when i need,however on restarting ubuntu, these services start automatically. sysv-rc-conf doesnot help.

---

### Post by doas777 on 2011-08-13
'sudo service smbd stop' should work fine for you, if you want to hook in and stop it after loading.

---

### Post by invader.sushil on 2011-08-13
it doesnot solve the purpose. i donto want these services to start when i restart ubuntu.

---

### Post by Soul-Sing on 2011-08-14
disable cups(d), edit the /etc/init/cups.conf 
comment out these three lines

start on (filesystem
          and (started dbus or runlevel [2345])
          and stopped udevtrigger)

---

### Post by The Cog on 2011-08-15
> **leoquant said:**
> disable cups(d), edit the /etc/init/cups.conf 
comment out these three lines

start on (filesystem
          and (started dbus or runlevel [2345])
          and stopped udevtrigger)

+1
That's the way to do it.

---

