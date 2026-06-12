---
title: "Active Directory Integrated DNS with BIND Secondaries"
date: 2013-01-29
forum: Server Platforms
---

### Post by Resilldoux on 2013-01-29
Hello,

So I'm currently setting up a lab so that I can figure out how to integrate BIND9 DNS servers into an existing Windows domain with their own AD-Integrated DNS zones. I'm trying to set up a BIND DNS server to either forward it's queries, or to pull the zone from a Windows DNS server on a Domain Controller so that it can respond to queries itself.

Either way, I wish to have my clients that send their queries to my Ubuntu BIND9 DNS server and have them answered one way or another so that they can reach other devices on the network by name and surf the web in general. So far I haven't been very succesful; I did manage to vaguely pull a zone that didn't require secure transfers (from a M$ DNS server that is), but I eventually messed up so my server so I had to restore a snapshot.

I'd like to eventually set something up that uses DNSSEC so that zones are transferred secure enough. For the last couple of hours I pretty much turned Google inside-out, but didn't find anything useful, so maybe some of you guys managed to do something similar to this? Perhaps maybe link me a guide or push me in the right direction?

---

### Post by SeijiSensei on 2013-01-29
First, if you're just setting up secondaries for an internal network, I don't see much need for DNSSEC.

Usually all that is needed to create a secondary is to add an entry to named.conf for the zone like this:

```

zone "example.com" {
     type slave;
     file "zone.example.com";
     masters { 10.10.10.10; 10.10.10.11; };
};

```

The semicolons matter; BIND is very picky about syntax.

You must tell the AD server that the BIND machine is a legitimate secondary.  By default most DNS servers will only transfer files to defined machines.  In BIND, for instance, there is the "allow-transfer" directive in named.conf.

---

### Post by Resilldoux on 2013-01-29
Thank for replying, I'll try to do that shortly. I agree there's little need for DNSSEC, but I would like to know how to set that up in my lab, just for kicks really.

I trust that the square bracket at the end should be a curly one?

---

### Post by SeijiSensei on 2013-01-29
> **Resilldoux said:**
> I trust that the square bracket at the end should be a curly one?

Oops.  Thanks.  I fixed it in the orignal in case someone else reads this thread.

I can understand wanting to learn, but I'd start by getting the primary and secondaries working before tackling DNSSEC.

Don't forget to restart named after changing named.conf.  You can do either "sudo killall -HUP named" or use the "service" command.  If all works correctly, you'll see the transfer logged in /var/log/syslog.

---

### Post by Resilldoux on 2013-01-29
Great, so after allowing zone transfers on the Windows DNS zone I was able to pull that zone to my Ubuntu BIND9 server. I can see that BIND stores the zone in /var/cache/bind/<filename> as specified in the /etc/bind/named.conf.local file.

Is this where it's supposed to be? I went through several guides on the interwebs and they have a habit of storing the zone files where the named.conf files are stored (/etc/bind in my case).

---

### Post by SeijiSensei on 2013-01-29
That depends on the distribution.  I don't run Ubuntu servers; I use CentOS.  Like all RedHat flavors, it runs named in a chrooted "jail" under /var/named/chroot.  The configuration is in etc/named.conf and the zone files under var/named below the chroot directory.  It's all a matter of taste at some point.

---

### Post by Resilldoux on 2013-01-29
Right, thanks for explaining. Come to think of it, I've been a little too complacent with using Ubuntu all the time...

Anyway, I think I've now successfully set up a BIND secondary and I'm currently figuring out how to transition it into a Master. Eventually I would like to have my clients  automatically register themselves to the zone on the BIND server. I then would like to see the Windows DNS servers dynamically adding/updating these records to their zone copies.

I can think of a couple more ideas to expand on this mixed environment (like a chroot jail as you mentioned to improve security), so it's a good thing I'm actually having fun doing this, hehe.

Any help is more than welcome.

---

### Post by SeijiSensei on 2013-01-29
So you would make the Ubuntu server the primary and the AD the secondary?  I don't think that would play well in AD systems.  The Active Directory server wants to be the DHCP/DNS server and manage all the addresses on the network.  I had a client switch to AD a couple years back, and we had to make the AD server the primary.  Before that we had a Linux box providing nameservice on the network.  Then we converted it to the AD's secondary.

If you do want to subvert the AD architecture, then you should look into installing the ISC DHCP server which has hooks to communicate with BIND.  That provides the same kind of dynamic assignments and naming that AD does.  Still I would be loathe to encourage any efforts to escape from the iron hand of MS in modern Windows networks.  It's all so integrated that I'd be afraid of breaking everything by changing something as fundamental as name service and address assignments.  That's why MS maintains such a powerful hold over corporate networks.  It's all so integrated and so proprietary precisely to make it hard to modify or leave.

Converting the BIND secondary into a master isn't that hard.  Usually the transferred zone files can work as the primary without modification.  You'll see that the "@" at the top of the primary zone file will be converted to the domain's name, and there will be some additional $ORIGIN statements that may not appear in the primary.

---

### Post by Resilldoux on 2013-01-29
Couldn't have said it better myself. Microsoft sure does a good job keeping their own stuff tightly integrated with each other. All the more reason not to tamper too much with it, nor was it really my intention.

I don't necessarily wish to replace the Windows primary server, but instead find a solution for both of the servers to dynamically update the same zone. One zone with both Linux clients registering to the BIND server, and Windows clients on the other side registering to the Windows DNS servers.

My plan is to find a way for all hosts to register themselves within the same zone.

Is this a viable angle to work on, or would you suggest something else so that both environments would have full knowledge of all the DNS names in the network? Maybe even maintaining different zones if my idea is crazy-talk?

---

### Post by Resilldoux on 2013-01-30
I finally got something to work which enabled me to dynamically update the BIND server with clients connecting to it. On the other side the Windows clients registered without any problems to the Windows DNS servers, like usual.

But here's the kicker, both the BIND server and the Windows DNS server know about each other's records. I set up two separate zones to distinguish between the Windows clietns and the Linux clients. The BIND is the master for the "linux" zone and The Windows DNS servers remain the primaries for the Windows DNS zones. Then I configured the BIND as a slave server for the Windows zone and vice versa for the linux zone.

My mixed workstations and servers can happily talk with each other.

For larger environments I think I might consider forwarding-only BIND servers and stub zones on the Windows servers, or something like that.

Thanks for all your support.

---

### Post by SeijiSensei on 2013-01-30
That's a clever solution, but don't the hosts now have names like ws1.linux.example.com and ws2.windows.example.com?  It probably doesn't matter much as a practical matter if the workstations do not need to communicate among themselves, or if you simply need to identify workstations with their users.  Otherwise ordinary users will always have to know whether a machine they need to reach is in the linux or the windows subdomain, yes?  

I presume servers still have names like mail.example.com?

---

### Post by Resilldoux on 2013-01-30
Well, in my test lab my Windows machines still reside in my lab.local zone, whereas the Linux machines are now being placed in my new linux.lab.local zone. The Linux machine names differ from the Windows machine names, but thanks for pointing out that caveat. That could be a problem.

Darn it, I thought I had it but I guess I'm still trying to get my head around designing a nifty DNS solution for a mixed environment, haha.

Maybe I can statically place my servers in the lab.local zone and have all of the clients (WIndows and Linux) being placed in a clients.lab.local zone? I think I can set up an ISC BIND9 + DHCP server as the master for the clients.lab.local and forward all of the queries outside its zone to the servers in the lab.local zone. I can then set up a conditional forwarder or a secondary zone on the servers in the lab.local zone to reach the clients in the clients.lab.local zone.

Oh well, back to square one. :)

---

### Post by SeijiSensei on 2013-01-30
Why don't you just let the Active Directory server handle DHCP and nameservice for all the machines?  It certainly can give out addresses to Linux boxes since DHCP is an open protocol.  The problem comes in getting the machines to announce their hostnames to Windows. You might want to take a look at [likewise-open]("https://help.ubuntu.com/community/LikewiseOpen") which is designed to help integrate Linux systems into a Windows environment. It might also be possible to use nmbd from the Samba suite to handle announcements, but I'm hardly an expert in these matters.

---

### Post by Resilldoux on 2013-01-30
To explain a little what started all this: I thought of how I could design a small business network for starting and young companies that don't have a very big budget te spend on IT. As we all know, doing everything Microsoft can be an expensive hobby to say the least, especially for the small and starting organizations. So after earning my LPIC-2 I was wondering how I could use my new skills to address the common budget problem by using Linux solutions for some of the things that would have otherwise been solved with costly Microsoft based solutions.

Things started to pop up in my head like Linux desktops, LTSP, LAMP, SAMBA and something with postfix and dovecot perhaps as an alternative for Exchange. As for integrating the Linux boxes in AD, I though I'd give the free Centrify Express a try, but I haven't tried it yet. Then I found that, indeed, annoucing the Linux hostnames was a pretty painful process, so I decided to have some BIND servers in the network as well to tackle that issue.

Maybe Centrify or Likewise could provide a solution to have the Linux boxes announce their hostnames to the Windows DNS, but I also wanted to work with BIND a little more, so I thought I could integrate it with the Windows DNS servers, just to see how it would look.

Turns out that's a tricky process as well, but on the positive side I learned quite much from the past couple of days. Experimenting like this also trains me and forces me to use Linux which I rarely get to (actually never) on the job.

---

### Post by Resilldoux on 2013-01-30
To sum it a bit up: I just like to experiment and think up these scenario's where Linux might provide a nice alternative to some other popular, but costly solutions. That, and it's quite fun. :)

---

### Post by Resilldoux on 2013-01-30
Ok, so Centrify Express works like a charm. It enables me to add tons of different Linux distributions in Active Directory and they register themselves to the Windows DNS servers. For more advanced features (like Group Policy enforcement) you'd have to upgrade to the paid versions, starting "at $65 per workstation and $385 per server for Standard Edition, with discounts for volume purchases. "

When using Linux desktops I guess you probably would want to go for the Standard edition to be able to lock down the workstations from a central management platform. But when you're just adding Linux based servers to the environment I guess the Express Edition would suffice for most of your needs (which is free as in beer!).

So it can be done and compared to a full blown Windows environment at could well pass as a less expensive alternative.

[IMG]http://img580.imageshack.us/img580/1457/74279696.png[/IMG]

---

