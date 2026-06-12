---
title: "Bind9 not working at startup"
date: 2008-04-27
forum: Server Platforms
---

### Post by Dr Small on 2008-04-27
Bind9 is actually starting at bootup, as it is listed as a process, yet it will not work over the network unless I stop bind9 and then start it again.

I thought maybe it had something to do with being ahead of my firewall rules at startup, so I placed it behind the firewall rules, and it still does not work.

When I did a portscan on the server, directly after rebooting, I get:
```
drsmall@darkghost:~$ nmap 192.168.0.70

Starting Nmap 4.20 ( http://insecure.org ) at 2008-04-27 12:15 EDT
Interesting ports on mycroft (192.168.0.70):
Not shown: 1687 closed ports
PORT      STATE SERVICE
21/tcp    open  ftp
22/tcp    open  ssh
25/tcp    open  smtp
79/tcp    open  finger
80/tcp    open  http
110/tcp   open  pop3
443/tcp   open  https
3306/tcp  open  mysql
5432/tcp  open  postgres
10000/tcp open  snet-sensor-mgmt

Nmap finished: 1 IP address (1 host up) scanned in 1.723 seconds

```

Port 53, domain is not listed there. But if I SSH into the server, restart bind9 and then portscan the system, it shows port 53 as open, and then my DNS works.

Is there any possible explanation for this?
Here is the startup, as in /etc/rc2.d/
```
S20courier-pop    S20postfix    S89cron
S10acpid                     S20denyhosts      S20proftpd    S99rc.local
S10sysklogd                  S20dyndns.update  S20rsync      S99rmnologin
S10xserver-xorg-input-wacom  S20firewall       S20saslauthd  S99stop-bootchart
S11klogd                     S20fwlogwatch     S20sqwebmail  S99uptimed
S12dbus                      S20inetd          S20ssh        S99usermin
S19postgresql-8.2            S20mailman        S21bind9      S99webmin
S19spamassassin              S20makedev        S21lampp
S20bandwidthd                S20ntop           S21quotarpc
S20courier-authdaemon        S20nvidia-kernel  S89atd

```

Dr Small

---

### Post by reedox.com on 2008-04-27
Run:

```

grep named /var/log/syslog

```

Any errors?

---

### Post by Dr Small on 2008-04-27
I don't see anything critical:
```
Apr 27 22:10:24 mycroft named[6860]: starting BIND 9.3.4 -u bind
Apr 27 22:10:24 mycroft named[6860]: found 1 CPU, using 1 worker thread
Apr 27 22:10:24 mycroft named[6860]: loading configuration from '/etc/bind/named.conf'
Apr 27 22:10:24 mycroft named[6860]: listening on IPv6 interfaces, port 53
Apr 27 22:10:24 mycroft named[6860]: listening on IPv4 interface lo, 127.0.0.1#53
Apr 27 22:10:24 mycroft named[6860]: command channel listening on 127.0.0.1#953
Apr 27 22:10:24 mycroft named[6860]: command channel listening on ::1#953
Apr 27 22:10:24 mycroft named[6860]: zone 0.in-addr.arpa/IN: loaded serial 1
Apr 27 22:10:24 mycroft named[6860]: zone 127.in-addr.arpa/IN: loaded serial 1
Apr 27 22:10:24 mycroft named[6860]: zone 255.in-addr.arpa/IN: loaded serial 1
Apr 27 22:10:24 mycroft named[6860]: zone mytheme.com/IN: loaded serial 1209151166
Apr 27 22:10:24 mycroft named[6860]: zone selftech.com/IN: loaded serial 1209151277
Apr 27 22:10:24 mycroft named[6860]: zone localhost/IN: loaded serial 1
Apr 27 22:10:24 mycroft named[6860]: zone darkghost.net/IN: loading master file /etc/bind/darkghost.net.hosts: file not found
Apr 27 22:10:24 mycroft named[6860]: zone laptop.net/IN: loaded serial 1209151516
Apr 27 22:10:24 mycroft named[6860]: zone mycroft.org/IN: loaded serial 1209150446
Apr 27 22:10:24 mycroft named[6860]: running

```

That was directly after a restart, and DNS does not work.
The strange thing is, everything works honky-dory if I ssh into the server and restart bind9.

Any other information you can supply on this would be helpful.
Thanks,
Dr Small

---

### Post by PeterK2003 on 2008-05-21
I am having the exact same issue!

Any solutions?

---

### Post by Dr Small on 2008-05-21
As of 3 weeks later, I am still having the same issue, I think. :(
(I haven't rebooted for awhile)

---

### Post by christhegoth on 2008-06-25
Yup, same issue.  Daft thing is this all worked fine under Gutsy.

I've disabled my firewall in case it was that but still have no joy.  Port 53 closed.

I did have apparmor getting in the way as well.  Disabled the profile and it's happy now, but still.  Thankfully this machine is just me playing at home.

---

### Post by confy on 2008-12-13
[https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/226495](https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/226495)

I hope that helps....

it seems you need to rename 
mv S21bind9 S91bind9

I'm having simular problem, i'll check it tomorrow....

---

