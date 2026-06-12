---
title: "How to know whether my IP is attacked ??"
date: 2009-09-08
forum: Security
---

### Post by anirudhpalla on 2009-09-08
hello mates...
can any one say me...how to know whether my IP is attacked by someone...??

---

### Post by cariboo on 2009-09-08
If you are connecting through a router, check the router logs, if you connected directly, check /var/log/auth.log, you will see many attempts to guess your ssh password.

---

### Post by anirudhpalla on 2009-09-08
i didnt get u mate... how i should i check it..??
im connected directly...
whats the code...used to check the logs and what things in logs show me that im infected??

anyways...thanks for ur quick response

---

### Post by Sporkman on 2009-09-08
> **anirudhpalla said:**
> i didnt get u mate... how i should i check it..??
im connected directly...
whats the code...used to check the logs and what things in logs show me that im infected??

anyways...thanks for ur quick response

Try this:

grep user /var/log/auth.log

If you see anybody trying to connect other than yourself, then someone's trying to break in.

---

### Post by pbulteel on 2009-09-08
And make sure that if you have users with passwords, that those passwords are strong. i.e combination of letters (uppercase & lowercase), numbers, even punctuation marks. 

You may want to run something like "logwatch" (apt-get install logwatch) which will send you an email every day of interesting events. Note that this happens once a day, so you won't know if people are attempting the log in right now... for that "tail -f /var/log/auth.log" would let you watch the log as people log in and out.

Also, run "last" which will tell you who has logged in and when they logged out. "sudo lastb" will give you the bad login attempts.


-P

---

### Post by bodhi.zazen on 2009-09-08
> **anirudhpalla said:**
> hello mates...
can any one say me...how to know whether my IP is attacked by someone...??

What do you mean "Attacked" ?

If you are connected to the internet you are under almost constant "attack".

**[B]Sticky:**[/B] 			                          			 			[Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812")

**[B]Sticky:**[/B] 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Intrusion Detection]("http://ubuntuforums.org/showthread.php?t=919472")

---

