---
title: "Commercial user-space applications and the GPL,"
date: 2009-02-13
forum: Ubuntu Dev Link Forum
---

### Post by Gordon Bennett on 2009-02-13
I have been reading up on GPL and how it applies to user-space applications and I am still unclear as to how it affects them.

Therefore I am posting here if anyone has a clear insight into my question:

Do user-space applications that dynamically link to user-space GPL libraries fall under the licence's remit?  From what I have read - yes?

Hypothetically speaking, a certain major audio application manufacturer which has invested a lot of money in forming its company (paying its staff and programmers thereof) is looking to port their application to Linux.  There is a lot of code in that program that gives them a competitive advantage for the time being and therefore able to sustain the company and its programmers.

However, because dynamically linking to GPL libraries constitutes derivative works (according to the GPL license) they are subject to:
a) Releasing their application source - it could mean a more powerful company taking the source, releasing a GPL derivative and using their greater resources to undermine the original authors.
b) Spend money, resources and time writing their own libraries just to get a damn app running.  Even at that, the libraries they'd have to use even for simple operations could be cross-linked to GPL ones and so on.  Cue legal mess.

Also, this goes for BedroomCoder(tm), who discovers a wonderful new way to perform function X with an app.  Now, BedroomCoder(tm) doesn't want to work in a burger stand for the rest of their life - he/she wants to keep on what they like doing and make money off it - bills need to be paid too.  Either they join a corporate which is subject to the same thing as above, or have to be curbed by the same restrictions, or use another OS.


Now, I am not busting for a flame war here - just any insight/feedback into what is going on.  This has partly been prompted by posts from software houses and individual coders alike with the usual end comment of 'oh, but I don't need to release my source on OSX or Windows' (understandable; preserving time spent and investment when it comes to capitalise on that effort in view of them paying for their kid's college education) and see them stop development on Linux because the situation is so unclear.

Add to that the recommendation from GPL to rescind copyright to them (ugh) and suggesting that LGPL libraries use GPL instead gives me the impression that Linux is more of a platform for servers and their services, because they can operate from a sandbox, when it comes to earning a decent buck for coders.

And that's the thing - we all know there is a vast amount of companies out there keeping people in gainful employment because they base their Linux-based services as such.  But one can't do that with an app.  A host-based user-focused GUI application cannot 'sit back' behind a closed system like a program running on a server can.

I am aware of Maya et al - but look at their interfaces etc - it's almost like they actively avoid violating any possible GPL condition, which means ironically the host system's original user-driven functionality is left gathering cobwebs because it may or may not cause legal problems :/

GPL says one thing, Linus says another, others say it's unclear - leaving the choice for a developer to try walking across the minefield or take the alternate OS road next to it.

So, is there any certainty for commercial, host-based Linux-based user applications, or should they just move on to another system?

---

### Post by yse on 2009-02-14
We are in the same problem with our company.

We have used some so called "open source" libraries and now we seems to be forced to remove them or replace because of the license which don't work with commercial products.

To be clear, we just cant release the products with source code.

---

### Post by Gordon Bennett on 2009-02-14
> **yse said:**
> We are in the same problem with our company.

We have used some so called "open source" libraries and now we seems to be forced to remove them or replace because of the license which don't work with commercial products.

To be clear, we just cant release the products with source code.

Quite ironic, isn't it, when one doesn't have the problem with writing an app for a Microsoft OS.

I sent an email to the Linux Foundation for any clarification on this - if I can track down Linus, I'd like to hear his opinion too.

I was thinking of making an easy-to-reference library database, so people can check if they are using GPL or LGPL libraries - that takes time off my development in other areas, for something that's a non-issue on OSX or Windows.

And with all good intentions, imho this is one of the main reasons professional GUI-focused application developers run a mile:

[http://www.gnu.org/philosophy/why-not-lgpl.html](http://www.gnu.org/philosophy/why-not-lgpl.html)

To me, the contents of that link reeks of the opinion of someone with a secure paying job who has completely lost touch with what it's like to be a working programmer.  :(

While the situation is unclear, you have choice - if you want to make a living off what you do as an applications developer you can either a) spend money and time checking everything you link to in Linux is legally kosher or b) just do it on another platform.

---

### Post by amauk on 2009-02-14
If the library you are linking to is under the **GPL**, then your program constitutes a **derived work** (building off of the library) and so your program must be GPL too.

If the library is under **LGPL** and you have not modified it, then linking is not considered a derived work (rather, you are using the library as intended, not deriving from it). Your program does not need to be under the GPL in this case

licensing under GPL or LGPL is at the library authors discretion

If the library is a self-contained "unit" designed to operate independently from any function of the "parent" program, an author may decide to license it under LGPL

While GNU & the FSF do produce a license that allows non-free programs to link to free libraries, it is frowned upon

I do understand the reasons for wanting to keep a program proprietary, but understand that you are working against the flow of free software

The goal of free software is to produce the best software for end-users, while preserving the end-user's freedom to use software on their machines as they see fit

If you open-source your audio program and another company / group forks it and produces a better product than yours, this is to the benefit of the program's future and the benefit of it's end-users
This is a case of the authors hampering potential progress of their own product, and sooner or later an open alternative will crop up anyway

To open a product and maintain your revenue, you have to shift your role
Shift from program writing to support and services
You, as a company, have limited resources - You do not employ the best programmers in the world
We have lots (and lots) of programmers
The right people from the open-source community **will** find your program, and offer to help improve it in any way (this includes cutting you out, if you're acting like a boat anchor....)

But if you shift your role in the project, there's no reason not to maintain a revenue stream.

Take a look at other companies built around open source software, and see what their actual role is

You may find a better revenue stream than your current one
(and equally you may not, it's entirely dependant on your in-house expertise)

Opening a piece of software will cause an influx of new talent that is not possible for proprietary software to tap into
(christ, just look what happened to Blender when that got opened)


*edit*
Addendum,
As long as you give back to the community, everyone will be happy
Under the GPL, you are getting someone else's work for free, with only **one** condition
Don't try and take away that freedom

An author *may* consider selling you the library under a different license
(a la MySQL, etc.)
you _are_ going to give back, whether that be in code, or in money

---

### Post by yse on 2009-02-14
> **Gordon Bennett said:**
> 
I sent an email to the Linux Foundation for any clarification on this - if I can track down Linus, I'd like to hear his opinion too.


I doubt you can solve anything, as far as i know nobody will answer for a long time.


> **Gordon Bennett said:**
> 
While the situation is unclear, you have choice - if you want to make a living off what you do as an applications developer you can either a) spend money and time checking everything you link to in Linux is legally kosher or b) just do it on another platform.

As i told you, we really have problems with this licenses, especially that we have cross platform applications prepared for almost release. I think we will go for point b). excluding Linux. Sad but true.

> **amauk said:**
> If the library you are linking to is under the **GPL**, then your program constitutes a **derived work** (building off of the library) and so your program must be GPL too.

If the library is under **LGPL** and you have not modified it, then linking is not considered a derived work (rather, you are using the library as intended, not deriving from it). Your program does not need to be under the GPL in this case


*edit*
Addendum,
As long as you give back to the community, everyone will be happy
Under the GPL, you are getting someone else's work for free, with only **one** condition
Don't try and take away that freedom

An author *may* consider selling you the library under a different license
(a la MySQL, etc.)
you _are_ going to give back, whether that be in code, or in money

In both cases, we cant release the sources.

As far as i know, there are no companies who are doing commercial products and release the sources.

Who win? I dont know.. I think in both cases we all lose something.

Please take the discussion as mature as you can, a commercial company need to make investments for good products, need to offer support for their products on so on, that called quality sometimes.

---

### Post by amauk on 2009-02-14
> **yse said:**
> As far as i know, there are no companies who are doing commercial products and release the sources.Oh, there's loads

My original point was, if the library you're linking to is LGPL, you won't have to release the source.

I'd be interested to know why you can't release code?

if it's purely
"well, we now can't sell the software"
then it's like I said before, you'll have to alter your role as a company

You can't really "sell" open-source software
(aside from nominal costs of providing a stamping a CD and printing a manual)

You'd have to take on a different role
support & services is always a winner

look at companies like:
- RedHat, Novell, Canonical (Linux vendors, support & services around their OS's)
- Codeweavers (support & services around Wine)
- Alfresco (support & services around their Enterprise content management systems)
- SugarCRM (support & services around their Enterprise CRM software)
- MySQL (support & services around their open source database)
- Zend (support & services around PHP)

there's loads more
most go for selling support and services around an open-source project, because most people are not computer experts and will pay for installation, a support contract, custom alterations, etc.

There's also large pluses to opening up your software
not least, you'll gain all the advances made to underlying libraries at no extra cost

Say you are using:
- an open-source, cross-platform sound system like PortAudio (as used by Audacity and others)
- an open-source, cross-platform GUI toolkit like QT

Any new architectures / OS's that the underlying libraries are ported to, and your program will be automatically ported too

You do no extra work, and suddenly you're on a system that your competitors will have to develop for in-house

I think the main thing to take away from this, is you can't succeed in an open-source world using closed-source business models

Research and emulate existing open-source companies' models

---

### Post by yse on 2009-02-14
> **amauk said:**
> 
look at companies like:
- RedHat, Novell, Canonical (Linux vendors, support & services around their OS's)
- Codeweavers (support & services around Wine)
- Alfresco (support & services around their Enterprise content management systems)
- SugarCRM (support & services around their Enterprise CRM software)
- MySQL (support & services around their open source database)
- Zend (support & services around PHP)



There arent so many. You can give me another 10 examples, their are not even 0.1% from all software made today. I can call them, exceptions.

Also, we have some concurrence, so, WE CANT release the sources, no matter what. We have to protect our business and our software patents also.

We dont take in account WINE, there is nothing legit about it. We will not support WINE it in the futures also. Only native platforms. We cant afford any quality drops because of using WINE.

---

### Post by amauk on 2009-02-14
well, if you're not willing to open the source under any circumstances (which is fine, it's a business model)

You are not going to be able to use GPL'd code
(LGPL, yes, but you may be stung by future versions changing to GPL - then you'll have to fork the last LGPL release and maintain it yourself)

You will, most likely, end up having to develop all code yourself, in-house

If you write all the code, and do not use any 3rd party libraries written by others, then you can sell the program under any license you choose

---

### Post by Gordon Bennett on 2009-02-14
Thanks for your input so far dudes, all in the cause of clearing up what is sometimes seen as a messy licensing area indeed!

I sit in both camps myself - I have released code in public domain which could have made me a fair wedge of dinero, but didn't because I wanted to 'further the cause' - however, there's also A Real World Out There and not some utopian fantasy, hence an individual/business must survive by taking certain roads.
Heck, I worked in several software companies as a programmer, which is in turn akin to selling the code you produce.

We all gotta eat sometime :)

As for the service model - indeed that works, although that goes primarily hand-in-hand with servers and server-based apps - it is way more difficult for a programmer/software house to apply that model for a GUI-based application which is orders of magnitude more complex.
Also note that the service-based companies that were mentioned (and others) only really started making a difference after receiving huge financial backing.  The OSS-friendly Google wouldn't have been here if it weren't for a substantial Venture Capital investment.  It's the way the cookie crumbles.

I don't disagree with the GPL model - it's very noble, but what I feel should be cleared up for potential application developers on Linux is a clear 'you can make commercial user-space apps here*' or a 'it's just not the platform to do that kind of thing - use OSX/Windows instead'.

  *As has been pointed out, if your app is dynamically linking to LGPL libraries, that's fine.  But looking at GPL's recommendation for libraries to try to convert to GPL puts that into the realm of future uncertainty - that legal risk is one a company is not going to take.

For me, having heavyweight, commercial apps on Linux would be cool, but if it's not possible for companies to do that, it should be made clear to them.  Unfortunately, this is why I still keep my Mac as the 'useful' GUI-based apps are still developed on it.  I actually enjoy paying commercial/shareware fees to the authors for their effort - they deserve it.

P.S.  Sometimes I feel the GPL financially discriminates against programmers - how about trying the GPL on doctors and teachers here in the UK - they got their education free, so they should do what they do for free.  Never mind money for living :P

---

### Post by amauk on 2009-02-14
Commercial apps are no problem under Linux
as long as it is **your** app

taking other people's code (in the form of libraries) and basing an app off of them makes the app only partly yours

As long as you write the entire application, you can release it under any license you wish, and charge what you want

But it needs to be 100% written by you in order to do this

software is like lego
OS, GUI server, window manager, graphical toolkits, etc. etc. are components (lego bricks)

All software is built off of some other, lower down software

If you keep everything free and open, the open-source way, then creating a user level application is considerably less expensive

You do not need to code a sound server for your audio app, use an existing OSS library
Nor do you need to design a GUI layer, use an existing OSS toolkit
Nor do you need to code an update mechanism, or deal directly with networking, or buy licenses from companies to use this-or-that essential feature

All you do is write your specific "bit"
and your bit is the top half-dozen lego bricks on a tower 6-foot tall

Proprietary software on the other hand,
you need to code everything from the ground up
(or pay for the priviledge of using someone elses work for the lower bricks)

OSS drastically reduces the cost of software development, compared to proprietary, so it's a little difficult to compare the two like for like

OSS = top half-dozen bricks
Proprietary = everything but the bottom foot of bricks

---

### Post by Gordon Bennett on 2009-02-14
> **amauk said:**
> Commercial apps are no problem under Linux
as long as it is **your** app

taking other people's code (in the form of libraries) and basing an app off of them makes the app only partly yours



That's the main issue though - *it isn't the case with getting the same type of app operating on Windows/OSX* - so basically it should be clear: Linux is not for commercial applications that need to use provided system libraries to operate.

---

### Post by glotz on 2009-02-14
Ask the people who know if you're unsure [http://www.fsf.org/licensing/](http://www.fsf.org/licensing/)

---

### Post by Gordon Bennett on 2009-02-14
> **glotz said:**
> Ask the people who know if you're unsure [http://www.fsf.org/licensing/](http://www.fsf.org/licensing/)

Thanks, I wasn't aware they had direct licensing contact point (I thought just the GPL site did).  I have emailed them and await the reply!

---

### Post by glotz on 2009-02-14
You're welcome.

---

### Post by amauk on 2009-02-14
> **Gordon Bennett said:**
> That's the main issue though - *it isn't the case with getting the same type of app operating on Windows/OSX* - so basically it should be clear: Linux is not for commercial applications that need to use provided system libraries to operate.
What do you mean by "provided system libraries"?

Let's take Skype as an example

it's free (as in price) but proprietary
they could charge money for the purchase of the program if they wished

Uses QT for it's GUI (It's gone LGPL recently, but up till a month or so ago, you had to purchase a commercial license from Trolltech if you wanted the non-GPL'd license)

Uses libsound2 to interface with Linux audio
LGPL - can use but not modify

Uses D-Bus to interface with the GUI environment (under the AFL license - similar to BSD, allows code to be closed)

---

### Post by Gordon Bennett on 2009-02-14
> **amauk said:**
> What do you mean by "provided system libraries"?

Let's take Skype as an example

it's free (as in price) but proprietary
they could charge money for the purchase of the program if they wished

Uses QT for it's GUI (It's gone LGPL recently, but up till a month or so ago, you had to purchase a commercial license from Trolltech if you wanted the non-GPL'd license)

Uses libsound2 to interface with Linux audio
LGPL - can use but not modify

Uses D-Bus to interface with the GUI environment (under the AFL license - similar to BSD, allows code to be closed)

Indeed - but Skype's app isn't exactly rocket science; I am referring to more complex (commercial) apps.
And btw, Skype uses your bandwidth to route data.

---

### Post by yse on 2009-02-14
> **amauk said:**
> What do you mean by "provided system libraries"?

Let's take Skype as an example

it's free (as in price) but proprietary
they could charge money for the purchase of the program if they wished

Uses QT for it's GUI (It's gone LGPL recently, but up till a month or so ago, you had to purchase a commercial license from Trolltech if you wanted the non-GPL'd license)

Uses libsound2 to interface with Linux audio
LGPL - can use but not modify

Uses D-Bus to interface with the GUI environment (under the AFL license - similar to BSD, allows code to be closed)

I really think Skype got commercial license from Trolltech years ago. Rest of licenses from Trolltech, no idea really.

---

### Post by hridyagati on 2009-02-15
Hey all 

I want to know how benificial is using the Open Source using for the commercial purpose ... or we have to choose something as alternate for this....

Please help 
[http://www.hridyagati.com/](http://www.hridyagati.com/)

---

### Post by yse on 2009-02-15
> **hridyagati said:**
> Hey all 

I want to know how benificial is using the Open Source using for the commercial purpose ... or we have to choose something as alternate for this....

Please help 
[http://www.hridyagati.com/](http://www.hridyagati.com/)

Just check before you use any libraries the license, dont make the mistake like some of to be forced to replace important parts of code because of that.

---

### Post by saulgoode on 2009-02-15
If it has not already been mentioned, the Software Freedom Law Center has provided a very nice [GPL Compliance Guide]("http://www.softwarefreedom.org/resources/2008/compliance-guide.html") which I would recommend.

> **Gordon Bennett said:**
> I don't disagree with the GPL model - it's very noble, but what I feel should be cleared up for potential application developers on Linux is a clear 'you can make commercial user-space apps here*' or a 'it's just not the platform to do that kind of thing - use OSX/Windows instead'.
To me, the two licenses would seem to make things rather clear -- if the GPL permitted dynamic linking then there would be no need for the Lesser General Public License to exist. 

Amauk has stated things quite clearly. I would just add that you should look at the licensing of the libraries you wish to use. It has been my experience that the majority of libraries required for development on a GNU/Linux system are under the LGPL or one of the university licenses. I can think of one potentially "problematic" exception to this: [GNU's Readline]("http://tiswww.case.edu/php/chet/readline/rltop.html") library. Do you have a specific library in mind which is GPLed that you wish to use?


> **Gordon Bennett said:**
>   *As has been pointed out, if your app is dynamically linking to LGPL libraries, that's fine.  But looking at GPL's recommendation for libraries to try to convert to GPL puts that into the realm of future uncertainty - that legal risk is one a company is not going to take.
Yes, there is the possibility that an LGPLed library will be re-licensed as GPL; however, you will always have the specific version that was LGPLed available under the LGPL meaning you can continue using it as such -- and even update it as necessary for your needs. (Your improvements *to the library* would need to be shared, but your proprietary code would remain "safe".)

This is actually a better situation than with a proprietary library, where the licensing (or charges) for updated versions is changed and you are left with the choice of either retaining your immutable deprecated version or submitting to the licensing/charges. Note it is often a more significant factor (to an OEM or ISV) that the new library may demand otherwise unnecessary upgrades to other software, or hardware, components in the system. I.e., you (or your clients) need to add more RAM (even purchase a new computer altogether) or purchase a new OS in order to do what might otherwise be quite straightforward with a slight modification of an LGPLed library.

I would also add that while such re-licensing from LGPL to GPL is *possible*, it rarely if ever occurs. Free Software developers tend to be VERY respectful to the licensing terms specified by contributors and do not re-license code to prevent improvements from being accessible to previous contributors.

> **Gordon Bennett said:**
> For me, having heavyweight, commercial apps on Linux would be cool, but if it's not possible for companies to do that, it should be made clear to them. ...
Again, I think this *is* readily apparent (and Amauk has expressed it well). The intent of the two licenses seems to be clear: companies are free to write code for GNU/Linux and to dynamically link with LGPLed libraries, but not with GPLed code. The question of whether this distinction is legally valid is a decision for the courts, but unless a company wishes to litigate the right to link with GPLed, it would seem obvious they should avoid doing it. There is still a great deal of capability available through the LGPLed libraries (not to mention that of the permissive licenses such as BSD, MIT, X11, etc). 

And I used the term "GNU/Linux" above because I wish to address your concern about Linus Torvalds possibly having said something in contradiction to the GPL. Applications written for GNU/Linux (the operating system) do not link with Linux (the kernel). Like kernel calls on most systems, Linux calls are invoked by loading a register with a function number and executing a software interrupt. From a legal standpoint, prevailing opinion seems to find this methodology distinct from "linking" (either statically or dynamically) and it seems pretty well established that no derived work results from such an interface between code. 

Furthermore, invoking Linux functions should never (hardly ever, anyway) be done directly by an application -- to do so would be an extremely poor programming practice. Instead, it is standard procedure that an application make Linux system calls using the GNU system's Standard C Library, GLIBC (even other programming languages employ bindings to GLIBC for Linux functions, though there are substitutes available). 

Fortunately, GLIBC is licensed under the LGPL and so there should be no question concerning the legality of dynamically linking with it (even IF there were some question about the interrupt-driven kernel interface and even IF the Linux developers' assertions that making normal system calls does not result in a derived work were found invalid).

> **Gordon Bennett said:**
> P.S.  Sometimes I feel the GPL financially discriminates against programmers - how about trying the GPL on doctors and teachers here in the UK - they got their education free, so they should do what they do for free.  Never mind money for living :P
If you mean that the GPL doesn't particularly accommodate the commercially marketed applications paradigm, it doesn't. If GPL developers aren't interested in what you have to offer, I hardly see that as discriminatory. As to the finances of programmers of marketed applications (maybe 10% of programmers in total), like the T-shirt says, "*Your failed business model is not my problem*". I'm more concerned about the growth and improvement of the software/computing ecosystem as a whole -- the availability of powerful, useful source code being made available to all programmers -- than in the ability of a small percentage of programmers to keep their code secret for some temporary marketing advantage. 

Your idea of doctors or teachers serving free in exchange for the expense of their education seems to me a fine one -- and is actually implemented here in the States. I have a friend whose daughter is currently teaching on a reservation in Alaska who chose to do so in exchange for her college tuition and expenses. She considers it to have been a fair trade, just as programmers who use GPLed software consider it a fair trade when they contribute their code improvements in exchange for not having to code everything themselves.

---

### Post by yse on 2009-02-15
In other words good luck with GPL/LPGL. Honeslty... dont expect to much commercial software to soon on Linux.

From my POV, we have our development system cross platform, honestly, is much clear and easy to target MacOS instead Linux. I no wonder why some other commercial software developers prefer MacOS instead Linux.

---

### Post by Gordon Bennett on 2009-02-15
> **yse said:**
> In other words good luck with GPL/LPGL. Honeslty... dont expect to much commercial software to soon on Linux.

From my POV, we have our development system cross platform, honestly, is much clear and easy to target MacOS instead Linux. I no wonder why some other commercial software developers prefer MacOS instead Linux.

That's because of the perceived uncertainty with the whole process; saulgoode's excellent post shed a considerable amount of light on it.

Btw, I didn't start this thread to bash Linux over the head - just that sometimes tough questions need to be made to get the right answers - personally, I arrived at Linux from years of development in OSX due to Apple's extremely poor bug-fixing record stilting any progress.

On a side note: a friend pointed something out which commercial newcomers to the open source paradigm miss out on: trademarks.  If you notice, all of the service-based projects making a buck (MySQL, Apache, etc) have the leverage of their trademark names.

I hope this discussion will help potential application developers inform themselves more clearly on the situation.

---

