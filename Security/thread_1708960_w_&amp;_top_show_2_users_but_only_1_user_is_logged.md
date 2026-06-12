---
title: "w &amp; top show 2 users but only 1 user is logged in ... i hope!"
date: 2011-03-17
forum: Security
---

### Post by mowgliee on 2011-03-17
i have 2 servers, web server & mail server. they show 2 users in the summary area when i run w or top commands.  but the actual list of users logged in (using either w or who) shows only 1 user.

ps -ef |grep username only shows my current login as a running sshd process.

so i can find no trace of this other user except in the summary line for w or top.  whats going on?!!

i have no shells or other logins left running elsewhere or abruptly terminated, no gui sessions (these are servers), no tty logins.

do i have another user logged in?  has someone hacked me & covered up most of their trail?  why do these commands show 2 users when everything else points to 1 user?

---

### Post by plucky on 2011-03-17
Every system shows two users.Your user and the /root user.If you log out then there is only the /root user.

> do i have another user logged in? [CENTER]**The /root user**[/CENTER]
> has someone hacked me & covered up most of their trail?  [CENTER]**No**[/CENTER] > why do these commands show 2 users when everything else points to 1 user?  [CENTER]**yourself and the /root user.**[/CENTER]


Good luck

---

### Post by uRock on 2011-03-17
This is normal.```
rabbit@ronnie-desktop:~$ w
 12:00:23 up 2 days,  4:56,  2 users,  load average: 0.17, 0.07, 0.06
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
rabbit   tty7     :0               Tue07    2days  2:30m  1.76s gnome-session
rabbit   pts/0    :0.0             12:00    0.00s  0.46s  0.01s w
rabbit@ronnie-desktop:~$ who
rabbit   tty7         2011-03-15 07:04 (:0)
rabbit   pts/0        2011-03-17 12:00 (:0.0)

```

---

### Post by mowgliee on 2011-03-17
plucky, i also have a file/nfs server & it only shows 1 user, both in the summary area & in the list of users (w or who).  & even the web & mail server showed 1 user in the past, which is why i find it strange they show 2 users now.  why would i have a root user logged in at all times?  that doesnt make sense.

also this is ubuntu; i dont log in as root.  i'm not even sudo -s when i run the commands.  i login as myself & run the commands.  i dont su to root or run them as sudo.  anyway the fact that i have other servers who only show 1 user refutes this explanation.

urock, the difference is when i run w or who, it says 2 users (like yours) but it only lists 1 user (unlike yours).  so it is not normal or typical behaviour.  if my output looked like yours, i wouldnt find it questionable at all.

i do agree its probably not been hacked or anything so dramatic.  but why is it doing this?  why is it saying 2 users but only listing 1?  why does 1 server show 1 user, but the other 2 show 2 users when all 3 only have 1 user logged in?

there must be some way to force the system to list who these 2 users are?

---

### Post by uRock on 2011-03-17
Can you show us the output of these commands, so that we can see what you're looking at?

Moved to Security Discussions sub-forum.

---

### Post by tgm4883 on 2011-03-17
An open terminal counts as a user.

Open up 5 terminals, then run the command. I bet you have 6 users listed

---

### Post by mowgliee on 2011-03-17
urock, sure thing

w results in:
```
 15:52:44 up 14 days,  3:49,  2 users,  load average: 0.03, 0.04, 0.00
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
user1      pts/0    xxx.xxx.xxx.xxx    12:03    0.00s  0.04s  0.03s sshd: user1 [priv] 

```

top results in:
```
top - 15:54:15 up 1 day,  3:50,  2 users,  load average: 0.03, 0.04, 0.00

```

but on another server, w results in:
```
 15:55:55 up 3 days,  3:40,  1 user,  load average: 1.43, 1.50, 1.42
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
user1      pts/0    host.name      12:05    0.00s  1.21s  0.12s sshd: user1 [priv] 

```

and for top:
```
top - 16:04:55 up 3 days,  3:49,  1 user,  load average: 1.25, 1.25, 1.33

```

so whats going on?  the first server shows 2 users but only lists 1.  the second server shows 1 user & lists 1 (as expected).  so it cant be anything to do with root user or other explanations provided here; otherwise both servers would exhibit same results.

---

### Post by mowgliee on 2011-03-17
yes i know every terminal counts as a user.  thats the point.  i have ONE terminal logged in, but its showing 2 users in the summary areas but only listing 1 user.  yet on another similar server, i have ONE terminal logged in & its showing only what i expect.

so if i open up 5 terminals why does it list 6 users vs 5 on 2 of my servers?  all other servers & clients dont exhibit this.  they're all on ubuntu.  there must be some spec or some command to reveal the reason for the discrepency?

---

### Post by uRock on 2011-03-17
Showing 2 users is normal. All 4 of my systems look exactly the same as the screenshot.

Are you logging in locally on the one showing 2 users and remotely on the one showing 1 user?

---

### Post by mowgliee on 2011-03-17
i login remotely via ssh into all systems.

even if its ok to show 2 users, it should still list 2 users in the list of users for w.  yours does.  mine doesnt.  thats my point.  i'm not debating 2 vs 1 users.  my point is my 2 systems in question say 2 users but only list 1.

yet other systems say 1 user & list 1 (which is what i expect & which also makes me think showing 2 users is not so normal).

---

### Post by cariboo on 2011-03-17
I would suggest that you are logged into the one server that shows two users, via the login prompt, while the other server that shows only one user, you are only logged in via ssh.

On my server the last time I physically logged on was when I added another hard drive about a month ago, otherwise it just sits at the login prompt all the time.

---

### Post by mowgliee on 2011-03-17
no i'm not logged in via console to any of them.  i ONLY ssh in.  they're not in the same room & i already checked on the console.  anyway, when i do login on the console, that user instance appears on the results of w & who, as it should.  but there is still that mystery extra user who doesnt appear!

---

### Post by bodhi.zazen on 2011-03-17
See urock's screenshot of top, one user is root (in his case running X) and the other his normal (logged in ) user.

Open a terminal and run top =)

My guess is the other user is one of your services (apache, samba, nfs ?) or something running as root (as X was for the rock).

---

### Post by mowgliee on 2011-03-17
its weird how i have to keep repeating this.

yes go see urock's screenshot.  that explains the dilemma!  both his user instances appear in the list beneath the summary line.  now go see my posts lower on the page.  only 1 of my users appears on the same list yet i have 2 users in the summary line just like urock.

figuring this out might be rocket science (i hope not), but is it really that hard to see that my systems are not behaving like urock's, which is the expected behaviour?

---

### Post by celsdogg on 2011-03-18
> **mowgliee said:**
> its weird how i have to keep repeating this.

yes go see urock's screenshot.  that explains the dilemma!  both his user instances appear in the list beneath the summary line.  now go see my posts lower on the page.  only 1 of my users appears on the same list yet i have 2 users in the summary line just like urock.

figuring this out might be rocket science (i hope not), but is it really that hard to see that my systems are not behaving like urock's, which is the expected behaviour?

yes, urock correctly shows two because one is X and then he also has that terminal window which he posted.

i am curious as to an explanation to this as well.

EDIT: maybe you can post the output of "netstat -paunt" to see what connection, if any, the system has. also, what does "finger" show?

---

### Post by celsdogg on 2011-03-18
so i just noticed the following trying to figure this out. i had logged into tty5 (ctrl + alt + f5) and logged out. after i logged out, i looked at top, it showed three users. i looked at w and who and it showed 2 users (expected for me as it is X and tilda (terminal)). but finger showed three, with an asterisks next to tty5, the tty i logged out of.

```
top - 09:11:43 up 55 min,  3 users,  load average: 1.25, 0.83, 0.62
Tasks: 200 total,   1 running, 199 sleeping,   0 stopped,   0 zombie

celsdogg@Sabine:~$ finger
Login     Name              Tty      Idle  Login Time   Office     Office Phone
celsdogg  <removed>  *tty5        8  Mar 18 09:03
celsdogg  <removed>   tty7       55  Mar 18 08:17 (:0)
celsdogg  <removed>   pts/0          Mar 18 08:17 (:0.0)

celsdogg@Sabine:~$ w
 09:11:52 up 55 min,  3 users,  load average: 1.28, 0.85, 0.63
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
celsdogg tty7     :0               08:17   55:37   2:53   0.21s gnome-session
celsdogg pts/0    :0.0             08:17    0.00s  0.23s  0.02s w

celsdogg@Sabine:~$ who
celsdogg tty7         2011-03-18 08:17 (:0)
celsdogg pts/0        2011-03-18 08:17 (:0.0)
celsdogg@Sabine:~$
celsdogg@Sabine:~$ 
```

here, tty7 is X, and pts/0 is tilda. I am wondering if top, like finger, shows logged off users for a certain amount of time. This is news to me if it does.

EDIT: from the man page for finger: (as a ``*'' after the terminal name if write permission is denied)

tty5 is currently logged out, so i guess write permission would be denied in this instance. . .

still researching. . .


> **celsdogg said:**
> yes, urock correctly shows two because one is X and then he also has that terminal window which he posted.

i am curious as to an explanation to this as well.

EDIT: maybe you can post the output of "netstat -paunt" to see what connection, if any, the system has. also, what does "finger" show?

---

### Post by uRock on 2011-03-18
> **bodhi.zazen said:**
> See urock's screenshot of top, one user is root (in his case running X) and the other his normal (logged in ) user.

Open a terminal and run top =)

My guess is the other user is one of your services (apache, samba, nfs ?) or something running as root (as X was for the rock).
I see what you are saying here. I don't have any of those types of services to check and see.
> **mowgliee said:**
> its weird how i have to keep repeating this.

yes go see urock's screenshot.  that explains the dilemma!  both his user instances appear in the list beneath the summary line.  now go see my posts lower on the page.  only 1 of my users appears on the same list yet i have 2 users in the summary line just like urock.

figuring this out might be rocket science (i hope not), but is it really that hard to see that my systems are not behaving like urock's, which is the expected behaviour?
This is uncalled for. Have you researched what bodhi.zazen is was talking about?

---

### Post by mowgliee on 2011-03-18
the netstat cmd shows 1 ssh connection only, my remote login session, as expected.

but finger shows 2, 1 with an * just like celsdogg has.

no clue what that means.

> **celsdogg said:**
> 

EDIT: maybe you can post the output of "netstat -paunt" to see what connection, if any, the system has. also, what does "finger" show?

---

### Post by mowgliee on 2011-03-18
celsdogg, you have exactly my situation!  well minus 1 overall user.  my w/who/top all show conflicting # of users just like yours does.  and my finger shows a tty1 user w/ an * beside it.

i rebooted 1 of the problem servers & it only shows 1 user now.  so i guess it all comes down to this: w/top show old logins in some latent manner?  like finger.  but for how long?  b/c i've had these servers up for weeks at a time & they would still show 1 extra user.  its almost as though the old login just never went away from memory or whatever (i'm talking about memory metaphorically, not in a ddram sense).

what use would such a lingering effect serve?

---

### Post by celsdogg on 2011-03-18
Mine still shows the one with the asterisks this morning. I am sure that we are just unaware of some behavior linux has. i still dont know, but i feel well enough that it is not something to worry about.

if you do "ps -ft <tty or pts>" it shows nothing is running except for getty, which is normal. still wondering. . .

---

### Post by celsdogg on 2011-03-18
looks like this has been going on for awhile:

[http://www.linuxquestions.org/questions/slackware-14/finger-shows-logged-in-to-console-tty1-even-after-logging-out-521862/](http://www.linuxquestions.org/questions/slackware-14/finger-shows-logged-in-to-console-tty1-even-after-logging-out-521862/)

---

### Post by bodhi.zazen on 2011-03-18
> **mowgliee said:**
> its weird how i have to keep repeating this.

yes go see urock's screenshot.  that explains the dilemma!  both his user instances appear in the list beneath the summary line.  now go see my posts lower on the page.  only 1 of my users appears on the same list yet i have 2 users in the summary line just like urock.

I can not help you further without a screenshot of the output of top.

You have posted partial outputs / insufficient information.

Please post a screenshot of top running in a graphical terminal.

---

