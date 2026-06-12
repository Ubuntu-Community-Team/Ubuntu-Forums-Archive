---
title: "Ubuntu noob security question"
date: 2017-10-17
forum: Security
---

### Post by langendoerfer on 2017-10-17
This question may be better suited for the security forum if so i'll gladly move the post, but as I'm brand new to Ubuntu i thought i'd start here.
In any case my question is a bit vague but i'm looking for some resources or advice on general security do's and don'ts for linux. I'm very new to this OS and over the last few days i've gotten a lot of help from the community solving issues! But in doing this i've blindly trusted throwing sudo commands that i do not fully understand into my terminal and publicly shared the results. While i'm sure that the 99.9% of responses have no nefarious intent (and i'm very grateful for the help and support) i would like to have a better understanding of what the red flags are so that I or others don't compromise or damage my system or security. I'd really like to hear any feedback or resources i could be pointed to.

---

### Post by yetimon_64 on 2017-10-17
There is a sticky thread in the Security sub forum that is a good start, here is a link to it ...
[https://ubuntuforums.org/showthread.php?t=510812]("https://ubuntuforums.org/showthread.php?t=510812")

Cheers, yeti.

---

### Post by ian-weisser on 2017-10-17
yetimon_64 is right. That Security sticky is a very good starting point.
Read it now...then return to it next week...and next month...and next year.

Edit: If anyone on *this forum* asks you to execute a command that turns out be malicious, please flag the post and let a moderator know.
The moderators here work hard to ensure a safe, friendly forum, and they do not tolerate such abusive behavior.

---

### Post by oldos2er on 2017-10-17
> **langendoerfer said:**
>  i've blindly trusted throwing sudo commands that i do not fully understand into my terminal and publicly shared the results. 

I think many of us did this when we were new and learning; I know I did.

Referring to ubuntuforums, if you have been asked to run a command and provide its output, chances are excellent that it's *not* malicious. It's simply the easiest way to obtain vital information about a system and/or any problems being asked about. If you have a question about a particular command someone's asking you to run, then ask them about it before running it. Anyone's who's legitimately trying to help you will be glad to answer.

If you come across a command you've seen in a blog or other website, plug it in to a site like [explainshell.com]("https://explainshell.com/"), which will give you some idea of what it would do.

Man pages are handy to consult also; they can give you a wealth of information on a given command, even though they may be difficult to understand at first.

---

### Post by langendoerfer on 2017-10-17
Excellent, thank you all very much for the guidance! The security sticky thread is a wealth of information, and explainshell.com is really awesome I wish i'd been pointed to that sooner. I often forget how great a resource the man pages are, coming from a windows background 'help' often yielded confusion but thus far each time i've used something like 'man get' I end up with more clarity. I very much appreciate the thought and help you all have provided.

---

### Post by mastablasta on 2017-10-19
sudo gives accesses to system files.

generally the ocmmands ar enot needed, but they work on every desktop. usually one can get same results using GUI (particularly KDE has many settings in GUI and they can be overwhelming for the user)

---

### Post by HermanAB on 2017-10-19
The most important lesson:
Always use very long unique passwords for everything and store them in a password safe such as KeepassX.

My typical passwords are 16 characters and my super user passwords are about 25 characters.

---

### Post by jpberes on 2017-10-29
The Ubuntu flavours have a very good firewall (where no special customizations have to be done) : Gufw ... (you can get it from the software center .. and simply activate it ...
That's normally enough as a fairly good security !
Other, but some Linux Guru's are against it, fairly good tool is : rkhunter ...
regards,
JP

---

### Post by slickymaster on 2017-10-29
*Thread moved to **Security**.*

---

