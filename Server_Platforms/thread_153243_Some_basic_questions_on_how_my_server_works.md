---
title: "Some basic questions on how my server works"
date: 2006-03-31
forum: Server Platforms
---

### Post by earth_walker on 2006-03-31
Hi everyone.

I have just put my first http server online using Ubuntu, and I'm really pleased with how easy it was. The only really confusing thing was trying to get the domain registrar, DNS and our dynamic IP all pointing in the right directions. 

Right now my server setup includes Ubuntu Base, Apache, PHP, MySQL server and http, SSH and SSH-Client, and DDClient to update the IP with the DNS.

However, with the easyness, there were several things that happened magically and I'd like to learn more about what it's actually doing now - I have some questions that don't seem to be covered in the many server HOW-TOs:

1. Currently if I leave it at the login prompt, the website breaks after a while, meaning either the IP is not being updated unless a user is logged in, or the server isn't working at all and the website is cached somewhere which is running out.

Should all of these (apache, php, ddclient, etc) be running at boot, or does a user have to be signed in for the server to be accessible? I installed everything using apt-get. Do I need to reconfigure things to run automatically?

2. I'm behind a hardware firewall. I probably also want a redundant software firewall. Did any of my apt-getting also put a firewall in? If so, how do I tell if it's working? 

If not, synaptic shows many options, including shorewall, firestarter, firehol, iptables, etc. Are these different frontends to the same basic firewall, or is there one in particular I should be going for? If installing everything from apt-get, does it take care of permissions, users, start-up scripting, recognizing running processes, and setting it up to run in the background etc., or do I have to change lots of settings? 

Is there anything else I should be concerned with security-wise?

3. I'd like to SSH into the server, however if I try [email]me@domain.com[/email] it hangs, and [email]me@servername.domain.com[/email] tells me there's no such service. Should this be possible, or can I only do it by specifying the IP of the router that forwards the port?

4. While reading about updating my dynamic IP with the DNS it seems that there were several options possible - software updater, router, or have a firewall do it.

I got ddclient working easily, but it doesn't support my router and instead uses a website to fetch the WAN IP. This works (at least when a user is logged in and ddclient has been manually started), but it seems to me the other methods may be better.

My router has the option to update the IP, but gives me no feedback as to whether it's working or not, and my first couple of tests with basic Zoneedit settings didn't seem to work (or at least the IP wasn't updated within 20 minutes of it changing), so I went with ddclient.

Are there any pros/cons to each of these methods? Is there a benefit to spending time trying to get the router to take care of this for me?

Thanks so much everyone.

---

### Post by s7eam on 2006-03-31
As much as I know the best way for a server is to assign a static IP address to it. 

If you're concerned about your security I would suggest to watch your logs. What does they say? Look at apache /var/run/apache2/error.log

---

### Post by LordHunter317 on 2006-04-01
[QUOTE=earth_walker]Hi 1. Currently if I leave it at the login prompt, the website breaks after a while, meaning either the IP is not being updated unless a user is logged in,[/quote]This makes no sense.  Zero.  Negative sense in fact.

Either your DDNS client is running, or it isn't.  If it is and the address isn't updating, you have a bug.  If it's only running when you login you need t (possibly) write an init script for it and make it run at startup.

> Should all of these (apache, php, ddclient, etc) be running at boot,Yes.

> 2. I'm behind a hardware firewall. I probably also want a redundant software firewall.No, you don't.  Why would you want that?

> 3. I'd like to SSH into the server, however if I try [email]me@domain.com[/email] it hangs, and [email]me@servername.domain.com[/email] tells me there's no such service. Should this be possible, or can I only do it by specifying the IP of the router that forwards the port?If you're behind NAT, you must port forward.

---

### Post by earth_walker on 2006-04-03
[QUOTE=LordHunter317]This makes no sense.  Zero.  Negative sense in fact.[/QUOTE]

Gee, thanks for the help. [sarc]Since it WAS exhibiting this behaviour, the server was obviously sitting in a parallel universe where things like negative sense exist. [/sarc]

For anyone who may be having similar problems as I was, apparently in order to have ddconf run as a daemon at startup, you need to add the line:

daemon=delay 

to /etc/ddclient.conf, where delay is the time delay between checks of the ip. I ended up getting my router to do it instead, which for some irrational reason I feel better with since I've had no feedback on Question 4.

Regarding Question 2, I know why I'd want both Hard and Soft firewall on a windows desktop. Is there any good reason to have both for an Ubuntu Server?

As for the Question 3, the SSH problem, I was forwarding the wrong port, and the answer to my question is yes, I can SSH in using [email]me@server.domain.com[/email].

---

### Post by mscman on 2006-04-03
> [QUOTE]Originally Posted by earth_walker
Hi 1. Currently if I leave it at the login prompt, the website breaks after a while, meaning either the IP is not being updated unless a user is logged in,
This makes no sense. Zero. Negative sense in fact.[/QUOTE]

Actually, I have a firewall at school that exhibits this exact problem: after an extended period of time, it loses its WAN connectivity and only allows LAN activity.  Granted, it's running Debian and not Ubuntu, but we still have yet to find out what is causing it.


> 
Quote:
[QUOTE]2. I'm behind a hardware firewall. I probably also want a redundant software firewall.
No, you don't. Why would you want that?[/QUOTE]

The more firewalls, the safer.  Granted, one good firewall should stop all of your infiltration, and using multiple firewalls can get confusing and cause troubleshooting problems, but being safe never hurt anyone.  If you want a simple firewall to throw on for extra protection, I recommend Firestarter.  It's easy to configure (in fact, almost no configuration is required), and is pretty strong.  The only thing you'll have to be aware of is that you'll have to unblock port 22 to allow for SSH tunnelling (as you stated you wanted)

---

### Post by LordHunter317 on 2006-04-04
[QUOTE=earth_walker]Gee, thanks for the help.[/quote]Well, it makes no sense.  Having a user logged in has no effect on system daemons, unless the user was starting the daemon through ~/.profile or similar (which would make it distinctively not a system daemon).

Your discription of the problem made no sense, you were confusing two unreleated things.

> Regarding Question 2, I know why I'd want both Hard and Soft firewall on a windows desktop.That being?

> Is there any good reason to have both for an Ubuntu Server?If your network firewall is solid, there's rarely any reason for any host level filtering ever.  Frankly, this is one of those, "If you have to ask, then the answer is automatically no" sorts of things.

[quote=mscman]Actually, I have a firewall at school that exhibits this exact problem: after an extended period of time, it loses its WAN connectivity and only allows LAN activity.[/quote]That has nothing to do with the behavior he described.  It's most likely caused by a flakey NIC or flakey NIC driver.  It's not a TG3 or a RealTek, is it?

> The more firewalls, the safer.Utter nonsense.  Two identical firewalls in series offer no added protection.  The proof of this is rather obvious and left as an exericse to the reader.

> Granted, one good firewall should stop all of your infiltration, and using multiple firewalls can get confusing and cause troubleshooting problems, but being safe never hurt anyone.Clearly, it did.  This statement is self-contradictory.

> If you want a simple firewall to throw on for extra protection, I recommend Firestarter.'simple' and 'Firestarter' don't go together.  Run 'sudo iptables -vL' if you don't believe me.  Then cry at how a simple thing was made so hard.

---

