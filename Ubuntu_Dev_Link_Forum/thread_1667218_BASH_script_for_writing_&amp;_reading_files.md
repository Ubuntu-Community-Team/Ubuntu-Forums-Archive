---
title: "BASH script for writing &amp; reading files"
date: 2011-01-14
forum: Ubuntu Dev Link Forum
---

### Post by Rodayo on 2011-01-14
I'm writing a bash script that will write a random file with a specified filesize(in my case 1G) and then read that same file. Both the write time and read time need to be logged and stored somewhere.

This is my first time writing a bash script and I've sorta been freestyling and making assumptions about the syntax so feel free to point out those kinds of mistakes:

```
#write a 1G file and store the write-time in rw_log
w_start = date +%s
dd bs=1G count=1 if=/etc/urandom of=/var/local/rangedb/0/tmp_file
w_stop = date +%s
echo "Write iteration x: " + w_stop-w_start  + "\n" >> /home/user_1/Documents/rw_log

#pause for 1 second
sleep 1

#read the same file and store the read-time in rw_log
r_start = date +%s
read /var/local/0/tmp_file
r_stop = date +%s
echo "Read iteration x: " + rstop-r_start + "\n" >> /home/user_1/Documents/rw_log
```

The whole procedure will be looped later so that's what the iteration stuff is. 

I'm assuming the "read" command works on files and hopefully I used it properly.

Any sort of help would be appreciated.

---

### Post by sanderj on 2011-01-14
Running (and debugging) this script on your own Ubuntu system will give you better feedback.

Apart from that: how about this:

```
sander@quirinius:~$ time dd bs=1k count=1000 if=/dev/urandom of=/tmp/weg

1000+0 records in
1000+0 records out
1024000 bytes (1.0 MB) copied, 1.44488 s, 709 kB/s

real	0m1.473s
user	0m0.012s
sys	0m0.892s
sander@quirinius:~$
```

---

### Post by Rodayo on 2011-01-14
> **sanderj said:**
> Running (and debugging) this script on your own Ubuntu system will give you better feedback.

Apart from that: how about this:

```
sander@quirinius:~$ time dd bs=1k count=1000 if=/dev/urandom of=/tmp/weg

1000+0 records in
1000+0 records out
1024000 bytes (1.0 MB) copied, 1.44488 s, 709 kB/s

real    0m1.473s
user    0m0.012s
sys    0m0.892s
sander@quirinius:~$
```

Yes, I read about that function. But couldn't figure out how to pipe that part in the first line("1.473s" from your example) to an output file or a variable at least.

---

### Post by Rodayo on 2011-01-14
I actually just finished the script. So I'm gonna mark this as solved.

---

