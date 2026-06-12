---
title: "Send LAN users to different site"
date: 2012-06-22
forum: Server Platforms
---

### Post by firedragoneater on 2012-06-22
Hi,
I'm trying to set up a domain so that if it is accessed from within the LAN it goes to a different directory than when accessed from an external location.
Is this possible? I am using Apache and Ubuntu Server 10.04

Many thanks,
Jordan

---

### Post by Merovingi0 on 2012-06-22
Hi,

in apache there is the possibility to configure 2 different virtual host that are listening to the same HTTP port but different IP address.

Is this your case?

---

### Post by pgp_protector on 2012-06-22
I did this Both work & at home

1) Set server to be the DNS Server for the network.
2) Create Virtual Server for your redirected site, or subdomain 
3) Apply DNS Settings to point to your Virtual Server.

---

### Post by firedragoneater on 2012-06-23
Okay, that's great, thanks. I think I'll give it a miss as it's not really possible for me to setup a DNS server there. However, if there is a way that I can do this without the need for DNS and just with a Virtual Host, that would be great.
Thanks for your help,
Jordan

---

### Post by volkswagner on 2012-06-23
Without knowing the specific reason for your request, I personally would have internal users access the site from a subdomain.  Create two virtual hosts [www.domain.com](www.domain.com) for external users and int.domain.com for internal users.

If you don't like that approach you can use php script, dns options as previously mentioned, or mod_rewrite.

Here are some basic ref. that may help your search.

[http://www.linuxquestions.org/questions/linux-server-73/apache-redirection-based-on-ip-865079/](http://www.linuxquestions.org/questions/linux-server-73/apache-redirection-based-on-ip-865079/)

[http://www.linuxquestions.org/questions/linux-server-73/source-address-based-virtual-hosting-787115/](http://www.linuxquestions.org/questions/linux-server-73/source-address-based-virtual-hosting-787115/)

---

### Post by SeijiSensei on 2012-06-23
Is the server "multi-homed" with two interfaces, one pointing to the LAN and one to the outside?  If so, then the easiest solution is to define a virtual host and bind it to the internal interface.  

Suppose the server has an external interface eth0 and and internal interface eth1, with address 192.168.1.10, pointing to the LAN.  Then create a virtual host definition in /etc/apache2/sites-available like this:

```

<VirtualHost 192.168.1.10:80>
    ServerName internal.example.com
    DocumentRoot /path/to/internal/site/directory
    etc.
</VirtualHost>

```

Visitors connecting to eth0 won't see this site at all.

If you only have one interface, then you'll have to discriminate by server name either with a local DNS server or the use of hosts files on the clients as others have suggested above.  In that case I'd make sure the internal site is limited to LAN users like this:

Suppose the server has IP 192.168.1.10, and it connects to the LAN router at 192.168.1.1, with all the client machines in the 192.168.1.0/24 subnet.  To limit access to the client machines, but not allow external access, means we need to block the router's address but not other machines in the LAN.

```

<VirtualHost *:80>
    ServerName  internal.example.com
    DocumentRoot /path/to/internal/site/directory
   
    <Directory "/path/to/internal/site/directory">
        Order allow,deny
        Allow from 192.168.1.0/24
        Deny from 192.168.1.1
        [etc.]
     </Directory>

     [etc.]

</VirtualHost>

```

The access controls in Apache are a bit weird, so I recommend reading the [documentation]("http://httpd.apache.org/docs/2.0/mod/mod_access.html#order").

---

### Post by firedragoneater on 2012-06-23
Great, thanks! I'll give it a try later.
Thanks again,
Jordan

---

