---
title: "Nmap shows MySQL and Apache ports open...dangerous?"
date: 2013-02-25
forum: Security
---

### Post by ButtBuntu on 2013-02-25
Hey all, I did a port scan of my computer today and it is showing that MySQL and Apache ports are Open.  Is there a way to "close" these ports while keeping the server and database running?  They are both running in the context of Snort IDS along with ACID/BASE.

Thanks.


In addition, it's showing CUPS and another domain process as open.  Googling these advises that there is no real danger having these ports open.  Would also entertain opinions on this.

---

### Post by Ms. Daisy on 2013-02-25
Totally depends on where you ran the scan from and if sql, apache & cups are NAT'd. If you ran the scan across the internet then those ports are open to the world, you'll need some extra controls around them. If these services are running behind a router and the ports aren't forwarded then it's far less of a concern.

Did you run the scan from inside the subnet? Which scanner did you use, shields up?

---

### Post by kevdog on 2013-02-25
I believe all ports are open by default but with no listening services.  If you do not have any listening services on these ports, then it doesn't really matter.  I you do have listening services (such as servers -- in your example a web server and mysql server), you should take appropriate security methods to restrict access to these services either through modifications of the /etc configuration files for the program, or via use of iptables or by placing your computer behind a router and limiting the NAT translation to your computer.

---

### Post by bodhi.zazen on 2013-02-26
Well, as the others have indicated, "it depends".

1. What / how did you perform the scan ? Port 80 (Apache) could be your router.

2. What services are you wanting to run ? Who do you want to have access.

In general, Apache is designed for public access, so what would be the point of blocking it with iptables ?

In general, mysql should only be listening on localhost, but it can be configured otherwise.

Based on what little information the OP has given, anyone's guess really.

---

### Post by aerokid240 on 2013-03-07
Sounds like you did a ***_# nmap localhost_*** scan lol. By default Mysql listens on 127.0.0.1, so unless you didn't explicitly changed this in the config, I can only imagine you may have portscanned your localhost.

---

