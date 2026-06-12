---
title: "Arch Linux: It's a virus I tell ya!"
date: 2009-09-01
forum: The Cafe
---

### Post by Metallion on 2009-09-01
I think it's safe to say that Arch is easily the second most loved distro on this forum after the obvious Ubuntu. Loads of people testify to trying it out once and never looking back, the thing getting named a gazillion times in every distro recommendation thread and so on.

I thought about playing with it myself many times but never really did since I didn't have the disk space to spare and wasn't feeling comfortable with it replacing my Ubuntu/Mint just yet. Now finally I got my hands on this old 60 gig HD and decided to dedicate it to trying out new distros.

To make it easy for myself, I partition the thing back in Mint, then boot Arch and start the installation with the Arch wiki open on my laptop. To my amazement I had a fully functional gnome environment up in less than 2 hours and I already knew most of the things explained in the wiki.

I really like what I've seen so far! It's just a nice feeling to be sitting on top of a system that I've put together myself even though I'm making it look just a Mint. I had moved to Mint for its good looks in the first place anyway. A very nice touch that even Mint Menu is available from AUR as well. :) Arch is notably faster too. Lastly I wonder how the rolling release is going to treat me. I was getting quite tired of reinstalling every 6 months to get the new stuff but I'm a tad afraid of possible instabilities in the bleeding edge software too.

It was meant to just be something for me to thinker with on the side but I think I've caught the Arch virus and it's getting bombarded into my main OS at an alarming rate.

---

### Post by Bachstelze on 2009-09-01
That's funny, I finally got some free time and decided to try arch just yesterday. It didn't last one day. My only reaction was: "Yeah, so it *this* what people are making so much fuss about?" Don't get me wrong, from what I could see, Arch seems to be a good distro, but nothing special. Back to Ubuntu.

---

### Post by HappinessNow on 2009-09-01
"arch, **arch**, [SIZE=4]**arch!**[/SIZE][SIZE=3]**"**[/SIZE]

> **HymnToLife said:**
> That's funny, I finally got some free time and decided to try arch just yesterday. It didn't last one day. My only reaction was: "Yeah, so it *this* what people are making so much fuss about?" Don't get me wrong, from what I could see, Arch seems to be a good distro, but nothing special. Back to Ubuntu.hilarious! I had a very similar experience; even left Arch installed for 3 or 4 months and played around with it a few times but all the hype only lead to disappointment. Great distro but perhaps I had too high expectations and it just didn't live up to satisfy.

I would say now a days must distros are just as good as the others, I prefer Ubuntu over all.

---

### Post by gn2 on 2009-09-01
> **Metallion said:**
> I think it's safe to say that Arch is easily the second most loved distro on this forum 

I don't.
Arch simply has a following of vociferous evangelists who like to tell everyone how snappily dressed the emperor is these days.

---

### Post by sisco311 on 2009-09-01
> **HymnToLife said:**
> It didn't last one day. My only reaction was: "Yeah, so it *this* what people are making so much fuss about?" Don't get me wrong, from what I could see, Arch seems to be a good distro, but nothing special. Back to Ubuntu.

That's the point of Arch: KISS. Once you have installed you get a minimal but fully functional system, then you have to install the packages you really want/need. Building your system from the bottom to the top makes you learn a lot of things about your computer and OS.

OP:

```
pacman -Ss bash completion
```;)

~/.bashrc:
```
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

```

---

### Post by hessiess on 2009-09-01
> **Metallion said:**
> Lastly I wonder how the rolling release is going to treat me. I was getting quite tired of reinstalling every 6 months to get the new stuff but I'm a tad afraid of possible instabilities in the bleeding edge software too.

Generally I have had verry few problems with it, but things can break when applications make large changes to the configuration format. For example when X11 switched to HAL/auto detect hardware insted of using /etc/X11/xorg.conf it caused the keyboard to die, but there is always a fix on the frount page of the arch website prittymuch instantly.Fixing the odd minor problem is still much easier than rebuilding the whole OS and recreating your custom configuration every 6 months just to have the latest softwere.

---

### Post by gn2 on 2009-09-01
> **sisco311 said:**
> That's the point of Arch: KISS. Once you have installed you get a minimal but fully functional system, then you have to install the packages you really want/need. Building your system from the bottom to the top makes you learn a lot of things about your computer and OS.

That can be done with many distributions, so it's really no big deal.
Tell me something truly unique that Arch has?

[silence]

---

### Post by Metallion on 2009-09-01
> **sisco311 said:**
> That's the point of Arch: KISS. Once you have installed you get a minimal but fully functional system, then you have to install the packages you really want/need. Building your system from the bottom to the top makes you learn a lot of things about your computer and OS.

Yeah indeed. That's why I think Arch would also look good on my CV. It clearly shows I have better than average linux knowledge.

> 
OP:

```
pacman -Ss bash completion
```;)

~/.bashrc:
```
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

```

Thanks mate, exactly what I was looking for. ;)

---

### Post by Bachstelze on 2009-09-01
> **Metallion said:**
> Yeah indeed. That's why I think Arch would also look good on my CV. It clearly shows I have better than average linux knowledge.

lol

---

### Post by hessiess on 2009-09-01
> **gn2 said:**
> That can be done with many distributions, so it's really no big deal.
Tell me something truly unique that Arch has?

[silence]

Rolling release, simplicity.

---

### Post by Bachstelze on 2009-09-01
> **hessiess said:**
> Rolling release, simplicity.

Same remark.

---

### Post by Metallion on 2009-09-01
> **gn2 said:**
> That can be done with many distributions, so it's really no big deal.
Tell me something truly unique that Arch has?

[silence]

In the end all distros are very similar... It's all linux. I'm not going to attempt anything as silly as trying to name something no other distro has. I just like the things that Arch has and so I'm using it.

---

### Post by Daisuke_Aramaki on 2009-09-01
> **Metallion said:**
> Yeah indeed. That's why I think Arch would also look good on my CV. It clearly shows I have better than average linux knowledge.


This one cracked me up! Use something like Slackware, Lunar, Sorcerer or Gentoo, then I would believe you.

---

### Post by K.L. on 2009-09-01
I won't speak for everyone, but that's what I like about Arch:

- Arch keeps it simple, yet it allows me to build my system from ground up

- Rolling release (a big plus in my eyes)

-  Arch doesn't include stupid features that I don't need

- Did I mentioned rolling release? :D

---

### Post by Dragonbite on 2009-09-01
> **HymnToLife said:**
> That's funny, I finally got some free time and decided to try arch just yesterday. It didn't last one day. My only reaction was: "Yeah, so it *this* what people are making so much fuss about?" Don't get me wrong, from what I could see, Arch seems to be a good distro, but nothing special. Back to Ubuntu.

> **&#20170 said:**
> "arch, **arch**, [SIZE=4]**arch!**[/SIZE][SIZE=3]**"**[/SIZE]

hilarious! I had a very similar experience; even left Arch installed for 3 or 4 months and played around with it a few times but all the hype only lead to disappointment. Great distro but perhaps I had too high expectations and it just didn't live up to satisfy.

I would say now a days must distros are just as good as the others, I prefer Ubuntu over all.

I've had similar thoughts on openSUSE. A lot of good things mentioned about it but it seems to fall flat on implementation for me.

---

### Post by Bachstelze on 2009-09-01
Rolling releases are overrated anyway. Most of the time, you absolutely don't need the newer version of a program. But of course, "my distro has a newer Pidgin version than yours, neener, neener!"

> **Dragonbite said:**
> I've had similar thoughts on openSUSE. A lot of good things mentioned about it but it seems to fall flat on implementation for me.

I use OpenSuse as a Xen dom0, and it's really good (not like I would use it for anything else, though).

---

### Post by Bachstelze on 2009-09-01
> **Dragonbite said:**
> I've had similar thoughts on openSUSE. A lot of good things mentioned about it but it seems to fall flat on implementation for me.

I use OpenSuse as a Xen dom0, and it's really good (not like I would use it for anything else, though).

---

### Post by HappinessNow on 2009-09-01
> **HymnToLife said:**
> Rolling releases are overrated anyway. Most of the time, you absolutely don't need the newer version of a program. But of course, "my distro has a newer Pidgin version than yours, neener, neener!"
 

+1

"Rolling Releases, **Rolling Releases**, [SIZE=3]**Rolling Releases!"**[/SIZE] are way over pushed! and only lead to further disappointment in "Arch, **Arch**, [SIZE=3]**Arch!"**[/SIZE]

---

### Post by K.L. on 2009-09-01
> **HymnToLife said:**
> Rolling releases are overrated anyway. Most of the time, you absolutely don't need the newer version of a program. But of course, "my distro has a newer Pidgin version than yours, neener, neener!"

Not really. With rolling release distro you don't need to reinstall every 6 months (or so). Newer programs can have many useful features, it's not just about version numbers. I know, you can have newest apps in Ubuntu too, but with Arch it's just simpler.

---

### Post by Skripka on 2009-09-01
> **gn2 said:**
> That can be done with many distributions, so it's really no big deal.
Tell me something truly unique that Arch has?

[silence]

For starters there's AUR.  But then again you're not really interested in the topic anyway, so why waste ascii bytes?

---

### Post by sisco311 on 2009-09-01
> **gn2 said:**
> That can be done with many distributions, so it's really no big deal.
Tell me something truly unique that Arch has?

[silence]

it's the distribution that best suits my needs.

---

### Post by Arup on 2009-09-01
sidux being cutting edge and rolling release is also another excellent option to arch. It has a KISS policy and is among the fastest distros out there.

---

### Post by gn2 on 2009-09-01
> **hessiess said:**
> Rolling release, simplicity.

Neither are unique.
Arch has quite a twisted interpretation of the word simplicity....

> **Metallion said:**
> In the end all distros are very similar... It's all linux. I'm not going to attempt anything as silly as trying to name something no other distro has. I just like the things that Arch has and so I'm using it.

That's great and I'm happy for you, but why do you and your fellow Archers feel the need to prattle on about Archery in the Ubuntu forums so much?
Are you looking to recruit converts to your faith or are you reinforcing your choice and justifying it to yourselves?

Stand back a minute and look at it objectively and you'll see how ridiculous it is.
Still not convinced?
Well how about if I posted in the Arch forums about how fantastic Ubuntu is and how it's great that you can get to spend twenty or thirty minutes every six months installing a new release and how it just works and has a massive support forum and it's got Synaptic and it's really brilliant and you oughta try it and it's really cool to have on your CV and did you know that a really cool space tourist dude and at least two nobel prize winners support it, and did you know it's got a really unique brown theme?

See now how daft you all look?

> **Skripka said:**
> For starters there's AUR.  But then again you're not really interested in the topic anyway, so why waste ascii bytes?

My interest in Arch merely extends to having discussion of it banned from the Ubuntu forums.
I doubt that will ever happen but I live in hope.

---

### Post by gn2 on 2009-09-01
> **sisco311 said:**
> it's the distribution that best suits my needs.

That's fine, discussion of it is openly welcomed [here]("http://bbs.archlinux.org/").

---

### Post by K.L. on 2009-09-01
> **gn2 said:**
>  See now how daft you **all** look?

All? Do all Arch users do this? Really?

---

### Post by Arup on 2009-09-01
Said and done, arch good or not will never be Ubuntu, I will never even dare for once to peddle arch to a Windows refugee, that would be the end of that person's Linux journey for sure. Ubuntu is the de facto distro thats putting Linux single handedly on the map and its for the very reason, Linux is now gaining popularity. Many Windows users are now curiuous about Linux and when I show them Ubuntu desktop and the myriads of software available, they are totally impressed. Then I show them how easy it is to run Live CD and install Ubuntu, its double WOW. I think few distros around accomplish it like Ubuntu.

---

### Post by kk0sse54 on 2009-09-01
> **gn2 said:**
> 
That's great and I'm happy for you, but why do you and your fellow Archers feel the need to prattle on about Archery in the Ubuntu forums so much?
Are you looking to recruit converts to your faith or are you reinforcing your choice and justifying it to yourselves?
A lot of people started with Ubuntu before moving to other distros like Arch but still continue to enjoy using these forums. When there's a thread asking about "what linux distro should i choose?" then yes naturally people are going to suggest arch especially if the OP is looking for a more DIY distro.

> Stand back a minute and look at it objectively and you'll see how ridiculous it is.
Still not convinced?
Well how about if I posted in the Arch forums about how fantastic Ubuntu is and how it's great that you can get to spend twenty or thirty minutes every six months installing a new release and how it just works and has a massive support forum and it's got Synaptic and it's really brilliant and you oughta try it and it's really cool to have on your CV and did you know that a really cool space tourist dude and at least two nobel prize winners support it, and did you know it's got a really unique brown theme?
Nobody is stopping you

> See now how daft you all look?
no

> My interest in Arch merely extends to having discussion of it banned from the Ubuntu forums.
I doubt that will ever happen but I live in hope.
Right, so we're not allowed to mention distros let alone operating systems other than Ubuntu?

---

### Post by RiceMonster on 2009-09-01
Oh wonderful, another Arch vs Ubuntu thread!

Someone is excited about Arch, then Ubuntu fans get angry.

---

### Post by hockeytux on 2009-09-01
> **Arup said:**
> Said and done, arch good or not will never be Ubuntu, I will never even dare for once to peddle arch to a Windows refugee, that would be the end of that person's Linux journey for sure. Ubuntu is the de facto distro thats putting Linux single handedly on the map and its for the very reason, Linux is now gaining popularity. Many Windows users are now curiuous about Linux and when I show them Ubuntu desktop and the myriads of software available, they are totally impressed. Then I show them how easy it is to run Live CD and install Ubuntu, its double WOW. I think few distros around accomplish it like Ubuntu.

Quite true. Making a direct transition from Windows to Arch is near impossible for most people. Once you have Ubuntu up and running for a while you can still sit down an afternoon to set up Arch (or anything else more DIY).

Maybe Kubuntu is even more of a Windows killer but Ubuntu 9.10 is supposedly going to have a more appealing default theme (which matters to many people unless they are introduced to Linux by someone who is already running it on their computer)

---

### Post by bodyharvester on 2009-09-01
how is it *simplicity* to have to build your own OS up from the ground?

---

### Post by hessiess on 2009-09-01
> **bodyharvester said:**
> how is it *simplicity* to have to build your own OS up from the ground?

Simple to get it exactly how you want it.

---

### Post by RiceMonster on 2009-09-01
> **bodyharvester said:**
> how is it *simplicity* to have to build your own OS up from the ground?

[http://wiki.archlinux.org/index.php/The_Arch_Way](http://wiki.archlinux.org/index.php/The_Arch_Way)

> Arch Linux defines simplicity as a lightweight UNIX-like base structure without unnecessary additions, modifications, or complications, that allows an individual user to shape the system according to their own needs. In short; an elegant, minimalist approach.

---

### Post by Bachstelze on 2009-09-01
> **bodyharvester said:**
> how is it *simplicity* to have to build your own OS up from the ground?

You don't even have to build it, just install a bunch of packages someone else built. How |33t is that?

---

### Post by JillSwift on 2009-09-01
Silliness.

I've no idea why folks insist that there's an objective hierarchy of ... well, of anything.

I don't at all mind folks talking about other distros - or other OSs outside of Linux based OSs. It's nice to hear about all the choices out there, what needs the fill well, what needs they don't fill well, interesting methodology and the various paradigms driving them. I think most folks do, too.

Where it falls flat is when there's an air of absolute "this is the best" surrounding the opinions. Worse still when it's said outright. The problem with that attitude is, it ignores the subjectivity of hierarchies.

Frankly, if there were some way of objectively rating all the distros, everyone would be forced by their own rational selves to *use* the best distro, with only a few statistical outliers. That not being the case, people are driven to use the distro that best suits them and thier needs and thier wishes, and even then it's not that often that one single distro does the trick.

So I encourage folks to talk about other distros here on these forums, where appropriate. I love hearing about them. Just keep in mind that your preference for distro X is only that, a preference. We all should keep that in mind too, when reading about those other preferences. There's no need to come galloping to the defense of our favorites, they're not under attack.

We hardly need a bunch of in-fighting over nothing other than differences of opinion, after all.

---

### Post by MONODA on 2009-09-01
> Well how about if I posted in the Arch forums about how fantastic Ubuntu is and how it's great that you can get to spend twenty or thirty minutes every six months installing a new release and how it just works and has a massive support forum and it's got Synaptic and it's really brilliant and you oughta try it and it's really cool to have on your CV and did you know that a really cool space tourist dude and at least two nobel prize winners support it, and did you know it's got a really unique brown theme?

I am sure that almost everyone on the arch linux forums has tried ubuntu in the past, if not used it as their main OS and then switched to arch since ubuntu didnt work too well for them (I am one of these people). So if you see a post promoting arch then I am quite sure that the person who posted it is making sure that people know their options and that arch might work a lot better for them than ubuntu (I never would have found arch if it werent for these posts and would probably would be back using windows and having headaches everytime I turn on my computer).

Also a few things that arch has that are special:

AUR
ABS
super fast package management with pacman
aur integration with yaourt
rolling release
it really is simple, if you follow the guide you learn that all daemons are in /etc/rc.d and all configs are in /etc/ and so on
REALLY FAST! (my laptop (see in sig) boots from grub to X in 15 seconds)
it uses BSD like boot script (or somethign like that, I cant seem to rememebr...) and uses /etc/rc.conf to configure most things
with aur their are pretty much no packages which you will not be able to install easily

Of course arch has its problems (what OS doesnt?) but in my experience the problems that arise seem to be a lot easier to solve/workaround.

---

### Post by RiceMonster on 2009-09-01
> **MONODA said:**
> REALLY FAST! (my laptop (see in sig) boots from grub to X in 15 seconds)

It's not really faster; you just have less services, etc running.

---

### Post by MONODA on 2009-09-01
> It's not really faster; you just have less services, etc running.
well yeah but Ive always found it hard to track down and properly remove these services from ubuntu so for me and probably most people, its faster.

---

### Post by Bachstelze on 2009-09-01
> **MONODA said:**
> 
it really is simple, if you follow the guide you learn that all daemons are in /etc/rc.d and all configs are in /etc/ and so on

Arch teaches you that daemons are in /etc/rc.d? It's a really bad teacher, then. Last I checked, it was init scripts.

> **MONODA said:**
> REALLY FAST! (my laptop (see in sig) boots from grub to X in 15 seconds)

My Ubuntu does it in 9 seconds. pwn3d

> **MONODA said:**
> it uses BSD like boot script (or somethign like that, I cant seem to rememebr...) and uses /etc/rc.conf to configure most things

So does Slackware.

---

### Post by wmcbrine on 2009-09-01
> **K.L. said:**
> Not really. With rolling release distro you don't need to reinstall every 6 months (or so).This is the third post in this thread to imply that you have to reinstall Ubuntu to get a new version. That's just not true. All you have to do is upgrade.

[quote=MONODA]REALLY FAST! (my laptop (see in sig) boots from grub to X in 15 seconds)[/quote]So does my desktop, running Ubuntu 9.04.

---

### Post by Bachstelze on 2009-09-01
> **MONODA said:**
> well yeah but Ive always found it hard to track down and properly remove these services from ubuntu so for me and probably most people, its faster.

For most people, Windows and Mac OS are the only OSes on earth. Just because "most people" believe something doesn't make it right.

---

### Post by Skripka on 2009-09-01
> **RiceMonster said:**
> Oh wonderful, another Arch vs Ubuntu thread!

Someone is excited about Arch, then Ubuntu fans get angry.

My money is on a disgruntled UFer making the attack on the archlinux.org servers :)

---

### Post by mrgnash on 2009-09-01
I don't mind people talking about other distros (or OSes, for that matter), either, but what I do find a little irksome is those arch converts who feel the compulsion to pass back through the veil of tears so that, like kindly Bodhisattva, they can liberate all us poor, unenlightened Ubuntu users. 

Sure, Arch seems like a great distro, and I'm certainly not knocking it, but I'm not sure why people think that using it connotes some kind of elite status. It is entirely possible to build Ubuntu up from a very minimal install, and even build the majority of your applications from source, compile your own kernel, etc. if you are so inclined.

---

### Post by Skripka on 2009-09-01
> **JillSwift said:**
> 

We hardly need a bunch of in-fighting over nothing other than differences of opinion, after all.

But this is the INTERNET.  It IS SRS BIZNS.

---

### Post by swoll1980 on 2009-09-01
I don't think the Arch hype on this forum has anything to do with it being a superior product, it's not by any stretch of the imagination.  I think it has more to do with people that think they are special if they can edit a configuration file, and want everyone else to know that they are special.

---

### Post by Bachstelze on 2009-09-01
> **Skripka said:**
> But this is the INTERNET.  It IS SRS BIZNS.

[img]http://imgs.xkcd.com/comics/duty_calls.png[/img]

---

### Post by JillSwift on 2009-09-01
> **swoll1980 said:**
> I don't think the Arch hype on this forum has anything to do with it being a superior product, it's not by any stretch of the imagination.  I think it has more to do with people that think they are special if they can edit a configuration file, and want everyone else to know that they are special.
If that's the case, then I'll add a suggestion: [COLOR=DarkRed]Want to demonstrate your prowess with configuration files? Spend more time in the help and support forums.[/COLOR]

---

### Post by kk0sse54 on 2009-09-01
> **swoll1980 said:**
> I don't think the Arch hype on this forum has anything to do with it being a superior product, it's not by any stretch of the imagination.  I think it has more to do with people that think they are special if they can edit a configuration file, and want everyone else to know that they are special.

You are so right, that's why I brag in every single thread that I respond to that I can edit my own  configuration  files so I must be special :roll:

---

### Post by Bachstelze on 2009-09-01
> **jillswift said:**
> if that's the case, then i'll add a suggestion: [color=darkred]want to demonstrate your prowess with configuration files? Spend more time in the help and support forums.[/color]

+1

It's funny to see that most people who participate in this thread seldom (never?) contribute to the suport forums.

---

### Post by RiceMonster on 2009-09-01
> **swoll1980 said:**
> I don't think the Arch hype on this forum has anything to do with it being a superior product, it's not by any stretch of the imagination.  I think it has more to do with people that think they are special if they can edit a configuration file, and want everyone else to know that they are special.

*sigh*

---

### Post by K.L. on 2009-09-01
The funny thing is I even didn't attack Ubuntu (I still use it), but here comes bunch of Ubuntu fans and attacks Arch: YOU MUST BE SPECIAL IF YOU USE ARCH!!!!!!!!!!!1!@ONE

Now I remember why I didn't post in Windows vs Linux / Arch vs Ubuntu threads for such a long time. 

Good day!

---

### Post by Bachstelze on 2009-09-01
> **K.L. said:**
> The funny thing is I even didn't attack Ubuntu

> **K.L. said:**
> Not really. With rolling release distro you don't need to reinstall every 6 months (or so).

In other words, with Ubuntu you need. But yeah, no attack.

---

### Post by swoll1980 on 2009-09-01
> **JillSwift said:**
> If that's the case, then I'll add a suggestion: [COLOR=DarkRed]Want to demonstrate your prowess with configuration files? Spend more time in the help and support forums.[/COLOR]

> **HymnToLife said:**
> +1

It's funny to see that most people who participate in this thread seldom (never?) contribute to the suport forums.

I'm sorry I've only posted 1000 help replies on these forums. At 3, or more minutes per reply that's at least 3000 minutes of my life I've spent helping people on these forums. FREE OF CHARGE! Shows you how much the staff appreciates the help.

---

### Post by Bachstelze on 2009-09-01
> **swoll1980 said:**
> I'm sorry I've only posted 1000 help replies on these forums. At 3, or more minutes per reply that's at least 3000 minutes of my life I've spent helping people on these forums. FREE OF CHARGE! Shows you how much the staff appreciates the help.

The keyword here is "most"... You can see who those users are by yourself, just click on their nicks and "Find more posts by...". If you see only Cafe/RD/Games threads, you found one.

---

### Post by swoll1980 on 2009-09-01
> **K.L. said:**
> The funny thing is I even didn't attack Ubuntu (I still use it), but here comes bunch of Ubuntu fans and attacks Arch: YOU MUST BE SPECIAL IF YOU USE ARCH!!!!!!!!!!!1!@ONE

Now I remember why I didn't post in Windows vs Linux / Arch vs Ubuntu threads for such a long time. 

Good day!

That's not what I said. I said that's what the fake hype is about. It's not different than any other distro. They're all pretty much the same.

---

### Post by swoll1980 on 2009-09-01
> **HymnToLife said:**
> The keyword here is "most"... You can see who those users are by yourself, just click on their nicks and "Find more posts by...". If you see only Cafe/RD/Games threads, you found one.

You did a +1 to his response, which was an attack against me. I could only assume that you agreed with his attack against me.

---

### Post by Simian Man on 2009-09-01
> **swoll1980 said:**
> I'm sorry I've only posted 1000 help replies on these forums. At 3, or more minutes per reply that's at least 3000 minutes of my life I've spent helping people on these forums. FREE OF CHARGE! Shows you how much the staff appreciates the help.

Ahh, they were agreeing with you actually...

Arch is a great distro, but is over-hyped on this forum.  It is strong in the areas where Ubuntu is weak, so a lot of users here really find it as a breath of fresh air.

Ubuntu, on the other hand, is over-rated not only here, but all over the internet so there ya go.

---

### Post by K.L. on 2009-09-01
> **HymnToLife said:**
> In other words, with Ubuntu you need. But yeah, no attack.

I did an upgrade once, it broke my system. When it'll be error free I'll take my words back.

---

### Post by Bachstelze on 2009-09-01
> **swoll1980 said:**
> You did a +1 to his response, which was an attack against me.

Are you sure? It didn't seem like a personal attack to me, just a message to incite people in general to participate more in the support forums. I think you were quoted only because the post was a logical continuation of yours.

> **K.L. said:**
> I did an upgrade once, it broke my system. When it'll be error free I'll take my words back.

There is a Chinese proverb that says (roughly): "If you bang your head against a vase and it makes a hollow sound, do not necessarily imply that it is the vase that is hollow."

---

### Post by Bachstelze on 2009-09-01
> **K.L. said:**
> I did an upgrade once, it broke my system. When it'll be error free I'll take my words back.

There is a Chinese proverb that says (roughly): "If you bang your head against a vase and it makes a hollow sound, do not necessarily imply that it is the vase that is hollow."

---

### Post by swoll1980 on 2009-09-01
> **HymnToLife said:**
> Are you sure? It didn't seem like a personal attack to me, just a message to incite people in general to participate more in the support forums. I think you were quoted only because the post was a logical continuation of yours.

Maybe I misunderstood, but it was easy to do considering the context.

---

### Post by Skripka on 2009-09-01
> **HymnToLife said:**
> 
There is a Chinese proverb that says (roughly): "If you bang your head against a vase and it makes a hollow sound, do not necessarily imply that it is the vase that is hollow."

Methinks, as a moderator, you should be above calling posters idiots.  Either openly or implied.  Post reported.  This thread was a testimonial about someone moving from Ubuntu to Arch, why do you need to make it an insult fest?

---

### Post by aaaantoine on 2009-09-01
> **Skripka said:**
> For starters there's AUR.  But then again you're not really interested in the topic anyway, so why waste ascii bytes?

I have to say that this is probably one of my favorite things about Arch, even though I pay it little mind.

On Ubuntu, if it isn't in the repository, I have to go out and either find a user created .deb package, or manually find all the dependencies and compile it myself.

On Arch, if it's not in the main repository, someone probably did all the dirty work for me in AUR.  I run yaourt -S obscureapp and if it shows up, it handles the dependencies for me.  I still have to compile it, but at least I'm not hunting for packages and dependencies.

The flip side is, I think anyone can make an AUR install file, and they can be used to malicious ends if you're not careful.

---

### Post by swoll1980 on 2009-09-01
I reread it, and I see where I misunderstood. I am terribly sorry to both of you, and couldn't feel more "stupider" than I do right now. *runs crying in shame*

---

### Post by JillSwift on 2009-09-01
> **swoll1980 said:**
> I reread it, and I see where I misunderstood. I am terribly sorry to both of you, and couldn't feel more "stupider" than I do right now. *runs crying in shame*
*offers peace mug of hot chocolate*

---

### Post by K.L. on 2009-09-01
> **HymnToLife said:**
> There is a Chinese proverb that says (roughly): "If you bang your head against a vase and it makes a hollow sound, do not necessarily imply that it is the vase that is hollow."

Wait a minute... You are saying that it was MY fault? Honestly, I have no more patience...

I bet we can agree on one thing. We use whatever we like, whatever suits our needs better. The OP found that Arch suits his needs better, so did MANY Ubuntu users. I don't see what is wrong with that.

And I'm waiting for apology! :p

---

### Post by Bachstelze on 2009-09-01
> **Skripka said:**
> Methinks, as a moderator, you should be above calling posters idiots.  Either openly or implied.  Post reported.

/facepalm

This was an analogy. Did K.L. bang his head against a vase? No. Sense of humor, get one. (What he did, though, was spreading FUD about Ubuntu.)

> **Skripka said:**
> This thread was a testimonial about someone moving from Ubuntu to Arch, why do you need to make it an insult fest?

Yeah, of course. You're so happy to find an occasion to jump on a mod that you seem to have lost your reading ability. In my first post in this thread, I acknowledged that Arch was, as far as I could see, a good distro. Just not good enough for me to switch.

> **K.L. said:**
> Wait a minute... You are saying that it was MY fault?

Well, yeah. If it works for thousands of people and not for you, it's because you're doing something wrong. Seems logical to me.

---

### Post by JillSwift on 2009-09-01
> **aaaantoine said:**
>  On Ubuntu, if it isn't in the repository, I have to go out and either find a user created .deb package, or manually find all the dependencies and compile it myself.

On Arch, if it's not in the main repository, someone probably did all the dirty work for me in AUR.  I run yaourt -S obscureapp and if it shows up, it handles the dependencies for me.  I still have to compile it, but at least I'm not hunting for packages and dependencies.So that's what AUR is. Cool stuff.

> **aaaantoine said:**
> The flip side is, I think anyone can make an AUR install file, and they can be used to malicious ends if you're not careful.
Ok, slightly scary stuff too. (But that's the thing with new ideas, mmm?)

---

### Post by swoll1980 on 2009-09-01
> **Skripka said:**
> Methinks, as a moderator, you should be above calling posters idiots.  Either openly or implied.  Post reported.  This thread was a testimonial about someone moving from Ubuntu to Arch, why do you need to make it an insult fest?

It was another misunderstood comment, but I believe it refers to false assumptions, rather than stupidity.

---

### Post by swoll1980 on 2009-09-01
> **JillSwift said:**
> *offers peace mug of hot chocolate*

*drinks hot chocolate* mmmmm

---

### Post by Perfect Storm on 2009-09-01
> **JillSwift said:**
> Silliness.

I've no idea why folks insist that there's an objective hierarchy of ... well, of anything.

I don't at all mind folks talking about other distros - or other OSs outside of Linux based OSs. It's nice to hear about all the choices out there, what needs the fill well, what needs they don't fill well, interesting methodology and the various paradigms driving them. I think most folks do, too.

Where it falls flat is when there's an air of absolute "this is the best" surrounding the opinions. Worse still when it's said outright. The problem with that attitude is, it ignores the subjectivity of hierarchies.

Frankly, if there were some way of objectively rating all the distros, everyone would be forced by their own rational selves to *use* the best distro, with only a few statistical outliers. That not being the case, people are driven to use the distro that best suits them and thier needs and thier wishes, and even then it's not that often that one single distro does the trick.

So I encourage folks to talk about other distros here on these forums, where appropriate. I love hearing about them. Just keep in mind that your preference for distro X is only that, a preference. We all should keep that in mind too, when reading about those other preferences. There's no need to come galloping to the defense of our favorites, they're not under attack.

We hardly need a bunch of in-fighting over nothing other than differences of opinion, after all.

+1


I don't mind people talking about other distros/OSs, as long it isn't the zealous approach way in my opinion. I just think a lot of people forget personal preferences when posting a "zealous" post. 

It is understandable people have a passion for X,Y,Z distro but they have to accept other people have that as well. We are all individuals with diffrent taste and flavor and not mindless zombie drones dancing the same dance to the same tune.

---

### Post by K.L. on 2009-09-01
> **HymnToLife said:**
> Well, yeah. If it works for thousands of people and not for you, it's because you're doing something wrong. Seems logical to me.

You must be right, I clicked that button wrong! :D

---

### Post by Sporkman on 2009-09-01
> **Skripka said:**
> Methinks, as a moderator, you should be above calling posters idiots.  Either openly or implied.  Post reported.  This thread was a testimonial about someone moving from Ubuntu to Arch, why do you need to make it an insult fest?

It was suitably diplomatic, I see no reason to fly off the handle.

---

### Post by Bachstelze on 2009-09-01
> **K.L. said:**
> You must be right, I clicked that button wrong! :D

Button? What button? o.o The key to successful upgrades is

```
sudo apt-get update && sudo apt-get dist-upgrade
```

I must admit Ubuntu has a nasty habit of pushing GUIs that do not work, but the command-line never fails. ;)

---

### Post by stwschool on 2009-09-01
Personally I've upgraded Ubuntu without problems, so yeah assuming that it's broken because it didn't work for you is rather ignorant really.

Edit to say: I did it the GUI way previously as I wasn't so comfy with the terminal, but these days I do most of my package management in terminal so would probably upgrade that way too.

---

### Post by Simian Man on 2009-09-01
> **HymnToLife said:**
> Well, yeah. If it works for thousands of people and not for you, it's because you're doing something wrong. Seems logical to me.

Are you really saying that Ubuntu's dist-upgrade is flawless and bug free?  Because my experience along with many things I've heard from others flies in the face of that assertion.

[quote=bodyharvester]
how is it simplicity to have to build your own OS up from the ground?[/quote]
Simplicity does not equal easiness.  The two concepts are totally separate.

---

### Post by sisco311 on 2009-09-01
> **HymnToLife said:**
> 

```
sudo apt-get update && sudo apt-get dist-upgrade
```



Hey, we are talking about Arch:
```
pacman -Syu
```):P

---

### Post by Bachstelze on 2009-09-01
> **Simian Man said:**
> Are you really saying that Ubuntu's dist-upgrade is flawless and bug free?

Well, it never failed for me, and I've used it on countless different systems, a lot of which were not mine. Maybe I have some kind of superpower, then?

---

### Post by CJ Master on 2009-09-01
You know, in my time here, it generally seems whenever somebody mentions Arch, Ubuntu users attack him. Why can we not all live in peace...? ;)

[quote=GN2]My interest in Arch merely extends to having discussion of it banned from the Ubuntu forums.
I doubt that will ever happen but I live in hope.[/quote]

I lost any respect that I've ever had for you right there. Freedom of speech is restricted enough on this forum, Other OS Talk was removed, and now you're basically saying, "I hate arch. People talk about it. It should be banned. LONG LIVE SHUTTLEWORTH!"

---

### Post by K.L. on 2009-09-01
> **HymnToLife said:**
> Button? What button? o.o The key to successful upgrades is

```
sudo apt-get update && sudo apt-get dist-upgrade
```I must admit Ubuntu has a nasty habit of pushing GUIs that do not work, but the command-line never fails. ;)

I just did what's written in Ubuntu home page :)

> **stwschool said:**
> Personally I've upgraded Ubuntu without problems, so yeah assuming that it's broken because it didn't work for you is rather ignorant really.

I posted my personal experience. Just browse a forums a bit and you'll see that I'm not the only one who had bad experience with Ubuntus upgrade.

---

### Post by swoll1980 on 2009-09-01
There's really no way to tell what went wrong with your upgrade. Could have been something you compiled, or installed on your own? Hardware driver maybe?

---

### Post by Perfect Storm on 2009-09-01
> **Simian Man said:**
> Are you really saying that Ubuntu's dist-upgrade is flawless and bug free?  Because my experience along with many things I've heard from others flies in the face of that assertion.


Usually those who makes the loudest noise are those who gets the most attention. We rarely hear from people where it went smooth.
But I can give you one if you like ;)
We have 7 Ubuntu Computers at my work (with diffrent flavors X/K/etc.) all gui upgraded from 8.04 to 9.04, so goes it with my families computers as well. All of them with diffrent components and apps.

---

### Post by K.L. on 2009-09-01
> **swoll1980 said:**
> There's really no way to tell what went wrong with your upgrade. Could have been something you compiled, or installed on your own? Hardware driver maybe?

Don't know, really. I just did a fresh install after that.

---

### Post by swoll1980 on 2009-09-01
> **CJ Master said:**
> You know, in my time here, it generally seems whenever somebody mentions Arch, Ubuntu users attack him. Why can we not all live in peace...? ;)



I lost any respect that I've ever had for you right there. Freedom of speech is restricted enough on this forum, Other OS Talk was removed, and now you're basically saying, "I hate arch. People talk about it. It should be banned. LONG LIVE SHUTTLEWORTH!"

The way it is over hyped, and how some (not all) users find a way to insert it in every thread they post in (you know who you are) It gets annoying after a while.

---

### Post by Simian Man on 2009-09-01
> **Artificial Intelligence said:**
> Usually those who makes the loudest noise are those who gets the most attention. We rarely hear from people where it went smooth.
But I can give you one if you like ;)
We have 7 Ubuntu Computers at my work (with diffrent flavors X/K/etc.) all gui upgraded from 8.04 to 9.04, so goes it with my families computers as well. All of them with diffrent components and apps.

I'm not saying that it is a horrible thing, or that it never works.  It worked three out of the four times I tried it.  I just think it's a bit rich for a moderator to essentially say a user somehow did it wrong when it didn't work.

---

### Post by stwschool on 2009-09-01
> **CJ Master said:**
> You know, in my time here, it generally seems whenever somebody mentions Arch, Ubuntu users attack him.

Could it possibly be because Arch users on here can be incredibly annoying sometimes? Ok yes we know about Arch, now quit banging on about it (and btw I'm someone who actually rather likes Arch as a concept and I'm working my way around learning it).

---

### Post by swoll1980 on 2009-09-01
> **Artificial Intelligence said:**
> Usually those who makes the loudest noise are those who gets the most attention. We rarely hear from people where it went smooth.
But I can give you one if you like ;)
We have 7 Ubuntu Computers at my work (with diffrent flavors X/K/etc.) all gui upgraded from 8.04 to 9.04, so goes it with my families computers as well. All of them with diffrent components and apps.

I've upgraded from every version since 7.04 without a hitch.

---

### Post by CJ Master on 2009-09-01
> **swoll1980 said:**
> The way it is over hyped, and how some (not all) users find a way to insert it in every thread they post in (you know who you are) It gets annoying after a while.

Of course, they are annoying, but it's a (vocal) minority, and they generally learn after a while.

---

### Post by stwschool on 2009-09-01
> **Simian Man said:**
> I'm not saying that it is a horrible thing, or that it never works.  It worked three out of the four times I tried it.  I just think it's a bit rich for a moderator to essentially say a user somehow did it wrong when it didn't work.
I don't think the mod said that. The mod simply suggested that assuming that the problem lies 100% with one thing without ruling out the other is wrong, especially when in 99% of cases the thing being blamed works fine. I hope that makes some sense.

---

### Post by Bachstelze on 2009-09-01
> **Simian Man said:**
> I'm not saying that it is a horrible thing, or that it never works.  It worked three out of the four times I tried it.  I just think it's a bit rich for a moderator to essentially say a user somehow did it wrong when it didn't work.

Or maybe you also did something wrong the fourth time. ;) The only times where it didn't work for me were when... I did something wrong. :p

---

### Post by K.L. on 2009-09-01
> **Simian Man said:**
> **I'm not saying that it is a horrible thing, or that it never works.**  It worked three out of the four times I tried it. ** I just think it's a bit rich for a moderator to essentially say a user somehow did it wrong when it didn't work.**

Exactly.

---

### Post by MONODA on 2009-09-01
> My Ubuntu does it in 9 seconds. pwn3d
WOW what are ur specs? What DM/WM?

> Arch teaches you that daemons are in /etc/rc.d? It's a really bad teacher, then. Last I checked, it was init scripts.
well in arch there in /etc/rc.d/ unlike most other distros.

> Just because "most people" believe something doesn't make it right.
I didnt say anything about believing anything, it's what many people have found works for them when other things did not.

---

### Post by Simian Man on 2009-09-01
> **HymnToLife said:**
> Or maybe you also did something wrong the fourth time. ;) The only times where it didn't work for me were when... I did something wrong. :p

Oh actually you're right I typed 'sudo rm -rf /' instead of 'sudo apt-get dist-upgrade'.  How can I have been so silly??

---

### Post by Perfect Storm on 2009-09-01
> **Simian Man said:**
> I'm not saying that it is a horrible thing, or that it never works.  It worked three out of the four times I tried it.  I just think it's a bit rich for a moderator to essentially say a user somehow did it wrong when it didn't work.

I may agree with HymnToLife to a degree. And yes the upgrade may fail because of something else than the person behind the computer. When I agree HymnToLife on this point, is that a failed upgrade can be something to do how the user have manually edited, install unsupported packages or made radical changes to the system.
A good exampel of this was back in the automatix (an installer script) days. It was popular and alot of newbies used it to get flash, java etc. but there was this little problem; It would break your Ubuntu if you upgraded to a newer version of Ubuntu. It was a nightmare in the support forum to say it at least.

---

### Post by Bachstelze on 2009-09-01
> **MONODA said:**
> WOW what are ur specs? What DM/WM?

Celeron 220, 1G of RAM, the DE obviously doesn't matter but if you want to know, XFCE.

> **MONODA said:**
> 
I didnt say anything about believing anything, it's what many people have found works for them when other things did not.

Fair enough, but once again, it is perfectly possible to install a minimal Ubuntu system and build from that, and it will give mostly te same result as Arch. Still lots of people believe (or pretend to believe) that Ubuntu can not be installed that way. And that's wrong, no matter how many people believe this.

---

### Post by RiceMonster on 2009-09-01
> **Simian Man said:**
> Oh actually you're right I typed 'sudo rm -rf /' instead of 'sudo apt-get dist-upgrade'.  How can I have been so silly??

I hate it when that happens!

---

### Post by sydbat on 2009-09-01
> **HymnToLife said:**
> Fair enough, but once again, it is perfectly possible to install a minimal Ubuntu system and build from that, and it will give mostly te same result as Arch. Still lots of people believe (or pretend to believe) that Ubuntu can not be installed that way. And that's wrong, no matter how many people believe this.I think my signature sums this (and the thread) up nicely...

---

### Post by Bachstelze on 2009-09-01
> **Simian Man said:**
> Oh actually you're right I typed 'sudo rm -rf /' instead of 'sudo apt-get dist-upgrade'.  How can I have been so silly??

Depending on your system, there might be more to it, of course... And don't tell me [font=monospace]pacman -Syu[/font] works in all cases. I'm pretty sure I could easily make my system require additional steps.

---

### Post by MONODA on 2009-09-01
> Fair enough, but once again, it is perfectly possible to install a minimal Ubuntu system and build from that, and it will give mostly te same result as Arch. Still lots of people believe (or pretend to believe) that Ubuntu can not be installed that way. And that's wrong, no matter how many people believe this.

I actually had no idea that you could do that :P anyway Im happy with arch and whenever I post anything promoting arch its in hope that others might try it and end up liking it like I have done. BTW I'm still having trouble believing that you get to X in 9 seconds, what did you do (sorry dont mean to hijack the thread but I cant help asking)?

> And don't tell me pacman -Syu works in all cases. 
well I've never had it not work but sometimes things break, but I either dont notice (oops?) or there is a post on the main page or I did something wrong (the latter is the most common :P, I cant help doing stupid stuff, its just so exciting :P)

---

### Post by CJ Master on 2009-09-01
> **HymnToLife said:**
> Depending on your system, there might be more to it, of course... And don't tell me [font=monospace]pacman -Syu[/font] works in all cases. I'm pretty sure I could easily make my system require additional steps.

It has always worked for me, and if you don't update Xorg then there's pretty much zilch chance of breakage. But, this is just in my experiences.

---

### Post by Perfect Storm on 2009-09-01
> **MONODA said:**
> BTW I'm still having trouble believing that you get to X in 9 seconds, what did you do (sorry dont mean to hijack the thread but I cant help asking)?

I get in X on Ubuntu in 6 sec. and that's without editing/removing stuff. But Again my computer is pretty fast.

---

### Post by Bachstelze on 2009-09-01
> **MONODA said:**
> BTW I'm still having trouble believing that you get to X in 9 seconds, what did you do (sorry dont mean to hijack the thread but I cant help asking)?

Easy:

1. Install minimal system
2. [font=monospace]sudo apt-get install xorg xfce4 gdm[/font]
3. Reboot
4. ????
5. PROFIT!

---

### Post by K.L. on 2009-09-01
> **Artificial Intelligence said:**
> I get in X on Ubuntu in 6 sec. and that's without editing/removing stuff. But Again my computer is pretty fast.

Specs please? :D

---

### Post by MONODA on 2009-09-01
> I get in X on Ubuntu in 6 sec. 

I think I just wet myself... May I ask for specs?

> Easy:

1. Install minimal system
2. sudo apt-get install xorg xfce4 gdm
3. Reboot
4. ????
5. PROFIT!

aha I see... :P

---

### Post by chris4585 on 2009-09-01
> **wmcbrine said:**
> This is the third post in this thread to imply that you have to reinstall Ubuntu to get a new version. That's just not true. All you have to do is upgrade.

Some people have issues with upgrading via update-manager, and can end up with a borked system.  Personally why waste my own time with upgrading if it could possibly break, and then reinstall. When I could have simply just reinstalled in the first place.  Some people have their own ways of doing things, I have all of my media on a separate HDD so reinstalling is a sinch.

I use both, Ubuntu, and Arch, they both are awesome.  I do agree Arch is over hyped on this forum, I wish it wasn't, and wish it was a little more respected, the same way Ubuntu is.

> **aaaantoine said:**
> I have to say that this is probably one of my favorite things about Arch, even though I pay it little mind.

On Ubuntu, if it isn't in the repository, I have to go out and either find a user created .deb package, or manually find all the dependencies and compile it myself.

On Arch, if it's not in the main repository, someone probably did all the dirty work for me in AUR.  I run yaourt -S obscureapp and if it shows up, it handles the dependencies for me.  I still have to compile it, but at least I'm not hunting for packages and dependencies.


I agree whole heartedly, that is my absolute favorite thing about Arch.  I never have to hunt down anything on a webpage to install anything, it's an awesome feeling knowing everything is at your fingertips literally.

Not everything everyone says is true, a lot of people shout how fast their Arch boot time is, mine is rather slow, but I can live with that, last time I rebooted was 21days ago.  I don't have a slow computer neither by modern standards, my laptop with Ubuntu boots faster with about equal specs.

I use Arch on my desktop, and Ubuntu on my laptop, and several other computers for ease of use.

---

### Post by Perfect Storm on 2009-09-01
Sure;

[http://polarbeardk.blogspot.com/2007/11/new-pc-64-bit.html](http://polarbeardk.blogspot.com/2007/11/new-pc-64-bit.html)

---

### Post by chris200x9 on 2009-09-01
> **gn2 said:**
> That can be done with many distributions, so it's really no big deal.
Tell me something truly unique that Arch has?

[silence]

pacman > ALL, though I'm really starting to like ports but yea pacman is still better.

---

### Post by mrgnash on 2009-09-01
> **swoll1980 said:**
> I've upgraded from every version since 7.04 without a hitch.

Me too, except I only made it to 8.10 before my PC died (hardware failure -- not Ubuntu's fault :P ). In any case, the upgrades were always pretty damn smooth considering how much I tinkered with my system, and that I usually upgraded to the next release while it was still in alpha.

---

### Post by LowSky on 2009-09-01
Wheres a "I like Windows 7 thread" when you need to do some bashing...LOL

Guys Arch is Linux, it shares much with Ubuntu... Let it go. No reason to be annoyed at someones personal choice in distros. 

I think Arch is a great teaching tool. It allows Ubuntu users to try a hand at something a bit more challaging. Don't give them grief for enjoying their hard work of installing Arch.

well I'm off to help some noobs in teh ABT forums...

---

### Post by K.L. on 2009-09-01
> **Artificial Intelligence said:**
> Sure;

[http://polarbeardk.blogspot.com/2007/11/new-pc-64-bit.html](http://polarbeardk.blogspot.com/2007/11/new-pc-64-bit.html)

Nice. But it's minimal install, right?

---

### Post by Perfect Storm on 2009-09-01
> **K.L. said:**
> Nice. But it's minimal install, right?

Actually no. There was a surprise performance boost when I went from current version of Ubuntu to another (back then). And it have been like that ever since (and yes everything works as it should).
When I gathered the pieces for this computer I made some research about every pieces to get the most linux friendly parts. (with exception of the audio card).

---

### Post by swoll1980 on 2009-09-01
> **LowSky said:**
> Wheres a "I like Windows 7 thread" when you need to do some bashing...LOL

Guys Arch is Linux, it shares much with Ubuntu... Let it go. No reason to be annoyed at someones personal choice in distros. 


There's a difference between being tolerant of people's choices, and being tolerant of spam.

---

### Post by RiceMonster on 2009-09-01
> **swoll1980 said:**
> There's a difference between being tolerant of people's choices, and being tolerant of spam.

What spam?

---

### Post by K.L. on 2009-09-01
> **Artificial Intelligence said:**
> Actually no. There was a surprise performance boost when I went from current version of Ubuntu to another (back then). And it have been like that ever since (and yes everything works as it should).
When I gathered the pieces for this computer I made some research about every pieces to get the most linux friendly parts. (with exception of the audio card).

I see. My PC is quite fast too, Quad Core, 4GB RAM, 7200rpm HDD (too lazy to write down everything :D), everything works out of the box, but it still boots in 20 secs.

And I thought my PC is Linux friendly :D

---

### Post by Skripka on 2009-09-01
> **swoll1980 said:**
> There's a difference between being tolerant of people's choices, and being tolerant of spam.

Ironically it was y'all Ubuntu folks who chose to make this an Ubuntu v. Arch thread.

---

### Post by Perfect Storm on 2009-09-01
> **K.L. said:**
> I see. My PC is quite fast too, Quad Core, 4GB RAM, 7200rpm HDD (too lazy to write down everything :D), everything works out of the box, but it still boots in 20 secs.

And I thought my PC is Linux friendly :D

I don't know why yours takes 20 secs. can it be some hardware combination versus the drivers/core?
Nevertheless I actually don't give much for bootups, in my world it's after the bootup that counts ;)

---

### Post by swoll1980 on 2009-09-01
> **RiceMonster said:**
> What spam?

I'm not even going to answer that. If you don't know what I'm talking about, then you will never know I guess, or you choose not to know.

---

### Post by kk0sse54 on 2009-09-01
> **chris200x9 said:**
> pacman > ALL, though I'm really starting to like ports but yea pacman is still better.

I like to use ABS to satisfy any ports like urges I get in Arch :), however IMO to make abs usable you need to write a few scripts first. 

Even though I'm primarily a FreeBSD user that's the one thing I like about Arch, versatility.

---

### Post by K.L. on 2009-09-01
> **Artificial Intelligence said:**
> I don't know why yours takes 20 secs. can it be some hardware combination versus the drivers/core?

I don't know, really :D It takes 20 secs to boot with most newer (15 secs with some) Linux distros (Ubuntu, Arch, Fedora, Debian).

> Nevertheless I actually don't give much for bootups, in my world it's after the bootup that counts ;)

True. I was just curious.

---

### Post by swoll1980 on 2009-09-01
> **RiceMonster said:**
> What spam?

I will answer that for people that are new around here. When the thread title is **"What's your favorite web browser?"** and one of the responses is "Firefox on Arch is the best", or the thread is **"What media player do you use?"** and someone says "mplayer on Arch rules!!!11!" **When your in Absolute beginner talk, and someone has a problem with there audio:** "You should install Arch Linux" **"What's your favorite pie?"** "Nothing taste better than Arch Linux pie!!!" If you don't see this kind of thing 10 times a week, then your on a different Internet than me.

---

### Post by Viva on 2009-09-01
> **swoll1980 said:**
> I will answer that for people that are new around here. When the thread title is **"What's your favorite web browser?"** and one of the responses is "Firefox on Arch is the best", or the thread is **"What media player do you use?"** and someone says "mplayer on Arch rules!!!11!" **When your in Absolute beginner talk, and someone has a problem with there audio:** "You should install Arch Linux" **"What's your favorite pie?"** "Nothing taste better than Arch Linux pie!!!"

:lolflag:

---

### Post by SonicSteve on 2009-09-01
> **JillSwift said:**
> Silliness.

I've no idea why folks insist that there's an objective hierarchy of ... well, of anything.

I don't at all mind folks talking about other distros - or other OSs outside of Linux based OSs. It's nice to hear about all the choices out there, what needs the fill well, what needs they don't fill well, interesting methodology and the various paradigms driving them. I think most folks do, too.

Where it falls flat is when there's an air of absolute "this is the best" surrounding the opinions. Worse still when it's said outright. The problem with that attitude is, it ignores the subjectivity of hierarchies.

Frankly, if there were some way of objectively rating all the distros, everyone would be forced by their own rational selves to *use* the best distro, with only a few statistical outliers. That not being the case, people are driven to use the distro that best suits them and thier needs and thier wishes, and even then it's not that often that one single distro does the trick.

So I encourage folks to talk about other distros here on these forums, where appropriate. I love hearing about them. Just keep in mind that your preference for distro X is only that, a preference. We all should keep that in mind too, when reading about those other preferences. There's no need to come galloping to the defense of our favorites, they're not under attack.

We hardly need a bunch of in-fighting over nothing other than differences of opinion, after all.

I have found that most people get very defensive far too quickly. We're all guilty of it at times. What makes it harder is that text doesn't communicate the whole story, it's missing the other communication factors like, intent, facial expression etc. Try making a friendly dig at someone in an email, usually it gets mis-interpreted because it's only robotic text.


On the subject of discussing other distros, lets do it! If we end up in angry words its simply childishness in immaturity. It's like players on the same team ending up in a fight and forgetting their common bond. What else is new under the sun?

---

### Post by RiceMonster on 2009-09-01
> **swoll1980 said:**
> I will answer that for people that are new around here. When the thread title is **"What's your favorite web browser?"** and one of the responses is "Firefox on Arch is the best", or the thread is **"What media player do you use?"** and someone says "mplayer on Arch rules!!!11!" **When your in Absolute beginner talk, and someone has a problem with there audio:** "You should install Arch Linux" **"What's your favorite pie?"** "Nothing taste better than Arch Linux pie!!!" If you don't see this kind of thing 10 times a week, then your on a different Internet than me.

I do see it, but I don't consider it spam, and I'm not annoyed by it. Yeah there's a lot of vocal Arch users, but it only annoys me when it's inappropriate. For example: "Hey, I want a distro that comes with GNOME by default, is easy to use and has codecs pre installed" "You should try arch!". Other than that, it's only as annoying as you make it.

---

### Post by swoll1980 on 2009-09-01
> **RiceMonster said:**
> it only annoys me when it's inappropriate. For example: "Hey, I want a distro that comes with GNOME by default, is easy to use and has codecs pre installed" "You should try arch!".

Yeah, good example. I see that one way to much as well.

---

### Post by chucky chuckaluck on 2009-09-01
to heck with this place. i'm going over to post at archsux.org.

---

### Post by SonicSteve on 2009-09-01
> **swoll1980 said:**
> Yeah, good example. I see that one way to much as well.


Instead of getting annoyed try giving the offender Grace, patience, and understanding. There's no way you can know what their full intent is. They might simply be really excited about something and want to share it with you. Even if they are being obnoxious, does it really matter? Grace, patience and understanding revolutionary.

---

### Post by Stan_1936 on 2009-09-01
> **&#20170 said:**
> ...I would say now a days must distros are just as good as the others, **I prefer Ubuntu over all**.

EXACTLY!  I agree.

Ubuntu ftw....

---

### Post by K.L. on 2009-09-01
> **swoll1980 said:**
> Yeah, good example. I see that one way to much as well.

A good example? I can't believe people say stuff like that :lolflag:

---

### Post by swoll1980 on 2009-09-01
> **SonicSteve said:**
> Instead of getting annoyed try giving the offender Grace, patience, and understanding. There's no way you can know what their full intent is. They might simply be really excited about something and want to share it with you. Even if they are being obnoxious, does it really matter? Grace, patience and understanding revolutionary.

I'm trying. Meekness is one of the qualities I need to work on.

---

### Post by SonicSteve on 2009-09-01
> **swoll1980 said:**
> I'm trying. Meekness is one of the qualities I need to work on.

Good on ya! You just succeeded.

---

### Post by Bachstelze on 2009-09-01
> **SonicSteve said:**
> Instead of getting annoyed try giving the offender Grace, patience, and understanding. There's no way you can know what their full intent is. They might simply be really excited about something and want to share it with you. Even if they are being obnoxious, does it really matter? Grace, patience and understanding revolutionary.

This could work for the OP, but not for the others. They are long time Arch users, they know what they're doing: preaching. And that's why it does matter.

---

### Post by Hallvor on 2009-09-01
I love these threads. A little popcorn and it would be perfect.

---

### Post by kk0sse54 on 2009-09-01
> **HymnToLife said:**
> This could work for the OP, but not for the others. They are long time Arch users, they know what they're doing: preaching. And that's why it does matter.

That's news to me.

---

### Post by &#32 Greg on 2009-09-01
I think the real problem is the lack of Other OS Talk- it basically dissolved into the Cafe and has caused a lot of dissent.

I know I joined UF because it's the most active Linux forum out there- it was the best place to discuss generic Linux stuff. Arch has a big following for a few reasons:

1) Rolling Release
2) Pacman, yaourt, and ABS
3) Makes people feel competent really easily- and in some cases makes them more competent

I know I use Arch because I get something near to the control of the source based distros without the annoyance of compiling all my packages. I prefer it over Ubuntu minimal because I don't like all the dependencies apt pulls in. For instance, if I install LXDE, I see no reason why gdm needs to come with it. I also like Arch's size when it comes to number of packages between the repos and the AUR.

---

### Post by Stan_1936 on 2009-09-01
Good for you.  Now, tell me why Ubuntu users should care....

---

### Post by Bachstelze on 2009-09-01
> **  Greg said:**
> I prefer it over Ubuntu minimal because I don't like all the dependencies apt pulls in. For instance, if I install LXDE, I see no reason why gdm needs to come with it.

Lies again. gdm *is not* a dependency of lxde.

[http://packages.ubuntu.com/jaunty/lxde](http://packages.ubuntu.com/jaunty/lxde)

I'm sick of this.

---

### Post by Skripka on 2009-09-01
> **Stan_1936 said:**
> Good for you.  Now, tell me why Ubuntu users should care....

Well, isn't it obvious?

[quote=gn2]
That can be done with many distributions, so it's really no big deal.
Tell me something truly unique that Arch has?
[/quote]


In short y'all asked, and folks are answering.  Why do y'all get grumpy when people answer your questions?

---

### Post by Bachstelze on 2009-09-01
> **Skripka said:**
> 
In short y'all asked, and folks are answering.  Why do y'all get grumpy when people answer your questions?

Because their answers are for the most part wrong.

---

### Post by &#32 Greg on 2009-09-01
> **HymnToLife said:**
> Lies again. gdm *is not* a dependency of lxde.

[http://packages.ubuntu.com/jaunty/lxde](http://packages.ubuntu.com/jaunty/lxde)

I'm sick of this.

Well, then I'd like to know why it magically comes in the two times that I installed lxde on an Ubuntu minimal.

---

### Post by Bachstelze on 2009-09-01
> **  Greg said:**
> Well, then I'd like to know why it magically comes in the two times that I installed lxde on an Ubuntu minimal.

Probably because you installed it with Aptitude, which automatically installs recommended packages in addition to dependencies. That's why I never use it, by the way.

---

### Post by K.L. on 2009-09-01
> **HymnToLife said:**
> Probably because you installed it with Aptitude, which automatically installs recommended packages in addition to dependencies. That's why I never use it, by the way.

How to install packages without apt then? Just curious.

---

### Post by &#32 Greg on 2009-09-01
> **HymnToLife said:**
> Probably because you installed it with Aptitude, which automatically installs recommended packages in addition to dependencies. That's why I never use it, by the way.

No, it was definitely through apt-get. Now I'm curious... I'm going to need to experiment in VMs with this. Right now my best guess is that Gnome was on there at one point, even though it had been removed, so maybe it just pulled gdm in since the package was already on the system.

---

### Post by earthpigg on 2009-09-01
> **Hallvor said:**
> I love these threads. A little popcorn and it would be perfect.

+1. i like how 7 pages ago was also 2 hours ago.

may as well toss my $0.02 in, but ill avoid the emotional disagreements.

arch is linux.
ubuntu is linux.

they both take the word 'simplicity' to extremes in their own way - and both do an outstanding job of it.

once we all recall that most words in the dictionary have more than one definition, we can all realize that this doesn't mean one is better than the other, or that one group of users is better than the other. that is just silly. 

arch excels at implementing the definition of 'simplicity' that it likes.
ubuntu excels at implementing the definition of 'simplicity' that it likes.

if we want to argue about which is 'better', then we may as well skip any/all mention of the distros and argue about which definition of the word 'simple' we like.

tldr version:
arch is an outstanding orange, and good at tasting like an orange.
ubuntu is an outstanding apple, and good at tasting like an apple.
both are great examples of fruit.

edit: o, and BSD is a potatoe. :lolflag:

---

### Post by Bachstelze on 2009-09-01
> **K.L. said:**
> How to install packages without apt then? Just curious.

Aptitude is not the only frontend to Apt. There is apt-get, Synaptic, the Ubuntu's Add/Remove thingie, and probably lots of others.

---

### Post by K.L. on 2009-09-01
> **HymnToLife said:**
> Aptitude is not the only frontend to Apt. There is apt-get, Synaptic, the Ubuntu's Add/Remove thingie, and probably lots of others.

I thought Aptitude and apt-get is the same thing. This thread isn't useless after all, I just learned something new :D

---

### Post by swoll1980 on 2009-09-01
> **  Greg said:**
>  I prefer it over Ubuntu minimal because I don't like all the dependencies apt pulls in. For instance, if I install LXDE, I see no reason why gdm needs to come with it. I also like Arch's size when it comes to number of packages between the repos and the AUR.

> **  Greg said:**
> No, it was definitely through apt-get. Now I'm curious... I'm going to need to experiment in VMs with this. Right now my best guess is that Gnome was on there at one point, even though it had been removed, so maybe it just pulled gdm in since the package was already on the system.


You said it was a Ubuntu minimal install. You just lost your credibility.

---

### Post by &#32 Greg on 2009-09-01
> **swoll1980 said:**
> You said it was a Ubuntu minimal install. You just lost your credibility.

It was. I'm assuming you're refering to the fact that Gnome was on there at one point. Based on that assumption, I will inform you that it was not my computer. I set up an Ubuntu minimal install on a friend's computer. I then compiled xmonad/xmobar through cabal. My friend wanted to play with other DEs/WMs for a guest account. He first went with Gnome, then removed it and decided to try out LXDE.

I'd prefer it if you didn't assume things.

---

### Post by Dragonbite on 2009-09-01
The Fedora, CentOS, PCLinuxOS, Mandriva, openSUSE, Mint, etc. users aren't as vocal (or "in your face") as Arch users here and arguably there are probably just as many or more users of these distros but you don't see them because they are more discreet.

---

### Post by doorknob60 on 2009-09-01
Glad you like Arch. My Arch install has probably remained here longer than any other OS on this computer without reinstalling, and it's still just as fast and stable as a new installation. That's why I like Arch. I could never do that with Ubuntu, I always manage to screw that up in about 3 months :P But yeah, I love Arch :D And AUR is just amazing, I wish Ubuntu had something like it (PPAs don't even come close).

---

### Post by gn2 on 2009-09-01
> **K.L. said:**
> All? Do all Arch users do this? Really?

You misinterpreted what I wrote.
The "all" refers to all those who prattle on about Arch in the Ubuntu forums.

> **sisco311 said:**
> pacman -Syu

Yeah, it's really quicker to copy and paste a few characters less. :rolleyes:

> **CJ Master said:**
> I lost any respect that I've ever had for you right there. Freedom of speech is restricted enough on this forum, Other OS Talk was removed, and now you're basically saying, "I hate arch. People talk about it. It should be banned. LONG LIVE SHUTTLEWORTH!"

You are mistaken, I have never said that I hate Arch, what bugs me is all the evangelist guff posted here by Arch zealots.
As already observed by Hymn To Life, much of it is wrong.
This is a private forum, restriction on allowed topics does not in any way impinge on anyone's fundamental right to freedom of expression.
Other OS talk was removed for a reason, but the group who seem to flout it's removal the most are the Archers who continue to discuss Archery.

> **chris200x9 said:**
> pacman > ALL, though I'm really starting to like ports but yea pacman is still better.

Cor, Arch has a package management application?
How fantastic is that!

---

### Post by swoll1980 on 2009-09-01
> **  Greg said:**
> It was. I'm assuming you're refering to the fact that Gnome was on there at one point. Based on that assumption, I will inform you that it was not my computer. I set up an Ubuntu minimal install on a friend's computer. I then compiled xmonad/xmobar through cabal. My friend wanted to play with other DEs/WMs for a guest account. He first went with Gnome, then removed it and decided to try out LXDE.

I'd prefer it if you didn't assume things.

Assume what? Your using "your friend's" "minimal Ubuntu install", which you had no idea what had been done to it, and used it as evidence that Ubuntu's package manager installs unneeded dependencies. Trust me, you lost your credibility.

FYI the command to uninstall the gnome metapackage looks like this

```
sudo apt-get remove alacarte app-install-data-commercial at-spi avahi-daemon bittorrent bluez-pin brltty-x11 bug-buddy capplets-data contact-lookup-applet dbus-1-utils deskbar-applet desktop-base desktop-file-utils ekiga eog esound evince evolution evolution-data-server evolution-exchange evolution-plugins evolution-webcal festival festlex-cmu festlex-poslex festvox-kallpc16k file-roller firefox firefox-gnome-support fping gaim gaim-data gcalctool gconf-editor gconf2 gconf2-common gdb gdebi gdm gedit gedit-common gimp gimp-data gimp-print gimp-python gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-mag gnome-media gnome-menus gnome-mime-data gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gnopernicus gok gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice gtk2-engines-ubuntulooks gtkhtml3.8 gucharmap guile-1.6-libs hal-device-manager hwdb-client im-switch language-selector launchpad-integration libaa1 libatk1.0-0 libatspi1.0-0 libavahi-core4 libavahi-glib1 libavc1394-0 libbeagle0 libbeecrypt6 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbtctl2 libcamel1.2-8 libcdio6 libcompfaceg1 libcroco3 libdaemon0 libdjvulibre15 libdv4 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-7 libedataserverui1.2-6 libeel2-2 libeel2-data libegroupwise1.2-9 libestools1.2 libexchange-storage1.2-1 libgail-common libgail-gnome-module libgail17 libgconf2-4 libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common libgimp2.0 libgksu1.2-1 libgksuui1.0-1 libglade2-0 libglew1 libglib-perl libglib2.0-data libgnome-desktop-2 libgnome-keyring0 libgnome-mag2 libgnome-menu2 libgnome-pilot2 libgnome-speech3 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomebt0 libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomecupsui1.0-1c2a libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgpod0 libgsf-1-113 libgsf-1-common libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkhtml2-0 libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgtop2-7 libgucharmap4 libguile-ltdl-1 libgutenprintui2-1 libkpathsea4 liblaunchpad-integration0 liblircclient0 liblpint-bonobo0 libmetacity0 libnautilus-burn3 libnautilus-extension1 libnotify1 liboil0.3 libopal-2.2.0 libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpisync0 libpoppler1-glib libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 librpm4 librsvg2-2 librsvg2-common libsdl1.2debian libsdl1.2debian-alsa libsexy2 libshout3 libsoup2.2-8 libtotem-plparser1 libvte-common libvte4 libwmf0.2-7 libwnck-common libwnck18 libxklavier10 libxml2-utils libxres1 metacity nautilus nautilus-cd-burner nautilus-data nautilus-sendto notification-daemon openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk pkg-config python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras python-gst0.10 python-gtk2 python-launchpad-integration python-libxml2 python-vte python2.4-cairo python2.4-glade2 python2.4-gnome2 python2.4-gnome2-desktop python2.4-gnome2-extras python2.4-gobject python2.4-gtk2 rdesktop rhythmbox rpm rss-glx scim scim-gtk2-immodule scim-modules-socket screensaver-default-images serpentine shared-mime-info sharutils sound-juicer ssh-askpass-gnome synaptic system-tools-backends tangerine-icon-theme tango-icon-theme tango-icon-theme-common totem totem-gstreamer tsclient ttf-arphic-ukai ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds unattended-upgrades update-manager update-notifier vino vnc-common whois xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xvncviewer yelp zenity
```

not

```
sudo apt-get remove gnome
```

---

### Post by earthpigg on 2009-09-01
> **swoll1980 said:**
> You said it was a Ubuntu minimal install. You just lost your credibility.

unless you use the --no-install-recommends argument, ubuntu will install gdm with lxde.

---

### Post by &#32 Greg on 2009-09-01
> **swoll1980 said:**
> Assume what? Your using "your friend's" "minimal Ubuntu install", which you had no idea what had been done to it, and used it as evidence that Ubuntu's package manager installs unneeded dependencies. Trust me, you lost your credibility.

Believe it or not, not everything has to be seen as evidence. This happened, and it was a mildly annoying experience for me. I know pretty much what was done to the system. What I know more, however, is that gdm wasn't there to start with, and when LXDE was installed, it appeared from the depths of the abyss.

---

### Post by swoll1980 on 2009-09-01
> **earthpigg said:**
> unless you use the --no-install-recommends argument, ubuntu will install gdm with lxde.

Whether, or not he is right, or wrong, is irrelevant to credibility. see previous post.

---

### Post by swoll1980 on 2009-09-01
> **  Greg said:**
> Believe it or not, not everything has to be seen as evidence. 

I know. I believe they call that politics.

---

### Post by Bachstelze on 2009-09-01
> **earthpigg said:**
> unless you use the --no-install-recommends argument, ubuntu will install gdm with lxde.

Holy crap, you're right! When was that changed? apt-get, you disappoint me. Maybe I should switch to Arch...

---

### Post by LowSky on 2009-09-01
Why is this thread so angry!

You don't see people screaming at the guy praising Puppy because Ubutnu fails to install on his hardware.


Im going to install Arch right now.

---

### Post by Dragonbite on 2009-09-01
> **LowSky said:**
> Why is this thread so angry!

You don't see people screaming at the guy praising Puppy because Ubutnu fails to install on his hardware.


Im going to install Arch right now.

Because the number of people piping in with "Install Arch" and "Arch is so great" blah blah blah is only surpassed by people bashing Microsoft and saying how much they hate them.

Well, maybe not second if you filter the Microsoft bashing to only those that properly spell "Microsoft" and not use Microshaft and M$ and such.

:)

---

### Post by Stan_1936 on 2009-09-01
> **  Greg said:**
> I think the real problem is the lack of Other OS Talk- it basically dissolved into the Cafe and has caused a lot of dissent....

That is SO TRUE!!!  Good eye.....

---

### Post by Raffles10 on 2009-09-01
I agree with many of the comments here...Arch...what's all the fuss about. I've tried Arch with all four DE's and can honestly say it doesn't beat any of the other distro's, Linux is Linux after all.

Most people try Arch because they think they're being clever. All this stuff about Arch being difficult to install is just rubbish, it's time consuming, not difficult. And after all that setting up you've got a system that's no better than Ubuntu that installs in less than half an hour. I actually found Ubuntu 9.04 to boot and run quicker than Arch + Xfce4.

One other thing, about the Arch forums...it's a boring place....lots of people slapping themselves on the back and thinking that they're clever because they're using a system that needs constant repairing thanks to 'pacman -Syu'.

Arch is for people with more time than sense.

---

### Post by sydbat on 2009-09-01
> **Dragonbite said:**
> Because the number of people piping in with "Install Arch" and "Arch is so great" blah blah blah is only surpassed by people bashing Microsoft and saying how much they hate them.

Well, maybe not second if you filter the Microsoft bashing to only those that properly spell "Microsoft" and not use Microshaft and M$ and such.

:)ZOMG!!!1!! I think you're onto something there...ARCH IS WINDOWS!!11! Those M$ bastards...:P

---

### Post by Skripka on 2009-09-01
> **Dragonbite said:**
> Because the number of people piping in with "Install Arch" and "Arch is so great" blah blah blah is only surpassed by people bashing Microsoft and saying how much they hate them.

Well, maybe not second if you filter the Microsoft bashing to only those that properly spell "Microsoft" and not use Microshaft and M$ and such.

:)

You just hate 99% of the people on UF, now don't you? :)

---

### Post by Tristam Green on 2009-09-01
> **Skripka said:**
> You just hate 99% of the people on UF, now don't you? :)

99% of people on any distro forum, more specifically.

---

### Post by Perfect Storm on 2009-09-01
[http://www.youtube.com/watch?v=1dYpnd_9TFs](http://www.youtube.com/watch?v=1dYpnd_9TFs)

---

### Post by aysiu on 2009-09-01
> **HymnToLife said:**
> Holy crap, you're right! When was that changed? apt-get, you disappoint me. Maybe I should switch to Arch...
It's new starting with Intrepid.

From [the Jaunty release notes](http://www.ubuntu.com/getubuntu/releasenotes/904): > **Recommended packages installed by default**
In accordance with the Debian Policy Manual (which says "The 'Recommends' field should list packages that would be found together with this one in all but unusual installations"), the package management system now installs packages listed in the Recommends: field of other installed packages as well as Depends: by default. If you want to avoid this for specific packages, use apt-get --no-install-recommends; if you want to make this permanent, set APT::Install-Recommends "false"; in /etc/apt/apt.conf. Be aware that this may result in missing features in some programs.

(This change was made in Ubuntu 8.10.)

---

### Post by Namtabmai on 2009-09-01
> **Artificial Intelligence said:**
> [http://www.youtube.com/watch?v=1dYpnd_9TFs](http://www.youtube.com/watch?v=1dYpnd_9TFs)

GAHHH SKA!!!

You really ought to have put a warning around that.

;)

---

### Post by Dragonbite on 2009-09-01
> **Skripka said:**
> You just hate 99% of the people on UF, now don't you? :)

Yeah, I'm just trying to find that 1% I don't hate and .. - eh? waitaminute.. THAT'S ME!!  Die you bloody *******! *gunshot!* *gunshot!* *gunshot!*




*looks at avatar* I guess I'm already dead.
:popcorn:

---

### Post by Tristam Green on 2009-09-01
> **Dragonbite said:**
> *looks at avatar* I guess I'm already dead.
:popcorn:

That, or you lay down the 'buntu (and play that funky music) til you die!

/lightenthestuffymood

---

### Post by koleoptero on 2009-09-01
> **gn2 said:**
> I don't.
Arch simply has a following of vociferous evangelists who like to tell everyone how snappily dressed the emperor is these days.

I really laughed with this. I'm so happy these ubuntu vs arch topics exist to keep us entertained.

---

### Post by Perfect Storm on 2009-09-01
> **Namtabmai said:**
> GAHHH SKA!!!

You really ought to have put a warning around that.

;)

Enjoy :popcorn:

---

### Post by Bachstelze on 2009-09-01
> **aysiu said:**
> It's new starting with Intrepid.

From [the Jaunty release notes](http://www.ubuntu.com/getubuntu/releasenotes/904): > **Recommended packages installed by default**
In accordance with the Debian Policy Manual (which says "The 'Recommends' field should list packages that would be found together with this one in all but unusual installations"),

Okay, then in that particular case, the package maintainer is doing it wrong. I can't see how it is "unusual" to have lxde installed with kdm, xdm, or even no display manager at all. gsm should be listed as "Suggested", maybe I should file a bug against it.

---

### Post by Simian Man on 2009-09-01
> **HymnToLife said:**
> Okay, then in that particular case, the package maintainer is doing it wrong. I can't see how it is "unusual" to have lxde installed with kdm, xdm, or even no display manager at all. gsm should be listed as "Suggested", maybe I should file a bug against it.

There's also slim which I use as a display manager for light setups.

---

### Post by aaaantoine on 2009-09-01
To tell the truth, if my system ever required a reinstall, I'd probably switch back to Ubuntu.  There are a lot of things I had to configure in Arch that I really don't feel like configuring again.

The main reasons I stick to Arch otherwise, in order of compulsion:

A. Currently using / preferring KDE, and Arch is a great KDE distro.
B. Rolling release means going back to a non dev version of Ubuntu at any point would be a "downgrade".
C. It's already installed.
D. AUR.

---

### Post by SuperSonic4 on 2009-09-01
Arch Linux is not a virus, let's get that straight.

I like arch, and will suggest it to anyone either willing to accept a steeper learning curve than most distros or someone wanting to try another distro. I use it to run IceWM on the laptop and KDE on the desktop. I know ubuntu minimal + packages could do that but I like pacman and other arch features.

I will not suggest arch to anyone who wants a system up and running with minimal effort- for that it's ubuntu or mint.

Also I have to agree with Point A from above, I frequent the ubuntu forums because I like to and I still know some kubuntu specific stuff



**edit**: turns out pacman was holding some KDEmod stuff it would appear I'm now using KDE 4.3.1 :D

---

### Post by earthpigg on 2009-09-01
> **HymnToLife said:**
> Okay, then in that particular case, the package maintainer is doing it wrong. I can't see how it is "unusual" to have lxde installed with kdm, xdm, or even no display manager at all. gsm should be listed as "Suggested", maybe I should file a bug against it.

if if-then arguments worked with apt-get recommended lists, here is one possible way to do it:

you tell apt-get you want to install lxde.

if any display manager is already installed and in use, then do not install one.
if none are, then recommend that slim be installed.


(slim seems like the most natural fit to lxde that i am aware of. gnome would be gdm, et cetera.)




or am i following my own well established pattern and re-inventing the wheel like i always do?

---

### Post by Bachstelze on 2009-09-01
> **earthpigg said:**
> if if-then arguments worked with apt-get recommended lists, here is one possible way to do it:

you tell apt-get you want to install lxde.

if any display manager is already installed and in use, then do not install one.
if none are, then recommend that slim be installed.


(slim seems like the most natural fit to lxde that i am aware of. gnome would be gdm, et cetera.)




or am i following my own well established pattern and re-inventing the wheel like i always do?

It is possible, one could just make lxde recommend slim OR kdm OR gdm OR xdm, etc. Since slim would be the first choice, if no other DM is installed, it would install it (if you didn't disable the automatic installation of recommended packages).

---

### Post by Namtabmai on 2009-09-01
There already is something like this isn't there? The x-display-manager meta package.

That's what lxde should depend/recommend surely?

---

### Post by Bachstelze on 2009-09-01
> **Namtabmai said:**
> There already is something like this isn't there? The x-display-manager meta package.

That's what lxde should depend/recommend surely?

[http://packages.ubuntu.com/search?keywords=x-display-manager&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=x-display-manager&searchon=names&suite=all&section=all)

But I think you meant a virtual package that any display manager would provide. It wouldn't work, because if no display manager was installed, Apt would just throw an error saying: "x-display-manager is a virtual package provided by: slim, kdm, gdm, xdm... You must install one of those".

---

### Post by SuperSonic4 on 2009-09-01
What does lxde and apt have to do with arch?

---

### Post by Bachstelze on 2009-09-01
> **SuperSonic4 said:**
> What does lxde and apt have to do with arch?

Had you followed the conversation, you would know what led us to talk about Apt and lxde.

---

### Post by SuperSonic4 on 2009-09-01
> **HymnToLife said:**
> Had you followed the conversation, you would know what led us to talk about Apt and lxde.

Still has little to do with this topic at this point in the topic though

---

### Post by Bachstelze on 2009-09-01
> **SuperSonic4 said:**
> Still has little to do with this topic at this point in the topic though

Yeah, so what?

---

### Post by &#32 Greg on 2009-09-01
> **SuperSonic4 said:**
> What does lxde and apt have to do with arch?

Simple. The thread started as an 'I switched to Arch' discussion, which of course quickly disintegrated into pages of Ubuntu vs. Arch vs. Everything Else, which after it died down changed into a LOL Y SO SRS discussion. Now lxde and apt flaired up in the remnents of the Ubuntu vs. Arch- it has nothing to do with Arch anymore, but the pacman vs. apt dependency debate led to discussion over when Ubuntu pulled in recommended dependencies and how the lxde package should be handled. And now we've come to the point where we're discussing what happened to the thread.

---

### Post by Namtabmai on 2009-09-01
> **HymnToLife said:**
> [http://packages.ubuntu.com/search?keywords=x-display-manager&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=x-display-manager&searchon=names&suite=all&section=all)

But I think you meant a virtual package that any display manager would provide. It wouldn't work, because if no display manager was installed, Apt would just throw an error saying: "x-display-manager is a virtual package provided by: slim, kdm, gdm, xdm... You must install one of those".

Ah you're right, I wrongly assumed the a virtual package if required would pull in a default or something.

But as someone mentioned before ( I think ) lxde or any WM/DE for that matter doesn't really require a display manager to run. So this goes back to the new apt setting of installing recommended apps by default. Particularly in a case like this where you don't get any reduced functionality in the package you are installing by not having gdm.
I understand this setting in relation to something like a music player so that it pulls in various codecs as well, as that directly adds to the functionality of the application you are installing.

I suppose this all comes down to Ubuntu's target audience and aims, for the majority of users this is perhaps the best method and for others like me it's just matter of changing the default back.

---

### Post by SuperSonic4 on 2009-09-01
> **HymnToLife said:**
> Yeah, so what?

I always thought it was the responsibility of the users not to digress and should that happen then the staff close it

---

### Post by Bachstelze on 2009-09-01
> **Namtabmai said:**
> 
But as someone mentioned before ( I think ) lxde or any WM/DE for that matter doesn't really require a display manager to run.

That was me. ;)

> **Namtabmai said:**
> So this goes back to the new apt setting of installing recommended apps by default. Particularly in a case like this where you don't get any reduced functionality in the package you are installing by not having gdm.

Installing recommended apps by default actually makes sense, since the Debian guidelines say that "The 'Recommends' field should list packages that would be found together with this one in all but unusual installations". The problem here is that it is clearly not the case for lxde and gdm, so it should be marked as suggested, not recommended (and by the way, it's the Debian maintainer who marked it recommended, not Ubuntu).

---

### Post by JillSwift on 2009-09-01
It's not a religion. It's an OS. The strengths and weaknesses of OSs can be discussed without getting angry or making it personal.

**Can** be.

Your choice.

If you feel attacked, remember it takes at least *two* to start a fight.

---

### Post by Bachstelze on 2009-09-01
> **SuperSonic4 said:**
> I always thought it was the responsibility of the users not to digress and should that happen then the staff close it

What makes you think so? This is a discussion thread, not a support one, and as with all discussions, digressions are unavoidable.

---

### Post by dragos240 on 2009-09-01
Well. It's fun. I use it for my server, and use it for GNOME. It works great. About a week of uptime ^.^

---

### Post by earthpigg on 2009-09-01
> **dragos240 said:**
> Well. It's fun. I use it for my server, and use it for GNOME. It works great. About a week of uptime ^.^

i think you will agree with me here, dragos, but ill state it for others:

long uptime with continual desktop usage, for those interested in that for whatever reason, is perfectly obtainable in both ubuntu and arch.

> What makes you think so? This is a discussion thread, not a support one, and as with all discussions, digressions are unavoidable.

+1. i agree that support discussions should be kept at least somewhat on track, but this is the Community *Cafe*... where we sit around and just roll with conversations (nearly) wherever they happen to lead us.

---

### Post by dragos240 on 2009-09-01
> **earthpigg said:**
> i think you will agree with me here, dragos, but ill state it for others:

long uptime with continual desktop usage, for those interested in that for whatever reason, is perfectly obtainable in both ubuntu and arch.



+1. i agree that support discussions should be kept at least somewhat on track, but this is the Community *Cafe*... where we sit around and just roll with conversations (nearly) wherever they happen to lead us.

Yep. You can do it in Ubuntu also. It's just more custom.

---

### Post by swoll1980 on 2009-09-01
> **earthpigg said:**
> i think you will agree with me here, dragos, but ill state it for others:

long uptime with continual desktop usage, for those interested in that for whatever reason, is perfectly obtainable in both Ubuntu and arch.



I wouldn't use either for a server though. That's what free BSD is for.

---

### Post by Bachstelze on 2009-09-01
> **earthpigg said:**
> i think you will agree with me here, dragos, but ill state it for others:

long uptime with continual desktop usage, for those interested in that for whatever reason, is perfectly obtainable in both ubuntu and arch.

And even Windows... It's only once you hit the one year mark that uptime starts to become significant.

---

### Post by dragos240 on 2009-09-01
> **swoll1980 said:**
> I wouldn't use either for a server though. That's what free BSD is for.

Well everyone has their preferences.

---

### Post by dragos240 on 2009-09-01
If I could get 1 year of uptime. I would be very very happy :)

---

### Post by RiceMonster on 2009-09-01
> **swoll1980 said:**
> I wouldn't use either for a server though. That's what free BSD is for.

Well, on the Linux side of things there is also Debian, and CentOS.

> **HymnToLife said:**
> And even Windows... It's only once you hit the one year mark that uptime starts to become significant.

Yep. I got a month of uptime on a laptop. Big deal.

---

### Post by earthpigg on 2009-09-01
> **swoll1980 said:**
> I wouldn't use either for a server though. That's what free BSD is for.

to each his own.

I will point out that Ubuntu seems good enough for Wikipedia, though, in addition to [insert the list we have all seen before of ubuntu server deployments].

---

### Post by chris4585 on 2009-09-01
:popcorn:

---

### Post by swoll1980 on 2009-09-01
> **earthpigg said:**
> to each his own.

I will point out that Ubuntu seems good enough for Wikipedia, though, in addition to [insert the list we have all seen before of ubuntu server deployments].

Ubuntu, while not my first choice, makes a fine server. I could never imagine choosing Arch Linux as my server distro though.

---

### Post by Cenotaph on 2009-09-01
Wow, reading this thread really made me feel bad to see what has become of these forums. What's with the fanboyism/hatism? A sign of what Ubuntu itself is becoming?

---

### Post by earthpigg on 2009-09-01
> **Cenotaph said:**
> Wow, reading this thread really made me feel bad to see what has become of these forums. What's with the fanboyism/hatism? A sign of what Ubuntu itself is becoming?

it used to be confined to the "Other OS Talk" subforum, which is now dead.

Ubuntu remains as open and friendly as always, in my opinion.

i do think it is a bit silly for folks annoyed by arch evangelists to come into the thread and act all surprised and shocked that this is an arch thread where people are talking about how great arch is... :confused: the thread title made it pretty clear to me what was being discussed in this thread before i came in. :D

---

### Post by dragos240 on 2009-09-01
> **swoll1980 said:**
> Ubuntu, while not my first choice, makes a fine server. I could never imagine choosing Arch Linux as my server distro though.

Why not?

---

### Post by swoll1980 on 2009-09-01
> **dragos240 said:**
> Why not?

Instability? Lets not add stability to the long list of imaginary benefits that Arch Linux provides.

---

### Post by Namtabmai on 2009-09-01
> **swoll1980 said:**
> Instability? Lets not add stability to the long list of imaginary benefits that Arch Linux provides.

Instability would only come through not managing your server correctly and just accepting the default releases.

I know some people that run a few Arch servers. For them it works really well, just set up two of your own repositories point the production machines at one, staging/development/testing/etc at the other and disable the default Arch repos. Then you simply control what goes into your repository and can test before pushing to you production repo.

---

### Post by gn2 on 2009-09-01
> **earthpigg said:**
> ~ the thread title made it pretty clear to me what was being discussed in this thread before i came in. ~

I have no proof, but I'm fairly certain the thread title has been changed to more accurately reflect the topic under discussion.

---

### Post by Bachstelze on 2009-09-01
> **gn2 said:**
> I have no proof, but I'm fairly certain the thread title has been changed to more accurately reflect the topic under discussion.

Indeed, The original title was "It's a virus I tell ya!"

---

### Post by swoll1980 on 2009-09-01
> **Namtabmai said:**
> Instability would only come through not managing your server correctly and just accepting the default releases.

I know some people that run a few Arch servers. For them it works really well, just set up two of your own repositories point the production machines at one, staging/development/testing/etc at the other and disable the default Arch repos. Then you simply control what goes into your repository and can test before pushing to you production repo.

I'm sure that would would work fine, That didn't come to mind.

---

### Post by gn2 on 2009-09-01
> **HymnToLife said:**
> Indeed, The original title was "It's a virus I tell ya!"

Which stirred my curiosity thinking it could be an interesting security related story.

---

### Post by Dharmachakra on 2009-09-01
I never realized people got so bent out of shape over distribution choices...

:-|

EDIT: Er, let me be more clear... I don't mean only the people in this thread. I mean both the people who think that Arch is the Holy Grail and those who think that it has nothing to offer.

---

### Post by sydbat on 2009-09-01
> **Dharmachakra said:**
> I never realized people got so bent out of shape over distribution choices...

:-|

EDIT: Er, let me be more clear, I don't mean the people in this thread. I mean both the people who think that Arch is the Holy Grail and those who think that it has nothing to offer.You'd be surprised what people get bent about.

---

### Post by tjwoosta on 2009-09-01
I use arch myself, but I must agree there are quite a few overzealous arch users on these forums. I think sometimes people just get a little excited. This is common when experiencing new things. Remember when you tried linux for the first time, Ill bet almost everyone started telling all their friends about it and hyping it up first chance they got.

That said I think its also a bit distasteful for people to get so defensive about it, and start flamewars over which operating system or distro someone likes. That goes for both sides.

---

### Post by CharmyBee on 2009-09-01
I would try Arch, but you know what prevents me from doing so?

Arch's lack of friendliness with fglrx. 

No, i'm not installing an entire operating system only to do 2D stuff. No, i'm not getting a bad nvidia card. No, i'm not going to brag about being content of playing 2D games like Age of Empires 2.

Arch is not for me.

---

### Post by .Maleficus. on 2009-09-01
> **Cenotaph said:**
> Wow, reading this thread really made me feel bad to see what has become of these forums. What's with the fanboyism/hatism? A sign of what Ubuntu itself is becoming?
^^ The only thought I had in my mind while reading the entire 21 pages of this completely ridiculous thread.  Some of the posts in here are so outrageous they're almost sig-worthy.  I am an Arch user.  I started with Ubuntu, but don't use it anymore.  I still recommend Ubuntu to someone wanting to try Linux for the first time.  Will I still recommend they come here for support?  Maybe not after reading this thread...

Linux Users: They're a virus I tell ya!


Edit:  And to add to the discussion about how Arch is recommended/talked about/whatever too much on Ubuntu Forums, I'd just like to point out that so far, 100% of cellphone threads here (that I've seen) have had someone mention how the HTC Hero is the best phone ever made, even when someone clearly doesn't want an Android phone, or has made any mention of Android.

---

### Post by tjwoosta on 2009-09-01
> I would try Arch, but you know what prevents me from doing so?

Arch's lack of friendliness with fglrx.

No, i'm not installing an entire operating system only to do 2D stuff. No, i'm not getting a bad nvidia card. No, i'm not going to brag about being content of playing 2D games like Age of Empires 2.

Arch is not for me.

That sounds like a very valid reason, but I think it should be said that not everyone has such issues, it depends on hardware. I play 3d games and such all them time in arch and get great framerates.

---

### Post by bodyharvester on 2009-09-01
> **HymnToLife said:**
> My Ubuntu does it in 9 seconds. pwn3d

=D>

how on earth does it boot so quickly? mine isnt too far off that time, faster than 15 though.

---

### Post by PurposeOfReason on 2009-09-01
> **wmcbrine said:**
> 
So does my desktop, running Ubuntu 9.04.
I can compare apples to oranges too. Desktop vs laptop. There might be a hardware issue going on here. If I disable internet I go from grub to a login in 5 seconds and x in 9 including typing and loading. Is that to say my OS is better? No, it's probably the SSD doing its thing.

OT:
I need some popcorn right now because this is the most entertaining thread ever. People attacking, people accusing others of attacking, trolls, fanboys, etc. I mean, all we need is Hugh Jackman and we're set for a early 2010 blockbuster.

It's an OS, not a religion. Leave it be.

---

### Post by Gen2ly on 2009-09-01
> **Skripka said:**
> Methinks, as a moderator, you should be above calling posters idiots.  Either openly or implied.  Post reported.  This thread was a testimonial about someone moving from Ubuntu to Arch, why do you need to make it an insult fest?

I'm with you Skripka,  The replies come across as antagonistic to me too.  The original poster doesn't knock any distro, just saying what he liked about trying one.  Prefer the replies be more impartial.  Is this thread going anywhere?

---

### Post by darrenn on 2009-09-01
People, people! The problems with Arch started when some of the fanboys started bashing ubuntu on the forums. Example

> I agree as well. I already switched to Arch some time ago so I could esape the nightmare of the last two releases of Ubuntu: New bugs, instability, bloat, slowness, PulseAudio (Who was the idiot who thought PA was a good idea for a stable production system? That person deserves to be fired.), I switched to Arch... which is like the anti-Ubuntu: Fast, small, stable, solid, rolling release, and gives me more control over what's installed, unlike Ubuntu: Bloated, slow, unstable, too short a discrete release cycle, and you're basically a slave to Canonical's (Increasingly frequently bad.) decisions over what is part of the system, like Pulse Audio or this web app debacle with 9.04.

When things like this started to appear on the forums a lot of good will towards arch users was lost. Unfortunately, a few bad apples spoils a bunch. But a lot of people think it was more than a few.

---

### Post by Skripka on 2009-09-01
> **earthpigg said:**
> +1. i like how 7 pages ago was also 2 hours ago.



Noob.

There's good reason why you can set the number of posts per page to 75 instead of the default 10. :)

---

### Post by CJ Master on 2009-09-01
> **darrenn said:**
> 
When things like this started to appear on the forums a lot of good will towards arch users was lost. Unfortunately, a few bad apples spoils a bunch. But a lot of people think it was more than a few.

Did you seriously save that post on your computer or something? It was made at least 6 months ago. 

Ubuntu users constantly troll about arch, far more then archers do about Ubuntu. But hey, it's the "Ubuntu" forums, so that's ok, right? ;)

---

### Post by darrenn on 2009-09-01
> Did you seriously save that post on your computer or something? It was made at least 6 months ago.

You seriously expect me to believe 6 months later that some arch users still don't have this opinion?

---

### Post by CJ Master on 2009-09-01
> **darrenn said:**
> You seriously expect me to believe 6 months later that some arch users still don't have this option?

I'm assuming you misspelled option for opinion. My opinion is that of which you quoted, of course I don't say it (in which a flameflest would start, which is the last thing I want,) but what's wrong with having a different opinion then you?

---

### Post by Irihapeti on 2009-09-01
This sort of thing happens pretty much everywhere. I have hung out on the Puppy linux forums from time to time, and there are a few there who hate Ubuntu with a passion - to the point where sometimes I've felt nervous about mentioning that I use it as my main distro.

I also remember the IBM XT vs. Mac 512 arguments from my BBS days. What a waste of energy. Mine, I have to say, as well as other people's.

Anyway, let's not write off a whole distro or community because of a few vocal individuals. If I were worried about a new user being put off by threads like these, I'd just tell them to restrict themselves to the technical forums and not bother reading this stuff.

But then, it wouldn't be the first time that I've ended up saying something that shows I don't know what I'm talking about. (Shortage of sleep doesn't help.)

---

### Post by Irihapeti on 2009-09-01
> **CJ Master said:**
> what's wrong with having a different opinion then you?

Nothing. My experience is that often it's not the opinion itself, it's the way in which it's expressed.

I've learned that if other people are taking what I'm saying in the wrong way, I need to express myself differently. No amount of saying that I didn't mean it that way is going to help.

---

### Post by Pogeymanz on 2009-09-01
> **gn2 said:**
> That can be done with many distributions, so it's really no big deal.
Tell me something truly unique that Arch has?

[silence]

BSD style init scripts. Easy as hell daemon configuration. ABS. AUR. The best Wiki ever. Pacman is way better than apt or yum.

---

### Post by PurposeOfReason on 2009-09-01
> **Pogeymanz said:**
> BSD style init scripts.**not unique, I believe BSD has them**:roll:
 Easy as hell daemon configuration. **Not unique nor is it hard on most distros**
ABS. AUR. **okay** **though I believe that gentoo and bsd both have very good systems like the AUR**
 The best Wiki ever.**I believe any real linux user will give that to gentoo before the crash**
 Pacman is way better than apt or yum.**opinion**

.

---

### Post by andamaru on 2009-09-01
I don't want to restart the flames but does anyone have technical reasons why pacman is better than other packages managers. To tell the truth I find most packages managers are at the point where they work well enough to not be cared about.

---

### Post by Viva on 2009-09-01
Is arch linux ready for the desktop?

---

### Post by kk0sse54 on 2009-09-01
> **andamaru said:**
> I don't want to restart the flames but does anyone have technical reasons why pacman is better than other packages managers. To tell the truth I find most packages managers are at the point where they work well enough to not be cared about.

It's mostly personal preference over anything else

---

### Post by Arup on 2009-09-01
> **Viva said:**
> Is arch linux ready for the desktop?

The big answer, NO. I dare Arch fanboyz looming around here to go peddle it to a person delving into Linux from Windows. It would be end of Linux for good.

---

### Post by Sporkman on 2009-09-01
You all know that FreeBSD is way better than Arch Linux, don't you?

---

### Post by RiceMonster on 2009-09-01
> **Arup said:**
> The big answer, NO. I dare Arch fanboyz looming around here to go peddle it to a person delving into Linux from Windows. It would be end of Linux for good.

*facepalm*

---

### Post by Viva on 2009-09-01
> **Viva said:**
> Is arch linux ready for the desktop?

> **Arup said:**
> The big answer, NO. I dare Arch fanboyz looming around here to go peddle it to a person delving into Linux from Windows. It would be end of Linux for good.

To answer the question myself, yes it is ready for the desktops of those who use it. I usually hate the "not ready for desktop" posts. Windows is not ready for my desktop because it doesn't fit all my needs without tweaking.

---

### Post by samjh on 2009-09-01
> **gn2 said:**
> Tell me something truly unique that Arch has?

Lack of Anti-Arch and Foaming-at-the-mouth-pro-Ubuntu fanboys/girls. ;)

On a more serious note, this thread is a good example of why Linux communities just can't seem to unite.

I mean, I use Arch because it is a stable, rolling-release distro (not need to reinstall every 6 to 12 months), with minimal unknown software and configuration settings lurking beneath the hood.  It suits me.

But... oh no, that's not good enough.  Some douchebags have to put on a long face and cry, "but whaaaaiiiiiiiiiiiiiiiiiiiiii?!".

Switch it around to "Tell me something truly unique that Ubuntu has?", and the resulting silence is greater than the vacuum of space.

I like Arch.  I like Ubuntu.  I win. :p

(PS: Don't take this post too seriously. It's meant more for satirical humour than reasoned argument.)

---

### Post by RiceMonster on 2009-09-01
> **samjh said:**
> 
I like Arch.  I like Ubuntu.  I win. :p

What!? THAT'S IMPOSSIBLE!

[img]http://morgellonspgpr.files.wordpress.com/2009/05/luke.jpg[/img]

---

### Post by Arup on 2009-09-02
> **RiceMonster said:**
> *facepalm*

:-({|=

---

### Post by RiceMonster on 2009-09-02
> **Arup said:**
> :-({|=

I'll fill you in on a little secret:

"Is arch ready for the desktop?" wasn't a serious question.

---

### Post by HappinessNow on 2009-09-02
This thread has been one long strange trip...I just read the whole thread. Believe it or Not!

I had about a half dozen quotes to reply to but then I felt any reply would be futile.

Awesome Arch-buntu hybrid Thread, great fun and an awesome way to fill/kill time!

I'm off to the local bar to have a few beers with some old viking friends who are visiting in town; be certain around a quarter before midnight we will have our mugs up high singing that old viking song "Arch, **Arch**, [SIZE=3][B]Arch!"

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=127125&stc=1&d=1251864546[/IMG]

I love Arch! I love Ubuntu! I love Macpup Opera! I love Linux!
[/B][/SIZE]

---

### Post by samjh on 2009-09-02
Arch-buntu hybrid.  As interesting as that might be, it will never happen as long as some people continue to hold onto their belief that Arch is Ubuntu's **arch**-enemy.

I'm punny, eh?

* gulp *

---

### Post by Arup on 2009-09-02
> **RiceMonster said:**
> I'll fill you in on a little secret:

"Is arch ready for the desktop?" wasn't a serious question.

And I will fill you in on one..........Arch is not a serious question to start with anyways.

---

### Post by kk0sse54 on 2009-09-02
> **Arup said:**
> And I will fill you in on one..........Arch is not a serious question to start with anyways.

And with that we come right back to where we started :roll:

---

### Post by RiceMonster on 2009-09-02
> **Arup said:**
> And I will fill you in on one..........Arch is not a serious question to start with anyways.

Good to know. I'll keep that in mind next time I ask the following question:

Arch?

---

### Post by JillSwift on 2009-09-02
> **C!oud said:**
> And with that we come right back to where we started :roll:
It's the great circle of no-life, Simba!

---

### Post by CJ Master on 2009-09-02
> **RiceMonster said:**
> Good to know. I'll keep that in mind next time I ask the following question:

Arch?

Exactly what I was thinking. How the heck is "Arch" a question?

---

### Post by earthpigg on 2009-09-02
> **samjh said:**
> Arch-buntu hybrid.  As interesting as that might be, it will never happen as long as some people continue to hold onto their belief that Arch is Ubuntu's **arch**-enemy.

I'm punny, eh?

* gulp *

lol, cute.

i know the hybrid suggestion was in jest, but

i'd be down to add an "Ubuntu Rolling Repository" and "Ubuntu User's Repository" to my sources.list and give it a shot on machines other than my primary desktop. URR and UUR. UUR could allow us to dispense with this whole annoying PPA thing we have going on here in Ubuntuworld.

could be interesting, to say the least.

how much - if at all - would the package managers (synaptic, apt-get, etc) need to be modified to make this realistic?

that is about as far as i would go towards trying any 'hybrid' out... debian is debian and arch is arch.

---

### Post by Arup on 2009-09-02
> **RiceMonster said:**
> Good to know. I'll keep that in mind next time I ask the following question:

Arch?

May I suggest a very nice cozy place for Arch questions........ [http://bbs.archlinux.org/](http://bbs.archlinux.org/)

---

### Post by kk0sse54 on 2009-09-02
> **Sporkman said:**
> You all know that FreeBSD is way better than Arch Linux, don't you?

Like totally duh! That's what I've been trying to say this entire time :lolflag:

---

### Post by earthpigg on 2009-09-02
> **C!oud said:**
> Like totally duh! That's what I've been trying to say this entire time :lolflag:

want to see a great youtube video on the subject?

o, wait....

*fans the flames*

---

### Post by gn2 on 2009-09-02
> **samjh said:**
> 
Switch it around to "Tell me something truly unique that Ubuntu has?"

A very nice looking brown default theme. ;)

For avoidance of doubt, I have no antipathy towards Arch the distribution.

---

### Post by keiichidono on 2009-09-02
I would like to state the fact that i have entered this thread preceding an Ubuntu Forums administrator closing this thread for review.

---

### Post by koleoptero on 2009-09-02
> **PurposeOfReason said:**
> I need some popcorn right now because this is the most entertaining thread ever. People attacking, people accusing others of attacking, trolls, fanboys, etc. I mean, all we need is Hugh Jackman and we're set for a early 2010 blockbuster. 

+1 :popcorn:

> **CJ Master said:**
> Did you seriously save that post on your computer or something? It was made at least 6 months ago. 

Ubuntu users constantly troll about arch, far more then archers do about Ubuntu. But hey, it's the "Ubuntu" forums, so that's ok, right? ;)

Damn right. No Arch trolling allowed lest you get shot in the leg.

> **samjh said:**
>  On a more serious note, this thread is a good example of why **any type of human** communities just can't seem to unite

Fixed that for you.

And while you're all shooting each other over Arch and Ubuntu, I'd like to note how better than both is windows 7. I can name a score of things that you can't do in arch or ubuntu while you can in windows 7.

---

### Post by bodyharvester on 2009-09-02
> **koleoptero said:**
> I can name a score of things that you can't do in arch or ubuntu while you can in windows 7.

there is a database of all viruses and trojans and spyware and malware at [www.threatexpert.com]("http://www.threatexpert.com") though i dont know how many actually can infect Win7 successfully. lol

On Topic: i would use arch if i didnt have to build it, i know that makes me sound lazy but the only things ive added to Ubuntu are Vuze, DrPython and aMSN.

---

### Post by koleoptero on 2009-09-02
> **bodyharvester said:**
> there is a database of all viruses and trojans and spyware and malware at [www.threatexpert.com](www.threatexpert.com) though i dont know how many actually can infect Win& successfully

That's a big plus too. Imagine all the support people and antivirus companies that would lose their jobs if less people used windows. It might lead to even more unemployment.

---

### Post by bodyharvester on 2009-09-02
> **koleoptero said:**
> That's a big plus too. Imagine all the support people and antivirus companies that would lose their jobs if less people used windows. It might lead to even more unemployment.

true :| when i think about all the work those security issues give to people across the world and all the creators of the software, there must be a lot of money in that part of the economy :o

---

### Post by howefield on 2009-09-02
> **Metallion said:**
> I think it's safe to say that Arch is easily the second most loved distro on this forum after the obvious Ubuntu.

Wow !! Don't know about "loved" but it must have something, 250 plus replies in under 24 hours... 

Your post has prompted me to install this weekend, although I don't hold out much hope for it. Every distro I try always seems to have something (missing) that makes me drift back to Ubuntu.

---

### Post by thisllub on 2009-09-02
There is absolutely nothing interesting about Arch.
I will go as far as to call it the most boring distro I have used in 10 years of Linux.
You install it.
It works.
You update it.
It works.

No new releases.
No hype.
It takes all the excitement out of upgrades.
The best package manager in the most up to date distro.
20 months now.
More than double second place. (SUSE 10.1)

---

### Post by sideaway on 2009-09-02
That's what I would call Mint... Not Arch... Install it, it works... I'm not sure what you used, but that wasn't my experience with Arch, took me an entire afternoon and some of the next day to get mine setup the way I wanted it.

---

### Post by sisco311 on 2009-09-02
> **samjh said:**
> **Arch-buntu hybrid**.  As interesting as that might be, it will never happen as long as some people continue to hold onto their belief that Arch is Ubuntu's **arch**-enemy.

I'm punny, eh?

* gulp *

[img]http://www.upload3r.com/serve/020909/1251889856.png[/img]

---

### Post by LookTJ on 2009-09-02
Bah! I hate "hate distros" threads.

On another note,  The only time pacman ever failed me was when I didn't upgrade for 4 months...causing a kernel panic.

---

### Post by nothingspecial on 2009-09-02
After a complete battering and bruising in a similar thread a while back I promised myself I wouldn`t enter this debate again, so I`m not going to.

---

### Post by nothingspecial on 2009-09-02
Oh b*****ks to it.

In 26 pages I didn`t see anyone "bashing" Arch itself, just bemoaning the fact that it gets hyped far too much on these forums. In my opinion (which isn`t that humble) this is true.

It`s also true that if you want a great big chufty badge that says "I`m an `advanced` linux user" because you had to edit a config file when you installed, then Arch is definitely the distro for you.

The thing I found was that after alot of p*****g about  I had something almost identical to my ubuntu install.

In the interests of balance I am posting this from my Arch install (I think).

---

### Post by JillSwift on 2009-09-02
> **sisco311 said:**
> [http://www.upload3r.com/serve/020909/1251889856.png](http://www.upload3r.com/serve/020909/1251889856.png)

:eek: :shock:
Frankendistro! :D

---

### Post by snowpine on 2009-09-02
If Arch is so great, why are they switching to the Ubuntu kernel?

I just tried installing Arch, but I couldn't see the desktop cube, just some letters on a black background. EPIC FAIL!!!! I'm reinstalling Windows 7 right now so I can install Ubuntu through Wubi.

---

### Post by itreius on 2009-09-02
> **snowpine said:**
> If Arch is so great, why are they switching to the Ubuntu kernel?

/facepalm

---

### Post by MONODA on 2009-09-02
> Most people try Arch because they think they're being clever. All this stuff about Arch being difficult to install is just rubbish, it's time consuming, not difficult. And after all that setting up you've got a system that's no better than Ubuntu that installs in less than half an hour. I actually found Ubuntu 9.04 to boot and run quicker than Arch + Xfce4.

One other thing, about the Arch forums...it's a boring place....lots of people slapping themselves on the back and thinking that they're clever because they're using a system that needs constant repairing thanks to 'pacman -Syu'.

Arch is for people with more time than sense.

Dude... why are you so angry? Chill... Generalizing like that about any group up people is just insulting and immature.

---

### Post by JillSwift on 2009-09-02
> **MONODA said:**
> is just insulting and immature.And this is just an appeal to emotion, and the problem with appeals to emotion is you don't always get the emotion you were hoping for.

The best thing to do to anyone who has gotten themselves all worked up about anything (on a forum or face-to-face) is to speak quietly and calmly, being as reasonable as you can manage. They'll calm down, you stay calm. Intelligent conversation can resume.

---

### Post by Pogeymanz on 2009-09-02
> **andamaru said:**
> I don't want to restart the flames but does anyone have technical reasons why pacman is better than other packages managers. To tell the truth I find most packages managers are at the point where they work well enough to not be cared about.

I couldn't give you a super-technical reason, but here are some things that I've noticed and YMMV.

Pacman really does seem faster on my machine.
I like pacman's usability better. Once you get used to certain flags, it makes a lot of sense. e.g. 
pacman -Syu == apt-get update && apt-get upgrade (is that how you do it?)
pacman -Sy == apt-get update && apt-get install
pacman -S == apt-get install

etc.

You learn to use an algorithm for pacman commands, whereas apt commands are words you have to remember. "Dang, was it 'apt-get remove' or 'apt-get uninstall' or 'apt-get-this-out-of-my-system'?"

And, this may not be apt's fault, but when I use Ubuntu I feel like I should be able to uninstall something without uninstalling the whole dang system, but apt tells me otherwise.

---

### Post by CJ Master on 2009-09-02
> **snowpine said:**
> If Arch is so great, why are they switching to the Ubuntu kernel?

I just tried installing Arch, but I couldn't see the desktop cube, just some letters on a black background. EPIC FAIL!!!! I'm reinstalling Windows 7 right now so I can install Ubuntu through Wubi.

I'm going to assume that was a joke post. In that case, that was the funniest thing I read all day, thank you. :D

---

### Post by Dragonbite on 2009-09-02
> **Pogeymanz said:**
> pacman -Syu == apt-get update && apt-get upgrade (**is that how you do it?**)
pacman -Sy == apt-get update && apt-get install
pacman -S == apt-get install


Naw.. I use Synaptic and Update Manager and it works fine for me. 

Even easy to get my wife to update the system which makes it easier for ME since she's on it during the day while I'm at work.

The idea of getting her to type in those commands sends chills down my back (or is that the AC that just kicked on? ;) )

---

### Post by &#32 Greg on 2009-09-02
> **CJ Master said:**
> I'm going to assume that was a joke post. In that case, that was the funniest thing I read all day, thank you. :D

Even if it wasn't, it still should be up there :)

---

### Post by tjwoosta on 2009-09-02
> **Dragonbite said:**
> Naw.. I use Synaptic and Update Manager and it works fine for me. 

Even easy to get my wife to update the system which makes it easier for ME since she's on it during the day while I'm at work.

The idea of getting her to type in those commands sends chills down my back (or is that the AC that just kicked on? ;) )

Of course one could always use shaman. But it does sound to me like ubuntu would be better suited for your needs.

---

### Post by Dragonbite on 2009-09-02
> **tjwoosta said:**
> Of course one could always use shaman. But it does sound to me like ubuntu would be better suited for your needs.

I've done my Gentoo stint.. got it out of my system and now I'm trying to just USE the computer, not constantly tweak it.

---

### Post by tjwoosta on 2009-09-02
> I've done my Gentoo stint.. got it out of my system and now I'm trying to just USE the computer, not constantly tweak it.

I hear you there. I had gentoo installed for about a week and a half. Just long enough to learn the ropes and get everything configured the way I like it, then I said screw this, its just too much effort.

---

### Post by Hallvor on 2009-09-02
> **Pogeymanz said:**
> 
And, this may not be apt's fault, but when I use Ubuntu I feel like I should be able to uninstall something without uninstalling the whole dang system, but apt tells me otherwise.

It is possible. You just don`t know how to do it. :)

What you are describing is the effect of having Gnome installed with a metapackage, and not a flaw in apt. If you installed your system without using metapackages, there would not be a problem at all.

However, it is still possible to delete something without uninstalling the "whole dang system". You do this by:

apt-get remove <package>
aptitude keep-all 

You can also completely turn off autoremove or just turn it off for certain packages.

---

### Post by szadek_ on 2009-09-02
Hello people , i have a own opinion about this kind of subject ... and i would like to share it with you .

For instance , i , was really curious about arch , i installed it , and , it is really fast , no doubt about it ... i've been using ubuntu for the last 4 or 5 years , i cant really precise it , so , i know the difference , and it is like that, arch really is faster .

But , in my own experience , arch didnt went well , i had lots of problems with the kernel , my wireless card is not supported , and i would have to patch it so it can work , or , work a bit .

So , i went back to ubuntu , and , it is really bloated and all , but , i dont mind editing files , of course , and i like to do that , but , i dont want to patch things so they can work ... a bit .This is my own experience , so , i have to sacrifice the "fast" to the "it works" .

But , when i was experimenting arch , i could remember , like ubuntu , its linux after all ,at the end of the day , im using linux , and , i know how to survive in this OS , only because of ubuntu , that was the distro that made me learn linux .And that no other distro can take , ubuntu is the only distro ( at least in my country ) known that can teach us and introduces quite easily to the linux world .I can screw up my system , and in 30 minutes , im back with everything working and ready to conquer =D .... that i can not do with arch.And nobody here can say , that with arch , in 30 minutes they can do it ... and if they say it , i dont believe it =D ( it would be admiting that im dumb loool , and maybe iam ) .


So people , yes , it is stupid , when someone asks "hey , my wireless is not working with *buntu .... " and then "hey you should try arch ... is faster ... " ... is the answer , but , more stupid would be " conversations about arch should be banned from this forums " .

I think , in one side , and on the other ... somenone should grow up ... because , we all are free to use whatever we want ... and talk about the distros we want ... without forcing or givin the impression that what we are not using is inferior ... maybe it could ( i dont believe it ) be true , but , we have to be respectfull ... after all , we all use linux , and most part of us , because ubuntu made us switch , easily ...

Stay cool , and respect others choices , thats what i recommend .

---

### Post by Sporkman on 2009-09-02
But the real question is:

Which is better:

Windows
Linux
BSD
Solaris
MacOSX
AIX

---

### Post by tjwoosta on 2009-09-02
> **Hallvor said:**
> It is possible. You just don`t know how to do it. :)

What you are describing is the effect of having Gnome installed with a metapackage, and not a flaw in apt. If you installed your system without using metapackages, there would not be a problem at all.

However, it is still possible to delete something without uninstalling the "whole dang system". You do this by:

apt-get remove <package>
aptitude keep-all 

You can also completely turn off autoremove or just turn it off for certain packages.

Even better, just use --no-install-recommends  when installing, that way you dont have to go through and remove all the unnecessary packages.

---

### Post by Viva on 2009-09-02
This thread is pathetic. I'd much rather put the effort of bashing arch into bashing windows, microsoft and apple:)

---

### Post by Bachstelze on 2009-09-02
> **Sporkman said:**
> But the real question is:

Which is better:

Windows
Linux
BSD
Solaris
MacOSX
AIX

It's IRIX, of course. BeOS was good in its day too.

---

### Post by RiceMonster on 2009-09-02
> **Sporkman said:**
> But the real question is:

Which is better:

Windows
Linux
BSD
Solaris
MacOSX
AIX

z/OS

---

### Post by koenn on 2009-09-02
> **Pogeymanz said:**
> 

You learn to use an algorithm for pacman commands, whereas apt commands are words you have to remember. "Dang, was it 'apt-get remove' or 'apt-get uninstall' or 'apt-get-this-out-of-my-system'?"

That's the first time I see someone claim that actual words are harder to remember than random combinations of characters.

---

### Post by HappinessNow on 2009-09-02
> **Sporkman said:**
> But the real question is:

Which is better:

Windows
Linux
BSD
Solaris
MacOSX
AIX

> **HymnToLife said:**
> It's IRIX, of course. BeOS was good in its day too.

> **RiceMonster said:**
> z/OS

Haiku

---

### Post by tjwoosta on 2009-09-02
> You learn to use an algorithm for pacman commands, whereas apt commands are words you have to remember. "Dang, was it 'apt-get remove' or 'apt-get uninstall' or 'apt-get-this-out-of-my-system'?"

> That's the first time I see someone claim that actual words are harder to remember than random combinations of characters.

Not that any of this makes a difference anyway.

Just add aliases to your .bashrc and you can update with whatever word you want. 

For instance

here is a small part of my .bashrc

```

alias update='yaourt -Syu --aur'

alias search='yaourt -Ss'

alias install='yaourt -S'

alias remove='yaourt -Rs'

```

with this I can update with a single command "update", I can search with "search" and I can install or remove with "install" or "remove"

example 

```
install firefox
```


The same can be done with any distro, and any commands.

---

### Post by koenn on 2009-09-02
> **samjh said:**
> 
Switch it around to "Tell me something truly unique that Ubuntu has?",...

a huge user base. Ubuntu was the first successful attempt to take desktop linux to the masses. That's an accomplishment in itself, and an indication that they most have done something right (that all others missed or did wrong)

---

### Post by tjwoosta on 2009-09-02
Actually arch has a fairly huge user base as well, I would think that just the amount of arch users on UF should be some indication of that. Not as many as ubuntu, but with the nature of the distro thats expected.

---

### Post by koenn on 2009-09-02
> **tjwoosta said:**
> Actually arch has a fairly huge user base as well, I would think that just the amount of arch users on UF should be some indication of that. 


```
Distribution
138676 registrations entered 141878 values

distribution	Count	Percent

arch linux	802 	0.58% 	
archlinux	700 	0.50% 	

ubuntu	       29173 	21.04% 	

```

[http://counter.li.org/reports/machines.php](http://counter.li.org/reports/machines.php)

---

### Post by tjwoosta on 2009-09-02
ok, so ubuntu has an enormous user base, but if we use that argument then windows must be better then every other OS because about 90% of people use it. They must be doing something better then linux..

---

### Post by Viva on 2009-09-02
> **tjwoosta said:**
> ok, so ubuntu has an enormous user base, but if we use that argument then windows must be better then every other OS because about 90% of people use it. They must be doing something better then linux..

The size of the community doesn't really matter for a proprietary OS, unless we are talking about the business side of it. More users in opensource world => More bug reports and more feedback and more support => Better software. I do find the userbase argument annoying though.

---

### Post by slakkie on 2009-09-02
> **Metallion said:**
>  Lastly I wonder how the rolling release is going to treat me. I was getting quite tired of reinstalling every 6 months to get the new stuff but I'm a tad afraid of possible instabilities in the bleeding edge software too.


So you want to use Arch for rolling releases, but you have never upgraded Ubuntu because you did a reinstall? OMG, that is just epic fail. I'm sorry, but it doesn't make any sense to me. 

Have fun with Arch, but you could do more or less the same with Ubuntu.

---

### Post by &#32 Greg on 2009-09-02
> **Viva said:**
> The size of the community doesn't really matter for a proprietary OS, unless we are talking about the business side of it. More users in opensource world => More bug reports and more feedback and more support => Better software. I do find the userbase argument annoying though.

Of course, then we can start talking about quality users, someone can make a remark along the lines of 'Arch has more knowledgable users than Ubuntu' and the flames would rekindle with a fiery passion.

---

### Post by Viva on 2009-09-02
> **  Greg said:**
> Of course, then we can start talking about quality users, someone can make a remark along the lines of 'Arch has more knowledgable users than Ubuntu' and the flames would rekindle with a fiery passion.

You've said it there, Arch is for more knowledgeable posters. Whether it is better than ubuntu depends on the user.

---

### Post by koenn on 2009-09-02
> **tjwoosta said:**
> ok, so ubuntu has an enormous user base, but if we use that argument then windows must be better then every other OS because about 90% of people use it. They must be doing something better then linux..
nice try.

we're talking about linux distributions here. 
And Windows had that 90% (and more) already before the first line of linux source code was written. It's a constant (sort of) 

The question I answered was 'what is unique to Ubuntu', not 'why is Ubuntu better than Arch' - although you may have read it that way (but then that's your problem, not mine)

---

### Post by tjwoosta on 2009-09-02
> **Viva said:**
> The size of the community doesn't really matter for a proprietary OS, unless we are talking about the business side of it. More users in opensource world => More bug reports and more feedback and more support => Better software. I do find the userbase argument annoying though.

I guess thats true, I didn't think of it that way. 

But I wouldn't say Ubuntu has more users because its better. It has more users because its more friendly, which leads to better support.


> The question I answered was 'what is unique to Ubuntu', not 'why is Ubuntu better than Arch' - although you may have read it that way (but then that's your problem, not mine)

?
> That's an accomplishment in itself, and an indication that they most have done something right (that all others missed or did wrong)

To me that sounds like your saying ubuntu is better, does it not?

---

### Post by koenn on 2009-09-02
> **Viva said:**
>  I do find the userbase argument annoying though.
and *that* is why linux is not ready for the desktop !!!!


but seriously
a/ getting linux to 'the masses' is one of ubuntu's objectives
b/ see my previous post

---

### Post by JillSwift on 2009-09-02
#-o

[attach]127189[/attach]

---

### Post by koenn on 2009-09-02
> **tjwoosta said:**
> 
?

see post 282

> **tjwoosta said:**
> 
To me that sounds like your saying ubuntu is better, does it not?
and to me, *this* sounds as if you actually *want* me to be saying ubuntu is better.

---

### Post by tjwoosta on 2009-09-02
lolwut?

and post 282 is the one i quoted.

---

### Post by koenn on 2009-09-02
> **tjwoosta said:**
> lolwut?
and post 282 is the one i quoted.
ok, then next time you ask a question, try putting some words in front of the question mark.

---

### Post by Dragonbite on 2009-09-02
> **Metallion said:**
> Lastly I wonder how the rolling release is going to treat me. I was getting quite tired of reinstalling every 6 months to get the new stuff but I'm a tad afraid of possible instabilities in the bleeding edge software too.


> **slakkie said:**
> So you want to use Arch for rolling releases, but you have never upgraded Ubuntu because you did a reinstall? OMG, that is just epic fail. I'm sorry, but it doesn't make any sense to me. 

Have fun with Arch, but you could do more or less the same with Ubuntu.

When it comes time for upgrading the system, Ubuntu makes it the easiest to do without reinstalling through the Update Manager!  

I haven't found upgrading so easy for Fedora or openSUSE and while I haven't actually tested it yet I plan on giving it a go when Karmic comes out.  

I know it is not perfect, but it is still ahead of what I've seen so far (and sure beats paying money to upgrade to Vista!)

It may not be as bad as a rolling update system but if my system gets borked because of something I can THEN reinstall from either the older version or right to the latest version.

That's where backups and seperate /home partitions comes in.

---

### Post by santaslittlehelper on 2009-09-02
[IMG]http://img17.imageshack.us/img17/3646/legendarythread.png[/IMG]
:popcorn:

---

### Post by CJ Master on 2009-09-02
> **koenn said:**
> see post 282


and to me, *this* sounds as if you actually *want* me to be saying ubuntu is better.

Keep at it while I get my popcorn. :popcorn:

---

### Post by slakkie on 2009-09-02
> **Dragonbite said:**
> When it comes time for upgrading the system, Ubuntu makes it the easiest to do without reinstalling through the Update Manager!  

I haven't found upgrading so easy for Fedora or openSUSE and while I haven't actually tested it yet I plan on giving it a go when Karmic comes out.  

I know it is not perfect, but it is still ahead of what I've seen so far (and sure beats paying money to upgrade to Vista!)

It may not be as bad as a rolling update system but if my system gets borked because of something I can THEN reinstall from either the older version or right to the latest version.

That's where backups and seperate /home partitions comes in.

I actually upgraded fedora 11 to 12 (devel) last night (to remove it this morning). Went smooth I might add, simple yum line does the trick. I fell asleep during the actual upgrade, but when I woke up I was running rawhide and could start my small test.

And regarding backups.. Look in my post history ;)

---

### Post by dragos240 on 2009-09-02
> **santaslittlehelper said:**
> [IMG]http://img17.imageshack.us/img17/3646/legendarythread.png[/IMG]
:popcorn:

Lol.

---

### Post by koleoptero on 2009-09-02
Now to get back on topic (I think) I don't believe that Arch is a virus, but this thread is.

---

### Post by Sporkman on 2009-09-02
> **koleoptero said:**
> Now to get back on topic (I think) I don't believe that Arch is a virus, but this thread is.

It would have to compell others to spawn similar threads.

---

### Post by CJ Master on 2009-09-02
I can see it now: "'Arch Linux: It's a virus I tell ya!': It's a virus I tell ya!"

---

### Post by MisfitI38 on 2009-09-02
> **gn2 said:**
> Arch has quite a twisted interpretation of the word simplicity....
**Perhaps your perception of the word 'simplicity' is more akin to the definition of 'newbie-friendly'.**
> 
Well how about if I posted in the Arch forums about how fantastic Ubuntu is ...?
**Go ahead, [URL="http://bbs.archlinux.org/viewtopic.php?id=44501&p=1"]there is already a thread about it, in fact.**
[/URL] 

**Further, slandering other distros [is strictly forbidden on the Arch forums.]("http://wiki.archlinux.org/index.php/Forum_Etiquette#Respect_Other_Distributions_and_Operating_Systems") Though, it doesn't seem to be an enforced rule over here.**

---

### Post by tjwoosta on 2009-09-02
> Now to get back on topic (I think) I don't believe that Arch is a virus, but this thread is.

I think for the most part this thread has remained fairly civil. Whats wrong with a little logical debate now and then. 

If you don't like the thread, don't post in it.

---

### Post by koleoptero on 2009-09-02
> **MisfitI38 said:**
> **Perhaps your perception of the word 'simplicity' is more akin to the definition of 'newbie-friendly'.**

**Go ahead, [URL="http://bbs.archlinux.org/viewtopic.php?id=44501&p=1"]there is already a thread about it, in fact.**
[/URL] 

**Further, slandering other distros [is strictly forbidden on the Arch forums.]("http://wiki.archlinux.org/index.php/Forum_Etiquette#Respect_Other_Distributions_and_Operating_Systems") Though, it doesn't seem to be an enforced rule over here.**

Who's slandering?

---

### Post by ChrT on 2009-09-02
Arch is a pretty awesome distro once you set it up right, I use it on my netbooks (ubuntu always seems to have trouble with some piece of hardware on thos), but on the desktop, absolute perfect optimisation isn't that much of an issue for me, so I prefer ubuntu.

---

### Post by MisfitI38 on 2009-09-02
> **koleoptero said:**
> Who's slandering?

Heh. I lol'd.

---

### Post by kelvin spratt on 2009-09-02
> **MisfitI38 said:**
> **Perhaps your perception of the word 'simplicity' is more akin to the definition of 'newbie-friendly'.**

**Go ahead, [there is already a thread about it, in fact.]("http://bbs.archlinux.org/viewtopic.php?id=44501&p=1")**[URL="http://bbs.archlinux.org/viewtopic.php?id=44501&p=1"]
[/URL] 

**Further, slandering other distros [is strictly forbidden on the Arch forums.]("http://wiki.archlinux.org/index.php/Forum_Etiquette#Respect_Other_Distributions_and_Operating_Systems") Though, it doesn't seem to be an enforced rule over here.**

I totally agree and threads that end up like this are nothing but childish and the mods are setting a very bad example with their replies. Misfit you are always just in your replies on the Arch forums as I am on the forum I moderate, shame on you Ununtu mods for allowing this to carry on.

---

### Post by HappinessNow on 2009-09-02
> **MisfitI38 said:**
> **Perhaps your perception of the word 'simplicity' is more akin to the definition of 'newbie-friendly'.**

**Go ahead, [there is already a thread about it, in fact.]("http://bbs.archlinux.org/viewtopic.php?id=44501&p=1")**[URL="http://bbs.archlinux.org/viewtopic.php?id=44501&p=1"]
[/URL] 

**Further, slandering other distros [is strictly forbidden on the Arch forums.]("http://wiki.archlinux.org/index.php/Forum_Etiquette#Respect_Other_Distributions_and_Operating_Systems") Though, it doesn't seem to be an enforced rule over here.**

> **koleoptero said:**
> Who's slandering?

> **MisfitI38 said:**
> Heh. I lol'd.

> **kelvin spratt said:**
> I totally agree and threads that end up like this are nothing but childish and the mods are setting a very bad example with their replies. Misfit you are always just in your replies on the Arch forums as I am on the forum I moderate, shame on you Ununtu mods for allowing this to carry on.

Shame on who?

---

### Post by kelvin spratt on 2009-09-02
Misfit 
By the way which Jersey are you from us, or channel isles

---

### Post by akiratheoni on 2009-09-02
32 pages in a day? Really?

On topic though, I used Arch virtualized on Ubuntu just to test it out, and I really liked it. Perhaps once I get a wired connection I'll try it, it just looks really interesting.

---

### Post by dmizer on 2009-09-02
Closed for review

---

