---
title: "Random system freeze, Ubuntu LTS on VMWare Server 2.02"
date: 2012-05-22
forum: Server Platforms
---

### Post by Javik on 2012-05-22
I have a very simple LAMP Ubuntu LTS webserver, running "CMS Made Simple" on VMWare Server 2.02 (free edition) for the past four years or so.

It's been stable for years and years, but occasionally crashed due to running out of disk space due to logs overflowing and backups accumulating.

Lately however the system has become increasingly unstable and will occasionally randomly completely lock up and the GUI goes unresponsive.

For a while the Update Manager has been saying an upgrade to a new LTS release is available, so I copied the virtual machine drive to retain the old system, then did the upgrade. All through the process it would say, "changed config file found, keep old config?" and every time I'd say no, since the differences were not made by me.

So it appears the system is fully up to date, with all the global config files of the new LTS version, plus my CMSMS and it works properly .,.... but still freezes solid occasionally.

This last week it has frozen up literally every other day. Not good when there are staff that depend on it being available.

It seemed like this could be a GUI graphics driver problem, so I set up alternative access. It did not help. I haven't ever seen a need for SSH, but installed it last week and left the system logged on through PuTTY to the shell prompt. When the system froze, both the GUI and the SSH prompt were unresponsive.

I hate hard-resetting a system running a MySQL database since it risks database corruption, but I have no other choice apparently.

I am contemplating building a brand new "clean install" Ubuntu LTS virtual machine and reinstalling CMSMS and the MySQL database on it, though before I do that, I should ask if there are any known problems with LTS and VMWare Server 2.02.

---

### Post by LHammonds on 2012-05-22
I'm not an expert on anything Linux or VMware Server, but I have been  running Ubuntu Server 10.04 LTS and 12.04 LTS as well as performing  in-place upgrades and out-right re-building a new 12.04 server in order  to migrate data/services from a 10.04 server.  All of this experience  has been while using it inside a VM running VMware's ESXi server 4.1.

I  have not found any stability issues with the server except when I was  initially trying it out inside Oracle's VirtualBox.  I'm not sure if it  was Virtualbox or Ubuntu or a combination of both but it was utterly  miserable trying to setup a 10.04 server to run Zimbra last year...that  is until I installed Ubuntu on ESXi and at that point, the stability  problems went away completely.  No more utterly random and  insanity-induced glitches.

I have dedicated servers running  Nagios, MySQL, Apache/MediaWiki, Apache/phpBB, Zimbra,  MineCraft/CraftBukkit, Zentyal CUPS printer and all of them running  Samba for file-sharing across different platforms.

So, with that  all said, my 1st recommendation would be to copy your VM to a different  PC and see if it will run in a stable manner on a different box to rule  out hardware issues such as bad ram/hd/psu/etc.

Once the problem  is isolated to just inside the VM, the next thing I would do would be to  re-build a new VM and see if you can make a similar stable platform  using the exact same versions of software you are running in your  original VM.  If it remains stable, try migrating your data to the new  VM and see if it continues to be stable.  If so, simply start using the  new VM as your primary service.

Once stable on the current  system, you can then start looking at creating a new VM with updated  software if you want to go that route (or simply duplicate the system  and see if an in-place upgrade will actually work).

I prefer  making new VMs from scratch when a new release comes out and migrate  data rather than trying to migrate in-place.  Too many variables can be  introduced during an upgrade (as you have seen) and the more complex  your system, the more complex the upgrade can be.  A migration of my MySQL database could not have been more simple going from a 10.04 server to 12.04...check my sig for the thread and look at the migration steps I did to transfer the database and make it live.  EASY!

When troubleshooting, always try to isolate potential problems to rule them out or prove the case.

LHammonds

---

