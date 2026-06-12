---
title: "What do you use to monitor remote servers and services?"
date: 2008-10-26
forum: Server Platforms
---

### Post by rslrdx on 2008-10-26
Hi and TIA

Here is what I'm looking for and I'm open to ideas. I need a server monitoring solution with remote agent, perhaps someone could share what they use and give me some ideas.

I need a way to monitor server i install for some clients, mostly lamp, but i like to monitor the servers for them, so instead of using ssh to go look at the logs, I like to have some tool with an active agent perhaps that can just alert me when something within some parameters comes up, like full HD, connectivity, crashes, outage, power failures, a really long high cpu load, or even some lm-sensors alerts etc etc, and also just reporting that its alive. General system health.

I like to have it report back to some server I can host out on the web, that way my server could perhaps alert me and then display it like in nagios, with some sort of status alert levels, like OK, WARNING, and CRITICAL, perhaps my server could email this alert to me

I'm not the only one who will use the monitoring solution, it will be a tiny tech team, so the simpler the process the better. (IMHO)

It would be nice if I could keep some record of this and compare it visually rather than text logs. I would be nice if i could also monitor some windows boxes.. but not really a requirement.

I've looked at nagios, zenoss, zabbix, Centreon, groundwork, and a few others, but didnt quite "hit the spot".

So, please gimme some ideas. I guessing this would be the kind of setup for a NOC team to work with... but i could be wrong...


I guess I should list some apps I will be monitoring,

Apache
Mysql
iptables
Zimbra
OpenLDAP
postfix
PostgreSQL
Sendmail
Openfire
Bind
Samba
Tomcat
Asterisk
apcd
Network UPS Tool (nut)


:lolflag: quite the little list... hopefully this list wont scare away good ideas, most of the server i want to monitor are outside my network and dont have all this apps installed

As you can see from my list, its mostly server apps, ups is about the only hardware i can think of that i might want monitoring for.

I dont need to have access to the box with with this tool.. just like to get the reporting on the status and perfornace logs shown in a simple way for my small tech team.

Thanks again.
Rodrigo

---

### Post by cariboo on 2008-10-26
Have a look at Cacti, it is available in the repositories. their Web site is here:

[http://www.cacti.net/](http://www.cacti.net/)

Jim

---

### Post by doogy2004 on 2008-10-26
I use Webmin for my monitoring needs.

[http://www.webmin.com](http://www.webmin.com)

---

### Post by rslrdx on 2008-10-26
> **cariboo907 said:**
> Have a look at Cacti, it is available in the repositories. their Web site is here:

[http://www.cacti.net/](http://www.cacti.net/)

Jim

I might be wrong... but i don't think cacti has an agent does it? I looked over the project before, didn't seem to have one, and since most of the monitoring takes place on servers outside my domain/network and over the net, I don't think cacti would work safely... 

Again.. I might be wrong.. still reconsidering as I type this.

Thanks again.

---

### Post by rslrdx on 2008-10-26
> **doogy2004 said:**
> I use Webmin for my monitoring needs.

[http://www.webmin.com](http://www.webmin.com)

I use webmin alot, but its not the best for monitoring, unless you got some good ways of tweaking it... if so share the knowledge please!!! 

Thanks

---

### Post by cariboo on 2008-10-27
Have a look at [Zabbix]("http:///www.zabbix.com/") I have it installed, but I haven't had time to set it up, it does use agents.

Jim

---

### Post by rslrdx on 2008-10-27
So far zabbix has been the best "contender" for this title, :P

Have you used any others?

---

### Post by alienprdkt on 2008-10-27
you could try Nagios:

[http://www.ubuntugeek.com/nagios-network-monitoring-system-setup-in-ubuntu.html](http://www.ubuntugeek.com/nagios-network-monitoring-system-setup-in-ubuntu.html)

They have an add-on which allows you to remotely execute Nagios plugins on other Linux/Unix machines.

[http://www.nagios.org/download/addons/](http://www.nagios.org/download/addons/)

---

### Post by rslrdx on 2008-10-27
> **alienprdkt said:**
> you could try Nagios:

[http://www.ubuntugeek.com/nagios-network-monitoring-system-setup-in-ubuntu.html](http://www.ubuntugeek.com/nagios-network-monitoring-system-setup-in-ubuntu.html)

They have an add-on which allows you to remotely execute Nagios plugins on other Linux/Unix machines.

[http://www.nagios.org/download/addons/](http://www.nagios.org/download/addons/)

I just took at look at that and thanks for the info, i didnt know about this plugin, however I think this is way to risky.. as it requires the host thats being monitored to be accessible from the internet over ssh basically, meaning, my server has to go out and check if the server is there and run all the things that it needs, but thats not what i (ideally) am looking for. I'd like to have a client that can just run on its own and report back to an address out on the web, not the other way arround.

while this tools are great for local inTRAnet monitoring, i'm trying to get reports on servers that are not on my network, not even by VPN or SSH. 

lets say i install LAMP server for someone, and they would like to monitor that server, and that server alone on their network, nothing else. I would simple get perfornace logs basically from mysql and apache, average cpu and memory load, sent out to my server on a webaddres, like reporting.domain.com and my server would read this logs and process the info from that point on.

This would be the setup for a few different places and it doesnt require ssh access, nor does it require my serve to go out and login to anyones boxes, nor does it require me to keep the connetion information such as user and password.

I should also mention that most of this monitored servers are for intranet only apps, and as such they are on a basic dynamic ip address. Downhere static ip address are way too expensive, about 300 to 400 bucks a month for a 256k connection, thats right, all i get is a 25 kiloBYTEs a second download or upload for that much... a megabit conection cost over a thousand bucks... almost as much as a basic network admin guy salary downhere... 

check out the image on the link below to get an idea of the setup i'm thinking. hopefully i made it clear about what i'm trying to achieve.

[[IMG]http://img353.imageshack.us/img353/4392/idealmx0.th.jpg[/IMG]](http://img353.imageshack.us/my.php?image=idealmx0.jpg)

---

### Post by rslrdx on 2008-10-27
bump

---

### Post by rslrdx on 2008-10-28
Bump

I think alot of us can benifit from something like this, and maybe its really simple to get it setup and i'm the one out of the loop.

---

### Post by alienprdkt on 2008-10-28
I agree with you but I am somewhat new to Ubuntu, so I really don't know. 
I have made a post last week wondering how to accomplish this with having log files monitor these things for me. Then email me the results via logwatch.
But upon trying this out in Ubuntu seems I have no clue how to customize log files for Apache, I can do it with syslog, but that doesn't help with monitoring Apache'.

Heres a link to last weks post.
[http://ubuntuforums.org/showthread.php?t=951219](http://ubuntuforums.org/showthread.php?t=951219)

I do think we can all benifit from these things, as do you, I am working and testing a few things will get back to you when I find a way to get it to work.

---

### Post by Dragonbite on 2008-10-28
Are there any good web-based monitoring / administrative applications anybody knows of?

---

### Post by rslrdx on 2008-10-28
> **Dragonbite said:**
> Are there any good web-based monitoring / administrative applications anybody knows of?

Monitoring yes, most of the ones listed here already, but administrative is a bit harder and a much wider thing to do. 

for monitoring (local network at least) I can think of several.. but administration can very on a application basis, if your server management, OS wise, ssh might be your best bet... but I love webmin for those little things... editing crontab on webmin is much easier than using then using ssh (IMHO), point and click..

As for monitoring... well here is the list that comes to mind easilly

zenoss
zabbix
nagios
centreon
cacti
groundwork
pandoraFMS
hyperic

... just to name a few.

---

### Post by rslrdx on 2008-10-28
Crap, sucks to be me... i found just something that works as i want to, but there is a problem, its a paid service and i want to host my own server. This tool works via http and doesnt require special firewall or network configs...

[http://www.hounddogiseasy.com/](http://www.hounddogiseasy.com/)

Anyone knows anything like it that i might be able to host

---

### Post by rslrdx on 2008-10-29
just thought i'd bump this up again.

---

### Post by FlaHAM on 2008-11-02
I monitor the Fla Amature Digital Comm Assoc's Packet network with Hobbit. Hobbit is a open source version of Big Brother. It has a server and a cilent. More info maybe found at [http://hobbitmon.sourceforge.net/]("http://hobbitmon.sourceforge.net/") 
The server can be accessed from a web browser.

Fla Ham

---

### Post by doogy2004 on 2008-11-03
> **rslrdx said:**
> I use webmin alot, but its not the best for monitoring, unless you got some good ways of tweaking it... if so share the knowledge please!!! 

Thanks

I'll look at what you want to monitor again, and I'll see if I can help you set something up using Webmin.

---

### Post by gtdaqua on 2008-11-04
I use [Zenoss]("http://www.zenoss.com") and its excellent. I am monitoring multiple locations with two Zenoss Servers.

---

### Post by Chxta on 2008-11-04
> **gtdaqua said:**
> I use [Zenoss]("http://www.zenoss.com") and its excellent. I am monitoring multiple locations with two Zenoss Servers.
Methinks Zenoss is what I've been looking for. Test running it today. Thanks.

---

### Post by rslrdx on 2008-11-05
> **gtdaqua said:**
> I use [Zenoss]("http://www.zenoss.com") and its excellent. I am monitoring multiple locations with two Zenoss Servers.

Are you monitoring multiple locations of the same company or just specific servers on someone else's network?

Unfortunately I'm not looking to simple monitoring multiple locations of the same company, but remote servers on different networks.

I don't even need to manage this servers form the console.. just monitoring and alerting.

---

### Post by cjacobsen on 2009-01-21
Personally, I like Logwatch. E-mails me a log summary report wherever I go!

---

