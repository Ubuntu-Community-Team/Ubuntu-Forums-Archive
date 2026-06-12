---
title: "mhddfs.log too big!"
date: 2010-04-27
forum: Server Platforms
---

### Post by gobbledigook on 2010-04-27
hey there!

I use mhddfs to fuse my drives together into one.... but i have noticed that the log file gets [SIZE="5"]HUGE![/SIZE]

would somebody be kind enough to explain to me how to make it split say... every week? or when it gets to a certain size? oh! and only to have say 5 logs archived :)

the line in fstab looks like:
```

#mhddfs
mhddfs#/media/movies/~/media/server fuse logfile=/var/log/mhddfs.log,allow_other 0 0
```

thanx!!

---

### Post by cdenley on 2010-04-27
I know how to make the log rotate, but I'm not sure how to make fuse start using the new log file. If you give me a script which would safely remount your filesystem so a new log is used, then I will give you a logrotate configuration which should work.
```

man logrotate

```

---

### Post by gobbledigook on 2010-04-27
cool that would be great!

But i'm having some trouble getting my samba shares to reconnect after i run the script? 

```
#!/bin/sh
#-------------------------------------------------------------
# A simple script to restart mhddfs
#-------------------------------------------------------------

#variables:

PID=$(pidof mhddfs)

#-------------------------------------------------------------
#kill mhddfs
kill -15 $PID

#give it a chance to close cleanly
sleep 5

#start mhddfs
mhddfs /media/movies-and-other-stuff/,/media/swap/,/media/series/,/media/extra/ /media/server -o logfile=/var/log/mhddfs.log

#restart samba
/etc/init.d/samba restart
#-------------------------------------------------------------

```

the script seems to exit without error:

```
server@server:~$ sudo ./kill_mhddfs
mhddfs: directory '/media/movies-and-other-stuff/' added to list
mhddfs: directory '/media/swap/' added to list
mhddfs: directory '/media/series/' added to list
mhddfs: directory '/media/extra/' added to list
mhddfs: mount to: /media/server
mhddfs: using debug file: /var/log/mhddfs.log, loglevel=2
mhddfs: move size limit 4294967296 bytes
 * Stopping Samba daemons                       [ OK ]
 * Starting Samba daemons                       [ OK ]

```

however it seems i have changed the permissions/ownership of the mountpoint? Which is also my samba share...

If i try to look at the mountpoint on the server i can only see it using sudo:

```
server@server:~$ ls /media/server
ls: cannot access /media/server: Permission denied
server@server:~$ sudo ls /media/server
incomplete  lost+found  movies-music-and-stuff  series  swap

```

i feel so close! But the only way (i could figure) to connect through samba was to reboot?

in the meantime i will check out logrotate :)

Thanx!

plus... do you think it would help to make it sleep a few seconds after starting mhddfs?

---

### Post by cdenley on 2010-04-27
/etc/logrotate.d/mhddfs
```

/var/log/mhddfs.log {
    size 100k
    rotate 5
    compress
    delaycompress
    missingok
    postrotate
        killall -w mhddfs
        mhddfs /media/movies-and-other-stuff/,/media/swap/,/media/series/,/media/extra/ /media/server -o logfile=/var/log/mhddfs.log
        /etc/init.d/samba restart
    endscript
    create 640 root adm
}

```

or I would think this would work:
```

/var/log/mhddfs.log {
    size 100k
    rotate 5
    compress
    delaycompress
    missingok
    postrotate
        umount /media/server
        mhddfs /media/movies-and-other-stuff/,/media/swap/,/media/series/,/media/extra/ /media/server -o logfile=/var/log/mhddfs.log
    endscript
    create 640 root adm
}

```

---

### Post by gobbledigook on 2010-04-28
ah, thanx for taking the time to look at this :)

i see what the different commands do from the logrotate manpage, very cool... and pretty simple, when you know how ;)

I'll have to check this out later on when i'm back from work... i assume i don't need the script i knocked up, but will have to see if i have the same issue after remounting

I like the killall -w command... learn new stuff all the time here :)

will let you know how i get on later.

---

