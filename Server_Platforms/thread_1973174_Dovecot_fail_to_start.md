---
title: "Dovecot fail to start"
date: 2012-05-04
forum: Server Platforms
---

### Post by newcruse on 2012-05-04
My dovecot ran immediately after config and ishut down my pc. when i power up to continue it has been given this error message:

/etc/init.d/dovecot start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dovecot start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start dovecot
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.79" (uid=1000 pid=3325 comm="start dovecot ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")

Can someone help out.

---

### Post by cmont899 on 2012-05-04
What are the outputs of the following command:

```
service dovecot status
```


If dovecot is stopped does the following command work to start?

```
service dovecot start
```


Still having trouble? Try:

```
update-rc.d dovecot defaults
service dovecot start
```

---

