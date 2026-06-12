---
title: "AAAAhhh, need script expert with grep, piping, do whiles etc..."
date: 2008-08-22
forum: Server Platforms
---

### Post by inphektion on 2008-08-22
The basic english of what I'm trying to do is get an email any time a specific user uploads something to my ftp server.

So my thought is to grep out user and UPLOAD from the log in a tail -f command and somehow everytime that hits mail goes out.

So I have a piece of it working... if I run this:
```

root@server1:~/script# tail -F /var/log/vsftpd.log | egrep "\<bigboy\>.*\<UPLOAD\>" 
Fri Aug 22 21:24:13 2008 [pid 8210] [bigboy] OK UPLOAD: Client "10.9.8.28", "/bes_policy.xls", 228864 bytes, 44.27Kbyte/sec
Fri Aug 22 21:24:20 2008 [pid 8210] [bigboy] OK UPLOAD: Client "10.9.8.28", "/hey/BerryaCode.zip", 16250 bytes, 8.86Kbyte/sec
Fri Aug 22 22:25:58 2008 [pid 8483] [bigboy] OK UPLOAD: Client "10.9.8.28", "/BerryaCode.zip", 16250 bytes, 45.30Kbyte/sec

```
and this works cause I uploaded after I ran the command and it showed up on my console.  

Now I'm stuck... how do I get it so every time output is added here i get an email? I have mailx installed but this did NOT work:
```

#!/bin/bash
while ((true))
do
tail -F /var/log/vsftpd.log | egrep "\<bigboy\>.*\<UPLOAD\>" | read
mail -s "UPLOAD" me@mycompany.com < mailbody
done

```

---

### Post by koenn on 2008-08-23
your script doesn't work because
a- 'read' need a variable to save the value it read
b- < mailbody assumes there is a file called mailbody in current dir, but you haven't created that file

also: this while loop will run continuously so you'll be getting the same message over and over again ; you only want this when something has changed

FIX:
1- create a cron job that runs every minute (or whatever interval seems suitable)

2- let the script save the output of tail, than the next time it runs, let it check whether the output of tail has changed.

try something like (pseudo code, untested, check syntax yourself)
```

[ -f /root/upload.latest ] || touch /root/upload.latest

tail -F -n20 /var/log/vsftpd.log | egrep "\<bigboy\>.*\<UPLOAD\>" > /root/upload.recent
diff -a -N /root/upload.latest /root/upload.recent > /root/upload.new
if [ "$?" -gt "0" ]; then 
	mail -s "UPLOAD" me@mycompany.com < /root/upload.new
	mv /root/upload.recent  /root/upload.latest
fi


```

---

### Post by thefekete on 2008-08-23
Lucky for you, Linux.com just had an [article]("http://www.linux.com/feature/144666") that may be what you're looking for...

> 
While traditional cron jobs are executed at set times, inotify cron, or incron, is a cron clone that watches the filesystem for specified changes and executes the relevant commands. You can set incron to monitor a particular file or directory for changes and schedule jobs for when those changes occur.


---

### Post by inphektion on 2008-08-23
Nice.  Both of these look promising.  I'll post back once I explore them and see which works for me the best.  I appreciate it, I was stumped with this.

edit: seems incron would allow me to run the script every time the file was modified.  This might be too frequent for me.  The benefit is that I'd know immediatley if there was an upload whereas if I used cron to run every 10 min I could be notified as late as 9 minutes later (though not a big deal).

I'll post back with what I end up with.

---

### Post by inphektion on 2008-08-23
> **koenn said:**
> 
FIX:
1- create a cron job that runs every minute (or whatever interval seems suitable)

2- let the script save the output of tail, than the next time it runs, let it check whether the output of tail has changed.

Ok I removed the -F off tail.  think that was messing it up.  So then I ran your script otherwise unmodified and on first run got.
```
0a1,4
> Fri Aug 22 14:31:51 2008 [pid 7918] [bigboy] OK UPLOAD: Client 
> "10.1.16.5", "/Device.xml", 13699 bytes, 2165.76Kbyte/sec Fri Aug 22 
> 21:24:13 2008 [pid 8210] [bigboy] OK UPLOAD: Client "10.9.8.28", 
> "/bes_policy.xls", 228864 bytes, 44.27Kbyte/sec Fri Aug 22 21:24:20 
> 2008 [pid 8210] [bigboy] OK UPLOAD: Client "10.9.8.28", 
> "/hey/BerryaCode.zip", 16250 bytes, 8.86Kbyte/sec Fri Aug 22 22:25:58 
> 2008 [pid 8483] [bigboy] OK UPLOAD: Client "10.9.8.28", 
> "/BerryaCode.zip", 16250 bytes, 45.30Kbyte/sec

```

then I uploaded one file and ran the script again and got:
```
1d0
< Fri Aug 22 14:31:51 2008 [pid 7918] [bigboy] OK UPLOAD: Client "10.1.16.5", "/Device.xml", 13699 bytes, 2165.76Kbyte/sec
4a4
> Sat Aug 23 17:04:55 2008 [pid 9466] [bigboy] OK UPLOAD: Client "10.9.8.22", "/bes_policy_v3.zip", 47772 bytes, 17.07Kbyte/sec

```


So i think maybe I need to remove anything that starts with < ? Not sure...

My last concern in running in a normal cron is if I only tail the last 20 or 50 lines every x minutes then in theory if other users pound the ftp server and generate 100 lines of log before that x minutes I could miss an upload from bigboy if it was buried in there.  This is where incron could help I presume but haven't looked into that yet... but the aptitude show of the package even shows: server upload notification
> incron can be used to : 
 * notifying programs (e.g. server daemons) about changes in configuration 
 * guarding changes in critical files (with their eventual recovery) 
 * file usage monitoring, statistics 
 * automatic on-crash cleanup 
 * automatic on-change backup or versioning 
 * new mail notification (for maildir) 
 * server upload notification 
 * installation management (outside packaging systems) 
 * ... and many others 

---

### Post by inphektion on 2008-08-23
ok script now is:
```
#!/bin/bash
[ -f /root/upload.latest ] || touch /root/upload.latest

tail -n50 /var/log/xferlog | egrep "\<i\>.*\<bigboy\>" > /root/upload.recent
diff -a -N /root/upload.latest /root/upload.recent > /root/upload.new
if [ "$?" -gt "0" ]; then 
        mail -s "UPLOAD" me@mycompany.com < /root/upload.new
        mv /root/upload.recent  /root/upload.latest
fi
```

I changed to use vsftp's wuftp style xfer log.  and the "i" in the egrep is for incoming.  Now it seems to be working well I'm only getting the latest upload in the email whereas when I was using the full vsftpd.log i seemed to be getting the one prior and maybe other things that might have changed....

Anyway if I make the tail 100 lines and put it in incron with IN_CLOSE_WRITE for the log this just might be perfect.

If anyone has any improvements or pitfalls I'm overlooking please let me know.  thanks.

OH QUESTION, multiple emails in the script? separate by comma?

EDIT:  just put this in incrontab
/var/log/xferlog IN_CLOSE_WRITE /root/script/ftpupload.sh $@/$#

seems to be working..

---

