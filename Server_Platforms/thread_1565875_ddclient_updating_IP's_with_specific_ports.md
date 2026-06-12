---
title: "ddclient updating IP's with specific ports"
date: 2010-09-01
forum: Server Platforms
---

### Post by glueball on 2010-09-01
I've got ddclient setup and working well.  I check my ip address on the web and use that to update my dns services provider.  However, I'd like to add a second domain name at the same IP, but on a different port.  So what I currently have is this:
CPU1.mydomain.com -> My IP -> CPU1
What I want is it to go to the web to find that my IP is 1.2.3.4, but  update my DNS service provider with 1.2.3.4:5, where 5 is some predefined  port number that I've had forwarded to the desired CPU by my router:
CPU1.mydomain.com -> My IP : Port 1 -> CPU1
CPU2.mydomain.com -> My IP : Port 2 -> CPU2

This would save me from having to specify a nonstandard port every time I connect to the machines.  The DNS sever would automatically direct me to the proper port.  The problem is that I can't find a way in ddclient to add a port number to the end of the IP address it finds on the web.  Anyone have any ideas on how I can do this?

Here is my full .etc.ddclient.conf:

daemon=300
pid=var/run/ddclient.pid
use=web, web=checkip.dyndns.org/
server=mydnsserver.com
login=mydnslogin
password='mydnspassword'
CPU1.mydomain.com, CPU1.mydomain.com

---

### Post by arrrghhh on 2010-09-01
You'll have to setup a vhost, you can't have dyndns forward based on a port number.  It fowards your ENTIRE IP - so every port.

So look at the [vhost doc](http://httpd.apache.org/docs/2.2/vhosts/) from apache.

---

### Post by glueball on 2010-09-01
I see, that's unfortunate.  I'm actually just trying to setup an address for the machines so I can ssh into them individually, without having to specify the ports manually. I don't want an http server or anything.  Either machine could be off, so I can't route the traffic once it arrives at one of the machines.  I guess there is no way to conveniently do this.

---

### Post by Bachstelze on 2010-09-01
> **glueball said:**
> I see, that's unfortunate.  I'm actually just trying to setup an address for the machines so I can ssh into them individually, without having to specify the ports manually. I don't want an http server or anything.  Either machine could be off, so I can't route the traffic once it arrives at one of the machines.  I guess there is no way to conveniently do this.

IPv6 yo. If your ISP doesn't offer it, send them an angry email telling them this is 2010. ;)

---

### Post by BkkBonanza on 2010-09-01
DNS doesn't resolve to port values at all, and ssh protocol, as far as I know, only communicates with IP values, not hostnames - so there would be no way to do this. 

What you need is called a "reverse proxy" with ssh support but if ssh doesn't pass hostname as part of it's protocol (which could be researched in more detail as I'm not entirely sure) then it would be impossible for any proxy to differentiate the intended final target.

Reverse proxies work for http/email because they do pass the hostname in the protocol.

If you just want to not type the port # then make a couple aliases that slip it in for you. eg.

alias ssh1='ssh -p 2345'
alias ssh2='ssh -p 5432'

ssh1 joe@bubgle

Or script it in.

---

### Post by Bachstelze on 2010-09-01
> **BkkBonaza said:**
> 
If you just want to not type the port # then make a couple aliases that slip it in for you. eg.

alias ssh1='ssh -p 2345'
alias ssh2='ssh -p 5432'

ssh1 joe@bubgle

Or script it in.

Or even better, put it in ~/.ssh/config, that's what it's for.

---

