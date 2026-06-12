---
title: "Very real bugs in Raring"
date: 2012-12-15
forum: Ubuntu Development Version
---

### Post by Chdslv on 2012-12-15
Some are actually programs supposed to help the user, but are real bugs.

The apport problem: the never ending crash reports is a bug, which the Ubuntu devs had not looked at. It is annoying. One can disable Apport problem by disabling it, but then one would never know, if there is a *real* problem later.

The Compiz matter:  The plugins Precise had, neither Quantal or Raring has. There is no Annimation-addon and you can't use the 3D windows add on. In the development fervour, these had been disabled or made not to work, most probably the latter. When you develop and something goes missing, then it is a bug. 

The Nautilus matter: Dual panes had been taken off the new nautilus, but Ubuntu should've given us the better, but old nautilus with the F3 option. There is no special need to abide by the ideas of the Gnome 3 devs, if the main UI is Unity for Ubuntu, so *not allowin*g the "old" Nautilus to be installed is a system-wide bug. One might try to install the SolusOS patched nautilus, but that's not the answer. Nautilus 3.4.2 should be in the repos as a variant. This is a Raring case.

The Grub setup matter: It was pretty easy in Precise. You simply did sudo grub-seup /dev/sda, but in Raring (and in Quantal) this had been taken off. The only solution to set the Grub is by using a ppa, Yannubuntu's Boot-repair. Or else reinstall grub-pc. 

Well, what do you think? Do you see any other bugs? The real annoying ones?

Seriously, Raring is better than Quantal or Precise. All these days, Ubuntu had warned us not to use the coming release on production machines, but that warning is now gone and you can download a daily, which is good as the devs are now very sure of their distro.

In my case, I don't think that Unity is a necessary evil to live with. I don't ever use Unity and search for other UIs. I've found one, an old one, which is practically discarded, because of its  universality, one that has no binding with a given WM or DE. (Devs appear to be *unhappy* with universal applications, so the go looking for others, such as Gnome-shell, Unity, Cinnamon...and taking away the right-click...)

When an ability is taken away, the whole thing becomes a bug.

---

### Post by QIII on 2012-12-15
The "Compiz matter" is not a bug.  What you mention is a feature that has been shelved because three guys can't keep it all up.  That's not "development furvour".  It's triage.

If you want the "bug" fixed, get in touch with Sam and offer to maintain the code.  He has asked for volunteers to do just that.

A lot of similar things have disappeared from KWin for ATI users because ATI hasn't bothered to move past OpenGL 1.4 and Martin and crew just can't maintain two code bases.  They had to cut ATI loose.

It is not a "bug" when features you like disappear.  That happens because of conscious decisions based on considerations you may not be aware of.

Apport, yes.  The other two are not bugs.

---

### Post by Chdslv on 2012-12-15
> **QIII said:**
> The "Compiz matter" is not a bug.  What you mention is a feature that has been shelved because three guys can't keep it all up.  That's not "development furvour".  It's triage.

If you want the "bug" fixed, get in touch with Sam and offer to maintain the code.

If it works in my Precise installation, and won't in the Raring one, then it is a bug.:D
The base became "developed" without some abilities.

When, you buy a new mobile, you simply change the sim, don't you?

I've installed a Natty application from a deb package in Precise, Quantal and Raring, but cannot install the "old" Compiz and the "old" Nautilus, so it is a system-wide bug. The "development" had brought in minuses.

---

### Post by QIII on 2012-12-15
No.  It is not a bug.  It is a feature that has been deprecated.  It is not a matter of development that broke something.  It is a matter of development that was shelved due to lack of resources.  It's not like a sim card.

You should try to maintain complex software with too little time and too few resources sometime.

See how you like it when you are told you aren't working hard enough.

Give Martin or Sam a call.  Let them know they don't know what they are doing and you want to take charge -- pro bono.

---

### Post by Chdslv on 2012-12-15
> **QIII said:**
> No.  It is not a bug.  It is a feature that has been deprecated.  It is not a matter of development that broke something.  It is s matter of development that was shelved due to lack of resources.  It not like a sim card.

A good feature had been deprecated?! Well, that's bug, because in the "development" fervour, the devs couldn't find enough lines to put in the code.

> See how you like it when you are told you aren't working hard enough.That's not a problem. In life you have to work hard, and it is not always enough.

> Give Martin or Sam a call.  Let them know they don't know what they are doing and you want to take charge -- pro bono.It works in Precise, so it is Ubuntu devs problem, not someone else's. The base is Ubuntu's not Compiz devs.  In the never ending 'development" fervour, they had missed something. What, if the same "old" Compiz is included, and not the "new" one? I've a feeling that the "new" Compiz works just as well as the "old" one in Precise. 

Anyway, I am not going to argue with you on this matter, as Raring had not being released yet. 

By the way, can you "grub-setup" in the new raring? Can you change to the "old" Nautilus? Mind you, Precise is LTS and there you'd always have the "old" Nautilus till 2017, but you can't have it in Raring, which would end life before that.

So, these are base bugs.

---

### Post by Chdslv on 2012-12-15
Thought I might download nautilus 3.4.2 from my Precise installation and try to install it in Raring. This is what I got;

> dependency problems prevent configuration of nautilus:
 nautilus depends on libgnome-desktop-3-2 (>= 3.2.0); however:
  Package libgnome-desktop-3-2 is not installed.
 nautilus depends on liblaunchpad-integration-3.0-1 (>= 0.1.17); however:
  Package liblaunchpad-integration-3.0-1 is not installed.
 nautilus depends on nautilus-data (<< 1:3.5); however:
  Version of nautilus-data on system is 1:3.6.3-0ubuntu3 So, the nautilus-data is *blocking* the installation of the "old' Nautilus. Of course, there is a way around that, change the nautilus-data, install the dependencies, use apt-get -f install.  

> dpkg: error processing nautilus (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for libglib2.0-0:amd64 ...
No such key `computer-icon-visible' in schema `org.gnome.nautilus.desktop' as specified in override file `/usr/share/glib-2.0/schemas/10_nautilus.gschema.override'; ignoring override for this key.
Processing triggers for man-db ...
Errors were encountered while processing:
 nautilusSome other things missing/changed.

This is not an upstream matter, but the Ubuntu devs decided to use the "new" Nautilus and by doing so, disallowed F3 dual panes.

---

### Post by cariboo on 2012-12-15
> **Chdslv said:**
> Some are actually programs supposed to help the user, but are real bugs.

The apport problem: the never ending crash reports is a bug, which the Ubuntu devs had not looked at. It is annoying. One can disable Apport problem by disabling it, but then one would never know, if there is a *real* problem later.

Apport is always turned on during the development cycle, if you find it to annoying, you can turn it off in /etc/default/apport, and setting it to zero:

```
enabled=0
```

> The Compiz matter:  The plugins Precise had, neither Quantal or Raring has. There is no Annimation-addon and you can't use the 3D windows add on. In the development fervour, these had been disabled or made not to work, most probably the latter. When you develop and something goes missing, then it is a bug.

The compiz plugins are orphaned, and no longer have a devloper, meaning that when a new version of compiz is released, the plugins aren't updated to work with the new version. You are welcome to take over maintaining them, as they are open source, and anyone can modify the code 

> The Nautilus matter: Dual panes had been taken off the new nautilus, but Ubuntu should've given us the better, but old nautilus with the F3 option. There is no special need to abide by the ideas of the Gnome 3 devs, if the main UI is Unity for Ubuntu, so *not allowin*g the "old" Nautilus to be installed is a system-wide bug. One might try to install the SolusOS patched nautilus, but that's not the answer. Nautilus 3.4.2 should be in the repos as a variant. This is a Raring case.

If you feel this is a bug, you should report it upstream to the gnome developers at [Gnome Bugzilla]("https://bugzilla.gnome.org/")

> The Grub setup matter: It was pretty easy in Precise. You simply did sudo grub-seup /dev/sda, but in Raring (and in Quantal) this had been taken off. The only solution to set the Grub is by using a ppa, Yannubuntu's Boot-repair. Or else reinstall grub-pc.

I don't think I've used grup-setup since grub legacy, we now use install-grub and update grub:

```
sudo grub install /dev/sdX && sudo update-grub
``` 

where /dev/sdX is where you want to install grub

> Well, what do you think? Do you see any other bugs? The real annoying ones?

Seriously, Raring is better than Quantal or Precise. All these days, Ubuntu had warned us not to use the coming release on production machines, but that warning is now gone and you can download a daily, which is good as the devs are now very sure of their distro.

Raring is still in development, and will be until April, it can still can and will break, be sure you have a fallback installtion, just in case Raring becomes unusable. There are several major bugs still floating around, especially the one where many of us are still stuck on the 3.5 kernel because our AMD cpu powered systems won't boot anything newer, and just tonight, I managed to break my Raring install on my netbook, by doing updates.

> In my case, I don't think that Unity is a necessary evil to live with. I don't ever use Unity and search for other UIs. I've found one, an old one, which is practically discarded, because of its  universality, one that has no binding with a given WM or DE. (Devs appear to be *unhappy* with universal applications, so the go looking for others, such as Gnome-shell, Unity, Cinnamon...and taking away the right-click...)

When an ability is taken away, the whole thing becomes a bug

Ubuntu has always  and always will be gnome based, so where gnome goes, so does Ubuntu.

**Note** this is my second attempt at this post, as some forum glitch screwed up the formatting on the previous version, so if you saw the other one, you weren't seeing things. :)

---

### Post by mc4man on 2012-12-15
> **Chdslv said:**
> Thought I might download nautilus 3.4.2 from my Precise installation and try to install it in Raring. This is what I got;

Wrong release. if you want nautilus 3.4 in raring you'd use the quantal packages
Whether they remain viable thru release, don't know, you could likely build if need be.

(personally don't miss 3.4 at all

---

### Post by Chdslv on 2012-12-16
> **cariboo907 said:**
> Apport is always turned on during the development cycle, if you find it to annoying, you canturn it off in /etc/default/apport, and setting it to zero:

```
enabled=0
```

This I know and been done as the first thing after installation.

> The compiz plugins are orphaned, and no longer have a devloper, meaning that when a new version of compiz is released, the plugins aren't updated to work with the new version. You are welcome to take over maintaining them, as they are open source, and anyone can modify the codeI don't want to maintain them. If the Compiz plugins are orphaned, and the earlier ones are good, why not use them, rather than the orphaned ones? 

> If you feel this is a bug, you should report it upstream to the gnome developers at [Gnome Bugzilla]("https://bugzilla.gnome.org/")They don't produce Ubuntu.:)

> 
I don't think I've used grup-setup since grub legacy, we now use install-grub and update grub:

```
sudo grub install /dev/sdX && sudo update-grub
```where /dev/sdX is where you want to install grubGrub-setup works with Precise, and Precise's grub-pc is different from Quantal's and Raring's, and the only help is Boot-repair. It was pretty simple in Precise, if you ever have a grub-rescue problem. 

> Raring is still in development, and will be until April, it can still can and will break, be sure you have a fallback installation, just in case Raring becomes unusable. Raring had been good to me. I had installations upgraded from Precise, and it never broke, only that way, I could keep Nautilus 3.4.2. I always have a Precise installation, and my home is somewhere else.

> There are several major bugs still floating around, especially the one where many of us are still stuck on the 3.5 kernel because out AMD cpu powered systems won't boot anything newer, and just tonight, I managed to break my Raring install on my netbook, by doing updates.I have a small program, which downloads everything, before installing, and it asks whether yes or no. You can find it somewhere in Web Up8 or Noobslab. Its called apt-fast. It uses Apt, and you can do different downloads in different Terminals and use Synaptic too at the same time.

> Ubuntu has always  and always will be gnome based, so where gnome goes, so does Ubuntu.That I agree, but Ubuntu has its own mind too. :)

> **Note** this is my second attempt at this post, as some forum glitch screwed up the formatting on the previous version, so if you saw the other one, you weren't seeing things. :)Yes, bugs around us...:)

I am using a Natty application, and it is universal, not worried about the bases. The idea is, if it works, don't change it. In this every 6 month "development" fervour, the devs makes mistakes in trying to re-invent the wheel, and trying to make a square wheel.:)

If Ikey could do wonders with the "old" Nautilus, why can't the Ubuntu devs? Ikey's patched Nautilus is in the Ubuntu repos and using  Web Up8's ppa, you can install that "old" Nautilus. 

Take care!

Ch

---

### Post by QIII on 2012-12-16
> **Chdslv said:**
> They don't produce Ubuntu.

Wrong way around.  Canonical doesn't produce it. Your concerns need to be communicated upstream to those who do.

> **Chdslv said:**
> A good feature had been deprecated?! Well, that's  bug, because in the "development" fervour, the devs couldn't find  enough lines to put in the code.

That's not a problem. In life you have to work hard, and it is not always enough.

Deprecation of a feature is not a bug.  "Bug" has a very specific meaning in my profession, and that is not it.

> **Chdslv said:**
> I don't want to maintain them. If the Compiz  plugins are orphaned, and the earlier ones are good, why not use them,  rather than the orphaned ones?

Because something worked with a previous version of Ubuntu does not mean it will in a newer version.  Ubuntu changes.  The APIs change because basic parts of the OS have.  Usually developers of things like Compiz have to constantly move to keep up.  Happens to me all the time as the world changes.  If you don't have the resources to maintain everything, you make choices.

In  any case, you are welcome to express your displeasure to the Compiz  developers.  Don't send your email to Canonical for the Ubuntu  developers.  It's NOT on them.  Compiz does not belong to Canonical and it is the developers of Compiz who removed the features.

Compiz developers != Ubuntu developers.

[http://www.compiz.org/](http://www.compiz.org/)

Sam has a blog.  You might be interested in this particular entry:

[http://smspillaz.wordpress.com/2012/09/07/maintainers-for-the-unsupported-plugins/](http://smspillaz.wordpress.com/2012/09/07/maintainers-for-the-unsupported-plugins/)

Let him know your concerns and how you would suggest addressing them.

As I said, the KWin developers have made similar choices.  It wouldn't do much good to contact the Fedora, Kubuntu or OpenSUSE developers to complain about Martin deprecating some functionality for users of KWin and ATI graphics cards.  None of them owns KDE.

Canonical owns Unity, but not Compiz.

You are correct.  There is no need to argue.  I don't believe you understand how this all fits together, so you are barking up the wrong tree.   Unlike Windows, where Microsoft controls the whole code stack, Linux does not work that way.

Drive on.  Happy holidays.

---

### Post by cariboo on 2012-12-16
Just a small correction, Sam is the major developer of compiz, and he is employed specifically to develop compiz by Canonical

---

### Post by Chdslv on 2012-12-16
> **QIII said:**
> Deprecation of a feature is not a bug.  "Bug" has a very specific meaning, and that is not it.

Oh, we are into an argument.:) 
Everything is written with words, so a person can make mistakes in writing words, and that's called code.

> In  any case, you are welcome to express your displeasure the Compiz  developers.  Don't send your email to Canonical for the Ubuntu  developers.  It's NOT on them.  Compiz does not belong to Canonical. 
[http://www.compiz.org/](http://www.compiz.org/)
Sam has a blog.  You might be interested in this particular entry:
[http://smspillaz.wordpress.com/2012/09/07/maintainers-for-the-unsupported-plugins/](http://smspillaz.wordpress.com/2012/09/07/maintainers-for-the-unsupported-plugins/)
Tell them they aren't working hard enough.

This is nothing to do with Compiz, but with Ubuntu devs. They decide what to put in and what to keep out. They make a mistake in their "coding" and suddenly something doesn't work, but still its called "development."

Interestingly, the MS guys put out a "release" with lot of fanfare and eye-candy and then slowly send out "service packs." And, KB something or other. And, survive too!

Thanks for the links.:)

Have a good day!

---

### Post by Chdslv on 2012-12-16
> **cariboo907 said:**
> Just a small correction, Sam is the major developer of compiz, and he is employed specifically to develop compiz by Canonical

Aha, then he is doing not enough...don't we need 3D windows...?

He is not working there anymore [http://smspillaz.wordpress.com/](http://smspillaz.wordpress.com/)

---

### Post by zombifier25 on 2012-12-16
> **Chdslv said:**
> This is nothing to do with Compiz, but with Ubuntu devs. They decide what to put in and what to keep out. They make a mistake in their "coding" and suddenly something doesn't work, but still its called "development."

Interestingly, the MS guys put out a "release" with lot of fanfare and eye-candy and then slowly send out "service packs." And, KB something or other. And, survive too!

Thanks for the links.:)

Have a good day!

So you're saying that the Ubuntu devs could have put in some non-existent plugins that works with the latest Compiz but chose not to? It's not their job that some Compiz plugins don't work with the latest version, it's the Compiz devs' job. Same goes with GNOME and Nautilus. Canonical does not own GNOME, so they can't tell the GNOME folks to put back the missing features. They can't keep the old GNOME either, if so they'll be giving their users outdated softwares.

You're basically blaming Ubuntu for all the upstream "bugs". I do agree with you that these are genuine problems, but complaining here won't help.

---

### Post by QIII on 2012-12-16
> **cariboo907 said:**
> Just a small correction, Sam is the major developer of compiz, and he is employed specifically to develop compiz by Canonical

Thanks, cariboo907.

Employed or contracted?  I always thought he was more or less an "independent" developer and that Canonical is simply the big consumer of Compiz any more.

> **Chdslv said:**
> Oh, we are into an argument.:smile: 
Everything is written with words, so a person can make mistakes in writing words, and that's called code.

This is nothing to do with Compiz, but with Ubuntu devs. They decide  what to put in and what to keep out. They make a mistake in their  "coding" and suddenly something doesn't work, but still its called  "development."

You may be in an argument.  I'm not.  I'm just hanging out on the Forum wasting my beans in the RR forum to entertain myself.  (And thinking I need to start digging a bit to find out why Firefox has crashed on me for times in the last hour or so.)

I simply don't think you are quite understanding that the features you want are not gone because of mistakes in the code -- bugs.  They were removed on purpose.  Sam has specifically asked for volunteers to help in maintaining the stack for some of those things so they can get back in.

Removing a feature, no matter how irksome or disappointing, is not a bug.

I really liked the cube deformation and 3D windows myself.  Like to use that eye-candy on people who only use Windows to see if I could interest them in using Linux, too.  Too bad for me.  And I can't use KDE on my ATI machines to get the same effects.  Also too bad for me.

If I had time, I'd offer to help maintain those things.  Unfortunately, I am selfish and would rather pay my mortgage, car payments, dinners out, kid's college tuition ...

---

### Post by Chdslv on 2012-12-16
> **zombifier25 said:**
> So you're saying that the Ubuntu devs could have put in some non-existent plugins that works with the latest Compiz but chose not to? 

Yes, of course!
They are not non-existent.  [https://help.ubuntu.com/community/CompositeManager#Compiz](https://help.ubuntu.com/community/CompositeManager#Compiz)

Precise has the stuff, while the* forward developed* Quantal and Raring doesn't, so the development hadn't helped much.

> You're basically blaming Ubuntu for all the upstream "bugs". I do agree with you that these are genuine problems, but complaining here won't help.I use Ubuntu, and I don't ever complain. if you read my other posts, you'd notice that.:)
I like Ubuntu since long gone days. I just mentioned real bugs in this post to see, how others look into it.

I just said bugs, but didn't complain, for I am not the complaining type. Everything is written with words, so someone might make a mistake in writing. And, I am making a statement; development for the sake of development is useless. Six months time limit would always become smaller and smaller, and a release** has **to come out, and someone has to **make** things/write codes, and that has to be something new, or there might be no job. Cannonical employs people, and they do the coding, for the pay packet. For pay, one has to show progress and sometimes that progress is regress.

If the code, or written words had been changed, so that some abilities are cut off, then it is negative development. You don't take away abilities of a growing child, you do everything to add more!

Now, I don't want to get into an argument with anyone. I only mentioned what I felt, that's all. 

If a application is working, and never breaks, then that program is excellent. You don't "develop" it to lose its abilities. I have an application, written even before Maverick, somewhere in 2007, which works in all releases from Lucid to Raring.  It works in **any** Debian based distro too. **It means it is universal.**

No developer had tried to "develop" it further, and thanks heavens for that. Someone tried to fork it and can't get his distro out with the "developed" application for last 2 years.

I downloaded it, both the 32 and 64bit. I don't want to change it, develop it, or even read the code. **It simply works and that's all there is to that. **

The idea is not to break excellent applications, but keep them, don't touch them, don't develop them, don't even read the code. Just leave it and it'd continue to work. But, develop the other stuff, which needs developing, and adapt it to whatever you make.

Every wheel is round, at least on this Earth, and there no square wheels. If the number 3.4.2 is working very well, there is no need for 3.6.2 with some subtractions. If Compiz 0.8x is working well, don't touch it and don't update it, and don't even maintain it, just leave it in the repos for downloading. If 0.9.x is not that good, scrap it.

Quantal is already old and lost its usefulness as Raring is on the way. All these xx.10s are like that, just transitional, and forgotten very quickly.

I don't want to get into an argument. These are* only* my thoughts.:)

If anyone had noticed a real bug, I'd like to know, so I can stay out of trouble. Anyway, Raring had not given me any trouble at all, except for those I mentioned, and they are not that big trouble too. There are so many non-distro specific file managers around, Gnome-commander, Midnight-commander, Sunflower etc with the original 2 panes.

Take care, guys!
And have a good day!

Ch

---

### Post by Chdslv on 2012-12-16
> **QIII said:**
> You may be in an argument.  I'm not.  I'm just hanging out on the Forum wasting my beans in the RR forum to entertain myself.  (And thinking I need to start digging a bit to find out why Firefox has crashed on me for times in the last hour or so.)

You don't waste beans, they get automatically added. :)
Funny, I never had a single crash of Firefox so many years. Maybe, it simply likes me.:) 

> Removing a feature, no matter how irksome or disappointing, is not a bug.It is a bug, not in the application, but in the head of the developer. He thinks there is a bug and try to remove it from an excellently working application and kills it.

You noticed that Unity 2d is not available now, but few files are there with unity2d name in the /usr/bin. Why should it be there? [I]Unity2d is not there, and it is there. 

[/I]So, shall we delete them? Oh, Unity might not work? 
Why? Unity2d is not there, right?
For Unity3d to work, something of Unity2d must be there. Then, why take away Unity2d?
Bug? 
Yes, bug in the thinking of some developer...

Why not use Compiz 0.8.x? Oh, yes, but 9 is larger than 8, so it shows progress.
Why not use Nautilus 3.4.2? Because 6 is larger than 4 and shows progress.
 [/quote]

Good day, pal!
Ch

PS: Compiz devs own words; [I]The 0.8.x version of compiz is stable and mostly feature complete in the  sense that it is less likely to fail and currently receiving only  maintenance updates. The 0.9.x version of compiz is in an unstable  state, which means it is more likely to exhibit bugs and crashes.

[/I]In Quantal and Raring what do we have? The 0.9.x series. Who decided to put it there? The Ubuntu devs, disregarding what the Compiz devs warnings.

---

### Post by deadflowr on 2012-12-16
Have you filed bug reports for any of the items listed?
Personally, I don't think any of them, with an exception for apport, are bugs.

---

### Post by QIII on 2012-12-16
I am not arguing with you.  If I were, you would know it and I would  have long ago been kicked off this forum as I have been on many others.  I have been at this techie gig for a long time.  I simply think you appear to be expressing a rather naive understanding  of how this all works and you appear to have also made personal value  judgements about those who develop the code.    What you have identified may indeed be troublesome, but many things in life are.

> **Chdslv said:**
> ... but keep them, don't touch them, don't develop them, don't even read the code ...


It simply does not work that way.  It didn't work that way 35+ years ago when I started doing this stuff and it doesn't work that way now.  Code must be maintained as the world changes around it.  That some things continue to work for a long time does not mean that everything will.  Furthermore, just because something is stable and works exactly as it did 10 years ago is not necessarily a good thing.  There is a context.  If the context changes and the software, application or system does not, then it may continue doing what it did, but it will have lost its value.  In the new context, it does not work well.

> **Chdslv said:**
> It is a bug, not in the application, but in the  head of the developer. He thinks there is a bug and try to remove it  from an excellently working application and kills it.
No.  Things get removed for any number of reasons.  In the industry there are many reasons to deprecate the use of old things or remove them entirely.  Again:  the term "bug" has a specific meaning and this is not it.

> **Chdslv said:**
> PS: Compiz devs own words; *The 0.8.x version  of compiz is stable and mostly feature complete in the  sense that it is  less likely to fail and currently receiving only  maintenance updates.  The 0.9.x version of compiz is in an unstable  state, which means it is  more likely to exhibit bugs and crashes.*

PS:  Ubuntu is leading edge.  Not bleeding edge, but it is leading edge and sometimes even cutting edge.  That means that some things that are perhaps less than perfectly stable will be included.   If you thought otherwise, then perhaps the semi-annual versions are not for you.  The LTS versions tend to be less cutting edge.

In the case of Compiz, which is so tightly married to the graphical interface, leaving it alone would be the *worst *thing to do.  As the IU is improved, as things like X Server change, Compiz plugins must be actively maintained to ensure that they work with the new state.

Plugins need to be maintained and brought along to keep up.  In the example of 3D Windows, there were simply not enough resources to do that.  The fact that it was taken from the code stack is a pretty good indication that there was work that needed to be done on it to keep it up, or it simply would not have been removed.  That wasn't a whim.  That was a decision based on what was most likely to be useful to the greatest number of users and what could be left behind with the least disruption to users.

It is also extremely expensive to maintain several code stacks that have to be maintained independently, so in my industry it is simply necessary to cut dead weight to be able to keep up.  You can't always maintain the old and be able to move forward with the new.

It ***IS ***frustrating and disappointing when things you like disappear and you certainly have every right to be frustrated and disappointed.  But that does not constitute a bug, nor does it mean the developers are not doing their jobs.

It means that decisions was made in consideration of what resources were available and what product features were most likely to be important to preserve.

---

### Post by zombifier25 on 2012-12-16
> **Chdslv said:**
> You noticed that Unity 2d is not available now, but few files are there with unity2d name in the /usr/bin. Why should it be there? [I]Unity2d is not there, and it is there. 

[/I]So, shall we delete them? Oh, Unity might not work? 
Why? Unity2d is not there, right?
For Unity3d to work, something of Unity2d must be there. Then, why take away Unity2d?
Bug? 
Yes, bug in the thinking of some developer...


Just a quick guess, it's some old and deprecated configs that apply to both Unity and Unity 2D.

> 
If a application is working, and never breaks, then that program is excellent. You don't "develop" it to lose its abilities. I have an application, written even before Maverick, somewhere in 2007, which works in all releases from Lucid to Raring. It works in any Debian based distro too. It means it is universal.

No developer had tried to "develop" it further, and thanks heavens for that. Someone tried to fork it and can't get his distro out with the "developed" application for last 2 years.

I downloaded it, both the 32 and 64bit. I don't want to change it, develop it, or even read the code. It simply works and that's all there is to that.

The idea is not to break excellent applications, but keep them, don't touch them, don't develop them, don't even read the code. Just leave it and it'd continue to work. But, develop the other stuff, which needs developing, and adapt it to whatever you make.

Every wheel is round, at least on this Earth, and there no square wheels. If the number 3.4.2 is working very well, there is no need for 3.6.2 with some subtractions. If Compiz 0.8x is working well, don't touch it and don't update it, and don't even maintain it, just leave it in the repos for downloading. If 0.9.x is not that good, scrap it.

It's a sad fact, but softwares are developed to do one function, and do it well, and do it well through the advances of time. It's not to the developers' interest that it contains old extra features that some old users may still use, it's to make the software modern and usable. Some may argue that Windows' Start menu is never broken, and Microsoft should never switch to Metro in the first place. Sure, it may not be the intent of all developers (Xfce, LXDE, etc.), but it's the intent of a large portion of them (case in point: KDE 4, GNOME Shell, Unity, Windows 8, iTunes 11, Facebook interface changes, etc. etc.)

Not arguing with you, just stating a fact :)

---

### Post by lisati on 2012-12-16
> **Chdslv said:**
> Some are actually programs supposed to help the user, but are real bugs.

Let's have a think about things for a moment. The technology used by most of the Ubuntu forums regulars, both software and hardware, represents a number of influences and developments over the years. On the hardware side, one of the influences was the original IBM PC introduced in the 1980s. If we look back at some of the computers of that era, we will find that [punched card]("http://en.wikipedia.org/wiki/Punched_card") readers were a kind of device that was still in use. 

These days, we're more likely to find a keyboard and mouse or touchpad hooked up; punched card readers are as rare as hen's teeth on the typical hoome user's setup.

The reality is technology and the needs of computer users changes, together with the focus of those responsible for maintaining software: if we filed a bug report about absence of support for punched card readers, it would be most liekly be closed quickly and otherwise ignored, even if we had a need for transferring a company's 30-year-old archives to our HDD.

(And yes, like a handful of other users of this forum, I have been round long enough to have actually used punched cards.)

---

### Post by Chdslv on 2012-12-16
> **QIII said:**
> I am not arguing with you.  If I were, you would know it and I would  have long ago been kicked off this forum as I have been on many others.  I have been at this techie gig for a long time.  I simply think you appear to be expressing a rather naive understanding  of how this all works and you appear to have also made personal value  judgements about those who develop the code.    What you have identified may indeed be troublesome, but many things in life are.

We are not arguing, but discussing, and I like it. I made a mistake in using words, I should've written the code is in the mind of the developer, rather than in the head. I was in a hurry and that slipped in. So, sorry for that. The mind is not in the head, but that's another story.

Absolutely no naive.  Think about the new guy, who comes in from whatever he'd been using. He'd get mad in an hour with all that crash reports, never ending, hard to get rid for the new guy, and sometimes for the old guy too.  

Taking Compiz for example, Ubuntu shouldn't use what's considered as unstable by the Compiz devs, to release a stable distro, Quantal. Or they should take it and make it stable, and then release it. Unity is engined by Compiz, and take it away, there is no Unity.  So, an unstable Compiz, an unstable Unity.
Is that a bug, or downright carelessness?

It *always* takes one person to think about something new, so Compiz is also an idea of one person. You can pick his brains, but you can't pick his mind. You can muddle his code, but you can't muddle his mind. He stays away, his ideas, which are born in his mind stay away.

> Code must be maintained as the world changes around it.  That some things continue to work for a long time does not mean that everything will.  Furthermore, just because something is stable and works exactly as it did 10 years ago is not necessarily a good thing.  There is a context.  If the context changes and the software, application or system does not, then it may continue doing what it did, but it will have lost its value.  In the new context, it does not work well.

If no one messes up with the code of excellent application, it would work all the time, as far as we are using 32 and 64 bit machines. What is good 10 years ago, is still good, like someone's mother. Mac guys are earning massive money by using pretty old applications. Have look inside a Mac.{/quote]

> No.  Things get removed for any number of reasons.  In the industry there are many reasons to deprecate the use of old things or remove them entirely.  Again:  the term "bug" has a specific meaning and this is not it.

Many times, some good things are taken off by foolish decisions at the Board table. All, foolish or not decisions taken thinking only of one thing, profit. 
What is code? Lines of words, half words, etc, but a lot of mind work. Guys sitting around a Board table, considering money matters most times get another coder to muddle it. So, we have strange results, like the apport matter. 

> PS:  Ubuntu is leading edge.  Not bleeding edge, but it is leading edge and sometimes even cutting edge.  
Ubuntu is Wheezy-edge, rather than cutting edge.:D

> In the case of Compiz, which is so tightly married to the graphical interface, leaving it alone would be the *worst *thing to do.  As the IU is improved, as things like X Server change, Compiz plugins must be actively maintained to ensure that they work with the new state.

Again, no Compiz, no Unity, so using the unstable Compiz is not good.

> Plugins need to be maintained and brought along to keep up.  In the example of 3D Windows, there were simply not enough resources to do that.  The fact that it was taken from the code stack is a pretty good indication that there was work that needed to be done on it to keep it up, or it simply would not have been removed.  That wasn't a whim.  That was a decision based on what was most likely to be useful to the greatest number of users and what could be left behind with the least disruption to users.

The resources are there. Cannonical has them. No Compiz, no Unity, so they are bound to keep everything in very good working order. You click 3D windows, the sides of the cube in Unity goes black. Something lacking with the Unity UI, and as someone cannot get around it, sort of kills it.

> It is also extremely expensive to maintain several code stacks that have to be maintained independently, so in my industry it is simply necessary to cut dead weight to be able to keep up.  You can't always maintain the old and be able to move forward with the new. 
What's there to maintain? A simple 100-300 kb file doesn't have to be watered, 

> It ***IS ***frustrating and disappointing when things you like disappear and you certainly have every right to be frustrated and disappointed.  But that does not constitute a bug, nor does it mean the developers are not doing their jobs.

The devs are anonymous. They get paid, so they listen, or lose the job. If you take SolusOS, we know who does the coding, who keeps them in the server, Ikey. We know, who keeps the files in a server in Mint, Clem. In Ubuntu, the devs are anonymous, just like in Redhat.

> It means that decisions was made in consideration of what resources were available and what product features were most likely to be important to preserve. I've sat in many board meetings and its always about profit and nothing else.

Good day!
Ch

---

### Post by Chdslv on 2012-12-16
> **lisati said:**
> Let's have a think about things for a moment. The technology used by most of the Ubuntu forums regulars, both software and hardware, represents a number of influences and developments over the years. On the hardware side, one of the influences was the original IBM PC introduced in the 1980s. If we look back at some of the computers of that era, we will find that [punched card]("http://en.wikipedia.org/wiki/Punched_card") readers were a kind of device that was still in use. 

My first uni computer took half the block and I had punched cards. My first personal computer was an Atari. My first IBM 286 and it had only 20Mb memory, but I had all kinds of applications in it, from a word processor to graphics, and all inside a 20MB! We even played in Basic. Lovely times!;)

---

### Post by Chdslv on 2012-12-16
> **zombifier25 said:**
> So you're saying that the Ubuntu devs could have put in some non-existent plugins that works with the latest Compiz but chose not to? It's not their job that some Compiz plugins don't work with the latest version, it's the Compiz devs' job. Same goes with GNOME and Nautilus. Canonical does not own GNOME, so they can't tell the GNOME folks to put back the missing features. They can't keep the old GNOME either, if so they'll be giving their users outdated softwares.

You're basically blaming Ubuntu for all the upstream "bugs". I do agree with you that these are genuine problems, but complaining here won't help.

No Compiz, no Unity!
Ubuntu wants Unity, then it must keep Compiz in good shape, in an excellent shape.

> GNOME Session]
Name=Ubuntu
RequiredComponents=gnome-settings-daemon;
RequiredProviders=windowmanager;panel;
DefaultProvider-windowmanager=compiz
DefaultProvider-panel=compiz
DesktopName=Unity

Did you notice, the default provider of the panel is Compiz? 
And, what panel this could be?
Who cannot live without the other, Compiz or Unity?
Any instability of Compiz directly hits Unity. 
So, who should *look after* Compiz?

---

### Post by grahammechanical on 2012-12-16
Ok. I will admit it. I have not been following this thread. I have opinions. And one of them is that the definition of what is a 'bug' is too broad to be useful.

And while we are discussing Compiz I think that this blog post would give useful insight into the situation.

[http://smspillaz.wordpress.com/2012/06/08/on-the-future-of-graphics-drivers/]("http://smspillaz.wordpress.com/2012/06/08/on-the-future-of-graphics-drivers/")

It is a later post from the one linked to earlier.

> The existence of different and proprietary implementations of OpenGL promote a culture whereby we don’t engage with problems directly, but we corner case particular drivers, hack around others and create a sub-par system for everyone.

> If you’ve ever written code with me you’ll understand one thing – I hate writing hacks. Hacks are a short term solution which make a long term problem worse. Hacks demonstrate that you haven’t given the problem your full attention because you don’t understand what the problem is. Hacks are like trying to shove the incorrect puzzle piece into the puzzle. If you build your reality based on that, you’ll end up with something that’s very fuzzy, not rigid and crumbles very easily.

> Writing against proprietary drivers requires writing hacks, simply because there is a point where you can research no further into what the problem really is.

I stopped using the Nvidia driver during the Quantal cycle because I simply could not get a working installation with it except by putting in a hack. Which I am not confident enough to try. Why should I need that skill level anyway? 

It is common policy on this forum to recommend the proprietary video driver. That was good advice in the past. But when an update to the latest video driver breaks the install, then something is wrong.

I my opinion, and I have expressed this view before, too much trust is put into upstream code. Canonical code is tested. That is part of the motivation for the 'skunkworks' project. But who tests the upstream code? Who tests proprietary drivers? The user. That is who.

Regards.

---

### Post by Chdslv on 2012-12-16
> **grahammechanical said:**
> Out who tests the upstream code? Who tests proprietary drivers? The user. That is who. Regards.

That's the gist of it. 
The one, who tests is the user. 
The devs usually live in clouds, and most of them are anonymous.

Now, take your Precise install and go to /usr/bin and you'd find unity, unity-2d-panel, unity-2d-shell, unity-2d-spread.
Click on unity-2d-shell and see what happens. I am in the Gnome-classic session. Look at the first screenshot. Gnome-panel, Unity launcher, dash.

In the 2nd screenshot, I had clicked unity-2d-panel, and I am still in the Gnome classic session with full blown Compiz effects. You can see the gnome-panel underneath.

Try that with a Quantal installation and a gnome-classic session. The unity-2d-panel or unity-2d-shell won't work. Delete those two and copy and paste the same named one from a Precise installation, and click on them and see what you get.

Do you see, why Unity 2D was deleted from Quantal?

From the 1st screenshot, you'd notice that, you can have the Gnom-classic session with the Unity launcher, and Dash. Someone had found this out, so the Unity 2D was taken off from Quantal. Are the devs with us or against us?

In other words, we can have that Unity launcher and the Dash with any panel, Lxde, Xfce or even on Tint2.
So, for the next 5 years, Gnome-Classic session could have the usefulness of the search ability of Dash, and if someone wants the launcher too!

---

### Post by mc4man on 2012-12-16
> **Chdslv said:**
> 

The idea is not to break excellent applications, but keep them, don't touch them, don't develop them, don't even read the code. Just leave it and it'd continue to work. But, develop the other stuff, which needs developing, and adapt it to whatever you make.

Every wheel is round, at least on this Earth, and there no square wheels. If the number 3.4.2 is working very well, there is no need for 3.6.2 with some subtractions. If Compiz 0.8x is working well, don't touch it and don't update it, and don't even maintain it, just leave it in the repos for downloading. If 0.9.x is not that good, scrap it.


The last Ubuntu release to use compiz 0.8.x was Lucid. 
0.9.x is being actively developed as is Ubuntu, whether that leads to a 'stable', efficient compiz remains to be seen, it is certainly much improved over 0.9.4 in Natty.

As far as 'missing' plugins they fall into 3 types. Some have been removed from the code, likely never to return.
Some others build but don't work with GLES, others don't even build.

When or if these plugins are fixed/**re-written** then they'll come back, if not they won't. Their absence (ie. inability to work or even build) can be considered a bug but of extremely low current importance.

---

### Post by Chdslv on 2012-12-16
> **mc4man said:**
> The last Ubuntu release to use compiz 0.8.x was Lucid. 
0.9.x is being actively developed as is Ubuntu, whether that leads to a 'stable', efficient compiz remains to be seen, it is certainly much improved over 0.9.4 in Natty.

As far as 'missing' plugins they fall into 3 types. Some have been removed from the code, likely never to return.
Some others build but don't work with GLES, others don't even build.

When or if these plugins are fixed/**re-written** then they'll come back, if not they won't. Their absence (ie. inability to work or even build) can be considered a bug but of extremely low current importance.

Read my earlier post with screenshots to feel the "current." 

If Compiz 0.9.x is unstable, Unity would be unstable all the time. So, should the Ubuntu devs, take care of Compiz? 

They appear to take away good stuff, like the Unity 2D, not because it cannot be maintained, but because it troubles them. The screenshots would show why.

> As far as 'missing' plugins they fall into 3 types. Some have been removed from the code, likely never to return.
Some others build but don't work with GLES, others don't even build.

When or if these plugins are fixed/**re-written** then they'll come   back, if not they won't. Their absence (ie. inability to work or even   build) can be considered a bug but of extremely low current  importance.Compiz plugins would work very well with any other OS, like Arch,  Debian, Sabayon, Fedora, OpenSuse, etc, but won't work with Quantal, Raring,  whether it is 0.9.x or older. Bug? Or not!

Unity can't run on Gnome-wm, Metacity or whatever, but** only **on compiz. So, if Compiz cranks, Unity would crank.
But, Unity 2D would work with Gnome-wm, Metacity, etc, so it had to be killed.

---

### Post by mc4man on 2012-12-16
> **Chdslv said:**
> Read my earlier post with screenshots to feel the "current." 
No idea what you mean

> **Chdslv said:**
> 
If Compiz 0.9.x is unstable, Unity would be unstable all the time. So, should the Ubuntu devs, take care of Compiz? 
That's what they are doing, the use of 'unstable' just means in dev (to me

> **Chdslv said:**
> 
They appear to take away good stuff, like the Unity 2D, not because it cannot be maintained, but because it troubles them. The screenshots would show why.
Don't  know or care what all the reason were, but no,  "they" weren't able to properly maintain unity-2d

> **Chdslv said:**
> 
Compiz plugins would work very well with any other OS, like Arch,  Sabayon, Fedora, OpenSuse, etc, but won't work with Quantal, Raring,  whether it is 0.9.x or older. Bug? Or not!
I don't think they use compiz-0.9, if so certainly not with GLES support.
I already said that the 'in code but not working or built plugins' can be considered a bug(s) of no real current importance

---

### Post by exploder on 2012-12-16
Kind of silly to me to be in a development forum complaining about bugs. At this stage of development I just expect them. People have to understand that different things are developed at different rates, so you can not expect all the bugs to be fixed overnight.

---

### Post by Chdslv on 2012-12-16
> **exploder said:**
> Kind of silly to me to be in a development forum complaining about bugs. At this stage of development I just expect them. People have to understand that different things are developed at different rates, so you can not expect all the bugs to be fixed overnight.

Where did you get the word "complaining?"

I wrote something, and replied to others, that's all.

In this development forum, we talk about what's happening with Raring. 3D windows and animation-addons are not that special to me, but I mentioned them, as they can be fully implemented in Precise, but not on the transit Quantal, and in Raring daily. That's all. The real bug is the Apport matter, which is annoying, and if we disable it, we won't get an info on a real crash.

When, the discussion went on, I said that, if the compiz variant used in Raring is unstable by own words of the Compiz developers, then the Unity would be unstable. I looked into the unity file in the /usr/bin in Precise, Quantal and Raring. It is the same in size. There are unity 2D files in both Quantal and Raring, but are not the same as in Precise. 

The Unity launcher and Dash in Unity 2D and in Unity are the same. If the Unity 2D files are in Raring, as in Precise, they could be used to get at the Unity launcher and Dash, and could be used with *any* WM and *any* panel. The unstable Compiz 0.9.x is not needed, if you don't want desktop effects.

The so-called Unity 3D *needs* Compiz, and the one used is the unstable one. This is what the Compiz devs say; 

> Compiz is a compositing window manager that utilizes modern graphics  drivers for X on the Linux desktop. As such, it could potentially  trigger problems in X or related drivers. You should take caution when  using Compiz. You probably wouldn't want to install is on important  production machines, such as servers, business workstations or other  systems where uptime is crucial. It is however, suitable for normal  desktop use. In the event that Compiz causes system failure or data  loss, you will need to know how to recover your system. The 0.8.x  version of compiz is stable and mostly feature complete in the sense  that it is less likely to fail and currently recieving only maintenance  updates. The 0.9.x version of compiz is in an unstable state, which  means it is more likely to exhibit bugs and crashes. So, if you are using Unity 3D, and it *needs* Compiz, then you are using a unstable distribution, whether it is Precise, Quantal or Raring. That's all I had to say. And, when people replied, I replied too. That's all there is to it.

**I am not complaining. I never do. Period!**

I always find  a way out. If I need, I know how to get at Dash to work for me **without **Unity 3D. I just wanted to know, what others think of these matters, but I found only those, who are ready for a fight, just for the sake. Even, your comment is such.

Now, that most of you caught the keyword "Compiz", and went on writing about it, I wrote a bit more about that. I can live without the Compiz variant issued by Ubuntu and still have a stable installation. All my installations, Precise, Quantal and Raring **are stable. **No crashes whatsoever!

I write about something, I don't write complains, so drop the famous American word complain. 

I am open to other people's thinking, but not to whining. Can you refute anything I wrote, really refute?

Good day!

Ch

PS: What would happen, in your thinking, if you install the Gnome-panel, and then completely un-install Unity, Compiz from your Precise, Quantal or Raring installation, would it stop working?

---

### Post by Stinger on 2012-12-16
My 10 cent's ;)

If Compiz is that good, why does everyone else not use it ?

I'm sure if compiz was the best compositing window manager (read fastest and lowest on resources) every other distro would be building their 'shell' as a compiz-plugin like Unity.

That seems not to be the case, and you may ask yourselves why ?? :shock:

---

### Post by Chdslv on 2012-12-16
> **Stinger said:**
> My 10 cent's ;)

If Compiz is that good, why does everyone else not use it ?

I'm sure if compiz was the best compositing window manager (read fastest and lowest on resources) every other distro would be building their 'shell' as a compiz-plugin like Unity.

That seems not to be the case, and you may ask yourselves why ?? :shock:

Good question!

Isn't that why Unity is going on the wrong track?

---

### Post by rrnbtter on 2012-12-16
Greetings,
Original by Chdslv
> One can disable Apport problem by disabling it, but then one would never know, if there is a *real* problem later.Great thread to all!  I don't think that the Apport (and results) is instructive to most end users.  It should not have persisted into the Precise LTS. I can see it's usefulness to developers in the unstable versions, so far as problem solving is concerned.  
It has been minimal in 13.04 for me thus far.  The rest of this thread deals with paradigm shifts and one's tolerance for change.  Certainly we don't have square tires but we do have alternative means of moving mass where round tires perform poorly.  How about the guy that fears winged flight much less rocket powered motivation.  Unity and Compiz are a paradigm and I have witnessed the struggle of many to move on from their comfort zone into a new idea. Many adapted and are pleased with the results.  Others still wish it would go away.  
  For my part I like what I have in RR 13.04 so much that I just want to go along for the ride.  Its like not being a gamer but putting Half Life in "treat me tender" mode and just going for the experience with graphics and the few bad guys left over.  
  I was pleased pink with Maverick and Gnome2, thought it was a rocket of a system, that doesn't even compare to RR. RR is a whole new paradigm for me and I love it!

rrnbtter
Life is good! Live it to the Ubuntu-ist!

PS: I do think this thread is instructional regarding the horrors of mounds of code, the complex involvement of architecture and the arena of ideas.

---

### Post by grahammechanical on 2012-12-16
Excuse me, but I do not see how this

> Isn't that why Unity is going on the wrong track?

follows that

> I'm sure if compiz was the best compositing window manager (read fastest and lowest on resources) every other distro would be building their 'shell' as a compiz-plugin like Unity.

Is Compiz limiting the design of Unity? How would Unity be improved if Compiz was the fastest and lowest on resources compositing window manager?

Not that I know the track that Unity is on. Except as the Unified User Interface for all kinds of devices. The test of Unity being on the right track will come during the next year and a bit. 
 
Will we see Ubuntu on all kinds of devices? Will the non-computer type users find the interface usable on these devices? Or will the market be too crowded or be going in another direction?

Regards.

P.S. Hands up all those who know what a 'paradigm' is and can pronounce it. :) :)

---

### Post by Stinger on 2012-12-16
> **Chdslv said:**
> 
Isn't that why Unity is going on the wrong track?

Unity as a UI or 'shell' is a very good and intuitive UI, but it lack's on customization and IMHO it has a lot of disturbing 'lenses'.

A UI should not 'get in the way' and steal the users attention, I think Unity does that a bit.

Building unity as a compiz-plugin is IMHO plain wrong and that's why Ubuntu has lost it's appeal and why other distros like [Mint]("http://linuxmint.com/"), [OpenSUSE]("http://www.opensuse.org/") and [Mageia]("http://www.mageia.org/en/") are gaining a lot of users.
You just can't 'make up' for that by applying another (useless) lense or a fancy icon theme.

IMHO You have to rethink the whole concept !

---

### Post by rrnbtter on 2012-12-16
Greetings,

Original by Stinger
> IMHO You have to rethink the whole concept !Meaning changing "paradigm", pronounced (pair uh dime),  definition (new understanding and experience with reality).   
):P
rrnbtter
Life is good! Live it to the Ubuntu-ist!

---

### Post by grahammechanical on 2012-12-16
> **rrnbtter said:**
> Greetings,

Original by Stinger
Meaning changing "paradigm", pronounced (pair uh dime),  definition (new understanding and experience with reality).   
):P
rrnbtter
Life is good! Live it to the Ubuntu-ist!

Ah! A thank you from this old cockney who failed his English exams almost 50 years ago. And has been struggling to understand his own language ever since.

Can we all agree that anyone upgrading from 10.04 to 12.04 or later will indeed experience a new reality? Would there be those alternative Unity realities if it were not for Unity?

Regards.

---

### Post by Stinger on 2012-12-16
> **grahammechanical said:**
> 
Can we all agree that anyone upgrading from 10.04 to 12.04 or later will indeed experience a new reality?
Agreed, no one can ague with that 
> **grahammechanical said:**
> 
 Would there be those alternative Unity realities if it were not for Unity?
Yes of course there would, Unity has nothing to do with that, they all have their roots in touch-based smartphones.
Unity does not have a patent on that 'paradigm' (gotcha rrnbtter :biggrin:)

---

### Post by rrnbtter on 2012-12-16
Greetings,
Original by Stinger
> Unity does not have a patent on that 'paradigm' (gotcha rrnbtter :biggrin:)Original by rrnbtter
> RR is a whole new paradigm for me and I love it!The point made it this whole thread it that it's a matter of perspective. Paradigm is a personal reality perception.  For some, smartphone is part of that perspective for others it is not and that is the problem.  That leaves the question will Unity be the desktop that changes that desktop paradigm for the masses. I have to agree that it is a "wait and see".  Remember Windows had a 30 year venture in paradigm shifts and there was a lot of hair pulling along the way.  I know because I was there for it all. Linux has just as much right to that journey as anyone.  There has to be free enterprise or we all are the losers. Unity is just one man's enterprise. Isn't it?

rrnbtter
Life is good! Live it to the Ubuntu-ist

---

### Post by NHclimber on 2012-12-16
> **QIII said:**
> If I had time, I'd offer to help maintain those things.  Unfortunately, I am selfish and would rather pay my mortgage, car payments, dinners out, kid's college tuition ...

And yet, I bet the OP is psyched you have enough time to venture an opinion about his opinion...

---

### Post by rg4w on 2012-12-16
I've enjoyed the rotating cube for many years, and anyone who's used it knows it looks much better with the 3D window effect.

And as the OP noted, I've discovered that support for many details of the rotating cube have fallen off with each release of Unity since it premiered in 11.04.

And I got over it.

As much as I enjoyed showing it off to friends, in retrospect that's the only benefit it ever provided for me.  I respect that it may have some utilitarian value for others, but for me what I really need is a good way to switch between desktops, and the built-in method is quick, simple, and keyboard-configurable enough that I don't really miss not using the cube anymore.

I went to USD in May to participate in the QQ cycle.  Interesting times.  Saw a lot of what goes on to make Ubuntu.  I can tell you, it's not slack.

No one there wants to kill any aspect of the cube.  They just have other priorities, and if something in Unity's evolution loses compatibility with a niche plugin like 3D windows, they just have to accept it and keep moving forward.

We live in a world of limitations, and no software project has unlimited resources.  Given what they have to work with and what they want to achieve, the 3D window plugin just isn't something they can spend money on right now.

But this is Linux.  The source is available.  Anyone who feels strongly enough about it can dive in and make any changes they want.  That's what free software is all about.

I appreciate the time and money Canonical and the rest of the community devotes to giving me a free OS.  I make suggestions, but when faced with a multimillion-dollar gift like Ubuntu I don't make demands.  I appreciate what they provide, and am willing to provide for myself anything they don't.

---

### Post by jbicha on 2012-12-16
> **Chdslv said:**
> The resources are there. Cannonical has them. No Compiz, no Unity, so they are bound to keep everything in very good working order.

No, Canonical has rather limited resources. I think they've gotten criticism for everything they've tried to do to make enough money to pay their employees (Launchpad, Landscape, Ubuntu One, Ubuntu One Music Store, enabling proprietary apps in the Ubuntu Software Center, Amazon integration, affiliate revenue in the web browser or the music player, etc.).

> **Chdslv said:**
> 
What's there to maintain? A simple 100-300 kb file doesn't have to be watered, 

Compiz is not just a few hundred kilobytes. One particular example of the maintenance needs is that GNOME 3.4 dropped gconf support for keyboard shortcuts. It was necessary for Compiz to switch from the deprecated gconf to gsettings, but nobody stepped up to do that work for Unity 2D. And no, permanently sticking with GNOME 3.2 isn't a good answer either.

> **Chdslv said:**
> 
The devs are anonymous. They get paid, so they listen, or lose the job. If you take SolusOS, we know who does the coding, who keeps them in the server, Ikey. We know, who keeps the files in a server in Mint, Clem. In Ubuntu, the devs are anonymous, just like in Redhat.

Actually, it's possible to see exactly who did what in most open source development. Not only is the source open, but so are the commit logs. For instance, visit [https://launchpad.net/compiz](https://launchpad.net/compiz) and click **Browse the code**. Click **Changes**.

Also, quite a bit of the work done in Ubuntu is done by volunteer contributors who are not paid by Canonical or even anyone at all for that work.

> **Chdslv said:**
> 
I've sat in many board meetings and its always about profit and nothing else.


How much have you paid for Ubuntu? Do you really feel like you are getting ripped off?

---

### Post by Chdslv on 2012-12-16
Its becoming nice now, as more guys are getting on board. The continuous news-about-crashes is a headache, which is there in Precise too. Don't know, whether it is a problem to Mark S, or he is using Mageia for his daily work. 

> **rg4w said:**
> I've enjoyed the rotating cube for many years, and anyone who's used it knows it looks much better with the 3D window effect.

And as the OP noted, I've discovered that support for many details of the rotating cube have fallen off with each release of Unity since it premiered in 11.04.
And I got over it.

No, I haven't. It is not the beauty of the 3D effect, but also the quickness of changing workplaces. 3D cube is still there in Raring, but if you enable 3D windows, you get black sides and blurred movement, if you can call that a movement.

And, that's bug--bad coding, bad thinking, lack of real interest in *one's own* WM and the compositing manager. 

> No one there wants to kill any aspect of the cube.  They just have other priorities, and if something in Unity's evolution loses compatibility with a niche plugin like 3D windows, they just have to accept it and keep moving forward.

Who are "they?" The guys, who work for Cannonical for pay, or the guys, who are willing to help out the "development" of the Ubuntu base, but has to go along with *the* board decision?

That *niche plugin *3D windows has more to give than the Unity's evolution. This "evolution" is going forward developing itself by killing off useful applications, such as Unity 2D and parts of Compiz, their own WM & CM. *Unity 2D, with its launcher and Dash was first to be designed, and now a must-have for Unity 3D to work, but lines of code could be moved to other files, hiding the fact. *If Ubuntu had dropped Unity 2D in QQ, then, why are the files of Unity 2Dhanging around in QQ and RR? 

Is it true, that Unity 3D was the *evolution *of Unity 2d, and now the dad is killed off? 
If you look at the screenshots, you'd notice that the Gnome-wm is working as the window manager,* and* Unity's launcher and Dash is present in *that* environment. The Gnome-wm has all the abilities of a 3D desktop, and Compiz is called in, *when *needed (compiz --replace).

It doesn't matter, what is your desktop environment, Gnome-wm, Metacity, Lxde, Xfce, the Unity launcher and the Dash works, *which makes* the Unity 3D redundant. So, the Unity 2D files had been changed, not to let the launcher and dash to come out, *withou*t the top panel. *Someone had found the danger*, and Unity 2D was killed off, even though most parts of Unity 2D is still needed, and always be needed, if Unity 3D is to work. (I *noticed* this as soon as the news about dropping Unity 2d was announced before QQ was released.)

Now, don't just take my word for this. Take a Precise installation, copy the 2 files from /usr/in, take your QQ or RR and delete the same-name 2 files, and paste them and click and see what you get. To make the experiment even better, rename the unity file in your /usr/bin for this session only. 

> We live in a world of limitations, and no software project has unlimited resources.  Given what they have to work with and what they want to achieve, the 3D window plugin just isn't something they can spend money on right now.

Keeping a small file in th e repos is not a big deal and doesn't cost more than few cents/annum. But, when these files trouble, they are killed off.

> But this is Linux.  The source is available.  Anyone who feels strongly enough about it can dive in and make any changes they want.  That's what free software is all about.

Are you sure, this is free software? Try to change a .so file, and you'd notice, how free it is. Try to install something, and you get a whole bunch of hangers on coming in. Sure, you can delete them later. You can't uninstall them, as that whole bunch would want to go, but you can physically delete them. 

> I appreciate the time and money Canonical and the rest of the community devotes to giving me a free OS.  I make suggestions, but when faced with a multimillion-dollar gift like Ubuntu I don't make demands.  I appreciate what they provide, and am willing to provide for myself anything they don't.

Cannonical is business company, which is profit oriented, and nothing, my friend, is given free from a business company. In a business, anything that won't make money would be dropped, even if its a charity. 

(I suppose, you know that charity is tax-deductible, so brings in more than that's given? The money spent on charity is eventually paid up by the government, meaning you and me, in tax-deductions, but that's another story. )

As Ubuntu is using a *unstable* application as its window and composite manager to make Unity 3D work, *then* Unity would be always unstable, if the Compiz developers *won't make* that Compiz stable.

---

### Post by NHclimber on 2012-12-16
Whoa. Oh look, my stop. This is where I get off...

---

### Post by Chdslv on 2012-12-16
> **NHclimber said:**
> Whoa. Oh look, my stop. This is where I get off...

Have a good journey!;)

---

### Post by KiwiNZ on 2012-12-16
it is **pre beta**, of course there will be issues the development has only just started.

If you feel there are bugs file reports and they may or may not be agreed with and worked on. Rotating discussion here is like shout about them in the wilderness.

---

### Post by rg4w on 2012-12-16
> **Chdslv said:**
> And, that's bug--bad coding, bad thinking, lack of real interest in *one's own* WM and the compositing manager. 
What did you find in your review of the source for Unity and Compiz led you to the opinion this is easy to address?

And if it's easy, did you submit the patch while you were at it?

---

### Post by Chdslv on 2012-12-17
> **rg4w said:**
> What did you find in your review of the source for Unity and Compiz led you to the opinion this is easy to address?

And if it's easy, did you submit the patch while you were at it?

Oops, people are getting angry.

Maybe, you could tell us, how come the same Compiz (0.9.x) works with *all *the plugins in Arch, Debian, Fedora, Gentoo (Sabayon, Calculate etc), OpenSuse, Slackware etc? 

Why is it that in Lubuntu, Xubuntu, Ubuntu-Gnome remix and any other QQ based or RR based distro, the 3D windows plugin doesn't work? The Animation-addons cannot be even seen?

I mentioned Debian, meaning Wheezy, and Ubuntu is based on Debian Wheezy, **but** the same application works very well with Debian, while it doesn't work with QQ or RR, even if you take off everything Unity!

So, is it a bug, a system-wide one, or not?

Jeremy, your Gnome-Remix under QQ has the same bugs. It doesn't appear to have anything Unity there, but it has *the* same problems. But, take Debian and (add Gnome 3.6) the problems go away. 

In this "development" fervour, certain libraries had been changed, so not to allow certain packages (Ubuntu Precise ones) to be installed. These libraries cannot be opened in Gedit. The newer version, say libsomething.so has a higher number, and won't allow a simple Ubuntu application of a lesser number to be installed. *That is, the "developed" higher number libsomething.so is lacking the abilities of the same libsomething.so with the lower number.*

When you upgrade your vehicle, you'd always want to have space for your beloved grandma in it, don't you? 

Have a good day, guys, and stop worrying or getting angry. 

By the way, I should've written "bugs in Ubuntu", rather than "bugs in Raring." 

Take care!

Ch

---

### Post by mc4man on 2012-12-17
> **Chdslv said:**
> 
Maybe, you could tell us, how come the same Compiz (0.9.x) works with *all *the plugins in Arch, Debian, Fedora, Gentoo (Sabayon, Calculate etc), OpenSuse, Slackware etc? 
Likely because they use an older 0.9.x & not this
> compiz (1:0.9.8.0-0ubuntu1) quantal-proposed; urgency=low

  * debian/control, debian/rules: 
    - enable gles on armel and armhf
    - use dh-translations rather than custom code

  [ Sam Spilsbury ]
  * Enable OpenGL ES building 
    - Refresh debian/patches/workaround_broken_drivers.patch
    - Remove non-ported plugins from compiz-plugins
    - Add FindOpenGLES2.cmake to compiz-dev

  [ Timo Jyrinki ]
  * New upstream release.
    - Code to make compiz work on GLES. This includes several changes 
      to the compiz API. (LP: #201342) (LP: #901097) (LP: #1004251)
      (LP: #1037710)
    - Draft first 0.9.8.0 NEWS and bump VERSION
  * debian/patches/compiz-package-gles2.patch:
    - Remove, obsoleted by the upstream GLES work 
  * Disable plugins that don't work on pure GLES on armhf/armel:
    - bench, firepaint, mblur, showmouse, splash, showrepaint, td, widget

 -- Sebastien Bacher <seb128@ubuntu.com>  Fri, 31 Aug 2012 22:59:50 +0200
> **Chdslv said:**
> 
In this "development" fervour, certain libraries had been changed, so not to allow certain packages (Ubuntu Precise ones) to be installed. These libraries cannot be opened in Gedit. The newer version, say libsomething.so has a higher number, and won't allow a simple Ubuntu application of a lesser number to be installed. *That is, the "developed" higher number libsomething.so is lacking the abilities of the same libsomething.so with the lower number.*


You may want to spend a bit more time reading than writing

> **Chdslv said:**
> 
That niche plugin 3D windows has more to give than the Unity's evolution.
I guess there's no discounting people's perceptions, as weird as they may be.

---

### Post by Chdslv on 2012-12-17
> **mc4man said:**
> Likely because they use an older 0.9.x & not this> 

Really?!
0.9.x is 09.0.x, where the x could be anything, but the series is the same.

[quote]You may want to spend a bit more time reading than writing

Exactly pal, I've reading, not only the articles, but the something more too.

[quote]I guess there's no discounting people's perceptions, as weird as they may be.

Isn't this your perception, as weird as they may be.

Good day!

---

### Post by Chdslv on 2012-12-17
Somethings to ponder about, Precise, Quantal and Raring, and also 13.10; Precise would end of life in April 2017, and by that time, Quantal and Raring would be long gone in April and in October 2014.  The still unnamed 13.10 would also end life in April 2017. Ubuntu 14.04 LTS would arrive.

Until such time in April 2017, all **four** releases would be transit ones, testing the individual user, but **not** the enterprise user. The enterprise user is given a solid OS to live with, work with, Precise.

Everything in Precise work, even the Compiz 0.9.x, Nautilus, Unity2D...:)

In Quantal, then in Raring, and the one to come, apps would be tested, users would be tested...and the support would be taken off from all three, to allow a new LTS to come. That LTS, whether you like it or not, would be enterprise class, and directed to businesses. I suppose, you heard the Google guys, why they use Precise and won't change it. 

You can, of course, install Linux kernel 3.7 in Precise, and if the still unnamed one would have 3.9, that too could be installed. Precise's development had stopped. There'd be very carefully thought out updates in Precise repos. *You just can't break an enterprise release, can you?* 

This Raring and the next unnamed one would be the transitional testing ones, but the *real *release would come in April 2014. *Lucid as a server installation lives untill April 2015!*
Even though Lucid as a desktop would end life in April 2013, it can still pull updates from repos untill April 2015.

Yes, I should've written "real bugs in Ubuntu", rather than Raring.

---

### Post by rrnbtter on 2012-12-17
Greetings,
Original by Chdslv 
> 
Yes, I should've written "real bugs in Ubuntu", rather than Raring.

Actually I got the idea from the very start of the thread. In addition I haven't found much to argue with in this thread from anyone.  The whole thing has been informative and instructive. 
You efforts are appreciated at least from this old hack. Just know that as an experienced former professional I have yet to use an OS without bugs. Drats!!! Some of them were quickly regretted even by the developer. I'm thinking Windows ME but there were others.
Best wishes and I'm also out of here!):P
rrnbtter
Life is good! Live it to the Ubuntu-ist!

---

### Post by Chdslv on 2012-12-17
> **rrnbtter said:**
> Greetings,
Original by Chdslv 


Actually I got the idea from the very start of the thread. In addition I haven't found much to argue with in this thread from anyone.  The whole thing has been informative and instructive. 
You efforts are appreciated at least from this old hack. Just know that as an experienced former professional I have yet to use an OS without bugs. Drats!!! Some of them were quickly regretted even by the developer. I'm thinking Windows ME but there were others.
Best wishes and I'm also out of here!):P
rrnbtter
Life is good! Live it to the Ubuntu-ist!

Greetings!

True, there are no OSs without bugs. You know, while Precise is quite alright, in this "development" fervour, certain apps had been taken away, saying they can't maintain them, which is disappointing. 

Unity 2D would live until April 2017 in Precise. Compiz 0.9.x would too in its full blast. The same Compiz 0.9.x cannot work Quantal and Raring as well as in Precise. And, I cannot take that as development, but as regression. 

I am betting that, someone found out that Unity launcher and dash could be implemented in any panel and in any WM, without the Unity prison, so was taken off, changed the libraries so no one would get it implemented in Quantal, Raring or the one is to come. It would've been a big loss, if someone released a distro/Os with the Gnome panel, Lxde panel or Xfce panel and with a cut down launcher and the Dash. 

I am from the pre-286 days, so old as you are or more.:p

Take care!

Ch

---

### Post by zombifier25 on 2012-12-17
> **Chdslv said:**
> Really?!
0.9.x is 09.0.x, where the x could be anything, but the series is the same.


Not the same. The version numbering may be different, but a lot of stuffs has happened (OpenGL ES port,...) Version numbering does not indicate the development process, though in most cases it does.

You know why Linus decided to move Linux from 2.6.a.lot.of.numbers to 3? Not because of some life-changing features introduced, simply because he is fed of the numbers. The man himself said that:
[quote=Linus Torvalds]So what are the big changes? NOTHING. Absolutely nothing. Sure, we have the usual two thirds driver changes, and a lot of random fixes, but the point is that 3.0 is *just* about renumbering, we are very much *not* doing a KDE-4 or a Gnome-3 here. No breakage, no special scary new features, nothing at all like that. We've been doing time-based releases for many years now, this is in no way about features. If you want an excuse for the renumbering, you really should look at the time-based one ("20 years") instead.[/quote]

---

### Post by jbicha on 2012-12-17
> **Chdslv said:**
> 
I am betting that, someone found out that Unity launcher and dash could be implemented in any panel and in any WM, without the Unity prison, so was taken off, changed the libraries so no one would get it implemented in Quantal, Raring or the one is to come. It would've been a big loss, if someone released a distro/Os with the Gnome panel, Lxde panel or Xfce panel and with a cut down launcher and the Dash. 


We've already explained several times in this thread why Unity 2D and several Compiz plugins were dropped (basically it requires challenging technical work and nobody volunteered to do it).

Your conspiracy theories and verbosity about stuff you don't understand is getting pretty annoying to those of us who are working to make Ubuntu better. I'm not saying that you can't have opinions, but your attitude is rather confrontational and you clearly don't have all the facts straight.

---

### Post by Elfy on 2012-12-17
This isn't going anywhere very fast, in fact it's fast catching up with it's tail.

Closed.

---

