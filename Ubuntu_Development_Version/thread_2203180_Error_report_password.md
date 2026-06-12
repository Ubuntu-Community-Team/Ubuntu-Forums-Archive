---
title: "Error report password?"
date: 2014-02-02
forum: Ubuntu Development Version
---

### Post by mips on 2014-02-02
A week ago I installed 14.04 64-bit alongside  a fresh windows7 install on someone's laptop for them in case windows ever dies or gives them issues again (hence the reinstall). Told them it's there if in case things go wrong and they can play with it, also warned them it's not stable yet but they can keep upgrading it and in April some time it will be stable.

Well this person is now using Ubuntu 95% of the time, everything is going really well except for one small annoyance, on reboot some times he gets a popup saying Ubuntu encountered an problem and needs to send off a error report (it does not give specifics about the error and everything works fine) and then promptly asks for a password which is not the user password, what password needs to be entered to send off the error report?

Does he need to sign up to launchpad, ubuntu one or something like that?

---

### Post by zika on 2014-02-02
As lazy to write as I am, I'll point You to this answer To Your question: [http://askubuntu.com/a/150205](http://askubuntu.com/a/150205) 
As I hope that first part is not what is happening at Your friend's place, second part gives the right answer: yes, he needs a Lauchpad account...
I will not suggest another possible &#8222;solution&#8220; i.e. turning reporting off...

---

### Post by mips on 2014-02-02
> **zika said:**
> 
As I hope that first part is not what is happening at Your friend's place, second part gives the right answer: yes, he needs a Lauchpad account...
I will not suggest another possible „solution“ i.e. turning reporting off...

As far as I understand it if the user account as admin rights via sudo his password should work. I think launchpad account is only needed if you want to manually file bugs.

I know how to disable apport but I would rather the devs get feedback.

This is what he is getting,

[IMG]http://i.stack.imgur.com/3kH8Z.png[/IMG]

[IMG]http://i.stack.imgur.com/h6rDO.png[/IMG]

Now he has admin privileges (via sudo) so my understanding is his password should be enough?

---

### Post by zika on 2014-02-02
> **mips said:**
> As far as I understand it if the user account as admin rights via sudo his password should work. I think launchpad account is only needed if you want to manually file bugs.

I know how to disable apport but I would rather the devs get feedback.

This is what he is getting,

[IMG]http://i.stack.imgur.com/3kH8Z.png[/IMG]

[IMG]http://i.stack.imgur.com/h6rDO.png[/IMG]

Now he has admin privileges (via sudo) so my understanding is his password should be enough?Did You try?

---

### Post by mips on 2014-02-02
> **zika said:**
> Did You try?

Try what?

---

### Post by zika on 2014-02-02
> **mips said:**
> Try what?Entering password?

---

### Post by mips on 2014-02-02
> **zika said:**
> Entering password?

Yes, as per my original post it does not work.

---

### Post by bapoumba on 2014-02-02
You can have look at /var/crash/ if there is something to worry about or if it is an old crash that still gets reported. If there is nothing alarming, you can remove everything that is in /var/crash/, the popup should go away.

---

### Post by grahammechanical on 2014-02-02
Some of us have reported failures by Apport not working as it should. I cannot find the original thread but here is a recent posting.

[http://ubuntuforums.org/showthread.php?t=2202287](http://ubuntuforums.org/showthread.php?t=2202287)

System crashes can be common place. I find that I can cancel the crash report and carrying on using the system without any problems. We usually need to authorise Apport to collect logs if the logs may contain user personal data and our user password should be enough for that. To get as far as reporting a bug in Launchpad we do need a Launchpad account. I am not sure if having a Ubuntu One Single Sign On account would do the job.

Did you set this user up with a Ubuntu One account at installation time. Early in the development cycle I had problems with the installer not being able to accept that I already was a registered Ubuntu One user. Perhaps this is where the problems occurs.

Regards.

---

### Post by zika on 2014-02-02
> **mips said:**
> Yes, as per my original post it does not work.Mea culpa, it seems that I did not get that clearly...

---

### Post by mips on 2014-02-02
> **grahammechanical said:**
> Some of us have reported failures by Apport not working as it should. I cannot find the original thread but here is a recent posting.

[http://ubuntuforums.org/showthread.php?t=2202287](http://ubuntuforums.org/showthread.php?t=2202287)

System crashes can be common place. I find that I can cancel the crash report and carrying on using the system without any problems. We usually need to authorise Apport to collect logs if the logs may contain user personal data and our user password should be enough for that. To get as far as reporting a bug in Launchpad we do need a Launchpad account. I am not sure if having a Ubuntu One Single Sign On account would do the job.

Did you set this user up with a Ubuntu One account at installation time. Early in the development cycle I had problems with the installer not being able to accept that I already was a registered Ubuntu One user. Perhaps this is where the problems occurs.

Regards.

The system works just fine if you ignore the error report thingy so it's not serious, just an annoyance.
I did not set the user up with an ubuntu one account. Thing is I can't see it helping as there is no request for login details of any sorts except for asking for a password.

> **zika said:**
> Mea culpa, it seems that I did not get that clearly...

No problemo ;)


I think I might just tell the guy how to disable apport to get rid of the popup, he's not worried about it but it's one of those little niggles. He's really happy with Ubuntu otherwise.

---

### Post by mc4man on 2014-02-02
There is no need for a launchpad account unless one wants to actually follow thru with reporting a bug (crashers) & that will only come up once apport has opened launchpad in your browser.
What your freind is showing is a pre login crash, that's why it's  root owned & requires auth to proceed

The orig. install accounts password should work fine to auth., maybe some miscommunication?
(there is no admin group anymore, it's now sudo, look in /etc/group

They could clear all .crashes, ect & see if it stops popping up - 
```
sudo rm /var/crash/*.*
```

---

### Post by mips on 2014-02-02
> **mc4man said:**
> 
The orig. install accounts password should work fine to auth., maybe some miscommunication?
(there is no admin group anymore, it's now sudo, look in /etc/group


When you say original install accounts password do you mean the password of the username setup during install? If 'yes' then it does not work which is what's bugging me. My understanding is that it should work.

---

### Post by mc4man on 2014-02-02
> **mips said:**
> When you say original install accounts password do you mean the password of the username setup during install? If 'yes' then it does not work which is what's bugging me. My understanding is that it should work.

Yes, it *should*..
I have 2 14.04 installs, one quite old, one from today. Atm I'm not getting any pre-login crashers so can't say for sure that there isn't something broken in the current apport in this regard.
( I may have a way to create a root owned crash so will try & see what happens.

---

### Post by mc4man on 2014-02-02
Gave it a test (the repo version of mpv will crash when trying to use an --ao of sdl, so I replaced mine with it &  ran mpv as root...
Didn't see any issue, screen 1 is the auth dialog, after entering my password it was accepted & produced screen 2

(what session is your friend using, above was from an ubuntu session (unity

---

### Post by mips on 2014-02-02
> **mc4man said:**
> 
(what session is your friend using, above was from an ubuntu session (unity

Bog standard Unity as it comes with Ubuntu, no changes.

---

