---
title: "Unable to install postfix atal: open database /etc/aliases.db: Permission denied"
date: 2010-03-14
forum: Server Platforms
---

### Post by Stuart1745 on 2010-03-14
Running newaliases
postalias: fatal: open database /etc/aliases.db: Permission denied


in my /etc I do not have a aliases.db only an aliases.

I cp aliases aliases.db 
 but when I try and install post fix again it gives me the same error and aliases.db goes away.

---

### Post by highonv8splash on 2010-05-23
Getting this same exact error and behavior from apt. We've just upgraded from 9.10 to 10.04. Does anyone have any ideas on how to fix this or what exactly is going wrong? 

It doesn't seem to be a permissions issue, at least directly, since the same problem occurs when the file doesn't exist or when it's 777'd. The only way we've been able to get postfix working properly currently is by restoring a previous aliases.db file and running newaliases with that file there.


/etc and /etc/postfix are 755 root:root


aliases and the working aliases.db file are 644 and list:daemon.


Thanks, Any help appreciated!

---

### Post by highonv8splash on 2010-05-27
bump, anyone have any ideas on how to fix this? Considering backing up some files and wiping/reinstalling postfix :-(

---

### Post by ViRMiN on 2010-05-27
You could try:

```

cd /etc
sudo postmap aliases

```

This will create the aliases.db file that you're missing, and should give it the right permissions.  Both /etc/aliases and /etc/aliases.db should have 644 perms and root:root ownership.

You should be able to fire-up postfix once you've sorted it :)

---

### Post by pytheas22 on 2010-06-19
I'm not sure if you all are still having trouble with this, but I was dealing with the same issue on a Lucid server install.  I found that the postfix installation would complete successfully if I renamed the file /etc/aliases to something else (deleting it altogether would probably also work), then ran:
```

sudo apt-get -f install
```

I'm pretty sure the issue arose because I previously had exim4, and later sendmail, installed on this machine, and I think one or both of them created /etc/aliases with permissions that postfix wasn't able to work with.  Getting rid of that file allowed postfix to recreate it using the permissions it wanted.

---

### Post by Ximbiot on 2011-06-13
I'm having the same problem after a recent postfix upgrade.  /etc/aliases.db does not exist and running postalias will not create it.  I have tried removing /etc/aliases and rerunning the installer, but configuration still fails with the same message.  Any more ideas?  Can I fix this short of a complete removal and reinstall?

---

### Post by pytheas22 on 2011-06-13
> **Ximbiot said:**
> I'm having the same problem after a recent postfix upgrade.  /etc/aliases.db does not exist and running postalias will not create it.  I have tried removing /etc/aliases and rerunning the installer, but configuration still fails with the same message.  Any more ideas?  Can I fix this short of a complete removal and reinstall?

What exactly is the error message you're getting?  If it's complaining about file permissions on /etc/aliases.db being wrong, then it's interesting that /etc/aliases.db doesn't exist at all.

Does it change anything if you create /etc/aliases.db as an empty file and with permissions that will allow postfix to write to it?

---

### Post by Ximbiot on 2011-06-14
> **pytheas22 said:**
> What exactly is the error message you're getting?  If it's complaining about file permissions on /etc/aliases.db being wrong, then it's interesting that /etc/aliases.db doesn't exist at all.

Does it change anything if you create /etc/aliases.db as an empty file and with permissions that will allow postfix to write to it?

This is the error message I'm getting from the installer and from postalias/newaliases after running the installer:

```

postalias: fatal: open database aliases.db: File exists

```

Here is a really weird workaround I found that temporarily fixes the postalias/newaliases problem - creating a new DB file with a different name and moving it into place:

```

**$ sudo newaliases**
postalias: fatal: open database /etc/aliases.db: File exists
**$ cd /etc**
**$ ls -l aliases.db**
ls: aliases.db: No such file or directory
**$ sudo cp aliases tempaliases**
**$ sudo postalias tempaliases**
**$ sudo postalias aliases**
postalias: fatal: open database aliases.db: File exists
**$ sudo mv tempaliases.db aliases.db**
**$ sudo postalias aliases**
**$ sudo postalias aliases**
**$ sudo newaliases**
**$** 

```

This would have been fine, even if this still doesn't make sense (1. the error message is wrong if the problem is that the file DOESN'T exist, 2. a program that creates the DB file shouldn't complain when the DB file doesn't exist, 3. postalias doesn't complain when the tempaliases.db file doesn't exist).

Unfortunately, attempting to complete the postfix install breaks everything again:

```

**$ sudo apt-get install -f postfix**
Reading package lists... Done
Building dependency tree... Done
postfix is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up postfix (2.2.10-1ubuntu0.4) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
postalias: fatal: open database /etc/aliases.db: File exists
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
**$ sudo newaliases**
postalias: fatal: open database /etc/aliases.db: File exists
**$**

```

Touching the aliases.db file is not enough to fix the problem:

```

**$ touch aliases.db**
touch: cannot touch `aliases.db': Permission denied
**$ sudo touch aliases.db**
**$ sudo newaliases**
postalias: warning: removing zero-length database file: /etc/aliases.db
postalias: fatal: open database /etc/aliases.db: File exists
**$**

```

But it is a clue that REMOVING the aliases.db file is going to be enough to recreate the problem:

```

**$ sudo newaliases**
**$ sudo rm aliases.db**
**$ sudo newaliases**
postalias: fatal: open database /etc/aliases.db: File exists
**$ sudo postalias tempaliases**
**$ sudo mv tempaliases.db aliases.db**
**$ sudo newaliases**
**$**

```

I see two ways to deal with this.  The ideal fix would be to fix postalias in such a way that it could deal with the missing DB file.  Alternately, how do I prevent the postfix installer from removing aliases.db before rerunning newaliases?

---

### Post by Ximbiot on 2011-06-14
Incidentally, this is happening on Dapper LTS.  Also, it could have to do with some sort of package conflict, as I have two identical servers exhibiting this problem (one was cloned from the other originally, though perhaps after the postfix issue started), and a third Dapper server with a different package selection which installed the same version of postfix without difficulty.

---

### Post by Ximbiot on 2011-06-14
> **Ximbiot said:**
> I see two ways to deal with this.  The ideal fix would be to fix postalias in such a way that it could deal with the missing DB file.  Alternately, how do I prevent the postfix installer from removing aliases.db before rerunning newaliases?

I settled on the latter workaround.  I edited /var/lib/dpkg/info/postfix.postinst to comment out the line that removed /etc/aliases.db and then `dpkg --configure postfix' ran fine.

There is still some sort of problem in postalias and, by extension, the installer, but this works around it and gets my mail working again.

---

### Post by cr03 on 2011-06-30
So:

```
sudo apt-get -y remove postfix 
sudo dpkg --purge postfix
sudo apt-get -y install postfix
sudo sed -i 's,rm -f /etc/aliases.db,#&,' /var/lib/dpkg/info/postfix.postinst 
sudo cp /etc/aliases /tmp/
cd /tmp/
sudo postalias aliases
ls -al aliases.db
sudo cp aliases.db /etc/
sudo chmod 777 /etc/aliases.db
sudo dpkg --configure postfix
```

... fixes it just fine but then the question is who should own aliases.db?  giving it to postfix doesn't help. Started thinking maybe apparmour was the problem but no entries in the logs about denied file access and nothing in /etc/apparmour* about postfix....

We installed a few other packages on a machine started with the 11.04 server image. I doubt it's a package conflict. Maybe the maintainer might want to investigate a fix so the postinstall is a little more resillient about creating the aliases.db? Just a suggestion.

---

### Post by benteveo on 2012-03-16
FWIW: I was getting the a very similar error when calling newaliases.

```

$ sudo newaliases 
postalias: fatal: open /etc/aliases.db: Permission denied

```

Turns out that the error was misleading.  It was the /etc/aliases that was owned by me rather than root that was causing the issue.

The solution I found was:

```

sudo chown root.root /etc/aliases
sudo newaliases

```

newaliases calls postalias, because postfix is my MTA.

Anyway, after fixing ownership on the source file /etc/aliases, the error went away.

HTH

---

