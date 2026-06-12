---
title: "apache2 restart FQDN  issue - don't know how to trace"
date: 2008-02-13
forum: Server Platforms
---

### Post by Gordster on 2008-02-13
Hi all,

I have just started using linux - ubuntu specifically - and I'm loving it!!!  
(learned Unix basic's and bash scripting in Univ.)  It installs so easily, and once I 're-familiarized' myself with the command line - all is good.  

Sort of  :-)

Here's the config:
Ubuntu 7.10 Host - running VMWare server 1.0.4 (all seems to be working fine)

1 Ubuntu 7.10 Virtual Machine running Oralce XE (working)
1 Ubuntu 7.10 Virtual Machine running Apache2 / PHP 5
- this one is 'working' in that I can get to the default apache page,
but I get the error when I start / restart apache

apache2: Could not reliably determine the server's fully qualified domain name using My.External.IP.Addy for ServerName

And it show's up twice before I get the [ OK ] and a command prompt again.

I had followed the tutorial for setting up Apache from the forum, and I copied the /etc/apache2/sites-available/default to 3 new files(yes - I did give them all different names  :-p).  I configured one of the copies for my domain, but I never did a a2ensite on it.  I did make a change the the apache2.conf file (after making a copy - apache2.conf.orig - in the same directory) - setting ServerTokens to Prod.

I restarted apache (sudo /etc/init.d/apache2 restart) and that's when the warning started...

So I copied the apache.conf.orig back over the apache.conf file and restarted apache - same warning.  I deleted the 3 copies I made of sites-available/default and restarted - same warning...

Checked my /etc/hosts file - only entry (other than the IPv6 stuff) is:
127.0.0.1      Localhost

My httpd.conf is empty too.
ports.conf lists defaults (80 and and 'IfModule mod_ssl.c' for SSL block)
'apache2ctl configtest'  also shows the warning + syntax OK

I do have 3 other directories in /var/www/ - 1 for each 'default' copy I wanted to test - as well as 'apache2-default' - but that wouldn't make a difference - would it?

Any thought's or troubleshooting tips would be greatly appreciated.

Corey

---

### Post by faulkes on 2008-02-13
> **Gordster said:**
> 
apache2: Could not reliably determine the server's fully qualified domain name using My.External.IP.Addy for ServerName


Look through the apache2.conf file or the sites-enabled files for the value called 

```

ServerName

```

The text My.External.IP.Addy should be there, change this to the IP address of your linux server.

Faulkes

---

### Post by Gordster on 2008-02-13
Thank you for the reply Faulkes, but

>  My.External.IP.Addy 

is of course not really the IP Address given - rather I chose to change it to protect my network...

And I have searched all of the mentioned files for any instance of 'ServerName' (in any case) - and can't find one???  So that's why I'm lookiing for a way to troubleshoot where this is coming from - because I can't seem to find any reference to ServerName in apache anywhere.  Maybe that is the issue - I don't have it listed anywhere (un-commented that is)...

Thanks again,

Corey

---

### Post by faulkes on 2008-02-13
try adding 

```

My.Eth0.IP.Address myhostname myhostname.mydomainname.com

i.e.
200.1.2.3 uberubuntuserver uberubuntuserver.mydomain.com

```

to /etc/hosts
Edit: I had /etc/aliases here, it's late, I'm tired ;) it is now fixed.
Faulkes

---

### Post by Gordster on 2008-02-14
Thanks again Faulkes - especially so late at night - but no go  :-(.

Here's the interesting part - prior to the change (now using my eth0 IP - inside my network) in the hosts file has changed the warning to the internal side IP.  As before that it was the 'external IP'.

So - I get the same 'apache2: could not ... FQDN, using "
but now it's "My.Internal.IP.Address for ServerName"
not "My.External.IP.Address" 
- and I still don't know where it was getting the external IP to begin with...

Corey

---

### Post by faulkes on 2008-02-14
Alright, a bit of confusion here;

You say you set it to use your "External" IP, is this the IP of your router? or does the linux machine have multiple ethernet interfaces? or are you talking about the VM IP?  iirc apache by default will listen on all interfaces that exist when it starts (specific to the machine starting the httpd daemon).

So, first things first, you should only ever deal with the interfaces that exist on the machine itself and not anything external to it (even if you port forwarded from your router).

Do you have a domain name for the server? (you don't need to tell me what it is, just if you have one).

If you do have one, has DNS been configured for it?

Check /etc/host.conf to make sure that the system knows to look at the host file first.

```

# The "order" line is only used by old versions of the C library.
order hosts,bind
multi on

```

Lastly, we may want to check the apache2.conf and the sites-enabled/* files, or at least one of them.  Attach them here in a redacted form as you need.

Thanks,

Faulkes

---

### Post by Gordster on 2008-02-14
Sorry for the confusion...

I added a line in /etc/hosts to include the IP address of eth0 (my internal address).

: for /etc/hosts
```

127.0.0.1   Localhost
10.0.0.1     MyApache
...  Then all the IPv6 stuff

```

Before I added that line - the warning showed my external IP (the outside interface of my router).  After adding in the line for eth0 IP address - the warning changed to so my internal IP (eth0).  I never put my external IP anywhere - which is why I was confused.

I do have 3 'domains' I want to host - and they are pointed to my external IP - but I have not configured the router to allow traffic through (this is a long story - I did have them working - but had to change my hardware / OS's to meet my needs, so I removed the router rules - and will put them back once I have everything configured and secured again).

/etc/host.conf  looks identical to what you posted.

I'm not sure if I have a domain name set up for this machine (I am pretty sure I don't - but I don't know how to tell).  Is it just having server.domain.ca in the hostname?

And apache2.conf is unchanged, as is /etc/apache2/sites-available/default.  I would attach them - but not 100% sure on how to get them off the VM and somewhere I can attach them from.  I haven't set up samba or ssh on this vm.  I will look into how I can do it and post them once I do.

Many thanks Faulkes for your assistance - it is greatly appreciated.

Corey

---

### Post by faulkes on 2008-02-14
> **Gordster said:**
> Sorry for the confusion...

I do have 3 'domains' I want to host - and they are pointed to my external IP - but I have not configured the router to allow traffic through (this is a long story - I did have them working - but had to change my hardware / OS's to meet my needs, so I removed the router rules - and will put them back once I have everything configured and secured again).

Corey

Ok, lets recap,

You have

linux server 
Oracle VM (linux)
Apache VM (linux)

I am assuming that all domains / sites are being configured in the Apache VM.

The expected setup from what you have written is that you will be using name based virtual hosts and access provided via port forwarding from the router.

Each site which is configured, will need to have a ServerName added to it, i.e. for the default site, the secondary and the tertiary.

ServerName [www.domain0.ca](www.domain0.ca)
ServerName [www..domain1.ca](www..domain1.ca)
ServerName [www.domain2.ca](www.domain2.ca)

(note that each line goes into it's specific site configuration file.)

The ServerName variable has to be there when you are using multiple sites with name based virtualization.

In /etc/hosts, you want to add lines for each of these sites, even though they will be using the same ip

<Apache VM IP>  myapache0 [www.domain0.ca](www.domain0.ca)
<Apache VM IP>  myapache1 [www.domain1.ca](www.domain1.ca)
<Apache VM IP>  myapache2 [www.domain2.ca](www.domain2.ca)

You also want to ensure that the sites you created are enabled, typically via the 

```

sudo a2ensite <site configuration file name>

-note the the config file has to be in the sites-available directory, 
not the sites-enabled.  a2ensite will create the link to that for you.

```

Also, reading the Server Guide for Apache may get your more comfortable with 
some of the configuration, you can find it at [https://help.ubuntu.com/7.10/server/C/httpd.html](https://help.ubuntu.com/7.10/server/C/httpd.html)

Faulkes

---

### Post by Gordster on 2008-02-14
Hi Faulkes,

> I am assuming that all domains / sites are being configured in the Apache VM.

The expected setup from what you have written is that you will be using name based virtual hosts and access provided via port forwarding from the router.
Correct.  And that was what I was attempting when the warning started - even though I had not yet enabled a site - other than the default that was enabled from install (so I figured that only the 'enabled' site config would be used).  The only thing I had done was to change the ServerTokens to Prod in apache.conf, and made the 3 config files in /etc/apache2/sites-available/ - each with their own name.  After the warning - I put the apache.conf back to the default, and deleted the 3 config files.  Still the same warning.

Now, apache is working - but I just get the warning.  Could this be related to the 'Host' maybe?  Do I need to have an internal DNS server?

And I have read the Apache server guide, and that was what I was trying to follow.

I tried to re-create all 3 again and set up the servername, and added in the 3 lines in /etc/hosts.

Now I get:
> apache2: Could not reliably determine the server's FQDN, using My.Eth0.IP.addy for ServerName
[Thu Feb 14 12:00:46 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Feb 14 12:00:46 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Feb 14 12:00:46 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[ OK ]
One question though - You said:
```
In /etc/hosts, you want to add lines for each of these sites, 
even though they will be using the same ip

<Apache VM IP> myapache0 www.domain0.ca
<Apache VM IP> myapache1 www.domain1.ca
<Apache VM IP> myapache2 www.domain2.ca
```
Do I need 3 instances of apache (myapache0, myapache1, myapache2)?  My understanding was that 'myapache' was the 'hostname' of the server that apache is running on. (set by typing 'hostname myapache' at the command prompt.  Does the entry into /etc/hosts not need that name?
  
Many thanks again!!!  - I'm sure I'm on the right track...

Corey
PS - once I figure out a way to get the config files copied somewhere I can attach from, I will...

---

### Post by faulkes on 2008-02-14
> **Gordster said:**
> Hi Faulkes,

Correct.  And that was what I was attempting when the warning started - even though I had not yet enabled a site - other than the default that was enabled from install (so I figured that only the 'enabled' site config would be used).  The only thing I had done was to change the ServerTokens to Prod in apache.conf, and made the 3 config files in /etc/apache2/sites-available/ - each with their own name.  After the warning - I put the apache.conf back to the default, and deleted the 3 config files.  Still the same warning.


Look to see what exists in the sites-enabled directory.

> 
Now, apache is working - but I just get the warning.  Could this be related to the 'Host' maybe?  Do I need to have an internal DNS server?
Now I get:

One question though - You said:
```
In /etc/hosts, you want to add lines for each of these sites, 
even though they will be using the same ip

<Apache VM IP> myapache0 www.domain0.ca
<Apache VM IP> myapache1 www.domain1.ca
<Apache VM IP> myapache2 www.domain2.ca
```

Do I need 3 instances of apache (myapache0, myapache1, myapache2)?  My understanding was that 'myapache' was the 'hostname' of the server that apache is running on. (set by typing 'hostname myapache' at the command prompt.  Does the entry into /etc/hosts not need that name?


Without DNS setup for the actual domains, all we are doing is telling the local system that these hostnames exist as /etc/hosts is usually checked first before a DNS query is made.

The actual hostname of the VM does not need to appear in /etc/hosts although having it there should not harm anything.  The important thing is that the virtual sites know how to resolve the addresses which belong to them.

The format of /etc/hosts is
```

<IP ADDR>  <short name> <FQDN>

or 

<IP ADDR> <FQDN> <short name>

```

both work.  In the grand scheme of things, the only important part here is that
the FQDN portion is set.

As for the error you are now getting:

> 
apache2: Could not reliably determine the server's FQDN, using My.Eth0.IP.addy for ServerName
[Thu Feb 14 12:00:46 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Feb 14 12:00:46 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Feb 14 12:00:46 2008] [warn] NameVirtualHost *:0 has no VirtualHosts


Look at each of the config files, at the top of each you should see NameVirtualHost and VirtualHost, both of those are set to *

I would change the *'s to match the FQDN of the sites (just the site name, i.e. [www.mydomain2.ca](www.mydomain2.ca) - no http:// or anything).

Faulkes

---

### Post by Gordster on 2008-02-14
Hi Faulkes,

I did the changes you mentioned, but I still get warnings...

```
apache2: Could not reliably determine the server's FQDN, using My.External.IP.Address for ServerName
[Date] [ warn] NameVirtualHost www.MyDomain1.ca:0 has no VirtualHosts
[Date] [ warn] NameVirtualHost www.MyDomain2.ca:0 has no VirtualHosts
[ OK ]
```

I did set up all 3 - so it looks like the first one goes OK, but the second and 3rd have issues.

Should I set up another VM for DNS internally?  I also went to my domain registar and set all the domains to point to my external (static) ip - only had to change 1 - a new one, the others were already pointed there.

Is there a different file I should look for that might be causing this?  Or again - maybe on the Linux Host?

Thanks for everything - I truely appreciate your help...

Corey

---

### Post by faulkes on 2008-02-14
> **Gordster said:**
> Hi Faulkes,

I did the changes you mentioned, but I still get warnings...

```
apache2: Could not reliably determine the server's FQDN, using My.External.IP.Address for ServerName
[Date] [ warn] NameVirtualHost www.MyDomain1.ca:0 has no VirtualHosts
[Date] [ warn] NameVirtualHost www.MyDomain2.ca:0 has no VirtualHosts
[ OK ]
```

I did set up all 3 - so it looks like the first one goes OK, but the second and 3rd have issues.

Should I set up another VM for DNS internally?  I also went to my domain registar and set all the domains to point to my external (static) ip - only had to change 1 - a new one, the others were already pointed there.


I don't think you need an additional VM just for DNS although you can certainly do so.  DNS (BIND) is rather light-weight in resource utilization.

If you told your registrar to point DNS to your external IP, you need to port forward DNS requests internally to where you setup BIND.

Setting up DNS may help but I can't say it will "officially" fix the problem.

Faulkes

---

