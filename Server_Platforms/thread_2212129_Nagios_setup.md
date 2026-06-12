---
title: "Nagios setup"
date: 2014-03-19
forum: Server Platforms
---

### Post by lykwydchykyn on 2014-03-19
I've been playing a little with Nagios to see if I can approximate a replacement for our Solarwinds monitoring that we used to monitor the general state of our WAN.

I've got a basic server setup, and I've added a few hosts using a tutorial I found online.  Seems OK, but I don't think editing config files by hand is going to scale up.  I know there are autodiscovery and web-based configuration tools for nagios, but it's a little overwhelming trying to figure out what to use.

Anyone have any advice for a nagios newbie?

---

### Post by nerdtron on 2014-03-19
Nagios really does need an automated host adding feature. Some tools like Groundworks which have Nagios can add a host using a web GUI.

Anyway, if all your host are just monitored by ping, then you can write a script that any user can run. They would just input the ip address of the server they want to monitor and the script will edit the necessary nagios config files.

---

### Post by sandyd on 2014-03-20
I hereby introduce you to [NagiosQL]("http://www.nagiosql.org/")

You will still need to configure nrpe/agent manually (I use btsync for this as after 30+ servers, it becomes boring), but the NagiosQL simplifies the nagios configuration process itself

---

### Post by lykwydchykyn on 2014-03-20
> **sandyd said:**
> I hereby introduce you to [NagiosQL]("http://www.nagiosql.org/")

You will still need to configure nrpe/agent manually (I use btsync for this as after 30+ servers, it becomes boring), but the NagiosQL simplifies the nagios configuration process itself

I'll take a look; it was on the short list of things to try, but I hadn't gotten to it yet.  I've spent all morning wrestling with lilac-reloaded, and yesterday with check_mk.  I think I've managed to bork the nagios config pretty badly. :)

I'll check nagiosql as soon as my patience level comes back to normal.

---

### Post by LHammonds on 2014-03-20
I don't use any automated configuration system (would not really want to) but I do have a tutorial on how I setup and configured my server which might be helpful.

[Nagios Setup on Ubuntu 12.04](http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=194)

LHammonds

---

### Post by nerdtron on 2014-03-20
> **sandyd said:**
> I hereby introduce you to [NagiosQL]("http://www.nagiosql.org/")

You will still need to configure nrpe/agent manually (I use btsync for this as after 30+ servers, it becomes boring), but the NagiosQL simplifies the nagios configuration process itself

Thanks for the tip sandyd. I think this will be useful on our new deployment OpenVPN clients.

---

### Post by koenn on 2014-03-21
> **lykwydchykyn said:**
> Seems OK, but I don't think editing config files by hand is going to scale up.  

Depends what you have in mind, both in terms of scale (how many hosts/services/....) and how you think to deal with it (distribute the  workload over lots of people ? automate it ? ...)
I don't know the tools others have mentioned, I run a pretty bare Nagios. In terms of scaling up, here are some thoughts :

- in a stable environment, you're probably not going to be adding hosts or services on a daily basis. Once nagios is set up, it's there, And you only occasionaly have to add somthing. (Unless your environment is so large that as soon as one round of decomissioning, upgrades or reorganization is finished, there's an other one starting already again). So in most cases,  once it's set you can pretty much leave it alone.  

- Nagios has a pretty powerful yet flexibel template system - for large numbers of similar hosts you can inherite practically all settings from a template, configuring a host is then  limited to the unique attributes of a host - often just a hostname, and an IP address, maybe a parent. Likewise for services.. (it reminds me of OO programming : cascading templates, multiple inheritance, ...).  Eg: if your template specifies hostgroup membership;  and your services definitions apply to hostgroups, a new host definition is all it takes to have the relevant service checks applied to the newly added host. 

- I hope that tutorial you found explained that you don't need to put everything in 1 config file. You can also have 1 file per host, or 1 file for similar hosts or similar services or ....  The good thing about that is that your linux skills in handling text files will pay off : you can organize them in a sensible directory structure, you can grep recusively to find stuff, you can add configuration by copying files and running a sed 'find and repleace' over them, and if you have to repeat that sort of stuff often, you wrap a bash loop around it and make it a script.  And you can organize your config files so that edit-by-script  becomes even easier (eg by having all files that are likely to be edited in 1 batch in the same subdir, that sort of thing) 

- Nagios supports wildcards (or even regex pattern matrching, iirc) which can be put to good use for adding hosts in hostgroups and the likes. I don't use it much because between the templates and the  standard text tools I haven't found a real need for it. 

you might find this interesting : [http://users.telenet.be/mydotcom/howto/nagios/config-advanced.html](http://users.telenet.be/mydotcom/howto/nagios/config-advanced.html)

this approach may reach its limits when you start doing more complex stuff such as interdependent services, or actions other than "notfiy-by-mail" - those are things I haven't really looked into yet so I can't guarantee that inheritance or (scripted) copy-and-edit will help much.

---

### Post by lykwydchykyn on 2014-03-21
Well, the "human side" of the scenario is that I'm pretty much the "Linux guy" around here, and if managing a system requires writing config files that's pretty much a nonstarter for most of my colleagues.  We don't need any super-fancy stuff, just monitoring the state of switches/routers/servers. 

I still need to investigate nagiosql.

---

### Post by nerdtron on 2014-03-21
Your lucky with a few server and routers to monitor. We have at least a thousand routers to monitor and changes are made everyday.

---

### Post by lykwydchykyn on 2014-03-21
> **nerdtron said:**
> Your lucky with a few server and routers to monitor. We have at least a thousand routers to monitor and changes are made everyday.

Well we don't have a thousand routers, but I wouldn't describe it as "a few" either.  How many nodes we end up monitoring depends on how much anyone else gets behind what I'm setting up, but it could easily be a few hundred depending on what we want to track.

---

### Post by koenn on 2014-03-21
> **lykwydchykyn said:**
> Well, the "human side" of the scenario is that I'm pretty much the "Linux guy" around here, and if managing a system requires writing config files that's pretty much a nonstarter for most of my colleagues.  We don't need any super-fancy stuff, just monitoring the state of switches/routers/servers. 


I had a quick look at the NagiosQL demo. Looks pretty good. Otoh, it looks like a rather thin layer on top of nagios config files - maybe  thin enough to understand what's going on underneath if you already know nagios while still  "GUI" enough for the textually challenged - but maybe not. Maybe sandyd can elaborate a bit on that.

unrelated  ; try planting the idea in your collegues' heads that if *real*  IT-guys should at least have some basic linux/unix skills - including editing a config file.  And it's not all that different from changing a value in regedit or editing an .ini file for a legacy application or so.

---

### Post by lykwydchykyn on 2014-03-21
> **koenn said:**
> I had a quick look at the NagiosQL demo. Looks pretty good. Otoh, it looks like a rather thin layer on top of nagios config files - maybe  thin enough to understand what's going on underneath if you already know nagios while still  "GUI" enough for the textually challenged - but maybe not. Maybe sandyd can elaborate a bit on that.


I've been working with it today, and that's pretty much what I'm finding.  Still, with some sensible setup it shouldn't be hard to get it to a point where adding a host or service won't be onerus for anyone.

> 
unrelated  ; try planting the idea in your collegues' heads that if *real*  IT-guys should at least have some basic linux/unix skills - including editing a config file.  And it's not all that different from changing a value in regedit or editing an .ini file for a legacy application or so.

There's a time to fight those battles, and a time to try to meet people where they are.  I have tons of respect for my coworkers, they may not have mad Linux skills but they have plenty of knowledge that I don't.

---

### Post by koenn on 2014-03-21
> **lykwydchykyn said:**
> 
There's a time to fight those battles, and a time to try to meet people where they are.  I have tons of respect for my coworkers, they may not have mad Linux skills but they have plenty of knowledge that I don't.

Oh, I didn't mean it as the opening skirmish of a pro-linux cruisade, more like a gentle challenge. And I definitly didn't mean that you should let the success or failure of your nagios project depend on it.

OTOH, I do think it's genuine good advice for sysadmins in the sort of place where I work : SME-sized organizations where linux and open source  tools are great for saving money and avoiding vendor lock-in on one hand, and with the unavoidable Windows servers and desktops  on the other. If, as a sysadmin in such environment, you only know "Windows" (or only know 'unix" for that matter), you're simply less valuable as an employee - no disrespect intended.  And of course this matters a whole lot less if the environment is large enough to warrant  specialization and there's a pool of sysadmins rather than just one or two.

---

### Post by lykwydchykyn on 2014-03-21
> **koenn said:**
> 
OTOH, I do think it's genuine good advice for sysadmins in the sort of place where I work : SME-sized organizations where linux and open source  tools are great for saving money and avoiding vendor lock-in on one hand, and with the unavoidable Windows servers and desktops  on the other. If, as a sysadmin in such environment, you only know "Windows" (or only know 'unix" for that matter), you're simply less valuable as an employee - no disrespect intended.  And of course this matters a whole lot less if the environment is large enough to warrant  specialization and there's a pool of sysadmins rather than just one or two.

You're preaching to the choir here; it's just I've been here 10 years, and most of the other guys have been around at least 6 or 7.  Everyone's gone through a "Linux phase", and despite my encouragement and offers of help it doesn't seem to stick.  We do stuff with Linux, but if it comes down to command lines and config files it usually ends up in my lap (and stays there); I've just come to terms with the fact that if I want to get a team consensus, it's got to at least have a basic GUI.

---

