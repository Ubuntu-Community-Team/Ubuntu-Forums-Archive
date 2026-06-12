---
title: "Question about cryptaded home folder?"
date: 2017-01-14
forum: Security
---

### Post by patrikmellq on 2017-01-14
I understand if some one get physical acces to my computer they can not view or enter my home folder as it is cryptated - i assume this is correct assumption.
But what happens if i get a hack or a script kidde entering my system, what function does my cryptated home partiation has? does it protect me from some one from the outside to read the content?

I mean i want my family photos and other material to be private.

I will run Tripwire on my new laptop - but it does not prevent a hack only show it has been a hack - and does not prevent some one to entering my computer.

Cheers

---

### Post by TheFu on 2017-01-14
If "cryptated" means "encrypted", then ....

If your userid is logged into the system, then the data is available as decrypted and the only controls are normal file and directory permissions.  Whole drive encryption works this way too except when the system it booted, all the data, OS, swap, are decrypted and available. Still, even with these issues, I use whole drive encryption for all my portable devices and portable storage.  

Disk encryption is only useful when the data is unavailable and the system is completely off.  Standby and hibernation break this security almost always.  There is always the "evil maid" attack to be concerned with, even with whole disk encryption.

Tripwire is hardly perfect. Can't say I'd recommend it to most people, especially end-users.  

Security is not a checkbox, it is constantly changing target, dependent on the different risk factors and attack vectors for your specific system and data.  By default, desktop Ubuntu doesn't have any listeners running, so external attacks require initiation by a user doing something or physical access.

There is a "Basic Ubuntu Security" page if you want more ideas for protecting a desktop system. For servers, things get more complicated and multiple layers are needed. I always start with network architecture as the first line of defense and try to keep desktops away from higher risk systems.

For most users, security starts and ends with 
* staying patched
* automatic, versioned, backups.
* Avoiding doing foolish things like running java applets or flash or using adobe products. 
* Watching log files. On high-risk systems, use remote logging.

To go to another level, running internet connected programs inside a container is an extra step that isn't too hard thanks to firejail.

---

### Post by patrikmellq on 2017-01-15
Thank you TheFu for the explination :-)
I also use Tripwire, it does not prevent intrustion, but sure show me if it has happen as i have the database on removable media.
And some one show me a software for encrypt files/folders and upload them into the cloud like google drive, will look into that later.

I have just buy a Asus laptop with 14 hours battery time and erase windows 10 and install Ubuntu Mate LTS :-)
Also  have VPN ...

---

### Post by patrikmellq on 2017-01-15
I look at Firejail and i want to use that solution - but i don't fully understand what it does - i assume it isolate all process into a contain enviroment - so if some one try to eplore or hack a weeknes with one of my softwares connecting to internet they will end upp in my container running my software in a jail enviroment with no acces to my other computer enviroment.

Is that correct?

EDIT: I find nice explination [http://www.linux-magazine.com/Issues/2015/173/Firejail](http://www.linux-magazine.com/Issues/2015/173/Firejail)

Thanks for the informaion TheFu :-)

---

