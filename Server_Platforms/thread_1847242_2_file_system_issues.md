---
title: "2 file system issues"
date: 2011-09-20
forum: Server Platforms
---

### Post by superspinner on 2011-09-20
Server: ubuntu 8.04.4 (virtual machine running on ESX)

1) Last night at 8pm our monitoring server registered an SNMP alert for this server.  I tested, and both ssh and SVN were unresponsive.  I used virtual center to access the console, but, again, I couldn't login to the machine.  I rebooted.  This morning users complained that their data from yesterday afternoon was missing.  I looked around, used find -mtime on some directories that I know were written to yesterday and, indeed, all yesterday's writes/creates were gone.
Any ideas?

2) When I run df, three separate disks show up as exactly 80% used.  There are about ten disks, and I find this awfully coincidental.  No disk is higher than 80%, however, in the past we've gotten alerts from our monitoring system about some of these disks going over 80%.  The alerts were usually cleared within a few days so I figured the users cleaned up after themselves.  Maybe I was wrong.  I don't believe there is any quoting installed.
Again, any ideas?

This server has been up for a few years without giving us any trouble, but these experiences have me worried.

---

### Post by An Sanct on 2011-09-20
That's an odd problem :)

As it is a VM, has the host got enough resources? Are there any other VMs running on it? 
Sharing resources can sometimes make a guest act 'sick', guest expects real HDD, CPU and RAM, yet does not get it ...

If the 80% thing is for real, that might be a bug ... 8.04 is not maintained any more, so I would recommend to upgrade to the last LTS (10.04)

---

### Post by Porcini M. on 2011-09-21
> **An Sanct said:**
> 8.04 is not maintained any more, so I would recommend to upgrade to the last LTS (10.04)

Server LTSs get 5 years support, as opposed to the 3 years for desktop versions.

---

### Post by An Sanct on 2011-09-21
Ubuntu 8.04's support **ended** on 12 May 2011 for desktops[]("http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#cite_note-HardyEOL-54") and **will end** in April 2013 for servers.

That is soon ... better switch to 10.04 soon, there is no extremely big difference between the two (no gnome-unity clash, ...)

---

