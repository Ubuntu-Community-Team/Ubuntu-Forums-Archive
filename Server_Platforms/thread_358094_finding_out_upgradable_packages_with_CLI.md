---
title: "finding out upgradable packages with CLI"
date: 2007-02-10
forum: Server Platforms
---

### Post by PetePete on 2007-02-10
i've got no X system on my server just command line interface.
how can i using apt-get, see a list of upgradable packages, and then choose which ones to install?

---

### Post by gombadi on 2007-02-10
To update the list of packages log on, become root and -

apt-get update
apt-get dist-upgrade -s

The "-s" will simulate what would happen and it will show you what it would do to upgrade your system. Just remove the -s to actually upgrade the system.

Others may comment about using dist-upgrade or upgrade. That is your choice. man apt-get to see the differences between them.


To install some packages only do
apt-get install package1 package2 -s

If you are happy with what it will do then remove the -s and run the command again.

If it is a server that runs 24x7 then put this in as a cron job
----------------------------------------------------------------------------------------------------
#!/bin/bash

# daily script to show packages available for update

# Config data
MAILTO="user@server.name"

{
echo "#########################################"
echo "## Package report for $(hostname)"
echo "#########################################"

today=$(/bin/date +%a)
# select a day of the week to get a full report
if [ "$today" = "Mon" ]; then

        # update the package list and let us see the result to check if we have any errors
        apt-get update
else
        # update the package list
        apt-get update &>/dev/null
fi

echo
echo "Updates available"
apt-get dist-upgrade -s

} | mail -s "Package Report for $(hostname) at $(date)" $MAILTO

----------------------------------------------------------------------------------------------------

---

### Post by MJN on 2007-02-11
A simple way is to install **apt-show-versions** and run it with the **-u** option. This will show you give you a list of which packages are currently upgradeable (it also happens to list installed packages that are newer than those in the repositories).

Mathew

---

### Post by PetePete on 2007-02-12
thanks mathew,
 i installed that and its very handy.

used the command 
```

apt-show-versions | grep upgradeable

```
and works like a charm! thx

hehe now im just going to restrict its use so any dodgy users cant use it to instantly see what software is vunrable lol

---

