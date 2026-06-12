---
title: "Help with Apache Reverse Proxy"
date: 2015-04-01
forum: Server Platforms
---

### Post by abernut on 2015-04-01
I currently have an Ubuntu server hosting my live website, Site1.com.  
I now need to host a windows web server out to the world, Site2.com.

The private IPs are
172.31.101.19 (Ubuntu)
172.31.101.12 (Windows)

I have read through ever article on setting up a reverse proxy that I can find.

At the current state, if I try to browse to Site2.com I get the default apache page.

I have created the following file.
[COLOR=#000000][FONT=Monaco][B]/etc/apache2/sites-available/Site2.com.conf
[/B][/FONT][/COLOR]that reads
```
<VirtualHost *>        
        ServerAdmin me@Site2.com
        ServerName Site2.com
# You can have list of space separated aliases if you server2 hosts multiple do$
        ServerAlias Site2.com
# If you have multiple hosts (NameVirtualHosts on server 2, you will need to pr$
# hostname, or you will always land at the root of
# the second server&#8230; ie: what ever the default site is.
        ProxyPreserveHost on
# Need to allow location / if you want the proxy to
# work when no folder is written in the url.
         <location />
          allow from all
     </location>


# This is where all the magic happens.
# You can modify the following for specific folders only and any remote host
# you can also specify a different port if you like
        ProxyPass / http://172.31.101.12/
        ProxyPassReverse / http://172.31.101.12/


</VirtualHost>
```

I have also edited the following file
[COLOR=#000000][FONT=Monaco][B]/etc/apache2/mods-available/proxy.conf
[/B][/FONT][/COLOR]```
<IfModule mod_proxy.c>

    # If you want to use apache2 as a forward proxy, uncomment the
    # 'ProxyRequests On' line and the <Proxy *> block below.
    # WARNING: Be careful to restrict access inside the <Proxy *> block.
    # Open proxy servers are dangerous both to your network and to the
    # Internet at large.
    #
    # If you only want to use apache2 as a reverse proxy/gateway in
    # front of some web application server, you DON'T need
    # 'ProxyRequests On'.


    #ProxyRequests On
    <Proxy *>
       AddDefaultCharset off
       Require all denied
       #Require local
    </Proxy>


    # Enable/disable the handling of HTTP/1.1 "Via:" headers.
    # ("Full" adds the server version; "Block" removes all outgoing Via: headers)
    # Set to one of: Off | On | Full | Block
    ProxyVia On


</IfModule>


# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

```

I am not sure what I have done wrong. 
Any assistance would be greatly appreciated.
Thanks

---

### Post by slickymaster on 2015-04-01
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by dragonfly41 on 2015-04-01
After editing your virtualhost

you need to *enable* them .. then reload or restart apache2.

sudo a2ensite Site2.com.conf

sudo a2enmod proxy.conf

sudo /etc/init.d/apache2 reload
or
sudo service apache2 reload

.. also check /etc/hosts file

---

### Post by abernut on 2015-04-01
When I run
```
sudo a2enmod proxy.conf
```
I get 
```
ERROR: Module proxy.conf does not exist!
```

Here is the content of the etc/hosts file
```
127.0.0.1    localhost
172.31.101.19    linuxsrvr.domain.local    linuxsrvr


#Virtual Hosts
#IP-ADDRESS GOES HERE




# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

---

### Post by abernut on 2015-04-01
proxy.conf is listed in the /etc/apache2/mods-enabled

---

### Post by matt_symes on 2015-04-01
Hi

> **abernut said:**
> When I run
```
sudo a2enmod proxy.conf
```
I get 
```
ERROR: Module proxy.conf does not exist!
```

You need to specify the module only.

```
sudo a2enmod proxy
```

Kind regards

---

### Post by abernut on 2015-04-01
That worked.
Although when I try to browse to Site2.com I still get the Apache2 Default Page

---

### Post by dragonfly41 on 2015-04-01
> You need to specify the module only.

Sorry about adding the (unrequired) extension .. I was writing from memory.

You don't specify what version of Ubuntu server and apache2 you are running.

Note that some directives changed in migrating from apache 2.2 to 2.4.

You don't have a virtualhost IP address specified in /etc/hosts

You have not specified DocumentRoot.

And more ..

I would research some blogs on virtualhost configuration.

[https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts)

---

### Post by abernut on 2015-04-01
I am running Ubuntu 14.04 LTS
and Apache 2.4.7

In all the posts I've read I've never seen one mention editing the etc/hosts file.

Would it look something like this:
```

127.0.0.1    localhost
172.31.101.19    site1.domain.local    site1


#Virtual Hosts
172.31.101.12    site2.com
```

---

### Post by abernut on 2015-04-01
[https://www.digitalocean.com/communi...untu-14-04-lts]("https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts")

That discussion appears to help if you have multiple sites on the same server.

---

### Post by abernut on 2015-04-01
I'm wondering if I need to modify the 000.default.conf file

---

### Post by abernut on 2015-04-02
Would this be easier if I were to migrate Site2 over to the Linux server.
The only issue is that Site2 uses ASP.NET

---

