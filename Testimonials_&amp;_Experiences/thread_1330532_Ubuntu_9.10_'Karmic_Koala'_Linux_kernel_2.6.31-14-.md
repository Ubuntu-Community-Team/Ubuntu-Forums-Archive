---
title: "Ubuntu 9.10 'Karmic Koala' Linux kernel 2.6.31-14-generic"
date: 2009-11-18
forum: Testimonials &amp; Experiences
---

### Post by rahilm on 2009-11-18
The latest ubuntu 9.10 is named 'Karmic Koala'. This is a personal unprofessional review/experience of ubuntu karmic koala.
Computer specs: Intel Core 2 Duo 2.0 GHz processor, I GB RAM, Intel Corporation 82946GZ/GL Integrated Graphics Controller, Ubuntu 9.04 Jaunty already installed.

THE LIVED-CD:
Booting from the Live-CD is pretty fast. 40-50 seconds is very good for a live cd. Good forst impression. 10 seconds and i encountered the first problem. Ubuntu loaded in 800x600 resolution. I did Settings->Preferences->Display to change it. Shocked to see that only 800x600 and 600x480 available. (NOTE: Developers and many enthusiasts claim that Karmic has improved support for intel graphic cards). I never had problem with Hardy, ingonarable problem with INterprid and Jaunty, but this is damn serious.

Next logical step, I decided to look for a solution. Disappointed to see that my broadband does not work OOTB with Karmic as it did with 8.04 - 9.04. So, natutally, i don't know how to fix it.So I decide to reboot into Jaunty and look for a solution.

After hours of searching and then asking in these forums, i was able to solve the first problem. The second, however, still remains unsolved. I assumed that its a Live-Cd problem, so i did a small 8 GB install in my extra partition i use to test distros.

THE KOALA:
Phew...22 seconds and I am inside...thats fast...in fact lightning fast. Corrected the resolution once again, but still net is not working. I tried to play around with things but that didn't help. I decided I better explore inside without internet and see what is available OOTB.
THE KOALA-INTERNET:
Karmic follows the previous distributions in justifying the fact:- Ubuntu - Internet = Fast Live-CD + headaches

so what's new...Empathy over pidgin..no big deal (what is wrong with these guys!!) Still can't test it without internet but i can say for sure that Pidgin is much better than Empathy form past experiences.

A reallllly good utility -  Palimpset Disk Utility - NICE!! (Bye bye command line)

The Ubuntu Software Centre - Only eye-candy nothing else. doesn't matter because i always apt-get or synaptic.

Ubuntu One - Cant comment.

A new feature(or bug), karmic mounts ext3 drives in /media/<uuid> (or whatever)

Sound is working fine (in fact excellent) but no mp3 (bcoz - no internet)

EXT4 system with grub2 -  good (but do remember to exercise caution while using softwares that are not fully developed yet)


To end it all:
Conclusion: Looks like a rushed up release to me. This is what happens when developers compete with deadlines. I'll keep it on my computer for a few more days and try to get the problems resolved, else i'll remove it. Waiting patiently for LUCID LYNX (please don't rush that up too!!we(I) can wait)

Nonetheless, Karmic is an ambitious release and I really congratulate Canonical for having the guts to do that. Canonical wishes to move forward, and that is what's important. Although it did stumble this time but that really sets the background for Lucid. Its good they are experimenting things, but they should really end this before the LTS and go with the stabler ones (that's an LTS)

---

### Post by running_rabbit07 on 2009-11-18
So you actually have to install drivers. How is that a problem? I had to do it and never cried about it. Using wireless? Try Network Manager, it works wonders.

Try asking for help in the proper forum to get those simple issues fixed.

---

### Post by rahilm on 2009-11-18
> **running_rabbit07 said:**
> So you actually have to install drivers. How is that a problem? I had to do it and never cried about it. Using wireless? Try Network Manager, it works wonders.

Try asking for help in the proper forum to get those simple issues fixed.

If you are talking about this:
[http://ubuntuforums.org/showthread.php?p=8332150](http://ubuntuforums.org/showthread.php?p=8332150)

and

[http://ubuntuforums.org/showthread.php?t=1302475](http://ubuntuforums.org/showthread.php?t=1302475)

I'd really appreciate if  you point me in the right direction..

---

### Post by running_rabbit07 on 2009-11-18
> **rahilm said:**
> If you are talking about this:
[http://ubuntuforums.org/showthread.php?p=8332150](http://ubuntuforums.org/showthread.php?p=8332150)

and

[http://ubuntuforums.org/showthread.php?t=1302475](http://ubuntuforums.org/showthread.php?t=1302475)

I'd really appreciate if  you point me in the right direction..


In your Ja8unty install, go to Synaptic and find which ATI or Nvidia driver is installed and install the same one in Karmic.

---

### Post by running_rabbit07 on 2009-11-18
> **rahilm said:**
> If you are talking about this:
[http://ubuntuforums.org/showthread.php?p=8332150](http://ubuntuforums.org/showthread.php?p=8332150)

and

[http://ubuntuforums.org/showthread.php?t=1302475](http://ubuntuforums.org/showthread.php?t=1302475)

I'd really appreciate if  you point me in the right direction..

Go to Synaptic and try the different programs for DSL. There are a few there.

---

### Post by rahilm on 2009-11-18
> **running_rabbit07 said:**
> In your Ja8unty install, go to Synaptic and find which ATI or Nvidia driver is installed and install the same one in Karmic.

I think you haven't read what i had written above...its too bad people don't read everything..feels to be wasted..

I don't have and ATI or NVIDIA cards . Its intel onboard


> **running_rabbit07 said:**
> Go to Synaptic and try the different programs for DSL. There are a few there.

And exactly how do you expect me to install them???

---

### Post by running_rabbit07 on 2009-11-18
> **rahilm said:**
> I think you haven't read what i had written above...its too bad people don't read everything..feels to be wasted..

I don't have and ATI or NVIDIA cards . Its intel onboard




And exactly how do you expect me to install them???

I read your post or I would not have commented. You still need drivers for onboard hardware. I have nvidia onboard and I still have to install the driver every time I do an install.

---

### Post by running_rabbit07 on 2009-11-18
> **rahilm said:**
>  doesn't matter because i always apt-get or synaptic.

To install something in Synaptic, search DSL, when the programs come up, click on each one and read what it does, when you find one that is an interface program for setting up DSL, click in the box, then click the green arrow to install it.

---

### Post by running_rabbit07 on 2009-11-18
> **rahilm said:**
> Great...will it install without connecting to the internet because thats why i am installing it...

I apologize for not thinking about that. You have 2 options that I know of.

1. Install Karmic in VirtualBox, so that it will use Jaunty's connection and install APTonCD from Synaptic, then install One of the DSL programs along with the Intel driver(s) then run APTonCD and put the file on a thumb drive or burn it to disc and load it in the hard install.

2. Stick with Jaunty.

---

### Post by rahilm on 2009-11-18
> **running_rabbit07 said:**
> To install something in Synaptic, search DSL, when the programs come up, click on each one and read what it does, when you find one that is an interface program for setting up DSL, click in the box, then click the green arrow to install it.

Great...will it install without connecting to the internet because thats why i am installing it...

---

### Post by realzippy on 2009-11-18
Dunno what dsl driver he is talking about,but it would be on the live CD.
Check Karmic-cd in software sources..

Edit:

Thougt this was solved?
[http://ubuntuforums.org/showthread.php?t=1302475&page=3](http://ubuntuforums.org/showthread.php?t=1302475&page=3)

---

### Post by running_rabbit07 on 2009-11-18
> **rahilm said:**
> Great...will it install without connecting to the internet because thats why i am installing it...

Catch 22, see post 9.

---

### Post by rahilm on 2009-11-18
> **realzippy said:**
> 

Thougt this was solved?
[http://ubuntuforums.org/showthread.php?t=1302475&page=3](http://ubuntuforums.org/showthread.php?t=1302475&page=3)

yes it was...i mentioned that i had one problem solved..i posted that to show that i tried for both

@running_rabbit07: seems to be solution but it will take time to install so i better do it tomorrow, as it is getting late where i live (HINT:don't install, use LIVE-CD)

---

### Post by rahilm on 2009-11-20
Nothing happened

---

### Post by Dougie187 on 2009-11-20
> **rahilm said:**
> Nothing happened

Just so you know, I replied to your networking issue.

---

### Post by rahilm on 2009-11-21
let me see..
well i never really made this thread for discussing my network problems

---

### Post by rahilm on 2009-11-21
Update:
I solved my networking issues..
i'll be back with another full review (like it or not)

---

### Post by jdrodrig on 2009-11-21
> **running_rabbit07 said:**
> So you actually have to install drivers. How is that a problem? I had to do it and never cried about it. Using wireless? Try Network Manager, it works wonders.

Try asking for help in the proper forum to get those simple issues fixed.

That is soo typical of many of us reading mildly negative *experiences* about ubuntu...attack the OP...

I think we need to improve our understanding of what a section of *experiences* mean and whether is a useful part of these forums...

It seems it is common that a negative experience is interpreted as a lazy OP that did not ask for help..and as this example shows, that is not always the case...

---

### Post by running_rabbit07 on 2009-11-21
> **jdrodrig said:**
> That is soo typical of many of us reading mildly negative *experiences* about ubuntu...attack the OP...

I think we need to improve our understanding of what a section of *experiences* mean and whether is a useful part of these forums...

It seems it is common that a negative experience is interpreted as a lazy OP that did not ask for help..and as this example shows, that is not always the case...

I guess you should have read the rest of the thread. His Networking issue did end up being an easy fix. As far as display drivers go, I have had to install them every time I do an install on my system, I don't complain about it, because I understand the fact that no OS is going to install every driver on every type of machine. Thank you for trying to rekindle an argument. As now that his networking is up and running, he can freely install his graphics drivers.

---

### Post by jdrodrig on 2009-11-21
> **running_rabbit07 said:**
> I guess you should have read the rest of the thread. His Networking issue did end up being an easy fix. As far as display drivers go, I have had to install them every time I do an install on my system, I don't complain about it, because I understand the fact that no OS is going to install every driver on every type of machine. Thank you for trying to rekindle an argument. As now that his networking is up and running, he can freely install his graphics drivers.

Totally agree.....

I skimmed through most of it, what I meant was the *initial* reaction to this type of thread some of us have....

this particular thread was a lucky one in which at the end, the lazyness and the solution to the problems were disproved and found respectively...but I have ran into soooo many in which an initial negative reaction to the OP converges way out of topic and almost always toward a "if you dont like it, go back to Windows and have a good day" type of attitude.

---

### Post by rahilm on 2009-11-21
Actually, i've found that complaining about a problem in this section actually is the fastest way of fixing it..
You can see that in this case. The networking issue could had never be fixed if Dougie187 had never pointed that it is a DNS issue...where are these people when i ask questions in the appropriate forums????

---

### Post by HappyFeet on 2009-11-21
> **jdrodrig said:**
> but I have ran into soooo many in which an initial negative reaction to the OP converges way out of topic and almost always toward a "if you dont like it, go back to Windows and have a good day" type of attitude.

Most of the time though, I only see those responses when someone has a very hostile attitude.

---

### Post by 3rdalbum on 2009-11-22
I'm sure Lucid will be a lot better on your hardware, if you actually help to test it when it hits first beta.

If you find problems in Karmic, it doesn't necessarily mean it was a "rushed release" or that Karmic is "unstable" - it may just mean that the developers didn't see the problems you see, because their hardware is different to yours.

That's why they need your help testing before release!

---

### Post by running_rabbit07 on 2009-11-22
> **rahilm said:**
> Actually, i've found that complaining about a problem in this section actually is the fastest way of fixing it..
You can see that in this case. The networking issue could had never be fixed if Dougie187 had never pointed that it is a DNS issue...where are these people when i ask questions in the appropriate forums????

**[SIZE=1]MTNL broadband not working!![/SIZE] [SIZE=5]_*(the karmic legacy)*_[/SIZE]**

That is why you got few responses even though you posted it in the right place. If you walk into the Ford dealership and tell them your car is broke _like usual_, they will be less likely to offer up good help.

---

### Post by rahilm on 2009-11-25
that may be so...

you have to excuse me. i have used all my download limit for this month so i cannot start my net or they'll start charging me again

until later then

---

### Post by solwic on 2009-11-25
> **HappyFeet said:**
> Most of the time though, I only see those responses when someone has a very hostile attitude.

Wait a second...people on the forums sometimes have hostile attitudes?!?!

Pssh!  I don't buy that at all....

</sarcasm>

:biggrin:

---

### Post by Tamlynmac on 2009-11-25
> solwic
Wait a second...people on the forums sometimes have hostile attitudes?!?!

Knowing how much HappyFeet enjoys Windows, I'm certain he's confusing this forum with one of his Windows forum accounts.
:lolflag:

---

### Post by solwic on 2009-11-25
> **Tamlynmac said:**
> Knowing how much HappyFeet enjoys Windows, I'm certain he's confusing this forum with one of his Windows forum accounts.
:lolflag:

:lolflag:  Yeah, that's got to be it.  :lolflag:

---

### Post by rahilm on 2009-12-01
> **running_rabbit07 said:**
> **[SIZE=1]MTNL broadband not working!![/SIZE] [SIZE=5]_*(the karmic legacy)*_[/SIZE]**

That is why you got few responses even though you posted it in the right place. If you walk into the Ford dealership and tell them your car is broke _like usual_, they will be less likely to offer up good help.

I don't see any problem with the title

---

### Post by running_rabbit07 on 2009-12-01
> **rahilm said:**
> I don't see any problem with the title

It looks like mockery to me.

Legacy
Legacy Leg"a*cy (l[e^]g"[.a]*s[y^]), n.; pl. Legacies
 (-s[i^]z). [L. (assumed) legatia, for legatum, from legare to
 appoint by last will, to bequeath as a legacy, to depute: cf.
 OF. legat legacy. See Legate.]
 [COLOR=Red]1. A gift of property by will, esp. of money or personal
 property; a bequest. Also Fig.; as, a legacy of dishonor
 or disease.
 [1913 Webster][/COLOR]

 2. A business with which one is intrusted by another; a
 commission; -- obsolete, except in the phrases last
 legacy, dying legacy, and the like.
 [1913 Webster]

 My legacy and message wherefore I am sent into the
 world. --Tyndale.
 [1913 Webster]

 He came and told his legacy. --Chapman.
 [1913 Webster]

 Legacy duty, tax paid to government on legacies.
 --Wharton.

 Legacy hunter, who flatters and courts any one for the
 sake of a legacy.
 [1913 Webster]
 
    -- From The Collaborative International Dictionary of English v.0.48

---

### Post by rahilm on 2009-12-01
[B]Wikipedia The Karmic

Karma[/B] ([Sanskrit]("http://en.wikipedia.org/wiki/Sanskrit"): &#2325;&#2352;&#2381;&#2350;  [*kárma*]("http://upload.wikimedia.org/wikipedia/en/d/d6/Karma.ogg") ([help]("http://en.wikipedia.org/wiki/Wikipedia:Media_help")·[info]("http://en.wikipedia.org/wiki/File:Karma.ogg")), *[kárman]("http://en.wiktionary.org/wiki/%E0%A4%95%E0%A4%B0%E0%A5%8D%E0%A4%AE%E0%A4%A8%E0%A5%8D#Sanskrit")-* "act, action, performance"[[1]]("http://en.wikipedia.org/wiki/The_Karmic#cite_note-0"); [Pali]("http://en.wikipedia.org/wiki/Pali"): *kamma*) in [Indian religions]("http://en.wikipedia.org/wiki/Indian_religions") is the concept of "action" or "deed", understood as that which causes the entire cycle of [cause and effect]("http://en.wikipedia.org/wiki/Causality") (i.e., the cycle called [sa&#7747;s&#257;ra]("http://en.wikipedia.org/wiki/Sa%E1%B9%83s%C4%81ra")) originating in [ancient India]("http://en.wikipedia.org/wiki/Ancient_India") and treated in [Hindu]("http://en.wikipedia.org/wiki/Hindu"), [Jain]("http://en.wikipedia.org/wiki/Jain"), [Sikh]("http://en.wikipedia.org/wiki/Sikh") and [Buddhist]("http://en.wikipedia.org/wiki/Buddhism") philosophies.[[2]]("http://en.wikipedia.org/wiki/The_Karmic#cite_note-1").

---

### Post by rahilm on 2009-12-02
Okay..I got my internet connection working now.. i shall complete my review/experience one and for all...

just one line...ubuntu continues to impress me..

another one...there are many alternates to windows but there is no alternate to ubuntu..

Ok the last one is questionable..

And for those who already know ubuntu 9.04..
Karmic Koala is just a very fast Jaunty Jackalope (don't compare speeds of koalas and jackalopes though) with empathy instead of pidgin and grub2 instead of grub legacy

have fun..

---

### Post by solwic on 2009-12-02
> **rahilm said:**
> Okay..I got my internet connection working now.. i shall complete my review/experience one and for all...

just one line...ubuntu continues to impress me..

another one...there are many alternates to windows but there is no alternate to ubuntu..

Ok the last one is questionable..

And for those who already know ubuntu 9.04..
Karmic Koala is just a very fast Jaunty Jackalope (don't compare speeds of koalas and jackalopes though) with empathy instead of pidgin and grub2 instead of grub legacy

have fun..

It actually ran a little slower on my machine, but hey, glad it's doing well for you.  :)

---

### Post by jdrodrig on 2009-12-03
> **running_rabbit07 said:**
> **[SIZE=1]MTNL broadband not working!![/SIZE] [SIZE=5]_*(the karmic legacy)*_[/SIZE]**

That is why you got few responses even though you posted it in the right place. If you walk into the Ford dealership and tell them your car is broke _like usual_, they will be less likely to offer up good help.


I totally disagree...if such car dealership or any business cared for their consumers, they should react even with more effort if they know you have had several problems in the past...

unfortunately, it is common in the linux-type of forum to react to such consumers as "well, what did you expect from a free product...if you don't like it, good bye have a nice day"

but maybe, you are right, and Ford/GM/Chrysler used to behave like that...care to see their profitability of the last 10 years?
(read, sarcasm).

---

