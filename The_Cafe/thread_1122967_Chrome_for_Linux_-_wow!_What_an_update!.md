---
title: "Chrome for Linux - wow! What an update!"
date: 2009-04-11
forum: The Cafe
---

### Post by joey-elijah on 2009-04-11
Forgive me if it's already been discussed, but i hadn't updated my packages for a few days, and in the mean time a pretty major update to Chromium seems to have been pushed out! 

Chromium now has working CLICKABLE tabs, new tab button, bookmarks bar, speed dial, ctrl+f dialogue, better font rendering, icognito browsing mode and i find it's by far the most stable build yet.

It really makes me excited to see the amount of progress made in just a few short weeks. That expected June release date seems totally feasible. 

If anyone's interested i've put some screencaps and a quick rundown on my blog.

[http://d0od.blogspot.com/2009/04/chrome-gets-major-linux-update-features.html](http://d0od.blogspot.com/2009/04/chrome-gets-major-linux-update-features.html)

---

### Post by SomeGuyDude on 2009-04-11
Is this still the one that's basically running through WINE, or is it finally a native app?

---

### Post by binbash on 2009-04-11
From your blog : 

The current testing builds of Google&#8217;s Chrome browser hit a very welcome update today. Chromium now sports 

--

Google Chrome and chromium are 2 different things.I guess your blog post is about chromium not Google Chrome!

---

### Post by Giant Speck on 2009-04-11
> **binbash said:**
> Google Chrome and chromium are 2 different things.I guess your blog post is about chromium not Google Chrome!

Yeah, people tend to mix up the terms Chromium and Google Chrome.  Google Chrome is a browser for Windows that is based off the Chromium project.  The people working on the browser for Linux are not Google, but the Chromium team.

---

### Post by SomeGuyDude on 2009-04-11
So... this is or is not a native Chromium browser.

---

### Post by Giant Speck on 2009-04-11
> **SomeGuyDude said:**
> So... this is or is not a native Chromium browser.

It's native as far as I can tell.

---

### Post by joey-elijah on 2009-04-11
Yes it's a native Linux version. It will, eventually, be fully GTk'd. (according to Google) 

Whilst i do know the different between the Chromium project and Google Chrome, to most people Chromium IS Google Chrome for all intents and purposes. After all Chromium was created by Google.

I was only trying to let people know that Chromium has had a significant update. 

For more on Chromium/Google Chrome 

[http://code.google.com/chromium/](http://code.google.com/chromium/)

---

### Post by speedwell68 on 2009-04-11
> **joey-elijah said:**
> Yes it's a native Linux version. It will, eventually, be fully GTk'd. (according to Google) 

Whilst i do know the different between the Chromium project and Google Chrome, to most people Chromium IS Google Chrome for all intents and purposes. After all Chromium was created by Google.

I was only trying to let people know that Chromium has had a significant update. 

For more on Chromium/Google Chrome 

[http://code.google.com/chromium/](http://code.google.com/chromium/)

I thought it was the other way around, Chromium was the project behind Google Chrome.

---

### Post by joey-elijah on 2009-04-11
> **speedwell68 said:**
> I thought it was the other way around, Chromium was the project behind Google Chrome.

it's a bit chicken and egg... 

Google created Chromium which in turn is the project behind Chrome. Chromium is, of course, now Open-Source and free to be forked by anyone who wishes too. 

From what i understand however the main chromium project itself is merely the 'development' of what will always become 'Google Chrome'. A forked Chromium browser would be based off Chromium which itself is merely the vanilla Google Chrome.

---

### Post by Polygon on 2009-04-12
so its *almost* usable now?

---

### Post by vishzilla on 2009-04-12
Can't wait for it.. Got to try the latest build, previous build didn't work for me. Web pages never loaded

---

### Post by BigSilly on 2009-04-12
I always thought Chromium was [a really cool Linux 2D shooter.]("http://www.happypenguin.org/show?Chromium%20B.S.U.&start=100") :confused:

---

### Post by joey-elijah on 2009-04-12
> **Polygon said:**
> so its *almost* usable now?

for a pre-alpha, hell yes! I wouldn't trust it as my sole browser - but it's perfectly usable. More stable than midori anyhow! :lolflag:

---

### Post by jrusso2 on 2009-04-12
> **joey-elijah said:**
> for a pre-alpha, hell yes! I wouldn't trust it as my sole browser - but it's perfectly usable. More stable than midori anyhow! :lolflag:

I don't even see a way to install it on Linux.  I went to the page you said and all the source is for win32.  How did you install it on Linux?

---

### Post by Devz0r on 2009-04-12
> **jrusso2 said:**
> I don't even see a way to install it on Linux.  I went to the page you said and all the source is for win32.  How did you install it on Linux?
Add this to software sources -> third party software, or to sources.list
[http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) intrepid main

Replace intrepid with jaunty or whatever if you are using a different version of ubuntu.
Then install chromium-browser.

---

### Post by khelben1979 on 2009-04-12
I assume it doesn't work on linux ppc architecture. Am I right?

---

### Post by Methuselah on 2009-04-12
Chrome...hmm...I'll pass.

---

### Post by Vadi on 2009-04-12
I'm on the PPA too. Some very nice improvements there with tabs.

---

### Post by Mr. Picklesworth on 2009-04-12
It already does use a bit of GTK, actually. For example, if you right click on the address bar you'll see a very familiar GTK text entry context menu, and the status bar thing is a proper tooltip.

It would be nice if they used their super powers to make the widgets on web pages be closer to GTK, but so far no browser has done that with webkit or gecko. (One issue being, I guess, that they need lots of flexibility for theming and the like so getting them more GTKish would require some tricky lower level stuff and a lot of maintenance).

---

### Post by ghindo on 2009-04-12
It's great to see that they're making steady improvements on Chromium for Linux.  Hopefully one day it will be stable :(> **joey-elijah said:**
> for a pre-alpha, hell yes! I wouldn't trust it as my sole browser - but it's perfectly usable. More stable than midori anyhow! :lolflag:That's really a bit of a stretch.  Have you tried the Midori PPA?  It's really quite stable.

---

### Post by Vadi on 2009-04-12
Nevermind that all that work is wasted when buttons on a webpage are styled with CSS.

I run both midori and chromium from ppas (frequently, I get updates for both) - and, well the differences in manpower are visible.

(I'm also not a fan of some of the ui decisions taken lately in midori like bottom-right checkboxes)

---

### Post by pt123 on 2009-04-12
Yeah the last update was amazing. 
They need to get the font hinting/smoothing to work next.

Hopefully it is a hint to Gnome to stop attempting to compete with the main players in the respective browser technologies and concentrate on their DE.

---

### Post by zekopeko on 2009-04-12
> **pt123 said:**
> Yeah the last update was amazing. 
They need to get the font hinting/smoothing to work next.

Hopefully it is a hint to Gnome to stop attempting to compete with the main players in the respective browser technologies and concentrate on their DE.

well webkit-gtk is going to be a big part of the Gnome desktop. and Gnome has it's offical browser just like KDE. you can't beat native integration.

---

### Post by Vadi on 2009-04-12
I seriously doubt google chrome is a contender for a native linux thing, and it doesn't look like it's even on the roadmap: [http://blogs.gnome.org/otte/2009/03/03/browsing-in-gnome/](http://blogs.gnome.org/otte/2009/03/03/browsing-in-gnome/)

---

### Post by Mehall on 2009-04-12
> **Vadi said:**
> I seriously doubt google chrome is a contender for a native linux thing, and it doesn't look like it's even on the roadmap: [http://blogs.gnome.org/otte/2009/03/03/browsing-in-gnome/](http://blogs.gnome.org/otte/2009/03/03/browsing-in-gnome/)

You're using... the GNOME blog to prove a GOOGLE product won't be made LINUX native?

that makes PERFECT sense /sarcasm

---

### Post by ghindo on 2009-04-12
> **Mehall said:**
> You're using... the GNOME blog to prove a GOOGLE product won't be made LINUX native?

that makes PERFECT sense /sarcasmI think you misunderstand his post.

---

### Post by Mehall on 2009-04-12
> **ghindo said:**
> I think you misunderstand his post.

probably, I skimmed.

---

### Post by bruce89 on 2009-04-12
Apart from WebKit, what is the point in Chrome(ium)?

---

### Post by ghindo on 2009-04-12
> **bruce89 said:**
> Apart from WebKit, what is the point in Chrome(ium)?[LIST]
[*]Fast Javascript.
[*]Arguably the best security among browsers.
[*]Separate processes per tab.
[/LIST]

---

### Post by monstrosity on 2009-04-13
If chromium had flash support, I'd be using it as my primary browser right now, and just switch back to firefox when it crashes.

It performs tasks ridiculously quickly for me. It's wonderful for non-critical browsing as is.

If only it worked with youtube...

---

### Post by gnomeuser on 2009-04-13
I really like Chrome, I tried it for a month when I was in Brazil last December and I can't wait for it to reach maturity on Linux. 

The only thing stopping me from using the pre-alpha right now is that there isn't any 64 bit support. This makes me a tad worried about the portability of the code as of yet, an important factor since I plan to get myself one of these new ARM netbooks.

---

### Post by TenPlus1 on 2009-04-13
Am sticking with Opera until a final release is available for linux :)

---

### Post by gnomeuser on 2009-04-13
> **ghindo said:**
> [LIST]
[*]Fast Javascript.
[*]Arguably the best security among browsers.
[*]Separate processes per tab.
[/LIST]

The security features in Chrome are according to several experts a really important step in the right direction. Whole new kinds of attacks will be needed since you would need to exploit the browse but also the sandbox it puts pages in. Currently there just aren't any such attacks available.

As for it being the best, it was the only browser to survive pwn2own and till Microsoft' Gazelle project is put into production it is the best design users can get their hands on. Gazelle though adds some nice additional containment making it even harder to exploit.

It's not just a security issue though, by separating tabs as processes (or as Gazelle does it even further down than tabs). You gain a whole lot of stability, as a user the days of one tab taking down the entire browser and losing your work are gone in the Chrome world.

Those are just two reasons I believe Chrome, or the Chrome approach is important. It seemlessly adds security and stability for users. Having really impressive JavaScript performance is important as well but to lure people onto the web platform for real we need to address those two areas with utmost care.

---

### Post by Vadi on 2009-04-13
Main thing for me is the javascript performance. Firefox performs like crap on Linux, it's been shown many times. Mozilla can blame anything they want, but chromium is far ahead of them in *all* benchmarks I tried - so it's not some fault of the linux stack as they like to place the blame off.

---

### Post by vishzilla on 2009-04-13
Wow... the latest chromium is amazing. It crashed few times in Gmail (the irony) but on the whole its great for an alpha software

---

### Post by forrestcupp on 2009-04-13
It's exciting to have one more option for Linux.  But for a while now, I've been using the fully functioning latest beta version of Chrome in Windows, and I'm probably going to switch back to Firefox.

Firefox is clunkier and slower, but there's too much about Chrome that I don't like, even in the stable version.

---

### Post by Tristam Green on 2009-04-13
I'm fairly excited about the rapid development going on with this (for Linux).  For a pre-alpha browser, it's pretty polished and works quite well.

---

### Post by Giant Speck on 2009-04-14
Whoo!  I was able to use Google Maps yesterday!  I wasn't able to do that last week.

---

### Post by wersdaluv on 2009-04-14
Oh. Yes, it has been upgraded. It looks gtk now. I hope to see the metacity fixed and the detachable tabs feature.

---

### Post by ghindo on 2009-04-14
> **vishzilla said:**
> Wow... the latest chromium is amazing. It crashed few times in Gmail (the irony) but on the whole its great for an alpha software*Pre*-alpha ;)

---

### Post by pt123 on 2009-04-14
> **zekopeko said:**
> well webkit-gtk is going to be a big part of the Gnome desktop. and Gnome has it's offical browser just like KDE. you can't beat native integration.
Yes you can when the native integration is developed at a very slow rate, when the Native DE is archaic. 
When it doesn't have the latest features.

This is why Firefox has killed IE on Windows (among power users) and Konqueror & Epiphany on Linux.

At the end of the day majority of users want a full featured browser, not something that is always playing catchup.

---

### Post by MikeTheC on 2009-04-14
> **BigSilly said:**
> I always thought Chromium was [a really cool Linux 2D shooter.]("http://www.happypenguin.org/show?Chromium%20B.S.U.&start=100") :confused:

[font=arial][size=5]**+**[/size][/font] [img]http://img4.imageshack.us/img4/9900/chromiumbsufighter.png[/img]

---

### Post by Giant Speck on 2009-04-14
> **MikeTheC said:**
> [FONT=arial][SIZE=5]**+**[/SIZE][/FONT] [IMG]http://img4.imageshack.us/img4/9900/chromiumbsufighter.png[/IMG]

Hmm... reminds me of the days I used to sit in pre-calculus class and play Platinum on my TI-89.

---

### Post by SomeGuyDude on 2009-04-15
> **pt123 said:**
> Yes you can when the native integration is developed at a very slow rate, when the Native DE is archaic. 
When it doesn't have the latest features.

This is why Firefox has killed IE on Windows (among power users) and Konqueror & Epiphany on Linux.

At the end of the day majority of users want a full featured browser, not something that is always playing catchup.

Not to mention "integration" makes my skin crawl. It's like code for "can't get rid of it". You can't uninstall IE in Windows because the system is built around it, Ubuntu (up to Hardy) had Firefox built into it to the point where it couldn't be uninstalled.

I like being able to pick and choose what I want. Don't make the browser "part" of the DE.

---

### Post by joey-elijah on 2009-04-15
> **SomeGuyDude said:**
> Not to mention "integration" makes my skin crawl. It's like code for "can't get rid of it". You can't uninstall IE in Windows because the system is built around it, Ubuntu (up to Hardy) had Firefox built into it to the point where it couldn't be uninstalled.

I like being able to pick and choose what I want. Don't make the browser "part" of the DE.

You can in Windows 7 :)

---

### Post by SomeGuyDude on 2009-04-15
> **joey-elijah said:**
> You can in Windows 7 :)

Windows 7 is, admittedly, the best jump forward since XP, possibly since 95. I tried out the beta and really like it.

---

### Post by Mr. Picklesworth on 2009-04-15
> **SomeGuyDude said:**
> Not to mention "integration" makes my skin crawl. It's like code for "can't get rid of it". You can't uninstall IE in Windows because the system is built around it, Ubuntu (up to Hardy) had Firefox built into it to the point where it couldn't be uninstalled.

I like being able to pick and choose what I want. Don't make the browser "part" of the DE.

Uhgh, no, that is not at all what integration is about. Quite the opposite. Integration is about following standards and shared [interoperability technologies]("http://www.freedesktop.org/"). This means that when the desktop environment *does* improve, every contained application improves with it.

Further, Firefox was not "integrated" into Ubuntu before Hardy as you believe. That was simply ugly packaging where ubuntu-desktop depended on firefox when it should have been a recommend.

Why do these discussions always come down to people picking on Epiphany with completely unfounded arguments, anyway?

---

### Post by Tristam Green on 2009-04-15
> **SomeGuyDude said:**
> Not to mention "integration" makes my skin crawl. It's like code for "can't get rid of it". You can't uninstall IE in Windows because the system is built around it, Ubuntu (up to Hardy) had Firefox built into it to the point where it couldn't be uninstalled.

I like being able to pick and choose what I want. Don't make the browser "part" of the DE.

I agree to an extent.  There should be a pre-packaged browser (and e-mail client) that comes default with a DE, but shouldn't be so intrinsic to that particular DE that it's nigh impossible to get rid of.

More the problem I have is binding default actions such as email notifications to Thunderbird, rather than Evolution (in GNOME), but that's for another thread altogether.

> **Mr. Picklesworth said:**
> 
Why do these discussions always come down to people picking on Epiphany with completely unfounded arguments, anyway?

I don't think he's picking on Epiphany exclusively, rather speaking more from his experiences with Windows and its abominable packaging with Internet Explorer(s).

---

### Post by joey-elijah on 2009-04-15
> **Mr. Picklesworth said:**
> 
Why do these discussions always come down to people picking on Epiphany with completely unfounded arguments, anyway?

I love Epiphany and use it as my default browser (yes!) in Ubuntu - mainly because for clicking on quick links, firefox takes an age to start up and get going.

Small noticeable update last few days - Chromium's bookmark bar now displays favicons regardless now. Before i found it would only display some (mainly those of 'mainstream' sites) and website fonts now seem to render more akin to Ubuntu settings. Before, they seemed to default to some really ugly, skinny font.

---

### Post by SomeGuyDude on 2009-04-15
> **Mr. Picklesworth said:**
> Further, Firefox was not "integrated" into Ubuntu before Hardy as you believe. That was simply ugly packaging where ubuntu-desktop depended on firefox when it should have been a recommend

...waitwaitwait. Firefox wasn't "integrated", ubuntu-desktop just "depended" on it. Did you just write that and think it made sense? ;) Okay, maybe you're arguing semantics but the point was that ubuntu-desktop shouldn't even have Firefox as a recommended package. Let me pick my browser.

Anyway, there are any number of other reasons pure integration is unnecessary. I've got one word: Konqueror. Great example of a team trying to make an app for everything and making it all go belly-up. Make my DE, let the browser guys make the browser.

---

### Post by Mr. Picklesworth on 2009-04-15
Well no, ubuntu-desktop is an empty metapackage at the root of your installation. If it didn't recommend or depend on packages, Ubuntu would basically not be usable. It is quite detached from what the packages actually do, though.

---

### Post by vishzilla on 2009-04-15
> **ghindo said:**
> *Pre*-alpha ;)
forgot one word :D

I wonder when will the first Google *official* build be released

---

### Post by Tristam Green on 2009-04-15
So, I wonder howcome I can't get the bookmarks manager to open up, and also howcome the bookmarks toolbar doesn't work.

Does everyone also get the terminal window that comes up when they are using Chromium's build?

---

### Post by joey-elijah on 2009-04-15
> **Tristam Green said:**
> So, I wonder howcome I can't get the bookmarks manager to open up, and also howcome the bookmarks toolbar doesn't work.

Does everyone also get the terminal window that comes up when they are using Chromium's build?

The bookmarks toolbar works - but you have to add a bookmark.

The bookmark manager (and most menu's) are still yet to be done so all bookmarks show on the bookmarks toolbar atm. Hit ctrl+B so bring it up.

> **vishzilla said:**
> forgot one word :D

I wonder when will the first Google *official* build be released

The first official Google build will be a beta - whenever Chromium reaches a beta state Google are happy enough to slap their logo on and push out to users! 

At least most Linux users won't be as dumb as a lot of Windows users.. 

Actual quote from the chrome help forum:

> "i wan't to remove Chrome and go back to original Google...will i lose my files and favorites"

There are loads more like it - read an article on it at

[http://googlesystem.blogspot.com/2009/04/google-chrome-and-original-google.html](http://googlesystem.blogspot.com/2009/04/google-chrome-and-original-google.html)

Bless!

---

### Post by wsonar on 2009-04-15
Chrome.....

I don't like how google read's your e-mail to target ads to you

---

### Post by Giant Speck on 2009-04-15
> **wsonar said:**
> Chrome.....

I don't like how google read's your e-mail to target ads to you

Umm... what are you talking about?

---

### Post by Seq on 2009-04-15
> **SomeGuyDude said:**
> ...waitwaitwait. Firefox wasn't "integrated", ubuntu-desktop just "depended" on it. Did you just write that and think it made sense? ;) Okay, maybe you're arguing semantics but the point was that ubuntu-desktop shouldn't even have Firefox as a recommended package. Let me pick my browser.

Integration means the system or desktop would not function without it. Everything would function fine if you removed firefox. But because of the misplaced dependency, removing firefox removed "ubuntu-desktop", which is needed for upgrades -- so you may have trouble down the road. This is fixed now. A recommend instead of depend means it installs firefox with ubuntu-desktop, but you can remove it with no ill effects.

There IS a significant difference. Webkit will probably become integrated, however ;)

> **SomeGuyDude said:**
> Anyway, there are any number of other reasons pure integration is unnecessary. I've got one word: Konqueror. Great example of a team trying to make an app for everything and making it all go belly-up. Make my DE, let the browser guys make the browser.

Uh, you know the DE guys (KDE and Konqueror) wrote KHTML, right? Which went on to become Webkit? Which is used in Chrome?

[http://en.wikipedia.org/wiki/KHTML](http://en.wikipedia.org/wiki/KHTML)

---

### Post by Erunno on 2009-04-15
> **Giant Speck said:**
> Umm... what are you talking about?

Google scans emails mechanically (no humans read your mail) and looks for specific keywords which in turn is used for personalized advertisment. Given the fact that most people send emails unencrypted the argument of confidentiality is moot.

---

### Post by Vadi on 2009-04-15
The terminal is always open for debugging purposes and to remind the user that it is a developers preview ;)

---

### Post by bruce89 on 2009-04-15
> **ghindo said:**
> [LIST]
[*]Fast Javascript.
[*]Arguably the best security among browsers.
[*]Separate processes per tab.
[/LIST]

The first 2 are due to WebKit.

> **wersdaluv said:**
> Oh. Yes, it has been upgraded. It looks gtk now. I hope to see the metacity fixed and the detachable tabs feature.

Metacity?

> **SomeGuyDude said:**
> ...waitwaitwait. Firefox wasn't "integrated", ubuntu-desktop just "depended" on it. Did you just write that and think it made sense? ;) Okay, maybe you're arguing semantics but the point was that ubuntu-desktop shouldn't even have Firefox as a recommended package. Let me pick my browser.

That's the whole point of recommends.

---

### Post by ghindo on 2009-04-15
> **bruce89 said:**
> The first 2 are due to WebKit.I thought that the fast JavaScript was a result of [V8]("http://en.wikipedia.org/wiki/V8_JavaScript_engine"), and the security wasn't specific to WebKit.

---

### Post by sports fan Matt on 2009-04-15
I cant seem to add [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main into software sources

---

### Post by Tibuda on 2009-04-15
> **sox fan Matt said:**
> I cant seem to add [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main into software sources
You forgot the deb

---

### Post by Giant Speck on 2009-04-15
> **Erunno said:**
> Google scans emails mechanically (no humans read your mail) and looks for specific keywords which in turn is used for personalized advertisment. Given the fact that most people send emails unencrypted the argument of confidentiality is moot.

Well, all online mail services scan messages.  And Google's privacy statement says that the information used to display the ads is only available to the sender and recipient and is never disclosed to a third party.  I doubt it's even stored.

---

### Post by Vadi on 2009-04-15
WebKit itself is also getting a new engine (Google just isnt using it, their made their own).

---

### Post by spier on 2009-04-15
Hmmm, seems really fast! Can't wait for plugins like flashblock, no script, adblock to start using it!

---

### Post by OutOfReach on 2009-04-15
Couldn't get it to work right in Arch (using 64 bit ATM) but I got it to work in 32 bit Ubuntu in VirtualBox. It was indeed very fast both at loading pages and rendering them correctly, also: There is no jittery scrolling! Woo! But of course there are bugs left, and I experienced crashing every once in a while. Hopefully the final release will be better.

---

### Post by joey-elijah on 2009-04-16
> **OutOfReach said:**
> It was indeed very fast both at loading pages and rendering them correctly, also: There is no jittery scrolling! Woo! But of course there are bugs left, and I experienced crashing every once in a while. Hopefully the final release will be better.

Let's just hope for a decent Beta first! ;)

Given the immense amount of progress so quickly - almost daily - i'm excited for a beta release partly because it'll probably be as stable as Chrome was initially - rock solid. Thus making a beta better than firefox on linux!

---

### Post by codyBane on 2009-04-16
>  Originally Posted by bruce89  View Post
Apart from WebKit, what is the point in Chrome(ium)?

    * Fast Javascript.
    * Arguably the best security among browsers.
    * Separate processes per tab.


I'll enjoy the separate processes.  It's other main advantages are it's simplistic and minimalist design resulting in it being more lightweight than it's competitors.

I like firefox but I have found it to be a bit slow and clunky (on win and linux) and a bit of a memory hog, unreasonably so.  I hope new firefox versions have better garbage cleanup.  Of course I.E. is even slower and clunkier than firefox in my experience.

If you're not using the alpha versions you can sign up here to be notified when a Linux version of Chrome is ready.

[http://www.google.com/chrome/intl/en/linux.html]("http://www.google.com/chrome/intl/en/linux.html")

I'm eagerly waiting for another good browser to be completed for Linux.  I'm not fond of using Epiphany as my secondary browser and for web development I usually have 2-3 different browsers open for testing.

---

### Post by bruce89 on 2009-04-16
> **codyBane said:**
> It's other main advantages are it's simplistic and minimalist design resulting in it being more lightweight than it's competitors.

[...]

I'm not fond of using Epiphany as my secondary browser [...]

These two things don't really go together...

---

### Post by Nagrom_17 on 2009-04-17
I have been building chromium nightly(it takes a few hours to build during which I cant use my computer) and am very satisfied. I used chrome as my main browser on windows xp and only switched to ubuntu a few weeks ago. after a few days of trying ubuntu I witnessed my first browesr crash since chrome has come out and felt a little pang when all 10 or so tabs i had open disappeared. Im glad this is coming along so well and am continuing to monitor its progress happily :D

---

### Post by izizzle on 2009-04-17
Upon some web surfing, I came upon [THIS]("http://chrometweaks.org/news/download-google-chrome-for-mac-and-linux/") bit of news. Being the Chrome fan that I am, I decided to post my bit of anxious excitement here on the forums. Perhaps someone is just as anxious for a stable release?

EDIT: New version [HERE]("https://launchpad.net/~chromium-daily/+archive/ppa")

---

### Post by Tibuda on 2009-04-17
That's the old wine version. You better try the native alpha:
[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

---

### Post by Giant Speck on 2009-04-17
Hmm... I like the font rendering on the Mac screenshot more than the rendering on the Linux screenshot.  I wish WINE had better font rendering capabilities.

---

### Post by izizzle on 2009-04-17
> **danielrmt said:**
> That's the old wine version. You better try the native alpha:
[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

:D Thanks for the updated link! Added to first post. :D

---

### Post by wersdaluv on 2009-04-17
That's not Google Chrome :| It's Chromium.

---

### Post by Wiebelhaus on 2009-04-17
> **danielrmt said:**
> That's the old wine version. You better try the native alpha:
[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

Thanks.

---

### Post by James_Lochhead on 2009-04-17
Yea Google Chrome is different from Chromium. Google Chrome is a browser for Windows. Chromium is an Open Source browser. The Chromium project was started by Google but not maintained by them (or so I believe).

---

### Post by Nagrom_17 on 2009-04-18
well basicaly chromium is google chrome until chromium is stable enough for a official release. then chromium keeps getting changes but google puts seperate changes into google chrome too. and for all development purposes when chromium gets good enough on an os then chrome will come to that os. so chromium just turns into chrome


edit:i think that a lot of the people doing heavy contributions to chromium are from google but there are a few who aren't I think

---

### Post by Tibuda on 2009-04-18
> [Chromium is the open-source project behind Google Chrome.]("http://code.google.com/intl/en/chromium/")

I understand that Chromium is like an "upstream Chrome", or Chrome is a "patched Chromium".

---

### Post by Vadi on 2009-04-18
It does have a funny font rendering atm. I hope they fix that.

---

### Post by days_of_ruin on 2009-04-18
Why didn't google just make chrome/chromium using gtk/qt in the first place?
Does everyone have to keep reinventing the wheel?

---

### Post by Vadi on 2009-04-18
Because those toolkits don't provide the maximum mac/windows integration, and google is aiming for highest quality on each platform.

---

### Post by joey-elijah on 2009-04-19
> **Vadi said:**
> Because those toolkits don't provide the maximum mac/windows integration, and google is aiming for highest quality on each platform.

Which i totally commend them for! Originally they debated just porting Chrome through WINE for Linux but the developers at google made a case for using GTK and so Google, wanting Chrome to be as awesome on each platform as possible, agreed! 

Of course, a QT version could easily be independently produced.

Lead Chrome interface designer, Ben Goodger, said: 

"Google [avoids] cross platform UI toolkits because while they may offer what superficially appears to be a quick path to native looking UI on a variety of target platforms, once you go a bit deeper it turns out to be a bit more problematic." 

Your applications end up "speaking with a foreign accent", he adds. 

In addition, Goodger claims that using something like Qt "limits what you can do to a lowest common denominator subset of what's supported by that framework on each platform."

---

### Post by =^,^= on 2009-04-19
Can you use things like flash with chromium yet?

---

### Post by Wiebelhaus on 2009-04-19
You know I tried for the last day or so and the deal breaker is....



No XMarks.


But for availability I think it's great!

---

### Post by =^,^= on 2009-04-19
> **sx66gns said:**
> You know I tried for the last day or so and the deal breaker is....



No XMarks.


But for availability I think it's great!

Xmarks?

---

### Post by Mehall on 2009-04-19
> **=^,^= said:**
> Xmarks?

Formerly FoxMarks.

Periodically updates your bookmarks with the xmarks server. If you have multiple computers, keeps all the bookmarks synced.

I <3 it

---

### Post by =^,^= on 2009-04-19
> **Mehall said:**
> Formerly FoxMarks.

Periodically updates your bookmarks with the xmarks server. If you have multiple computers, keeps all the bookmarks synced.

I <3 it

I see.

---

### Post by joey-elijah on 2009-04-19
> **sx66gns said:**
> You know I tried for the last day or so and the deal breaker is....



No XMarks.

To be fair, Xmarks still only support firefox atm - even on Windows. IE and Safari extensions are still in beta and given Chrome doesn't have extension capabilities even in it's Windows Dev releases (as of yet) it's a bit unfair to expect it in a pre-alpha browser!

---

### Post by PhoHammer on 2009-04-19
> **Polygon said:**
> so its *almost* usable now?

Haha, yes! It's just slow enough on my system to make me think each time I load a new page "Did
 it just freeze?" and then it shows the new page. I am looking forward to a stable version though!

---

### Post by mamamia88 on 2009-04-19
just out of curiousity where did you download it?

---

### Post by PhoHammer on 2009-04-19
> **joey-elijah said:**
> 

In addition, Goodger claims...

Off topic: Is that an alias for Google I haven't seen yet? Just wondering... If it was a typo that's
 really funny!:D

---

### Post by Giant Speck on 2009-04-19
> **PhoHammer said:**
> Off topic: Is that an alias for Google I haven't seen yet? Just wondering... If it was a typo that's
 really funny!:D

Nope.  He's a real person:

[img]http://upload.wikimedia.org/wikipedia/commons/thumb/2/2f/Bgoodger.jpg/225px-Bgoodger.jpg[/img]

---

### Post by Vadi on 2009-04-19
> **mamamia88 said:**
> just out of curiousity where did you download it?

[http://tombuntu.com/index.php/2009/03/16/pre-alpha-chromium-browser-now-available/](http://tombuntu.com/index.php/2009/03/16/pre-alpha-chromium-browser-now-available/)

---

### Post by joey-elijah on 2009-04-20
The latest Chromium update on Linux has a feature i don't have in either my dev Chrome or Chromium builds on Windows. 

It's a simple 'icon' next to the drop down 'smart bar' results that tell you whether it's a web result, history result or a search term.

[IMG]http://img407.imageshack.us/img407/9681/asdasdasdasdasdthumb1.png[/IMG]

A few other small updates this week - draggable bookmark bar bookmarks; continued improvement in rendering (getting faster!) and (finally!) some menus have been written! 

[http://d0od.blogspot.com/2009/04/small-chrome-updates-include.html](http://d0od.blogspot.com/2009/04/small-chrome-updates-include.html)

---

### Post by Giant Speck on 2009-04-20
> **joey-elijah said:**
> The latest Chromium update on Linux has a feature i don't have in either my dev Chrome or Chromium builds on Windows. 

It's a simple 'icon' next to the drop down 'smart bar' results that tell you whether it's a web result, history result or a search term.

[IMG]http://img407.imageshack.us/img407/9681/asdasdasdasdasdthumb1.png[/IMG]


I didn't notice that before! Cool!

---

### Post by ghindo on 2009-04-20
Very interesting update.  It's cool to watch these updates come in incrementally.  Looking forward to when this is stable :popcorn:

---

### Post by binbash on 2009-04-20
Can you stop calling this CHROME?This is NOT OFFICIAL GOOGLE CHROME

---

### Post by Giant Speck on 2009-04-20
> **binbash said:**
> Can you stop calling this CHROME?This is NOT OFFICIAL GOOGLE CHROME

Chill, dude.  You'll scare the children.

---

### Post by SushiR on 2009-04-20
> **binbash said:**
> Can you stop calling this CHROME?This is NOT OFFICIAL GOOGLE CHROME

Oh really! Calm down a bit...

---

### Post by Vadi on 2009-04-20
I think you shouldnt worry about the icon thingy - remember that you're using *the* latest version of chromium, while google chrome is obviously a bit later and more stabler code.

---

### Post by joey-elijah on 2009-04-20
> **binbash said:**
> Can you stop calling this CHROME?This is NOT OFFICIAL GOOGLE CHROME

No, but it's as good as. Chromium was created, made and is still largely developed by Google. Google Chrome is just a stable snapshot of Chromium with a different icon, the word 'google' on the tab bar and an installer hosted on the main Chrome site. 

For all intents and purposes it is Google Chrome as there will be no major differences between the Chromium project and Google Chrome. Anyone is free, of course, to take the Chromium source and fork it but it wouldn't be called 'Chromium'.

---

### Post by mister_k81 on 2009-04-20
> **izizzle said:**
> 
EDIT: New version [HERE]("https://launchpad.net/~chromium-daily/+archive/ppa")

I've been getting the dailies from there for over a week now, and not a single one has worked for me yet. I continue to get this error message at start-up:   

```
:~$ chromium-browser
[8407:8407:4387691415:ERROR:/build/buildd/chromium-browser-2.0.175.0~svn20090418r14008/build-tree/src/chrome/common/temp_scaffolding_stubs.cc(148)] Not implemented reached in static bool FirstRun::IsChromeFirstRun()
Illegal instruction

```

I don't expect any solutions to this, because it's still in pre-alpha and will probably get sorted out in time.... But, has anyone else received this error message, or something similar to it?

---

### Post by SomeGuyDude on 2009-04-20
Still won't work on my Arch64 installation (possibly because it needs all those lib32 packages). I just get a window with a bunch of squares instead of text.

---

### Post by mamamia88 on 2009-04-20
cool just installed it and it's plenty fast options doesn't work can't wait for full release maybe ill have a keeper browser

---

### Post by joey-elijah on 2009-04-21
> **mister_k81 said:**
> I've been getting the dailies from there for over a week now, and not a single one has worked for me yet. I continue to get this error message at start-up:   

```
:~$ chromium-browser
[8407:8407:4387691415:ERROR:/build/buildd/chromium-browser-2.0.175.0~svn20090418r14008/build-tree/src/chrome/common/temp_scaffolding_stubs.cc(148)] Not implemented reached in static bool FirstRun::IsChromeFirstRun()
Illegal instruction

```

I don't expect any solutions to this, because it's still in pre-alpha and will probably get sorted out in time.... But, has anyone else received this error message, or something similar to it?

Usual questions - what version of Ubuntu? 32 or 64? have you tried removing it then reinstalling?

---

### Post by joey-elijah on 2009-04-21
> **mamamia88 said:**
> cool just installed it and it's plenty fast options doesn't work can't wait for full release maybe ill have a keeper browser

I adore Chrome in Windows, and i'll love it even more on Linux. 

I'm shocked at how fast it is for a pre-alpha, but very happy. Once it get's a few of those menu's sorted, i'd probably find myself using it more than Firefox purely because it is just so fast to start up and load pages.

---

### Post by RaZoR1394 on 2009-05-08
Is there really no way to get flash on this one?

---

### Post by HappinessNow on 2009-05-08
Google Chrome in Windows is simply the best web browser (including better then Firefox or Opera), IMHO.

Let's hope Chromium reaches the same pinnacle in Linux.

---

### Post by mikewhatever on 2009-05-08
> **&#20170 said:**
> Google Chrome in Windows is simply the best web browser (including better then Firefox or Opera), IMHO.

Let's hope Chromium reaches the same pinnacle in Linux.

Really? I wonder why? Does it wash the dishes while you are gone?
I've tried Chrome on Windows a couple of times when it came out and didn't like it, here is why:

It installs into an obscure and hard to find location.
After removal, the installation folder is not deleted along with 45 MB of data in it.
It didn't run under non-admin accounts, very becoming of a Windows only app.
It didn't have the extensions like adblock and noscript.
It had a ridiculous EULA, probably counting on the fact that most Windows users never read EULAs.
It was disgustingly blue (this one is very subjective, but counts as a personal preference).

---

### Post by mister_k81 on 2009-05-08
> **joey-elijah said:**
> Usual questions - what version of Ubuntu? 32 or 64? have you tried removing it then reinstalling?

I'm running Ubuntu 9.04 32bit, and yes I have tried uninstalling and reinstalling it. Though I think I've found the issue, this current build doesn't seem to work with older AlthlonXP processors because it has SSE2 enabled. 

Here's a link issuing the problem: 

[http://code.google.com/p/chromium/issues/detail?id=9007#c35](http://code.google.com/p/chromium/issues/detail?id=9007#c35)

---

### Post by sports fan Matt on 2009-05-10
Im running 904 32 bit as well and when I added the repository to jaunty nothing worked..any ideas?

---

### Post by joey-elijah on 2009-05-10
> **mikewhatever said:**
> I've tried Chrome on Windows a couple of times when it came out and didn't like it, here is why:

It installs into an obscure and hard to find location.
After removal, the installation folder is not deleted along with 45 MB of data in it.
It didn't run under non-admin accounts, very becoming of a Windows only app.
It didn't have the extensions like adblock and noscript.
It had a ridiculous EULA, probably counting on the fact that most Windows users never read EULAs.
It was disgustingly blue (this one is very subjective, but counts as a personal preference).

1. I don't think it matters where it install so logn as you can use it right?

2. The same cold be levelled against hundreds of other applications - including Firefox in Linux.

3. I never had this issue.

4. If you don't agree with an EULA don't agree to it then! I find nothing overtly 'ridiculous' within Chromes EULA than i do with firefox, opera or other browsers.

5. Well neither does Internet Explorer, Midori, iCab and plenty of other browsers; so you don't like Chrome because it doesn't support Firefox extensions? Aside from the fact that an extension framework is currently being developed, Google never advertised Chrome as having extentions in the first palce, so your point is moot!

6. It's not 'disgutsingly blue' if you use it in Windows Vista or Windows 7 (or use Chromium pre-alpha in Linux!)

---

### Post by albinootje on 2009-05-10
> **mikewhatever said:**
> 
After removal, the installation folder is not deleted along with 45 MB of data in it.

ouch.. :(
> 
It didn't have the extensions like adblock and noscript.
Too bad :( but what do you expect from a data-mining and advertisement company like Google ? ;-)

---

### Post by Mr. Picklesworth on 2009-05-10
Ah, but the lack of ad blocking is irrelevent since it blocks annoying popups quite elegantly and it is still considerably faster than Firefox + adblock even on the most ad-laden sites.

You also get that warm fuzzy feeling that, by not blocking all ads like the plague, you are helping small web content providers earn some pocket change.

---

### Post by sports fan Matt on 2009-05-10
this is the error i get after adding the repo..E: Couldn't find package chromium-browser

---

### Post by albinootje on 2009-05-10
> **sox fan Matt said:**
> this is the error i get after adding the repo..E: Couldn't find package chromium-browser

Did you do "sudo apt-get update" ?
```

$ apt-cache search chromium
chromium - fast paced, arcade-style, scrolling space shooter
chromium-data - data pack for chromium
chromium-browser - Chromium browser
chromium-browser-dbg - chromium-browser debug symbols
chromium-testsuite - Chromium test suite
chromium-testsuite-dbg - chromium-testsuite debug symbols

```

> 
# testing chromium
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) hardy main
# deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) hardy main


---

### Post by sports fan Matt on 2009-05-10
within 5 minutes it crashed three times...

---

### Post by Mr. Picklesworth on 2009-05-10
> **sox fan Matt said:**
> within 5 minutes it crashed three times...

Read the first page it shows you again ;)
The one with the giant warning sign. (Then gaze in amazement that, even with that scary message, session restoring still works)

---

### Post by sports fan Matt on 2009-05-10
Yeah it does..:lolflag:...just wish it wouldnt crash so much

---

### Post by Hells_Dark on 2009-05-15
New update !

No bug on the tabs…
It's a really good browser yet :)

---

### Post by ghindo on 2009-05-15
Are there any plans for a 64-bit build?

---

### Post by mister_pink on 2009-05-15
I still can't test because of [this]("http://code.google.com/p/chromium/issues/detail?id=9007") issue, which relies on [this]("http://code.google.com/p/chromium/issues/detail?id=8475") bug being fixed. Tried compiling myself without the sse2 flag, and no luck.

---

### Post by joey-elijah on 2009-05-15
> **mister_pink said:**
> I still can't test because of [this]("http://code.google.com/p/chromium/issues/detail?id=9007") issue, which relies on [this]("http://code.google.com/p/chromium/issues/detail?id=8475") bug being fixed. Tried compiling myself without the sse2 flag, and no luck.

Have you tried the stand alone version? You can grab it from [http://build.chromium.org/buildbot/snapshots/chromium-rel-linux/](http://build.chromium.org/buildbot/snapshots/chromium-rel-linux/) (scroll to the very, very bottom to get the latest). It runs as an executable from the extracted folder  so no installation needed.

---

### Post by mister_pink on 2009-05-15
> **joey-elijah said:**
> Have you tried the stand alone version? You can grab it from [http://build.chromium.org/buildbot/snapshots/chromium-rel-linux/](http://build.chromium.org/buildbot/snapshots/chromium-rel-linux/) (scroll to the very, very bottom to get the latest). It runs as an executable from the extracted folder  so no installation needed.
I haven't, but as far as I understand it no current builds will work on older processors unless you compile yourself. They've turned on a flag as a workaround to one bug, and its the default in the build scripts. It means that any processors that don't support that instruction set won't be able to run it, until the original bug is fixed and they turn the flag off.

There was an issue with the same thing with google earth a while back, not sure what the status of that is now, but I remember not being able to upgrade to a newer version.

---

### Post by Vadi on 2009-05-15
Strange, the tabs were striped for me and now back to the white & blue.

---

### Post by PaulFXH on 2009-05-15
> **joey-elijah said:**
> Have you tried the stand alone version? You can grab it from [http://build.chromium.org/buildbot/snapshots/chromium-rel-linux/](http://build.chromium.org/buildbot/snapshots/chromium-rel-linux/) (scroll to the very, very bottom to get the latest). It runs as an executable from the extracted folder  so no installation needed.

You got the executable to run?
When I tried (using version 16158 of today) I get this:
> This browser is not ready yet!

This is a pre-alpha build of Chromium on Linux. It is woefully incomplete. No work has been done on performance yet, much of the UI is missing, plugins don't work, and many more bugs remain.
and that's as far as it goes. :icon_frown:
How did you get it to actually run?

---

### Post by Giant Speck on 2009-05-15
> **Vadi said:**
> Strange, the tabs were striped for me and now back to the white & blue.

That's the developers saying "yeah..... let's not mess with the tabs right now."

---

### Post by Vadi on 2009-05-15
Ahh. Yeah, they are doing some pretty unusual (but nice stuff with them).

---

### Post by Mr. Picklesworth on 2009-05-15
They should really just go for a GTKNotebook :/
Their own tab bar isn't doing anything particularly unique here, except for the moving Plus sign (which I THINK is doable with the GTK widget).

---

### Post by Vadi on 2009-05-15
The nice animations are unique... revolutionary for gtk in fact. They prolly had to do some very weird gdk hackery.

---

### Post by Tipped OuT on 2009-05-15
Hey, I don't if they have done this yet, or plan this but you know how there is a blue area? They should have that change color to whatever your GTK theme window color is, to match. :D

---

### Post by joey-elijah on 2009-05-16
> **Tipped OuT said:**
> Hey, I don't if they have done this yet, or plan this but you know how there is a blue area? They should have that change color to whatever your GTK theme window color is, to match. :D

That is the plan, and various implementations of it do pop up in builds now and again.

---

### Post by ibuclaw on 2009-05-16
I've tried the native version. Didn't really like it in the end.

Yes, it appears to be a noticeably fast browser, but my thumbs are down because for the first time in my 4 years old using Linux I got a bombarding stream of popup advertisments ... :o

---

### Post by Metar on 2009-05-17
It feels... Slick. The working portions feel spot-on like the Windows version.

Frankly, as soon as they enable the Options screen, fix the copy-paste bits and add Flash (which are probably the three hardest tasks), I'll start using it as my only browser. For now, I still have to use Firefox if I intend to use Flash, or visit a specific site that requires a security certificate exception - but other than that. As for stability, it's more stable than Epiphany and Galeon.. And tab recovery works great.

Priority-wise, I reckon implementing Flash is the only thing that keeps it from becoming my full-time browser.


Also, whatever build arrived on my PC today finally removed the console-window running in the background. :D

---

### Post by Sashin on 2009-05-17
It's font rendering needs to be fixed as well.

---

### Post by joey-elijah on 2009-05-17
I think a lot of you are forgetting that it's not even an alpha build yet, so all this talk of "i tried it but don't like it" are a wee bit premature! The extension framework has just been implemented in the Windows dev version of Chrome, so i'd expect to see it start to work it's way in to Chromium after the first alpha. 

> **Sashin said:**
> It's font rendering needs to be fixed as well.

Yes it does. Strangely it did improve a while back in several builds but then reverted back to that horrible "windows xp" type look.

---

### Post by Sashin on 2009-05-17
I hope it looks like this when complete.

[IMG]http://i41.tinypic.com/32zrwhf.png[/IMG]

---

### Post by joey-elijah on 2009-05-18
> **Sashin said:**
> I hope it looks like this when complete.

[IMG]http://i41.tinypic.com/32zrwhf.png[/IMG]

That's almost spot on to what it will look like, though it will have a deeper shadow on non-active tabs and no separator between tabs and the navigation bar, like so (i'm using the Dust theme): -

[IMG]http://3.bp.blogspot.com/_FJH0hYZmVtc/SgxV6SLPVOI/AAAAAAAAB_E/U1SSsowmBVk/s400/screenshot_003.png[/IMG]

---

### Post by Sashin on 2009-05-18
Ah cool, I'm using a modification of the dust theme. That's why it's sorta blue grey. I did it to match my green background.

---

### Post by Metar on 2009-05-18
I wonder, though - wouldn't it look a bit better if the transition between the whiter bit and the theme-coloured section were a bit smoother? A gradient of sorts? (I realize, that might be too hard to implement).

---

### Post by sdowney717 on 2009-05-18
ADD Block 
all browsers need to be able to block adds.

I tried out chromium and was bombarded with adds. It is not what I am used to seeing.

---

### Post by sdowney717 on 2009-05-18
[http://www.x-menorigins.com/](http://www.x-menorigins.com/)

how about flash? Does not seem to work in this chromium

---

### Post by Tibuda on 2009-05-18
> **sdowney717 said:**
> [http://www.x-menorigins.com/](http://www.x-menorigins.com/)

how about flash? Does not seem to work in this chromium

Do you know this is not even alpha?

---

### Post by zika on 2009-05-18
> **izizzle said:**
> :D Thanks for the updated link! Added to first post. :D
I've added these ppa lines to sources.list but I do not see chromium-browser in synaptic, only some chromium arcade game ... ?
yes, I did update ... :)

---

### Post by Bölvaður on 2009-05-18
> **zika said:**
> I've added these ppa lines to sources.list but I do not see chromium-browser in synaptic, only some chromium arcade game ... ?
yes, I did update ... :)

yeah I had the same
you have to select the correct repo on the left

---

### Post by thomasboleyn on 2009-05-18
> **ghindo said:**
> Are there any plans for a 64-bit build?

I'm running the latest chromium build on Ubuntu 64-bit :o

---

### Post by zika on 2009-05-18
> **Bölvaður said:**
> yeah I had the same
you have to select the correct repo on the left
I've tried that already without any success ... :)

---

### Post by nolliecrooked on 2009-05-18
run this in terminal;

sudo apt-get install chromium-browser

---

### Post by zika on 2009-05-18
> **nolliecrooked said:**
> run this in terminal;
sudo apt-get install chromium-browser
that (almost surely) might work but I do not like to install anything I can not uninstall through synaptic afterward ... :)
as I said, it works, but:```
The following extra packages will be installed:
  ia32-libs ia32-libs-chromium-browser lib32asound2 lib32gcc1 lib32ncurses5
  lib32stdc++6 lib32z1 libc6-i386
The following NEW packages will be installed:
  chromium-browser ia32-libs ia32-libs-chromium-browser lib32asound2 lib32gcc1
  lib32ncurses5 lib32stdc++6 lib32z1 libc6-i386
```
too many 32-bit dependenicies on my almost all 64 bit machine ... I'll wait ... :)

---

### Post by Vadi on 2009-05-18
They won't be going 64bit anytime soon - V8 is 32bit only afaik (they do a lot of low-level optimizations to make it that fast to begin with, so 64bit isn't as easy as compiling on a 64bit machine).

---

### Post by Mazza558 on 2009-05-18
I'm using Chrome on Ubuntu 9.04 now. 

Is it me or is this faster than the Windows version?

---

### Post by joey-elijah on 2009-05-18
> **Mazza558 said:**
> I'm using Chrome on Ubuntu 9.04 now. 

Is it me or is this faster than the Windows version?

it's been a few weeks since i last booted into windows, but that's the same perception i get!

---

### Post by Giant Speck on 2009-05-18
> **Mazza558 said:**
> I'm using Chrome on Ubuntu 9.04 now. 

Is it me or is this faster than the Windows version?

It could be because it has a lot fewer features than the Windows version, especially considering it's only a pre-alpha.

---

### Post by binbash on 2009-05-18
> **Mazza558 said:**
> I'm using Chrome on Ubuntu 9.04 now. 

Is it me or is this faster than the Windows version?

Because there are not any features.Even an options window

---

### Post by Zorael on 2009-05-18
Give Qt Chromium. With extensions support. :´<

---

### Post by joey-elijah on 2009-05-18
> **binbash said:**
> Because there are not any features.Even an options window

There is an options window now, actually... only there's nothing in it! :P 

I think you have to judge page rendering on Chromes merits as well. I'm sure an options menu and slightly more elegant bookmarks bar aren't going to interfere with the V8 Javascript engine *too* much.

---

### Post by joey-elijah on 2009-05-18
> **Zorael said:**
> Give Qt Chromium. With extensions support. :´<

Google chose to go with a Native GTK version of Chrome (and thus Chromium), but it's open source so it's up to some plucky developers to fork it into a GT version. I do feel sorry for KDE users because aside from Konquerer, every browser looks awful - even Opera (which is QT) looks ugly in it.

---

### Post by Metar on 2009-05-20
I dunno if it's faster... I do know that it tends to use a lot more CPU power. Are the graphics natively computed yet? Because currently, when using Chromium, it shows CPU usage levels similar to those I get while running Wine programs.

---

### Post by ghindo on 2009-05-20
> **Mazza558 said:**
> I'm using Chrome on Ubuntu 9.04 now. 

Is it me or is this faster than the Windows version?Well, the version in the PPA is bleeding-edge - which is why we see new features before the Windows version.  The Windows version you're probably using is a stable release (version 1.0.something).

---

### Post by binbash on 2009-05-20
> **Metar said:**
> I dunno if it's faster... I do know that it tends to use a lot more CPU power. Are the graphics natively computed yet? Because currently, when using Chromium, it shows CPU usage levels similar to those I get while running Wine programs.

%0.5 cpu usage here

---

### Post by JanDM on 2009-05-23
Last builds have an updated splash (startup) screen, mentioning Alpha instead of Pre-alpha.
> 
This is an alpha build of Chromium on Linux. The following, significant chunks of functionality are known to be missing:
[LIST]
[*]Plugins, inc Flash (so no YouTube, Hulu etc)
[*]Printing
[*]Complex text
[*]Complex tab dragging
[*]Gears support
[/LIST]

Other parts of the browser are notably incomplete, poorly tuned and broken. User beware!

Looks like they are preparing a first alpha?

I added the repository a few weeks ago. Back then it often crashed and missed functionality. But now its quite stable and usable, only problems for me are missing Flash and some text input problems. Its really fast, as others have said it feels even faster than the Windows version :)

edit: That multi-process thing is very nice as well. I just killed a *chrome* process and the tab turns immediately to a *sad tab*. Just press *reload* and it starts again :)

---

### Post by Metar on 2009-05-23
It still crashes occasionally when I scroll fast on the mouse, for some reason - and almost always crashes when adding a security exception. That, no Flash, occasional glitches when moving the tab-order... But it's getting there.

---

### Post by Giant Speck on 2009-05-23
The new alpha doesn't seem to forbid users from filing bug reports now.  :)

---

### Post by stmiller on 2009-05-23
This is the browser in the new moblin netbook OS. Works OK there.

Here is a link to the latest snapshots:

[http://build.chromium.org/buildbot/snapshots/chromium-rel-linux/](http://build.chromium.org/buildbot/snapshots/chromium-rel-linux/)

---

### Post by zekopeko on 2009-05-23
> **stmiller said:**
> This is the browser in the new moblin netbook OS. Works OK there.

Here is a link to the latest snapshots:

[http://build.chromium.org/buildbot/snapshots/chromium-rel-linux/](http://build.chromium.org/buildbot/snapshots/chromium-rel-linux/)

no it's not. it's a custom shell for the mozilla engine ie. gtkmozembed

---

### Post by Vadi on 2009-05-23
> **Giant Speck said:**
> The new alpha doesn't seem to forbid users from filing bug reports now.  :)

Heey. Noticed that. Not much to bug though, most of the stuff is "not in yet"...

---

### Post by Metar on 2009-05-23
Not only that, but take a look at the Options screen: The checkbox to send anonymous reports is there again.


That being said, I have yet to crash today's build of Chrome - even enabling SSL exceptions, which used to crash it, works now.

---

### Post by Vadi on 2009-05-23
Checkbox doesn't work tho, it doesn't save that setting.

Also, I have not noticed their dev tools before. Looking good: 

[[img]http://www.ubuntu-pics.de/thumb/14924/screenshot_100_060__v9ZCV6.png[/img]](http://www.ubuntu-pics.de/bild/14924/screenshot_100_060__v9ZCV6.png)

---

### Post by Tibuda on 2009-05-23
> **Vadi said:**
> Checkbox doesn't work tho, it doesn't save that setting.

Also, I have not noticed their dev tools before. Looking good: 

[[img]http://www.ubuntu-pics.de/thumb/14924/screenshot_100_060__v9ZCV6.png[/img]](http://www.ubuntu-pics.de/bild/14924/screenshot_100_060__v9ZCV6.png)

That's a webkit thing. It is available in Epiphany WebKit too.

EDIT: Reference in [http://blogs.gnome.org/xan/2009/03/15/good-news-everyone/](http://blogs.gnome.org/xan/2009/03/15/good-news-everyone/)

---

### Post by Metar on 2009-05-23
Indeed it doesn't save that setting... However, that setting wasn't there until now.

Still using today's build for several hours straight and not a single crash.

---

### Post by OutOfReach on 2009-05-23
> **Metar said:**
> 
Still using today's build for several hours straight and not a single crash.

Same here, this build is rock solid

---

### Post by Vadi on 2009-05-23
> **danielrmt said:**
> That's a webkit thing. It is available in Epiphany WebKit too.

EDIT: Reference in [http://blogs.gnome.org/xan/2009/03/15/good-news-everyone/](http://blogs.gnome.org/xan/2009/03/15/good-news-everyone/)

I see. So I'm guessing this whole thing is html+js then? I was wondering about the look.

---

### Post by Metar on 2009-06-01
Seems like they implemented tab-specific crashes: While the previous versions were perfectly stable (but when they crashed, the whole ship went down), the last two-three builds started crashing on Facebook quite often - however, only the Facebook tabs crashed! The rest of the windows remained whole.

Also, when using a non-English keyboard layout, the Ctrl+something keys don't work. For example, Ctrl+V on the Hebrew layout only results in He (&#1492;), the letter corresponding to that key. That's in Chromium only.

---

### Post by OutOfReach on 2009-06-01
> **Metar said:**
> Seems like they implemented tab-specific crashes: While the previous versions were perfectly stable (but when they crashed, the whole ship went down), the last two-three builds started crashing on Facebook quite often - however, only the Facebook tabs crashed! The rest of the windows remained whole.


I can confirm this, except for Myspace.

---

### Post by JanDM on 2009-06-05
There is an official dev-channel [available](http://blog.chromium.org/2009/06/danger-mac-and-linux-builds-available.html) now.

Not much difference (of course) except for the logo: Chrome logo is much more colorful than the Chromium one :)

---

### Post by JanDM on 2009-06-09
In the last nightly there is a checkbox *Use system title bar and borders* in the tabs context menu.

On my laptop I have only 800 pixels so this gives me some more pixels. 
One of the great things about Chrome: it does not waste your screen space with a status bar, bookmarks bar, etc.

---

### Post by Metar on 2009-06-09
You mean, like in the Windows version, without the Gnome title bit?

I sometimes regret switching to the Google Chrome build: The daily updates on Chromium were more fun and were newer..

---

### Post by JanDM on 2009-06-09
> **Metar said:**
> You mean, like in the Windows version, without the Gnome title bit?

Yes. [Here](http://www.google.com/chrome/intl/nl/images/dlpage_lg.jpg) is a Windows screenshot. On Linux the tab bar is even smaller because there is no space above the tabs.
> 
I sometimes regret switching to the Google Chrome build: The daily updates on Chromium were more fun and were newer..
I had the same thought so I just re-added the Chromium nightly. You can install them both :)

---

### Post by merkourio on 2009-06-09
Cool.. Hopefully the stable version will be comni'n out!

---

### Post by Sashin on 2009-06-09
You people all realise you can have both.

---

### Post by Metar on 2009-06-09
HD space constrains on the OS partition. I already made a note to enlarge it next time around.

---

