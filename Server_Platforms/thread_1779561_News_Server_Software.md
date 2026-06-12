---
title: "News Server Software"
date: 2011-06-10
forum: Server Platforms
---

### Post by silveringking on 2011-06-10
Hi, its a pleasure to meet everybody. I have a question, I want to make my dedicated server, a news server (usenet) with high retention (1000+ days). Is it possible? What software should I use? How do I install it? (It is just for me).
I use Ubuntu lucyd linx (10.4 if I am not mistaken) and plesk 10.

Thank you so much!

Edit: It is both for posting and downloading news!

---

### Post by andrew.46 on 2011-06-11
If the server is just for you I suspect you would be happy with the proxy NNTP server leafnode. Version 1 is available in the Ubuntu repository and there is a slightly outdated guide to compiling version 2 on these forums. I have used leafnode 2 for some years for exactly the purpose you have mentioned and it is a very nice piece of software!

The only possible fly in the ointment is 'Plesk' which I am not familiar with at all :(.

---

### Post by silveringking on 2011-06-11
> **andrew.46 said:**
> If the server is just for you I suspect you would be happy with the proxy NNTP server leafnode. Version 1 is available in the Ubuntu repository and there is a slightly outdated guide to compiling version 2 on these forums. I have used leafnode 2 for some years for exactly the purpose you have mentioned and it is a very nice piece of software!

The only possible fly in the ointment is 'Plesk' which I am not familiar with at all :(.

Hello, I was just appointing the type of panel that I use, I use Parallel Plesk Panel (in order to setup databases, subdomains, etc etc). I dislike Cpanel or Direct Admin.

Edit: I was searching in the net, and the only thing I do find is INND (InterNet News Daemon) :P

Edit: How works that retention thing with leafnode?

Edit: andrew.46 you mean this guide of yours right? [http://ubuntuforums.org/showthread.php?t=676837&highlight=leafnode](http://ubuntuforums.org/showthread.php?t=676837&highlight=leafnode)

---

### Post by andrew.46 on 2011-06-11
> **silveringking said:**
> Edit: How works that retention thing with leafnode?

In Leafnode 2, which is the one I use, retention is set in the /etc/leafnode/config file and suggested settings are:

```

## Unread discussion threads will be deleted after this many days if
## you don't define special expire times. Mandatory.
expire = 150

```

This is my own setting of 150 days, I also define a shorter period for my local testing group:

```

## Non-standard expire times (glob(7) wildcard constructs possible). Optional.
## SYNTAX DIFFERS FROM THAT OF LEAFNODE 1.9!
## groups too big to hold articles 20 days:
# groupexpire = comp.os.linux.* 5
## very interesting, hold longer:
# groupexpire = any.local.newsgroup 100
## to archive a group, just set this to 24800 for now, which is 68 years

groupexpire = local.test 1

```

which expires my own group in a single day. Many possibilities there including 68 years :).

> **silveringking said:**
> Edit: andrew.46 you mean this guide of yours right? [http://ubuntuforums.org/showthread.php?t=676837&highlight=leafnode](http://ubuntuforums.org/showthread.php?t=676837&highlight=leafnode)

That is the one! There are a few holes in this one under Natty which I have been tossing up whether to address or not as the guide has not been all that popular.... I could get it fixed if you were interested? I keep involved with leafnode 2 rather than leafnode 1 as I run it at home but I also look after a [slackware installation script]("http://slackbuilds.org/repository/13.37/network/leafnode/").

---

### Post by silveringking on 2011-06-11
andrew.46, fix it in that topic if you please! Yet I have a doubt, I know the higher the retention is, the more space it occupies in my disk. I have a question then, suppose I go to a binaries group, and my retention is of lets say 1000 days, do I have to keep all the binaries of that group until 1000 days old? Because that's scary and I do not go to those so often...
About if I post binaries and my retention is 1000 days, do I have to keep that binary 1000 days in my sever right? But if one of those premium usenet servers keep it from 1100, they just copy the file to their server and keep it for 1100 days right?

Sorry for such noobish questions, but when I started to use usenet I never questioned myself about this...

Edit: Ok another question, I normally use grabit but I do want a client that serves both for posting and reading, using the combination powerpost+grabit maybe is a bit tricky to me to setup. What's the best option to use, that allows me both and yet keeping it simple to use like grabit?

---

### Post by andrew.46 on 2011-06-11
> **silveringking said:**
>  Yet I have a doubt, I know the higher the retention is, the more space it occupies in my disk. I have a question then, suppose I go to a binaries group, and my retention is of lets say 1000 days, do I have to keep all the binaries of that group until 1000 days old?

There are two settings that you can use, one is global and another can be per group. Thus you can keep all groups for 1000 days and one binary group for 30 days.

> **silveringking said:**
> Ok another question, I normally use grabit but I do want a client that serves both for posting and reading, using the combination powerpost+grabit maybe is a bit tricky to me to setup. What's the best option to use, that allows me both and yet keeping it simple to use like grabit?

I am afraid that I am not familiar with grabit but a quick look at it makes me suspect that it would not work or be needed with a proxy caching server. My own usenet usage is with individual.net --> Leafnode 2 --> slrn and I do not use binaries, this has been my setup for many years.

Give me a little while and I shall resurrect the leafnode 2 guide, there is another patch needed and Natty has changed a few things. I have spread myself a little thin with Ubuntu Forums guides :).

---

### Post by silveringking on 2011-06-11
> **andrew.46 said:**
> There are two settings that you can use, one is global and another can be per group. Thus you can keep all groups for 1000 days and one binary group for 30 days.

So I can keep, one specific group for 30 days while having a 1000 days retention? So if the group has 100 gb I have to keep 100gb in my disk right, and they will be deleted after those 30 days even if my retention is of 1000 days? That group won't be updated without my order right? But I would like to maintain a bit longer my own news :P . (Sorry for being such a noob)

> **andrew.46 said:**
> I am afraid that I am not familiar with grabit but a quick look at it makes me suspect that it would not work or be needed with a proxy caching server. My own usenet usage is with individual.net --> Leafnode 2 --> slrn and I do not use binaries, this has been my setup for many years.

Give me a little while and I shall resurrect the leafnode 2 guide, there is another patch needed and Natty has changed a few things. I have spread myself a little thin with Ubuntu Forums guides :).

Take your time... It doesn't matter!

Ps: There's a tool to know how much space a certain group occupies with X retention without downloading it?

---

### Post by silveringking on 2011-07-14
Sorry for ressurecting the thread but you told me you would give me an answer :P

---

### Post by andrew.46 on 2011-07-18
I have been a little slow with this one I am afraid :(. Good news is that I have partially renovated the leafnode guide and in its present form it should work well with Natty. I will revisit the guide in the next week to make it a little more cosmetically sound!

> **silveringking said:**
> So I can keep, one specific group for 30 days while having a 1000 days retention? So if the group has 100 gb I have to keep 100gb in my disk right, and they will be deleted after those 30 days even if my retention is of 1000 days? That group won't be updated without my order right? But I would like to maintain a bit longer my own news

Yes, you can set both a global limit for retention as well as individual rules for specific groups. I don't believe there is a method for deciding retention based on disk usage though, although I have been wrong before....

---

### Post by silveringking on 2011-07-26
Thank you! But my desktop is Natty, my server is still Lucyd LOL

---

### Post by andrew.46 on 2011-07-28
Unfortunately I only have a Natty setup so I can't test the guide on other versions of Ubuntu :(.

---

