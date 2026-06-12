---
title: "Is ubuntu server right for this?"
date: 2010-05-18
forum: Server Platforms
---

### Post by gday301 on 2010-05-18
I want to set up a home web server.  The server will be for testing a site mainly, and also allowing select people examine and test the site remotely.  This is not meant to be production.  I would like to also use this server on my home network if I can make it work securely. I am new to ubuntu.  I will be using drupal for most of the development.  I am running on a fast comp but the HD is not that big (using an old one I have).  

Basic set up is a 60gb hd, AMD 64 bit processor 1 gig memory.  I am not looking to be blazing fast on it. I just want it to work with minimal server maintenance.  In fact what I really want is something I can set and forget, It won't have monitor on it even.  Just need it secure. I will probably install a control panel for ease, something like openpanel (suggestions welcome here also).  A gui would be nice for setup since I'm new to linux and the terminal.  The only use on my network may be serving files to my htpc if I add a bigger HD or my external HD (not sure if I'm doing this or not).  Mainly a testing server.  

Anyway mainly a test server that needs to allow me to have non local people on my team log in, look at my work and try to break my site.  Then after testing I will migrate my sites to the real servers.  I'm interested in linux and learning more but time wise I need a solution that doesn't make me spend my time on the server work, since my main concern will be the actual sites, hopefully I will be able to play with the server stuff more later to optimize etc.  

Is there such thing as an install package that I can spend an afternoon on just to get a secure server, and then later add things and customize? (wish full thinking probably)

And no I don't want to use windows because I will be migrating to a linux server and I am trying to emulate the future environment of my sites as much as possible. Also I kind of hate IIS.  

thanks
Greg

---

### Post by Jakob Lundberg on 2010-05-18
Ubuntu server should do nicely for your needs.

I'm not familiar with server guis, but some like webmin.

If you want to make it more secure you should try to remove packages and services that are not needed. There is no obvious solution as it depends on what you need to have on the server.

---

### Post by terazen on 2010-05-18
If you're going to use a server in the future that's cli only I'd use cli now personally.  If I remember correctly, drupal is mostly just the web interface besides occasionally using the cli to download and add things.

One thing I'd test now with linux is how to optimize the server for a high number of users and running backups.  Automysqlbackup is pretty good.

---

