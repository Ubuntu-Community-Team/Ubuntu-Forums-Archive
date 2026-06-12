---
title: "How-to for crontab"
date: 2005-12-12
forum: Tutorials
---

### Post by ardchoille on 2005-12-12
**What Is Crontab?**

A crontab is a simple text file that holds a list of commands that are to be run at specified times. These commands, and their related run times, are controlled by the cron daemon and are executed in the system's background. More information can be found by viewing the crontab's man page. We will run through a simple crontab example later.


**How Does It Work?**

The system maintains a crontab for each user on the system. In order to edit or create a crontab, you must use the text editor that is specified by your system. The nano text editor is the default text editor on my system. This text editor must be opened with the command crontab using the -e option. To create a crontab open a term and type:

```
crontab -e
```

The nano text editor will open with a blank window for the desired times and commands to be entered. Each line represents a seperate crontab entry - also known as a "cron job". If you are not familiar with the nano text editor you should obtain a tutorial for it as that information is beyond the scope of this post.


**Crontab Sections**

Each of the sections is separated by a space, with the final section having one or more spaces in it. No spaces are allowed within Sections 1-5, only between them. Sections 1-5 are used to indicate when and how often you want the task to be executed. This is how a cron job is layed out:

minute (0-59), hour (0-23, 0 = midnight), day (1-31), month (1-12), weekday (0-6, 0 = Sunday), command

```
01 04 1 1 1 /usr/bin/somedirectory/somecommand
```

The above example will run /usr/bin/somedirectory/somecommand at 4:01am on any Monday which falls on January 1st. An asterisk (*) can be used so that every instance (every hour, every weekday, every month, etc.) of a time period is used. Code:

```
01 04 * * * /usr/bin/somedirectory/somecommand
```

The above example will run /usr/bin/somedirectory/somecommand at 4:01am on every day of every month.

Comma-seperated values can be used to run more than one instance of a particular command within a time period. Dash-seperated values can be used to run a command continuously. Code:

```
01,31 04,05 1-15 1,6 * /usr/bin/somedirectory/somecommand
```

The above example will run /usr/bin/somedirectory/somecommand at 01 and 31 past the hours of 4:00am and 5:00am on the 1st through the 15th of every January and June.

The "/usr/bin/somedirectory/somecommand" text in the above examples indicates the task which will be run at the specified times. It is recommended that you use the full path to the desired commands as shown in the above examples. The crontab will begin running as soon as it is properly edited and saved.


**Crontab Options**

The -l option causes the current crontab to be displayed on standard output.
The -r option causes the current crontab to be removed.
The -e option is used to edit the current crontab using the editor specified by the VISUAL or EDITOR environment variables.

After you exit from the editor, the modified crontab will be checked for accuracy and, if there are no errors, installed automatically.


**Crontab Example**

Below is an example of how to setup a crontab to run updatedb, which updates the slocate database: Open a term and type "crontab -e" (without the double quotes) and press enter, type the following line, substituting the full path for the one shown below, into the editor:

```
45 04 * * * /usr/bin/updatedb
```

Save your changes and exit the editor.

Crontab will let you know if you made any mistakes. The crontab will be installed and begin running if there are no errors. That's it. You now have a cron job setup to run updatedb, which updates the slocate database, every morning at 4:45.

Note: The double-ampersand (&&) can also be used in the "command" section to run multiple commands consecutively. 

```
45 04 * * * /usr/sbin/chkrootkit && /usr/bin/updatedb
```

The above example will run chkrootkit and updatedb at 4:45am daily - providing you have all listed apps installed.

I hope this little tutorial is of help to the community.

---

### Post by Gandalf on 2005-12-12
Nice HOWTO very usefull for crontab newbies, just want to add a simple thing but usefull, you can overwrite system editor by running
```

EDITOR=vi && crontab -e

```

replace vi with your favorite one :D

---

### Post by evs on 2005-12-12
Excellent howto!! This is very helpful stuff.  Thanks a lot.

---

### Post by ardchoille on 2005-12-12
[QUOTE=Gandalf]Nice HOWTO very usefull for crontab newbies, just want to add a simple thing but usefull, you can overwrite system editor by running
```

EDITOR=vi && crontab -e

```

replace vi with your favorite one :D[/QUOTE]
Thanks, that solves part of it. Any way to get that to be permanent?

---

### Post by ardchoille on 2005-12-12
[QUOTE=evs]Excellent howto!! This is very helpful stuff.  Thanks a lot.[/QUOTE]
You're welcome, glad it is helpful.

---

### Post by frodon on 2005-12-12
[QUOTE=ardchoille]Thanks, that solves part of it. Any way to get that to be permanent?[/QUOTE]Just put this line in your .bashrc, if you want to use gedit (for exemple) when you type crontab -e : ```
export EDITOR=gedit
```

---

### Post by ardchoille on 2005-12-12
[QUOTE=frodon]Just put this line in your .bashrc, if you want to use gedit (for exemple) when you type crontab -e : ```
export EDITOR=gedit
```[/QUOTE]
Thank you very much :)

---

### Post by ToastedToad on 2005-12-13
Thank you.

---

### Post by henriquemaia on 2005-12-14
Thanks for this Howto!

By the way, how do I run GUI commands from cron? I have done this before, in Mandrake, but in Ubuntu I just can't make it work. Does anyone know anything about this?

---

### Post by evs on 2005-12-14
[QUOTE=henriquemaia]By the way, how do I run GUI commands from cron? I have done this before, in Mandrake, but in Ubuntu I just can't make it work. Does anyone know anything about this?[/QUOTE]
KDE has a program called KCron which does the trick, but I don't know if there's anything like it for Gnome.

---

### Post by henriquemaia on 2005-12-14
[QUOTE=evs]KDE has a program called KCron which does the trick, but I don't know if there's anything like it for Gnome.[/QUOTE]

Thanks for your reply, but that is not what I meant. I do not need a GUI tool for crontab or to create cron jobs (there are also a few for gnome), but I need cron to run GUI applications, like a music player or whatever. Thanks, anyway.

---

### Post by evs on 2005-12-14
Oh ok, sorry I can't help you with that.  But I would be interested to find out how to do that as well.

---

### Post by v0xel on 2005-12-14
Would someone be interested in writing "Anacron HowTo", so we can have complete scheduling howto for Ubuntu?

---

### Post by xtacocorex on 2005-12-15
It didn't occur to me to use the export EDITOR=vi to get crontab -e to use vi. Must have been a brain fart when making my crons, since I have never done them until recently.

Thanks for the info.

---

### Post by henriquemaia on 2005-12-16
**First, an explanation**: this was meant to be a separate howto, but for some reason unknown to me, my thread didn't showed up.

To learn more about crontab, please refer to the parent post of this [**thread**]("http://ubuntuforums.org/showthread.php?t=102626&highlight=cron").

My motivation to find this out was because there are several radio shows I really like and I was always missing them. As such, I needed something to start amarok playing the chosen radio station at specific times. Probably this could be achieved through a more elegant solution, but this serves its purposes. Also, I knew that by learning how to do this, I could use it for many other things.

To accomplish this, you have to edit your crontab:

```
crontab -e
```

you can also use a nicer GUI tool to edit crontab, like **Gnome Schedule** (not in the repositories) or **KCron** (available on the repositories).

If you use a GUI tool, please adapt the instructions accordingly. I will explain this using as basis the default crontab editor.

To run a GUI command on cron, you'll have to tell cron what display the program should use. For that you use:

```
export DISPLAY=:0 
```

**:0** is the default. If you like the program to run on other display, please change the number accordingly (e.g. **:1**, **:2**, etc).

So, you add to what is explained [here]("http://ubuntuforums.org/showthread.php?t=102626&highlight=cron"):  

```
01 04 * * * /usr/bin/somedirectory/somecommand
```

the **export** variable, like this: 

```
01 04 * * * export DISPLAY=:0 && /usr/bin/somedirectory/somecommand
```

So, in my case, as I want **amarok** to play Antena2 (radio station) at a specific time, I use:

```
30 16 * * 7     export DISPLAY=:0 && amarok mms://rdp.oninet.pt/antena2 
```

This will make amarok start the Antena2 url every Sunday, at 16:30. But I want also to shut up amarok after the show is finished. So, I use:

```
0 17 * * 7     export DISPLAY=:0 && amarok -s

```

This will shut up amarok at 17:00 every Sunday. 

You can use this export trick to the limits of your imagination with every kind of application you want. 

Another example that occurs me is for file sharing and when your greedy ISPs only allows you a low monthly download limit, but have some kind of free download period (normally very late at night - this is the case of my ISP 8)). As such, I need to start nicotine (soulseek network application) only during that free period (3AM - 9AM). So, I use:

```
0 3 * * * export DISPLAY=:0 && nicotine
```

that will start nicotine everyday at 3AM. To shut it down, I use:

```
0 9 * * * killall nicotine
```

This will shut it down at 9AM.

Hope this helps some of you.

ps: I posted this here as it is related with the subject matter and to answer **evs**.

ps2: If one of the admins gets to see this, please find out what happened to my thread. I'm just wondering, because my browser looks kind of overbuggy lately (too many extensions ;) ) and I don't even know if it was sent in the first place. Thanks a lot.

---

### Post by shane2peru on 2006-12-05
very informative, and nice howto on crontab's.  Thanks.
```

30 23 05 * * tar cvpzf /home/shane/storage/homebackup.tgz --exclude=/Portable --exclude=/storage 
--exclude=/Pictures

```

Here is a simple backup crontab that I have added to mine.  My question is how can I get this to do this for root, as root?  Thanks.  Or do I need to add this here: ```

crontab -u root -e

```
and then add my backup for my file system?  Thanks.

Shane

---

### Post by NobodySpecial on 2006-12-09
shane2peru - I believe you log in as the root user, then set the crontab.

Or better yet, use the "su" command.

First, set a password for root:
```
sudo passwd root
```
Then become root:
```
su
```
Then issue your crontab commands as per above tutorial.

---

### Post by shane2peru on 2006-12-10
Oh, my bad, the real command I was using is: ```
sudo crontab -u root -e
```  Also I did get the logs to work.  Unfortunately, there was some problem with my tar, and I tried to restore a backup file, and very much messed things up so I had to re-install.

Shane

---

### Post by herbster on 2007-03-12
How could I get cron to run weighttraninglog.xls every night at 11pm? I don't know what the command is to run an .xls file, which is associated with OpenOffice for me and works fine of course, just don't know the terminal command. Anyone ??

---

### Post by pidgas on 2007-03-31
To open an xls file on a schedule just requires a synthesis of what's been put in this thread so far.  The only piece of missing info is the command for openoffice calc (like excel).  That command is "oocalc".  To open a file using oocalc from the command-line is just 

```
oocalc /path/to/file.xls
```

To get a job to do this on a schedule just create a cron job to perform following command on the schedule you wish.  The command(s) you need is/are:

```
export DISPLAY=:0 && oocalc /path/to/file.xls
```

This cron job line should do what you want to do (adjust path to your excel file as necessary)

```
00 23 * * * export DISPLAY=:0 && /usr/bin/oocalc /path/to/weigttraininglog.xls
``` 

Hope that helps!

---

### Post by herbster on 2007-04-01
pidgas,

Thanks! I just did the following:

```
crontab -e
```

then this is crontab now:
```
# m h  dom mon dow   command
0 22 * * *      export DISPLAY=:0 && /usr/bin/oocalc
/home/bobby/Desktop/bffmtracking.xls
```"

but I get this on exiting nano after saving it:
```
crontab: installing new crontab
"/tmp/crontab.k2bMoS/crontab":2: bad minute
errors in crontab file, can't install.
Do you want to retry the same edit?
```

I have changed the minutes to 00 and 0, still the same tho.

???

---

### Post by kinson on 2007-04-24
> **herbster said:**
> pidgas,

Thanks! I just did the following:

```
crontab -e
```

then this is crontab now:
```
# m h  dom mon dow   command
0 22 * * *      export DISPLAY=:0 && /usr/bin/oocalc
/home/bobby/Desktop/bffmtracking.xls
```"

but I get this on exiting nano after saving it:
```
crontab: installing new crontab
"/tmp/crontab.k2bMoS/crontab":2: bad minute
errors in crontab file, can't install.
Do you want to retry the same edit?
```

I have changed the minutes to 00 and 0, still the same tho.

???

I don't think you should have a carriage return after your /usr/bin/oocalc line. As far as I know, each crontab should be on one line only. Thats why we have the "&&"(which means "and") to string the commands together.

I tried adding a carriage return to separate my commands, and had a similar error..that bad minute thingy. I think the "2" in your error message is pointing to the line that the error occurs. (The "#" means its a comment, and probably doesn't count. But I'm not an expert on this :p )

Hope this helps.

Cheers,
Kinson

---

### Post by herbster on 2007-04-24
Kinson,

The check is in the mail my friend, that worked like a charm! It actually wasn't a carriage return, it was a normal space, but it was going to the next line because of the size of my Terminal window. I maximized it and it is now on one line, no error, and I just set it to run now and it ran perfectly. Thanks!!! :) :)

---

### Post by kinson on 2007-04-24
> **herbster said:**
> Kinson,

The check is in the mail my friend, that worked like a charm! It actually wasn't a carriage return, it was a normal space, but it was going to the next line because of the size of my Terminal window. I maximized it and it is now on one line, no error, and I just set it to run now and it ran perfectly. Thanks!!! :) :)

Yeah, I just tried that. It does seem to do that...weird :/ Maybe its some kinda word wrap setting in Nano(just guessing, absolutely no idea :p ).

Anyways, glad you got it working, crontabs would be a major feature of Linux if you ask me :)

Cheers,
Kinson

---

### Post by tommytomato on 2007-06-25
Does crontab give off a log ?

I have this in my crontab

```
 sudo crontab -l
Password:
# m h  dom mon dow   command
12 * * * * /backup/scripts/rgwlinux.sh
14 * * * * /backup/scripts/rgwforum.sh
16 * * * * /backup/scripts/rgwgallery.sh
18 * * * * /backup/scripts/rgwfishing.sh
25 * * * * /backup/scripts/rgwfamily.sh
20 * * * * /backup/scripts/rgwdatabase.sh
```


TT

---

### Post by TravMan63 on 2007-08-06
Crontabs are stored in:

/var/spool/cron/crontabs

and are stored per user name

---

### Post by md5hash on 2007-09-03
i needed this, thanks alot :guitar:

---

### Post by rshel on 2007-09-10
Great how-to.  Thanks.

But I have a question.  I have a script that backs up several directories into individual tgz files.  

tar cvpjf BackupA.bz2 DirectoryA/
tar cvpjf BackupB.bz2 DirectoryB/
tar cvpjf BackupC.bz2 DirectoryC/

and then moves them to a backup directory.

The script works great when I run it from the command line, but whenever cron executes it, the tgz files are created but they are empty.  What am I doing wrong here?

Thanks.

---

### Post by herbster on 2007-09-10
rshel,

Could be permissions of the directories? Do you use sudo when executing from CLI?

---

### Post by rshel on 2007-09-14
I don't think its a permissions thing.  The crontab executes the script as root.

---

### Post by wkdown on 2007-10-13
I guess I have an advanced cron question.  I want to set up a cron job to run a certain process, send the output to a file, but append the current date to the filename.  Example:

```
30 0 * * * netstat -lnp > netstat-lnp_DATE.txt
```

So every night at 1230am, the output goes to a file called, say, netstat-lnp_Oct13.txt

How do I get it to do that?

---

### Post by two_beers on 2007-10-13
> **wkdown said:**
> I guess I have an advanced cron question.  I want to set up a cron job to run a certain process, send the output to a file, but append the current date to the filename.  Example:

```
30 0 * * * netstat -lnp > netstat-lnp_DATE.txt
```

So every night at 1230am, the output goes to a file called, say, netstat-lnp_Oct13.txt

How do I get it to do that?

```
30 0 * * * netstat -lnp > netstat_`date +%b%d`.txt
```

This should solve your problem...

---

### Post by Mostlyharmless42 on 2007-10-29
I'm trying to get my crontab to run exaile at 6:15 a.m.
This is my crontab entry, but i can't figure out why it doesn't work.

```
# m h  dom mon dow   command
15 06 * * 1-5 export DISPLAY=:0 && /usr/bin/exaile
```

---

### Post by herbster on 2007-10-29
> **Mostlyharmless42 said:**
> I'm trying to get my crontab to run exaile at 6:15 a.m.
This is my crontab entry, but i can't figure out why it doesn't work.

```
# m h  dom mon dow   command
15 06 * * 1-5 export DISPLAY=:0 && /usr/bin/exaile
```

Try just using "exaile" instead of the full path.

---

### Post by Mostlyharmless42 on 2007-11-06
i've tried both

---

### Post by TeeAhr1 on 2007-11-21
Big thanks to ardchoille, henriquemaia, and everyone who's asked questions and posted replies in this thread.  You guys solved my problem before I even asked the question!

---

### Post by aoakley on 2008-01-02
> **rshel said:**
> tar cvpjf BackupA.bz2 DirectoryA/
...
The script works great when I run it from the command line, but whenever cron executes it, the tgz files are created but they are empty.  What am I doing wrong here?

You need to make sure you've changed into the right directory first; in your case, the directory where DirectoryA is a subdirectory. You can specify your home directory using ~/ or /home/myusername/ . For example, if DirectoryA were contained within ~/whatever :

cd /home/myusername/whatever && tar cvpjf BackupA.bz2 DirectoryA/

---

### Post by p-stone on 2008-01-05
I'm having an issue with my cron jobs. I have created a few very simple scripts, which execute perfectly from the command line, however when added as cron jobs, Here is my crontab currently
```

# m h  dom mon dow   command
#01 23 * * * /usr/bin/rsyncipod
#01 03 * * * /usr/bin/rsyncbackup
#01 01 * * 1-5 /usr/bin/newzgroups
#01 03 * * 6,0 /usr/bin/newzgroups
37 * * * * /usr/bin/newzgroups
37 * * * * /usr/bin/rsyncipod

```
the commented lines are how I would like the jobs to run eventually, the bottom two I've been using for testing, changing the minute place to a minute after the current time.
here are the two scripts (rsyncbackup has the same behavior and is almost exactly the same as rsyncipod so I won't include it)
```

#rsyncipod
#!/bin/bash
rsync -r --size-only --del /media/storage/music /media/IPOD/
rsync -r --size-only --del /media/storage/other/booksontape /media/IPOD/
touch /media/storage/downloads/rsync.done
exit 0

```
```

#nzbperl
#!/bin/sh

/usr/bin/nzbperl.pl --config /home/cornucrapia/nzbperl.cfg /media/storage/downloads/*.nzb
touch /media/storage/downloads/test.temp
rm /media/storage/downloads/*.nzb
exit 0

```
The reason I know the scripts are executing is that the files the script is supposed to touch show up after the specified time and in the case of nzbperl my nzb files are erased. The issue in each is the main command I need to run, nzbperl and rsync. I don't believe it to be a permission issue as I've used the same crontab as root and as my regular user.
If anyone knows why cron has trouble running either of these scripts I'll be eternally grateful. 
Thanks in advance

---

### Post by PhilipOwrutsky on 2008-01-24
ok so i am a super nub (running ubuntu < 2weeks), but i just spent 2.5 hrs playing around with what i think is a similar problem and i think i came up w/ a solution (tho there may be better ones).

Basically i wrote a short script to backup a bunch of files (called backup) and put it in /bin so that simply typing "backup" in a terminal does the job.  When i set up cron following the forum it didn't run as well.

i.e making my crontab
xx yy * * * backup

didn't run backup at yy xx oclock

To fix I made my crontab
xx yy * * * export DISPLAY:=0 && xterm backup

you can of course add lines to kill the xterm if you so desire...Hope this works for you / helps.

---

### Post by kranny on 2008-01-27
My Internet Connection allows me to D/l for free,from 10-pm to 6 am
So ive made a crontab entry like

00 06 * * * /sbin/poweroff
Evrything is fine but i think shutting down doesnt disconnect properly..

Between im using Reliance Dialup connection:
and use wvdial for connecting....Ctrl+c disconnects...i just need to disconnect it and then poweroff.....
 anyone help plz?

Sorry if my english is bad

---

### Post by coolbeansdude51 on 2008-01-27
Can you use these special time savers with Ubuntu?

@reboot 	Run once, at startup.
@yearly 	Run once a year, “0 0 1 1 *”.
@annually 	(same as @yearly)
@monthly 	Run once a month, “0 0 1 * *”.
@weekly 	Run once a week, “0 0 * * 0&#8243;.
@daily 	Run once a day, “0 0 * * *”.
@midnight 	(same as @daily)
@hourly 	Run once an hour, “0 * * * *”.

Examples:
Run ntpdate every hour:
@hourly /path/to/ntpdate

Make a backup everyday:
@daily /path/to/backup/script.sh

-Coolbeansdude51

---

### Post by petteriIII on 2008-01-28
> **shane2peru said:**
> very informative, and nice howto on crontab's.  Thanks. 
 
....

Here is a simple backup crontab that I have added to mine.  My question is how can I get this to do this for root, as root?  Thanks.  Or do I need to add this here: [code]

.... 
Shane

Actually, this is more a question than answer. But at least I believe that your dilemma is solved by: gksudo gedit /etc/crontab
In that file you can also define the user. But the question is: is it wise to edit that file ?

But anyway, thanks for this HowTo.

---

### Post by PhilipOwrutsky on 2008-01-28
Again super nub here and i haven't tested this yet...but the man says you can select which user's crontab you are editing explicitly... so that

sudo crontab -u root -e

should let you set up the root crontab and execute as root accordingly.

-PO

---

### Post by nflamel on 2008-01-31
Great howto! Would you mind if I translate into Spanish to post it in my blog?

---

### Post by adza on 2008-02-20
great how-to! i have a question though, i have entered the following into my crontab...

01 04 * * * /usr/local/sbin/rst_detection_tool /

to run a program to detect if my server has been hijacked for someones botnet, however i want to email the results to myself... how should i do this? can i use the sendmail, if so what is the syntax?

---

### Post by Alysum on 2008-04-30
Hello,

I wanted to edit my crontab on Ubuntu 7.10 server 

> $crontab -e
crontabs/<user>: Permission denied

This is the first time I encounter this, how do I enable/create a crontab for the user ?

I have sudo on the server but I don't want to use root's crontab for this.

I have added the user to the crontab group, it didn't help.

Strangely I'm struggling to find any answers on google, so perhaps it would be good to put that info in the first post :)

Cheers,

---

### Post by tommytomato on 2008-04-30
Are you log in as a user or root account ?

I find that once you are a root user you shouldn't have a problem editing your crontab.

crontab -l to list

crontab -e to edit

TT

---

### Post by Alysum on 2008-04-30
I thought my post clearly mentionned I'm trying to edit a user crontab (so not the root).
I have no problems with the root's crontab (sudo crontab -e) :)

---

### Post by chenel on 2008-06-05
Maybe the info in [this thread]("http://ubuntuforums.org/showthread.php?t=625184") will help.

> **Alysum said:**
> Hello,

I wanted to edit my crontab on Ubuntu 7.10 server 



This is the first time I encounter this, how do I enable/create a crontab for the user ?

I have sudo on the server but I don't want to use root's crontab for this.

I have added the user to the crontab group, it didn't help.

Strangely I'm struggling to find any answers on google, so perhaps it would be good to put that info in the first post :)

Cheers,

---

### Post by HDave on 2008-06-06
I have an a different problem.  In my case it appears that my user specific crontab doesn't run at all.  Based on some research I added a line just to see if cron was running my jobs at all...it doesn't appear to be.

However, "ps" shows cron is running.  I have restarted cron with: 
```
sudo /etc/inet.d/cron restart
```

Here is the output of "crontab -l"

```
# m h  dom mon dow   command
* * * * * /usr/bin/touch /tmp/test.file
```

Any ideas?

---

### Post by GuiGuy on 2008-06-10
> **ardchoille said:**
> **What Is Crontab?**

Note: The double-ampersand (&&) can also be used in the "command" section to run multiple commands consecutively. 


Thanks for the "How To". In respect of the &&, I wanted to execute a couple of commands consecutively. However, the editor or some other effect splits the line, thereby causing an error when I exit crontab -e.

Is there a way to deal with this situation?

Thanks

---

### Post by chochem on 2008-06-10
> **GuiGuy said:**
> Thanks for the "How To". In respect of the &&, I wanted to execute a couple of commands consecutively. However, the editor or some other effect splits the line, thereby causing an error when I exit crontab -e.

Is there a way to deal with this situation?

Thanks

Putting your commands in a shell script?

---

### Post by GuiGuy on 2008-06-10
> **chochem said:**
> Putting your commands in a shell script?

Yea, thanks, that thought had occurred. So the verdict is that multiple lines can't be handled within crontab?

---

### Post by chenel on 2008-06-10
> **GuiGuy said:**
> Thanks for the "How To". In respect of the &&, I wanted to execute a couple of commands consecutively. However, the editor or some other effect splits the line, thereby causing an error when I exit crontab -e.

Is there a way to deal with this situation?

Thanks

Is the problem just that your line is too long?  I tried it with multiple &&s and it worked fine for me.

Note that nano (the default crontab editor) splits lines longer than the width of your terminal window by default -- if you don't want it to, you need to start it with the "-w" option.  You can get this effect (so far as I can tell) by running
```
export EDITOR="nano -w" && crontab -e
```
to set the default editor to nano without line wrapping.

Hope that helps.

---

### Post by chenel on 2008-06-10
Addendum:  you can set nano to permanently never wrap lines by inserting
```
set nowrap
```
in the file .nanorc in your home directory (create if it doesn't exist).

Other nano options that can be set in the .nanorc file are listed in the  [nano manual]("http://www.nano-editor.org/dist/v2.1/nano.html#Nanorc-Files").

---

### Post by NTolerance on 2008-06-10
> **adza said:**
> great how-to! i have a question though, i have entered the following into my crontab...

01 04 * * * /usr/local/sbin/rst_detection_tool /

to run a program to detect if my server has been hijacked for someones botnet, however i want to email the results to myself... how should i do this? can i use the sendmail, if so what is the syntax?

So many discussions about crontab are carried out with little mention of one of its best features - email notification.  Anyways, I just spent some time learing about this on Hardy.  Basically crontab supports sending mail to users on the local machine by default, but it needs an SMTP server to be installed if you want to send mail to the internet.  If you just want local mail, here's what you do:
```
crontab -e
```

Add a MAILTO line in the file like so and change "localaccount" to a valid user on your Ubuntu system:
```
# m h  dom mon dow   command
MAILTO=localaccount
0 4 1,5,10,15,20,25 * * /home/nt/bin/backup.sh
```

Now, if you want to send email notifications out to the internet, you need to install an SMTP server:
```
sudo apt-get install exim4
```

Next, you will need to run through the menu-driven exim4 config:
```
sudo dpkg-reconfigure exim4-config
```

Follow the prompts.  By default exim4 will only allow mail to be sent from localhost, so you should be safe in that your Ubuntu machine won't be an SMTP relay for spam or anything.  Make sure to choose the options that allow you to send mail directly to the internet (ignore the warning about dynamic IPs getting blacklisted).  

Once exim4 setup is complete, simply put your actual email address into crontab:
```
crontab -e
```

```
# m h  dom mon dow   command
MAILTO=youraddress@gmail.com
0 4 1,5,10,15,20,25 * * /home/nt/bin/backup.sh
```

Also, if you get tired of getting emails everytime cron runs, you can have it only send email if your script or program encounters an error by adding > /dev/null to the end of any commands in your crontab or script.  Here's an example:

```
sudo rsync -avze ssh --progress --delete /etc nt@10.0.0.1:/media/hdb5/dv6000t > /dev/null
```

Finally, I want to add that my method of sending mail directly to the internet via exim4 is probably less desirable than relaying the messages through Gmail or another SMTP server, I merely use it for simplicity.  I'm open to any suggestions for configuring exim4 in a better way.

---

### Post by aysiu on 2008-06-10
Does anyone know where this crontab file is actually stored when you run the *crontab -e* command?

---

### Post by GuiGuy on 2008-06-10
> **chenel said:**
> Is the problem just that your line is 
```
export EDITOR="nano -w" && crontab -e
```
to set the default editor to nano without line wrapping.

Hope that helps.

It does. Many thanks.

---

### Post by chenel on 2008-06-10
> **aysiu said:**
> Does anyone know where this crontab file is actually stored when you run the *crontab -e* command?

```

/var/spool/cron/crontabs/(user)

```

But don't edit it there -- you'll break things.  That's what 'crontab' is for :)

---

### Post by izrafeel on 2008-06-25
Hi,

I'm trying to use crontabs to automatically shutdown some end-user computers I've configured with Ubuntu 8.04. I'm primarily interested in getting the machines to automatically shutdown at scheduled times and crontabs were suggest for this purpose ([here]("http://ubuntuforums.org/showthread.php?p=5221320#post5221320")). If there's an easier way to accomplish this task, I'd love to hear it.

In working with crontabs so far, I have two issues.

The first is that it seems only the numeric part of the "cron expression" gets validated. The specific command you want to run does not. For example, the following cron expression schedules Firefox to run everyday at 8am.

```
0 8 * * * export DISPLAY=:0 && firefox
```

After saving the changes and exiting out of nano, I get a notice in the terminal saying, "crontab: installing new crontab," and indeed Firefox does open at the designated time.

Now if I change the expression to the following:

```
0 8 * * * export DISPLAY=:0 && abc_some_fake_app
```

I get the same notice after saving my changes and exiting out - "crontab: installing new crontab." No error messages are shown even though the referenced application is bogus. Any ideas on why this might be?

My second issue brings me to the heart of my problem. Shutting down the machine with a command line requires root privileges, as in:

```
sudo shutdown -H now
```

How would I apply that to a crontab? I want to shutdown my machines at 6pm, Monday to Thursday, and at 5pm, Friday to Sunday.

I'm relatively new to Ubuntu so any help is much appreciated.

---

### Post by chenel on 2008-06-25
> **izrafeel said:**
> 
The first is that it seems only the numeric part of the "cron expression" gets validated. The specific command you want to run does not. 

That's correct.  In fact it's not designed to do that.  All cron is supposed to do is at the specified time, pass whatever it was you specified verbatim to your default shell.  (In fact, it wouldn't make sense to have it try to validate things: if you have it run some crazy Bash expression, the only way for cron to check it might be to run it... and then you could screw something up for somebody who has a super-time-sensitive command...)  The best way to check if something works is to first set it to happen every minute or something and check it.  Sidenote:  be sure to specify the whole path to any executable you want to run (e.g., /usr/bin/firefox rather than just 'firefox') because the cron daemon doesn't run things with your whole PATH... sometimes it works, but most of the time it doesn't.  This has caused no end of headaches to a lot of people.

> 

Shutting down the machine with a command line requires root privileges, as in:

```
sudo shutdown -H now
```

How would I apply that to a crontab? 

Use the root crontab:
```

sudo crontab -e

```
and put the shutdown command (without 'sudo', of course, because it'll be run as root in the first place) in there at the appropriate time.

---

### Post by md5hash on 2008-06-25
i always receive this message... 

Error: Can't open display: 0.0

heres is my cron 
*/1 * * * * export DISPLAY=:0 && $HOME/scripts/test.sh >> /home/aqlx86/test_sh.log

---

### Post by izrafeel on 2008-06-26
> **chenel said:**
> That's correct.  In fact it's not designed to do that.

So, it's by design and not in spite of it? Ok. It still seems that this whole operation would work better if it did, or at least, report an error if the command in the cron expression were invalid or at least malformed, like it does for the other components in the expression.

> **chenel said:**
> 
Use the root crontab:
```

sudo crontab -e

```
and put the shutdown command (without 'sudo', of course, because it'll be run as root in the first place) in there at the appropriate time.

I was very excited when you suggested this because it seemed like such a simple and obvious solution. When I actually tried it though, I wasn't able to get the computer to shutdown after installing the following expression:

```
* * * * * shutdown -P now
```

Neither was I able to open Firefox with this expression:

```
* * * * * export DISPLAY=:0 && /usr/bin/firefox
```

Since crontabs are user specific, this led me to believe that one user's crontabs would not run when another was logged on. Root's crontabs would not run when I'm logged in as another user. If so, is there a way to change this? If not, what am I doing wrong?

---

### Post by chenel on 2008-06-26
> **izrafeel said:**
> 
```
* * * * * shutdown -P now
```


What I said about specifying the whole path applies to things run as root, as well.  The 'shutdown' command resides in /sbin, so what you really want is
```
* * * * * /sbin/shutdown -P now
```

I tested it myself (except that I substituted the actual number of the next minute on my clock so that the computer wouldn't shut itself down the next minute after I turned it on :)) and it worked fine for me.  Hope it does for you as well.

> 
Neither was I able to open Firefox with this expression:

```
* * * * * export DISPLAY=:0 && /usr/bin/firefox
```

Since crontabs are user specific, this led me to believe that one user's crontabs would not run when another was logged on. Root's crontabs would not run when I'm logged in as another user. 

Not quite.  All crontabs run at their specified intervals, regardless of whether the user is logged in at the terminal--after all, root is *never* logged in on Ubuntu in the normal setup, so it would never run otherwise!--but you're on the right track, I think.  I'm a little fuzzy myself on the mysteries of X display handling, but my understanding is that whoever logs into X opens and then owns the display.  Thus, if you log in as one user, and then another user's cron tries to send some program to that display, X will refuse because the job doesn't have the appropriate permissions.  Similarly if no user is logged in at all; no display is open, so (obviously) your program won't be able to get a display.

Cron logs to /var/log/syslog by default, and my guess is that if you do
```
grep CRON /var/log/syslog
```
you'll see some kind of error for firefox saying that it couldn't connect to the display.  (You'll also see lots of stuff from the root crontab saying it was running 'run-parts', which is anacron doing its thing.)

Hope this helps you.

---

### Post by izrafeel on 2008-06-26
I tip my hat to you chenel. Setting the full path to shutdown did the trick and the machine quickly went down. While your explanation as to why Firefox didn't come up makes a lot of sense, in looking at the cron syslog with grep, there were no indications that errors had occurred in the processing of that command. 

I'll chalk that feature up to cron though, :)

---

### Post by chenel on 2008-06-26
Come to think of it, it's my fault, not cron's.  By default cron mails all the output of a cron job to the user who ran it.  If you don't have any program that includes a 'sendmail' binary on your system (like 'heirloom-mailx' or 'exim4', or a full-fledged mail server like postfix) then it just won't do anything.  And even if it does, you still need something (like exim4) to read the mail files, unless you want to read the mail files in /var/mail or /var/spool/mail yourself.  If you still want to see the output from a cron job (without getting mailed), you have to redirect its output:

```
* * * * * export DISPLAY=:0 && /usr/bin/firefox > $HOME/firefox.log 2>&1
```

This does two things: (1) redirect normal output from the job (STDOUT) to $HOME/firefox.log (" > $HOME/firefox.log"), and (2) redirect all messages sent to STDERR (normal error channel, which goes to the console when you're logged in) to STDOUT (" 2>&1"), which you just redirected to $HOME/firefox.log.

If you run it that way you might get more results :)

---

### Post by izrafeel on 2008-06-26
Ok, this is a good idea but I'm not too keen on having the results mailed to me from my own system, particularly if I need to install a mail server in order for it to do so. How would I generalize this expression so that the output from all cron jobs (errors in particular) get written/appended to, say, a text file in a location of my choosing?

---

### Post by chenel on 2008-06-26
So far as I know you can only redirect the output on a per-job basis (the way I described in my post from before).  You might be able to find some more help from Google...  And I haven't found it to be problematic as there are only a few jobs on my system that I really want to know output from: once I know they're working, I just redirect the output to /dev/null.  If you want finer control you could check out tools like [cronic]("http://habilis.net/cronic/").

Best wishes.

---

### Post by WARnux on 2008-07-09
Here is what I did.
I put
```
0 2	* * *	root	cd /home/scripts && ./backupHome.sh > ./backup.log
```
in /etc/crontab
then
```
sudo /etc/init.d/cron restart
```

It will run everyday at 2 am.

---

### Post by Potatoj316 on 2008-07-22
Thank you, it was very helpful

---

### Post by andrewxyz on 2008-07-22
btw guys, how about running php file with cron??..any ideas???

---

### Post by chenel on 2008-07-23
> **andrewxyz said:**
> btw guys, how about running php file with cron??..any ideas???

You can run PHP from the command line if you want.  Install "php5-cli" using synaptic, then you can run scripts using (I think)
```
php5 [name-of-script.php]
```

in your cron.

Most people usually prefer to write system scripts in Perl or Python (or even Bash) though...

---

### Post by kahrytan on 2008-08-12
For those interested in setting up cron tab events, you don't have to use command line to do it. 

Just use Gnome-Schedule. 

```
sudo apt-get install gnome-schedule
``` or via APTURL: [Gnome-Schedule]("apt:gnome-schedule")

 Notice: Above link uses apturl to install gnome-schedule using official repositories.


Gnome-Schedule still needs to use ```
export DISPLAY=:0 && 
``` to run GUI apps.

---

### Post by DataMatrix on 2008-08-13
This is a very nice how-to with lots of nice and useful comments. I have some dificulties with the weird syntax with executing a script every one minutes and not every first minute of the hour, but I'm getting the hang of it.

---

### Post by markofealing on 2008-08-15
Excellent tutorial, solved my problems trying to schedule Transmission.

BTW having used the GUI scheduler, I don't really see the point. Crontab is simple and very flexible.

Thank you

---

### Post by Dragon Smaug on 2008-08-20
> **two_beers said:**
> ```
30 0 * * * netstat -lnp > netstat_`date +%b%d`.txt
```

This should solve your problem...

I tried to do your date syntax (though the rests of the command is different) for writing to a file, however it did not work.

I tried to do it with a mysqldump, and I am getting this error: "EOF in backquote substitution".  Any ideas?

---

### Post by chenel on 2008-08-21
> **Dragon Smaug said:**
> I am getting this error: "EOF in backquote substitution".

Usually that means that you have a syntax error in the part of your command that's between the backquotes (the ` characters).  What does your cron line look like?

---

### Post by Dragon Smaug on 2008-08-21
> **chenel said:**
> Usually that means that you have a syntax error in the part of your command that's between the backquotes (the ` characters).  What does your cron line look like?

Here:

```
33 14 * * * mysqldump --user=user --password=password > /path/to/backup/dbbackup_`date +%b%d`.sql
```

I tried first using a longer combination of the date operands (the little percent sign-letter combinations), and when that did not work I shortened it to two_beers' exact example, but it still fails.

Thanks for taking a look at it.

---

### Post by chenel on 2008-08-21
Ha!  You're going to kick yourself.

So I tried out your command verbatim (changing only what I had to to get it to run), and it worked fine.

Then it occurred to me: what if the mysql login info is wrong?

So I substituted a wrong password for one of my mysql users, and ... BAM.  Mail from CRON: "EOF in backquote substitution".

So, check your username and password.  Make sure you can log in with them into the interactive mysql shell ('mysql -u user -p').

Hope this fixes your problem :)

---

### Post by Dragon Smaug on 2008-08-21
Yeah, I am able to log in as the user.  Also, I just realized the cron line is a little different than what I wrote. It is:

```
33 14 * * * mysqldump --user=user --password=password databasename > /path/to/backup/dbbackup_`date +%b%d`.sql
```

When copying to here before I had left out the database name.

Anyway, when I try to log in to mysql from the command line, it works.  When I run the above command (the same thing but without the cron time signifiers) from the command line it works.  But from cron, I get the error. :(  I'm using the mysql root user, I don't know if that could mean anything.

---

### Post by chenel on 2008-08-21
Try escaping the percent signs with backslashes:

```
 ... /path/to/backup/dbbackup_`date +\%b\%d`.sql 
```

They are special characters and I think maybe sh is breaking on them.

---

### Post by Spiny Norman on 2008-08-21
I have been using gawk to help name compressed versions of my testing server Harry's MySQL dump file called imaginatively enough "SqlDump.sql" The shell script looks like this:

# Small script to compress the dump file and add DOW 
tar -cvpzf Harry`date |gawk '{print$1}'`Bk.tar.tgz SqlDump.sql
echo now its all squished up

The output is HarrySunBk.tar.tgz

This gives a rolling 7 days available on my test server for rolling back. I also use gawk (on my backup server)to rename files I pull daily to the backup server. On my testing server I run the same script but without the gawk part to generate the target for this pull. 

You may insert $1$2$3$4$5 or parts therof to get the desired date parts you want.

You will need to install gawk using #apt-get install gawk
I hope this is of some use

---

### Post by Dragon Smaug on 2008-08-21
> **chenel said:**
> Try escaping the percent signs with backslashes:

```
 ... /path/to/backup/dbbackup_`date +\%b\%d`.sql 
```

They are special characters and I think maybe sh is breaking on them.

Thank You! You must be right about them being special characters (perhaps signifying EOF). Your suggestion worked!

---

### Post by Omega2Four on 2008-10-03
I am trying to set up cron to run a script. I thought I had done everything right but the script didnt autorun...soooo...I tried this as a benchmark..just for cron to launch pidgin every minute...well..it doesnt launch pidgin either...what am I doing wrong?

gempak@xxxxxxx:/data/ldm/gempak/tasksched$ crontab -l
* * * * * pidgin

---

### Post by chenel on 2008-10-03
> **Omega2Four said:**
> I am trying to set up cron to run a script. I thought I had done everything right but the script didnt autorun...soooo...I tried this as a benchmark..just for cron to launch pidgin every minute...well..it doesnt launch pidgin either...what am I doing wrong?

gempak@xxxxxxx:/data/ldm/gempak/tasksched$ crontab -l
* * * * * pidgin

Probably it's the same issue as one that people were having earlier in the thread: you need to put the FULL path of any program you want to run.  On my machine, anyway, pidgin lives in /usr/bin/ (you can find out where it lives by doing 'which pidgin' at a terminal), so the line you want would be 
```
* * * * * /usr/bin/pidgin
```

Hope this helps.

---

### Post by Iturbide on 2008-10-09
Disregard below. I hadn't scrolled to page 9 of the thread yet. Nevermind.

Hi,

I just ran into this and found this thread googling for the answer.
Looks like this will be your solution, but I haven't tried it myself yet:

[http://www.mail-archive.com/freebsd-questions@freebsd.org/msg22297.html](http://www.mail-archive.com/freebsd-questions@freebsd.org/msg22297.html)

Summing it up:
Crontab treats '%' characters specially --- see crontab(5).  It will
automatically replace a '%' character with a newline, as a method of
being able to include multiline shell input into the crontab file.

To get a literal '%', type '\%'

Good luck!

René

---

### Post by IanHobson on 2008-10-12
For those new to Ubuntu, like me... if you find that "crontab -e" give you a missing command error, then you need to install the package cron

   sudo apt-get install cron

---

### Post by smite_of_bloodstone on 2008-10-29
In the hopes that this will save someone the time I just wasted, also be very sure that your crontab line is ended with a carriage return.  If you don't your command will not run, you may not get any error message, and frowning may ensue.

correct:
* * * * * /usr/bin/touch /tmp/this.file
<EOF>

incorrect:
* * * * * /usr/bin/touch /tmp/this.file<EOF>

---

### Post by WARnux on 2008-10-29
"frowning may ensue"

I know the feeling.

About your post:

Carriage Return (13) is Mac.  Line Feed (10) is Unix/Linux.
I always just say Line Break or New Line when referring to creating a line - that avoids confusion.

---

### Post by kevdog on 2008-10-30
Just wondering if you could add instructions on how to modify the system wide crontab file.  This capability may want to be added -- for example to periodically update the dyndns address, or something similar.

That would be great, since the process is slightly different than the user crontab procedure.

---

### Post by Rodney9 on 2008-11-06
Hello,

I found this code in the Community Cafe, it works even went music is playing, just what I need.

However I have tried adding

echo "Its" `date "+%l oclock"` | aoss festival --tts

to Gnome-Schedule, but it will not allow the percentage symbol %

How else can I run it every half hour, or is there some workaround with the % symbol ? If I use backslash it actually says "backslash"

Rodney.

---

### Post by chenel on 2008-11-06
> **Rodney9 said:**
> Hello,

```
echo "Its" `date "+%l oclock"` | aoss festival --tts
```

Rodney.

My guess is that there's a problem with the quotation marks.  Try

```
echo "Its `date +\%l` oclock" | aoss festival --tts
```

instead -- your version passes 'oclock' as part of the command line for the date command (anything between the ``s will be in the command line), and date doesn't know anything about 'oclock' :)

---

### Post by Rodney9 on 2008-11-07
> **chenel said:**
> My guess is that there's a problem with the quotation marks.  Try

```
echo "Its `date +\%l` oclock" | aoss festival --tts
```

instead -- your version passes 'oclock' as part of the command line for the date command (anything between the ``s will be in the command line), and date doesn't know anything about 'oclock' :)

Thank You, that solved my problem.

---

### Post by Rodney9 on 2008-11-07
> **Rodney9 said:**
> Thank You, that solved my problem.

But now I can not get Gnome Schedule / Cron to run.

I run sudo gnome-schedule, set recurrently task for 00,30 , add command  " echo "Its `date +\%l\%M\%P` oclock" | aoss festival --tts " say apply, ok.

I test execute it, and it runs perfectly in the test.

But does not each run each half hour in real time, nothing happens.

What am I doing wrong ?

---

### Post by Rodney9 on 2008-11-07
> **Rodney9 said:**
> But now I can not get Gnome Schedule / Cron to run.

I run sudo gnome-schedule, set recurrently task for 00,30 , add command  " echo "Its `date +\%l\%M\%P` oclock" | aoss festival --tts " say apply, ok.

I test execute it, and it runs perfectly in the test.

But does not each run each half hour in real time, nothing happens.

What am I doing wrong ?

**Solved** - Actually I did not have to use sudo, only gnome schedule from applications/system tools/scheduled tasks.

---

### Post by jake3988 on 2008-11-13
Thanks for the howto, very good.

However, my cron job still won't launch.

Here's the job in crontab: 
04 18   * * 4   export display=:0 && xmessage hi

Here's what it says in syslog:
Nov 13 18:04:01 jake3988-desktop /USR/SBIN/CRON[19237]: (jake3988) CMD (export display=:0 && xmessage hi)

But it does work.  I want to have scheduled reminders pop up using xmessage to remind me when my favorite shows are on (I ALWAYS forget)... but for some reason the command isn't being launched.
(For instance, I'd like to have 50 19 * * 2 export display=:0 && xmessage House,M.D. will be on in 10 minutes.)

I tried launching rhythmbox or any other application and they wouldn't work either.

What could be the problem?  Thanks for any help!!

---

### Post by chenel on 2008-11-13
> **jake3988 said:**
> Thanks for the howto, very good.

However, my cron job still won't launch.

Here's the job in crontab: 
04 18   * * 4   export display=:0 && xmessage hi

Here's what it says in syslog:
Nov 13 18:04:01 jake3988-desktop /USR/SBIN/CRON[19237]: (jake3988) CMD (export display=:0 && xmessage hi)

But it does work.  I want to have scheduled reminders pop up using xmessage to remind me when my favorite shows are on (I ALWAYS forget)... but for some reason the command isn't being launched.
(For instance, I'd like to have 50 19 * * 2 export display=:0 && xmessage House,M.D. will be on in 10 minutes.)

I tried launching rhythmbox or any other application and they wouldn't work either.

What could be the problem?  Thanks for any help!!

See [post #85]("http://ubuntuforums.org/showpost.php?p=5266633&postcount=85") in this thread :)

---

### Post by jake3988 on 2008-11-13
If you mean using the full pathname, no that doesn't either.  Tried it.

---

### Post by chenel on 2008-11-13
> **jake3988 said:**
> If you mean using the full pathname, no that doesn't either.  Tried it.

Oh, you might also want to write 'DISPLAY', not 'display'.  Environment variables are case-sensitive.

---

### Post by jake3988 on 2008-11-13
Still no :)

Thanks though...  Trust me, I've tried every combination of everything in the book.

---

### Post by chenel on 2008-11-13
> **jake3988 said:**
> Still no :)

Thanks though...  Trust me, I've tried every combination of everything in the book.

Really?  I tested it and the command worked for me with the full path and display in uppercase...  Here's the exact command I ran:

```
* * * * * export DISPLAY=:0 && /usr/bin/xmessage hi 
```

---

### Post by jake3988 on 2008-11-13
Doing it straight from command-line works fine and it displays in syslog that it fired just fine.

But it just simply doesn't work from cron.  In fact trying to launch anything (like conky for instance) just plain doesn't work.

Thanks for your help though.

---

### Post by jake3988 on 2008-11-15
I also tried putting the command in an external file and launching that, and that didn't work.

I tried calling the external file using sh (inside cron) and that didn't work.

I even tried launching a command using the 'at' command (completely outside of cron) and even THAT didn't work.

What the heck am I doing wrong that my computer won't let me do absolutely anything dealing with time?

Edit:  I was also told to grep the 'env' command for command, and it turned out to be :0.0, so I tried that and that doesn't work.

---

### Post by ScarySquirrel on 2008-11-22
I thank the creator of this post for their specific, succinct, accurate, and lucid explanation of a Linux feature which has entailed a great difficulty for me.
After reading this post, I finally used this command rightly.

---

### Post by chenel on 2008-11-22
> **jake3988 said:**
> I also tried putting the command in an external file and launching that, and that didn't work.

I tried calling the external file using sh (inside cron) and that didn't work.

I even tried launching a command using the 'at' command (completely outside of cron) and even THAT didn't work.

What the heck am I doing wrong that my computer won't let me do absolutely anything dealing with time?

Edit:  I was also told to grep the 'env' command for command, and it turned out to be :0.0, so I tried that and that doesn't work.

Have you tried running something non-graphical, to see if maybe that's where the hangup is?  Something like

```
* * * * * /usr/bin/touch /home/[your user]/crontest
```

Then you should have a file 'crontest' in your home directory with a modification date of when cron ran...

If this works, then you'll at least have narrowed it down to something having to do with your graphical system.

---

### Post by solitaire on 2008-11-23
I've an issue with the failure messages cron sends out.

They should be going to root@laptop but they end up in: ```
 /var/mail/nobody
``` instead of root's mailbox.

I've a few cron errors going to ```
/var/mail/<my username>
``` and those are ok. Well i can deal with them using alpine.

where do i change the email so it sends it to my username or root instead of going to nobody? (which i assume is due to the fact that root is dissabled as a logon user).

---

### Post by chenel on 2008-11-24
> **solitaire said:**
> I've an issue with the failure messages cron sends out.

They should be going to root@laptop but they end up in: ```
 /var/mail/nobody
``` instead of root's mailbox.

I've a few cron errors going to ```
/var/mail/<my username>
``` and those are ok. Well i can deal with them using alpine.

where do i change the email so it sends it to my username or root instead of going to nobody? (which i assume is due to the fact that root is dissabled as a logon user).

So you are using the root crontab ('sudo crontab -e') for the cron errors you want to redirect?  If so, you should be able to redirect them to another e-mail address by appending 
```
MAILTO=user@domain
```
to the crontab.

---

### Post by yknivag on 2008-11-25
Thanks for such a brilliant how-to.

Maybe this is a silly question, but I'd be very grateful if one of the many gurus on this forum could confirm this for me...

As I understand it:

```
0 * * * * * command > /dev/null 2>&1 #Comment
```

should send STDOUT and STDERR to null and thus supress all emails. Whereas:

```
0 * * * * * command > /dev/null #Comment
```

should send only STDOUT to /dev/null.  Would STDERR still go to an email in this case?  And would I, therefore, get an email if the job failed?

---

### Post by chenel on 2008-11-25
> **yknivag said:**
> 

```
0 * * * * * command > /dev/null #Comment
```

should send only STDOUT to /dev/null.  Would STDERR still go to an email in this case?  And would I, therefore, get an email if the job failed?

I believe that you're essentially correct, but CRON doesn't produce output that goes to STDERR (or STDOUT, for that matter).  Instead, I think you'd only get an e-mail if 'command' produces some output that is sent to STDERR.

---

### Post by alj on 2008-11-27
I can't get crontab to work under su.

I've setup a script to run under my normal login and it works ok. However, when I change to root and use exactly the same cron parameters, it doesn't trigger. 

the cron I use in both instances is:

35 23 * * * python /home/myname/test.py

The test.py file creates a txt doc with the current date and time. I've tried moving the test.py file out into the /tmp/ directory but that doesn't make any difference. I've changed the permissions on the file for all to read and write. 

Am I just stupid? :confused:

---

### Post by unutbu on 2008-11-27
alj, please post your test.py, and indicate if you are running
```

sudo crontab -e
```
or editing /etc/crontab.

---

### Post by alj on 2008-11-28
Hi,

The test.py is:

import time
mystring = "The crontab ran at " + str(time.strftime("%a, %d %b %Y %H:%M:%S +0000", time.localtime())
)
f = open('test.txt','w')
f.write(mystring)
f.close()
print "done"

I was using:
sudo crontab -e

It looks like the cron gets installed ok as I can see it when I "crontab -l".

ALJ

---

### Post by unutbu on 2008-11-28
alj, I tried your script. It worked for me.
test.txt is written to /root/test.txt.

Here is what shows up in /var/log/syslog :
```

Nov 28 07:32:01 localhost /usr/sbin/cron[5822]: (root) RELOAD (crontabs/root)
Nov 28 07:32:01 localhost /USR/SBIN/CRON[6415]: (root) CMD (python /home/unutbu/pybin/test.py)
Nov 28 07:33:01 localhost /USR/SBIN/CRON[6450]: (root) CMD (python /home/unutbu/pybin/test.py)

```

(For debugging, I changed the crontab line to
```
* * * * * python /home/unutbu/pybin/test.py
```
so it would run once every minute.)

Perhaps check your /var/log/syslog to see if the script is being run. It might give a useful error message as well.

---

### Post by alj on 2008-11-28
Hi .... I've just looked in my /root/ and ... erm ... I found the test.txt file. I just assumed (reasonably?) that it would be written relative to the originating python script.

Thanks for your help.

---

### Post by alj on 2008-11-28
... so how would you get it to write to the correct place without editing the python script?

---

### Post by unutbu on 2008-11-28
This works:
```

35 23 * * * cd /home/myname && python /home/myname/test.py

```

---

### Post by alj on 2008-11-30
Hi ...again!

There's something obviously going wrong with my python scripts. They go off and collect info off the web. I've run them from the terminal and they work ok. However, when they are run through the cron they run to a certain extent and then bail out. I use Python logging so I can see the python logfile and how far the app gets to, and the data that it produces. But that's it. There's nothing in the logs that give me any clues. I've checked the var/logs/syslog but all I can see is that the cron was run. 

Is there anyway to get the console to open when the python scripts are run through the crontab so I can see any other error messages?

[ggggghhhhhaaaaaaahhhhhH!!!!!!!!]

---

### Post by unutbu on 2008-11-30
Hi alj. Since cron is running the script, it's doing its job as far as it's concerned. 

At this point a common problem is that environment variables (like HOME or PATH or CWD) are not what you expect. If your script writes or reads from files, maybe try making all the paths explicit. 

You mentioned the logging module. Can you sprinkle
logging.debug messages throughout your script to find out exactly where the script is dying? What line is it dying on? That's often a big clue.

If using the logging module is not working as expected, here is a very low-brow but effective method to get feedback from your script:
 [PHP]
fh=open('/tmp/script.out','a')
fh.write('Got here!')
fh.close()[/PHP]


When you have a script that doesn't work, try to create a stripped-down version of it that still exhibits the problem. The simpler the script, the easier it will be to find the problem.

Finally, imaging running your script as an unprivileged user from a foreign directory. Even if this is not the case in reality, it might put you in the right frame of mind to catch what's going wrong.

For more concrete suggestions, you'll have to post your script or preferably, the stripped-down version.

---

### Post by alj on 2008-12-03
I've managed to get it working after quite a lot of work. There appears to be a problem when using dual logging on python with crontab. 

I opened up a discussion on the python forums and there was also some additional advice for people trying to debug scripts going through the console. It is possible to hook into the console, for example.

Running a Python script from crontab 
[http://groups.google.co.uk/group/comp.lang.python/browse_thread/thread/4d4afda860f17967/e11e63b5d58054f0?hl=en](http://groups.google.co.uk/group/comp.lang.python/browse_thread/thread/4d4afda860f17967/e11e63b5d58054f0?hl=en)

Thanks for the help

---

### Post by CarlosinFL on 2008-12-03
I am looking to run a cron job every 5 minutes of every day. How does this look like in crontab?

*5 * * * * /usr/bin/rsync ....

???

---

### Post by chenel on 2008-12-03
> **Carlwill said:**
> I am looking to run a cron job every 5 minutes of every day. How does this look like in crontab?

*5 * * * * /usr/bin/rsync ....

???

Close.  You want

```
5 * * * * /usr/bin/rsync
```

(i.e., 5th minute of every hour of every day of every month.....)

---

### Post by unutbu on 2008-12-03
```
*/5 * * * * /usr/bin/rsync ...
```
This crontab line will run the rsync command every 5 minutes (e.g 9:00, 9:05, 9:10, ... etc)

---

### Post by chenel on 2008-12-03
> **unutbu said:**
> ```
*/5 * * * * /usr/bin/rsync ...
```
This crontab line will run the rsync command every 5 minutes (e.g 9:00, 9:05, 9:10, ... etc)

Whoops, you're right.

---

### Post by CarlosinFL on 2008-12-04
Awesome - that is what I wanted!

I need the job to run ever 5 minutes of the day!

---

### Post by danielmorris on 2008-12-21
> **Gandalf said:**
> 
```

EDITOR=vi && crontab -e

```


I think this should be...

```
EDITOR=vi crontab -e
```

:)

---

### Post by deadjones on 2008-12-25
i did ..

01 00,06,12,16,18,20 * * * php /home/user/somewhere/file.php

at 1 minute after midnight, 6am, 12pm, 4pm, 6pm and 8pm, crontab will run the php command.  


i got this right?

---

### Post by chenel on 2008-12-25
> **deadjones said:**
> i did ..

01 00,06,12,16,18,20 * * * php /home/user/somewhere/file.php

at 1 minute after midnight, 6am, 12pm, 4pm, 6pm and 8pm, crontab will run the php command.  


i got this right?

Looks like it.

---

### Post by johann_p on 2009-02-17
Oddly, since I upgraded to 8.10 the script I used to automatically change my wallpaper stopped to work. 
Is there any reason why a command like 
  gconftool-2 -t str --set /desktop/gnome/background/picture_filename filename.jpg
did work in the previous version and not anymore?
If a run this script from the command-line it does work like a charm.

---

### Post by unutbu on 2009-02-17
Try using these two commands in conjunction:
```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename /path/to/image.jpg
gconftool-2 -t string -s /desktop/gnome/background/picture_options scaled

```

---

### Post by johann_p on 2009-02-17
> **unutbu said:**
> Try using these two commands in conjunction:
```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename /path/to/image.jpg
gconftool-2 -t string -s /desktop/gnome/background/picture_options scaled

```

That is actually what I am doing (except that I use "zoom" instead of "scaled")  and it is all part of a longer script that determines the image file etc.
As I said, the script works fine when invoked from the command line interactively, it worked fine with ubuntu 8.04 when running from my user's crontab and it does not work any more in 8.10 when running from my user's crontab. 
I have tried to debug this by putting "echo" commands that write to a log file into the script and all the commands do get executed, running the script itself in the crontab does not produce any error messages either (no emails, and no output when I redirect both stderr and stdout to a file)

This is odd.

---

### Post by scoon on 2009-02-17
> **johann_p said:**
> That is actually what I am doing (except that I use "zoom" instead of "scaled")  and it is all part of a longer script that determines the image file etc.
As I said, the script works fine when invoked from the command line interactively, it worked fine with ubuntu 8.04 when running from my user's crontab and it does not work any more in 8.10 when running from my user's crontab. 
I have tried to debug this by putting "echo" commands that write to a log file into the script and all the commands do get executed, running the script itself in the crontab does not produce any error messages either (no emails, and no output when I redirect both stderr and stdout to a file)

This is odd.

Hey there, 

I am having the same problem with xfce.  I have written a Perl that dynamically changes my desktop.  When I run it alone, the script works.  When I try and run it in cron, it runs but no desky changes.  It is quite odd. 

Thanks.

---

### Post by unutbu on 2009-02-17
See [https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/285937](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/285937)
There appears to be a solution there -- you need to source a file in /home/$USER/.dbus/session-bus/ so DBUS_SESSION_BUS_ADDRESS is defined.

---

### Post by scoon on 2009-02-18
> **unutbu said:**
> See [https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/285937](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/285937)
There appears to be a solution there -- you need to source a file in /home/$USER/.dbus/session-bus/ so DBUS_SESSION_BUS_ADDRESS is defined.

Hey there, 

I wonder if maybe this bug is more of my problem: [https://bugs.launchpad.net/ubuntu/+source/cron/+bug/327190]("https://bugs.launchpad.net/ubuntu/+source/cron/+bug/327190").  Is anyone here running xubuntu and using a hand rolled script with cron to update their desktop wallpapers?

thanks.

---

### Post by tacomodo on 2009-03-22
I am sort of trying to understand how crontab works and wonder if anyone can help me.

If I put an entry in with crontab -e that will run a simple "echo blabla" every minute, where will this echo to?

---

### Post by unutbu on 2009-03-22
In general, unless you set up crontab differently, the output will go nowhere. You simply won't see anything.

If you put 
```

MAILTO=tacomodo

```
(substitute your username for tacomodo) at the top of your crontab file, and if your system has a mail transfer agent (like exim4) installed, then you will get mail with the output of each cron job.

I believe Intrepid comes with exim4 installed by default, so on Intrepid, all you should need to do is put the MAILTO line in your crontab. 

In contrast, on Gutsy, there is no mail transfer agent installed by default, so even with the MAILTO line, you don't receive any output in your mail. Of course, you can install exim4, and then I believe you would receive the output in your mail...

If you don't want to fuss with mail, you could also edit your cron job command to be
```

echo blabla >> ~/cron.out
```

And then the output would be appended to ~/cron.out.

---

### Post by tacomodo on 2009-03-22
Thanks for the reply.

So only "MAILTO=tacomodo" at the top of the crontab file, all by itself, and cron understands how to mail it and such? Pretty cool if so.

---

### Post by unutbu on 2009-03-22
Yes indeed, I believe that is true.
Though I have been known to be wrong before... :)

---

### Post by statmonkey on 2009-03-23
Every other once in a while I stumble over an absolutely fantastic thread that reminds me how outstanding the Ubuntu Community is.  This thread is certainly one of them.  Great tutorial and some very helpful posts.  Just wanted to say thanks to everyone who contributed to this thread.

---

### Post by chenel on 2009-03-23
> **tacomodo said:**
> So only "MAILTO=tacomodo" at the top of the crontab file, all by itself, and cron understands how to mail it and such? Pretty cool if so.

Just so long as you don't mean "send mail through the internet."  It'll put mail in the queue for the 'tacomodo' user on your local machine, which you'll have to read locally on the machine (you can use exim as noted by unutbu, or alpine [my personal favorite], or something to that effect).  If you want to install a mail *server* (postfix, for example), you can send mail to any internet e-mail address and read the mail in the local machine queue from anywhere.  But that takes more work :)

---

### Post by davidstri on 2009-04-14
It's not working for me... I opened a terminal, typed crontab -e and added the following line to make a program run at 6:05 pm : 05 18 * * * /usr/bin/anki . But for some reason it did not open anki. Am I doing something wrong?

---

### Post by unutbu on 2009-04-14
Perhaps try this:
Edit your crontab to include
```
DISPLAY=:0
```
at the top of the file.

This may or may not work, but if it does, here is the explanation:
cron runs commands in a stripped-down environment that doesn't include DISPLAY. Programs with GUIs often read DISPLAY to determine where to place its graphics.

---

### Post by jaketrunk on 2009-06-09
I must be doing something wrong.  I've written a script to back up my system:


#!/bin/bash

tar cvpzf /var/lib/mythtv/videos/Backup/mythdown_backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/var/lib/mythtv/videos --exclude=/var/lib/mythtv/recordings /


And placed the script named backup in the /sbin directory.  When I type (from the /sbin directory): 

sudo backup 

everything works great.

I've tried editing the crontab by typing:

sudo crontab -e 

and then adding my script (30 19 * * * /sbin/backup).

The problem is the script will run, but will only backup a small portion of my system.

What am I doing wrong?  Why does the script work from the command line, but not from cron?

Any help will be greatly appreciated.

---

### Post by Gourgi on 2009-06-10
> **jaketrunk said:**
> I must be doing something wrong.  I've written a script to back up my system:


#!/bin/bash

tar cvpzf /var/lib/mythtv/videos/Backup/mythdown_backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/var/lib/mythtv/videos --exclude=/var/lib/mythtv/recordings /


And placed the script named backup in the /sbin directory.  When I type (from the /sbin directory): 

sudo backup 

everything works great.

I've tried editing the crontab by typing:

sudo crontab -e 

and then adding my script (30 19 * * * /sbin/backup).

The problem is the script will run, but will only backup a small portion of my system.

What am I doing wrong?  Why does the script work from the command line, but not from cron?

Any help will be greatly appreciated.
try using #!/bin/sh

---

### Post by jaketrunk on 2009-06-10
please see below

---

### Post by jaketrunk on 2009-06-10
> **Gourgi said:**
> try using #!/bin/sh

I made the changes, but still the same result.  When run from the command line with sudo the script produces a full backup (~800 megs).  When run from crontab, the file is only about 11 megs.  Is there a way I can see what is causing the backup to end prematurely?

---

### Post by unutbu on 2009-06-10
Perhaps try changing
```

30 19 * * * /sbin/backup
```

to
```

* * * * * /sbin/backup 1>/tmp/backup.out 2>&1 
```

Then wait a minute (for the cronjob to run) and then look in /tmp/backup.out.
It should contain all the output from stdout and stderr.
Look for any errors. That may give us a clue.

I think I recall one thread where the mere fact that stdout and stderr was directed somewhere was enough to make the cronjob succeed (whereas before it kept bailing out early). I haven't been able to reproduce this problem on my machine, but maybe you will find this true for you too.

---

### Post by jaketrunk on 2009-06-10
> **unutbu said:**
> Perhaps try changing
```

30 19 * * * /sbin/backup
```

to
```

* * * * * /sbin/backup 1>/tmp/backup.out 2>&1 
```

Then wait a minute (for the cronjob to run) and then look in /tmp/backup.out.
It should contain all the output from stdout and stderr.
Look for any errors. That may give us a clue.

I think I recall one thread where the mere fact that stdout and stderr was directed somewhere was enough to make the cronjob succeed (whereas before it kept bailing out early). I haven't been able to reproduce this problem on my machine, but maybe you will find this true for you too.

That did it!  The script ran perfectly.  Thank you so much for your help!  Can you tell me in noob terms what "1>/tmp/backup.out 2>&1" does?

Thanks again!!:D

---

### Post by unutbu on 2009-06-10
Wonderful. I'm glad it worked for you jaketrunk.

Usually when you run a program from the terminal, the program has a notion of "stdout" and "stderr". When a program prints something to stdout, you see it on the screen. 
stderr is similar to stdout except it is used for the program's error messages. Usually it is also printed in the terminal's window. Both stdout and stderr can be redirected to a single file, or to different files, or to /dev/null (a special file, where everthing sent there gets ignored.)

In contrast to programs run in the terminal, when you run cronjobs, stdout and stderr are not directed anywhere by default. (If you set up a mail transfer agent, however, you can get each cronjob's stdout and stderr to be sent to your mailbox...)

"1>/tmp/backup.out" tells /sbin/backup to send stdout to /tmp/backup.out. 
"2>&1" tells /sbin/backup to send stderr to wherever stdout is pointed to.

The numbers 1 and 2 are file descriptors. By convention, file descriptor 1 is stdout, and file descriptor 2 is stderr.

---

### Post by jaketrunk on 2009-06-10
Unutbu, that makes sense.  Thank you for the valuable info.  I will keep in mind as a work on additional scripts.

---

### Post by renaldy on 2009-06-11
hello guys im having problem with my crontab, im still a newbie in this, i tried created a crontab that will make my com restart (just to learn how to use it,lol) and this is the line i wrote:

00 12 * * * /sbin/shutdown -r

however,it does not seem to work, i create this crontab in root account so i dont think it has got to do with privilege problem, someone please help me on this :D

---

### Post by unutbu on 2009-06-11
renaldy, try running
```

sudo /sbin/shutdown -r
```

in a terminal. You'll find that it gives this error:
```

shutdown: time expected
Try `shutdown --help' for more information.
```

If you want the machine to reboot immediately, try 
```

sudo /sbin/shutdown -r now
```

---

### Post by renaldy on 2009-06-11
> **unutbu said:**
> renaldy, try running
```

sudo /sbin/shutdown -r
```
 
in a terminal. You'll find that it gives this error:
```

shutdown: time expected
Try `shutdown --help' for more information.
```
 
If you want the machine to reboot immediately, try 
```

sudo /sbin/shutdown -r now
```
 
i see..thanks,thats a great help! anyway, if my crontab is installed in root user, must i use sudo to let the command run on root privilege? :D

---

### Post by unutbu on 2009-06-11
You are correct -- when you use root's crontab, you do not need sudo:
```

00 12 * * * /sbin/shutdown -r now
```

---

### Post by renaldy on 2009-06-11
alright,thank you :D

---

### Post by canabal on 2009-06-25
Hey guys,

Is there a way to schedule a program for a certain amount of time and then shutdown at the end?

Basically, I want to have a slideshow start with feh, so my command is "0 0 * * * feh -r -z -D 5 -F -Z --hide-pointer /home/username/Pictures" those -Z etc are just to get the slideshow how I want... i.e. fullscreen.

When I run this command in shell it starts fine, but with cron it does not.

I want it to run for a time because at a certain time (8:00) I want it to shutdown and run firefox for an hour on the weather channel.  Then at 9 to shut firefox and start the slideshow again.

I am making a digital picture frame that shows the weather for an hour before I go to work basically.

---

### Post by chenel on 2009-06-25
> **canabal said:**
> Hey guys,

Is there a way to schedule a program for a certain amount of time and then shutdown at the end?


It's ugly, but you could always schedule a
```
 killall feh 
```
for an hour later.  This should shut it down cleanly since kill only gives the TERM signal (which the program is allowed to handle as it sees fit) by default.

> 
When I run this command in shell it starts fine, but with cron it does not.

You probably need to use the full path to feh: do
```
which feh
```
and make sure you include the whole path that you get back in the cron script.  If that doesn't do it (and I suspect it won't), check [earlier in the thread]("http://ubuntuforums.org/showpost.php?p=6172910&postcount=101") for advice on how to set the display.  (None of the environment variables that are automatically set when you open a shell are set for the cron job -- you need to set them by hand.)

-chenel

---

### Post by canabal on 2009-06-25
Thanks, I will look into that in the morning.

I am using the gnome-schedule gui to do the crontab (I am still a rookie at it, but will likely switch to cmd line stuff for this now that I found this thread), could that be making a difference in this?

---

### Post by chenel on 2009-06-26
> **canabal said:**
> I am using the gnome-schedule gui to do the crontab (I am still a rookie at it, but will likely switch to cmd line stuff for this now that I found this thread), could that be making a difference in this?

That I don't know -- I've always just used the 'crontab' utility from the command line.  (Everybody else is welcome to comment if they know better!)  Judging from the cron line you quoted before, though, it looks fine.  And after all, I bet that it's designed to produce the same cron files. :)

You could always check by setting things with gnome-schedule, then checking on the cron file via the command line (crontab -l) and comparing...

My gut feeling is that it's probably the other two things I mentioned before.  Those are very common mistakes that people tend to make when they're new to cron, and they produce exactly the symptoms you described (works from shell, not from cron).

---

### Post by canabal on 2009-06-26
I got it working, thanks.

The directing it to the actual directory did not help, but the export DISPLAY=:0 did.

I am going to try to make a tutorial for the software side of the setup of my digital picture frame and post it up in the next little while.

---

### Post by asadqamber on 2009-07-02
My cron deamon is running, I checked it with 

ps aux |grep cron

but no command is being executed, even  when the crontab had:

* * * * * echo "Print this every minute"

any idea?

---

### Post by chenel on 2009-07-02
> **asadqamber said:**
>  even  when the crontab had:

* * * * * echo "Print this every minute"


You'd need to redirect the output from 'echo' to a file if you want to see anything -- echo doesn't run in a particular terminal so you'd never see it otherwise.  Try something like

```
 * * * * * /bin/date >> /home/[your user]/test.out 
```

That should append the current date and time to test.out in your home directory every minute.  Let us know if that produces any results

---

### Post by asadqamber on 2009-07-03
Now its working. cheers!

Thanks for the help.

---

### Post by chenel on 2009-07-03
> **asadqamber said:**
> Now its working. cheers!

Thanks for the help.

Glad you got things to work.

---

### Post by ducksun43 on 2009-07-07
this one is pretty good too [http://sunoano.name/ws/public_xhtml/time.html#cron](http://sunoano.name/ws/public_xhtml/time.html#cron)

---

### Post by Martin H. on 2009-07-13
Hi all !
 
 
Im currently having problems with the cron - execution of a script i wrote that needs root - privileges. The root - account on my machine is deactivated so i won't be able to switch to root - user. 
 
I have done the following : 
 
original script : test.sh
wrapper script : test2.sh ( just calls test.sh via "sudo completePathToScript/test.sh" ) 
 
And i edited the crontab with "sudo crontab -e" to add the following line :
 
/5 * * * * completePathToScript/test2.sh
 
The script test.sh seems to run, but cannot fullfill the parts where 'root' is requirred... 
Is there a better way to achieve the goal (execute script with root rights via cron) ?
 
I have read through this thread, but nothing seems to apply to my problem. 
Any help would be greatly appreciated!
 
Thx in advance,
M.

---

### Post by unutbu on 2009-07-13
When you run "sudo crontab -e" you are editing root's personal crontab.
So all cron jobs run that way will already have root privileges.

So there is no need for root to run test2.sh. Rather, it should be able to run test.sh.

How about try

```

sudo crontab -e

*/5 * * * * completePathToScript/test.sh
```

Note that the crontab entry needs "*/5" at the beginning not "/5" if you want the job to run every 5 minutes.

---

### Post by Martin H. on 2009-07-13
Thx alot,
 
 
the missing * was a typo - but your advice works perfectly ! 
No need to "sudo - around" here :)!
 
Thanks for your help,
M.

---

### Post by spynappels on 2009-07-14
Finally, I've got the CRON thing working. I'm using it to run a script from a Online Backup Manager to do an incremental backup of a server every evening and finally I'm not getting Backup Failed emails from the backup providers anymore. Their own scheduler did not work, but running a manual backup through CRON has solved the problem.

Thanks for all the help.

---

### Post by scripterworld on 2009-07-27
[SIZE=2]nice post[/SIZE]
[SIZE=2]some more information about crontab[/SIZE]
[SIZE=2][http://scripterworld.blogspot.com/2009/07/unix-crontab-configuration-with.html](http://scripterworld.blogspot.com/2009/07/unix-crontab-configuration-with.html)[/SIZE]

---

### Post by MarkX on 2009-10-07
Has it crossed anyone's mind that putting cron into a GUI would save everyone a lot of work and any idiot might be able to use it in seconds?

---

### Post by Gourgi on 2009-10-07
> **MarkX said:**
> Has it crossed anyone's mind that putting cron into a GUI would save everyone a lot of work and any idiot might be able to use it in seconds?

```
sudo apt-get install gnome-schedule
```
maybe ?

---

### Post by kevinguillorytraining on 2009-10-07
This is one of the basic thing in Linux world. You ROCK :).

---

### Post by grunf_tnt on 2009-11-08
hello 

i am a newbie with cron and with ubuntu, and as you assume i have a problem with it :D

so here is my cron

```
* * * * * /bin/crtajdiag 1>/tmp/backup.out 2>&1
```

and my backup.out is empty!

here is what i get in my auth.log 

```
Nov  8 15:42:01 ubuntu CRON[6872]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov  8 15:42:01 ubuntu CRON[6872]: pam_unix(cron:session): session closed for user root
Nov  8 15:43:01 ubuntu CRON[6898]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov  8 15:43:01 ubuntu CRON[6898]: pam_unix(cron:session): session closed for user root
```

and syslog

```
Nov  8 15:42:51 ubuntu wpa_supplicant[1030]: CTRL-EVENT-SCAN-RESULTS 
Nov  8 15:43:01 ubuntu CRON[6899]: (root) CMD (/bin/crtajdiag 1>/tmp/backup.out 2>&1)
Nov  8 15:43:51 ubuntu wpa_supplicant[1030]: CTRL-EVENT-SCAN-RESULTS 
Nov  8 15:44:01 ubuntu CRON[6921]: (root) CMD (/bin/crtajdiag 1>/tmp/backup.out 2>&1)
```

adn here is my crtajdiag script witch is working whena i call her up from comand line like this 
```
sudo /bin/crtajdiag
```
i get a fine diagram like in the atachment 
but with cron nothing is hapening the time axis is updated buth without the diagram...
and te script lool like this
```
#!/bin/sh

rrdtool graph /var/www/potrosnja-10min.png --start end-10m --width 323 --end now --slope-mode --no-legend --vertical-label Watts --lower-limit 0 --alt-autoscale-max DEF:Power=powertemp.rrd:Power:AVERAGE LINE1:Power#0000FF:"Average" > /dev/null
```

please HELP!!!!!!

---

### Post by grunf_tnt on 2009-11-08
:D i did not update a correct rrd database :D am i stupid or not :D...thx myself

---

### Post by ~(/\)idow~ on 2009-11-11
Ubuntu does have a gui to start programs its here:

system: preferences: startup applications.  

That auto starts any gui program when you log in.

(i personally use kde though on my ubuntu system due to the way it looks etc..  i  have both on my box though but i don't see gnome much these days )

---

### Post by waz668 on 2009-11-14
cron has been driving me nuts  ](*,)
oh thank the sweet baby Jesus for this thread! :KS

---

### Post by ufarmer on 2009-11-20
I just can't get my crontab to work.  I have saved:

*/15 * * * * /home/kevin/grapes.pl

to a file named kevin.cron, and then run:

crontab /home/kevin/kevin.cron.

However, the out put of crontab -l is empty.  I tried running crontab -e and this opened up my editor.  I then enter the same values in the editor but when I try to save it I get a complaint that a file like /tmp/crontab.1tXyq6/crontab does not exist.  I created this file, saved my crontable and still the output of crontab -e is empty.  Incidentally, repeating this procedure just keeps generating complaints that a file on some very random seeming path like /tmp/crontab.<random number> does not exist.

It shouldn't be this mysterious.  Any advice is appreciated.

---

### Post by growthmetal on 2010-01-09
Note to all of you who were unable to get your cron job to work:

Be sure to include a newline at the end of the file!  Cron will silently ignore jobs on lines that don't have newlines at the end.

Sorry if someone already mentioned this, I'm too lazy to look through all 18 pages of this thread.

---

### Post by FatBoyNotSoSlim on 2010-04-24
My VPS was unexpectedly shut down in a power outage in its DC last week, and since then the crontab hasn't been working. I've been trying to figure it out for a week, but I'm at the point of needing help from others.
This is the crontab in question:
```
# m h  dom mon dow   command
*/3 * * * * /root/flexget_neil/flexget/flexget.py config.yml -q
*/3 * * * * /root/flexget_matt/flexget/flexget.py config.yml -q
*/3 * * * * /root/flexget_ahk/flexget/flexget.py config.yml -q
*/5 * * * * /root/removelock.sh
50 23 * * * /root/ps3tc_au.sh
55 23 * * * /root/ps3tc_fbnss.sh
*/30 * * * * /usr/bin/flexget --cron

```
Running the shell scripts by hand or invoking both the types of flexget commands work, but no longer from in the crontab.
This is under the root account (yeah yeah yeah...) and yet they still won't play nice. I figured the shutdown last week might have corrupted a file, and a '.lock' file was created or some permissions changed, but I'm not having any luck with it.
Any help would be great. :)

EDIT: I fixed it. I got some help in another forum, and typically I skipped over the basic step of checking if cron was even running. :)

---

### Post by lance bermudez on 2010-05-06
could someone look at my post and tell me what i'm doing wrong
[http://ubuntuforums.org/showthread.php?p=9248513](http://ubuntuforums.org/showthread.php?p=9248513)

---

### Post by targa86 on 2010-08-21
Great examples.

  Always use full paths in cron!

---

### Post by GrouchyGaijin on 2010-12-25
Hi,

I use a really cool program called autokey-gtk the only problem is that over time it takes more and more ram.  I found that quitting the program and restarting it will keep the program from becoming so bloated that it no longer functions.

I'd really like to be able to automatically have the program launch then 58 minutes later automatically quit and then after one minute relaunch.

I'm not sure how to do this.  I tried adding 01 * * * * autokey-gtk via crontab -e to see if I could get the program to launch.  It didn't work.

I'd appreciate any help.

Thank you.

---

### Post by Zasmoker on 2011-01-29
Hello all, i`m new with Ubuntu and i like it but i`m having trouble installing a cronjob i vahe try`d but it not working like i want to so i figure i miss spelled something in the command 

i did crontab -e ( unde root username ) 

added this line there 
```
59 *    * * *  cd /home/PATCH TO FILE/psychostats3.1 &&  ./stats.pl && echo "Stats update: $(date)" >>  /tmp/mybackup.log
```From what i`v read in this topic this line should run ./stats.pl and add a line in mybackup.log every 59 minutes. 

If there is something wrong there please someone help me figure this out .

ps : sry for bad language.

Nvm : working as intended :D thx too

---

### Post by BeNiza on 2011-07-27
Thanks for this really useful HowTo. Could you please also tell us how to execute cronjobs requires authentication (like syncing a folder with a remote server over ssh)

---

### Post by wolterh on 2011-07-27
> **ardchoille said:**
> Thanks, that solves part of it. Any way to get that to be permanent?
*(He was talking about selecting the editor from which the cron file is edited)*

I don't know if this was answered to you in the way I did below, as I did not read every page in this thread, but check it out:

```
sudo select-editor
```

---

### Post by wolterh on 2011-08-12
Oh thanks, that comes pretty handy to me :) just one question, does it start at 00 by default or is that something one can specify?

---

### Post by mackconsult on 2011-12-03
I tried searching on this thread for my problem but could not find anything.

I have a QNAP TS259 with the most recent firmware.  I log in as admin and then edit the admin crontab file to add two lines to run backup scipts.  These were added the end of last week, and then today I saw that these entries were gone.  I verified mid week they were there.

It's as if the admin crontab file is being over written every so often.

Is there a way to make the crontab changes stick.

---

### Post by dtheurer on 2013-07-06
Hi all,

I'm trying to simplify my crontab entries. I currently have them like:
```
1 1 * * * root /scripts/test.sh >>/scripts/test.sh.log 2>>/scripts/test.sh.err
```
and these work just fine. However, I'd like to replace the redirects with variants of the actual script name - something like:
```
1 1 * * * root /scripts/test.sh >>&0.log 2>>&0.err
```
The only format I've found for use of the & in crontab entries is like:
```
1 1 * * * root /scripts/test.sh >/scripts/test.sh.log 2>&1
```

Note: The redirects need to be appendable (i.e. I must be able to use >> instead of > )

Is this possible?

Thanks for any and all suggestions/help.
Dirk

---

### Post by dtheurer on 2013-07-06
I wasn't familiar with what the 2>&1 was actually doing. Found some good info on it.
  [http://stackoverflow.com/questions/818255/in-the-shell-what-is-21](http://stackoverflow.com/questions/818255/in-the-shell-what-is-21)

I  found some other info on accessing the name of the script that's  running (in bash, this would be $0). So, my next attempt looked like:
```
1 1 * * * root /scripts/test >>$0.log 2>&1
```
It does produce a file; unfortunately, it's named *.log* and it winds up in the *root* user's directory.

So, I  renamed *test.sh* to *test2.sh*, and created */scripts/test.sh* which contains:
```
#!/bin/bash
/scripts/test2.sh >>$0.log 2>>%0.err
```
which is invoked by the crontab entry:
```
1 1 * * * root /scripts/test.sh >/dev/null 2>&1
```
Log is now written to */scripts/test.sh.log* and errors to */scripts/test.sh.err*. Bit of a hack, but **yea!** :D

Dirk

---

### Post by jplello on 2013-09-06
Hi, can someone please help or redirect me?

I am running kubuntu 12.04I have scheduled tasks in System Settings - Task Scheduler.
Now, some of these tasks do run properly, others don't. When I type crontab -l I can see the tasks set in the task scheduler, but if I opne etc/crontab with Kate, for instance, I see only a few root commands.
When one of those tasks is not run, I see in syslog the line:
(root) CMD (if [ -x /usr/bin/gsmsmsrequeue ]; then /usr/bin/gsmsmsrequeue; fi)
My questions are:
1. What file is crontab -l reading?
2. Why some tasks do run and others don't?
3. Where should I place the MAILTO= to have emails from cron sent to my email?
4. What is gsmsmsrequeue and what is it doing here?


Thank you

---

### Post by geazzy2 on 2014-08-15
Thanks for this tutorial :)

---

