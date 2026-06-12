---
title: "slocate doesn't seem to work"
date: 2010-08-24
forum: Server Platforms
---

### Post by davidshere on 2010-08-24
I've found information about slocate here: [https://help.ubuntu.com/community/FindingFiles#locate](https://help.ubuntu.com/community/FindingFiles#locate)

I have installed the slocate package. I've manually run its daily cron job: 
```
david@growler:~$ sudo /etc/cron.daily/slocate
david@growler:~$
```
I have given it almost an hour to index about 1 TB of data. It does not seem to be indexing all of my filesystems:  
```
david@growler:~$ locate address
/usr/share/doc/ifupdown/examples/check-mac-address.sh
/usr/share/doc/ifupdown/examples/get-mac-address.sh
/usr/share/doc/libncurses5-dev/html/ada/terminal_interface-curses-forms-field_types-ipv4_address__adb.htm
/usr/share/doc/libncurses5-dev/html/ada/terminal_interface-curses-forms-field_types-ipv4_address__ads.htm
/usr/src/linux-headers-2.6.24-27-server/include/config/mtd/docprobe/address.h
/usr/src/linux-headers-2.6.24-27-server/include/config/mtd/nand/diskonchip/probe/address.h
/usr/src/linux-headers-2.6.24-27-server/include/config/scsi/sym53c8xx/dma/addressing
/usr/src/linux-headers-2.6.24-27-server/include/config/scsi/sym53c8xx/dma/addressing/mode.h
/usr/src/linux-headers-2.6.24-28-server/include/config/mtd/docprobe/address.h
/usr/src/linux-headers-2.6.24-28-server/include/config/mtd/nand/diskonchip/probe/address.h
/usr/src/linux-headers-2.6.24-28-server/include/config/scsi/sym53c8xx/dma/addressing
/usr/src/linux-headers-2.6.24-28-server/include/config/scsi/sym53c8xx/dma/addressing/mode.h
david@growler:~$
```

I have many files in my /media directory and subdirectories with "address" in them.

What could be the problem?  This is what that cron job looks like: 

```

david@growler:~$ more /etc/cron.daily/slocate
#! /bin/sh

if [ -x /usr/bin/slocate ] && [ ! -x /usr/bin/mlocate ]
then
        if [ -f /etc/updatedb.conf ]
        then
                . /etc/updatedb.conf
        fi

        # Adjust I/O priority of current process (default: best effort)
        ionice -c ${IONICE_CLASS:-2} -n ${IONICE_PRIORITY:-7} -p $$

        if [ -f /etc/updatedb.conf ]
        then
                nice -n ${NICE:-10} /usr/bin/slocate -u
        else
                nice -n ${NICE:-10} /usr/bin/slocate -u -f proc
        fi
        chown root.slocate /var/lib/slocate/slocate.db
fi
david@growler:~$
```

---

### Post by capscrew on 2010-08-24
> **davidshere said:**
> I've found information about slocate... 
I think it is working.  Try this:  Create a test file in your home directory  ```
touch ~/updatedb.test
```
Look for using slocate ```
locate updatedb.test
```

This should fail as you have not updated the slocate database.  Now update slocate```

sudo updatedb
```

Now test locate again```
locate updatedb.test
```

The file should now be found.

---

### Post by davidshere on 2010-08-27
Thanks!  Your example does work.

Apparently the cron job "/etc/cron.daily/slocate" does not update the database.  Do I have to write my own cron job to do this?

---

### Post by capscrew on 2010-08-27
> **davidshere said:**
> Thanks!  Your example does work.

Apparently the cron job "/etc/cron.daily/slocate" does not update the database.  Do I have to write my own cron job to do this?

There are 2 file indexing front ends and by default they use different databases.  One is [COLOR="Red"]**locate **[/COLOR]and another is [COLOR="Blue"]**slocate**[/COLOR].

Try the same thing using slocate only and you will see.  The man pages will also shed some light.

**[COLOR="Green"]Edit: There already is a cron job both databases.  You might have to manually initialize the database for it to work correctly.  But then again you may have done that.  Try using both *slocate *and *locate *  to locate the files.[/COLOR]**

---

