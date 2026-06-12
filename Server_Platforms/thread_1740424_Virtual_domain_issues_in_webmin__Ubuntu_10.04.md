---
title: "Virtual domain issues in webmin / Ubuntu 10.04"
date: 2011-04-27
forum: Server Platforms
---

### Post by markosjal on 2011-04-27
I have ubuntu 10.04 installed on 2 different hosts both with Webmin. 

On server 1 , I found I had to configure [www.domain.com](www.domain.com) as well as domain.com for each domain. It seems to work fine.

On server 2 , I can configure [www.domain.com](www.domain.com) but domain.com never works


I use my doimain registrars DNS , so I only set up this part of webmin, and not webmin DNS.

Is it normal that I must enter the domain with "www." and without?

I have set up a test domain and no matter what I do on server 2 I can never see the domain without the www.

I am not sure what the difference is on the two servers and they were set up a couple months apart, but it is clear I do not get the same behaviour

I would like it if I can do a wildcard like *.domain.com and handle both with www. and without, as well as other subdomains that my php scripts use for detection such as es.domain.com. In addition, I will be setting up multiple domains to the same virtual server director. The script behaves differently for each domain. I would however settle for the behaviour of server 1 on server 2 and can not get that

Thanks in advance

---

### Post by elico on 2011-04-27
what service is stored on the server\s?
couldn't understand your question.
it a web server yes.
if you setup the dns on your registrar system it should work as long as the service is allowed to use both names.
so how many physical machines and ips you have?

---

### Post by markosjal on 2011-04-27
to clarify , the issue is NOT DNS related, both servers are LAMP. Currently only one IP on each

The issue is on server 2 the one I most recently put up. It will act as a webserver for both [www.domain.com](www.domain.com) and domain.com , serving files from the same path for both. However I can not seem to get domain.com (without [www.)](www.)) working, Both resolve to the correct IP in the DNS , which I have confirmed with ping.

Server 1 seems to work fine with what seems to be the same configuration. I set up [www.domain.com](www.domain.com) and domain.com 

when accessing domain.com (without [www.)](www.)) server 2 displays
Not Found

The requested URL /cgi-sys/defaultwebpage.cgi was not found on this server.
Apache/2.2.14 (Ubuntu) Server at domain.com Port 80

---

### Post by thinmintaddict on 2011-04-27
You don't need to create a separate virtualhost for the www. subdomain if this is what your asking. In the configuration file for the vhost, you can just create a **Server Alias**. In webmin you can edit the configuration file by clicking "Edit Directives" in the **Virtual Host Options** page. so underneath the line that says```
ServerName domain.com
```
add a line that says
```
ServerAlias www.domain.com
```

Now as long as you have DNS set up correctly to point both the root domain and the subdomain at the correct IP, this should work splendidly.

---

### Post by markosjal on 2011-04-27
Thanks but no joy there either. Alises are not working either

---

### Post by volkswagner on 2011-04-27
I have had unexpected results setting up virtual hosts with Webmin.  With the wizard style of questions, it is not always easy to determine/remember how a previous setup was performed.

Please post your virtual host file so we can check syntax.

After making changes be sure to restart apache2.

---

### Post by markosjal on 2011-04-27
I think what you ask for looks much like that below in its current state. I have tried this a separate virtual hosts and as aliases and neither seems to work. In fact It seems thay it never seems to work with domain.com (no [www.)](www.)) at all


<VirtualHost *:80>
DocumentRoot "\var\www\domain"
ServerName domaion.com
ServerAlias [www.domain.com](www.domain.com) 2domain.com [www.2domain.com](www.2domain.com)
<Directory "\var\www\domain">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

---

### Post by volkswagner on 2011-04-27
> **markosjal said:**
> 
I have set up a test domain and no matter what I do on server 2 I can never see the domain without the www.


Thanks in advance

Is domain.com getting rewritten in the url to [www.domain.com?](www.domain.com?)

Your site must have some rewrite in place.  Try this with just a static html index file and see if you can get both www. and domain.com separated.

---

### Post by markosjal on 2011-04-27
My site presently consists of only index.htm while I resolve this issue. That index.htm is a pure test file

---

### Post by volkswagner on 2011-04-27
I'd love to help but it seems your answers are very short on not descriptive.  ie:  You post "like my vhost" file, how about the actual file (a lot can be messed up by just editing to mask info, let alone posting from memory or guessing)?  

You have not given a description of "it does not work".  What happens in the browser when navigating to domain.com?  Do you have any record of access in /var/log/apache2/access.log, or any errors in /var/log/apache2/error.log?

Are you certain your dns is working correctly?

What do you get for the following?

```
host www.domain.com
```

or 

```
host domain.com
```

---

### Post by markosjal on 2011-04-28
Resolves both with and without www. as expected

The only real difference between host and ping is that host tells me the nameserver and mailserver. As I stated earlier the name both with and without www. resolves correctly, as verified by ping

---

### Post by volkswagner on 2011-04-28
What happens in the browser?  Error, timeout, ???

Does apache log the attempt?

You either have an error in your vhost file or a conflict in a second file.  Do you have any bindings in /etc/host causing the conflict?  Have you tried other client machines/locations outside LAN?

Can you PM me your domain name?

---

### Post by markosjal on 2011-05-01
I will get a test domain pointed back there (I have tested with several already) and PM you when it is ready. Thanks

---

