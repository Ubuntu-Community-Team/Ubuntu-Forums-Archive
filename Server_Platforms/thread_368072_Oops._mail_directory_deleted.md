---
title: "Oops. mail directory deleted"
date: 2007-02-22
forum: Server Platforms
---

### Post by moulin on 2007-02-22
On my test server I deleted the /var/spool/mail directory by accident. Of course I know this is not smart. :-) Is it possible to recreate these directories? Can this be done with postfix or with normal root access? Hope someone can help.

---

### Post by Mr. C. on 2007-02-22
Sure you can create new directories.  But I'm afraid if you're looking for mail that was there, you're out of luck unless you have a backup.

---

### Post by moulin on 2007-02-23
It is not a problem that the mail is lost since it is a test system. Adding the mail directory to the /var/spool/ should be enough?

---

### Post by Mr. C. on 2007-02-23
Should be.  Also note /var/spool/mail is a symlink.

Just be sure the permissions and ownership are correct:

mkdir /var/mail
chmod 2755 /var/mail
chown root:mail /var/mail
cd /var/spool
ln -s ../mail

---

### Post by MJN on 2007-02-23
If it was literally /var/spool/mail that you deleted then, as Mr C says, it's just a symlink hence your target mail directory will still exist (thus nothing lost inside it).

Mathew

---

### Post by ocdude on 2007-06-13
I've actually gone and deleted the /var/mail directory. THAT is stupid. any idea how I can fix that?

---

### Post by Mr. C. on 2007-06-13
```
mkdir /var/mail
```

The files are gone.

---

### Post by dominator22 on 2007-06-13
Unless you used shred to delete it, and haven't been writing anything into that drive space, you can [recover](http://recover.sourceforge.net/linux/) your files.

---

### Post by Mr. C. on 2007-06-14
This is not accurate.  The operative word is "may", not "can".  There are no guarantees of recovery, regardless of how quickly one tries to "undelete".

---

