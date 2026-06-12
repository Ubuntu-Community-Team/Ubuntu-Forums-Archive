---
title: "(The Lack Of) Documentation: The Bane Of Linux"
date: 2007-12-11
forum: The Cafe
---

### Post by Duneatreides on 2007-12-11
My name is Chris.  I am 25 years old and I have been using Linux (or GNU/Linux for those are whinny and technical) for approximately two years now.  My first experience with linux was Ubuntu 5.10 "Breezy Badger".  Overall I was impressed with Ubuntu 5.10.  It was simple and user friendly, but straight from the get-go I ran into a major problem:  I couldn't mount the floppy drive.  Remember, at that time all of my computing experience was with Microsoft and despite all of unscrupulous design choices that Microsoft made, at the very least when you want to read/write to a floopy on Windows you can do it.  I had no clue on how to fix this problem, in fact I didn't know anything about linux at that time.  As it turns out, the pmount had a bug in it and it was resolved when I upgraded to Ubuntu 6.10. 
 
	As my experience with linux grew, I learned that I could get on the forums and ask questions to help me with my problems, then I ran into RTFM (Read The ******* Manual), or various other acronyms such as GIYF (Google Is Your Friend) etc etc followed by a link to Eric S. Raymonds paper "How To Ask Questions The Smart Way" [1].  I can understand from a "Hacker" perspective why Eric S. Raymond wrote this, and from that stupid "Hacker" perspective it is logical.  However, I am not a "Hacker".  I do not give a damn about programming, and the only reason I am interested in learning to program is that I know as an engineer I will more than likely need programming skills.  I am a user, and from a "User" perspective than Eric Raymond's paper is fairly condescending.  It also does not make much sense either because of the 800 pound gorilla in the Open Source World:  Microsoft.  

	I don't give a damn what your views are on Microsoft: the fact is that Microsoft, either legitimately or illegitimately, currently dominates the operating system world.  According to W3Counter.com, Internet Explorer has 62.36% of the market while Firefox has 27.77% of the market.  The operating systems adoption statistics, according to W3Counter.com is Microsoft has 90.25% of the market while Linux has 1.77% of the market [2].  Note, these statistics were gathered from one website only, W3Counter.com and depending on the methodology used other websites will report different values.  Now if the Open Source world wants to increase it's market share it is going to have to take people away from Microsoft.  Linux is in direct competition with Microsoft, and due to the cost involved in changing operating systems Linux has to make a strong case to convince someone to switch.  

	Linux has been, and probably will be, an operating system for the technical user.  There is nothing inherently wrong with that, but the problem lays in the fact that is currently only geared toward the technical user.  Those millions of people are locked into the Microsoft way of thinking and generally they are not technical users.  If Linux wants to increase its user base, it has to accommodate the non-technical user.  Further more, non technical users do not read highly technical computer manuals, cryptic man pages, or generic README files.  In fact, they do not give a damn because in their mind they have have more important priorities than to scour a generic computer generated README file, maillists, forums, or anything else for that matter.  The non-technical user just wants his/her software to work so they can be productive.  

	It can be argued that documentation for open source is ridiculously incomplete, and yet when people have problems and asks what the "Hackers" consider a stupid question, they are told to read the manual.  To all the "Hackers" everywhere here is a news flash:  YOUR ******* MANUAL IS A PIECE OF ****.  IT IS WOEFULLY INCOMPLETE, CRYPTIC, AND GENERALLY ONE MUST BE DONALD KNUTH TO TIE THE PIECES TOGETHER.  Sorry about the profanities.
 
	What do I suggest in this rant?  Software developers should stop coding for a minute and write some damn documentation in a clear and concise manner.  Do away with the automatically generated README file and actually write a real README that deals with the software you are coding.  Include a comprehensive INSTALL README that tells the user how to install the software, and a COMPLETE list of dependencies and include a COMPLETE build order to resolve those dependencies.  You had to do it anyway when you wrote the software, so why not document it and tell the rest of us so we don't have to re-invent the wheel.  I would like to give praise to GNOME in this regard since they have included both a complete dependency list and the proper build order [3].

	I know what people will say.  "You can help write the documentation!".  True, I could help write the documentation If I knew the software!  I can just imagine what would happen if I signed on to help write the documentation for some project, lets call it Ultra-Foo.  So I ask the development team "What are the dependencies?  What is the build order?  How do I install It? Are there any caveats or special installation/configuration steps that needs to be done?"  Since I want to write complete and thorough documentation, I will probably end up pestering the development team and pissing them off.  

	Another suggestion is not release software until the documentation is up to date.  For example, XFCE released version 4.3 ( I believe) of their Desktop Environment, and I was interested in trying it out.  I read on their website that the 4.3 documentation was not up yet but you can consult the version 4.2 documentation , mailing list, and forums to resolve any problems.  As soon as I read that, I hit the back button and I haven't been to XFCE since.
  
	This is becoming a long, rambling rant so to close:  Software developers out there, your amazing software project is absolutely worthless without decent documentation.  Take a few hours to properly document your project, include a complete installation guide (including dependences and build order), and a user guide.  These few hours of work will save you the hassle of the "nOObs" from bugging you on a constant basis.  Eric S. Raymond's "How to Ask Questions The Smart Way" is often on a must read list for any newcomer to linux.  Therefore I propose that the following be required reading for software developers.  The first is Eric S. Raymond's "The Luxury Of Ignorance: An Open Source Horror Story" [4].  I found this amusing as that Mr. Raymond experience first hand what newcomers to linux experience, and how the lack of documentation is a large part of the problem.  The second required reading is Joseph Betz's "Why Bill Gates Is Still Rich" [5].  Joseph Betz discusses some of the least discussed problems of linux.  

References

[1] 	"How To Ask Questions The Smart Way"
	[http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html)

[2]	W3Counter
	[http://www.w3counter.com/globalstats.php](http://www.w3counter.com/globalstats.php)

[3]	Gnome 2.20 Dependency and Build Order
	[http://www.gnome.org/start/2.20/notes/en/index.html#rninstallation](http://www.gnome.org/start/2.20/notes/en/index.html#rninstallation)

[4]	"The Luxury Of Ignorance: An Open Source Horror Story"
	[http://www.catb.org/~esr/writings/cups-horror.html](http://www.catb.org/~esr/writings/cups-horror.html)

[5]	"Why Bill Gates Is Still Rich"
	[http://www.newhorizonssucks.net/LiveCD.html](http://www.newhorizonssucks.net/LiveCD.html)

---

### Post by 23meg on 2007-12-11
[QUOTE=Duneatreides]
I know what people will say. "You can help write the documentation!". True, I could help write the documentation If I knew the software! I can just imagine what would happen if I signed on to help write the documentation for some project, lets call it Ultra-Foo. So I ask the development team "What are the dependencies? What is the build order? How do I install It? Are there any caveats or special installation/configuration steps that needs to be done?" Since I want to write complete and thorough documentation, I will probably end up pestering the development team and pissing them off.[/QUOTE]

Do you "know" Ubuntu? You've been using it for two years, so perhaps you do to some extent. You could probably help Ubuntu's documentation.

The [documentation team]("http://doc.ubuntu.com/") has a [style guide]("http://doc.ubuntu.com/ubuntu/styleguide/en/index.html"), which addresses some of your complaints with documentation in general.

---

### Post by regomodo on 2007-12-11
well. I didn't read all of your post but i mainly agree with what i read. 

It miffs me of a treat which is why when i can't find any guides/help out there in the web/wikis/irc i post it on my blog and then to appropriate wikis.
I also do it as i have a habit of borking installs and i don't want to spend hours trying to figure something trivial out again.

---

### Post by p_quarles on 2007-12-11
Non-technical users don't read the documentation. They usually rely on job training, family and friends who are computer-savvy, and intuitive GUIs. The Ubuntu project is largely about getting to a point where a solid, featureful GNU/Linux distribution can be used without needing any documentation. 

I mean, this is what Mac OS X aims for: Apple's idea of a good user experience is not needing a manual. OpenBSD, on the other hand, is exhaustively documented, and I dare anyone to tell me that OpenBSD is geared toward the "non-technical" user.

---

### Post by 23meg on 2007-12-11
[QUOTE=p_quarles]Non-technical users don't read the documentation.[/QUOTE]

The majority of them don't sit down and *read* it, but some do skim through it when they run into problems, which is why non-technical user oriented documentation should [facilitate scanning]("http://doc.ubuntu.com/ubuntu/styleguide/en/scanning.html").

---

### Post by daynah on 2007-12-11
I always thought the best documentation was another person. I mean, that's why we go to Home Depot classes and get How To Videos instead of reading the techinal manual that comes with the tool.

From that point of view, I think Ubuntu (Ubuntu specifically) has a leg up. All of the "documentation" (the community) is in one central easy to find location. It's easy to understand (there's a forum and chat for most languages and everyone here is speaking casually) and it's easy to empliment (copy aand paste).

I'm an average, non technical user and I never use man and no matter how much work ya'll put into it I never will. I'll just whine here, thanks. :)

---

### Post by HermanAB on 2007-12-11
Stop moaning, go to tldp.org and write some docs.

---

### Post by igknighted on 2007-12-11
I think the system-wide documentation needs to be done by the distro, and that means volunteers.  Every app in the repo has a spec sheet that has all the depends and everything else listed, so you can get that info without pestering anyone.  I think that it is unreasonable to expect the writer of a piece of software to write documentation relevant for every user.  If a distro aims to be "easy for new users", they should write their own documentation.  If you were talking about on a per-application basis (say, how do you do ___________ in rhythmbox), I have found that the documentation available is usually very good, but if you have found otherwise, what did you find lacking?

Unfortunately, writing documentation is not cool or glamorous, even amongst geeks.  So it often doesn't get the attention it deserves.

---

### Post by Krydahl on 2007-12-11
I've been using Ubuntu since July - a noob in other words.

I'm already seeing questions asked that I've found answers to by searching. Why didn't this poster do a search, I can't help wondering.

Much of the advice in "how to ask questions" seems like common sense to me, not arrogance.

Sure, the documentation isn't great. Have you ever read Microsoft's? Have you even seen it? Most OEM PCs don't include any.

Difference is, almost everyone knows someone who knows their way round Windows. Plus, there are loads of good books on the topic.

There are quite a few books on Linux these days too, but with a distro like Ubuntu they have a nasty habit of being out of date before they hit the shelves.

The truth is, documenting software is hard. I used to write software (professionally for a large company) and I can tell you that our documentation was complete crap. I don't think I've ever met a software engineer who enjoyed doing the documentation.

Big companies pay people to document - and those poor folk have to prise the information out of the coders with threats.

So in the open source world, where most coders are doing it voluntarily, it's hardly surprising that the documentation lags. 

Personally, I think the online documentation for Ubuntu makes a pretty good stab at the basics - but it is far from perfect. I can't see a good solution though. In my view, getting the individual responsible for the code to do the documentation doesn't work. They're too close to it. They make assumptions about what's obvious, because to them it is - they've been living inside that piece of software for months, often years. The best solution is to have a technical author who spends time trying to install and use every aspect of whatever is being documented, who has a hotline to the engineers responsible for the coding for when he gets stuck, but who doesn't know how the thing works when he starts - but that's not going to happen in the FOSS world is it?

So, while I understand your plea, I can't see how to fix it. 'Cause asking the devs to write everything up, I can almost guarantee will fall on deaf ears.

---

### Post by aysiu on 2007-12-11
I agree with a couple of your points (the Eric Raymond piece being a bit outdated or irrelevant in the desktop Linux world, the *man* pages and README files being cryptic), but I don't know if I agree with your solution.

My response to the Raymond piece is [here](http://ubuntucat.wordpress.com/2007/08/06/getting-the-best-help-on-linux-forums/).

What new user is going to read a well-written README file and compile from source and care about the build order of dependencies? Instead of developers putting their energy into making what you consider a proper README file, I'd rather they just package their programs as .deb and .rpm files and get them into software repositories, so new users don't have to worry about dependencies at all.

---

### Post by Darkhack on 2007-12-11
What really upsets me is a lack of developer documentation.  "Read the code" is not an acceptable answer to someone who wants to contribute patches to a project.  Some applications are easier than others and reading the source code is an acceptable means of learning, but some projects will have millions of lines of code and no documentation on how they all work together.

---

### Post by sloggerkhan on 2007-12-11
What's really missing are annoying intro tutorials for every app... ;)
Quite honestly, those are actually how I've learned a fair bit of software, as sad as it sounds. They get you going to point where you get the gist of things and can take off.

---

### Post by red_Marvin on 2007-12-11
The op brings up a couple of good points, but I see a possible flaw in the conclusion that developers should write more documentation, which I mean is a little like asking the car engineers to handle the driver's tutoring -being good at one doesn't imply being good at the other.

---

### Post by hanzomon4 on 2007-12-11
> **red_Marvin said:**
> The op brings up a couple of good points, but I see a possible flaw in the conclusion that developers should write more documentation, which I mean is a little like asking the car engineers to handle the driver's tutoring -being good at one doesn't imply being good at the other.

True, I also disagree with the OP's thoughts on Including a comprehensive INSTALL README, build order, etc... That is information users don't need. Only the packagers should need that info, and perhaps advanced users, in either case I'm sure they can get the info they need(I know I can).

---

### Post by glotz on 2007-12-11
Yes, it is called GNU/Linux! I just wished to point out that documentation is always the problem with everything. And there's no reason to flame and rant. Let's keep it constructive, shall we?

---

### Post by LaRoza on 2007-12-11
"Write me free software, then write a book for the average person to understand"

---

### Post by pjkoczan on 2007-12-11
Half of the problem is that the people who are qualified to write documentation are also some of the poorest people to do so. Knowing what they know, they tend to skip steps or assume that people know what they're doing behind the scenes, which are often unreasonable assumptions to make. There is quite a bit of merit to the idea that non-experts (i.e. not the programmers) should write tutorials and user-level documentation and leave the programmers to write the cryptic manuals. Unfortunately, they'll need to struggle and learn through it as well. It's a nice pseudo-chicken-and-egg problem.

I've written quite verbose documentation for aspects of my job, and when teaching some of these things to other staff, I realize that I've skipped a lot of steps that I thought were trivial.

Also, as part of my job I teach new students the basics of Unix so they can do their coursework. I tell them about man pages and how to use them, but they quickly learn that there is a *huge* difference between manuals and tutorials.

---

### Post by hanzomon4 on 2007-12-11
OP what do you think of Freebsd's documentation? It's touted as the best documentation for any OS.

---

### Post by igknighted on 2007-12-11
> **hanzomon4 said:**
> OP what do you think of Freebsd's documentation? It's touted as the best documentation for any OS.

The BSDs tend to have the tightest review/control of what software is added (well, aside from apple I guess... but at least if you add your own stuff to BSD they don't lock it up!), so it would follow that they would be able to provide excellent documentation.

Along with BSD, Gentoo (which 'ported' the BSD port system) probably has the best documentation of any linux distro.  It's not an easy distro for sure, but the documentation is so thorough anyone could install and use it if they are willing to follow directions carefully.

---

### Post by hanzomon4 on 2007-12-11
Tru dat... 
[SIZE="1"]**puts cool face on**[/SIZE]

---

