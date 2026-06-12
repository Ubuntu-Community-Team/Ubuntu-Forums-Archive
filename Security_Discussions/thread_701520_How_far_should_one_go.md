---
title: "How far should one go?"
date: 2008-02-19
forum: Security Discussions
---

### Post by Kivech on 2008-02-19
Hi all,

I'm fairly fresh to Ubuntu 7.10 x64, since I've made my final full switch about a week ago.

I have everything running I need and am quite happy with it all. For the first time ever I have a problem free stable OS. Needless to say, I feel a bit lost and figured to spend some time on studying security on Linux.
I've read the sticky on security written by bodhi.zazen and the links he provided in his post; very interesting stuff indeed. I even went through the whole 'paranoid' guide.

Now since I once (a long time ago) used to be a HP Unix admin, security is of course something that interests me. I've been out of the *nix scene for quite some time, so I'm really rusty here.
I installed Tiger on my system and had it run a report. Don't think it came up with much alarming stuff, however I did notice some parts that do concern me, and which got me thinking. This got me to the following points/questions:

Keep in mind that I have my system running flawlessly (which I consider quite an accomplishment for Linux, since in previous distros that was next to impossible), so the less I have to change, the better.

1) How secure is Ubuntu 7.10 x64 out of the box? I did install all security add ons for Firefox according to the stickied post on this forum, but is there any other 'must do' stuff?

2) I'm a bit alarmed about how Ubuntu is set up as in that my root password by default is the same as my user password. In my book that is a mortal sin. How would I go about to separate those and have a seperate root password?

3) Related to 2): I would like to be able to log into root at the login screen to do maintenance work, so I really keep root and normal users separated, how do I get to that point?

4) For security reasons, doesn't it make more sense to start up Ubuntu with a command prompt instead of with Xwin by default, and then start it manually? At least in terminal mode one can see all messages by the system, now I don't see at all what's going on.

5) I like the idea of an encrypted system, but I'm not sure the whole hassle of reinstalling everything just to encrypt my system is worth the hassle for me. Would you say that for a normal home PC these things are really needed? Because if you feel it is, I could start planning building a secure system.

6) The 'paranoid guide' is written for Debian, is this one valid for Ubuntu 7.10 x64 as well?

7) In my case I'm the main user of my PC, and my wife just uses it to browse every now and then. Since she definately is not a techy I'm going to set up a seperate account for her one of these days with everything set up she needs. Is there a simple way to port all settings of my desktop to hers, but just not allowing her the same flexibility I have to prevent her from messing up things?

8) Last question: I like my system the way it is generally now, which is basically a default Ubuntu install with customized partitions and a whole customized desktop environment (compiz bells and whistles, etc.). Is there a way to make that fully secure with encryption and stuff like mentioned in the sticky of this forum?

Anyway, enough for now. If you guys want to I can post the output of tiger later (am at anoter pc at the moment). Please let me know what you guys think, since I do value security a lot after having had some issues in the past (ea. credit card info being misused and such), and I want to make sure my pc is not vulnerable for that.

Oh, forgot to mention that I'm behind an ADSL modem/router in default config. Not sure I should delve into that one's config as well.

Thanks in advance for any advice,

Kivech

---

### Post by Dr Small on 2008-02-19
1) Ubuntu is fairly secure out of the box, unless you go installing services like FTP or SSH. Then you would have to lock those services down.

2) Ubuntu uses Sudo, and the Root Password is disabled by default. Please read more about RootSudo at the Ubuntu Wiki:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

3) Logging in as Root is not necessary, as everything can be managed from your user account with Sudo. Also, logging it as Root is considered o security risk.

4) I think that GRUB needs to be setup not to boot into 'quiet' mode, so you can see the messages at it boots.

5) I would say that is really isn't essential unless you are housing sensitive data.

6) Ubuntu is based off of Debian, so most guides written for Debian should also work for Ubuntu.

7) As long as she is not in the admin group and she can not sudo, then it would be quite difficult to mess the system up.

---

### Post by wirelessmonkey on 2008-02-19
1) Fairly secure.  You should configure your firewall as appropriate for your environment.  There are very few open ports facing the internet by default.  If you are really concerned about security, there are (of course) other things that can be done.

2)Your root password is not the same as your user password.  Your user has 'sudo' rights, allowing it to run certain commands with root privs. Your root password is basically useless gibberish, unless you purposefully change it. I could not, for instance, brute force your root password from my machine on a default install.

3) Log in as your normal user.  From the command line : ~$ sudo su
enter your password, and you will have a root shell, then  ~$ passwd
this password will the the new root password for your system.  
I don't suggest doing this as enabling root does very little that using 'sudo' wouldn't do better (securitywise).

4) On a server, yes.  Ubuntu is meant for desktop users generally.
5)No, not for a normal home user.
6)Yes
7) /etc/skel
8) Absolutely, but I'll have to get back to you ;)

Good Luck

---

### Post by Kivech on 2008-02-19
Thanks for the elaborate replies so far. I really appreciate you guys taking your time to educate an old timer on these things.

I have to admit though, sitting behind a *nix system does get my blood pumping a bit again. It brings back good memories ;)

Seems to me that so far things will be fairly easy to approach. I can see the security risk with a separate root-user login, so I'll leave that as is.
Same goes for the terminal mode logon. I guess it's just an old habit from my admin days.

Since I have no intention of running FTP or SSH services I guess I'm fine on that part also.

My wife in general doesn't do any stupid things on the comp, it's just that preventing is better than curing. So I guess I'll set up an account with restricted permissions for her. That shouldn't be too hard to do.

Now, theoretically speaking, would it be possible to backup my whole system, repartition it with encryption and then put my whole system back on the encrypted system?
I can see how this can be complicated since certain encryption services will have to be running, but is there a way to do this? Or is it possible to encrypt an existing system like that (in a reliable way that is)?

Thanks again for all your replies, they are very useful.

Kivech

---

### Post by Kivech on 2008-02-19
On a side note to wirelessmoney:

I just now noticed that you are using Slackware. Talk about memories! I used that in my early days of unix admin to learn how to administer the system. 
How is this distro these days? I remember that I favored it over the others due to it being to so open, yet easy to use. We're talking about more than 10 years back though. :p

Anyway, more good memories...

Kivech

---

### Post by freelinuxhelp on 2008-02-20
I started with Slack too... I forget the version, but it was in 96 or 97. Version 12 was released not long ago, and it's still good old slackware. It doesn't have many of the bells and whistles that some of the other distros have, not that you couldn't add them... by compiling from source, but is still very Unix-like and stable.

---

