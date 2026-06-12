---
title: "The way Automatix is perceieved"
date: 2006-06-10
forum: The Cafe
---

### Post by zugu on 2006-06-10
I have a dilemma and I hope someone will enlighten me.

Back in the days of Breezy :p folks on #ubuntu would rather not recommend Automatix to new users. Actually, this is the reason I never installed it. I was told that the script is insecure and using it can mess up the whole system.

Now I see more and more people on the forums recommending Automatix to new users.

Did Automatix get better? Do the #ubuntu people feel the same about it or they have changed theit opinion? Or may be people recommand Automatix because this way is easyer to deal with new users? In other words, what is the current community stance in relation with Automatix?

Thank you.

---

### Post by aysiu on 2006-06-10
I created a poll about this:
[What has been your Automatix experience?](http://www.ubuntuforums.org/showthread.php?t=123569)

---

### Post by loell on 2006-06-10
[QUOTE=zugu]I have a dilemma and I hope someone will enlighten me.

Back in the days of Breezy :p folks on #ubuntu would rather not recommend Automatix to new users. Actually, this is the reason I never installed it. I was told that the script is insecure and using it can mess up the whole system.

Now I see more and more people on the forums recommending Automatix to new users.

Did Automatix get better? Do the #ubuntu people feel the same about it or they have changed theit opinion? Or may be people recommand Automatix because this way is easyer to deal with new users? In other words, what is the current community stance in relation with Automatix?

Thank you.[/QUOTE]

I don't know if that is true, because there are also ubuntu users that recommend easyubuntu over automatix, surely automatix has made some improvements, the  ubuntu users seems to have a divided opinion about automatix, easyubuntu, or manuall APT. it just boils down to personal preference i guess..;)

---

### Post by zugu on 2006-06-10
Thank you for the answers.

---

### Post by KiwiNZ on 2006-06-10
[quote=aysiu]I created a poll about this:
[What has been your Automatix experience?]("http://www.ubuntuforums.org/showthread.php?t=123569")[/quote]

Given new versions of both Ubuntu and Automatix I have closed the poll

---

### Post by benplaut on 2006-06-10
this is, um, a political issue =/

there was a prominent member of #ubuntu who was very against AX, and would [attack?] anyone recommending it.  People followed his/her example. given the high status of this person, and hate began to spread.

There are still problems, but i don't think either is explicitely recommended over the other.

---

### Post by aysiu on 2006-06-10
Based on the poll KiwiNZ just closed, I would say...

If Automatix somehow messes up your system, I'm not surprised. And if Automatix works perfectly, I'm also not surprised.

I don't see any problem in recommending it to people as long as they realize it's another program you're adding in, and it's not standard.

Any time you add a non-standard program, there's a risk, however small, of breakage.

In the vast majority of cases, though, it's a wonder-tool, and the user ends up happy with how easily it installs numerous popular applications.

If there ends up to be breakage... well, the other Automatix users on this forum are more than happy to help fix the breakage.

For the record, [one forum member has written up a little summary of BUMPS, EasyUbuntu, and Automatix to help new users choose](http://www.ubuntuforums.org/showthread.php?t=185643).

---

### Post by 23meg on 2006-06-10
The following isn't personal for anyone, or specific to any software. I've felt like saying it in many other threads but haven't found the right time or the right words.

"Who is saying what on Automatix" (or any other software) will ultimately never go beyond gossip and surface politics. To have your own idea about whether it's good or not, safe or not, you need to *be informed*. If you lack the time or technical know-how to be informed in depth on this specific issue, just read through the two threads linked off aysiu's poll where there's lots of discussion and well laid out information for a start, and decide for yourself.

If you're underinformed, and can't bother to get informed, please kindly step out of any discussion where information is a prerequisite.

Understanding is only genuine when you've understood something for yourself with your own reasoning, not based on bits and pieces of disconnected half ideas and gossip floating around.

---

### Post by aysiu on 2006-06-10
23meg, I'll be the first to confess that I'm not terribly informed, and I don't know all the technical aspects of how Automatix works.

I do, however, think there's something to be said for the aggregate experience of 255 users.

---

### Post by 23meg on 2006-06-10
aysiu, my concern wasn't for your post (it may have felt like that since my post was right after yours) which wasn't even there by the time I started writing, but the whole point of this thread and similar ones. In a software context "What does A say on B?" will never go beyond useless gossip without clear technical reasoning behind it.

---

### Post by aysiu on 2006-06-10
Ah, I get it. Nevertheless, I don't actually know all the technical issues involved with Automatix.

---

### Post by Christmas on 2006-06-10
I heard Automatix is a good starter program so I tried it once, it seems pretty good. However I like to install all those things manually, especially because all that Automatix does can be done manually. For those who don't have enough time and want to have all out of the box looks like Automatix is the best choice out there.

---

### Post by zugu on 2006-06-10
[QUOTE=23meg]aysiu, my concern wasn't for your post (it may have felt like that since my post was right after yours) which wasn't even there by the time I started writing, but the whole point of this thread and similar ones. In a software context "What does A say on B?" will never go beyond useless gossip without clear technical reasoning behind it.[/QUOTE]

I started the thread because I found some posts in the'Absolute Beginner Talk' asking for guidance in installing support for Java, Flash among others, and some one recommended Automatix. Because I never used it, I didn't know wether it was right or wrong to recommend it.
It never was my intention to flame or troll, but to inquire the community about current atittude towards Automatix, given the previous somewhat official statements about it. I needed feedback in order to decide what to do further when someone asks for software Automatics makes easy to install.

---

### Post by cstudent on 2006-06-10
I've used Automatix many times without a problem. I also know enough about bash scripting and zenity to understand what the script code is going to do. I personally never felt that the code was all that dangerous. Automatix is best used to setup a new install of Breezy or Dapper. If it were to fail, then just starting over isn't that big of a deal. Once the system is setup with all the software you want, then there is no real need to run Automatix again. There was a big issue with some folks because it used the force install switch, which could cause problems if you forced a package to install that didn't have all it's dependencies available. I haven't read through the new code, but I think the use of the force switch has been removed. The thing with Automatix is it makes use of the internet to download the software and then install. If a problem would occur during the download, then there could be problems with an install. If I were to rewrite the code, I would write it so that all packages to be installed were downloaded first and then verified that they downloaded OK. *Then* have the script install the packages. The real meat code of Automatix is nothing more than apt-get, wget and dpkg commands. Nothing really different than sitting there entering them one by one into a terminal window. I have no problem recommending Automatix to anyone. Nor would I have a problem with Easy Ubuntu, but EU doesn't have as many packages available. But the bottom line is, just about any software package could do something to break your system if some unusual circumstance occurred during installation. How many disclaimers have we read when installing new software were the developer says they are not responsible for what may happen? In other words, sh*t happens.

.

---

### Post by 23meg on 2006-06-10
[QUOTE=zugu]I started the thread because I found some posts in the'Absolute Beginner Talk' asking for guidance in installing support for Java, Flash among others, and some one recommended Automatix. Because I never used it, I didn't know wether it was right or wrong to recommend it.[/quote]Good, so you actually started the thread to *get informed* somehow.
> It never was my intention to flame or troll, 
I didn't say that it was; and it's obvious from your original post that it isn't. Just to clarify again, my first post should be read as a general statement that applies to all software discussion; it's not specific and limited to Automatix, this thread, or any particular person.

---

