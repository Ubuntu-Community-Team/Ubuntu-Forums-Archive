---
title: "Recover MySQL from files?"
date: 2009-10-12
forum: Server Platforms
---

### Post by grenadier32 on 2009-10-12
I see a bunch of people have asked this already without success, but here goes anyway: if an installation gets borked and my only way of reaching it is to view the files on the hard drive from a USB stick, is there any way to make a dump of my MySQL databases so I can add them to a new installation? I can see all of MySQL's data in /var/lib/mysql, but I can't view or use it in any way. Is there some other method I could do to guarantee MySQL can use them?

---

### Post by cariboo on 2009-10-13
If you have enough ram, you should be able to install mysql while running from you usb device, then you can use mysqldump to dump the databases.

---

### Post by Lars Noodén on 2009-10-14
> **grenadier32 said:**
> is there any way to make a dump of my MySQL databases so I can add them to a new installation? 

There is actually a utility called '[mysqldump](http://manpages.ubuntu.com/manpages/jaunty/en/man1/mysqldump.1.html)'.  You can use it to save the data, the structure or both.

Here is a cut-n-paste from an old cron job to copy the structure:

```

# needs a user which can *read* everything 
# in that particular database
mysqldump nameofdatabase \
                --add-drop-table \
                --add-locks \
                --comments=0 \
                --create-options \
                --lock-tables \
                --no-data \
                -u userwithfullreadaccess -p  \
        | gzip -c \
        > mysql-structure-backup-`date +"%Y-%m-%d"`.gz


```

You can play with the settings, such as take out --no-data, to do other things.

---

