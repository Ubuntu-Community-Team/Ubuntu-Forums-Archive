---
title: "Ubuntu Teamspeak Server auto start (as a runlevel)"
date: 2007-05-18
forum: Server Platforms
---

### Post by amlucent23 on 2007-05-18
I have set up and made a teamspeak server of my very own on ubuntu desktop edition (wanted a gui sorry). I followed this [guide]("http://ruckman.net/tech/2007/05/17/setting-up-and-securing-a-linux-teamspeak-server/") to do it. I would prefer the teamspeak application to start up on boot and turn off on shutdown, to run as a runlevel in short.  In the guide the author has me using chkconfig but alas it is unavailable in ubuntu. I see now that several of the config files made through this guide are dependant on chkconfig. Is there an easy way for me to adapt this guide to ubuntu? Also how come I can not just add a service to services-admin (gui). (one thing I love about suse... a gui runlevel editor)

Any advise is appreciated guys

---

### Post by brigux on 2007-05-24
... Just copy the demon (teamspeak probably)  in /etc/init.d then S99teamspeak and K99teamspeak in each rc.d folder.
(just a thought)

---

### Post by williamruckman on 2007-10-09
try using **update-rc.d**

It is very similar to chkconfig in red hat related distros.

Write a script. put it in the /etc/init.d/ directory.
Lets say you called it FOO. You then run

% update-rc.d FOO defaults

You also have to make the file you created, FOO, executable, using
$chmod +x FOO

You can check out
% man update-rc.d for more information. It is a Debian utility to install scripts. The option “defaults” puts a link to start FOO in run levels 2, 3, 4 and 5. (and puts a link to stop FOO into 0, 1 and 6.)

Also, to know which runlevel you are in, use the runlevel command. 

Thanks, William Ruckman ([http://ruckman.net](http://ruckman.net))

---

