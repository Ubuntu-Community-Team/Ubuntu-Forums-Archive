---
title: "How Do I Lock Down Network Manager/WICD"
date: 2009-09-08
forum: Security
---

### Post by hurricanesfan66 on 2009-09-08
Ok, so we have approximately 2000 eeePCs running UNR in an elementary school.  One challenge has been students accidentally/on purpose deleting the pre-shared key.  We use a rather lengthy one, that teachers do not know, so it takes a tech going in, usually a few days later, to reset the key.

What we want to do is either lock the settings via locking the directory, moving the directory to a separate read-only partition, or through some other means.

What would you suggest?

---

### Post by hal10000 on 2009-09-08
I think the best idea is to move the directory to a read-only partition.
If i had to administrate 2000 machines, i would reflect about to remove or at least restrict the sudo functionality and create instead a root account with a password

Take in mind that through the sudo command every user who is member of the admin group can change almost everything he/she likes. So you may want to remove the users of the machines from the admin group, thus they cannot gain root privileges and have no acces to network manager.

What are the permissions of the relevant directory and files?

You could also use extended file attributes (look for the commands [COLOR="Red"]chattr[/COLOR] and [COLOR="Red"]lsattr[/COLOR]) to restrict access to directory and files.

---

### Post by The Cog on 2009-09-09
I believe that wicd keeps all its config in /etc/wicd, e.g. /etc/wicd/wireless-settings.conf. It doesn't require sudo to be able to save its config there (config changes made in the GUI), so I guess that the wicd daemon process is doing the writing. 

I tried setting it readonly, but the GUI can still change this file so I also guess the daemon is holding its handle. I haven't tried setting it readonly and then rebooting but it may be worth a shot. Failing that, perhaps make a copy of the directory and have a boot-up script replace/overwrite it (before the wicd daemon gets started).

---

### Post by hal10000 on 2009-09-09
I guess i got a solution, maybe it's not the best, but it works.

In your /etc/wicd directory there is a file called [COLOR="Red"]wireless-setting.conf[/COLOR] . This is, as you can guess, the file where the settings are stored (by default including the wireless keys).
You can make this file immutable and undeletable by using the exteded file-attributes:

[COLOR="Red"]**sudo chattr +iu /etc/wicd/wireless-settings.conf**[/COLOR]

Then it's no longer possible (even for root) to change anything in this file. A disadvantage may be, that now the user is no longer able to connect to another network, which has not been set up before you have run the chattr program.

That means, if one wants to use the pc at home and tries to connect with his own accesspoint (or wireless router), he/she can not connect unless the configuration of his home network was not made before changing the extended file attributes.

Also i must say that this method is not 100% save, because as long as a user can perform the sudo command (and has the skill), he can change back the attributes with [COLOR="Red"]**sudo chattr -iu /etc/wicd/wireless-settings.conf**[/COLOR]

[EDIT] btw., you can list your extended attributes with [COLOR="Red"]sudo lsattr /etc/wicd/wireless-settings.conf[/COLOR]

---

### Post by bodhi.zazen on 2009-09-09
You can lock it down with apparmor.

---

