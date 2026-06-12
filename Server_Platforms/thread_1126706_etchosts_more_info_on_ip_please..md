---
title: "/etc/hosts more info on ip please."
date: 2009-04-15
forum: Server Platforms
---

### Post by Spikerok on 2009-04-15
Following is a sample /etc/hosts file:
[PHP]
           IPAddress     Hostname    		 Alias
           127.0.0.1			localhost	 	 deep.openna.com
           208.164.186.1		deep.openna.com		 deep
           208.164.186.2		mail.openna.com		 mail
           208.164.186.3		web.openna.com		 web
[/PHP]
if i correctly understood them are intranet ip's, so there are 3 servers on intranet which have ip's *.1, *.2 and *.3.
208.164.186.1
208.164.186.2
208.164.186.3

so if their will be only one computer, with intranet ip of *.2
their will be no way of accessing *.1 and *.3, because there is only one server with ip of *.2?

---

### Post by volkswagner on 2009-04-15
Your question is very confusing.   You may need to add some information.

Hopefully the following will help clear things up.

/etc/hosts is best used for accessing local machines by their hostname rather than the IP address.  When I have three machines on my LAN I add the static IP address and hostname for each machine, on all /etc/hosts files.  This way I can ssh user@hostname rather than the IP.  I can also access using hostnames within a browser if needed.

I am making an assumption that you may be confusing apache2 virtual hosts with your /etc/hosts.  I could be way off, so please explain what you are trying to accomplish.

---

### Post by BkkBonanza on 2009-04-16
Your file has an error in that deep.openna.com is being resolved to 2 different ips. You can only have one ip per name but can have several names per ip.

If you only have one server then you should have all the names that you want resolving to the server resolve to that ip. eg.

127.0.0.1            localhost
208.164.186.2        deep.openna.com         deep
208.164.186.2        mail.openna.com         mail
208.164.186.2        web.openna.com         web

There is no problem with having all these names go to this server. Having them go to a server ip that doesn't exist is not going to work at all. Keep in mind that the /etc/hosts file is only used by the local machine. If you need name resolution for your whole netowrk you should use a dns server or dnsmasq as a simple replacement. Your router normally handles this function. If you need name resolution for public computers on the internet then you should use a public dns provider.

And as the commenter above noted - if you are trying to get multiple domains on a web server working then that is a different thing altogether - for that you need to configure apache for name based virtual hosting. See apache docs.

---

### Post by Spikerok on 2009-04-16
thank you for help, i understand it now.

---

