---
title: "Server for backup"
date: 2007-06-23
forum: Server Platforms
---

### Post by Inferno. on 2007-06-23
Hello, today i went to my work just to find out that we have been robbed. Affortunately the thiefs didn' take the servers, just some workstations (7) and lcd's (3). I'm planning in telling our boss to buy another machine (They bought today another 8 coreduo2 and 3 lcds) and make it a backup server.

Now, i never did something like that, can you give me a name of a software, guide, link, something? Maybe rsync/cygwin? backuppc?

Basicaly all the machines are XP in a domain, I suppose that there are like.. twenty, thirty machines.

Regards,

---

### Post by Maxtorm on 2007-06-23
Is your environment completely Linux/other *nix?  If so, rsync should handily accomplish what you're speaking of.  If you're in a mixed environment with Win boxes, rsync may have trouble on "live" files like databases. 

For tape or file backup, tar will do quite well. 

If you're looking at automating the task, Bacula ([http://www.bacula.org/](http://www.bacula.org/)) or Amanda ([http://www.amanda.org/](http://www.amanda.org/)) will make life easier for you.  Reasonably priced commercial options also exist, such as Arkeia ([http://www.arkeia.com/](http://www.arkeia.com/)).

---

### Post by coastdweller on 2007-06-24
He mentioned this already.

> **Inferno. said:**
> 
Basicaly all the machines are XP in a domain, I suppose that there are like.. twenty, thirty machines.

Regards,

---

### Post by Maxtorm on 2007-06-24
> **coastdweller said:**
> He mentioned this already.

Doh!  Sorry.  XP boxes should not be a problem for rsync.  Share out the directories you're going to backup and create smb mount points for them on the Ubuntu box.

Another option that I have only recently started dabbling in is the VMWare Converter ([http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)).  This will create a virtual image of a running machine.  If the machine dies, you can fire up the virtual image in VMWare and pull the data off however you like.  As I say though, we're just starting to dabble in it and it is more for complete recovery after a disaster than a day-to-day backup solution.

---

