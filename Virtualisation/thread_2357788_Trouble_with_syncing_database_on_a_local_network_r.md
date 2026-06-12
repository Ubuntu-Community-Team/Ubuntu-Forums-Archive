---
title: "Trouble with syncing database on a local network running windows 7 under vbox"
date: 2017-04-06
forum: Virtualisation
---

### Post by therrera1550 on 2017-04-06
Hi all,

I have three windows 7 workstations and 1 Lubuntu laptop running a vbox virtual machine with windows 7 in the vbox.  All are running a contact management software called Act!.  version 11.0 (under windows 7).  One of them is the database server which is setup to sync with the workstations.  They all work fine syncing except for the laptop Linux machine running Act! under a windows 7 vbox.  I get an error message saying that the local database is unable to contact the sync server and fails when attempting to sync.

I thought it might be a firewall issue so am running the sync server and the laptop Linux machine with the firewall disabled on each.  No firewall enabled in the laptop Linux pc, no firewall in the vbox windows 7 virtual machine on the laptop and no firewall enabled on the sync server itself.  I can freely ping back and forth between all workstations without issue.  The sync still fails as if something were blocking the data from the laptop or to the sync server.  I can freely browse between shares on each machine and create folders, copy and delete files remotely via the shares so I know there is communication going on between them.

Anyone have an idea what is going on or where I might look for the problem?

Any help is greatly appreciated,

thanks in advance

---

### Post by howefield on 2017-04-06
Moved to the "*Virtualisation[lubuntu]*" forum.

---

