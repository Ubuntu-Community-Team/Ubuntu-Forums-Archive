---
title: "Adept vs. Synaptic"
date: 2006-07-27
forum: The Cafe
---

### Post by shane2peru on 2006-07-27
Does anyone else that has used both think that Adept is a joke???  Or is it just me?  I have used Synaptic, and apt-get and Adept.  Am I missing something or is Adept really as sorry as I think it is?  Uninstalling and installing, I'm not impressed.  I can **NEVER** find programs when searching in Adept, even with any suite selected and both boxes check marked.  I tried searching for a program installed (via apt-get) and it didn't show it.  I searched with synaptic, and viola, there it was, and I did a complete removal so I could re-install it on a clean slate.  Why is Adept so lacking?

Shane

---

### Post by LordRaiden on 2006-07-27
adept is harder to use than synaptic, but I don't think it is a "joke". The 2.0 version is taking long to work on, but I'll be happy once it is done.

---

### Post by Lord Illidan on 2006-07-27
I don't like adept too much either. Synaptic beats it by a long while.. I'd rather the KDE guys ported Synaptic to QT widgets instead of wasting time on Adept.

---

### Post by aysiu on 2006-07-27
I use *aptitude*, but I agree that Synaptic is more fully featured than Adept.

---

### Post by ColinG on 2006-07-27
I heard somewhere that Smart was taking over as the package manager. Don't know how true that is but it's a nice piece of software ;-) 

Certainly I prefer Synaptic to Adept.

---

### Post by Lord Illidan on 2006-07-27
> **ColinG said:**
> I heard somewhere that Smart was taking over as the package manager. Don't know how true that is but it's a nice piece of software ;-) 

Certainly I prefer Synaptic to Adept.

Smart is written in Python. I don't know about you guys, but python apps suck lots of memory and cpu out of this machine.. Synaptic is working, so why fix it?

I remember in Fedora core 5, the applications for updates and installing stuff were all in python..as slow as hell.

---

### Post by shane2peru on 2006-07-27
> **LordRaiden said:**
> adept is harder to use than synaptic, but I don't think it is a "joke". The 2.0 version is taking long to work on, but I'll be happy once it is done.

I guess I spent quite a bit of time on Gnome, and really grew to like Synaptic, and as far as easy to learn and use, I prefer it.  What is and when is Adept 2 coming out?  I would really think that they would be better off just porting Synaptic over.  Let me fire a question at you.  How do you "completely remove"  a program using Adept?  Or does it always "completely remove"?  Those how have used Synaptic will understand the difference, I have yet to discover this in Adept.

Thanks for all the input, I was starting to think that I wasn't very adept at using Adept. :D 

Shane

---

### Post by John T. Monkey on 2006-07-27
Synaptic probably is better, but Adept is okay. It does it's job, and I don't use it that often anyway. I set my system up and don't really need to (un)install very often. And when there are updates, I start it off and then leave it alone. 

I would like to know about completely removing programs though. That is something I've never been sure about.

---

### Post by LordRaiden on 2006-07-27
Adept 2 is out now. Still having the bugs sorted out. It's on Kubuntu Edgy at the moment, and I occasionally use it (apt-get is faster for me since i use Yakuake as a console). Adept works in the same way as apt-get and synaptic, if you get rid off a package, all the packages that depend on it are removed as well.

In Kubuntu, you have two ways to get to Adept. The first is the add/remove programs option (Application names instead of package names). Under System or Utilties, there is Adept Package Manager which is more like synaptic. It also has nice features like being able to look for packages under a different subset (all, xorg, dev, games etc..).

---

### Post by gingermark on 2006-07-27
I think Adept is fine. My only issue with it is that it doesn't tell you what it's doing all the time.

When you go to install something for example it doesn't tell you what extra packages will be installed, or if there are conflicts which packages will be removed. You have to preview changes to find that out.

On the other hand Adept does provide more info on each dependency. Before you install something, you can see it's dependencies, and their dependencies, and get far more information about each package then you can with Synaptic.

I personally prefer Synaptic, but I think both package managers have their strengths and weaknesses.

---

### Post by bailout on 2006-07-27
Adept was terrible in breezy but I haven't had any problems with it in dapper.

I can't understand how you had difficulty searching for a package with as I think searching is much better in adept than synaptic as it is in real time. Just don't use the check boxes (ie leave them all checked as in the default) and it defaults to all packages in the list.

I have also heard people complain before about it not saying what it is going to do. The problem here is that it doesn't throw up flashing neon warnings and require you to double check. The bottom right of the "status bar" displays how many packages are going to be installed, removed or updated. If you want to see details then you need to click the preview button.

I think all the check boxes and tag system makes the gui confusing and I can't imagine many people use them tbh. Also I was surprised they wrote it from scratch instead of just finishing the development of kynaptic instead. However, now I think I prefer it to synaptic.

---

### Post by aysiu on 2006-07-27
You shouldn't have to click the *preview changes* button to find out that about 100 of your desktop-crucial packages are about to be uninstalled.

---

### Post by bailout on 2006-07-27
You don't have to, as I said it displays what chages are going to happen in the status bar. Also I would love to know what you did that caused it to delete 100 of your destop-crucial packages. I find it hard to believe that if this happened it can really be blamed on Adept and not the user ;)

---

### Post by LordRaiden on 2006-07-27
Adept 2 is actually a whole lot better than I thought. I don't use it for updating since I have the console on all the time, but it makes it really easy to search for packages whose names you don't know. The checkboxes and tag boxes can seem intimidating, but if you understand how to use them, they are very useful tools. It's still a work in progress, but I really like how things are shaping up.

I have one screenshot here of what it looks like if anyone wants to see.

---

### Post by aysiu on 2006-07-27
Can you show me a similar post to this regarding Synaptic? > I startup Adept, enter my password, type "fam" in the search box and it shows. I right click the fam package and select install. Click commit. And that was the end of my kubuntu instalation. Adept switched to the text dpkg output view. Suddenly its scrolling. Every line starts with "Removing". I'm a bit surprised as i see it removing almost 400 packages, many of them related to KDE, like Amarok which was _running_ at the time. After removing what i estimate to be around 200 packages, Adept crashed, maybe because it removed itself. From [this thread](http://ubuntuforums.org/showthread.php?t=134614).

---

### Post by gingermark on 2006-07-27
I have to admit, I once clicked "Commit changes" instead of "preview changes" by accident (the two buttons are right next to each other).

As I said before, I think both Synaptic and Adept have their stregnths and weaknesses, but in my opinion any application requiring root priviledges needs to give the user a chance to change their mind. This is Adept's major weakness.

---

### Post by aysiu on 2006-07-27
The only time you can blame a user for a problem is when...

1. The user experiences the same problem with all similar applications (for example, can't use OpenOffice... but also can't use MS Office or Gnome Office or AbiWord...)
2. The user has too much experience with one application and thus cannot adapt to a new way of thinking (Has used Windows setup.exe files for ten years... just started with package management)
3. No other user has had the same problems (self-explanatory)

---

### Post by shane2peru on 2006-07-27
> **LordRaiden said:**
> 
In Kubuntu, you have two ways to get to Adept. The first is the add/remove programs option (Application names instead of package names).** Under System or Utilties, there is Adept Package Manager which is more like synaptic. **It also has nice features like being able to look for packages under a different subset (all, xorg, dev, games etc..).

Ahhh, that is nice.  I think that was what I needed to know.  That is why I thought Adept was sooooo ridiculous, I didn't know they were different.  I will have to try that one and see how that is.  Thanks for the tip.

Shane

---

### Post by LordRaiden on 2006-07-27
Just don't hit commit before preview. Maybe the Adept devs should should just take off the commit button in the normal view and only let it appear in the preview. That way, the user would have to preview before committing. Also, the button should be more distinguished and possibly moved to the side.

---

### Post by shane2peru on 2006-07-27
Ok, I looked and I don't have that one.  Where is it?  I checked under System and Utilities?  I must be missing something?  Help.

Shane

---

### Post by LordRaiden on 2006-07-27
it's under the K-menu --> System --> Adept Manager. I'm running Edgy by the way so that is what I see.

---

### Post by TheRingmaster on 2006-07-27
i like the way adept automatically searches based on what I typed. other than that I like synaptic's features better.

---

### Post by Jucato on 2006-07-27
In this thread, I made a sort of "comparison" list of the different package manager frontends, like Synaptic and Adept.

I don't think Adept is a "joke", although it could certainly do better. There are some things which Adept has that I prefer over Synaptic:

1. Customizable toolbars: meaning you can re-arrange those to suit your workflow. You want to click Preview Changes first, without accidentally clicking on Apply Changes? That's easy. Here's an example of my "toolbar workflow" in Adept.

[IMG]http://i73.photobucket.com/albums/i206/jucato/screenshots/adept.jpg[/IMG]

2. (Filter) search: it's quick to access and comprehensive. I don't know what's causing people to have problems locating packages using that. Maybe a wrong combination of check boxes? In Adept, just type the package name, description, or maintainer,and it will display all possible results. The combinations of checkboxes can help narrow down the search. In Synaptic, you have to click on the search button to initiate a search, and the combination of where to search is a bit limited. Of course, Synaptic has a quick search feature (this one)

[IMG]http://i73.photobucket.com/albums/i206/jucato/screenshots/synaptic.jpg[/IMG]

But this is a bit limited in because it only search for an exact package name match and it only goes to that exact package, and doesn't hide non-matching items. So if you type in "3d", it will just go to the first package that starts with "3d", while in Adept, it will display anything that has "3d" in the name, description, etc., and hide everything else.

Of course, there are also some things that I don't like (almost hate) in Adept:
1. A scary default UI: It will undoubtedly confuse new users. Deb-tags? what are they? do most users know what they are? Why are they on by default? Why can't we permanently hide/disable it?

2. No categories: Although I don't think it's used that much, it's still a nice feature to have, specially if you're just browsing for a particular kind of program.

3. It presumes you know exactly what you are doing: no intrusive confirmation pop-ups. I've seen this behavior wreck havoc on new users' computers too many times. aysiu can attest to that.

One thing that has somewhat discouraged me about Adept's future is one remark in a [kde bug/wishlist report regarding Adept](https://bugs.kde.org/show_bug.cgi?id=112819). It was a suggestion to have an intrusive confirmation dialog box whenever you try to make changes, similar to Synaptic's. The dev's response was not very encouraging (no offense to Petr Rockai).

I would have preferred if they continued development of KPackage. It's already a very useful and powerful package manager frontend, but it needs a bit more tweaking to make it run/startup faster. Smart Package Manger sounds good, but I heard that it's quite slow at the moment. I'm not sure if a majority of our users are willing to have that.

Just my $ 0.02...

EDIT: Conclusion: By itself, Adept is a powerful package manager. However, it is not something that new, or even intermediate, Linux users would appreciate. So far, the only people singing its praises are experienced Linux users or developers/programmers. While Synaptic isn't that perfect, either, among the present alternatives available, it is the best. 

Now if only Aptitude had a "true" GUI...

---

### Post by shane2peru on 2006-07-27
> **LordRaiden said:**
> it's under the K-menu --> System --> Adept Manager. I'm running Edgy by the way so that is what I see.

Ok, this seems to be the problem.  I'm looking at the screen shots and . . .  . I don't have that look.  Here is what is listed below my KMenu - System - and:
AVg
Kiok
Synaptic
QT Parted
Keep
Kinfo Center
Language Support
KsysGuard
KsystemLog
Kron
Konsole

That is it.  Nothing else. 
Under Utilities I have:
Moto4Lin
Avg
Binary Editor
Scientific Calc
Bibletime
Desktop Widgets
Kandy
Kpilot
Personla Alarm Scheduler
The SMB...
Ktip
Kate
Ark
Krusader
Krusader -root
ISkim
KDE Groupware Wizard
Karm
Knotes
KjobViewer
Terminal

Well, those are my options.  I think I can retract my statement about Adept being a joke.  I only have the Add/Remove Programs Adept package manager.  How can I get that nice version you all are using?  BTW - I'm using Dapper up-to-date.  
----------------------------------------------------------------------------------------
Never mind - I just ran ```
kdesu adept
``` and now I get all those wonderful options like everyone is talking about in Adept.  Why wasn't that in my Menu choices from the start?  That is wierd.  I will add it.  Thanks for all the healthy discussion.

Shane

---

### Post by missmoondog on 2006-07-30
adept is totally a joke! slower than molasses, inept at finding anything when searching, doesn't show what's happening all the time. Completely laughable!!

now, my question is, can i remove that thing and just use synaptic?

thanks

edit:
yep, you can remove adept!! =P~

---

### Post by Jucato on 2006-07-30
You can remove Adept, but it will also remove kubuntu-desktop, which might make future upgrades a bit more difficult. You can safely install Synaptic without touching Adept, if you want. I think you might also want to install *update-notifier* and *update-manager* if you want the same features in Kubuntu.

I personally don't like Adept, but I wouldn't go as far as calling it a joke.

---

