---
title: "Request: aDesklets"
date: 2005-05-04
forum: Ubuntu Backports
---

### Post by seph on 2005-05-04
Would this be possible to add?  They seem more stable than gDesklets.

---

### Post by 23meg on 2005-05-04
right, it would be cool to have them in the repos. i've been meaning to try them after my disappointment with gdesklets.

---

### Post by XDevHald on 2005-05-04
[QUOTE=23meg]right, it would be cool to have them in the repos. i've been meaning to try them after my disappointment with gdesklets.[/QUOTE]
 I think this would be really cool, here's the URL for some that are not sure what they might look like.

[http://adesklets.sourceforge.net/desklets.html]("http://adesklets.sourceforge.net/desklets.html")

Latest Release was 0.4.8 from SourceForge.

---

### Post by jdong on 2005-05-04
Sure. I'll package 0.4.8 now.

---

### Post by XDevHald on 2005-05-04
[QUOTE=jdong]Sure. I'll package 0.4.8 now.[/QUOTE]
 jdong, you make it sound so easy :p

---

### Post by jdong on 2005-05-04
Well, it really isn't too difficult to package a backport :)

It's done compiling, just waiting to upload. I'm currently uploading Acrobat Reader 7, which weighs in at 40MB -- so it's gonna be a while. ;)

---

### Post by 23meg on 2005-05-05
thanks for the effort. i can't find it in the repos yet, though; is it already there?

---

### Post by XDevHald on 2005-05-05
[QUOTE=23meg]thanks for the effort. i can't find it in the repos yet, though; is it already there?[/QUOTE]
 He might have them but didn't upload them to the back yet because I didn't receive them as well, so they could be on hold for now.

---

### Post by jdong on 2005-05-05
[http://backports.ubuntuforums.org/backports/dists/hoary-backports-staging/universe/binary-i386/](http://backports.ubuntuforums.org/backports/dists/hoary-backports-staging/universe/binary-i386/)

It's definitely in Hoary Backports Staging / universe.

Is it not showing up?

---

### Post by 23meg on 2005-05-05
got it now, thanks. but i have a problem: i can't configure any of the desklets. when i right click and choose "configure", nothing happens. anyone able to configure them?

---

### Post by McQuaid on 2005-05-08
I never heard of adesklets, but going to it's site I don't see what this brings to the table over gdesklets, karamba.

I mean, in their faq they should have a faq on why use this over gdesklets. Lighter on resources? more stable?  

Also does it use gtk2?  Doesn't really matter when actually looking at a desklet, just curious when right clicking and modifying a desklet as to what toolkit it uses.

---

### Post by 23meg on 2005-05-08
from what i can tell by right clicking, no, it doesn't use gtk2.

> I never heard of adesklets, but going to it's site I don't see what this brings to the table over gdesklets, karamba.

I mean, in their faq they should have a faq on why use this over gdesklets. Lighter on resources? more stable?  

why does it have to bring anything to the table? open source software doesn't have to have a specific target audience, reason to exist, specific opponents to "beat" etc; it just exists on its own and it's up to the user to make his choice on what software to use. no piece of software has to "make a case"; it's good enough that it's available as a free (as in freedom) choice. i haven't seen a single open source app that states in its faq why one should prefer it over its "rivals"; maybe they do exist, but i don't recall seeing any. in the open source world similar software isn't meant to "compete" in the proprietary/commercial sense but coexist in a mutually beneficial way.

---

### Post by McQuaid on 2005-05-08
Your right, it doesn't have to be there to 'beat' anything.  But, sometimes an open source project will be born out of a developer's itch.  e.g. Developer might love gdesklets but finds it takes too much resources and thinks he can do it better.  Or he might think it is a little limited in what can be done with the current version, and believes he can do it better and REQUIRES starting from scratch.

I emphasized requires because I think it would be better sometimes if someone joined the team (gdesklets in this case) if he believes he can offer improvements.  

But your right again, the developer might just want to start his own simply for the learning experience.

But users, well now they are a more fickle bunch.  If a user is using gdesklets, and hears about adesklets, but finds it's not as stable, has less features, and less applets, why is he going to use this?  Now, he might if the goal is to obtain better performance, or something over the existing popular one.  Of course, some users will try it anyways. I'm just saying that things become popular usually when they fill a need/desire.

Me for example, I like gdesklets but find some a little resource hungry, if I read that say 'adesklets typically uses 50% less resources' it would already be installed.  I skimmed over their faqs, and forums and have already moved on.

Note: In no way am I saying adeskets is unstable, less feature complete etc than gdesklets just making an example and I wish their devs all the best.

---

### Post by 23meg on 2005-05-08
i see your point, but still i'd rather read from independent peer reviews that "bdesklets is 55% more resource intensive than cdesklets", rather than in an faq on the cdesklets site. that way, chances are that i'll be seeing further opinions from other people, which may support or contradict the original review, and i'll take them into account too if they state clear reasons for their statements.

i think i'm too exhausted by years of attempts from companies and their paid reviewers to convince me that "product a is better / lighter / cooler than product b" ;)

---

### Post by Michal Fapso on 2005-05-11
Hello, I have installed adesklets, but when loading any applet, I am getting this error message:

```

Traceback (most recent call last):
  File "./yab.py", line 48, in ?
    import adesklets
  File "/usr/lib/python2.4/site-packages/PIL/__init__.py", line 36, in ?
    
  File "usr/lib/python2.4/site-packages/adesklets/initializer.py", line 60, in __init__
adesklets.error_handler.ADESKLETSError: adesklets interpreter initialization error - X Error of failed request:  BadWindow (invalid Window parameter)

Exception exceptions.AttributeError: <exceptions.AttributeError instance at 0xb7e773cc> in <bound method _Communicator.__del__ of <adesklets.communicator._Communicator instance at 0xb7d6574c>> ignored

```

I have not seen python before, so I do not know what is it all about :o(

---

### Post by cRoMo on 2005-06-13
New adesklets 0.4.10 has showed up. I tried to install it from debian repository, but I get following dependencies problem:

dpkg: dependency problems prevent configuration of adesklets:
 adesklets depends on python (<< 2.4); however:
  Version of python on system is 2.4.1-0ubuntu2.

---

