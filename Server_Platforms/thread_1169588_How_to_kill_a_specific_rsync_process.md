---
title: "How to kill a specific rsync process?"
date: 2009-05-25
forum: Server Platforms
---

### Post by Underpants on 2009-05-25
How to kill a specific rsync process? 

I have a server that runs a few different rsync processes that take lots of time. These processes are invoked by shell script and a scheduled cron job. All of the scripts run every day. One of them sometimes has to deal with more data than there is time in the day to deal with. 
(the long running job copies a bunch of stuff over a WAN)
So I need a way that the script can kill the previous version of itself when it is run on the next day, if it is still running. If I dont do this, multiple copies of the script will run simultaneously and run the same rsync command over and over and over and bog down the connection to an unusable point, making the script take longer and longer and run more... you get the idea.

Whats the best way to do this? Using the script, can I put a timeout in it? Can I make rsync run under a certain process ID and kill just the specific rsync that I want? What's the safest way to go about this?

---

### Post by leandromartinez98 on 2009-05-25
You can use the "--timeout=XXX" option of rsync, which determines the
maximum time (in seconds) of the transfer. 

However, it is strange that you get that king of load if only modified
files are updated. In this case, the second rsync process shouldn't do 
many things if the first one has already backed up the same files. At the
same time, if all the files have been modified, stoping the previous 
rsync process will turn out to only backup the same files (leaving the
end of the backup always incomplete).

---

### Post by Underpants on 2009-05-25
I'll try the timeout.

Just to clarify:

I'm working with a 10mbit line and hundreds of gigs of data. 
for the sake of explaining this, lets say that on Monday the data sync will take 36 hours.

so on monday, rsync fires up, and works for 24 hours, then on tuesday, the same rsync script is invoked and starts another process doing the same thing only able to use half of the lines bandwidth, making the first one go slower. So now the rsync that was going to take 36 hours is now going to take 48 or longer, and the tuesday rsync that could have been finished in less than 24 hours could potentially turn into 48 hours because of a lack of bandwidth. 

See how that can start snowballing? I've seen as many as 8 days worth of the processes running to the point where 2 or 3 different rsync threads are working on the same file, making the process even worse :D

Get it?

---

### Post by masmad on 2009-05-25
Maybe you should look into using [rsnapshot](http://www.rsnapshot.org/), and incremental backups.

Is there a specific reason why you need to make a full backup every day? 

You can also use the scripts pid-file to kill the previous script, but wouldn't that sort of ruin the whole purpose of the backups?

---

### Post by leandromartinez98 on 2009-05-25
If your data is not being modified every day, then on the second
day rsync will do almost nothing (use the -a option for the backup
to be incremental):

```

rsync -a /source /target

```

If your data IS being modified every day, then you have a problem,
because stopping the previous rsync process will result in an
incomplete copy of your data. The new process will start from the
begining and the the final data will never be backed up. Killing,
or putting a time limit to the previous process will result in 
a backup that probably is not worthy.

Therefore, as I see, there are two options: 1) Do an incremental
backup in order that the second backup is fast, if the data
is not being modified all the time. 2) You simply cannot
do a realiable backup of your data through this connection, because
your data is generated faster than the backup can be made.

---

### Post by Underpants on 2009-05-25
This is getting off topic. I think I have my original question answered, but to continue the tangent, here is more info.

* I use synthetic or reverse incremental backups, whichever you want to call it. If you don't know what that is, check Wikipedia. The upside to this is that I NEVER have to make new "full" backups. Every day is incremental. I always have a full backup and X number of days of increments. The downside to this is that the "full" backup file changes every day and the deltas need to be sent across the wire.  Because of this rsnapshot is really not of much use. 

* My data is modified every day. Some files are 200gb+ and those files may only contain 10 or 20gb of actual changes. This is why I chose rsync to do the job.

* If you kill rsync in the middle of something it does not ruin the transfer as you have stated. You can kill it, and restart it just fine. It will blow through the part that it has already transferred at nearly 300mbit per second until it gets to the part that it hasn't updated yet. 

* Keep in mind that only 1 out of 10 days does the amount of data exceed the amount of time in a day. (ie, end of the month reporting, or development making HUGE changes to things) Letting it go over on that one day and not stopping it causes the scenario I described in my first post and it will never recover on it's own until I restart it by hand.

---

### Post by leandromartinez98 on 2009-05-25
> **Underpants said:**
> This is getting off topic...
 I think I have my original question answered, but to continue the tangent, here is more info.


Adding more info is good for other people (as me).;)

> 
* My data is modified every day. Some files are 200gb+ and those files may only contain 10 or 20gb of actual changes. This is why I chose rsync to do the job.


As I understand, the incremental backup of rsync is file by file. That is, if a single file 200gb is changed, rsync will back it up all again, even if there is a single line changed in that file. Is that wrong? If I'm wrong, which is the rsync option associated with this behaviour, because it will be very useful to me as well.

> 
* If you kill rsync in the middle of something it does not ruin the transfer as you have stated. 


Sorry, I didn't mean that. What I said is that you would be always backing up only part of your data if the rsync process is started over and over without finishing, and the data is been always modified. But clearly this is not the case, most times it does finish.

---

### Post by leandromartinez98 on 2009-05-25
Just another idea (I'm writing this because I'm interested, so don't
feel that I'm trying to convince anyone of nothing).

Instead of killing the previous rsync (which can be about to finish), an  idea would be to check if it is running and only run the new backup if the previous one is finished. This could be done by launching rsync from
a script like:

```


#!/bin/bash

# This checks if the previous rsync process is still running
check_rsync=`cat /tmp/rsync_pid`
check_rsync=`ps ax |grep $check_rsync |grep rsync`
if [ check_rsync -gt "0" ]; then
  exit
fi

# This starts the new backup and writes its pid to the file
rsync -av /source /target &
echo "$!" > /tmp/rsync_pid



```


(the $! returns the pid of the previous rsync launch).
I've not tested that, and I'm not sure if the "if" conditional
should be that way, but you get the idea.

---

### Post by Underpants on 2009-05-25
> **leandromartinez98 said:**
> Just another idea (I'm writing this because I'm interested, so don't
feel that I'm trying to convince anyone of nothing).

Instead of killing the previous rsync (which can be about to finish), an  idea would be to check if it is running and only run the new backup if the previous one is finished. This could be done by launching rsync from
a script like:

```


#!/bin/bash

# This checks if the previous rsync process is still running
check_rsync=`cat /tmp/rsync_pid`
check_rsync=`ps ax |grep $check_rsync |grep rsync`
if [ check_rsync -gt "0" ]; then
  exit
fi

# This starts the new backup and writes its pid to the file
rsync -av /source /target &
echo "$!" > /tmp/rsync_pid



```



(the $! returns the pid of the previous rsync launch).
I've not tested that, and I'm not sure if the "if" conditional
should be that way, but you get the idea.



I like the idea behind that, but I have multiple rsync processes going at once.... so I would need to modify it to grep the script name, not the rsync part.

---

