---
title: "server backup - seems to be much harder than it ought !"
date: 2006-11-21
forum: Server Platforms
---

### Post by neill on 2006-11-21
hi

i run a kubuntu 6.06 LTS (64 bit) home server which acts as a fileserver for a handful of home PCs running a mix of XP and Linux on various boxes

there are 4 users in the house, all with accounts on the server. i'm the only one with sudo rights

what i want to do is backup daily everyones /home to a NAS share - which is a simple CIFS share mounted as follows

mount -t smbfs //freeNAS/share /mnt/backup

(when i get it to work i'll do it all in fstab of course)

ideally i want to have a system that does daily hard linked backups over time so i can easily pick a past version of whatever file i need and restore it using standard (GUI) file tools, whilst not end up eating up the space on the NAS device with duplicate file copies

pdumpfs is ideal in most regards but it baulks !

sudo pdumpfs /home /mnt/backup - gives me a permissions error as soon as it tries to write the first user folder

but ... sudo pdumpfs /home /backup (where /backup is a local folder on the server) works beautifully ](*,) 

any of you server gurus out there any thoughts on what soft i  might use to do this sort of thing, or any ideas what's causing pdumpfs to hiccup ? :-k 

thanks

neill

ps - the reason for the paranoia is that /home on the server is an LVM spread across 2 physical drives - so i feel RAID 0 exposed to HDD failure - quite apart from all the usual reasons for backups

---

### Post by MJN on 2006-11-21
Have you looked at rsync? The bees knees when it comes to flexible backups in my opinion.

Plenty of guides available for 'standard' backups, and several too for more advanced ones taking advantages of hard links as you desire (e.g. [http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/) - not read it thoroughly but found it with a *+rsync +hard +links* Google search).

Mathew

---

