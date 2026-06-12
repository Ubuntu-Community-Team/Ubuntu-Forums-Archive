---
title: "Virtualbox backups - Ubuntu/Windows 7/Windows XP"
date: 2013-03-10
forum: Virtualisation
---

### Post by hashky on 2013-03-10
Looking for backup software:

I have been running a dual boot (on 3 computers) of XP and Ubuntu 12.04 for about 5 years.  On 2 of these computers Ubuntu is the OS of choice.  The main computer runs XP as primary.  I have several programs that will only run in Windows.  So I must have a computer that runs Windows.  Some of the latest updates of these programs will not run in XP.  So I have to move to a newer version of Windows.

After several days, I now have Ubuntu 12.04 64 bit running as the host under Virtualbox.  I have Windows 7 64 bit and Windows XP running as guests.   Also, I still can boot into my old systems.  

In the past I used Acronis True Image to backup.  I have 2 hard drives installed in my computer.  I use the 2nd hard drive for backup.  I run automatic backups.  I backup the OS weekly.  After 5 weeks the backups are consolidated into 1 backup.  I keep 3 monthly backups.  I backup my data partition 3 times a week and keep 9 copies of each.  I set this up 3 years ago and have not changed it.  A restore has never failed in the 8 years I have used  Acronis.

Acronis will backup ext4 file system, but will not run under Linux.  So if I stick with Acronis, I must use Windows 7 as my host.

I would like to use Linux as my host.  
It seems that most folks use Windows 7 as the host.

I really like the looks of Back In Time, but it only does data as best I can tell.  Mondo Rescue seems to be the only backup that backs up open files.  It is not very easy to use.  I don't know about running it automatically.

I will not make manual backups regularly.  I have been burned by that too many times.  Every few months I make a copy of the 2nd hard drive to an external hard drive.  I also use CrashPlan on-line backup.

What are folks using for OS backkups?

Ron Spruell

---

### Post by SeijiSensei on 2013-03-10
If you just want to back up the virtual machine, you can simply copy the $HOME/username/.VirtualBox directory to another location.  It contains the images of all the virtual machines.  Otherwise you can use the "export" function in VB to take snapshots.

---

### Post by hashky on 2013-03-10
Thanks for the quick response.  

It looks like Deja Dup or Back In Time either one will backup the Home folder automatically.  Back In Time seems like it has a more user friendly and flexible gui.  

How would I backup the OS?  It seems I made a lot of changes to get Virtualbox to work.

---

