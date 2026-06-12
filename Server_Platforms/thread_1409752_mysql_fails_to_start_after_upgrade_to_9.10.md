---
title: "mysql fails to start after upgrade to 9.10"
date: 2010-02-18
forum: Server Platforms
---

### Post by alexm@nus.edu.sg on 2010-02-18
I've just upgraded to 9.10, and mysql fails to start. When I do an /etc/init.d/mysql start, I just get 
 * Starting MySQL database server mysqld
   ...fail!
with no additional errors or information to say what went wrong. :(

I saw this thread [http://ubuntuforums.org/showthread.php?t=1322070](http://ubuntuforums.org/showthread.php?t=1322070) but the fix mentioned does  not apply, as I don't have the *#skip bsd* line in my config file.

Anyone have any suggestions?

thanks,
Alex

---

### Post by ARhere on 2010-02-18
just a wild shot, but are you out of disk space?  It will not start without the free space.

type df -h just to be sure.

-AR

---

### Post by alexm@nus.edu.sg on 2010-02-21
Thanks for the suggestion, but I don't think that's the problem:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              39G  3.9G   33G  11% /
tmpfs                  39G  3.9G   33G  11% /lib/init/rw
varrun                 39G  3.9G   33G  11% /var/run
varlock                39G  3.9G   33G  11% /var/lock
udev                   10M   20K   10M   1% /dev
df: `/dev/shm': No such file or directory

Not sure what the last line, complaining about /dev/shm, signifies, or whether that may be related.

Note that my server is also having the following problem, in case that suggests a possible cause: 
[http://ubuntuforums.org/showthread.php?t=1409157](http://ubuntuforums.org/showthread.php?t=1409157) 

thanks!
Alex

---

### Post by endeavormac on 2010-02-21
There may be something useful in /var/log/mysql.err

Try:

sudo cat mysql.err

Let us know what you get

---

### Post by datdesignguy on 2010-03-08
Alex,

Did you ever solve this problem?

I've isolated what the problem is on mine... If your upgrade was causing an unstable connection and you did something like what was suggested in [this thread here]("http://ubuntuforums.org/showthread.php?t=1319631&page=2"), then you most likely lost your loopback address. I did. Trying to figure out how to fix it ATM.

Hope this helps,

-datdesignguy

---

### Post by alexm@nus.edu.sg on 2010-04-30
Sorry, no I never figured this out. Will try again after upgrading to 10.4...

---

