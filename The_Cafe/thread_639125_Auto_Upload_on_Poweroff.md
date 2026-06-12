---
title: "Auto Upload on Poweroff?"
date: 2007-12-12
forum: The Cafe
---

### Post by NonPermissive on 2007-12-12
I'm wondering if it would be possible to write a shell script which would, on poweroff, upload the contents of a folder (In this case, just a few kilobytes) to say, xdrive.

I ask because I plan on doing a remastered live CD (with remastersys) with all my preferences, and I would hate to lose my chat logs after shutting down the machine.

Thanks in advance.

---

### Post by NonPermissive on 2007-12-12
Just to be clear, xDrive is the site I plan to upload to to, in case you aren't sure what it is.

---

### Post by toupeiro on 2007-12-12
You can set a shutdown script at any run level you want (/etc/rc0.d to /etc/rc6.d), you just want to begin the name of the script with the letter K (in caps) and a number indicating the order of execution, 1 being first, and 99 being last.  I would definately do something like this before the script where your network services are stopped :)

So the answer is yes.  If the process you want to do can be scripted, it can be set to execute on system shutdown.


I dont know if these runlevels are different with ubuntu but traditionally your runlevels would be something like this:
/etc/rc0.d = system halt
/etc/rc1.d = Single User Mode
/etc/rc2.d = Multi-user mode with no network 
/etc/rc3.d = Default CLI start - Multi user mode
/etc/rc4.d = Reserved for whatever you want
/etc/rc5.d = X-windows (KDE/Gnome)
/etc/rc6.d = system reboot


here is a look at my /etc/rc6.d directory so you can see the naming its looking for: (Note: they don't HAVE to be links)

> 
lrwxrwxrwx 1 root root  13 2007-12-06 06:45 K01gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root  18 2007-12-07 08:25 K01timidity -> ../init.d/timidity
lrwxrwxrwx 1 root root  17 2007-12-06 06:45 K01usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root  13 2007-12-08 12:01 K15mpd -> ../init.d/mpd
lrwxrwxrwx 1 root root  22 2007-12-06 06:45 K16avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root  16 2007-12-06 06:45 K16dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx 1 root root  20 2007-12-06 06:45 K18consolekit -> ../init.d/consolekit
lrwxrwxrwx 1 root root  16 2007-12-06 06:45 K20apport -> ../init.d/apport
lrwxrwxrwx 1 root root  20 2007-12-06 06:45 K25hwclock.sh -> ../init.d/hwclock.sh
lrwxrwxrwx 1 root root  20 2007-12-06 06:45 K50alsa-utils -> ../init.d/alsa-utils
lrwxrwxrwx 1 root root  26 2007-12-06 06:45 K59mountoverflowtmp -> ../init.d/mountoverflowtmp
lrwxrwxrwx 1 root root  21 2007-12-06 06:45 K99laptop-mode -> ../init.d/laptop-mode
-rw-r--r-- 1 root root 353 2007-10-04 04:17 README
lrwxrwxrwx 1 root root  41 2007-12-06 06:45 S01linux-restricted-modules-common -> ../init.d/linux-restricted-modules-common
lrwxrwxrwx 1 root root  22 2007-12-06 06:45 S15wpa-ifupdown -> ../init.d/wpa-ifupdown
lrwxrwxrwx 1 root root  18 2007-12-06 06:45 S20sendsigs -> ../init.d/sendsigs
lrwxrwxrwx 1 root root  17 2007-12-06 06:45 S30urandom -> ../init.d/urandom
lrwxrwxrwx 1 root root  22 2007-12-06 06:45 S31umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx 1 root root  18 2007-12-06 06:45 S40umountfs -> ../init.d/umountfs
lrwxrwxrwx 1 root root  20 2007-12-06 06:45 S60umountroot -> ../init.d/umountroot
lrwxrwxrwx 1 root root  16 2007-12-06 06:45 S90reboot -> ../init.d/reboo



So I might write a script called K01sync and put it in /etc/rc0.d and /etc/rc6.d so its the first thing done on system shutdown or reboot.

---

### Post by NonPermissive on 2007-12-13
What command would I use to upload the files?

---

### Post by toupeiro on 2007-12-13
Well, after poking around on x-drive, it appears they don't support FTP or SFTP, they want you to use a proprietary desktop client.  So, you might be screwed with xdrive.

I did find one called mediamax which says they support ftp (generally not secure, but easy).  Their security is apparently in the storage of data, not in the transfer of it, but not bad still for free.  If you have sensitive data, encrypt it ahead of time. :)

they give you 25GB free, but have some limitations (single file size, etc.)  worth checking out though.

So, here is what I would so if I had to do something like this:


```
#!/bin/bash

#First, get todays date in a variable.  This will allow you to keep the script unattended for the most part because you dont have to worry about naming.
DATE=$(date +"%b-%d-%y")

# Compress the file or directory

sudo tar -zcvf <insert_name_nere>-$DATE.tar.gz  /path/files/wildcardifneeded

# now configure your ftp upload script

HOST='ftp.whatever.you.use.com'
USER='your_login_id_here'
PASSWD='your_password_here'
FILE='<insert_name_here>-$DATE.tar.gz'

ftp -n $HOST <<END_SCRIPT
quote USER $USER
quote PASS $PASSWD
put $FILE
quit
END_SCRIPT
exit 0
```

you can also substitute several FILE variables for 1

FILE1=whatever.whatever
FILE2=whatever.whatever

then
put $FILE1
put $FILE2


I do recommend the use of tar for management and ease.

---

### Post by NonPermissive on 2007-12-13
This suits my purposes exactly. The next step is to download the chat logs again on next startup.

*makes note to learn more shell commands*

---

### Post by toupeiro on 2007-12-13
Awesome!  Glad this is going to work out for you.

Yes, while you can do most things with the GUI, its always good to get familiar with the CLI and shell commands :)

Startup scripts you create principly the same way you do shutdown scripts, but instead of using K##scriptname you use S##scriptname whee ## is the priority you want for execution (01 being first  and 99 being last, yadda yadda)

In the FTP script above, you might have to get more specific about filenames, but  essentially, if you are doing this on the same day, you can just change the word 'put' to 'get' and it should work for you.  This is assuming you reboot every day, which you probably do not do.

you can also do something like this instead of the get command:

prompt
mget *

which will just copy down all the logs.

issuing the prompt command in FTP turns off interactive prompting (no, are you sure? y/N stuff)

---

### Post by NonPermissive on 2007-12-14
Thank you *very* much.

Y'know, you could probably do the same thing for your firefox profile, saved documents, installed programs, heck, all the changes you've made to the system could be restored during every boot!

I could make an entire distro off of this concept!

I must thank you again.

---

### Post by NullHead on 2007-12-14
Wouldn't this process be rather slow??? I mean (in my case) uploading content only goes at 35kb/s ... I wouldn't want for edited video files to upload and download every time I boot. 

Also should look into raid if you're worried about loosing data.

---

### Post by NonPermissive on 2007-12-14
> Wouldn't this process be rather slow???
Well, yes, at least if you're in North America. It would work a lot better in the Asian countries that get 500 Mbps both ways (yes, I am drooling), but if you make only minor changes to a system, and have an average upload speed, it could be feasible.

---

### Post by toupeiro on 2007-12-14
if you don't want this script to run on boot, research crontabs :)

Sure there are other ways you can get data from one place to another.  millions in fact.  This is a solution for the question the OP asked for.  Sure, RAID is good, but this solution is a remote solution.  The OP could drop this down to any system desired, regardless of the state of the originating system.  This may be more practical for what he wants, else he could have simply used an external drive.  I assume that a person wants an answer when they ask a question first and foremost (I know, crazy, huh?).  If their answer doesn't give them the results they expect, then sure, I am more than happy to suggest alternatives.


I don't always presume to know a better way to get something done.  sometimes, people just want their questions answered.  If everyone deferred every answer away from what they actually wanted to accomplish, things like this wouldn't be searchable for later use by someone else with a need for this procedure. 

**:edit:**
within reason of course.  If someone is trying to do something that might compromise their system, thats a different scenario


Not trying to rant here, just trying to make a point.

---

### Post by smartboyathome on 2007-12-14
Would I be able to run a script on logout?

[off-topic]Also, is there a way to make a linux account without a password? I am thinking of setting up a guest account on my machine which deletes the content of the user's guest directory after they log out.[/off-topic]

---

### Post by toupeiro on 2007-12-15
> **smartboyathome said:**
> Would I be able to run a script on logout?

From a GUI?  I'd have to google it..  I've never tried it  you can try creating a .bash_logout file in your home directory with the script you want to run there, but I can't swear that gnome will read it.  I think there is something called /etc/gdm/PostSession/Default which you might be able to play with too.  Again, just guesses there.

> [off-topic]Also, is there a way to make a linux account without a password? I am thinking of setting up a guest account on my machine which deletes the content of the user's guest directory after they log out.[/off-topic]

I'm sure there is, but I can't say I've ever tried this.  I've done some maintenance tasks like you are talking about, but I used a root crontab rather than an account.  There might be an answer in the general help areas for this.

---

### Post by NonPermissive on 2007-12-15
Just to be clear, my idea was so that you could run it as a live DVD, and have all of you setting stored online, so that you would be booting into an environment which never has to be installed on the system (that would defeat the purpose) and your "hard drive" is loaded from the Internet at boot. All changes would be consistent.

Maybe I'm being a bit ambitious here, but I'm just putting the idea out there.

---

### Post by toupeiro on 2007-12-15
:)  I have a few of my servers doing something similarly.  I have 2 NAS boot servers and I have a couple servers HBA attached to a SAN that boot the OS on disks not directly on the server.  Its a very cool idea if you have the bandwidth :)

---

### Post by NullHead on 2007-12-15
Well I don't have the bandwidth!:lolflag: , but I can see why one would want to use this script .. it's just my thinking is why would you want to take hours at a time uploading and downloading files witch would be easier accessed by direct hard-drive. I didn't mean to change anyone's mind about this process, it's just I was curious about why you wouldn't use raid, because it seemed like he just wanted a backup.

---

### Post by NonPermissive on 2007-12-15
Again, as long as you make only minor changes, or have an amazing connection (like those in Honk Kong that made the Digg front page a while back) then it could be very useful.

---

### Post by jken146 on 2007-12-15
> **smartboyathome said:**
> [off-topic]Also, is there a way to make a linux account without a password? I am thinking of setting up a guest account on my machine which deletes the content of the user's guest directory after they log out.[/off-topic]

Yes there is -- I've seen it in a thread somewhere on this site a while ago.  It involves changing the /etc/shadow file to use the encrypted garble that's equivalent to the empty string.  Not recommended of course.

---

### Post by smartboyathome on 2007-12-15
> **jken146 said:**
> Yes there is -- I've seen it in a thread somewhere on this site a while ago.  It involves changing the /etc/shadow file to use the encrypted garble that's equivalent to the empty string.  Not recommended of course.

Of course it isn't recommended, but as long as I don't give it permission to run administrative tasks, it shouldn't cause a security hole.

---

