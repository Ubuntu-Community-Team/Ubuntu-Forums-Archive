---
title: "Conserned with DHCP server setup"
date: 2011-02-27
forum: Server Platforms
---

### Post by DrReaper on 2011-02-27
I have a basic question about setup of a LAMP server. I am on a DHCP from Time warner cable. That is a problem only because my IP can change. I expect I can still get my domain to update using Dyndns. However the server itself is programed with my wan ip address that may change. I have never setup Dydns. or a server without a set ip. Should I be concerned? Is this even going to work? 

I am concerned because to get the server to be seen on the Internet I had to program in my external ip in more then a few files in my wordpress. If the ip ever changes I would have to re enter the new ips.  Is there a way to automate this change or should I just give up and get a dedicated IP at the cost of $150.00 per month? I really don't have the money to be paying for that kind of hosting.

---

### Post by Vegan on 2011-02-27
Do not feel bad, everyone has the same problem.

My ISP rarely has to change IP addresses as they are still OK with the address pool.

---

### Post by SeijiSensei on 2011-02-27
> **DrReaper said:**
> Is there a way to automate this change or should I just give up and get a dedicated IP at the cost of $150.00 per month?

A *much* cheaper option is to [rent a virtual machine for $20/month]("http://www.linode.com/").  You'll have a public IP, a huge pipe, backup generators, and for a couple bucks more a month, daily snapshot backups.

---

