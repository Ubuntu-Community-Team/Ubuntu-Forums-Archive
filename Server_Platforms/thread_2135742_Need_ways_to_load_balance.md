---
title: "Need ways to load balance"
date: 2013-04-15
forum: Server Platforms
---

### Post by Rpgglitchy on 2013-04-15
[COLOR=#000000][FONT=verdana]Hi,[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]I am having an issue installing load balancing methods and I am in need of aid.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Let me start with explaining my setup:[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I have 1 load balance server which will be the the server that will be surfed to. for everything (phpmyadmin, all websites, etc..) and this one will redirect to the others. [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2 identical webservers with unison syncing. (2 webservers is not the limit, this is just my testing setup)[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]1 MySQL server to have a standalone database server.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana](these are all Ubuntu 12.10)[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]My question is to find a good way to load balance (maybe with a nice webgui? not mandatory) that supports awstats on load balance level (it needs to have statistics for all websites on all servers) or something similar to awstats. [/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]I have already succeeded in configuring a load balance method with apache with proxies and balancer clusters. it works, but I cannot combine it with a statistics app, like awstats.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]I tried Ispconfig 3 but I just cannot figure it out. There aren't many good tutorials to where I want to go to. I only need To use the webservers part, but every tutorial comes with DNS and Postifx and Mail services. I don't need those. I just need to add the websites that are on the webservers and load balance on this servers but I cannot find out how to achieve this.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]I really hope to find some help here and I thank you for your time to read this and maybe think of a way and share it with me.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Thanks,[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Glitchy[/FONT][/COLOR]

---

### Post by Rpgglitchy on 2013-04-17
bump

---

### Post by pfeiffep on 2013-04-17
For large commercial load balancing BigIP is solid solution. I have no knowledge of free alternatives

---

### Post by Habitual on 2013-04-18
I would stick varnish-cache in front of the webservers.

All that GUI admin stuff, no. Centralized? Webmin in a cluster "mode" (if it has such a thing, I don't know, I use C-LI)

We just setup a varnish > apache2 > serving wowza content with a remote mysql just this week.

varnish was up in front in like an hour (and I had never done it).

2 file edits and start varnish with NO changes to your webservers.

---

