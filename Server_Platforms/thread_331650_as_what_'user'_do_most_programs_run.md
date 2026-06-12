---
title: "as what 'user' do most programs run?"
date: 2007-01-04
forum: Server Platforms
---

### Post by coughlin on 2007-01-04
I ask due to difficulty with programs using my FAT32 partition.

While I can read or write the FAT32 partition, programs, I run, often can't do so.  For example, subVersion can't change permissions after copying files to a repository, which I would prefer to have reside on the FAT32 partition.

The FAT32 partition is owned by 'root' and the 'plugdev' group (the default?).

The reason I ask "as what user do most programs run"? is ... I was thinking that, if I added that user to the 'plugdev' group, then the programs might run, properly.

... or am I thinking about this all the wrong way?

Thanks - for whatever input ...

---

### Post by goatflyer on 2007-01-04
FAT format doesn't support the idea of owners or groups.  The Linux way of handling that is to make everything appear to be owned by root.

You can eliminate all ownership/permissions problem with your FAT partition by making sure that your /etc/fstab entry has umask=000 for it like this

```

...
/dev/hda5       /media/hda5     vfat    umask=000       0       0
...

```


As for your other questions, most application programs run by you are run with your userid.  System services have their own names/groups.

Hope this helps.

---

### Post by Brazen on 2007-01-05
> **goatflyer said:**
> 
As for your other questions, most application programs run by you are run with your userid.  System services have their own names/groups.

That's right.  In the case of Subversion, it will not run as you or as root.  It would have it's own user, which is probably in the conf file.  But, as **goatflyer** said, FAT does not have ACLs so it could be the masking problem.

---

### Post by coughlin on 2007-01-05
> **goatflyer said:**
> FAT format doesn't support the idea of owners or groups.  The Linux way of handling that is to make everything appear to be owned by root. 

Ahhh ... I vaguely recall reading about that.  The fact that the security Properties still show owners as plugdev/root threw me off ...

Thanks - for the reminder!  :D 

> **goatflyer said:**
> 
You can eliminate all ownership/permissions problem with your FAT partition by making sure that your /etc/fstab entry has umask=000 for it like this

```

...
/dev/hda5       /media/hda5     vfat    umask=000       0       0
...

```


As for your other questions, most application programs run by you are run with your userid.  System services have their own names/groups.

Hope this helps.

ok ... I edited /etc/fstab ... and re-booted ... Now, that FAT32 partition shows that it's owned by root/root.

Though the security police might have a coronary at having root own a drive partition, this is only storage area, used for dual Linux/Windows visibility ... and to be able to backup one's documents from one location.

thanks,
Mike

---

### Post by coughlin on 2007-01-05
> **Brazen said:**
> That's right.  In the case of Subversion, it will not run as you or as root.  It would have it's own user, which is probably in the conf file.  But, as **goatflyer** said, FAT does not have ACLs so it could be the masking problem.

yes, after editing /etc/fstab to 000, as instructed, subVersion could create a repository on the FAT32 partition, BUT importing a directory squalked as follows:

Error while performing action: Can't chmod '/media/hda2/Development/svnDbS/db/transactions/0-1.txn/rev'

So, I guess the subVersion repository is going to have to reside in /home/userName ... and I'll just have to remember to back it up from there!

Thanks - for the background, though ...

Mike

---

### Post by mkramer on 2007-08-12
Bonus question:  How do I find out what user a program is running as?  For instance, I am trying to find out what user Apache 2 is running as on my Fiesty Fawn installation.

---

### Post by gnaunited on 2007-08-12
To check the current user just look in /etc/apache2/apache2.conf

Most likely it will be www-data

---

### Post by MJN on 2007-08-13
**ps aux |more** will show you a snapshot list of running processes, along with the users running them.
 
Mathew

---

