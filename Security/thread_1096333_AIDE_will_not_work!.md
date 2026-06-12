---
title: "AIDE will not work!"
date: 2009-03-14
forum: Security
---

### Post by computer_freak_8 on 2009-03-14
I am trying to run the "aide" program, but I have a very aggravating situation that is preventing it.

Whenever I try to run it, (trying to "check",) whether as root or another user, I am presented with:
```
Couldn't open file /var/lib/aide/please-dont-call-aide-without-parameters/aide.db for reading

```
or
```
Extra parameters given
```

I have tried many commands, including:
```
aide -C
aide --check
aide -V
**aide -V 20**
aide --verbose
aide -C -V
**aide -C -V 20**
aide --check --verbose
aide --check --verbose=20
aide -C -r stdout
aide --check -r stdout
aide -V -r stdout
**aide -V 20 -r stdout**
aide --verbose -r stdout
aide -C -V -r stdout
**aide -C -V 20 -r stdout**
aide --check --verbose -r stdout
aide --check --verbose=20 -r stdout
aide -C --report=stdout
aide --check --report=stdout
aide -V --report=stdout
aide -V 20 --report=stdout
aide --verbose --report=stdout
aide -C -V --report=stdout
**aide -C -V 20 --report=stdout**
aide --check --verbose --report=stdout
aide --check --verbose=20 --report=stdout
```

The commands in bold give the second error; all the rest of the commands give the first error.


This is really irritating; I'm questioning if I will be able to finish my project in time.

Any help would definitely be appreciated!

---

### Post by bodhi.zazen on 2009-03-15
I have not used AIDE. See if these links help :

[http://www.linux.com/feature/113919](http://www.linux.com/feature/113919)

[http://www.securityfocus.com/infocus/1424](http://www.securityfocus.com/infocus/1424)

---

### Post by shad0w_crash on 2009-03-15
I once got that problem on FreeBSD, The problem was that the database file was initialized but not filled. 

I replaced it with an other version and it worked perfectly. What are the permissions of the .db file? Maby the installer, updater is still locking it because it's updating?

---

### Post by MattBlack on 2009-03-19
Get the same think here when run the commands manually.
sudo /etc/cron.daily/aide does work ok.

will do more investigation later.

---

### Post by crazybrain on 2009-03-29
I had the same issue, and about lost my mind trying to find the answer.

These two links helped a ton:

[http://fixunix.com/debian/121980-aide.html](http://fixunix.com/debian/121980-aide.html)

[http://svn.debian.org/wsvn/pkg-aide/trunk/debian/aide-common.README.Debian?op=file&rev=0&sc=0](http://svn.debian.org/wsvn/pkg-aide/trunk/debian/aide-common.README.Debian?op=file&rev=0&sc=0)

I'm still working with this so I haven't gotten it completely figured out yet. Good luck.

---

### Post by StefanX on 2009-04-06
Try "aide.wrapper" instead of "aide", so "aide.wrapper -i" or even "aideinit".

---

### Post by pocake on 2009-04-13
Hi, 
I have got the same error when run aide first time before init database. The command /etc/cron.daily/aide takes a long time but fix the problem. AIDE built the database.

Link [http://www.debuntu.org/intrusion-detection-with-aide](http://www.debuntu.org/intrusion-detection-with-aide)

---

### Post by computer_freak_8 on 2009-05-20
Finally I got a chance to try this again!

I have tried everything listed in this thread, except for the cron job. I don't want it to completely automate the whole process; I want to learn how to do it manually.
Here are some attempts:
```
root@Team-3:~# **aide --init**
Couldn't open file /var/lib/aide/please-dont-call-aide-without-parameters/aide.db.new for writing
root@Team-3:~# **aide -i**
Couldn't open file /var/lib/aide/please-dont-call-aide-without-parameters/aide.db.new for writing
root@Team-3:~# **aideinit** 
Running aide --init...
34:syntax error:(
34:Error while reading configuration:(
Configuration error
AIDE --init return code 17; see */var/lib/aide/aide.db.new* for details
root@Team-3:~# **aide.wrapper** 
34:syntax error:(
34:Error while reading configuration:(
Configuration error
root@Team-3:~# **aide.wrapper -i**
34:syntax error:(
34:Error while reading configuration:(
Configuration error
root@Team-3:~# **aide.wrapper --init**
34:syntax error:(
34:Error while reading configuration:(
Configuration error

```
And also:
```
root@Team-3:~# **cat /var/lib/aide/aide.db.new**
cat: /var/lib/aide/aide.db.new: No such file or directory

```

Any other ideas?

---

### Post by Pev on 2010-08-31
After following the links on this page I managed to get it working for me.
After installing aide
```
#sudo apt-get install aide 
```I ran
```
sudo touch /var/lib/aide/aide.db
sudo chmod 755 /var/lib/aide/aide.db
```
and finally 
```
sudo aide --config=/usr/share/aide/config/aide/aide.conf --check
```

Thanks,
Pev

---

### Post by rarb on 2010-12-22
Regarding the post from Pev
"I ran
Code:
sudo touch /var/lib/aide/aide.db
sudo chmod 755 /var/lib/aide/aide.db"

making the file executable and readable by world and group is not advisable from a security point of view

I recommend leaving it as 
sudo chmod 600 /var/lib/aide/aide.db
to keep defence in depth

see the NIST guidelines on hardening redhat enterprise - it discusses setting up aide securely that also works with ubuntu

R

---

### Post by bkasterm on 2011-08-02
I had the same error message.  In my case it was caused by having a configuration file that did not specify the locations of the database files.  Adding the following three lines (with FILENAME specified) resolved this problem.

```

database=file:FILENAME.db
database_out=file:FILENAME.db.new
database_new=file:FILENAME.db.new

```

---

### Post by GhettoYhetti on 2012-03-01
**Below is a sample of /etc/aide/aide.conf (0600 permissions or rw- --- --- if you will)**
```
# AIDE conf

# The daily cron job depends on these paths
database=file:/var/lib/aide/aide.db
database_out=file:/var/lib/aide/aide.db.old
database_new=file:/var/lib/aide/aide.db.new
gzip_dbout=yes

#AIDE conf

   # Here are all the things we can check - these are the default rules 
   #
   #p:      permissions
   #ftype:  file type
   #i:      inode
   #n:      number of links
   #l:      link name
   #u:      user
   #g:      group
   #s:      size
   #b:      block count
   #m:      mtime
   #a:      atime
   #c:      ctime
   #S:      check for growing size
   #I:      ignore changed filename
   #md5:    md5 checksum
   #sha1:   sha1 checksum
   #sha256: sha256 checksum
   #sha512: sha512 checksum
   #rmd160: rmd160 checksum
   #tiger:  tiger checksum
   #haval:  haval checksum
   #crc32:  crc32 checksum
   #R:      p+ftupe+i+l+n+u+g+s+m+c+md5
   #L:      p+ftype+i+l+n+u+g
   #E:      Empty group
   #>:      Growing logfile p+ftype+l+u+g+i+n+S
   #The following are available if you have mhash support enabled:
   #gost:   gost checksum
   #whirlpool: whirlpool checksum
   #The following are available and added to the default groups R, L and >
   #only when explicitly enabled using configure:
   #acl:    access control list
   #selinux SELinux security context
   #xattrs:  extended file attributes
   #e2fsattrs: file attributes on a second extended file system

   # You can alse create custom rules - my home made rule definition goes like this 
   #
   MyRule = p+i+n+u+g+s+b+m+c+md5+sha1 

   # Next decide what directories/files you want in the database

   /etc p+i+u+g     #check only permissions, inode, user and group for etc
   /opt p+i+u+g	    #check only permissions, inode, user and group for opt
   /bin MyRule      # apply the custom rule to the files in bin 
   /usr/bin MyRule      # apply the custom rule to the files in bin 
   /usr/local/bin MyRule      # apply the custom rule to the files in bin 
   /sbin MyRule     # apply the same custom rule to the files in sbin 
   /usr/sbin MyRule     # apply the same custom rule to the files in sbin 
   /usr/local/sbin MyRule     # apply the same custom rule to the files in sbin 
   /var MyRule		
   !/var/log/.*     # ignore the log dir it changes too often
   !/var/spool/.*   # ignore spool dirs as they change too often
   !/var/log/wtmp$  # ignore the file /var/log/wtmp
   !/var/log/btmp$  # ignore the file /var/log/btmp
   !/var/lib/urandom
   !/var/mail/.*
   !/var/run/.*
   !/var/tmp/.*
   !/var/lib/urandom/random-seed
```

**[COLOR="Red"]Customize the above for what you want to check.[/COLOR] Keep in mind this is really basic.**

**Then run the following:**

```
sudo /usr/bin/aide.wrapper -c /etc/aide/aide.conf --init

```

**Then run:**

```
sudo /usr/bin/aide.wrapper -c /etc/aide/aide.conf --check

```

**Then:**

```
sudo /usr/bin/aide.wrapper -c /etc/aide/aide.conf --compare

```

**followed by:**

```
sudo /etc/cron.daily/aide
```

**Per your aide.conf, the following files should now exist:**

```
your-machine-name:/var/lib/aide# ls -rot
total 3124
-rw------- 1 root 1062640 2012-03-01 20:10 aide.db
-rw------- 1 root 1062640 2012-03-01 20:11 aide.new
-rw------- 1 root    1544 2012-03-01 20:29 aide.conf.autogenerated
-rw------- 1 root 1062722 2012-03-01 20:29 aide.db.old

```

**You should get an email notification for root (if you have it configured)**

**Tweak as necessary.  Celebrate that AIDE is working for you**

---

