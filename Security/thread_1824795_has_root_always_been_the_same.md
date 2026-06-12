---
title: "has root always been the same?"
date: 2011-08-14
forum: Security
---

### Post by sjvinc on 2011-08-14
I was reading some other articles about using sudo and root and so on.   I know that the version of cd that I have at home is something like 6 or later could be 8, but the version I found on my pc is 2 or 3.   Does anyone know how root was treated back then? could someone have put in a password for root then? or is it just the redirects stopping me from doing anything with my Ubuntu live cd. Would it be better to put my pc on a secure server to get to the Ubuntu and fix it or can I possibly use a memory stick or cd.

---

### Post by cariboo on 2011-08-14
I'm not sure exactly what you are asking, but Ubuntu installs sudo by default, and doesn't give you the option of setting a root password during installation, most other distributions do.

For more info on sudo and root, have a look at the [RootSudo]("https://help.ubuntu.com/community/RootSudo") page

---

### Post by sjvinc on 2011-08-14
That is what I have read all along. But that is where I am confused, I saw where root (the user I mean) was making actual changes to the system, setting it up in its present form. then I saw it change to Ubuntu and tried to log back into root again and could not. I dont think that is actually Ubuntu, possibly something else. I mean for it to be version 2 or 3, that is fairly old, if Ubuntu is at 11 now.  besides all of that, my Ubuntu live never actually got around to an install. it just went through a very weak motion of acting like it did. I saw all of this in the logs and also remember and wrote down what it did when I was trying to get started. I had to cancel the install three times because of things it did. each time it appeared to be halting the system correctly and shutting down. but the system is there or at least it thinks that it is. I had to shut down with control alt delete when it was putting me into that fake command line even then it would halt the system and shut down.

I think that I will get some better help on this and hope for the best. obviously, it was put where ever and just forgotten there. It was not actually put onto the systems where it is now, that was a fluke of an accident when the entire node went down, or so I think.  when my isp got the node back up, two days later... every machine that was logged into the ISP at the time was infected. my logs only go back to late 2004 and that is when my ISP had the crash and lost the node for two days.

---

### Post by tubezninja on 2011-08-14
I'm going to try to help, but to be honest, it's really hard to figure out what's going on here exactly.

To answer some of your questions: Even though the root user login is disabled, it's entirely possible for a linux installation to still be running processes as root.  In fact, that's what you're doing every time you preface a command with "sudo."  You're running a command with super user privileges (root) without actually logging in as that user.  it's intended to be a safeguard to ensure that a user really wants to do this.

Perhaps it would be best if you started at the beginning.  To even start to help you, we need to know:

1. What behaviors, exactly, are your computers doing that you are finding suspicious?
2.  You mention logs a lot. Can you copy and paste portions of these logs that you think are relevant, so that we can have an idea what you're talking about?
3. TO find out what version of ubuntu you have running exactly, follow the instructions at this link:

[https://help.ubuntu.com/community/CheckingYourUbuntuVersion](https://help.ubuntu.com/community/CheckingYourUbuntuVersion)

and post back.

---

### Post by sjvinc on 2011-08-14
It acts just like a rootkit would. In fact, I just realized that I have  never run any tools on the Ubuntu side of the system, I have always run  these tools on the xp side!  I will first go and get a rootkit scanner  to scan this, also something that will give me a much better log file.  Since I can have these guys with the secure server make one up for me,  they can also put in permissions so that only the rootkit scanner that I  use can read and write to the memory stick... or is that possible? is  there a better way to do that? 

Just to let everyone know in answer to an earlier comment, I paid for  all three of my computers that have this problem... I paid at least 7k  for them and that does not include the HD monitors or other things I  purchased to go along with them. I have never stolen anything in my life  and I am not about to start now. I do not mean that as angry as it  might sound, but to tell the truth, this problem with my computers has  me more than a little angry and I have been that way since this first  happened. Since I already have the email address of two that was talking  over the stream in this setup,  I could do something about that... I  really would rather forgive and forget as long as they leave me alone.  this was not done to me on purpose, it was directed at SBC and through  an accident, this rootkit infected many who were logged in through SBC  at the time.

---

### Post by sjvinc on 2011-08-14
My original question was about Ubuntu v2, no need to answer that one. It is something put together to look like Ubuntu. I have also found all the other things that I was asking about. I guess you can close this too. 


?I do not always use a ? so it might be loaded with questions and have no "?"

---

### Post by cariboo on 2011-08-15
It would help if we knew exactly what version of Ubuntu you are running, as there was no version 2 or 3. Ubuntu uses the month and year of a release for versioning. Currenttly the latest relaese is Natty Narwhal 11.04 released in April of 2011. We are currently testing 11.10 Oneiric Ocelot which will be released at the end of October 2011. TO find what release you are actually using, open a terminal and type:

```
cat /etc/lsb-release
```

the result should look similar to this:

> cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu oneiric (development branch)"

---

### Post by scorp123 on 2011-08-15
> **sjvinc said:**
> My original question was about Ubuntu v2 There never was a "Ubuntu v2". Ubuntu started at 4.10 because it was released on October 2004 for the first time. Afterwards came 5.04, 5.10, 6.06, 6.10, 7.04, 7.10, 8.04 LTS, 8.10, 9.04, 9.10, 10.04 LTS, 10.10, and 11.04 where we are now. In October there will be 11.10 and after that 12.04 ...

"Ubuntu v2" or "Ubuntu v3" .... doesn't exist. And I really have a hard time to understand what you want to say.

---

### Post by haqking on 2011-08-15
There is a Ubuntu V2 but it is not a canonical thing.

It is from Symbian i believe or for symbiam phones.

perhaps he means that ?

Edit: yes thought so, see here [http://ubuntu-v2.en.softonic.com/symbian](http://ubuntu-v2.en.softonic.com/symbian)

---

### Post by scorp123 on 2011-08-15
> **haqking said:**
> There is a Ubuntu V2 but it is not a canonical thing. It is from Symbian i believe or for symbiam phones. That's just a theme for Symbian phones. I don't think he meant that??

Quote from there: [I]"... The Ubuntu v2 theme adds an impressive array of new icons to your system's menus. ..."
[/I]

---

### Post by Elfy on 2011-08-15
After closing some rather lengthy threads that didn't actually appear to contain much, a PM from the OP was received by me
> 
but no problem, you can now close all of my open questions. I found the exploits that have been used on my machines.


Thanks anyway.

Thread closed

---

