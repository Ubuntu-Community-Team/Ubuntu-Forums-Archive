---
title: "/etc/hosts.allow and /etc/hosts.deny howto"
date: 2006-08-31
forum: Server Platforms
---

### Post by madtinkerer on 2006-08-31
Hi,

I'm running sshd on my server and I want to limit incoming login attempts to ips in my lan, basically 192.168.65.*  How can I configure the hosts file to get that to work?

Thanks

---

### Post by matko on 2006-09-01
hello,

basic a advice put to /etc/hosts.deny

```
sshd: ALL
```
this will block all connection to ssh

in hosts.allow you can put allowed IP

```
sshd: 195.168.65.*
```

you can alson use expresions like 
```
sshd: ALL EXCEPT 195.168.26.56, 85.216.25.368
```

or you can try install this very good DenyHosts

script. this scripts reads info from /var/log/auth.log and automayicly add IP to hosts.deny. You can also use purge function to delete old blocking

```
http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts[http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts]("http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts")
```

---

