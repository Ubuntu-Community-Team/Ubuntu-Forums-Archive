---
title: "testing  in 18.04"
date: 2017-10-19
forum: Ubuntu, Linux and OS Chat
---

### Post by ventrical on 2017-10-19
@all,

 Hi everyone.

As most of you know I have been corresponding with developers at Canonical for a few years now, trying to bridge the gap so ubuntuforums could be more connected to Canonical sources and vis a versa.

I have also  been corresponding With Mark. I had recently reminded to him that we (and the U+1 team) have been testing unity7 alongside gnome3 for the 17.10 cycle. I had asked him directly if he would like us to continue testing during 18.04 and he answered in the affirmative. So I have asked Cariboo if we can continue to do so.

Regards..

---

### Post by Chanath on 2017-10-19
> **ventrical said:**
> @all,

 Hi everyone.

As most of you know I have been corresponding with developers at Canonical for a few years now, trying to bridge the gap so ubuntuforums could be more connected to Canonical sources and vis a versa.

I have also  been corresponding With Mark. I had recently reminded to him that we (and the U+1 team) have been testing unity7 alongside gnome3 for the 17.10 cycle. I had asked him directly if he would like us to continue testing during 18.04 and he answered in the affirmative. So I have asked Cariboo if we can continue to do so.

Regards..

Anyway, its *being stated* that the "Ubuntu" session is the default, so is the fully supported desktop. Also, that Cannonical would not remove packages that are still available in the distribution on upgrades, and the users would have an additional "Unity" session. Unity is still present in universe and the devs would continue to look in and give the best effort at checking. Some features are/would be slightly modified, so they won't collide with Gnome experience. There is also "Gnome" session for those who want vanilla Gnome experience. 

All told, one can have Ubuntu, Ubuntu on Xorg, Gnome, Gnome on Xorg and Unity in one install. And, for those who have computers that won't allow Wayland experience, would get an automatic fallback to corresponding Xorg session.

---

### Post by slickymaster on 2017-10-19
Since Unity isn't an official flavour thread moved to **Ubuntu/Debian BASED** for a better fit.

---

### Post by Chanath on 2017-10-19
> **slickymaster said:**
> Since Unity is an official flavour thread moved to **Ubuntu/Debian BASED** for a better fit.

Is Unity an official flavour?

---

### Post by slickymaster on 2017-10-19
> **Chanath said:**
> Is Unity an official flavour?

That was a typo in my previous post which is already corrected.

---

### Post by Chanath on 2017-10-19
> **slickymaster said:**
> That was a typo in my previous post which is already corrected.

OK.
But, isn't this thread about testing Ubuntu 18.04? That is, about any desktop environment or session that comes/available in Ubuntu 18.04? 
The Cannonical developer Didier had mentioned in his blog, what I mentioned above. [https://didrocks.fr/2017/10/18/ubuntu-gnome-shell-in-artful-day-16/](https://didrocks.fr/2017/10/18/ubuntu-gnome-shell-in-artful-day-16/)
Gnome session and Unity Session are included in any upgrades from 16.04 or 17.04 to 17.10 and to anyone, who wants to add them and use them. 3rd picture in his blog. 
So, these sessions are part of Ubuntu, but not in a separate distro based on Ubuntu.

EDIT: You can also read about this here, [https://community.ubuntu.com/t/ubuntu-gnome-in-artful-day-16/790](https://community.ubuntu.com/t/ubuntu-gnome-in-artful-day-16/790). Unity is an official session.

---

### Post by ventrical on 2017-10-19
> **Chanath said:**
> OK.
But, isn't this thread about testing Ubuntu 18.04? That is, about any desktop environment or session that comes/available in Ubuntu 18.04? 
The Cannonical developer Didier had mentioned in his blog, what I mentioned above. [https://didrocks.fr/2017/10/18/ubuntu-gnome-shell-in-artful-day-16/](https://didrocks.fr/2017/10/18/ubuntu-gnome-shell-in-artful-day-16/)
Gnome session and Unity Session are included in any upgrades from 16.04 or 17.04 to 17.10 and to anyone, who wants to add them and use them. 3rd picture in his blog. 
So, these sessions are part of Ubuntu, but not in a separate distro based on Ubuntu.

EDIT: You can also read about this here, [https://community.ubuntu.com/t/ubuntu-gnome-in-artful-day-16/790](https://community.ubuntu.com/t/ubuntu-gnome-in-artful-day-16/790). Unity is an official session.

@Chanath,

I asked you several times not to discuss opinions on this.  I can't run any sort of maintenance base for unity unless I can do it in Ubuntu Development Version. I also cannot do the testing I need to do from community.ubuntu.com. So now I am getting my threads booted again. If you have opinions then by all means post them at the new link you have mentioned. Since I signed the CoC I have to follow certain protocols. The moderators have given me a lot of leeway but we have to stay focused. So I ask what you can do best .. continue to declare your assumptions and document your work (report bugs and concept fixes and pointers to files at launchpad..)

Thanks

Regards..

---

### Post by Chanath on 2017-10-19
> **ventrical said:**
> @Chanath,

I asked you several times not to discuss opinions on this.  I can't run any sort of maintenance base for unity unless I can do it in Ubuntu Development Version. I also cannot do the testing I need to do from community.ubuntu.com. So now I am getting my threads booted again. If you have opinions then by all means post them at the new link you have mentioned. Since I signed the CoC I have to follow certain protocols. The moderators have given me a lot of leeway but we have to stay focused. So I ask what you can do best .. continue to declare your assumptions and document your work (report bugs and concept fixes and pointers to files at launchpad..)

Thanks

Regards..

OK.
I only said what Didier had said in his blog, which is linked to community.ubuntu.com. Unity is an official session in default Ubuntu. Its not my own opinion. Didier is the person developing the default Ubuntu DE and also the author of Unity, the one you'd find in /usr/bin. He had stated that Unity session will be in 18.04 development time.

---

### Post by ventrical on 2017-10-19
> **Chanath said:**
> OK.
I only said what Didier had said in his blog, which is linked to community.ubuntu.com. Unity is an official session in default Ubuntu. Its not my own opinion. Didier is the person developing the default Ubuntu DE and also the author of Unity, the one you'd find in /usr/bin. He had stated that Unity session will be in 18.04 development time.

But it is not an official standalone distribution! Development has been closed on unity7. For unity to become a distro development would have to be re-opned. This would take a large (or small) community team of volunteers. I have a few developers that are keen  on helping a new community team maintain unity. Once that is done and it doesn't present a security problem then perhaps it may be considered to be an official distro and get seconded back to /main.

> 
 Unity is an official session in default Ubuntu. Its not my own opinion.


But this is not the topic. So if one bifurcates like this  then people get their hair up - if you know what I mean. ;)

Regards..

---

### Post by wildmanne39 on 2017-10-19
Let me explain why it is important to stay on topic, suppose you are using your favorite search engine and you have been looking for a solution to your problem for days and you find a thread marked solved that looks like you have the answer and it is a large thread because of all the off topic conversation but you read the whole thing in hopes of finding the answer only to get all the way to the end to find the answer does not answer the topic of the thread but another topic all together, you wasted all that time and got your hopes up for nothing, or worse yet you think it is the answer and you do what is instructed in the thread and it breaks your system because it was the answer but not to the topic posted in the title and you did not realize that.

---

### Post by cariboo on 2017-10-19
Since this thread is more a discussion about Unity, rather than anything specific, moved to ULOSC

---

### Post by ventrical on 2017-10-19
Thanks Wildmanne39. That applies very well to general help issues of course. In UDV it is important because we may be learning a process or trying to triage a bug and so it takes  a lot of focus and concentration (as I had mentioned many times before). But , also , as Cariboo says .. we don't want it to stop being fun either, else intense forensic study only could be very draining. So I am just saying that (in most all the echos) there has to be a ballance between the intensely disciplined content and the cordial, friendly  and  community minded content. Happens in all the threads;)

Regards..

---

### Post by ventrical on 2017-10-19
> **cariboo said:**
> Since this thread is more a discussion about Unity, rather than anything specific, moved to ULOSC

Ahh yes. Thanks.

Regards..

---

### Post by mc4man on 2017-10-19
Simple - 
If unity-session package is available in 18.04 dev (universe) then is it, unlike any other package in universe,  being excluded from threads in this forum's  Development subforum?

---

### Post by ventrical on 2017-10-19
> **mc4man said:**
> Simple - 
If unity-session package is available in 18.04 dev (universe) then is it, unlike any other package in universe,  being excluded from threads in this forum's  Development subforum?

@mac4man,

 I really appreciate what you are saying.. what you are asking.

Regards..

---

### Post by slickymaster on 2017-10-20
> **mc4man said:**
> Simple - 
If unity-session package is available in 18.04 dev (universe) then is it, unlike any other package in universe,  being excluded from threads in this forum's  Development subforum?

From the Development subforum label> This forum is for the discussion of the development of the next version of Ubuntu or for discussion of testing point releases of the current LTS

---

### Post by mc4man on 2017-10-20
> **slickymaster said:**
> From the Development subforum label

A simple yes or no would have  been  better. So I'll take that as 'yes',  discussion is ok.

---

### Post by ventrical on 2017-10-21
@mac4man,

We are free to discuss it here: [https://community.ubuntu.com/t/testing-unity7-during-18-04-cycle/841/2](https://community.ubuntu.com/t/testing-unity7-during-18-04-cycle/841/2)

as popey puts it:

> 
Some teams may decide to organise themselves  around official flavours, or specific narrow topics. However, as an  individual you&#8217;re welcome to test whatever you like, whenever you like.  It&#8217;s your time to spend, and you can choose what to spend it on.
 While it may sound alarming that threads are being removed about  Unity 7 discussions, I&#8217;d imagine that&#8217;s just to keep focus to what the  team remit is?


Although it would be better if unity were to be an official flavor. I am trying to make the case for this but it is a real rock and hard place not to be able to use UDV forum. I was hoping .. three months into testing 18.04 and we could request for official flavor status. atm there are several developers from Canonical that are keen to take up the task of continued maintenance and offer assistance to the next maintainers team.

regards..

---

### Post by mc4man on 2017-10-21
> **ventrical said:**
> @mac4man,

We are free to discuss it here: [https://community.ubuntu.com/t/testing-unity7-during-18-04-cycle/841/2](https://community.ubuntu.com/t/testing-unity7-during-18-04-cycle/841/2)

as popey puts it:



Although it would be better if unity were to be an official flavor. I am trying to make the case for this but it is a real rock and hard place not to be able to use UDV forum. I was hoping .. three months into testing 18.04 and we could request for official flavor status. atm there are several developers from Canonical that are keen to take up the task of continued maintenance and offer assistance to the next maintainers team.

regards..
That's all well & good but I'm referring to a package - unity-session. It is not a "flavor", not a 'distro', just a package available for any user to install like any of the other 10's of thousands packages in universe.
As a forum they can do anything they want one though  would hope them to be a little more transparent & less disingenuous.

so again - Is unity-session being specifically excluded?
(- and if so the **actual **reason would be interesting but as it's a forum not required.

---

### Post by wildmanne39 on 2017-10-21
mc4man it would probably be best to ask about this specific question in the Resolution Centre where all the admins will see it.

[https://ubuntuforums.org/forumdisplay.php?f=123](https://ubuntuforums.org/forumdisplay.php?f=123)

---

### Post by ventrical on 2017-10-21
> **mc4man said:**
> That's all well & good but I'm referring to a package - unity-session. It is not a "flavor", not a 'distro', just a package available for any user to install like any of the other 10's of thousands packages in universe.
As a forum they can do anything they want one though  would hope them to be a little more transparent & less disingenuous.

so again - Is unity-session being specifically excluded?
(- and if so the **actual **reason would be interesting but as it's a forum not required.

To be honest.. yes.. there are other reasons why it is being blocked.  I agree with your argument totally but there are others who don't. Some of the discussion became too chatty  and some didn't like it. Also , it is a hot item topic and it drew a lot of attention, which was less testing for other flavors.
So now , basically, it is persona non gratis.

Regards..

---

### Post by Frogs Hair on 2017-10-21
> [COLOR=#000000]Is unity-session being specifically excluded?[/COLOR] Speaking for my self regarding U+1, no more than other stand alone sessions/packages including E17, Cairo Dock session , Compiz stand alone , XFCE4, and others that generally don't appear in in the U+1 forum.

---

### Post by mc4man on 2017-10-21
> **Frogs Hair said:**
> Speaking for my self regarding U+1, no more than other stand alone sessions/packages including E17, Cairo Dock session , Compiz stand alone , XFCE4, and others that generally don't appear in in the U+1 forum.
Wow, progress..
So I guess this was an inappropriate thread & posts.. (out of hundreds if one wanted to waste time searching..
[https://ubuntuforums.org/showthread.php?t=2280437](https://ubuntuforums.org/showthread.php?t=2280437)

---

### Post by cariboo on 2017-10-21
> **mc4man said:**
> Simple - 
If unity-session package is available in 18.04 dev (universe) then is it, unlike any other package in universe,  being excluded from threads in this forum's  Development subforum?

We will support the package in the U+1 Dev sub-forum, we don't have a problem with that. What we do have a problem with is someone using the development sub-forum as substitute for sites like [Gnome.org]("https://www.gnome.org/"),[ Lubuntu.ne]("http://lubuntu.net/")t and [Xubuntu.org]("https://xubuntu.org/").

---

### Post by mc4man on 2017-10-22
> **cariboo said:**
> We will support the package in the U+1 Dev sub-forum, we don't have a problem with that. What we do have a problem with is someone using the development sub-forum as substitute for sites like [Gnome.org]("https://www.gnome.org/"),[ Lubuntu.ne]("http://lubuntu.net/")t and [Xubuntu.org]("https://xubuntu.org/"). 
Fair enough

---

### Post by Frogs Hair on 2017-10-22
This is general question and not community re-spin discussion. I didn't write that other sessions were excluded just that they generally don't  appear in U+1 as part of testing because they are mostly community maintained packages and not new versions of Ubuntu.  

> [COLOR=#000000]Wow, progress..[/COLOR]
[COLOR=#000000]So I guess this was an inappropriate thread & posts.. (out of hundreds if one wanted to waste time searching..[/COLOR]
[https://ubuntuforums.org/showthread.php?t=2280437](https://ubuntuforums.org/showthread.php?t=2280437)

---

### Post by ventrical on 2017-10-22
> **Frogs Hair said:**
> This is general question and not community re-spin discussion. I didn't write that other sessions were excluded just that they generally don't  appear in U+1 as part of testing because they are mostly community maintained packages and not new versions of Ubuntu.

It has always been common practice to test other desktops on top of individual official flavors during development cycyles at U+1. For example, razorqt, xmonad, fvmw-cyrstal and cairo-dock just to name a few and nobody said boo as far as I know, since Effenberg has asked me to be Team Captian of U+1 and maintainer of the U+1 wiki. The bottom line is that I asked Mark Shuttleworth if he would like us ( U+1 team ) to continue to test unity-session  (at UDV ubuntuforums)during the 17.10 cycle and, most recently the 18.04 cycle and he answered in the affirmative. People are always saying that developers don't visit here. Well I had rectified that problem to some extent. (Part of the U+1 team captains' job is to link in with developers and make it more accessible  for them to study the work we do here.)  So it seems to me now like the goal posts are all of a sudden being moved here. I really think it is unfair for some to class me in with trying to use development version sub-team as some sort of caveat for a unity7 fanfare show because that is very far from the truth. I did alot of  work to contact developers and build bridges with them for the benefit of the whole forum. unity-session just happened to be a viable ways and means to do so. As for the re-spin  - if one looks at the message base - I had asked Cariboo to move it at my request so bringing that into the equation is totally irrelevant.

Regards..

---

### Post by Chanath on 2017-10-22
> **cariboo said:**
> We will support the package in the U+1 Dev sub-forum, we don't have a problem with that. What we do have a problem with is someone using the development sub-forum as substitute for sites like [Gnome.org]("https://www.gnome.org/"),[ Lubuntu.ne]("http://lubuntu.net/")t and [Xubuntu.org]("https://xubuntu.org/").

Does it mean, we talk in U+1, only about default Ubuntu?
Or do we talk about Ubuntu based other sessions, or only about officially supported derivatives? 
For example, ubuntu-session and gnome-session are available in the main repo. 
One can uninstall ubuntu-desktop, but keep ubuntu-session, and his installation would/might still work. 
Another might uninstall both ubuntu-desktop and ubuntu-session, but keep gnome-session.
Do we talk about them?

---

### Post by Frogs Hair on 2017-10-22
> [COLOR=#000000]It has always been common practice to test other desktops on top of individual official flavors during development cycyles at U+1. For example, razorqt, xmonad, fvmw-cyrstal and cairo-dock[/COLOR]

I am one who has tried and used many different sessions including those you wrote about and a Unity user supporter since 11.04. Unity is now like any of these other sessions with the difference that 16.04 will use Unity until 2021 just as some releases used Gnome 2 until end of life.

---

### Post by ventrical on 2017-10-22
> **Frogs Hair said:**
> I am one who has tried and used many different sessions including those you wrote about and a Unity user supporter since 11.04. Unity is now like any of these other sessions with the difference that 16.04 will use Unity until 2021 just as some releases used Gnome 2 until end of life.

What you mentioned is the 'brass tacks' of this whole equation. What happens when persons (who are using unity by default on 16.04 upgrade to 18.04?? If unity-session is not in repos they will be seconded to gnome3/wayland/xorg dash to dock panel. There is no way that this is going to happen . It is just too large a base and the reason why we have to test unity-session in 18.04 alongside gnome3 - and not only that but the community team that maintains unity-session (either the one I proposed or some other team) better make sure it's working!! If we don't test it then it leaves the possiblity that the whole upgrade from 16.04 to 18.04 will break on several machines. This is not about personal preference, it's about code and bare metal pc mechanics. Either they have to work  as separate spins (ISOs) or co-exist together.I mean , think about it frogs hair, you are one of the most diligent testers - it shouldn't be hard for you to see the writing on the wall during that upgrade scenario. If they do pull it off it will be a lot of man hours in the chair.

Regards..

---

### Post by Frogs Hair on 2017-10-22
> **ventrical said:**
> What you mentioned is the 'brass tacks' of this whole equation. What happens when persons (who are using unity by default on 16.04 upgrade to 18.04?? If unity-session is not in repos they will be seconded to gnome3/wayland/xorg dash to dock panel. There is no way that this is going to happen . It is just too large a base and the reason why we have to test unity-session in 18.04 alongside gnome3 - and not only that but the community team that maintains unity-session (either the one I proposed or some other team) better make sure it's working!! If we don't test it then it leaves the possiblity that the whole upgrade from 16.04 to 18.04 will break on several machines. This is not about personal preference, it's about code and bare metal pc mechanics. Either they have to work  as separate spins (ISOs) or co-exist together.I mean , think about it frogs hair, you are one of the most diligent testers - it shouldn't be hard for you to see the writing on the wall during that upgrade scenario. If they do pull it off it will be a lot of man hours in the chair.

Regards..

I think there is a question as to whether Unity will even be in Universe right now so pending that answer I'll take pause here. I am aware of your membership and role as a U+1 team administrator. I'm not sure the name dropping helps your cause. Good luck with the Unity flavor !

---

### Post by ventrical on 2017-10-22
> **Frogs Hair said:**
> I think there is a question as to whether Unity will even be in Universe right now so pending that answer I'll take pause here. I am aware of your membership and role as a U+1 team administrator. I'm not sure the name dropping helps your cause. Good luck with the Unity flavor !

Not name dropping. Just synopsizing  the chain of events so we have a clearer and more vivid  understanding. It's not me that will need luck with the unity flavor. It's the whole community at large that is affected and will need luck. If unity-session was not in 18.04 universe I wouldn't be writing these messages. But , well .. to each our own..I wish you all well in your new adventure.

Regards..

---

### Post by Frogs Hair on 2017-10-22
> [COLOR=#000000]If unity-session was not in 18.04 universe I would be writing these messages. [/COLOR] Yes you're correct, it will be in universe which means no development and any maintenance going forward would be in question.

---

### Post by Chanath on 2017-10-22
Atm, its a clean slate at U+1 forum. Right now, people are trying to guess the next name. There's no 18.04 dev branch yet, so any talk about it is useless. We'd see, who'd move to 18.04 dev branch their default Ubuntu. I fear there won't be many.

---

### Post by ventrical on 2017-10-22
> **Frogs Hair said:**
> Yes you're correct, it will be in universe which means no development and any maintenance going forward would be in question.

Well thats what I have been saying basically for the last 6 months.

[https://community.ubuntu.com/t/will-unity-be-in-the-ubuntu-18-04-lts-repositories/402/2?u=dale-f-beaudoin](https://community.ubuntu.com/t/will-unity-be-in-the-ubuntu-18-04-lts-repositories/402/2?u=dale-f-beaudoin)

---

### Post by ventrical on 2017-10-22
> **Chanath said:**
> Atm, its a clean slate at U+1 forum. Right now, people are trying to guess the next name. There's no 18.04 dev branch yet, so any talk about it is useless. We'd see, who'd move to 18.04 dev branch their default Ubuntu. I fear there won't be many.

Iv'e been doing U+1 for a good 5 years. I get used to it.  It always works out somehow. Iv'e tested early wayland and weston and mir and just about every desktop. unity or no unity I'm going to keep testing. Just read between the lines .. it's going to be ok.;)

Regards..

---

### Post by QIII on 2017-10-22
I believe my esteemed colleague provided succinct and sufficient guidance in post #24.

If the discussion is in the same vein as any other topic U+1, we are happy to support it.  If it becomes a place to manage the development of a currently unsupported flavor, then it is not welcome.  That needs to take place elsewhere, as described.  To that I will add that we will not allow the U+1 forum to be commandeered and appropriated to the extent that it becomes the exclusive venue of one project.  We have had users suggest that they feel that very thing is happening and they are being turned off.

Cool it.  Period.  You have your guidance.

Thread closed.

---

