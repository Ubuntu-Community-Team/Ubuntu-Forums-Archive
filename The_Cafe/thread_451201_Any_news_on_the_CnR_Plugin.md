---
title: "Any news on the CnR Plugin?"
date: 2007-05-22
forum: The Cafe
---

### Post by ablaze on 2007-05-22
Does anyone know when CnR will go public and if and when we will see Ubuntu support for it? Has Linspire already published its first version based on Ubuntu?

Questions, questions... But perhaps anyone here has got some insight.

---

### Post by chakkaradeep on 2007-05-22
> **ablaze said:**
> Does anyone know when CnR will go public and if and when we will see Ubuntu support for it? Has Linspire already published its first version based on Ubuntu?

Questions, questions... But perhaps anyone here has got some insight.

Please ask [here]("http://forum.freespire.org") than here

---

### Post by vseehua on 2007-05-22
[http://wiki.freespire.org/index.php/Freespire_2.0_Schedule](http://wiki.freespire.org/index.php/Freespire_2.0_Schedule)

---

### Post by ablaze on 2007-05-22
Thanks a lot.

---

### Post by Adamant1988 on 2007-05-22
> **ablaze said:**
> **Does anyone know when CnR will go public and if and when we will see Ubuntu support for it? Has Linspire already published its first version based on Ubuntu?**

Questions, questions... But perhaps anyone here has got some insight.

No, and for the good of Ubuntu users everywhere I really hope it stays that way.

---

### Post by awakatanka on 2007-05-22
> **Adamant1988 said:**
> No, and for the good of Ubuntu users everywhere I really hope it stays that way.

Think some want it. So i hope you speak for yourself ;). Hope it will come soon.

---

### Post by Adamant1988 on 2007-05-22
> **awakatanka said:**
> Think some want it. So i hope you speak for yourself ;). Hope it will come soon.

I'm not looking forward to the flurry of support requests because 'CNR broke apt'.  CNR has a well documented history of not playing nicely with other package managers. If you're going to use JUST CNR then I suppose it's fine.

---

### Post by jrusso2 on 2007-05-22
> **Adamant1988 said:**
> I'm not looking forward to the flurry of support requests because 'CNR broke apt'.  CNR has a well documented history of not playing nicely with other package managers. If you're going to use JUST CNR then I suppose it's fine.

considering that CNR is supposed to be a web front end for APT I don't see why this would happen.  It would use the same repository with the addition of the proprietary software that Linspire wants to sell.

---

### Post by Polygon on 2007-05-22
and not to mention that canonical is working with linspire on this project,  i highly doubt that they will include it by default or an option to enable it in ubuntu if it is buggy and will break apt.

I think its just going to be like "Add/Remove Software" or "Synaptic". Both are different programs, let you install/remove software  software and add entries to the apt database.

---

### Post by Adamant1988 on 2007-05-22
> **jrusso2 said:**
> considering that CNR is supposed to be a web front end for APT I don't see why this would happen.  It would use the same repository with the addition of the proprietary software that Linspire wants to sell.

Whoever told you that is completely full of it.  CNR is NO such thing.   If you need any proof of this, please, by all means, try using apt on Linspire 5-0.  CNR is it's own package manager that at it's back end STILL does use .deb and .rpm just like anything else, it is not a front end for anything.   Also, I am not the only one who is concerned with the ability of apt to handle the presence of CNR, there are several Ubuntu devs who worry about it too.

---

### Post by jrusso2 on 2007-05-22
> **Adamant1988 said:**
> Whoever told you that is completely full of it.  CNR is NO such thing.   If you need any proof of this, please, by all means, try using apt on Linspire 5-0.  CNR is it's own package manager that at it's back end STILL does use .deb and .rpm just like anything else, it is not a front end for anything.   Also, I am not the only one who is concerned with the ability of apt to handle the presence of CNR, there are several Ubuntu devs who worry about it too.

This is from CNR.COM

Does CNR.com use new packages rather than the traditional .deb and .rpm systems?

No! The great thing about CNR.com, is that it normalizes the installation process for the user WITHOUT requiring a new or altered packaging system. CNR.com uses standard .deb and .rpm files, but hides the complexity of this from the user. This allows developers to continue using their same methods and the different distributions to continue with their normal release management practices, yet provide their users with a much easier software management system.

Can I still use other installation methods, such as apt-get or YAST, along with CNR?

Absolutely.

Will I break anything if I sometimes use CNR and at other times use other install systems such as apt-get or YAST?

You shouldn't, provided you only pull from the same version repository when using either CNR or the other method. CNR does have several additional safeguards that other install technologies do not have to automatically correct dependency problems, but as long as you are using the same version repository, you should be able to install using both CNR and other install systems. However, if you mix repositories (pulling from other versions of your distributions), then you do run the risk of creating dependency problems within your system. Rather than having to pull from multiple warehouse pools, it is our desire to have as much current software in the CNR Warehouse pools as possible, so the need to go outside these pools is minimized, thereby reducing the risk of breaking your system.

---

### Post by Adamant1988 on 2007-05-22
> **jrusso2 said:**
> This is from CNR.COM

Does CNR.com use new packages rather than the traditional .deb and .rpm systems?

No! The great thing about CNR.com, is that it normalizes the installation process for the user WITHOUT requiring a new or altered packaging system. CNR.com uses standard .deb and .rpm files, but hides the complexity of this from the user. This allows developers to continue using their same methods and the different distributions to continue with their normal release management practices, yet provide their users with a much easier software management system.

Can I still use other installation methods, such as apt-get or YAST, along with CNR?

Absolutely.

Will I break anything if I sometimes use CNR and at other times use other install systems such as apt-get or YAST?

You shouldn't, provided you only pull from the same version repository when using either CNR or the other method. CNR does have several additional safeguards that other install technologies do not have to automatically correct dependency problems, but as long as you are using the same version repository, you should be able to install using both CNR and other install systems. However, if you mix repositories (pulling from other versions of your distributions), then you do run the risk of creating dependency problems within your system. Rather than having to pull from multiple warehouse pools, it is our desire to have as much current software in the CNR Warehouse pools as possible, so the need to go outside these pools is minimized, thereby reducing the risk of breaking your system.

You give them far too much credit.  Let's disect this: 
> Does CNR.com use new packages rather than the traditional .deb and .rpm systems?

No! The great thing about CNR.com, is that it normalizes the installation process for the user WITHOUT requiring a new or altered packaging system. CNR.com uses standard .deb and .rpm files, but hides the complexity of this from the user. This allows developers to continue using their same methods and the different distributions to continue with their normal release management practices, yet provide their users with a much easier software management system.

Right, exactly like I said.. it uses .deb and .rpm at it's back end, but it is NOT a front-end for apt or anything else.  .deb != apt. 


> Can I still use other installation methods, such as apt-get or YAST, along with CNR?

Absolutely.
 You forgot the sub-text: "Once in a while, maybe." 

> Will I break anything if I sometimes use CNR and at other times use other install systems such as apt-get or YAST?

You shouldn't, provided you only pull from the same version repository when using either CNR or the other method. CNR does have several additional safeguards that other install technologies do not have to automatically correct dependency problems, but as long as you are using the same version repository, you should be able to install using both CNR and other install systems. However, if you mix repositories (pulling from other versions of your distributions), then you do run the risk of creating dependency problems within your system. Rather than having to pull from multiple warehouse pools, it is our desire to have as much current software in the CNR Warehouse pools as possible, so the need to go outside these pools is minimized, thereby reducing the risk of breaking your system.

Now, here's what they don't tell you: 
CNR does not talk to apt, it does not tell apt what you have installed. Dependency problems are not the issue, the issue is CNR completely and utterly breaking apt after use, or vice-versa.  If you need any proof of this, again, use apt on Linspire.  You'll be left with a system of broken package management galore, EVEN THOUGH you use the same 'version repos'.

---

### Post by jrusso2 on 2007-05-22
I will pass on using Linspire as its old broken junk that you have to pay for.  I did use Freespire for a bit which is also old broken junk that you don't have to pay for.

I installed synaptic on Freespire and it used the exact same repository as the CNR with the exception of the stuff you have to buy.

Sometimes when I used CNR and it had a broken package I  would use synaptic to remove the broken package.

---

### Post by dca on 2007-05-22
Do we really need a ton of package managers on a single distribution?  
 
I'm gonna' wait this one out.
 
 
Kind of like a SuSE thing.  You can config your printer using YaST (if you have a spare forty mins) or use the tool in the control center.  Redundancy is a killer on distro(s) trying to stay within a single CD ISO.

---

### Post by forrestcupp on 2007-05-22
Adamant, the CNR they will be releasing for Ubuntu is absolutely not the CNR that you used and had bad experiences with.  The Ubuntu version of CNR will not be anything like using apt with Linspire.  Ubuntu is made to use apt, and it works well.  Linspire was not made to use apt.  The Ubuntu version of CNR will use our current repos and it will be a complete makeover.  You really should not spread FUD based on your experiences with the old version of CNR that is completely different code.

If there is a flood of help requests for CNR, it is your right to not respond to these requests.  It's definitely your right to not use CNR if you don't want it.

Now back to the original legitimate question.  Has anyone heard any news on the Ubuntu CNR release?

---

### Post by Adamant1988 on 2007-05-22
> **forrestcupp said:**
> Adamant, the CNR they will be releasing for Ubuntu is absolutely not the CNR that you used and had bad experiences with.  The Ubuntu version of CNR will not be anything like using apt with Linspire.  Ubuntu is made to use apt, and it works well.  Linspire was not made to use apt.  The Ubuntu version of CNR will use our current repos and it will be a complete makeover.  [B]You really should not spread FUD based on your experiences with the old version of CNR that is completely different code.
[/B]
If there is a flood of help requests for CNR, it is your right to not respond to these requests.  It's definitely your right to not use CNR if you don't want it.

Now back to the original legitimate question.  Has anyone heard any news on the Ubuntu CNR release?

Can you verify that it's of completely different code? Last I checked CNR for Linspire 5-0 was a closed source application, how am I to know you haven't simply opened that up, let the community work on it, and pretty up the interface for the site? 

Also, again, I am not the only one who is concerned that CNR is going to start breaking systems left and right with extended use, I know of several Ubuntu developers who are gritting their teeth on this one too.  Seems to me like the developers of Ubuntu would have a clue on the matter, but maybe that's FUD too. 

Also, my response to the users of CNR who experience breakage is going to be the same as people who use Automatix and have problems with an upgrade, or experience breakage.  "I told you so".

---

### Post by aysiu on 2007-05-22
[Kevin Carmony announced in September that it'd be going open source](http://www.osweekly.com/index.php?option=com_content&task=view&id=2344&Itemid=468)

---

### Post by Adamant1988 on 2007-05-22
> **aysiu said:**
> [Kevin Carmony announced in September that it'd be going open source](http://www.osweekly.com/index.php?option=com_content&task=view&id=2344&Itemid=468)

Yes, he said the next version of CNR would be open source.  My claim is that we have no way of knowing if that is brand new code or not, since the original versions are closed.

---

### Post by aysiu on 2007-05-22
> **Adamant1988 said:**
> Yes, he said the next version of CNR would be open source.  My claim is that we have no way of knowing if that is brand new code or not, since the original versions are closed.
Well, if the functionality is different, the code probably is too. Only time will tell.

I don't know if there's a point in arguing about this. Good or bad, CNR is going to be ported to Ubuntu. Good or bad (and whether CNR works will with apt or not), we are going to get more support requests because of CNR (anything new brings new support requests).

The best you can do is not use if you don't like it, not recommend it if you know it breaks systems, and not support people if you don't want to.

You can't stop the juggernaut!

---

### Post by Adamant1988 on 2007-05-22
> **aysiu said:**
> Well, if the functionality is different, the code probably is too. Only time will tell.

I don't know if there's a point in arguing about this. Good or bad, CNR is going to be ported to Ubuntu. Good or bad (and whether CNR works will with apt or not), we are going to get more support requests because of CNR (anything new brings new support requests).

The best you can do is not use if you don't like it, not recommend it if you know it breaks systems, and not support people if you don't want to.

You can't stop the juggernaut!

You make a strong point Aysiu, but I think I would be in the wrong if I didn't tell people "Hey, this can seriously screw up your system".  I'll just sit back and wait, I know I won't be using it.

---

### Post by forrestcupp on 2007-05-22
> **Adamant1988 said:**
> Can you verify that it's of completely different code? Last I checked CNR for Linspire 5-0 was a closed source application, how am I to know you haven't simply opened that up, let the community work on it, and pretty up the interface for the site? 


Well, that's a good point.  But on the other hand, you have no proof that it's not different code.  All we have is what Linspire tells us, and they tell us that they are rewriting it to work on different distros alongside their current packaging systems.  So you have no idea if the new version will break apt.  Do you even know that CNR was the part of Linspire that caused apt to break?

I can understand where you are coming from, but it's possible that it may not be as bad as what you think.

---

### Post by Adamant1988 on 2007-05-22
> **forrestcupp said:**
> Well, that's a good point.  But on the other hand, you have no proof that it's not different code.  All we have is what Linspire tells us, and they tell us that they are rewriting it to work on different distros alongside their current packaging systems.  So you have no idea if the new version will break apt.  **Do you even know that CNR was the part of Linspire that caused apt to break?**

I can understand where you are coming from, but it's possible that it may not be as bad as what you think.

Yes, and my breakage resulted from something as simple as installing Xchat.  After attempting to install xchat with apt (I use the word attempt there for a reason, as it wasn't properly installed either) CNR and apt both failed to function properly.  I was informed that that was not all too uncommon to have happen, and was warned about the dangers of using apt on a Linspire system.

Now, I don't doubt that this situation has improved massively, but I (and others) remain on edge about the oncoming CNR plugin as, and this is straight from a prominent community member's mouth:  "We just don't know if apt can handle it..." 

That is NOT encouraging.

---

### Post by smoker on 2007-05-22
> but I (and others) remain on edge about the oncoming CNR plugin

i think ultimately it is up to the individual whether they use it or not, and scaring people away from something because you have a dislike, or worry, about it, imo isn't the right thing to be doing. i'm sure many people will use and embrace it when it comes, and many may not, but it is up to them to decide!

---

### Post by aysiu on 2007-05-22
I think we have to wait until it comes out.

Sure, you could argue that since CNR has broken apt in the past that you are rightfully suspicious of it continuing to do so, but we won't know for sure until it is released for Ubuntu.

When it is released, however, and if it does start breaking people's systems, you can bet I'll be first in line to tell people, "Don't use CNR!" Of course, it could turn ugly if there are a lot of CNR fanatics (just look at any discussion here of Automatix).

---

### Post by forrestcupp on 2007-05-22
I'll try it out when it's released, and I'll give a full report.  The worst that could happen is that I would have to back up my home directory and reinstall my system.  Between Windows and Linux, I've probably done that a hundred times.  To me the possibility of all of CNR's benefits are worth that risk.

---

### Post by MetalMusicAddict on 2007-05-22
> **Adamant1988 said:**
> You make a strong point Aysiu, but I think I would be in the wrong if I didn't tell people "Hey, this can seriously screw up your system".  I'll just sit back and wait, I know I won't be using it.

I will have more faith in CnR then Automatix. Really. I think your bring overly pessimistic. There's smart guys working on this and I'm sure they will work out the issues, ;)

---

### Post by robertsaron on 2007-05-24
The problem with apt, is it is not user friendly, that is the main problem with linux in general. Ubuntu and some other distros have come a long ways in reworking themselves to become more user friendly with the GUIs. 

I installed freespire for a day, and for a NEWB linux user that is not a bad packet management system. its very simple easy to use. I did not like it personally, but then I am used to adept, and apt-get. The thing  I did like about CNR, was its descriptions of the software and the user ratings. That was great. Which is nice for new users. I used CNR for software research to decide what programs to install then I used apt-get or adept to install them.

---

### Post by hellmet on 2007-05-24
Your username fits you well, Adamant.

---

### Post by saulgoode on 2007-05-24
> **robertsaron said:**
> The problem with apt, is it is not user friendly, that is the main problem with linux in general.

You confuse user-friendly with learning-friendly. Notepad-like text editors are extremely easy to learn but are quite "unfriendly" because they don't have any features.

---

### Post by awakatanka on 2007-05-24
APT and Synaptic/adapt can also break a system, if you shop outside the normal repo's. Same thing can happen for CnR. We have to wait and see, its not good to scare people for something that isn't there yet. 

I have had bad experience with (k)ubuntu in the past, do i need to warn people to use it because it can be trouble to get something working? Bad things that happened in the past are not points to warn people in the future because the product can be changed.

---

### Post by KiwiNZ on 2007-05-24
I used inspire for a period of time to see what it was like so I could advise customers. I used CNR with out any issues . I worked very well.

---

### Post by igknighted on 2007-05-24
> **smoker said:**
> i think ultimately it is up to the individual whether they use it or not, and scaring people away from something because you have a dislike, or worry, about it, imo isn't the right thing to be doing. i'm sure many people will use and embrace it when it comes, and many may not, but it is up to them to decide!

I think people have heard all the propaganda about "CNR" and will flock to it, probably many will wreck their systems, and many will be very angry.  This is a MAJOR change, nothing to be taken lightly.  ANYONE who uses CNR should be aware that there is (until proven otherwise) a fairly substantial risk.

CNR might turn out great.  It might be just what Ubuntu needs.  I am not bashing CNR, I am merely pointing out the need for caution here.  Right now, CNR has a very poor track record.  And just because it is coming to Ubuntu doesn't mean that will change.  It has to earn the respect.  I strongly believe that we as a community should NOT recommend it for any production machines until it proves that it is beyond these issues and not take anything for granted.  As has been said, time will tell.

> APT and Synaptic/adapt can also break a system, if you shop outside the normal repo's. Same thing can happen for CnR. We have to wait and see, its not good to scare people for something that isn't there yet.

I have had bad experience with (k)ubuntu in the past, do i need to warn people to use it because it can be trouble to get something working? Bad things that happened in the past are not points to warn people in the future because the product can be changed.

YES!  You should warn people!  Don't say that they are bad and suck and blah blah blah, but tell them I did this, and then this and this other thing broke.  It's important information.  CNR is no different.  Think about it like this.  The Chrysler/Dodge/Plymouth minivans in the late 90's and early 00's were notorious for having really poor transmissions.  Then they did a remake of the design.  Would you tell your buddy who wants to buy one what happened with your transmission still?  I would.  It's due caution.  So its not something to freak out about, but everyone should be aware of CNRs track record and the issues it had in the past so they are aware of the risks involved.

---

### Post by aysiu on 2007-05-30
Does this diagram make sense to anyone? I don't know what all the arrows mean.

I got it off the CNR.com website.

---

### Post by starcraft.man on 2007-05-30
> **aysiu said:**
> Does this diagram make sense to anyone? I don't know what all the arrows mean.

I got it off the CNR.com website.

Ok... I'm no expert but I believe the gist of it is that "CNR Warehouse" represents their giant repos/servers. They are updated (download and loaded with) with 3rd party software and open source/linspire apps on their side, and also sync with the Ubuntu repositories (which are updated with open source software and other third party apps). Thusly, the giant  "warehouse" has a lot of apps both from Ubuntu official repos and their own, and then you use CRN plugin and can select what you want to install OR still use apt and get access to regular ubuntu apps.

I'm not sure what blue arrows mean... maybe go to cnr website from desktop/labtop and install the cnr plugin?

Did I get it right? Do I get a prize if I did? If not, feel free to correct me... I am after all, only a lowly Zealot in the great army of Aiur :D.

---

### Post by GSF1200S on 2007-05-31
> **aysiu said:**
> Well, if the functionality is different, the code probably is too. Only time will tell.

I don't know if there's a point in arguing about this. Good or bad, CNR is going to be ported to Ubuntu. Good or bad (and whether CNR works will with apt or not), we are going to get more support requests because of CNR (anything new brings new support requests).

The best you can do is not use if you don't like it, not recommend it if you know it breaks systems, and not support people if you don't want to.

You can't stop the juggernaut!

Not only do I have concerns with it breaking things, but I also dont like the idea of proprietary software making its way into Ubuntu.. Seeing a price listed in an Ubuntu package manager just scares me. While I would stick to apt, I dont necessarily scorn the use of CNR. 

I cant say WHY Adament is worried about breakage, but I know why I do: Ubuntu is a very easy to use, fairly cutting edge, and very stable Linux OS that gets better with the more support it receives. If this CNR crap starts causing massive stability issues, people may be immediately turned off by what they perceive to be a buggy and proprietary operating system. Its so easy to try and use other great Linux OSes, im afraid these issues will diminish the strength of the community, which IMO is one of greatest strengths of Ubuntu...

---

### Post by aysiu on 2007-05-31
You *may* have a point, but Ubuntu isn't exactly rock solid right now anyway, *and* there are plenty of proprietary applications that have already been ported to Ubuntu (check out the entire Multiverse repository).

---

### Post by mozetti on 2007-05-31
> **starcraft.man said:**
> Did I get it right? Do I get a prize if I did? If not, feel free to correct me... I am after all, only a lowly Zealot in the great army of Aiur :D.

Here's your cookie! That's the way I read it, too.

Both (a)Linspire and (b)Ubuntu use OSS & 3rd Party Software as sources, using clearinghouse functions, called (a) publishing and (b) release management, to populate their (a) CNR warehouse and (b) repository. The (a) CNR warehouse and (b) repository synchronize daily.

Ubuntu users use the (a) CNR plugin to get software from the (a) CNR warehouse like they use (b) aptitude/apt-get to obtain software from the (b) repository. To FIND the software in the (a) CNR warehouse, Ubuntu users go to (a) CNR.com.

That enough (a)'s and (b)'s for ya? :D

---

### Post by sloggerkhan on 2007-05-31
[http://www.cnr.com/screenshots.html](http://www.cnr.com/screenshots.html)

I don't really like the look... 
Doesn't really look.... efficient...?

Hmm.

---

### Post by GSF1200S on 2007-05-31
> **aysiu said:**
> You *may* have a point, but Ubuntu isn't exactly rock solid right now anyway, *and* there are plenty of proprietary applications that have already been ported to Ubuntu (check out the entire Multiverse repository).

I see what youre saying. The multiverse may be propietary, but you dont pay $ to use it. Im just a little concerned with the possibility of $ rolling across Ubuntu screens.

Granted, im running Kubuntu currently (off KDE core thanks to your post), but what stability issues are you talking about? You said Ubuntu isnt rock solid right now, but aside from minor application issues, its been DEAD reliable for me? As far as I know Kubuntu is supposedly SLIGHTLY less stable than Ubuntu. Besides, from what Ive seen and experienced, Feisty Fawn is a very good release for Ubuntu...

**I feel the need to mention that this is what Ive heard. Ive heard its as a result of KDE being C++ based while GNOME is GTK+. This of course is not to say Kubuntu's kernel is any less stable than Ubuntu's as theyre the same, just the DE itself. I dont want to throw any FUD, so if im wrong on this, feel free to throw some details in. Most threads on this seem to be larglely opinion and nothing more...

---

