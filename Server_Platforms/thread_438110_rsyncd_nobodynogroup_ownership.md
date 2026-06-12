---
title: "rsyncd nobody:nogroup ownership"
date: 2007-05-09
forum: Server Platforms
---

### Post by pht3k on 2007-05-09
hi wanted to backup my home dir with rsyncd and it worked except that all files are owned by nobody:nogroup while i used the -raz flag.  any idea?

thanks,
pht3k

---

### Post by MJN on 2007-05-09
Howcome you're using the rsync daemon? I'm sure there's a way round it even if you do, but I can't help feel things woud be easier using the standard rsync, running over SSH if you're doing it remotely.

Mathew

---

### Post by pht3k on 2007-05-10
hmm.  the command i used is rsync.  i dont know exactly how it works.  i thought that rsync used rsyncd in the background.  sorry for my fault.  

but the problem remain... rsync -raz gives me files with nobody:nogroup ownership.

---

### Post by MJN on 2007-05-11
That's alright... perhaps if we take a few steps back and see what you're actually doing then we can sort it out.
 
What's the full command you're issuing and where are the source and destinations? I'm asking because if we're talking about transfers between different machines then the solution is slightly different. Also, who owns the files that you're backing up? The same user that's running rsync?
 
Also, have you changed any default config (rsynd.conf specifically - I think that's the only configurable file). We don't actually want to use rsyncd, well *I *don't anyway as things are simpler without it IMHO.
 
Mathew

---

### Post by pht3k on 2007-05-11
the full command i used is:
rsync -raz --stats --delete /home 127.0.0.1::backup

my rsyncd.conf file is the following:
[backup]
   path = /mnt/backup
   comment = backup
   read only = false

i tried to use the command as pht3k user and root user with the same results

/mnt/backup is chmod 777

the dir i try to backup is /home

thanks again for your help :)

---

### Post by MJN on 2007-05-11
We'll ignore rsyncd - it's really not needed.

Instead try **rsync -av --stats --delete /home /mnt/backup**

Note there's no need for -r as recursion is implied by the -a archive option. Also, the -z compression only applies when trasferring remotely - and only the data over the wire rather than the files themselves.

If you're backing up anything not owned by the user (you) running rsync then prefix it with **sudo** otherwise you won't be able to create the backup file owned by the other user.

Mathew

---

### Post by pht3k on 2007-05-11
fast reply...
and it works!!

rsync -av --stats --delete /home 127.0.0.1::backup 
gave me nobody:nogroup
but
rsync -av --stats --delete /home /mnt/backup
like you suggested worked fine!!

thanks a lot!!! now i can crash my hard drive :)

---

### Post by MJN on 2007-05-11
Of course it worked! ;)

Don't bother running rsyncd - if you've got it in a startup script get rid of it, you don't need it running for local backups. Indeed you don't need it running for remote backups either - just have rsync *available* at both ends and connect the two with SSH. But that lesson is for another day... ;) (search the archives for plenty of usage discussion)

Mathew

---

