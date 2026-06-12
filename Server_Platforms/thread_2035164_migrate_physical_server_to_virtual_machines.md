---
title: "migrate physical server to virtual machines"
date: 2012-07-30
forum: Server Platforms
---

### Post by neuling1 on 2012-07-30
Hello all,

Currently we have one Server, which is running following services - Typo3,vBulletin,FTP,Wiki and SVN

This should be changed to the following setup:
one virtual server for Typo3 and vBulletin
one virtual server for FTP and the Wiki
one virtual server for SVN

Which way would be the best to migrate the existing server configuration and the neccessary data of the physical machine to the virtual ones? What I've read so far, is that one possible solution is to copy the files via ssh (scp command) from the old to the new system.

Is this a good way to do this or is there a better solution?

Thanks!

---

### Post by continuous on 2012-07-30
I would virtualise the physical server in triplicate and then remove the components you don't want from each virtual server, rather than risking not finding all the configs and files required for a specific server....just a thought.

---

### Post by neuling1 on 2012-07-30
> **continuous said:**
> I would virtualise the physical server in triplicate and then remove the components you don't want from each virtual server, rather than risking not finding all the configs and files required for a specific server....just a thought.

Ok, and what is the best way to do this, just cloning the whole system? Could I make it like described here...
[http://eggsonbread.com/2010/01/28/move-ubuntu-to-another-computer-in-3-simple-steps/](http://eggsonbread.com/2010/01/28/move-ubuntu-to-another-computer-in-3-simple-steps/)

Another point is, that the old system runs ubuntu 8.10 and the new one ubuntu 12.04, so I don't know if this could lead to complications.

---

### Post by continuous on 2012-07-30
Neuling1, I'm not so sure it is a good idea to mix to actions - migrate and upgrade at the same time. You are virtualising, so all you need to do is capture the image from real hard disks to equivalent virtual ones. I would use something like partimage for this.

Once you have it running as a VM, then consider upgrading it one version at a time - it's a relatively long way from 8.10 to 12.04...

The way described in the link will probably work too, but I personally wouldn't have the confidence that I could find all the bugs and fix them with that approach - you may find it easy though - horses for courses.

---

### Post by thnewguy on 2012-07-30
There are tools to convert physical machines into virtual ones. You could probably use something like partimage or Clonezilla to do this, but I'd recommend looking at dedicated tools for this sort of conversion.
[https://en.wikipedia.org/wiki/Physical-to-Virtual](https://en.wikipedia.org/wiki/Physical-to-Virtual)

---

### Post by neuling1 on 2012-07-31
Thanks for the answers guys,

my problem is mainly, that I more or less have to do a migration and upgrade at the same time. The admin in our company set up 3 virtual machines running ubunut 12.04 and gave me access via ssh to the old server which is running ubuntu 8.10.

and he want's the old services to run on the new servers, as I already mentioned. So somehow I have to manage it, to put the old 8.10 server config onto the new 12.04 server...so I don't think that an image is the solution.

Is there any other way I could accomplish this?

...or should I just tell my admin, that we should install the 8.10 version on the virtual machines -> put image of old system on the virtuall machines -> update virtuall machines from 8.10 to 12.04?

---

### Post by Cheesemill on 2012-07-31
I really wouldn't attempt upgrading 8.10 to 12.04, there have been so many changes that you  are more than likely to break something.

Also there is no straight upgrade path from 8.10 to 12.04 , you would have to upgrade each machine 4 times:
 8.10 > 9.04
 9.04 > 9.10
 9.10 > 10.04
10.04 > 12.04

The best thing to do in this situation is to set up each VM with a clean installation of 12.04 and then set up the services you need from scratch, only copying across the data you need for each service.

Take a good look at the documentation that was written when the original server was set up along with any current installation and migration guides for the services, such as:

[http://www.hostucan.com/webmaster-tutorials/how-to-migrate-vbulletin-site](http://www.hostucan.com/webmaster-tutorials/how-to-migrate-vbulletin-site)
[http://www.dmitry-dulepov.com/2008/06/migrating-typo3-installation-to.html](http://www.dmitry-dulepov.com/2008/06/migrating-typo3-installation-to.html)

Doing any sort of upgrade from 8.10 to 12.04 is likely to be unsuccessful and will only create more problems in the long run, a fresh install is definately the best way forward.

---

### Post by neuling1 on 2012-07-31
Thank you Cheesemill,

this was exactly what I was looking for. Hope there won't be any trouble because of the different ubuntu versions...

I will definitely try that and let you guys know if it worked.

---

### Post by LHammonds on 2012-07-31
If I were in your shoes, I would not backup/restore a physical to virtual.  It would be best to build your virtual server in the virtual environment (no legacy physical drivers and such to worry about).

But since you are also wanting to upgrade the OS as well, cheesemill has already mentioned the long upgrade path and each upgrade can present its own problems.  If you are not very familiar with each upgrade/OS, you might be better off setting up a 12.04 virtual server and getting each of the services setup and running (to get familiar with how the services work in the new OS).  Once you are familiar with setting up the service in the new OS, the take a look at how to migrate the data and configuration.  You might be better off configuring the services the same way they are in the original system rather than trying to figure out how to "migrate" the actual config files.  The historical data/log files will also have to be examined and figured out how they can be made to be accessible in the new system.

Unfortunately, there is a lot to figure out.

* Virtualized OS
* New version of the OS
* New versions of the services
* How to setup and maintain the new services
* How to configure the new system like the old system
* How to get the old data into the new system
* Possibly new backup/restore procedure for the virtual servers

LHammonds

---

