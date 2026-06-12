---
title: "hosts.deny All: All ?"
date: 2011-05-16
forum: Security
---

### Post by Phil Stone on 2011-05-16
Hi,

Just looking to blanket deny everything and then allow exterior connections on a per connection basis. Note - In case you now have to collect your spleen off the floor this is more out of curiosity about working process of hosts and security in general rather than for practical reasons :)

I thought I would be able to add All: All to my hosts.deny file but maybe i'm confusing setting up server with the os runtime environment (?) as source shows the command All: ALL as 'unfound' - and doesn't light up Tan in emacs. 

so far in forums I have found lists of example hosts.deny files but not any blanket solutions. Any suggested reading or comments pls? 

PS

---

### Post by Lars Noodén on 2011-05-16
> **Phil Stone said:**
> I thought I would be able to add All: All to my hosts.deny file but maybe i'm confusing setting up server with the os runtime environment (?)

This is also called tcpwrappers.  Not all services are compiled to be tcpd-aware, but many are.

If you are running tcpd-aware servers, then having ALL: ALL in /etc/hosts.deny will block everyone, including yourself.

---

### Post by bodhi.zazen on 2011-05-16
> **Phil Stone said:**
> Hi,

Just looking to blanket deny everything and then allow exterior connections on a per connection basis. Note - In case you now have to collect your spleen off the floor this is more out of curiosity about working process of hosts and security in general rather than for practical reasons :)

I thought I would be able to add All: All to my hosts.deny file but maybe i'm confusing setting up server with the os runtime environment (?) as source shows the command All: ALL as 'unfound' - and doesn't light up Tan in emacs. 

so far in forums I have found lists of example hosts.deny files but not any blanket solutions. Any suggested reading or comments pls? 

PS

What servers are you running and what makes you feel you need anything more then

```
sudo ufw enable
```

See the security sticky.

---

### Post by Phil Stone on 2011-05-17
*. may be solved now: Ah. - I just read the hosts.deny prompts again - maybe it is I should be using "ALL  EXCEPT:" to allow specific access while blocking everything else.   
Better rtm re hosts-access and options. sz.
.*

I have been looking at the security stickies - there is a bit to get my  head around in there, Apparmour looks a good place to start though.  
 
I am not actually running any live servers - not just yet (to the  world's advantage heheh). But I have made the apache2 install so as to  have a local test server for website fun rather than using the live  sites. Originally I installed the msi on windows before realising it  would be better overall to switch into linux for a more rounded  understanding. 
 
Here I am not querying how to control access at a server level rather  how to control access at a local pc lecvel. Hence the local/server  confusion theory.  
//please bear with me i am finding out stuff as i go - it now appears  there are only hosts files in etc and not in httpd folders as well.  Previously I thought there were two sets - but think i was getting  confused with httpd.conf file please see below.
 
So, the hosts file controls access at tcp level. I will look into tcpwrappers and see if I can further that line of knowledge. 
 
I seem to recall documentation when setting up the server that I  followed which pertained to hosts files in the httpd programs. I was to  enter All: All to deny all access - so I  couldn't call the 'It Works'  page. But the hosts.deny file in my local programs doesn't appear to  allow this. When I type the command source $ deny.hosts to refresh the  code I am told 'ALL: ALL is not recognised'.  Now I can only find hosts  files in my etc directory and nowhere else (ie httpd directories)
 
Ah. - I just read the deny prompts - maybe it is I should be using "ALL  EXCEPT:" to allow specific access while blocking everything else.  

within my httpd.conf file I have Listen set as

Listen: 80

and no Servername set - this prompts when starting apachectl saying no  servername found but works anyway so i did not pay too much attention to  it. (guessing -this perhaps sends out to use a virtualhost.)

should the Servername be set to 127.0.0.1 / 127.0.1.1 as per my IP local address in the hosts file?



my hosts files are as below
 
hosts file: in /etc/
 
127.0.0.1    localhost
127.0.1.1    my-computer

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

hosts.deny in /etc/  // note my attempt at ALL marker - i also switched paranoid on.

# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
  ALL: ALL  // my recent attempt to input ALL: ALL
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
  ALL: PARANOID

hosts.allow:

# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#

---

### Post by bodhi.zazen on 2011-05-17
First, understand that running apache is somewhat different from other servers.

Is it a public server ? Then you will want to allow all and deny only those who are a problem (blacklist).

This is just the opposite of a ssh server, where you do not want public access, so you will deny all, and allow a few (whitelist).

Second, apache does not use TCPWrapper (hosts.deny).

See:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

[http://blog.bodhizazen.net/linux/how-to-blacklist-an-ip-address-in-apache/](http://blog.bodhizazen.net/linux/how-to-blacklist-an-ip-address-in-apache/)

You might also want to look at mod_evasive and mod_security

---

### Post by SeijiSensei on 2011-05-17
In Apache, you use the Order and Deny/Allow directives to control access to virtual hosts and directories.

---

### Post by Phil Stone on 2011-05-18
This has made things clearer for me now, thanks I'll get into looking at those links.

---

