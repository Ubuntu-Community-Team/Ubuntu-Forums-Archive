---
title: "iptables logviewer"
date: 2007-08-03
forum: Server Platforms
---

### Post by eentonig on 2007-08-03
Hi,

I'm looking for a nice GUI that allows me to see the output of iptables hits.

I know I can use 

> tail -f /var/log/messages
 (actually, I output fw logging to /var/log/iptables.log. but that's not important.)

But what I would like to have, is a tool that allows me to follow real-time logging, with layout that is easy for my eyes, allows sorting and that has extensive filtering capabilities.

(Basically, I'm looking for the functionality that Checkpoint Smartview Tracker has to offer, but then for iptables :lolflag:).

I want to push iptables in my company to be used for the smaller sites. But I will need something similar if I ever want to achieve this.

---

### Post by zidane2 on 2007-08-03
firestarter is a GUI for iptables that reads iptables log file and displays it.

it is easy to enable a port and connection from a certain host etc
as well as disable ports and connections from a host and ip ranges etc
very easily

i use firestarter to allow people in to my ssh server and it is very easy to use

hope it helps :)

---

### Post by trak87 on 2007-08-03
This would give you more control:

```
grep -i <search_spec> /var/log/messages | less
```

Just insert whatever search spec is used by iptables.

'grep' searches for text strings. The 'less' command is for viewing pages one page at a time, and it gives you PgUp/PgDn control. Press '/' and you can do searches as well.

---

### Post by eentonig on 2007-08-04
I'm not looking for a tool to configure the fw. I use fwbuilder for that, because it offers  a lot more flexibility then firestarter.

What I need, is a monitoring solution.

@trak87: Thanks, but I know how to filter on output. I was hoping to find a GUI that would facilitate this. 

For me, it's not a problem. But I need to hand over the day to day follow up to the 'telephone monkeys' in first line. They do a good job, but I can't expect them to start working with a CLI. So, I need an intuitive GUI that would allow monitoring the iptables log. (PS. And please don't propose the standard System Log viewer. I know that's a GUI. But it's not tailored to fw logging.)

---

### Post by trak87 on 2007-08-05
I did a google search on 'iptables gui monitor', and found that webmin has a nice gui interface for iptables. I've heard good things about webmin before, I used it back in my Mandrake days. Webmin isn't listed in my Ubuntu respostories but perhaps it's available elsewhere as a deb.

The second listing shows  a program called bifrost: [http://freshmeat.net/projects/bifrost-fw/?branch_id=30280&release_id=129324](http://freshmeat.net/projects/bifrost-fw/?branch_id=30280&release_id=129324)

Hope this helps.

---

### Post by dreadlord_chris on 2007-08-05
maybe [fwlogwatch]("http://fwlogwatch.inside-security.de/")
it's in the repositories

---

### Post by eentonig on 2007-08-05
fwlogwatch is CLI based. So not very userfriendly for basic operators. I use it myself though.

webmin interface is for configuring and is rather slow and limited compared to fwbuilder.

bifrost seems like something to have a look at. 

Thanks all.

---

### Post by dreadlord_chris on 2007-08-05
> **eentonig said:**
> fwlogwatch is CLI based. So not very userfriendly for basic operators. I use it myself though.

webmin interface is for configuring and is rather slow and limited compared to fwbuilder.

bifrost seems like something to have a look at. 

Thanks all.

hmmmm....
[quote=http://fwlogwatch.inside-security.de/]
fwlogwatch is a packet filter / firewall / IDS log analyzer written by Boris Wesslowski originally for RUS-CERT. It supports a lot of log formats and has many analysis options. It also features incident report and realtime response capabilities, **an interactive web interface** and internationalization.
...
Output as plain text or HTML (W3C XHTML 1.1 with inline or linked CSS level 2) with limit and sort options.
The current status of the program can be followed and controlled through a web interface.
[/quote]

---

### Post by eentonig on 2007-08-05
Oops, I stand corrected.

I guess I must dig deeper into the program then. I installed and ran it, but I only got cli output. Guess I need to search for how to access the web interface.

---

