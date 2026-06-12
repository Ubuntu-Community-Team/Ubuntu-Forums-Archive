---
title: "Need help setting up SSL Self Signed Cert for apache2 web server"
date: 2010-06-30
forum: Server Platforms
---

### Post by miken01 on 2010-06-30
Hi,

I'm new to the forum, and I am also fairly new to server administration. What I am trying to do is enable a self signed cert to be used as the default SSL for the server. I have a default SSL setup, and it works just fine when I enter my IP address, or any of my vhost domains that I have on my server, and that is the problem.

If I go to one of my vhost sites and enter the protocol HTTPS into my browser (eg. [https://example.com](https://example.com)) the browser opens the document root from the default SSL file. 

What I want to happen is when someone types in "https://example.com" then the actual site renders. I understand that a security warning will appear, but after you  confirm the exception then the site should still render. I know it is possible to do this, but I'm not sure how.

Can anyone please help or point me to some documentation that covers this?

Thanks,
Mike

---

### Post by uncleLaz on 2010-06-30
Hi

You can't use SSL Certs on virtual hosts (i assume you are using vhosts)

Basically, the hostname in the header is encrypted, so Apache can't redirect it to the correct virtual host.

You need to set up a standalone instance of apache on another IP address

Hope this helps

Uncle Laz

---

### Post by miken01 on 2010-06-30
Thank you for your post, and I don't mean to be argumentative, but that doesn't sound correct. At the company I work for we have a similar setup. We host hundreds of sites on a single server, and anytime you go to one of our client domains and enter the HTTPS protocol, if they do not have an SSL specifically for their domain, then a security message appears, once you confirm the certificate exception the site will then render. I'm just wanting a similar setup. Any ideas?

---

### Post by uncleLaz on 2010-06-30
Hi There

Sorry - I did make some assumptions which i thought I had put in the reply, but reading it again, I must have only thought them

Every individual site, that uses SSL, must have a unique IP address. What I was trying to say was Named based Virtual Hosts won't work with SSL.

I think I guessed that this is what you were doing as everything was going to your other domain.

If this is not the case then make sure the DNS for the domain you want over SSL is correctly configured, and your are listening on port 443 for the unique IP address of the domain you want to serve over SSL.

For example

NonSSLDomain: Listen 10.4.152.1:80

SSLDomain: Listen 10.4.152.2:443

Hope this helps

UncleLaz

---

### Post by DjangosClouds on 2010-07-01
Hi miken01,
   I think I may be able to help (bit of a beginner myself). I recently setup a system with 3 sites on ports 80, 8080 and SSL. The SSL site is the same as the site on port 80 but it's shared on the internet so that there is some encryption of the passwords.
   I spent quite a while messing about trying to generate a certificate before I realised that Apache 2 automatically created one anyway.
Once I'd discovered that it was simply a matter of using the default SSL configuration:
```
sudo a2ensite default-ssl
sudo a2enmod ssl
sudo /etc/init.d/apache2 restart
```
The important thing to note here is the 2nd line (which I missed first time around). Without out it things go wrong and I think that's what you were describing.
Hope this helps,
   Al

---

### Post by miken01 on 2010-07-01
Thanks for the help guys. I already enable SSL, and I'm sure all of the ports are configured correctly because the actual HTTPS transmission works just fine. I was just wanting to find a way to allow all of my vhosts to share the same SSL, but it sounds like that is not possible to do without the site being on it's own IP address.

Now I have another question, but first I want to give some info for my server. I should have done this first, sorry:)

uncleLaz, you were correct that I am using vhosts to serve my sites. I have a simple server configuration where I have all my sites in the /var/www/vhosts directory, and each site has an associated vhost file that points to the correct directory. I have enabled SSL for the server, and I found that there is a default-ssl vhost file. I can update this file to point to any directory (site) that I want. By using this setup I naturally thought it would be possible to do the same for each vhost (site).

My question now is, how do you suggest I setup, or can you point me to some documentation that can explain how to have multiple IP addresses on a single server, and then have a single site on it with SSL? Any ideas? I'm just out of my element a little. I'm a programmer by trade, and this is the first time I've tried to setup an SSL on a server.

Thanks for all the help everyone!

---

### Post by miken01 on 2010-07-01
Also,

Do you have any suggestions on a better way to run multiple sites on a server? The vhost method is the only one I know of. Are there other ways of having multiple sites on the same IP? Perhaps a way that would allow them all to share the same SSL?

Thanks

---

### Post by Vegan on 2010-07-01
Apache is looking at supporting name based vhosts for SSL but that is not finished yet.

I expect it will be available with the next LTS version of Ubuntu.

Until then the blades have to stay.

---

### Post by uncleLaz on 2010-07-02
Hi,

Yes, Apache are trying to allow NamedHosts to use SSL, but it kind of breaks the thinking behind SSL.

Anyhow, adding IP addresses to a server is quite simple, and I generally follow these instructions [http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

However make sure that you are allowed to use the IP addresses. Don't use one that is currently assigned to another server or a live DHCP client!!!

Once your sever is listening on multiple IP address, setting up apache is a bit like named hosts, and a good link to follow is [http://httpd.apache.org/docs/2.2/vhosts/ip-based.html](http://httpd.apache.org/docs/2.2/vhosts/ip-based.html)

You end up with a one host being

<VirtualHost www.site1.com:443>

and the other being

<VirtualHost www.site2.com:443>

You may need to edit your /etc/hosts file to reflect the IP addresse
/etc/hosts

192.168.0.1     [www.site1.com](www.site1.com)
192.168.0.2     [www.site2.com](www.site2.com)

Hope this helps

UncleLaz

---

### Post by sh1ny on 2010-07-02
If you're using 10.04 you can use SSL in virtual hosts. Why ? RTFM :)

As an example :

[https://onlin*****.bg](https://onlin*****.bg)
[https://stats.dodo.bg](https://stats.dodo.bg)
[https://panel.hostingdodo.com:8080/](https://panel.hostingdodo.com:8080/)

They're all on the same IP and they use 3 different certificates. If this doesn't work for you - upgrade/switch browsers.

First link is filtered by the forum :( I won't spell it out here, but if someone still wants to know, drop me a pm.

---

### Post by sh1ny on 2010-07-02
And here's some of the configs :


```
<IfModule mod_ssl.c>
###########################################################
# SSL Vhost
###########################################################

<VirtualHost 83.148.126.69:443>
      DocumentRoot /var/www/onlin*****.bg/web
  
    ServerName onlin*****.bg
    ServerAlias *.onlin*****.bg
    ServerAdmin webmaster@onlin*****.bg
    
    ErrorLog /var/log/ispconfig/httpd/onlin*****.bg/error.log


    SSLEngine on
    SSLCertificateFile /var/www/clients/client1/web2/ssl/onlin*****.bg.crt
    SSLCertificateKeyFile /var/www/clients/client1/web2/ssl/onlin*****.bg.key
    
</VirtualHost>
</IfModule>
```

```

<IfModule mod_ssl.c>
###########################################################
# SSL Vhost
###########################################################

<VirtualHost 83.148.126.69:443>
      DocumentRoot /var/www/stats.dodo.bg/web
  
    ServerName stats.dodo.bg
    ServerAdmin webmaster@stats.dodo.bg
    

    SSLEngine on
    SSLCertificateFile /var/www/clients/client3/web8/ssl/stats.dodo.bg.crt
    SSLCertificateKeyFile /var/www/clients/client3/web8/ssl/stats.dodo.bg.key
    
</VirtualHost>
</IfModule>
```

---

