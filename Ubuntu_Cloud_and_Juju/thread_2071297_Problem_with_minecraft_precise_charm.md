---
title: "Problem with minecraft precise charm"
date: 2012-10-15
forum: Ubuntu Cloud and Juju
---

### Post by Fajkowsky on 2012-10-15
Hey I have problem with deployment minecraft server on ubuntu maas/juju. When I juju ssh to node responsible to minecraft server I receive this:

```
Last login: Thu Oct 11 07:15:31 2012 from ubuntuserver.local
ubuntu@node-00127968a7be:~$ service minecraft status
minecraft stop/waiting
ubuntu@node-00127968a7be:~$ service minecraft update
minecraft: unrecognized service
ubuntu@node-00127968a7be:~$ service minecraft restart
stop: Unknown instance:
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.14" (uid=1000 pid=1501 comm="start minecraft ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
ubuntu@node-00127968a7be:~$
```

---

