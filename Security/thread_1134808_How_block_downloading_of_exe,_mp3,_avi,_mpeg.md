---
title: "How block downloading of exe, mp3, avi, mpeg"
date: 2009-04-23
forum: Security
---

### Post by cheesewizz on 2009-04-23
Hello
I am newbie in linux
I setup ubuntu as my internet proxy server
i used webmin for gui 
i installed squid proxy

and its works fine now i used ip address: 192.168.1.1 and port : 8888

actually i found a tutorial but its not working to my proxy
[http://www.cyberciti.biz/faq/squid-content-filter-block-files/](http://www.cyberciti.biz/faq/squid-content-filter-block-files/)

still i can able to download 

please anybody can help me


thanks

---

### Post by bodhi.zazen on 2009-04-24
You need to use a proxy, squid, dansguardian, etc. 

If it not working, it is not configured properly. We need to know more about your exact configuration.

The squid conf file is very very very large, do not even *think* of posting that here, no one will read it looking for your edits :lolflag:

You need to tell us what you have done and post the Relevant lines from your config file.

---

### Post by cheesewizz on 2009-04-24
Here is the squid.conf:

first is i change this:

#  TAG: visible_hostname 192.168.1.0
#	If you want to present a special hostname in error messages, etc,
#	define this.  Otherwise, the return value of gethostname()
#	will be used. If you have multiple caches in a cluster and
#	get errors about IP-forwarding you must set them to have individual
#	names with this setting.
#
#Default:
[COLOR="Red"]visible_hostname rsumook-desktop[/COLOR]


on the ACL Section

I put like this:

#Recommended minimum configuration:
[COLOR="Red"]acl all src 192.168.1.100[/COLOR]
[COLOR="Red"]acl happy src 192.168.1.158[/COLOR]
[COLOR="Red"]acl blockfiles urlpath_regex "/etc/squid/block.files.acl"[/COLOR]
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443
acl SSL_ports port 563 # https
acl SSL_ports port 873 # snews
acl Safe_ports port 80 # rsync
acl Safe_ports port 21 # http
acl Safe_ports port 443 # ftp
acl Safe_ports port 70 # https
acl Safe_ports port 210 # gopher
acl Safe_ports port 1025-65535 # wais
acl Safe_ports port 280 # unregistered ports
acl Safe_ports port 488 # http-mgmt
acl Safe_ports port 591 # gss-http
acl Safe_ports port 777 # filemaker
acl Safe_ports port 631 # multiling http
acl Safe_ports port 873 # cups
acl Safe_ports port 901 # rsync
acl purge method PURGE # SWAT
acl CONNECT method CONNECT
acl QUERY urlpath_regex cgi-bin \?


on the HTTP_ACCESS

I put like this:

#Default:
#http_access deny all 
[COLOR="Red"]deny_info ERR_BLOCKED_FILES blockfiles[/COLOR]
[COLOR="Red"]http_access deny blockfiles[/COLOR]
#Recommended minimum configuration:
#
# Only allow cachemgr access from localhost
http_access allow manager localhost
[COLOR="Red"]http_access allow all [/COLOR]
[COLOR="Red"]http_access allow happy[/COLOR]
# Only allow purge requests from localhost
http_access deny manager
# Deny requests to unknown ports
http_access allow purge localhost
# Deny CONNECT to other than SSL ports
http_access deny purge


all with red colors means i update the squid.conf



thanks

---

### Post by bodhi.zazen on 2009-04-24
what is in the your "ERR_BLOCKED_FILES" file ?

what is in "/etc/squid/blocks.files.acl" ?

---

### Post by cheesewizz on 2009-04-25
hello thanks for your reply

actually i just follow the instruction that i found here [http://www.cyberciti.biz/faq/squid-content-filter-block-files/](http://www.cyberciti.biz/faq/squid-content-filter-block-files/)


about this: "ERR_BLOCKED_FILES" file
to display custom error message when a file is blocked

Create custom error message HTML file called ERR_BLOCKED_FILES in /etc/squid/error/ directory or /usr/share/squid/errors/English directory.

something like this:
<HTML>
<HEAD>
<TITLE>ERROR: Blocked file content</TITLE>
</HEAD>
<BODY>
<H1>File is blocked due to new IT policy</H1>
<p>Please contact helpdesk for more information:</p>
Phone: 555-12435 (ext 44)<br>
Email: [email]helpdesk@yourcorp.com[/email]<br>


and for this one: squid/blocks.files.acl
i just add this add to the following lines to your squid ACL section:
acl blockfiles urlpath_regex "/etc/squid/blocks.files.acl"

and here is the content:

\.[Ee][Xx][Ee]$
\.[Aa][Vv][Ii]$
\.[Mm][Pp][Gg]$
\.[Mm][Pp][Ee][Gg]$
\.[Mm][Pp]3$

thanks

---

### Post by sej7278 on 2009-04-29
you can do it on the firewall too apparently.....

iptables -A FORWARD -m string --string '.exe' -j DROP

---

### Post by karthick87 on 2010-06-23
> **sej7278 said:**
> you can do it on the firewall too apparently.....

iptables -A FORWARD -m string --string '.exe' -j DROP

Tried the above command,

```
karthick@Ubuntu-desktop:~$ iptables -A FORWARD -m string --string '.exe' -j DROPCould not determine whether revision 1 is supported, assuming it is.
iptables v1.4.4: STRING match: You must specify `--algo'
Try `iptables -h' or 'iptables --help' for more information.

```

---

### Post by bodhi.zazen on 2010-06-23
> **getyourkarthick said:**
> Tried the above command,

```
karthick@Ubuntu-desktop:~$ iptables -A FORWARD -m string --string '.exe' -j DROPCould not determine whether revision 1 is supported, assuming it is.
iptables v1.4.4: STRING match: You must specify `--algo'
Try `iptables -h' or 'iptables --help' for more information.

```

I think you need to add --algo bm

```
iptables -A FORWARD -m string --string --algo bm '.exe' -j DROP
```

---

### Post by bodhi.zazen on 2010-06-23
> **getyourkarthick said:**
> Tried the above command,

```
karthick@Ubuntu-desktop:~$ iptables -A FORWARD -m string --string '.exe' -j DROPCould not determine whether revision 1 is supported, assuming it is.
iptables v1.4.4: STRING match: You must specify `--algo'
Try `iptables -h' or 'iptables --help' for more information.

```

Also, if you are wanting to add this rule on a Desktop, not a router, you probably want to use INPUT rather then FORWARDING.

Keep in mind, to some extent you are hijacking another's thread and the OP is asking about squid and, I assume, using squid on a router of some kind (or gateway).

---

