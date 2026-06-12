---
title: "wireless home server, access via mac"
date: 2009-07-16
forum: Server Platforms
---

### Post by jovianchiron on 2009-07-16
i am looking to start a linux setup (ubuntu 9.04) to use as a home server, and i need help with direction as far as documentation on setting something like this up. although i am still new to linux, i am willing to take a vast amount of my time to learn any needed material.

a pc i have built will hold various data and a large amount of multimedia, which i'd like to be used while on the pc or through the network connection on one of two macbook pros. in other words, i am looking for a standard jaunty ubuntu setup to use for home use and as a base i can access through a wireless connection. with what i have gathered so far, it seems as if i can partition off my harddrives in such a way to run ubuntu, a nice temp storage, and another partition that can be accessed via a wireless connection.

it would be very helpful to have any documentation or advice directed here so that i can learn what i need to set this up or get my information straight.

---

### Post by Waappu on 2009-07-16
Hi

I hope you find this somehow useful
[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by jovianchiron on 2009-07-16
so it would be far more efficient to use ubuntu server edition?

---

### Post by Waappu on 2009-07-16
> **jovianchiron said:**
> so it would be far more efficient to use ubuntu server edition?

It depend your needs. You can install all those features also to desktop edition.

Guide is just how you can install e.g. ssh, file server and so on

---

### Post by Belnoctourne on 2009-07-16
server edition is much more effecient but if you aren't very comfortable spending all your time in console and mouseless it isn't your best bet, if your just serving out files to essentially yourself and a few other computers what you want to do is just install a version of ubuntu desktop (I always advise the version right before the current one which I beleive presently is 8.10) look for some walkthrough's for your version of ubuntu on how to set up the following things and if you get all of this working you'll be very happy with the result

ndiswrapper - if your wireless drivers dont work already
(hope very hard that they do)
samba - for your file sharing with windows machines
afp - for your file sharing with mac's
dhcp-server - if you need to serve dhcp
bind9 - dns if you need it done locally
masquerading and nat - if your box needs to share your internet connection out
deluge - my favorite bit torrent client, you can run the gui portion on any os and connect directly to it and add torrents just liek you would any other local program so you dont need to vnc over
vnc - its a nice tool to have so you can remote in
apache2 - webserver
iptables - for your firewall (its harder but much better)
if you find your in terminal a lot bind your windows key to launch terminal

cant think of anything else at the moment, good luck!

---

### Post by rbishop on 2009-07-16
One place I use from time to time for reference is:

[http://www.howtoforge.com]("http://www.howtoforge.com/")

---

### Post by jovianchiron on 2009-07-16
excellent. thank you very much! this is laid out very straightforward, and i can figure out the technical stuff as i go.

---

