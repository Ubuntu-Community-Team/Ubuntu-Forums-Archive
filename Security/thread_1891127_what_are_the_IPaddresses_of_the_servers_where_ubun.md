---
title: "what are the IPaddresses of the servers where ubuntu updates reside?"
date: 2011-12-04
forum: Security
---

### Post by Rajeshv_99 on 2011-12-04
what are the IPaddresses of the servers where ubuntu updates ([FONT=Georgia][SIZE=3]Ubuntu 8 .04):)[/SIZE][/FONT] reside?

---

### Post by newbie-user on 2011-12-05
it would be better to connect to them via domain name, for example archive.ubuntu.com, since the ip addresses might change.  Also, you could make your own local repository server.

---

### Post by Lars Noodén on 2011-12-05
Look for the host names in [font=Courier New]/etc/apt/sources.list[/font] and then use [dig](http://manpages.ubuntu.com/manpages/precise/en/man1/dig.1.html) or [host](http://manpages.ubuntu.com/manpages/precise/en/man1/host.1.html) to convert the host name to an IP address.

However, it is nearly always better to work with the hostnames rather than IP addresses.

---

### Post by Rajeshv_99 on 2011-12-05
What are the server names of the servers where ubuntu updates reside?

---

### Post by Lars Noodén on 2011-12-05
You will find them in [font=Courier New]/etc/apt/sources.list[/font].  It will be something like "gb.archive.ubuntu.com", but with the 'fi.' replaced with your own country code.

```

less /etc/apt/sources.list

```

---

### Post by Rajeshv_99 on 2011-12-05
Thanks Lars!!!

---

