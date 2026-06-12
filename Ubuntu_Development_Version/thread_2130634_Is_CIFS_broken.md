---
title: "Is CIFS broken?"
date: 2013-03-30
forum: Ubuntu Development Version
---

### Post by cole.mickens on 2013-03-30
[https://bugzilla.redhat.com/show_bug.cgi?id=832741](https://bugzilla.redhat.com/show_bug.cgi?id=832741)

I found this. Seems potentially relevant. I'm trying the following:

```

sudo mount.cifs -o user=USER,password=PASS //HOSTNAME/media ./tmp

sudo mount.cifs -o user=USER,password=PASS,ip=192.168.1.102 //HOSTNAME/media ./tmp

sudo mount -t cifs -o user=USER,password=PASS,ip=192.168.1.102 //HOSTNAME/media ./tmp

```

They all have the same result:

```

mount error(22): Invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```


**WORKAROUND HERE:** (post #9 in this thread) [http://ubuntuforums.org/showthread.php?t=2130634&p=12581550&viewfull=1#post12581550](http://ubuntuforums.org/showthread.php?t=2130634&p=12581550&viewfull=1#post12581550)

And I say workaround, because this still looks like a bug.

---

### Post by cariboo on 2013-03-30
Probably, it breaks every dev cycle, it usually gets fixed before the dev version is released.

---

### Post by Gyokuro on 2013-03-30
> **cole.mickens said:**
> [https://bugzilla.redhat.com/show_bug.cgi?id=832741](https://bugzilla.redhat.com/show_bug.cgi?id=832741)

I found this. Seems potentially relevant. I'm trying the following:

```

sudo mount.cifs -o user=USER,password=PASS //HOSTNAME/media ./tmp

sudo mount.cifs -o user=USER,password=PASS,ip=192.168.1.102 //HOSTNAME/media ./tmp

sudo mount -t cifs -o user=USER,password=PASS,ip=192.168.1.102 //HOSTNAME/media ./tmp

```

They all have the same result:

```

mount error(22): Invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

Could you check whether smbfs is installed?? dpkg -i | grep smbfs

---

### Post by cole.mickens on 2013-03-30
'smbfs' was replaced by 'cifs-utils' which is definitely installed.

---

### Post by tgalati4 on 2013-03-30
MOUNT.CIFS(8)                                                  System Administration tools                                                  MOUNT.CIFS(8)

NAME
       mount.cifs - mount using the Common Internet File System (CIFS)

SYNOPSIS
       mount.cifs { service  } {mount-point} [-o options]

Perhaps put the options at the end?

---

### Post by cole.mickens on 2013-03-30
Didn't help. :(

---

### Post by tgalati4 on 2013-03-30
Is HOSTNAME defined in /etc/hosts?  Does ./tmp exist?  Is it off of the root directory /?  Perhaps removing the dot (.) and just use /tmp or the complete path.

Or, it really is a parsing bug that you have linked.

Can you browse the network share in Nautilus and mount it?

---

### Post by zuti on 2013-03-30
I had to define "sec=ntlm" to get CIFS to work at all, even though that should be a default option if omitting the sec part? 

Was pulling my hair for hours after updating to 13.04, because my mounts worked fine before.

And man... "Invalid argument". Very helpful...

---

### Post by cole.mickens on 2013-03-30
> **tgalati4 said:**
> Is HOSTNAME defined in /etc/hosts?  Does ./tmp exist?  Is it off of the root directory /?  Perhaps removing the dot (.) and just use /tmp or the complete path.

Or, it really is a parsing bug that you have linked.

Can you browse the network share in Nautilus and mount it?

HOSTNAME is a windows hostname. It is properly looked up, and the same thing happens when I manually specify the ip instead of the hostname in the share path.

./tmp is a local directory. It spits out a different (and more useful) error if you give it an invalid mount path.

Yes, I can browse the share in both nautilus and dolphin.

> **zuti said:**
> I had to define "sec=ntlm" to get CIFS to work at all, even though that should be a default option if omitting the sec part? 

Was pulling my hair for hours after updating to 13.04, because my mounts worked fine before.

And man... "Invalid argument". Very helpful...

Attempting now, will edit this post.

edit: NICE CATCH! You're the man! Hopefully this gets up there in Google search results.

**To fix the error 22: Invalid argument, try the following:**

```
sudo mount -t cifs -o user=USER,password=PASS,**sec=ntlm** //HOSTNAME/media ./tmp
```

or, if you have it wide-open for everyone, use guest mode:

```
sudo mount -t cifs -o guest,**sec=ntlm** //HOSTNAME/media ./tmp
```

Thanks be to Zuti!!

---

