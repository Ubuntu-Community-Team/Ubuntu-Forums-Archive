---
title: "Problem with cron on Server 8.04 LTS"
date: 2009-10-21
forum: Server Platforms
---

### Post by tuxx on 2009-10-21
Hello ppl,

I have a very, to me, strange problem with my rdiff-backup script and cron.

I won't run a.k.a. it starts on time, touches my rdiff-backup-data dir inside my destinationdir and then via 'top' I can see rdiff-backup aint running.

Syslog informs me cron starts my script. Nowhere on my system can I see any errors - it's like it believes everything is okay.

If I run my script manually via cli it runs and completes fine. If I take my command from within my script and put that in my crontab it does the same as explained above, so it's not a scriptissue.

My localuser (the one who runs the script) is in cron.allow (I've tried with and without).

Any clues? It's very odd to me!

Best regards,

---

### Post by Lars Noodén on 2009-10-21
Are you depending on any environment variables, such as PATH, which need to be set explicitly?

---

### Post by tuxx on 2009-10-21
Hrm, maybe, but I can't see why. I have my script within my homedir/bin and that is in my path.

Also, if I take out the command from the script and put it directly in crontab it also fails on completion.

Something is running/working as my rdiff-backup-data dir gets "touched" (timestamp updated) but no data within is updated, neither files nor logs plus rdiff-backup aint showing from 'top'.

---

### Post by tuxx on 2009-10-21
> **tuxx said:**
> Hrm, maybe, but I can't see why. I have my script within my homedir/bin and that is in my path.



Just for the sake of proof I tested it - provided full path within the script, but sadly with the same end-result :-(

This is driving me nuts, figurely speaking :confused:

---

### Post by Lars Noodén on 2009-10-21
Ok.  I apologize that the following will be very lame.  

Copy your script.  In the copy, put an echo before each normal line, set to append to some file in /var/tmp, a temp directory which stays between reboots.

e.g. original:

[INDENT][FONT="Courier New"]find
rsync
touch[/FONT][/INDENT]

modified copy:
[INDENT][FONT="Courier New"]
echo > /var/tmp/x

echo "One" >> /var/tmp/x
find

echo "Two" >> /var/tmp/x
rsync

echo "Three" >> /var/tmp/x
touch[/FONT][/INDENT]

Then set cron to run your modified script two minutes from now (if you have enough time to edit and save cron before the top of the minute, then one minute will do)

That should at least show which line it gets stuck on.

---

### Post by tuxx on 2009-10-21
Hey,

I tried that just now, but I'm not sure what I/we can learn from the output as I've got only one command.

Here's my original script:

#!/bin/sh
/usr/bin/rdiff-backup -v6 --exclude /home/martinlj/.hellanzb /home/martinlj /mnt/sdb-backup/guldfaxe/rdiff-backup

Here's the altered one:
#!/bin/sh
echo > /var/tmp/xxx
echo "One" >> /var/tmp/xxx
/usr/bin/rdiff-backup -v6 --exclude /home/martinlj/.hellanzb /home/martinlj /mnt/sdb-backup/guldfaxe/rdiff-backup

Output from /var/tmp/xxx is:
One

Using a script for my backup may seem overkill, but that script is in it's early stages as I intend on improving it over time. I therefore tried to see if it makes any difference with the pure command in crontab instead if the script, but it's the same'ol result.

---

### Post by Lars Noodén on 2009-10-22
> **tuxx said:**
> Hey,

I tried that just now, but I'm not sure what I/we can learn from the output as I've got only one command.

Here's my original script:

#!/bin/sh
/usr/bin/rdiff-backup -v6 --exclude /home/martinlj/.hellanzb /home/martinlj /mnt/sdb-backup/guldfaxe/rdiff-backup

Here's the altered one:
#!/bin/sh
echo > /var/tmp/xxx
echo "One" >> /var/tmp/xxx
/usr/bin/rdiff-backup -v6 --exclude /home/martinlj/.hellanzb /home/martinlj /mnt/sdb-backup/guldfaxe/rdiff-backup

Output from /var/tmp/xxx is:
One

Using a script for my backup may seem overkill, but that script is in it's early stages as I intend on improving it over time. I therefore tried to see if it makes any difference with the pure command in crontab instead if the script, but it's the same'ol result.

Using a script is the right way to do  it.  It allows you to add or change things much more easily as you need.  

Ok.  The script is simpler than I thought.  If there is output from the script it should be found in a e-mail sent locally to the user under whose account the cron job is run.  You can also try capturing the output by modifying the rdiff-backup line to redirect both stdout and stderr to the tracking file:

```

 # catch both output and error messages:
 /usr/bin/rdiff-backup -v6 --exclude /home/martinlj/.hellanzb \
    /home/martinlj /mnt/sdb-backup/guldfaxe/rdiff-backup >> /tmp/xxx 2>&1
 # add this line too:
 echo "rdiff-backup exited with status code '$?'" >> /tmp/xxx

```

That should trap error message as well.

---

### Post by tuxx on 2009-10-22
Hi Lars,

Thanks for your effort.

I went ballistic sometime yesterday and deleted my entire rdiff-backup and updated my crontab with a more specific runtime. Plus I installed postfix (I didn't have a MTA at first).

Presto - it worked - this morning I had an unattended backup on my second drive.

However I'll not mark this thread solved yet, I'm still a bit pessimistic so I'll let it run for a few days and see if it runs as intented.

I'm still not sure _what_ made it work though..

---

### Post by tuxx on 2009-10-23
Well, it has been running for 2 nights now, all well.

I guess we can call it solved.

---

