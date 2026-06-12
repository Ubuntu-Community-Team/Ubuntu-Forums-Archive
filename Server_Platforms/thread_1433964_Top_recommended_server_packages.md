---
title: "Top recommended server packages"
date: 2010-03-19
forum: Server Platforms
---

### Post by Webnet on 2010-03-19
We're about to upgrade our Ubuntu server and are looking for a complete package set that includes a firewall, some kind of snoopy, and whatever else we "must have" or that would just be extremely useful.  What do you guys find the most absolutely necessary and needed packages for running a linux server in regards to security and performance.

---

### Post by jrssystemsnet on 2010-03-19
Not exactly what you asked for, but - I can't for the life of me understand why **pv** isn't part of the default distribution.  If you don't know about it, install it and play with it.

Nethogs, iotop, and iftop are all really good monitoring tools to know about / have around.

Firewalls are overrated, especially for servers - you should be keeping an eye on what ports are open, and closing any that shouldn't be, not just trying to wrap an unknown mess in a firewall like some kind of soggy burrito with a hard chocolate shell.  The only good use for a firewall on a server is for doing port or address limiting on services that don't offer port or address limiting (or you don't trust the code for the same) in the service itself.  Anyway, ufw is already part of the distro, you don't have to go looking for it.

Know how to use grep, find, sed, replace, dd, xargs, and maybe awk.  REALLY know them, as in know how to use most of the optional arguments you can feed them, not just the default usage.  Know how to use redirection to chain all of the above together.  Once you've got all that - learn Perl, for the tasks that are still a little too complicated for just chaining together commands from the shell.  All of these things are FAR more valuable to you than any random software package.

Understand logging.  If you're letting Apache log directly to logfiles... STOP DOING THAT.  You need to learn what cronolog is and start using it... it will make your life incredibly easier.

If you don't already have and aren't already married to some other webstats package... try awstats.

Learn how the Alias directive in httpd.conf files works.  Learn how the Location and Directory blocks work, and why you'd sometimes want to use one, but sometimes want to use the other.  Learn the differences between applying Apache directives in .htaccess files, and applying them in conf files... and why you'd sometimes want to do it one way, and sometimes do it another.

I could go on and on with this stuff; really the best things you can do for security and performance are understand how the basic tools work.  *Other* tools generally aren't even icing on the cake, they're more like the little button icing flowers *on* the icing on the cake. :)

---

### Post by inphektion on 2010-03-19
if its an external server I'd move the default ssh port.
i find fail2ban quite helpful/useful.  I have a default iptables script i run that blocks everything but the services i'm using so that gives a bit of piece of mind though you can see/verify what is working with an netstat -an

What is the server used for we can give more tips.

---

### Post by brian mcgee on 2010-03-20
**Security**

[LIST]
[*]Get familiar with iptables. That's your firewall. Still, disable and restrict any listening services you don't need. We use iptables primarily to limit access to admin web interfaces and DB servers (e.g., so only a web-frontend has access). It works well!
[*]Keep your servers patched. I love apticron for update alerts
[*]SSH: denyhosts is great. Also, consider disabling root logins via SSH, and change the default port if publicly exposed
[*]Try to always have at least a couple layers of security. This isn't always practical, but it's a decent rule of thumb.
[*]Check out Snort (depending on the environment, this might be overkill)
[/LIST]
 I've heard that logcheck is a good option for simple log monitoring. For overall system monitoring, I'd recommend Zabbix / Nagios (especially if you plan on multiple servers. We use Zabbix). Also, try to gain some familiarity with the iostat, netstat, vmstat and free commands. I also like htop.

This is really simple and general. To help more, I'd need to know... what does your server serve? ;)

---

