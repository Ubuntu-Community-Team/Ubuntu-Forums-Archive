---
title: "Problems with jackd???"
date: 2012-07-28
forum: Ubuntu Studio
---

### Post by charliebp on 2012-07-28
Hi I am an reasonable experianced linux user. I usually manage to google most of my problems but this one has drawn a blank.  I am trying to set up a little music recording thing to practise my guitar and keyboard on and record it on the computer but it does not seem to want to play ball.  rakarrack or rosegarden etc it say's jackd is not working. My keyboard is conected with a midi to usb cable and my electric guitar is connected with a guitar link usb interface. Both new. When I try to start jack control it displays this message
 p, li { white-space: pre-wrap; }  "Could not connect to JACK server as client."
 The message window log will not copy and paste sorry but it said I was unable to run realtime scheduling and told me to check my /etc/security/limits.conf for the following lines
@audio - rtprio 100
@audio - nice -10
I have checked and these lines were not there so I edited the file and added them. Then restarted but this error still occurred. It also said I did not appear to have a sane system configuration. and would likely get x runs.
Sorry this is a long one but linux looks really good for recording and playing music on and it would be nice to fix the bug/error.
Many Thanks
Gareth:guitar:

---

### Post by jejeman on 2012-07-28
Are you in audio group?

---

### Post by charliebp on 2012-07-28
> **jejeman said:**
> Are you in audio group?

To be honest I'm not sure, I assume probably not if i have not heard of it.

---

### Post by jejeman on 2012-07-28
I assume that you didn't install ubuntu studio but Ubuntu, since your limits.conf wasn't set.

Check with this
```
groups
```
if you don't see audio group listed, add your username to it.

---

### Post by sgx on 2012-07-28
rt 'priority' should work at 99 or lower, never used it at
100...and the priority
shown in qjackctl is a ratio of that, maximum 89.

I can use lower settings, like 70 etc in qjackctl, but use 89, for luck, since I don't use the computer beyond recording/browsing.

[http://jackaudio.org/linux_rt_config](http://jackaudio.org/linux_rt_config)

good info

Cheers

---

### Post by UndercoverLawyer on 2012-08-16
Oops, misread your post, disregard my feeble reply.

---

