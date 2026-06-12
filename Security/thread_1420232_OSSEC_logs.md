---
title: "OSSEC logs"
date: 2010-03-02
forum: Security
---

### Post by Advait on 2010-03-02
Hi All,

I installed and activated OSSEC on my Ubuntu 9.10. I did not activate the email notification feature of OSSEC cause I thought I would just look at the logs locally. After doing a few hours of research I'm totally confused as to how to look at the OSSEC logs on my local machine. I tried to get into the /var/ossec directory to see what's there, but it won't let me in, even when I use sudo.

How can I see the OSSEC alert log on my local machine? I looked thru the OSSEC manual but didn't find a solution.

Can I somehow view the OSSEC logs directly? Or do the OSSEC logs need to be fed into some kind of database before they can be seen? The OSSEC manual describes how to view the logs using MySQL and Postgres, but that seems to be meant for a server environment, not a workstation. And those instructions looked a bit above my ability level.

Thanks,

Tom

---

### Post by bodhi.zazen on 2010-03-03
The logs are in /var/ossec

You can read them as root with any editor.

```
gksu gedit
```

Have you tried looking at the web interface ?

---

### Post by Advait on 2010-03-03
I researched the OSSEC web interface and found myself in *way* over my head. Wow. More and more it seems that to use Ubuntu its like wanting to drive but I have to first learn how to build a car from scratch. Ouch.

So before I get myself even more confused about the OSSEC web interface, could you give me a bit more info about the easiest path you would take to install the "OSSEC web interface"? Please remember that I can't even navigate the directories without doing some research on the learning curve.

Thanks,

Tom

---

### Post by bodhi.zazen on 2010-03-03
[http://ubuntuforums.org/showpost.php?p=5786522&postcount=7](http://ubuntuforums.org/showpost.php?p=5786522&postcount=7)

That post assumes you already have apache installed (from previous posts).

It takes time to learn a new OS and it gets easier as you get more experience.

Security is a complex ever changing topic on any OS and many users get lulled into complacency.

---

### Post by Advait on 2010-03-03
Thanks for the info. You guys are very patient with newbies like me! (smile!)

It looks like in order to use the OSSEC web interface I need to install Apache. I'm nervous about doing that because I'm guessing that not using and maintaining Apache correctly can lead to all kinds of security holes and unintentionally opened ports. And I'm paranoid about security (that's why I switched to Ubuntu). And I can only imagine the many hours it would take to learn just the basics of Apache. Remember I barely know how to use the cd command.

So I'll end my adventures with OSSEC and AppArmor here before it turns into a full time hobby.

On my WIndows PC I was able to easily stay safe by not doing the usual dumb things and by using eeye Blink, Firefox/NoScript and LastPass/Yubikey. I think I'm even safer with Ubuntu, but I *really* wish I could use tools like App Armor and OSSEC. Unfortunately I don't have the many hours it would take to learn how to install and use them properly, even though I'm having lots of fun learning Ubuntu.

Perhaps in a few years someone will build some newbie oriented GUIs around OSSEC and AppArmor so they can be installed and working in a few moments. Just like I was able to download Thunderbird and have it running and fully functional in 5 minutes.

Thanks again for all the info. This is a great forum.

Tom

---

