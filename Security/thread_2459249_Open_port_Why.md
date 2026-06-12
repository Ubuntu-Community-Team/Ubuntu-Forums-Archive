---
title: "Open port Why?"
date: 2021-03-14
forum: Security
---

### Post by thumper76 on 2021-03-14
My question is why on Ubuntu 20.04.2 LTS Desktop is port 25 (smtp) open and who is master? Does this mean I am unknowingly running a  mailserver or is something else going on? 

```
[rick@PowerSystem:~$ sudo lsof -nP -i | grep LISTEN
systemd-r    731 systemd-resolve   13u  IPv4  36602      0t0  TCP 127.0.0.53:53 (LISTEN)
cupsd        939            root    6u  IPv6  44275      0t0  TCP [::1]:631 (LISTEN)
cupsd        939            root    7u  IPv4  44276      0t0  TCP 127.0.0.1:631 (LISTEN)
riseup-vp   1546            rick   32u  IPv4  53481      0t0  TCP 127.0.0.1:6061 (LISTEN)
master      2731            root   13u  IPv4  53319      0t0  TCP *:25 (LISTEN)
master      2731            root   14u  IPv6  53320      0t0  TCP *:25 (LISTEN)
```

---

### Post by CharlesA on 2021-03-14
Hi,

master is the name of the process and it's probably related to postfix or exim, which are both mail servers.

They can get installed as a dependency if you install something such as smartmontools.

You can try to purge it and see which packages it wants to remove to see what installed it.

```
sudo apt purge postfix
```

---

### Post by thumper76 on 2021-03-14
Thanks for the reply. I ran "purge postfix" and that removed open port 25 and master. Nothing else was listed a a dependency so I'm not sure how postfix got installed.

---

### Post by TheFu on 2021-03-14
cron wants there to be an MTA so you can get email notifications. When it was installed, there should have been some questions ask with the postfix install asking what sort of SMTP server this was. If you chose "Satellite", then it won't accept inbound email, but can send email out ... like to your gmail account through an SMTP gateway system run by your ISP. This would have been the "Relay host" question which was asked.

I don't know what exim asks, if anything. Never touched that.

All my systems run satellite postfix SMTP servers and send email to my internal mail server. They will not accept any email through a network connection, only email that begins no the same system, locally.

---

### Post by kevdog on 2021-03-17
Master to my knowledge belongs to postfix.  I've had to alter the master.conf file when setting up postfix in the past.

---

### Post by Skaperen on 2021-03-18
you can configure postfix to listen to port 25 from localhost only.  then. the only way to connect is to 127.0.0.1:25 (in IPv6 [::1]:25).  if you need to get local-only email, that's the way to do it.  then you can add TCP tunnels from outside hosts to connect to it if you want email from other locations, or not.

---

