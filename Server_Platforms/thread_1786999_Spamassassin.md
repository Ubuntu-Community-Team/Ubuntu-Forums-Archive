---
title: "Spamassassin"
date: 2011-06-20
forum: Server Platforms
---

### Post by Jay89 on 2011-06-20
Hello,
   I have amavisd-new configured with spamassassin and clamav. Is there a way to test the configuration to make sure it works? I tried forwarding spam and spamassassin did not mark it as such. I would like to know if there is a way from the command-line to see if it will work. If not, then any way to test it would be appreciated.


Thanks!

---

### Post by ruffEdgz on 2011-06-20
I know when I played with Spamassassin awhile back, the original email would show the 'score' spamassassin gave it. The spamassassin server would then see if that score is high enough to drop it or send it along.

I would take a look at these two pages I found about your dilemma:

[http://wiki.apache.org/spamassassin/HowScoresAreAssigned](http://wiki.apache.org/spamassassin/HowScoresAreAssigned)
[http://spamassassin.apache.org/tests_3_3_x.html](http://spamassassin.apache.org/tests_3_3_x.html)

Cheers!

---

### Post by falko on 2011-06-21
First, you can run ```
spamassassin --lint
``` to check if the syntax is right (if the command just returns to the command line, everything is fine).

If you use SpamAssassin in conjunction with amavisd, you can take a look at your mail log to check out what is happening.

---

### Post by Jay89 on 2011-06-21
Thank you for the replies. I looked in syslog and I noticed an error from clamav. 

[B]run_av error: Too many retries to talk to /var/run/clamav/clamd.ctl (Can't connect to UNIX socket /var/run/clamav/clamd.ctl: No such file or directory) at (eval 115) line 373.
[/B]
Not sure what that means.. I looked in that directory but that file isn't there. Do *I* have to create in manually? What is that for? I also checked your command falko and it said my syntax was fine for spamassassin. 

Thanks!

---

### Post by Jay89 on 2011-06-21
I also checked for and couldn't find clamav.conf. (**grep -R clamav *** in /etc)

---

### Post by Jay89 on 2011-06-21
Found it. Apparently it's now called clamd.conf.

---

### Post by Jay89 on 2011-06-21
Resolved the clamav issue, had to re-install the clamav-daemon

---

