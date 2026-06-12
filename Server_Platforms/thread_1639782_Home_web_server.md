---
title: "Home web server"
date: 2010-12-07
forum: Server Platforms
---

### Post by Win-Smash on 2010-12-07
Hello I and setting up a home web server using Ubuntu 10.04 server (local only). I am currently using Webmin 1.53 to access it remotely all is going great very easy to use. Webmin - Check, ftps-fileZilla - Check, Apache -It Works  BUT I cant seam to set up Apache as a named server using Bind DSN.  Tried most of the help in the fourms and youtube I think my problems is in the master server selection, do i have to use ns1.example.com or can i just use myservername. I have tryed both with no luck. First time with the server addition.

DSN config
//include "/etc/bind/zones.rfc1918";

zone "Smashhome" {
    type master;
    file "/var/lib/bind/Smashhome.hosts";
    };
Apache
Handles the name-based server smasherver on address ***.***.1.***.
 **Address** ***.***.1.***
**Port** 80 **Server Name** smashserver
**Document Root** /home/smash/www

---

### Post by windependence on 2010-12-07
In all likelyhood you don't need to run your own DNS server. You would be much better off using your domain registrar's or ISP's DNS servers for your external DNS. Internally, unless you have 10 or 20 or more machines, a DNS server is not necessary.
 
-Tim

---

### Post by wojox on 2010-12-07
You followed this [Domain Name Service (DNS)]("https://help.ubuntu.com/10.04/serverguide/C/dns.html")

---

### Post by Win-Smash on 2010-12-07
I can access it using the Ip but not as a name. is the problem then with my router. I'm not using a external domain.

---

### Post by Win-Smash on 2010-12-07
My BIND config  looks correct. At least to me

---

### Post by Win-Smash on 2010-12-09
Ok i tuned of the DNS server off and still cant use the name to access the site just the IP. It listed under /ect/apache2/sites-available.

---

### Post by HugoSerrano on 2010-12-09
Hi.
You configured a DNS server, but did you configure other machines in your network to use it?
Anyway, that's not the best way to do that...

If you got a small network, it's best to go to hosts files in the machines and add the resolution from the name to the IP in there. You got some examples in the file.

In ubuntu the file is: /etc/hosts
In windows I think it's c:/windows/system32/drivers/etc/hosts (don't have windows here to check if that&#8217;s right) 

The pretty way and free, is to configure a dynamic dns service, like no-ip or ddns. In the router, forward Port 80 to your webserver, and then you can access to your page with your dynamic dns name!

Regards!

---

