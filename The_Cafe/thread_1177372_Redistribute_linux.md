---
title: "Redistribute linux"
date: 2009-06-03
forum: The Cafe
---

### Post by imalloch on 2009-06-03
Hi all 
Im quite new to Linux been using ubuntu for a two years, I have a question about redistributing ubuntu with a few changes, my idea it to take ubuntu netbook remix change the look a bit and add a few apps, call it something else base round a soccer theme (football. outside the usa). My thinking is kids would like to have there favourate team colors on there desktop, they are a lot more experimental than adults.
Am I ok doing this in Linux/ubuntu ? Or do I have to compile Linux myself from scratch? Sorry I’m new to all this not to sure how the Linux community works.
:?

---

### Post by monsterstack on 2009-06-03
You can go right ahead and do that. Theming can be a bit tricky if you want to get into the nitty gritty tweaking, but totally possible. You don't have to use your own repositories, either. "Crunchbang Linux", for instance, is a version of Ubuntu that has been tweaked and modified to not only look different but behave differently. Still, its users benefit from being able to install the same Ubuntu software and get the same Ubuntu updates.

A great place to start is by installing Remastersys and Gnome Art Manager. The Art Manager is in the repositories, and follow the steps [here]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html") [ubuntugeek.com] to install remastersys.

Then, on a clean install, go right ahead and theme your computer, install the applications you want, remove the ones you hate, and fire up remastersys. It'll build you a custom live-cd with all your settings intact. The link I gave has a few examples of how to use remastersys, and I think there are Howtos on the forums somewhere. Once you've made your own custom Ubuntu flavour, you can go right ahead and burn as many discs as you want, and give them to all your friends.

---

### Post by imalloch on 2009-06-03
I Was thinking more of redistributing over the internet, Is this still ok?

---

### Post by Sealbhach on 2009-06-03
> **imalloch said:**
> I Was thinking more of redistributing over the internet, Is this still ok?

If I were you I would contact Canonical or even Debian before doing something like that. Under the terms of the GPL you would have to make the source code available, even if it's just a few design changes without any new code added.


.

---

### Post by Viva on 2009-06-03
You don't really need to worry about the licensing issues

---

### Post by aysiu on 2009-06-03
As long as you don't call it *SoccerBuntu* or *Ubuntu, Soccer Edition*, then you should be fine.

According to [Ubuntu's trademark policy](http://www.ubuntu.com/aboutus/trademarkpolicy), Ubuntu welcomes people doing their own spins on Ubuntu, as long as they call the spins something like *Ubuntu, Soccer Remix*.

In terms of making the source code available, I'm not sure how one would do that. I did a remix recently (for the HP Mini 1120nr), and I wouldn't know the first thing about what source code to make available. I'm using only applications available through the repositories. If some are GPL'ed, can't you get the source from the package maintainer? If others aren't but are still distributable, then the source can't really be made available anyway, right?

---

### Post by mofrikaantje on 2009-06-03
Be careful adding your own applications however: not all software is free to distribute as you like... When you go to "Add/Remove Software", the option "All Open Source Software" gives you a list of (not all!) software you can freely distribute. Good luck with your project :)

---

### Post by koenn on 2009-06-03
> **aysiu said:**
> 
In terms of making the source code available, I'm not sure how one would do that. I did a remix recently (for the HP Mini 1120nr), and I wouldn't know the first thing about what source code to make available. I'm using only applications available through the repositories. If some are GPL'ed, can't you get the source from the package maintainer? If others aren't but are still distributable, then the source can't really be made available anyway, right?
If you're distributing this remix, your (re-)distributing or 'conveying' binaries, for which you should make available the source code in one of the ways that are acceptible under the license. That's for the GPL software.
Other licenses may have similar requirements.

If you are offering iso images for download or hand out CD's, the following may be suitable :

> # d) Convey the object code by offering access from a designated place (gratis or for a charge), and offer equivalent access to the Corresponding Source in the same way through the same place at no further charge. You need not require recipients to copy the Corresponding Source along with the object code. If the place to copy the object code is a network server, the Corresponding Source may be on a different server (operated by you or a third party) that supports equivalent copying facilities, provided you maintain clear directions next to the object code saying where to find the Corresponding Source. Regardless of what server hosts the Corresponding Source, you remain obligated to ensure that it is available for as long as needed to satisfy these requirements.
> # e) Convey the object code using peer-to-peer transmission, provided you inform other peers where the object code and Corresponding Source of the work are being offered to the general public at no charge under subsection 6d.
You probably also need to include a copy of the GPL on your CD's

[http://www.gnu.org/licenses/gpl-3.0.html](http://www.gnu.org/licenses/gpl-3.0.html)

---

### Post by aysiu on 2009-06-03
> **koenn said:**
> If you're distributing this remix, your (re-)distributing or 'conveying' binaries, for which you should make available the source code in one of the ways that are acceptible under the license. That's for the GPL software.
Other licenses may have similar requirements.

If you are offering iso images for download or hand out CD's, the following may be suitable :



You probably also need to include a copy of the GPL on your CD's

[http://www.gnu.org/licenses/gpl-3.0.html](http://www.gnu.org/licenses/gpl-3.0.html)
But if a copy of the GPL is supposed to be on the CD, and the CD is just a remastered version of Ubuntu, wouldn't Ubuntu have already put a copy on there? (I certainly didn't remove it, if it's there.)

---

### Post by koenn on 2009-06-03
> **aysiu said:**
> But if a copy of the GPL is supposed to be on the CD, and the CD is just a remastered version of Ubuntu, wouldn't Ubuntu have already put a copy on there? (I certainly didn't remove it, if it's there.)
There probably should be a copy of the GPL somewahere on any Ubuntu install CD. However, if your remastering a an installed system into an iso image, the question is : is there a copy of the license somewhere in the installed system's directory tree ?


EDIT:
found them:
```
:~$ ls /usr/share/common-licenses/
Artistic  GFDL      GPL    GPL-3  LGPL-2    LGPL-3
BSD       GFDL-1.2  GPL-2  LGPL   LGPL-2.1

```

---

### Post by aysiu on 2009-06-03
Okay. And my point is that I haven't removed them. So if Ubuntu had to put them there, they're there. If Ubuntu didn't have to, then I don't have to either (I'm sure their legal team is much better than mine).

You seem to have demonstrated that the GPL license is /usr/share/common-licenses/, so if I don't remove that directory, I should be good, I think.

---

### Post by imalloch on 2009-06-03
Okay i have just one more question, is advertising on the website deemed as commercial use? Some Linux distros have Google ads and such on there websites to try and make some money back i assume, i do not intend to sell the distribution

---

### Post by aysiu on 2009-06-03
> **imalloch said:**
> Okay i have just one more question, is advertising on the website deemed as commercial use? Some Linux distros have Google ads and such on there websites to try and make some money back i assume, i do not intend to sell the distribution
The GPL allows for selling of software:
[http://www.gnu.org/philosophy/selling.html](http://www.gnu.org/philosophy/selling.html)

---

### Post by Viva on 2009-06-03
Nah, you won't have any problem with advertising. You're even allowed to sell it as far as I'm aware.

---

### Post by koenn on 2009-06-03
> **aysiu said:**
> 
You seem to have demonstrated that the GPL license is /usr/share/common-licenses/, so if I don't remove that directory, I should be good, I think.
sounds about right. 

You sound a bit defensive about my mentioning this copy of the GPL. I was merely pointing out the GPL's requirements for distributing binaries :
- have source code available in one of the prescribed ways
- include a copy of the license
It's up to you to see how you meet them.

---

### Post by imalloch on 2009-06-03
Thanks to all, you have been very helpful :D

---

### Post by aysiu on 2009-06-03
> **koenn said:**
> sounds about right. 

You sound a bit defensive about my mentioning this copy of the GPL. I was merely pointing out the GPL's requirements for distributing binaries :
- have source code available in one of the prescribed ways
- include a copy of the license
It's up to you to see how you meet them.
Sorry for coming off as defensive. I just want to make sure I'm doing the right things legally. But I also don't want to go overboard and do more than I have to.

---

### Post by mofrikaantje on 2009-06-03
> **imalloch said:**
> Thanks to all, you have been very helpful :D

Keep us updated of your project!

---

### Post by earthpigg on 2009-06-03
he can simply 'make the source code available' by pointing to where it is hosted, no?

since he is already using ubuntu's repos, that means the ubuntu source code repos as well. ubuntu has already taken care of all the GPL requirements for him, as i understand it.

all he needs to do is remove ubuntu branding.

---

### Post by koenn on 2009-06-03
> **earthpigg said:**
> he can simply 'make the source code available' by pointing to where it is hosted, no?

since he is already using ubuntu's repos, that means the ubuntu source code repos as well. ubuntu has already taken care of all the GPL requirements for him, as i understand it.

all he needs to do is remove ubuntu branding.
For GPL programs : 
> Regardless of what server hosts the Corresponding Source, **you** remain obligated to ensure that it is available for as long as needed to satisfy these requirements
The obligation is to the person distributing the software, and relying on a 3rd party such as the Ubuntu repo's doesn't change that obligation. It dos make things easier.

Also, this only goes for unmodified programs. The OP mentions 'minor modifications"

As others have pointed out, not all software, artwork, ... in Ubuntu is GPL. Other licenses may apply, and may have specific requirements about modifications and redistribution.

---

