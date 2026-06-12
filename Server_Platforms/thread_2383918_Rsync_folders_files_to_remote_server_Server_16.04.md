---
title: "Rsync folders files to remote server Server 16.04"
date: 2018-01-31
forum: Server Platforms
---

### Post by patdundee on 2018-01-31
Hi Guys
Using rsync in cron to copy all files from a web server to a remote server using the following command 

```
rsync -arvzh /home/foldername/* root@***.***.***.***:/home/foldername>> /var/log/filename`date +%d%m%y`.log 2>&1
```

This works fine for all folders and files used by ftpuser and ftpgroup

However if any files or folders are added by www-data it does not copy or sync them.

How can i get it to copy all files and folders recursivly no matter who owns them please

---

### Post by TheFu on 2018-01-31
> **patdundee said:**
> How can i get it to copy all files and folders recursivly no matter who owns them please

Run as root or with sudo.  That's the only way to bypass normal file and directory permissions.  But doing that opens up other security considerations.  Remote root is a huge security issue and requires extraordinary security protections.

---

### Post by patdundee on 2018-01-31
Hi
It is already running as root with security in place on both servers. 
P

---

### Post by wildmanne39 on 2018-01-31
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by TheFu on 2018-01-31
> **patdundee said:**
> Hi
It is already running as root with security in place on both servers. 
P

Try:
```
# /usr/bin/rsync -arvzh /home/foldername/ root@***.***.***.***:/home/foldername
```

Also, any .files (files that aren't shown without the ls -a) won't be gotten in the top directory. The regex doesn't match those.  The trailing slashes can be very important.  When you run the command from a root shell, does it work?

From the rsync manpage:
```
       A  trailing slash on the source changes this behavior to avoid creating
       an additional directory level at the destination.  You can think  of  a
       trailing / on a source as meaning "copy the contents of this directory"
       as opposed to "copy the directory by  name",  but  in  both  cases  the
       attributes  of the containing directory are transferred to the containâ
       ing directory on the destination.  In other words, each of the  followâ
       ing  commands copies the files in the same way, including their setting
       of the attributes of /dest/foo:

              rsync -av /src/foo /dest
              rsync -av /src/foo/ /dest/foo
```
I'm less than 10% that this will make a difference.  I just don't use root accounts directly very often.

---

### Post by papibe on 2018-02-01
Hi patdundee.

> **patdundee said:**
> However if any files or folders are added by www-data it does not copy or sync them.
Are any of those files 'dot' files? (because it looks like your command does not transfer dot files, as TheFu pointed it out).

> **patdundee said:**
> This works fine for all folders and files used by ftpuser and ftpgroup
Try this:
```
cd /home/foldername/
sudo mkdir transfer_test
sudo touch transfer_test/file
sudo chown -R ftpuser:ftpgroup transfer_test
sudo chmod -R 700 transfer_test
```
Is the new directory and file transfered?

Regards.

---

