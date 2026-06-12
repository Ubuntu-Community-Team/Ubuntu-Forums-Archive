---
title: "Server Utilities"
date: 2009-08-10
forum: Server Platforms
---

### Post by harry.richardson on 2009-08-10
Hey guys,

Not sure if this is the appropriate place for this, if not accept my apologies. I work for a big datacenter company and I am not a huge fan of web-based tools. I've got a server that I have full control over and I have Ubuntu on (my favorite Linux Flavor I might add)  I am on the support side for customers that have email with us. A lot of the troubleshooting we do is checking iptools and other things.

[Note I am using SSH for this box.]

I am much more comfortable with the command line interface through ssh then I am with web-based interfaces. I am looking for some ideas of good tools to have installed on the server. 

Currently I have:

[LIST]
[*]dnsutils (use dig for MX record checks)
[*]Telnet to log into mail servers to do a manual check of what the mailservers do if clients are having issues wit
[/LIST]
This is my personal server, and the tools are just a way of me getting around wonky and irritating interfaces. Just looking for some suggestions.

just ti give you all a quick rundown, we Check MX and A records, we check whois to make sure domains are owned by clients or resellers under us. we also check logs to diagnose problems. We read Mail headers and such. So anything that you guys might be able to suggest that would be able to let me bypass some web-interfaces for generic tools, I would be forever grateful..

Thanks in advance
Harry Richardson.

---

### Post by R.Bucky on 2009-08-11
A couple of my favorite:

Checks PTR records
```
nslookup
set type = ptr
```

I like htop for a semi-gui Terminal based system monitor

nmap - for network mapping

```
netstat -tulpn
```

---

### Post by harry.richardson on 2009-08-11
Awesome Thanks for the advice, Htops is nice to make sure im not killing this poor little guy.

---

