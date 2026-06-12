---
title: "iptables and rc.local"
date: 2009-09-20
forum: Security
---

### Post by noway2 on 2009-09-20
I was trying to configure a set of rules for IPTables that will load upon startup and I placed the "iptables-restore < /etc/iptables.rules" command in the rc.local script file.  My problem is that placing the command in this file doesn't appear to have any effect.

From what I can tell, rc.local is called as part of the run level 2 init script as it is symbolically linked in as part of the rc2.d directory. From what I can tell rc.local is what causes Snort to execute and this does occur.  The referenced script file does an if -x check to see if /etc/rc.local exists and from I can tell executes it if it does.  So basically, I think it should be calling the script, but it doesn't appear to.

Does anybody have any ideas or suggestions?

I was able to work around the issue by placing the iptables-restore command in /etc/networking instead, but I am curious as to why it doesn't seem to work in rc.local.

---

### Post by kevdog on 2009-09-20
Just curiously, I wonder if you put your iptables commands within a shell script file, and then call this executable shell script file from within rc.local if this works.

---

### Post by noway2 on 2009-09-22
It appears that the answer is no.  I created a small script with just that line.  I made the script executable, and then verified that it works by manually executing it.  I verified that it does restore the IPTables rules, as designed.  I then set rc.local to execute this script.

I then reboot the system and confirmed that the rules were NOT restored.  I am wondering if rc.local is really be executed.  In order to find out I will need to add a message to one of the logs, such as syslog and then look for the entry as the system is a semi-remote server that I don't usually keep a monitor on.

---

### Post by The Cog on 2009-09-23
Just a quick thought: Have you tried:
```
/sbin/iptables-restore < /etc/iptables.rules
```
I wonder if it's just a missing path at this point in the boot process

---

### Post by Lars Noodén on 2009-09-23
It might be worth taking a look at [upstart(7)](http://upstart.ubuntu.com/faq.html) since that is what Ubuntu and Debian are beginning to use to replace the SystemV scripts.

---

### Post by injate on 2009-09-23
The way I learned to do this was to put a script in the network interface up folder: /etc/network/if-up.d/
I also made a /usr/sbin/ symbolic link to that script for easy iptables-reloading

```


vi /etc/network/if-up.d/iptables-reload
# input this: 


#!/bin/sh
iptables-restore < /etc/firewall.conf
modprobe ip_conntrack_ftp
echo "IPTables reloaded"


# then:
chmod +x /etc/network/if-up.d/iptables-reload

ln -s /etc/network/if-up.d/iptables-reload /usr/sbin

iptables-reload

# To test:
shutdown -r now

```

---

