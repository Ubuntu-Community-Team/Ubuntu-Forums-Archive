---
title: "Something broke after power outage"
date: 2015-06-26
forum: Server Platforms
---

### Post by michael298 on 2015-06-26
Hi all,

I'm fairly new to Ubuntu (coming from a Windows Server world), but about a year ago I setup a small Ubuntu 14.4 Server running LAMP on VMWare ESXi.  Everything has been running flawlessly until yesterday when we had an unexpected power outage.

When the server came back up, I noticed that the website runs fine for displaying static pages, but whenever it needs to display a dynamic page that connects to the MySQL db  it always fails with a  "[2003] Can't connect to MySQL server error (110)".

And yet I can connect just fine to the MySQL instance on the production machine both remotely (using the MySQL Workbench tool) and locally using straight command line on the server itself, and I can run queries with no problems. Netstat tells me port 3306 is open. 

The problem is that it simply will not connect to the database from  the web server running on the production machine, it will however work perfectly fine if I  connect to the MySQL DB from a  different web server running the exact same code. In other words, if I run the website from the production server, I get a connection error when querying MySQL, but if I run the exact same website from a different machine while still pointing the MySQL connection to the production server, everything works fine.

As far as I can tell there are no firewall rules in place blocking MySQL, and as stated earlier, it worked fine for an entire year before the power outage.

So my guess is that something got corrupted, but I am at a loss as to where to start.  I'm not savvy enough with the Linux CLI tools do any thorough diagnostics (I'm more at a beginner-intermediate level in terms of knowledge of the CLI), and I'm not even sure what I'd be looking for anyway. At this point I feel the problem lies somewhere between Apache, PHP, or perhaps some hidden firewall setting.  

Any ideas on what else I need to check? I've already tried running apt-get update and upgrade to no effect. I've checked the my.cnf file numerous times and networking is enabled, port number is correct, nothing there seems out of place, especially since I can connect to it from everywhere else. 

If all else fails, is there a way to do the equivalent of a "repair" install of the LAMP stack without losing all my settings?

Thanks in advance.

---

### Post by TheFu on 2015-06-26
There aren't any hidden firewall settings - **sudo iptables -L** shows them all.

Have you run **fsck** against all the file systems yet? Did it fix any errors?

Perhaps now is the time to restore from the backup from the night before? That is the normal way to "repair" things on Unix - restore from a backup.

---

### Post by michael298 on 2015-06-26
> **TheFu said:**
> 
There aren't any hidden firewall settings - **sudo iptables -L** shows them all.

When I run iptables, it show nothing listed in any of the chains (INPUT, FORWARD, OUTPUT)



> 
Have you run **fsck** against all the file systems yet? Did it fix any errors?

When I enter the fsck command I get a warning that it "***WILL*** cause ***SEVERE*** filesystem damage." So I'm not sure I want to go there.


> 
Perhaps now is the time to restore from the backup from the night before? That is the normal way to "repair" things on Unix - restore from a backup.

Well I do have backups of the database, but not of the OS itself

---

### Post by TheFu on 2015-06-26
fsck is a basic tool for all Unix systems. You need to learn to use it.  It cannot/shouldn't be run against a mounted file system. The easiest way to get around that is to boot from alternate media - like a liveCD environment, then run it.  If you try to run fsck on a mounted file system, it will warn you (like it appears it did).

[http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html](http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html) shows how to handle most partitions, except /.

If all you need is to run fsck on the / filesystem - run **sudo touch /forcefsck** then reboot - at the next boot, it will run fsck before mounting it.

A DB backup doesn't capture the settings or data outside the DB. Perhaps there are other files that should be backed up too?

---

### Post by michael298 on 2015-06-26
> **TheFu said:**
> fsck is a basic tool for all Unix systems. You need to learn to use it.  It cannot/shouldn't be run against a mounted file system. The easiest way to get around that is to boot from alternate media - like a liveCD environment, then run it.  If you try to run fsck on a mounted file system, it will warn you (like it appears it did).

[http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html](http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html) shows how to handle most partitions, except /.

If all you need is to run fsck on the / filesystem - run **sudo touch /forcefsck** then reboot - at the next boot, it will run fsck before mounting it.

A DB backup doesn't capture the settings or data outside the DB. Perhaps there are other files that should be backed up too?

Wow! sudo touch /forcefsck did the trick!!  Yay!  Thank you so much for the help. :)
I'll be adding this to my Linux cheat sheet

---

### Post by TheFu on 2015-06-26
> **michael298 said:**
> Wow! sudo touch /forcefsck did the trick!!  Yay!  Thank you so much for the help. :)
I'll be adding this to my Linux cheat sheet

Did that fix any issues ... it should have been clear if something was fixed. Just because this worked, that doesn't mean the problem is solved. There are hundreds of other things that could be broken still, too.

---

### Post by michael298 on 2015-06-26
> **TheFu said:**
> Did that fix any issues ... it should have been clear if something was fixed. Just because this worked, that doesn't mean the problem is solved. There are hundreds of other things that could be broken still, too.

After it rebooted, the VMWare console remained black for a pretty long time before the log-in prompt appeared. When I checked the site afterward, it was working again.  I'll keep an eye on it, but so far everything else seems to be fine as far the server's duties are involved.  The cronjob to backup the db is working, the smb shares are working, all the site administration interfaces are working.

---

### Post by TheFu on 2015-06-27
Hopefully, this little scare has you planning a better backup strategy. 
There was only a 20% chance that fsck would solve the issue.  You were lucky, IMHO.

---

### Post by michael298 on 2015-06-27
> **TheFu said:**
> Hopefully, this little scare has you planning a better backup strategy. 
There was only a 20% chance that fsck would solve the issue.  You were lucky, IMHO.

Agreed.  This server is really for the learning experience than actual mission-critical stuff.  But it seems a good backup strategy is also something that I need to add to the learning experience.  :)

---

