---
title: "Clean ubuntu to free up disk space"
date: 2010-10-11
forum: Server Platforms
---

### Post by Thyagaraj on 2010-10-11
The ubuntu 9.10 cloud server has left only 900MB of disk space. I'll just empty the directory /tmp and wondering if there is any other location to clean up.

---

### Post by arrrghhh on 2010-10-11
You could do a ```
sudo apt-get autoclean
```... There may be some others, that's just one off the top of my head.

---

### Post by oldfred on 2010-10-11
I kept some notes:

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes dependencies
 no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependencies
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Recover Lost Disk Space 
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

Script to remove packages often not used and houseclean
[http://ubuntuforums.org/showthread.php?t=1545502](http://ubuntuforums.org/showthread.php?t=1545502)

HOWTO: Recover Lost Disk Space 
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.

Some also recommend Computer Janitor but I have not used it.

---

### Post by Thyagaraj on 2010-10-11
Thanks a lot I have atleast 1.1GB of disk space

---

