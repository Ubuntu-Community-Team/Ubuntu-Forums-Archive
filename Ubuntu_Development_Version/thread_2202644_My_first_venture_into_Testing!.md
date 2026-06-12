---
title: "My first venture into Testing!"
date: 2014-01-30
forum: Ubuntu Development Version
---

### Post by robin7 on 2014-01-30
It didn't work out very well, but hopefully the team can learn something from the attempt:

[http://adoptedsidekick.wordpress.com/2014/01/30/gee-that-didnt-work-out-very-well/](http://adoptedsidekick.wordpress.com/2014/01/30/gee-that-didnt-work-out-very-well/)

I've shared all this on the xubuntu development e-mail list, along with my hardware profile.  I tried setting up the profile and all that stuff on the wiki but I guess I don't know how.  Any pointers on doing that would be appreciated.

Anyway some folks might enjoy reading about a first-time tester's halting ventures into helping out in my own small way.

---

### Post by ventrical on 2014-01-30
First rule of thumb.

Never use the Update/upgrade Mangler. :) lol

[http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873](http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873)

---

### Post by grahammechanical on 2014-01-30
If things in the development branch worked out well all the time then testers would not be needed. Take my experience this morning. My usual Trusty install loaded to a broken desktop. No unity. I use recovery mode to update/upgrade and resume to get to a desktop. Then I rebooted and was able to get to a desktop without being in the llvmpipe fallback mode. So far, so good.

I decided to install the one Windows program that I need and which does not have a Linux version. So, far so good but it needed MS fonts. So, I installed  ttf-mscorefonts-installer through the Software Centre and I did not get an option to accept the EULA. Only an option to decline the EULA. 

Installation of the installer was successful but the MS fonts did not get installed. After several attempts I worked out the specific command to use in the terminal. Success! I have never had this problem in other stable versions of Ubuntu
 
This kind of stuff always happens when we do not have the time for messing around. Such is life.

Regards.

---

### Post by Bucky Ball on 2014-01-30
If you don't have the time to mess around I don't advise using Trusty as your main squeeze. ;)

I consider testing releases exactly that - testing - and I always have a rock solid LTS installed. Other things I refer to as my 'playthings' and they live in one of the playpens (their own partitions).

---

### Post by robin7 on 2014-01-30
It was fun!  I'm learning a little as I go, and I'm not sorry I tried.  I just hope it was useful for more than just educating me!

---

### Post by ventrical on 2014-01-30
> **grahammechanical said:**
> If things in the development branch worked out well all the time then testers would not be needed. Take my experience this morning. My usual Trusty install loaded to a broken desktop. No unity. I use recovery mode to update/upgrade and resume to get to a desktop. Then I rebooted and was able to get to a desktop without being in the llvmpipe fallback mode. So far, so good.

I decided to install the one Windows program that I need and which does not have a Linux version. So, far so good but it needed MS fonts. So, I installed  ttf-mscorefonts-installer through the Software Centre and I did not get an option to accept the EULA. Only an option to decline the EULA. 


  I have never directly installed ttf-mscorefonts-installer from the software center but I have installed it by using ubuntu-restricted from the software center and it works every time. I just wonder that if ttf-mscorefonts-installer was previously installed by installing ubuntu-restricted  if that would bring up that negative prompt.?

Thanks for sharing.

Regards..

---

### Post by ventrical on 2014-01-30
> **robin7 said:**
> It was fun!  I'm learning a little as I go, and I'm not sorry I tried.  I just hope it was useful for more than just educating me!

With ubuntu-testing the sky is the limit to what you can do! :)

One philosophy is to try to break a development cycle.  When we bust things we discover things ... and this is fun .. and fun is why we are here in U+1 ! :)

---

### Post by robin7 on 2014-02-01
I'd like to post my findings to QA, but I keep runing into this:

---

### Post by robin7 on 2014-02-02
It could have been great, I think, but I guess I'm done being a tester.  And I know I'm not the only person to hit such a stupid brick wall when trying to help out.

[Why Ubuntu has too few testers]("http://wp.me/p2fr89-4X")!

---

### Post by Bucky Ball on 2014-02-02
Testing is not for everyone and you obviously had no idea what you were getting into. Unsure what the rant on the link is on about, but anyway, good luck.

If you install a testing release, be prepared to jump through some hoops. I don't get it. 14.04 is not released until April. You were expecting a stable, solid install??? I wouldn't think so. It is not an easy ride ...

Reporting bugs and testing releases is a piece of cake, if that's what you actually want to do ... :-k

> **ventrical said:**
> ... try to break a development cycle.  When we bust things we discover things ... and this is fun .. and fun is why we are here in U+1 ! :)

^^^
This. If you're not there, don't run an unreleased Ubuntu. ;)

---

### Post by robin7 on 2014-02-02
> **Bucky Ball said:**
>  I don't get it. 14.04 is not released until April. You were expecting a stable, solid install??? 

Not at all. I was expecting to be able to REPORT the results of my testing the way the Wiki seems to suggest is the "proper" way.

I know better than to expect Alpha software to behave perfectly without any bugs or snags.  

But instead of jumping through all the hoops on a web site that is either broken or deliriously confusing, I'll simply play and report my findings to the e-mail list instead of putting myself through the aggravation and confusion of "joining the QA team" to report my findings "properly."

It's all good.

And by the way, my ranting blog post had *nothing* to do with how 14.04 performed in a test. It's about the confusing and frustrating process of joining the QA team.  Jus' say'n.

---

### Post by Bucky Ball on 2014-02-02
All good. ;)

---

### Post by Elfy on 2014-02-03
> But to report my findings I must create a hardware profile using my Single Sign-On account,I know blogs are blogs and full of inaccuracies - this is wrong. 

I've got no such thing.

If you have an issue with SSO - then you need to go to - [https://forms.canonical.com/sso-support/](https://forms.canonical.com/sso-support/)

---

### Post by robin7 on 2014-02-03
> **Elfy said:**
> I know blogs are blogs and full of inaccuracies - this is wrong. 

I've got no such thing. 

It's "Step Two" on [this page]("https://wiki.ubuntu.com/U+1/iso-testing-qa").  

> **Elfy said:**
> 
If you have an issue with SSO - then you need to go to - [https://forms.canonical.com/sso-support/](https://forms.canonical.com/sso-support/)

I did.  And I sent a support request via e-mail, which four days later has still not been answered.

I, apparently, am the *only* person *ever* to have trouble with "single" sign-on or with joining QA.  And apparently "Well, it works for me" is some kind of formula or incantation or something that fixes whatever is wrong.  Because no one has offered any *other* advice on how to get past the roadblock I described.

And apparently, I'm the only **muggle** in the Ubuntu community. But you know what? I have deleted the blog post, since I'm obviously mistaken about the lack of testers.  In fact *all* Ubuntu users are testers. Unknowingly and unwittingly so perhaps, but testers nonetheless, unless they're using a two or more year old LTS or some long-expired and unsupported version.

---

### Post by Elfy on 2014-02-03
I didn't say it wasn't on the wiki.

You said before you changed the blog you had to do it - you don't - I don't.

---

### Post by robin7 on 2014-02-03
It's all okay.  I missed something, can't follow directions, or whatever.  Since I can't manage the "simple" procedure required to join the QA team, I'll do something else to help out.

**I remain a devoted Xubuntu fanboy.** Call me "Robin the Fanboy Wonder."  While it's probably way past time I upgraded my hardware, I'm actually having a little contest with myself to see how long I can keep this old relic running without doing that.  

I bought this computer when my kids were little, and they're both grown up and out of the house now!  Xubuntu keeps it going strong and I'm absolutely delighted with the distro.  

But lesson learned... I jumped the gun, failed to follow directions somewhere along the way, and over-reacted like a spoiled brat.  So I'll find other ways to help out my favorite distro.  And I'll stick with 12.04 until it reaches the end of it's support life and then upgrade to Trusty, which will be three years old and probably bug-free by then, and with two more years of life left to it!

If I can keep this old relic running this beautifully until I become a grandfather that would be awesome.  So far I haven't needed to run off to Lubuntu, Puppy, or AntiX to meet that goal. And if my luck holds out that long maybe I'll have bragging rights to *something*, even if I can't manage to follow directions. ;)

---

### Post by Bucky Ball on 2014-02-03
About to chuck an SSD and 4Gb of RAM in my thirteen year old desktop relic currently running a P4 3GHz and 1Gb of RAM. There's life in the old beast yet! Still goes fine as is but beefing it up to use as audio workstation.

But apologies, I digress ... :-k

---

### Post by ventrical on 2014-02-04
> **robin7 said:**
> It's "Step Two" on [this page]("https://wiki.ubuntu.com/U+1/iso-testing-qa").  



I did.  And I sent a support request via e-mail, which four days later has still not been answered.

I, apparently, am the *only* person *ever* to have trouble with "single" sign-on or with joining QA.  And apparently "Well, it works for me" is some kind of formula or incantation or something that fixes whatever is wrong.  Because no one has offered any *other* advice on how to get past the roadblock I described.

And apparently, I'm the only **muggle** in the Ubuntu community. But you know what? I have deleted the blog post, since I'm obviously mistaken about the lack of testers.  In fact *all* Ubuntu users are testers. Unknowingly and unwittingly so perhaps, but testers nonetheless, unless they're using a two or more year old LTS or some long-expired and unsupported version.

 Just keep coming back to U+1 and report your experiences here. Your questions or theories may help somebody else find a solution. The whole concept of U+1 is that we don't have to be rocket scientists to be part of the contribution process. All of our contributions , large or small, correct or incorrect are like building blocks to the greater framework of the final release.

Regards..

---

### Post by Elfy on 2014-02-04
> All of our contributions , large or small, correct or incorrect are like building blocks to the greater framework of the final release.
+1 to that

---

### Post by ventrical on 2014-02-04
> **Elfy said:**
> +1 to that

:)

---

