---
title: "Best Option for File Backup/Storage Server??"
date: 2006-09-10
forum: Server Platforms
---

### Post by SSTwinrova on 2006-09-10
Long story semi-short, my dad's work laptop crashed (nothing recoverable off the HD, and of course he had no personal backups outside of what his company had archived), so it didn't take much for me to sell him on getting a backup system in place. First option I thought of was just getting an external HD, but that'd require him to remember to plug it in on a regular basis when he's home. Second option (which is the one he likes better) is just setting up a backup server on our network and get an automatic backup program that will backup his necessary files weekly in the middle of the night. This also has the benefit of being able to act as a storage server for music/video that can be accessible from all our other computers. Now I'm in the mode of trying to find out the best way to set this up.

According to him, he just wants the latest copy of everything backed up (so no need to worry about setting up a SVN server or anything). Because of the amount of time he's gone during the week, a way for him to somehow connect to the server and pull off a file that may of gotten deleted/corrupted on his laptop would also be convenient. Software wise, I'm thinking just a shared folder for the local connections. I'm open to suggestions for the remote access method that would preferably be as brain-dead simple as possible (meaning even like an FTP server would be near the bottom of the list). Web server + a password-protected directory listing script w/ download functionality maybe?

On the hardware side, here are my options: we have two old computers (both Dells, a P3 550 and a P4 2.0) that would be available to use given the necessary HD upgrades (and I'd put Dapper on them of course). Yesterday, however, I stumbled onto a page pointing out [this]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1118334819312&pagename=Linksys%2FCommon%2FVisitorWrapper") which uses external HDs and shares them across a network. Apparently it has a [decent community]("http://www.nslu2-linux.org/") around it for hacking/adding functionality. I've yet to do a price comparison between these two methods, but does anyone have any suggestions on which might be better for my needs?

---

### Post by lukew on 2006-09-11
Cant beat a physical computer, physical wire and rsync. Those devices act like a computer and wont have samba on. I am sure it is doable but would be far easier, and cheaper for some discs on the old machines.

Stable and steady with the backups. I personally have two ext usb2 hds. I keep one at work and one at home and every few weeks swap them over. always have work and home data backed up onsite and off. 

But of course this is personaly preferences.

Luke

---

### Post by kzm. on 2008-03-20
the initial post is from 2005.. answer from 2006. i hope my adding doesnt stay unanswered for so long.

i have no experience with servers really except putting files on them. i am fine with ubuntu desktop for some time back. iwonder if anybody has any useful advise, links, experienced view for me on following scenario:

home backup file server:
- likes linux/osx/pc users
- easy to use (like come home, start app, cook dinner, eat, watch movie, close computer)
- easy to install (since there is no gui of course i am prepared to push the commandline)
- optional: sort of versioning for certain things

i have installed ubuntu server edition (6.06) on an old computer grabbed from the street.. i would like to buy two identical harddrives for data, just to have everything mirrored in case one disk dies. put that thing in my closet and forget it exists physically... ok, may be i will install some sort of media server so i can rescue everything from my dying cd's.

i thought rsync and cron will be my friends for mirroring but not sure for the clients. i googled and got blown away by all the possibilities.. what worked best for you?

---

