---
title: "Technology choice for hosting multiple websites on single server"
date: 2015-01-20
forum: Server Platforms
---

### Post by tntteam2 on 2015-01-20
Hello there,

First, sorry for my bad english and maybe wrong forum category choice :)

I work in an university and one of my task is manage the hosting of websites we provide for our users / professors / research centers / etc.

Currently we host this using nginx as frontend server, apache as backend server (different server than front end), and ispconfig to create / manage websites. Basicly we offer disk space + mysql database, and users work with that to deploy their CMS or whatever they like.
This, is the infrastructure design I have to work with but I did not setup it.
I'm not a fan of this setup, first for security reasons, as 1 website attacked, the others are in danger so do the system itself.

I'm looking for infrastructure designs that would provide me 1/ ease to admin 2/security and 3/performances, as performances is not a problem nowadays. The target is about hosting 500 websites with medium - low activity.

First I was thinking about linux containers that I know (vserver), then looked about new stuff in this category and got to openvz, lxc and docker. Did the online tutorial of docker, seems nice but I see flaws in what I want (I may be wrong but updating packages inside docker apps seems one by one and not centralized ??).

What I'm looking for may answer all or partially the following requirments :

Host system and other containers best isolation for security
Possibility to limit container cpu/ram/disk/(network not mandatory as nginx frontend can do this work) assignment and real time usage 
Have a "mainframe" apache/php/mandatory libraries (like php-mysql) on host that get auto updated with ubuntu security auto updates and have all the containers benefit in real time of these security updates
Possibility to deploy different apache modules per container

Also creating / modifying / deleting containers using 100% command line would be very nice, as I could script things for ispconfig.

//secondary question

Also I'm open to suggestion for alternatives about ispconfig that would fit better my requirements. I don't need user access, resellers, email / dns management.
All I need is create containers of website with disk space, create user account inside it and give it sftp access, and create mysql db/user on separate sql server. Ability to reconfigure frontend nginx would be ++.
I don't need anything else, that's why I find ispconfig a little too much complicated/rich for this work.


Thanks for all the inputs you guys could give me :)

---

### Post by newbie-user on 2015-01-20
[Proxmox]("https://www.proxmox.com/"). It does linux containers, and supports clustering and high availability. It's based on debian, so you can script all you want.

---

### Post by TheFu on 2015-01-20
Don't use containers if you care at all about security. The technology isn't mature enough to know how secure any of those options are and with all the hype, I'm expecting an LXC/Docker webhost to be completely pown'd any day now.  I definitely wouldn't trust them in a university environment.  Stay with well-understood virtualization.  Perhaps openvz/proxmox is mature enough?  I've never used it but it has been widely available for a long time.  KVM or/and Xen **are** well-known, understood, ready for production use.  Don't know about a self-serve model for those, but ISPs must be doing somehow.

If you don't want to build this stuff yourself, use the "perfect server" setup from Falco. Don't know how to allow safe, user-managed, nginx config management, sorry. If you don't want DNS, don't deploy it.

Googled a little - opennebula seems interesting, but I don't know anything about it. Came across a top 10 or 20 cloud management article somewhere.

Definitely have the mysql on a different physical server. Don't think I'd allow any ssh access to it.

---

### Post by newbie-user on 2015-01-20
> **TheFu said:**
> Don't use containers if you care at all about security. The technology isn't mature enough to know how secure any of those options are and with all the hype, I'm expecting an LXC/Docker webhost to be completely pown'd any day now.  I definitely wouldn't trust them in a university environment.  Stay with well-understood virtualization.  Perhaps openvz/proxmox is mature enough?  I've never used it but it has been widely available for a long time.

Proxmox does containers and full virtualization. Best of both worlds.

---

### Post by SeijiSensei on 2015-01-20
As someone who might be a prospective customer, I'd prefer having PostgreSQL as an option, too.

---

### Post by TheFu on 2015-01-20
> **SeijiSensei said:**
> As someone who might be a prospective customer, I'd prefer having PostgreSQL as an option, too.

Postgres is definitely preferable to MariaDB, which is preferable to MySQL, but it is likely the school has standardized on mysql for student projects.   

The University where I gave multiple talks last year had never heard of Postgres or MariaDB - they are so MSFT-centric for almost all their IT/CS coursework.

---

### Post by tntteam2 on 2015-01-21
Hey there,

Thanks for the messages :)

Quick about MySQL : That's a question I've been thinking about. Today, the mysql server works and do what we ask him to do. For Postgre I believe apps needs to support it ? And I guess many webapps don't.
But I did think about MariaDB, as I believe it is 100% compatible with any mysql webapp ? But this is going to be a "next step" in the renewal of the hosting system. Today it's on a isolated server, tomorrow I want it to be a master/master cluster, but that's not the topic yet :)


Ok so you guys wouldn't recommend containers today for security reasons. So I believe I should try and run a proxmox system in virtualization mode / not container mode ?

About ""perfect server" setup from Falco" I don't really like all packaged solutions as they are often hard to customize and then upgrades breaks all modified stuff.
Also I'm not a fan of "cloud" systems.
What I'm looking for is really simple system, and I'm really close to make my own web control pannel that would do the work.
Basicly I only need to :
Create mysql db
Create the user
Create the storage to receive user's web files
Create sftp user
Configure the vhost on backend
Configure the vhost on frontend

Nothing more.

But I'm still unsure on how create the "user space" as I need to have it secure (receive security updates from the host) isolated (from other user spaces).

I'm going the check out opennebula and Proxmox, but proxmox NOT in container mode if I understood you guys correctly ?



EDIT :

Checked opennebula and proxmox but I'm not convinced. I think it will create overhead of running separated systems + these systems needs to be patched. Is there any solution for making 'cloud' of VMs that are childs of a main VM that would benefit from system upgrades of the main VM ?

What could work with a cloud system like for me :
I make a template VM with Apache, ssh keys, snmp, whatever needed.
I deploy 1 VM from this template for 1 website using customization like : IP, name, user account, name of the webserver
Then I update the template VM let's say I upgrade php package

Is there any solution to make the upgrade from the main template automaticly apply to child VMs ?

---

### Post by TheFu on 2015-01-21
Are you providing shared hosting
or
are you providing IAAS?
These are very different needs.

---

### Post by tntteam2 on 2015-01-21
Users request webspace for blabla.universty.fr
We create the space, configure frontend, backend, mysql, and send back to user sftp access so he can drop his wordpress or whatever he wants and he configure his webapps using the mysql informations we gave him.

---

### Post by tntteam2 on 2015-01-26
Bumping my thread for any ideas.

My question remains open :

What I need :
I make a template VM with Apache, ssh keys, snmp, whatever needed.
I deploy 1 VM from this template for 1 website using customization like : IP, name, user account, name of the webserver
Then I update the template VM let's say I upgrade php package

Is there any solution to make the upgrade from the main template automaticly apply to child VMs ?

Or  must I use paravirtualization systems ? Or containers can be upgraded  from parent containers ? Sorry this sound stupids but I'm not familiar  with all possibility of containers.

---

