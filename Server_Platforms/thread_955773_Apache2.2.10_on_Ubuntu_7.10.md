---
title: "Apache2.2.10 on Ubuntu 7.10"
date: 2008-10-22
forum: Server Platforms
---

### Post by bruparel on 2008-10-22
I have two Ubuntu 7.10 laptops and a Windows XP laptop. I am connected to the  internet via a Linksys wireless router. I have installed Apache 2.2.10 on one of my Ubuntu laptop.  I have not yet configured the with a logical ServerName so when I start Apache it starts on 127.0.1.1 with an appropriate warning.

I can bring up the browser on this laptop and just type in:

[http://127.0.1.1](http://127.0.1.1) and it displays the It Works! message.

I can bring up the browser on the other Ubuntu Laptop and type in:

[http://192.168.1.104](http://192.168.1.104) and it again displays It Works.  192.168.1.104 is my laptop's IP address which is running Apache.

Now, when I try to do the same thing from my Windows machine, it fails to bring up the It Works page.  I tried pinging the IP address 192.168.1.104 of my Ubuntu laptop running Apache from the Ubuntu client and Windows XP client, Ubuntu client immediately connects and responds whereas Windows client does not.

My questions are:

1.  Why is Windows having a hard time just pinging other computers on the network?  Whereas Ubuntu clients do not.

2.  Is there an easy setup that I can follow to create a private testing network using a fully qualified domain name for my Ubuntu laptop acting as a server without having to get an actual DNS name and expose the machine to the Internet as a server?

Thanks in advance for your time.

Bharat

---

### Post by cdenley on 2008-10-22
Can the windows computer connect to anything? Are you sure it is working?

---

### Post by bruparel on 2008-10-22
> **cdenley said:**
> Can the windows computer connect to anything? Are you sure it is working?

Yes.  The windows machine goes out to the Internet fine.  I can browse all publicly accessible sites and the company intranet sites too (I am connected to the company VPN using an access key).  Is there a setting in windows that is preventing me from seeing my own little network behind my linksys router?

---

### Post by cariboo on 2008-10-22
I have seen it where a vpn has been set up in windows and that is then the only interface that is available, to make it usable you have to disable the vpn.

Jim

---

### Post by bruparel on 2008-10-23
Thanks Jim.  You were right.  I tested my Windows machine without starting the VPN and things work.

Now if someone can help me with the second question that I originally posted that is; how to setup Apache for an internal network where I do not have a DNS. I am not an Apache expert so any help in this will be appreciated.

Bharat

---

### Post by Seq on 2008-10-23
Now that you have communication between hosts, if you just want name resolution (and your router does not provide this) you could install Apple Bonjour on your windows machine, and use the .local domain addresses ($HOSTNAME.local).

You could get into all sorts of fancy bind stuff and set up an internal DNS, but it may just suit your needs to let avahi and bonjour do the work.

---

### Post by cdenley on 2008-10-23
Or you can just edit the hosts file on each client.

in linux: /etc/hosts
in windows: c:\windows\system32\drivers\etc\hosts

---

### Post by bruparel on 2008-10-23
> **Seq said:**
> Now that you have communication between hosts, if you just want name resolution (and your router does not provide this) you could install Apple Bonjour on your windows machine, and use the .local domain addresses ($HOSTNAME.local).

You could get into all sorts of fancy bind stuff and set up an internal DNS, but it may just suit your needs to let avahi and bonjour do the work.

Thanks.  I looked up information on Avahi.  It is already running on both my laptops and allows me to refer to each machine as $HOSTNAME.local.  I guess I need Apple Bonjour for my Windows machine to talk to Ubuntu laptops?

Are there any easy to use references that you are aware of?

Regards,

Bharat

---

### Post by bruparel on 2008-10-23
> **cdenley said:**
> Or you can just edit the hosts file on each client.

in linux: /etc/hosts
in windows: c:\windows\system32\drivers\etc\hosts

Can you please give some examples?

Thanks.

Bharat

---

### Post by Seq on 2008-10-23
> **bruparel said:**
> Thanks.  I looked up information on Avahi.  It is already running on both my laptops and allows me to refer to each machine as $HOSTNAME.local.  I guess I need Apple Bonjour for my Windows machine to talk to Ubuntu laptops?

Are there any easy to use references that you are aware of?

Regards,

Bharat

Download Bonjour for Windows from apple's site, install (and probably reboot), and $HOSTNAME.local works on windows too. It's designed to not be hard :)

---

### Post by cdenley on 2008-10-23
> **bruparel said:**
> Can you please give some examples?

Thanks.

Bharat
this easy format
```

myip hostname1 hostname2 hostname3...

```
some examples
```

192.168.0.30 macserver
192.168.0.2 ubuntu myserver.com www.myserver.com

```
There should already be examples in your hosts files. Can't get much easier than that.

---

### Post by bruparel on 2008-10-24
> **cdenley said:**
> this easy format
```

myip hostname1 hostname2 hostname3...

```
some examples
```

192.168.0.30 macserver
192.168.0.2 ubuntu myserver.com www.myserver.com

```
There should already be examples in your hosts files. Can't get much easier than that.

Thank you everyone for your patient help, I sincerely appreciate it.  I am beginning to realize that I do not understand the basic interaction of Apache with /etc/hosts at this point, so pardon the naive questions.

I have been trying to get a ruby on rails application run in my home network environment amongst my two Ubuntu laptops and one Windows machine using Apache modrails (a.k.a Passenger).  I have succeeded in doing so this morning (well almost).  But this has left open just as many questions.  Here is my /etc/hosts file:

127.0.0.1       localhost
127.0.1.1       bharatUbuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
root@bharatUbuntu:/usr/local/apache2/bin# 

Now Ubuntu created the second line during installation which reads
127.0.1.1       bharatUbuntu
Up until now, I have been using these laptops primarily as clients and therefore I did not have to pay much attention to these files.  Now that I am trying to turn one of them in a server, these questions have come up.  I have installed Apache in /usr/local/Apache2 directory and I built it from the sources.  Here is the Virtual Host file that gets included into the httpd.conf:

<VirtualHost *:80>
   ServerName 192.168.1.104
   DocumentRoot /var/www/apps/learningrails/current/public
   <Directory  "/var/www/apps/learningrails/current/public">
      Options FollowSymLinks
      AllowOverride None
      Order allow,deny
      Allow from all
   </Directory>
</VirtualHost>
root@bharatUbuntu:/usr/local/apache2/conf/apps# 

This is the bottom of the httpd.conf file where the virtual host gets included:

<IfModule ssl_module>
SSLRandomSeed startup builtin
SSLRandomSeed connect builtin
</IfModule>

NameVirtualHost *:80
Include conf/apps/

Now when I start Apache, I get the following message:

root@bharatUbuntu:/usr/local/apache2/bin# ./apachectl start
httpd: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
root@bharatUbuntu:/usr/local/apache2/bin# 

Q1.  Why is Apache starting on 127.0.1.1?

Also, please advise on creating a simple and usable set of entries in my /etc/hosts file and the virtualhost that I have defined.

Right now, I am working with IP addresses but would like to ideally use the $HOSTNAME.local logical name that Avahi provides.  But I am willing to take baby steps.  I am trying to understand the interaction of Apache Virtual Hosts with /etc/hosts at this point so that I can leverage that knowledge in my Ruby on Rails work with Phusion Passenger.

Sorry for the long post and thanks again in advance.

Bharat

---

### Post by cdenley on 2008-10-24
If you don't mind using hostname.local, then maybe you should try bonjour. I never tried it. Usually people want to use real hostnames which they will use once the server is put on the internet.

The /etc/hosts file is used in linux and windows to resolve hostnames. Before your computer queries your DNS server to determine the correct IP address for a given hostname, it checks to see if there is an entry for that hostname in /etc/hosts. If there is, it uses that for name resolution instead.

If you want a client to try connecting to your server's IP address when you enter a specific hostname in a web browser, you must have an entry for that hostname in the hosts file on that client.

As far as the server goes, I don't think that warning message is something to be concerned about. If you want to set the hostname apache looks for...

Edit the file /etc/hosts:
```

myhostname.com

```

Run the command:
```

sudo hostname myhostname.com

```

configure the servername for your default site
```

ServerName myhostname.com

```

You must use a fully qualified domain name, such as "mysite.net" or "myserver.com". Also, it must resolve to a LAN IP your server is listening on. This means you will probably have to edit /etc/hosts on the server.
```

192.168.1.104 myhostname.com

```

---

### Post by Seq on 2008-10-24
> **bruparel said:**
> Q1.  Why is Apache starting on 127.0.1.1?

Also, please advise on creating a simple and usable set of entries in my /etc/hosts file and the virtualhost that I have defined.


Well it is probably using 127.0.1.1 as that is what it finds in your hosts file that matches your hostname. The error it is finding is that it can't find a FQDN (mymachine.mydomain.com versus just mymachine).

Also, the error you posted doesn't say it is only binding 127.0.1.1, but that it is using that as it's servername. It sounds like from your previous posts that it still binds to all external addresses. It's just apache doesn't know it's proper name. You can set it's name in the apache config file if you want (mymachine.local)

To be honest, I never touch hosts file that often. The problem is that you will have to keep all clients up to date if anything changes. And if you want clients to be resolvable by name, then you need to avoid using DHCP for network addresses.. DNS was invented because of issues with the hosts file.

> **bruparel said:**
> Right now, I am working with IP addresses but would like to ideally use the $HOSTNAME.local logical name that Avahi provides.  But I am willing to take baby steps.  I am trying to understand the interaction of Apache Virtual Hosts with /etc/hosts at this point so that I can leverage that knowledge in my Ruby on Rails work with Phusion Passenger.

$HOSTNAME.local should automatically work between Ubuntu hosts. Have you tried it yet? Just try ping mymachine.local.

---

### Post by bruparel on 2008-10-24
"$HOSTNAME.local should automatically work between Ubuntu hosts. Have you tried it yet? Just try ping mymachine.local."

It works exceedingly well.  Thank you both gentlemen.  This discussion is immensely useful to me since I am moving towards setting up a number of named virtual hosts so that one instance of Apache can host multiple Ruby on Rails sites using Passenger.

---

