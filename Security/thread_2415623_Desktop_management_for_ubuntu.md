---
title: "Desktop management for ubuntu"
date: 2019-03-29
forum: Security
---

### Post by mparthi24 on 2019-03-29
please suggest opensoure Desktop management for ubuntu (like Patch management & Inventory)

---

### Post by TheFu on 2019-03-29
I use ansible to setup brand new servers and to maintain configurations in a standard way.  

As far as weekly patching, A trivial script works for me:
```

#!/bin/sh
# weekly-update script

CMD1="sudo apt-get update"
CMD2="sudo apt-get dist-upgrade"
DEPLOYID="deploy5423ut"  # userid that has ssh keys and sudo apt-get 
#                                            permissions on each system. 

# space separated list of servers/IPs.
SRVS="regulus dms44 zcs43 mon45 crm46 xen51 pki52 pad47 dms01 \
            dms02 romulus posc vpn01 vpn02 istar osmc kodi pi3"
 
# ###########################################################
# start of main()
for D in $SRVS ; do
  echo "

INFO: Working on $D"
      ssh  $DEPLOYID@$D   "$CMD1;  $CMD2;"
done
```

Just run it like this:
```
$ ~/bin/weekly-update | tee log.weekly 2>&1 
```
so a log of everything is created.  If there are multiple admins, put the script on a specific "admin server" in the /usr/local/sbin/ directory. That is where admin scripts belong.

If you use a different deployment userid for each system, just put it into the SRVS list instead and remove the DEPLOYID stuff.

That is "patch management" on Ubuntu systems, assuming you use repositories and PPAs.  If you want to get a list of installed packages for each system, there are multiple ways.  I usually just want the list of manually installed packages, not those installed during installation or through dependencies.  apt-mark can do that.  Modify the script above to get a list for every server.
If you want a hardware inventory, modify the script above or use something like **ansible -m setup**.  The way that I deal with software and hardware inventories is by storing them on each box in the /root/backups directory. They are updated nightly, just before backups happen.  That location is included in every backup, so I know what is needed to rebuilt a server from scratch with only the data held inside the backups.

If you need to run jobs in parallel, there are many different techniques.  The easiest would be to use a queue manager like taskspooler with 2 queues and submit half the ssh commands to each queue or 3 or 5  or 10 or 20 queues. Whatever you need.

To limit the internet use for downloading packages, you can run a local repo cache with **apt-cacher-ng** which pulls the packages from the repo when the first request is made, then all other systems use the local copy.  Just tell APT about it ... /etc/apt/apt.conf.d/02proxy and
```
Acquire::http { Proxy "http://istar:3142"; };
```  istar is my local apt-cache box.

Anyway, hope this is helpful.  Something that may be useful to know is that unlike Windows-SMS, if the system is on the network, then it will be patched.  You only need worry about the 10% failure rate for systems that are powered off or portable.  For them, just run the patching during work hours.  If you like, you could let each client setup when they want patches to happen with some easy scripting.  Say the CEO wants his system patched at 5pm every Friday or 8am Mondays. Entirely possible without giving the end-user any extra privileges.

---

