---
title: "Workbuntu - ubuntu for the habitual timewaster"
date: 2009-07-29
forum: The Cafe
---

### Post by Crick on 2009-07-29
Hi all,

The point of this post is that I had an idea and wanted to get some more expert opinion on feasibility, pointers to implement it, etc.

**Background**
I'm sure there is a sizable population of people who will use their computer to slack off in various ways, when they (or their employer) know that they should be doing work. Game/internet/IM addictions are basically the problem. Anything that is more addictive than work and accessible via computer is the problem.

If you are addicted to various computer-related time wasters and also require use of a computer to work, then you have a problem. People who aren't addicted in the same way don't have this problem and usually find it impossible to understand. It's certainly not all bad, more of a double-edged sword - the same OCD type personality that can give a person the capability to be an expert in the field can also be easily amused by lots of activities on a computer. And you can be fully realizing of how troublesome these activities can be and yet give in to them time and time again.

The way a default Ubuntu installation is set up, it is analogous to having a fully stocked bar in the home or workplace of an alcoholic (and harder drugs if you are so inclined). There are so many addictive ways to waste time, and as Ubuntu is set up you can't configure your computer to be maximally useful in a work environment and "in a moment of clarity" prevent yourself from wasting time.

A possible solution is to give up on any career requiring a computer to work, but that is not realistic or desirable for most. Some people have invested 4 or more years into a computer science, engineering degree etc.

**Solution**
My goal would be to build an application, a hack, some sort of configuration choice in the default install or an app downloadable through synaptic that has the following attributes or abilities:
1) All, or almost all the power of a default install. That is, all apps that have only a "work" type application, installable from main, universe, multiverse, and perhaps custom repos. 
2) All games, im or irc clients have been filtered out of synaptic or apt, so that they can't be installed. apt-get would have to refuse to install them too.
3) Sudo power is retained. I find that I use sudo too much to not give myself access to this. To be maximally useful, sudo has to be able to install work applications at a whim.
4) Once enabled, there is either no way to go back even with sudo, or it takes long enough (e.g. days, weeks, etc) to get your system back to default that the instant gratification of procrastination is delayed to the point where there is no alternative but to do your work. Or getting your system back to default is so hard that it starts to look like work.

5) Maybe eventually, a whitelist type setup for net access. However, this is less important because a zeroshell box between your computer and the internet can be configured to do this with a whitelist (you give half the password to a trusted friend or work colleague with instructions to prevent yourself enabling things, and you have the other half of the password for security reasons. Simply put all the sites necessary for your work in the whitelist - over time you will find that you can get most of your work done this way. Especially if you are a bit creative - e.g. .gov sites will often have useful info but not particularly addicting sites. Enable google to search with but not news.google etc. 

What would be nice though would be to be able to have unfettered internet access during set times, e.g. an hour at the end of the day, so that any out of the ordinary things can be researched. As you find things you need to research during the day, you can just make a note of them.

I imagine that if created, this would have use not only for various game addicts etc who realize they have a problem, but would also be perfect for a corporate setting.

So, is what I'm imagining possible? How much work would it be to implement? Any pointers? Does something like this already exist?

---

### Post by pigphish on 2009-10-01
I think what you are discribing is a variation of  [http://www.workrave.org/welcome/]("http://www.workrave.org/welcome/")

---

### Post by Sean Moran on 2009-10-01
I'd stand by that idea if the workrave site listed above is not the solution.   I have the word 'BossUbuntu' ringing in my ears although that would be taking things to extremes, especially after the reading the answers you have provided.

---

### Post by sliketymo on 2009-10-01
:confused:> **Crick said:**
> Hi all,

The point of this post is that I had an idea and wanted to get some more expert opinion on feasibility, pointers to implement it, etc.

**Background**
I'm sure there is a sizable population of people who will use their computer to slack off in various ways, when they (or their employer) know that they should be doing work. Game/internet/IM addictions are basically the problem. Anything that is more addictive than work and accessible via computer is the problem.

If you are addicted to various computer-related time wasters and also require use of a computer to work, then you have a problem. People who aren't addicted in the same way don't have this problem and usually find it impossible to understand. It's certainly not all bad, more of a double-edged sword - the same OCD type personality that can give a person the capability to be an expert in the field can also be easily amused by lots of activities on a computer. And you can be fully realizing of how troublesome these activities can be and yet give in to them time and time again.

The way a default Ubuntu installation is set up, it is analogous to having a fully stocked bar in the home or workplace of an alcoholic (and harder drugs if you are so inclined). There are so many addictive ways to waste time, and as Ubuntu is set up you can't configure your computer to be maximally useful in a work environment and "in a moment of clarity" prevent yourself from wasting time.

A possible solution is to give up on any career requiring a computer to work, but that is not realistic or desirable for most. Some people have invested 4 or more years into a computer science, engineering degree etc.

**Solution**
My goal would be to build an application, a hack, some sort of configuration choice in the default install or an app downloadable through synaptic that has the following attributes or abilities:
1) All, or almost all the power of a default install. That is, all apps that have only a "work" type application, installable from main, universe, multiverse, and perhaps custom repos. 
2) All games, im or irc clients have been filtered out of synaptic or apt, so that they can't be installed. apt-get would have to refuse to install them too.
3) Sudo power is retained. I find that I use sudo too much to not give myself access to this. To be maximally useful, sudo has to be able to install work applications at a whim.
4) Once enabled, there is either no way to go back even with sudo, or it takes long enough (e.g. days, weeks, etc) to get your system back to default that the instant gratification of procrastination is delayed to the point where there is no alternative but to do your work. Or getting your system back to default is so hard that it starts to look like work.

5) Maybe eventually, a whitelist type setup for net access. However, this is less important because a zeroshell box between your computer and the internet can be configured to do this with a whitelist (you give half the password to a trusted friend or work colleague with instructions to prevent yourself enabling things, and you have the other half of the password for security reasons. Simply put all the sites necessary for your work in the whitelist - over time you will find that you can get most of your work done this way. Especially if you are a bit creative - e.g. .gov sites will often have useful info but not particularly addicting sites. Enable google to search with but not news.google etc. 

What would be nice though would be to be able to have unfettered internet access during set times, e.g. an hour at the end of the day, so that any out of the ordinary things can be researched. As you find things you need to research during the day, you can just make a note of them.

I imagine that if created, this would have use not only for various game addicts etc who realize they have a problem, but would also be perfect for a corporate setting.

So, is what I'm imagining possible? How much work would it be to implement? Any pointers? Does something like this already exist?
What a party poopin' idea.

---

### Post by slakkie on 2009-10-01
So by keeping root rights via sudo you will basicly give them the tool to install everything you don't want to be installed.

wget [http://my.favorite.im/sources.tar.gz](http://my.favorite.im/sources.tar.gz) 
tar xvf sources.tar.gz
cd sources
./configure --prefix=/opt/myim && make && make test && sudo make install

And I have my favorite messenger again, without apt knowing about it. 

If you remove root rights, use kiosk mode, have a proxy that filters out sites, block IM ports on your network you should be able to do this. But only by using a distro... I don't see that happening, too many ways to circumvent the issues.

---

### Post by Keyper7 on 2009-10-01
You are offering no solution for the greatest timewaster of 'em all: random internet browsing.

---

