---
title: "Fancy Firewall / User based proxy"
date: 2007-01-26
forum: The Cafe
---

### Post by schurtek on 2007-01-26
I am requiring a solution like IPCop... but more trying to stop data going out...

We recently had an episode where a staff member was sending out confidential company information using a webmail type email account.

Now yes, I can go block that url, but then they can just use another provider... what I want to do is have a firewall / proxy server that allows me to have a seperate set of rules for each user on the network. 

That I can assign each person access to the websites that they require access to...

Any ideas?

---

### Post by mips on 2007-01-26
How many employees, what desktop OS ? Use DHCP ? You need to give us a bit more info.

It is very easy to over-complicate things. Maybe you should just get a list of websites from each employ and only allow access to those sites. If additional access is required the site gets added.

I hear most about Squid proxy. For firewall I would just use the normal IP Tables and use Firewall builder to generate the ruleset.

[http://www.netfilter.org/](http://www.netfilter.org/)
[http://www.squid-cache.org/](http://www.squid-cache.org/)
[http://www.fwbuilder.org/](http://www.fwbuilder.org/)
[http://www.linux.org/docs/ldp/howto/Firewall-HOWTO.html](http://www.linux.org/docs/ldp/howto/Firewall-HOWTO.html)
[http://www.aboutdebian.com/proxy.htm](http://www.aboutdebian.com/proxy.htm)
[http://www.ubuntuforums.org/showthread.php?t=89320](http://www.ubuntuforums.org/showthread.php?t=89320)
[http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)

---

### Post by schurtek on 2007-01-27
Staff: about a dozen... will grow in the future

You see this is the situation. I want to give certain people access to certain sites only... others to other sites (ie only the sites that pertain to their jobs)... but then three people need complete unrestricted access as they do our research. I know it's easy to block undesired sites... but then I will be adding stuff every day. Rather I would have it that when someone needs to access a certain site then they simply request access and management can decide if we give that person access or not. 

We have been suffering from bandwidth abuse and want to curb it, but since there are certain sites that pertain to certain departmental functions we can't just cut net access all together.

I have been playing around with IP Cop quiet a bit and have found a tool called advanced proxy... seems to have potential... but I would also like to assign a daily bandwidth allocation to each member of staff, according to the occupational requirements?

---

### Post by saulgoode on 2007-01-27
I have only been using IPcop for a short while and if I understand your needs correctly, I do not think it is well-suited to meet them. To address your last question first, there is no capability to impose quotas on specific IPs (although that feature may be in the next version). 

In order to restrict access to particular users, I thinky you would have to run your IPcop in reverse -- employing [DMZ pinholes](http://www.ipcop.org/1.4.0/en/admin/html/section-firewall.html#section-dmz-pinholes) to permit particular IPs with access to the outside network. The problem with this is that, by the default IPcop setup, the Internet becomes the GREEN zone and if you are not careful, you could serve up your network to the world.

You could probably have the GREEN network of this "reversed" IPcop run through a second (normally configured) IPcop to the Internet but I would have to imagine there are better solutions available.

---

### Post by schurtek on 2007-01-28
I am actually running a hardware firewall between the IPCop box and the Internet... and it's pretty strong...

---

