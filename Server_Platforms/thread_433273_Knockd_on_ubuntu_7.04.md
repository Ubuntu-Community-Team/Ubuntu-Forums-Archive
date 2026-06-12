---
title: "Knockd on ubuntu 7.04"
date: 2007-05-04
forum: Server Platforms
---

### Post by Luis McDOugall on 2007-05-04
[SIZE="3"]Hi!

I just installed Knockd using Synaptic.
I have made the changes to the config file in /etc/defaults.
when I try to start knockd via /etc/init.d/knockd start
It complaints about every line I put in the config file.

Any solutions?

Thnks.
-L[/SIZE]

---

### Post by SadaraX on 2007-08-13
I got my knockd to start by running it from command line first with --debug and --verbose to see what was wrong. In my case, it did not like the configure file lines that were no under [something] headers. So I removed them. My configuration file looks like this:

```

[options]
  logfile = /var/log/knockd.log
  interface = eth0

[openSSH]
  sequence    = 7000,8000,9000
  seq_timeout = 5
  command     = /sbin/iptables -A INPUT -s %IP% -p tcp --dport 22 -j ACCEPT
  tcpflags    = syn

[closeSSH]
  sequence    = 9000,8000,7000
  seq_timeout = 5
  command     = /sbin/iptables -D INPUT -s %IP% -p tcp --dport 22 -j ACCEPT
  tcpflags    = syn

```

Pretty standard, none of the original default stuff left there at all. Try this.

---

