---
title: "Server migration with all services from Ubuntu Linux 10.04.3 to 14.04"
date: 2015-01-06
forum: Server Platforms
---

### Post by Manirul_Islam on 2015-01-06
Dear All,

[SIZE=3][FONT=times new roman]I need a server migration with all services from Ubuntu Linux 10.04.3 to 14.04. I need a head ahead suggestion regarding this job. I am stuck in the loophole of backup  and recovery process by googling.

Thanks in advance.

Manirul Islam[/FONT][/SIZE]

---

### Post by nerdtron on 2015-01-06
This is will be hard. What are the requirements? timeframe? how much data are we talking here? Is there a new hardware available or you are going to upgrade the machine itself?
If you have a new server, then it's good. If you are just upgrading the current server to a new OS, be warned for hiccups along the way. There is a big chance that an in-place upgrade will make your server unbootable.
As always be prepared and always test before any migration of live systems.
1. Account all running services like apache, mysql, samba share, websites databases, and also know their configurations. Account also the user registered on the server.
2. Backup all data in the server, you should consult the users on which data is being used on the server, it's location and how is it acessed.
3. Ready the next server and try to install each application, service like the old server. (don't make this a production server yet)
4. Copy the data from the old server to the new server.
5. Test everything. Like are the website up? are the databases accessible? are the files/data accessible? Let the users access the new server and try to get feedback if something is wrong.
6. If all is well, then just unplug the old server and plug the new server on the network.

---

### Post by slickymaster on 2015-01-06
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by Manirul_Islam on 2015-01-06
Dear Nerdtron,

I have an old server of version 10.04.3 and a new hardware with server version 14.04. It has not much data. Approximately about 16GB. 

I'll let u know later about other services that I'm using.

Thanks for quick response.

Manirul Islam

---

### Post by TheFu on 2015-01-06
[http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview)

Between 10.04 and 14.04, a few things have changed. There will be more than a few manual changes needed and it is likely that a few packages you have depended on are not available anymore.  Resolve.conf is managed differently and there is a new version of Samba and Apache.  The samba changes could be nothing or complex, depending on the setup.  

Basically, the best recommendation i have is to practice the migration a few times (about 3 should be enough) and verify everything is working.  Take notes, perhaps create a script to help document it?

---

### Post by Manirul_Islam on 2015-01-07
I've divided these job into following fields:

-Planning
-Scripting
-Testing
-migration
-failure scenario
-live

Please provide me suggestion in every steps.

Thanks in advance.

---

