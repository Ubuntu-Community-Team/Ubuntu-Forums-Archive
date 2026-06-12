---
title: "Securing vmware server"
date: 2007-01-13
forum: Server Platforms
---

### Post by tweedledee on 2007-01-13
VMware server, via xinetd, opens port 902 for remote connections, which means that port is wide open to the whole world.  Since I don't actually use remote connections, this function is useless to me and a security problem.  Short of installing a local firewall, is there some way (without disrupting local connections of vmware) to prevent this?  Do I really need xinetd to be running if I'm not using remote connections?  If I do, can I just convince it to listen locally rather than to the whole world?

Any help would be appreciated.  I realize I could just use firestarter to seal my computer, but it's a pain for my laptop when I use multiple interfaces, and seems like overkill to close a single port.

---

### Post by tweedledee on 2007-01-20
After wasting a great deal of time with different (typically about 80% accurate) instructions on how to work with IP tables, and working through the fact that IP tables itself is very inconsistent, I arrived at this solution:

```
sudo iptables -A INPUT -p tcp --dport 902 -j DROP
```

This just blocks inbound packets on port 902, so at least I'm not wide open on the port any more and I don't have to mess around with firewall software I don't need.  I'd still prefer to actually prevent xinetd from listening on that port in the first place, so if anyone has any suggestions.....

---

### Post by gombadi on 2007-01-20
To stop xinetd from listening on port 902

edit -
/etc/xinetd.d/vmware-authd

change -
disable = no to disable = yes

Regards,
Lyndsay

---

### Post by gombadi on 2007-01-20
and of course restart with

/etc/init.d/xinetd restart

---

### Post by yabbadabbadont on 2007-01-21
I think that will prevent him from running the vmware-server console, even on the local machine.  Perhaps a better solution would be to add (or change) "only_from = localhost" in /etc/xinetd.conf and then restarting xinetd.  (or just reboot)

---

### Post by Moldz on 2007-01-21
Another note:  your IPTABLES command is only valid until you reboot your machine.  You will notice that after a reboot the port will be open again.  Usually the command is stored in a script somewhere that is started automatically in case of a reboot.

---

### Post by gombadi on 2007-01-21
The vmware-server console, even though it listens on port 902, does not actually use it if you connect to local host. The iptables rule would also have stopped any connections from localhost.

---

### Post by tweedledee on 2007-01-21
All - thanks for the feedback.

gombadi - your solution works perfectly, thank you.

yabbadabbadont - for whatever reason, your solution had no effect.  xinetd was still listening on 0.0.0.0:*.

Moldz - thanks for pointing that out, I managed to overlook that (or it wasn't directly mentioned) in the guides I was trying to follow for iptables.  Even though I no longer need it for this purpose, I am trying to use iptables to restrict access to my samba ports on the same machine, so I will set up a script to make sure those restrictions stay put.

---

### Post by ukjimbow on 2008-07-15
Worked great! cheers!

---

