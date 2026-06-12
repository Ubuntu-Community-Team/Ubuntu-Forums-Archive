---
title: "[IDEA] Distinguish between native Gnome, KDE, etc. apps in 'Add/Remove Programs'"
date: 2007-10-23
forum: Ubuntu Brainstorm
---

### Post by teasum on 2007-10-23
I know that there is no problem running KDE apps in Gnome, and vice-versa.

That being said, I would like the desktop application installer (Add/Remove Programs) to be able to filter based on their integration.  In other words, each application listing comes with a handy couple of icons that indicate whether or not the program is well-integrated into gnome or kde.  I would like to be able to filter according to those icons from the pull-down menu at the top. 

I know others have argued that this would discourage people from trying KDE apps in Ubuntu, and give the false impression that they were somehow incompatible.  I argue, however, that a) this is the default behavior in Adept, KDE's desktop app installer, and b) this would only offer easier searching and filtering of applications for those who already know they do or do not want gnome or kde apps installed.  (This was raised in the Gutsy idea pool some months ago.)

Thanks!

---

### Post by smartboyathome on 2007-10-23
I would say a better way to work around this is to _try_ to build a tool which "integrates" QT apps into GNOME (like qt-gtk). This way, there are no worries. Unless you don't mean they "look" integrated?

---

### Post by screaminj3sus on 2007-10-23
KDE tries to do this already, I wish gnome would too, KDE has a GTK QT theme to try and make apps look better. This is definately something gnome should do.

---

### Post by rsambuca on 2007-10-23
I actually think this would be a great benefit to users of older machines.  Many don't realize that the mixed libraries on old hardware can substantially slow things down.

---

### Post by raul_ on 2007-10-23
Pretty mucj every KDE app has a "k" on it, so you can start there

---

### Post by exile on 2007-10-23
Doesn't it already say in the app description in Add/Remove something like "This works well  in gnome desktops"?

---

### Post by whitewizardcoder on 2007-10-23
> **exile said:**
> Doesn't it already say in the app description in Add/Remove something like "This works well  in gnome desktops"?

Yes, but it's not really that prominent and you can't display only gnome or kde apps.  Perhaps a dropdown list/collection of checkboxes that give the user the option to display all programs, gnome-friendly apps, and kde-friendly apps.

---

### Post by teasum on 2007-11-03
Just to clarify a few points from my original post:

> **smartboyathome said:**
> I would say a better way to work around this is to _try_ to build a tool which "integrates" QT apps into GNOME (like qt-gtk). This way, there are no worries. Unless you don't mean they "look" integrated?

Although looks are important, and I support this idea, I was more concerned about those who want to stick to only Gnome apps, for example.

Also, I got this idea from the package manager in Kubuntu, which has a filter option to display only KDE or only Gnome apps.  

> **whitewizardcoder said:**
> Yes, but it's not really that prominent and you can't display only gnome or kde apps.  Perhaps a dropdown list/collection of checkboxes that give the user the option to display all programs, gnome-friendly apps, and kde-friendly apps.

I love the idea of a simple pull-down menu or a few checkboxes that would filter the display in this way, especially if they used the icons used in the package descriptions (i.e. the little heart, the Gnome foot, etc. etc.).

---

### Post by amiga_os on 2007-11-03
There was a blueprint on launchpad to think about how to flesh out add/remove programs... I'm scouring Launchpad now to find it.  More search fields was one of the ideas mentioned, though I don't remember choosing the compatible desktop environment (or rather base widget set) being one of them

If I do, I'll post a link to this thread.  But your best bet is still a comment on that.

(it may even be in a bug report)

---

### Post by teasum on 2007-11-04
> **amiga_os said:**
> There was a blueprint on launchpad to think about how to flesh out add/remove programs... I'm scouring Launchpad now to find it.  More search fields was one of the ideas mentioned, though I don't remember choosing the compatible desktop environment (or rather base widget set) being one of them

If I do, I'll post a link to this thread.  But your best bet is still a comment on that.

(it may even be in a bug report)

Thanks for the information.  I'm just observant enough to notice things I think can be improved, but not savvy enough to know what to do about it--your post will help me fill the gap!  Thanks again.

---

### Post by BungaMan on 2007-11-06
Beginners don't know much about KDE or Gnome.  

Better is to have the applications apply the desktop manager's theme so that a KDE looks like a gnome app in gnome and a gnome app looks like a kde app in kde.  I can't be lieve this hasn't been standardized between the different environments yet.

---

### Post by whitewizardcoder on 2007-11-06
> **BungaMan said:**
> Beginners don't know much about KDE or Gnome.  

Better is to have the applications apply the desktop manager's theme so that a KDE looks like a gnome app in gnome and a gnome app looks like a kde app in kde.  I can't be lieve this hasn't been standardized between the different environments yet.

The problem isn't necessarily the theme of the application, it's all of the libraries that the program needs to install to be able to run.  KDE apps require certain KDE libraries, and Gnome apps require Gnome libraries, which is why some people are hesitant to install apps from a different environment.  These extra libraries take up more disk space and can use more system resources.

---

### Post by teasum on 2007-11-07
> **BungaMan said:**
> Beginners don't know much about KDE or Gnome.  

Better is to have the applications apply the desktop manager's theme so that a KDE looks like a gnome app in gnome and a gnome app looks like a kde app in kde.  I can't be lieve this hasn't been standardized between the different environments yet.

I agree with the response #12, that the issue isn't the look of the programs (or at least not ONLY the look--some people care about that), but more so the libraries.  Still, I second the call, quoted above, for standardization between the two environments, though I don't know how feasible or desirable that is for those behind either KDE or Gnome.

Back to the original issue: although many beginners might not know the difference between KDE and Gnome, I don't see why that would preclude the inclusion of a filter in the desktop application installer.  The distinctions are already made and indicated by icons in the program descriptions.  And finally, to repeat a point from an earlier post, this feature is already available in the application installer for Kubuntu.

---

### Post by coolen on 2007-11-08
I think this is a good idea. KDE libraries stick around in my system long after I close the last KDE application. Not a big deal on my machine, but on older hardware, it'd be an issue.

---

### Post by sicofante on 2008-01-12
I've heard somewhere that Add/Remove will be improved for Hardy. I'd like to suggest that it allows to filter out apps based on the desired Desktop Environment. In other words: allow the user to choose Gnome-only or KDE-only apps.

I know KDE apps will work in Gnome and viceversa, but for some (like myself) user interaction consistency is a must and installing KDE apps in Gnome breaks that consistency.

Sometimes is hard to tell if an app is designed for the KDE or the Gnome desktop (using Qt or GTK). Allowing the user to see only Gnome apps (or only KDE apps for Kubuntu users) would be helpful.

---

### Post by smartboyathome on 2008-01-13
I think this has been said before, and it wouldn't make sense to a new person, who would say "what is gnome and what is kde? why is it important to filter it?".

---

### Post by sicofante on 2008-01-13
Oh, nice that it has been said before. I'm insisting then. It would make sense to all the people that are concerned about keeping UI consistency. Besides, we better start explaining what Gnome and KDE are and their differences, or newcomers will start asking "why are all those apps looking so horribly different...?"

---

### Post by k99goran on 2008-01-13
Couldn't you have the DE shown in the list.
Example:
Now you have "Application" and "Popularity".
Couldn't you have "Application", "Popularity" and "Desktop Environment"?

---

### Post by sicofante on 2008-01-13
I see threads have been merged. Having read it all now, I want to insist that it's not just about the looks. KDE apps have a different file browser, a different philosophy and they make the UI inconsistent between apps. This is against elementary good user interaction design. That's my main reason for staying away from KDE apps as much as possible and that's why filtering KDE aps out of Add/Remove is a good option.

---

### Post by mangar on 2008-01-13
[http://www.metatheme.org/](http://www.metatheme.org/)
mostly complete, but stale for the last 3 years

---

### Post by MaX on 2008-01-13
Well, Sometimes I try KDE when something fun happens there, and I don't want it to "polute" my Gnome menus.

That said I don't want gnome to polute my KDE menus either.
I'd want an option only to show Native KDE stuff in KDE and Native Gnome stuff in Gnome, I know I can hack ALL of the .desktop files to add ShowOnlyInKDE=True (or words to that effect) but that's a pain in the...

---

### Post by smartboyathome on 2008-01-13
> **MaX said:**
> Well, Sometimes I try KDE when something fun happens there, and I don't want it to "polute" my Gnome menus.

That said I don't want gnome to polute my KDE menus either.
I'd want an option only to show Native KDE stuff in KDE and Native Gnome stuff in Gnome, I know I can hack ALL of the .desktop files to add ShowOnlyInKDE=True (or words to that effect) but that's a pain in the...

That would make it a hassle though to those of us that use some KDE apps in GNOME (I do).

---

### Post by MaX on 2008-01-15
> **smartboyathome said:**
> That would make it a hassle though to those of us that use some KDE apps in GNOME (I do).

Well I do want it as an option... I used Amarok in GNOME too but then I could have choosen to show only Amarok.

---

### Post by smartboyathome on 2008-01-15
This is starting to sound complicated. Showing only *certain* apps from a DE? What if someone came from Windows, didn't find Amarok, asked why it wasn't there, and people said "you have to use this to make it visible". They would obviously be confused as to why it is like this.

---

### Post by sicofante on 2008-01-15
This is not complicated at all. As a matter of fact, the suggestion is so simple that it's amazing it's taking 3 pages to make it clear and understandable (maybe someone *doesn't want* to understand?): 

** Have an option in Add/Remove to show applications intented for Gnome, KDE or both. **

The obvious default status should be "show all apps". Really, smartboyathome, you sometimes love to make it sound difficult when it's straightforward.

---

### Post by MaX on 2008-01-19
Yes, but in the Gnome and or KDE menu I'd like the option to show Gnome, KDE or Both as well.

See, if I have a multi user system, I don't want my fathers and my Gnome menu to be cluttered up by our little brother running KDE.... That's why I want the choice.
Of course the default should be Show applications from both desktops but I want to be able to turn it of, and if I do turn it off I should be able to go into the menu editor and change the value so an individual application shows up in both desktops anyway.

---

### Post by Jay_Bee on 2008-01-19
+1 for the idea of being able to search DE specific applications.

---

### Post by coolen on 2008-01-19
MaX, you may be interested in [this]("http://gtk-apps.org/content/show.php?content=73515"). It creates a KDE sub-menu within the Gnome menu. I tried it once, and it seemed to work rather well.

For your little brother, there's a companion project [here]("http://www.kde-apps.org/content/show.php/K+Menu+Gnome+%28Debian+Package%29?content=31031&PHPSESSID=7174503fbf87271afb790e251f19ef99"), although I'm not sure if they'll coexist well on a single machine.

---

### Post by oomingmak on 2008-01-21
> **BungaMan said:**
> Beginners don't know much about KDE or Gnome.  
Nor do they know much about Proprietary versus Open Source applications, but yet there are still menu options for both of those in Add / Remove.

> **sicofante said:**
> This is not complicated at all. As a matter of fact, the suggestion is so simple that it's amazing it's taking 3 pages to make it clear and understandable (maybe someone *doesn't want* to understand?): 

 Have an option in Add/Remove to show applications intented for Gnome, KDE or both**. **

The obvious **default** status should be "show all apps".

I agree 100% with this.

---

### Post by coolen on 2008-01-21
Maybe someone doesn't want to understand...or maybe, just maybe, someone doesn't think this is a good idea.

---

### Post by sicofante on 2008-01-21
Sure, but it's always better to say so instead of trying to expose imaginary issues.

---

### Post by coolen on 2008-01-22
To simply state one's opposition without justification is the mark of a fool.

---

### Post by Voland on 2008-03-12
Here it is my idea: in "Add/Remove Applications" we can choose  all available applications, all open source and so on. Why cannot we choose soft only for Gnome or only for KDE? If I choose Amarok in Ubuntu, I need to download KDE libraries. This is not suited for everybody. Any agreement/disagreement?
[[IMG]http://brainstorm.ubuntu.com/idea/4336/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/4336/)

---

