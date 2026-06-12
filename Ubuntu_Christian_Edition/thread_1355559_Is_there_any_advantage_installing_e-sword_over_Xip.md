---
title: "Is there any advantage installing e-sword over Xiphos?"
date: 2009-12-15
forum: Ubuntu Christian Edition
---

### Post by longtom on 2009-12-15
Hi,

I see some folks around here struggling with there e-sword installations.  Got me thinking....(dangerous...)

Why would one install a windows program with wine when you can use a Linux program which runs natively? 

In other words - what can e-sword in wine can do what Xiphos or Bibletime can't?

---

### Post by Axel777 on 2009-12-15
> **longtom said:**
> 
In other words - what can e-sword in wine can do what Xiphos or Bibletime can't?e-sword have quite a few things you will not find in other apps. 
- the search options is better,
- note taking capabilities with scripture links and Rich Text
-scripture bookmarks
- strongs hebrew and greek dictionary standard with install.  
- topic studies capabilities that can be saved and edited
- easy to use and learn interface.

The open source programs is good but e-sword is a program that are as good/better that many commercial bible study software out there.
Kudus to Rick Meyers for making such a great program.:popcorn:

---

### Post by refdoc on 2009-12-28
Show me one thing that e-sword does, that Xiphos does not do as well or better!

> **Axel777 said:**
> e-sword have quite a few things you will not find in other apps. 
- the search options is better,

xiphos searches are: singleword, multiword, phrase, indexed, Strongs, morphology, custom ranges, multimodule, regex. etc etc etc What does e-sword offer here that Xiphos does not have? 

> - note taking capabilities with scripture links and Rich Text

xiphos has ability to
- annotate individual verses,
- take study notes. Can be saved as plain text and as HTML
- create personal commentaries and export them for others to use them
- create journals  and topic studies
- all of the above can be saved as plain text and as HTML.

> -scripture bookmarks
Xiphos has a powerful ability to make bookmarks and can export them for sharing.
 
> - strongs hebrew and greek dictionary standard with install.
Xiphos has via the CrossWire and its own repo access to many dictionaries including several Strong based ones. These are deliberately not installed at install time to a) allow the user a choice between the deifferent ones available and b) to cater more appropriate to the fact xiphos is capable of running in a multitude of languages. 

It appears to us wrong and offensive to have a default install biased towards English language users.
   
> - topic studies capabilities that can be saved and edited

Please see above
> 
- easy to use and learn interface.


Xiphos uses a standard GTK/Gnome based interface which should be familiar to all Ubuntu users. Most stuff is easily discoverable, covered with tooltips and explained in a manual which comes along and is searchable via yelp. There is a IRC channel dedicated to it full of helpful people and this is accessible from within the programme.
 
> The open source programs is good but e-sword is a program that are as good/better that many commercial bible study software out there.
Kudus to Rick Meyers for making such a great program.:popcorn:

Without wanting to diminish Rick Meyers' work there is little or nothing in e-sword which is not available in Xiphos. There is of course a lot in Xiphos which does not exist in e-sword. Including the most important fact that Xiphos is open source and open to contributions - something Rick Meyers strongly and often rudely opposes.

The only current advantage e-sword can have (apart from simple familiarity) is the availability of certain for-buy texts.

Peter

DOI Xiphos and CrossWire developer

P.S.: Following Wiki page was made by us CrossWire developers to compare our different frontends:

[http://www.crosswire.org/wiki/Choosing_a_SWORD_program](http://www.crosswire.org/wiki/Choosing_a_SWORD_program)

It might be useful as a basis for discussion when you want to compare other programmes too

---

### Post by zerubbabel on 2009-12-28
On that last point, will there ever be a way to add licensed translations such as NKJ and NASB to Xiphos?

---

### Post by refdoc on 2009-12-28
> **zerubbabel said:**
> On that last point, will there ever be a way to add licensed translations such as NKJ and NASB to Xiphos?

There is a way to publish licensed translations and (for the publisher, not us) to make money from it - we will distribute an encrypted module, the publisher will sell the decryption key

Whether this is used depends more on the publishers than on us.

NASB we are working on and will hopefully we able to publish as a for-sale module.

The NET is sold in this fashion as is the German HfA. We have other agreements with non English publishers in the pipeline. 

NKJ - we never got any response on all our multiple enquiries. Please add to the pressure by asking too.

FWIW I always found that users asking publishers for whether their text could be made available is at least as powerful as if we developers ask.

---

### Post by jonathonblake on 2009-12-28
> **refdoc said:**
> Show me one thing that e-sword does, that Xiphos does not do as well or better!

Indus Valley Writing system support.

Do any TSP front ends have an export to PDF function? 

jonathon

Disclaimer: e-Sword and Pocket e-Sword documentation writer.

---

### Post by jonathonblake on 2009-12-28
> **longtom said:**
> 
In other words - what can e-sword in wine can do what Xiphos or Bibletime can't?

The major reason is that e-Sword has a number of resources that aren't available for TSP. (The Sword Project. Xiphos and Bibletime are the front ends.) The legality of those resources is a different issue.

The minor reason is that it is much easier to create resources for e-Sword, than for TSP.

jonathon

Disclaimer: e-Sword and Pocket e-Sword documentation writer.

---

### Post by refdoc on 2009-12-28
> **jonathonblake said:**
> Indus Valley Writing system support.

Do any TSP front ends have an export to PDF function? 


Complex Indic scripts can be displayed on Xiphos without problems. Everything that can be done by Pango can be done by Xiphos.

Export to PDF - all you need to do is to print what you want to print onto PDF.

I think you are scraping the bottom of the barrel here a bit.

---

### Post by refdoc on 2009-12-28
> **jonathonblake said:**
>  The legality of those resources is a different issue.

The legality of these resources is usually the defining one.

> The minor reason is that it is much easier to create resources for e-Sword, than for TSP.

1) Xiphos can create every single module form apart from "Bible" right within the programme.

2) Creating modules for CrossWire is well documented (see CrossWire's wiki)

3) While CrossWire's use of OSIS XML may appear as a hurdle, there is no such hurdle in the other formats - VPL for Bibles, IMP for everything.

VPL is exactly that Verse Per Line.

IMP is equally simple.

---

### Post by longtom on 2009-12-29
Ups...  now the last thing I wanted is to light a flame war.

I just wanted to know if, for my personal use, there is any advantage to install Sword with wine above Xiphos or Bibletime.  
I should add that I have done away with anything running in wine since I do not trust it as a reliable platform to run applications (with all due respect to everybody working on wine and based purely on personal experience).

From what I read above I will keep wine were it is and use rather a native Linux application for me bible study needs.  For what I need and use it it will serve my needs just fine.

Thank you all for your contributions.

---

### Post by jonathonblake on 2009-12-29
> **longtom said:**
> 
I just wanted to know if, for my personal use, there is any advantage to install Sword with wine above Xiphos or Bibletime.  

If you have any STEP resources, you can use them in e-Sword, assuming they aren't password protected.

>  For what I need and use it it will serve my needs just fine.

That is the crucial issue.  How well the specific application serves you specific needs.

If your needs/requirements are akin to those laid out for the SBL Bible Study Software Shootout, depending upon how many failures you are willing to tolerate, you have either none, or one semi-viable option for Windows, and one good option on Mac OS-X. Nothing in the mobile device market works. (Nonetheless, Olive Tree deserves credit for at least taking on that challenge. No doubt by this time next year, they'll be able to demo how to find all of the weak Hebrew verbs and the range of variations for each of the conjunctions.)

jonathon

---

### Post by Axel777 on 2009-12-31
> **refdoc said:**
> Show me one thing that e-sword does, that Xiphos does not do as well or better!



xiphos searches are: singleword, multiword, phrase, indexed, Strongs, morphology, custom ranges, multimodule, regex. etc etc etc What does e-sword offer here that Xiphos does not have? 



xiphos has ability to
- annotate individual verses,
- take study notes. Can be saved as plain text and as HTML
- create personal commentaries and export them for others to use them
- create journals  and topic studies
- all of the above can be saved as plain text and as HTML.


Xiphos has a powerful ability to make bookmarks and can export them for sharing.
 

Xiphos has via the CrossWire and its own repo access to many dictionaries including several Strong based ones. These are deliberately not installed at install time to a) allow the user a choice between the deifferent ones available and b) to cater more appropriate to the fact xiphos is capable of running in a multitude of languages. 

It appears to us wrong and offensive to have a default install biased towards English language users.
   


Please see above


Xiphos uses a standard GTK/Gnome based interface which should be familiar to all Ubuntu users. Most stuff is easily discoverable, covered with tooltips and explained in a manual which comes along and is searchable via yelp. There is a IRC channel dedicated to it full of helpful people and this is accessible from within the programme.
 


Without wanting to diminish Rick Meyers' work there is little or nothing in e-sword which is not available in Xiphos. There is of course a lot in Xiphos which does not exist in e-sword. Including the most important fact that Xiphos is open source and open to contributions - something Rick Meyers strongly and often rudely opposes.

The only current advantage e-sword can have (apart from simple familiarity) is the availability of certain for-buy texts.

Peter

DOI Xiphos and CrossWire developer

P.S.: Following Wiki page was made by us CrossWire developers to compare our different frontends:

[http://www.crosswire.org/wiki/Choosing_a_SWORD_program](http://www.crosswire.org/wiki/Choosing_a_SWORD_program)

It might be useful as a basis for discussion when you want to compare other programmes too

I have used Xiphos and I can respond to each of your comments but it would just end up being a flame war instead of a useful discussion.
If Xiphos was really better(more functional, easy to use) (And Xiphos is a great piece of software in my mind), then obviously all those people here would have run it only instead of struggling to get E-sword running in wine.
Either you have not yet fully used E-sword or you are in complete denial on its ease of use and functionality over open source equivalents.  Either way it would be useless to try and reason further. If Xiphos does the job for you, great, but I prefer what works best for me. So bye.

---

### Post by refdoc on 2010-01-02
You have made a number of very specific assertions which are demonstrably wrong.
To point this out in detail has little to do with flaming. 

I will always prefer a open source programme to a closed one, but then try and contribute that my preferrence will become the better solution. I do think we are on a good road here with Xiphos.

---

### Post by david_kt on 2010-01-02
For me, I would just leave it open for users to choose whatever program they would like to run. That is why I put both option available. But e-sword is not pre-installed due to license restriction. 

DK

---

### Post by Pepe Lebuntu on 2010-01-05
I've been having a look at Xiphos for the last few days, and so far, here's my 2 cents. I'm sure refdoc will be more than willing and able to show me where I'm mistaken in my thoughts of Xiphos inadequacies, but hey, on what I've seen so far, these are my thoughts.


[LIST=1]
[*]Xiphos has the advantage of being able to show the Biblical text kinda in the paragraph formats we'd be familiar with from print Bibles, and also allows for the usual printed headings should you want them. I'm not gonna get into the whole "headings are evil because they're not the inspired text" game - the point is, if you want them, you got them. E-Sword is just verse by verse, with no paragraphing, and no headings... and no choice about it.
[*]The huge problem Xiphos has, is the problem that E-Sword had for ages too - the "big-boys" like Zondervan not taking them seriously enough to create modules for them. Hence, no unambiguously legal and simple way for the average user to get the NIV, TNIV, NRSV, NLT, etc on thier Xiphos. No way of getting the BNTC or countless other modules. This is that classic "chicken and the egg" thing - Zondervan etc won't take Xiphos seriously enough to license and create modules until its used widely enough, but it won't be used widely enough until it gets these modules. E-Sword had to deal with this, and so will Xiphos. The fact that the first one of these "big-boys" that Xiphos will probably get is the NASB from Lockman is indication of this, since that's one of the first that Rick Meyer got too.
[*]Aesthetically, both look awesome and are highly functional. E-Sword has some more easy ways to show/hide bits-and-bobs, such as sliding the dictionary or whatever to the side, and just floating your pointer over it to get it to pop out. But these are all easily replicable for Xiphos - they should just use some of the function keys shortcuts for the show-hide functions in their menus, and that'd do it. The ability to change the background color, and color-scheme generally (important for the eyes!) is much easier in Xiphos.
[*]I also think that in Xiphos the need to open a commentary in a pop-up window just to edit it is going to get real annoying. I'd also say the Personal Commentary module shouldn't be a module, it should just come as standard.
[*]Xiphos should take a leaf out of E-Sword's book, with regard to where Personal commentaries etc are stored. They should be specifically directed somewhere else from the rest of the modules, namely, under the Documents Folder (or wherever the user wants to). This would significantly increase the ability to back up personal commentaries, imo, without having to put EVERYTHING in the one folder.
[*]Putting the Strongs numbers underneath the word rather than side-by-side is going to win some people, and lose others. I like it. Point is, if this is open-source, each user should (and probably one day will, I suspect) be able to choose exactly how we want this to work for ourselves.
[*]While I greatly appreciate all the work JB and DK have put into their E-Sword installer, there are still little bugs that pop up here and there, as you would expect with a Wine reliant program. These include not being able to often change the default study notes format, which I've mentioned in another thread. I've managed to get that working, but hey. Also, unlike other Wine programs, E-Sword doesn't seem to be able to change its format to the color scheme etc that you put into the Wine Configuration. It's a little thing, but can be annoying. The fact is, though, all of these will become a massively mute point when Rick Meyer makes a linux version of E-Sword (and it's gotta be when, not if - he's far too cluey not to do it eventually, especially if we all keep asking him to).
[*]I consider E-Sword semi-open source, in that many of its modules are free, as is the program, which means that altruistic spirit of open-source is evident. You can put together a nice Bible system, with ESV, GNB, KJV w/ Strongs, Strongs itself, and Barnes and Clarke etc together. But we all know that E-Sword AIN'T open-source - it's code etc are locked in stone. This will cost it in the long run, and is why I suspect Xiphos will eventually - perhaps quite a while in the future, but Who knows - overtake it.
[*]Let me explain that last point - Xiphos will be able to do what Firefox has been able to do, have all manner of add-ons. Yes, E-Sword has modules for comms, dicts, bibles, maps etc, made by users, but that's not what I'm talking about. It's other things, that go beyond these three or four things, entire functions that Rick Meyer can't have even thought of yet. Some bright spark out there has come up with some cool function they WISH was in their Bible study software - the ability to use google-translate for their French Bible, for example (I'm just making this up, but you get the idea...). In E-Sword they have no way of integrating that, other than emailing Rick Meyer and asking him to do it for them - and everybody else - in the next update. Xiphos is open source, so such add-ons will become commonplace.
[*]Actually, here's an add-on somebody can make - an Open Office plugin for pasting Xiphos into odts. As linux users, we don't use Word, and you know there's no way Rick Meyer is going to make one for linux oo users! The point is, somebody in Xiphos doesn't NEED to do this - because it's open source, somebody else can do it. This will become a MAJOR advantage for Xiphos.
[*]Xiphos' module manager is pretty good, but will improve to be even better. It's heaps better than the module-by-module way we have to do things in E-Sword. They should include an option for actually updating the whole program to the latest version in their module manager though. I downloaded Xiphos from Synaptic some time around the 3rd of January, and it was still the old version, despite an update coming out on Christmas Eve. It should either be updateable from Ubuntu's Update manager (which is unlikely), or from its own module manager.
[*]If somebody can make an easy-to-use automated converter from E-Sword SQL format to Xiphos formats, that will go a long way to giving it a boost. I appreciated refdoc's guide to converting them contained in another thread, but for the average user, I suspect this is just unmanageable at the moment. Y'know, that'd be a cool add-on for some open-sourcer to make for Xiphos...
[/LIST]
Well, that's a long post, and I apologise if it's too verbose, but I hope it helps you out making your choice, and promotes further discussion about the pros-and-cons of the two programs. Bottom line - to God be the glory, and may His word be read, better understood, and proclaimed more faithfully, through either or both of these wonderful tools.

---

### Post by longtom on 2010-01-06
Pepe Lebuntu,

Thank you very much for your comprehensive post.  That certainly helped me a lot to form a opinion about the subject.

Apart from the mechanics of the programs itself one needs to work in the open source factor in.  I didn't do that and now, since you put my nose into that direction, my perspective on the subject is somewhat changed.

Thank you once again.

---

### Post by refdoc on 2010-01-06
> **Pepe Lebuntu said:**
> I've been having a look at Xiphos for the last few days, and so far, here's my 2 cents. I'm sure refdoc will be more than willing and able to show me where I'm mistaken in my thoughts of Xiphos inadequacies, 

Thanks for the very thorough and useful review. There are some points where I think i should respond to specifically.

> I also think that in Xiphos the need to open a commentary in a pop-up window just to edit it is going to get real annoying. I'd also say the Personal Commentary module shouldn't be a module, it should just come as standard.

Noted and will be passed on.

>  Xiphos should take a leaf out of E-Sword's book, with regard to where Personal commentaries etc are stored. 

Noted and passed on. 

> Let me explain that last point - Xiphos will be able to do what Firefox has been able to do, have all manner of add-ons. 

We have thought about this from time to time. As such the developers community is both very small, very friendly and very open (I got my svn login shortly after my first submission), so there is ample space for people to join and contribute. Whether a plugin mechanism would enable more contribution or dievert teh few current developers is a debateable point of view. Xiphos is currently far removed from Firefox in terms of ubiquuitousness and developer popularity. On teh other side, I have seen much smaller projects doing well with a plugin mechanism. 

Anyway, noted and will be passed on.

> Actually, here's an add-on somebody can make - an Open Office plugin for pasting Xiphos into odts.

Right - Xiphos builds on libsword from CrossWire. There is no specific need to go via Xiphos to achieve this (apart from building up an actual module library, unless you want to do this via command line - possible). In fact only 2 days ago someone published a python script which plugs into Autokey (see repos) and uses the sword modules library installed. It is a bit rough and ready but it does the job. And i am sure someone could make it a lot better very soon. It works by hitting a chosen key combination and then you can paste in text into any programme (not just OOo) you are working with. I am using it on Lyx. I do not have the link here right now, but will post it later.

> As linux users, we don't use Word,

With Autokey you could paste even into MS Word (if it runs on Wine). Not that I would want to...

> Xiphos' module manager [..]should include an option for actually updating the whole program to the latest version in their module manager 

This will likely not happen on Ubuntu. It goes against the grain of Ubuntu and Debian packagemanagement and will not endear us with anyone in charge. 

On Windows it is indeed the most common way of ensuring autoupdate and we have thought about it. But i guess whatever we do, it will likely get disabled unless it can be made to work with the package manager. 

Having said this, we have now an excellent team of packagers which means that Ubuntu is actually seeing recent relases. It did not until recently.

> If somebody can make an easy-to-use automated converter from E-Sword SQL format to Xiphos formats, that will go a long way to giving it a boost. I appreciated refdoc's guide to converting them contained in another thread, but for the average user, I suspect this is just unmanageable at the moment. Y'know, that'd be a cool add-on for some open-sourcer to make for Xiphos... 

There have ben various rumours of lawsuits in the making directed at anyone ever considering to do so. Jonathon (here present on the list) has been very active in frightening people away from doing such things. He knows what I think about him and his behaviour.. We have approached Rick Myers in the past in a very open and honest way about this matter and were given essentially short shrift but little actual substance as response. The emails are up somewhere for public perusal. 

So, with this in mind, i would not suggest that anyone goes down this route unless they know exactly what they are doing (legally) and is willing and happy to put up with some nastiness along the way. I am not. what I published is public knowledge gleaned from various places. I have never used it to produce my own imported modules nor do I have any intention to do so. 

This experience has made me even more committed to using open source only, particularly in Christian matters. What we produce should be freely accessible to others and should be open to adaption and improvement.
>  Well, that's a long post, and I apologise if it's too verbose, but [..]

And mine now too.... :-)

---

### Post by refdoc on 2010-01-06
* deleted as double posted*

---

### Post by jonathonblake on 2010-01-06
> **Pepe Lebuntu said:**
> 
 the point is, if you want them, you got them. E-Sword is just verse by verse, with no paragraphing, and no headings... and no choice about it.

There have been several RFEs for pericopes within e-Sword.  Thus far Rick hasn't chosen to create it.  (My guess is that two issues are at play here: Rick doesn't see the point of such a component, and the libraries he uses make implementation non-trivial. If he does implement it, it probably would accept user created pericope resources.  At any rate, the current work around is to create the pericope headings in a commentary file.)

The "display paragraph" option that Xiphos has, is a direct result of the different philosophy that _The Sword Project_ has, about how content should be stored. (Technically, it is about the difference in markup, but it comes back to storage issues.)

> the "big-boys" like Zondervan not taking them seriously enough to create modules for them.

Open source scares content copyright owners. Their fear is that by releasing content in an open source program there will be widespread distribution of that content, in other, unapproved formats.

AFAIK, _The Sword Project_ is the only FLOSS Bible Study Program that has gained any traction, and retained its FLOSS license. 

> [*]Xiphos should take a leaf out of E-Sword's book, with regard to where Personal commentaries etc are stored. They should be specifically directed somewhere else from the rest of the modules, namely, under the Documents Folder (or wherever the user wants to). This would significantly increase the ability to back up personal commentaries, imo, without having to put EVERYTHING in the one folder.

That is an ironical criticism of Xiphos, since one of the current criticisms of e-Sword is that it puts content into two different directories.

>  E-Sword doesn't seem to be able to change its format to the color scheme etc that you put into the Wine Configuration. It's a little thing, but can be annoying. 

The colour scheme used by e-Sword is picked up from the Windows theme.  If you can figure out what registry setting that is, you should be able to create/change it for e-Sword.

> The fact is, though, all of these will become a massively mute point when Rick Meyer makes a linux version of E-Sword (and it's gotta be when, not if - he's far too cluey not to do it eventually, especially if we all keep asking him to).

I'm not that confident that Rick will create a version of e-Sword for Linux.  More precisely, I expect to see a version for Mac OS X, prior to seeing one for Linux.

Until Microsoft files Chapter # 7 bankruptcy, Linux usage on the desktop will always be a hotly debated issue.

> I consider E-Sword semi-open source, in that many of its modules are free, as is the program, which means that altruistic spirit of open-source is evident.

I think "closed source, open architecture" is a slightly better way to describe e-Sword.  Regardless, the ability for users to create their own resources, that can be integrated into the program, is something that most of the closed source Bible Study programs do not offer.

> E-Sword AIN'T open-source - it's code etc are locked in stone. This will cost it in the long run, and is why I suspect Xiphos will eventually - perhaps quite a while in the future, but Who knows - overtake it.

Replace _Xiphos_ with _The Sword Project_, and you might be correct. The big issue is always going to be resources. Will users be willing to pay for the content.  

_If_ an average price of US$100.00 per resource is acceptable, then the resource issue is solved. OTOH, if the only acceptable price is gratis, it isn't solvable.  FWIW, the same thing applies to e-Sword.

>  It's other things, that go beyond these three or four things, entire functions that Rick Meyer can't have even thought of yet. Some bright spark out there has come up with some cool function they WISH was in their Bible study software 

Some of those things are available in third party utility programs for e-Sword. However, distribution of those programs is a copyright violation.

>  Xiphos is open source, so such add-ons will become commonplace.

Those add-ons probably will be more in tune with the original Unix Philosophy, than the Microsoft philosophy that Xiphos takes as its guiding principle.

> [*]Actually, here's an add-on somebody can make - an Open Office plugin for pasting Xiphos into odts. As linux users, we don't use Word, and you know there's no way Rick Meyer is going to make one for linux oo users! 

The utility to paste Sword Project content into OOo is either in alpha or beta testing. (Come to think of it, I don't think it is is OOo specific. Nor will it be Linux specific.)

The big issue with OOo specific macros, or extensions, is the learning curve for the OOo API. (You basically have to study the entire OOo code base, in order to grok what the API is trying to do.)

> Xiphos' module manager is pretty good, but will improve to be even better. It's heaps better than the module-by-module way we have to do things in E-Sword. 

That module by module thing is an artefact of how e-Sword resources are distributed.  There are scripts for copying both non self-executing archived, and unarchived resources into the appropriate e-Sword directory. However, the self executing scripts, and the ones constructed with program installers still can only be done one by one.

jonathon

---

### Post by jonathonblake on 2010-01-06
> **refdoc said:**
> been very active in frightening people away from doing such things.

Thus far, Rick, Phil, I, and a couple of other people have managed to talk most of the lawyers, and the organizations that they represent, out of filing criminal, and/or civil charges against resource creators and software developers. (In one instance, the court dismissed the case due to a lack of service.)

jonathon

---

### Post by ransom1982 on 2010-06-08
> **jonathonblake said:**
> 
Those add-ons probably will be more in tune with the original Unix Philosophy, than the Microsoft philosophy that Xiphos takes as its guiding principle.


We take the Microsoft philosophy as the our guiding principle? That's pretty funny.

At any rate, background work is going on now to provide plugin mechanisms. Eventually plugins will be able to be written in Python, C, Vala, C#, and Javascript. Probably it will be a year or so before it is ready.

---

