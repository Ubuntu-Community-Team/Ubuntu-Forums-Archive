---
title: "mdadm email notification"
date: 2009-02-17
forum: Server Platforms
---

### Post by rappa on 2009-02-17
I have setup a raid on Ubuntu Server 8.0.4 and now I want to make sure that I will get notified in the event of a raid failure.  I configured Exim to forward mail to my gmail account and verified mdadm can email with the following test:

mdadm --monitor --scan --test --mail [email]myemail@gmail.com[/email]

I added my email address as MAILADDR in mdadm.conf but when the server boots I don't see my email in the 'ps -ef | grep mdadm':

/sbin/mdadm --monitor --pid-file /var/run/mdadm/monitor.pid --daemonise --scan --syslog

Does this mean that it doesn't read mdadm.conf, or maybe it just doesn't show the mail arg?  Just to be safe, I added the mail arg to /etc/init.d/mdadm   I'm not sure this is correct but at least now if shows in the process:

/sbin/mdadm --monitor --pid-file /var/run/mdadm/monitor.pid --daemonise  **--mail=myemail@gmail.com**  --scan --syslog

Any thoughts?  

Thanks

---

### Post by shizzy-t on 2009-02-17
I never noticed that until I stumbled across your post.  Oddly enough this seems to only affect 8.10 servers, the MAILADDR setting was moved from /etc/default/mdadm to /etc/mdadm/mdadm.conf.  Crap now I'm going to have to test this out.

---

### Post by rappa on 2009-02-17
I added  --test to /etc/init.d/mdadm and removed --mail= and still got an email so I think it works just fine.

---

