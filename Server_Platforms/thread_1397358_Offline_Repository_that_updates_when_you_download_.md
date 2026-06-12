---
title: "Offline Repository that updates when you download for the first time"
date: 2010-02-03
forum: Server Platforms
---

### Post by elexhobby on 2010-02-03
Hi,

We have a server and four computers/users connected to it all using ubuntu. The internet connection that we have is pretty slow. 

Is it possible to create a local repository on the server such that whenever some user downloads a package for the first time, the server also creates a local copy of the package. This way, later when another user wishes to download the same package, the server checks if it already has a local copy, and if yes, sends the user this local copy. This way the user won't have to wait long for the package to be downloaded from the online repository.

I read that it is possible to create an offline copy of the entire repository, but that would be very huge.

I'm sorry if this is a naive question. But I'm a newbie to system administration, and any suggestions regarding where to search for would be very helpful.

---

### Post by ICEB3AR on 2010-02-03
This should be interesting to you:
[https://help.ubuntu.com/community/Apt-Cacher-Server]("https://help.ubuntu.com/community/Apt-Cacher-Server")

---

### Post by Lars Noodén on 2010-02-03
As ICEB3AR writes, apt-cacher is very likely to meet your needs.  I've used it in such a situation to good effect.  A few things to look for.  

First, make sure that the cache is large enough so that if one machine loads files early on, they are still there in the cache by the time the last machine needs them.  Update one machine, then when that has finished update a second machine while watching the logs using tail -f to be sure.  If you see 'MISS' then the cache was too small.  

Second, if you are going to need the files in a hurry, you can pre-cache by running an update on a single machine prior to when you need the files.  That is more important in a classroom lab or something similar.  

Third, if speed is of importance (such as in a classroom lab) be sure that there is enough bandwidth on your LAN.  Many switches allow *x* Gb/s for each connection but if your server has only one connection, then that *x* is divided by the number of connections.  So accessing the apt-cacher server in stages will help.  For example, if you use a cronjob for your update, stagger each machine's scheduled time so that they don't run all at once.

Fourth, you might be able to mix apt-cacher with [apt-p2p](http://manpages.ubuntu.com/manpages/karmic/en/man8/apt-p2p.8.html) so that the network load is spread out among many machines and the one apt-cacher server is less of a bottleneck.

---

### Post by elexhobby on 2010-02-04
Thanks ICEB3AR and Lars Noodén for your replies. Lars, I do not entirely understand the problems and solutions you've described, but I'll google stuff.

apt-cacher is exactly what I was looking for. I tried it and its working. I have one more question though.

I do not want to maintain all the packages on the server, but instead on any of the client machines. i.e. if I want to download a package, my machine should check if any of the users have already downloaded the package. If not, it should access the online repository.

Right now, I have entered the ip address of my machine in the /etc/apt/apt.conf.d/01proxy file as specified in the link. So now, when any user downloads a package, my machine is checked first. How do I configure it so that all the client machines will be checked before downloading a package? I tried repeating the line 
Acquire::http::Proxy "http://<IP address or hostname of the apt-cacher server>:3142";
in the file /etc/apt/apt.conf.d/01proxy with a different ip address on each line, but that did not work. Any additional changes I need to make?

Thanks.

---

### Post by thecoshman on 2010-02-04
I have looked into this same thing. As far as I can tell, the cache works like a proxy would.

Say you decide to add a new package, the package is downloaded through the computer running apt-cache, and saved their for a while. If any other machines try to download this new package, I believe they will automatically get served the cached copy from the server.

The package caching server will have a copy of every package and ever updates that gets requested by any client in the network, it dose not matter (I believe) if the package is installed on the cache server or not.

You can also configure it so that the clients get these cached server automatically with out any settings up (unlike if you mirror an entire repository). I think this works by setting the firewall wall to redirect to the cache server first, which then downloads the requested update.

I would love to know how you get on with this, as I too will soon be needed such a service.

---

### Post by Lars Noodén on 2010-02-04
> **elexhobby said:**
> 
I do not want to maintain all the packages on the server, but instead on any of the client machines. i.e. if I want to download a package, my machine should check if any of the users have already downloaded the package. If not, it should access the online repository.


Apt-p2p will go out to peers first.  
[http://www.camrdale.org/apt-p2p/faq/](http://www.camrdale.org/apt-p2p/faq/)

With apt-cacher, it will only keep what one of your clients has fetched via apt-cacher.  Even then it will keep it only until space is needed.  Again, check the cache settings to make sure you have space for the files fetched.  The clients will check the cache and the cache will check the real repository to see if the file is still fresh.  If it is not, or if it is missing, then it will be downloaded.  When room is needed, files are removed on a FIFO basis.  See [expire_hours=0](http://manpages.ubuntu.com/manpages/karmic/en/man1/apt-cacher.1.html)

So, it *should* work (haven't tried that combination yet) to have apt-p2p go via apt-cacher.  I can't think of many cases that would be so very useful, but it might be.  One case would be if you do an installation, erase the clients and do the same installation again.  

Not all packages are available via the main repository, I always have to get opera from the Opera.com repository and [mononono](http://tim.thechases.com/mononono/) from its site.

---

### Post by richlyn9 on 2010-03-06
check this [http://rxezlqu.wordpress.com/2010/02/15/updating-ubuntu-on-slow-connectionsoffline/](http://rxezlqu.wordpress.com/2010/02/15/updating-ubuntu-on-slow-connectionsoffline/)

---

### Post by elexhobby on 2010-04-02
Hi,

Sorry for the delay in getting back. I had other pressing issues to deal with.

Here is where I am currently:
I have 3 clients A,B and C and a server. For apt-cacher purposes, I have made A act as the server i.e. whenever B or C want to download a package, they first check if A already has the package. If yes, B/C download it from A. If not, download it from the internet.

What I want to achieve is the following:
If any of A,B,C want to download a package, it should check if any of the remaining two have already downloaded it. If yes, download it from the client having the package, if not, download it from the internet.

A possible solution that came to my mind is: Right now, if B or C want to download a package, they check A first. If A doesn't have the package, it is downloaded from the internet. Can I set up things so that when B or C download the package from the internet, they also store a copy of the package on A, so that whenever any other client wants to download the package, it will be available with A, which is the only computer that's probed.

@Lars Noodén:
I'm trying to figure out how to configure and use apt-p2p, but I haven't found good help/documentation.

---

