---
title: "I'm getting a lil tired of waiting so long for updates ._."
date: 2009-09-26
forum: The Cafe
---

### Post by hoppipolla on 2009-09-26
Like, the new emesene is out now and I want it but... it's so much effort to start installing repositories and stuff.

Is there anyway to just get these updates sooner? Is this stuff in  "backports" or "unsupported" or something?  Or am I using the wrong distributions for up-to-date stuff?

It's just getting a little old ._.  Sometimes you really want to try the shiny new releases of your favourite programs without waiting ^_^

What's my best solution? ^_^

Hoppi :)

---

### Post by JillSwift on 2009-09-26
> **hoppipolla said:**
> Like, the new emesene is out now and I want it but... it's so much effort to start installing repositories and stuff.

Is there anyway to just get these updates sooner? Is this stuff in  "backports" or "unsupported" or something?  Or am I using the wrong distributions for up-to-date stuff?

It's just getting a little old ._.  Sometimes you really want to try the shiny new releases of your favourite programs without waiting ^_^

What's my best solution? ^_^

Hoppi :)
For me, I learned to compile.

Of course, I've been caught in dependency hell once or twice, so it's not really an "optimum" solution.

Someone will mention Arch in 3, 2, 1... ;)

---

### Post by JDShu on 2009-09-26
...0!

Try out Arch, Gentoo, or Slackware ;)

---

### Post by Xbehave on 2009-09-26
IMO no you are not on the wrong distro if you only want a few components to be cutting edge but ar happy with a stable base try backports (not that upto date) or the [ppa]("http://webupd8.blogspot.com/2009/08/emesene-15-with-webcam-support.html"). If however you want everything to be cutting edge you should look at debain sid/arch linux maybe even gentoo/sabyon

if you only want 1 package to be bleeding edge [SIZE="3"]YOU ARE NOT ON THE WRONG DISTRO: ==> [ppa]("http://webupd8.blogspot.com/2009/08/emesene-15-with-webcam-support.html")s[/SIZE] are great for specifically this kind of thing
edit: not in before arch suggestion!

---

### Post by Tibuda on 2009-09-26
> **hoppipolla said:**
> Is there anyway to just get these updates sooner? Is this stuff in  "backports" or "unsupported" or something?  Or am I using the wrong distributions for up-to-date stuff?
If you are using Ubuntu jaunty, yes you are using the wrong distro.

---

### Post by hoppipolla on 2009-09-26
> **danielrmt said:**
> If you are using Ubuntu jaunty, yes you are using the wrong distro.

heh, yeah it's just... I have been using Linux a long time, and I am all for the progression of the OS, so I love using the one which is the kinda... biggest and more progressive! :)

But thing is... I like having the new versions... is backports maintained enough?

---

### Post by Tibuda on 2009-09-26
> **hoppipolla said:**
> heh, yeah it's just... I have been using Linux a long time, and I am all for the progression of the OS, so I love using the one which is the kinda... biggest and more progressive! :)

But thing is... I like having the new versions... is backports maintained enough?

I think Xbehave got the best suggestion if you only want some applications to be updated. No, don't rely on backports, you better use PPAs. Some app devs have their own PPAs like transmission and pidgin.

---

### Post by Pogeymanz on 2009-09-26
It's already been said, but I'll reiterate.

If you only want certain packages to be new and shiny, Ubuntu with PPA's is good.

If you want everything up-to-date, you can't go wrong with Arch. It is the most updated distro, according to someone, somewhere...

---

### Post by credobyte on 2009-09-26
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware) - not as hard as it might seem to be :rolleyes:

---

### Post by jmszr on 2009-09-26
hoppipolla,

If you're the pragmatic type: [http://www.getdeb.net/search.php?keywords=emesene](http://www.getdeb.net/search.php?keywords=emesene) .
Better to have it in backports or a ppa, but.....

Or you could try this: [http://packages.ubuntu.com/karmic/emesene](http://packages.ubuntu.com/karmic/emesene)

---

### Post by lovinglinux on 2009-09-26
> **hoppipolla said:**
> Like, the new emesene is out now and I want it but... it's so much effort to start installing repositories and stuff.

If you think adding a repository is too much trouble, then ignore all comments about Arch and about compiling yourself. As far as I know, Arch requires a lot of configuration, which will probably be too much trouble for your taste. Compiling yourself is nice, since you can optimize the application for your system, but it's a LOT more time consuming than adding a single PPA line to the software sources.

> **hoppipolla said:**
> What's my best solution?

Another option would be trying to find a deb in the PPA repositories or at getdeb.net and install it manually. But the best solution imo is to add individual PPA's for the applications you want to keep updated. I can't seriously consider this "so much effort".

You might wan to consider a rolling release. Perhaps Debian would be good for you. I never tried tho, so I can't say it is easy to setup or not.

---

### Post by hoppipolla on 2009-09-26
> **lovinglinux said:**
> If you think adding a repository is too much trouble, then ignore all comments about Arch and about compiling yourself. As far as I know, Arch requires a lot of configuration, which will probably be too much trouble for your taste. Compiling yourself is nice, since you can optimize the application for your system, but it's a LOT more time consuming than adding a single PPA line to the software sources.



Another option would be trying to find a deb in the PPA repositories or at getdeb.net and install it manually. But the best solution imo is to add individual PPA's for the applications you want to keep updated. I can't seriously consider this "so much effort".

You might wan to consider a rolling release. Perhaps Debian would be good for you. I never tried tho, so I can't say it is easy to setup or not.

Yeah, I mean don't get me wrong, I have spent AGES with distros before, I have compiled kernels and programs, spend hours and days and weeks configuring machines... you know? I've done all that stuff, but after a while you do just have a craving for it all to do it by itself, I mean that way, if you think about it, the work only has to be done once (at the distribution's end) and not separately by each user.

I KNOW it sounds lazy, but it's really not it's just... ease of use. Adding PPAs for everything can become very time-consuming ._.

I don't want to go back to Windows, but I did appreciate the fact that programs just updated themselves when needed to the latest versions :)

---

### Post by Tibuda on 2009-09-26
> **hoppipolla said:**
> I KNOW it sounds lazy, but it's really not it's just... ease of use. Adding PPAs for everything can become very time-consuming ._.

It is time-consuming only the first time. You don't have to add a PPA for an application everytime a new version is available, but only the first time.

---

### Post by hoppipolla on 2009-09-26
> **danielrmt said:**
> It is time-consuming only the first time. You don't have to add a PPA for an application everytime a new version is available, but only the first time.

I know, there are just a lot of apps lol

I think for now, I'll make do with enabling backports, and maybe playing around with enabling proposed as well! That way it doesn't require a lot of hunting around or a complete OS install, it just gets the system that little bit more up-to-date! :)

---

### Post by ukblacknight on 2009-10-02
> **hoppipolla said:**
> Yeah, I mean don't get me wrong, I have spent AGES with distros before, I have compiled kernels and programs, spend hours and days and weeks configuring machines... you know? I've done all that stuff, but after a while you do just have a craving for it all to do it by itself, I mean that way, if you think about it, the work only has to be done once (at the distribution's end) and not separately by each user.

I KNOW it sounds lazy, but it's really not it's just... ease of use. Adding PPAs for everything can become very time-consuming ._.

I don't want to go back to Windows, but I did appreciate the fact that programs just updated themselves when needed to the latest versions :)

I know how you feel.  Adding PPA's is the only solution, but you find yourself adding loads, and then you need to add them again when a new release of the distro is out.

Take Banshee for example.  In Intrepid, I think it had version 1.0 in its repo's, but the much improved 1.4 was out for a long time.  The only way to update was to add the PPA.  My friend, isn't too technical, was having problems with 1.0 and wanted to upgrade to 1.4 and I had to run him through the process of adding a PPA (adding the Keys is a *very* strange process - although I think this is improved in Karmic).

It would be kind of nice if there was an option in Software Sources that allowed us to have these updates straight away, but I suppose that would require quite a change in the way the system works.

---

### Post by forrestcupp on 2009-10-02
> **JDShu said:**
> ...0!

Try out Arch, Gentoo, or Slackware ;)

Lol!  Do you think a guy who said it's too much of a pain to set up extra repositories really wants to deal with the hassle of setting up Arch, Gentoo, or Slackware?

Props for getting it in by the 3rd post, though.

---

### Post by hoppipolla on 2009-10-02
> **forrestcupp said:**
> Lol!  Do you think a guy who said it's too much of a pain to set up extra repositories really wants to deal with the hassle of setting up Arch, Gentoo, or Slackware?

Props for getting it in by the 3rd post, though.

For the record Mr Jones (hehe, sorry I'm only playing :) ) I have run Slackware for years before. I am well versed in the terminal, I have compiled my own software and kernels, I have... well you get the idea lol

It's not that I CAN'T do this stuff, it's that it's nice when the OS does it for the user :)

---

### Post by SomeGuyDude on 2009-10-02
Aaaaaaaarch.

Every so often I'll find a thread on here about how the new Pidgin/Gimp/Firefox is in the Ubuntu repo's and I've been using it for a month already. ;)

---

### Post by forrestcupp on 2009-10-02
> **hoppipolla said:**
> For the record Mr Jones (hehe, sorry I'm only playing :) ) I have run Slackware for years before. I am well versed in the terminal, I have compiled my own software and kernels, I have... well you get the idea lol

It's not that I CAN'T do this stuff, it's that it's nice when the OS does it for the user :)

You can't have it both ways.  Either wait for the backports, or put up with the pains of manually configuring a rolling release distro. ;)

---

### Post by Perfect Storm on 2009-10-02
Please, don't turn this thread into another arch thread which will evolve into a vs. thread.

Thanks.


regards
A.I. Dude
Ubuntu Forum Staff

---

### Post by hoppipolla on 2009-10-02
> **forrestcupp said:**
> You can't have it both ways.  Either wait for the backports, or put up with the pains of manually configuring a rolling release distro. ;)

I don't know if that's true though, I mean there are ways to get the latest stable releases of programs onto Ubuntu, like you get on commercial operating systems :)

There was recently a very loooong thread we all had about this, the outcome of which being we decided it would be nice to make a repository specifically for this for those that want it, to save having to add lots of individual PPAs.  I dunno, I'm considering getting a few people together and giving it a go :)

---

### Post by Regenweald on 2009-10-02
> **hoppipolla said:**
> I don't know if that's true though, I mean there are ways to get the latest stable releases of programs onto Ubuntu, like you get on commercial operating systems :)

There was recently a very loooong thread we all had about this, the outcome of which being we decided it would be nice to make a repository specifically for this for those that want it, to save having to add lots of individual PPAs.  I dunno, I'm considering getting a few people together and giving it a go :)

Could be a cool venture, but you are going to have to maintain possible new dependencies also, else they will be bleeding ppa's full of broken software.

---

### Post by anonymous_user on 2009-10-02
I face the same dilema as the OP. A rolling release Ubuntu (NOT Debian!) would be so cool.

Being Ubuntu would mean its easier to setup than Arch and the like, and the rolling release means I'll never have to hunt for PPAs ever again.

Alas, its just a pipe dream :(

---

### Post by forrestcupp on 2009-10-02
> **hoppipolla said:**
> 
There was recently a very loooong thread we all had about this, the outcome of which being we decided it would be nice to make a repository specifically for this for those that want it, to save having to add lots of individual PPAs.  I dunno, I'm considering getting a few people together and giving it a go :)

A while back, there used to be a couple of privately run repos that did exactly what you're talking about for several different popular packages.  I don't remember what they were, and I don't know if they're still around.  But you're basically trusting your security to an unknown person.

---

### Post by hoppipolla on 2009-10-02
> **forrestcupp said:**
> A while back, there used to be a couple of privately run repos that did exactly what you're talking about for several different popular packages.  I don't remember what they were, and I don't know if they're still around.  But you're basically trusting your security to an unknown person.

I know, it's true. But then you are doing that with ANYTHING you install, whether it's an individual or a collection of people.

If I did it anyway I wouldn't run it solo, I would get a group of us together and turn it into a proper project :)

---

### Post by Firestem4 on 2009-10-02
> **forrestcupp said:**
> A while back, there used to be a couple of privately run repos that did exactly what you're talking about for several different popular packages.  I don't remember what they were, and I don't know if they're still around.  But you're basically trusting your security to an unknown person.

Us windows users sure are trusting! lol We don't even have trusted repo's =P

---

### Post by wilee-nilee on 2009-10-02
This might help, [http://linux.softpedia.com/get/Communications/Chat/eMeSeNe-15445.shtml](http://linux.softpedia.com/get/Communications/Chat/eMeSeNe-15445.shtml)  Here is the search. [http://www.google.com/#hl=en&q=emesene+linux+download&aq=f&aqi=&aq=0&aqi=g1g-m1&oq=emesene+linux&fp=2cca7b2e99206b9c](http://www.google.com/#hl=en&q=emesene+linux+download&aq=f&aqi=&aq=0&aqi=g1g-m1&oq=emesene+linux&fp=2cca7b2e99206b9c)

---

### Post by SomeGuyDude on 2009-10-02
> **Artificial Intelligence said:**
> Please, don't turn this thread into another arch thread which will evolve into a vs. thread.

Thanks.


regards
A.I. Dude
Ubuntu Forum Staff

Sorry, my point wasn't to proselytize for Arch, but to explain that the only way around this particular dilemma is a rolling release distro. At least without causing some headaches.

---

### Post by hoppipolla on 2009-10-02
> **SomeGuyDude said:**
> Sorry, my point wasn't to proselytize for Arch, but to explain that the only way around this particular dilemma is a rolling release distro. At least without causing some headaches.

It's not the only way ._.

It's a very good way though :)

Unfortunately the problem is, Ubuntu already has the model it has, and Ubuntu is the biggest distro in the world and very user-friendly. That's why I wanted to help improve it by offering the latest software to people, if I can ^_^

---

### Post by kevdog on 2009-10-02
Seriously -- I'd just learn how to compile therefore you are dependent on no one but yourself.  If you get stuck, IRC is a good resource since the developers usually help you out!

---

### Post by juancarlospaco on 2009-10-02
*BTW You can use Arch's Repos on Ubuntu too...*

---

