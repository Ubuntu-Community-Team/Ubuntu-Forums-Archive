---
title: "Transfering UbuntuStudio Directories"
date: 2011-07-13
forum: Ubuntu Studio
---

### Post by JASONFUSARO on 2011-07-13
I have UbuntuStudio 64 bit on partition 7 which was my original until I could not boot into it and I installed a fresh copy on partition 8.

Can I copy or merge my previous directories into the new copy so I can have all my settings and downloaded software intact? I had the original pretty much set the way I wanted it with all the installed software and I don't feel like redoing it all over again.


If it is possible, what directories need to be ported over, or is there an option somewhere within UbuntuStudio to take care of it? 


Thanks

---

### Post by jejeman on 2011-07-13
No option for that.
I guess you could copy settings from home folder, personaly I would not do it.
Programs you need to install again.

---

### Post by JASONFUSARO on 2011-07-13
> **jejeman said:**
> No option for that.
I guess you could copy settings from home folder, personaly I would not do it.
Programs you need to install again.


Why wouldn't you copy settings????

Oh, I forgot, there is an option when installing "copy data from another partition"
when I selected it an error came up about changing the file type, is this a way of using setting from the old setup???

---

### Post by jejeman on 2011-07-14
> Why wouldn't you copy settings????Because I'm not shure about the results of that action. And I don't mind setting system again, specally because the setting would improved by experience I gained.
If it is the same Ubuntu version, than it should probably work.

---

### Post by JASONFUSARO on 2011-07-14
I merged my home directory, that got me my background but not my Cairo Dock or any software. What directories are those concerned with, opt, var, usr?

---

### Post by iiiears on 2011-07-14
Hello,

I know how much time it takes to setup.
Just blithely nuke it all and start over!?? 
Um, Uh-uh 
salvage the config files even if you can't easily reuse them with recent updates.
 
Use the find command to see what files where modified around the time you configured everything.
see - [http://www.cyberciti.biz/faq/howto-finding-files-by-date/](http://www.cyberciti.biz/faq/howto-finding-files-by-date/)

Starting fresh is easy it's reading the details on dozens of manpages to tweak everything again that is hard.

See rsync
Make notes as you modify those rascally config files and add it to the rsync backup.
 
Best Wishes.

---

### Post by Flaggmann on 2011-07-17
I always have put the /home directory on a partition of it's own, then when I install a new versions or reinstall an old one, I use manual disk partitioning and select to use the /home partition as it is without reformatting; just format the / (root) and other system partitions.

It saves all the user files and all the hidden user specific settings files as well.

If you are multi booting Centos, Fedora, ubuntu and openSUSE, of course you will have to create a separate /home for each flavor, but again when upgrading each of these you can put on the same root partition and use the same option to retain the /home data without doing a reformat of that partition.

---

### Post by JASONFUSARO on 2011-07-18
> **Flaggmann said:**
> I always have put the /home directory on a partition of it's own, then when I install a new versions or reinstall an old one, I use manual disk partitioning and select to use the /home partition as it is without reformatting; just format the / (root) and other system partitions.

It saves all the user files and all the hidden user specific settings files as well.

If you are multi booting Centos, Fedora, ubuntu and openSUSE, of course you will have to create a separate /home for each flavor, but again when upgrading each of these you can put on the same root partition and use the same option to retain the /home data without doing a reformat of that partition.




Can I copy or move each of my eight Distro's home directories to a single partition I name as say Home and store each distro in a  seperate subdirectory. 

If so what is more effective a move or a copy?

---

