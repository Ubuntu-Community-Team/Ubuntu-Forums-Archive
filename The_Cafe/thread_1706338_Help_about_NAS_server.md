---
title: "Help about NAS server"
date: 2011-03-13
forum: The Cafe
---

### Post by achmed744 on 2011-03-13
Hello, i am pretty new to this so i decided to ask before doing anything. I want to buy a NAS server, probably the Western Digital My Book Elite 1500 GB. And this is what i want to know: 

1) I readed on internet that the NAS servers are capable of running webserver and mailserver - Is the WD My Book Elite capable of that too?

2) Again :D I readed on internet that there is OS similiar to Linux and there is a FTP and SSH access, if is that true, probably i can run some apps on it and what i want to know is: If it has SSH access, can i run there something like a game server? More accurately a Counter Strike server? And has all of that the  WD My Book Elite?

And is ANY NAS server capable of this? :D 

Thanks for responses and sorry for my stupidity and maybe bad english, i'm from Czech Republic. :D

---

### Post by PartisanEntity on 2011-03-13
I have bad experiences with NAS servers.

I used to have a LaCie NetworkSpace. It had a very limited control panel.

Now I use an old laptop that's running Ubuntu, I use it for:

- file server across the network smb and afp protocols)
- TimeMachine backups for my iMac and MacBook
- media server to watch movies on my TV

Using an old laptop and Ubuntu may be the better/cheaper option with loads of features and functions.

---

### Post by handy on 2011-03-13
I used the FreeBSD based FreeNAS for about a couple of years. It never let me down, it was very specifically built for NAS. The more tricks you put into your NAS box the more vulnerable it becomes to both security issues & failure. The reason I stopped using it was due to the energy usage of the machine I was running it on, that was just way too powerful for the job.

[http://en.wikipedia.org/wiki/FreeNAS](http://en.wikipedia.org/wiki/FreeNAS)

I've been using a ReadyNAS Duo, for a year this month. I bought it drive less & added a WD Green 1.5 TB drive, doing it this way was much cheaper. 

It can take 2 drives; 2 drives are automatically set up to be in RAID-1 (mirroring) config'. Which I consider to be a great waste of a drive & a perfect way to duplicate corruption & use more power. 

You can also set the Duo up to have 2 RAID-0 drives which means that when one is full you can add another for more storage space. This is what I do.

The Duo is a great torrent slave via a Transmission add-on. Their forum is terrific for sorting out any problems that you may have. It runs with windows, OS X, & Linux, with variety of network protocols that can be run in whatever combination. You can backup from it to another USB drive via its USB ports. You can create a website & show all your photos on it (I've never bothered using this). You can't play games on it as it is built to do what it does & has a very energy efficient Sun CPU & runs a cut down version of Debian which you will never see.

You access the configuration of the ReadyNAS via a browser interface from a client. Sophisticated permissions can be used & backups configured including Time Machine for OS X. 

Anyway, if it sounds interesting have a search & you will find out more...

Good luck.

---

### Post by themarker0 on 2011-03-13
Spend a little more for a thecus nas. There hasn't been one issue with that unit since the day i bought it, three years ago.

---

