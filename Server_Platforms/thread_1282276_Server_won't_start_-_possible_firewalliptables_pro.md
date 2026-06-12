---
title: "Server won't start - possible firewall/iptables problem."
date: 2009-10-04
forum: Server Platforms
---

### Post by Truenash on 2009-10-04
We recently rented a dedicated server running on Ubuntu Server edition. We then preceeded to follow tutorials to install Apache, Php5, Mysql etc. I installed Shorewall during this process, but found I wasn't fond of it versus another firewall, so I uninstalled it.

Shortly after the uninstall, I rebooted the server, from which it didn't come back up.

The people we rent it from are giving us KVMoIP access tomorrow to try and fix it. Of course, not being terribly hot on Linux anyway, I have no idea what the problem is, let alone how to fix it.
Any help would be greatly appreciated, and failing that, is it possible to do a fresh install over a KVMoIP connection?

Thanks
Nash

---

### Post by Lars Noodén on 2009-10-04
**If** the problem was your new firewall settings, I would recommend a fail-safe to let you back in because it is possible to lock yourself out.  

First, be sure the rules allow new port 22 (ssh) incoming connections so you can log in.

Second, because mistakes happen, before changing the firewall settings, make a way to automatically restore the working settings after a few minutes.  

[INDENT][FONT="Courier New"]
# save spare working iptables rules
sudo iptables-save > /etc/iptables.rules
[/FONT][/INDENT]

Make a place for a restoration script
[INDENT][FONT="Courier New"]
sudo touch /usr/local/sbin/restore.firewall.sh
sudo chmod +x /usr/local/sbin/restore.firewall.sh
[/FONT][/INDENT]

Fill it with this:

```

#!/bin/sh

# this shell script uses 
#       echo(1), test(1), iptables-restore(8), at(1)

# go forward only if there are spare rules
test -f /etc/iptables.rules || exit;

# restore the spare rules automatically after a time
echo 'iptables-restore < /etc/iptables.rules' | at now +3 minutes

```

Then before testing new firewall settings, you can set the working rules to be restored automatically.  

[INDENT][FONT="Courier New"]
sudo /usr/local/sbin/restore.firewall.sh
[/FONT][/INDENT]

Apache and PHP on Linux is the same as on the Solaris you are already comfortable with.  At the user level, and even the system administration level there is not much difference.  At the sysadmin level, even OS X and BSD are very similar to linux.  Learn once, run anywhere for most things.  IPTables is unique to linux, but the shell scripting to manage them is the same as elsewhere.

---

