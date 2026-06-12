---
title: "Best Windows feature: &quot;Undo System Restore&quot;"
date: 2009-12-02
forum: The Cafe
---

### Post by 3rdalbum on 2009-12-02
Apparently Windows told them to do a System Restore. I never created a restore point for them, and they never created one. Hours of work installing programs, drivers and customisations: down the drain.

Thankfully, Windows can undo system restores.

Well... thankfully for Microsoft, it can. Otherwise the next piece of software that computer would get would be Ubuntu.

---

### Post by quinnten83 on 2009-12-02
I don't follow...

---

### Post by jwbrase on 2009-12-02
It seems the OP had some friends whose Windows install for some reason (probably some error or other), advised them that they should do a System restore. Apparently they complied with this, and since they hadn't set a restore point, this returned the install to "factory" settings.

Windows has a bad habit of trying to have the OS give advice to the user, which gives an impression of user friendliness, but tends to cause lots of headaches when un-computer-savvy users comply with said advice without understanding what they're doing or why.

---

### Post by pwnst*r on 2009-12-02
> **3rdalbum said:**
> Apparently Windows told them to do a System Restore. I never created a restore point for them, and they never created one. Hours of work installing programs, drivers and customisations: down the drain.

Thankfully, Windows can undo system restores.

Well... thankfully for Microsoft, it can. Otherwise the next piece of software that computer would get would be Ubuntu.

in before "cool story, bro"

---

### Post by Dragonbite on 2009-12-02
If you are installing Windows XP yourself, how do you set up the system for system restores?  I've never really fully understand this.

I understand the overall concept but I'm not sure where this lands with vendors setting up separate partitions and how to configure the system to do these backups.  Can you copy these restore points and back them up somewhere?

Pardon my ignorance.

---

### Post by szymon_g on 2009-12-02
> **3rdalbum said:**
> Apparently Windows told them to do a System Restore. I never created a restore point for them, and they never created one. Hours of work installing programs, drivers and customisations: down the drain.

Thankfully, Windows can undo system restores.

Well... thankfully for Microsoft, it can. Otherwise the next piece of software that computer would get would be Ubuntu.

does linux (ubuntu to be more specific) offers something with similar functionality (i have never heard about it's equivalent)? you know- update goes wrong, and you would like to, for example, come back to previous version of a driver?

---

### Post by Chame_Wizard on 2009-12-02
You can always fall back to the previous kernel versions.:guitar:

---

### Post by pwnst*r on 2009-12-02
> **Chame_Wizard said:**
> You can always fall back to the previous kernel versions.:guitar:

not even the same.

---

### Post by Diluted on 2009-12-02
> **Dragonbite said:**
> If you are installing Windows XP yourself, how do you set up the system for system restores?  I've never really fully understand this.

I understand the overall concept but I'm not sure where this lands with vendors setting up separate partitions and how to configure the system to do these backups.  Can you copy these restore points and back them up somewhere?

Pardon my ignorance.
By default XP will allocate part of your disk space for System Restore. You can change the amount of disk space to dedicate for any disks through the System Control Panel applet. Aside from that, you don't have to do anything and Windows should automatically take snapshots for you.

As for separate partitions, I'm assuming you're talking about restore partitions on OEM PCs? They are full XP images to restore from if you want to reinstall XP. They're not related to System Restore.

As for whether you can back up the restore points, I don't think so. I'm not too sure on how it works, but I assume it takes old files as a starting point and the snapshots will only contain the changes to the file since then. You would need the old copy and all the restore points up to the time you wanted in order to restore that particular version of the file. So you would need a copy of the whole partition, not just the restore points, in order to make it work.

---

### Post by NoaHall on 2009-12-02
Meh, I do something called "fixing the real problem". Not running away and ignoring it.

---

