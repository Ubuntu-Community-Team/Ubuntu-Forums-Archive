---
title: "Ubuntu One excruciatingly slow and other questions"
date: 2011-03-30
forum: Ubuntu One (CLOSED)
---

### Post by sea_dawg on 2011-03-30
Ubuntu One is excruciatingly slow, taking hours to update 2 small spreadsheets today and still grinding away.  Taking over 12 hrs yesterday to update a hand full of small files.

The problems may be of my own making.  I am syncing 3 user defined directories across 3 computers.  Because these files come from multiple directories I didn't want to just toss them into the Ubuntu One folder and have to sort them out on each machine.

My first question is how to make Ubuntu one behave and run at a decent speed?  So far I have tried limiting bandwidth, this has no apparent effect even when the values are set extremely low.

At home, on a slower DSL connection Ubuntu One takes over 100% of my bandwidth leaving me with no usable internet connection.

Ubuntu One starts up without my asking it to upon startup.

Once it is running on the slower home DSL I cannot open System -> Preferences -> Ubuntu One to disconnect, slow it down or stop it.  There is a brief window of time, less than one minute, on first startup where I have an opportunity to control Ubuntu One.

My second question is how to stop Ubuntu One from syncing a given directory?  Simply un-checking the "Synchronize this Folder" in Places only works for a while.  Ubuntu one eventually decides to go back to work on that folder, even if no files have been added/deleted/modified. 

My last question is if I cannot get Ubuntu One to behave how to I permanently shut it down so it won't ever run again?  Lugging USB drives around is a far better procedure for me than this

---

### Post by r-senior on 2011-03-30
I really want Ubuntu One to work, I really do. I'm trying to use it for non-essential stuff and it's definitely getting better but personally I still don't trust it with anything important.

You might be better off with Dropbox, which syncs in seconds, doesn't get confused and doesn't crash.

There's a guide to removing it completely here:

[https://answers.edge.launchpad.net/ubuntuone-client/+faq/778](https://answers.edge.launchpad.net/ubuntuone-client/+faq/778)

---

### Post by Perfect Storm on 2011-03-30
Moved to 'Ubuntu One' forum.

---

### Post by sea_dawg on 2011-03-30
r-senior,

Thank you for the quick response and link.  I'll give it a try.  Ubuntu One has been working for over 5 hrs now to update two small spread sheets. It's got to go.

---

### Post by duanedesign on 2011-04-06
These commands from the terminal can tell you how many files are in your queue and help you to gauge progress.
```

u1sdtool --waiting-metadata | wc -l
```

```
u1sdtool --waiting-content | wc -l
```

Ubuntu One starts at boot, if you do not want it too you will need to remove it from the startup applications *System > Preferences > Startup Applications*

To see folders that you have syncing with Ubuntu One you can use:

```
u1sdtool --list-folders
```

You will get something like:
id=3f8341ab-g431-4c8a-93f7-f512faa55hca subscribed=True path=/home/duanedesign/Pictures

to stop syncing a directory take the folder_ID and put it in the following command:
```
u1sdtool --unsubscribe-folder=FOLDER_ID
```
using the example:
```
u1sdtool --unsubscribe-folder=3f8341ab-g431-4c8a-93f7-f512faa55hca
```
to stop syncing and delete from the server:
```
u1sdtool --delete-folder=FOLDER_ID
```
using the example:
```
u1sdtool --delete-folder=3f8341ab-g431-4c8a-93f7-f512faa55hca
```

What version of Ubuntu are you running? If you are on Maverick and getting poor performance I would recommend upgrading to the [nightlies PPA]("https://launchpad.net/~ubuntuone/+archive/nightlies"). The newest version of Ubuntu One that is in Natty/nightlies PPA has many impovements. Be aware that once you upgrade to a newer version you can not go back to an older version of U1 as they likely use different metadata.

---

### Post by whollycow on 2011-04-08
I'm having a similar problem running an up-to-date Natty. I just set things up to sync my wxbanker information via U1 (consisting of 2 files: a transaction database file and a config file).

When I close wxbanker, even if I have made no changes, it has to resync the files. I guess because the database is being accessed, the file is being changed in some small way? In any case, U1 then proceeds to upload the 2 local bank.db and config files and it takes at least 1/2 hour! These are only 2 tiny files - 50kb and 100 bytes respectively.

I've noticed if I run 
```
u1sdtools -waiting | wc -l
```
it tells me there are some 500 files that are being uploaded.

When I look at the syncdaemon log, it looks like it is repeating the same action over and over again on bank.db-journal. I'm not entirely sure what this all means, but I've attached a small part of syncdaemon.log for reference.

---

### Post by dacovale on 2011-04-18
I'll add a +1 on the *really* slow sync for Ubuntu One. During 3 days, it managed to sync a whopping 2 MB (yes, MB). Today it jumped up to 240 MB without any explanation, but as I asked it to sync my Documents folder (850 MB) it is still a really long way from finished. Since I have a 100/100 line here ( or at least that's what I pay for, I usually don't get more than 80 Mbit up or down ), I can't really blame this on my connection.

I run the 11.04 beta, so the sync was something I wanted to test, now that Ubuntu One was so heavily marketed. I can't say anything good about it yet though.

Is there some setting I've missed here? Or some bug I can help triage?

---

### Post by Zilioum on 2011-05-12
Same here. Added my Documents directory (about 500mb) to Ubuntu One and it's been syncing for more than two days. At the moment only 127mb are already uploaded. 
On both of my pc's (both on 11.04) it takes hours for ubuntu one to change from "File sync starting" to actually syncing something.
I would love to move from dropbox to ubuntu one, but this is kind of a deal breaker for me.
Let me know, if anyone needs more information (logs etc.).

---

### Post by Zilioum on 2011-05-14
Things started to improve on my end. I don't know what the actual upload speed was, but at some point point things started to run smoothly and the directory synced in about 3 hours.
Now it also starts syncing pretty much instantaniously after I boot up. 
Does anyone share this experience?

---

### Post by nigeldodd on 2011-08-22
I can only add to the general mood of ignorance. Sometimes it works and sometimes it doesn't. Last week I set up a friend's laptop with Ubuntu 11.04 and registered a new ubuntu One account. New files placed in the Ubuntu One folder were instantly uploaded; all her picture files. Returning inspired to my setup I installed Ubuntu 11.04 on my old laptop. Ubuntu One behaves on my old laptop in a similar way to my desktop i.e. it spends forever saying "File Sync starting" but never actually does anything. Given that it happens on a new install of the OS I can't believe it is an OS problem. It would be good if somebody with knowledge of the Ubuntu One servers could respond.

---

### Post by duanedesign on 2011-08-23
> **nigeldodd said:**
> I can only add to the general mood of ignorance. Sometimes it works and sometimes it doesn't. Last week I set up a friend's laptop with Ubuntu 11.04 and registered a new ubuntu One account. New files placed in the Ubuntu One folder were instantly uploaded; all her picture files. Returning inspired to my setup I installed Ubuntu 11.04 on my old laptop. Ubuntu One behaves on my old laptop in a similar way to my desktop i.e. it spends forever saying "File Sync starting" but never actually does anything. Given that it happens on a new install of the OS I can't believe it is an OS problem. It would be good if somebody with knowledge of the Ubuntu One servers could respond.

Can you check what you get when you run the Terminal command:

```
u1sdtool -s

```
If you get State:READY you need to run the following to connect:

```
u1sdtool -c

```
after a couple minutes run the status command:

```
u1sdtool -s

```
Also could you check the file at ~/.cache/ubuntuone/log/syncdaemon-exceptions.log. A quick command in the Terminal to open it:

```
gedit ~/.cache/ubuntuone/log/syncdaemon-exceptions.log
```

---

### Post by tomek_wap on 2011-11-13
Same here, took up to 5 minutes to sync my PC with Ubuntu One server, 2 files: 220KB !!!

But uploaded about 7mb of photos from my Android phone in no time.

---

### Post by GTull on 2012-01-11
UbuntuOne is really slow uploading from my desktop computer aswell takes several hours to upload a couple of music files i (keep getting a window coming up every 30 minutes or so saying upload has started but i checked my upload speeds using sytem monitor and it will upload a few KB's and then freeze for a few minutes), yet i uploaded a couple music files from my android phone and it takes a few minutes, makes no sense.

---

### Post by BlinkinCat on 2012-01-11
> **GTull said:**
> UbuntuOne is really slow uploading from my desktop computer aswell takes several hours to upload a couple of music files i (keep getting a window coming up every 30 minutes or so saying upload has started but i checked my upload speeds using sytem monitor and it will upload a few KB's and then freeze for a few minutes), yet i uploaded a couple music files from my android phone and it takes a few minutes, makes no sense.

You really should have started your own thread as there were several issues discussed on this one

Cheers - :)

---

### Post by hackertarget on 2012-01-11
Not that I have much technical detail to add but I recently tested Ubuntu One and found it very slow and unreliable.

This could be an excellent service to be bundled with Ubuntu, and help move towards the 200 million user mark; however unless its as fast and stable as Evernote, it will only generate frustration.

---

