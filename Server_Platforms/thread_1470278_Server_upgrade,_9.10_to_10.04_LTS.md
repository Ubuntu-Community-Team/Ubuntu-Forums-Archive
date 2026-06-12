---
title: "Server upgrade, 9.10 to 10.04 LTS"
date: 2010-05-02
forum: Server Platforms
---

### Post by Loki57701 on 2010-05-02
Currently, I'm running Ubuntu server 9.10 and running samba, vsftpd, and openSSH. Should I upgrade to 10.04 since it's an LTS release? 

I've never done a server upgrade, so I don't know if its a good idea. The old motto "If it ain't broken don't fix it" comes to mind.

I guess what I'm most concerned about is that the upgrade will mess up one of the above mentioned services, or system settings like ufw, network, and cron job config's.

---

### Post by CharlesA on 2010-05-02
What I usually do if I want to "upgrade" is image the machine, then do a clean install with the new OS.

You can try running the upgrade and seeing if it works ok, but I prefer just doing clean installs, that way there isn't a whole lot of "leftovers" around.

YMMV ofc.

---

### Post by Loki57701 on 2010-05-02
Can you recommend a not-to-ridiculously-complicated way if imaging the system hard drive, lol?

---

### Post by Xianath on 2010-05-02
I'm in the same boat. Only, my server is completely headless (not even on-board video on it), and all of my workstations are diskless, booting off it. In other words, I have ONE shot at this :) I'll probably wait until I get a laptop, it will also give me a month or so for some post-release bugs to be weeded out.

---

### Post by CharlesA on 2010-05-02
I user clonezilla livecd.

---

### Post by Loki57701 on 2010-05-02
I forgot about CloneZilla, I've used that in the past. Thanks CharlesA.

Xianath- One question, why do you have that setup?

---

### Post by Bob P on 2010-05-02
I use Acronis True Image.  Works great.  will have to look at clonezilla.

---

### Post by Bob P on 2010-05-02
[http://en.wikipedia.org/wiki/List_of_disk_cloning_software](http://en.wikipedia.org/wiki/List_of_disk_cloning_software)

---

### Post by Bob P on 2010-05-02
Going back to the OP's question about whether or not to upgrade -- I am of the opinion that if your server is not broken, then you shouldn't fix it.  Continually updating places a working server at risk of being broken by an upgrade. If downtime is not a problem then go for the update.  OTOH if downtime is a problem then avoid it.

The only times that I'll update a server is when one of these conditions is met:

1.  A security breach has been discovered that presents a real threat, so an upgrade is necessary
2.  A problem has been encountered that requires an upgrade to repair it
3.  A new functionality exists in the upgraded software that doesn't exist in the current software, so an upgrade is necessary to obtain the new functionality.

IMO if you can't meet one of those criteria, then the decision should be not to upgrade a server.  I am presently looking at upgrading a Gentoo based server that I built in 2005.  The only reason I'm even thinking about replacing it is because of reason (3): I want to deploy new features and the system is no longer upgradeable due to its age.  So now its time for a complete OS rebuild.  Instead of completely rebuilding this server from source code using Gentoo, I'm currently auditioning packaged distributions.

WRT my personal opinions on Ubuntu Server 10.04 LTS, see my MOTD thread about a potential security issue.  I know that I should duck for cover as I say this, but I find the MOTD issue to be a deal breaker for Ubuntu.   I really like Red Hat Enterprise 5.4 or CentOS.

---

### Post by CharlesA on 2010-05-02
The only reason I can see to upgrade is so that you are running a LTS release. But that might just be my opinion. I'll be running Ludic until EoL Probably.

---

### Post by Xianath on 2010-05-08
> **Loki57701 said:**
> Xianath- One question, why do you have that setup?

Err... because I can? :) Really. To keep things quiet in the living room and bedroom, I have diskless HTPCs there (alas, not fanless, but at ten feet the ION fan is inaudible). The server is shoved somewhere where its four 120mm fans and twelve disks can purr happily. Other benefits include being able to use LVM snapshots for Windows backup (much, MUCH more efficient than what Windows 7 has to offer), having all my data and OS'es on RAID6, and the sheer performance of it. The beast easily sustains enough IO throughput to saturate a gigabit link. Finally, the theoretical and practical aspects of this setup provided enough material for two Master's theses, one of which I had been postponing for five years.

Overall, the benefits outweigh the possible upgrade pains of which, I have to admit, I've had none so far. It started with 8.04 LTS and has been upgraded to 8.10, 9.04 and 9.10 without so much as a hiccup that I can recall. I just watch the forums for a month or so and if nothing outrageous comes up, I bite the bullet.

---

### Post by cariboo on 2010-05-09
I would give it about 3 months before considering an upgrade, that way most of what some would call showstoppers have been dealt with.

The unfortunate thing is that during testing the server version gets neglected, as no one wants to be constantly updating it (2 to 5 times a day), and in many cases re-installing the software weekly. It's to bad, as the devs are coming up with some really cool enterprise features, that will eventually filter down to us home users.

---

### Post by Xianath on 2010-05-10
No sooner than an hour after my last post, my server went down. If I were (more) religious, I'd say I had been reminded very vividly of the sin of pride (it's time like these that I am, in fact, more religious than my usual self). Anyway, since I had to plug a keyboard and video anyway (and mcgyver a standard profile bracket for it in the meanwhile), I bit the bullet and did a distribution upgrade. No hiccups with the actual upgrade process.

The boot process, however, would get stuck in mountall if it couldn't find a filesystem listed in fstab (ouch!) or an iSCSI target (double ouch!!!). Kind of a nasty thing for a server, methinks. Interestingly enough, and perhaps completely unrelated, my caps lock key wouldn't work when that happened. It took six hours to figure out hot to get past mountall. Since I have no fix other than removing all remote and removable filesystems from fstab, I'll be seeking help in a separate topic and likely log a bug if confirmed by others.

The fact the tftpd-hpa replaced (but backed up) my config was a piece of cake. Also, my root filesystem got damaged a little somewhere along the line of not-so-clean reboots, but hopefully not beyond the point of repair (still going through lost+found, about 20 files in there). Overall, for a home server, it went quite smoothly.

---

