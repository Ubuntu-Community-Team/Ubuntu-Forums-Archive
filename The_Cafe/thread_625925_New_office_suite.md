---
title: "New office suite"
date: 2007-11-28
forum: The Cafe
---

### Post by Xbehave on 2007-11-28
ive been using Ubuntu for a while now and have no problem using its office programs, but i feel that they just want to be like MS office when they could be so much more.
In office 2007 MS improved the interface substantially, and left alternatives looking dated. The best way to not just to get level but also prevent this happening again is to design an office suit that will suite the users needs, with a GUI to suit (ideally letting the interface be customised substantially even to imitate the MS version if wanted)

I think open source office suites should stop trying to be MS office and start showing MS how to do it!
(in the same vain as firefox, even if only 13% use it, 22% use IE7 which is clearly based on the same ideas*)

my idea Fireoffice (better name pending)
(disclaimer: i dont know much about programming, widgets, firefox, OO)
i think an office based on XUL (and maybe OO) could kick MS ****
*easily configurable but advanced 
*tabbed interface
*extensions to suit each users needs
*a light core

_toolbars_
common office suits clutter the interface with atleast two rows of buttons just to perform basic operations, to perform more complicated tasks users are forced to add extra menus or resort to menus. To resolve this Fireoffice would feature:

**tabbed toolbars**
instead of having multiple toolbars having one tool bar with multiple sets of buttons that switch depending on the active toolset.
|P:P|A:B:C|Fill area|P:P|
P=permanent button
A,B,C would toggle whats in the fill area
this would all be configurable like firefox's toolbars (ive actually figured out most scenarios to make it fully customisable and easy to customise, but will save you the details)

intelligent spelling corrector
**Contextual toolbars**
Based on context the active fill buttons could change.
for example in a spread sheet when your editing a formula, useless buttons would be replaced by icons for common functions

**themeable toolbars**
to allow the user to customise the icons to suit their design

**more complicated button states**
to allow better customisation and default themes.
priority: buttons that are likely to be used (e.g if a paragraph is selected then left/right/justify)
usable: buttons that have a function (e.g if a paragraph is selected then add table)
disabled: buttons that cant do anything  (e.g if a paragraph is selected then remove column from table)
this would allow disabled buttons to be removed,priority buttons to be highlighted, usable buttons to be reduced to dropdown menus

**combined buttons**
buttons that perform different options depending on the mouse action allowing users to save space
e.g **B**/*I*/_U_ button would make text bold on left click, italic on middle, underlined on right
or a print button could preview on left, instant print on middle, goto print settings on right.

Everything would be stored in open files allowing users to share their improvements easily

_Tabbed documents_
Documents could share the same window,
This would be configurable at least to always/never/same type/same folder/same name

_Extensions_
by using XUL the possibilities for extensions would be endless here are some ideas i had:
**paper view**: makes pages look like paper and can be manipulated as such
**pencil**: lets you draw/doodle on the page
book maker: allows printing to ebook formats and viewing as a book
**preview**: would let you see the definition of a word on dictonary.com using something like colaris preview (or wikipedia or thesaurus or ...)
**webformater**:convert the document to forum/HTML/anything formatted text
**WebDev**:turns a word processor into a basic HTML+CSS editor
**multiview**:would allow you to split the view between documents to compare them or read 1 and write 1 or...
**DiffView**: compare two (or more) versions of a document
**spelling corrector**: learns you common spelling mistakes and auto-corrects them (warns/highlights when it does it)
error finder: highlights errors like unclosed brackets, no spaces after . etc

**A light core**
the program would be distributed in 2 version 
**FireOffice** would be packaged with various buttons,extensions and themes.This produces a suit that can do more than the average user would want
it would come with 4 themes/configs
Redmond 07 - look and acts mainly like office 07
Redmond - looks and acts mainly like the old office
Minimal - a minimal space using setup leaving the document with most of the screen (could probably be reduced to a single line)
and Full

**FireOffice-lite** would be just the core applications, probably for users who only want the most basic functionality

these are just a few of my ideas, and the extensions just what i thought of in 5 minutes because otherwise i would have gone on all night. i also have a hell alot of ideas for the toolbars and supper buttons (open/new) (save/as/ver). unfortunately i have no programing ability :( 

are any of my ideas doable with existing OSS?
do you like/hate my ideas?

---

### Post by Depressed Man on 2007-11-28
While I agree with most of your post.. I personally think the interface in Office 07 is horrid. I'm still trying to find things even when I use it. Compared to previous versions of Office or other writer/word/whatever type programs. Though to each their own, my sister likes it. While I have a friend who hates it as well, so I guess it's really user dependent.

I'd add the ability to modify the interface. As one size does not fit all.

---

### Post by ssam on 2007-11-28
i say get rid of the whole WYSIWYG (what you see is what you get) idea.

you should work on the stucture of the document. so you add sections and subsections. which can be folded up like a filesystem tree view.

all formating is in a style sheet (appart from things like making a word bold).

then when you are finished (or when you want to preview), the document is rendered onto what ever page size you want.

(can you that i use LaTeX)

---

### Post by smartboyathome on 2007-11-28
I would like it if you could change the size of the toolbar as well as change which buttons are part of which toolbar. Also, using tabbed toolbars is basically the same thing as what Office07 did.

---

### Post by Depressed Man on 2007-11-28
And Microsoft has a patent on the ribbon interface (what the tab interface is considered if your trying to make it like Office 07). Though I personally find it ridiculous that you can patent that (if What's next, creating a circular interface and patenting that?). I'd understand if they patented the actual layout itself so competitors couldn't copy the layout word for word, but the entire idea of a ribbon interface?

---

### Post by samwyse on 2007-11-28
[http://koffice.org/kword/](http://koffice.org/kword/)
[http://en.wikipedia.org/wiki/Kword](http://en.wikipedia.org/wiki/Kword)

Kword is doing something different.

BTW, XUL is slow. I hope Mozilla gets rid of it.

---

### Post by Xbehave on 2007-11-28
> **ssam said:**
> i say get rid of the whole WYSIWYG (what you see is what you get) idea.

but TBH thats what most users including me want, if i want to send a letter i really dont care about the underlying file, If i want to edit an file i use kate or kedit but a document editor is what i was going for

> I'd add the ability to modify the interface. As one size does not fit all.
> I would like it if you could change the size of the toolbar as well as change which buttons are part of which toolbar.
thats what i was going for i probably should have mentioned the use a userchrome style file and unless it causes performance problems the storing of toolbars as editable text files
by change toolbar size in firefox can change height but not the width which is always full width
as i imagined it the toolbars would be customised like the firefox toolbars with the adition of:
*A listbox to choose between the differend sets of buttons which you are free to add as many times as you want to any menu you want
*A fill option, it would apear likea flexible resize
*A set of unused icon
when an unused icon is droped into a fill box a new menu apears wich you add buttons that apear when that fillbar is active, then you add the newly bound icon wherever you want.
there would also be a setting for what to do when the toolbar gets full
1)nothing (firefox style)
2)overflow to new toolbar
3)use dropdown boxes(OO style)
and an option somewhere for weather to aply this to the whole toolbar or the fillbar

I thought Office07 did it in a dreamweaver style whereas my method would be more generic and allow the tabs to be inline(my diagram) or in a sperate bar (Office07) or inline in a seperate bar.
ribbon interface?

---

### Post by LaRoza on 2007-11-28
> **ssam said:**
> i say get rid of the whole WYSIWYG (what you see is what you get) idea.

you should work on the stucture of the document. so you add sections and subsections. which can be folded up like a filesystem tree view.

all formating is in a style sheet (appart from things like making a word bold).

then when you are finished (or when you want to preview), the document is rendered onto what ever page size you want.

(can you that i use LaTeX)

+1

---

### Post by popch on 2007-11-28
> **ssam said:**
> i say get rid of the whole WYSIWYG (what you see is what you get) idea.

you should work on the stucture of the document. so you add sections and subsections. which can be folded up like a filesystem tree view.

all formating is in a style sheet (appart from things like making a word bold).

then when you are finished (or when you want to preview), the document is rendered onto what ever page size you want.

(can you that i use LaTeX)

MS word did exactly that when I looked last time, with a so called 'Outline' mode. I can not find an outline mode in OO, though.

Why do you stop at making words bold? All literature on style sheets and so on suggests that you separate intent from looks at that level, too.

However, separating writing and formatting is not what most users known to me would prefer. It has, of course, also to do with education.

---

### Post by BobSongs on 2007-12-11
[FONT=Verdana]Meh, my two cents.

On the one hand: I agree. May it be that OpenOffice.org gets an interface that blows past anything MS has ever done. Let them look on, drool and copy the OpenSource community again.

On the other hand: I don't find a tool you feel familiar with "dated". Drop a long time Word user in front of MS Word 2003 and s/he's doing what s/he needs to do.

Drop the same person before Vista Word and the "ribbon" throws them. Productivity drops. Not good.

I imagine that those who learn Word with the "ribbon" are as productive as non-ribbon users. But to the seasoned user the change in interface can appear as "change for change's sake" -- yet another test of the MS users' patience: more re-learning the same interface while MSFT continues to find different ways to make it "new" again.
________________________

The problem with the Linux development community is: they often believe MSFT dollars spent in "ribbon" and other research are well spent. So it's just a matter of time until these ideas are ported to our interface. Linux developers don't have the same time/resources/money to spend offering test groups different interface choices.

Why must we feel MSFT's decision to go with the "ribbon" means it is beneficial? In a search over at **Download.com** I came across a small app that restored, to this glorious "ribbon", the standard menu choices and familiar icons for MS Office. The old-style menu is obviously desired, and the "ribbon" isn't so darn sexy that no one wants the old menus back.

Let's not get caught up in MSFT's hype. Sometimes I am led to believe these changes are done to see how much others will copy them (can MSFT actually be a trend setter?). Icons are nice, but I'm far too used to digging through menu choices from the menu bar to let MSFT remove these from me.
_______________________________

**Edit**: what I find irksome too is MSFT's certainty that everyone will love their new "ribbons". So much so that turning them "off" and putting Vista Office back (in my opinion) "as it should be" isn't possible. Odd that, huh? You can restore the Windows 95-style Start Menu in Windows XP. You can even do it in Windows Vista (in other words: their new Start Menu can be restored to the "old style" 2 generations in... but the "old stlye" Office menu bar cannot be restored on MSFT's first replacement). Imagine! But you cannot restore the Office interface, one you may have used since Windows 3.1 and MS Office 4.3.

And the idea of choice is why Linux is my O/S. If not GNOME, then KDE. If not, then XFCE. If not **bash** then **fish** or **csh** or ... well, you get my drift. If a "ribbon" is imitated partially or entirely in OpenOffice.org (or in the emerging OxygenOffice.org), then give me the choice to "go back" to a previous look/feel.

Uhm. OK. I'll get down from this here soap box now.
[/FONT]

---

### Post by Whiffle on 2007-12-11
> **ssam said:**
> i say get rid of the whole WYSIWYG (what you see is what you get) idea.

you should work on the stucture of the document. so you add sections and subsections. which can be folded up like a filesystem tree view.

all formating is in a style sheet (appart from things like making a word bold).

then when you are finished (or when you want to preview), the document is rendered onto what ever page size you want.

(can you that i use LaTeX)


I knew as soon as I saw the first line that you were going to refer to LaTeX.  Maybe its because I'm writing a report in Kile right now.  Since learning to use LaTeX (poorly, I'm still a noob), I get really annoyed with regular word processors, they're just so annoying!  They always try to predict what you're doing while you're doing it (like numbering), and that gets tedious when they don't do what you want.  Then you have to undo what it did wrong automagically, and it wastes time.  I like to type what I've got, hit Alt+1 and watch it pop up before my eyes as a perfectly formatted PDF file, without having to fight the talking paperclip.

Anyway, on the OP:
Toolbars:  I prefer them to be static, but with icons that I don't used removed.  I don't want them constantly changing while I work, its annoying.

Themes: This is pretty much already implemented.

button states:  not really sure whats different about that.

combined buttons:  I don't use most of the buttons (but other people might), so it wouldn't help me at all.

tabs:  Tabs are nice.  Split windows are even better.  Kile does tabs, Kword does split views.  I'd expect both to have both features in the not to distant future.


On office 2k7:
Can't stand it.  End of story.

---

### Post by igknighted on 2007-12-11
> **ssam said:**
> (can you that i use LaTeX)

If you were truely 1337 you would use troff/nroff and code it all... If I have to hear about how great troff is one more time from my 80 year old prof at school I swear to god...


EDIT: Xbehave, have you tried KOffice 2's beta's yet?  They seem like they me be similar to what you want.  And there's always google's office...

I'm not an XUL/Firefox fan.  I would prefer to see as few apps made with that platform as possible.

---

### Post by stmiller on 2007-12-11
Another vote for KOffice. 
KOffice 2.0 will be out early 2008, and looks to be great. KWord 2.0 looks like it will be a monster program.

---

### Post by hanzomon4 on 2007-12-11
OP you should be beat senseless for your poor choice in thread title!!

I'm joking, your thread title had me all ready for a new office suit :lolflag: Oh the letdown :( 
Love the philosophy behind your idea though :KS

---

### Post by Chilli Bob on 2007-12-11
> **ssam said:**
> i say get rid of the whole WYSIWYG (what you see is what you get) idea.

you should work on the stucture of the document. so you add sections and subsections. which can be folded up like a filesystem tree view.

all formating is in a style sheet (appart from things like making a word bold).

then when you are finished (or when you want to preview), the document is rendered onto what ever page size you want.

(can you that i use LaTeX)
  
That sounds awesome to me.  Methinks I'll be checking out LaTeX tonight.

---

### Post by hanzomon4 on 2007-12-11
What is LateX exactly? Like what do you use it for?

---

### Post by Erdaron on 2007-12-12
[LaTeX]("http://en.wikipedia.org/wiki/LaTeX") is popular type-setting format. It's kind of like HTML, only far more powerful.

Code view could be an alternative to WYIWIG view? You can work in WYSIWIG or LaTeX, and switch between the two with a press of a button. I mean, if I just need to write a simple essay, I don't need to see all those code guts.

How about having a suite engine (like gecko or webkit for browsers), on top of which you can build your own suite? This would allow people to design more specific GUIs, if they wanted.

---

### Post by Mr. Picklesworth on 2007-12-12
**The problem** with office suites is that they cater to two distinctly different audiences: Home users and business users. Business users care about getting all the functionality possible, and don't seem to care about how that affects usability or prettiness. Evolution, for example, is a program built for businesses. As a home user, it drives me crazy by being a bloated and ugly program to use, but I can see how a business would love it; it supports (or aims to support) every business scheduling solution under the sun! Microsoft's Outlook has the same thing going on.

Where this really shows is word processors. When word processors were a new idea, the idea of somebody using the things at home or "for fun" was unheard of. Microsoft designed their entire office suite around businesses, and as a result it is stuffed full of "business features." This sounds a bit weird, probably. What exactly does this business-oriented stuff offer that's so special? Nothing. *It's [business](www.dilbert.com).*
The important detail is that, like the bureaucratic back-end of most businesses, these programs never change, and end up very complicated for no good reason. They just stretch and stretch and stretch. Where one new feature is similar to another but does not quite account for some vague situation, it will be added *in addition to* that old feature. Nobody dares to rename something or rearrange a menu even if that would be to fix a serious usability blunder, because there is no telling what over-sensitive business it could adversely affect -- and their smelly bureaucracies may be slow and overcomplicated, but they sure can count money!
Don't believe me? Just look at the Options dialog. ...Oh, and don't forget Customize.

Office 2007 is an interesting example of how Microsoft is trying to change this matter. That interface is a serious revision, and it is the first time Office has actually had a pruning since the beginning of its existence. Microsoft realized that they have a home audience in addition to business users, and that Apple is really ready to dominate in that space as soon as people catch on to how much better their stuff is for the home. Office 2007 is an attempt to make the program easier and less businessy, and it is a noble attempt. However, as has been pointed out, it just does not cut it. It still has all those features such that there are way too many tabs and buttons to poke through. As soon as you break past the ribbon, you are back to the same old 1995-style dialog boxes. (They pulled the same trick with Vista's not-so-redesigned Control Panel).

In addition, Office 2007 still has every past version's way of doing things. That is, HTML-style layout limited to natural text flow. No absolute positioning without a fight. Only regular letter-style pages with margins alowed. (Unless you want to engage in an argument progressing through about six different dialog boxes). At this point, that can not ever change because it will break compatibility.

This is where Apple comes in. iWork is easy. It is great for home use because it has a dead simple interface (it does not need a crazy "ribbon" thing to be organized). Where Word would have piles of crazy table stuff and a "sidebar" object, iWork just lets people position any content absolutely wherever they like, and has all the other content flow around it. Thus, there is no need to mess with margins, tables, sidebars, borders... it just works how a home user looking for quick and easy word processing wants.

Apple's only problem is that they lack a program to compete with Microsoft in supporting those insane businesses. Frankly, I'm happy about this. The sooner these idiotically complicated business schemes die, the better, and from the supporting software is as good a place to start as any. As a free software person, I am also a big fan of small businesses. They keep things simple and generally benefit from cooperation much more than the collossal messes of workers do.

Microsoft did not anticipate these home users. The only big OS player that really seemed to is Apple, who go straight for the home users. Microsoft has built their entire collection of properties around businesses, and with their recent acquisition of very fun-oriented property, the scramble to catch up is palpable. Everyday users are left with MS Word because that is all they really know exists, and they are out of place with it.

Where does free software fit in? I think OpenOffice and Evolution are two great programs for businesses. They have every right to stay alive and kicking just as they are. Somebody likes them, and that "somebody" just happens to be a lot of money, advertising and general mass.
However, those programs both fail on most counts for supporting small home users who just want an easy way to create a flyer for their community rowing club. (Evolution's friendly documentation and happy vibes being the exception).

This is where a new project would be. If I was in charge, I would code-name it GNOME At Home until someone else came up with a title that wasn't horribly unoriginal. Hey, at least it rhymes! (You can tell I'm a GNOME person).
The mission: An easy document editor for people who want things to just work, and who are not insane business-loving lunatics that spend every minute of their waking lives worrying about "good value;" who also care whether things are nice.
And yes, I intentionally said "an easy document editor" in place of "an office suite". iWork shows us something else of interest: The distinction between Numbers, Pages and Keynote (and even iWeb) is practically zilch when the interface is so simple and the behaviour so similar. Really, the biggest difference is the output... but getting there is nearly identical. That confuses users who wonder what the difference actually is, and gets them worrying too much about which program to use. There are numerous examples of how this is bad. Back to the rowing club example (sorry, opposite example here): Scoring for a little regatta; Excel does calculating, copied to and printed via Word. The wrong use, sure, but it looks like all Excel does is a crazy table thing. Who wants the results looking like that?
Why not just merge them into a single decently designed program?

It we are not a crazy business that relies on fugly last-minute software built by in house PASCAL developers, we do not need that weird tables metaphor. A better choice would be simply "number crunchers", with inputs and outputs. I think the ideal metaphor there is wires, pipes or nodes, snapping together the inputs and outputs with number crunchers in between. We can expect anybody to grasp that metaphor, since it can be applied to many different concepts (two of which I listed: water and electricity). Furthermore, it's a heck of a lot more tidy than having the whole document become a table, it makes sense to keep everything under a single program, and it gives us a chance for some fancy compositing goodies. (Switch to work on number crunchers; page content fades to the background, hidden number cruncher stuff jumps to the foreground from behind the page. Cool). Neat thing there is the idea that a number crunching document can actually be as pretty and as nicely formatted as any other document. Put your table anywhere. Maybe use number crunchers to keep track of unusual things like the document's filing number as part of a template.

There are two spaces here, and they are simply incompatible. Instead of doing the Microsoft thing by trying to force them both together, let's give them both what they want.

---

