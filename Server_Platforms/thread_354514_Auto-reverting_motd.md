---
title: "Auto-reverting motd"
date: 2007-02-06
forum: Server Platforms
---

### Post by Werner_vd_Walt on 2007-02-06
Referring to a couple of older threads which do not seemed to have been answered, I am bringing up the issue of the auto-reverting motd text again.

After changing the motd text in either /etc/motd (which is just a link in any case) or /var/run/motd directly everything works okay until the box has to be restarted. After the reboot the motd reverts back to the original install text. I have grepped through all the files to try and find the source file feeding this text but the only thing that is found is /var/run/motd itself.

The problem is that this behaviour is not consistant as on different boxes it will sometimes keep the changes through a reboot after the initial customization. If you then later on want to further customize you can forget it as it will now just keep on reverting back to the 1st custom version.

Bizarre... if any knows what is feeding the original text for the motd after the initial install it will be of great help. Alternatively if anyone knows whether the text is being cached somewhere during a session maybe one can clear the cache forcing it to re-read the changes?

Thanks.

Werner

---

### Post by Werner_vd_Walt on 2007-02-07
Okay seeing as this seems to be a problem experienced by a couple of people I did some research and came up with the following. If anything is incorrect or you disagree then you're more than welcome to jump in on the thread :)

In /etc/init.d/ there is a file bootmisc.sh that runs at boot time. In the file there is a section that addresses the update of motd during the boot. Basically what it will do is take a portion of the uname string value and then concatenates the text from the /etc/motd.tail file to it. So whatever is in your motd will just be overwritten with those values. In actual fact it seems like this is the process that actually creates the /var/run/motd file in the first place on the fly at every boot. If you comment these commands out, reboot and check, then you'll see that there is no /var/run/motd.

So to prevent the overwrite of your custom message the best option is:
1. Place the text you want to display in the /etc/motd.tail file and not in the /etc/motd file as everyone always suggests (this is for Ubuntu, I have not checked if it works the same on other distributions).

I tried to comment out the lines in /etc/init.d/bootmisc.sh and then manually create my own /var/run/motd file with the text in it. It seems however there is a clean-up script that runs (I presume at shutdown?) that removes the motd file, so whatever you created there is going to disappear in any case. I haven't been able to figure out which script removes it yet but will post the answer when I have it :)

I hope this helps.

Werner

---

### Post by marlon_za on 2007-07-20
Yes, an annoying little one.
If you prefer to not have the MOTD automatically updated, 
check inside /etc/default/rcS

Find this line:
# Set EDITMOTD to "no" if you don't want /etc/motd to be editted automatically
EDITMOTD=yes

Set it to
EDITMOTD=yes

Save, and voila... This was introduced in Debian etch iirc.
:KS

---

### Post by saaz on 2007-10-05
From the manpage on rcS (in Feisty):

```
The EDITMOTD variable is no longer used.
```

Anyone know of the new way to fix this problem? Seems kinda stupid that you can't edit the motd file and have it stick like on every other *NIX. Very annoying..

---

### Post by tasos on 2007-10-09
The one that Werner_vd_Walt proposed works fine for me..

the script is **/etc/rcS.d/S80bootmisc.sh**

find the following code in it:
```
# Update motd
 uname -snrvm > /var/run/motd
 [ -f /etc/motd.tail ] && cat /etc/motd.tail >> /var/run/motd
```

Comment the second line:
```
# Update motd
# uname -snrvm > /var/run/motd
 [ -f /etc/motd.tail ] && cat /etc/motd.tail >> /var/run/motd
```
and place your custom text in /etc/motd.tail that way the motd file will be created with your text

---

### Post by satimis on 2007-11-23
Hi folks,


Ubuntu 7.04 server amd64
Postfix 2.3.8


I expect running /etc/motd to notify users who login advising them "Server will be down for repair within half an hour..... Pls save your work, etc."  Will /etc/motd be reverted automatically to it original after reboot removing all the msg added?  Or I have to edit /etc/default/rcS adding a line "EDITMOTD=yes" to take effect?


$ cat /etc/default/rcS```

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=yes
VERBOSE=no
FSCKFIX=no

```


TIA


B.R.
satimis

---

### Post by NorthernGit on 2007-12-21
From the official Debian Etch release notes:

5.15 Message of the day

/etc/motd is now a symlink to /var/run/motd which is rebuilt by /etc/init.d/bootmisc.sh from a template, /etc/motd.tail, at each reboot. It means that changes made to /etc/motd will be lost. Changes made into /etc/motd.tail are not automatically applied to /etc/motd other than at reboot.

Also, the EDITMOTD variable at /etc/default/rcS no longer has any effect. If you wish to disable updating of the motd, or want to maintain your own content for the message of the day you just have to point the /etc/motd symlink to a different file such as /etc/motd.static and make your changes there.

[http://www.debian.org/releases/stable/i386/release-notes/ch-information.en.html]("http://www.debian.org/releases/stable/i386/release-notes/ch-information.en.html")

---

