---
title: "Base libraries should be installed by default"
date: 2010-03-02
forum: Ubuntu Dev Link Forum
---

### Post by pushkarajthorat on 2010-03-02
Greetings,

I've come across linux from last 3 years, this question is about dependencies which are required to satisfy before installations.

Before I start, let me tell you, I've worked extensively on windows as a user and a developer form last 10 years, and I've never installed any lib. to satisfy dependency, except DirectX and few others. So here I assume MS ships all the required lib. with its OS, and so external dependencies are almost NOT required.

Now, when I came accross linux developement, I was pretty confused with the dependencies and their versions which are required to satisfied. I managed to solve the problem with apt, but, lame user for which, I suppose, ubuntu is targetted, will not understand these tricky things.

Here I wish if we could club all the MOST requied lib. and ship them with distributions.

When user recieves a .deb file it won't give any dependency problem while installation.

Regards, Pushkaraj

---

### Post by byStanderone on 2010-03-02
hello,

...will only be speaking in behalf of myself regarding the matter which you just brought out, for one, am only a newbie ubuntu user...don't know much about the other linux distros.

to begin with, am currently using karmic and would be udgrading to lucid within a month or so...and since my first ubuntu (gutsy), haven't shared out a penny to the ubuntu community as token of gratitude for their service.
your idea is fine, the main problem would be distribution and considering the files that would be added to the install disk that would support the needed dependencies that you mentioned...i would say it is not feasible or economical at the least...besides being impractical. each user has his/her preferences, imagine the useless added files which will be incorporated to the disk! hence there exist the repositories wherein as per once need, download can always be facilitated....enjoy your ubuntu.

---

### Post by pushkarajthorat on 2010-03-02
> **byStanderone said:**
> 
your idea is fine, the main problem would be distribution and considering the files that would be added to the install disk that would support the needed dependencies that you mentioned...i would say it is not feasible or economical at the least...besides being impractical. each user has his/her preferences, imagine the useless added files which will be incorporated to the disk! hence there exist the repositories wherein as per once need, download can always be facilitated....enjoy your ubuntu.


Issue is regarding usability of naive user, not the disk space need or the bandwidth we will spend downloading ISOs.

I see that the basic library set is **not standardize** on any of the linux distros, so there are many redundant libraries present. Now if we one application developer chooses one and another developer chooses secondand so on.. we have a large set of libraries needed to run less amount of applications.

In my opinion, if should standardize library set, like we have on Windows, eg. .NET framework or all the .dlls under system32 folder. 

And as far as the cost of ISOs or bandwidth is concerned, it will not be bigger after standardizing the library set.

---

### Post by amrypma on 2010-03-03
> **pushkarajthorat said:**
> Issue is regarding usability of naive user, not the disk space need or the bandwidth we will spend downloading ISOs.

I see that the basic library set is **not standardize** on any of the linux distros, so there are many redundant libraries present. Now if we one application developer chooses one and another developer chooses secondand so on.. we have a large set of libraries needed to run less amount of applications.

In my opinion, if should standardize library set, like we have on Windows, eg. .NET framework or all the .dlls under system32 folder. 

And as far as the cost of ISOs or bandwidth is concerned, it will not be bigger after standardizing the library set.

One important difference in choosing standard libraries it that MS can say 'these are the standard libraries'. A linux distro can't really do that because, nothing is holding any developer back from using something else.

On the MS side there are many unused libs installed taking up space and specialized libs are usually home made or expensive to buy.(I to have been in dll-hell too) Still resulting in libraries with the same functionality.

On the linux side only libraries that are needed are installed. Yes even if two different libraries provide the same functionality. But because programmers like to flock to standards some libraries will gain popularity over others, reducing redundancies.

So you kind of end up at the same place where standard libraries are concerned.

Now for the n00bs.

Just about every distro uses a packaging system which keeps account of what software package needs to function. So naive users don't have to go and hunt for them. The simples way is to use Synaptic.

System -> Administration -> Synapitc

Look for the program you want and it'll tell you what other stuff needs to be installed and asks if your ok with synaptic making them also for installation.

[INDENT]Note: I think there is a simpler version called Software center but I've never used it.
[/INDENT]

Now if you want to program on your machine you need a bit more than the binaries of the libraries. You need the *headers* for those libraries so gcc or what have you can compile programs to use them. This type of packages usually have the '-dev' suffix.

I hope this has been of help.

---

### Post by pushkarajthorat on 2010-03-03
Hi amrypma, yes this is useful.. thanks for your reply.

---

### Post by amrypma on 2010-03-10
You're welcome.

---

