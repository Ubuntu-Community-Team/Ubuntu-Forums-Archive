---
title: "Log in with a domain user account"
date: 2008-10-15
forum: Security
---

### Post by bsautner on 2008-10-15
Hello

I just built a very nice samba Domain Controller using ubuntu 8 server and successfully connected two Ubuntu 8 workstations to it. That is, got a positive response when running these commands:

sudo net rpc getsid
sudo net rpc join -S MYDOMAIN -U Administrator

I'm stumped on something kind of silly. there is a domain user, let's say named tom all, set up on the DC. When i'm at the ubuntu logon screen i can't seem to log in as tom. The best analogy i can give for what i'm trying to do comes from, i'm sorry, windows. When i add an XP workstation to a domain the logon screen has the option to log in to the local machine or the domain. I can't seem to log into the client as a domain user. I've tried tom@MYDOMAIN etc - nothing works.

---

### Post by cdenley on 2008-10-15
Samba joining a domain has nothing to do with system authentication. You need to configure winbind with pam modules and stuff. This should point you in the right direction, even though it is for AD domains.
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto#Join%20AD%20domain](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto#Join%20AD%20domain)

Maybe likewise can do this, I never tried it.
[https://help.ubuntu.com/community/LikewiseOpen](https://help.ubuntu.com/community/LikewiseOpen)

---

### Post by Gamma746 on 2008-10-15
Can you try logging in as ```
MYDOMAIN/tom
```

Also, read [http://gentoo-wiki.com/Gentoo_%2B_Active_Directory_made_EASY](http://gentoo-wiki.com/Gentoo_%2B_Active_Directory_made_EASY).

---

### Post by UsTBo8xo on 2008-10-18
**[[color=red]Buy Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[[color=red]Sell Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[size=3][color=red]Make money online,now![/color][/size]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---

### Post by bsautner on 2008-10-20
thanks for the reply guys - i think you got what i'm trying to do. I need to log into workstations with a domain account and run with that accounts privliges. Right now i can do things with the domain accounts i create in ssh sessions etc but i need to log in interactivly at the ubuntu log in screen as a domain user. MYDOMAIN/tom does not work right now which makes sense to me since i haven't given the ubuntu workstation the info it needs to validate the user - adding the machine to the domain isn't enought.

so - i'm futsing around with likewise open and will post my results here, right now i'm fighting with some blocked ports likewise needs.

- happily refusing to build a Windows 2008 DC server (a vista based server good god)

---

### Post by bsautner on 2008-11-06
For thos 250+ people who hit this thread, an update.

My goal is to have ubuntu workstations that i can log into as a domain user from the log in screen and work as that user, accessing network resources etc. I've made some progress and built a samba DC, also i found that you need to build an openLDAP Server with DNS, configure and install Kerberos etc.

in windows, i'd build a DC - add xp clients to the Domain, grant domain users login rights to the xp clients and log in...

No real luck getting this working... a lot of contradicting tutorials -  I'm getting the impression that ubuntu and linux in general just isn't ready for this but i find that hard to believe. If anyone know how to get the above going i'd appriciate a link.

---

### Post by dschutt on 2008-11-07
I've been attempting to do the same thing, but unfortunately no success. I have a Freebsd based Samba server providing NT style logons. Windows workstations work fine, and I've use the winbind package and pam_winbind with other Linux distributions with not too many problems.

I wanted to try Ubuntu 8.10, and got almost there, but I've been stumped by a problem where a session is successfully opened, but then immediately closed with no indication in the logs of why.

Unfortunately, I'm running out of time that I can spend on this, which is a bummer as I was looking forward to using Ubuntu here.

---

### Post by dschutt on 2008-11-07
I can't believe it, I found my problem.

Missing some lines in smb.conf, specifically

    template shell = /bin/bash

which might explain things, i.e. no shell, no session.

also missing were

     winbind enum users = yes
     winbind enum groups = yes

which explains why getent wasn't returning suers and groups.

If I get this mess debugged completely I'll post my configs.

---

