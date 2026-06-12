---
title: "First impressions on Ubuntu 12.04"
date: 2012-05-07
forum: Testimonials &amp; Experiences
---

### Post by lads on 2012-05-07
Folks, just share some words [I posted in my blog]("http://attheedgeoftime.blogspot.com/2012/05/first-impressions-on-ubuntu-1204.html").

> The last few months I waited for this new release of Ubuntu with great expectation. The developers and promoting folks from Canonical promised that it would solve the long lasting issues with Sandy Bridge processors. I happen to work with one of these processors since last September at the office and the relationship with the Linux kernel has always been difficult. With Ubuntu 11.04, which still used a version 2 kernel, there were constant CPU freezes, with important costs in time and productivity. Ubuntu 11.10 solved that with a version 3 kernel but at the expense of battery lifetime. Whilst with Ubuntu 11.04 the battery would last over 5 hours, with version 11.10 it wouldn't go much beyond 2 hours. Ubuntu 12.04 was supposed to fix all that and hence I eagerly expected for the 26th of April.

I ended up being out of the country at the date and so I was only able to try the upgrade this past week when I came back to the office. The first difficulty came already to start the upgrade, though all the guides out there in the web would say that checking for new updates at the Update Manager would bring about an option to upgrade, to me it never happened. Thus I downloaded the CD iso from the Ubuntu website and mounted it; again no luck, there is no script or executable in the iso able to start the upgrade. The iso has been lacking this feature for the past few releases, an option that I don't understand that well, forcing you to have an internet connection to upgrade. Browsing the Ubuntu Forum I found out how to start the upgrade from the command line and went from there. For a system that is called by its creators "Linux for human beings", this doesn't look that humane.

The first thing to note is that this was one of the smoothest Ubuntu upgrades I ever had, no applications broken, no loss of usability, no issues with external devices, just the way it should be. All the software I use in daily work remained in perfect order. The last update I had was quite traumatic, with Ubuntu not only deactivating, but completely deleting one of the applications I use the most: Lotus Notes. This forced me to set it up on a Winblows virtual machine, something that certainly helped smoothing the upgrade process.

The first negative impact came with the unexpected change in context menus to light backgrounds. I use the Ambiance colour theme, which these days is the closest you get to a proper dark theme for Ubuntu. The logic of Canonical was that light elements should produce light background menus and dark elements dark menus. Me, I only got light menus. Very annoying. Luckily the folks at OhMyGodUbuntu! promptly provided a fix for this mess up. Though this was quickly solved, it is another unfortunate symptom of the amateurish way Canonical still occasionally treats the user interface. If I use Ambience it is precisely because I prefer the dark backgrounds, why would someone think I would like to change it? And since I'm at it, it is about time that a full dark theme is made natively available again for Ubuntu. This was the case with Gnome 2, but since the change to Unity it doesn't exist any more.

One of te features that has been mostly praised by users and critics in general is the Heads Up Display (HUD), which is basically an extension to the Unity application search mechanism, allowing it to search also among the menus in the foreground application. I like the idea but the fact is that so far I haven't been able to take advantage of it. First of all because I use the keyboard for most stuff, which is far faster than anything else, but mostly because the programme I use the most, Eclipse, doesn't integrate with the HUD. Anyway, this feature puts Unity in the vanguard of usability within window managers for Linux; further integration and development will surely be rewarded.

To me there is another improvement to Unity that has had a larger impact: the new behaviour of the application launcher. Now the launcher remains alawys visible by default, windows that may extend into its space are relegated to the background, without overlapping it. I only use large resolution monitors so the auto-hide behaviour never quite worked for me, most of the time I had to manually increase the size of the windows just to the point where they wouldn't force the launcher to hide. The best thing about this change is that the old behaviour is still available, just by tweaking the configuration, which may be handy for folk that use low resolution displays.

Another much promoted feature of this new release is the inclusion of a Privacy menu in the Configuration Settings. The Unity application search mechanism had been extended to search files in the hard drive by logging the user's recent activity. When typing a keyword for the search Unity shows all the files that may match it, regardless of their relevance or type. This poses obvious security and privacy issues when using the feature in public; it begs the question why hadn't the developers noticed the issue when the search mechanism was extended. To my surprise the Privacy menu was not installed by the upgrade. After inquiring in the Ubuntu Forum I was told that this new menu is included on fresh Ubuntu installs, but not on upgrades, in my view another nonsensical choice. I had to manually install the menu, not much of a problem for me, but once again something that could be daunting to a user not that familiar with Linux.

And so after a few days working with Ubuntu 12.04 on my desk I finally had to use the laptop at a meeting and check the improvement in energy consumption. I was fortunate enough that the meeting didn't last more than 2 hours, the battery barely made it. In effect Ubuntu 12.04 seems to be drying the battery even faster than in version 11.10. What a disappointment. I'm quite puzzled by this and still hope it is just something that didn't went quite well during the upgrade. Colleagues that also had the upgrade are reporting improvements in energy consumption, but on different hardware setups. Sandy bridge processors are not exactly new, I'd expect Kernel developers to be a bit more on the issue. I'm not giving up on the subject yet and during the coming days I'll be hitting the Ubuntu Forum in search of a solution.

Ah well, that's Ubuntu. Part of the magic is the constant development and introduction of new features, there is always some novelty kicking dopamine into your brain. Now and then things don't go that well, but the quest for a solution is also part of the game and I quite enjoy it. Ubuntu isn't perfect, but it is possibly the closest you get to perfection. Unity has come of age the past few months and clearly brings Ubuntu ahead of the remainder Linux field. When using other window managers, like Xfce or Winblows, I can easily get lost and immediately feel a reduction of productivity. Partly due to the light-hearted way in which certain changes are brought about, Ubuntu isn't yet the universal Linux distribution for all ages, from 8 to 88, that Canonical envisions. But once its user base gets over a critical threshold things can happen pretty fast. The move of desktops operating systems into smart-phones might just provide the launch pad for that transition.

---

### Post by BeRoot ReBoot on 2012-05-07
> winblows

Stopped reading. You're a bad person and you should feel bad.

---

### Post by thatguruguy on 2012-05-07
> **lads said:**
> Folks, just share some words [I posted in my blog]("http://attheedgeoftime.blogspot.com/2012/05/first-impressions-on-ubuntu-1204.html").

It seems like you posted ***all*** of the words, rather than just some of them.

---

### Post by CharlesA on 2012-05-07
> **thatguruguy said:**
> It seems like you posted ***all*** of the words, rather than just some of them.
Er yeah.

A summary would have been fine.

---

### Post by billyseth on 2012-05-07
> **BeRoot ReBoot said:**
> Stopped reading. You're a bad person and you should feel bad.

Yeah, I have never really cared for any of those spoof names (windoze, M$).
Do windows users have awesome:rolleyes: names like those for different Linux distros??!

---

### Post by bob-linux-user on 2012-05-07
I was annoyed by the number of things I had to do just to make 12.04 usable.

1) The gnome fallback ssession is not installed by default.
2) I had to remove the bizzare overlay scrollbars.Would have preferred to have been given a choice at installation.
3) The grub menu is set by default at 640*480, which my graphic card did not like so I had to install grub customizer. It is not in the default repositories.
4) The window buttons were strangely on the left so, I had to install MWbuttons to put them back. Again, this very useful programme is not in the repositories.
5) None of the themes looked very good. The least worst was greybird. However the scroll bars are too thin in my view.
6) The themes are not easily customizable like they were in Gnome 2

If Canonical are hoping to win converts from Microsoft Windows they are hardly going the right way about it.

---

### Post by billyseth on 2012-05-07
> **bob-linux-user said:**
> I was annoyed by the number of things I had to do just to make 12.04 usable.
**6) The themes are not easily customizable like they were in Gnome 2**

If Canonical are hoping to win converts from Microsoft Windows they are hardly going the right way about it.

I was pretty surprised about this too, have you come across any way to easily change the colors and other basic options within a theme?

---

### Post by wojox on 2012-05-07
> **billyseth said:**
> 
Do windows users have awesome:rolleyes: names like those for different Linux distros??!

Geeks :P

Sounds more like a testomonial.

---

### Post by CharlesA on 2012-05-07
> **wojox said:**
> Geeks :P

Sounds more like a testomonial.
Maybe.

I do recall something about Ubuntu being for those that cannot install Debian.

Meh, the installers are the same anyway - at least the server and the minimal install ones are.

---

### Post by wojox on 2012-05-07
> **CharlesA said:**
> 
I do recall something about Ubuntu being for those that cannot install Debian.

:p That one always makes me lol.

---

### Post by lads on 2012-05-08
> **CharlesA said:**
> Er yeah.

A summary would have been fine.

This was the first time I linked from this Forum to my blog. Had I posted just a digest it would have been blatant blog-whoring; I feared it could been taken as unpleasant. Next time I'll know, thanks.

---

### Post by lads on 2012-05-08
> **billyseth said:**
> Yeah, I have never really cared for any of those spoof names (windoze, M$).

I read the term **Winblows** for the first in a tutorial on the [Linux directory structure]("http://www.tuxfiles.org/linuxhelp/linuxdir.html"). It is quite funny and pays the right homage to the Microsoft systems I once had to use for work. Luckily I only Ubuntu these days.

---

### Post by 3rdalbum on 2012-05-08
> **bob-linux-user said:**
> I was annoyed by the number of things I had to do just to make 12.04 usable.

1) The gnome fallback ssession is not installed by default.
2) I had to remove the bizzare overlay scrollbars.Would have preferred to have been given a choice at installation.
3) The grub menu is set by default at 640*480, which my graphic card did not like so I had to install grub customizer. It is not in the default repositories.
4) The window buttons were strangely on the left so, I had to install MWbuttons to put them back. Again, this very useful programme is not in the repositories.
5) None of the themes looked very good. The least worst was greybird. However the scroll bars are too thin in my view.
6) The themes are not easily customizable like they were in Gnome 2

If Canonical are hoping to win converts from Microsoft Windows they are hardly going the right way about it.

People looking to switch from Windows don't care if Gnome Fallback is preinstalled; nor do they even care if it's in the repositories. Unity is Ubuntu's face, to a new user, and new users don't even really know that you can install different DEs. Unity is very usable these days; maybe you should try using it?

Ditto for Overlay Scrollbars and window buttons on the left. They've been on the left since 10.04 anyway, most Ubuntu users are used to it now.

I agree about your GRUB problem; if it's known to cause an issue with your graphics card, then it should be set up properly in the first place. I also agree with the themes; a selection of the community's best themes would be a good idea, even though I actually stick with the default Ambiance theme on my computers. The "it's not easy to customise themes" is a purposely-missing feature in Gnome 3, so you're complaining to the wrong people there. In fact, Ubuntu patched-in the ability to change themes; it's missing in default Gnome 3.

Ubuntu changes and you'll have to deal with that. Sorry. But at least you could tweak things to mostly the way you want them. Most of the issues you mention are simply not relevent to new users anyway.

---

### Post by mastablasta on 2012-05-08
> **3rdalbum said:**
> The "it's not easy to customise themes" is a purposely-missing feature in Gnome 3, so you're complaining to the wrong people there. In fact, Ubuntu patched-in the ability to change themes; it's missing in default Gnome 3.
 
 
was about to mention that... it's really a Gnome 3 issue not Ubuntu.
 
for more custumisations i suggest KDE or XFCE if you really must have it. themes need some time to catch up to new DE that Gnome 3 is.

---

### Post by bob-linux-user on 2012-05-08
@Billyseth.

I do not know a way of customizing the colors inside a theme (as we used to do on gnome 2).Sorry.

Bob-linux-user.

---

