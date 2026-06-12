---
title: "Three great structural problems about Ubuntu and Debian-like distros"
date: 2007-06-11
forum: Testimonials &amp; Experiences
---

### Post by eldino on 2007-06-11
Hi all,
I'd like to post some opinions about Ubuntu (and Linux in general) but trust me, I don't want to flame, but just search some answers to some questions, if they exist. I'd like to read some stuff from some devs and some commercial-involved people as well, not just fanboys. Fanboying is cool but not so good by a pratical point of view :-) Ok, let's start.

Some weeks ago I got by mail the nice Ubuntu 7.04 cd from Canonical. Nowadays it's so fashion talking about Ubuntu, testing Ubuntu, installing Ubuntu etc that I decided to give it a try. I used linux for 2 years (2002-2004), then I quit because there were more problems than advantages into using it, and I was using the most user-experience-focused distro available at that time (Mandrake 9.2), or at least the best between those I tested (Debian 3.0 Woody (shipping with preistoric software on it), Red Hat and some derivates (let me decide the packages I want to install, b1tch!), Gentoo (it needed some geological eras for a complete install!), Slackware, Knoppix and tons of other live cds). 
I put the cd inside my Toshiba M30 laptop, the nice graphical boot appears, fine. Gnome loads: "Nice orange theme" I think. I start experimenting with programs, menus, icons etc. Everything is "inspired" by Mac OS X but there are some original ideas as well (like the "Enlarge icon" thing for the desktop icons). "Ok, everything seems working" and I install it. The partitioning step is a bit buggy (if you choose an option and then go back, all the text formatting messes up) and it's not as cool&easy as in Mandriva, when you really have control over things. Btw it works. "Now I have 25Gb for Windows and 12 for Ubuntu! Well done!", I say (my disk is 40GB). The importing-user-image-from-Windows is very nice as well. Ok I restart the machine and I boot into Ubuntu. 
Let's list what I disliked :-) I'd like to say that some points are not strictly Ubuntu-related, but I write theme here because behind Ubuntu there is a commercial company that -I presume- have interest to make a commercial-level OS (or sort of). Corollary: more quality we give = more possibilities to get back the invested money.

1) The italian localization is in the reality a 80%english+20%italian localization.
I have no problem using english-localized apps, but at least the operating system and the browser must be localized, don't they? How many Kbs are all the localizations? 100Kb/each? And don't tell me there is no space for them on the cd, because you lie. And don't tell me "localizing teams work slowly and they have not completed all the translation work in time". I'm a Joe User, I don't care about your excuses. The volunteers don't work? Pay somebody to do the translations for them. I'm a Joe user, I want the OS in my language to get a good initial opinion of it, I don't think I'm asking so much. Imagine Apple or Microsoft shipping their OSes partially translated..WTF! People'd piss them off! "But Ubuntu is free".. True, but free doesn't mean unprofessional or crappy. Or if you mean that, you are wrong. Stop using the "cost=0$" variable as a shield for the crappyness. If you want to really compete with commercial OSes, you have to offer the same basic functions and the right localizations. I hope you will start considering this as a priority.

2) There are no codecs to listen a simple mp3 from my Windows partition or to watch a dvd movie. This is just absurd. You could tell me "Fire up Automatix or Synaptic and get all of them in a breeze". Wrong. That's not the right approach. 
a) I have not internet connection at home, and many people are in my same situation. But, when I format and install Windows XP on my machine I have nearly-everything out-of
the-box, without any need to waste additional time and money. Same thing when I install Mac OS X Tiger on my Mac (except for the fact Apple nicely provides for free more software than Microsoft, like the iLife suite for example). Imagine to buy a car provided out-of-the-box without tires but just with the address of a nice mechanic who will give you the tires for free when you will go to his shop, located somewhere. Is it frustating, doesn't it?
b) I don't care about the fact you fear to be sued by some license-owner and then you don't bundle codecs into your product. Really, I don't care. If you want to push me, a Joe user, to appreciate  your product you may satisfy my basic user needs - and nowadays the ability to listen a mp3 is considered a basic need, doesn't it?
Being a commercial reality involved into spreading a Linux distro without codecs is like being a car brand (ex. Mercedes) and selling cars without Goodyear or Bridgestone tires, because you fear to be sued by Goodyear or Bridgestone since you didn't pay a buck for their licensing, and pretend to make money with it. WTF! Licenses cost? Pay for them and increase the value of you product. "Free as in freedom" is a good philosophy, but in the reality is not always possible to apply it. Stop dreaming. 
98% of people listen to their music saved in mp3 format, so you have two ways to attract them with your product: push'em to convert, use, rip, love, share music in the better Ogg Vorbis format (better by the licensing and audio-quality points of view) or provide them a way to listen out-of-the-box their mp3s. The first one seems really impossible to happen to me. 

3) Ubuntu's way to install stuff is wrong. But that's is not its fault, but it depends by the fact it derives from Debian, the less user-oriented distro ever, great for programmers, nerds and people who likes to waste time babysitting their computers and saturate their DSL bandwidths every time they mess up things and need to reinstall all the software again. Same thing happen to the users of many other distros. Let me explain why. 
As I said, I have no internet connection at home, so it's nearly impossible to install stuff on my new, shiny Ubuntu installation. Ok, you can download the .deb packages with another computer/OS, save them on a pen drive, bring them at home and install them from Terminal, typing manually the following lines:

cd /folder/in/which/you/downloaded/your/deb/packages
dpkg -i *.deb

or 

"configure-make-make install" if the software you need is only distributed as source files inside a nice tar.gz package. Sure you can do all this procedure. It doesn't look exactly user-friendly but it can be done. Ok, try to do it with Amarok, for example. Go to Ubuntu Packages site (that is well done), type "Amarok" in the search box, download it together with all the dependencies it needs (they are nicely listed on the same page of the app) and after like 30 minutes of work you have everything you need, maybe. You go back to home, type in Terminal the right commands and you get a bunch of errors, complaining that you miss the libxxxx or the libyyyyy that respectively need the libzzzzzz installed for proceed. WTF! To install an app all this stuff???? You are kidding me, doesn't you?
When I need an app for my Mac, I just open macupdate.com from a friend's computer or an university computer or even from my PSP (using some nice wifi hotspots), I type the app I need in the search box, I click "download" and I have everything I need inside a nice .dmg file. In the rarely cases the application needs some additional libraries or software (read: max 2-3 additional downloads), they are nicely linked on the application page: "Application X need Y software to work. Click here to get it, it's freeware". Same thing happens when I need a Windows app. 
Using the Mac or Windows approach, you are 99% sure that when you come back to your home computer with the .dmg or the .exe file inside your pendrive, you can surely install the software you need without any problem in 3 steps, and start immediately to use it. Using the Linux approach you are sure you will need 3-4 additional days of browsing and dowloading to get stuff done. More time wasted, more frustation, less productivity.
The Mac or Windows approach gives you the freedom to choose how get your applications, Linux doesn't. With Linux you are dependant from a repository. Do you really like that way? I don't. Mandriva solved partially the problem, giving you a lot of apps (and also all the codecs, except the one for video-dvds) inside its installation dvd. Ok urpmi is proprietary, but who cares? you don't spend a buck for it, it works and it provides nice descriptions, mostly localized as well, for every package. Mandriva is the only Linux-involved company I know that has designed a nice bussiness over Linux. Stuff is good enought if you'd spend money for it. And I admit, I'd spend money for Mandriva PowerPack. I actually run Mandriva 2007.1 On Mandriva, installing Amarok and make it working inside Gnome without wasting time into babysitting procedures is easy: just select, click and install.
What I'm talking about is not that Mandriva is better than Ubuntu or other distro, but it's that the Linux way of installing stuff must be re-designed. Software may be provided in a single, big package, that can run on all the distros and on all the architectures in 2 clicks. Like Apple does with Universal Binaries. 
There is no sense to have the same stuff packaged singularly for Debian, for Ubuntu, for Mandriva, etc.. they are all Linux, they have same libraries, same kernel etc, so stop doing single package but bundle everything inside a single .linux (or .whatever)package.  Next, every distro have to include every library, to satisfy every dependency without pain.
Finally, setups files have to be like "Next-Next-Finish" .exe setup files or simpler (like Apple's "drag .app into Applications folder. Done." way).
When all those points will be satisfied, Linux will start to be an alternative to commercial OSes, not just something to play with or experiments. Programmers and geeks are maybe 3% of the market. Pc-babysitters are 7%. The rest is made by Joe users. I hope it will be your priority to point to that 90%.

If I missed something, tell me. 
If you are really sure that Joe user wants to have joy with Terminal for just installing an app, tell me. 
If you think Linux is ready for every desktop, don't tell me anything, but write some lines for Digg, somebody will trust you.

Just my 2 cents :-) too harsh uhuh?

eldino

ps. Please don't go off topic.I'm talking about desktop experience and Joe user productivity. I know that Linux rocks as server os, as render-farms os, as Google-backend os etc.. I'm talking about everyday use. In the everyday use of you car you don't open daily your engine, right? Ok. So why in the everyday use of your computer you have to open the Terminal to install an app? :-)

---

### Post by Kobalt on 2007-06-11
I think you just completely missed the Linux point of view of things. Espacially when you say such things as "Pay somebody to do the translations" or "Pay for [licences] and increase the value of you product"... 
There are many many good articles about what really IS Linux and its philosophy. I think you should read some of them, because you really don't seem to be agreeing with that. And if you don't, well then maybe Linux isn't for you. For my part I never claim that Linux is ready for everyone or that everyone is ready for Linux. You seem not to be : > setups files have to be like "Next-Next-Finish" .exe setup files

The same remark is true for Debian packaging system. Since you seem to know very few things about Debian I'd recommend you to also read a few things...
> they have same libraries, same kernel etc
This is indeed very untrue.

---

### Post by eldino on 2007-06-11
Hi Kobalt, thx for replying :-)

> **Kobalt said:**
> I think you just completely missed the Linux point of view of things. There are many many good articles about what really IS Linux and its philosophy. I think you should read some of them, because you really don't seem to be agreeing with that. 

I know a lot about the philosophy about Linux, open source, open knowdledge etc and I have like 80GB of nice Creative-Commons/Netlabel music. I bought 2 books by Stallman as well, instead of downloading them, and I buy every month 2 Linux magazines. What I don't agree is the hypocrisy behind this "philosopy". In a world full of proprietary stuff you can't pretend to be a serious alternative to commercial OSes and rest linked striclty to the open source policy. Hypocrisy like "Ok, we don't bundle mp3 codecs in out distro, but if you need them, get them here: [link]" WTF! If you provide a way to manage proprietary stuff, you admit its value and importance and you f*ck off your philosophy. 

> And if you don't, well then maybe Linux isn't for you. 

Probably yes. it's not for me and for the 90% of Joe users out there. :-)

> 
The same remark is true for Debian packaging system. Since you seem to know very few things about Debian I'd recommend you to also read a few things...


I will, thanx :-)

---

### Post by Kobalt on 2007-06-11
> WTF! If you provide a way to manage proprietary stuff, you admit its value and importance and you f*ck off your philosophy.
Let's first calm down and be polite, at least. 

MP3 support in Ubuntu isn't included by default because of legal purposes : 
*"Ubuntu is limited by patents and license restrictions in some countries, which make it illegal for Ubuntu to include them."*
I don't see the hypocrisy in saying we want an OpenSource OS respecting the [Free Software Philosophy]("http://www.ubuntu.com/ubuntu/philosophy") and not including proprietary formats... 

You complain about the Italian translation about Ubuntu : did you take part in it ? You can participate through the Launchpad really easily, to improve the OS or translate it if you like it and make it your very own, in some way. If you don't want to, then don't do it, but don't complain as well about the translations. That I'd call hypocrisy. 

You know at the end of the day, you're still very free to buy softwares you will use but not own, and not be part of this community...

---

### Post by tgalati4 on 2007-06-11
Check back in a few years and see how Ubuntu has matured.  Then compare it to Vista.

---

### Post by bitonw on 2007-06-11
this is my view on ubuntu... how open source is this ubuntu?

i made some nice sounds for start up and shutdown in OGG Vorbis format. do you think i can use them... no way!!!

it only excepts files in WAV format... this is making me very angry that people don't respect open source communitie. building a linux destro with only WAV format as start up sounds...

more info about WAV [http://en.wikipedia.org/wiki/WAV](http://en.wikipedia.org/wiki/WAV) and see it's from Mickey $oft (well and IBM too)

bt

---

### Post by weblordpepe on 2007-06-11
Now that's an oddity. I remember trying to set an ogg as a startup sound & running into the same trouble.

Anyway with regards to the original post:
You are able to go 'next next finish' with installation of software in Ubuntu. Repositories are optional.

And as far as 'not having an internet connection' then how do you aquire the latest DirectX or service packs or security patches etc while in UnnamedCommercialOS?

On a disc? Then use the same disc for your MP3 codec in Ubuntu.


Installing thing.tar.gz from the command line isn't geared towards end-users. At least that's my understanding. You could make a GUI for it, and that might be a good idea. But the command line is easier and quicker for certain tasks. Noobs and experts alike.

EDIT: One more thing. Ubuntu might ship without MP3 support, but Windows ships without an office productivity suite. I'm happy with that swap.

---

### Post by noenter1 on 2007-06-11
Lol... First of all, if you dont want to flame then dont. Second I admit it is hard to have all of Ubuntu's fetures(updates, apps, libs, ect...) and compatability(codecs) without an internet conection. Third its illegal to SHIP all those codecs WITH the OS without PAYING for them, however you can download them for free. Again internet connection reqierd. Yes Ubuntu is ready for average Joe with at least dsl or higher, and who is sick of microsoft, and/or having to pay more for apps and an OS then the actual computer. However I do admint that it isnt ready for those WITHOUT an internet conection.

---

### Post by weblordpepe on 2007-06-11
Yeah its a bit unnerving coming back to an Ubuntu system after a few weeks & seeing all the updates needed. It'd be nice to have em on disc.

---

### Post by eldino on 2007-06-11
> **Kobalt said:**
> 
You complain about the Italian translation about Ubuntu : did you take part in it ? You can participate through the Launchpad really easily, to improve the OS or translate it if you like it and make it your very own, in some way. If you don't want to, then don't do it, but don't complain as well about the translations. That I'd call hypocrisy.

Have I take part to it? I'm a Joe user interested to use this operating system, nothing more. It's like to go to Mercedes shop and complain about an engine problem, and being answered with "Did you contribute? No? So you can't complain!".. what kind of answer is this? :-) To use an operating system I have to contribute? If yes, my father will never use it :-) He has any time to contribute :)

---

### Post by timcredible on 2007-06-11
your rants are without merit - do a search and you'll find you can rsync any repo you want to an external drive and use it as your repos - i've copied repos for ubuntu and pclos to an external drive and used it to install tons of stuff on a relative's PC that has no internet access, it's not that big a deal.

---

### Post by eldino on 2007-06-11
> Check back in a few years and see how Ubuntu has matured. Then compare it to Vista.

Vista indeed sucks. Ubuntu is mature enought to compete with it. In fact, many Joe user friends installed Ubuntu on their laptop instead of VIsta.

> EDIT: One more thing. Ubuntu might ship without MP3 support, but Windows ships without an office productivity suite. I'm happy with that swap.

Nice point :-)

---

### Post by weblordpepe on 2007-06-11
;) Cheers

But in all fairness I think the first post in this thread represents an attitude which you will find out in the real world.

People who are coming from the Windows world will bark at the idea of contributing. By far the biggest bonus of Linux is that it is free. People on the whole are selfish.

Now personally, I get a real buzz out of knowing that my tiny wee suggestion made it into some software that is used on the other side of the planet. I get a buzz when an author of popular software replies to my email (Irfanview and Winamp come to mind).

But that doesn't compare to the buzz of knowing that the software in your OS is safe-guarded by the fact that both the developers and everyone else just don't want nastyness in the programs.

Commercial software, yeah sure. It has its place and I do see the point to it. But not in an OS. I think the -platforms- should be free an open.  Linux is alot like science, in that it self-regulates.

Not everyone is going to contribute.  Some people will bitch & moan. At least people have the -opportunity- to bitch & moan.

---

### Post by wolfen69 on 2007-06-11
btw, windows doesnt ship with mp3 or dvd codecs. so what's your point? i have to do alot more downloading after install with windows than linux.

---

### Post by Kobalt on 2007-06-11
> **eldino said:**
> Have I take part to it? I'm a Joe user interested to use this operating system, nothing more. It's like to go to Mercedes shop and complain about an engine problem, and being answered with "Did you contribute? No? So you can't complain!".. what kind of answer is this? :-) To use an operating system I have to contribute? If yes, my father will never use it :-) He has any time to contribute :)
When you'll be able to receive your Mercedes for free through Mercedes ShipIt! system please warn us :)
As I said, you missed the whole point of Linux.

---

### Post by Geekkit on 2007-06-11
> **wolfen69 said:**
> btw, windows doesnt ship with mp3 or dvd codecs. so what's your point? i have to do alot more downloading after install with windows than linux.

Yeah, this was what I was thinking of too. Also, specific video card drivers for tuning the specifics for your video card and monitor (usually with all sorts of gamma tweaks, color settings and the like), DIVX support, Quicktime support, Real Media support, Flash support, PDF support, and OGG support just to name a few.

I think this perception that Windows comes out of the box is nothing more than a mirage - brought on by some great marketing.

---

### Post by weblordpepe on 2007-06-11
Yeah I'd agree. People forget the troubles they've had with Windows. They just go 'ohh Linux didn't do xxx and yyy and zzz so it sucks!'....forgetting that Windows XP does next to nothing after a fresh install.

---

### Post by Al Fairclough on 2007-06-11
I guess that because I have done it so often, I forget the enormous volume of drivers, patches and maintenance software required just to run XP. Board drivers, video drivers, network setup (LAN) and the AV/Firewall must all be installed, whereas Ubuntu does all of these things (or doesn't need them) as a matter of course.

---

### Post by noenter1 on 2007-06-11
Not to metion the fact you need to restart you comp after you change network settings on windows. And just about every single update and app installation too.

---

### Post by Hendrixski on 2007-06-11
> **eldino said:**
> 
1) The italian localization is in the reality a 80%english+20%italian localization.
I have no problem using english-localized apps, but at least the operating system and the browser must be localized, don't they? How many Kbs are all the localizations? 100Kb/each? And don't tell me there is no space for them on the cd, because you lie. And don't tell me "localizing teams work slowly and they have not completed all the translation work in time". I'm a Joe User, I don't care about your excuses. The volunteers don't work? Pay somebody to do the translations for them. I'm a Joe user, I want the OS in my language to get a good initial opinion of it, I don't think I'm asking so much. Imagine Apple or Microsoft shipping their OSes partially translated..WTF! People'd piss them off! "But Ubuntu is free".. True, but free doesn't mean unprofessional or crappy. Or if you mean that, you are wrong. Stop using the "cost=0$" variable as a shield for the crappyness. If you want to really compete with commercial OSes, you have to offer the same basic functions and the right localizations. I hope you will start considering this as a priority.


You are welcome to help make the translations better instead of just complaining about it.
[https://translations.launchpad.net/](https://translations.launchpad.net/)

---

### Post by DFreeze on 2007-06-12
> **eldino said:**
> 
b) I don't care about the fact you fear to be sued by some license-owner and then you don't bundle codecs into your product. Really, I don't care. If you want to push me, a Joe user, to appreciate  your product you may satisfy my basic user needs - and nowadays the ability to listen a mp3 is considered a basic need, doesn't it?

I understand you don&#8217;t want to have to care, but any OS that wants to be legally fit for install globally HAS to do it. And the way Ubuntu solved it is maybe the least intrusive way of not having the codecs, but showing the way (and leaving responsibility with the user). Really, it ain&#8217;t pretty, but it&#8217;s the way it has to be, for now. You only have to care a few times (the times you click on a file Ubuntu can&#8217;t read yet).

> 
3) Ubuntu's way to install stuff is wrong. [&#8230;]
cd /folder/in/which/you/downloaded/your/deb/packages
dpkg -i *.deb
or 
"configure-make-make install" [&#8230;]

Finally, setups files have to be like "Next-Next-Finish" .exe setup files or simpler (like Apple's "drag .app into Applications folder. Done." way).

If you install your software like that then yes, I&#8217;m never gonna be able to teach my mother that. Have you doubleclicked a .deb file once? It &#8216;ll fire up gdebi, which will install the app graphically with a few &#8216;Next&#8217; buttons. Very sweet.

> 
When all those points will be satisfied, Linux will start to be an alternative to commercial OSes, not just something to play with or experiments. Programmers and geeks are maybe 3% of the market. Pc-babysitters are 7%. The rest is made by Joe users. I hope it will be your priority to point to that 90%.

I&#8217;m with you in that there&#8217;s a way to go before we have the polish some proprietary OS&#8217;es have. But as someone here said: you can help! I know that&#8217;s not what you had in mind, and you&#8217;re certainly not expected to, but you can. Your father doesn&#8217;t have to, you don&#8217;t have to, but you can&#8230; See, I wouldn&#8217;t help beef up software I shelled out a hundred bucks for. I paid for it, they should have their act together! But once you see what this OS is about, and all the work people do in their spare time to get this far, man I must say it itches me too. I can&#8217;t code well, but I&#8217;m good with words. I only lack the time to contribute (have to quit the band first), but if I had time, I would try to help as well. Not because they told me to, but because I want to.

Really, I see your point and I think the new users need to get adjusted to the whole OS as well as the ideas and ideologies. Maybe they won&#8217;t, well then they just have put up with it or leave. If they do, even slowly, I think they will relax and start to understand (and care).

---

### Post by eldino on 2007-06-12
> btw, windows doesnt ship with mp3 or dvd codecs. so what's your point? i have to do alot more downloading after install with windows than linux.

Here (italy) windows xp ships with windows media player bundled. and so you can play mp3s and dvds on it out of the box. it's not a so great player but it has the codecs.

> If you install your software like that then yes, I&#8217;m never gonna be able to teach my mother that. Have you doubleclicked a .deb file once? It &#8216;ll fire up gdebi, which will install the app graphically with a few &#8216;Next&#8217; buttons. Very sweet.

Double click on the .deb file gave me lot of "dependency xxx missing" error. that's why i went command-line way. Sources have to be compiled via Terminal btw so problem partially rests.

Thanx anybody for the nice replies btw :-) What I pointed rests mostly unanswered or someboody agrees with me, but I have some ideas more clear now :-) 
Thnx anyway guys!

---

### Post by HJam72 on 2007-06-13
> **eldino said:**
> Have I take part to it? I'm a Joe user interested to use this operating system, nothing more. **[SIZE="3"]It's like to go to Mercedes shop and complain about an engine problem, and being answered with "Did you contribute? No? So you can't complain!"[/SIZE]**.. what kind of answer is this? :-) To use an operating system I have to contribute? If yes, my father will never use it :-) He has any time to contribute :)



Hahahahahahahahaha!!!

Sorry for the interruption, but that's just hilarious. 

I think Ubuntu is ready to START taking over the desktop. If you have the right hardware, and it has drivers (or you can get them), and you have some know-how, it's ready. Most people are going to have to sort of make the switch as they replace the hardware, and momentum will increase. 

I know one thing: my next computer will be made for Linux.

---

### Post by chudder on 2008-05-10
> **weblordpepe said:**
> ;) Cheers

But in all fairness I think the first post in this thread represents an attitude which you will find out in the real world.

People who are coming from the Windows world will bark at the idea of contributing. By far the biggest bonus of Linux is that it is free. People on the whole are selfish.

Now personally, I get a real buzz out of knowing that my tiny wee suggestion made it into some software that is used on the other side of the planet. I get a buzz when an author of popular software replies to my email (Irfanview and Winamp come to mind).

But that doesn't compare to the buzz of knowing that the software in your OS is safe-guarded by the fact that both the developers and everyone else just don't want nastyness in the programs.

Commercial software, yeah sure. It has its place and I do see the point to it. But not in an OS. I think the -platforms- should be free an open.  Linux is alot like science, in that it self-regulates.

I think this says a lot here and is profoundly true.  Commercial software has it's place but with OSes it's become way too much control over the users.  

The most common reason I find people not wanting to switch to linux is it's not easy to learn and let's be honest coming from Windows (or even Mac) it's quite the learning curve, it took me 2 months just comfortably navigate in the OS.  

A lot of people just want a computer to get done what they need to get done and they don't really care about if it's done through a monopolistic and in my opinion an unethical company.  They just want it done and done easily.  Linux is not just an OS for most of its users but an idealogy and dare I say a religion.  I didn't just wake up and say I'm going to use Linux.  

I was first introduced to open source through firefox by two of my first roommates who would fiddle with Gnome distros of whatever kind way back when Ubuntu was just being conceived.  I had enormous problems with "Internet Exploder" and spyware and they introduced me to Firefox (then Firebird) after I got all that crap removed.  Then over time I got fed up with Office (I don't even remember what anymore) before you know it, I was using OpenOffice.  Then eventually I realized I just didn't like Windows at all.  A guy in major and myself were having a conversation about Linux and he showed me a live CD and I was very impressed.  I started with a dual boot with the help of my two first roommates.  Internet didn't work at all for the life of that laptop on the Ubuntu partition.  Otherwise I was impressed.  One thing I noticed immediately was that I didn't have to wear tight jeans that were difficult to walk in, in Ubuntu I could choose almost whatever program I wanted to do for a specific task.  Was it difficult to learn, yes.  But I liked the freedom even if it was at times tedious.  

The point I'm trying to make is that there are some people who will never convert to Linux or it will take miracles because it's just not what they want in computing.  There are people who are gradually realizing that there are viable alternatives to the big corporate software.  That's why it should be very easy for a user to try linux, when I was exploring it, I had no idea how to run a live CD, if some directions were printed on it and the average joe user could run it and see what is going on then they might try it out and just maybe in the end go to linux.  Many people don't like something until they try it.  Trying needs to be made easier and painless.

---

### Post by karellen on 2008-05-11
> **eldino said:**
> Hi all,
I'd like to post some opinions about Ubuntu (and Linux in general) but trust me, I don't want to flame, but just search some answers to some questions, if they exist. I'd like to read some stuff from some devs and some commercial-involved people as well, not just fanboys. Fanboying is cool but not so good by a pratical point of view :-) Ok, let's start.

Some weeks ago I got by mail the nice Ubuntu 7.04 cd from Canonical. Nowadays it's so fashion talking about Ubuntu, testing Ubuntu, installing Ubuntu etc that I decided to give it a try. I used linux for 2 years (2002-2004), then I quit because there were more problems than advantages into using it, and I was using the most user-experience-focused distro available at that time (Mandrake 9.2), or at least the best between those I tested (Debian 3.0 Woody (shipping with preistoric software on it), Red Hat and some derivates (let me decide the packages I want to install, b1tch!), Gentoo (it needed some geological eras for a complete install!), Slackware, Knoppix and tons of other live cds). 
I put the cd inside my Toshiba M30 laptop, the nice graphical boot appears, fine. Gnome loads: "Nice orange theme" I think. I start experimenting with programs, menus, icons etc. Everything is "inspired" by Mac OS X but there are some original ideas as well (like the "Enlarge icon" thing for the desktop icons). "Ok, everything seems working" and I install it. The partitioning step is a bit buggy (if you choose an option and then go back, all the text formatting messes up) and it's not as cool&easy as in Mandriva, when you really have control over things. Btw it works. "Now I have 25Gb for Windows and 12 for Ubuntu! Well done!", I say (my disk is 40GB). The importing-user-image-from-Windows is very nice as well. Ok I restart the machine and I boot into Ubuntu. 
Let's list what I disliked :-) I'd like to say that some points are not strictly Ubuntu-related, but I write theme here because behind Ubuntu there is a commercial company that -I presume- have interest to make a commercial-level OS (or sort of). Corollary: more quality we give = more possibilities to get back the invested money.

1) The italian localization is in the reality a 80%english+20%italian localization.
I have no problem using english-localized apps, but at least the operating system and the browser must be localized, don't they? How many Kbs are all the localizations? 100Kb/each? And don't tell me there is no space for them on the cd, because you lie. And don't tell me "localizing teams work slowly and they have not completed all the translation work in time". I'm a Joe User, I don't care about your excuses. The volunteers don't work? Pay somebody to do the translations for them. I'm a Joe user, I want the OS in my language to get a good initial opinion of it, I don't think I'm asking so much. Imagine Apple or Microsoft shipping their OSes partially translated..WTF! People'd piss them off! "But Ubuntu is free".. True, but free doesn't mean unprofessional or crappy. Or if you mean that, you are wrong. Stop using the "cost=0$" variable as a shield for the crappyness. If you want to really compete with commercial OSes, you have to offer the same basic functions and the right localizations. I hope you will start considering this as a priority.

2) There are no codecs to listen a simple mp3 from my Windows partition or to watch a dvd movie. This is just absurd. You could tell me "Fire up Automatix or Synaptic and get all of them in a breeze". Wrong. That's not the right approach. 
a) I have not internet connection at home, and many people are in my same situation. But, when I format and install Windows XP on my machine I have nearly-everything out-of
the-box, without any need to waste additional time and money. Same thing when I install Mac OS X Tiger on my Mac (except for the fact Apple nicely provides for free more software than Microsoft, like the iLife suite for example). Imagine to buy a car provided out-of-the-box without tires but just with the address of a nice mechanic who will give you the tires for free when you will go to his shop, located somewhere. Is it frustating, doesn't it?
b) I don't care about the fact you fear to be sued by some license-owner and then you don't bundle codecs into your product. Really, I don't care. If you want to push me, a Joe user, to appreciate  your product you may satisfy my basic user needs - and nowadays the ability to listen a mp3 is considered a basic need, doesn't it?
Being a commercial reality involved into spreading a Linux distro without codecs is like being a car brand (ex. Mercedes) and selling cars without Goodyear or Bridgestone tires, because you fear to be sued by Goodyear or Bridgestone since you didn't pay a buck for their licensing, and pretend to make money with it. WTF! Licenses cost? Pay for them and increase the value of you product. "Free as in freedom" is a good philosophy, but in the reality is not always possible to apply it. Stop dreaming. 
98% of people listen to their music saved in mp3 format, so you have two ways to attract them with your product: push'em to convert, use, rip, love, share music in the better Ogg Vorbis format (better by the licensing and audio-quality points of view) or provide them a way to listen out-of-the-box their mp3s. The first one seems really impossible to happen to me. 

3) Ubuntu's way to install stuff is wrong. But that's is not its fault, but it depends by the fact it derives from Debian, the less user-oriented distro ever, great for programmers, nerds and people who likes to waste time babysitting their computers and saturate their DSL bandwidths every time they mess up things and need to reinstall all the software again. Same thing happen to the users of many other distros. Let me explain why. 
As I said, I have no internet connection at home, so it's nearly impossible to install stuff on my new, shiny Ubuntu installation. Ok, you can download the .deb packages with another computer/OS, save them on a pen drive, bring them at home and install them from Terminal, typing manually the following lines:

cd /folder/in/which/you/downloaded/your/deb/packages
dpkg -i *.deb

or 

"configure-make-make install" if the software you need is only distributed as source files inside a nice tar.gz package. Sure you can do all this procedure. It doesn't look exactly user-friendly but it can be done. Ok, try to do it with Amarok, for example. Go to Ubuntu Packages site (that is well done), type "Amarok" in the search box, download it together with all the dependencies it needs (they are nicely listed on the same page of the app) and after like 30 minutes of work you have everything you need, maybe. You go back to home, type in Terminal the right commands and you get a bunch of errors, complaining that you miss the libxxxx or the libyyyyy that respectively need the libzzzzzz installed for proceed. WTF! To install an app all this stuff???? You are kidding me, doesn't you?
When I need an app for my Mac, I just open macupdate.com from a friend's computer or an university computer or even from my PSP (using some nice wifi hotspots), I type the app I need in the search box, I click "download" and I have everything I need inside a nice .dmg file. In the rarely cases the application needs some additional libraries or software (read: max 2-3 additional downloads), they are nicely linked on the application page: "Application X need Y software to work. Click here to get it, it's freeware". Same thing happens when I need a Windows app. 
Using the Mac or Windows approach, you are 99% sure that when you come back to your home computer with the .dmg or the .exe file inside your pendrive, you can surely install the software you need without any problem in 3 steps, and start immediately to use it. Using the Linux approach you are sure you will need 3-4 additional days of browsing and dowloading to get stuff done. More time wasted, more frustation, less productivity.
The Mac or Windows approach gives you the freedom to choose how get your applications, Linux doesn't. With Linux you are dependant from a repository. Do you really like that way? I don't. Mandriva solved partially the problem, giving you a lot of apps (and also all the codecs, except the one for video-dvds) inside its installation dvd. Ok urpmi is proprietary, but who cares? you don't spend a buck for it, it works and it provides nice descriptions, mostly localized as well, for every package. Mandriva is the only Linux-involved company I know that has designed a nice bussiness over Linux. Stuff is good enought if you'd spend money for it. And I admit, I'd spend money for Mandriva PowerPack. I actually run Mandriva 2007.1 On Mandriva, installing Amarok and make it working inside Gnome without wasting time into babysitting procedures is easy: just select, click and install.
What I'm talking about is not that Mandriva is better than Ubuntu or other distro, but it's that the Linux way of installing stuff must be re-designed. Software may be provided in a single, big package, that can run on all the distros and on all the architectures in 2 clicks. Like Apple does with Universal Binaries. 
There is no sense to have the same stuff packaged singularly for Debian, for Ubuntu, for Mandriva, etc.. they are all Linux, they have same libraries, same kernel etc, so stop doing single package but bundle everything inside a single .linux (or .whatever)package.  Next, every distro have to include every library, to satisfy every dependency without pain.
Finally, setups files have to be like "Next-Next-Finish" .exe setup files or simpler (like Apple's "drag .app into Applications folder. Done." way).
When all those points will be satisfied, Linux will start to be an alternative to commercial OSes, not just something to play with or experiments. Programmers and geeks are maybe 3% of the market. Pc-babysitters are 7%. The rest is made by Joe users. I hope it will be your priority to point to that 90%.

If I missed something, tell me. 
If you are really sure that Joe user wants to have joy with Terminal for just installing an app, tell me. 
If you think Linux is ready for every desktop, don't tell me anything, but write some lines for Digg, somebody will trust you.

Just my 2 cents :-) too harsh uhuh?

eldino

ps. Please don't go off topic.I'm talking about desktop experience and Joe user productivity. I know that Linux rocks as server os, as render-farms os, as Google-backend os etc.. I'm talking about everyday use. In the everyday use of you car you don't open daily your engine, right? Ok. So why in the everyday use of your computer you have to open the Terminal to install an app? :-)

it's simple. you don't care. so why should the community care for you? you just demand, and in the meantime you are not willing to do anything by yourself. I find you your post outrageously and absurd. I'm sorry if I'm too harsh, but the things you've said would piss off everyone. you'd better stay with Mac OSX or Windows. you're not talking here about Joe user, but about Stupid User...

---

### Post by Riffer on 2008-05-11
> **wolfen69 said:**
> btw, windows doesnt ship with mp3 or dvd codecs. so what's your point? i have to do alot more downloading after install with windows than linux.

My thought exactly, the hours I spent looking for codecs.

---

### Post by chewearn on 2008-05-11
Why are you guys bringing out an old thread?  The OP was long gone, the last post from him was July 6th 2007.

There are more than enough "Hardy Sxxks" threads this month (if you feel you really must be argumentative); no need to rehash old discussions.

---

### Post by Samhain13 on 2008-05-11
Responding to the original post:

> If I missed something, tell me. 

1) The problem is logistical, not structural.

> I'm a Joe User, I don't care about your excuses. The volunteers don't work? Pay somebody to do the translations for them.

If there were paid workers to do all the localisations, it would be hard to imagine Ubuntu being a free (as in no cost) OS.

2) The problem is legal, not structural.

> I don't care about the fact you fear to be sued by some license-owner and then you don't bundle codecs into your product. Really, I don't care.

Canonical surely would care if they are the ones who get sued over the shipping of proprietary codecs with Ubuntu, among other things. Now, depending on which country they get sued in, there's a chance for them to lose. If they lose, it would be hard to imagine getting the next version of Ubuntu.

3) The problem is preferential, not structural.

> cd /folder/in/which/you/downloaded/your/deb/packages
dpkg -i *.deb

You can do this, if you prefer:
Open Nautilus, right-click on the package.
Select "Open with GDebi Package Installer".
Click the "Install" button.
Key-in your administrator's password.

:)

> Why are you guys bringing out an old thread? The OP was long gone, the last post from him was July 6th 2007.

Ooops! ](*,)

---

### Post by Cifra on 2008-05-11
I think the mp3/dvd issue is a legal matter, actually.

---

### Post by Linux&amp;Gsus on 2008-05-11
> **eldino said:**
> Finally, setups files have to be like "Next-Next-Finish" .exe setup files or simpler (like Apple's "drag .app into Applications folder. Done." way).
When all those points will be satisfied, Linux will start to be an alternative to commercial OSes, not just something to play with or experiments. Programmers and geeks are maybe 3% of the market. Pc-babysitters are 7%. The rest is made by Joe users. I hope it will be your priority to point to that 90%
........
Just my 2 cents :-) too harsh uhuh?

Too harsh? No. Maybe not always really polite.

Anyways.
Did I understand that above statement right that you prophesy a 10% market share for Linux, just now? Man, you have more faith than I do.
But right, why not. Since you need all the "next-next-finish" steps to install a program. I personally find it easier to search in a local app or the console for a program rather then using Google and searching through tons of websites. But this is really a matter of personal choice. Period. Not even speaking of updates. Tell me again, how is the exact procedure in Windows and Mac to install updates for all installed programs? Do all apps tell you anyway when there is an update available? Not even talking about the need to reboot in Windows.

While I do understand some of your concerns I must say it's a bit not quite right to point out some things that would be nice to make it different for Joe Average. There are just as many things that have a superior solution in Linux. 

I guess everyone must understand that there is no 100% solution that suits everyone the same. Depending on your needs, habits, preferences, willingness to learn new things, etc. Linux will or will not be an option for you.

Besides all that, your car analogy totally fails. If I go to Mercedes and order a car I pay quite some money for that. I therefore expect that the steering wheel is on the correct side for my country, the speedometer shows KM or Miles, according to my countries default, the manual is written in my mother language, etc. If, however, you get a car for free in most cases it's because it's not worth a cent anymore but might still work more or less good. Every no and then there might be a exception but that is really probably just a very rare occasion.
Compared to that I would say that Linux has a far higher value compared to a free car. After all, you get what you pay for. If you get a car for free you might need to put in some money to make it road legal. Why not helping then a little bit with a translation for a app or OS that you got for free? It doesn't even cost you any money.

Really, no one forces you to use Linux. If you don't like it, if it doesn't suit your needs and/or expectation that's fine. You are free to use Windows or OSX. Or would you complain that when I give you my car for free that the fuel tank is 3/4 empty?

I think that people need to get their attitude right. Everybody who has ever installed Windows from scratch will bow at the Linux devs for how easy they made it to install including a whole bunch of apps, all that for free.
If it works different and looks different it might be due to the fact that Linux actually **is** different. People tend to forget that they needed some time to learn how to use a computer. Well, I don't know about others but at least for me it took more than 2 months to learn the necessary details of using Windows and all the apps. How do I install them, how to check and get and install updates, etc etc etc.


Just my 0.02$
Steve

---

### Post by conorsulli on 2008-05-16
I think you are right, I mean they don't have to supply the distro with anything propitiatory like codec's, But they could be smart about their ideology! "Linux for human beings" couldn't they provide links in the install process to install these features onto our desktops or even after the install?
EXAMPLE, when boot up my freshly ubuntufied computer, or the first time I click the Add/Remove button - I get something like this.

Welcome Ubuntu user, you have successfully installed the core operating system onto your computer...<all the crap about freedom and open source goes here> as of this your system is run on completely open source software however you may require some restricted software to let your Desktop run more efficiently, This includes extra propitiatory code to allow you perform: Media playback, Use of java, flash media, and added support for hardware.

Would you like to Download these restricted extra features from the online repository now?    

                  (yes)-recommended                  (No thanks)

Ubuntu is OK and I'm not flaming, But I have seen features similar to this on other Linux distro's that didn't want to run the risk of being sued. Ubuntu does a fair Job on a few things but for something that states their os is "Linux for human beings" they have forgot about the user interface a bit in comparison to other Linux distro's I have used. I hope somebody reads this and gives it serious consideration.

---

### Post by 23meg on 2008-05-16
Try double clicking a WMV file, or visiting a website that uses Flash. Yeah, welcome to 2008.

---

### Post by 3rdalbum on 2008-05-16
> **eldino said:**
> Have I take part to it? I'm a Joe user interested to use this operating system, nothing more. It's like to go to Mercedes shop and complain about an engine problem, and being answered with "Did you contribute? No? So you can't complain!".. 

No, it's like taking a ride on a herritage tram run by volunteers, and complaining that the paint is peeling off. Then the answer would be "If you'd like to fix this, you could join our volunteer club and help us repaint the tram".

---

### Post by rgb1701 on 2008-05-17
> **23meg said:**
> Try double clicking a WMV file, or visiting a website that uses Flash. Yeah, welcome to 2008.

I don't know what the intent or tone of this comment was, but Ubuntu's default Firefox browser will pop up a simple, trivial "Install Plugins" dialog box to install things like Java or Flash when you hit a site that needs them.  You do this once, then no issue- easier than the XP installs I've done in the past, where I had to manually go to the Sun and Adobe sites to download then install those plugins.

Of course, Totem/gstreamer will automagically ask you for MP3/other codecs install when needed, or trivial to install from MediBuntu, or siply use Mint 4.0/5.0 which does have DVD decryption and basically all common codecs preinstalled with other media players, and is Ubuntu compatible.

So, the "ease of installing Java/FLash plugin" and codecs issues have been dead since at least Fall 2007 on Linux, if not before.

re: the OP-

For North American users installing XP Pro/Home from a legal install CD, there is no DVD playback decryption either.  You must purchase a DVD player like PowerDVD/Windvd to decrypt commercial DVD's.

A North American home installed XP box cannot be made safe and fully functional without one of two things- (1) either a prior download and burn of patches from
[http://www.softwarepatch.com/windows/index.html](http://www.softwarepatch.com/windows/index.html)

plus installers for Flash/Java/DirectX 9c/Firefox/OpenOffice/Audacity/torrent client/p2p clients/universal IM client/etc, or an (2) internet connection.

How is this better than Ubuntu, which has OpenOffice, Firefox, P2p, torrent, IM and other apps ready at bootup, with trivial popups to install Flash/Java/gstreamer Mp3??

Comparing a non-North American XP install CD (or darknet bootleg) to Ubuntu is not apples-apples- Mint 4.0/5.0 ("non North American version of Ubuntu") to a loaded foreign/darknet CD might be more fair comparison.

---

### Post by 23meg on 2008-05-17
> I don't know what the intent or tone of this comment was,

> So, the "ease of installing Java/FLash plugin" and codecs issues have been dead since at least Fall 2007 on Linux, if not before.

That was my point. Some people seem to be stuck in 2006 so it's no surprise they're complaining about issues that have been solved a year ago.

---

### Post by chewearn on 2008-05-17
OMG people!

Please read the thread thoroughly, and check the OP post most carefully.

[I said this already 5 days ago]("http://ubuntuforums.org/showpost.php?p=4933576&postcount=27"), I will repeat it one more time.  The OP is long gone. Check the date; it's almost a year old.  Last time the OP was in the forum was July 6th 2007.  Geez!

The next guy to post in this thread replying to the OP is a clown.  I mean it! :mrgreen:

.

---

### Post by BlueSkyNIS on 2008-05-17
What does OP stands for?


OK, I'm a clown :lolflag:

---

### Post by chewearn on 2008-05-17
> **BlueSkyNIS said:**
> What does OP stands for?
OP = Original poster.



> OK, I'm a clown :lolflag:

Saved, since you didn't reply to the OP. :mrgreen:

---

### Post by rgb1701 on 2008-05-17
> **23meg said:**
> That was my point. Some people seem to be stuck in 2006 so it's no surprise they're complaining about issues that have been solved a year ago.

Well, I still wanted to address the flawed apples-apples comparisons that occure too frequently all around te net re: XP/Vista self-installs vs Linux self-installs and Windows vs Linux commercial instals, i.e. Dell Linux boxes have DVD playback by default just like Win commercial boxes.  Similarly, Win self installs *don't* have DVD playback vs an Ubuntu self install.

---

### Post by rgb1701 on 2008-05-17
> **23meg said:**
> That was my point. Some people seem to be stuck in 2006 so it's no surprise they're complaining about issues that have been solved a year ago.

Well, I still wanted to address the flawed apples-apples comparisons that occur too frequently all around the net re: XP/Vista self-installs vs Linux self-installs and Windows vs Linux commercial installs, i.e. Dell Linux boxes have DVD playback by default just like Win commercial boxes.  Similarly, Win self installs *don't* have DVD playback vs an Ubuntu self install.

...and the plug-ins issue.

..and the need for Internet connection issue.

The bottom line is, when evaluating these kinds of complaints and reviews, be sure to put your critical thinking cap on.

If the poster is using a commercial Windows pre-install in their argument, be sure he's comparing to an equivalent commercial OEM Linux pre-install.

If he's comparing a foreign Windows install CD, be sure to compare to a non North American targeted Linux distro (i.e. no software patent issues or default media codec differences).

If a poster complains about the need for an internet connection, be sure to compare the need for third party patches/drivers/plug-ins on both OS's, which require downloads in all cases.

The logic flaws across the net are blaring and too common.

---

### Post by 23meg on 2008-05-17
It's simply too tiring to point to people's lack of logic and sense all the time, and it gives you an undeserved "defensive" reputation, when in fact you're just pointing to facts and debunking flawed arguments, which fall apart at the first application of logic.

[IMG]http://imgs.xkcd.com/comics/duty_calls.png[/IMG]

---

### Post by rgb1701 on 2008-05-17
> **23meg said:**
> It's simply too tiring to point to people's lack of logic and sense all the time, and it gives you an undeserved "defensive" reputation, when in fact you're just pointing to facts and debunking flawed arguments, which fall apart at the first application of logic.



What may be self-evident to us experienced/technical users may not be to casual non-technical readers/lurkers/noobs who may be interested enough to try to install Linux on their own.

Calmly pointing out the logic flaws and counter arguments without appearing defensive or combative and devoid of ad hominem attacks helps balance the view and uncover the truth for the unaware/un-saavy.

---

### Post by punxtux on 2008-05-18
> **weblordpepe said:**
> ;)

Linux is alot like science, in that it self-regulates.

Nice out look! :D I like! I'm just an Observer here and I like some interesting metaphors people use towards Linux.

EDIT: I love your DOPEFISH avatar. 'DOPEFISH LIVES' - Quake 1.
I've been following that silly fish since Commander Keen. Thumbs up on your pic. Friends?

---

