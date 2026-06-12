---
title: "HOWTO: Set KDE Cache to RAM to Improve Desktop Performance"
date: 2014-05-19
forum: Tutorials
---

### Post by wd5gnr2 on 2014-05-19
This seems to work pretty well. The idea is to have KDE put temporary files in RAM instead of on your hard drive. This works well if you have a slow writing drive (e.g., RAID and write throughs) and/or lots of RAM. 

**Step 0:** You should really have a backup before you do this. If you can't be bothered, at least backup /etc/fstab:
```
mkdir ~/backup
cp /etc/fstab ~/backup/fstab

```


**Step 1: Create a mount point for a tmpfs**
```
sudo mkdir /tmp-ram
```

**Step 2: Mount tmpfs on new mount point**
```
sudo <your favorite editor> /etc/fstab
```
Examples of <your favorite editor> would be nano, kate, etc.

Add this line to the bottom of the /etc/fstab
```
tmpfs         /tmp-ram     tmpfs      noatime,nosuid,nodev,size={SIZE}    0    0
```

{SIZE} is the maximum amount of RAM you want to dedicate to the temporary file system.
For example, I have:

 ```
tmpfs         /tmp-ram     tmpfs      noatime,nosuid,nodev,size=900    0    0
```

The default limit is 1/2 of your RAM and swap space. If you exceed this, you can make your machine perform slowly or not at all, so don't commit too much memory.

**Step 3: Create mount**
Issue:
```
sudo mount -a
```
Or if you are lazy, just reboot. I prefer do to the mount -a so if I made a typo I will see an error message and can go fix it.
If you want to verify just say:
```
mount
```
And verify that /tmp-ram is mounted with tmpfs file system.


**Step 4: **
Create file in ~/.kde/env named relo.sh with your favorite text editor (no sudo required)
```

export KDETMP=/tmp-ram 
export KDEVARTMP=/tmp-ram 
ln -s /tmp-ram/kde-{USERID}  ~/.kde/tmp-{HOSTNAME}

```

Replace {HOSTNAME} with whatever the hostname command tells you your computer name is. For example, mine is:
```
~/.kde/tmp-enterprise
```

Replace {USERID} with your user ID

Edit file /etc/rc.local and put these lines before the exit 0 that should be at the end:
```

mkdir /tmp-ram/{USERID}
chown -R {USERID} /tmp-ram/{USERID}
chmod 700 /tmp-ram/{USERID}

```

Again, use your user ID, like this:
```

mkdir /tmp-ram/alw
chown -R alw /tmp-ram/alw
chmod 700 /tmp-ram/alw

```

**Step 5. Log out of KDE**
Just use the leave button and tell it to log off. You should go back to the login screen.

**Step 6. Get a Console** 
Open a console (Control+Alt+F1) and log in.

**Step 7. Remove tmp-{HOSTNAME}**
Issue from the console:
```
rm ~/.kde/tmp-{HOSTNAME}
```
(replace {HOSTNAME} with your hostname)

You can then exit the console or if you are lazy you can reboot by issuing the command:
```
sudo reboot[CODE]

**Step 8. Return to X and log in**
If you didn't reboot, make sure /tmp-ram/kde-{USERID} exists (issue the 3 commands you put in rc.local manually, if not, or just reboot) and use Control+Alt+F7 (not sure it is always on F7). Then log in as usual

**Step 9. Verify**
Open a konsole prompt and issue:
[CODE]
ls -l ~/.kde

```

You should see cache-XXX, socket-XXX, and tmp-XXX as links to /tmp-ram (XXX is your hostname).

**Reversal**

It is pretty easy to reverse all of this. Simply remove relo.sh and  delete the tmp file (~/.kde/tmp-{HOSTNAME}) when KDE is not running. Then log back in. You can also  unmount the tmpfs, remove the fstab line, and delete the tmp-ram mount  point. I would wait to do that until after you logged back into KDE and verified that the files no longer point to /tmp-ram.


**Limitation & Notes**
When KDE starts up it will have to rebuild the cache it uses which means you will get a slightly slower startup. It is imperceptible on my machine. Your mileage may vary.

This seems to work well for me. Then again, I have a write through SSD  cache to a RAID array so writes are expensive even if cached.

---

### Post by giocitta on 2014-06-24
It doesn't work for me: Kubuntu 14.04; x86_64. I always get this answer: "call to lnusertemp failed". I think the problem is inherent to the "ln -s  /kde-ram/kde-USERNAME" (in my case, kde-puzzolaccio): what the link points towards ? I hope you will kindly help me. Thanks

---

### Post by wd5gnr2 on 2014-06-24
Oops, I chopped off part of step 4 on an edit. Try again and let me know.

---

### Post by giocitta on 2014-06-25
Thanks for your reply. I repeated the whole procedure, but I end up - after a normal KDE login screen - in a black screen where I see only the mouse's arrow (in other words, no KDE). What do you think I should do?

---

### Post by wd5gnr2 on 2014-06-25
Hmm.. I would move or delete relo.sh from a command prompt (ALT+F1 and then log in from there). Then restart and you should be able to get into KDE. 

You can then back off the changes to fstab, etc. and decide if you want to try again or not.

---

### Post by chuckyanutsup on 2014-07-05
I run kubuntu on top of Ubuntu Studio. I followed the steps above, while tmp and cache are linking ok for me, socket is not. Your method seems to have fixed a problem I was having with RAM, thank you for posting :)  

```
ls -la
```
in my .kde folder shows
```
tmp-{HOSTNAME} -> /tmp/kde-{USERID}
``` 
```
cache-{HOSTNAME} -> /var/tmp/kdecache-{USERID}
``` 
```
socket-{HOSTNAME}
```

---

### Post by wd5gnr2 on 2014-07-07
Well, my host name is enterprise and I have socket-enterprise -> /tmp-ram/ksocket-alw

If you type:

echo $KDETMP

and

echo $KDEVARTMP

from a shell inside KDE (e.g., Konsole) what do you see?

Also, did you put the commands in rc.local and either reboot or make sure they executed?

---

### Post by chuckyanutsup on 2014-07-08
Both echo commands returned nothing.
My rc.local looks like this 
```
#!/bin/sh -e
#
# rc.local
#explanation of what script does
mkdir /etc/rc.local/christopher
chown -R christopher /tmp-ram/christopher
chmod 700 /tmp-ram/christopher

exit 0

```

I'm a little unclear on step 4. Should the relo.sh file contain the below code? When it does I am unable to log into kde, I've tried making the file executable but to no avail so I've left it as a blank file.
```

export KDETMP=/tmp-ram 
export KDEVARTMP=/tmp-ram 
ln -s /tmp-ram/kde-{USERID}  ~/.kde/tmp-{HOSTNAME}
```

---

### Post by wd5gnr2 on 2014-07-08
You need to replace {USERID} with your user ID and {HOSTNAME} with your host name. So since I am alwill on computer enterprise,  my line looks like this:

ln -s /tmp-ram/kde-alwill  ~/.kde/tmp-enterprise

Your rc.local the mkdir should NOT say /etc/rc.local/christopher
It should say:

mkdir /tmp-ram/christopher

That's probably your problem right there.

---

