---
title: "Reverseproxy"
date: 2012-09-21
forum: Server Platforms
---

### Post by mcc28x on 2012-09-21
Hi,

I have Ubuntu server running with Apache installed and working. I have a virtual WordPress appliance(Virtualbox) running on the server. 

The server ip is 192.168.0.32 and the WordPress server is on 192.168.0.14. To reach the WordPress server I type 192.168.0.14/wordpress - using the hostname (wordpress) doesn't work and I can't ping it on the network (but I can ping 192.168.14).

The Ubuntu server hostname is thaddeus and I want to be able to type [http://thaddeus/wordpress](http://thaddeus/wordpress) and reach the wordpress appliance running at 192.168.0.14/wordpress - I understand Proxypass/ProxypassReverse do this...

Under sites-available I have added the file wordpress:
```
#This is for virtual host sites on server2 @ 192.168.0.14
<VirtualHost *:80>
        ServerAdmin webmaster@domain.com
        ServerName wordpress
# You can have list of space separated aliases if you server2 hosts multiple domains
        ServerAlias wordpress
# If you have multiple hosts (NameVirtualHosts on server 2, you will need to preserve
# hostname, or you will always land at the root of
# the second server. ie: what ever the default site is.
        ProxyPreserveHost on
# Need to allow location / if you want the proxy to
# work when no folder is written in the url.
         <location />
          allow from all
     </location>

# This is where all the magic happens.
# You can modify the following for specific folders only and any remote host
# you can also specify a different port if you like
        ProxyPass /wordpress http://192.168.0.14/
        ProxyPassReverse /wordpress http://192.168.0.14/

</VirtualHost>
~

``` 

and enabled the site & restarted Apache. It doesn't work though - the Apache error log says /var/www/wordpress does not exist.

Could anyone help please?

thanks

Mark

---

### Post by koenn on 2012-09-23
Tw questions

1- is there a reason you think you need a proxy for this ?
2- where did you get the proxy conf from ?

re 1-
You can probably do this with a bit of DNS config (or simply editing /etc/hosts)

re 2- I think something like this might work : ```

        ProxyPass     /    http://192.168.0.14/wordpress
        ProxyPassReverse / http://192.168.0.14/wordpress

```
but I'm not exactly sure what you're trying to achieve. For one, if you want "thaddeus" to proxy for the virtual wordpress, I'd expect this apache conf on thaddeus ( 192.168.0.32 ?), not on "server2 @ 192.168.0.14"

---

### Post by volkswagner on 2012-09-23
This is not a proxy issue.

You have no local DNS entry for a LAN machine to resolve the webserver ip to the domain name.

On the machine you are trying to view the Wordpress from, do as mentioned with the /etc/hosts file.

Your entry will look like:

```
192.168.0.14  thaddeus wordpress
```

The above will let you access the site with:
 [http://thaddeus/wordpress](http://thaddeus/wordpress)

or

 [http://wordpress](http://wordpress)

Provided you fix the issue of "cannot find /var/www/wordpress" this should get the hostname working.

Where is word press installed on the server?

You will need name based virtual host working on the web server for this to work also.

I would start with the DNS issue first, by performing the /etc/hosts edit on the client machine.  Then setup a proper vhost file for apache to listen on Servername with the proper DocumentRoot.

---

### Post by koenn on 2012-09-23
> **volkswagner said:**
> This is not a proxy issue.


I agree, 
but I kinda like the idea that one could run a handfull of Virtual Appliances, presumably with private addresses, on a server (possibly with a public address) and abstract all of it away by putting a reverse proxy in front of it. 


> Provided you fix the issue of "cannot find /var/www/wordpress" this should get the hostname working.

Where is word press installed on the server?

The issue there is that the wordpress is on the virualbox, but his browser talks to apache on the host server - I think.
the "proxy" apache doesn't have a wordpress directory, and no Location or Alias for /wordpress, so it looks in DocumentRoot for a subdir of that name, and finds nothing is there. 

I think my solution #2 might is one way of fixing that (and defining an Aliases or a Location might be another), but I agree with you that fixing this with DNS (and maybe a vhost) would be preferable, unless there's a very good reason to try this by way of a reverse proxy.

---

### Post by volkswagner on 2012-09-23
Perhaps I was not following as I should.

To clear things up, I was expecting this setup for a LAN environment only.  If the OP needs one webserver to respond to all requests and forward certain requests to different web server machines then he will need a reverse proxy.

If  all traffic is behind the router (LAN only), you can happily have many web servers running on port 80 with no need for a central server acting as a reverse proxy.

---

### Post by mcc28x on 2012-09-25
> **volkswagner said:**
> Perhaps I was not following as I should.

To clear things up, I was expecting this setup for a LAN environment only.  If the OP needs one webserver to respond to all requests and forward certain requests to different web server machines then he will need a reverse proxy.

If  all traffic is behind the router (LAN only), you can happily have many web servers running on port 80 with no need for a central server acting as a reverse proxy.

To clarify my ubuntu server is running on an ip of 192.168.0.32 hostname thaddeus. On this box I had a VM hostname 'wordpress' (Turnkey appliance) on 192.168.0.14 bridged network adapter. I had updated all the /etc/hosts files so that the ip's were all listed locally.

All I wanted to do was type in [http://thaddeus/wordpress](http://thaddeus/wordpress) and have the pages served from the wordpress VM with thaddeus acting as proxy.

The wordpress site was a virtual host (pre-configured as part of turnkey appliance) so [http://192.168.0.14](http://192.168.0.14) was the same as [http://192.168.0.14/wordpress](http://192.168.0.14/wordpress).

I thought reverseproxy would be a good solution for this. I could only get it to partially work. I thought that reverseproxy / would be equivalent to [http://192.168.0.14/wordpress](http://192.168.0.14/wordpress) but this didn't work whereas / /http://192.168.0.14 worked partially. I think I needed to add a DocumentRoot statement too.

I might return to this in the next few days but was put off when I discovered that enabling the wordpress site under sites-enabled meant that, for example sites-enabled/gallery or sites-enabled/myownsite was no longer found. Something in the wordpress virtual host file had caused a problem so I have temporarily disabled it.

cheers for the comments.

---

### Post by HugoSerrano on 2012-09-25
If you can't ping the name, you can't access it.
You really need to be able to solve the name thaddeus to 192.168.0.14 first then anything.

As you may not have a local DNS server, you need to add it in /etc/hosts (or equivalent in windows, think c:/windows/system32/drivers/etc/hosts) to all the machines from where you will access the site.

---

### Post by mcc28x on 2012-09-25
> **HugoSerrano said:**
> If you can't ping the name, you can't access it.
You really need to be able to solve the name thaddeus to 192.168.0.14 first then anything.

As you may not have a local DNS server, you need to add it in /etc/hosts (or equivalent in windows, think c:/windows/system32/drivers/etc/hosts) to all the machines from where you will access the site.

I as mentioned above did update the hosts files for all machines on the Lan. I can ping all machines by host and no problem there is no local DNS server. 

I can reach thaddeus via the FQDN over the Internet but as I only have one IP I wanted to have thaddeus act as a proxy for the VM with Wordpress site. 

Cheers

---

### Post by volkswagner on 2012-09-25
> **mcc28x said:**
> ....
I can reach thaddeus via the FQDN over the Internet but as I only have one IP I wanted to have thaddeus act as a proxy for the VM with Wordpress site. 

Cheers

Thanks for clarifying.  You will need a reverse proxy when you host multiple web servers using only one external ip address.

> **mcc28x said:**
> To clarify my ubuntu server is running on an ip of 192.168.0.32 hostname thaddeus. On this box I had a VM hostname 'wordpress' (Turnkey appliance) on 192.168.0.14 bridged network adapter. I had updated all the /etc/hosts files so that the ip's were all listed locally.

All I wanted to do was type in [http://thaddeus/wordpress](http://thaddeus/wordpress) and have the pages served from the wordpress VM with thaddeus acting as proxy.

The wordpress site was a virtual host (pre-configured as part of turnkey appliance) so [http://192.168.0.14](http://192.168.0.14) was the same as [http://192.168.0.14/wordpress](http://192.168.0.14/wordpress).

I think you will have better results with subdomains.  I'm no expert, but the combination of reverse proxy and NameBasedVirtualHosts may not work well with sub folders as the sole distinguishing factore between two different machines.  I think you would be better off creating a subdomain like wp.thaddeos or your real domain name....

Then you will create the reverse proxy on the machine (192.168.0.32) which has port 80 forwarded from the router .

Start with a basic config and add as necessary:
```
<VirtualHost *>
	ServerAdmin webmaster@wp.thaddeus
	ServerName wp.thaddeus
	ProxyPreserveHost on
	 <location />
          allow from all
     </location>


     	ProxyPass / http://192.168.0.14/
     	ProxyPassReverse / http://192.168.0.14/

</VirtualHost>

```

With the above setup you would want your wordpress vhost file having a document root pointing directly at wordpress so you can eliminate the /wordpress from the url.

else you would need to enter "wp.thaddeus/wordpress" in the url **and** have the following vhost for reverse proxy:

```
<VirtualHost *>
	ServerAdmin webmaster@wp.thaddeus
	ServerName wp.thaddeus
	ProxyPreserveHost on
	 <location />
          allow from all
     </location>


     	ProxyPass /wordpress http://192.168.0.14/wordpress
     	ProxyPassReverse /wordpress http://192.168.0.14/wordpress

</VirtualHost>

```



each time you add an additional host on a machine other than 192.168.0.32, you will want a similar vhost.  You will need the appropriate dns records for your fqdn.  This changes things if you are using a free dns without the ability to create subdomains.

---

