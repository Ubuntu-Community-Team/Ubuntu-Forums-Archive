---
title: "Live / Instant rsync for master slave setup"
date: 2011-02-08
forum: Server Platforms
---

### Post by Lord_ on 2011-02-08
Hi everyone,

I need to perform instant filecopy between a pair of servers. Its loosely based on a master slave setup as we have ucarp floating a virtual IP between the two. services are on both boxes (tftp, apache)

I'm happy with that, I now need a way to instantly sync files from set directories, as we could see problems if files have changed should the system fail over without being in sync

I know I could cron *\1 but I don't want it running EVERY minute, in any case, if the change was within the last minute, then it wouldnt have the change anyway.

I think it can be done with rsync daemons on box boxes, but I can't find a guide to to this. ATM the slave has been setup to accept rsync from the master, so i just need the config to have all changes on the master instantly replicated

any ideas? I'm not *totally* against moveing away from rsync, IF there is a really good alternative.

Thanks,
Joe

---

### Post by rubylaser on 2011-02-08
How about using lsyncd? 
[http://fak3r.com/geek/howto-build-your-own-open-source-dropbox-clone/]("http://fak3r.com/geek/howto-build-your-own-open-source-dropbox-clone/")

This is pretty easy to setup, and works very well.

---

### Post by Lord_ on 2011-02-08
Thanks, this looks good. I did actually see this project on my googling earlier, but at the time it seemed a bit excessive. Now i've searched a bit more, im pretty sure rsync can't do what I want so i'll give it a try now.

The nice thing is, as I have rsyncd working and ready to receive on the slave, there won't be any need for change on that side. so I can just configure and go

---

### Post by Lord_ on 2011-02-08
Yep works nicely I can confirm that. I installed lsyncd 2.x instead of the version shown in the guide so I had to had to play about with lua dependencies. The guide is a good starting point, even for that version

(apt-get install lua5.1 liblua5.1-dev ) The -dev IS needed

I also had to build a config in lua, NOT XML, but there are some guides in the examples/ dir from where you build. If anyone reading is put off by this don't be. the config is MUCH simpler than the old xml style.

Had a good few tests and it does everything i want and quickly :)

---

