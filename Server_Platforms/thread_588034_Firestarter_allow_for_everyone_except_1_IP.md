---
title: "Firestarter allow for everyone except 1 IP ??"
date: 2007-10-23
forum: Server Platforms
---

### Post by micheline on 2007-10-23
Can firestarte allow incoming connections on a  port for everyone except 2-3 IPs ? If so please help me configure it this way ... thank you !

---

### Post by dmizer on 2007-10-23
what exactly do you need to do?  blocking 2 or 3 ip's is not likely the solution.  most ip addresses are dhcp (change frequently), so while you may be blocking the desired ip today ... tomorrow (or in a couple hours) ... the same individual could easily access your system. and even if they do not change, it's a simple matter to use a proxy server and present any ip you desire.

you can also take a look here: [http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

---

### Post by micheline on 2007-10-23
yes i know ... I am running a l2j server ... and i opened up port 2 ports for the l2j server for "everyone" beacouse i have 200-300 users all the time ... and i am having trouble wyth some russians haxors , and i want to make an exception and ban them ... and dont worry i know all the IP range of those IPs ... now, is it posible ?

---

### Post by dmizer on 2007-10-23
yes it's possible to block a range of ip's (see the link i provided above).  but again, it's a painfully simple matter to bypass that kind of protection.

---

