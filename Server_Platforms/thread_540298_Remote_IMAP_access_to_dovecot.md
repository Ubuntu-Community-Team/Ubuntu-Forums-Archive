---
title: "Remote IMAP access to dovecot"
date: 2007-09-01
forum: Server Platforms
---

### Post by cliptin on 2007-09-01
I have a working Roundcube installation hosted at unixshell but I want to access my mail remotely.

On the server "telnet localhost imap" yields "* OK Dovecot ready."

On the server "netstat -tl | grep -i imap" yields "tcp        0      0 localhost:imap2         *:*                     LISTEN"

When I telnet to the server on 143 or 110 from a remote computer I get "Connect failed".

How do I find the problem?

---

### Post by HermanAB on 2007-09-01
Check iptables, since Netfilter may be blocking the ports:
$ sudo iptables -L

Also check /etc/hosts.allow and hosts.deny, since tcpwrappers may also be blocking remote access.  Read 'man hosts.allow' for details.

Cheers,

Herman

---

