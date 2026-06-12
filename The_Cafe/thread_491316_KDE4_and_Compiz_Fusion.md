---
title: "KDE4 and Compiz Fusion"
date: 2007-07-03
forum: The Cafe
---

### Post by Raffo on 2007-07-03
KDE devs are doing a great job with the desktop and their new composite engine... but when KDE4 will be released how will it work with compiz? Will compiz be used only with GNOME??

---

### Post by Bachstelze on 2007-07-03
What you need to understand is that the window manager is just one program among others. KWin is KDE's window manager, and it does have some compositing featurs already (even in KDE 3), but you can very well use Compiz instead of it if you wish. It' just like taking your computer, remove the gray case, and put a black one instead. The computer will still work as well as before.

---

### Post by Raffo on 2007-07-03
> **HymnToLife said:**
> What you need to understand is that the window manager is just one program among others. KWin is KDE's window manager, and it does have some compositing featurs already (even in KDE 3), but you can very well use Compiz instead of it if you wish. It' just like taking your computer, remove the gray case, and put a black one instead. The computer will still work as well as before.
I see you thought I'm a noob :D 
I know what a WM is and that KWIN is KDE's WM... My English is so poor, in my mind the meaning of my post was: Why don't spend time supporting officially compiz and integrating it with KDE desktop? You will use compiz under KDE when KDE4 will be released?

Maybe now it's better...maybe not ;)

---

### Post by igknighted on 2007-07-03
> **Raffo said:**
> I see you thought I'm a noob :D 
I know what a WM is and that KWIN is KDE's WM... My English is so poor, in my mind the meaning of my post was: Why don't spend time supporting officially compiz and integrating it with KDE desktop? You will use compiz under KDE when KDE4 will be released?

Maybe now it's better...maybe not ;)

I think you will be pleasantly surprised.  In many ways the window manager for KDE4 will be more advanced than compiz.  The effects will all be able to be turned off 100% so you are not locked into them, but there are some nice ones.  I lost the link I had before, but check out planet KDE for more info.  The effects in KDE4 are not as gaudy as compiz and are more focused on usability, so I doubt you will see a rotating cube, but transparencies, mild wobbly windows and much more will be there.

The problem with compiz (and beryl) is that they cannot exist on their own.  I think that it will forever be in the realm of "testbed" and when things become stable enough the features will be integrated into other WMs.  But I don't think KDE or Gnome will ever make compiz a part of them.

---

### Post by Raffo on 2007-07-03
> **igknighted said:**
> I think you will be pleasantly surprised.  In many ways the window manager for KDE4 will be more advanced than compiz.  The effects will all be able to be turned off 100% so you are not locked into them, but there are some nice ones.  I lost the link I had before, but check out planet KDE for more info.  The effects in KDE4 are not as gaudy as compiz and are more focused on usability, so I doubt you will see a rotating cube, but transparencies, mild wobbly windows and much more will be there.

The problem with compiz (and beryl) is that they cannot exist on their own.  I think that it will forever be in the realm of "testbed" and when things become stable enough the features will be integrated into other WMs.  But I don't think KDE or Gnome will ever make compiz a part of them.
Interesting. I was thinking about compiz integration in KDE (or GNOME) because I see that many famous distros (ubuntu, fedora...) are now offering ways to install and use easily compiz... but maybe this is happening just because lots of people are interested in linux just because of "the wow effect"...

---

### Post by Erunno on 2007-07-03
[Aaron Seigo wrote in the comments:]("http://dot.kde.org/1180541665/")

> - kwin works everywhere (degrades gracefully on less capable hardware), beryl doesn't
 - kwin is a production ready *window* *manager*, which means it has all sorts of window management oddities fixed; take a look at the handling of transients in the code to see just how crazy this is. how lubos maintains his sanity i'll never know ;)
 - kwin has various kde integration features and we can continue to maintain that easily
 - it is easier to add what beryl has on top of the above than it is to add the above to beryl
 - we all share the benefits of what is going into the shared infrastructure (x.org) so it's not all lost efforts
 
 and if you care .. s,beryl,compiz,g

> > Why is it I never experienced those?
 
 they are called "fringe" for a reason. a production window manager that is relied on as heavily as kwin is needs to be solid in all cases. these include all sorts of things such as the handling of certain types of java windows, apps that try to self-manage their windows, etc.
 
 > What are "transients"?
 
 windows that only exist in conjunction with another window; e.g. a warning dialog associated with a main window.
 
 you also seemed to have skipped over the "works on all hardware" bit.

> "I think it would be better served if Kwin did their own branding of Compas+Beryl."
 
 it has nothing to do with branding or ego. the technical reasons have been explained repeatedly, and they are purely technical. the first thing we (kde) did when trying to decide what to do was to look at the options and play with each of them; they included:
 
 - writing a new WM from scratch (there were even experiments here)
 - adapting compiz/beryl (either wholesale or just the compositing technologies)
 - improving kwin
 
 each was given a lot of thought and testing. there is no perfect solution, agreed, but there are better solutions and worse solutions where "better" and "worse" are judged in relation to the effect on our userbase.
 
 and remember that our userbase includes schools in "third world" countries, banks and governments in the "first" world, hard core hackers, hobbyist computer users, SMBs, 'regular' home users .......

> "'perfectly valid reasons' were things like"
 
 someone else filled in the details for you, if you look above there is a list of things kwin does right today that beryl/compiz doesn't. i try not to spend more than a minute or two writing replies here, so apologies for not being more thorough.
 
 "I REALLY doubt it would be anywhere near as hard as duplicating that much of Beryl's functionality was"
 
 well, it is. in part because the proper window management takes a -lot- of testing under all kinds of conditions and compositing tech is far more self-contained of a problem space: it either works or it doesn't. neither is trivial, but one is faster to get through. the work compiz/beryl have done also shows the way quite nicely; they deserve massive kudos for that.
 
 we have a known good solution that our userbase absolutely relies on. beryl/compiz doesn't work for the entirety, majority even, of that user base. ergo the chosen solution.
 
 btw, this isn't a kde thing. metacity is doing the same thing and, as i understand it, for the same reasons.

---

### Post by Raffo on 2007-07-03
Thank you for the post... this is what I want to read... I don't use compiz right now since I don't need all of its special effects... I'll be glad to use the new, improved, KWIN. 
I'm just curious to see if KDE users will use compiz with KDE4...

---

### Post by Andrewie on 2007-07-03
> **Raffo said:**
> Thank you for the post... this is what I want to read... I don't use compiz right now since I don't need all of its special effects... I'll be glad to use the new, improved, KWIN. 
I'm just curious to see if KDE users will use compiz with KDE4...

I'm not going to be using compiz fusion with KDE 4, I've been using Beryl with Linux for a long time, and a lot of the "wow" effects really don't do it for me, but mostly some of the odd issues I've had with compiz is whats going to draw me away.

---

### Post by Nekiruhs on 2007-07-04
> **Andrewie said:**
> I'm not going to be using compiz fusion with KDE 4, I've been using Beryl with Linux for a long time, and a lot of the "wow" effects really don't do it for me, but mostly some of the odd issues I've had with compiz is whats going to draw me away.
There is no more Beryl. Compiz Fusion IS Beryl AND Compiz.

---

### Post by mips on 2007-07-04
> **Nekiruhs said:**
> There is no more Beryl. Compiz Fusion IS Beryl AND Compiz.

Shhh, you are gonna shatter his/her illusion.

---

### Post by maniacmusician on 2007-07-04
> **Nekiruhs said:**
> There is no more Beryl. Compiz Fusion IS Beryl AND Compiz.
more accurately, it's a heavily revised compiz-core with plugins ported from beryl back to compiz in the form of compiz-plugins and compiz-plugins-extra.

The core is still compiz, and not beryl. I think that compiz-core still needs to see some massive improvements. Some of the plugins aren't working as well as they used to with beryl...but this is expected of an application in such an early stage. I think it'll get better as time goes on. 

Back on topic: KDE4 will work fine with Fusion. The basic thought is, though, that if KWin works well enough people won't bother with Fusion. KWin will have some nice features, I'm sure, but I doubt it'll be able to stack up to the likes of Fusion...and it's not supposed to! As the base window manager, Kwin should provide some basic features, but it really doesn't need to be extensive. It would be a smarter idea for KDE developers to incorporate basic compositing features into KWin, while at the same time, helping to make Fusion more integrated into KDE.

---

### Post by tehkain on 2007-07-04
There are only a few things I use in compiz(fusion).  One of them is scale and the other is expo. I am sure I can afford to lose expo so kwin for kde4 sounds good. Now all I need is a scale like plugin. Oh and they need to pull me away from gnome.

---

### Post by Erunno on 2007-07-04
I could imagine that the developers want to have a fully-featured yet eye-candy enabled window manager for the 4.0 release without having to rely on code heavily in development. Either losing functionality and potentially stability or compositing-support with highly visible effects is not the best solution from a marketing point of view.

---

### Post by GeneralZod on 2007-07-04
A one-month-old demo of some of the experimental effects can be found here:

[http://www.youtube.com/watch?v=4WBLlc6xCQ4](http://www.youtube.com/watch?v=4WBLlc6xCQ4)

As always, I remind you that many of these are intended merely as demos, and don't aspire to aid usability, and are still very rough around the edges.

The sluggishness was partly due to the fact that the screen was being recorded at the time, and partly due to a bug in the texture_from_pixmap code that Lubos recently fixed.

---

