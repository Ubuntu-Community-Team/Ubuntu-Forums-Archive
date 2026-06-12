---
title: "copy files between PC's"
date: 2006-02-02
forum: The Cafe
---

### Post by gezzabob on 2006-02-02
I am having a brain dead moment, I am not at home at the mo but my situation is I have Ubuntu installed on my main pc with a couple of harddrives in as usual one of them is set as Vfat I can access that ok as normal from the main PC,  I have a second PC with a faulty harddrive was running windows XP but will not boot so want to copy My Documents from the second PC to the main PC running Ubuntu.  I can boot the seconf windows pc with the live ubuntu cd and mount the windows drive but how do I copy the files over network to my main Ubuntu PC onto the spare Vfat harddrive.

I have been tring to use Samba and SMB4K but getting confused somewhere along the lines.

I can remote VNC from my main PC to the 2nd PC running from the live CD so they can see each other over the netwok ok but still cannot seem to copy files accross.

Can somebody point me in the right direction...

Main PC running Ubuntu.

Second PC with files on I want to copy over to main PC booted from live CD and windows harddrive mount as normal.

What is the easiest and quickest way of just coping the files off the 2nd PC to the Main PC that I need.

I will have a search around the forum but not sure where to begin with searching for samba or networking or file sharing etc...

---

### Post by TechSonic on 2006-02-02
1. See this page [https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)
2. Put the Windows Drive in the other computer and mount it ( The computer you want to move the files to ) from there. Make sure the drive is set as HDB1, this is done by selecting SLAVE on the drives jumper settings.  Usually a white or black tab on the back end of the drive it's self.  Put the drive in, tell BIOS to auto detect it and once in Ubuntu mount it and copy the files over and then run " sudo chmod 0777 -R Directories you want to unlock.  The -R command makes them so that all files and sub folders will get the same permissions, this avoids manually permissioning all the files one by one.

---

### Post by gezzabob on 2006-02-02
[QUOTE=TechSonic]1. See this page [https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)
2. Put the Windows Drive in the other computer and mount it ( The computer you want to move the files to ) from there. Make sure the drive is set as HDB1, this is done by selecting SLAVE on the drives jumper settings.  Usually a white or black tab on the back end of the drive it's self.  Put the drive in, tell BIOS to auto detect it and once in Ubuntu mount it and copy the files over and then run " sudo chmod 0777 -R Directories you want to unlock.  The -R command makes them so that all files and sub folders will get the same permissions, this avoids manually permissioning all the files one by one.[/QUOTE]

That probably the easier option to put the drive into my main PC But I was tring to avoid manually swapping the HDDs around and just copy them across the network saves manually moving HDD's around.  PS I cannot get onto [https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions) link maybe something to do with firewall setting here at work so I will look at that link when I get home.

---

