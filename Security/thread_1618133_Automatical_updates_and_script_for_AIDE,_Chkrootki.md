---
title: "Automatical updates and script for AIDE, Chkrootkit, and ClamAV"
date: 2010-11-10
forum: Security
---

### Post by toolmania1 on 2010-11-10
How can I get AIDE, Chkrootkit and ClamAV to update automatically?  I found something about crontab.  I put the update scripts in there but I could not tell if they ran yesterday at the scheduled time.Also, I tried to make a script with the AIDE --update and --check in it.  The script would not run.  sudo sh myscript.shIs that how I would make the script also?

---

### Post by toolmania1 on 2010-11-10
sudo aide --config=/usr/share/aide/config/aide/aide.conf --updatesudo aide --config=/usr/share/aide/config/aide/aide.conf --checksudo chkrootkitsudo freshclam -dclamscan -ri –bell --exclude-dir=proc --exclude-dir=sys --exclude-dir=dev----------------------------The above is what I wanted to have run every day or at least put in a script that I just run.First off, can I jam all that into one script?Secondly, how would I put all that into a script?  ( I know it may be simple, but I had an issue with my script and it errored our displaying symbols and such in the error )

---

### Post by toolmania1 on 2010-11-10
I'm sorry, that was messy.  I am reposting so it is easier to read.
-----------------------------------------------------
sudo aide --config=/usr/share/aide/config/aide/aide.conf --update
sudo aide --config=/usr/share/aide/config/aide/aide.conf --check
sudo chkrootkit
sudo freshclam -d
clamscan -ri –bell --exclude-dir=proc --exclude-dir=sys --exclude-dir=dev
---------------------------------------------------

The above is what I wanted to have run every day or at least put in a script that I just run.First off, can I jam all that into one script?Secondly, how would I put all that into a script? ( I know it may be simple, but I had an issue with my script and it errored our displaying symbols and such in the error )

---

### Post by toolmania1 on 2010-11-29
Just a follow up.

How can I get things to run automatically, like with a script maybe?  

1. Do I use crontab?
2. Can AIDE, be ran from crontab?
3. Can chkrootkit, be ran from crontab?
4. Can clamav be ran from crontab?

---

### Post by anomie on 2010-11-29
You seem eager to learn about scripting, so here is a very good starting point (for bash): 
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

Of course you can run those programs non-interactively in a cronjob. 

For sudo([COLOR="Black"]8[/COLOR]) entries in a script to work, you'll need a NOPASSWD sudoers(5) tag - preferably for just a few specific commands - for the user the cronjob is running as. 

Alternatively, you can run this as root's cronjob. I'm not sure how that sort of thing is viewed in the *buntu community, though, so I will defer to a guy/gal who is more thoroughly immersed in the culture. ;)

---

### Post by toolmania1 on 2011-01-08
I found that I can put some of these things into crontab. That seems automatic which is more of what I wanted besides doing a manual run of a script.

---

