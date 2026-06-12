---
title: "Chkrootkit warning"
date: 2012-05-15
forum: Security
---

### Post by Maintech on 2012-05-15
When I run chkrootkit in 12.04 I get a warning I have never seen before. It is located in /var/run/utmp.
> Checking `chkutmp'...                                        The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! root         1198 tty7   /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none


Is this a new type of security issue or a false positive?:confused:

---

### Post by Enigmapond on 2012-05-15
That is simply a false positive. That's all you will ever get a sgetting a rootkit is highly unlikely to happen.....relax/play...this is Linux. ):P

---

### Post by QIII on 2012-05-15
Don't be so cavalier about security.

Rootkits can and do appear in Linux environments.  It is particularly possible if you have been "socially engineered" into installing something malicious when using elevated privileges.  An untrusted source or "something cool I found on the internet" can both make you vulnerable.

Assuming that we are somehow "safe" from the dangers of the world by virtue of using Linux is foolhardy.  We should be every bit as vigilant as Windows users.  Linux invulnerability is a myth.

Use chrootkit.  If you get a hit, ask or google.  If it's a false positive, better safe than sorry.

---

### Post by Enigmapond on 2012-05-15
> **QIII said:**
> Don't be so cavalier about security.

Rootkits can and do appear in Linux environments.  It is particularly possible if you have been "socially engineered" into installing something malicious when using elevated privileges.  An untrusted source or "something cool I found on the internet" can both make you vulnerable.

Assuming that we are somehow "safe" from the dangers of the world by virtue of using Linux is foolhardy.  We should be every bit as vigilant as Windows users.  Linux invulnerability is a myth.

Use chrootkit.  If you get a hit, ask or google.  If it's a false positive, better safe than sorry.

I wasn't being cavalier,I was speaking from experience. In 15yrs of working with Unix/Linux and working with people working on Linux, niether i or anyone else I know or work with has ever gotten a virus or rootkit. While I know it's not impossible, I merely stated it was very unlikely.

---

### Post by QIII on 2012-05-15
Nobody you know does not mean nobody.  

It can and does happen.  Hence, a tool to check for it.

I've been at this for 35 years going back to Unix.  I've learned a hard lesson or two.

---

### Post by unspawn on 2012-05-16
Regardless of intent a lot of people on everything from fora to mailing lists think they should decide for others what is good and what is not. Instead, and in keeping with the Fish vs Fishing Rod thingie, it would be better to say that if this is a FP then it is often caused by processes, commonly associated with logging in, that haven't written to utmp *yet*. 

Those practicing forensics at whatever level know evidence gathering should be step one in case of suspicion and those even fleetingly familiar with security know it requires a multi-layered approach, meaning not just running a single post-incident auditing tool.

---

### Post by MattressVon on 2012-05-28
Hey all,

I got these four replies with rkhunter and chkroot:

/usr/bin/unhide.rb                                       [ Warning ]
Checking for passwd file changes                         [ Warning ]
Checking for group file changes                          [ Warning ]
Checking for hidden files and directories                [ Warning ]

Anyone know what I should do to deal with these? Does this mean I have a rootkit installed? 

Thanks

---

### Post by Ms. Daisy on 2012-05-28
> **MattressVon said:**
> Hey all,

I got these four replies with rkhunter and chkroot:

/usr/bin/unhide.rb                                       [ Warning ]
Checking for passwd file changes                         [ Warning ]
Checking for group file changes                          [ Warning ]
Checking for hidden files and directories                [ Warning ]

Anyone know what I should do to deal with these? Does this mean I have a rootkit installed? 

ThanksIf you're going to use rkhunter & chkroot, then you need to learn how to understand the warnings.  Check the documentation as you will get lots of false positives. Google is probably your best bet- google the warnings you get and you'll find lots of information out there.

As for a few of the warnings you listed, I found them in this thread which indicated they're nothing to worry about:

[http://ubuntuforums.org/showthread.php?t=1928115&page=2](http://ubuntuforums.org/showthread.php?t=1928115&page=2)

---

### Post by kleenex on 2013-01-23
Hi, I'm sorry, that I'm writing in this topic, but I think my *problem* seems to be similar. Yesterday I launched chkrootkit to check some things. Everything seems to be fine, but I'm wonder on this: 
```
Checking `chkutmp'...  The tty of the following user process(es) were not found in /var/run/utmp !
! RUID          PID TTY    CMD 
! kleenex        3816 pts/0  bash 
! kleenex        5146 pts/0  sudo chkrootkit 
! root         5147 pts/0  /bin/sh /usr/sbin/chkrootkit 
! root         5782 pts/0  ./chkutmp 
! root         5784 pts/0  ps axk tty,ruser,args -o tty,pid,ruser,args 
! root         5783 pts/0  sh -c ps axk "tty,ruser,args" -o "tty,pid,ruser,args"
```Is it normal? There is so many informations about chkrootkit and e.g. chkutmp on the network and I'm so confused and amazed. Whether it is a record of what actions were taken by chkrootkit? (./chktump etc.) Or it is something else? In the [COLOR=Green]utmp[/COLOR] man page, we could read, that *The utmp file allows one to discover information about **who** is currently using the system.* etc. Okay. That's sounds nice. As we can see, in my case, there is only one (me; kleenex) and root users. Next entries like [COLOR=Navy]PID, CMD [COLOR=Black]- for  me - seems to be related with chkrootkit's [COLOR=Green]Checking `chkutmp'...[/COLOR][/COLOR] [COLOR=Black]scan.[/COLOR]
[/COLOR]
Generally, Could anybody tell me what's going on?

---

### Post by uRock on 2013-01-23
Thread is almost a year old and inactive. Please start a new thread on your topic.

Thread Closed.

---

