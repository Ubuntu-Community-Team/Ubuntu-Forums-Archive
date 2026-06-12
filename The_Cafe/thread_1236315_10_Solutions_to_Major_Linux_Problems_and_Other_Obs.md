---
title: "10 Solutions to Major Linux Problems and Other Observations"
date: 2009-08-10
forum: The Cafe
---

### Post by keiichidono on 2009-08-10
I've only been providing the community with problems i think should be solved, but not actually providing real solutions. With this article I will spread these solutions and make sure something is done about them. I hope other Linux bloggers follow my example and get involved in fixing the problems that plague us.

Solution #1 - Tony Mobily says that [Linux software installation is broken]("http://www.freesoftwaremagazine.com/columns/2009_software_installation_linux_broken_and_path_fixing_it"), and provides his solution to the problem. I'm providing my thoughts and improvements to his ideas. I agree that users should be able to install user software, and should only be required to enter their root password for installing system and/or administrator software. This can easily be changed by identifying software as user or system software at the package/package manager level. Per-user installation seems a tad bit redundant though, i think per-user settings would be a better idea instead. Also, I believe in developing websites for the latest web browsers with (optional) fall backs so i don't see eye to eye with him on graphic designers who need to install several versions of Opera and Firefox for website design. Software being installed system-wide is faulted only by not allowing two different users to have two separate settings as I said before, such as when i set gnome-do to start up on log-in, it does that on other accounts too which is a big inconvenience. I think program sharing should be simplified so that in the package manager you're able to grab a program with settings from the local disk and package it for sharing, or just package it from the repositories.

Solution #2 - [Shutter]("http://www.freesoftwaremagazine.com/columns/six_new_editing_tools_and_four_plugins_shutter_just_got_even_better") is a great screenshot utility and it should be the default screenshot tool for Gnome. recordMyDesktop is the best desktop recording software out there for Linux and along with Shutter will be used in a secret upcoming project of mine, so I'll get a lot of hands on time with them. Even though these two tools are the best at what they do many people don't know about them, so spreading the word about these and other praiseworthy applications will greatly benefit the community.

Solution #3 - Kazade points out quite a few [problems]("http://kazade.livejournal.com/2451.html") with [Wine's development model]("http://kazade.livejournal.com/2045.html") and not only do i wholeheartedly agree with him/her but i also think Wine would benefit from a merge with [PlayonLinux]("http://www.playonlinux.com/en/"). Richard thinks including a shortcut to install wine on the desktop titled &#8220;Install Windows Compatibility&#8221; would help new users get exposure to Wine, but I think a welcome dialog on first boost would be a cleaner solution. I've also [asked the community]("http://ubuntuforums.org/showthread.php?t=1220779") what role they think Wine should take and most think that Wine developers should focus on making a powerful back-end and let other people do the front-end as Wine's GUI is currently ineffective in doing it's job.

Solution #4 - A lot of Windows software is free (of cost) but not open source. Most software doesn't need to be closed source, so why won't developers of free software license it under a FOSS license? Many say they see no need for it and don't want people to steal their work. We (as a community) need to encourage them that open sourcing their code will benefit them with additional developers without the risk of their code being stolen, and in turn will benefit us with the proliferation of FOSS.

Solution #5 - There are currently so many Linux related meetings and expositions it's impossible to keep track of them all, and they don't attract much media attention besides blog posts by those who have gone. We need to push for a merge of all Linux meetings into a dozen or less developer conferences and a couple of big Linux software and hardware expo's. After a discussion on how to get this done efficiently azangru of Ubuntu Forums came up with this:
> Gathering together in one place is partly why you have to listen to a dozen of people speak all in one day. If the event is decentralized and speakers are spread all over the globe, nothing prevents a conference to morph into a very different format.
Imagine: one or two pre-scheduled talks on a certain day, the topic being announced beforehand. A specially designed web site dedicated to the conference. Those with special interest in the announced topics can send their questions prior to the talk so that the speaker can address them if he chooses.

After a talk, if it is live and supervised by a moderator, there may be some time for questions and answers in real time. Alternatively, questions may be sent after the talk so that they will be addressed the next day. The talk could thus be viewed both live and in recording, while the opportunity to interact with the speaker is retained.

I mean, well, this scheme is not perfect, but it is feasible (google for webinars and see for yourself), and if this sort of thing could ever happen, it could transform conferencing as we know it into an ongoing educational and social event. To get a taste of what I'm talking about, [see the interview with Mark Shuttleworth]("http://ubuntupodcast.net/2009/04/14/ubuntu-podcast-episode-24-mark-shuttleworth/") at Ubuntu Podcasts.
Solution #6 - A lot of people complain about OpenOffice being slow and looking out-dated. They should use their time pushing for OpenOffice to remove it&#8217;s dependency on Java and and [help out with the interface redesign]("http://wiki.services.openoffice.org/wiki/Renaissance/Design_Proposals_for_%E2%80%9CAccessing_Functionality%E2%80%9D") instead of whining. I've noticed that there's no easy way to configure the Lock Dialog, even though someone has [already programmed a fix]("http://gnome-look.org/content/show.php/Lock+Dialog+Preferences?content=100871"). Another thing I've noticed is the fact that Gnome has no easy way to download and install themes even though it has already been done in Emerald. I plan on submitting bug reports on both of these problems. [IMG]http://bagoflies.wordpress.com/files/2009/08/emerald.png[/IMG]

Solution #7 - Linux hardware support isn't as good as it could be, and not many computer manufacturers include Linux as an option when buying a PC. We need to lobby hardware makers to support Linux, by documenting the fact that Linux users will buy Linux friendly hardware with a decent Linux distribution preinstalled more often than not.

Solution #8 - Mono (C# for Linux) is [seriously dividing]("http://www.linuxinsider.com/story/67512.html?wlc=1249143951") the community and [not for the better]("http://www.linuxinsider.com/story/67729.html"). Idiotic zealots on both sides are blowing this situation way out of proportion when the solution is quite easy and simple. [Vala]("http://en.wikipedia.org/wiki/Vala_(programming_language)") (v for short) has all the benefits of C# without the fear, uncertainty and doubt surrounding Mono. Tests even reveal it to be faster than other programming languages, including Mono. People against Mono should push for Mono apps to switch to Vala and because of it's speed, power, and simplicity it may even become a big part of GNU/Linux in the future. I'm going to try my hand at converting Paint.Net-Mono to Vala to make sure i roughly understand how hard it is to port Mono applications to Vala.

Solution #9 - [Nathive]("http://www.nathive.org/") looks **very** promising, and i propose that when it matures it should replace GIMP in the default Gnome installation. Most GIMP users complain of it's learning curve and only use a subset of it's features. In addition, Nathive could accelerate development by using Gimp code and only implementing user friendly features (much like [paint.net]("http://en.wikipedia.org/wiki/Paint.NET") on windows has done) to get a usable stable release out of the door faster.

Solution #10 - Recent efforts by 4chan to stop AT&amp;T censorship has inspired me to start a &#8220;Spread FOSS&#8221; campaign as a meta-campaign for all free and open source software. Similar to Spread Firefox, but much more powerful and with much more exposure. 4chan was successful in bringing the issue to light because they had a majority of their community working towards the same goal of spreading awareness. Jack Wallen asks [Why aren't schools adopting open source?]("http://blogs.techrepublic.com.com/opensource/?p=811") and the answer is simply exposure to open source. Getting thousands of students to call and write to schools asking for FOSS in the education system, getting FOSS to be a trending topic on twitter and other social networking websites, getting thousands of people to give out Linux Distribution CD's on the streets; now **that** is exposure. The kind of exposure FOSS needs.

Observations -
Chromium may be suitable to replace Firefox in Gnome in the near future.
I am pleased that [Google may take aim at Web video standards with On2 purchase]("http://arstechnica.com/media/news/2009/08/google-may-take-aim-at-web-video-standards-with-on2-purchase.ars").
I don't understand the whole [web font thing]("http://arstechnica.com/web/news/2009/08/web-font-services-join-fray-as-webfont-format-gains-support.ars"), can someone be so kind as to explain it to me?
[Synapse IM]("http://synapse.im/") looks quite good even though it's an alpha release, could replace Empathy/Pidgin in the future.
It may be beneficial to study Chromium&#8217;s security model and see if/how we can apply it to Linux.
I agree with [Shuttleworth's long speech]("http://lwn.net/Articles/345353/") about collaboration but why oh why did he have to make it so long?!

---

### Post by t0p on 2009-08-10
This is a link to your blog, right? Which makes this spam!

---

### Post by keiichidono on 2009-08-10
> **t0p said:**
> This is a link to your blog, right? Which makes this spam!

How so?

---

### Post by kpkeerthi on 2009-08-10
> **t0p said:**
> This is a link to your blog, right? Which makes this spam!

Its perfectly fine to post a link in the Community Cafe.

---

### Post by Arup on 2009-08-10
Package manager broken????? I have installed numerous software via Synaptic and deb files and never ran into any issues. Only Fedora 11 gave me grief with Opera install.

---

### Post by t0p on 2009-08-10
> **kpkeerthi said:**
> Its perfectly fine to post a link in the Community Cafe.

Really? It is ok to post links to your own sites? To generate traffic to your own sites? I did not know that.

Sorry OP. I take it back.

---

### Post by koenn on 2009-08-10
it depends.
If you use a link to documentation (a fix, a howto) in a support thread, and the information happens to be on your own website, its obviously no problem.

If you post links to your blog with no other reason but to drive traffic there or get it indexed by google / improve page rank with a 'link from a high quality site', it's spam.

There's some grey area in between.

---

### Post by overdrank on 2009-08-10
But it would seem that the op is spamming the blog
[Bag of lies]("http://ubuntuforums.org/showthread.php?t=1220533&highlight=bag+lies") 
[Real Sexism]("http://ubuntuforums.org/showthread.php?p=7761870#post7761870")

---

### Post by uljanow on 2009-08-10
> Solution #2 – Shutter is a great screenshot utility and it should be the default screenshot tool for Gnome
This is indeed a **major** linux problem. I stopped reading after that sentence.

---

### Post by thisllub on 2009-08-10
#1 Disagree completely.
Users are free to install software on their computers IF they are also the administrator. This feature is probably the greatest weakness in Windows.

#4 If you write bad code you probably want to keep it a secret. 
Much Windows freeware is amateur at best.

#8 Agggggggh.
If it is good software it will prosper.
Gnome Do is a bit heavy for me but it is helping to do away with the mouse paradigm.


#9 GIMP is great. I even install it on Windows machines.

---

### Post by The Toxic Mite on 2009-08-10
This is spam.

EDIT: I would like to coin the term "traffic fascist" - a person who spams forums and mailing lists with links to his/her own site.

---

### Post by Arup on 2009-08-10
When it criticizes apt-get it just has no place but in SPAM bin.

---

### Post by koenn on 2009-08-10
> **overdrank said:**
> But it would seem that the op is spamming the blog
[Bag of lies]("http://ubuntuforums.org/showthread.php?t=1220533&highlight=bag+lies") 
[Real Sexism]("http://ubuntuforums.org/showthread.php?p=7761870#post7761870")

I'd say it's kinda leaning strongly towards spam.
anyway, you're the mod, not I.

---

### Post by t0p on 2009-08-10
*deleted by poster*

---

### Post by 3rdalbum on 2009-08-10
If those are 10 "Major" Linux problems, then our operating system must be incredibly good.

I'll disagree with your solution to the hardware drivers - what's in it for the hardware manufacturers? The real solution is to get the hardware manufacturers to come together and work out standards for classes of device. For instance, all wireless cards basically do the same thing, they should all be built to communicate with the computer via a standard API rather than the current situation where different chipsets require different drivers.

What's in it for hardware manufacturers? Well, they would no longer have to write drivers for every new device. Even discounting the huge benefits that open standard drivers would have for Linux, there'd be great benefits for Windows users: Every new version of Windows would still work with standards-compliant hardware, even if the kernel changes; you wouldn't need to install a mess of drivers every time you reinstall Windows, and there'd be no such thing as driver conflicts because there would only be a handful of drivers running, all in-kernel, all maintained by the kernel's developers.

Not only is this good for Linux as we can implement the standard drivers, but if you decided to switch to OpenSolaris or FreeBSD or ReactOS you'd find that all your hardware would still be working because those operating system developers have also implemented the standards.

That's the best solution to the hardware support problem, and it doesn't require hardware manufacturers to be actively friendly towards Linux.

---

### Post by The Toxic Mite on 2009-08-10
> **3rdalbum said:**
> If those are 10 "Major" Linux problems, then our operating system must be incredibly good.

I'll disagree with your solution to the hardware drivers - what's in it for the hardware manufacturers? The real solution is to get the hardware manufacturers to come together and work out standards for classes of device. For instance, all wireless cards basically do the same thing, they should all be built to communicate with the computer via a standard API rather than the current situation where different chipsets require different drivers.

What's in it for hardware manufacturers? Well, they would no longer have to write drivers for every new device. Even discounting the huge benefits that open standard drivers would have for Linux, there'd be great benefits for Windows users: Every new version of Windows would still work with standards-compliant hardware, even if the kernel changes; you wouldn't need to install a mess of drivers every time you reinstall Windows, and there'd be no such thing as driver conflicts because there would only be a handful of drivers running, all in-kernel, all maintained by the kernel's developers.

Not only is this good for Linux as we can implement the standard drivers, but if you decided to switch to OpenSolaris or FreeBSD or ReactOS you'd find that all your hardware would still be working because those operating system developers have also implemented the standards.

That's the best solution to the hardware support problem, and it doesn't require hardware manufacturers to be actively friendly towards Linux.

I agree with you on that.

---

### Post by chucky chuckaluck on 2009-08-10
> Solution #4 – A lot of Windows software is free (of cost) but not open source. Most software doesn’t need to be closed source, so why won’t developers of free software license it under a FOSS license? Many say they see no need for it and don’t want people to steal their work. We (as a community) need to encourage them that open sourcing their code will benefit them with additional developers without the risk of their code being stolen, and in turn will benefit us with the proliferation of FOSS.

the open source 'entitlement' mentality bothers me and this is a prime example. if someone doesn't want to make their project open to others, i don't see how anyone thinks they have a right to badger them to make it open. it's not even property. it's the thinking of an individual that you would be insisting on access to.

---

### Post by hellmet on 2009-08-10
> **overdrank said:**
> but it would seem that the op is spamming the blog
[bag of lies]("http://ubuntuforums.org/showthread.php?t=1220533&highlight=bag+lies") 
[real sexism]("http://ubuntuforums.org/showthread.php?p=7761870#post7761870")

+1

---

### Post by chucky chuckaluck on 2009-08-10
ok, so maybe the op is spamming. let the mods deal with that and let's get back to the subject.

---

### Post by phrostbyte on 2009-08-10
I think apt-get can be improved. We are only scratching the surface of what can be done with package management. I'm not saying this as a Ubuntu vs other OS comparison though.

---

### Post by Orlsend on 2009-08-10
**on point 2**

Shutter its not a app we should adrvertise, the web features never 

**on point 6**

the Project epidermis is the solution to the theming problem

**on point 8**

When you used the word "Idiotic zealots", you lost all credibility.

**on point 9**

You got to be crazy, gimp its probably one of the best examples of the community. so strong that is often compared and favored even more than photo-shop.

---

### Post by The Toxic Mite on 2009-08-10
> **orlsend said:**
> **on point 2**

shutter its not a app we should adrvertise, the web features never 

**on point 6**

the project epidermis is the solution to the theming problem

**on point 8**

when you used the word "idiotic zealots", you lost all credibility.

**on point 9**

you got to be crazy, gimp its probably one of the best examples of the community. So strong that is often compared and favored even more than photo-shop.

+1

---

### Post by unknownPoster on 2009-08-10
> **Arup said:**
> When it criticizes apt-get it just has no place but in SPAM bin.


I disagree. Granted, I didn't read the blog post. However, if someone has a valid and factual criticism of any piece of software, whether it be apt-get, Ubuntu, etc., that doesn't mean it's spam.

---

### Post by Arup on 2009-08-10
> **unknownPoster said:**
> I disagree. Granted, I didn't read the blog post. However, if someone has a valid and factual criticism of any piece of software, whether it be apt-get, Ubuntu, etc., that doesn't mean it's spam.

He never mentioned whats wrong with apt-get the post is SPAM.

---

### Post by hissyfut on 2009-08-10
There may not be something major wrong with apt-get, however it may be the implementation and the use of it. The debian packaging system has some serious issues. For example get any simple source tarball that uses ./configure, make, make install, and try to create a debian package using the default instructions for the dh_make part:
[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)
It never works. What type of source is this default way looking for?


#9) "Most Gimp users..."
This is made up, right? Gimp has been around for a long time. Where are these "Most Gimp users"?

---

### Post by nobodysbusiness on 2009-08-10
> We are only scratching the surface of what can be done with package management.

@phrostbyte: Can you give some examples of other cool things that could be done with package management in the future? I always thought of package management as being pretty much about as good as it would ever get.

---

### Post by dragos240 on 2009-08-10
@OP
Try to replace the html tags with BBCODE tags.

---

### Post by keiichidono on 2009-08-11
> **dragos240 said:**
> @OP
Try to replace the html tags with BBCODE tags.

This thread has degenerated so much i wouldn't even waste my time doing that.

---

### Post by directhex on 2009-08-11
Point 8 shows some serious naiveté. **ALL** the benefits of C#? Nope. Vala offers a *subset* of C#'s benefits - and a variety of its own, including the performance points you mention. But there are an enormous number of things which it's also impossible to do with Vala. Pros & cons need to be weighed up in *actual* terms, not starting out with the false presumption that it can do everything C# can do

---

### Post by phrostbyte on 2009-08-11
> **nobodysbusiness said:**
> @phrostbyte: Can you give some examples of other cool things that could be done with package management in the future? I always thought of package management as being pretty much about as good as it would ever get.

Some things off the top of my head (maybe apt can do these things, I am not 100% sure)
[LIST]
[*]Being able to install multiple versions of a package side by side
[*]An easy way to suppress updates of single packages
[*]Support for delta packages
[*]More configuration options on packages
[/LIST]

---

### Post by thisllub on 2009-08-11
> **phrostbyte said:**
> Some things off the top of my head (maybe apt can do these things, I am not 100% sure)
[LIST]
[*]Being able to install multiple versions of a package side by side
[*]An easy way to suppress updates of single packages
[*]Support for delta packages
[*]More configuration options on packages
[/LIST]

Pacman is the best package manager.
It already does most of this.
Delta support is coming.

pacman -Ss to search followed by pacman -S to install is so much nicer than apt-cache search followed by apt-get install



[http://wiki.archlinux.org/index.php/Pacman](http://wiki.archlinux.org/index.php/Pacman)

---

### Post by HappinessNow on 2009-08-11
> **CalvinB said:**
> I've only been providing the community with problems i think should be solved, but not actually providing real solutions. With this article I will spread these solutions and make sure something is done about them. I hope other Linux bloggers follow my example and get involved in fixing the problems that plague us.<!--more-->

Solution #1 - Tony Mobily says that <a href="http://www.freesoftwaremagazine.com/columns/2009_software_installation_linux_broken_and_path_fixing_it"> Linux software installation is broken</a>, and provides his solution to the problem. I'm providing my thoughts and improvements to his ideas. I agree that users should be able to install user software, and should only be required to enter their root password for installing system and/or administrator software. This can easily be changed by identifying software as user or system software at the package/package manager level. Per-user installation seems a tad bit redundant though, i think per-user settings would be a better idea instead. Also, I believe in developing websites for the latest web browsers with (optional) fall backs so i don't see eye to eye with him on graphic designers who need to install several versions of Opera and Firefox for website design. Software being installed system-wide is faulted only by not allowing two different users to have two separate settings as I said before, such as when i set gnome-do to start up on log-in, it does that on other accounts too which is a big inconvenience. I think program sharing should be simplified so that in the package manager you're able to grab a program with settings from the local disk and package it for sharing, or just package it from the repositories.

Solution #2 - <a href="http://www.freesoftwaremagazine.com/columns/six_new_editing_tools_and_four_plugins_shutter_just_got_even_better">Shutter</a> is a great screenshot utility and it should be the default screenshot tool for Gnome. recordMyDesktop is the best desktop recording software out there for Linux and along with Shutter will be used in a secret upcoming project of mine, so I'll get a lot of hands on time with them. Even though these two tools are the best at what they do many people don't know about them, so spreading the word about these and other praiseworthy applications will greatly benefit the community.

Solution #3 - Kazade points out quite a few <a href="http://kazade.livejournal.com/2451.html">problems</a> with <a href="http://kazade.livejournal.com/2045.html">Wine's development model</a> and not only do i wholeheartedly agree with him/her but i also think Wine would benefit from a merge with <a href="http://www.playonlinux.com/en/">PlayonLinux</a>. Richard thinks including a shortcut to install wine on the desktop titled “Install Windows Compatibility” would help new users get exposure to Wine, but I think a welcome dialog on first boost would be a cleaner solution. I've also <a href="http://ubuntuforums.org/showthread.php?t=1220779">asked the community</a> what role they think Wine should take and most think that Wine developers should focus on making a powerful back-end and let other people do the front-end as Wine's GUI is currently ineffective in doing it's job.

Solution #4 - A lot of Windows software is free (of cost) but not open source. Most software doesn't need to be closed source, so why won't developers of free software license it under a FOSS license? Many say they see no need for it and don't want people to steal their work. We (as a community) need to encourage them that open sourcing their code will benefit them with additional developers without the risk of their code being stolen, and in turn will benefit us with the proliferation of FOSS.

Solution #5 - There are currently so many Linux related meetings and expositions it's impossible to keep track of them all, and they don't attract much media attention besides blog posts by those who have gone. We need to push for a merge of all Linux meetings into a dozen or less developer conferences and a couple of big Linux software and hardware expo's. After a discussion on how to get this done efficiently azangru of Ubuntu Forums came up with this:
<blockquote>Gathering together in one place is partly why you have to listen to a dozen of people speak all in one day. If the event is decentralized and speakers are spread all over the globe, nothing prevents a conference to morph into a very different format.
Imagine: one or two pre-scheduled talks on a certain day, the topic being announced beforehand. A specially designed web site dedicated to the conference. Those with special interest in the announced topics can send their questions prior to the talk so that the speaker can address them if he chooses.

After a talk, if it is live and supervised by a moderator, there may be some time for questions and answers in real time. Alternatively, questions may be sent after the talk so that they will be addressed the next day. The talk could thus be viewed both live and in recording, while the opportunity to interact with the speaker is retained.

I mean, well, this scheme is not perfect, but it is feasible (google for webinars and see for yourself), and if this sort of thing could ever happen, it could transform conferencing as we know it into an ongoing educational and social event. To get a taste of what I'm talking about, <a href="http://ubuntupodcast.net/2009/04/14/ubuntu-podcast-episode-24-mark-shuttleworth/">see the interview with Mark Shuttleworth</a> at Ubuntu Podcasts.</blockquote>
Solution #6 - A lot of people complain about OpenOffice being slow and looking out-dated. They should use their time pushing for OpenOffice to remove it’s dependency on Java and and <a href="http://wiki.services.openoffice.org/wiki/Renaissance/Design_Proposals_for_%E2%80%9CAccessing_Functionality%E2%80%9D">help out with the interface redesign</a> instead of whining. I've noticed that there's no easy way to configure the Lock Dialog, even though someone has <a href="http://gnome-look.org/content/show.php/Lock+Dialog+Preferences?content=100871">already programmed a fix</a>. Another thing I've noticed is the fact that Gnome has no easy way to download and install themes even though it has already been done in Emerald. I plan on submitting bug reports on both of these problems. <img class="alignright size-full wp-image-94" title="Emerald Theme Manager" src="http://bagoflies.wordpress.com/files/2009/08/emerald.png" alt="Emerald Theme Manager" width="476" height="294" />

Solution #7 - Linux hardware support isn't as good as it could be, and not many computer manufacturers include Linux as an option when buying a PC. We need to lobby hardware makers to support Linux, by documenting the fact that Linux users will buy Linux friendly hardware with a decent Linux distribution preinstalled more often than not.

Solution #8 - Mono (C# for Linux) is <a href="http://www.linuxinsider.com/story/67512.html?wlc=1249143951">seriously dividing</a> the community and <a href="http://www.linuxinsider.com/story/67729.html">not for the better</a>. Idiotic zealots on both sides are blowing this situation way out of proportion when the solution is quite easy and simple. <a href="http://en.wikipedia.org/wiki/Vala_(programming_language)">Vala</a> (v for short) has all the benefits of C# without the fear, uncertainty and doubt surrounding Mono. Tests even reveal it to be faster than other programming languages, including Mono. People against Mono should push for Mono apps to switch to Vala and because of it's speed, power, and simplicity it may even become a big part of GNU/Linux in the future. I'm going to try my hand at converting Paint.Net-Mono to Vala to make sure i roughly understand how hard it is to port Mono applications to Vala.

Solution #9 - <a href="http://www.nathive.org/">Nathive</a> looks <strong>very</strong> promising, and i propose that when it matures it should replace GIMP in the default Gnome installation. Most GIMP users complain of it's learning curve and only use a subset of it's features. In addition, Nathive could accelerate development by using Gimp code and only implementing user friendly features (much like <a href="http://en.wikipedia.org/wiki/Paint.NET">paint.net</a> on windows has done) to get a usable stable release out of the door faster.

Solution #10 - Recent efforts by 4chan to stop AT&amp;T censorship has inspired me to start a “Spread FOSS” campaign as a meta-campaign for all free and open source software. Similar to Spread Firefox, but much more powerful and with much more exposure. 4chan was successful in bringing the issue to light because they had a majority of their community working towards the same goal of spreading awareness. Jack Wallen asks <a href="http://blogs.techrepublic.com.com/opensource/?p=811">Why aren't schools adopting open source?</a> and the answer is simply exposure to open source. Getting thousands of students to call and write to schools asking for FOSS in the education system, getting FOSS to be a trending topic on twitter and other social networking websites, getting thousands of people to give out Linux Distribution CD's on the streets; now <strong>that</strong> is exposure. The kind of exposure FOSS needs.

Observations -
<ul> Chromium may be suitable to replace Firefox in Gnome in the near future.
I am <strong>very</strong> pleased that <a href="http://arstechnica.com/media/news/2009/08/google-may-take-aim-at-web-video-standards-with-on2-purchase.ars">Google may take aim at Web video standards with On2 purchase</a>.
I don't understand the whole <a href="http://arstechnica.com/web/news/2009/08/web-font-services-join-fray-as-webfont-format-gains-support.ars">web font thing</a>, can someone be so kind as to explain it to me?
<a href="http://synapse.im/">Synapse IM</a> looks quite good even though it's an alpha release, could replace Empathy/Pidgin in the future.
It may be beneficial to study Chromium’s security model and see if/how we can apply it to Linux.
I agree with <a href="http://lwn.net/Articles/345353/">Shuttleworth's long speech</a> about collaboration but why oh why did he have to make it so long?!</ul>I'm sorry this post is just too messy to read, please edit your OP in the proper format.

---

### Post by keiichidono on 2009-08-11
Just did. Gonna depreciate this article and make a better one after more research.

---

### Post by keiichidono on 2009-08-11
> **thisllub said:**
> #1 Disagree completely.
Users are free to install software on their computers IF they are also the administrator. This feature is probably the greatest weakness in Windows.

#4 If you write bad code you probably want to keep it a secret. 
Much Windows freeware is amateur at best.

#8 Agggggggh.
If it is good software it will prosper.
Gnome Do is a bit heavy for me but it is helping to do away with the mouse paradigm.


#9 GIMP is great. I even install it on Windows machines.

Why should you be admin to install chess from the repo's? I see where you're coming from though. > Much Windows freeware is amateur at best So why not open it to the community to make it better? I didn't say Gimp wasn't the best, it's just extremely un-intuitive.

> **3rdalbum said:**
> If those are 10 "Major" Linux problems, then our operating system must be incredibly good.

I'll disagree with your solution to the hardware drivers - what's in it for the hardware manufacturers? The real solution is to get the hardware manufacturers to come together and work out standards for classes of device. For instance, all wireless cards basically do the same thing, they should all be built to communicate with the computer via a standard API rather than the current situation where different chipsets require different drivers.

What's in it for hardware manufacturers? Well, they would no longer have to write drivers for every new device. Even discounting the huge benefits that open standard drivers would have for Linux, there'd be great benefits for Windows users: Every new version of Windows would still work with standards-compliant hardware, even if the kernel changes; you wouldn't need to install a mess of drivers every time you reinstall Windows, and there'd be no such thing as driver conflicts because there would only be a handful of drivers running, all in-kernel, all maintained by the kernel's developers.

Not only is this good for Linux as we can implement the standard drivers, but if you decided to switch to OpenSolaris or FreeBSD or ReactOS you'd find that all your hardware would still be working because those operating system developers have also implemented the standards.

That's the best solution to the hardware support problem, and it doesn't require hardware manufacturers to be actively friendly towards Linux.

That was amazing, please become an editor for my blog. Can i quote you?

> **chucky chuckaluck said:**
> the open source 'entitlement' mentality bothers me and this is a prime example. if someone doesn't want to make their project open to others, i don't see how anyone thinks they have a right to badger them to make it open. it's not even property. it's the thinking of an individual that you would be insisting on access to.

It's not entitlement, most apps would do better with peer review inside and out and open source happens to offer that by design.

> **phrostbyte said:**
> I think apt-get can be improved. We are only scratching the surface of what can be done with package management. I'm not saying this as a Ubuntu vs other OS comparison though.

Please explain more. :popcorn:

> **Orlsend said:**
> **on point 2**

Shutter its not a app we should adrvertise, the web features never 

**on point 6**

the Project epidermis is the solution to the theming problem

**on point 8**

When you used the word "Idiotic zealots", you lost all credibility.

**on point 9**

You got to be crazy, gimp its probably one of the best examples of the community. so strong that is often compared and favored even more than photo-shop.

This is barely legible. Please clean it up or else i can't reply.

> **directhex said:**
> Point 8 shows some serious naiveté. **ALL** the benefits of C#? Nope. Vala offers a *subset* of C#'s benefits - and a variety of its own, including the performance points you mention. But there are an enormous number of things which it's also impossible to do with Vala. Pros & cons need to be weighed up in *actual* terms, not starting out with the false presumption that it can do everything C# can do

Then can you explain to me in more detail the pro's and cons?

> **phrostbyte said:**
> Some things off the top of my head (maybe apt can do these things, I am not 100% sure)
[LIST]
[*]Being able to install multiple versions of a package side by side
[*]An easy way to suppress updates of single packages
[*]Support for delta packages
[*]More configuration options on packages
[/LIST]

What about bittorent as an update model for apt-get? Anything else? :confused:

---

### Post by 3rdalbum on 2009-08-11
> **CalvinB said:**
> That was amazing, please become an editor for my blog. Can i quote you?

Well, thank you. You may quote me if you want. I'm sorry but I'll have to decline the position of editor - I have barely enough time to work on my own projects :-)

---

### Post by 3rdalbum on 2009-08-11
> **hissyfut said:**
> There may not be something major wrong with apt-get, however it may be the implementation and the use of it. The debian packaging system has some serious issues. For example get any simple source tarball that uses ./configure, make, make install, and try to create a debian package using the default instructions for the dh_make part:
[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)
It never works. What type of source is this default way looking for?

I don't think this is a problem with the Debian packaging system as a whole. I just make packages by setting the ./configure script to "install" its files to a folder in my home directory, and then I create the DEBIAN directory inside this and populate the necessary files, then run "dpkg-deb" on the whole lot. Presto, Debian package.

---

### Post by directhex on 2009-08-11
> **CalvinB said:**
> Then can you explain to me in more detail the pro's and cons?

Vala is effectively a preprocessor with C#-like syntax, which emits C as an intermediary, and uses GObject for faking a "class library"

As a result, it makes dealing with GObject pretty simple. Conversely, it picks up plenty of syntactic mess from dealing with GObject so directly.

Want a major con? It's ill-defined - ill-defined enough that the simple GTK "hello world" from the top of [http://live.gnome.org/Vala/GTKSample](http://live.gnome.org/Vala/GTKSample) wouldn't compile for me on Jaunty. Other missing pieces? LINQ, Reflection, language interop, cross-platform behaviour

---

### Post by bapoumba on 2009-08-11
CalvinB: your blog allows comments. Please keep the discussions related to your articles where they belong, on your site, thanks.

---

