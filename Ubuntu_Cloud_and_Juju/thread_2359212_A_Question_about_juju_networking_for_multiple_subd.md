---
title: "A Question about juju networking for multiple subdomains."
date: 2017-04-21
forum: Ubuntu Cloud and Juju
---

### Post by katja2 on 2017-04-21
[COLOR=#1A1A1A]Hi, I'm not super sure if this is posted in the right place, but i need some help with an issue. I know what i'm doing to a point, but i need some advice to move forward.[/COLOR]

[COLOR=#1A1A1A]I've made a small media buisness. we go out and film for people, audio recording. I do audio engineering and my partner does video editing and we have a few other people who help out and help us operate. very small operation, however we need a website and a way to communicate/transfer media, etc. so i set up a cloud with MAAS and JuJu on a ubuntu server install. works perfect. i've got my website up, all the services we need are able to be seen on LAN by computers in the network. its perfect. however, here's the issue:[/COLOR]

[COLOR=#1A1A1A]i have one website. its hosted on a virtual machine in our "cloud" ... but we need to have another web app served up by someone visiting a subdomain, or different URL. i know full well, how to do this on a normal server, bind9, and apache2 virtual hosts.. however now i'm working with a cloud where each of the two apache2 servers are its own VM.. the mysql databases are their own machine.. and the bind9 server its its own machine, because its a cloud running with the JuJu software. how would i go about setting something like that up? obviously, i should make one "main" server that's port forwarded with bind9 and an apache2 proxy or something on it. but i'm not sure how to go about doing that. any tips? this is my first "cloud."[/COLOR]

---

