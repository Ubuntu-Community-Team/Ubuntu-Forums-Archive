---
title: "Do you run Windows as Administrator?"
date: 2006-11-01
forum: Windows
---

### Post by Ubunted on 2006-11-01
I thought it would be interesting to see what kind of replies I would get asking this in a forum where people understand the value of limited accounts and the dangers of running as root.

Personally, I do run as Admin on my XP Pro x64 box. It's a pain in the butt doing it otherwise, thanks to the general world's ignoring of user account permissions and requiring admin rights to run most new games.

Besides, I have an AV, run behind a router and in general know what I'm doing, so I've never had security problems.

---

### Post by aysiu on 2006-11-01
I have two accounts at my work computer (thanks to the IT department accommodating my quirky needs): one is administrator, one is a limited user.

I use the limited user mostly. When I need to accomplish an administrator task, I use the **Run as...** feature.

---

### Post by rfruth on 2006-11-01
I don't have a Windows (XP) box anymore but when I did yes I used the admin account, tried not to but like you said it was a pain not to :evil:

---

### Post by randomnumber on 2006-11-01
I doubt that most xp only users know what an administration account is and assume they are not using an admin account when they find out what it is. I think most on this forum are less ignorant than that. Although, I am sure that there are linux users that are just as ignorant, just not in so high percentages.

---

### Post by turkenator on 2006-11-02
i always use 2 run as admin untill i converted to linux :D i knew running admin had its dangers but ms duzn really gimme a choice the limited user is crippled as

---

### Post by 3rdalbum on 2006-11-03
I did try running day-to-day as the limited user, really I did. But it sucks.

For starters, some programs don't work as the limited user; you need to do a Run As... on them. But, it seems to me that programs are always spawned as the host user account, not as the account that spawned them.

i.e. I tried installing iTunes 7 with Run As. The iTunes installer itself seemed to work, but when it tried to start the Quicktime installer, that failed because it was running under the limited user account. On Ubuntu, if you run a program with *sudo*, when that program tries to start other programs, those other programs will also have root privileges.

My modem is never turned on at the same time as Windows, so I didn't see the point in persisting with such a badly-conceived and totally-incompatible security framework.

---

### Post by aysiu on 2006-11-03
Windows is meant to be run as administrator. **Run as** is crippled.

More details:
[http://psychocats.net/ubuntu/security#versuswindows](http://psychocats.net/ubuntu/security#versuswindows)

---

### Post by Senak^2 on 2006-11-03
In XP I use the admin account, it's too much of a pain not too. In 2000 mostly the "Power User" account.

---

### Post by SunnyRabbiera on 2006-11-03
Always in administrator mode, its impossibe to do anything under anything else.
No wonder why XP is easy to get into (though Ubuntu's sudo is scary sometimes, I perfer root)

---

### Post by Chinkostu on 2006-11-03
I always run XP as Admin. its just easier in the long run. i have a firewall and AV so i'm not exactly opening myself too much. i would limited account my brothers user but then he can't run most things he uses from day to day. if it was more like 2k pro (with user groups that can do certain things) then it would be easier

---

### Post by Smirre on 2006-11-03
Well, I do.  Hasn't really posed a problem, I do take my precautions.

I feel safer when in Ubuntu tho. :)

---

### Post by Tiede on 2006-11-03
I don't think somehow windows was intended to be run with limited user account for daily usage. Really, it's just such a pain!
So I run an administrator account on windows... Would wish it otherwise, but :(
Anywho, I heard it'll have 'normal' limited user account in vista... If only I was interested in it :D

---

### Post by AlphaMack on 2006-11-04
> **aysiu said:**
> Windows is meant to be run as administrator. **Run as** is crippled.

More details:
[http://psychocats.net/ubuntu/security#versuswindows](http://psychocats.net/ubuntu/security#versuswindows)


Agreed; Windows is a single-user OS with hacks for user 'privileges.'  Personally, I have quite a number of programs that expect full single-user privileges.

---

### Post by ShadowVlican on 2006-11-08
i run as admin all the time

i don't like to be restricted in any way

so long as you don't do dumb things, Admin 24/7 works fine

---

### Post by rattlerviper on 2006-11-08
100% of the time...and never a problem.  It's all in what you do whilst you are in the account that makes you vulnerable.

---

### Post by julian67 on 2006-11-09
> **rattlerviper said:**
> 100% of the time...and never a problem.  It's all in what you do whilst you are in the account that makes you vulnerable.

I have to disagree. It's not just about your online behaviour but also your account status. If you run as Administrator your AV and firewall can be taken down/bypassed, malware such as rootkit can be installed and you probably will never even know it. If you run XP or 2000 as restricted user and your AV and firewall are protected with strong passwords you are an awful lot more secure. But of course running  as user is a PITA in Windows. The only way I could do it and have it work reasonably well was to clean  install with all my apps as admin and then change that account to user.  This also involved setting permissions for specific folders for those many apps which want to write to C:\Programs  instead of writing to C:\docs&settings\username\.   It means adding certain new applications and especially new users is a nightmare. I still have an XP partition (I'm not sure I remember why tho....oh yeah..Photoshop) and run it as admin but it contains no personal data, no mail client etc. and is rarely used online. If I was seriously using XP or 2000 again it would be as restricted user, same as on linux. I'm surprised how Linux users in this thread run Windows as admin. Probably you could get away with running desktop linux as root for a long time surfing and clicking any old thing, but Windows? You get owned and never even know.

---

### Post by Bender the Robot on 2006-11-09
I run as administrator but I'm in a 'sandboxed' environment, when online, and nothing is allowed to 'phone home' or update (even my AntiVir) without my permission. My C: partition is only 2Gbs as it's only used for the OS and App files so, as all my files are on D:, I hit F11 on bootup, once a week and use 'Acronis Recovery Manager' to restore the PC to a freshly installed state. 

 'Acronis' is a wonderful app for those of us, with 'Windows', who use 'nLite' and bold_fortune - [http://www.bold-fortune.com/forums/index.php?act=idx](http://www.bold-fortune.com/forums/index.php?act=idx)

---

