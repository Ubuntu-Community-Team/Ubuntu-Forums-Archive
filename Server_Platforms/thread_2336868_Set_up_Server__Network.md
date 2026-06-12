---
title: "Set up Server / Network"
date: 2016-09-12
forum: Server Platforms
---

### Post by nisha4040 on 2016-09-12
Hey guys, I am new on ubuntu and i have been given a task to setup a small network along with servers which can support a small company for selling fruits

The internal network needs to be created using DHCP server and all the server needs to be given a static IP address

The servers are as follows:-

DHCP server
Web sevrer
IDPS
File server 

Can anyone guide me how should i start the task ?

Just need some guidance

---

### Post by howefield on 2016-09-12
Thread moved to the "*Server Platforms*" forum for a better fit and retitled..

---

### Post by Vegan on 2016-09-12
1 NAT is handled by network boxes 

2 servers can all be run behind the network box fine

LAMP handles all web appliance requirements

FreeNAS can make a lower cost storage appliance too

---

### Post by ian-weisser on 2016-09-12
Security habit: Do not put internal files on a public-facing system. Always assume any server may be compromised. Part of your job is to make those compromises few and far between, and to have good notes and versioned backups in place to restore from after a catastrophe. 

Start by creating the versioned backup server. Create a test VM. Create the backup server in the test VM. Create an offsite backup for the backup server.
Next, create the fileserver. Create another test VM. Create the fileserver in the test VM. Set up the user accounts and secure the services. Set up backups to the backup server. Import data onto the server.
Finally, create the webserver. Create another test VM. Create the webserver in the test VM. Set up accounts and secure the services. Set up backups to the backup server.  Import the website data.
Multiple VMs can operate on a single host, so you can easily do all this testing and networking on one laptop.

There. Now you know how to do it. Better yet, now you know how to fix it and restore it...since you took good notes.

Use those notes to set up your production systems.The production systems can be local hardware or offsite servers or cloud-based; the setup isn't terribly different from your VM test systems.

---

### Post by Habitual on 2016-09-13
> **ian-weisser said:**
> Always assume any server may be compromised.
I thought I was alone.

---

### Post by TheFu on 2016-09-13
> **Habitual said:**
> I thought I was alone.

Nope. I always assume my servers will be hacked at some point.  Versioned backups are mandatory to deal with that possibility. Don't be like [http://www.wired.com/2009/01/magnolia-suffer/](http://www.wired.com/2009/01/magnolia-suffer/) .

Unix systems are extremely flexible, so there isn't **1-way** to do anything. For example, I'd never use the "LAMP" config option - don't trust php web-apps enough and would much prefer postgres over mysql.  Personal decision, to be certain, but I see my job as a network and server admin primarily to avoid bad things and keep those things from happening to my users.  Never let a network/server issue impact users. NEVER.  That means making smart choices with the network architecture, security architecture, application architectures .... BEFORE bringing up any servers. We always say there are 500 different ways to accomplish ${X} with Unix. That number is low. ;)

Besides that, I pretty much agree with the posts above.

OTOH, there are all-in-one distros that do many of these things (google "clearos vs" to see options). Call it personal issue, but I haven't and never would deploy one of those. Might be something the OP is interested in.  Just know that putting too much into the same system is a liability.

---

### Post by Habitual on 2016-09-13
> **nisha4040 said:**
> Just need some guidance
[https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)

---

