---
title: "trying to Configuring Zimbra and Apache"
date: 2011-05-26
forum: Server Platforms
---

### Post by chris.tanaka on 2011-05-26
Hi there, 

I'm trying to install Zimbra and Apache. I'm having difficulty setting up DNS (if necessesary) and also configuring my /etc/hosts
Could anyone show me what the /etc/hosts should look like. 

Thanks

---

### Post by Lars Noodén on 2011-05-26
You shouldn't have to mess with /etc/hosts.  The registrar where you registered the domain should also provide a means to assign it to your specific IP address, if that's what you're trying to do.

Further some applications are designed  to ignore /etc/hosts, so that kludge won't work in all cases.

---

### Post by chris.tanaka on 2011-05-27
Many thanks. So when configuring Zimbra I just use 198.168.x.x and have all the MX records of my domain point to my ubuntu box?

---

### Post by Lars Noodén on 2011-05-27
You have an external IP number to use, right?

---

