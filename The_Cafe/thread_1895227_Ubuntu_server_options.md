---
title: "Ubuntu server options?"
date: 2011-12-14
forum: The Cafe
---

### Post by jesushero on 2011-12-14
I used to run my own server at home for my website, but since I moved this is no longer possible. I am looking for a server somewhere to host whatever was on my old server.

I don't need more than 10GB of hard drive space currently, but I do need plenty of bandwidth, SSH access, the ability to install/remove/update any server software, and the server to be in a fairly civilized country with fast internet connections. 

I run a basic LAMP, SVN repositories, FTP with several users, icecast radio streams, IRC chat server, and want to also set up a mail server.

Apart from the MySQL databases, most of the hard drive space is taken up by music, video and image files, which are regularly uploaded and downloaded. It includes video tutorials, music, electronic schematics, and stuff like that.

It is for a project that deals with free software and open hardware, and offers a limited number of services to fund itself. 

Our budget is very limited for our website, as we prioritize our projects. Is renting a dedicated server the best way to go? Or is there better options out there? 

Up to now I have been offered server space for free by many different people who like our projects, but it is usually something along the lines of "send me the data and I'll put it up", but we need to be able to update stuff regularly, and since it is a group of several people doing this, it would quickly turn messy if it has to go through too many different people until it is up. So unless we can have several ssh and ftp users on the server, to work on it themselves, it won't really work out.

Thanks in advance for any help or advice.

---

### Post by BrokenKingpin on 2011-12-14
Look into [www.GoDaddy.com](www.GoDaddy.com), they have some pretty good prices for web hosting. You will just have to check to see if they provide all the servers you are looking for.

---

### Post by sandyd on 2011-12-14
> **jesushero said:**
> I used to run my own server at home for my website, but since I moved this is no longer possible. I am looking for a server somewhere to host whatever was on my old server.

I don't need more than 10GB of hard drive space currently, but I do need plenty of bandwidth, SSH access, the ability to install/remove/update any server software, and the server to be in a fairly civilized country with fast internet connections. 

I run a basic LAMP, SVN repositories, FTP with several users, icecast radio streams, IRC chat server, and want to also set up a mail server.

Apart from the MySQL databases, most of the hard drive space is taken up by music, video and image files, which are regularly uploaded and downloaded. It includes video tutorials, music, electronic schematics, and stuff like that.

It is for a project that deals with free software and open hardware, and offers a limited number of services to fund itself. 

Our budget is very limited for our website, as we prioritize our projects. Is renting a dedicated server the best way to go? Or is there better options out there? 

Up to now I have been offered server space for free by many different people who like our projects, but it is usually something along the lines of "send me the data and I'll put it up", but we need to be able to update stuff regularly, and since it is a group of several people doing this, it would quickly turn messy if it has to go through too many different people until it is up. So unless we can have several ssh and ftp users on the server, to work on it themselves, it won't really work out.

Thanks in advance for any help or advice.
Alright. Lets see....

These days, VPSes (Virtual Private Servers) are quite cheap. Good ones will go about ~$15/mo. 99.99% of hosts will have Ubuntu. If you use nginx instead of Apache, you could stash that all into a box with 512mb ram. Besides, nginx response time is faster. If you want, theirs also some managed options out there.

The best thing to do is to get them on promotion. Theirs a bunch of promotions you can go through at [http://www.webhostingtalk.com/forumdisplay.php?f=104](http://www.webhostingtalk.com/forumdisplay.php?f=104) , but you will want to do a bit of research on the provider as well. The main problem people seem to have with VPSes is I/O Latency. With that many people on one server, the latency can get quite high.

Dedicated servers are an entirely different thing all together. These days, the cheapest (and still reliable), will go for $50/mo. Check with worldstream, joe's datacenter, and leaseweb resellers such as HostPlate (don't go with leaseweb themselves, they have horrible support). Try Kimsufi.ie if your in USA. Or use the other domains if your elsewhere.

Dedicated servers are a bit better in the regards that your the only person on the server itself, but they are much more expensive. The support is always a bit slower, but the resources that you have are guaranteed, which ensures that you don't have stuff like the I/O Latency I mentioned earlier. Some companies are also a big PITA, and don't offer a "reboot" button, or an "reinstall OS" button, where the SolusVM Panel used in most VPSes nowadays have it. Those companies will require you to submit a ticket to get the server rebooted if you don't have something like an APC Remote Reboot module or something. Not really a problem in most companies, but a bit anoying. If you order extra IPs, you have to set them up yourself (i.e. through /etc/network/interfaces ). VPS images are auto-configuring, and will setup the IPs automatically.

If your site is going to be up for long term, and you want dedicated, a good idea is to go colo. You can pick up the parts at newegg (or whereever), and assemble a 1U server, and ship it off to colocation. Colocation can easily be found for $50/mo. The only problem then would be that if hardware fails, you are going to have to either pay the datacenter to replace it, or send parts in yourself.

In that case, most of the failures involve the hard drive. I would reccomend getting two of those SAS Enterprise HDs (make sure the motherboard supports it). Their equal on speed to SATA3, and their made to run 24/7, unlike normal HDs. Their a bit expensive, but a good one-time investment. Put them in RAID 1, so that if one fails (unlikely), your server will still be up while your getting the new HD. Otherwise, just get the normal Enterprise-grade HDs, and put them into RAID 1.

Theirs also a nice list of dedicated server promotions here -> [http://www.webhostingtalk.com/forumdisplay.php?f=36](http://www.webhostingtalk.com/forumdisplay.php?f=36)

---

### Post by CharlesA on 2011-12-14
I've heard of Linode before, seems pretty good.

---

### Post by Primefalcon on 2011-12-14
I'd say unless you need dedicated go godaddy, if yo need dedicated, at that point it's starts to become cheaper to do it yourself

---

### Post by Ctrl-Alt-F1 on 2011-12-14
Virtual Servers are the way to go.  You get dedicated server resources unlike with shared hosting.  They are reasonably priced in comparison to renting an actual server/data center space.

Because it's a virtual machine you can install and run anything you want pretty much as long as you have enough RAM.  If you're running a Linux server with PHP and MySQL, you should be able to get by with not too much.

*Sounds like sandyd has first hand experience with virtual servers. My experience is mostly second hand.  I definitely don't recommend shared hosting if you have a significant number of visitors or plan to do any processor intensive tasks like web services.

---

### Post by CharlesA on 2011-12-15
> **Ctrl-Alt-F1 said:**
> 
*Sounds like sandyd has first hand experience with virtual servers. My experience is mostly second hand.  I definitely don't recommend shared hosting if you have a significant number of visitors or plan to do any processor intensive tasks like web services.

Aye. Shared hosting is great for a small site, but if you are doing a medium or large site, dedicated is the way to go.

---

