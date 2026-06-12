---
title: "Proposed: Chromium as Ubuntu's default browser"
date: 2013-05-13
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2013-05-13
[Chromium as default browser]("https://blueprints.launchpad.net/ubuntu/+spec/foundations-1305-chromium-default-browser")> Chromium has matured to being as good or better than Firefox. It will be the foundation of a lot of Ubuntu Touch code and webapps code. We should consider using Chromium as the default browser in Ubuntu.
So why is Chromium (by Canonical/Ubuntu/Community) still at version 25? I think Canonical's Firefox team is more "on time" in terms of providing a current browser to its users.

---

### Post by monkeybrain2012 on 2013-05-13
Based on what does he say that chromium is as good or better than Firefox? It is quite useless IMO, it is outdated, it doesn't have the rich addon ecology of FF, and multimedia plugins barely works in it (gecko-mediaplayer mainly) One great selling point for Chrome is pepper flash but chromium doesn't have it. If it becomes the default I hope I can easily remove it without removing the whole desktop (not like konqueror or whatever it is called now in KDE distros), which is exactly what I do whenever I install lubuntu (and install Firefox and Chrome afterwords) 

Besides, instead of a full blown first class open source browser like Firefox why would he want a crippled version of Chrome (that is what  Chromium basically is) as the default on the flagship Linux distro?

---

### Post by cflow on 2013-05-13
From what I know, this is a blueprint - and I think most people registered on launchpad can file them. Whether this one will become accepted or not is still very questionable as news right now. As an example, for Fedora 19, a developer proposed Cinnamon to be the default desktop environment, and was interpreted by some sites as news - but that switch probably won't happen.

---

### Post by craig10x on 2013-05-13
Chrome would be a much better default then chromium...it has the latest version of flash thanks to it's pepper flash plug in arrangement with adobe (which Chromium does not) and excellent built in pdf reader (in the browser) and even adds a ppa for automatic updates....plus it is always ahead of chromium in latest versions...I guess there is the license aspect of it that would prevent ubuntu from using it...a real shame...

I think firefox is a fine browser but i always install Chrome...Chrome has become so popular that it's offered as a 2nd browser on many windows laptops and desktops these days...My toshiba had it added on the windows 7 install i originally had on my laptop...It's actually more popular then internet explorer these days...

---

### Post by vasa1 on 2013-05-13
> **cflow said:**
> **From what I know, this is a blueprint** - and I think most people registered on launchpad can file them. Whether this one will become accepted or not** is still very questionable as news right now**. As an example, for Fedora 19, a developer proposed Cinnamon to be the default desktop environment, and was interpreted by some sites as news - but that switch probably won't happen.
"Proposed" is in the title. The link clearly includes "blueprint". I posted in the Chat section. So what's your point?

---

### Post by monkeybrain2012 on 2013-05-13
Other than flash (and html5) almost no other media content plays in Chrome under Linux  Simple example. Try to access this with chrome.[http://www.ciut.fm/listen-now/](http://www.ciut.fm/listen-now/)  

I can play both the mac and windows links on Firefox with gecko-mediaplayer but gm would not even load in Chrome (tried different versions of gm and chrome and on different machines and different versions of Ubuntu, it doesn't work on Chrome with Ubuntu since 11.04 and gm version 1.04 or something, and it doesn't not  work with Chrome in Fedora 18, the only place where it works, strangely is Debian sid) Totem plugin can play some contents  on a good day but very limited comparing to gecko-mediaplayer. 

Firefox plays both flash and html5 as well as Chrome except for very few sites that require pepper or  html5 sites that require h264, but they are rare and there are  workarounds for popular ones like vimeo.

I can easily handle 100+ tabs on FF on my not so cutting edge laptop, Chrome chokes for memory with about 20. Speedwise there is very little difference except Chrome is a little faster on startup (maybe because of the 100+ tabs in Firefox)

I think Firefox is still overall the best browser on Linux, aside from the fact that Chrome can never be the default because it is non free.

---

### Post by vasa1 on 2013-05-13
> **craig10x said:**
> Chrome would be a much better default then chromium...it has the latest version of flash thanks to it's pepper flash plug in arrangement with adobe (which Chromium does not) and excellent built in pdf reader (in the browser) and even adds a ppa for automatic updates....plus it is always ahead of chromium in latest versions...I guess there is the license aspect of it that would prevent ubuntu from using it...a real shame...

I think firefox is a fine browser but i always install Chrome...Chrome has become so popular that it's offered as a 2nd browser on many windows laptops and desktops these days...My toshiba had it added on the windows 7 install i originally had on my laptop...It's actually more popular then internet explorer these days...
I use both Chrome and Firefox. Because of that dependency issue, I'm still waiting on Chrome 27. I was hoping it would be released during I/O 2013 [but that doesn't seem to be the case]("https://code.google.com/p/chromium/issues/detail?id=226002#c63"). So, if my math is correct v26 >>> v27 will have taken much more than ~ six weeks :(

---

### Post by cflow on 2013-05-13
> **vasa1 said:**
> "Proposed" is in the title. The link clearly includes "blueprint". I posted in the Chat section. So what's your point?

Well... I think the title of the thread could still be kind of decieving and prone to causing another browser war: Some might interpret this as Ubuntu *as a whole* giving full thought about the proposal to switch web browsers, and get everyone complaining about which web browser should rule the universe. The power of one blueprint, and the media exposing it... just like the fedora example I explained. I guess I wanted to prevent a wildfire here :KS.

---

### Post by deadflowr on 2013-05-13
Maybe they should show it can handle timely updates first.

---

### Post by monkeybrain2012 on 2013-05-13
> **craig10x said:**
> ..Chrome has become so popular that it's offered as a 2nd browser on many windows laptops and desktops these days...My toshiba had it added on the windows 7 install i originally had on my laptop...It's actually more popular then internet explorer these days...

Yes, on Windows may be, but the only advantage of Chrome over FF on Linux is flash and that's just about it.

---

### Post by castrojo on 2013-05-13
>  Some might interpret this as Ubuntu as a whole giving full thought about the proposal to switch web browsers, and get everyone complaining about which web browser should rule the universe. The power of one blueprint, and the media exposing it... just like the fedora example I explained. I guess I wanted to prevent a wildfire here.

It's marked as accepted for UDS tomorrow and it's on the schedule.

---

### Post by castrojo on 2013-05-14
> So why is Chromium (by Canonical/Ubuntu/Community) still at version 25? I think Canonical's Firefox team is more "on time" in terms of providing a current browser to its users.

It's a few weeks behind due some builder issues, and right now it's in universe so it's a best effort. Assuming it would be accepted it would be put into main and have the same up-to-date packaging every release like Firefox does.

---

### Post by cflow on 2013-05-14
> **castrojo said:**
> It's marked as accepted for UDS tomorrow and it's on the schedule.

I see... That makes this proposal more newsworthy, finding this page:

[http://summit.ubuntu.com/uds-1305/meeting/21788/foundations-1305-chromium-default-browser/](http://summit.ubuntu.com/uds-1305/meeting/21788/foundations-1305-chromium-default-browser/)

May the browser debates be useful there...

---

### Post by monkeybrain2012 on 2013-05-14
Just make it easy to uninstall and I am happy.

---

### Post by craig10x on 2013-05-14
hey...you can always add firefox like i add chrome now ;)

and @ vasa1: i know you are running 13.10...but did you try the dependency download first and then install Chrome stable?  should work....i did with no problem on a live session of saucy...
and if not, then you could use Chrome Beta temporarily until it reaches the stable channel...Any time i tried Chrome beta it seemed quite stable to me....

---

### Post by monkeybrain2012 on 2013-05-14
> **craig10x said:**
> hey...you can always add firefox like i add chrome now ;)



Of course I can, but why do I need 3 browsers with Chromium just basically junk? :) 

I have Fedora on KDE, It is terrible that I cannot remove konqueror even  though I easily install Firefox and Chrome. So I just get rid of the  desktop file to hide it but it is still there and taking up space.

Why should the default browser be part of the desktop anyway? I like the  way lubuntu handles it, it comes with Chromium but you are free to  remove it without removing the rest of your desktop.

It is not a good selling point to the new users, they know Chrome, and then they ask you what the hell is Chromium, ans: It is open source version of Chrome and the advantage is that it has all of Chrome's most useful functions removed, it is Chrome's crappy brother. Isn't it great advertisement for Open Source?  Firefox is  open source and good (especially on Linux), and it is not the lesser of something like it which is popular on WIndows and Mac. 

I don't really see the purpose of this. You have the best open source browser now why switch it out for a pretty mediocre one? If they try to latch on to Google's brand it is a bad move by offering a crappy version of Google's flagship  product.

---

### Post by vasa1 on 2013-05-14
> **craig10x said:**
> hey...you can always add firefox like i add chrome now ;)

and @ vasa1: i know you are running 13.10...but did you try the dependency download first and then install Chrome stable?  should work....i did with no problem on a live session of saucy...
and if not, then you could use Chrome Beta temporarily until it reaches the stable channel...Any time i tried Chrome beta it seemed quite stable to me....

@craig10x, I'm on Raring, not Saucy. When on Windows, I used to be on the beta channel because the updates on Windows are differential/incremental and not the full browser each time as we have in Ubuntu.

With Firefox it's a different story because I've installed Firefox beta direct (and in my home folder) and not from the repos. I get weekly incremental updates of about 2MB.

---

### Post by carl4926 on 2013-05-14
> **monkeybrain2012 said:**
> Based on what does he say that chromium is as good or better than Firefox? It is quite useless IMO, it is outdated, it doesn't have the rich addon ecology of FF, and multimedia plugins barely works in it (gecko-mediaplayer mainly) One great selling point for Chrome is pepper flash but chromium doesn't have it. If it becomes the default I hope I can easily remove it without removing the whole desktop (not like konqueror or whatever it is called now in KDE distros), which is exactly what I do whenever I install lubuntu (and install Firefox and Chrome afterwords) 

Besides, instead of a full blown first class open source browser like Firefox why would he want a crippled version of Chrome (that is what  Chromium basically is) as the default on the flagship Linux distro?

Chromium would be great if pepper flash came with it
Pepper has been put in the multimedia repos of Packman for openSUSE and I raised this @medibuntu but they couldn't do it.
It's the flash player that's going to be the biggest bug for us. Integrate Pepper some how and I'd say yes. Mind I still prefer it over FF, which is sluggy by comparision

---

### Post by malspa on 2013-05-14
I couldn't care less about which default browser ANY distro comes with, but I prefer to use Chromium first, Chrome second. I don't use Firefox anymore unless I absolutely have to, and that's been quite awhile now; the last time I had to was back when I had to fire it up to use the GNOME Shell extensions site.

However: When posting here in Chromium (from Debian Wheezy or from Chakra), I don't have formatting options, etc., showing up in the toolbar above the text field! Not cool. They are there in Chrome. I haven't been able to find a thread (yet) where this issue is addressed (maybe someone can point me in the right direction), but if this is a problem, I guess it wouldn't make much sense for Chromium to be the default browser for Ubuntu!

---

### Post by mgngapyin on 2013-05-14
Will webapps work in Chromium like Firefox? I've enabled "click-to-play plugins" in Chromium, and webapps just stop working.

---

### Post by MadmanRB on 2013-05-14
I think the switch to chromium makes sense as one can repackage pepperflash and make it optional so not need google chrome

---

### Post by coffeecat on 2013-05-14
> **malspa said:**
> However: When posting here in Chromium (from Debian Wheezy or from Chakra), I don't have formatting options, etc., showing up in the toolbar above the text field! Not cool. They are there in Chrome. 

And they are there for me in the current Ubuntu repository Chromium version 25.0.1364.160 in 13.04. Could this be a browser settings issue for you?

---

### Post by vasa1 on 2013-05-14
> **coffeecat said:**
> And they are there for me in the current Ubuntu repository Chromium version 25.0.1364.160 in 13.04. ...
Same here. I think they're all there.

---

### Post by malspa on 2013-05-14
> **coffeecat said:**
> And they are there for me in the current Ubuntu repository Chromium version 25.0.1364.160 in 13.04. Could this be a browser settings issue for you?

I don't know. Here, the toolbar isn't there at all. Right now, typing from Chromium 26.0.1410.63 (192696) in Chakra as far as I know, I use the same settings in Chromium that I use in Chrome, but the toolbar is there in Chrome. I think the mods will want me to start a new thread about this since it's kinda off-topic. I'll log into Ubuntu 12.04 and see how things look from there.

---

### Post by malspa on 2013-05-14
My new thread regarding the missing formatting toolbar issue: [http://ubuntuforums.org/showthread.php?t=2145090&p=12647474#post12647474](http://ubuntuforums.org/showthread.php?t=2145090&p=12647474#post12647474)

---

### Post by craig10x on 2013-05-14
@vasa1:  that works for raring too...that's how i installed Google Chrome 26 stable in my newly installed 13.04.....Just grab the dependency deb file from the linked article and then grab the google chrome deb from their website....right click each deb and install with ubuntu software center (no need to do it in the terminal as shown in the article)....be sure to have it install the dependency first...Once Chrome 27 makes it way to stable, there won't be any need to use this method anymore as 27 has the "fix" from Chrome...
[http://handytutorial.com/install-google-chrome-in-ubuntu-13-04-fix-dependency-problem/](http://handytutorial.com/install-google-chrome-in-ubuntu-13-04-fix-dependency-problem/)

---

### Post by vasa1 on 2013-05-15
> **castrojo said:**
> It's marked as accepted for UDS tomorrow and it's on the schedule.
Anyone know if this has this happened? Is there a YouTube link?

It's here: [http://summit.ubuntu.com/uds-1305/meeting/21788/foundations-1305-chromium-default-browser/](http://summit.ubuntu.com/uds-1305/meeting/21788/foundations-1305-chromium-default-browser/)

2013-05-**16** 16:05..17:00 in Client 1

---

### Post by landersohn on 2013-05-16
I do think Chromium is better than FF: I have had nothing but trouble with FF, some websites, like Lumosity, don't run on FF but are flawless on chromium. On the other hand, the decision not to include proper PDF integration into Chromium - I understand the reasons - makes it utterly useless to me. SO basically, I don't care what the default is, on my system both are gone.

---

### Post by shoushikochou on 2013-05-16
i thought chromium was chrome

---

### Post by monkeybrain2012 on 2013-05-17
I watched the summit video. Basically this is just pushed by a bunch of Chromuim enthusiasts. They have not given a single valid reason for the switch. They were listing problems and missing features in Chromium which are all solved in Firefox, they either dismissed these as "non problems" because they are not typical in the "general use case", or that they may be able to work out some solutions by reinventing the wheel (like running Firefox's pdf js in Chromium??!!) And their ultimate justification is that they should switch because Chrome is outpacing FF in other platforms and Chromium would be perferrred by the "general user" on Ubuntu . Chrome and Chromium are not the same, Chrome has a lot of features that Chromium lacks, so if the "general user" cannot tell the difference then she is just going to conclude that Ubuntu is such a crappy platform that even Chrome doesn't work as well. Great way to advertise  Ubuntu. 

Finally a guy said that Chromium is inferror to Firefox in terms of functions and features but they can hopefully close the gap so that they can compare the two based on merits?? Isn't  the comparison already made by his own admission? Isn't functons and features the decisive standard of merits??!!I They didn't make any sense.

---

### Post by craig10x on 2013-05-17
> **shoushikochou said:**
> i thought chromium was chrome

Chromium is the completely open source version of what becomes google chrome....it is their development channel, then they take it and put some refinements into, and some other tweaks and put it out as Google Chrome (the licensed version)....

Chrome adds such refinements as a built in pdf reader (so you can read pdf files without downloading them to your hard drive, although you still have the option to do so from it, if you so desire) and the "pepperflash" flash plug in (they have an agreement to provide the current version of adobe flash in it) Chromium does not contain those features and for flash, it uses the flash you get in the ubuntu restricted extras...and that flash is old and only gets security updates and no new versions because adobe dropped it for linux (except for pepperflash with google)....

Chrome also automatically adds a "ppa updater" to your software sources so you always get the latest version through ubuntu's software updater...
And the Chrome version is always more up-to-date then Chromium is (Chromium is still in the Version 25 series where as Chrome is in Version 26 series)...

But ubuntu can't put Chrome as the default browser already installed because it has a license agreement you must say yes to in order to download it...
So, the way we get it is from the Google Chrome website, where we download the deb file and then right click it and have the ubuntu software center install it...

The Chromium version you can get in the Ubuntu Software Center...

I think that should clarify it for you... :)

---

### Post by newbie2 on 2013-05-17
> Ubuntu developers are planning a discussion on an Ubuntu mailing list to solicit a more broad range of feedback on switching from Firefox to Chromium.
[http://news.techeye.net/software/firefox-about-to-lose-the-ubuntu-linux-vote](http://news.techeye.net/software/firefox-about-to-lose-the-ubuntu-linux-vote)
:roll:

---

### Post by vasa1 on 2013-05-17
Existing threads:
[http://ubuntuforums.org/showthread.php?t=2144962](http://ubuntuforums.org/showthread.php?t=2144962)
[http://ubuntuforums.org/showthread.php?t=2145873](http://ubuntuforums.org/showthread.php?t=2145873)

---

### Post by smellyman on 2013-05-17
> **monkeybrain2012 said:**
> I watched the summit video. Basically this is just pushed by a bunch of Chromuim enthusiasts. They have not given a single valid reason for the switch. They were listing problems and missing features in Chromium which are all solved in Firefox, they either dismissed these as "non problems" because they are not typical in the "general use case", or that they may be able to work out some solutions by reinventing the wheel (like running Firefox's pdf js in Chromium??!!) And their ultimate justification is that they should switch because Chrome is outpacing FF in other platforms and Chromium would be perferrred by the "general user" on Ubuntu . Chrome and Chromium are not the same, Chrome has a lot of features that Chromium lacks, so if the "general user" cannot tell the difference then she is just going to conclude that Ubuntu is such a crappy platform that even Chrome doesn't work as well. Great way to advertise  Ubuntu. 

Finally a guy said that Chromium is inferror to Firefox in terms of functions and features but they can hopefully close the gap so that they can compare the two based on merits?? Isn't  the comparison already made by his own admission? Isn't functons and features the decisive standard of merits??!!I They didn't make any sense.

ding ding ding

FF imo makes a far superior browser.   Opinions/prefs of people will differ so who cares.

However, FF is the epitome of FOSS and the epitome of an open web with true web standards.

Going to google sounds so dirty and makes my skin crawl.  It would be like adding some Amazon searching in your OS!  Who would do such a thing?

---

### Post by vasa1 on 2013-05-17
> **shoushikochou said:**
> i thought chromium was chrome

[FONT=Comic Sans MS]This may help[/FONT] ;)

---

### Post by craig10x on 2013-05-17
@smellyman: not at all...i see the same targeted ads on firefox browser that i see on the Chrome browser...they both track you and target the ads accordingly....
so it certainly isn't cleaner...

---

### Post by malspa on 2013-05-17
> **smellyman said:**
> Opinions/prefs of people will differ so who cares.

Yep, who cares. Install whatever browser you prefer to use if it isn't offered as the default browser.

---

### Post by vasa1 on 2013-05-17
> **malspa said:**
> Yep, who cares. Install whatever browser you prefer to use if it isn't offered as the default browser.
???

Being the default <any_software_here> may have implications in terms of support.

---

### Post by DMGrier on 2013-05-18
I don't think it matters honestly for those of us who have been using Ubuntu for a while since we all have preferences of our favorite web browser but I think for new users to ubuntu it could set a bad first impression, I don't think chromium is horrible but today I gave it a try  for the first time and I am constantly having plugin crashes.

If there is a open source alternative that is equal to a proprietary I will always pick that but in some cases proprietary wins and that is why many of us Ubuntu since you can have a nice mixture or open source and proprietary tools working together to provide the best user experience. What bothers me is some day and I would expect by early next year the flash plugin will be out of date and then what Canonical? Provide a product with not all functioning tools? I am sure there is a way for Canonical to work something out with google to ship chrome on Ubuntu, or would it be possible to include the pepper plugin in the Ubuntu restricted extras for Chromium?

---

### Post by carl4926 on 2013-05-18
> **DMGrier said:**
>  would it be possible to include the pepper plugin in the Ubuntu restricted extras for Chromium?

I asked about this at Medibuntu
But there was some issues:
> [FONT=arial]Howdy,[/FONT]

[FONT=arial]Re: [/FONT][https://answers.launchpad.net/medibuntu/+question/227027](https://answers.launchpad.net/medibuntu/+question/227027)

[FONT=arial]A while ago I looked into doing this, and since then I've made a package[/FONT]
[FONT=arial]and a script to do just what you want there.  However, due to the[/FONT]
[FONT=arial]license, you can't package (pepper) flash[1], if you're interested in[/FONT]
[FONT=arial]that bit.  Otherwise, the source of the package is at:[/FONT]

[FONT=arial]dget [/FONT][http://vanir.unit193.tk/source/chromium-](http://vanir.unit193.tk/source/chromium-)
[FONT=arial]pepperflash_11.7.700.169-1.dsc[/FONT]

[FONT=arial]You can drop my name off it fully, I don't care.  If you use it, you may[/FONT]
[FONT=arial]want to fix d/copyright, it's hardly formatted so gives lintian errors.[/FONT]
[FONT=arial]If you end up using the package, I have a couple scripts that help me[/FONT]
[FONT=arial]keep it up to date I can share too.[/FONT]

[FONT=arial][1] [/FONT][https://www.google.com/intl/en/chrome/browser/privacy/eula_text.html](https://www.google.com/intl/en/chrome/browser/privacy/eula_text.html)
[FONT=arial]Adobe section 3a[/FONT]
[FONT=arial]Source for the script is [/FONT][http://unit193.tk/download-flash](http://unit193.tk/download-flash)
Yet they did it over at Packman/openSUSE

---

### Post by pqwoerituytrueiwoq on 2013-05-18
Is there any poll for users to take relating to this?

---

### Post by MadmanRB on 2013-05-18
You see there is the reason for ditching firefox, it will be rendered useless once flash 11.2 goes kaput.
Chromium is compatible with pepperflash and firefox isnt so do the math, cut loose the browser that will be useless for things like youtube and go to a browser that will do such things.
In fact all distros should ditch firefox, shumway has a long way to go and html5 is not even on the main platter yet.

---

### Post by craig10x on 2013-05-18
Yep...that's another factor, firefox doesn't have the pepperflash agreement with adobe to provide the latest versions for linux for google....you are just getting security updates on a rather outdated adobe flash for linux (the last one they did before stopping the linux version)...

Ideally, Chrome would be best since it already has it (as well as the built in pdf reader) so it is a shame they can't offer it...but even Chromium will work with pepper of course...If they have to go with Chromium, they should offer it as an option to add it on in the software center (even i it needs to include an agreement you have to say yes to)...perhaps they could also offer the pdf reader as well, in that same manner...

I wish the developers were reading this thread, i think i just made a good suggestion here :)

---

### Post by CharlesA on 2013-05-18
Polls don't do jack, especially polls here, cuz the devs rarely visit forums and prefer to stick to mailing lists.

Do any "normal users" actually use the mailing lists? I know I don't.

---

### Post by pissedoffdude on 2013-05-18
Eh, I don't see a problem.  Personally, I prefer chromium and so do many other users, and those who use firefox as their primary browser will install it anyway

---

### Post by Elfy on 2013-05-18
> **pissedoffdude said:**
> Eh, I don't see a problem.  Personally, I prefer chromium and so do many other users, and those who use firefox as their primary browser will install it anyway

Which is the same argument people who prefer firefox use :)

Merged threads.

---

### Post by Elfy on 2013-05-18
> **pqwoerituytrueiwoq said:**
> Is there any poll for users to take relating to this?

Not that I'm aware of.

Though apparently

> Final decision to be taken after feedback with community

(From [noparse]http://www.omgubuntu.co.uk/2013/05/chromium-to-replace-firefox-as-default-browser-in-ubuntu)[/noparse]

Not sure where that quote comes from - nor if it's even a real point or just something someone heard in passing by one person amongst others. 

I'd guess that there would be more information from the UDS session - but I didn't listen in and I'm not going to now either.

The video and etherpad for that session are here [http://summit.ubuntu.com/uds-1305/meeting/21788/foundations-1305-chromium-default-browser/](http://summit.ubuntu.com/uds-1305/meeting/21788/foundations-1305-chromium-default-browser/)

irc logs are here [http://irclogs.ubuntu.com/2013/05/16/%23ubuntu-uds-client-1.html#t16:01](http://irclogs.ubuntu.com/2013/05/16/%23ubuntu-uds-client-1.html#t16:01)

---

### Post by BigSilly on 2013-05-18
Personally I would still want Firefox. I'd like to see it stay as default purely as I think it's better, but as long as it's available and I can remove Chromium that's fine.

I don't know why people are stating Flash support as a major factor for Chromium adoption. I'm no expert but it looks to me like Flash is in its final throes. I use a Nexus 7 too and that doesn't feature any Flash support at all (unless you sideload it - I don't), and it is not missed. While obviously Ubuntu is a different beast from Android, I still feel the web is done with Flash, and it isn't a major game changer nowadays. Let it die.

---

### Post by goldshirt9 on 2013-05-18
each to their own, can always install ff later on

---

### Post by BlinkinCat on 2013-05-18
> **goldshirt9 said:**
> each to their own, can always install ff later on

That's what I'll be doing - :)

---

### Post by vasa1 on 2013-05-18
> **Elfy said:**
> ...
Not sure where that quote comes from - nor if it's even a real point or just something someone heard in passing by one person amongst others. 
...
If you're referring to "*Final decision to be taken after feedback with community*", Jason Warner @42:35 and 43:35 and right at the end said something that could be taken that way: putting things up on the mailing list.

What fun. Already the OMG comments section has the usual suspects :D

---

### Post by MadmanRB on 2013-05-18
> **BigSilly said:**
> Personally I would still want Firefox. I'd like to see it stay as default purely as I think it's better, but as long as it's available and I can remove Chromium that's fine.

I don't know why people are stating Flash support as a major factor for Chromium adoption. I'm no expert but it looks to me like Flash is in its final throes. I use a Nexus 7 too and that doesn't feature any Flash support at all (unless you sideload it - I don't), and it is not missed. While obviously Ubuntu is a different beast from Android, I still feel the web is done with Flash, and it isn't a major game changer nowadays. Let it die.

The fact its still around is where the issue lays, sure flash might be dying but it will take longer then the time we have left to get out of its shadow.

---

### Post by monkeybrain2012 on 2013-05-18
> **BigSilly said:**
> 
I don't know why people are stating Flash support as a major factor for Chromium adoption. I'm no expert but it looks to me like Flash is in its final throes. I use a Nexus 7 too and that doesn't feature any Flash support at all (unless you sideload it - I don't), and it is not missed. While obviously Ubuntu is a different beast from Android, I still feel the web is done with Flash, and it isn't a major game changer nowadays. Let it die.

I don't know why flash would even be an issue in this discussion. Chromium is not Chrome, it doesn't have pepper flash. It uses the same flash plugin as Firefox.

Some people claim that there are ways to rigg Chromium to install pepper flash, that is just idiotic even if it works. If you want pepper flash just install Chrome, end of story.

---

### Post by monkeybrain2012 on 2013-05-18
> **DMGrier said:**
> 
If there is a open source alternative that is equal to a proprietary I will always pick that but in some cases proprietary wins and that is why many of us Ubuntu since you can have a nice mixture or open source and proprietary tools working together to provide the best user experience. What bothers me is some day and I would expect by early next year the flash plugin will be out of date and then what Canonical? Provide a product with not all functioning tools? I am sure there is a way for Canonical to work something out with google to ship chrome on Ubuntu, or would it be possible to include the pepper plugin in the Ubuntu restricted extras for Chromium?

There is already an open source browser that is better than proprietary, it is called Firefox. Open vs proprietary has no bearing on this discussion. Chromium is also (sort of) open source but  lacks many features and therefore sucks.  flash is proprietary no matter what browser you use. 

As said before if you want up to date flash, just install Chrome. I think flash is way over rated. I am much more interested in browsers where media plugins actually work and that is Firefox on Linux (Chrome/Chromium  is useless if you need to access contents that require windows media plugins for example)  In my Fedora install I haven't even installed system flash but I can watch most flash videos just fine on Firefox with greasemonkey scripts and gecko-mediaplayer (Youtube, Vimeo, dailymotion, ted etc) Much better performance than flash and with hardware acceleration. If I have to use flash in occasions where these scripts don't work, just fire up Chrome. I use Chrome only for this, otherwise Firefox is a lot better and feature complete.

---

### Post by Elfy on 2013-05-18
> **vasa1 said:**
> If you're referring to "*Final decision to be taken after feedback with community*", Jason Warner @42:35 and 43:35 and right at the end said something that could be taken that way: putting things up on the mailing list.

What fun. Already the OMG comments section has the usual suspects :D

So it wasn't said as such then ;)

I'd have no idea who the normal omg suspects are I try hard not to look at it. 

Though perhaps they mean the 20 or 30 on the irc logs - hard to tell as usual.

---

### Post by s9032g@comcast.net on 2013-05-18
I run Chrome in beta on windows 7 and it works well - constantly updated. How about doing the same thing with Cromium?

Tried Cinnamon, hated it, didn't work smoothly. Removed it.

---

### Post by uRock on 2013-05-19
I have 12.04 on my netbook and have no reason to updte any time soon, but if I did, then I would be installing Firefox and uninstalling Chromium. I only run ubuntu via the 12.04 LiveCD on my desktop system, so this change won't be affecting me any time soon.

---

### Post by binaryhermit on 2013-05-20
I don't particularly like this proposed change.  However, since it's dead simple to install firefox anyway, it's not that big of a deal.  I mean, it's not like they're removing firefox from the repos.

---

### Post by craig10x on 2013-05-20
Right...it is simply a matter of installing the other browser....Ubuntu has always come with firefox as the default...since i like chrome, i install that and use it...and even though i don't use firefox very often, i leave it on my unity dock (even though i could remove it, of course)...not a biggie, really...

Even with Chromium becoming the default (if they decide as such) since i prefer chrome, i will still be doing the same thing i was doing before...

---

### Post by Lyfang on 2013-05-20
Pepper Flash installer that works with Chromium on Ubuntu 13.04: [https://launchpad.net/~skunk/+archive/pepper-flash](https://launchpad.net/~skunk/+archive/pepper-flash)

---

### Post by monkeybrain2012 on 2013-05-20
> **Lyfang said:**
> Pepper Flash installer that works with Chromium on Ubuntu 13.04: [https://launchpad.net/~skunk/+archive/pepper-flash](https://launchpad.net/~skunk/+archive/pepper-flash)

Can't see the point really. If you are an open source purist then you won't install flash, period, If you are not why not just install Chrome? Chromium maybe interesting for developers, but it is neither here nor there for end users. Other than flash Chromium also lacks many other features, the video summit mentioned pdf reader and they suggested that they should get the evince developers to make a customized plugin for Chromium (guess these guys didn't know about the old mozplugger) is this a joke?

---

### Post by monkeybrain2012 on 2013-05-20
> **craig10x said:**
> Right...it is simply a matter of installing the other browser....Ubuntu has always come with firefox as the default...since i like chrome, i install that and use it...and even though i don't use firefox very often, i leave it on my unity dock (even though i could remove it, of course)...not a biggie, really...

Even with Chromium becoming the default (if they decide as such) since i prefer chrome, i will still be doing the same thing i was doing before...

Only if it is easy to remove Chromium, but what if removing it takes 100 packages along with it? (like removing konqueror in Kubuntu or iceweasel in Debian) I use FF and occasionally Chrome, I don't really want to keep a rather useless third browser around.

---

### Post by monkeybrain2012 on 2013-05-20
Leaving aside the actual inferiority of Chromium with respect to FF (which can be objectively assessed based on features, even the Chromium pushers on the video admitted that) , I find the prime reason given to the change  indefensible on many levels. 

The claim is that since Chrome (not Chromium, mind you) is getting more popular than Firefox on the proprietary platforms Linux should follow suits to abandon Firefox. First of all the fact that some people may find better experience in using Chrome doesn't translate to Chromium which is a vastly crippled version of Chrome in terms of features, people are not so stupid that they would just go by the branding similarity. Secondly, these guys sound as though Firefox is dead , which is entirely false, it is neck in neck with Chrome in terms of user base, the growth of both is mainly at the expense of IE. Mozilla, however, is the epitome of open source and the staunchest defender and champion of  open web standard, much more than Google, If indeed it is taking a beating on the proprietary platforms as alleged  it is  all the more reason for Linux distros to stick with it.

---

### Post by craig10x on 2013-05-20
Still wish there was a way they could have Chrome instead of Chromium...as you said, Chromium is like a stripped down version, where as (to me) Chrome is quite comparable to Firefox and even has slightly better web page rendering...it compares to safari on the mac and that's probably because it's underbase is quite similiar...

---

### Post by VeeDubb on 2013-05-20
> **monkeybrain2012 said:**
> ....people are not so stupid that they would just go by the branding similarity.

I agree with everything you just said, except that bit.  It would be nice if that were true, but the entire marketing industry exists to prove that statement wrong.  :P

---

### Post by monkeybrain2012 on 2013-05-20
> **craig10x said:**
> Still wish there was a way they could have Chrome instead of Chromium...as you said, Chromium is like a stripped down version, where as (to me) Chrome is quite comparable to Firefox and even has slightly better web page rendering...it compares to safari on the mac and that's probably because it's underbase is quite similiar...

Depends on your use case. In my case even Chrome is not comparable to FF. I regularly have 100+ tabs open in FF, that will freeze my computer completely if I do that with Chrome, can't get the addon I use in FF in Chrome ( e.g videodownloadhelper, the Chrome equivalent just sucks) streaming doesn't work at all or barely in Chrome if it is not flash, if I accidentally close a tab I cannot reopen it with all the history intact like in FF and more..  I don't notice any speed difference except FF may take a little longer to start up (but I have 100+ tabs open) and once started both are smooth.

---

### Post by monkeybrain2012 on 2013-05-20
> **VeeDubb said:**
> I agree with everything you just said, except that bit.  It would be nice if that were true, but the entire marketing industry exists to prove that statement wrong.  :P

True, but that kind of deceptions usually backfire. If some unsuspecting new user tries out Ubuntu and confuses Chromium with Chrome (as these guys in the video summit wished), he/she would soon discover that features he/she takes for granted in Windows or Mac are missing in Ubuntu's version of "Chrome" and comes to the conclusion that Ubuntu is a crappy OS where even Chrome doesn't work as well.

---

### Post by lovebluesky2009 on 2013-05-20
it depends, I myself use chromium as the main web browser before, but since last year, I found firefox is more suitable for me. if you do not want use firefox, just set chromium as your default web brower, it's easy, you do not have to wait for chromium become the default of the UBUNTU, as far as i know, firefox still has lots of fans like me

---

### Post by smellyman on 2013-05-20
Also, part of the reason Chrome is gaining popularity is the shear amount of advertising.  Chrome is suggesested on so many web installs etc.  "make the web faster".  So many of my users install it or ask if they "need" to install it because it says it will make the "web faster".  Then boom it is their default web browser.  Many of them have no idea they made the switch to another browser.  LOL

---

### Post by alphacrucis2 on 2013-05-20
I find Firefox to be better all round. I have even had Chrome crash on google's own google apps where Firefox has worked perfectly.

---

### Post by 3mutts on 2013-05-20
I find them to be pretty equal in terms of compatibility, speed, amount of Addons, and new features included in new releases.

---

### Post by vasa1 on 2013-05-20
> **3mutts said:**
> I find them to be pretty equal in terms of compatibility, speed, amount of Addons, and new features included in new releases.
Whether the "amount of Addons" is an aspect to be given importance is one thing, but the quality can differ. Two clear examples are AdBlock Plus and Stylish. Both extensions have far more features in the Firefox version than in the Chrome version. I don't use NoScript but, again, there's no comparison between NoScript (Firefox) and "equivalents" available for Chrome.

---

### Post by s9032g@comcast.net on 2013-05-21
I keep the default Firefox only because there is a very small chance that Chromium won't work at a given site. Chromium/Chrome is by far the simple and fast connection. Firefox come in third at best, after Chrome and IE10.
Firefox has a lot of extensions because it needs them - and they don't always work well together.

---

### Post by LordDelta on 2013-05-26
> **s9032g@comcast.net said:**
> I keep the default Firefox only because there is a very small chance that Chromium won't work at a given site. Chromium/Chrome is by far the simple and fast connection. Firefox come in third at best, after Chrome and IE10.
Firefox has a lot of extensions because it needs them - and they don't always work well together.

Wait what lol?

IE10? XD

Go use Windows you silly person.

I personally have always hated the entire IE experience. I've been a heavy duty Google Chrome user, and the ONLY thing that was better about it was some new features.

Firefox has many many more benefits. And I do not support an Open OS turning to the Spy State browser as its default. The metrics problem at Google is terrible, and getting to the point of being criminal.

Make Chrome the default Ubuntu browser if you support surveillance states.

---

### Post by Rob Sayer on 2013-05-29
> **vasa1 said:**
> Whether the "amount of Addons" is an aspect to be given importance is one thing, but the quality can differ. Two clear examples are AdBlock Plus and Stylish. Both extensions have far more features in the Firefox version than in the Chrome version...

... however, I'm seriously thinking of using chromium (already installed) instead of firefox because adblock plus is no longer working for me with firefox, and it's the main reason I use it.  I'm also sick of ff getting steadily slower every new version since v.5.

---

### Post by vasa1 on 2013-05-29
> **Rob Sayer said:**
> ... however, I'm seriously thinking of using chromium (already installed) instead of firefox because adblock plus is no longer working for me with firefox, and it's the main reason I use it.  I'm also sick of ff getting steadily slower every new version since v.5.
If that is your experience, you should certainly use chromium.

---

### Post by Sam Mills on 2013-05-29
> **monkeybrain2012 said:**
> Just make it easy to uninstall and I am happy.
```
sudo apt-get remove chromium-browser
```
Easy enough?

---

### Post by monkeybrain2012 on 2013-05-30
> **Sam Mills said:**
> ```
sudo apt-get remove chromium-browser
```
Easy enough?

Not quite. Try to do that with iceweasel in Debian or Konqueror in Kubuntu, it will remove half of your desktop. My point is that I don't care if Chromium is default as long as I can remove it easily WITHOUT GETTING INTO DEPENDECY PROBLEMS. Is that clear enough?

---

### Post by vasa1 on 2013-05-30
> **monkeybrain2012 said:**
> Not quite. Try to do that with iceweasel in Debian or Konqueror in Kubuntu, it will remove half of your desktop. My point is that I don't care if Chromium is default as long as I can remove it easily WITHOUT GETTING INTO DEPENDECY PROBLEMS. Is that clear enough?
Konqueror isn't just a browser so the analogy may not be appropriate. I've installed and purged (not removed) several browsers several times without dependency issues. Here I'm using "dependency" in a very restricted sense.

There's one interesting point to note. And that is that the "system" will insist that you have a browser that it (the system) recognizes. So let's say we talking about a distro that comes with just Browser_A. If we try to remove or purge Browser_A using apt-get, the system will automatically inform us that it's going to install Browser_B in Browser_A's place. I wrote a bit about it [here]("http://ubuntuforums.org/showthread.php?t=2061033") in the context of Lubuntu.

---

### Post by craig10x on 2013-05-30
You have to remove it? why? is your hard drive that small?  ;)
All you have to do is is point your mouse at it, right click (remove from favorites) you will never have to see it again...

Then install your browser of choice and pin it to the unity dock...

What is this obsession some have that they must un-install something they don't use... I don't use Libre Office nor do i use Firefox (i install Chrome which is MY favorite)... but i don't uninstall them...
I think hard drives these days are kinda large these days, aren't they...

---

### Post by mips on 2013-05-30
> **landersohn said:**
> I do think Chromium is better than FF: I have had nothing but trouble with FF, some websites, like Lumosity, don't run on FF but are flawless on chromium. On the other hand, the decision not to include proper PDF integration into Chromium - I understand the reasons - makes it utterly useless to me. SO basically, I don't care what the default is, on my system both are gone.

I can install pepper flash & pdf integration with a simple install command on Arch based distros (yaourt -S chromium-pepper-flash-stable chromium-libpdf-stable). Don't see why this can't be done on Ubuntu.

---

### Post by craig10x on 2013-05-30
> **mips said:**
> I can install pepper flash & pdf integration with a simple install command on Arch based distros (yaourt -S chromium-pepper-flash-stable chromium-libpdf-stable). Don't see why this can't be done on Ubuntu.

Actually, it wouldn't be bad to have Chromium as the default browser if ubuntu would have an optional package that you could install (and accept any license agreement if needed like we do with getting the microsoft fonts) which would automatically add the 2 items (pdf viewer and pepper flash plug in)...I wonder if the developers have thought of doing that...

Only thing is...do you get updates on your pdf viewer and pepper flash when you install it like that?

---

### Post by JamesTheAwesomeDude on 2013-05-30
I personally would love to see Chromium added as the default for Ubuntu - I was one of FF's biggest fans, and it will always have a special spot in my heart (and my hard drive ;),) but the fact is, Firefox is getting slower as time goes by. I originally stuck to Firefox anyway, because I thought it was the only good open-source browser, but with Chromium becoming such an excellent, modern browser, I think it's time to take the plunge.
The only real problem is getting Launchpad's builders on the ball. Their version of Chromium is like 5 versions stale..

For those who are worried about media compatibility, Chromium offers support for plugins, so all we need to do is beef up the media options in the Restricted/Universe repositories, and voilà! If that doesn't work, we can always just mooch off of Firefox's code... the MPL is very permissive... :mrgreen:

---

### Post by monkeybrain2012 on 2013-05-30
> **JamesTheAwesomeDude said:**
> I personally would love to see Chromium added as the default for Ubuntu - I was one of FF's biggest fans, and it will always have a special spot in my heart (and my hard drive ;),) but the fact is, Firefox is getting slower as time goes by. I originally stuck to Firefox anyway, because I thought it was the only good open-source browser, but with Chromium becoming such an excellent, modern browser, I think it's time to take the plunge.
The only real problem is getting Launchpad's builders on the ball. Their version of Chromium is like 5 versions stale..

  

I never get this complaint about FF being "slow", it might have been true back in FF 3.6 but since FF4 it has been speeding up quite spectacularly. The start up time may appear to be slower than chrome/Chromium but only if you have no tab opened in Chorme/Chromium. If you have something like 6-7 tabs opened  Chrome/Chromium  will take longer than Firefox to become usable even though its browser interface may appear faster. It is because Chrome/Chromium loads every tab while FF disables all of them but the active one (used the "bartab" addon before FF has this feature, Chrome has something similar called tabmemfree, but it doesn't stop tabs from loading at startup, only time them out later and with it you often lose tabs). On all machines (32bits, 64 bits, Nvidia, Adm Intel) and all the disros I have used (*buntus, Fedora, Debian)  Firefox is always fast (since ver4)

The only occasion where I find Firefox to be slow is on Windows 7 (which I used at work), so I won't be surprised if a lot of the Firefox is slow meme is actually coming from Windows users or dual booters.

---

### Post by JamesTheAwesomeDude on 2013-05-30
> **monkeybrain2012 said:**
> I never get this complaint about FF being "slow", it might have been true back in FF 3.6 but since FF4 it has been speeding up quite spectacularly. The start up time may appear to be slower than chrome/Chromium but only if you have no tab open in Chorme/Chromium. If you have something like 6-7 tabs opened it Chrome/Chromium it will take longer than Firefox to become usable even though its browser interface may appear faster. It is because Chrome/Chromium loads every tab while FF disables all of them but the active one. On all machines I have tried (32bits, 64 bits, Nvidia, Adm Intel) Firefox is always fast.The only exception is in Windows 7.
It's been my experience that the recent updates of Firefox have seemed more sluggish, even after removing all add-ons. In fact, that's what prompted me to start using Chromium in the first place. I don't start up either browser with more than one tab, and I'm not trying to say that Chromium is *definitively* better than Firefox. Firefox is a more robust browser, with stricter adherence to the official W3 standards (SVG support is one of my favorites,) as well as performing more efficiently when loaded down with tabs, BUT - for most everyday purposes, Chromium's Webkit base renders pages well (and fast) enough, also Stack Exchange no longer works well [SIZE=1](at all)[/SIZE] with Firefox on Linux. I know this is a very subjective issue, but with revitalizing older/last-gen machines being one of the main uses of switching to Linux, I think that the everyday performance/startup boost of switching to Chromium would be benificial. Also remember that, just because a browser isn't the default doesn't mean you can't install it in 30 seconds. If anyone feels that Firefox would be a better choice for their browsing needs/habits, they can simply switch browsers in a few clicks (and with Debian's nice package system, you can uninstall the unused browser without too much hassle.) However, for the majority of users without a strong preference, the added speed for normal browsing usage would be appreciated.

---

### Post by codingman on 2013-05-30
> **malspa said:**
> I couldn't care less about which default browser ANY distro comes with,

Same here. I always remove every browser and install elinks. :)

Chromium = Chrome's baby brother.

I don't see why Firefox doesn't work, and if you are going to change browsers, Ubuntu, I would suggest having Chrome.

---

### Post by codingman on 2013-05-30
@James...

Since when does stack exchange not work in FIrefox? It works perfectly fine for me. I have firefox 4 both on a system with 3.2 kernel, and one with 3.8.

---

### Post by vasa1 on 2013-05-30
> **codingman said:**
> @James...

Since when does stack exchange not work in FIrefox? It works perfectly fine for me. I have firefox 4 both on a system with 3.2 kernel, and one with 3.8.
@James,
No problems with Firefox. As someone pointed out, ever since its rapid release cycle, it's just getting better and better. I use both Firefox and Chrome and don't see much of a difference in speed.
No problems accessing any of several Stack Exchange sites with Firefox. Have you mentioned it in any meta site of SE? Link?
In what way is Chrome lacking in SVG support? Or what is implied by "Firefox is a more robust browser, with stricter adherence to the official W3 standards (**SVG support** is one of my favorites,)"?

BTW, I use Firefox, and Chrome and Chromium.

---

### Post by Rob Sayer on 2013-05-31
> **vasa1 said:**
> If that is your experience, you should certainly use chromium.

Actually I found out how to make adblock plus work again in ff from the adblock forums.  Just refresh the list.

I wouldn't personally really care if ubuntu installed with whatever browser.  Just install what you like.  Kubuntu comes with just rekonq and I *hate* that program.  An easy fix though.

---

### Post by neu5eeCh on 2013-05-31
Does it really matter what the default browser is? 

But if I were going to have a say, I would argue strongly against Chrome or Chromium. I do a lot of WordPress blogging and both Google's browsers are _worse_ than useless. They actually make formatting _more_ difficult. Here are two concrete examples: **1.)** If you hit coontrol-delete in FF, you don't get a space between one paragraph and the next and the formatting is carried over. If you use the same key-combo in Chrome or Chromium, not only do you *not* get single space, but it fouls up the spacing of the paragraph above. **2.) **Moving an image from one paragraph to another is painless is FF. Chrome or Chromium both add hard-returns where the image *used* to be. This means having to re-format the paragraph and backspacing doesn't work without messing up the prior paragraph. Both of Google's browser's are PITA's.  

I finally completely removed Chrome. 

Worst of all, the memory management in Chrome is a complete disaster. FF isn't all that the much better, but it at least FF isn't throwing around bits and pieces of itself like an exploding blob of jello  (see Task Manager). Use Chrome long enough,. and it will merrily eat up whatever memory is available.

---

### Post by VeeDubb on 2013-05-31
> **VTPoet said:**
> Does it really matter what the default browser is?

Nope.  It truly doesn't.

You dislike chrome and chromium because of a very specific set of behaviors when editing text in the browser that most users couldn't care less about.

I love Chrome because it integrates so well with google services and syncs automatically with my android tablet and phone, which most users either couldn't care less about, or choose to accomplish using pluggins for their favorite browser.

Everybody has their favorite browser for one reason or another, but pretty much all of them work just fine for what you'd expect a default browser to do.  The simple fact is that installing a different browser and making it the default is trivial on any computer these days, and especially trivial using Ubuntu.  Most anything they'd use as a default browser takes up so little space that leaving it in place and simply not using it should be a non-issue, and if you want to remove it, you can.  *sudo apt-get purge firefox*  **ta-da!**

I just tried it, and the only thing it took with it was a bunch of firefox addons I'd installed through repos, a Unity pluggin that I didn't use, and a remote log-in config package I didn't use.

---

### Post by mips on 2013-05-31
> **monkeybrain2012 said:**
> I never get this complaint about FF being "slow", it might have been true back in FF 3.6 but since FF4 it has been speeding up quite spectacularly. 
No I reckon FF is slow compared to Chromium but the startup is much faster. I use to swear by FF but no more.

---

### Post by Anders Stroem on 2013-05-31
I don't mind using either Chrome/-ium or Firefox. Usually I will spend a couple of weeks using one of them, and along comes a need-to-have feature in the other, warranting a switch.

---

### Post by neu5eeCh on 2013-05-31
> **VeeDubb said:**
> You dislike chrome and chromium because of a very specific set of behaviors when editing text in the browser that most users couldn't care less about.


Possibly. However, there are presently [66,488,04]("http://en.wordpress.com/stats/")[3 Wordpress.com sites]("http://en.wordpress.com/stats/"). And Chrome _*sucks air on every one of them*_. How many of those bloggers care? I don't know. But even if it's just a third of them, that's a serious limitation. Why make your default browser one that's a sucky, train wreck on one of *the* most popular free blogging sites in the universe (let alone wordpress.net)?  :-k

Just sayin'.

P.S. And yeah, I could back up that "universe" assertion, but then the men in black would come knocking on my door.

---

### Post by VeeDubb on 2013-06-01
> **VTPoet said:**
> Why make your default browser one that's a sucky, train wreck...

Just for the sake of discussion, I don't have the statistics handy, but I suspect that there are more android users out there than 'active' wordpress bloggers, so your argument could just as easily be used to support using Chrome/ium.

My point wasn't that switching to chromium should be done.

My point was that the entire discussion is moot because installing a different browser to use as default is trivial, and both chromium _and_ firefox meet the reasonable expectations for a pre-installed default browser.  i.e. - you can browse the web with them.

---

### Post by uRock on 2013-06-01
I have an Android and would not want its browser synced with the one on my PC. The capability of syncing is one of the reasons I stopped using Chrome. I see that function as a privacy reducing security hazard. I use Firefox with Ghostery and, though it is offered for Chrome, the purpose is negated when the browser is backing itself up to a server that is shared with 3rd party sources without my consent or knowledge.

---

### Post by CharlesA on 2013-06-01
Firefox offers sync as well, but I have it disabled.

---

### Post by OrangeCrate on 2013-06-01
> **CharlesA said:**
> Firefox offers sync as well, but I have it disabled.

I used the Firefox sync for a short time a couple of years ago, and I seem to remember, that there were a lot of hoops to jump through to get it hooked up. I prefer the Chromium/Chrome set-up now, and use it on three different computers.

---

### Post by CharlesA on 2013-06-01
> **OrangeCrate said:**
> I used the Firefox sync for a short time a couple of years ago, and I seem to remember, that there were a lot of hoops to jump through to get it hooked up. I prefer the Chromium/Chrome set-up now, and use it on three different computers.

I think I used it once and only for bookmarks as I don't save passwords via the browser. I don't think I even bothered syncing it with another machine cuz it was so clunky.

I think I'll stick to keepass for my password management. ;)

---

### Post by JamesTheAwesomeDude on 2013-06-09
> **vasa1 said:**
> No problems accessing any of several Stack Exchange sites with Firefox. Have you mentioned it in any meta site of SE? Link?> **codingman said:**
> Since when does stack exchange not work in FIrefox? It works perfectly fine for me. I have firefox 4 both on a system with 3.2 kernel, and one with 3.8.I can't delete my comments or edit/flag/delete posts at all in Firefox. I think may have mentioned it in a meta somewhere, but I think it either died or got closed as Too Localized.. Doesn't matter now, though, as I seem to be the only one with the problem, and I'm using Chromium now.
> **vasa1 said:**
> In what way is Chrome lacking in SVG support? Or what is implied by "Firefox is a more robust browser, with stricter adherence to the official W3 standards (**SVG support** is one of my favorites,)"?

BTW, I use Firefox, and Chrome and Chromium.Oh, wow, I just saw that Chromium added SVG support... First time I tested it was a long time ago, and all I saw was raw XML... Yay for my new browser!:biggrin:


> **codingman said:**
> Same here. I always remove every browser and install elinks. :)

Chromium = Chrome's baby brother.

I don't see why Firefox doesn't work, and if you are going to change browsers, Ubuntu, I would suggest having Chrome.Do you have any idea of the uproar that would ensue from including a proprietary browser as *the default* in Ubuntu? Proprietary drivers are one thing (and controversial at that,) but including a closed-source browser with a bad rap for tracking users' behavior in the default software suite is going a little overboard...

---

### Post by craig10x on 2013-06-09
Tracking your behavior? What do you think your search engines do? your web browser? and probably a lot of websites you use frequently... same thing...6 of one half a dozen of the other....
The only way any of you "privacy hounds" can get totally privacy is to...here comes the obvious...stop using the internet completely :D

I wish ubuntu would make chrome the default (not that it matters to me that much as i download and install it in 5 minutes) still, would be nice...
Zorin Os has Chrome as the default...of course, they are small...

---

### Post by uRock on 2013-06-10
I want this browser on my system! [http://spikes.com/](http://spikes.com/)

---

### Post by Copper Bezel on 2013-06-10
I think you mean you want it not on your system. = ) An odd but intriguing concept, a lot like running a browser through a VM and with less overhead. All that hardware separation seems like it'd be a pain, though, for some features - while it would certainly stop Flash adverts from stealing your camera and mic, it might make Google Hangouts a bit more complicated to set up. 
 
I kinda want to know how the browser itself looks and works - I mean, is the interface another Chromium respin, I wonder? (Not that that would make it any less unique a product!)

---

### Post by kahrkunne on 2013-06-12
Honestly that would be a reason for me to stop using Ubuntu.

Yes, I know that it's open source and all, but it's still made by google. I don't trust google.

---

### Post by uRock on 2013-06-12
> **kahrkunne said:**
> Honestly that would be a reason for me to stop using Ubuntu.

Yes, I know that it's open source and all, but it's still made by google. I don't trust google.

Why would it be a reason to stop using ubuntu? Removing Chromium and installing Firefox can be done in one command. ```
sudo apt-get remove chromium-browser && sudo apt-get install firefox -y
```

---

### Post by craig10x on 2013-06-12
Also, he doesn't trust Google but he does trust search engines, all the websites he visits, social media he participates with (say like facebook, twitter, etc) and so on and so forth...google doesn't do anything that the rest don't do as well, so why single them out in particular?  All i know is, Google makes a great browser (Chrome) which i love better then any other browser i have used...and i would like to see it as the default browser (rather then chromium actually)...but i guess there is just no way that will happen...

---

### Post by vasa1 on 2013-06-14
More:
[Debate Continues on Ubuntu 13.10&#8242;s Default Browser]("http://www.omgubuntu.co.uk/2013/06/ubuntu-developer-continue-to-mull-switch-to-chromium")
and
[https://lists.ubuntu.com/archives/ubuntu-desktop/2013-June/004240.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2013-June/004240.html)

---

### Post by vasa1 on 2013-06-14
More:
[Debate Continues on Ubuntu 13.10&#8242;s Default Browser]("http://www.omgubuntu.co.uk/2013/06/ubuntu-developer-continue-to-mull-switch-to-chromium")
and
[https://lists.ubuntu.com/archives/ubuntu-desktop/2013-June/004240.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2013-June/004240.html)

---

### Post by monkeybrain2012 on 2013-06-14
Removed by author for double posting.

---

### Post by monkeybrain2012 on 2013-06-14
> [I]In the past few weeks I’ve  seen quite a few articles and comments on the possible switch, and in  light of those I’d like to focus this discussion a few ways.
[/I]
*[I]1. This is NOT about which browser is better.*
 *2. This is NOT about which browser has more features or X, Y or Z feature.*
 *3. Openness and freedom are still  part of our core values. However I’d rather not turn this thread into a  “who is more open/free” debate.*[/I]
* What is important, and  ultimately should be the deciding factor, is the common end user  experience. Which browser, in the common case, will be the best for the  general end user?*

This doesn't even make any sense. What decides end user experience if not "which browser is better" and "which browser has more features"???

I think some people are just trying to push Chromium and even they know their case is weak.

---

### Post by vasa1 on 2013-06-14
It's quite sad that no one has explained clearly why Chromium is so outdated.

The "push" seems to be based on the intended use of "qtwebkit":
[http://ubottu.com/uds-logs/archives/uds-1303/%23ubuntu-uds-appdev-2.log](http://ubottu.com/uds-logs/archives/uds-1303/%23ubuntu-uds-appdev-2.log)
[http://www.youtube.com/watch?v=pfONv4GdmEo](http://www.youtube.com/watch?v=pfONv4GdmEo)

In the log, look at the entry for 2013-03-05T18:45:27. There wasn't a response to that.

---

### Post by Copper Bezel on 2013-06-14
> **monkeybrain2012 said:**
> This doesn't even make any sense. What decides end user experience if not "which browser is better" and "which browser has more features"???

I think some people are just trying to push Chromium and even they know their case is weak.
Depends on what you mean by "better" and what you mean by "features." Consistency and predictable support for unpredictable conditions seem like more important "features" to me than theming or some crazy new tab switcher, for instance (not that either browser in this case has anything to do with those examples.) Fewer buttons can be better than more buttons if the experience is simpler (which probably *is *in this case an argument for Chromium.) Arguing which browsers are "better" or "best" still has to account for best "for whom" and "at what." (Of course, there's just as much chance for arguing about the "experience" or "average user," too, but I can see why Warner would want to avoid getting into another typical browser war argument of the kind we see in Recurring here; whether just stating those three stipulations has any chance of avoiding that is another question.)

---

### Post by vasa1 on 2013-06-14
I suspect the decision has been made a while ago and what's going on now is [put suitable word here]. See the Twitter link: [https://twitter.com/chrisccoulson/status/340150649901678594](https://twitter.com/chrisccoulson/status/340150649901678594)

And for those extremely helpful people who keep coming up with "sudo apt-get install browser_of_your_choice", I wonder if they've really been following things. Perhaps they may be able to explain why Chromium has been stuck at v25 for ages even though a Canonical employee has been assigned to "maintain" Chromium quite a few months ago. 

Maybe the same people have an explanation for the status of [Please update to 27.0.1453.110]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1183086") which has "Importance: undecided" and "Assigned to: unassigned".

---

### Post by uRock on 2013-06-15
> **vasa1 said:**
> I suspect the decision has been made a while ago and what's going on now is [put suitable word here]. See the Twitter link: [https://twitter.com/chrisccoulson/status/340150649901678594](https://twitter.com/chrisccoulson/status/340150649901678594)

And for those extremely helpful people who keep coming up with "sudo apt-get install browser_of_your_choice", I wonder if they've really been following things. Perhaps they may be able to explain why Chromium has been stuck at v25 for ages even though a Canonical employee has been assigned to "maintain" Chromium quite a few months ago. 

Maybe the same people have an explanation for the status of [Please update to 27.0.1453.110]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1183086") which has "Importance: undecided" and "Assigned to: unassigned".

Not sure what being helpful in getting the browser of choice on a system and having to be in the game of maintaining Chromium have to do with each other. It doesn't matter how up to date Chromium is, newcomers will be asking how to get Chrome or Firefox installed and the old timers will open a terminal and get it done. In the end, users are going to want their browser to be something they recognize from Windows or Apple. I will gladly help them get that accomplished.

---

### Post by unbuntu77 on 2013-06-15
right now my sound is all choppy on regular Chrome on Ubuntu. 
Chromium doesn't seem to let you create profiles. 
well that prompted me to Google it and I found this:
[http://www.chromium.org/developers/creating-and-using-profiles](http://www.chromium.org/developers/creating-and-using-profiles)

---

### Post by monkeybrain2012 on 2013-06-15
> **uRock said:**
> Not sure what being helpful in getting the browser of choice on a system and having to be in the game of maintaining Chromium have to do with each other. It doesn't matter how up to date Chromium is, newcomers will be asking how to get Chrome or Firefox installed and the old timers will open a terminal and get it done. In the end, users are going to want their browser to be something they recognize from Windows or Apple. I will gladly help them get that accomplished.

I guess his point is that if Firefox is not the default it probably wouldn't be maintained and become as out of date as Chromium is now. So sudo apt-get install firefox would probably do you no good.

---

### Post by vasa1 on 2013-06-15
> **monkeybrain2012 said:**
> I guess his point is that if Firefox is not the default it probably wouldn't be maintained and become as out of date as Chromium is now. So sudo apt-get install firefox would probably do you no good.

Thank you :)

They could clarify what will happen to Firefox. Will it be moved from main (with support from Canonical) to universe (support by the "community" and all that that implies)? From what I understand, Chris Coulson was looking after both Firefox (stable, beta, and Aurora) **and** Thunderbird. Will Thunderbird remain in main?

---

### Post by smellyman on 2013-06-15
The epitome of all things good in FOSS.  The application that epitmoizes FOSS.  And imo, still the best broweser out there.

dumped for the ulimate spy company.

no thanks.

---

### Post by Erik1984 on 2013-06-15
From a practical standpoint it's not a big problem. Firefox is not installed by default in Kubuntu anyway so I already have to apt-get install firefox as one of my first actions on a fresh install. 

But I agree with smellyman, Firefox has symbolic value. Mozilla may be sponsored by Google but their intentions and spirit seem totally different. Firefox was likely the first open source application that I used, starting on Windows ~ 10 years ago. When I installed Ubuntu I was glad to see Firefox there installed already :) I have used it ever since on any OS installation and still do today. According to what I read Firefox is slow compared to Chrome(ium) but I haven't noticed that myself. The extensions were awesome and still are today. Firefox Forever!

---

### Post by malspa on 2013-06-15
I couldn't care less about "symbolic value." Frankly, I'm surprised by all the whining in this thread and elsewhere about the possibility that Ubuntu will go with Chromium. I use several other distros that don't include my preferred web browser by default, and it's ***no big deal***. Whatever Canonical decides about this is totally fine with me.

---

### Post by uRock on 2013-06-15
> **monkeybrain2012 said:**
> I guess his point is that if Firefox is not the default it probably wouldn't be maintained and become as out of date as Chromium is now. So sudo apt-get install firefox would probably do you no good.

I keep forgetting how easy it is to install from a binary, but I am sure I will remember when the time comes.

---

### Post by monkeybrain2012 on 2013-06-15
> **uRock said:**
> I keep forgetting how easy it is to install from a binary, but I am sure I will remember when the time comes.

Then why bother to maintain it in the first place? Yes, in Debian I do download the binary from Mozilla cos iceweasel is outdated and doesn't work with some addons. Pro. there is no need for installation, it works by just clicking the bin file Con: whenever there is an update the launcher disappears and I have to relink the .desktop file.

---

### Post by monkeybrain2012 on 2013-06-15
> **Euroman said:**
> From a practical standpoint it's not a big problem. Firefox is not installed by default in Kubuntu anyway so I already have to apt-get install firefox as one of my first actions on a fresh install. 

But I agree with smellyman, Firefox has symbolic value. Mozilla may be sponsored by Google but their intentions and spirit seem totally different. Firefox was likely the first open source application that I used, starting on Windows ~ 10 years ago. When I installed Ubuntu I was glad to see Firefox there installed already :) I have used it ever since on any OS installation and still do today. According to what I read Firefox is slow compared to Chrome(ium) but I haven't noticed that myself. The extensions were awesome and still are today. Firefox Forever!

+1

---

### Post by vasa1 on 2013-06-15
> **uRock said:**
> I keep forgetting how easy it is to install from a binary, but I am sure I will remember when the time comes.

That's why Canonical has (or had) a team to "maintain" Firefox and Thunderbird and has a "maintainer" for Chromium. No doubt people who keep forgetting how easy it is to install binaries could help fix this bug: [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1183086](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1183086)

BTW, this topic of discussing the proposed change seems to bother some people. I don't see why. The discussion was initiated in the vUDS. Feedback was solicited.

Anyway, there's always the "report" button. Far more effective than sarcasm.

---

### Post by malspa on 2013-06-15
> **vasa1 said:**
> So why is Chromium (by Canonical/Ubuntu/Community) still at version 25? I think Canonical's Firefox team is more "on time" in terms of providing a current browser to its users.

> **vasa1 said:**
> It's quite sad that no one has explained clearly why Chromium is so outdated.

Yeah, I keep wondering about this, too. If Chromium is chosen as the default browser, one would hope that part of the deal would involve keeping it more up-to-date.

> **vasa1 said:**
> The discussion was initiated in the vUDS. Feedback was solicited.

Then, I wonder if anyone involved with making the decision has been following this thread.

And I wonder if anything posted in this thread has led anyone to change their position or opinion on the matter. Probably not, I'd guess.

Well, it certainly seems to be an important (and often emotional) topic to some people; and for some others -- shrug of the shoulders, "Whatever." I think a lot of good points have been made for and against, and it'll be interesting to see how it all plays out. My guess is that Firefox will remain the default, and everybody will go on as they have before, using whatever browser they prefer most. (Or Chromium will become the default, and everybody will go on as they have before, using whatever browser they prefer most.)

:cool:

---

### Post by monkeybrain2012 on 2013-06-16
I am not sure what kind of users is Chromium supposed to target. Those who want Firefox would uninstall it at the first chance, those who want a Chrome experience will get the real thing and also uninstall Chromium at their first chance. That leaves a few rare people who like an open sourced, albeit crippled Chrome experience and those who like the Chrome feel but are convinced that Google spies on them. Well I don't think there are enough of such people (like Chrome feel but don't want Chrome) to warrant using Chromium as default.

---

### Post by malspa on 2013-06-16
> **monkeybrain2012 said:**
> Well I don't think there are enough of such people (like Chrome feel but don't want Chrome) to warrant using Chromium as default.

You may be right about that.

As for uninstalling "at the first chance," I don't know about other users, but I don't even bother trying to uninstall a distro's default browser if it happens to be one I don't prefer using. Having it there doesn't bother me at all. Maybe it would if hard drive space was an issue, I guess.

---

### Post by craig10x on 2013-06-16
I agree with malspa...even though i rarely use firefox but rather Chrome instead, i  never un-install it...in fact it's on my unity dock as we speak, i don't even remove it from there!
In the case of Chromium as default, i might remove it from my unity dock as it would be a little confusing to see 2 chrome type icons on there (even though they are different colors...lol)
but i wouldn't un-install it, just not use it...

I also agree with monkeybrain2012 scenerio he mentioned above...the problem is they wanting (and insisting) it be Chromium rather then Chrome...that's basically what makes the change useless for so many...

---

### Post by Copper Bezel on 2013-06-16
Yeah, as a Chrome user well aware of the existence of Chromium (I even periodically install it to not use it,) I also wonder who would really be likely to choose to use Chromium. People who want to get away from Google generally shoot a little further afield; to me, Chromium is just a less colorful icon in my Launcher and a loss of the PDF viewer, which I actually use as my default PDF viewer (with --new-window.) 

I think, though, that this is still about the default Ubuntu experience, users who don't care enough to switch browsers. Even for them, though, it's an odd choice, because even for them, there's still some subtle brand recognition in Firefox and Chrome that Chromium doesn't have, and they're still likely to react to that. Chrome or Firefox would still be a familiar icon in an unfamiliar desktop, and I think that does good work in making the desktop feel just a little more accessible. If Chrome isn't an option (and there are good reasons why that seems to be the case,) Firefox still makes the most sense to target those users, and still would whether or not Chromium was the better browser outright.

---

### Post by vasa1 on 2013-06-16
This maybe interesting as background: [ Webkit maintenance strategy]("https://blueprints.launchpad.net/ubuntu/+spec/client-1303-webkit-maintenance")

---

### Post by Copper Bezel on 2013-06-16
Does that tell us anything that your earlier link to the video didn't? I get that Canonical may be working on its own, entirely new browser based on Webkit, but that project can't possibly hit by 14.04, can it? In the shorter term, the question of whether Chromium or Firefox is used on the desktop seems like a separate one. I know that Chromium uses Webkit, but I don't think that using it as a default app would offer any meaningful stepping stone toward the in-house Webkit browser, and I'm guessing that the "Webkit maintenance strategy" is specifically about the new browser.

---

### Post by malspa on 2013-06-16
> **Copper Bezel said:**
> If Chrome isn't an option (and there are good reasons why that seems to be the case,) Firefox still makes the most sense to target those users, and still would whether or not Chromium was the better browser outright.

But how many people would actually choose or not choose a distro because of the default web browser? How many people get turned off by, say, a KDE distro that comes with only Konqueror by default? I'm thinking that the number's quite tiny. One of the first things anyone does after installing Linux, you go and install your favorite software, right? 

If you're a Windows user who uses Firefox instead of the default Internet Explorer, and you decide to try Linux, is it really going to bother you to install Firefox to use instead of the default Chromium (if that was the case)?

---

### Post by Copper Bezel on 2013-06-16
No, I don't think it would, and I don't think that users would choose not to use a *distro* because of the default browser - though I suppose that there are smaller complaints I've heard as reasons I've heard for switching from Ubuntu to Mint, say - but Ubuntu is marketed as a first-time-user's Linux, and I really do think that there would be a tiny, tiny effect on new Linux users' experience seeing at least one familiar icon on the Launcher, even if it's an app that they don't personally use on their own machines. I'm not so worried about things that might cause a user to consciously decide that the system wasn't for them so much as things that have a subconscious effect of welcoming or distancing.

And maybe I am looking at it too much from the POV of a picky Linux user - seeing Iceweasel as a default browser *would *be a sign to me that a distro probably isn't intended for my purposes.

---

### Post by malspa on 2013-06-16
> **Copper Bezel said:**
> And maybe I am looking at it too much from the POV of a picky Linux user - seeing Iceweasel as a default browser *would *be a sign to me that a distro probably isn't intended for my purposes.

Interesting, because Iceweasel in Debian is another one that came to mind here. When I install Debian, I *might* use Iceweasel *once*, but then I kinda forget that it's there.

With most distros, I tend to have more than one web browser installed anyway, usually with more than one on the panel or whatever. I'm (obviously, perhaps) biased towards Chromium, and that's what I prefer to use, but I'll use something else if the situation calls for it.

---

### Post by Copper Bezel on 2013-06-16
Sure. I'm not arguing that - I never bother to uninstall Firefox, and I do use it on occasion. Chrome still has a bug on downloading files from Google Drive, and Firefox's user agent string switcher is still simpler than Chrome's, so if I'm doing anything to do with those, I pull up Firefox. And I use Epiphany / Web when I want to play with Epiphany / Web. = ) I was looking at those first impressions rather than daily use.

---

### Post by malspa on 2013-06-23
One nice thing about the conversations on this subject, got me to finally go back and spend some time using Firefox after some years of not using it. I can't say that I actually like it better than Chromium, but I feel good enough about it that I think I might use it a lot more often than I have over the last few years. Always good to have options!

If Ubuntu does go with Chromium, should be fun to see how riled up people get about it.

---

### Post by vasa1 on 2013-06-23
> **malspa said:**
> ... Always good to have options! ....
I wonder if it's possible to have another thread with actual examples of what one browser can do that the other can't (excluding things like being faster, using less RAM, etc).

For example: With the pdf.js PDF Viewer in Firefox, it's possible to customize the appearance of the PDF page. So if one doesn't like the common white background (of the actual pdf page), it's possible to tweak the white to something milder like #aaa. This can't be done in Chrome's PDF Viewer. And so I now have Firefox as my default PDF Viewer rather than Chrome or Evince. Evince can only totally invert colors so one gets white text on a black background.

---

### Post by monkeybrain2012 on 2013-06-23
> **vasa1 said:**
> 

For example: With the pdf.js PDF Viewer in Firefox, it's possible to customize the appearance of the PDF page. So if one doesn't like the common white background (of the actual pdf page), it's possible to tweak the white to something milder like #aaa. This can't be done in Chrome's PDF Viewer. And so I now have Firefox as my default PDF Viewer rather than Chrome or Evince. Evince can only totally invert colors so one gets white text on a black background.

But this is not about Chrome. Chromium doesn't even have a PDF viewer. :)

---

### Post by vasa1 on 2013-06-23
> **monkeybrain2012 said:**
> But this is not about Chrome. Chromium doesn't even have a PDF viewer. :)
Very true. In my defense I did suggest "another thread" ;)

---

### Post by craig10x on 2013-06-24
I've always viewed Chromium as a "stripped down Chrome" (which it is actually)...I'm not an open source purist...I'm a features purist :D

Chrome adds "smart search" (my name not theirs...lol) in the url search, very nice pdf reader in browser (with option to download file of course)  up-to-date adobe flash (pepper) and ppa added to your software sources for the latest Chrome version as soon as it arrives, through the software updater...

I'll take the one that comes with all the features out the door, thank you very much ;)

---

### Post by malspa on 2013-06-24
> **craig10x said:**
> I'm not an open source purist

I don't think I am, either, but... if Chromium in Ubuntu was kept more up-to-date, I'd use it instead of Chrome, anyway. Even without the .pdf viewer. :)

---

### Post by monkeybrain2012 on 2013-06-24
> **craig10x said:**
> I've always viewed Chromium as a "stripped down Chrome" (which it is actually)...I'm not an open source purist...I'm a features purist :D

Chrome adds "smart search" (my name not theirs...lol) in the url search, very nice pdf reader in browser (with option to download file of course)  up-to-date adobe flash (pepper) and ppa added to your software sources for the latest Chrome version as soon as it arrives, through the software updater...

I'll take the one that comes with all the features out the door, thank you very much ;)

You can be both an open source purist and a feature purist by using Firefox. :)

Seriously Ubuntu is supposed to showcase free software, at least Mark Shuttleworth says so. It would be against Ubuntu's professed philosophy to distribute proprietary software as default while there is a better FOSS solution,--the current default.

Chromium is neither here nor there. It has few features and it doesn't have  Firefox's open source credentials.

---

### Post by malspa on 2013-06-24
Good points, monkeybrain. Well, I like Chromium better, so I hope it gets forced on *everyone*! :)

Seriously, I'll be glad when the decision is made, one way or the other.

---

### Post by King Dude on 2013-06-24
Honestly, I believe Chromium would be fantastic as a default browser.

---

### Post by craig10x on 2013-06-24
> **malspa said:**
> I don't think I am, either, but... if Chromium in Ubuntu was kept more up-to-date, I'd use it instead of Chrome, anyway. Even without the .pdf viewer. :)

It would help if ubuntu does decide to make it the default, if they would set up an optional package in the ubuntu software center, that would add on the pdf viewer and the pepperflash plug in without having to go through all the current extra hassles to add them in and in addition, as you said, they kept it more up to date, hopefully on par with Chrome itself....then i'd think i would probably use it instead of Chrome because then i'd have all my features back...

---

### Post by vasa1 on 2013-06-24
> **craig10x said:**
> It would help if ubuntu does decide to make it the default, if they would set up an optional package in the ubuntu software center, that would add on the pdf viewer and the pepperflash plug in without having to go through all the current extra hassles to add them in and in addition, as you said, they kept it more up to date, hopefully on par with Chrome itself....then i'd think i would probably use it instead of Chrome because then i'd have all my features back...
Even if Chromium is available with Pepper Flash and PDF Viewer (as optional installs) I would still stay with Chrome because it is my belief/understanding that Chromium is a "precursor" to Chrome and not a final product.

---

### Post by craig10x on 2013-06-24
@vasa1:  That's a very good point, yes, i have heard that that aside from adding in those features, they do make other tweaks and refinements on the finished (Chrome) product...

---

### Post by BrokenKingpin on 2013-06-24
I have been using Chromium for years, and find it to be a better user experience than Firefox. That being said, I don't really care what they have installed by default.

---

### Post by vasa1 on 2013-06-24
> **vasa1 said:**
> [Chromium as default browser]("https://blueprints.launchpad.net/ubuntu/+spec/foundations-1305-chromium-default-browser")
So why is Chromium (by Canonical/Ubuntu/Community) still at version 25? I think Canonical's Firefox team is more "on time" in terms of providing a current browser to its users.

Jeremy Bicha has weighed in with a "timeline" here: [https://lists.ubuntu.com/archives/ubuntu-desktop/2013-June/004250.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2013-June/004250.html)
> ...  but it seems clear
to me that Chromium **still does not have a track record** yet of being
maintained well enough to replace Firefox as the default desktop
browser yet (except perhaps on arm).   

---

### Post by malspa on 2013-06-25
> ... but it seems clear
to me that Chromium still does not have a track record yet of being
maintained well enough to replace Firefox as the default desktop
browser yet (except perhaps on arm).

Seems to me that it's Ubuntu that doesn't have the good track record (as far as keeping Chromium up-to-date). I have much more recent Chromium versions running in Bridge Linux, Sabayon, openSUSE... even in Debian Stable!

---

### Post by monkeybrain2012 on 2013-06-25
This is kind of only partially related. I am always wondering about the claim that Chrome has overtaken Firefox in user adoption. Today I have the answer, at least part of it. I haven't touched Windows for a few years except for a copy of XP in Vbox to run one program, but today  I was setting up WIn7 for someone. Went through the usual things of installing ccleaner and anti-virus, turned out almost all of these come with Chrome with a box prechecked. So after finishing all these I was surprised to find Chrome there as I had only downloaded and installed FF with IE.

---

### Post by uRock on 2013-06-25
> **monkeybrain2012 said:**
> This is kind of only partially related. I am always wondering about the claim that Chrome has overtaken Firefox is user adoption. Today I have the answer, at least part of it. I haven't touched Windows for a few years except for a copy of XP in Vbox to run one program, but today  I was setting up WIn7 for someone. Went through the usual things of installing ccleaner and anti-virus, turned out almost all of these come with Chrome with a box prechecked. So after finishing all these I was surprised to find Chrome there as I had only downloaded and installed FF with IE.
Of course the next thought it, "What else did those third party apps install?" Maybe a good topic for another thread. :D

---

### Post by craig10x on 2013-06-26
@monkeybrain 2012:  yes...it is VERY common today....quite a few manufacturers INCLUDE Google Chrome pre-installed along with Internet Explorer...I have noticed that when i go to stores and look at the desktops and laptops...I can tell you that HP and Toshiba and Sony do (probably others as well) and my Toshiba 17" laptop which i bought about 6 months ago, came with Windows 7, Internet Explorer and Google Chrome installed...None have Firefox pre-installed...The reason why they have added it is because Chrome has become so immensely popular, even beating out IE these days...

---

### Post by CharlesA on 2013-06-26
Don't you mean the OEMs put Chrome on their factory image because they get kickbacks?

*hides*

---

### Post by craig10x on 2013-06-26
@CharlesA: perhaps they do...but i do suspect it's also due to Chrome's tremendous popularity now...When Chrome was younger, and not as popular as it has become, i never saw ANY computers coming with it already installed and now most do...

---

### Post by aysiu on 2013-06-26
> **CharlesA said:**
> Don't you mean the OEMs put Chrome on their factory image because they get kickbacks?

*hides* I don't think you need to hide. Isn't it quite obvious it's because of kickbacks? I also don't see it as some big conspiracy either. It's a simple business transaction. "We pay you X money, and you preinstal' our software on your computers."

---

### Post by CharlesA on 2013-06-26
> **craig10x said:**
> @CharlesA: perhaps they do...but i do suspect it's also due to Chrome's tremendous popularity now...When Chrome was younger, and not as popular as it has become, i never saw ANY computers coming with it already installed and now most do...

I dunno if it is strictly because of popularity or if it is to get their name/product to more people.

> **aysiu said:**
> I don't think you need to hide. Isn't it quite obvious it's because of kickbacks? I also don't see it as some big conspiracy either. It's a simple business transaction. "We pay you X money, and you preinstalled our software on your computers."

Indeed. It is a bit about marketing too, getting your product visible to more people.

---

### Post by ushpiy on 2013-06-26
I'd be happy with Chromium as the default browser. I hardly use FF nowadays.

---

### Post by King Dude on 2013-06-27
I can't remember, is Firefox open-source? If not, then that's all the more reason to opt for Chromium. Or maybe Canonical could pull a Google and use Chromium as a base for Ubuntu's own browser, say Ubuntu Chrome, so that more Ubuntu-exclusive additions can be implemented than if it were standard Chromium.

Just a thought.

---

### Post by aysiu on 2013-06-27
> **King Dude said:**
> I can't remember, is Firefox open-source? Firefox is open source, definitely.

If it weren't, Ubuntu would never have included Firefox as the default browser in the first place.

---

### Post by I2k4 on 2013-06-27
Hate to disappoint users, but Ubuntu is _not all about performance or browser features_.  Ubuntu has ambitions, especially in the mobile space, and is threading its way among browsers produced by real or potential competitors. Chromium project doesn't skim user data for Google the way full-featured Chrome does, and Ubuntu wants to do, and FireFox is now floating itself as a mobile platform competing with Ubuntu.

---

### Post by Tar_Ni on 2014-05-30
I am sorry to dig up that thread but so finally, what's the long-term plan?

Will Canonical go on with Firefox in it's next releases or will it go with Chromium?

---

### Post by cariboo on 2014-05-30
> **Tar_Ni said:**
> I am sorry to dig up that thread but so finally, what's the long-term plan?

Will Canonical go on with Firefox in it's next releases or will it go with Chromium?

[VUDS]("http://uds.ubuntu.com/") is from June 10 to June 12, you can check it out yourself, and see what the plans for the coming version are.

---

