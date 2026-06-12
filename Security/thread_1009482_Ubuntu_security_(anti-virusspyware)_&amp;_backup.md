---
title: "Ubuntu security (anti-virus/spyware) &amp; backup?"
date: 2008-12-12
forum: Security
---

### Post by Tamalin on 2008-12-12
I was wondering, what programs are available for Ubuntu anti-virus, and backup?  I know that Linux is pretty much safe from viruses, but you can never be sure... And then there's spyware, addware, etc...

Does anyone have any recommendations?
Thanks!

---

### Post by aysiu on 2008-12-12
Having anti-virus installed won't protect you from any future threats, and there are essentially no current threats, so it isn't really "just in case"; it's "just useless."

For backup solutions look here:
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

### Post by aysiu on 2008-12-12
Having anti-virus installed won't protect you from any future threats, and there are essentially no current threats, so it isn't really "just in case"; it's "just useless."

For backup solutions look here:
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

### Post by scouser73 on 2008-12-12
What I have done with my PC is to have all the things I have downloaded from the repositories burnt onto a CD from a program called APTonCD; [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) once you have installed and done the necessary tasks, you should then install Remastersys, which makes a ISO backup of your system; [http://www.ubuntugeek.com/creating-c...mastersys.html](http://www.ubuntugeek.com/creating-c...mastersys.html)

Both are extremely easy to use, it took only 20 minutes to have everything back up and running as normal again.

---

### Post by donkyhotay on 2008-12-12
The only anti-virus for linux that I know of is clamAV which is available in the ubuntu repositories.

---

### Post by Tamalin on 2008-12-12
Well, I have tried avast anti-virus, but I'm just not sure how well it works.  It required me to sign up for a registration code as well.

---

### Post by aysiu on 2008-12-12
I think you're better off employing *real* security measures instead of using anti-virus.

Here are some quick tips for you: [list][*]Don't enable extra network services unless you know how to lock them down.[*]Use strong passwords[*]Stick to only the official repositories when installing software and updates[*]Read up on how to avoid social engineering[*]Use NoScript in Firefox[/list]

---

### Post by Tamalin on 2008-12-13
Well, what exactly is "NoScript"?  I had Javascript disabled in my browser for a while, but I couldn't use most web pages...
And also, what is "Social Engineering"?

I have installed grsync, and it appears to work quite well.

---

### Post by hikaricore on 2008-12-13
[https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)

> The NoScript Firefox extension provides extra protection for Firefox, Flock, Seamonkey and other mozilla-based browsers: this free, open source add-on allows JavaScript, Java, Flash and other plugins to be executed only by trusted web sites of your choice (e.g. your online bank), and provides the most powerful Anti-XSS protection available in a browser. 


[http://en.wikipedia.org/wiki/Social_engineering_(computer_security](http://en.wikipedia.org/wiki/Social_engineering_(computer_security))

Example, you click on a link from myspace that takes you to what appears to be a myspace login page, but actually is on a some server in china.
Example, you install a new piece of software that you are not familiar with that pops up a box asking you for **all** of your system login info, the software then pretends to crash while quietly sending off your personal info to scammers.

As far as ad/spy/mal -ware you won't find much of that on Linux.
The operating system is much better designed as far as security is concerned.

---

### Post by upapilot on 2008-12-13
I think AVG have recently announced an antivirus software for Linux. But i seem to agree with aysiu that there are no viruses threatening Linux right now. And i've tried No Script on Firefox...........Rubbish in my opinion....It's even troublesome as it stops everything any website would do):P

---

### Post by Trist on 2008-12-13
Hi,
I used to use clamav for virus scanning but in 4 years of using Ubuntu it never picked anything up so I don't bother with it any more. For backing up file and folders pybackpack is quite good. I also used to use Noscript but I found it to be very annoying.

---

### Post by lukjad on 2008-12-13
NoScript is my #1 addon for Firefox. In the newest version, you can enable certain scripts only on a certain page. Very useful. If you trust a page, you can click allow all and it lets all the scripts start to run. It can be a bit of a hassle if they start to run other scripts which start to... you get the picture. But at that point, you probably are not on a well built website.

---

### Post by Tamalin on 2008-12-13
Ok, but there is no scripts that could install malicious code onto my computer without my knowledge?  I found one site that managed to send my computer into a wreck, I think it was some scam from China.  I just wanted protection against those sort of threats.  Just how often do these kind of threats pop up for Ubuntu?

Our Windows server managed to collect a sizeable 130 infected files while just sitting around doing nothing!

---

### Post by lukjad on 2008-12-13
Edit: I removed this post as it seems to be wrong. Thanks bodhi_zazen.

---

### Post by arrancaru on 2008-12-13
Antivirus for linux are useless, since has no virus at all capable of affecting linux. You can use clamav, i think, in linux to protect files in windows machines. There's no spyware or adware too, at least yet. Neither you have to worry about disk defrag nor registry fixes etc, this is all windows problems.

---

### Post by bodhi.zazen on 2008-12-13
> **lukjad007 said:**
> Well, there is no protection anywhere from 0 day attacks. That is to say, that if something is brand new, there will be no protections at all for it, anywhere.


That is not true. Although we by definition do not know the nature of the zero day attack, so we can never be fully protected, there are several tools that can potentially help.

Ubuntu uses apparmor for example. There is also SELinux. You can also use something like OSSEC to monitor host integrity.

I suggest you read the stickies at the top of the security section :

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

### Post by Tamalin on 2008-12-14
So, basically, Linux has built in anti-virus, and I don't need to worry about it?

---

### Post by bodhi.zazen on 2008-12-14
> **Tamalin said:**
> So, basically, Linux has built in anti-virus, and I don't need to worry about it?


No, Basically Linux is not Windows, and just as you can not run Windows applications, Viruses are a non-issue in Linux Security.

Read this link :

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

That is not the same as saying Linux is invulnerable to malware, so part of learning a new OS is learning how to secure it. Please see the stickies at the top of this forum.

---

### Post by oilit on 2009-01-28
> **bodhi.zazen said:**
> No, Basically Linux is not Windows, and just as you can not run Windows applications, Viruses are a non-issue in Linux Security.

Read this link :

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

That is not the same as saying Linux is invulnerable to malware, so part of learning a new OS is learning how to secure it. Please see the stickies at the top of this forum.

Thanks for this, very interesting reading - and answered a ? I have had in the back of my mind for a while - (malware & privacy), + you actually helped me learn some new things today (moved to Ubuntu/linux for the first time a month or so ago, and now im up and running starting to try and get an understanding and dig deeper into why certain things dont do what I want them to - which as a poster up above stated is about gaining a new appreciation when you change to a new OS)

Thanks again - great community.

---

