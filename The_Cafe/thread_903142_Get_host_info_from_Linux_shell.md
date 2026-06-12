---
title: "Get host info from Linux shell"
date: 2008-08-28
forum: The Cafe
---

### Post by sudo_t43p on 2008-08-28
Hi,

Is there a "good" program that can be run in the linux shell which can be used to collect as much "leagal" info from a server that is possible?

And also, is there a way to verify e-mail address via the shell, a little like this: [http://verify-email.org/](http://verify-email.org/)

Thanx!

BR,
Chrisse

---

### Post by FFighter on 2008-08-28
curl

---

### Post by Vivaldi Gloria on 2008-08-28
> **sudo_t43p said:**
> Is there a "good" program that can be run in the linux shell which can be used to collect as much "leagal" info from a server that is possible?


nmap is the main tool for this. Read its man page. There are also guides around.

Even telnet, curl, wget, whois can give some info. Try "wget -S www.google.com" or "whois www.google.com" for example.

---

