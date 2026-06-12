---
title: "Is ubuntu server install secure enough ouf of the box?"
date: 2005-09-15
forum: Server Platforms
---

### Post by jlist on 2005-09-15
I don't have much experience with linux servers. 
Is ubuntu server install secure enough ouf of the box?
If not, what do I need to do to secure it?

Is ubuntu a good choice for a production server?

Thanks,
Jack

---

### Post by lao_V on 2005-09-15
Define secure.

Do you consider the following to be insecure (just to name a few)?

[list]
[*]being able to SSH into your server after installation without modifying anything
[*]have all servers (web, mail etc) running after installation
[*]allow remote root login to your server
[*]be able to su -
[/list]then Ubuntu is not for you as all of the above is possible with Ubuntu out of the box.

Try Trustix instead. The most secure and easy to use server I've come accross [b]yet.

[/b]Apart from that as long as you don't do "sudo apt-get upgrade" without knowing what exactly you are upgrading you should be fine with Ubuntu as your production server. This is because on my system apt-get upgrade has broken the linux kernel/image quite a few times.

---

### Post by LordHunter317 on 2005-09-15
[QUOTE=lao_V]Define secure.

Do you consider the following to be insecure (just to name a few)?

[list]
[*]being able to SSH into your server after installation without modifying anything
[*]have all servers (web, mail etc) running after installation
[*]allow remote root login to your server
[*]be able to su -
[/list]then Ubuntu is not for you as all of the above is possible with Ubuntu out of the box.[/quote]Umm, Ubuntu does none of those things out of the box.

You have to explictly take action as user to enable all of those things.  So I don't know what you're talking about.

---

### Post by TheDanMan on 2005-09-15
I run 6 Ubuntu machines as servers.  As far as secure... I have the default openssh setup and today 221.12.29.103 tried to brute force attack me via ssh unseccessfully.

As far as number two poster, ignore him.  Ubuntu doesn't do any of those things out of the box.

---

### Post by jlist on 2005-09-15
Thanks for the replies. I'm from the Windows camp so please bear me with my naive questions.

I find in my testing that by default (I don't know how to enable/disable sshd etc. so I suppose what it does is by default) it does:

- allow ssh in
- allow "sudo -s" as root once I've ssh-ed in.
- su seems to respond but fails with authentication error.

BTW, I read somewhere that ubuntu doesn't have a root user, how come I become root after "sudo -s" but su fails.

Back to security, does ubuntu has a firewall and by default is it enabled? How do I allow ports? And if there is a firewall and the firewall is running, I suppose sshd (port 22) is enabled by default?

Oh, TheDanMan, can you tell me how to check ssh logs?

Thanks
jlist

---

### Post by LordHunter317 on 2005-09-15
[QUOTE=jlist]I find in my testing that by default (I don't know how to enable/disable sshd etc. so I suppose what it does is by default) it does:

- allow ssh in[/quote]You must have done this on your own, as it's not enabled OOB in my Hoary install.

> - allow "sudo -s" as root once I've ssh-ed in.Not as root, but to root.  And yes, it's supposed to.

> BTW, I read somewhere that ubuntu doesn't have a root user, how come I become root after "sudo -s" but su fails.Because it does have a root user, you just can't login directly.  But you can use sudo to elevate privileges.

[quote[Back to security, does ubuntu has a firewall and by default is it enabled?[/quote]Yes and no, because there is no need.  No publically accesible services run by default.

---

### Post by lao_V on 2005-09-16
[QUOTE=TheDanMan]I run 6 Ubuntu machines as servers.  As far as secure... I have the default openssh setup and today 221.12.29.103 tried to brute force attack me via ssh unseccessfully.

As far as number two poster, ignore him.  Ubuntu doesn't do any of those things out of the box.[/QUOTE]

TheDanMan, the IP you've quoted is public and I'm assuming you have set up your 6 Ubuntu servers in a LAN via a router? So unless the server you're trying to access is in DMZ or you've directed port 22 to your server how do you expect to access it?

Also sudo -s is similar to su - in that your user account can gain root access. This is done be default in Ubuntu and can be considered a security risk on a public server.

I agree root is disabled in Ubuntu by default but once you enable root you **can** login as root via SSH because in sshd_config the parameter "Permitrootlogin" is set to yes.

Anyway, I will contest anyone who says you can't SSH into your Hoary Ubuntu server out of the box. And I'm not sure how you can trust me but once I get home in the evening, I will be doing a fresh server install and demonstrate to you that by default ubuntu has sshd running and as such there is nothing stopping you from logging into your server as yourself and gaining root privileges.

---

### Post by TheDanMan on 2005-09-16
Those six machines all have public IPs themselves.  Now, I installed ubuntu server two days ago and no SSH is not installed by default.  I had to explicitly issue apt-get install openssh.

---

### Post by jlist on 2005-09-16
I might have apt-get sshd. I don't remember exactly what I did when I installed it :razz: 

Regarding firewall, if I understand LordHunter317 correct, there is no firewall installed by default? If I want to install a firewall, what should I apt-get? (I will be running some services - that's what a server is for ) :)

---

### Post by LordHunter317 on 2005-09-16
[QUOTE=lao_V]This is done be default in Ubuntu and can be considered a security risk on a public server.[/quote]Hoary limits it to only a specific class of users, so it's not really a security risk, unless you hand out administrative access to someone you don't trust.

>  And I'm not sure how you can trust me but once I get home in the evening, I will be doing a fresh server installAhh, I guess this wasn't clear.  I don't know about the server install, I don't run it anywhere.  The regular install certainly doesn't, however.

> such there is nothing stopping you from logging into your server as yourself and gaining root privileges.There's nothing stopping you from doing this on the console so it's just not a security problem.  It's something that must occur for the system to function.


[quote=jlist]Regarding firewall, if I understand LordHunter317 correct, there is no firewall installed by default?[/quote]Oh, it's there, there are just no rules.

You could install a GUI tool to generate rules like firestarter, but they all suck, IMNSHO.  I really recommend you read the basic netfilter documentation at [www.netfilter.org](www.netfilter.org), or post here with your specific requirements and I'd be happy to help you architect a firewall specific to your needs.

---

### Post by lao_V on 2005-09-16
/me starts to beat himself with a large shame stick and welcomes anyone else to do the same.

Ok, just done a fresh server install and ssh server is not installed by default.

I sincerely apologise for my earlier comment regarding this.

/me starts to disappear

---

### Post by jlist on 2005-09-16
[QUOTE=LordHunter317]Oh, it's there, there are just no rules..[/QUOTE]
Yes, I found iptables installed.

[QUOTE=LordHunter317]You could install a GUI tool to generate rules like firestarter, but they all suck, IMNSHO.  I really recommend you read the basic netfilter documentation at [www.netfilter.org](www.netfilter.org), or post here with your specific requirements and I'd be happy to help you architect a firewall specific to your needs.[/QUOTE]
When you say GUI tool you mean X-Window tool? I did a server install and it doesn't have X Window...

It'll be great if you can help me create the initial firewall setup. I think I'll be running a dns server, sshd, a web server (lighttpd or Apache, maybe both,) mysql(does mysql need to open a port or should I be tunneling the client-server connection through ssh?)

And I suppose out going packets will not be filtered? Because I'll also be using some client side software such as wget, dns lookup, etc.

Thanks!

---

### Post by LordHunter317 on 2005-09-16
[QUOTE=jlist]When you say GUI tool you mean X-Window tool? I did a server install and it doesn't have X Window...[/quote]Some of them require X-Windows, but not all of them.  Some will run on the command line.

> I think I'll be running a dns server,I'd assume this is for internal services.

> mysql(does mysql need to open a port or should I be tunneling the client-server connection through ssh?)MySQL can use TCP/IP sockets, but you won't use them unless your client is on a different box.

> And I suppose out going packets will not be filtered?It could be, but unless this is going in a co-lo or something, it is pointless to do so.

I'll post rules later tonite or tomorrow.

---

### Post by jlist on 2005-09-17
[QUOTE=LordHunter317]Some of them require X-Windows, but not all of them.  Some will run on the command line.[/QUOTE]

Do you have some command line iptable config tools to recommend?

[QUOTE=LordHunter317]I'd assume this is for internal services.[/QUOTE]

Actually, it'll be on internet for external domains.

[QUOTE=LordHunter317]MySQL can use TCP/IP sockets, but you won't use them unless your client is on a different box.[/QUOTE]

I'm thinking of allow the port so that I can use GUI tools to configure the server. The question is, is it secure enough to open that port, or should I create ssh tunnels?

[QUOTE=LordHunter317]I'll post rules later tonite or tomorrow.[/QUOTE]
That'll be great. Appreciate it!

---

### Post by GTvulse on 2005-09-17
[QUOTE=jlist]Do you have some command line iptable config tools to recommend?
[/QUOTE]

Shorewall is available in the main repository (that is, it is supported) and doesn't require a GUI.

---

### Post by LordHunter317 on 2005-09-17
[QUOTE=jlist]Actually, it'll be on internet for external domains.[/quote]That's a major, major no-no.  

Internet-facing authortative DNS needs to be run as the sole service on a box, and needs at least 1 redundant servers on a seperate pipe, preferably in a seperate colo physically far-away.

If you can't meet those requirements, find a free DNS hosting service or pay someone with the proper resources to host your Internet facing DNS for you.

It's really just that important I don't consider it acceptable to mess around with.

If it was internal, that's a different story.

> I'm thinking of allow the port so that I can use GUI tools to configure the server. The question is, is it secure enough to open that port, or should I create ssh tunnels?I wouldn't do it unless the network is trusted or you setup SSL.   Using SSH tunnels is more complicated and yield slower performance, because OpenSSH's buffering for tunnels is completely broken.

---

### Post by jlist on 2005-09-17
[QUOTE=LordHunter317]That's a major, major no-no.  

Internet-facing authortative DNS needs to be run as the sole service on a box, and needs at least 1 redundant servers on a seperate pipe, preferably in a seperate colo physically far-away.

If you can't meet those requirements, find a free DNS hosting service or pay someone with the proper resources to host your Internet facing DNS for you.

It's really just that important I don't consider it acceptable to mess around with.[/QUOTE]

This box is for some DNS server testing at this point. I guess it's ok for that purpose  :)  But it may become a production DNS server in the future.

I understand DNS's importance but I don't fully understand the necessity of running a dedicated server. As long as the server can handle the load (which is low for a DNS server) I guess it's ok?

I understand that for running a production DNS server, a secondary DNS server would be needed (in my case two master DNS servers for backup purpose) and I will probably run a monitor service that checks up on the DNS servers once in a while to make sure everything is ok.

[QUOTE=LordHunter317]I wouldn't do it unless the network is trusted or you setup SSL.   Using SSH tunnels is more complicated and yield slower performance, because OpenSSH's buffering for tunnels is completely broken.[/QUOTE]

I'm not sure if mysql's tcp connection is encrypted. If it is, then there's no need for SSL? How do I setup SSL? With STunnel?

Thanks

---

### Post by LordHunter317 on 2005-09-18
[QUOTE=jlist]But it may become a production DNS server in the future.[/quote]Well, it really shouldn't.

> As long as the server can handle the load (which is low for a DNS server) I guess it's ok?Well, but DNS must always be available.  Meaning even if the DNS server will never use 100% of the CPU resources of a box, it must have it available at all times.  

If you're running a webserver on that box serving dynamic content, it's hard to make that guarantee.  One or the other service suffers.  Having DNS suffer is a very bad thing.

Also, DNS is not something with a traditionally awesome track record, which is why it tends to be isolated as well.

[quote[(in my case two master DNS servers for backup purpose)[/quote]Why?  Slave DNS works perfectly well and is what is needed.

> I'm not sure if mysql's tcp connection is encrypted. If it is, then there's no need for SSL?It's not, that's why I'm saying use SSL if your network is untrusted.

> How do I setup SSL? With STunnel?Read the appropriate chapter of the MySQL documentation.  It's not hard if you have any experience with OpenSSL whoatsoever,

---

### Post by jlist on 2005-09-18
[QUOTE=LordHunter317]Well, but DNS must always be available.  Meaning even if the DNS server will never use 100% of the CPU resources of a box, it must have it available at all times.  [/QUOTE]I think I get the point. When it goes to production, (and if I have more servers, :) ) I would separate them.

[QUOTE=LordHunter317]Why?  Slave DNS works perfectly well and is what is needed.[/QUOTE]This has something to do with the dns server I'll be using: sheerdns or mydns. Both are master DNS servers. They serve from disk files or MySQL db respectively. So the zone transfer mechanism doesn't work for them, at least not for sheerdns as far as I know. Even if it does, because they can not be used as secondary DNS server, I would have to have a different DNS server setup for slave DNS. I think I'd rather use a file/db replication mechanism to sync up the data and run two identical setup for both DNS servers.

[QUOTE=LordHunter317]Read the appropriate chapter of the MySQL documentation.  It's not hard if you have any experience with OpenSSL whoatsoever,[/QUOTE]

Will do, thanks a lot for the help!

---

### Post by LordHunter317 on 2005-09-18
[QUOTE=jlist]This has something to do with the dns server I'll be using: sheerdns or mydns. Both are master DNS servers. They serve from disk files or MySQL db respectively. So the zone transfer mechanism doesn't work for them, at least not for sheerdns as far as I know.[/quote]I'll be rather blunt and say they're crap then, and have no business being used to do production DNS serving.

Sorry.  I'm very hardline on this because I've had service failures for companies I've worked for in the past because DNS wasn't properly provisioned.

BIND 9 in a chroot sounds like the best way to go.  If you really want to use them, feel free, but I wouldn't be comfortable without some sort of replication mechanism in place.  It's just too difficult to sanely manage.

---

### Post by jlist on 2005-09-19
[QUOTE=LordHunter317]I'll post rules later tonite or tomorrow.[/QUOTE]hi LordHunter317,  Any chance that you have got some time to work out the rules? If not, I can understand.

---

### Post by LordHunter317 on 2005-09-19
I don't right now (break between classes for lunch) but I will this afternoon.  Check back around 5PM EDT or so.

---

### Post by LordHunter317 on 2005-09-20
[QUOTE=LordHunter317]I don't right now (break between classes for lunch) but I will this afternoon.  Check back around 5PM EDT or so.[/QUOTE]Sorry it took so long for me to finally get to this, but this ought to work:```
#!/bin/sh

set -e

PATH="/bin:/sbin:/usr/bin:/usr/sbin"

case "$1" in
	start)
		iptables -F
		iptables -t nat -F

		# Default Deny Policy
		iptables -P INPUT DROP
		iptables -P FORWARD DROP

		# Existing connections
		iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

		# Localhost is always trusted.
		iptables -A INPUT -i lo -j ACCEPT

		# Allow SSH, WWW, DNS
		iptables -A INPUT -m state --state NEW -p tcp --syn --dport ssh -j ACCEPT
		iptables -A INPUT -m state --state NEW -p tcp --syn --dport www -j ACCEPT
		iptables -A INPUT -m state --state NEW -p udp --dport domain -j ACCEPT
		iptables -A INPUT -m state --state NEW -p tcp --syn --dport domain -j ACCEPT
		;;
	stop)
		iptables -P INPUT ACCEPT
		iptables -P FORWARD ACCEPT
		iptables -F
		;;
	restart|reload)
		"$0" start
		"$0" stop
		;;
	*)
		echo "Usage: $0 {start|stop|reload|restart}"
esac
```Save as /etc/init.d/firewall.sh or similar.  Run in runlevel S, anywhere after (I highly recommend 41 so it runs after networking starts).

This lets anyone access the services noted.  If that's inadequate, let me know and I'll show how to filter further.

---

### Post by jlist on 2005-09-21
Thank you very much! I'll try it out.

---

### Post by Stryker777 on 2005-10-27
Totally agree about the dns servers.  Ive been lucky with my personal servers.  My isp sets up slave zones for my domain names and I point ns1 and ns2 to them (free of course).  With mine as the master, they get the updates so they are always saying what i want, but I get no queries from other sources.  Another great thing about slaves on dedicated dns servers is you can expire faster without bogging your local bandwidth or server so rerouting is much faster.
Stryker777

---

### Post by bmichel on 2005-10-27
[QUOTE=jlist]Yes, I found iptables installed.


When you say GUI tool you mean X-Window tool? I did a server install and it doesn't have X Window...

It'll be great if you can help me create the initial firewall setup. I think I'll be running a dns server, sshd, a web server (lighttpd or Apache, maybe both,) mysql(does mysql need to open a port or should I be tunneling the client-server connection through ssh?)

And I suppose out going packets will not be filtered? Because I'll also be using some client side software such as wget, dns lookup, etc.

Thanks![/QUOTE]

Think about webmin as your central point to manage locally or remotely your servers. With webmin you can install modules that support/configure shorewall, apache, mysql, ssh, dns, postfix, qmail, ...

advice: better to install webmin modules with apt-get rather than through the webmin interface.

---

