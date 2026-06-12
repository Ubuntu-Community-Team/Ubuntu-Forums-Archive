---
title: "mount new partition over /var/www"
date: 2011-02-26
forum: Server Platforms
---

### Post by Kljuka on 2011-02-26
My system hard drive is small, so I would like to mount /var/www directory to another disk (/dev/sdd1). I can't access the server physically, so everything has to be done remotely (ssh). And I would prefer not to have any down time (it's a production server).

I've formated the partition (**mkfs.ext4 /dev/sdd1**), copied data to it after temporarily mounting it to /mnt/ (**cp ax /var/www /mnt/**) and afterwards mounting it to /var/www (**mount /var/www /dev/sdd**). I will add it to fstab afterwards.

- Where did all the original files/directories from /var/www go to (I've unmounted the new partition, and /var/www got previous data. Where did the data go after the mount? I want to delete it after mounting)?
- Is this procedure correct, or did I miss something?

Thank you for your help

---

### Post by CharlesA on 2011-02-26
I'm not quite sure where the data "goes" but I have a feeling it's still on the drive, you'd just told the OS to look to the other drive for files that go in /var/www

In any case - the best thing to do would probably be to copy the current data from /var/www to another folder (home directory, whatever) and then create an entry in fstab to mount the new drive to /var/www.

Test it with:

```
sudo mount -a
```

If it mounts without errors, copy the data to the new drive and test it.

---

### Post by SeijiSensei on 2011-02-27
Yes, it's still on the original drive.  If you unmount tne new /var/www, you'll see the old data sitting there (and using up space, I might add).

---

### Post by koenn on 2011-02-27
> **Kljuka said:**
> I want to delete it after mounting)?
If you delete the contents of /var/www *after* mounting, you'll delete the new files (from /dev/sdd1)

You have to unmount /var/www, then delete the contents of /var/www, then mount /dev/sdd1 on /var/www again. 
And you really want to get this right.

---

### Post by Kljuka on 2011-02-27
Thank you for your help.
But what happens if there are some open  files or sockets? Will they be automatically closed and reopened after mount on the new partition?  I'm running jailkit in directory (so there is a socket that redirects  logs from jailed dir to /var/log):
```
lsof | grep "/var/www"
COMMAND     PID     USER   FD      TYPE             DEVICE  SIZE/OFF       NODE NAME
jk_socket  1654   nobody    5u     unix 0xffff880138f73300       0t0       5990 /var/www/clients/client1/web1/dev/log
```Further  I would like to mighrate /home directory. Will there be any problems  with moving /home/ directory while being connecte with ssh (is there a problem if a user doesn't have a home directory for a moment)?

---

### Post by koenn on 2011-02-27
no idea. 

I thought we were talking /var/www, not the entire /var
I don't thing apache would complain much if you replace /var/www  under it, but you can always shut it down, or restart afterwards.

Sockets and open files and such - try to avoid them by shutting down as much as possible  (announce a 30 minute maintenance break or so)


I'm pretty sure you can move home dirs during an ssh session, just make sure your working dir is not in your home. cd / , or so.

---

### Post by Kljuka on 2011-02-28
thanks for help. Actually I wanted to move only /var/www. And I didn't have any problems doing it live (no restart of server, only stopped apache).

---

### Post by koenn on 2011-02-28
good to hear

---

