---
title: "Nautilus has no global menu. Huge usuability issue and confusing"
date: 2012-08-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by philinux on 2012-08-15
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1037081](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1037081)

If anyone agrees please tick affectse too. Cheers.

---

### Post by mc4man on 2012-08-15
While not the last email I got on this - the last one that referenced this  directly - 

>  09/08/2012 17:05, Michael Terry a écrit :
>
> Picking one of the forks of 3.4 nautilus means that either we are the sole stewards or we will conflict with the existing maintainers over design goals (which sounds a lot like GNOME but with less manpower).
>
> I don't think we have the energies to own a whole file manager.  I vote we just ride along with GNOME on this one and patch it to fit better when running under Unity. 
Hey Michael,

I agree with that mostly, I think we have some issues with 3.6 we need to solve at minimum:
- we need to get our "desktop menu" (the one you get when you are on an empty workspace) back
- we need to get the HUD working back with nautilus (we probably need to figure a solution for all apps using gear-icon-popup-menus)
- we probably want a traditional menubar back, the gear menu and the app menu just doesn't work well in Unity and is different from all our other apps
- I'm not sure what to think about things like the dropping of compact view or extra pane mode...

We at least need to solve the 3 first items and we should have an opinion on the last one.

I see 2 ways for this cycle:
- spend the time to fix those 3 items at minima and figure what to do next at UDS
- upload nautilus 3.4 to the archive, have both for one cycle (they will conflict but that's fine), default to 3.4, discuss what to do next at UDS

The second one is a "safer" option imho, especially if nobody has time to work on fixing the issues listed previously.

Cheers,
Sebastien Bacher 

---

### Post by Stinger on 2012-08-15
I share with you my thoughts about this huge usability issue. 

To Quote myself from another thread:
> The Ubuntu dilemma is that Unity probably will not be compatible with the future Gnome apps that will integrate more and more with Gnome-Shell, and IMHO Unity will break more and more apart, or need to fork all needed Gnome-apps.

The " Ubuntu dilemma " hit Nautilus as the first Gnome app.

And another quote I made earlier on the same thread has the solution:
> The right decision for Ubuntu IMHO is to follow Gnome with one cycle delay, gives more stability.

Else the developers will have to do an awful lot of patching to get Unity up and running.

---

### Post by ronacc on 2012-08-15
for the last couple of cycles , since the start of unity , it has been like watching a slow motion train wreck . It is just a question of when the bulldozers will be called in to bury the smoldering debris .

---

### Post by cariboo on 2012-08-16
> **ronacc said:**
> for the last couple of cycles , since the start of unity , it has been like watching a slow motion train wreck . It is just a question of when the bulldozers will be called in to bury the smoldering debris .

Unity itself works quite well, it's the changes in Gnome, that have made the process a bit of a train wreck, it seems the Gnome devs would rather go their own way, rather than pay attention to what the users are saying. These same changes, also make gnome-shell a bit of a pain to use too.

---

### Post by vexorian on 2012-08-16
Didn't they say they were going to use old nautilus in 12.10? 

If these gear icons for menus are going to become common, then I guess the global menu bar could be updated to use them. But it would still be pretty inconsistent.

---

### Post by mc4man on 2012-08-16
> **cariboo907 said:**
> 
it seems the Gnome devs would rather go their own way, rather than pay attention to what the users are saying. These same changes, also make gnome-shell a bit of a pain to use too.

Sounds quite familiar to what many have/are & will continue to say about Ubuntu

While having 3 menus may be initially somewhat confusing don't see any huge loss of usability (as menus) & I wouldn't be surprised if it changes some more.. 

(- I'd take a gear/toolbar/app menu any day over the Hud

---

### Post by BigSilly on 2012-08-16
> **cariboo907 said:**
> Unity itself works quite well, it's the changes in Gnome, that have made the process a bit of a train wreck, it seems the Gnome devs would rather go their own way, rather than pay attention to what the users are saying. These same changes, also make gnome-shell a bit of a pain to use too.

I totally disagree. Gnome shell works fantastically well, and I'll never really understand why Ubuntu didn't just sync with the Gnome team and just theme up the shell to suit.

---

### Post by Stinger on 2012-08-16
> **cariboo907 said:**
> Unity itself works quite well, it's the changes in Gnome, that have made the process a bit of a train wreck, it seems the Gnome devs would rather go their own way, rather than pay attention to what the users are saying. These same changes, also make gnome-shell a bit of a pain to use too.

The train wreck is a Unity problem entirely.
The Ubuntu developers should have foreseen this scenario when they placed Unity as user interface on top of Gnome3.
You say "These same changes, also make gnome-shell a bit of a pain to use", can you explain what you mean by that ?

---

### Post by Stinger on 2012-08-16
> **BigSilly said:**
> I totally disagree. Gnome shell works fantastically well, and I'll never really understand why Ubuntu didn't just sync with the Gnome team and just theme up the shell to suit.

+1 for that I totally agree !

IMHO Unity should have been made as one or more [Gnome-Shell Extensions ]("https://extensions.gnome.org/"), this would have given the developers more time to actually develop Ubuntu, instead they'll now spend a whole lot of time on either patching the Gnome-apps to match Unity's needs or maintaining forked Gnome-apps because patching just ain't enough.
I won't say the time is wasted but it would have been better spent developing Ubuntu instead.

Another benefit would be that Ubuntu won't rely on compiz anymore :-D

---

### Post by BigSilly on 2012-08-16
Well I didn't mean to send things off topic, so apologies, but I do feel that this sort of problem was inevitable once you step outside of the arena and begin your own forks. Mint will no doubt be feeling the strain too, doubly so now they've decided to fork Nautilus themselves because of the new changes.

I think what confuses me most between Gnome and Ubuntu, is that essentially the goals are the same, are they not? A one size fits all approach to the desktop/tablet area. Like I say, with this in mind, what exactly was the argument again? Unity and Shell are very similar in many ways and aim for the same goals, so why does Canonical suddenly feel the changes being made to Nautilus are not to their taste? Surely it fits their own paradigm?

---

### Post by GreatDanton on 2012-08-16
Stay on the topic guys. This thread is about Nautilus usability issue not discussion about Unity and Gnome shell.

Regards.

---

### Post by BigSilly on 2012-08-16
> **GreatDanton said:**
> Stay on the topic guys. This thread is about Nautilus usability issue not discussion about Unity and Gnome shell.

Regards.

Of course. Again, apologies. I felt the similarity of issues warranted the points.

---

### Post by stinkeye on 2012-08-16
Have nautilus-scripts also been ditched as well?

---

### Post by Stinger on 2012-08-16
> **GreatDanton said:**
> Stay on the topic guys. This thread is about Nautilus usability issue not discussion about Unity and Gnome shell.

Regards.

I beg to differ, I think the reason why Nautilus has no global menu, causing confusion and huge usability issues, is caused by Unity and not Nautilus.
Therefore I mean that the discussion of integration of Nautilus, or lack of the same,in Unity, is highly relevant.

---

### Post by ronacc on 2012-08-16
I agree with stinger . This is part and parcel of the decision to fork away from the mainline development of Gnome in such a radical way . Incompatibilities will inevitably arise ,requiring workarounds that can rapidly build into a house of cards that cannot stand . That is the train wreck I mentioned above .

---

### Post by EgoGratis on 2012-08-16
It's not only Ubuntu that doesn't see GnomeShell as something their target user wants.

And it's not like Gnome folk don't know what Ubuntu is and that it uses Gnome and Unity. Maybe the solution for this problem would be global menu by default in Unity and "local menu" option with menu button.

But for something like that to happen Gnome and Ubuntu folk should plan together and talk months ahead not silly little actions over night and then some folk arguing on forums if Unity or GnomeShell is better. Ubuntu uses Unity on top of Gnome and get over it why waste time arguing over this.

I don't know if folk involved knows this but we are past "hobby time", Linux desktop is starting to gain some traction and folk involved will have to start behave more professionally if they like it or not.

---

### Post by BigSilly on 2012-08-16
Well in my defence I'm not arguing over which is better. I'm simply looking at how similar they are. I'm not disputing Unity or Gnome; I love to use either or, personally, and have both installed.

As you say, I'd love to see them collaborate like the "old days", and have less of the need to fork. I can't see Ubuntu wanting to fork Nautilus in all honesty, even though the Mint team already have. I just hate to see the separated, wasted effort. My concern is this gets harder and harder as time goes on, especially as Gnome is very much on its path now.

---

### Post by EgoGratis on 2012-08-16
Yes if folk involved will work against each other they lose and we lose and everybody else that has nothing to do with Linux on desktop win, because Linux on desktop folk did it again!

---

### Post by vexorian on 2012-08-16
When I compare unity with gnome shell. Gnome shell has some hopes of becoming functional, only after you add 25 extensions. Unity is functional from the start, but can't be customized, that's their main flaw. But to me, unity is the sensible default. 

Believe it or not, most users care about stuff that works out of the box and would rather not tweak their systems. Which is bad to gnome-shell which requires you to spend 20 man-hours looking for the right combination of extensions. Worse, after adding all those extensions to gnome-shell, I noticed it becomes cinnamon... Between cinnamon and unity, gnome-shell really has no reason to exist. It is a project with an "elegant", impractical idea of keeping you going to the same corner every 5 seconds, and spending 2 of those seconds watching animations.

Forks are part of the way FOSS works. Eventually, some of the forks will persist and be merged and other will die. It is survival of the strongest and this will ensure that at the end only the best ideas will remain in the spotlight. That future benefit of course comes at the prize of the difficulty we are facing right now. But, big deal? What's the worst thing that could happen? We will still have less than 1% of users? So what?

Making unity a gnome-shell extension would not have saved Canonical any work to do. Unity is already a compiz extension, so it is not like unity was reimplementing window or desktop management at all. Most of the work canonical spent is in the launcher, the dash and the global menubar. It would have taken canonical the same amount of work to implement them as extensions to gnome-shell or compiz. But as gnome-shell extensions, it would have rendered canonical even more subject to the whims and caprice of gnome's. Every time the gnome-shell version number increases by 0.1 half of the extensions in the extensions site stop working.

---

### Post by Gyokuro on 2012-08-16
The problem is that users and developers are not satisfied with the current form of Gnome or the way the project goes. You have now two forks of Nautilus - Nemo and Marlin and each come with the burden that both projects have to be maintained and tested/used by users and developers - with the result of lower developer output as if you have only one project. All this dissatisfaction lead to more forks and a lot of users/developers go somewhere else - which slow down development of the projects and the spread of Linux on the desktop which is the most bad thing in this case. Sorry to get OT of the Nautilus problem but we have too much forks:

KDE3 - Trinity
Gnome 2 - Mate
Gnome 3 - Cinnamon and somehow Unity 

and the other DE's

XFCE
Gnome3
KDE4

so someone can only wounder how many developers and users switched projects/DE's. It's time to think about what developers and users want and later kill/end at least three of this projects.

---

### Post by vexorian on 2012-08-16
> **Gyokuro said:**
> The problem is that users and developers are not satisfied with the current form of Gnome or the way the project goes. You have now two forks of Nautilus - Nemo and Marlin and each come with the burden that both projects have to be maintained and tested/used by users and developers - with the result of lower developer output as if you have only one project. All this dissatisfaction lead to more forks and a lot of users/developers go somewhere else - which slow down development of the projects and the spread of Linux on the desktop which is the most bad thing in this case. Sorry to get OT of the Nautilus problem but we have too much forks:

KDE3 - Trinity
Gnome 2 - Mate
Gnome 3 - Cinnamon and somehow Unity 

and the other DE's

XFCE
Gnome3
KDE4

so someone can only wounder how many developers and users switched projects/DE's. It's time to think about what developers and users want and later kill/end at least three of this projects.
Too many forks slows down development. But I think that it is better than having fast development towards stuff that does not satisfy your goals. I think that man hours don't really translate to quality. 200 developers might be faster than 5 developers. But if the 5 developers really believe in what they are doing and are really in agreement with the DE's philosophy, they will put a lot more work on it.

The only way to test which philosophy will persist or if there are enough developers to develop each philosophy is to do the forks and test them in the wild. With real users trying them and making opinions of them.

This fork stuff is a crisis - a crisis in its original sense. The gnome world had it very easy before, only having to care about the guys obsessed with the letter K. But now they have to face heavy competition. But thanks to all of this, a philosophy that is developed and polished better and turns out to be better for users will be the result. And that is a good thing.

So, honestly, we can never have too many forks.

---

### Post by Gyokuro on 2012-08-16
> **vexorian said:**
> Too many forks slows down development. But I think that it is better than having fast development towards stuff that does not satisfy your goals. I think that man hours don't really translate to quality. 200 developers might be faster than 5 developers. But if the 5 developers really believe in what they are doing and are really in agreement with the DE's philosophy, they will put a lot more work on it.

The only way to test which philosophy will persist or if there are enough developers to develop each philosophy is to do the forks and test them in the wild. With real users trying them and making opinions of them.

This fork stuff is a crisis - a crisis in its original sense. The gnome world had it very easy before, only having to care about the guys obsessed with the letter K. But now they have to face heavy competition. But thanks to all of this, a philosophy that is developed and polished better and turns out to be better for users will be the result. And that is a good thing.

So, honestly, we can never have too many forks.

+1 - I agree with you that we have somehow a crisis at the desktop front. In the past we had two major DE's: KDE and Gnome but now we have forks of both and that's the shame and I'm not so optimistic about forks as you express but time will tell - as in my experience a lot of code get duplicated (reinventing wheels) over the time, developers give up and the project dies and useful code get not merged. I know it's OT but I think it's better to integrate parts/ideas of Cinnamon in Gnome as Canonicals idea of Unity which is in the end only a clone of Apple's idea of a desktop.

---

### Post by BigSilly on 2012-08-16
> **vexorian said:**
> Too many forks slows down development. But I think that it is better than having fast development towards stuff that does not satisfy your goals. I think that man hours don't really translate to quality. 200 developers might be faster than 5 developers. But if the 5 developers really believe in what they are doing and are really in agreement with the DE's philosophy, they will put a lot more work on it.

The only way to test which philosophy will persist or if there are enough developers to develop each philosophy is to do the forks and test them in the wild. With real users trying them and making opinions of them.

This fork stuff is a crisis - a crisis in its original sense. The gnome world had it very easy before, only having to care about the guys obsessed with the letter K. But now they have to face heavy competition. But thanks to all of this, a philosophy that is developed and polished better and turns out to be better for users will be the result. And that is a good thing.

So, honestly, we can never have too many forks.

I sincerely hope you are right, and I'll try not to worry. :D  There are of course many positives; Cinnamon so far is proving to be amazing as a fork of Gnome Shell, and of course so is Unity. Both projects are unique and have their own directions. I hope they both go from strength to strength.

---

### Post by Mr. Picklesworth on 2012-08-16
> **vexorian said:**
> So, honestly, we can never have too many forks.

The thing that scares me with forks is that it's directing a lot of energy at a redundant effort. I don't think there are enough developers in this space to support six different forks of GNOME in a reliable way. I picture a project, with a codebase the size of Nautilus, running with one core developer. That should chill anyone to the bone. More developers means more people checking each other's code and ideas, and it means a project won't shrivel up and die when someone gets hit by a bus. We need projects with strong developer communities in order to get anywhere. No amount of forking will create that. 

> **BigSilly said:**
> I think what confuses me most between Gnome and Ubuntu, is that essentially the goals are the same, are they not? A one size fits all approach to the desktop/tablet area. Like I say, with this in mind, what exactly was the argument again? Unity and Shell are very similar in many ways and aim for the same goals, so why does Canonical suddenly feel the changes being made to Nautilus are not to their taste? Surely it fits their own paradigm?

What I've noticed is Unity's focus has been, to this point, entirely on Unity itself. The dash is doing more and more of what Software Centre does, for example, and Ubuntu TV seems to be entirely wrapped around the Unity look and feel (which, to be fair, works pretty well in that situation). Outside of the obvious changes to add screen space, I haven't seen any movement for actually making *applications* touch-friendly, for example. (There has been a lot of nice work on touch support at a lower level, though, so perhaps someone, somewhere, is doing something cool?).

GNOME isn't moving especially quickly there, but they have been working with application designs that connect very tightly with their vision for the shell. In addition, their design whiteboards make some [obvious references to touch]("https://live.gnome.org/GnomeOS/Design/Whiteboards/Touchscreen") as a priority throughout the software stack. They obviously really want to move applications forward (in some direction).

On the other hand, Ubuntu seems to be very preoccupied by the Unity shell. I've been assuming the idea is that desktop applications are fine as they are and tablet / touch-friendly apps are completely different beasts, and I think that's perfectly reasonable (while perhaps a smidge unimaginative). So, I don't think GNOME's work with applications fits in the Unity paradigm for the simple reason that I haven't really *seen* a Unity paradigm for applications other than the implied "whatever was normal with GNOME 2." I'd love to be proven wrong.

---

### Post by ronacc on 2012-08-16
although its a bit off topic , I have serious doubts about trying to bring touch to the desktop in any wholesale manner .Even apple who more than anyone has had great success with their touch IOS , is being very careful about integrating IOS features into OSX . We will soon see how much success MS has with windows 8 in touch mode on a real desktop . As one who has actually played with a "touch enabled " desktop I can tell you that the glamor wears off really quickly (about 5 minutes in my case ) .A tablet and a desktop are just too different to live together peacefully .Each has its strong points and weak points and a merger of the 2 is more likely to emphasize the weak points to the point of being a very unhappy marriage .

---

### Post by cariboo on 2012-08-16
I have to agree with ronacc, I can't see using a touch screen on a desktop system without a huge change in the way we use them. A touch screen on a vertical surface is not very comfortable to use for any length of time, and as he said, the novelty wears off fairly quickly

That being said, I'm typing this sitting on my deck, using my Android based tablet, and even typing these two paragraphs is taking quite a bit longer than it would on my desktop system.

---

### Post by Mr. Picklesworth on 2012-08-17
Oh absolutely, there's no way to make a desktop application (as we have them) work on touch without changing that application significantly, and designing something to work on both touch and mouse/keyboard would be quite difficult. However, you can make applications support touch to a *reasonable* extent, and you can also improve your UI toolkit so it's easy for developers to write touch-friendly applications.

I don't find the touch thing especially interesting either (and I don't think anything has it as a main objective yet) so I was really just using that as an example of how these projects differ in their approach. GNOME 3's work with applications isn't really touch focused: it's pretty well your usual refinement of the desktop thing: type to search as a common element, emphasizing content, and encouraging direct manipulation as opposed to toolbars filled with buttons. There are natural benefits for other form factors, too, but they aren't a requirement :)

---

