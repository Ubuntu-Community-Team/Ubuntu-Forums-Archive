---
title: "Nagios on Ubuntu?"
date: 2006-01-12
forum: Server Platforms
---

### Post by Mr_Grieves on 2006-01-12
Anyone here that tried it out? Please share any interesting experiences :)

---

### Post by nocturn on 2006-01-13
I have it running.

Not much to say, Nagios is great, just aptitude install it and set it up.

It's much better then Big Brother IMO

---

### Post by hamsteri on 2006-01-13
Yup nagios is great.
Check out [http://www.itgroundwork.com/products/gwm-architect.html](http://www.itgroundwork.com/products/gwm-architect.html) for easy configuation of nagios (after you get monarch to run )

---

### Post by Mr_Grieves on 2006-01-13
Oh.. I'm an old Netsaint/Nagios user.. contributed abit to the real plugin.. if you use it.. even got myself published on the site after holding a seminar on Nagios (stands abit tall) :)

I wanted to know about the experiences about Ubuntu with Nagios. Thanks for the response!

I've done quite some comparising with Nagios and commercial solutions like HP-OV, Netcool, Nervcenter, SNMPc, Patrol, Tivilo.. and I found that Nagios, functional and capacity wise is a strong compeditor in almost every way. I like it very much.

I was thinking of publishing my lecture on Nagios, but atm. it's only in Swedish I'm afraid. I'm planning of doing a translation to English as soon as I have time. It's about doing service and system surveillence with Nagios, going thru the functionality and making interesting comparisons with commercial solutions.

I have it running on Debian mostly.. so I figured Ubuntu would be a great choice for Nagios.

---

### Post by hamsteri on 2006-01-14
I personally use nagios at work and it's really nice when it's setup properly.
I run it on Centos, debian and ubuntu, and it runs flawlessly.

---

### Post by cscashby on 2006-02-07
I've just completed a nagios setup and found I needed to do the following after installing using apt:

Create /etc/apache/conf.d/nagios.conf with the following config:
```

ScriptAlias /nagios/cgi-bin /usr/lib/cgi-bin/nagios
<Directory /usr/lib/cgi-bin/nagios>
        Order allow,deny
        Allow from all
        AllowOverride AuthConfig
        Options ExecCGI
</Directory>


Alias /nagios /usr/share/nagios/htdocs/

<Directory /usr/share/nagios/htdocs>
        Order allow,deny
        Allow from all
        AllowOverride AuthConfig
        Options none
</Directory>

```

Change the permissions of /var/run/nagios to rwxrws---

Create /usr/lib/cgi-bin/nagios/.htaccess:
```

AuthName "Nagios Access"
AuthType Basic
AuthUserFile /etc/nagios/htpasswd.users
require valid-user

```

Has everyone else had the same sort of experience? If so I'd like to write a wiki page on the subject...

---

### Post by ice60 on 2006-04-10
Double Post

---

### Post by ice60 on 2006-04-10
hi, i'm trying to find a program to replace Pingplotter (win32) :(

quote from Pingplotter
> It uses a combination of traceroute, ping, and whois to collect data quickly, and then allows you to continue to collect data over time to give you the information you really need to identify problems (both short-term and long-term trends). 

PingPlotter is unique in its ability to collect data (over a period of hours, days or weeks), and then allow you to focus on particular aspects of that data to determine where the problem is happening. PingPlotter graphically shows problems in a way that allows you to shorten the time it takes to pinpoint a problem.

[img]http://www.pingplotter.com/nessoftgraph.gif[/img]

will Nagios fit-the-bill, or is it perhaps too much, i'm particularly worried about it being a server which is something i don't really need on my standalone computer.

i just want to be able to monitor router hops in real-time using a good GUI and graph functions. i found and used traceproto which is a small CLI program that shows hops and router names, but it's not what i really want. i love CLI for 90% of programs, but this is one of the 10% i really need a good solid GUI. so can someone tell me if i should install Nagios? thanks :)

---

### Post by DancesWithBikers on 2007-05-03
Maybe [SmokePing]("http://oss.oetiker.ch/smokeping/") or [Cacti]("http://cacti.net/")?

---

### Post by luv2ride on 2007-06-13
Has anyone used and/or configured nagios plugins? I have a few setup and working properly but am having a helluva an issue with check_dhcp.

Here's what I've done to this point

chown root.nagios check_dhcp
chmod 4750 check_dhcp
ls -la -r-sr-x--- 1 root nagios  25464 2007-06-12 11:02 check_dhcp

I believe I have the syntax right, permissions correct due to port below 1024 this should run as root.

I get a permissions error in Nagios and can't find whats causing it.

Anyone?

---

