---
title: "internet access via proxy server"
date: 2010-04-28
forum: Server Platforms
---

### Post by salim.madni on 2010-04-28
ubuntu lts server distro using on remote machine

i have remote site where internet access given via squid proxy. so when we enter in browser it start working internet fine.

but on command line(bash shell prompt terminal) like wget,ping,nslookup,traceroute etc these commands does not work.

advise where what work around needed?

---

### Post by withjigs on 2010-04-28
hi..
try this
[http://blog.taragana.com/index.php/archive/how-to-use-wget-through-proxy/](http://blog.taragana.com/index.php/archive/how-to-use-wget-through-proxy/)

---

### Post by salim.madni on 2010-04-28
/etc/profile i have edit it enter details
/etc/resolv.conf i update all local and global dns

but still commands like ping,traceroute,netstat,ssh outside world not working i want pass everything through proxy

wget start working now

suggest for other commands of linux what to do?

---

### Post by kiwicito22 on 2010-04-28
Mira en [http://tuxxeando.blogspot.com/2010/04/proxy.html](http://tuxxeando.blogspot.com/2010/04/proxy.html)

---

