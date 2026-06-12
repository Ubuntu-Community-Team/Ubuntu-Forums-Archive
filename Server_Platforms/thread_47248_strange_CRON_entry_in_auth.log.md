---
title: "strange CRON entry in auth.log"
date: 2005-07-07
forum: Server Platforms
---

### Post by blaylock on 2005-07-07
Hi, 

I keep getting these two lines every hour in my auth.log file and i cant figure out what is happening, or why. 


```
Jul  7 19:17:01 methane CRON[27711]: (pam_unix) session opened for user root by (uid=0)
Jul  7 19:17:01 methane CRON[27711]: (pam_unix) session closed for user root

```

I tried running ethereal and top exactly when it happend to see what was going on but nothing funny looking showed up,

Any idea as to what is going on here?

---

### Post by dmccarney on 2005-07-07
That is normal. It is just cron running root jobs for you like backing up files etc. It's perfectly normal from what I understand. Read the man for cron and you can probably figure out how to list the cron jobs and see if anything is fishy.

---

### Post by blaylock on 2005-07-08
thanks, i was getting paranoid after i found a bunch of ssh login attempts earlier today.

---

### Post by Ride Jib on 2005-07-08
[QUOTE=blaylock]thanks, i was getting paranoid after i found a bunch of ssh login attempts earlier today.[/QUOTE]

You will get those all the time! It kinda gets under my skin, but I've learned to deal with it, since they have yet to successfully log in. Good thing my passwords aren't in a dictionary!

---

### Post by dmccarney on 2005-07-08
If the automated SSHD Dictionary attacks bother you then follow my [HOWTO](http://www.ubuntuforums.org/forumdisplay.php?f=58) to change you default SSHD port.

Most of these attacks are really dumb and are hard-coded to just attack port 22 (the default SSH port). Change the port and the majority of the attacks are moot.

---

### Post by LordHunter317 on 2005-07-08
Sigh.  Not this again.  The right advice and only worthwhile thing to do is provide strong passwords.  Changing ports will make the attack go away, but if they do attack you on a different port, it won' t stop them from getting in.

---

### Post by Awareness on 2008-07-06
What i want to do is to dissable the user/password kind of login and let only key athentification to log in... i think its the more secure thing to do...
and dont log in the normal user with sudo privileges... but to creat another user....

This is the safer thing to do... well i still didnt succeded in configuring this... but im on it ;)

---

