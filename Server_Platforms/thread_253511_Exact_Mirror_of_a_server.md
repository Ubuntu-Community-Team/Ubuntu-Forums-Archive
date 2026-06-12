---
title: "Exact Mirror of a server"
date: 2006-09-08
forum: Server Platforms
---

### Post by egraham on 2006-09-08
I have two Dell Servers that are exactly hardware  wise.  I already have one set up as a file server on a Windows network.

What I want to be able to do is make an exact copy of that server onto the other server as a backup, and keep it up to date with rsync.

I have yet to find a source that explaines how to do this.  Does anyone know where i can find a source that walks me through setting this up or give me some pointers on how to set it up?

Thanks
Eric

---

### Post by Uluen on 2006-09-09
Maybe [Partimage]("http://www.partimage.org/Main_Page") will do the trick?

---

### Post by insane_alien on 2006-09-09
partimage would do it but updating would be manual. he's on the right track with rsync but i'm not sure how it would be done.

---

### Post by Macchi on 2006-09-10
(Sorry, the post became quite long)
With help of rsync, cron and a ssh-server you can regularly synchronize the contents of two machines at a suitable pace. Rsync is supposed to be very efficient and I believe that for many applications it is acceptable to perform synchronizations a few times per hour, thus reducing the load.  

An example for testing is:
```
rsync -av --stats --dry-run -e ssh username@machine:/source/directory/path/ /destination/directory/path

```

Later you can change it to 
```

rsync -av -e ssh username@machine:/source/directory/path/ /destination/directory/path

```

Finally you could insert that into a script called regularly by cron. 

There are lots of trade-offs to consider: Home directories could be synchronized quite often, but you could be more conservative about /etc with the configuration files, being careful about what has to be excluded from updates. There is a special case when software could be updated on one machine and not on the other due to the random nature of availability of Ubuntu package repositories on the internet.
During update both machines are subject to additional loads (network,cpu,memory) thus it might be good to alternate rsyncs on both machines.

Observe the useful options "--dry-run" for testing "--stats" for statistics, and "-e ssh" for encrypted transfers through SSH. The destination and sources can be on different machines, therefore the "user@machine:/directory notation"
  
There is also a minor catch to be observed: "rsync /origin /destination" syncronizes the contents  of origins and the origin directory itself. Using "rsync /origin/ /destination" syncronizes only the contents of origin. On the destination   
 
Additional comments:
A more sofisticated solution would also have a daemon that monitors a heartbeat signal between the machines. In case of failure of the primary server then its IP address is spoofed by the secondary server, that later takes over the operation. Recovery of the primary server probalby requires manual intervention (?). Hardware redundancy is also desirable, specially double network connections to avoid single points of failure.

There is a high-availablity project at [http://www.linux-ha.org/](http://www.linux-ha.org/)
and high performance clusters at [http://www.linuxhpc.org/](http://www.linuxhpc.org/) 

There are many solutions for high availability but unfortunately I have not had time yet to experiment with them. I use software RAID 1 on my server and have a reserve machine (actually my desktop application server) that is not completely synchronized due to hardware differences.

---

### Post by egraham on 2006-09-13
Ok...so I do my rsync...If my primamry machine goes down, how do I change the name and IP address for my backup machine so I don't have to remap to the backup machine for everyone?  ie:
My main machine is named Primary with IP 1.1.1.1, my backup is named Mirror with IP 1.1.1.2, how would I change the backup to be named Primary with IP 1.1.1.1?

Also so that my Windows users were able to access the shares on the Ubuntu box I had to do a useradd and also add them to teh Samba upassword database, how can I ensure these get copied over?

---

### Post by Macchi on 2006-09-13
This is only a fst sketch of a solution, hope it helps as a starting point. Later we may refine this. There are at least two solutions a,b,c1 and a,b,c2 (to start with):

Your machines have fixed IP addresses x.y.z.1 and x.y.z.2

a)Test the rsync manually with dry-run, verbose and statistics 
Create two script for synchronizing for instance the /home catalogs from 1 to 2 and from 2 to 1

b)Add lines with the times and scripts at /etc/crontab.
man /etc/crontab will give you an explanation of the syntax.

Machine 1 runs one rsync towards machine 2 every hour at hh.05, hh.25 hh. and hh.45.

Machine 2 runs one rsync towards machine 1 every hour at hh.15, hh.35 hh. and hh.55.

This would provide one synchronized copy every ten minutes thus distributing the load among both machines.
Observe that I avoid hh.00 and hh.30 in case other jobs would start 

c1) Upon a problem, the manual solution would be to change IP address for machine 1 to 3 and 2 to 1. Thus machine 2 takes over the main role in your network and you can repair machine 3. When problems are fixed it can be conected againand will become machine 2. 

c2) A more sofisticated approach: Use a DNS-server (a third machine?)
Rsync operates with the fixed IP-addresses but all the services are only accessed by name towards a DNS server.
The DNS server has the IP addresses of both machines for the same name but at different priorities. Normally it directs the access to the first machine. If something happens the first machine and it does not anwer, then the second would answer right away! For instance you can remove or reboot the first machine and if everything turns out to be ok then it will take over again as the main server.

I have to elaborate more this later on. This arrangement would allow a hot stanby.
Software updates should not be simultaneous to avoid the risk of one update breaking both machines. You could the same period but alternate when to update or you could have one machine that is updated every week and the othe every second week.

---

