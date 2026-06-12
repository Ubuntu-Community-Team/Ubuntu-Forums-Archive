---
title: "Adding harddisk check at shutdown"
date: 2009-01-23
forum: Ubuntu Brainstorm
---

### Post by oblidor on 2009-01-23
I have currently 2.5 Tb hard disk capacity in my computer. Three of the partitions are 500Gb each. The big problem now is when the harddisks need to be checked (due to number of mounts) it will take **forever to** check a 500Gb harddisk. This means that you have to wait maybe 20-30 min or more at boot for the check to complete. You can always press Escape to skip the test, but the test should eventually be done.

In my Debian days I made a hack of the hard disk check script and added one to also check at shutdown. I managed to check everything except /, but that was acceptable. It worked just like the checkup at startup, but only for shutdown, not reboot. That was a design choice as a reboot generally means you don't want to wait 20 min, but for a shutdown it doesn't matter if the computer uses 20 min to check a harddisk before powering off.

To me it makes sense if Ubuntu considers making a system that checks at shutdown if a harddisk needs to do a check and then run fsck on it. This way one may skip the check on startup and get the checks at shutdown which is less annoying.


EDIT: After posting I found when googling again with different keywords that this has been proposed before.

However, I do NOT propose to move the checking to shutdown. I want to Add it. I think moving is not a good idea. 
Second, it has been argued that this is not nice for laptop users. Well just make the script an installable package you can choose to install. If you have a laptop you can uninstall it if you wish.
Autofsck may be a solution but it just checks either at shutdown or boot.

---

### Post by oblidor on 2009-01-23
Quick hack if you want to do this on your computer. Best solution is that Ubuntu includes a system in their distribution. This problem will not be smaller in the future.

```
sudo -i
cd /etc/init.d
cp checkfs.sh shutdown-checkfs.sh

```


The only change needed to do in the shutdown-checkfs.sh is to change:

  stop)
        # No-op
        ;;

to 

  stop)
        do_start
        # No-op
        ;;

in the case statement at end of the script. 

then: 

```
cd /etc/rc0.d
ln -s ../init.d/shutdown-checkfs.sh S50shutdown-checkfs.sh

```

make sure that S50 is after umountfs and before umountroot in the /etc/rc0.d. For Ubuntu 8.10 it is S40 and S60 respectively, so the number must be between 40 and 60, thus 50.

to test

```

touch /forcefsck

```

and now shutdown (not reboot) your computer.

Please let me know if doesn't work for you.

NB: The reason for copying the checkfs.sh to shutdown-checkfs.sh is to avoid that the checkfs.sh is overwritten in a future update.

HTH

---

