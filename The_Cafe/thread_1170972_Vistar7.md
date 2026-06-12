---
title: "Vistar7"
date: 2009-05-26
forum: The Cafe
---

### Post by sandyd on 2009-05-26
Do you think this will encourage more users to come to linux (if a livecd of this was created)

and is there any way of making this my default look instead of having to use the new account?

could someone set up a permanent direct link to the file? 40-50 kb isn't all that fast...

[http://www.kde-look.org/content/show.php/V...?content=104232](http://www.kde-look.org/content/show.php/V...?content=104232)

---

### Post by Deamos on 2009-05-26
> **carlee said:**
> Do you think this will encourage more users to come to linux (if a livecd of this was created)

and is there any way of making this my default look instead of having to use the new account?

could someone set up a permanent direct link to the file? 40-50 kb isn't all that fast...

[http://www.kde-look.org/content/show.php/V...?content=104232](http://www.kde-look.org/content/show.php/V...?content=104232)

I don't know if this will encourage more users, however that looks pretty bloody good.

---

### Post by hanzomon4 on 2009-05-26
Well it's just a theme and some settings so I guess you could just copy all the settings are rename the Vistar account. But to answer you question.. No, Linux is not windows and having a look a like would just confuse people when it doesn't behave like Windows.

---

### Post by Sublime Porte on 2009-05-26
Why would Windows users want something that looks like Windows, smells like Windows, sounds like Windows, but can't run Windows apps? That would be believing the nonsense that people use Windows merely because of the 'familiar interface'.

It seems to have features people often change (ie. the look and feel) in Windows anyway, yet not the one feature almost all users stay addicted to Windows for, the applications written for it.

---

### Post by monsterstack on 2009-05-26
> **Sublime Porte said:**
> Why would Windows users want something that looks like Windows, smells like Windows, sounds like Windows, but can't run Windows apps? That would be believing the nonsense that people use Windows merely because of the 'familiar interface'.

It seems to have features people often change (ie. the look and feel) in Windows anyway, yet not the one feature almost all users stay addicted to Windows for, the applications written for it.

I find it weird too. If you want Windows, install Windows. It's not as if Windows users try to make XP or Vista look more like Ubuntu [WAIT WHAT]("http://techpp.com/2009/02/13/ultimate-collection-ubuntu-themes-visual-styles-for-windows-xp-vista/")? [techpp.com]. All we can learn from this is some people just don't know *what* they want.

---

### Post by mamamia88 on 2009-05-26
i'm gonna say no but if you created that them way to go sir looks brilliant

---

### Post by pwnst*r on 2009-05-26
that's a great looking theme, but only for someone that just uses linux and/or XP.  definitely not for a new user as others have mentioned.

---

### Post by monsterstack on 2009-05-26
Oh right, yeah, to answer your original query, you might be able to do it by tinkering with the *install.sh* file. I can't get bittorrent where I am so I can't look at it for you. Perhaps you should attach that file to one of your posts so we can see what needs to be changed.

---

### Post by sandyd on 2009-05-27
heres install.sh

---

### Post by monsterstack on 2009-05-27
Well it looks to me that the only bit in the *install.sh* file that needs to be changed is this bit:

```
echo "Creating user."
useradd -m $NEWUSERNAME -s /bin/bash && \
echo "User created. Enter password for new user."
passwd $NEWUSERNAME
```

Which needs to be commented out. And then this bit:

```
NEWUSERNAME="_vistar7_"
```

Which you should change to your current username. Just to be on the safe side, create a new user manually and test it out there in case I've missed something from the script that could ruin your computer!

---

### Post by Dark Aspect on 2009-05-27
> **Sublime Porte said:**
> Why would Windows users want something that looks like Windows, smells like Windows, sounds like Windows, but can't run Windows apps? That would be believing the nonsense that people use Windows merely because of the 'familiar interface'.

Well considering that most programs have a Linux equivalent and Linux is free, doesn't that mean that most people do in fact use windows for the familiar interface?

[Linux software equivalent to Windows Software]("http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software")

---

### Post by Paqman on 2009-05-27
Not wanting to be a party pooper, but those icons look awfully like the ones in Windows. I hope you haven't ripped off any copyright material to make this theme.

---

### Post by DeadSuperHero on 2009-05-28
I personally like the idea.

Oh gosh...this could be the basis for the next "Mojave" project, they'll just put a theme on a Linux distribution with almost no actual apps.

"Guys, look how fast it is! Goodness!"

---

### Post by monsterstack on 2009-05-28
> **Mr. Psychopath said:**
> I personally like the idea.

Oh gosh...this could be the basis for the next "Mojave" project, they'll just put a theme on a Linux distribution with almost no actual apps.

"Guys, look how fast it is! Goodness!"

Yeah. They could call it Longhorn.

---

### Post by sandyd on 2009-05-28
> **monsterstack said:**
> Well it looks to me that the only bit in the *install.sh* file that needs to be changed is this bit:

```
echo "Creating user."
useradd -m $NEWUSERNAME -s /bin/bash && \
echo "User created. Enter password for new user."
passwd $NEWUSERNAME
```

Which needs to be commented out. And then this bit:

```
NEWUSERNAME="_vistar7_"
```

Which you should change to your current username. Just to be on the safe side, create a new user manually and test it out there in case I've missed something from the script that could ruin your computer!

Thanks!

---

### Post by SomeGuyDude on 2009-05-28
I find it hilarious that there's all this anger against Vista-clone themes, but "Mac4Lin" is a well-supported project that no one around here complains about.

---

### Post by Dark Aspect on 2009-05-28
> **SomeGuyDude said:**
> I find it hilarious that there's all this anger against Vista-clone themes, but "Mac4Lin" is a well-supported project that no one around here complains about.

Maybe its because Vista sucks more than Mac OSX, which I think pretty low of both operating systems really.

---

### Post by monsterstack on 2009-05-28
> **carlee said:**
> Thanks!

No problem. Just consider yourself lucky it wasn't too complicated for me.

---

### Post by DeadSuperHero on 2009-05-28
> **Dark Aspect said:**
> Maybe its because Vista sucks more than Mac OSX, which I think pretty low of both operating systems really.
I think the real tragedy here is the lack of high-quality original themes. There's only a small handful compared to the plethora of Aero, Luna, and Aqua clones. I understand that theming can be difficult and take lots of practice, but there really ought to be more of a rallying for original themes that adhere to either Oxygen standards, Tango guidelines, or something completely different altogether.

---

### Post by Delever on 2009-05-28
> **monsterstack said:**
> It's not as if Windows users try to make XP or Vista look more like Ubuntu [WAIT WHAT]("http://techpp.com/2009/02/13/ultimate-collection-ubuntu-themes-visual-styles-for-windows-xp-vista/")?

This is just brilliant :)

---

### Post by jjpcexpert on 2010-03-02
Could I run it on the OCT 2009 system (waiting for APR 2010 system :) ) or do I have to use the APR 2009 system?

---

### Post by swoll1980 on 2010-03-02
I think it creates a false sense of security. If it looks like Winders, people will expect it to act like Winders.

---

### Post by DubyBreaks on 2010-03-02
> **swoll1980 said:**
> I think it creates a false sense of security. If it looks like Winders, people will expect it to act like Winders.

wouldn't that be a false sense of ***insecurity***? :lolflag:

---

### Post by MuTz777 on 2010-07-08
> **Sublime Porte said:**
> Why would Windows users want something that looks like Windows, smells like Windows, sounds like Windows, but can't run Windows apps? That would be believing the nonsense that people use Windows merely because of the 'familiar interface'.

It seems to have features people often change (ie. the look and feel) in Windows anyway, yet not the one feature almost all users stay addicted to Windows for, the applications written for it.

Use WineHQ, it allows you to run windows applications in ubuntu!
Or if you have the money, you can purchase CrossOver the commercial, bug-free version of WineHQ...:)

---

### Post by Legendary_Bibo on 2010-07-08
> **MuTz777 said:**
> Use WineHQ, it allows you to run windows applications in ubuntu!
Or if you have the money, you can purchase CrossOver the commercial, bug-free version of WineHQ...:)
...which also works just as well

---

### Post by fatality_uk on 2010-07-08
> **swoll1980 said:**
> I think it creates a false sense of security. If it looks like Winders, people will expect it to act like Winders.

This!

---

### Post by Lucradia on 2010-07-08
> **monsterstack said:**
> Well it looks to me that the only bit in the *install.sh* file that needs to be changed is this bit:

```
echo "Creating user."
useradd -m $NEWUSERNAME -s /bin/bash && \
echo "User created. Enter password for new user."
passwd $NEWUSERNAME
```

Which needs to be commented out. And then this bit:

```
NEWUSERNAME="_vistar7_"
```

Which you should change to your current username. Just to be on the safe side, create a new user manually and test it out there in case I've missed something from the script that could ruin your computer!

Too bad "new users" would never do that.

---

### Post by Frogs Hair on 2010-07-08
I'm not sure why someone would create a theme like this for Linux . When I want or need  to use Windows I just boot it . Of all the possible things that can be done with the Linux theme this is not an option for me.

---

### Post by cascade9 on 2010-07-08
That theme is just u-g-l-y IMO. 

> **SomeGuyDude said:**
> I find it hilarious that there's all this anger against Vista-clone themes, but "Mac4Lin" is a well-supported project that no one around here complains about.

Mac4Lin is u-g-l-y as well. Feel better now? :) 

(BTW, that coming from someone who used a fairly 'mac-ish' brushed metal theme on winXP for years)

---

### Post by BrokenKingpin on 2010-07-08
The last thing I want on a Linux box is something that reminds me of Windows. I came to Linux because I hated Windows.

---

