---
title: "SU Session allowed for a Desktop User Account"
date: 2011-09-12
forum: Security
---

### Post by SparTacux on 2011-09-12
I was going through some of my Auth log files and found pam_unix allowing su sessions  for a standard desktop user. Is this normal or should I treat it as suspicious?


Aug 15 09:17:01 Firestorm CRON[1556]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 15 09:17:01 Firestorm CRON[1556]: pam_unix(cron:session): session closed for user root
Aug 15 09:18:16 Firestorm su[1659]: Successful su for spartacux by root
Aug 15 09:18:16 Firestorm su[1659]: + ??? root:spartacux
Aug 15 09:18:16 Firestorm su[1659]: pam_unix(su:session): session opened for user spartacux by (uid=0)
Aug 15 09:18:16 Firestorm su[1659]: pam_unix(su:session): session closed for user spartacux
Aug 15 09:18:16 Firestorm su[1674]: Successful su for spartacux by root
Aug 15 09:18:16 Firestorm su[1674]: + ??? root:spartacux
Aug 15 09:18:16 Firestorm su[1674]: pam_unix(su:session): session opened for user spartacux by (uid=0)
Aug 15 09:18:16 Firestorm su[1674]: pam_unix(su:session): session closed for user spartacux
Aug 15 09:18:16 Firestorm su[1698]: Successful su for spartacux by root
Aug 15 09:18:16 Firestorm su[1698]: + ??? root:spartacux
Aug 15 09:18:16 Firestorm su[1698]: pam_unix(su:session): session opened for user spartacux by (uid=0)
Aug 15 09:18:16 Firestorm su[1698]: pam_unix(su:session): session closed for user spartacux
Aug 15 09:18:16 Firestorm su[1719]: Successful su for spartacux by root
Aug 15 09:18:16 Firestorm su[1719]: + ??? root:spartacux
Aug 15 09:18:16 Firestorm su[1719]: pam_unix(su:session): session opened for user spartacux by (uid=0)
Aug 15 09:18:17 Firestorm su[1719]: pam_unix(su:session): session closed for user spartacux
Aug 15 09:18:35 Firestorm su[2097]: Successful su for spartacux by root
Aug 15 09:18:35 Firestorm su[2097]: + ??? root:spartacux
Aug 15 09:18:35 Firestorm su[2097]: pam_unix(su:session): session opened for user spartacux by (uid=0)
Aug 15 09:18:35 Firestorm su[2097]: pam_unix(su:session): session closed for user spartacux
Aug 15 09:18:35 Firestorm su[2112]: Successful su for spartacux by root
Aug 15 09:18:35 Firestorm su[2112]: + ??? root:spartacux
Aug 15 09:18:35 Firestorm su[2112]: pam_unix(su:session): session opened for user spartacux by (uid=0)
Aug 15 09:18:35 Firestorm su[2112]: pam_unix(su:session): session closed for user spartacux
Aug 15 09:18:35 Firestorm su[2133]: Successful su for spartacux by root
Aug 15 09:18:35 Firestorm su[2133]: + ??? root:spartacux
Aug 15 09:18:35 Firestorm su[2133]: pam_unix(su:session): session opened for user spartacux by (uid=0)
Aug 15 09:18:35 Firestorm su[2133]: pam_unix(su:session): session closed for user spartacux
Aug 15 09:18:35 Firestorm su[2155]: Successful su for spartacux by root
Aug 15 09:18:35 Firestorm su[2155]: + ??? root:spartacux
Aug 15 09:18:35 Firestorm su[2155]: pam_unix(su:session): session opened for user spartacux by (uid=0)
Aug 15 09:18:35 Firestorm su[2155]: pam_unix(su:session): session closed for user spartacux
Aug 15 09:18:49 Firestorm gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Aug 15 09:18:57 Firestorm gdm-session-worker[1149]: pam_unix(gdm:session): session closed for user spartacux

---

### Post by SparTacux on 2011-09-13
I thought it might be something to do with the screensaver activating as logs mention this towards the bottom. I am unable to reproduce this su session. This user should  be unable to type sudo & cannot do so. Anyone?

---

### Post by CharlesA on 2011-09-13
su and sudo are two different things. Even if a user is unable to use sudo, they can still su (Switch User) to a different user, as long as they know that user's password.

---

### Post by SparTacux on 2011-09-13
I'm a pro you know ;-)
ok - got that - I don't use the command line much 

DESCRIPTION
       The su command is used to become another user during a login session.
       Invoked without a username, su defaults to becoming the superuser. The
       optional argument - may be used to provide an environment similar to
       what the user would expect had the user logged in directly.


Can't ever remember doing that - bash history doesn't show that I typed a command either. Looking at the logs the root user actually did the switch to spartacux?

I played around with su and managed to change users in the terminal and had a look at the corresponding changes in the auth log. I was unable to log on as root and had a password failure.
Any chance you can explain what is likely to have happened here?

---

### Post by CharlesA on 2011-09-13
The root account is locked by default so you cannot su to it.

I checked my auth log on my Ubuntu box and I didn't see anything like that in the auth log - most of the stuff I had were related to sudo.

---

### Post by haqking on 2011-09-13
> **SparTacux said:**
> I'm a pro you know ;-)
ok - got that - I don't use the command line much 

DESCRIPTION
       The su command is used to become another user during a login session.
       Invoked without a username, su defaults to becoming the superuser. The
       optional argument - may be used to provide an environment similar to
       what the user would expect had the user logged in directly.


Can't ever remember doing that - bash history doesn't show that I typed a command either. Looking at the logs the root user actually did the switch to spartacux?

I played around with su and managed to change users in the terminal and had a look at the corresponding changes in the auth log. I was unable to log on as root and had a password failure.
Any chance you can explain what is likely to have happened here?


your entries are normal.   Root has to start or run a given service and then pass on control to the user which in this case is spartacux (such as a cron job)

and as CharlesA states, root acount is locked by default which is why you cant login as root, sudo is the preferred method for a user to elevate a privelege.

---

### Post by SparTacux on 2011-09-16
I'm glad to see it's normal

I've used sudo a few times for configuring files and launching programs , etc. 
I guess the more I look at the logs the more I'll become familiar with them. They are cryptic at a first glance but they do get easier. I wonder what they are like if I drop a tab of Acid ;-)

Cheers for your help

---

