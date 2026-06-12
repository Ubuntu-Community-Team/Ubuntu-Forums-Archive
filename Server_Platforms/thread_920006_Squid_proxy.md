---
title: "Squid proxy"
date: 2008-09-14
forum: Server Platforms
---

### Post by Drezard on 2008-09-14
I have set up a squid proxy at home. But, im trying to access it from a remote network (Its better not to ask why... long story) but Im trying to add the lines:

> 
acl WORK_NETWORK src 10.0.0.1/32 
http_access allow WORK_NETWORK


10.0.0.1 is actually an internet address but for this question I dont need to disclose it (or where I work). 

But when using:

> 
/etc/init.d/squid restart


It throws an error on those two lines. 

Is there anything wrong with these lines?

Daniel

---

### Post by RealPSL on 2008-09-16
Those 2 lines should have worked fine. Any chance you could post the error message (without the IP's of course)?

---

### Post by kpatz on 2008-09-16
I just added those exact lines to my squid.conf and got no errors.

Maybe you put them in the wrong place?  I added mine after the line "http_access allow localhost".
> 
#
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS

# Example rule allowing access from your local networks. Adapt
# to list your (internal) IP networks from where browsing should
# be allowed
#acl our_networks src 192.168.1.0/24 192.168.2.0/24
#http_access allow our_networks
http_access allow localhost

[b]acl WORK_NETWORK src 10.0.0.1/32
http_access allow WORK_NETWORK[/b]

# And finally deny all other access to this proxy
http_access deny all

#  TAG: http_access2
Also, you didn't indicate that you put "sudo" before the command to restart squid.

Also, I don't know your exact situation, but if possible you might want to use a ssh tunnel to access your squid.

---

