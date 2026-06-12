---
title: "Announcing Artha ~ An off-line English thesaurus with hot key look up &amp; notifications"
date: 2009-02-09
forum: The Cafe
---

### Post by legends2k on 2009-02-09
[COLOR=Blue]**New version 1.0.2 released for both Windows and Linux!**[/COLOR]


Hi,

I would like to announce [Artha]("http://sourceforge.net/projects/artha") - A handy off-line English thesaurus based on [WordNet]("http://wordnet.princeton.edu/"). Artha has unique features like hot key look up, passive desktop notifications, regular expression based search, spelling suggestions, etc.

[CENTER][IMG]https://sourceforge.net/dbimage.php?id=204250[/IMG]
[/CENTER]

When executed, Artha sits on the system tray monitoring for a set hot key combination. When the user selects some text on any window and presses this hot key, Artha pops up with the definitions of the selection. Should the user prefer notifications over pop-ups, he/she can enable notifications, where instead of popping-up, is shows passive notification of the selected text's most important definition alone. With the 0.9.1 release, Artha also has regex based search for finding words that are vaguely known. Wildcard (*), Joker (?), Range ([, ]), etc. can be used in the regex search pattern to zero-in the sought word.



[CENTER][IMG]https://sourceforge.net/dbimage.php?id=202156[/IMG]
[/CENTER]


Apart from showing the definitions of a word, it also shows its relatives like Synonyms, Antonyms, Derivatives, Attributes, Pertainyms, Similar term and 6 more detailed trees. It can also show domain terms i.e. if 'photography' is searched for, in the 'Domain' tab results, it lists jargon words used in the photography domain like contrast, blow-up, solarise, retouch, intensify, sensitise, etc.

Artha has two modes: simple and detailed. While the former is for a casual user, latter is for people who need more detailed analysis of a given word. In detailed mode, for a given word, Artha displays trees of information like 'Type of', 'Types', 'Part of', 'Parts', etc. (e.g. see screenshot 1, for 'water' is kind of... tree)

For many recently-migrated-from-Windows users, WordWeb (proprietary) would have been a very handy tool there and they ask for a clone/replacement of WordWeb in Linux. Well, Artha could be used as an advanced replacement for WordWeb in *nix environments by not a clone, as it has a wider feature list than WordWeb.

Artha comes in .deb fromat, for easy installation in Ubuntu. Simply double click the .deb or type in the following command. Please do not use *dpkg*, as it doesn't have the ability to resolve dependencies automatically.

```
$ sudo gdebi artha_1.0.2-1_amd64.deb
```Download for [URL="http://sourceforge.net/projects/artha/files/artha/1.0.2/artha_1.0.2-1_i386.deb/download"]i386 - artha_1.0.2-1_i386.deb
[/URL]  Download for [amd64 - artha_1.0.2-1_amd64.deb]("http://sourceforge.net/projects/artha/files/artha/1.0.2/artha_1.0.2-1_amd64.deb/download")
 
**Homepage:** [http://artha.sourceforge.net/](http://artha.sourceforge.net/)

**P.S.:** This is my first open-source application :D

---

### Post by sharathpaps on 2009-02-09
@Sundaram,
           Artha is a wonderful name for this really really nice app. I liked the interface, its clean and very usable. Everything is working flawlessly. Congratulations. Looking forward to this one reaching the repos soon.

---

### Post by Tekmoor on 2009-02-09
I agree, very clean and usable. It works good, I'm really liking it so far. I wanted something like this, great job!

---

### Post by anechoic on 2009-02-09
a nice tool for a writer/word nerd! nice job! :)

---

### Post by Faolan84 on 2009-02-09
SWEET! This is something that should be included on the Jaunty disc. It's something that's simple, elegant, and very useful. Having a dictionary feature here would make it rock twice as much.

---

### Post by pt123 on 2009-02-11
impressive

---

### Post by Chokkan on 2009-02-11
This looks awesome. Great job.

---

### Post by kostkon on 2009-02-11
Great work, really great.

Ah, and you can use a PPA if you want to more easily distribute it (for Ubuntu users, that is).

---

### Post by Nevon on 2009-02-11
Great! As for feature requests, I think you should be able to configure the hotkey for calling Artha. Also, a more long term goal should be to include other languages besides English.

---

### Post by GrouchoMarx on 2009-02-11
I was just thinking the other day how nice it would be to have a decent off-line thesaurus. Looks great. However the excessive tool-tips are annoying and get in the way when scanning text.

---

### Post by imlinux on 2009-02-11
will that notifications feature work in lxde environment?

---

### Post by Faolan84 on 2009-02-11
After a day's use, I can't imagine not having it. This should definitely be default in the Jaunty install.

5 stars out of 5.

---

### Post by Incense on 2009-02-11
> **Faolan Devyn Aodfin said:**
> After a day's use, I can't imagine not having it. This should definitely be default in the Jaunty install.

5 stars out of 5.

+1, What a very useful app! I've been waiting for something like this for quite some time.

---

### Post by Mr. Picklesworth on 2009-02-11
I wish Artha was a bit quieter and stayed off the notification area unless actually notifying me about something. For much of my time its icon is just wasting space, but when I need a thesaurus it is spectacularly handy :)

Wish list: It would be awesome to add dictionaries, espacially if they could work through a little plugin system. Imagine having a dictionary that talks to all your code documentation (eg Devhelp)!

PS:
18 °C in January?! I am jealous.
It's 5° and "feels like -2" (more like -50) here :(

---

### Post by Nevon on 2009-02-12
> **Mr. Picklesworth said:**
> PS:
18 °C in January?! I am jealous.
It's 5° and "feels like -2" (more like -50) here :(

Dude. I just checked the temperature. It's -22°C here.:P

---

### Post by Faolan84 on 2009-02-12
Partly Sunny, 75 F here in beautiful Tallahassee, FL :P

---

### Post by ameermawia on 2009-02-15
i install arhta on my machine but is not being installed ,first time it gave dependency error(when i downloaded for i386) and next time it gave wrong architecture error when i donloaded for AMD64(i have AMD 64 ATHLON processor)..........can some body tell from where to downloaded the exact package and how to install (better by command line)..........

---

### Post by Mr. Picklesworth on 2009-02-15
> **ameermawia said:**
> i install arhta on my machine but is not being installed ,first time it gave dependency error(when i downloaded for i386) and next time it gave wrong architecture error when i donloaded for AMD64(i have AMD 64 ATHLON processor)..........can some body tell from where to downloaded the exact package and how to install (better by command line)..........

Do you have the AMD64 build of Ubuntu? In this case, the software is completely abstracted from your computer hardware; what Artha needs is the appropriate *operating system* which is either using the 64-bit stuff or not

As for the dependency error, you'll encounter that either way. It's completely normal; the package needs some other packages to be installed. If it got that far, the first one you downloaded was probably the appropriate package. Is it saying that it can't find the dependencees, or that they are the wrong version? What *version* of Ubuntu are you running (7.10, 8.04, etc)? Have you changed anything with Ubuntu's Software Sources list?

---

### Post by legends2k on 2009-02-16
Hey guys,
Thanks for the wonderful comments, its really encouraging to see so many. And sorry for replying late as I couldn't get online for a few days.

Now for your queries:

> **kostkon said:**
> Great work, really great.

Ah, and you can use a PPA if you want to more easily distribute it (for Ubuntu users, that is).

@kostkon: Artha is getting into Debian's Main repos (got a sponsor and the process is happening). Hence when Ubuntu is synced with Debian, it should automatically move to Ubuntu's Universe. Even I am waiting for that to happen. If it will take time, I will put it in PPA.

> **Nevon said:**
> Great! As for feature requests, I think you should be able to configure the hotkey for calling Artha. Also, a more long term goal should be to include other languages besides English.

@Nevon: Your request is actually one of the TODOs top most, since I want it cusomizable too. I was just trying out the hot key coding and I just released it with 4 hardcoded options to see how it goes. I will, in the next release, in which I am planning for a preferences box, make it choosable. As for the long term goal, I have written it as generic as possible, and in no way it is tied hard to the Eng. WordNet, when we have a decent WordNet for some other language, we can see if Artha works fine with it. And if yes, we can make it pluggable. But as you mentioned, its for the long term plans :D

> **GrouchoMarx said:**
> I was just thinking the other day how nice it would be to have a decent off-line thesaurus. Looks great. However the excessive tool-tips are annoying and get in the way when scanning text.

@GrouchoMarx: I sometimes find it annoying too, thanks for notifying me of it, I will trim them in the next release

> **imlinux said:**
> will that notifications feature work in lxde environment?

@imlinux: Ideally, as far as other notifications like **System Update**, etc. come up, then Artha's should also work, as there is no diff. in the library used. But I am not 100% sure, since I haven't used LXDE, while you could try it & post the results here :)

> **Mr. Picklesworth said:**
> I wish Artha was a bit quieter and stayed off the notification area unless actually notifying me about something. For much of my time its icon is just wasting space, but when I need a thesaurus it is spectacularly handy :)

Wish list: It would be awesome to add dictionaries, espacially if they could work through a little plugin system. Imagine having a dictionary that talks to all your code documentation (eg Devhelp)!

@Mr. Picklesworth: In the next release, I will add an option for toggling sys. try icon's visibility like Always, Only when notifying and Never. As for you wish, Artha works completely on WordNet's protocol right now; what you ask for is something like a dictionary could be compiled and made to work with as a plugin for Artha (like *Nevon* has asked for Artha on other languages). May be I can unify both the ideas and create a tool to compile dictionaries and make reqd. changes in Artha to use the tool's result at runtime. This will be a nice long term feature. Well, thanks for the suggestion :P

> **ameermawia said:**
> i install arhta on my machine but is not being installed ,first time it gave dependency error(when i downloaded for i386) and next time it gave wrong architecture error when i donloaded for AMD64(i have AMD 64 ATHLON processor)..........can some body tell from where to downloaded the exact package and how to install (better by command line)..........

@ameermawia: Its easy to fix this. First, your machine is i386 and hence please do not use AMD64. Next is, you may have used *dpkg* to install the downloaded i386 deb file. Please do not use ***dpkg***. It does not have the ability to resolve dependency, hence use ***gdebi*** (has the ability to resolve dependencies).

Most importantly, make sure **Universe** repositories are enabled. Uncomment the following lines in /etc/apt/sources.list (gksudo gedit /etc/apt/sources.list)

```

deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

```

Then do:

```

sudo apt-get update
gdebi [artha_0.8.0-1_i386.deb]("http://downloads.sourceforge.net/artha/artha_0.8.0-1_i386.deb?modtime=1234245725&big_mirror=0&filesize=56432")

```


Thanks for all your valuable feedbacks :P I will try to incorporate as many as possible in the future releases.

---

### Post by twipley on 2009-04-21
> **Nevon said:**
> Dude. I just checked the temperature. It's -22°C here.:P

dudes, -22°c is nothing, believe me. in february, it fell to -43°c for three days in a row in my hometown, breaking a record (in addition to breaking our cars!). :)

concerning the port to linux of wordweb (wordnet), i think it would be very nice to have this added to ubuntu. far too people are not even aware of the existence of that dictionary. thank you, princeton! (and all wordnet-related developers).

peace out,
twipley

---

### Post by legends2k on 2009-04-22
Yes Twipley, I think I will make another release for Artha (with regex search options :) and then submit it to Debian for inclusion in its apt repositories, which in turn will be reflected in the next Ubuntu release (9.10) when it's getting sync'd with Debian. Until then we have 2 options: Personal Package Archives of a gentleman named Arnaud: [https://launchpad.net/~weboide/+archive/ppa]("https://launchpad.net/%7Eweboide/+archive/ppa") using with Artha can be apt-get installed, or  direct downloading of the deb from [http://artha.sourceforge.net](http://artha.sourceforge.net).

And yay! Today is 9.04 release of Ubuntu, sit back and enjoy while it gets installed/upgraded!!!

---

### Post by brallan on 2009-05-20
BRILLIANT! thank you soooooo much for this wonderful program! wordweb was one of the things keeping me in windows for a long time. eventually I just got fed up with dual booting and said goodbye to wordweb, but now and then an unbearable nostalgia would overtake me! I was going to try installing it in wine, and lo and behold, no need thanks to another generous community member working hard to give us a wonderful tool! 

> **legends2k said:**
> And yay! Today is 9.04 release of Ubuntu, sit back and enjoy while it gets installed/upgraded!!!

I'd also like to tell mac users about it, is there a mac (or windows .exe) installer yet?

---

### Post by monsterstack on 2009-05-20
This is one of the best apps I've come across in a while. Really useful stuff. Light enough to keep running in the background, too. I think that's crucial. Well done. :)

---

### Post by legends2k on 2009-05-22
**@brallan:** Thank you for your compliments! Have you tried the new release Artha 0.9.1 (or the prev. one 0.8.0)? It has the additional feature of regular expressions based search; this will match Artha with WordWeb Pro too :) I am yet to port it to Mac and Windows. I will do it sometime.

**@monsterstack:** Thank you! :)

Artha 0.9.1 (both .deb and .tar.gz) can be downloaded from here: [http://artha.sourceforge.net/wiki/index.php/Download](http://artha.sourceforge.net/wiki/index.php/Download)

---

### Post by joemun on 2009-05-28
Artha rocks!...to the repos please...it works flawlessly. Thanks and congrats.

---

### Post by kickwin on 2009-05-29
Works like a charm. Thanks a ton to the developer. 

I have been looking for a Wordweb-like app for linux and Artha is the solution. Though, I have to say, it was not easy to find it by searching online. I think it needs a little PR work. 

Btw, I have a couple of quick questions. When I press the keyboard shortcut (Ctrl + Alt + A or W), I always find Artha minimized on the task bar. Then I have to Alt+Tab to go the Artha. Is it how it is built or I have tweak something? 

Also I don't see the "Detailed Lookup" button on the notification when the "Notify" mode is enabled. 

Thanks once again for the great app.

---

### Post by brallan on 2009-05-30
> **kickwin said:**
> Though, I have to say, it was not easy to find it by searching online. I think it needs a little PR work.

I agree. 

I included a link on the [WordNet]("http://en.wikipedia.org/wiki/Wordnet") wikipedia page, as well as a mention in the WordWeb article. 

there is no [Artha]("http://en.wikipedia.org/wiki/Artha") article in wikipedia yet (only the hindu concept), but would likely be impossible to make one until there is some media attention for the project.

on the website, folks can nominate it for the community choice awards:
[http://artha.sourceforge.net/]("http://artha.sourceforge.net/")

perhaps we can add a mention in some of the pages which list windows equivalencies.

Looking at the wordnet wikipedia page, it seems that something like wordnet is available for a number of other languages. Balkanet, etc. Should Artha become multilingual, it could offer things that wordweb does not. it could then produce quite a sensation and publicity might get rolling just by authors and journalists using it, particularly if ported to mac and windows.

---

### Post by legends2k on 2009-05-30
**@[joemun]("http://ubuntuforums.org/member.php?u=131103"):** Thank you![B]

[@kickwin]("http://ubuntuforums.org/member.php?u=840263"):[/B]
> I think it needs a little PR work. Yeah, I think so, but I should say I'm not good at selling things ;) Probably you guys can help me out here. [already joemun had sent a mail on Artha to [Life Hacker]("http://lifehacker.com/")]

> I always find Artha minimized on the task bar. Then I have to Alt+Tab to go the Artha. Is it how it is built or I have tweak something?I find this annoying too. But no, Artha's not designed so. In other distros like Xubuntu, Kubuntu, Fedora flavours, etc. when the user presses the hot key it gets presented to the user with the keyboard focus in it; while on Ubuntu, it doesn't.

> I don't see the "Detailed Lookup" button on the notification when the "Notify" mode is enabled. The latest release of Ubuntu (9.04) doesn't support buttons on passive desktop notifications and hence I removed it. I forgot to change the help text and the screenshots accordingly; will do so in the next release. However, clicking on the earlier available 'Detailed Lookup' button will just show Artha's window on the desktop. This can be done by clicking on the Artha's status icon itself, hence removing it is not loss of any feature :)

Thanks for your comments!

**@[brallan]("http://ubuntuforums.org/member.php?u=52299"):** Thanks :)
Long back, I did send a mail to WordNet webpage maintainer, asking to add Artha to their [Related Projects]("http://wordnet.princeton.edu/links") page. He said he will do so, I could never see it get listed. I send another mail with no response.

As for other language WordNets, Artha should work perfectly fine as long as they follow the same protocol as the English WordNet does. But I haven't tried it yet on other languages.

Am now porting it to Windows, but I have a missing piece in the puzzle; am not able to get the selected text on Windows. Hence I'm still stuck on this one, with no fruitful help by Googling. Probably some community member can help me out if they know; let's see.

---

### Post by kickwin on 2009-05-30
I have also mentioned Artha in some ubuntu forum posts which were the top google search results for queries like "linux wordweb".

---

### Post by meho_r on 2009-05-30
Thank you for this fantastic app. I think it goes in Startup Applications from now on ;) I've been using StarDict for a long time now, but I'm not sure if the project is alive anymore :( And I had some issues with it. But it really has nice features I would love to see in Artha some day in future, e.g., support for Babylon etc. dictionaries. And one more thing comes in mind: is it possible to include some kind of pronunciation addon or something (voice would be nice too)? It would help a lot in learning english. Thanks again.

---

### Post by kickwin on 2009-05-31
> **meho_r said:**
> And one more thing comes in mind: is it possible to include some kind of pronunciation addon or something (voice would be nice too)? 

I second that. IMO, pronunciation help like in Wordweb would suffice.

---

### Post by Viva on 2009-05-31
Excellent alternative to wordweb

---

### Post by legends2k on 2009-06-01
Looks like pronunciation is one of the most wanted feature! I agree that pronunciation would be a good aid in learning English. There are two forms, one is to display phonetics for a word (text) and the other is vocal pronunciation of the word (audio). The latter is possible, I will work on it, probably in the next release, we can have that feature.

But for the former I.e. to display phonetics for every word, does anyone know of a free phonetics database or some kind of library which can be used to get the phonetics a word? If so, we can integrate that too.

---

### Post by oOarthurOo on 2009-06-01
I'm confused... is it a thesaurus, or a dictionary/thesaurus? The screenshot suggests the latter.

---

### Post by kickwin on 2009-06-01
> **oOarthurOo said:**
> I'm confused... is it a thesaurus, or a dictionary/thesaurus? The screenshot suggests the latter.

Artha is a dictionary. The screenshot shows the OP querying the definition of the word 'thesaurus'.

---

### Post by kickwin on 2009-06-01
> **legends2k said:**
> There are two forms, one is to display phonetics for a word (text) and the other is vocal pronunciation of the word (audio). The latter is possible, I will work on it, probably in the next release, we can have that feature.

Wouldn't this (latter one) make the app heavy?

---

### Post by legends2k on 2009-06-02
> I'm confused... is it a thesaurus, or a dictionary/thesaurus? The screenshot suggests the latter.
**@[oOarthurOo]("http://ubuntuforums.org/member.php?u=690246"):** You are right, it is a dictionary and thesaurus. It is based on [WordNet]("http://wordnet.princeton.edu/") the famous thesaurus by Princeton University.


**@kickwin:** It is not a dictionary alone, but a thesaurus too. Dictionary is something that gives the definition(s) of a given word, thats it. It doesn't tell you about a word's relatives like synonyms, antonyms, etc. Artha gives a long list of a word's relatives apart from it's definitions, and hence is a thesaurus and a dictionary.

And giving a vocal pronunciation shouldn't make it heavy, since we have very good text to speech engines available on Linux, which will get the word and spell it out. Don't worry, we'll never bloat Artha, I want it as light as possible. Thanks the inputs :)

---

### Post by Kushal Sejwal on 2009-06-08
Great app, brilliant effort Sundaram. Proved to me that there is no single app that cannot have a even better Open-source alternative. Kudos to your effort.

Sweet, simple, straight! Just loving it.

---

### Post by ws.venkateswaran on 2009-06-21
thanks... really nice app..

how do i keep it updated... is there an method or should i keep checking the site..

---

### Post by legends2k on 2009-06-22
**@Kushal:** Thanks!

**@Ventakeswaran:** If you are asking about updates to Artha, yes, you can check the [website]("http://artha.sourceforge.net/"). But if you are asking for an update to the dict/thesaurus database Artha uses, namely [WordNet]("http://wordnet.princeton.edu/"), it won't be updated daily or so. It' primarily aimed at off-line usage.

---

### Post by lammoth on 2009-07-05
anyway to change the shortcuts for artha? i tried in man artha, couldnt find any way

---

### Post by legends2k on 2009-07-06
Hi [lammoth]("http://ubuntuforums.org/member.php?u=868673"),
I guess you are trying to change Artha's hotkey (and not the shortcut, which will be in Applications->Accessories on a Ubuntu machine). As of now, Artha doesn't allow to change the set hot key I.e. it is not customizable; I will be working on this feature in the next release to make it customizable. In the latest release (0.9.1) Artha tries to set a hot key in the following order: **Ctrl + Alt + ***[ W | A | T | Q ]* I.e. first Ctrl + Alt + W, if it is occupied by some other app. then *A* and so on.

Hope that helps :)

---

### Post by ugutugut on 2009-07-28
to : legends2k

Thank you very much for your contribution in this computing world.
Your software is really useful.

---

### Post by bhadotia on 2009-07-29
So will it be in the official karmic universe repos?

And thanks for this great piece of software! ;)

EDIT:
Never mind, I see its in the karmic repos now.

---

### Post by jabe_z on 2009-12-17
Hi,

very Nice application. I use wordweb alot on windows and found Artha very much better than Wordweb. 

When i enabled Notification, its not giving any notification. I'm just getting another small popup with Warning   symbol on the windows. Is this the right way how notification comes??? I'm asking this because, when i saw the Screenshot in Artha's home page, Notification is showing in a different way. 

I'm using it on Ubuntu 9.10.

---

### Post by legends2k on 2009-12-18
Hi [jabe_z]("http://ubuntuforums.org/member.php?u=701960"),
What you're getting is a alert box (with an exclamatory symbol on it). Are you getting it as a message box or as a notification? What message do you get on the box with the exclamatory 'pop-up'? Is it showing the queried word's definition in the box? Could you post a screen shot or give some more details?

What version of Artha are you using? How did you install it?

---

### Post by Linuxforall on 2009-12-18
Thank you very much for this app, after stardic, this is my second preference. Since stardict development has stopped, I was worried about the future of the offline thesarus and dictionary in Linux, your app fills that void.

---

### Post by lelamal on 2009-12-28
> **legends2k said:**
> Hi [jabe_z]("http://ubuntuforums.org/member.php?u=701960"),
What you're getting is a alert box (with an exclamatory symbol on it). Are you getting it as a message box or as a notification? What message do you get on the box with the exclamatory 'pop-up'? Is it showing the queried word's definition in the box? Could you post a screen shot or give some more details?

What version of Artha are you using? How did you install it?

Hi, I'll try to answer on his behalf, if that's OK, for I've been wondering the same thing. Basically, on Ubuntu Jaunty what you got was a notification (if enabled) while now on Karmic you only get a message box, which you have to close manually.

Interestingly enough, though, today I found out that when the word is not found, Artha will show a notification (see Screenshot 1.png), while will pop up an alert box when the word is found (see Screenshot 2.png) - most of the times, that is.

Artha version 0.8.0, installed through Synaptic. Many thanks!

---

### Post by legends2k on 2009-12-30
@[lelamal]("http://ubuntuforums.org/member.php?u=702367") and [jabe_z]("http://ubuntuforums.org/member.php?u=701960"),
From Ubuntu Jaunty Jackalope (9.04) onwards Mark Shuttleworth changed the *Notifications* scheme in Ubuntu, where the notification looks sleek and semi-transparent, but with **NO buttons on** it. Ubuntu versions prior to it have a kind of Window's balloon tip look and feel, which allowed buttons on it or a pie chart to show the time out period remaining (image attached for ref.).

Until Artha 0.8.0, notifications in Artha have a *Detailed Lookup* button on them where the user can click on it and get the actual Artha main window popped up; but once this new scheme came into place, the handling done by the Ubuntu 9.04 (or later) is to show the notification as a message box, *if it has buttons* I.e. when a notification doesn't have a button, then it shows it in the newer, sleekier way; but if the code asks for buttons to be shown, it never shows it as a passive notification window, but as a message box. More on this here: [http://wiki.ubuntu.com/NotifyOSD](http://wiki.ubuntu.com/NotifyOSD)

[IMG]http://img191.imageshack.us/img191/9003/notifications.jpg[/IMG]
This is the reason you get the "Oops - Queried term not found" notification as a notification (since it doesn't have any buttons attached to it) while the actual succeeded lookup as a message box (since it has buttons on it). So as to avoid this problem, I've altogether removed buttons in notifications from Artha 0.9.1 onwards; so both failed and succeeded look-ups don't ask the notification daemon to show a notification with buttons, so the user always get the notifications as notifications rather than as message boxes.

** Ubuntu repos now have only Artha 0.8.0; The newer 0.9.1 is yet to be synced.** You can either wait for that to happen, or download the deb for your architecture from [http://artha.sourceforge.net/wiki/index.php/Download](http://artha.sourceforge.net/wiki/index.php/Download) and install it.

Hope this helps :)

---

### Post by lelamal on 2009-12-30
> **legends2k said:**
> 
Hope this helps :)

Definitely! Many thanks for your detailed explanation, and for all your good work.

---

### Post by legends2k on 2010-01-15
Guys, a new version of Artha (1.0.0) is released! It has the most wanted hot-key customization feature now :)
Apart from, in it's previous versions, Artha wouldn't always come to the user's focus on the hot-key summon, this too is fixed now. Also it's got lot of minor optimzations and fixes.

> Great! As for feature requests, I think you should be able to configure the hotkey for calling Artha. Also, a more long term goal should be to include other languages besides English.@Nevon: This hotkey customization feature is now done in 1.0.0 release of Artha :)

---

### Post by Linuxforall on 2010-01-15
How bout setting up a ppa for Ubuntu users? That way updates would be far more convenient.

---

### Post by legends2k on 2010-01-15
Right now 0.9.1 is present in Lucid, I guess. The newer versions take time to reach Ubuntu's repos usually. Am working on getting this 1.0.0 updated in Debian (who too has 0.9.1), if this is done within the Lucid's Debian Import Freeze date (Feb. 14th), then 1.0.0 will make it into Lucid's repos. Meanwhile someone can probably can set up a PPA.

---

### Post by kickwin on 2010-01-15
> **legends2k said:**
> Apart from, in it's previous versions, Artha wouldn't always come to the user's focus on the hot-key summon, this too is fixed now.
Feature works great. Keep up the good work.=D>

Pronunciation tip is the only thing that I think is missing from Artha.

---

### Post by handy on 2010-01-15
**@legends2k:** I've just tried to install the newly superseded version of Artha on Arch via AUR, but after dealing with wordpress it failed as follows:

[I]==> ERROR: Failure while downloading artha-0.9.1.tar.bz2
    Aborting...
Error: Makepkg was unable to build artha package.[/I]

Anyway, I marked the 0.9.1 package as out of date over at AUR, so hopefully the package maintainer will be able to organise the PKGBUILD for us Arch users who already do use Artha, & for me too, who wants to.

Artha looks like an incredibly useful tool, thanks you for making it for us. :)

---

### Post by bryonak on 2010-01-15
I was using StarDict for a long time and it did the job fine, except for a few glitches.
When the rumours of it's development stop came about, I switched to the then new GoldenDict, which is basically a StarDict clone with many improvements (similar interface, supports all dict formats, WebKit rendering, GPLv3, full text translation, web templates, audio spelling ...) and I'm quite happy with it.

Enough about that, I'm going to give Artha a spin if it seems like it can fit my bill.
That is: how does Artha compare to GoldenDict? Does it support all those dictionaries StarDict supported? I mean .ifo/.dict./.idx/.syn/.bgl/.dsl ... WordNet alone isn't enough for me ;)

Besides, I'm not sure StarDict is really dead, with the latest stable release being in May 2009. The forums however don't work.

---

### Post by Linuxforall on 2010-01-15
Stardict works fine here for me, the pronounciation also works via tts file, does Goldendict support pronounciation as well? I don't see it mentioned anywhere on their site.

---

### Post by legends2k on 2010-01-16
@kickwin: Thank you for your kind words :) I'll try to implement the pronunciation and region flag (UK/US/Aus, etc.)

@handy: Am not sure of Arch linux's package management, however, Artha should be build-able on any system with glib, gtk+, dbus and wordnet development headers availability. You can download the source from [http://artha.sourceforge.net/wiki/index.php/Download](http://artha.sourceforge.net/wiki/index.php/Download)

@bryonak: There are lot of heavy weight dictionaries/thesaurus like StartDict, GoldenDict, etc. out there, which cater a larger crowd, who wish to have all the dictionary databases in their disposal; but the whole purpose of Artha is to have something very handy and minimal, with a simple interface and bare dependencies, that it works on even a mobile without hassle (it's run on maemo ~ Nokia 810). So, no, Artha doesn't support anything other than WordNet; am not sure, if it ever will.

---

### Post by handy on 2010-01-16
> **legends2k said:**
> 
@handy: Am not sure of Arch linux's package management, however, Artha should be build-able on any system with glib, gtk+, dbus and wordnet development headers availability. You can download the source from [http://artha.sourceforge.net/wiki/index.php/Download](http://artha.sourceforge.net/wiki/index.php/Download) 

The previous version was being used on Arch, via the AUR (Arch User Repositories). For some reason the package fails to complete it's installation process at the moment.

I am inexperienced with more than minor editing of PKGBUILD files.  Even so, I spent some time this morning trying to get your current version to install, but I couldn't quite crack it.  

I tried using both the source & using the .deb package via *deb2targz* before I gave up.  I really didn't feel like spending the hours learning all of the fine details of editing PKGBUILD files today. :)

The WordNet package already exists in AUR which is helpful too.

Anyway, thanks for your reply, I'm sure it won't be too long before the maintainer has a look at the comments & modifies the PKGBUILD. :)

---

### Post by legends2k on 2010-01-16
Just in case, actually, in the newer 1.0.0 version, dependencies are now reduced. I.e. libnotify and python are no more needed to build artha from source. So the same dependencies list of 0.9.1 is not needed, it's actually less. [http://artha.sourceforge.net/wiki/index.php/Installation](http://artha.sourceforge.net/wiki/index.php/Installation) ~ This paage has instructions on building and also try to look @ the INSTALL file I.e. if you've the mood ;)

---

### Post by handy on 2010-01-16
**@legends2k:** In case you are curious, I've posted a PKGBUILD that apparently worked fine for installing artha on Arch:

```

pkgname=artha
pkgver=0.9
pkgrel=1
pkgdesc="English thesaurus that works completely off-line and is based on WordNet"
arch=(i686 x86_64)
url="http://artha.sourceforge.net/"
license="custom"

depends=(
'glib'
'gtk2'
'wordnet'
)

source=(
"http://sunet.dl.sourceforge.net/project/$pkgname/$pkgname/$pkgver.$pkgrel/$pkgname-$pkgver.$pkgrel.tar.bz2"
)

md5sums=(
'6614a81980e7bccf55449ad6ab9ee080'
)

build() {
cd $startdir/src/$pkgname-$pkgver.$pkgrel
./configure --prefix=/usr || return 1
make || return 1
make DESTDIR=$startdir/pkg install || return 1
}

```

---

### Post by bryonak on 2010-01-16
@legends2k:
Thanks for the info, I just gave v1.0.0 a try.
I like the clean interface as well as the speed... performance always caters to me.
Somehow I wasn't able to bind the Super (Meta, Win) key as lookup hotkey, for example "Super+<" triggers on "<" only but not on "Super" and "<".
Speaking of which, using the notification system is really cool, but it doesn't display two subsequent lookups at the same time (above each other, like the usual notifications). Try looking up more than 3 words in a one-second-intervall to see what I mean.

Like stated, WordNet isn't enough for me, so I probably won't be using Artha...
Great job nevertheless!


@Linuxforall:
Yes, GoldenDict supports pronunciation.

---

### Post by Shazaam on 2010-01-16
Good work with Artha!

One thing I would like to see is an Artha right-click context menu entry for highlighted text. Then there would be no need for a hotkey.

---

### Post by legends2k on 2010-01-16
**@handy:** I see that you've missed dbus-glib-1 dependency in your PKGBUILD. Try adding that for 1.0.0 and executing the same. Without dbus-glib Artha won't run.

**@bryonak:** Thanks for notifying me of the Super key, it's actually a bug I see in 1.0.0, I've fixed it, this can be in seen in the next release.

**@Shazaam:** Thanks :) Although am not very sure of context sensitive menus in Linux, I'll see if I can make one for Artha.

---

### Post by handy on 2010-01-17
> **legends2k said:**
> **@handy:** I see that you've missed dbus-glib-1 dependency in your PKGBUILD. Try adding that for 1.0.0 and executing the same. Without dbus-glib Artha won't run.


Thanks, I'll give that a try & see how it goes.

---

### Post by handy on 2010-01-18
**@legends2k:** I gave it a shot with the *dbus-glib-1* package as a dependency but it got an error that basically said Arch doesn't use it. :)

---

### Post by legends2k on 2010-01-18
**@handy:** Oops! Change the *dbus-glib-1* to *dbus-glib*. It is available in Arch, refer this [http://www.archlinux.org/packages/extra/i686/dbus-glib/](http://www.archlinux.org/packages/extra/i686/dbus-glib/)

---

### Post by handy on 2010-01-19
> **legends2k said:**
> **@handy:** Oops! Change the *dbus-glib-1* to *dbus-glib*. It is available in Arch, refer this [http://www.archlinux.org/packages/extra/i686/dbus-glib/](http://www.archlinux.org/packages/extra/i686/dbus-glib/)

**@legends2k:** dbus-glib was in the system already; I added it as a dependency anyway, but still no go?

I just emailed the guy that maintains Artha in AUR, so hopefully he'll make a few mod's to the PKGBUILD, test it & release it into the wild!

---

### Post by legends2k on 2010-01-20
[SIZE=4][COLOR=Blue]**[Artha 1.0.1]("https://sourceforge.net/projects/artha/files/") is released!**[/COLOR][/SIZE]

* Suggestions are now made with priority given to the English locale thats set in the user's session
* Fixes for hotkeys with mods like Super, Hyper, etc. are now made to work
* Artha fully works on KDE 4.3 from this release

It's recommended that you update to this release, from now on :)

---

### Post by handy on 2010-01-24
**@legends2k:** After 10 days of waiting, I asked on the Arch/AUR sub-forum, if anyone could help me with a PKGBUILD.

Very quickly that AUR package maintainer was dumped from Artha & the other packages that he used to maintain.

Someone posted a new PKGBUILD in answer, & on waking this morning, I look to find that someone who hadn't made any communication in the thread I started on this topic has adopted the package & made a new PKGBUILD that worked beautifully for me. :)

So Artha 1.0.1-1 is installed on my 64bit Arch/Openbox, I have Openbox configured via .config/openbox/autostart.sh to call Artha when Openbox starts, which it does quietly & cleanly, putting its icon in my uncluttered xfce4-panel.

From my thus-far brief experience with Artha, I think it will become a permanent part of my system.

So thanks legend2k, for all of your work on Artha. :)

Here is the PKGBUILD that works for anyone interested:

```
[I]# Contributor: ShadowKyogre <shadowkyogre@gmail.com>
# Maintainer: res <andres87p gmail>
pkgname=artha
pkgver=1.0.1
pkgrel=1
pkgdesc='A free cross-platform English thesaurus based on WordNet'
arch=(i686 x86_64)
url=http://$pkgname.sourceforge.net/wiki/index.php/Home
license=(GPL)
depends=(wordnet gtk2 dbus-glib)
source=(http://downloads.sourceforge.net/sourceforge/$pkgname/$pkgname-$pkgver.tar.bz2)
md5sums=(53c533dee11af70d6592eea43891e1cd)

build() {
    cd $pkgname-$pkgver

    ./configure --prefix=/usr
    make || return 1
    make DESTDIR=$pkgdir install
}
[/I]
```

---

### Post by meho_r on 2010-01-25
Ah, I simply love this application :) An idea (sorry if it was mentioned before): is it possible to make the hotkey a switch, so when you press it first time it summons Artha, and when you press it second time it minimizes it to the notification area?

---

### Post by legends2k on 2010-01-26
[@handy]("http://ubuntuforums.org/member.php?u=55341"): Thanks for your kind words :) I hope this helps other Arch users to install Artha.

[@meho_r]("http://ubuntuforums.org/member.php?u=281491"): No one has suggested it yet, you're the first to do so :) But once Artha gets summoned on a lookup, we've the **Escape** key to push it back to the system tray, if you've not noticed it yet. Will that be sufficient? Or do we still need to make the hotkey a switch?

Thanks for the comments guys!

---

### Post by handy on 2010-01-26
> **legends2k said:**
> [@handy]("http://ubuntuforums.org/member.php?u=55341"): Thanks for your kind words :) I hope this helps other Arch users to install Artha. 

Now that Artha has a knowledgeable & conscientious package maintainer, it will be as easy & simple as it is supposed to be to install on Arch.

Thanks again, you have done a really nice job. :)

---

### Post by meho_r on 2010-01-26
> **legends2k said:**
> ...

[@meho_r]("http://ubuntuforums.org/member.php?u=281491"): No one has suggested it yet, you're the first to do so :) But once Artha gets summoned on a lookup, we've the **Escape** key to push it back to the system tray, if you've not noticed it yet. Will that be sufficient? Or do we still need to make the hotkey a switch?

Thanks for the comments guys!

I caught myself keeping my hand on the hotkey combination on the keyboard while reading translations of a sequence of words, and that's when I noticed that it may be a good idea. Of course, Esc still do the job, but you must move your hand up-down all the time (and that can be annoying in some cases, believe me :D) What others think? Of course, if it's a lot of work to implement, just leave it, this is absolutely the lowest priority request :)

---

### Post by sarthorks on 2010-02-14
Thanks legends2k! I had been waiting for this for soo long! Thanks a ton. However, I wish Artha soon incoporates the WordWeb pronunciation key feature, its a boon for any dictionary.

I am having a problem. Everytime i try to use the wildcards ? or *, in a fashin like: 
```

a*

```
i get the following error:
```

File sense.index not found at /usr/share/wordnet
Please install it and restart Artha to do a regular expression based search.

```

Can you tell me what that means, and what should i do to get it right?
Thanks once again!

---

### Post by legends2k on 2010-02-14
**@[sarthorks]("http://ubuntuforums.org/member.php?u=612179"):** May I know how you installed Artha? What distro are you using? If it's Ubuntu, Artha's direct dependency is WordNet (package: *wordnet*); there's one more package by the name ***wordnet-sense-index***, this is not a must-have dependency to run Artha but a recommended-to-have package which will enable the regex based search feature of Artha. If that is not installed, *index.sense* file will not be present in the path the error says about. If it's installed, you can make the regex-based search (*, ?, etc.). To install it in Ubuntu/Debian:

> sudo apt-get install wordnet-sense-index

Try this, it should fix it; if not you can always ping me regd. the same. Hope it helps :)

**@[meho_r]("http://ubuntuforums.org/member.php?u=281491"):** I've made a note of it, mate :) I'll see how I can fit it in.

---

### Post by sarthorks on 2010-02-15
> **legends2k said:**
> **@[sarthorks]("http://ubuntuforums.org/member.php?u=612179"):** May I know how you installed Artha? What distro are you using? If it's Ubuntu, Artha's direct dependency is WordNet (package: *wordnet*); there's one more package by the name ***wordnet-sense-index***, this is not a must-have dependency to run Artha but a recommended-to-have package which will enable the regex based search feature of Artha. If that is not installed, *index.sense* file will not be present in the path the error says about. If it's installed, you can make the regex-based search (*, ?, etc.). To install it in Ubuntu/Debian:



Try this, it should fix it; if not you can always ping me regd. the same. Hope it helps :)


Thanks! I am using Hardy, and i did as you said. Its working very well now!

---

### Post by johnterdi on 2010-02-21
I really like Artha. A sound replacement for wordweb on linux platform. I just love the simple design Artha is given. I don't think I can switch to other dictionary as this one is proving itself to be very compact and reliable.

I'd love to see **phonetic transcriptions** added as an important core feature. It would help a lot when trying to learn English and its pronunciations.

---

### Post by legends2k on 2010-02-21
> **johnterdi said:**
> I really like Artha. A sound replacement for wordweb on linux platform. I just love the simple design Artha is given. I don't think I can switch to other dictionary as this one is proving itself to be very compact and reliable.

I'd love to see **phonetic transcriptions** added as an important core feature. It would help a lot when trying to learn English and its pronunciations.

@johnterdi: I'm thinking of implementing pronunciation feature using [eSpeak]("http://espeak.sourceforge.net/index.html") (both textual and vocal) in the next release :)

---

### Post by johnterdi on 2010-02-23
Awesome! That's great to hear. I hope it comes out soon so I can use it to studying.

Many thanks.

---

### Post by CupofDice on 2010-02-24
Using opensuse 11.2 KDE 64bit, I have this problem when running Artha in the terminal. I installed first by tracking down a fedora RPM, but that gave me an error and Artha wouldn't search, so then I installed by source code. I have libwordnet-devel installed, which I think is wordnet-dev on ubuntu, but I also installed the wordnet package from the princeton site to see if that would work. 

Either way ,I keep getting this error when running Artha in the terminal and my searches turn up empty.

> Failed to open WordNet database files!
Make sure WordNet's database files are present at

(null).

If present elsewhere, set the environment variable WNHOME to point to it.

Thanks for any help.

---

### Post by legends2k on 2010-02-25
@[CupofDice]("http://ubuntuforums.org/member.php?u=165588"): I installed OpenSUSE 11.2 (with KDE 4.3) fresh in a virtual machine and tried searching for packages 'wordnet', 'wordnet-devel', 'libwordnet-devel' using the command
> zypper install wordnet wordnet-devel libwordnet-devel and all of them returned a "[COLOR=Red]'package' not found[/COLOR]" message. It is to be noted that the WordNet package is not yet available in the OpenSUSE official repositories. It's currently in their wishlist only ([http://en.opensuse.org/Wishlist_Various](http://en.opensuse.org/Wishlist_Various)); so wordnet cannot be installed from OpenSUSE's repositories with a single command; one has to install it from source.

So I downloaded WordNet's tarball from Princeton's site ([http://wordnetcode.princeton.edu/3.0/WordNet-3.0.tar.bz2](http://wordnetcode.princeton.edu/3.0/WordNet-3.0.tar.bz2)) and tried compiling its source; but for building WordNet from source, Tcl and Tk development headers are required (as told by WordNet build system). Hence I installed them by > zypper install tcl-devel tk-devel. Then I was able to successfully build and install WordNet (tried running command 'wnb' and searched some random terms in the thesaurus for which results got returned properly. Finally, I installed Artha from source ([http://sourceforge.net/projects/artha/files/artha/1.0.1/artha-1.0.1.tar.bz2/download](http://sourceforge.net/projects/artha/files/artha/1.0.1/artha-1.0.1.tar.bz2/download)). It worked fine the very first time; search returned results normally as it should.

I can see that you've installed Artha from source properly; but I'm skeptical of your WordNet installation. Can you please tell how you installed WordNet in your machine?

---

### Post by CupofDice on 2010-03-23
> **legends2k said:**
> @[CupofDice]("http://ubuntuforums.org/member.php?u=165588"): I installed OpenSUSE 11.2 (with KDE 4.3) fresh in a virtual machine and tried searching for packages 'wordnet', 'wordnet-devel', 'libwordnet-devel' using the command
 and all of them returned a "[COLOR=Red]'package' not found[/COLOR]" message. It is to be noted that the WordNet package is not yet available in the OpenSUSE official repositories. It's currently in their wishlist only ([http://en.opensuse.org/Wishlist_Various](http://en.opensuse.org/Wishlist_Various)); so wordnet cannot be installed from OpenSUSE's repositories with a single command; one has to install it from source.

So I downloaded WordNet's tarball from Princeton's site ([http://wordnetcode.princeton.edu/3.0/WordNet-3.0.tar.bz2](http://wordnetcode.princeton.edu/3.0/WordNet-3.0.tar.bz2)) and tried compiling its source; but for building WordNet from source, Tcl and Tk development headers are required (as told by WordNet build system). Hence I installed them by . Then I was able to successfully build and install WordNet (tried running command 'wnb' and searched some random terms in the thesaurus for which results got returned properly. Finally, I installed Artha from source ([http://sourceforge.net/projects/artha/files/artha/1.0.1/artha-1.0.1.tar.bz2/download](http://sourceforge.net/projects/artha/files/artha/1.0.1/artha-1.0.1.tar.bz2/download)). It worked fine the very first time; search returned results normally as it should.

I can see that you've installed Artha from source properly; but I'm skeptical of your WordNet installation. Can you please tell how you installed WordNet in your machine?

Thanks legends2k. I followed your instructions, but they didn't work, but 'cnf wnb' told me that there was now a 'wordnet' package. Also, I have some repositories (like packman) which is where I think I got the other wordnet packages from. Not really sure though. 

Opensuse handles repositories differently than Ubuntu and confuses me a bit.

But it is now working. Thanks again for the great app! :D

---

### Post by gvlists on 2010-04-18
This is exactly the tool I was looking for as I am out of internet when I am travelling. Gnome-dictionary is almost not usable for me then. May be it is a wordweb hangover.  The shortcut and notification feature of artha fits my requirement  better. Thanks again.

---

### Post by go_beep_yourself on 2010-04-21
Can Artha do Language to Other Language definitions and vise versa? That would be nice!

---

### Post by legends2k on 2010-04-21
**@gvlists:** Am glad it helps :)

**@go_beep_yourself:** No, it doesn't. Artha's primary goal is to be a very light thesaurus. I'm planning to make Artha work with more than one WordNet i.e. it works with the English WordNet now, but I want it to work with other language WordNets too; in fact, right now, any WordNet that follows English WordNet's format should work with Artha fine ~ so only integrations is something I'm trying to work on, but translations ~ nope. It would make it heavy.

---

### Post by theoryl on 2010-05-23
Thanks Legends2k for your awesome work! I really enjoy using your great app. I have one suggestion, which is to have a "history" that remembers the past queries. It will be useful for an English learner to remind himself of the unfamiliar words.

Thanks again!

---

### Post by legends2k on 2010-05-24
Thanks for the compliments theoryl. Even I've been wanting to do *Persistent History* for some time now, but pushed it to the back of the ToDo list in favour of other ones, but now it's moved from the *ToDo* list to User's *Wishlist*; so yes, in version next to the coming one you'll have it  :)

Attached is a sneak peek of the next release (M$ Windows version is imminent)!

---

### Post by theoryl on 2010-05-24
Thank you in advance, I'll look forward to it! Although of course I'm already a happy Artha user without the "history" feature. =)

---

### Post by kltpzyxm on 2010-05-27
Wow! Just wow! I never thought I'd come close to liking any app as much as WordWeb, but now, I can't stand to use WordWeb on Windows. Take a bow, legends2k. This is just an incredible program.

A couple of things:

1. I know you've included a hotkey editor, but I just can't seem to find it. The wiki says "press the hotkey button on the toolbar", but i don't see any hotkey button on the program's toolbar. I'm new to linux, so could anyone please give me a dummy's pointer to it? I'm using Ubuntu Lucid Lynx.

2. A feature request, if you're taking them: In WordWeb, I had gotten used to just clicking on a word (not highlighting it, just clicking on it) and hitting the hotkey to bring up the definition. Could the same functionality be brought to Artha?

Also, i'm with Mehr_o for the feature request to make the hotkey into a switch instead of the current "hotkey to bring it up, Esc to shut down" option.

---

### Post by legends2k on 2010-05-27
[SIZE=4][COLOR=Blue]**[Artha 1.0.2]("https://sourceforge.net/projects/artha/files/") released!**[/COLOR][/SIZE]

* Artha fully ported to Microsoft Windows ~ works on XP and above (both 32 & 64-bit)
* Notification turnaround should be a lot quicker
* Futile search notifications now show the searched word
* Lots of minor fixes

It's recommended to update to this release from now on :smile:

Please help me spread the word by suggesting your Windows friends to try [Artha for Windows]("http://sourceforge.net/projects/artha/files/artha/1.0.2/artha_1.0.2.0.exe/download"), which is a better option than WordWeb Pro ~ WordWeb (free) doesn't have regex based search and only the Pro version (not free) has it; while Artha, apart from having the regex feature, it has additional ones like notifications, detailed mode, etc., above all it's open and free!

---

### Post by Linuxforall on 2010-05-27
Is Artha supporting pronunciation yet via TTS files?

---

### Post by legends2k on 2010-05-27
**@kltpzyxm:** Thanks a lot for your kind words of appreciation. I'm glad that Artha is of use to you. Here goes your replies:

1. Hotkey editor feature was implemented in 1.0.0 ~ so it'll be available on that or later versions of Artha; while Lucid Lynx repository has only 0.9.1. So I recommend that you install it via the deb file provided @ Artha's Homepage -> [Download]("http://artha.sourceforge.net/wiki/index.php/Download") section.

2. I'll check it's feasibility first. If so, I'll surely implement it. Although I should say that it isn't the top priority one in ToDo right now; it's the pronunciation feature requested by so many learners ~ once it's done, I'll look into this.

3. As for making the hotkey a switch ~ yes, I've noted it down in my ToDo list, you'll have it in the next release :)

Hope it helps!

---

### Post by legends2k on 2010-05-27
**@Linuxforall:** I'm afraid, not yet. In the next release, textual phonetics will be displayed next to each word, since I've felt phonetics are the most proper way to learn the pronunciation properly; TTS is not human-like and is sometimes confusing. Although, it'll be implemented after phonetics option; probably both together in the next release. Sorry, if you've been expecting it dearly :(

---

### Post by Linuxforall on 2010-05-27
> **legends2k said:**
> **@Linuxforall:** I'm afraid, not yet. In the next release, textual phonetics will be displayed next to each word, since I've felt phonetics are the most proper way to learn the pronunciation properly; TTS is not human-like and is sometimes confusing. Although, it'll be implemented after phonetics option; probably both together in the next release. Sorry, if you've been expecting it dearly :(

legends2k,

No issues really, keep up your good work. The TTS sometimes gives a fair amount of idea on how close one is to the correct word and it comes in handy then.

Also do consider a ppa for Artha, that way it would automatically update to latest edition when released and users don't have to hunt for it.

---

### Post by legends2k on 2010-05-27
**@Linuxforall**: Yeah, I should setup a PPA, it should be a lot helpful. Thanks for reminding me :)

---

### Post by Linuxforall on 2010-05-27
With death of Stardict, your work now is more important than ever.

---

### Post by legends2k on 2010-05-27
Startdict dead? I didn't know that. But hey, I tried [http://stardict.sourceforge.net/](http://stardict.sourceforge.net/) it seems to be normal?

Anyways, it's always sad to hear the death of an open-source project, the project's initial conceiver will feel bad more than anybody else :(

---

### Post by Linuxforall on 2010-05-27
Development stopped a year back, there is Goldendict but the interface isn't as functional. Now the onus is on you. Also most critical dictionaries have gone missing from Stardict servers, Moby Thesarus being an important one.

---

### Post by kltpzyxm on 2010-05-28
@legends2k Updated deb package worked perfectly, thanks :)

It's working smoothly and v1.2 seems to have much faster notification pop-ups than the 0.9 i was on. Great work!

---

### Post by yargy on 2010-06-17
Hey I think it would be great if you could save a definition list as well! I use artha a lot when I am reading Ebooks, to lookup words so I think it would be handy to be able to save a list of words I looked up for each book that I read.

Also another feature that I think would be great would be if Artha could be integrated with [http://www.thefreedictionary.com/](http://www.thefreedictionary.com/) and things like wikipedia and also if it supported Bablyon dictionaries! 

I really love Artha though and was thrilled to see a wordweb/bablyon replacement for linux. Thanks for everything!! Keep up the good work!!

---

### Post by sethupathy on 2010-06-18
Actually it is available in ubuntu software centre... :-)

---

### Post by Linuxforall on 2010-06-18
It is but I would rather have a ppa for getting latest one automatically.

---

### Post by meho_r on 2010-06-20
> **legends2k said:**
> **@Linuxforall:** I'm afraid, not yet. In the next release, textual phonetics will be displayed next to each word, since I've felt phonetics are the most proper way to learn the pronunciation properly; TTS is not human-like and is sometimes confusing. Although, it'll be implemented after phonetics option; probably both together in the next release. Sorry, if you've been expecting it dearly :(

This is a great news. Phonetics are essential indeed. I have two questions/suggestions, they may be "you-wish-too-much" stuff, but I'll still ask:

1. Is it possible to have hyphenation patterns for words, like [Merriam-Webster](http://www.merriam-webster.com/) dictionary?

2. Is it possible to link pronunciation of a word to some of online sources which have real speakers pronouncing the word, like [Dictionary.com](http://dictionary.reference.com/)?

Again, thanks for your effort, you've really made life easier for many of us. :)

---

### Post by uttam2707 on 2010-06-25
sir, if you make artha to show the past and past participle forms of the verbs also, it will be of more help. i know it is a thesaurus...even though...

---

### Post by pbenerjee on 2010-06-29
Shame that I got to know about Artha only yesterday although it seems to be around for fairly long time.
I think enough has been rightly said about this great application. Its robustness, clean interface and hot key feature makes it an ideal candidate for being default dictionary in most distros. 

Seriously, show me a better one. I think the default dictionary that came with GNOME applications menu is  a crap (sorry to developers of that application). Artha should be immediately elevated to default dictionary item in main menu. Offcourse we ( me and wife) did it on our laptops.

I want to autostart Artha in Lucid Lynx. Which is the script/program I need to call ?

---

### Post by pbenerjee on 2010-06-29
Hi, I got it myself. That was very simple.
From Main menu->System->Prefereces->Startup Applications
Click 'Add' then the command is artha

It rocks :guitar:

---

### Post by nomnex on 2010-07-01
legends2k, congratulation for this app. I found reference to Artha  on another thread about off-line dictionaries.

I would too welcome a PPA, and a word pronunciation feature.

a side-note reading the GUI:

- I would replace the star icon by the dictionary icon (star is commonly associated with the bookmark feature) or any other icon.

- Isn't there another exit button than this ugly red (qt look like) icon?

- an option to reduce the icon size (big, medium, small - no icon and some menus) would be welcome, the icons are a bit invasive one a small display.

But never mind, these are little details anyway.

---

### Post by legends2k on 2010-07-01
**@nomex:** Except for Artha's "open-book" dictionary icon, none other icons are packed with it i.e. they're taken from the users machine. Icons for QUIT, ABOUT, NOTIFY, etc. are stock icons used from the user's machine and are not pre-packed and shipped. Change your icon theme and you'll see them changed in your Artha window too. Revert in case you have confusions.

**@pbenerjee:** Thanks for the compliments, glad you like it :)

**@uttam2707:** That is a bit far fetched I guess, yet I'll add it to user's wish list.

**@meho_r:** I'm thinking of getting the pronunciation data from the English Wiktionary site, since it's the only database, I know of, that has pronunciation which is free to use, copy and redistribute. I'll see what I can do about the hyphenation pattern, it should be possible. And linking it to an on-line dict. site to have original pronunciation audio file is easy.

**@yargy:** I've noted down your request in saving word look up history/ Will be there in the next release. Although integrating Artha with on-line sites is not a short term goal, it's already there in the long term goals.

Pronunciation, hyphenation, persistent work look up history (savable to a file as well) and setting up a PPA are the prime concerns of the forth coming release, I'm yet to work on it since I'm a bit caught up personally and professionally too; however, I'll start working on it in a few days.

Hope it helps guys :)

---

### Post by nomnex on 2010-07-01
legends2k, good point regarding the icons. what about an option "Default size" | "Small size" in the widget toolkit? maybe other could tell?

I usually keep the GUI open with the option "always on top" when I look up for definitions. My screen size is small and the default title bar + the icons of Artha eat up quite a lot of space.

a way to minimize the GUI would come in handy. My reasoning is the pop-up windows is nice feature, but the information is a little sparse. "always on top" and moving the GUI over a text is a better option when I need to learn some definitions.

---

### Post by legends2k on 2010-07-03
May I know what is the machine you're using nomnex? Is it desktop or is it a mobile like Nokia N900 (Maemo)? Also minimizing, on a normal desktop machine should make Artha get iconified in the system tray area.

As for the toolbar icons display settings, it's also not part of Artha, but system settings controlled. If you want smaller ones or you what only text and not the icons, etc. go to **System -> Preferences -> Appearances**. In that choose *Interface* tab. Change the settings in the drop down combo **Toolbar button labels**.

Hope it helps :)

---

### Post by nomnex on 2010-07-03
The smaller machine is a Panasonic Let's note notebook CF-R9K 10' LCD, resolution 1024x768.

[http://panasonic.jp/pc/products/r9k/index.html](http://panasonic.jp/pc/products/r9k/index.html)

The icon in the taskbar is nice, but the information available in the pop-up window is limited. A system wide change is not a convenient solution either.

Some GUI configurations to have a bar minimum window (e.g.  icon, or/and title bar enabled/disabled) would be helpful when needing the full Artha features (i.e. having the Artha window open over a text file or a html page.) on a small LCD display.

---

### Post by whollycow on 2010-07-05
Very useful!  Thanks!  

1) Any news on a ppa?  
2) What about the ability to hide the icon in the notification area?  It would be nice if it could run invisibly)
3) Any progress on integrating other languages?  I'd like to brush up on my Italian...

---

### Post by brallan on 2010-07-06
> **pbenerjee said:**
>  Artha should be immediately elevated to default dictionary item in main menu.?

You should know that the dictionaries and the programs are different. Artha (just like its proprietary equivalent Wordweb) is a front-end for Wordnet, but the development of wordnets in languages other than English (i don't know of a single one) is slow and inadecuate to make them useful for a multilingual distro like ubuntu. So unless many other-language wordnets were to be developed, this would be very hard to see at any point in the future.

But lets dream about that and meanwhile pass Artha on to all our english-speaking friends. (windows, too!) The more people who see how useful wordnet is, the more of us will be dreaming of other language wordnet projects!

---

### Post by brallan on 2010-07-06
so happy to see that the windows version works, as i have been forced while traveling to use a friend's netbook with 7. I also updated the info on:

[http://alternativeto.net/desktop/artha](http://alternativeto.net/desktop/artha)

let me know if anything needs changing.

---

### Post by quadraphenia on 2010-07-15
:) Thank you for the share! 
Makes life so much easier :KS:KS:KS:KS:KS

---

### Post by shan23 on 2010-10-18
Well - I know I'm a LOT late in congratulating the author for such a good and much-needed app - but the plus side is, all the suggestions are now implemented AFAIK, so I can just sit back and use it with my spanking new install of Ubuntu 10.10 !! It is killer apps like these that would make users switch over from Windows in future...

---

### Post by brallan on 2010-11-04
Any reason not to include the regular expressions search capaility (wordnet-sense-index) by default?

This is one of the best features, and will convince many wordweb pro users to consider a freeware alternative or to help them consider migrating to linux, especially in crossword puzzle circles.

thanks for all your hard work, legends2k!

> **legends2k said:**
> **@[sarthorks]("http://ubuntuforums.org/member.php?u=612179"):** May I know how you installed Artha? What distro are you using? If it's Ubuntu, Artha's direct dependency is WordNet (package: *wordnet*); there's one more package by the name ***wordnet-sense-index***, this is not a must-have dependency to run Artha but a recommended-to-have package which will enable the regex based search feature of Artha. If that is not installed, *index.sense* file will not be present in the path the error says about. If it's installed, you can make the regex-based search (*, ?, etc.). To install it in Ubuntu/Debian:



Try this, it should fix it; if not you can always ping me regd. the same. Hope it helps :)

**@[meho_r]("http://ubuntuforums.org/member.php?u=281491"):** I've made a note of it, mate :) I'll see how I can fit it in.

---

### Post by legends2k on 2010-11-24
Sorry for tha late reply guys, have been *really* caught up with  many other things in life. In the coming weeks, I'm going to work on  Artha :) I'm making a list of ToDo's for this (next post). If you wanna  add more to it, please do.

**@brallan:** I do agree, regex search is one of the best features in Artha. In Debian, for creating deb package rules, there's **Depends**  field where, only what is bare minimum necessary for the package to run  should be added; since wordnet-sense-index is like a plug-in for Artha  (i.e. Artha will work even wtihout it, but if found, it'll allow regex  searches too) the Debian sponsor who allowed it inside Debian project  said it shoulnd't be added, ideally. Hence I added it to the **Recommends** field; but I guess it can be added to Depends since it makes it the main differentiator.

**@brallan & ****pbenerjee**: WordNets for other  languages are starting to get developed, I've seen some :D Once they're  mature (i.e. they're inline with Eng. thesaurus protocols), I can try  wrapping them up with Artha, which would unify all language WordNet  usages into one simple app :)

**@whollycow:** In the coming release PPA and status icon invisible features will be done!

**@nomnex:** In the coming release, I'll try giving the feature of  enabling/disabling the title bar, icons, etc. for smaller devices, where  the job can be done by shortcuts.

---

### Post by legends2k on 2010-11-24
ToDo list for the forthcoming release:

0. Phonetics, Hyphenation and Pronunciation
1. Bookmarks
2. Persistant and save-able history
3. Icon and Title bars (chrome) enable/disable or make smaller
4. Invisible status bar icon
5. Ctrl W/Q for Quit (aliging with Linux philosophy)
6. Starting a PPA
7. Getting the latest version in to Debian and thereby Ubuntu

---

### Post by vamsi_spr on 2010-12-28
> **legends2k said:**
> ToDo list for the forthcoming release:

0. Phonetics, Hyphenation and Pronunciation
1. Bookmarks
2. Persistant and save-able history
3. Icon and Title bars (chrome) enable/disable or make smaller
4. Invisible status bar icon
5. Ctrl W/Q for Quit (aliging with Linux philosophy)
6. Starting a PPA
7. Getting the latest version in to Debian and thereby Ubuntu

Thumbs up bro ...looking forward for this release , tired of emulating wordweb in wine ..really in need of all these features !!

---

### Post by coldraven on 2011-03-22
Hi legends2k, Thanks for Artha, it's extremely handy.
Just to inform you that none of the images will enlarge at 
[http://artha.sourceforge.net/wiki/index.php/Home](http://artha.sourceforge.net/wiki/index.php/Home)
Keep up the good work :)

---

### Post by spinifex on 2011-04-30
Another pat on the back for you legends2k. 

I have been using WordWeb in XP for years and, to be honest, it was the dealbreaker when it came to using Linux. 

Really, this is fantastic. 

I have been stuffing around with WordWeb in Wine, it (WordWeb) throwing up errors here and there, and basically just not working seamlessly, and came across your App whilst troubleshooting. 

Artha is excellent.  I love it!  I really do.  Thankyou for building this. It has saved me much heartache.  

FYI, am actually using Fedora 14-64 and got it straight from the repo but wordnet-sense-index **isn't** in the Fedora repo so not sure if I have all the Artha features enabled.  

I can't wait for future builds as you increase the feature set. But, hey, it already does what I need. 

Really good work. Well done!

---

### Post by marl30 on 2011-04-30
I've been using this dictionary ever since I found it. It's quite handy, especially with the ctr+alt+w shortcut for quickly looking up highlighted words. It works well with OOo/LO.

---

### Post by legends2k on 2011-05-01
**@spinifwex:** From what I remember last, Fedora repos doesn't have wordnet-sense-index separately, it's already part of the wordnet package! So I think you already have the full working Artha installed :) Thanks for the appriciation, but I've to admit that I've not updated Artha for quite a long time now, it's high-time that I should really have to dive deep into it.

**@marl30:** Thanks man.

---

### Post by Copper Bezel on 2011-05-01
I hadn't seen this before. Sweet tool; I've been wondering if something like this existed. I love the regular expression searches! = ) 

(I wonder if an option to disable the system tray icon might be offered? If Artha's bound to a keystroke, it doesn't seem to be needed, and even if it's set to Notify, running the app again loads the full UI.)

Edit: Mistyped something.

---

### Post by spinifex on 2011-05-02
> **legends2k said:**
> **@spinifwex:** From what I remember last, Fedora repos doesn't have wordnet-sense-index separately, it's already part of the wordnet package! So I think you already have the full working Artha installed :) Thanks for the appriciation, but I've to admit that I've not updated Artha for quite a long time now, it's high-time that I should really have to dive deep into it.

**@marl30:** Thanks man.

Yeah, Artha is working.  I don't think its missing anything.  I do have WordWeb still installed, but it is buggy. 

PLEASE PLEASE do some more work on Artha.  I can't wait.  I love it.  WordWeb, as I said before, (and this sounds insane) is what kept me bound to XP for several years.  All the other Linux Dictionaries just don't cut it. Now, Artha isn't 'perfect' BUT its Bl**dy good ... and I have it running right now.  

Would you consider taking 'feature requests'????? Seriously, this is a showcase piece of software you have here.   I would even pay you for it (or donate) if you added some more features and prettied it up. I have PAID over $200 bucks for WordWeb and updates etc since Version 2 years ago.  WordWeb is VERY usable and intuitive. I do love it. But running it through Wine is just too buggy.  Artha just WORKS!..... and works well.. 

Seriously, I encourage you to expand the feature set.   I have come across a few words not in Artha that are in WordWeb so not sure about the database WordWeb uses. 

Also, I like the Nouns, Verbs, Adjectives etc buttons in WordWeb. That would be something to consider as it ads to the cross functionality. 

BIGGIE of a request, some how integrate it into OpenOffice spell check????   WOOOOHOOOOO.... yeah!!!!  now your talking... but I am totally out of my depth there.... 

One thing with Artha I am trying to get use to and that is Tabing through definitions, synonyms etc. It is a bit more drawn out. But, I still love it. 

Its the best Linux Thesaurus I've used so far.  Please keep it up...  :)

---

### Post by silent_shade on 2011-05-04
thanks! lovely piece of software. since i cannot work around some weird problem with dictd server on my machine, Artha IS oh, so very welcome

---

### Post by CentralCaFan on 2011-05-11
Problem with fonts rendering for description paragraph in entries with Artha. Instead what displays are consecutive square boxes where if I copy and paste into my browser search area the text from the description area for the entry displays.

I have KDE (version installed with) Kubuntu 11.04.

I like Artha, prefer it to KThesaurus for one because KThesaurus would require part or all of KOffice which I don't use. 

(I've searched for a bit in various places for an answer, Googled, here on this forum site and on the Artha application page, but found no solution yet. Should this have been a separate post?)

---

### Post by spinifex on 2011-06-27
Interested in Keyboard Shortcuts for Artha. 

Are there any?   I haven't been able to locate any. 

Keyboard Shortcuts would be a boon for Artha's usability. 

When will 1.0.2 be updated in the Redhat/Fedora Repo?

---

### Post by nomnex on 2011-07-06
[https://admin.fedoraproject.org/updates/artha-1.0.2-1.fc14?_csrf_token=c53962164183b33e8c23ba434778027d6b5345e2](https://admin.fedoraproject.org/updates/artha-1.0.2-1.fc14?_csrf_token=c53962164183b33e8c23ba434778027d6b5345e2)

it's there.

---

### Post by twipley on 2011-07-15
Hello legends2k, hope you are going well.

Version 3.1 is now out, how cool is that?
[http://wordnetweb.princeton.edu/perl/webwn](http://wordnetweb.princeton.edu/perl/webwn)

I think that the WordNet project is a very important one. Language is just everything, in this world of ours.

I have given some feedback the other night, see:
[https://answers.launchpad.net/artha/+question/163342](https://answers.launchpad.net/artha/+question/163342)

Please forgive the "ugliness" mentions. Overall, this is an application I would recommend any day to any one.

Peace out,
twipley

---

### Post by rkanth on 2011-08-06
Hi. Thanks for a very useful software.
Is there any way I can add Artha's functionality to right-click menu? like, I highlight a word and right-click it to choose something like 'look up with artha'?
2. Is there a way to have only one shortcut key-combo for Artha? It changes between ctrl+alt+q to ctrl+alt+a to ctrl+alt+w etc. everytime I launch the program.
Thanks

---

### Post by legends2k on 2011-08-07
Thanks for the comments. As for your questions:

i. Right now the right-click functionality is not there. The hot key/shortcut key feature is for this purpose only.
ii. The shortcut key you've set for Artha should stay the same forever unless you change it. If it changes without your intervention, then it's a bug. Can you please tell me what you've done? Or the steps to reproduce this bug.

---

### Post by anieruddha on 2011-08-09
simple interface. do what it suppose to do. Great and keep it up. 
Thanks just downloaded and installed it. 
Will use regularly

Why u name "artha" because of word  "[COLOR=#000000][FONT=Arial]&#2309;&#2352;&#2381;&#2341;"[/FONT][/COLOR]

---

### Post by Kushal Sejwal on 2011-08-31
Hi Sundaram,

I have been eagerly awaiting for the pronunciation feature which I see in the "sneak peaks of the next release"

Any updates, when we should expect the next version?

Thanks,

Kushal

---

### Post by legends2k on 2011-09-01
@Kushal: The problem of Artha with pronunciation getting delayed this much is that there're not any open source phonetic database available. Even if text to speech engines are available, it's customized to a specific region (en_GB, en_US, en_IN, etc.), while Artha depends on WordNet which is region agnostic, hence tying it up with a specific region's pronunciation would be killing of it's generic behaviour. Even libhypen which provides hypenates (breaks down) complex words into syllables for easy pronunciation has the same issue. Thus the delay :(

---

### Post by sffvba[e0rt on 2011-09-01
Cool... didn't know there was an Artha thread... just like to say I think it is an awesome application :)


404

---

### Post by Docaltmed on 2011-09-01
Artha is simply the Best Program I Have Ever Used. I use it multiple times daily. 

Thank you!!!!

---

### Post by tumerictj on 2011-09-09
I love Artha and am so thankful that you made such a practical and crucial contribution to the open-source community.  

My one complaint is that I can't figure out how to increase the font size.

Thank you.

---

### Post by rojaasensei on 2011-09-09
I just discovered Artha last week.  It's a great addition to my Xubuntu desktop.

---

### Post by anshulfy on 2011-10-16
I was looking for a similar app........thanks for the info :)

---

### Post by altocumulus on 2012-02-05
I've just discovered artha as an alternative to wordweb, and it's an interesting app. However, in contrast to wordweb, artha does not provide the phonetic/syllable info of words....Would that be a possible addon sometime ?;)

---

### Post by legends2k on 2012-02-06
@altocumulus: Thanks for your compliments; as for the phonetic/syllable info, if you follow up this thread, you'll see that I couldn't locate a single open-source/GPL'd English phonetic database that is up to the mark to be used; hence this state.

It would be much appreciated if someone point me to such a free, open-source English phonetic database.

---

### Post by twipley on 2012-02-15
Just as a curiosity, and feelings on how it seems to be taking such a long time for the new version database files to be released?

Also, I realize I have not been given any feedback on both of my ideas. Perhaps, re-reading it again after such a long time, I had been unjustly harsh in my wording choice. If this is the case, then let me apologize, and restate everything anew.

Let this turn into a brainstorm, then! ;)

(1) is it just me, or word tags such as "rare" or "common" do not seem to fit well, in esthetical terms, in the overall interface? Or perhaps are they part of the official database files, and that is the reason for their inclusion? If this is the case, I would really like to be able to disable those mentions through a setting toggle, though;

(2) WordWeb (well, I guess most reading this thread are already familiar with it) had a feature through which one could click on chosen "meaning numbers," which would then produce synonym highlighting for that specific word meaning. I think that might be a nice addition to Artha in the future, although I am aware that the reverse feature, which is returning through highlighting the specific meaning number following a click on a chosen synonym, is already implemented and working well.

Hope those criticisms are now a little more constructive. Let us contribute for the better to this flowering open-source world, then! :)

---

### Post by bobchillaxed on 2012-03-17
Is Artha still being updated?

---

### Post by sunfromhere on 2012-04-26
I just recently discovered this program and it's great.
However, notifications don't work in Ubuntu 12.04 (I have libnotify installed).
Anyone got it going?

---

### Post by go_beep_yourself on 2012-05-09
For those of you that like Text To Speech (TTS) Software, this is a new one and best one hands down I've found for linux.

[http://linuxinnovations.blogspot.com/2012/05/jspeak-ultimate-in-linux-text-to-speach.html](http://linuxinnovations.blogspot.com/2012/05/jspeak-ultimate-in-linux-text-to-speach.html)

---

### Post by squidlips89 on 2012-06-11
Is there a way to add your own words and definitions into Artha? That would be completely amazing! :guitar:

---

### Post by twipley on 2012-08-27
> **squidlips89 said:**
> Is there a way to add your own words and definitions into Artha? That would be completely amazing! :guitar:

I always have been seeing Artha as a GUI to WordNet, and nothing more, though.

A yummy GUI though, indeed! (A sure alternative to the official WordNet-Browser GUI.)

---

### Post by legends2k on 2012-10-16
I've finally gotten enough time to release a new version of Artha, this version has the following in it:


[LIST]
[*] [One-the-fly search/filtering]("http://artha.sourceforge.net/wiki/index.php/Features#On-the-fly_Search") of wordnet terms as you type
[*] [Lookup history made persistant]("http://artha.sourceforge.net/wiki/index.php/Features#Persistant_History"); can be cleared or stored for user's reference
[*] Status/tray icon display now made optional
[*] Familiarity/Polysemy count display now made optional
[*] Show window on startup made optional
[*] Lots of bug fixes
[/LIST]
[IMG]http://artha.sourceforge.net/wiki/images/0/09/Autocomplete.png[/IMG]


Apologies for not yet implementing the most sought-after feature of "Pronunciation", I surely hope that it will be in next release.

---

### Post by stinkeye on 2012-10-16
Thank you very much for this update, specifically the reimplementation of
the notifications.
One of my first installed applications.
Do you have a way to donate or somewhere you would like a donation sent?

---

### Post by twipley on 2012-11-18
legends2k: wow very nice, i'm glad i've checked this topic back.

download link: [http://sourceforge.net/projects/artha/files/artha/](http://sourceforge.net/projects/artha/files/artha/)

the new interface feels *great*! :)

does 1.0.3 include the latest, 3.1 wordnet database files?
-- [http://wordnetcode.princeton.edu/wn3.1.dict.tar.gz](http://wordnetcode.princeton.edu/wn3.1.dict.tar.gz)

---

### Post by twipley on 2012-11-18
Just some feature requests in case you would be craving for them. :)


It would be nice to be able to highlight particular senses directly by clicking on the margin numbers. WordWeb (which this application replaces) does this, and it is quite convenient. One can that way see, in a fast manner, which relatives (e.g., synonyms) stand for each sense.

For example, having looked for "great," one could click on its second meaning, "of major significance or importance," and then the "outstanding" synonym would get highlighted, which is linked to that particular sense.

Of course, the converse feature works (returning sense highlighting through selecting specific relatives), although it might not be as convenient in all cases.


Another feature suggestion would be to link a combo such as "alt+left" to the back button, and "alt+right" to the next-search-term one, which would permit increased comfort of keyboard navigation.

Nice again to see the app being improved. Kudos. ;)

---

### Post by Beardedturtle on 2012-11-18
sudo gdebi artha_1.0.2-1_amd64.deb 

When i put this command in  it will say not a valid command.

Edit I got it to install via the software center

---

### Post by ottadini on 2012-12-09
Are there any command-line options? 

I would like to call artha from another programme, by supplying a selected word to artha and have it return suggestions.

---

### Post by twipley on 2012-12-16
I feel like I am monopolizing the topic. :oops:

Take it as a compliment towards software-greatness recognition, though. :)

I was wondering the reason no WordNet GUI to date uses the 3.1 database. Is it because the guys over at Princeton have not yet published the necessary files for 3.1 to be available offline? (Just curious.)

---

### Post by twipley on 2012-12-20
Bug report: I have installed this on some Windows-XP machines, although upon moving its window Artha freezes and then crashes (a minute or so later).

The workaround is not to move the window, or to maximize it on start, so as to prevent it being movable. The problem remained even using custom settings. Take note that the freeze are happening on Windows XP, although this is a custom operating-system built of mine that I have installed here and there. However, I have never seen an incompatibleness between this distro and custom software, except this one.

Cheers!

---

### Post by patrick-gelin on 2013-12-18
Thank you for this excellent software ! I would like to know how you edit the content of the thesaurus ? My idea where to edit content with my own french words for professionnal needs. Is-it possible ? Thank you for your response.

---

### Post by rewyllys on 2013-12-22
To Legends2k:
Many thanks for Artha!  I've used it for several years, and find it invaluable.

---

### Post by LillyDragon on 2013-12-25
I have to chime in myself to praise Artha! It has been my go-to thesaurus and dictionary for everything for the past two years, on both Windows and Linux. I can't remember the last time I visited Thesaurus.com! (It loaded slowly anyway. =P) Artha has put any new or barely used word I want to know instantaneously at my fingertips, I love it.

---

