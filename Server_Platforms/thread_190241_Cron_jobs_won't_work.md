---
title: "Cron jobs won't work"
date: 2006-06-06
forum: Server Platforms
---

### Post by elm on 2006-06-06
Hello from Down Under!

Here is my crontab, edited via "crontab -e" and shown with "crontab -l" :



```

SHELL=/bin/bash
PATH=/usr/local/bin:/usr/local/sbin:/root/sbin:/bin:/usr/bin

* * * * * /backup/ftplogs.sh >> /backup/logs.txt
* * * * * /backup/date.sh >> /backup/logs.txt
#--------------------------------------------------------------


```

After editing (with nano) it displays "crontab: installing new crontab"
So there shouldn't be any mistakes in the syntax

The scripts should run every minute, just for testing reasons (to start off with at least)

Nothing happens. logs.txt stay empty.
If I execute the scripts from the command line, they work perfectly (ftplogs automatically transferring data, date just showing the date).
I have created the "/etc/cron.allow" file and written root in it. Still no help. ](*,) 

I created everything and am running everything as root. Even got the last empty line saved in there.


Anyone any ideas?
Thanks in advance!
Flo



BTW: Am running Ubuntu 5.10 SERVER on an old Compaq PIII with SCSI HDD and 1GB RAM.

---

### Post by linuchsan on 2006-06-06
Are the files executable?

---

### Post by Iowan on 2006-06-06
[QUOTE=elm]If I execute the scripts from the command line, they work perfectly (ftplogs automatically transferring data, date just showing the date).
[/QUOTE]I presume this means they are executable...
Where did you put the crontab file?

---

### Post by LordHunter317 on 2006-06-06
I'm pretty sure that won't execute every minute.  You need to add '/1' to the minute bit to get it to execute.

---

### Post by linuchsan on 2006-06-06
[QUOTE=Iowan]I presume this means they are executable...
Where did you put the crontab file?[/QUOTE]

not when he did sh scriptname to test the script.

---

### Post by linuchsan on 2006-06-06
[QUOTE=LordHunter317]I'm pretty sure that won't execute every minute.  You need to add '/1' to the minute bit to get it to execute.[/QUOTE]
No, * is ok.

---

### Post by benmhall on 2006-07-10
I fought with cron on Ubuntu for quite a bit too.  I found that it would would run things like "echo "test" >> /tmp/test" but wouldn't run my scripts in my home directory.  I found that if I called the script by "sh /home/test/test.sh" it would work as expected.  

So, this wouldn't work:

* * * * * /home/test/test.sh

but this does work:

* * * * * sh /home/test/test.sh

It was posted elsewhere that a new PATH is set in /etc/cronttab, so perhaps this is either a limitation or a "feature" of the default cron that you should have to call only programs in the crontab PATH.  Or maybe I'm way off.  Anyway, works for me now.

Ben

---

### Post by deadgoon on 2006-07-10
Here's the easiest way I've found to do cron.

First create a file with your job(s) in it and save it with any filename (e.g. crontab_file).  Put each job on it's own line like so:
```

* * * * * sh /home/bob/script1
* * * * * sh /home/bob/script2

```
Next run crontab with sudo on the file you just created.  Be sure to select your user with the -u option:
```

sudo crontab -u bob crontab_file

```
That should be it.  Run crontab -l to make sure it worked and enjoy the goodness of cron!

---

### Post by mikeym on 2006-07-12
I'm having similar problems to this poster - my perl scripts wont run in crontab. My crontab looks like:

```

# m h  dom mon dow   command
20 07 * * * sh /home/mikey/GetNZBFiles.sh

```

and the file it launches looks like:

```

mkdir /home/mikey/nget 2> /dev/null
mpc play
perl /usr/local/bin/nzbperl.pl /mp3/dvd/NZB/*.nzb
shutdown -h now

```

I know the script is being launched because mpc is plaing my music player daemon, but the logs show the perl script isn't starting. It does start OK when I run it from the terminal.

I have tried the script with the --daemon option where it loads as a daemon without trying to create any text graphic displays, this also doesn't work.

Any ideas?

---

