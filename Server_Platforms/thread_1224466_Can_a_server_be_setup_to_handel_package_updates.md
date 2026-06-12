---
title: "Can a server be setup to handel package updates?"
date: 2009-07-27
forum: Server Platforms
---

### Post by majdi on 2009-07-27
Hi,

Can a server be setup to handle package updates for all client desktops running ubuntu? 

The idea is to have the package update process automated for only critical or necessary updates.

Your feedback on this is appreciated......

---

### Post by sherl0k on 2009-07-27
two methods: first one is having a server in the building act as an aptitude server, the second method has all the clients using regular apt servers. the first method requires only the server to have an internet connection, the second method requires all the clients to have one.

method one:

1. install apt-mirror and apache on your server. your server will need close to 40-50gb of space, since the server will hold every package update like a real apt server.

2. sudo ln -s /var/spool/apt-mirror/mirror/us.archive.ubuntu.com/ubuntu/ /var/www/ubuntu

this will symlink the directory that holds all the packages, to /var/www. you can also change the apache conf to set the root location to this, but i find this easier (unless you're already using apache and have stuff in /var/www)

2. set up all your clients to connect to your server's IP for updates. this can be done in /etc/apt/sources.list - i hope your server has a static IP. 

3. edit /etc/apt/apt.conf.d/50unattended-upgrades and uncomment the lines for what set of updates you want to be downloaded and installed automatically. mine looks like this:


```
Unattended-Upgrade::Allowed-Origins {
	"Ubuntu jaunty-security";
	"Ubuntu jaunty-updates";
	"Ubuntu jaunty-backports";
};
```

you can remove the repos you don't want by just deleting the lines.

method 2:

just do step 3 from above. this method is taxing on your bandwidth and on the repo's bandwidth, because instead of having one server download all the updates and then pushing it out via LAN, you're having x amount of computers grab the same updates over one WAN connection. it would also be slower unless you have some crazy pipe and/or not a lot of clients.

hope this helps!

---

### Post by majdi on 2009-07-28
That sounds great, has anyone tested this with ubuntu 9.04?

---

### Post by sherl0k on 2009-07-30
I'm doing it right now actually, using a server with 2 NICs - one is on the private LAN and one on the public internet.

---

### Post by majdi on 2009-08-01
sherl0k, are you using 9.04, and what's the feedback so far? How is it running?

---

### Post by cariboo on 2009-08-02
Using apt-mirror to update system on the network is a little much for most people. [Apt-cacher]("http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher"), is much better for what you are wanting to do.

---

### Post by sherl0k on 2009-08-03
> **majdi said:**
> sherl0k, are you using 9.04, and what's the feedback so far? How is it running?

Runs beautifully :) Haven't had an issue yet!

> **cariboo907 said:**
> Using apt-mirror to update system on the network is a little much for most people. [Apt-cacher]("http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher"), is much better for what you are wanting to do.

This is another option too. I wasn't sure if my main server was going to require packages differing from the other servers on the network so I opted to go the mirror route.

---

