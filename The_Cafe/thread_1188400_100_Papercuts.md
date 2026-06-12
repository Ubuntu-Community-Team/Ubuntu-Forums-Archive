---
title: "100 Papercuts"
date: 2009-06-15
forum: The Cafe
---

### Post by Messyhair42 on 2009-06-15
I just read this article from Ars Techinca [http://arstechnica.com/open-source/news/2009/06/canonical-to-boost-ubuntu-usability-by-tackling-papercuts.ars]("http://arstechnica.com/open-source/news/2009/06/canonical-to-boost-ubuntu-usability-by-tackling-papercuts.ars") and immediately had ideas. since I didn't find a direct link to where the discussion has been going on I'm appealing to the forum community. the very first thing that came to mind as a "papercut" is that the volume control in the panel does nothing at all on my computer and i've heard the same thing from other users IRL and on the forums; i mean it just sits there and doesn't function like it should.

---

### Post by jsmidt on 2009-06-15
Here is where to report "100 Papercuts" bugs.  Please remember to only add your bug if:

1. Fixing it would improve usability.
2. The fix is easy enough that it can be implemented quickly.
3. It must effect the default Ubuntu install only.  
4. It must be an issue most Ubuntu users would be concerned with.

---

### Post by Wiebelhaus on 2009-06-15
I don't recall this in the Weekly newsletter , Has there been or will there be an official announcement asking for participation?

[100 Paper cuts  ]("http://arstechnica.com/open-source/news/2009/06/canonical-to-boost-ubuntu-usability-by-tackling-papercuts.ars")



[IMG]http://static.arstechnica.com/ubuntu-papercut.png[/IMG]


> Canonical, the company behind the popular Ubuntu Linux distribution, is launching a new project to improve the usability of the platform. The developers aim to identify and resolve 100 minor bugs that negatively impact the Ubuntu user experience before the release of the next major version in October.

The initiative, which is called One Hundred Paper Cuts, will be implemented by Canonical's new design and user experience team in collaboration with the Ubuntu community. Canonical's design experts have called for Ubuntu users to participate by helping to identify relevant bugs. They are specifically looking for easily fixable bugs that impact the usability of key system components such as the panels and file manager. Canonical hopes to boost the overall quality of the platform by addressing a multitude of subtle issues that developers would otherwise ignore. Many of the improvements that are applied through this effort will directly benefit upstream projects.

Canonical began assembling a team of professional designers last year to lead a broad community-driven usability initiative called Project Ayatana. The new One Hundred Paper Cuts initiative is one of several strategies that comprises Ayatana. Another major facet of Ayatana is Canonical's experimental notification system, which was introduced in Ubuntu 9.04. During this development cycle, the new notification system will receive additional improvements as the design team simultaneously tackles the papercuts.

David Siegel, the developer of the popular GNOME-Do launcher, recently joined Canonical as part of the user experience and design team. In his blog, he describes the function of the One Hundred Paper Cuts project and provides more specific insight into what kind of issues are classified as papercuts.

"If some small usability detail has been bothering you release after release, now is your chance to step up and get it the attention it deserves," he wrote. "If we can find and heal one hundred paper cuts, Ubuntu 9.10 will surely be the most usable release of Ubuntu yet."

Users can participate by reporting bugs and flagging them as papercuts in Ubuntu's Launchpad development site. As Siegel points out in his blog, this is a great way for new contributors to get involved in the process of improving Ubuntu. Users can also help by participating in the Ubuntu 9.04 usability study. If the papercut project is successful, Siegel says, it might be reiterated during future development cycles.

Many of us who are experienced Linux users have become so accustomed to ignoring minor glitches that such problems practically become invisible. The result is that there are a lot of really subtle deficiencies that have long been overlooked by developers but are immensely frustrating to new users. The One Hundred Paper Cuts project looks like an effective way to overcome this challenge and smooth out some of Ubuntu's rough edges.

Did I just miss it like a dummy or what?

---

### Post by pt123 on 2009-06-15
I wonder if this would be as ineffective as the brainstorm website. 

Considering how long they have been talking about a new theme and not implemented it, I wonder if this project will take the same road.

---

### Post by TheLions on 2009-06-15
here is easy one to fix: Improve Firefox speed compiling it with PGO

---

### Post by pt123 on 2009-06-15
I wonder if this would be as ineffective as the brainstorm website.

Considering how long they have been talking about a new theme and not implemented it, I wonder if this project will take the same road.

---

### Post by Wiebelhaus on 2009-06-15
> **pt123 said:**
> I wonder if this would be as ***_ineffective_*** as the brainstorm website.

Considering how long they have been talking about a new theme and not implemented it, I wonder if this project will take the same road.

Really? I don't see how you came to that conclusion , the site is busy as heck and constantly producing good ideas. I don't understand.

---

### Post by rCXer on 2009-06-15
Personally, I think this is a good idea. I've even found a few fixes for some of my problems. [Here](https://bugs.edge.launchpad.net/hundredpapercuts/+bugs?start=0) is a list the paper cuts submitted so far. For those who have launchpad accounts, [here's](http://blog.davebsd.com/2009/06/10/one-hundred-paper-cuts/) a link describing how to mark a bug as a paper cut. 

My paper cut would be that the gnome-screensaver activates during many fullscreen applications even though the keyboard and mouse are being used.  Apparently gnome-screensaver doesn't detect keypresses and clicks while a fullscreen application running.  The [bug](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/32457) is 3 years old with 20 duplicates.

---

### Post by Wiebelhaus on 2009-06-15
> **rCXer said:**
> Personally, I think this is a good idea, I've even found a few fixes for some of my problems. [Here](https://bugs.edge.launchpad.net/hundredpapercuts/+bugs?start=0) is a list the paper cuts submitted so far. For those who have launchpad accounts, [here's](http://blog.davebsd.com/2009/06/10/one-hundred-paper-cuts/) a link describing how to mark a bug as a paper cut. 

My paper cut would be that the gnome-screensaver activates during many fullscreen applications even though the keyboard and mouse are being used.  Apparently gnome-screensaver doesn't detect keypresses and clicks while a fullscreen application running.  The [bug](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/32457) is 3 years old with 20 duplicates.

Thanks mate.

---

### Post by Islington on 2009-06-15
> **pt123 said:**
> I wonder if this would be as ineffective as the brainstorm website.

Considering how long they have been talking about a new theme and not implemented it, I wonder if this project will take the same road.

what are on about? evolution not revolution, and the themes have been going just that way. These are easily fixable bugs, why wouldn't this project proceed.

---

### Post by Barnstormer on 2009-06-15
> **Islington said:**
> what are on about? evolution not revolution, and the themes have been going just that way. These are easily fixable bugs, why wouldn't this project proceed.
I really want to believe this will help, but 100 usability issues is nothing.  Usability should be taken seriously rather than ignored and tackled years after the software has launched.

While I do not agree with [this blog post]("http://piestar.net/2009/03/20/gnome-226-partying-like-its-1995/") 100% it brings up some good points.  I think a more fundamental approach needs to be given to fixing usability - hell, the next few versions should focus on nothing but usability if they want to catch up with OSX, and now Windows 7 (which is very impressive).  Unless it is put at the front Ubuntu will always be behind.

---

### Post by zekopeko on 2009-06-15
> **Barnstormer said:**
> I really want to believe this will help, but 100 usability issues is nothing.  Usability should be taken seriously rather than ignored and tackled years after the software has launched.

While I do not agree with [this blog post]("http://piestar.net/2009/03/20/gnome-226-partying-like-its-1995/") 100% it brings up some good points.  I think a more fundamental approach needs to be given to fixing usability - hell, the next few versions should focus on nothing but usability if they want to catch up with OSX, and now Windows 7 (which is very impressive).  Unless it is put at the front Ubuntu will always be behind.

i don't think you understand what exactly 100 papercuts is about.
it's not about redesigning Gnome usability. it's about fixing simple bugs that are user visible (like in the GUI). Small problems that a user encounters multiple time a day. check the projects page.

---

### Post by Wiebelhaus on 2009-06-15
> **Barnstormer said:**
> I really want to believe this will help, but 100 usability issues is nothing.  Usability should be taken seriously rather than ignored and tackled years after the software has launched.

While I do not agree with [this blog post]("http://piestar.net/2009/03/20/gnome-226-partying-like-its-1995/") 100% it brings up some good points.  I think a more fundamental approach needs to be given to fixing usability - hell, the next few versions should focus on nothing but usability if they want to catch up with OSX, and now Windows 7 (which is very impressive).  Unless it is put at the front Ubuntu will always be behind.

I disagree with basically everything you said , I use Ubuntu because it's better than those two you mentioned.

---

### Post by Barnstormer on 2009-06-15
> **zekopeko said:**
> i don't think you understand what exactly 100 papercuts is about.
it's not about redesigning Gnome usability. it's about fixing simple bugs that are user visible (like in the GUI). Small problems that a user encounters multiple time a day. check the projects page.
I think what is lacking is an actual understanding of what usability is, and how it should be treated in the development process.  While admirable, this push has no real hope of handling any true usability concerns and given the friction on even obvious problems will not really lead to any massive improvements.

[http://www.joelonsoftware.com/printerFriendly/uibook/fog0000000249.html](http://www.joelonsoftware.com/printerFriendly/uibook/fog0000000249.html) is pretty old, but it is very insightful and shows how software usability should be treated.

Besides, the Linux community gets itself into a frenzy about seriously tackling usability every 6 months or so and nothing ever really comes of it.  I am allowed to be a bit skeptical :)

---

### Post by Barnstormer on 2009-06-15
> **Wiebelhaus said:**
> I disagree with basically everything you said , I use Ubuntu because it's better than those two you mentioned.
Personally I use Windows 7 because it's better for my needs than Ubuntu (as do thousands of other people) - I wish this wasn't the case but it is.  

The key questions should be 'Why is this the case' and 'What can we do about it'.  A statement of victory and bravado is not the answer, evangelism has no real use here.

---

### Post by keiichidono on 2009-06-15
one of my papercuts would be to make it easier to edit the lock dialogue theme. There's already an implementation in the below link, just add it into Ubuntu.

[http://www.gnome-look.org/content/show.php/Lock+Dialog+Preferences?content=100871](http://www.gnome-look.org/content/show.php/Lock+Dialog+Preferences?content=100871)

Also, I just noticed that sometimes when I right click a link in Firefox it randomly opens up a bookmark or an info window instead of displaying the context menu. =\

---

### Post by ugm6hr on 2009-06-16
> **CalvinB said:**
> Also, I just noticed that sometimes when I right click a link in Firefox it randomly opens up a bookmark or an info window instead of displaying the context menu. =\

This is a known FF bug.  Use FireGestures FF addon to fix it.

Here it is: [https://bugs.edge.launchpad.net/ubuntu/+source/firefox-3.0/+bug/187313](https://bugs.edge.launchpad.net/ubuntu/+source/firefox-3.0/+bug/187313)

Just noticed that it is now "Fix Released"

---

### Post by 23meg on 2009-06-16
> **CalvinB said:**
> one of my papercuts would be to make it easier to edit the lock dialogue theme. 

That's not a paper cut. 

David Siegel made a blog post to clarify (again) the definition of a "paper cut" for this project:

[http://blog.davebsd.com/2009/06/15/calling-all-paper-cutters/](http://blog.davebsd.com/2009/06/15/calling-all-paper-cutters/)

Please pay attention to these definitions before proposing new ones.

[QUOTE=Barnstormer]While admirable, this push has no real hope of handling any true usability concerns and given the friction on even obvious problems will not really lead to any massive improvements.

[http://www.joelonsoftware.com/printe...000000249.html](http://www.joelonsoftware.com/printe...000000249.html) is pretty old, but it is very insightful and shows how software usability should be treated.
[/QUOTE]

This project is a *top-down* initiative that aims to fix a large number of existing minor issues. It doesn't *aim to* fix some of the more deeply rooted problems in free software usability that I assume you may mean by "true usability concerns". Spolsky's famous article, in contrast, goes *bottom-up*, and despite describing the right approach in the longer term and from a per-application design perspective, it's not really relevant to a decidedly top-down project that focuses on trivial issues, deals with multiple software, and has a fixed time frame.

---

### Post by pt123 on 2009-06-16
> **Wiebelhaus said:**
> Really? I don't see how you came to that conclusion , the site is busy as heck and constantly producing good ideas. I don't understand.

When it started out it was much more busier, lot of people have lost faith in it. The brainstorms are grouped and too generalised, the brainstorms that are very general get most of the votes. 
The developer response and feedback has been very poor on the brainstorms. 

> **Islington said:**
> what are on about? evolution not revolution, and the themes have been going just that way
They were scheduled for 8.04 and nothing has been done on it. I would have prefered the evolving type approach like using Dust as the default theme, and using Tango Icons as the base then modifying the icons gradually.

---

### Post by Islington on 2009-06-16
> **pt123 said:**
> 
They were scheduled for 8.04 and nothing has been done on it. I would have prefered the evolving type approach like using Dust as the default theme, and using Tango Icons as the base then modifying the icons gradually.
Since 8.04 they have tested bugs in a dark theme, added new engines to human, made small incremental improvements.
Human theme has been evolving for a while now, new community built themes are now included by default. Human icons will probably/possibly going to be replaced by Breathe.  I honestly have no idea what you are on about. Suddenly using Dust as default is in no way evolution.

---

### Post by hanzomon4 on 2009-06-16
Does this one count: When ever I full-screen a web video, from say hulu, any adjustments made via hotkeys to volume, screen brightness, or keyboard backlight causes the full screen video to go back regular size in the browser. This is very annoying.

Another one: Why do my hotkeys work in gnome but not kde? Shouldn't something like that be DE agnostic? I mean I may want to adjust my screen light, keyboard light, or volume without loading up the gui. Same with internet... Why can't I have it, easily, without a DE?

---

### Post by pt123 on 2009-06-16
> **Islington said:**
>   I honestly have no idea what you are on about. Suddenly using Dust as default is in no way evolution.
I don't know what you are on about, a major default theme change was "promised" for 8.04 but every release since then it has been pushed back. I really don't what's not to get about this. 

Choosing Dust is following the community's popular adaptation of it, evolving based on natural selection than because "God" chose it. 

Make it the default will go a long way to attracting new users to try Ubuntu. The current default theme looks border line 90s.

---

### Post by 3rdalbum on 2009-06-16
It might not really be a "paper cut", but I nominated "Rhythmbox cannot open smb:// locations". It should be possible to fix it by adding a little bit of code that converts for instance "smb://chris-server/share" to "~/.gvfs/share on chris-server".

Terribly annoying bug. And I'm sure the KDE developers are laughing that Gnome's default music player doesn't work with Gnome's default virtual filesystem!

---

### Post by Barnstormer on 2009-06-16
> **pt123 said:**
> I don't know what you are on about, a major default theme change was "promised" for 8.04 but every release since then it has been pushed back. I really don't what's not to get about this.
There was loads of amazing concept pieces made in response to the Hardy announcement where they solicited for ideas from the public (and non-programmers in general).

It seems one of the FOSS communities biggest problems is that they start off these endevours but rarely manage to follow through once the initial interest fades.  The only people who have any real input seem to be developers, when in reality to make truly great software you need to engage with all sorts of people - designers, testers, ui specialists.

---

### Post by Sealbhach on 2009-06-16
.

EDIT: According to Launchpad there has been a fix released:

[https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/360553](https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/360553)

.

---

### Post by TBerk on 2009-06-16
> **CalvinB said:**
> one of my papercuts would be to make it easier to edit the lock dialogue theme. There's already an implementation in the below link, just add it into Ubuntu.

[http://www.gnome-look.org/content/show.php/Lock+Dialog+Preferences?content=100871](http://www.gnome-look.org/content/show.php/Lock+Dialog+Preferences?content=100871)

Also, I just noticed that sometimes when I right click a link in Firefox it randomly opens up a bookmark or an info window instead of displaying the context menu. =\



I'll be following the link to the actual papercuts themselves but I wanted to echo a 'me too' on this one:  Firefox 3.0.11 on Ubuntu 9.04 has a very irritating 'bug' where it chooses to think I let the mouse button up and therefore chose a certain function when clicking on links, but esp when Right-clicking on links (expecting he menu to come up but instead getting who knows what function to take place.) Sometimes it open the email app, sometimes it hopes to bookmark a link, rarely do I get ti to work right unless I hold the mouse real still and hold the button down a second or two.

My other main pet peeve is in the file manager I cant Right-Click and get a chance to (for example) rename a folder or file on the fly.   (Huh, I need to go back and recreate that one, but basically if I create a new folder from within a 'save' dialog box and mistakenly type the wrong name for said new folder I can rename it prior to saving the file I want. I can either make a second, correctly spelled folder or save the file in the 'wrong' folder and go and rename the folder outside of the 'Save As...' dialog window.


berk

---

### Post by matthekc on 2009-06-21
Once and a great while when I right click web page links evolution opens.  It's really weird because there is no menu option for that.

---

### Post by ugm6hr on 2009-06-21
> **matthekc said:**
> Once and a great while when I right click web page links evolution opens.  It's really weird because there is no menu option for that.

It is the "Send Link..." option.

---

### Post by MJWitter on 2009-06-21
> **matthekc said:**
> Once and a great while when I right click web page links evolution opens.  It's really weird because there is no menu option for that.

Right click -> Send link.  This opens evolution.

---

### Post by lswb on 2009-06-21
> **jsmidt said:**
> Here is where to report "100 Papercuts" bugs.  Please remember to only add your bug if:

1. Fixing it would improve usability.
2. The fix is easy enough that it can be implemented quickly.
3. It must effect the default Ubuntu install only.  
4. It must be an issue most Ubuntu users would be concerned with.

Ha Ha! Good post!

---

### Post by 23meg on 2009-06-21
> **Barnstormer said:**
> 
It seems one of the FOSS communities biggest problems is that they start off these endevours but rarely manage to follow through once the initial interest fades.  The only people who have any real input seem to be developers, when in reality to make truly great software you need to engage with all sorts of people - designers, testers, ui specialists.

This effort is being led by a team consisting mostly of established interaction designers; many of whom are designers first, free software users second. And it's open to all sorts of people in the community to suggest, triage and fix the bugs in question.

---

### Post by sim-value on 2009-06-21
100 ?! lol

more than 459 Bugs already ...

---

### Post by rCXer on 2009-06-21
> **sim-value said:**
> 100 ?! lol

more than 459 Bugs already ...

And 14 are "Triaged" or "In Progress" meaning that they are working on them...

---

### Post by HappyFeet on 2009-06-21
> **Barnstormer said:**
> I think a more fundamental approach needs to be given to fixing usability

I didn't know ubuntu wasn't usable. I personally know many people that use ubuntu and they find it *more* usable than windows.

---

### Post by jaj23 on 2009-06-27
I am currently working on a usability project on Ubuntu and am analyzing survey comments, which should find quite a few genuine paper cuts, directly proposed to Canonical

Also keep your eyes posted for a re-design survey coming in the next few weeks, with more major re-design proposals

jaj23

---

### Post by jaj23 on 2009-06-27
> **HappyFeet said:**
> I didn't know ubuntu wasn't usable. I personally know many people that use ubuntu and they find it *more* usable than windows.

Whilst that is true, it doesn't mean it can be made even more usable and facilitate a better user experience


jaj23

---

### Post by dragos240 on 2009-06-27
100 papercuts? I'M BLEEDING!!!!

---

### Post by philliptweedie on 2009-06-27
Would it be bad form to submit the way update manager now behaves as a papercut? ;)

---

### Post by mikewhatever on 2009-06-27
> **philliptweedie said:**
> Would it be bad form to submit the way update manager now behaves as a papercut? ;)

I think so. The notification behavior was changed intentionally.
[http://www.ubuntu.com/getubuntu/releasenotes/904#Change%20in%20notifications%20of%20available%20updates](http://www.ubuntu.com/getubuntu/releasenotes/904#Change%20in%20notifications%20of%20available%20updates)

---

