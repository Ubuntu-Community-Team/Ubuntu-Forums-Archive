---
title: "Need some webserver advice"
date: 2016-08-03
forum: Server Platforms
---

### Post by do.marmor on 2016-08-03
Im in the process of building a new server, that mainly going to be used for websites and ftp file sharing,
im thinking of making the server in virtualbox vm easy to keeps backups so i never need to do same settings again if hardware should fail. 
My system would then be

ubuntu server 64bit with virtualbox installed

VM with ubuntu server x86 (webserver)

VM clone of above for testing new software settings before applying them to main server (this vm will only be running when needed)

my first question is , is it a good idea to run the server as vm?

second no matter if i have the system normally installed as now or use above example,
 i want to be able to give a few family member possibility to make a website seeing i been askt if they can host there webpage on my server because they want to learn, 
However this is total beginners that click first and think later , i lost count on all the times i fixt there computers, so i do not want to give them any access where they screw tings up other then there own website but same time i do not want to lock them out to much seeing u learn by doing.

So basically i need a dummy web interface kinda like free web hosting sites have where they will be able to add there domain and create there webpages whiteout affecting anything else on the server

i found a few options i was wondering if any of u had experience with below options and can advice on what u would use

web min (is what i use probably to advanced )

below looks promising

[http://ajenti.org/](http://ajenti.org/) 
[http://www.ispconfig.org/](http://www.ispconfig.org/)
[http://www.zpanelcp.com/](http://www.zpanelcp.com/)

i cant make up my mind so hopefully someone here can help me out

---

### Post by Habitual on 2016-08-03
Yes, IMO it is a **great** idea to run a server in a vm.

---

### Post by 1clue on 2016-08-03
> **do.marmor said:**
> Im in the process of building a new server, that mainly going to be used for websites and ftp file sharing,
im thinking of making the server in virtualbox vm easy to keeps backups so i never need to do same settings again if hardware should fail. 
My system would then be

ubuntu server 64bit with virtualbox installed

VM with ubuntu server x86 (webserver)

VM clone of above for testing new software settings before applying them to main server (this vm will only be running when needed)

my first question is , is it a good idea to run the server as vm?


Yes. Most remotely hosted servers are VMs. It's an incredibly good idea.

You might want to consider something like [https://www.docker.com/](https://www.docker.com/) which is in Ubuntu as 'docker.io'. You start with a preloaded Linux image (Ubuntu 16.04 for example) and then script your changes to it such that it becomes what you want it to be. This includes adding software, configurations, etc.

What this gives you is not just a backup, but a way to build a fresh server without losing the stuff you changed on it. You can put your setup in git, and track what changes you did when.

> 
second no matter if i have the system normally installed as now or use above example,
 i want to be able to give a few family member possibility to make a website seeing i been askt if they can host there webpage on my server because they want to learn, 
However this is total beginners that click first and think later , i lost count on all the times i fixt there computers, so i do not want to give them any access where they screw tings up other then there own website but same time i do not want to lock them out to much seeing u learn by doing.

So basically i need a dummy web interface kinda like free web hosting sites have where they will be able to add there domain and create there webpages whiteout affecting anything else on the server


I haven't even looked for years, it used to be that in Apache httpd a user could have a url 'http://your.domain.name/~yourbrother/' which would allow the 'yourbrother' user to have their own private page. All the files would be stored in /home/yourbrother/html or something like that without the need for special access and without the possibility of screwing up your main site.

> 
i found a few options i was wondering if any of u had experience with below options and can advice on what u would use

web min (is what i use probably to advanced )

below looks promising

[http://ajenti.org/](http://ajenti.org/) 
[http://www.ispconfig.org/](http://www.ispconfig.org/)
[http://www.zpanelcp.com/](http://www.zpanelcp.com/)

i cant make up my mind so hopefully someone here can help me out

---

### Post by do.marmor on 2016-08-03
TY both for your advice VM it is then, good idea about docker [COLOR=#000000]1clue[/COLOR], i not used it before but was just reading some on there homepage i probably try it out

> [COLOR=#000000]I haven't even looked for years, it used to be that in Apache httpd a user could have a url 'http://your.domain.name/~yourbrother/' which would allow the 'yourbrother' user to have their own private page. All the files would be stored in /home/yourbrother/html or something like that without the need for special access and without the possibility of screwing up your main site.[/COLOR]

u talking about redirects and sub domains , i was thinking about that to at first , i think i do that until they know what they doing ,
but in the future i want to find a simple web interface so they can add there own domain names and change setting affecting only there account whiteout me haft to do it all for them , might just try different interface systems on a test clone, most be something out there that works xd

---

### Post by 1clue on 2016-08-03
You might look into something like WordPress.  It's been awhile so there might be something more recent than that.

It lets you pick a look and then all the content is generated from text, so non-experts can do it.

What I described does not need separate domains or certificates.

Apache2 can easily host any combination of domains on a single box with a single IP address. I'm not an expert on the options, I only know what I've used.  Apache2 docs are verbose and easy to understand, and there are lots of examples of everything you might try. This forum will also have lots and lots of expertise on that.

---

### Post by 1clue on 2016-08-03
Another thing you might want to start with is a lamp server.  Lamp is Linux, Apache, MySQL, PHP.  This is so frequently used that Ubuntu Server has a pre-made configuration just for that.

For docker, look for "Ubuntu 16.04 LAMP". You'll find exactly that, and also a lamp with wordpress right under it.

Keep in mind that when you use docker, you don't want to modify the root image. Docker is growing incredibly quickly but my biggest issue with it was understanding that each dockerfile builds on the parents above it.  So I might have a LAMP server and a LAMP+WordPress, each of which use Ubuntu 16.04, and LAMPW presumably uses LAMP.  If you modify the bare image of the Ubuntu 16.04 image then it affects all the subsequent builds generated from it.

Another thing, I would recommend that you map your data and configuration directories over to your host machine, so that when your docker image gets upgraded your data stays with you. This makes the docker image essentially disposable since you can build everything you need in a few minutes with a single command.

Good luck and have fun.

---

### Post by mastablasta on 2016-08-04
maybe virtualmin or vesta cp. i dont' think zpanel is being actively worked on in fact wiki even calls it dead. 

Ajenti is something else and won't allow various installs. i mean it does have some apps and modules, but nothing compared to says cpanel and is more aimed at administering the server than for hosting.

have a look at this list if you find something.: [https://en.wikipedia.org/wiki/Comparison_of_web_hosting_control_panels](https://en.wikipedia.org/wiki/Comparison_of_web_hosting_control_panels)

---

