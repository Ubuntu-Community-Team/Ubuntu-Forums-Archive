---
title: "ToriOS"
date: 2014-01-17
forum: Ubuntu, Linux and OS Chat
---

### Post by amjjawad on 2014-01-17
Hi,

[h=3]The Name[/h] Tori ( &#40165; ) means Bird in Japanese. A bird is a symbol for freedom which this project is all about.

[http://torios.top/](http://torios.top/)

 [h=3]The Announcement[/h] Ali, the founder of ToriOS has announced in 14th of January, 2014,  “the beginning of a new era for Old Hardware” and quite possibly a full  featured replacement for Windows XP.
ToriOS – a GNU/Linux Distribution – is the best option for NON-PAE machines.

 
  [h=3]General Features[/h] Minimal, Simple, Fast, Small.
ToriOS aims to give users the freedom of choice to build a system the way they want it, and in just the way they like.

 
  [h=3]Technical Features[/h] 1. ToriOS will always be based on the Long Term Support releases of Debian and Ubuntu, and be a [Long Term Support Operating System]("https://wiki.debian.org/LTS/")
2. There will be very minimal programs by default. The user has 100%  freedom to choose, download and install any program needed, wanted or  desired. ToriOS will work out-of-the-box with this very lightweight  system. The user can then decide the rest. ToriOS is planned to ship  with a minimal, fully functional graphical user interface.
3. Working old computers with [NON-PAE CPUs]("https://help.ubuntu.com/community/PAE"),  and other low resource computers, will not need to be wasted in  landfills. ToriOS will be the system to breathe new life into systems  that seem to be useless.
ToriOS will use [Non-PAE Kernel.]("https://blueprints.launchpad.net/torios/+spec/non-pae-support")
4. RAM Usage will be as minimal as possible – the target is to create a system that uses less RAM than [Lubuntu]("https://wiki.ubuntu.com/Lubuntu#System_Requirements") (and other distributions).
5. ToriOS will have a lightweight option for the default installer.  Ubiquity (Ubuntu’s default installer), as everyone may know, needs more  than 256MB RAM at the best and in some cases, it requires even more.
 
  [h=3]Why ToriOS?[/h] 1. The latest versions of Ubuntu and its official variants, specifically Lubuntu, do not support NON-PAE hardware by default.
2. While everyone can download, install and build a system with the Mini  ISO, some users have difficulties doing it. The installation of ToriOS  will be much simpler than installing the Mini ISO.
3. ToriOS will work out-of-the box. ToriOS will also provide a working  system with a Graphical User Interface after installation, as well as  one to test out on machines using a Live CD, this is contrary to the  Mini ISO where there is NO GUI, only a command line interface.
4. ToriOS is so special because of the community (team). It is based on  open, transparent team work. The community is very friendly, and work as  a family. No decision, no matter what, is made unless everyone votes  and the majority agree. It took 3 days to decide a name for this project  because everyone had to vote for it. This gives the community full  creative input.

Thank you!

---

### Post by amjjawad on 2014-02-08
1- [Website]("http://torios.org/") is up and running but still under constructions.

2- [Some roles are not yet filled]("https://blueprints.launchpad.net/torios/+spec/torios-team-structure"). We need interested and dedicated people for this project. We had someone for the Development but sadly she didn't wish to carry on and decided to focus on her own project.

The current team members are working hard to move things forward. While we don't have someone in charge for the Artwork Team, Rafeal (Lubuntu Artwork Team Leader) has offered his help. He is so supportive and he is a good friend of mine.

Anyone is more than welcome to join. 

If you have any question in mind, please ask :)

Thank you!

---

### Post by Tar_Ni on 2014-02-09
Very interesting!

This is exactly the kind of OS I need for my 1GB RAM, 2,8 Ghz proc and 80gig Hard drive. Lubuntu doesn't work well on it, due to sound issues. Booting the PC I had no sound then rebooting I got some.. and so on and so forth..

I just hope you guys don't plan to use the LXDE desktop environment otherwise I'll have to stay away from it, as my hardware doesn't seem do be fully recognized in it.. Not sure why. I've tried Peppermint OS, LXLE, ZorinOS LXDE and the same thing happened in all of them. Either annoying sounds issues again or the keyboard would not set properly regardless of what I tried with any LXDE OS I used. It shouldn't be such a pain for these basics. I am not saying it's no good though, simply that it doesn't work for me.

And keep the Ubuntu installer! I found that when it's too complicated to install an OS, the beginners will give up. (Linux Puppy is a good exemple at least to me)

---

### Post by lykwydchykyn on 2014-02-09
Was just looking over your discussions on WM/DE on launchpad.  I'm not sure the thing you're looking for exists.  You don't want LXDE or XFCE or any of their components, but you want something aimed at users of XP that looks nice.  Hrm...

I've spent a lot of time with lightweight distros and piecing together desktop environments from lightweight components over the years.  There's a reason why LXDE was created; piecing together a basic DE is easy, but making it cohesive and user-friendly is another thing.  Making it all that,  and then making it not look like 1998 warmed over is another feat yet.

I'd suggest looking at some of these distros and how they approach the desktop stack:

- Vector Linux Light
- Porteus
- Puppy Linux Wary
- Tinycore CorePlus
- Slitaz

Also, rather than trimming down the desktop environment, you might consider using a lighter X server like TinyX, XVesa, or XFBdev.  X11 itself is a beast on 10+ yr-old systems, no matter what you run in it.

---

### Post by amjjawad on 2014-02-10
Hi and thanks for posting :)

> **Tar_Ni said:**
> Very interesting!

This is exactly the kind of OS I need for my 1GB RAM, 2,8 Ghz proc and 80gig Hard drive.

 ToriOS will be designed to work on even less powerful machines than yours, that is our target :)

Is your machine a NON-PAE?

> Lubuntu doesn't work well on it, due to sound issues. Booting the PC I had no sound then rebooting I got some.. and so on and so forth..
So the only problem with Lubuntu is the sound issue?

> I just hope you guys don't plan to use the LXDE desktop environment otherwise I'll have to stay away from it, as my hardware doesn't seem do be fully recognized in it.. Not sure why. 

[LXDE  is not an option]("https://blueprints.launchpad.net/torios/+spec/de-wm"). We're not planning to create a new system with LXDE because there are Lubuntu and others with LXDE already. 

I'm a [former team leader for Lubuntu]("https://wiki.ubuntu.com/amjjawad/Lubuntu-Team"). I know almost all the strengths and the weakness of Lubuntu. LXDE has some bugs that aren't yet fixed which I personally don't like and would like to stay away from. Not to mention, [LXDE is not the lightest DE]("http://l3net.wordpress.com/2013/03/17/a-memory-comparison-of-light-linux-desktops/") :)

> I've tried Peppermint OS, LXLE, ZorinOS LXDE and the same thing happened in all of them. Either annoying sounds issues again or the keyboard would not set properly regardless of what I tried with any LXDE OS I used. It shouldn't be such a pain for these basics. I am not saying it's no good though, simply that it doesn't work for me.
Yes, I totally understand what you mean. For me, Lubuntu worked the best to my needs but then some bugs that aren't fixed and while all my machines are PAE and I have no problem with that, there are many with NON-PAE machines and I'd like to draw a smile on their face. I think it is a mistake to leave them without support while someone can do something. 

> And keep the Ubuntu installer! I found that when it's too complicated to install an OS, the beginners will give up. (Linux Puppy is a good exemple at least to me)
Yes, I know what you mean. This is one of the challenges we have. OBI Founder has [replied]("https://lists.launchpad.net/torios/msg00394.html"). We need to study [our options]("https://blueprints.launchpad.net/torios/+spec/default-installer") carefully.

Thank you again for your post :)

Feel free to join [our team on Launchpad]("https://launchpad.net/~torios") if you're interested to help!

---

### Post by amjjawad on 2014-02-10
Hello and thanks for posting :)

> **lykwydchykyn said:**
> Was just looking over your discussions on WM/DE on launchpad.  I'm not sure the thing you're looking for exists.  You don't want LXDE or XFCE or any of their components, but you want something aimed at users of XP that looks nice.  Hrm...

Oh, but just to make sure we both at the same page, the aim is not really to have something nice as XFCE or LXDE (yes, some think it is beautiful and like it while others don't - I'm still [contributing to LXDE]("https://wiki.ubuntu.com/amjjawad#LXDE") project anyway) but rather something 'Lightweight' or 'Very Lightweight' :)

One of ToriOS member did a test on Debain and this is what he sent me:

> I'm a bit in hurry, just some short sentences.  Xfwm4 was a bad idea, with all the things a user needs (menu, something  to draw the desktop) the memory usage was quickly around 60 MB, and it  wasn't even 'fullfeatured'. 
The best result I could achieve was  E17, with 47 MB RAM usage. Conditions were: no display manager (like  LightDM), no nm-applet, but with audio control and stuff. I used Debian  testing for rapid prototyping.



> **lykwydchykyn said:**
> I've spent a lot of time with lightweight distros and piecing together desktop environments from lightweight components over the years.  There's a reason why LXDE was created; piecing together a basic DE is easy, but making it cohesive and user-friendly is another thing.  Making it all that,  and then making it not look like 1998 warmed over is another feat yet.
It is good to know someone who has experience with lightweight DEs :)

As started on my previous post, I was one of [the most active members of Lubuntu]("https://wiki.ubuntu.com/amjjawad/Lubuntu-Team") Community but had to seek a different challenge when the direction of the project was moving on a path that I couldn't carry on with. 

You're right, each task is a challenge. We know that it is not going to be easy at all. We're looking now for a skilled developers to help us. 

> I'd suggest looking at some of these distros and how they approach the desktop stack:

- Vector Linux Light
- Porteus
- Puppy Linux Wary
- Tinycore CorePlus
- Slitaz


I'm a huge fan of SliTaz. Yet, ToriOS supposed to be different in the way it will offer [the packages]("https://blueprints.launchpad.net/torios/+spec/needed-packages") and being based on [Ubuntu]("https://blueprints.launchpad.net/torios/+spec/ubuntu12.04-mini-iso") (or Debian).

The idea is to offer a working system and give the user all the freedom to build that system the way he/she wants. Yes, we know that being going that path, ToriOS won't be for everyone but for those with some knowledge who can tweak the system to their needs. However, there are two skilled members who are good with Wiki and Documentations and I trust their experience and skills and I am sure they can make it as easy as possible even for someone who just started to use Linux. I am not worried much about that because I trust my team's abilities. 

> Also, rather than trimming down the desktop environment, you might consider using a lighter X server like TinyX, XVesa, or XFBdev.  X11 itself is a beast on 10+ yr-old systems, no matter what you run in it.

This seems a very nice and new idea. Do you have any experience with other display servers? this is something I haven't thought about it to be honest :)

Thanks a lot!

---

### Post by lykwydchykyn on 2014-02-10
> **amjjawad said:**
> 
I'm a huge fan of SliTaz. Yet, ToriOS supposed to be different in the way it will offer [the packages]("https://blueprints.launchpad.net/torios/+spec/needed-packages") and being based on [Ubuntu]("https://blueprints.launchpad.net/torios/+spec/ubuntu12.04-mini-iso") (or Debian).

I just posted those as examples of systems that have lighter-than-lxde desktops (though I think slitaz uses bits from LXDE).  Vector Linux Lite, for example, uses IceWM with (if memory serves) pcmanfm doing the desktop.  I ran it for a while on a celeron 800MHz.  If you can acheive your goals with e17, though, that's probably your best bet for balancing speed, looks, and friendliness.

> 
The idea is to offer a working system and give the user all the freedom to build that system the way he/she wants. Yes, we know that being going that path, ToriOS won't be for everyone but for those with some knowledge who can tweak the system to their needs. However, there are two skilled members who are good with Wiki and Documentations and I trust their experience and skills and I am sure they can make it as easy as possible even for someone who just started to use Linux. I am not worried much about that because I trust my team's abilities. 

Is it for experienced users or new users?  Is the default DE just a throwaway environment for install, or do you expect that users will stick with it?
> 
This seems a very nice and new idea. Do you have any experience with other display servers? this is something I haven't thought about it to be honest 

I have experience trying and failing to make them run on Debian-based distros.  :)  Many small/lightweight distros use these, though, like TinyCore, DamnsmallLinux, etc.  It makes things lighter but of course limits things like resolution, color depth, GPU features, etc.  Such a move would be a decisive step away from "general purpose distro" towards "super-lightweight distro", which is good and bad.

---

### Post by amjjawad on 2014-02-12
> **lykwydchykyn said:**
> I just posted those as examples of systems that have lighter-than-lxde desktops (though I think slitaz uses bits from LXDE).  Vector Linux Lite, for example, uses IceWM with (if memory serves) pcmanfm doing the desktop.  I ran it for a while on a celeron 800MHz.  If you can acheive your goals with e17, though, that's probably your best bet for balancing speed, looks, and friendliness.

How about [this]("http://imghost4you.com/?v=debianjess.png")?

>  Is it for experienced users or new users? 
Without good documentation, it won't be helpful for very fresh and new users to Linux. I have two members on my team and I'm the 3rd who can make life very easy for newcomers.

> Is the default DE just a throwaway environment for install, or do you expect that users will stick with it?
Kind of throwaway yes because the concept of this system is to give the user the choice and freedom to choose what he/she likes and wants.

However, day after day, I am kind of thinking to maybe include two default DE/WM but only if the time allows that.

Also, [see this]("https://lists.launchpad.net/torios/msg00436.html") ;)

> I have experience trying and failing to make them run on Debian-based distros.  :)  
It appears that Debian is lighter than Ubuntu Mini ISO as per our tests so far.


> Many small/lightweight distros use these, though, like TinyCore, DamnsmallLinux, etc.  It makes things lighter but of course limits things like resolution, color depth, GPU features, etc.  Such a move would be a decisive step away from "general purpose distro" towards "super-lightweight distro", which is good and bad.

Yes. I know what you mean. This is one of the challenges me and my team will face but if truth to be told, this is not our highest priority. If we could draw a smile on someone with Non-PAE machine that could go back to life again, that is our highest priority :)
We can then worry about being user friendly system or not. 

As I explained above, I do have lots of experience with Wiki and Documentation and I have people who can help with this so with great steps, the users will have options to tweak this system if his/her machine can handle it.

Let's see how things will go :)
I'm managing this project as per [Priorities]("https://lists.launchpad.net/torios/msg00449.html") and Votes. No decisions to be made unless we all vote. Also, we arrange our tasks as per priority - [example]("https://lists.launchpad.net/torios/msg00462.html") :)

Thanks for posting :)

---

### Post by amjjawad on 2014-02-12
Please help ToriOS team to choose between two designs for the official logo

Which one you like the most?

[ATTACH=CONFIG]250286[/ATTACH]

Or

[ATTACH=CONFIG]250287[/ATTACH]

**Tip:** [I]Tori (**&#40165;**) means Bird in Japanese

[/I][[SIZE=4]**Poll is here **[/SIZE]]("https://docs.google.com/forms/d/1OytMW9pa1v4yUcy2_V9jbXe4xV8GRPMLo5E2vNJDhPA/viewform")

Thank you so much!

---

### Post by lykwydchykyn on 2014-02-12
> **amjjawad said:**
> How about [this]("http://imghost4you.com/?v=debianjess.png")?

JWM is probably one of the lightest.  If light & fast is the priority and the environment isn't intended for long-term use, it would be a good choice.

> 
Without good documentation, it won't be helpful for very fresh and new users to Linux. I have two members on my team and I'm the 3rd who can make life very easy for newcomers.


Kind of throwaway yes because the concept of this system is to give the user the choice and freedom to choose what he/she likes and wants.

Just my opinion, but it seems like you really want to decide one way or the other.  Otherwise you'll waste a lot of time trying to make a minimal environment useful and user-friendly.

> 
However, day after day, I am kind of thinking to maybe include two default DE/WM but only if the time allows that.

Here's a brainstorm, but howabout a piece of software that analyzes the CPU, RAM, and Video hardware and recommends a choice of DE's to the user?  E.G., the program detects a Pentium 4 with 1 GB of RAM and intel hardware, so it offers LXDE or enlightenment as choices (with screenshots and some bullet points, of course).

> 
Also, [see this]("https://lists.launchpad.net/torios/msg00436.html") ;)

By developing your own WM, do you actually mean WM or DE?  Seems like the world [has enough window managers](http://www.gilesorr.com/wm/table.html) as it is.  And what with X11 on the way out, it doesn't seem sensible to start developing a new one.  Makes more sense to build up some kind of User Experience from existing parts and solidify it as the needs really gel (sort of like what's happening with Unity).
> 
It appears that Debian is lighter than Ubuntu Mini ISO as per our tests so far.

That's a whole other can of worms, though I'm not surprised.


> 
Yes. I know what you mean. This is one of the challenges me and my team will face but if truth to be told, this is not our highest priority. If we could draw a smile on someone with Non-PAE machine that could go back to life again, that is our highest priority :)
We can then worry about being user friendly system or not. 

As I explained above, I do have lots of experience with Wiki and Documentation and I have people who can help with this so with great steps, the users will have options to tweak this system if his/her machine can handle it.

Let's see how things will go :)
I'm managing this project as per [Priorities]("https://lists.launchpad.net/torios/msg00449.html") and Votes. No decisions to be made unless we all vote. Also, we arrange our tasks as per priority - [example]("https://lists.launchpad.net/torios/msg00462.html") :)

Thanks for posting :)

Well, I sincerely wish you luck!

---

### Post by amjjawad on 2014-02-14
Hi and thanks for posting :)

> **lykwydchykyn said:**
> JWM is probably one of the lightest.  If light & fast is the priority and the environment isn't intended for long-term use, it would be a good choice.
We're still doing lots of testing and experiments. Once we review our findings, we then decide which WM/DE will be our default.

> Just my opinion, but it seems like you really want to decide one way or the other.  Otherwise you'll waste a lot of time trying to make a minimal environment useful and user-friendly.
There is nothing as perfect and will never ever be. Also, you can't, no matter what, make everyone happy, no doubt about that.
However, creating a balance is good idea and I do believe we can do it. 

What is the lightest official flavour of Ubuntu as the world know it? the answer is Lubuntu, right?
Lubuntu as of today doesn't support Non-PAE machines by default + it is not very very lightweight + despite it is beautiful and easy, some thing the otherwise and some thing it's not user-friendly (how I know? I've been a leader for Lubuntu for 2 years and I've read each and every feedback as I was in charge of all its social media channel). 

ToriOS, if we shall go for Ubuntu as the base of our system, should be even lighter than Lubuntu and does support Non-PAE machines and also LTS (I know Lubuntu 14.04 supposed to be LTS - [I did create a youtube video]("http://www.youtube.com/watch?v=JxV4XjOksYQ") to promote that myself). 

The idea is to provide a better option than Lubuntu for the machines that Lubuntu couldn't help.
Also, give a simple system to the users as the base of what they will build themselves. We count on our skills for this. Our Wiki Team that I trust, I am sure they will provide all the needed steps to achieve that for those who don't know. By doing that, ToriOS will not longer be for expert of non-beginners but will be for everyone. Being easy or hard, that is subject to the users themselves to decide.

Let's see ... we are still at the very beginning ;)

> Here's a brainstorm, but howabout a piece of software that analyzes the CPU, RAM, and Video hardware and recommends a choice of DE's to the user?  E.G., the program detects a Pentium 4 with 1 GB of RAM and intel hardware, so it offers LXDE or enlightenment as choices (with screenshots and some bullet points, of course).
If there is something like that, please share :)

> By developing your own WM, do you actually mean WM or DE?  Seems like the world [has enough window managers]("http://www.gilesorr.com/wm/table.html") as it is.  And what with X11 on the way out, it doesn't seem sensible to start developing a new one.  Makes more sense to build up some kind of User Experience from existing parts and solidify it as the needs really gel (sort of like what's happening with Unity).
I mean a Window Manager (WM). And, we're not re-inventing the wheel nor anything. Developing our own WM has nothing to do with ToriOS current Development. If you read [the announcement]("https://lists.launchpad.net/torios/msg00436.html"), you will come to know that having our own WM is a Sub-Project that should never ever affect the main project, that is developing ToriOS and that is exactly why the team is doing tests and experiments ;)
New member joined us recently and he suggested that idea so I wanted to encourage him and allow him to prove himself. He has lots of experience as he said and works as Release Manager or something similar in Real Life. So, why not have something 'unique' for ToriOS? I see no harm with that. Some projects develop their own software as per their needs :) Not sure if I made it clear enough?

The target/plan now is to keep looking for the best WM for ToriOS while another sub-project is on going. Overkill and extra headache? no doubt but again, there is someone who is willing to do so.

> That's a whole other can of worms, though I'm not surprised.

I do like challenges a lot. That is why I am insisting to use Ubuntu as the base ;) however, it is not a strict requirement. If for the best of the users and the project to go for Debian, so be it. But as long as we still can go deeper and deeper + we believe in our skills, I see no reason to give up now and just go for Debia without trying. I don't give up and will never will unless each and every possibility is a dead end. 

> Well, I sincerely wish you luck!
Thank you, appreciate that :)
Our team is growing bigger and new skilled people are asking to join. I am glad to see that and hope we could do something 'useful' and 'different'.

---

### Post by amjjawad on 2014-02-16
Hi,

ToriOS Logo has been decided:
[http://torios.org/news/the-winner-logo/](http://torios.org/news/the-winner-logo/)

Time for ToriOS Website to go from Alpha to Beta:
[http://torios.org/news/website-feedback/](http://torios.org/news/website-feedback/)

Thank you!

P.S.
If you're interested to join, please let us know :)

---

### Post by amjjawad on 2014-02-22
1- ToriOS Website Development:
[http://torios.org/news/website-development/](http://torios.org/news/website-development/)


2- Results of ToriOS Website Feedback:
[http://torios.org/news/results-of-website-feedback/](http://torios.org/news/results-of-website-feedback/)

3- One of our developers will provide a downloadable ISO file for a pre-alpha build of ToriOS :)

4- ToriOS IRC Channel:
[http://torios.org/news/torios-irc-channel-on-freenode/](http://torios.org/news/torios-irc-channel-on-freenode/)

5- ToriOS Social Media Channels:
[http://torios.org/news/social-media-channels/](http://torios.org/news/social-media-channels/)

Thank you!

---

### Post by Tar_Ni on 2014-02-24
So will ToriOS (nice logo by the way) be based on Ubuntu? And what will be the system requirements for the first release?

---

### Post by amjjawad on 2014-02-24
> **Tar_Ni said:**
> So will ToriOS (nice logo by the way) be based on Ubuntu? And what will be the system requirements for the first release?

Hi and thanks for posting :)

Thanks for the feedback, we had a long process until we chose the logo and glad you like it :)

Yes indeed, it should be based on Ubuntu. The idea of this project started as to create a lightweight of Lubuntu (which is already the lightweight version of Ubuntu) and then the idea has developed further. That leads to your next question :)

One of our team members achieved less than 50MB of RAM Usage the other day (but if truth to be told, he was playing with Debian). We haven't yet done any ISO because we're trying to go as far as we could. That said, whatever Lubuntu will fail to help, ToriOS should be the way to go.
In other words, we do hope to go below 256MB of RAM and most importantly, ToriOS should support Non-PAE CPU. This is our highest priority.

One of my good friends and former QA Lead of Lubuntu is working on a Community Kernel that supports Non-PAE machines which should be available for everyone to use :)

ToriOS should be lighter than Lubuntu and has different path. It leaves the choice to the users to chose their own path with their system and to build it the way they like.

Hope that helps!

---

### Post by amjjawad on 2014-02-25
And finally, some real fun is about to begin :)

[http://torios.org/news/torios-development-preview/](http://torios.org/news/torios-development-preview/)

---

### Post by Tar_Ni on 2014-03-02
Nice stuffs, can't wait to see some screenshots.

So, based on Ubuntu 12.04 will ToriOS 1 somehow be a LTS?

Anyway, I have a [LEFT]Dell EC280 Mini-ITX  PC with [/LEFT]
1.2Ghz proc and 512MB RAM laying around. It's not that old actually, it was released in 2007 for basic taks with XP but really cannot handle much today  with a standard OS and so would be considered ''useless'' by many. I am not sure Lubuntu would work well on it and Puppy Linux is such a pain to install for a newbie like me.

I am waiting for this ToriOS, a real alternative to Puppy and Lubuntu and that seems very interesting.

---

### Post by amjjawad on 2014-03-19
Hi,

> **Tar_Ni said:**
> Nice stuffs, can't wait to see some screenshots.
Yes, me too :)

>  So, based on Ubuntu 12.04 will ToriOS 1 somehow be a LTS?
Yes, we're interesting in an LTS release but whether it is based on 12.04 or not? some updates happened lately that we might (or might not) re-consider our options - [see this, please]("https://lists.launchpad.net/torios/msg00532.html").

There are some friends of mine I used to be with them on the same team (Lubuntu) are working on this issue (support for old machines) for sometime now. So, I was thinking to have a meeting with them to be up-to-date with what they're up to and see which option might help ToriOS instead of re-inventing the wheel.

I will keep everyone updated about what will happen, that is for sure.

> Anyway, I have a [LEFT]Dell EC280 Mini-ITX  PC with [/LEFT]
1.2Ghz proc and 512MB RAM laying around. It's not that old actually, it was released in 2007 for basic taks with XP but really cannot handle much today  with a standard OS and so would be considered ''useless'' by many. I am not sure Lubuntu would work well on it and Puppy Linux is such a pain to install for a newbie like me.
With 512MB RAM, Lubuntu should be just fine on that machine. 


> I am waiting for this ToriOS, a real alternative to Puppy and Lubuntu and that seems very interesting.
As for ToriOS, we're trying to creating something that should be even faster and more lightweight than Lubuntu. Also, support a wide range of old hardware as much as we can.

The challenge is whether to use a new kernel series or old one? 

Phill for example, thinks it is better to use a new one.
Me and some other think it is better to use an old one. Why? because some drivers and support for very old machines are not found on the newer kernels.

That is why, I need to have a meeting with my friends to find out what we could do next :)

As for ToriOS overall development, Real Life was the main reason why there is nothing happened yet.

A month ago or less, we were supposed to have an ISO to look at but not yet happened. I talked to Alex (ToriOS Developer) and he apologized for being so busy.

Thank you!

---

### Post by amjjawad on 2014-03-23
Hi,

Nothing really new but thought to update with the [latest news]("http://torios.org/news/dear-real-life/").

Sadly, not great news at all. However, I'm full of hope that this will be changed soon :)

Thank you!

---

### Post by vasa1 on 2014-04-18
Any news here?

---

### Post by amjjawad on 2014-04-23
> **vasa1 said:**
> Any news here?

Hi,

Yes, there you go :D

[http://torios.org/news/time-for-torios/](http://torios.org/news/time-for-torios/)

Thank you!

---

### Post by amjjawad on 2014-06-08
Hi,

ToriOS is looking for a new QA Lead

Please read for more details:

[http://torios.org/news/qa-lead/](http://torios.org/news/qa-lead/)

Thank you!


-----------------------

The good news is:
[http://torios.org/news/torios-pre-alpha-is-coming-very-soon/](http://torios.org/news/torios-pre-alpha-is-coming-very-soon/)

Thank you :)

---

### Post by amjjawad on 2014-07-08
Hi,

[http://torios.org/news/changes-within-torios-project/](http://torios.org/news/changes-within-torios-project/)

---

### Post by amjjawad on 2014-07-12
Hi,

More news and updates from ToriOS:
[http://torios.org/news/weekly-meetings/](http://torios.org/news/weekly-meetings/)

---

### Post by amjjawad on 2014-08-30
Hi,

After very long wait, here is ToriOS Alpha:

[http://torios.org/iso.html](http://torios.org/iso.html)

We need your help to test it and report back :)

To contact us:
[http://torios.org/contact.html](http://torios.org/contact.html)

Thank you!

---

### Post by amjjawad on 2014-10-13
Hi,

Latest build for ToriOS:
[http://torios.org/news/torios-latest-build-is-ready-for-testing/](http://torios.org/news/torios-latest-build-is-ready-for-testing/)

ToriOS RAM Usage:
[http://torios.org/news/how-lightweight-torios-could-be/](http://torios.org/news/how-lightweight-torios-could-be/)

ToriOS on DistroWatch.com:
[http://distrowatch.com/weekly.php?issue=20141013#waiting](http://distrowatch.com/weekly.php?issue=20141013#waiting)

We are looking for marketing people to join and help:
[https://twitter.com/Tori_OS/status/521616951907328001](https://twitter.com/Tori_OS/status/521616951907328001)

For more, join the mailing list/contact us:
[http://torios.org/contact.html](http://torios.org/contact.html)

Many thanks :)

---

### Post by mastablasta on 2014-10-16
downloaded and waiting for some free time to try it out. How much hard disk space does it need?

I am thinking it could replace Chrunchbang on ye old laptop. but we'll see how it fares first in vbox, then live, then maybe...

---

### Post by sudodus on 2014-10-16
It depends how much you want to add/install and how much space you need for personal data. I think the original installed system fills less than 2 GB disk space, but I would install it into partition with 8 GB (or more).

Edit: I think you can try it with a vbox drive of 4 GB or slighly more (because the installer might not want to install into less than 4 GB).

---

### Post by mips on 2014-10-16
> **amjjawad said:**
> 
ToriOS RAM Usage:
[http://torios.org/news/how-lightweight-torios-could-be/](http://torios.org/news/how-lightweight-torios-could-be/)


Hi,

When I open [https://lists.launchpad.net/torios/msg01142.html](https://lists.launchpad.net/torios/msg01142.html) all I see is garbled characters?

---

### Post by amjjawad on 2014-10-31
> **mips said:**
> Hi,

When I open [https://lists.launchpad.net/torios/msg01142.html](https://lists.launchpad.net/torios/msg01142.html) all I see is garbled characters?

Hi and so sorry for the late reply, my real life is yet again messed up and it is not easy to find yourself into very different time zone so it will take sometime :)

Well, yes, that is because there was an image and for some reason, Launchpad will not show that as an attachment and instead, it will show these weird stuff. It happened with me as well.

Here is a better version:
[http://torios.org/news/how-lightweight-torios-could-be/](http://torios.org/news/how-lightweight-torios-could-be/)

Tip: I'd suggest you subscribe to our mailing list if you are interested :)

---

### Post by amjjawad on 2014-10-31
> **mastablasta said:**
> downloaded and waiting for some free time to try it out. How much hard disk space does it need?

I am thinking it could replace Chrunchbang on ye old laptop. but we'll see how it fares first in vbox, then live, then maybe...

Hi,

ToriOS is very VERY lightweight system that only needs minimal hardware. That said, for the system only, I don't think you need more than 2-3 GB as HDD space. However, if you wish to install packages, etc then of course more.

As long as we are at the alpha stage, you are most likely going to use a virtual machine so you can change the size of the disk as you like. For me, I use Oracle VB and choose Dynamic disk. Because I use that for tests only, I don't really need more than 6-8 GB for Ubuntu GNOME. For ToriOS, you need less :)

Crunchbang is full OS with many packages installed. ToriOS has different philosophy. We are sure that sooner or later, it will replace all the lightweight systems that we know ;) only time will tell :)

---

### Post by amjjawad on 2014-11-02
Hi,

For anyone who might be interested, here is the very latest meeting we had:

> This is the log of tonight meeting (morning in my time): 
[http://phillw.net/meetbot/torios/2014/torios.2014-11-01-20.10.moin.txt](http://phillw.net/meetbot/torios/2014/torios.2014-11-01-20.10.moin.txt) 

For the full log: 
[http://torios.org/news/team-weekly-meetings/](http://torios.org/news/team-weekly-meetings/)

The reason I am posting it here is because at that meeting, we discussed lots of NEW ideas. I am planning to implement these ideas and take that to the next level.

Also, ToriOS beta is around the corner as well.

Here is my test report for the daily build of 25102014:
[https://lists.launchpad.net/torios/msg01214.html](https://lists.launchpad.net/torios/msg01214.html)

Things are getting very close to be stable and work nicely :)

Thanks!

P.S.
We need contributors so if you have free time + interested about the idea of ToriOS, please join!

---

### Post by amjjawad on 2014-12-30
Hi everyone,

For those who have never heard of OBI, here is a post:
[http://torios.org/news/OBI](http://torios.org/news/OBI)

This post explains about OBI, Why ToriOS is going to use OBI and some updates about the project.

Happy reading :)

---

### Post by amjjawad on 2015-02-03
[ATTACH=CONFIG]259678[/ATTACH]

ToriOS Pre-Beta :)

The screenshot says it all :)

By the way, we have new domain: torios.net as we have a serious problem with torios.org (our system admin has faded away - yes, we learned the lesson) and we can't access it. What you see now on the website, this is the last time we had access to it :(

The new website should be ready hopefully soon and Beta is ready too.

Please see:
[https://lists.launchpad.net/torios-dev/msg00015.html](https://lists.launchpad.net/torios-dev/msg00015.html)

ToriOS beta is not going to be for testing only, but stable to the point that we shall call it: ToriOS 0.5 and we shall ask users to use that on daily basis. That is indeed why it took us so long ...

Also, ToriOS now has two teams on Launchpad:

[LIST=1]
[*]General: [https://launchpad.net/~torios](https://launchpad.net/~torios)
[*]Development and QA: [https://launchpad.net/~torios-dev](https://launchpad.net/~torios-dev)
[/LIST]

Our news section is the only site we have access to so we try to keep that updated with our news. You can always refer to logs:
[http://torios.org/news/team-weekly-meetings/](http://torios.org/news/team-weekly-meetings/)

You see, we're not dead :) we're so active but behind the scenes! 

Thank you!

---

### Post by flaymond on 2015-02-03
Hey, I'm a Linux beginner and a programming beginner. I wish to help in development also to gathering my first experiences to work on source code. At least, with bug tracking? Anyway, I wish your luck with the ToriOS. :D

(Actually, I'm looking for this OS for a long time. My PC is not good with Lubuntu, since my PC very slow to use it. I hope the ToriOS will don't have much issues with this old pc.)

Also, just wanna inform that at ToriOS website, there is no download size of the ISO, I don't know how big it is actually.

---

### Post by amjjawad on 2015-02-03
> **InterProg said:**
> Hey, I'm a Linux beginner and a programming beginner. I wish to help in development also to gathering my first experiences to work on source code. At least, with bug tracking? Anyway, I wish your luck with the ToriOS. :D

Hi and thanks for posting :)
Everyone is more than welcome to join us. We're few in quantity but super high in quality. You would learn a lot, enjoy a lot and can do a lot.

That said, you need a Launchpad account and you need to join the teams I mentioned on my previous post ;)

>  (Actually, I'm looking for this OS for a long time. My PC is not good with Lubuntu, since my PC very slow to use it. I hope the ToriOS will don't have much issues with this old pc.)
ToriOS has started as an idea to create a community spin for Lubuntu for Non-PAE machines and/or old machines that Lubuntu can't handle nicely.
Lubuntu team has rejected the idea and wasn't excited about it. I have decided to carry on with the idea and created new project.
It is very safe to say that ToriOS is much lighter than Lubuntu and super fast :)

We're so close to Beta but real life and the website issue is holding us back and keeping us slow ... and above all, our pursuit for semi-perfection is making us slow as well. We're trying to solve all the bugs as much as we can ...

> Also, just wanna inform that at ToriOS website, there is no download size of the ISO, I don't know how big it is actually.

The link on the website is very old :(
Sadly, we have no access to remove it as I explained on my previous post. Soon, torios.net should be ready.

The best way is to join our Launchpad teams to stay in the loop.

Thank you!

---

### Post by amjjawad on 2015-02-06
Hi,

I just read:
[http://crunchbang.org/forums/viewtopic.php?id=38916](http://crunchbang.org/forums/viewtopic.php?id=38916)

Sad but true :(

That's why ToriOS has been founded (just one of the reasons). I hope the founder of CrunchBang go back to the project just like what happened with the founder of Bodhi Linux but whether that will happen or not, ToriOS will be very ready very soon and hope we could be a help and support to those users of old machines.

Nothing in this life worth a smile on someone's face. Helping others and spread humanity is a mission we should hold and carry on with. That's why I love Ubuntu and that's why I'm using + contributing to Linux :)

Thank you!

---

### Post by amjjawad on 2015-02-06
Hi,

[https://lists.launchpad.net/torios/msg01652.html](https://lists.launchpad.net/torios/msg01652.html)

Thanks!

---

### Post by amjjawad on 2015-02-24
Hi,

[http://torios.net/torios-0-5-rc2-has-been-released/](http://torios.net/torios-0-5-rc2-has-been-released/)

We're very very close :)

Help is needed to test and if you are good with packaging and/or developing, please help us. The reason why it took so long because we have only one developer working only whenever he got some free time to do so.

We appreciate if we could get some extra hands!

Many thanks :)

[ATTACH=CONFIG]260189[/ATTACH]

---

### Post by marseille2 on 2015-02-24
This is just what I need for my netbook! I'm taking the beta out for a test drive very soon;)

---

### Post by sudodus on 2015-05-24
Congratulations Israel Dahl and Hi all toriosadores,

Today's (May 24 2015) version of [ToriOS-beta]("http://phillw.net/isos/torios/") is a great improvement.

I tested it live and I installed it, this time into my old IBM Thinkpad T42 with a Pentium M CPU without a PAE flag.

The live session works - and the OBI works.

And the iso file is within CD size, 669 Mibibytes, so there is a margin to the limit 700 Mibibytes (or to be more exact, I think 703 Mibibytes) for growth due to upstream updates.

The installed system works - also nm-applet and my wifi. After installing some restricted-extra multimedia software, I could even
listen to a youtube clip from last night's Eurovision Song Contest,

```
sudo apt-get install lubuntu-restricted-extras
```

[The winning song or should I say performance]("https://www.youtube.com/watch?v=3avE4Zsp14g")

I have not tested everything, but I am very happy with the current version of ToriOS :-)

Best regards
Nio

---

### Post by flaymond on 2015-05-24
[QUOTE=sudodus]Today's (May 24 2015) version of [ToriOS-beta]("http://phillw.net/isos/torios/") is a great improvement.[/QUOTE]

+1

Israel Dahl is really focusing on this project, and the improvement is very big. Thanks to you too sudodus, for helping Israel Dahl improving ToriOS day-by-day! :D

---

### Post by sudodus on 2015-05-24
And thanks to you InterProg for your contributions, reporting bugs and suggesting improvements :-)

---

### Post by amjjawad on 2015-05-29
I feel super bad that my personal problems, real life, etc ... are blocking me to do anything useful to my own project :'(
But, I do trust ToriOS team that I have spent lots of time, energy and efforts building it and it is as strong and solid as rock so I am not worried and if ToriOS will make it and release the 1st version, that is more than enough to be proud of this great team and what they have done so far. I think they have challenge the impossible to the very last bit of it. WELL DONE, ToriOS Team!

It's a pleasure and an honour to work with you and despite I feel bad for the lack of contributions, the smile that we shall draw on many faces is all what does really matter. So many people out there need ToriOS :)

Respect!

---

### Post by amjjawad on 2015-06-09
Hi,

ToriOS has now more features and we're very very close to the final release :D
We're not at 0.8 (AKA Beta) and once we test the new features and add some missing other features and fix some minor bugs, we'll be ready for 0.9 (AKA RC).

[http://torios.net/more-new-features/](http://torios.net/more-new-features/)

The more testers we get, the faster we release the first stable version :)

Thank you!

---

### Post by sudodus on 2015-07-31
[SIZE=4]ToriOS beta tarball[/SIZE]

There is a tarball with ToriOS (beta version) updated from the repositories yesterday (July 30, 2015).

[ToriOS-pae-OEM_prec_use-by-OBI-in-trusty.tar.xz](http://phillw.net/isos/one-button-installer/tarballs/ToriOS-pae-OEM_prec_use-by-OBI-in-trusty.tar.xz)

This tarball was made with zmktbl in the [One Button Installer](https://help.ubuntu.com/community/OBI), OBI, version 3.1, and it can be installed with the same version of the OBI. ToriOS is installed in OEM mode, and should work well in old and middle-aged computers. It is a 32-bit system and the installation method works in BIOS mode. Use another linux distro and other installation method to install in UEFI mode (for example a 64-bit version of an Ubuntu flavour and mkusb).

Edit:

[SIZE=4]ToriOS beta compressed image file[/SIZE]

ToriOS can also be installed 'directly' with [mkusb](https://help.ubuntu.com/community/mkusb), for example into a pendrive of at least 8 GB from the following compressed image file

[dd_ToriOS-LubuCore-pae-OEM_precise_7.8GB.img.xz](http://phillw.net/isos/linux-tools/compressed-images/dd_ToriOS-LubuCore-pae-OEM_precise_7.8GB.img.xz)

Both of these images (the tarball and the compressed image file) are made from an OEM system, where Lubuntu Core was installed in order to help the system for final installation (ubiquity) render the graphical user interface correctly. However, you should ***focus on ToriOS***. (Do not use the Lubuntu session, because it has passed end of life and receives no security updates).

Edit 2:

I uploaded two screenshots: yes, your eyes are telling the truth - this system, based on Ubuntu 12.04 LTS runs idle using only 79 MB RAM.

Edit 3:

I installed with mkusb from the compressed image file into my IBM Thinkpad with a Pentium M, that lacks a PAE flag. This particular ToriOS system comes with fake-pae and the 3.2.0-88-generic-pae kernel. See the third attached file and good luck :-)

---

### Post by amjjawad on 2015-09-11
Hi all,

This is to confirm that we shall 'stop' waiting for the newer versions of JWM. We shall 'now' focus on the **minor bugs** and **missing features** of ToriOS and, the team is dazzling me day after day. I, the founder of this project, did NOT imagine ToriOS will be like that, not even in my dreams so thanks a million for each and everyone who invested 1 second of his/her time on ToriOS.

To download the latest build, [here is the link]("http://phillw.net/isos/torios/oldISO/ToriOS-2015-09-06-beta-precise.iso") - the server was down lately but it is up and running now.

MD5SUM:
```
ee04ec76b61651db3ebd27791e75fb74  oldISO/ToriOS-2015-09-06-beta-precise.iso
```

More information can be found here:
[http://phillw.net/isos/torios/](http://phillw.net/isos/torios/)

Our website:
[http://torios.net/](http://torios.net/)

The old website:
[http://torios.org/](http://torios.org/)
is **NO** longer used unless the newer one (.net) is down.

I can't tell you 'when' we shall release ToriOS 1.0 but I can 'see' it coming.

The more 'you' test, the faster we release the 1st stable version :)

Thank you!

---

### Post by sudodus on 2015-09-12
Which version should we test?

```
ee04ec76b61651db3ebd27791e75fb74  ToriOS-2015-09-06-beta-precise.iso
```
or
```
d71fe6e72c9265da7245fcfe52a4a82b  ToriOS-2015-09-10-beta-precise.iso
```

---

### Post by amjjawad on 2015-09-12
> **sudodus said:**
> Which version should we test?

```
ee04ec76b61651db3ebd27791e75fb74  ToriOS-2015-09-06-beta-precise.iso
```
or
```
d71fe6e72c9265da7245fcfe52a4a82b  ToriOS-2015-09-10-beta-precise.iso
```

Hi, sorry for the late reply. I was AFK and just logged in.

Whenever it is QA/Testing, and whenever it is a daily build, we almost always test the 'latest' build:
[http://phillw.net/isos/torios/oldISO/ToriOS-2015-09-10-beta-precise.iso](http://phillw.net/isos/torios/oldISO/ToriOS-2015-09-10-beta-precise.iso)

I didn't know there was a new one. When I posted here, it was ToriOS-2015-09-06-beta-precise.iso :)

So, please let's test the latest one, that is: 2015-09-10 :)

Thank you!

---

### Post by sudodus on 2015-11-13
[SIZE=4]ToriOS daily iso file, ToriOS OEM tarball and ToriOS OEM compressed image file[/SIZE]

Try the new ultra-light distro ToriOS, based on Ubuntu 12.04 LTS and the window manager JWM. It uses only ~ 90 MB RAM or less, when running idle after booting (the RAM usage varies depending on the computer hardware). If you want to run ToriOS in old hardware with a weak processor and low amount of RAM, you need ultra-light application programs too. In a bit more powerful computer and with more RAM, it will be very fast, and you can use the standard linux application programs.

ToriOS is not yet released. It is still developed, so although it is quite debugged and polished by now, the daily iso file is still developed and there can be hiccups. *The installed system is more stable than the live system with the installer.* This is why there are alternatives that use different install methods. See the following link

[ToriOS - ultra-light distro based on Ubuntu and the window manager JWM](http://ubuntuforums.org/showthread.php?t=2302798)

---

### Post by nik0laus on 2015-11-15
Greetings from Greece,
Nice job 
I've just installed ToriOS in my wife's ancient laptop.
HP presario 700 , AMD Duron 996 MHz, 384 MB Ram , and everything is running far better than expected regarding the low specs of this machine.

Awaiting for the first stable full release
For long time I was searching for a distro to revive this old laptop with the ease of Ubuntu  OS.
I tried a lot of distros for "Old Hardware", like puppies, Antix, Slitaz etc but I liked this one from the first sight and I customized very easily since I am not a pc guru :)

Keep on great job guys

---

### Post by shimoda on 2016-05-28
I'm just starting with it but in my case seems to fit very well with my old Asus EEE900! 
Thanks!! :)

The Trackpad configuration is really complete, but I can't achieve the two finger scroll... :S 
Any ideas?

---

### Post by sudodus on 2016-05-28
You can test

```
synclient VertEdgeScroll=on VertTwoFingerScroll=on HorizEdgeScroll=on HorizTwoFingerScroll=on
```

We can modify the jwm-settings-manager to have this option if it works

---

### Post by vasa1 on 2016-05-28
> **sudodus said:**
> You can test

```
synclient VertEdgeScroll=on VertTwoFingerScroll=on HorizEdgeScroll=on HorizTwoFingerScroll=on
```

We can modify the jwm-settings-manager to have this option if it works

But shimoda could clarify whether two-finger scroll works with any other operating system on that machine. For example, it doesn't work on my Lubuntu 16.04 (and previously 14.04) running on a Dell Inspiron 1545.

I first identified my device, *AlpsPS/2 ALPS GlidePoint*, with **xinput -l**:```
07:30 PM ~ $ xinput -list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PixArt USB Optical Mouse                	id=11	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; HID 413c:8161                           	id=9	[slave  keyboard (3)]
    &#8627; Integrated_Webcam_1.3M                  	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=14	[slave  keyboard (3)]
07:30 PM ~ $ 
```
I then ran **xinput list-props "AlpsPS/2 ALPS GlidePoint" | grep Capabilities**:```
07:30 PM ~ $ xinput list-props "AlpsPS/2 ALPS GlidePoint" | grep Capabilities
	Synaptics Capabilities (311):	1, 1, 1, 0, 0, 1, 0
07:33 PM ~ $ 
```And from the explanation of the output, described in **man synaptics**, ```
       Synaptics Capabilities
              This  read-only  property  expresses the physical capability of the
              touchpad, most  notably  whether  the  touchpad  hardware  supports
              multi-finger tapping and scrolling.

              8  bit  (BOOL),  7  values (read-only), has left button, has middle
              button, has right button, two-finger detection, three-finger detec&#8208;
              tion, pressure detection, and finger/palm width detection.

```I see I don't have two- or three-finger multi-touch or finger/palm width detection.

In such cases, I'm guessing modifying *jwm-settings-manager* wouldn't help?

---

### Post by amjjawad on 2016-09-09
Hi everyone,

I thought to update you about the progress and guess what? 1.0 has been officially released:
[http://torios.top/torios-1-0-has-been-released/](http://torios.top/torios-1-0-has-been-released/)

Thanks a lot for everything :D

---

### Post by SagaciousKJB on 2016-09-09
Wow I wish I had known about this before putting Puppy on all my low resource machines! For some reason I am always fixing computers for clients that want to hold on to computers like they're antique collectibles, and I always put Puppy on there just so they can have some usability--usually giving them to their kids for a game/edutainment machine.  I'll be excited to give this a try, my only real complaint with Puppy was that it wasn't Ubuntu/Debian based and had to be specially configured for a persistent install.

---

### Post by shimoda on 2016-09-10
> **vasa1 said:**
> But shimoda could clarify whether two-finger scroll works with any other operating system on that machine. For example, it doesn't work on my Lubuntu 16.04 (and previously 14.04) running on a Dell Inspiron 1545.


Yes, I was using Puppy & now Bodhy Linux and works in both cases...

> **sudodus said:**
> You can test

```
synclient VertEdgeScroll=on VertTwoFingerScroll=on HorizEdgeScroll=on HorizTwoFingerScroll=on
```

We can modify the jwm-settings-manager to have this option if it works

It doesn't seems to work... But no prob, I perfectly can live without that ;P

thanks!!! :)

---

### Post by amjjawad on 2016-09-10
Ladies and Gentlemen, guess what? ToriOS now has a Japanese website administrated by our newest family member BALLOON from Japan:

[http://torios-jp.jimdo.com/](http://torios-jp.jimdo.com/)

What? didn't see that coming? the name is Japanese after all so definitely someone from Japan will join and contribute :D

Thanks BALLOON, we highly appreciate that ;)

What about you? why don't you help ToriOS with your native language?!

---

### Post by mastablasta on 2016-09-12
congratulation team! time for me to schedule a download and have a look.

---

### Post by amjjawad on 2016-09-12
> **mastablasta said:**
> congratulation team! time for me to schedule a download and have a look.

Thank you so much :D
That would be great as we do need some feedback before we start working on ToriOS 2.0 ;)

[http://torios.top](http://torios.top)

Before we get over excited, there will be 1.1, 1.2, etc until 2.0 which should be different than 1.0 not only an improved version.

I already have some basic ideas but will wait until we receive some feedback!

---

### Post by amjjawad on 2016-09-12
Hi,

More updates and more good news :D

ToriOS now is on:
**Projects waiting evaluation**
For:
[http://distrowatch.com/](http://distrowatch.com/)

Which means hopefully soon, ToriOS will be listed on the active database of DistroWatch website.

More information: [http://distrowatch.com/dwres.php?resource=links#new](http://distrowatch.com/dwres.php?resource=links#new)

Oh, and by the way, if you wish to help translating ToriOS to another languages, please let us know ;)

Thanks!

---

### Post by amjjawad on 2016-12-12
Dear all,

I'm glad to announce that ToriOS has been officially listed on DistroWatch.com

[http://distrowatch.com/weekly.php?issue=20161212](http://distrowatch.com/weekly.php?issue=20161212)
[http://distrowatch.com/weekly.php?issue=20161212#new](http://distrowatch.com/weekly.php?issue=20161212#new)
[http://distrowatch.com/table.php?distribution=torios](http://distrowatch.com/table.php?distribution=torios)

And, there is an email from Debian so ToriOS is now listed here:
[https://wiki.debian.org/Derivatives/Census/ToriOS](https://wiki.debian.org/Derivatives/Census/ToriOS)

Thank you everyone for your endless support!

We are working hard to improve ToriOS and make it even better :D

---

### Post by mastablasta on 2016-12-19
After "kicking" my kid off the PC i took some time for myself and decided to clean up virtualbox installs and finally try ToriOS. the downloaded version i had at hand was 1.0. 

My PC is a single core Athlon64 3200+ which is running at 2Ghz (i think 2.4Ghz but whatever). it has 4 GB DDR2 RAM and is running windows XP Home SP3. an Antivirus and firewall take a bit of CPU. The virtual appliance i created was assigned 1 GB ram, 64Mb graphics and 8 GB virtual hard disk. since the computer is not much to show Toris OS should fit right into it.

Install (via OBI) was mostly smooth. The one thing that kind of stuck was the keyboard and locale selection. this part too quite a while and at final screen it showed just terminal. so i didn't know if we stopped or not. closing the terminal screen made it proceed normally. for locale i deliberatelly selected only my country code and English. updates were made during install. and it was all finished quite fast (if i don't count the time i was waiting at the empty terminal screen after those locale selections).
The install is preety basic. I was bothered a bit that the time had American form despite choosing the lcoale. This could be a limit of jwm (to have one option as default?). I quickly solved it as it is easy to switch to desired time format and form. not sure why, but the OS also didn't change to my locale. Or does it need "translations" to be able to do that?

Next was restricted extras package. this is the part where i got a bit annoyed. before i chose my language and EN and now this package pulled in all locales and languages. are these all actually needed? just to see some movies? is it because of the fonts?

i then added the browser (chromium) to test out youtube. it works! though slow, but this is because of my PC.

i then checked the windows magager settings. they seems  bit rough arround the edges. it could be because of VB or something else but it was interesting how every change looked as if the desktop reset it self. nothing strange came out of it. i was missing the keyboard switch button. going through the default apps there should be a nice GUI text editor there. VIM is a bit unusual for people that are used to notepad and such. office is installed from OBI, but to try out the keyboard settings etc. i installed the lighter & smaller abiword.


oh and the default web browser (links) didn't seem to work. i need to investigate this.


All in all i think ToriOS is a really good solution for an old PC or a new PC where you want a simple and light interface. Since this was a virtual PC i am not sure how well it does on the battery. but other system resources use is good. To me it falls into beginner/advanced user. The setup needs a bit of knowledge (i was expecting more of a fire and forget experience), so if somoene could install and set it up, then i think beginner would have no issue using it. Also default theme is simple, clear and very easy on the eyes. I think it works really well.


I am thinking of replacing the old chrunchbang on the 1.2 ghz, 256MB, 32MB GPU, 20 GB HDD laptop (if it still boots). but this will come much later, once i can figure out what i can use it for. before it was used to watch youtube videos and for a few kids games, but now i am not sure what it could be used for. maybe a Doom2/Quake server?! i wonder if UT2004 server would run on it... :-)

---

### Post by sudodus on 2016-12-19
Links2 works, but there is a learning curve. You will probably install a more user friendly and powerful web browser ;-)

1. ***Click on the white strip near the top of the window***, and there will be dropdown menus

2. ***Select File - Go to URL***, for example

```
ubuntuforums.org
```

and press the Enter key. You may need the **http://** prefix with some web sites, for example

```
http://torios.top
```

---

### Post by mastablasta on 2016-12-20
I think the issue with browser was as it doesn't redirect for some reason from the .net to .top address...

Now a few pics of the issues i menitoned. For some reason i wasn't able to install guest additions. would not be a big issue on bare metal install i guess...

[ATTACH=CONFIG]272784[/ATTACH][ATTACH=CONFIG]272785[/ATTACH][ATTACH=CONFIG]272786[/ATTACH][ATTACH=CONFIG]272787[/ATTACH]

---

### Post by amjjawad on 2017-02-15
Hi,

To all those who have used or tried ToriOS 1.0, kindly help the project by writing a review here:
[http://distrowatch.com/dwres.php?resource=ratings&distro=torios](http://distrowatch.com/dwres.php?resource=ratings&distro=torios)

I think this is a new feature introduced by DistroWatch.com website. I don't remember I've seen it before.

Your review will help us to gain more attention as ToriOS Project is in need to that.

Also, we'd like to invite you to join our mailing list and/or our Slack team.

For more information:
[http://torios.top/](http://torios.top/)

Thank you in advance :)

---

