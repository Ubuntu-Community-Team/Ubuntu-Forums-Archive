---
title: "Suspicious line in my crontab"
date: 2010-02-05
forum: Security
---

### Post by sdetheridge on 2010-02-05
Hi,

I just logged on to my box, and went to add something to my cron. (First time I've done this on this machine)

I noticed that it contained one line:
```
* * * * * /tmp/.mc-root/update > /dev/null 2>&1
```I don't remember putting this line there.

The directory /tmp/.mc-root does not exist. Neither chkrootkit or rkhunter show anything suspicious. I can't see any processes running that I don't recognise.

Google search turns up one result (in German) that looks suspicious... Something about IRC traffic. But there's no IRC traffic coming from my machine either.

Any ideas?

---

### Post by Sarmacid on 2010-02-05
That does seem very supicious, I have nothing on either my user's crontab or root's crontab. Just to be sure I'd reinstall Ubuntu.

---

### Post by BkkBonanza on 2010-02-05
When you checked for that directory you did check for hidden files right?

ls -lsa

Just wanted to make sure. Google turned up one hit in Hungarian about that file but I couldn't make much sense of the translation. Seemed related to rkhunter but I wouldn't say that's convincing it's safe. 

There is a way to do a full package signature check to ensure your system files are originals. I couldn't find a link to the process though - maybe someone else has a link. You would want to use a live cd to verify so that any potential rootkit won't cover up.

---

### Post by The Cog on 2010-02-05
I agree with both answers above. I would look round /tmp/.mc-root with hiddeb file viewing enabled to see if I coulf find enything interesting, then re-format and reinstall Ubuntu to make sure I'd got rid of whatever the intruder did. 

Also, you should worry about how the intruder got in. If you reinstall identically, he can do it again.

---

### Post by msrinath80 on 2010-02-05
> **sdetheridge said:**
> Hi,

I just logged on to my box, and went to add something to my cron. (First time I've done this on this machine)

I noticed that it contained one line:
```
* * * * * /tmp/.mc-root/update > /dev/null 2>&1
```I don't remember putting this line there.

The directory /tmp/.mc-root does not exist. Neither chkrootkit or rkhunter show anything suspicious. I can't see any processes running that I don't recognise.

Google search turns up one result (in German) that looks suspicious... Something about IRC traffic. But there's no IRC traffic coming from my machine either.

Any ideas?

Seems to have been reported elsewhere[1] too. How exactly did this happen?

[1] [http://translate.google.ca/translate?hl=en&sl=hu&u=http://budacsik.blog.hu/2008/11/23/backdoor_bindtty&ei=y6xsS-enLoaoswPF1eGxDQ&sa=X&oi=translate&ct=result&resnum=3&ved=0CA8Q7gEwAg&prev=/search%3Fq%3D/tmp/.mc-root/update%26hl%3Den%26sa%3DG](http://translate.google.ca/translate?hl=en&sl=hu&u=http://budacsik.blog.hu/2008/11/23/backdoor_bindtty&ei=y6xsS-enLoaoswPF1eGxDQ&sa=X&oi=translate&ct=result&resnum=3&ved=0CA8Q7gEwAg&prev=/search%3Fq%3D/tmp/.mc-root/update%26hl%3Den%26sa%3DG)

---

### Post by wirelessmonkey on 2010-02-05
A quick google shows something bad from the samba lists....

[http://lists.samba.org/archive/linux/2009-June/023679.html]("http://lists.samba.org/archive/linux/2009-June/023679.html")

---

