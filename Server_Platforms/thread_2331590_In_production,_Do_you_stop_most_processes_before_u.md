---
title: "In production, Do you stop most processes before upgrading the packages?"
date: 2016-07-23
forum: Server Platforms
---

### Post by negora on 2016-07-23
Hello:

When I need to upgrade the packages installed in my servers, I always schedule a maintenance period during which most services are turned off (I usually reboot the machines after that). This means that I've to notify my clients in advance, so that they notify their own users. It's a very tiring task. Specially when I've to upgrade the packages of a host machine that runs several virtual machines, because I need to count with the approbation of everybody. But that's not always possible and, very often, I've to postpone the upgrades for another time. In addition to that, when I reboot the machines, I've to verify that all the existing daemons have started properly, among other checks.

**I know that you can upgrade the packages while the applications and daemons are running.** Because the old versions of the files are kept in disk (and maybe in memory) while they're in use. Indeed, that's what happens in any typical GNU/Linux system although you stop the most processes. Because always there are some essential processes that must be running, which also are subject to upgrades. Otherwise, a GNU/Linux system couldn't upgrade itself without rebooting.

But, in my opinion, the least processes are running, the smallest is the possibility of a crash. Specially if there are processes that handle data that can become corrupted, such as database servers. I know that the updates in stable distributions usually contain security patches and bug fixes only, so they don't change the ABIs. But still... I'm a little paranoid. Furthermore, some updates cause that the daemons are restarted automatically, which makes things even worse.

So my question is: What do you do in your production servers? **Do you stop as many processes as possible before upgrading, with the corresponding downtime? Or do you upgrade with all them running? If you do the later, Do you choose manually those upgrades that won't cause an automatic restart of the process?**

In my case, the only thing that I do to make the upgrade process more agile is downloading the upgrades very often, but without installing them (apt-get -d upgrade). That way, when I do the real upgrade, it will be done faster.

Thank you!

---

### Post by Vegan on 2016-07-23
most tasks are loaded into memory so the executables can be replaced no problem
restarting deals with reloading tasks etc

---

### Post by TheFu on 2016-07-23
I don't stop services or reboot unless necessary. If they need to be stopped, the package install will handle it. Check whether rebooting is needed after all the systems are patched. Rebooting after patching is something Windows admins do.  My Unix admin background taught a different method - don't reboot unless it is necessary.

Only manage about 30 servers now - small operation.  Have standing downtime scheduled for nightly backups (2am-3am) and every Saturday morning from 4am-6am to patch.  If I don't need the time, fine, but it is available and doesn't impact many people. Nobody works at that time on these systems. Actually, I get more grief over the backup windows than anything, people like to work late sometimes.

If anyone is working and is impacted, they understand why.  On my small systems, backup outages usually take 1-2 minutes per system. Less with LVM snapshots on the newer machines. I didn't always use LVM, so there are some services which have to be down the entire time the backup runs for that machine. 

And running an apt-cache-ng server so patches are downloaded once on the network, saves some download time.

If I'm on the .1 LTS release, I run update/upgrade and that's it. Nothing special.
If I'm on the .2, .3, .4, .5 releases, then update/dist-upgrade and that's it.
New released are tested on non-production environments for a month before use anywhere important.

After all the updates are done, a small script checks whether any systems need rebooting. Usually patching everything is finished in less than 15 minutes - 20 min if reboots are needed.

---

### Post by negora on 2016-07-24
> **Vegan said:**
> most tasks are loaded into memory so the executables can be replaced no problem
restarting deals with reloading tasks etc

Thanks for your answer. I've one question with regard to your first sentence. Are dynamic libraries loaded at once, when the process is run for first time? Or could it happen that a hypothetical executable with version 1.0.0 (the old one) could load a library with version 1.0.1 later (the new version), during its execution? Usually, versions 1.0.0 and 1.0.1 of the executable and the library share the same ABI and wouldn't crash, but... That's one of the matters that worries me more. That some executable "sees" a library with a newer version than it should be and something bad happens.

> **TheFu said:**
> I don't stop services or reboot unless necessary. If they need to be stopped, the package install will handle it. Check whether rebooting is needed after all the systems are patched. Rebooting after patching is something Windows admins do.  My Unix admin background taught a different method - don't reboot unless it is necessary.

...



Thank you. So you schedule a maintenance period anyway, although you don't stop the services or reboot the machine? During that period of time, Do you tell your users not to use the services at all, or you just warn them that the services could stop working randomly (although in practice it doesn't happen often)?

And one more question... When you update the libraries that affect some service, Do you restart it so the changes take effect? Or do you let it running until you are forced to restart it? Because in that case, it wouldn't have much sense to update, Right? 

**I've a serious problem to schedule the downtime.** I've customers from different countries, so it's very difficult to set a time in which they ALL almost don't use the servers. When the users of a client are sleeping, the users of another client are at work. That's a problem when they use virtual machines and I've to update the host machine. Even some of my customers have, in turn, customers from different countries too. So it's a nightmare. That's why I was considering updating the systems while they are running.

---

### Post by TheFu on 2016-07-24
Maintenance downtime is a standing thing.  Backup downtime is a standing thing. I don't have to schedule anything - except when the system is first brought online.
Backups take services down, daily, so if there are any patches applied, those get restarted during the backup period, if I don't bother to reboot the box.  Most of the time, it is 5 minutes even though 1-2 hrs are scheduled. It isn't a big deal. If they can't access the service, a coffee break or toilet break and it will be back up when they return. That's the practice.

If the systems needed to be up all the time, then I'd have duplicate systems on opposite sides of the planet and budget to support sub-15 minute async data replication. If the systems were doing financial transactions, it would be synchronized data replication and every transaction would be slower due to that requirement.

Unreasonable demands don't help anyone.

How did you discuss RTO/RPO with the clients for DR needs?  We use a spreadsheet to set expectations. Single computer systems only promise 96% uptime. That leaves over 6 hours/wk of unplanned downtime.  That is what the written agreement says - we've never had that much unplanned downtime, but it is there and we are protected if it is needed.  We don't over-promise, but we do over deliver what their budget supports.  If their RTO/RPO are extremely low, then they have to provide the proper investment to support those numbers. If they don't, then we don't change the written agreement.  Putting it in writing is important. Clients can be pissed about downtime, but if they don't provide the proper funding to reduce it or eliminate it, that's not our problem and I don't lose any sleep about it.

Sounds like the current setup doesn't allow you to provide what the clients want. Hopefully, you can renegotiate the contracts to be realistic.  I wish you luck.

---

### Post by negora on 2016-07-25
> **TheFu said:**
> ...

I've liked and enjoyed your message. It has made me think a lot. And I've came to the conclusion that I'm trying to offer more than what I wrote in the contracts.

It's very complicated to avoid downtimes with a single physical machine. If they want an availability that is near 100%, they should pay for that. I guess that I became too obsessed about this matter, as if it were something granted implicitly. But no, it isn't. In later contracts, I'll try to be more explicit about this topic.

Thank you!

---

