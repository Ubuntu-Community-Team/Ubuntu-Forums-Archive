---
title: "Home Server with own Repo's"
date: 2007-06-07
forum: Server Platforms
---

### Post by nzruss on 2007-06-07
Hi there.  

I need some help / pointers on  something i have little knowledge about. 


[B]
Background: [/B] I'm about to set up a server share for my home network, (2x fiesty machines, 1x dapper (about to be fesity)  and 1x windows (about to be festy) 

More on my hardware[ is here:]("http://nzruss.blogspot.com/index.html#1727021280484810764")  


**Issue: **  As I have multiple machines running Fiesty, and I'd like the ability for the server to get the updates for all the machines so they are only downloaded once from the internet. Any tips on how to set this up or what to search for would be appreciated. (I'm just not sure what to look for?) The idea being that the server knows what packages are active on the machines and gets the ones that need updating, or when it gets a request it caches that request somehow. (just for repo's and ubuntu system updates, I dont want a full squid server). 


I found some info in the forum archives, but it appears to be about manually downloading repo updates... is [this ]("http://ubuntuforums.org/archive/index.php/t-7455.html")the best approach? 
[I]> [I]
It's best practice to put such a repository in a system-wide place, like /var/apt/ubuntu, and own it as root. Otherwise, the user pinco and any app run as pinco can inject apps onto your Ubuntu system.

and if you have several machines on your local network to update, then you should be able to share that directory using NFS or Samba (or whatever) and your other machines should then be able to see it so that you can then set them to use that exported/shared directory as a source (you will have to edit their sources list appropriately)[/I][/I]

---

### Post by keithweddell on 2007-06-08
Have a look at apt-cacher.  It should do what you want.

Keith

---

### Post by nzruss on 2007-06-08
Thanks, will do!

-------------

added: That is exactly what I was after. Thanks.

---

