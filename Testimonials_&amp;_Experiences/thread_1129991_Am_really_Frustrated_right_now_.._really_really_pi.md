---
title: "Am really Frustrated right now .. really really pist off"
date: 2009-04-19
forum: Testimonials &amp; Experiences
---

### Post by bigbrovar on 2009-04-19
Ok I started running linux around 2007, started with feisty fawn 6 months later i wiped off my vista dualboot and ran exclusively on linux, i loved the free and open nature of the linux desktop and also the linux community which i find as selfless and always willing to help. I while i have enjoyed most of my stay in linux there are moments when i feel the linux community is starting to lose it. Mark Shuttleworth said sometimes last year that Linux needs to blow past the Mac when it comes to user experience,( or something like that) Unfortunately many people interpreted that to mean better GUI and eye candy, dont get me wrong i love Eye candy and an integrated user interface, but what i feel the community should focus more than anything else is STABILITY. what people want is a stable system that just gets out of the way and allows you to do just want you want to do with your computer without bothering about the inner workings or things (at least if you careless)
 
Sure i quite understand the immense challenge linux devs face due to the proprietary and restrictive culture of some hardware vendors do neither release the source code of their hardware drivers or specification that would help the devs write their own drivers. In light of this the linux community has no option than to use reverse engineering to get round this issues, some of the problems the linux desktop face today are caused by badly written binary blobs which often times break many systems during updates, again they is little the community can do about this. 

However what am pissed about are things which we can do somthing about but which for some reasons are just messed up. When i give my last laptop to my brother (partly because i love him and partly because i was sick and tired of Nvidia and sony vaio) i decided to get a system with open hardware and that comes preinstalled with ubuntu. so i got a dell xps m1330 all intel hardware 

The default Hardy Heron worked out of the box but for one problem.

**PULSE AUDIO  **
recording or using skype to make calls just wont work. not because my hardware was not supported but because the software side of things were messed up. Why Ubuntu or any linux system decided to ship with pulseaudio somthing that is still bleeding edge and will probably not be ready for prime time till 2011 ( or probably never) unfortunately for me i easily got run the pulse problem by switching to alsa.
 
when Ibex was released i upgraded to it. and it was a just short of a deserter Many things that worked out of the box on Hardy Heron were broken in Intrepid, finger-print reader, Bluetooth, webcam, Internal Mic, Display Graphic all either partially worked or didn’t work at all. To be (Fair many of this problems were upstream problems and i faced them too when i tried Fedora 10. ) To get things to work i had to to some research and in some cases compile, and tweak the system to get around some of the problems i faced . Fortunately most of the issues like web-cam and blue-tooth were fixed by updates. unfortunately things like internal mic and my display driver (which always gave me some funky screen corruption when i enable compositing compiz or metacity) didn’t work no matter what i tried. 

now with the release jaunty jackalope one would expect things to have improved..  (to be honest some things have) but somethings are gone worse .. its still early days since jaunty is still in RC but there are no hope that things would improve for now

finger print authentication just doesn't work.  even though it worked perfectly on hardy heron and on ibex if u use a 3rd party PPA.. on jaunty it just doesn't work.. and from bug reports no sign of it working anytime soon. this is unacceptable for a distribution that wants mainstream attention. 

Pulse Audio is still a problem. there is no way to make skype calls on this laptop. i have tried every guide and tips still doesnt work. i had to rely on my nokia n810 for making skype calls. which is a shame really .. no mainstream OS should ever ship a release with a broken audio. especially when the hardware is not the problem. then it should just work.
am not sure if anybody on windows or mac knows what their sound server is but why should there, this things just work right now the state of pulse audio in linux is a mess  and a PITA to its users i can not confidently recommend linux to a nowbie because of Pulse audio.. just today i tried making a screencast for a blog post i was writing .. and guess what no voice .. not even audio recorder worked.. i mean WTF this is 2009!!!! little things like this are what matters. they are more important than a 5 sec boot time or some notification applet. Ubuntu should get down to the basics make things work at least dont break the once that work. its frustrating .. right now i cant function on my laptop which came ubuntu pre installed and am condering getting a mac just to make a screencast. its really really frustrating .

---

### Post by acimmarusti on 2009-04-19
I know pulseaudio sucks... but to tell you the truth skype runs very well on my computer. I could try giving you tips to make it work.

It turns out that since skype only works well with ALSA directly, if you are running any other application such as firefox, rhythmbox, etc that is using pulse for audio, then skype's sound won't work. So, you basically have to run it "alone". 

The other important thing to make it work properly, is that once you've logged in, go to options and then audio settings. Once there, DON'T leave everything as default!. Choose the ALSA driver for your sound card (with plughw) for ringing and output. For input, that depends on what you are using as a mic. I'm using the built-in usb mic in my webcam, so I choose that from the list (hw only). Once you've selected everything properly, click apply and do test sound and make a test call.

Hopefully this will work for you

---

### Post by 3rdalbum on 2009-04-19
I'd suggest moving to Debian - they have a tighter focus on stability plus you still get to keep the huge repositories.

I must admit I've not had a problem with Pulseaudio. Before I rebooted it had crashed and caused sound to not work, but I was running a program that triggered a kernel bug that caused Pulseaudio to crash.

---

### Post by Cracauer on 2009-04-19
The mess with the many sound APIs is really Linux's worst part, and it is 100% home-grown, we didn't need the help of any hardware vendor for it.

Of course problems with the hardware drivers, provided by the vendor or not, come on top.

All these problems with sharing sound and generally one hand of a Linux system being ignorant about what the other hand is doing all all resulting directly from having developed too many half-baken things instead of focusing on one thing. And the quality of some of the implementations is awful, too, and documentation, well...

---

### Post by Copernicus1234 on 2009-04-19
If Linux wants to become a serious competitor to Mac or Windows, it needs a lot more eye candy. Its not a coincidence that Windows 95 quickly got more popular than Windows 3.11, or that Windows XP beat Windows 2000 out of the water. For the non-tech user, its the looks that matters.

Thats why MacOS is getting so much attention too. And IPhone. And IMac. And even IPod.

Looks is very important these days.

---

### Post by ddrichardson on 2009-04-19
> **Copernicus1234 said:**
> Its not a coincidence that Windows 95 quickly got more popular than Windows 3.11
Perhaps your other examples hold water but people moved to Windows 95 because it had pre-emptive multi-tasking and better TCP/IP support amongst other things.

In most cases, Windows next version quickly gains popularity because OEM manufacturers stop supplying the previous OS, I'd take the idea of XP's eye candy over 2000 with a pinch of salt too, because the production environments we upgraded it to, one of the first things people did was switch back to "Windows Classic" theme.

One of Windows consistent criticisms on a new release is that people can't find how to do something they knew how to do in a previous release.

With regard to Macs - I suspect you're arguing the same point as me - its not eye candy, so much as consistency and that's one thing I would agree with as important in any interface.

With regard to eye candy - how much more can you get than in Linux? Compiz-fusion, thousands of free themes and icons?

---

### Post by bigbrovar on 2009-04-19
> **Cracauer said:**
> The mess with the many sound APIs is really Linux's worst part, and it is 100% home-grown, we didn't need the help of any hardware vendor for it.

Of course problems with the hardware drivers, provided by the vendor or not, come on top.

All these problems with sharing sound and generally one hand of a Linux system being ignorant about what the other hand is doing all all resulting directly from having developed too many half-baken things instead of focusing on one thing. And the quality of some of the implementations is awful, too, and documentation, well...

U took the word out of my mouth really .. its time the community sit down and ask our selves some hard questions 

What do we really want?
what should be our target user base?
do we really want to go mainstream?
right now am considering going back to hardy heron because that is the only version of ubuntu that has worked 100 of my computer ( a computer that came preinstalled with ubuntu) unfortunately if i were running windows i would consider this a big !fail and probably write a BOLD blog post about how my upgrade to another newer version of windows failed.. but i love FOSS i love the community, i love the philosophy behind foss even though i feel that we as a community need to get some fact straight, what happened to the linux that never crashes, what happened to the linux that was rock solid stable and just worked? it seems now we are obsessed with the latest and the greatest, forgetting technologies that has served us and have always worked. i understand the need to improve things but if ubuntu wants to be a distribution that as its eyes on mainstream it has to work harder on the quality of its releases. if i get a laptop with ubuntu.. it should just work with any version of ubuntu i upgrade to. if not we should stop this charade and tell it as it is .. linux is for geeks and has no place in the mainstream.

> 
Copernicus1234  	
Re: Am really Frustrated right now .. really really pist off
If Linux wants to become a serious competitor to Mac or Windows, it needs a lot more eye candy. Its not a coincidence that Windows 95 quickly got more popular than Windows 3.11, or that Windows XP beat Windows 2000 out of the water. For the non-tech user, its the looks that matters.

Thats why MacOS is getting so much attention too. And IPhone. And IMac. And even IPod.

Looks is very important these days. 

like i said i have nothing again eye-candy and i feel that it has its on role to place. but what makes the Mac great is not the eyecandy but the fact that an apple machine that ships mac just works, u start it and play music, make skype calls, do screencast and it just works without u have to fiddle with or have an understanding of what a sound server is. start your webcam and it just works, bluetooth just works, this is what people expect when there get a computer that ships with ubuntu. not an ubuntu preloaded laptop that wont work when u upgrade to another version of ubuntu. 

I just hate the obession with eyecandy, if for example the among to dev time ubuntu spend of the the new notification on jaunty was spend on fixing pulse audio, or reverting that to what worked, i think the community would be appreciate better.

---

### Post by ddrichardson on 2009-04-19
> **bigbrovar said:**
> like i said i have nothing again eye-candy and i feel that it has its on role to place. but what makes the Mac great is not the eyecandy but the fact that an apple machine that ships mac just works, u start it and play music, make skype calls, do screencast and it just works without u have to fiddle with or have an understanding of what a sound server is. start your webcam and it just works, bluetooth just works, this is what people expect when there get a computer that ships with ubuntu. not an ubuntu preloaded laptop that wont work when u upgrade to another version of ubuntu. 
Then that's not really an issue with OSS - its an issue with OEM manufacturers not developing and testing a working release for their machines and buying codec packs and ensuring they work before release.

---

### Post by bigbrovar on 2009-04-19
> **ddrichardson said:**
> Then that's not really an issue with OSS - its an issue with OEM manufacturers not developing and testing a working release for their machines and buying codec packs and ensuring they work before release.

They are times when OEMS are at fault for a broken OS .. now is not the time .. Dell has nothing to do with the broken bluetooth module that shipped with Ibex, after the old bluetooth framework was rewritten by gnome, nor do there have anything to do with how the bug in Hal broke thinkfinger that shipped in the ibex and jaunty repos making it hard to use finger-print ready something that worked fine on hardy , or the fact that fprintd and libusb did not ship with jaunty hence the gnome 2.26 feature which makes it have better support for finger print reader doesnt work on jaunty, dell nor do any oem have nothing to do with the messy state the intel gma965 is at now in jaunty where users with this hardware which is INTEL (hardwares dont get more open than intel) gets lockups and freezes and terrible composite perfomances that the latest RC update disbled compiz altogether, nor do OEM have anything to do with pulse audio, which today is the most cursed application in linux.. nope when the OEM mess up we should stick it to them, and when our OS messup we shouldnt try to cover it. that doesnt make you hate FOSS u are just speaking up so that things can improve.

---

### Post by Tamlynmac on 2009-04-19
> ddrichardson
Then that's not really an issue with OSS - its an issue with OEM manufacturers not developing and testing a working release for their machines and buying codec packs and ensuring they work before release.

+1
Your statements are on target.


> bigbrovar
U took the word out of my mouth really .. its time the community sit down and ask our selves some hard questions 

What do we really want?
what should be our target user base?
do we really want to go mainstream?

Who is "WE" and why all the concern regarding target base? Simply because some systems have issues with specific functionality in Ubuntu, you believe the dev's focus should shift to these problems. Thus resolving your issues. Others may have a different agenda based on their issues.

Logic suggests that each individual who experiences a problem with system functionality will view their problem as critical and demand resolution. Perhaps the "WE" your talking about should begin with "YOU". Get involved in being part of the solution, instead of complaining and pushing your agenda. You place yourself in a position of speaking for the community - have you endeavored to become involved in problem resolution or do you believe that by being part of the forum, that your in a position to speak for the community?

Numerous issues exist and finding solutions may prove to be more complex than one can initally comprehend. I suggest if your going to speak for the community, you take an active role in helping with resolution, instead of simply complaining about it. Ranting about a problem will not resolve the problem, generally it just exasperates the issue.

I can not speak for others, but I for one would appreciate it if your going to use words like "We" or "The Community" that you actually represent the entire community, not just a group of individuals with an issue. I hope ranting and complaining is not reflective of the community as a whole. Instead the community (IMHO) should reflect a concerted effort to resolve issues based on priority and improve functionality for all users. Not just those that use Skype or have audio issues probably due to hardware.

Just my $0.02

---

### Post by Wiebelhaus on 2009-04-19
I understand what your saying mate and mostly agree. But why get pissed off about it? I"m concerned for your well being , Is there anything you can do to help you relax maybe a girl friend or some ganja or maybe a night out drinking with your mates.

It'll all work out buddy and I hope you get to feeling better.

Cheers mate.

---

### Post by ddrichardson on 2009-04-19
> **bigbrovar said:**
> They are times when OEMS are at fault for a broken OS .. now is not the time .. Dell has nothing to do with the broken bluetooth module that shipped with Ibex, after the old bluetooth framework was rewritten by gnome, nor do there have anything to do with how the bug in Hal broke thinkfinger that shipped in the ibex and jaunty repos making it hard to use finger-print ready something that worked fine on hardy , or the fact that fprintd and libusb did not ship with jaunty hence the gnome 2.26 feature which makes it have better support for finger print reader doesnt work on jaunty, dell nor do any oem have nothing to do with the messy state the intel gma965 is at now in jaunty where users with this hardware which is INTEL (hardwares dont get more open than intel) gets lockups and freezes and terrible composite perfomances that the latest RC update disbled compiz altogether, nor do OEM have anything to do with pulse audio, which today is the most cursed application in linux.. nope when the OEM mess up we should stick it to them, and when our OS messup we shouldnt try to cover it. that doesnt make you hate FOSS u are just speaking up so that things can improve.
Dude, I didn't understand a word of that.

---

### Post by Cracauer on 2009-04-19
We should really stop bashing the hardware drivers.

It's not that Windoze sound drivers work much better, generally speaking. Creative Labs alone in particular is responsible for probably half of "Windows crashes" in the last 20 years.

But the API mess :eek:

---

### Post by karellen on 2009-04-19
I'm with the OP on this matter. there's no (logical) reason for a piece of hardware/software that worked in a previous release to stop working in the current one. OEMs have nothing to do with this. to put it simple, it's a lack of consistency and focus (multiple sound systems, all trying to do basically the same job...with very mixed results). reinventing the wheel and changing things every time a new distro comes out won't help anyone (not to mention Linux adoption as a functional **desktop **OS).

---

### Post by ddrichardson on 2009-04-19
> **karellen said:**
> I'm with the OP on this matter. there's no (logical) reason for a piece of hardware/software that worked in a previous release to stop working in the current one.
Yes there is - dependencies. So many things require something else and given the rate of development its inevitable in a system with a six month cycle that something might break.

However, if stability is that big a problem in your experience with upgrades then why not move to a distribution on a much more infrequent release model such as Debian Stable?

I also didn't blame *all* the OP's points on OEM's only the one area that was relevant.

---

### Post by karellen on 2009-04-19
> **ddrichardson said:**
> Yes there is - dependencies. So many things require something else and given the rate of development its inevitable in a system with a six month cycle that something might break.

However, **if stability is that big a problem in your experience with upgrades then why not move to a distribution on a much more infrequent release model such as Debian Stable**?

I also didn't blame *all* the OP's points on OEM's only the one area that was relevant.


I dual boot Mandriva with Windows Vista, so I've answered your suggestion ;)

---

### Post by bigbrovar on 2009-04-19
> **Tamlynmac said:**
> +1
Your statements are on target.




Who is "WE" and why all the concern regarding target base? Simply because some systems have issues with specific functionality in Ubuntu, you believe the dev's focus should shift to these problems. Thus resolving your issues. Others may have a different agenda based on their issues. Point of correction The dell XPS M1330 am talking about came preinstalled with Ubuntu 8.04 so 1> its not just any hardware its an hardware that came preinstalled with ubuntu and one that worked without a flaw on ubuntu hardy heron. Out of the box, 6 month later bluetooth,webcam,finger print reader,graphic card, all got broken because of bugs in the softwares that shipped in ubuntu. 

Finger print reader didn't work because of a bug in [**hal**]("https://bugs.launchpad.net/hal/+bug/256429") that broke thinkfinger the application that is used to setup Finger print reader. the problem is yet to be fixed in [**Jaunty**]("https://bugs.launchpad.net/ubuntu/jaunty/+source/thinkfinger/+bug/311732"). Dell or any OEM has nothing to do with this? its software issue pure and simple. and it doesn't affect just my hardware .. 

> Logic suggests that each individual who experiences a problem with system functionality will view their problem as critical and demand resolution. Perhaps the "WE" your talking about should begin with "YOU". Get involved in being part of the solution, instead of complaining and pushing your agenda. I said we because the linux community is a we thing, i may not be a developer or be able to contribute a line of code but i  help i documentation and my [**guide on how i got ubuntu intrepid ibex to work on my dell m1330**]("http://bigbrovar.wordpress.com/2008/11/20/ubuntu-intrepid-ibex-on-dell-xps-m1330/") has the highest hit in my blog till date (which shows am not alone) so when i complain and let out my frustration and pain with the direction ubuntu is taking it doesn't mean i don't try to help out the best i can.

>  You place yourself in a position of speaking for the community - have you endeavored to become involved in problem resolution or do you believe that by being part of the forum, that your in a position to speak for the community? 
Numerous issues exist and finding solutions may prove to be more complex than one can initially comprehend. I suggest if your going to speak for the community, you take an active role in helping with resolution, instead of simply complaining about it. Ranting about a problem will not resolve the problem, generally it just exasperates the issue. 
 
dude i am subscribed to many launchpad bug report, and also spend quality time helping out newbies to get their feet on the ground, i formed an ubuntu loco in my country and have given [**out ubuntu cd + aptoncd**]("http://ubuntunigeria.wordpress.com/2009/01/07/115/") and also helped configured ubuntu systems for countless of people in my country .. i also maintain the blog for my loco group [**www.ubuntunigeria.wordpress.com**]("www.ubuntunigeria.wordpress.com")
and also helped setup a mailing list were people can post questions about linux [**http://groups.google.com/group/ubuntunigeria/**]("http://groups.google.com/group/ubuntunigeria/") and an irc channel .. plus providing support and advocating free software in  Computer section of the biggest online forum in Nigeria [**http://www.nairaland.com/nigeria/topic-11508.864.html**]("http://www.nairaland.com/nigeria/topic-11508.864.html") add to this am also the system admin for the most advance science school in Nigeria African University of science and technology and help setup 2 computer labs and over 400 works stations all running ubuntu [**http://aust.edu.ng/node/70**](**http://aust.edu.ng/node/70**) i try the best i can and try to play my part, and when am unhappy with a certain thing i speak out. i recommend ubuntu to lots of people everyday and i want to know that when i say use ubuntu am actually recommending the best for them and not just letting my passion get in the way of reason


> 

I can not speak for others, but I for one would appreciate it if your going to use words like "We" or "The Community" that you actually represent the entire community, not just a group of individuals with an issue. I hope ranting and complaining is not reflective of the community as a whole. Instead the community (IMHO) should reflect a concerted effort to resolve issues based on priority and improve functionality for all users. Not just those that use Skype or have audio issues probably due to hardware.

Just my $0.02

when am using the world we , am saying ubuntu as a community everybody, its better than say "they" or canonical, or the dev, am saying the we are all to blamed in this flaw, all am saying is that we need to have a system that is guaranteed to work so that even though ubuntu cant work on 100% of hardwares out there .. there are infact systems that would work. and where is best to start than with OEM it took me a lot of money and stress to be able to buy a laptop with ubuntu it cost me $500 more than it would cost to get a vista equivalent because dell dont sell ubuntu laptop in my country. and i had to buy it through a friend in the USA. which means if the system should break am not covered by warranty.. and am on my own. i did all this to support the ubuntu project which i have much believe in and to also make sure that come rain my hardware will always be supported no matter the version of ubuntu. that was why i choose open hardwares and avoided nvidia or other closed source drivers.

Its sad that when a person comes to Ubuntu Testimonials & Experiences to express some frustrations with ubuntu he is flamed .. what the FOSS community need is not cheer leaders and yes men. i didnt post this in my blog or some other place i posted it in the Ubuntu Testimonials & Experiences which is a form of feed back to the community on how my experience in ubuntu has been. **please read my post before you decide to reply and flame me.**

---

### Post by kspncr on 2009-04-19
> **bigbrovar said:**
> 
The default Hardy Heron worked out of the box but for one problem.

...

i easily got run the pulse problem by switching to alsa.

You know...you don't HAVE to upgrade from Hardy Heron. If it works perfect then why not keep it instead of frustrating yourself with something that doesn't work?

---

### Post by bigbrovar on 2009-04-19
> You know...you don't HAVE to upgrade from Hardy Heron. If it works perfect then why not keep it instead of frustrating yourself with something that doesn't work?
same question i asked my self today.. as i write am just done installing hardy heron and am setting up my desktop, it just leaves a bad taste that i cant upgrade to a newer version due to unresolved bugs :(

---

### Post by mdsmedia on 2009-04-19
> **kspncr said:**
> You know...you don't HAVE to upgrade from Hardy Heron. If it works perfect then why not keep it instead of frustrating yourself with something that doesn't work?
That was my thought, too.

I hate to bring this in as a comparison, but if your hardware comes pre-installed with one version of an OS, it doesn't necessarily stand to reason that the later version will work 100%. If you had Windows XP pre-installed, it doesn't necessarily follow that Vista will work on your system. Windows 3.1 systems weren't guaranteed to run Windows 95.

Hardy is supported for 3 years, Intrepid and Jaunty for 1.5 years. Hardy will still be supported for another 2 years, being LTS.

---

### Post by bigbrovar on 2009-04-19
> **mdsmedia said:**
> That was my thought, too.

I hate to bring this in as a comparison, but if your hardware comes pre-installed with one version of an OS, it doesn't necessarily stand to reason that the later version will work 100%. If you had Windows XP pre-installed, it doesn't necessarily follow that Vista will work on your system. Windows 3.1 systems weren't guaranteed to run Windows 95.

last time i checked that was not an advantage of windows, its one of the many things people slack MS for, but even then its kind of comparing apples to oranges because 

1 - 6 months is too short a time for things that worked on a version of ubuntu to become updated or unsupported in the newer version of ubuntu .. so what am i suppose to do get a new hardware? 

2- most of the upgrading issuse are not due to non compatibility but due to bugs in code, like hal, or pulse audio, or the latest Mesa. which is my point if ubuntu want to go mainstream greater effort should be made so that buggy upstream packages are not shipped with a release. am just saying that the quality of release should improve with more focus on stability

---

### Post by mdsmedia on 2009-04-19
As I said, I hate to use it as a comparison, but you're talking about similar things.

No, you don't have to buy new hardware, you don't have to upgrade.

And Jaunty isn't final yet, either, so complaining about bugs in software is probably a little premature.

I've got Jaunty installed on my desktop, which is for all intents and purposes my play machine. My laptop which is my work machine has Hardy installed. I'm quite happy with Hardy and don't see any real reason to upgrade at this stage. 

I might be reinstalling simply because of some rendering issues in Firefox and Opera.....reinstalling only because a fresh install of Opera appears to have rendering issues even when I installed it just because of the rendering problems in Firefox. I'll try reinstalling Firefox first, though.

Edit: Come to think of it, I can't see why a fresh install would help with rendering issues, if a fresh install of Firefox won't.

---

### Post by bigbrovar on 2009-04-19
> **mdsmedia said:**
> As I said, I hate to use it as a comparison, but you're talking about similar things.

No, you don't have to buy new hardware, you don't have to upgrade.

And Jaunty isn't final yet, either, so complaining about bugs in software is probably a little premature.

I've got Jaunty installed on my desktop, which is for all intents and purposes my play machine. My laptop which is my work machine has Hardy installed. I'm quite happy with Hardy and don't see any real reason to upgrade at this stage. 

I might be reinstalling simply because of some rendering issues in Firefox and Opera.....reinstalling only because a fresh install of Opera appears to have rendering issues even when I installed it just because of the rendering problems in Firefox. I'll try reinstalling Firefox first, though.

Edit: Come to think of it, I can't see why a fresh install would help with rendering issues, if a fresh install of Firefox won't.

You are quite right .. i was just worried and a little frustrated at the among of broken upstream projects that ubuntu has to ship with. anyway am back to hardy now an every thing is rock solid as before .. removed pulse audio and am back to alsa .. i dont see my self upgrading anytime soon (which is pretty bad but then life happens) although my netbook will continue to run jaunty (for documentations and blogging purposes) thanks to everybody that had something to say .. i guess this is was a happy ending (sort off) it really feels good to have a computer that just works again :D

---

### Post by Tamlynmac on 2009-04-19
> bigbrovar
i didnt post this in my blog or some other place i posted it in the Ubuntu Testimonials & Experiences which is a form of feed back to the community on how my experience in ubuntu has been. **please read my post before you decide to reply and flame me.**

Had you read and understood my response, you would realize I was objecting to your use of the words "We" & "The Community". I also was pointing out the fact that everyone that has a functionality problem believes their problem should be given the number one priority. I did not attempt to flame you, only suggested that I found your words offensive. As stated in my response, I can not speak for others or the community and personally don't appreciate anyone speaking for me.

What's "sad" is that you felt the need to use a pre-released version of Ubuntu, when an LTS version was already fully operational. I've done many an install and have helped many a user, including phone support. Not once have I spoke for others or even suggested that somehow any issues I incurred should immediately be addressed. I've used launchpad and to date I don't believe the issues I presented there have been resolved. Should I come to this section and start ranting because they didn't place my issues at top the the priority list? Really?

I'm a EM (Electron Microscope) component level engineer, so when endeavoring to blow your horn, your may wish to consider that others have skills comparable to yours or possibly even beyond.

Had you waited for the actual release (or after the first or second update) you may have found that some issues were resolved. Instead you chose to install a pre-release and then came here to rant. Had you read any of my previous posting you'd know I'm anything but a "yes man". However, I guess you didn't bother doing that either. In your opinion what Ubuntu needs now is based solely on your own perception. Perhaps, you may find that many others don't share that perception. Coming to the forum and ranting about what the devs should do to correct issues, seems counter productive as the devs don't live here. So what is your objective in complaining here, instead of to devs? Are your recruiting or simply satisfied with a platform whose audience has limited if any input to the devs.

Good Luck with your rant and know that I have no desire to involve myself any further with this thread (will unsubscribe). Should you feel the need to respond - do so for those that wish to continuee reading and sympathize with your misfortunes.

---

### Post by bigbrovar on 2009-04-20
> **Tamlynmac said:**
> Had you read and understood my response, you would realize I was objecting to your use of the words "We" & "The Community". I also was pointing out the fact that everyone that has a functionality problem believes their problem should be given the number one priority. I did not attempt to flame you, only suggested that I found your words offensive. As stated in my response, I can not speak for others or the community and personally don't appreciate anyone speaking for me.
it would be nice if you actually read the post you know. Most of the problems i talked about were existed in the intrepid ibex, like the bluetooth, finger print, graphic screen corruption, pulse audio, etc and theses problems didn't affect just my pc. my point is that ubuntu devs should work better at the quality of their release so that it doesn't break compatibility. i went for a system with open hardwares so as to have an out of the box compatibility with ubuntu. but most of the problems i highlighted are software bugs and have nothing to do with hardware. again it am not the only one affected by the pulse audio issue, or the webcam problem, or the finger print issue.. i even went to post the various bug reports highlighting this problems

> What's "sad" is that you felt the need to use a pre-released version of Ubuntu, when an LTS version was already fully operational. I've done many an install and have helped many a user, including phone support. Not once have I spoke for others or even suggested that somehow any issues I incurred should immediately be addressed. I've used launchpad and to date I don't believe the issues I presented there have been resolved. Should I come to this section and start ranting because they didn't place my issues at top the the priority list? Really?

I used a pre-release version (which is in Release candidate anyway) because of the many issues i had with intrepid ibex it was that bad that i felt probably the release candidate of jaunty would be better .. right now they is a bug with the GMA965 which freezes the system i posted the bug link in my previous post, lots of people use this graphic card so again its not just me. (even then this thread is about personal experience right? i can only say what affects me) my point is that ubuntu should improve the quality of their release.. many people now have computers that cant make skype calls just because of pulse audio, its about 1 year now since its release still its as buggy as hell.

> I'm a EM (Electron Microscope) component level engineer, so when endeavoring to blow your horn, your may wish to consider that others have skills comparable to yours or possibly even beyond.

Good for you, made an assumption that i should play my part before complaining .. i was just letting you know i just don't sit on my **** and do nothing .. am involved in promoting the ubuntu project the best i can. 
> 
Had you waited for the actual release (or after the first or second update) you may have found that some issues were resolved. Instead you chose to install a pre-release and then came here to rant.
its obvious u have not been reading my posts. i said most of the problems existed in ibex, ibex was unbearable for me.. that was why i decided to try the release candidate which is a reflection of the final release bearing any last minute change, i was just sad that bugs like the intel bug that causes lockup made it to RC. Jaunty is a great release and i noticed lots of improvements, just that things like pulse audio, and the intel card regression will cause a big dent on user experience
> 

 Had you read any of my previous posting you'd know I'm anything but a "yes man". However, I guess you didn't bother doing that either. In your opinion what Ubuntu needs now is based solely on your own perception. Perhaps, you may find that many others don't share that perception. Coming to the forum and ranting about what the devs should do to correct issues, seems counter productive as the devs don't live here. So what is your objective in complaining here, instead of to devs? Are your recruiting or simply satisfied with a platform whose audience has limited if any input to the devs.
the "yes man" post wasn't referring to you or anybody in particular ,, it was just saying that ubuntu needs critiques not just people that would praise it when it does right.. people should criticize too when it goes wrong. it was not referred to you in anyway

> Good Luck with your rant and know that I have no desire to involve myself any further with this thread (will unsubscribe). Should you feel the need to respond - do so for those that wish to continuee reading and sympathize with your misfortunes.

from your post if obvious you feel offended, it was not my intention and if you feel i have in anyway insulted you then am sorry. i was just posted my experience with recent release on ubuntu generally. and what i feel could be improved.

---

### Post by megamania on 2009-04-20
> **mdsmedia said:**
> I hate to bring this in as a comparison, but if your hardware comes pre-installed with one version of an OS, it doesn't necessarily stand to reason that the later version will work 100%. If you had Windows XP pre-installed, it doesn't necessarily follow that Vista will work on your system. Windows 3.1 systems weren't guaranteed to run Windows 95.
There's a big difference. If you have XP or 2000, you can install NEW software by just double-clicking on the new program which you downloaded off the net.
With Ubuntu, if you don't upgrade you have no _easy_ chance to get new programs. You'll have to enable some backports or compile yourself.

I'm not saying you're wrong, but you're probably underestimating this BIG difference. My dad, for example, has a 5-year-old copy of XP but he is perfectly able to install new software. That's why he's still using windows while I only use Linux.

I personally install alpha6 or beta of each Ubuntu release primarily (but not only) to get updated versions of the programs I use.

---

### Post by stalkingwolf on 2009-04-20
where to start? hmmm!  ok ill start here.

> There's a big difference. If you have XP or 2000, you can install NEW software by just double-clicking on the new program which you downloaded off the net.
With Ubuntu, if you don't upgrade you have no easy chance to get new programs. You'll have to enable some backports or compile yourself.  this is not exactly true. I have one desktop
that i own and two that i administer.  software is not always available.  for instance to use the software that i already own
with xp i have to install 98me then upgrade to xp.  if i need xp sp2 im screwed for various reasons i cant install it.  so as yet
i cant use my webcam.  If i install an xp install not an upgrade
i cant use the 1000.00 worth of software i already own.

There have been several post lately that suggest that WE the community need to "sit down and decide" where WE want the OS to go. From where i sit that will never be possible.  Ubuntu is based on choice.  That is the reason that most of us use it. We
will never come to a consensus because each of us  has different needs and a different collection of hardware.

As I recall dells preinstalled computers ship with a custom build of Ubuntu, one that Dell built for their systems.  To suggest that an off the shelf release is bad because it has issues on a system that shipped with a custom build is plumb dumb.

I have 8.10 installed on my 2 desktops. it works fine.  the program that i need to work works as does my webcam.  It doesnt work on my laptop, no wireless.  I havent had the time to tyr and fix it. so I reinstalled 8.04. , everything but the cam works.

As for software and updates until this summer  as I recall 7.10 still has a functioning repository.  After that 8.04 is supported for 3 years.

---

### Post by megamania on 2009-04-20
> **stalkingwolf said:**
> for instance to use the software that i already own with xp i have to install 98me then upgrade to xp.  if i need xp sp2 im screwed for various reasons i cant install it.  so as yet
i cant use my webcam.  If i install an xp install not an upgrade
i cant use the 1000.00 worth of software i already own.

I agree with you. But we are talking about different things, I think:
1) Why would anybody need to upgrade Ubuntu to the newest version, besides the improvements in the OS?
Because if you keep the old version, you'll have access to repositories with old software. Installing new versions of the software is possible, but often not very convenient.

2) Does windows work better than Ubuntu?
No, and I guess we knew that. Most of us are here because we like linux. And I only use Linux.
I've been through windows' compatibility/drivers-install/updates hell and BSODs too many time to mention. But I think this is a different subject.

---

### Post by bigbrovar on 2009-04-20
> 
As I recall dells preinstalled computers ship with a custom build of Ubuntu, one that Dell built for their systems. To suggest that an off the shelf release is bad because it has issues on a system that shipped with a custom build is plumb dumb.

i just want to correct this statement .. the ubuntu that comes preinstalled on dell laptops and desktop are just vanilla ubuntu with proprietary codecs and probably some proprietary drivers.. the main different between the ubuntu shipped wiht my dell and vanilla ubuntu is the fact that the dell ubuntu doesnt giev you an option to partition your system the way u want. so you can choose how big you want your home partition or swap.. it does it automatically.

---

### Post by karellen on 2009-04-20
> from your post if obvious you feel offended, it was not my intention and if you feel i have in anyway insulted you then am sorry. i was just posted my experience with recent release on ubuntu generally. and what i feel could be improved.

from my point of view, there's no need for an excuse ;). it's just some people can't stand any form of criticism regarding their favorite distro (or any Linux OS)

---

### Post by Bios Element on 2009-04-20
> **karellen said:**
> from my point of view, there's no need for an excuse ;). it's just some people can't stand any form of criticism regarding their favorite distro (or any Linux OS)

From my point of view, flame dell; Not ubunbu. Dell is the one who shipped it. Hardy is still supported so I fail to see the issue. Flame me all you want but just because your system doesn't work and dell doesn't have it working (with a yet to be released) update doesn't mean ubuntu is bad.

---

### Post by Thanh-BKK on 2009-04-21
> **Copernicus1234 said:**
> If Linux wants to become a serious competitor to Mac or Windows, it needs a lot more eye candy. Its not a coincidence that Windows 95 quickly got more popular than Windows 3.11, or that Windows XP beat Windows 2000 out of the water. For the non-tech user, its the looks that matters.

Thats why MacOS is getting so much attention too. And IPhone. And IMac. And even IPod.

Looks is very important these days.

Hi.

You can't be serious, can you..? I have been running Vista... which is about as much eye-candy as there is in Windows. Mac OS blows it out of the water with no efforts.

But my trusty Hardy, which replaced Vista as has been my sole OS since one year, blows Mac OS not only out of the water but right out of our galaxy! And i'm running Gnome-only on my main machine.........

In the morning today i did my first trial run with Jaunty on my experimental machine which i keep for just that purpose - downloading all the updates to it and see if the system is stable, and only if it is then same updates are allowed on the main machine. Prevented me from catching some bugs due to botched updates which are usually fixed the next day or so :)

However today i wiped that out and installed Jaunty, a CD that's a week old so probably not the latest build. And because that went so flawlessly i installed KDE (Kubuntu-desktop) right after it.

And booted to KDE.

Guess what? The login screen alone has more eye-candy than Mac OS! And EVERYTHING really "just worked". No fiddling. No drivers. After install was completed it had the desktop effects already enabled, i only needed compiz-settings thingy to turn on every bell and whistle that ships with it... WOW, i can only say. 

And that's on an Athlon 3500+ single core, 1 GB RAM, 128 MB Nvidia graphics machine. 

My main system will stay on Hardy though, i need it to run a LTS distro and Hardy works flawlessly, however i am seriously thinking about putting KDE on that, too, just to impress some of my friends who still say "Linux? That's text-only, isn't it?"

Kind regards.....

Thanh

---

### Post by richaustin on 2009-04-21
> **Copernicus1234 said:**
> If Linux wants to become a serious competitor to Mac or Windows, it needs a lot more eye candy. Its not a coincidence that Windows 95 quickly got more popular than Windows 3.11, or that Windows XP beat Windows 2000 out of the water. For the non-tech user, its the looks that matters.

Thats why MacOS is getting so much attention too. And IPhone. And IMac. And even IPod.

Looks is very important these days.

I definitely disagree with part of what Copernicus has said here. It is fair to say that W95 became more popular than 3.11 because it looked better. However, the main reason was that W95 was a better system overall (still crap but you get the idea!).
XP took off largely because W95 / W98 / NT / W2K were truly awful (let's not mention Millenium Edition!) from a business perspective. While XP may be complete rubbish, in comparison to Ubuntu let's say, from a business perspective it is the only M$ OS that makes any sense. It's stable. It's (hah! hah!) secure (ok, it's not, but it is perceived as being so in the business world). Users can bung a CD in the drive and, largely, the software / hardware works.
Overall, as the start of this thread clearly shows, users of any OS want a system that just darn works! I can be a bit geeky at times I must admit but tbh I can't always be bothered with messing around. I just want my PC to do what I want it to do, and who cares what the screen looks like? 
However, my wife loves Linux cos she thinks it looks great and she loves the Penquins! So what do I know huh?

Rich

---

### Post by karellen on 2009-04-21
> **Bios Element said:**
> From my point of view, flame dell; Not ubunbu. Dell is the one who shipped it. Hardy is still supported so I fail to see the issue. Flame me all you want but just because your system doesn't work and dell doesn't have it working (with a yet to be released) update doesn't mean ubuntu is bad.

too bad most of Linux zealots don't apply this line of thinking to Windows (in its case OEMs are never to be blamed ;) )

---

### Post by ddrichardson on 2009-04-21
> **richaustin said:**
> I definitely disagree with part of what Copernicus has said here. It is fair to say that W95 became more popular than 3.11 because it looked better.
With respect, that's tripe, I remember a lot of resistance to the new interface when it was released.

Windows 95 became popular for two reasons - OEM installation and that it was capable of some basic operating functions such as a decent(ish) TCP/IP stack and pre-emptive multi-tasking, not to mention long file names - that other OS had had for years.

---

### Post by bigbrovar on 2009-04-21
> **Bios Element said:**
> From my point of view, flame dell; Not ubunbu. Dell is the one who shipped it. Hardy is still supported so I fail to see the issue. Flame me all you want but just because your system doesn't work and dell doesn't have it working (with a yet to be released) update doesn't mean ubuntu is bad.

The Above statement is really unfortunate, I have been an ubuntu users running it exclusively as my mine OS for close to 2 years, yet i am not blinded by fanboism/cheerleading syndrome, were i feel improvements can be made i come out an say it.

One of the biggest criticism of Microsoft is that most of its updates break hardware compatibility. even though its OS release are always years apart compared to ubuntu.   

If am an OEM and i want to ship ubuntu. we all agree that the best practice  that will ensure compatibility with ubuntu and linux in general is to use hardwares that are open, and whose drivers works with the linux kernel, hardwares that will work with and FSF approved OS without any tweaking. This is the type of hardware that came with my dell m1330, which came preinstalled with ubuntu hardy heron.

When i decided i didnt like the partitioning layout of the presinstalled ubuntu, i decided to install a vanilla hardy heron and that worked to out of the box. when intrepid ibex was release, I like every other ubuntu user wanted to enjoy some of the goodies and new feature of intrepid and i decided to upgrade my computer. but to my Dismay most of the things that worked on hardy heron did not work on intrepid ibex due to bugs in many of the applications that shipped with Intrepid Ibex

[**Bluetooth**]("https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/268502"): The result is a broken bluetooth in intrepid. on hardy i could right click on anyfile and send as bluetooth, not possible with intrepid, i had to installed [**blueman**]("http://bigbrovar.wordpress.com/2009/02/14/blueman-an-awesome-bluetooth-manager-for-ubuntu/") from a ppa which really improved the bluetooth situation. Dell had nothing to do with this, infact one of the reasons dell is still shipping hardy heron on their ubuntu PC is because of the current state of things in ibex, my hope is that things improve on jaunty.

[**InternalMic**]("https://bugs.launchpad.net/bugs/275998")
just doesnt work, in intrepid i have tried billions of ways to make my mic work with skype or sound recorder, the best i got was a very small sound that sounded like a whisper even though i was shouting at the top of my voice, again this is plan software issue. Again do you want to blame dell here, dell played its part by shipping their ubuntu hardware with an open sound card, something that works on alsa its ubuntu's job to make sure that whatever they decide to include in ubuntu next release dont break hardwares shipped by its OEM partners esp when this hardwares adhere to open standards.

**Pulse Audio** only god with know why ubuntu and major linux distros decided to ship Pulse Audio by default. today its the most cursed application in Linux. it is unstable, causes gnome to hack, its just not ready for prime time, the fact that the pulse dev came out and said ubuntu messed up in pulse audio configuration hardly inspires [confidence]("http://0pointer.de/blog/projects/jeffrey-stedfast.html") 

> Some distributions did a better job adopting PulseAudio than others. On the good side I certainly have to list Mandriva, Debian, and Fedora. OTOH Ubuntu didn't exactly do a stellar job. They didn't do their homework. Adopting PA in a distribution is a fair amount of work, given that it interfaces with so many different things at so many different places. The integration with other systems is crucial. The information was all out there, communicated on the wiki, the mailing lists and on the PA IRC channel. But if you join and hang around on neither, then you won't get the memo. To my surprise when Ubuntu adopted PulseAudio they moved into one of their 'LTS' releases rightaway. Which I guess can be called gutsy -- on the background that I work for Red Hat and PulseAudio is not part of RHEL at this time. I get a lot of flak from Ubuntu users, and I am pretty sure the vast amount of it is undeserving and not my fault.
 

again how is dell to blame for this, sound in 2009 should just work, sadly the way things are going in jaunty its unlikely that pulse would be fixed till probably the release of kermic. its just not acceptable for a distro that tries to be mainstream.

**Finger Print reader** one of the cool things about my computer is the ability to use my finger swap for all my authentication this greatly improves my works flow since i have a very long passwd which i hate to type everytime i need to use sudo. sadly on intrepid ibex the thinkfinger in the repository is broken, and doesnt work well due to a bug in **[hal]("https://bugs.launchpad.net/hal/+bug/256429")**, even though it worked flawlessly on hardy, worse still there seem to be no hope of this being fixed in [**jaunty**]("https://bugs.launchpad.net/ubuntu/jaunty/+source/thinkfinger/+bug/311732"). again how is dell responsible for a bug in hal? which brings me to the point of, nobody should ever know the inner workings of his system, (not if you are a geek) it should just work. how many mac users no the sound system of mac,? it just works, why should i know about hal, or pulse try telling your girlfriend that sorry i couldnt call you because pulse audio as a problem with skype.

**Graphic Card issues** On intrepid ibex i could use compositing because of this [**problem**]("https://answers.launchpad.net/ubuntu/+source/compiz/+question/62004") on jaunty the state of Intel GMA 965 is very [**critical**]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392") system freezing up, like 10 times in a day. got so bad that the recent compiz update in jaunty blaclisted the card all together, and the way things are going it doesnt seem this problem would be fixed before jaunty is released in about 2 days time, again how is dell to blame for a regression mesa which is a cause of this problem.

On a final note Am just saying that Ubuntu should work to improve the quality of their release, It is  nolonger a distro for geeks and more and more non geek are starting to consider it as a better alternative. and if 
things like sound and bluetooth is still a problem in 2009 then its just arent good enough

---

### Post by rozilla on 2009-04-21
> **kspncr said:**
> You know...you don't HAVE to upgrade from Hardy Heron. If it works perfect then why not keep it instead of frustrating yourself with something that doesn't work?

My sentiments exactly. There is no logic to upgrading from an LTS release that "just worked" to an RC release and then whine about this bug and that bug. What do you expect? The only real reason to upgrade would be due to an existing issue that is being experienced by the user, and is **solved** by upgrading. I think most people just slap on the latest Ubuntu beta whatever, simply because of nothing more than fanboyism and the need to have a shiny new toy.

You know what they say, if it ain't broke, don't fix it.

> **Tamlynmac said:**
> What's "sad" is that you felt the need to use a pre-released version of Ubuntu, when an LTS version was already fully operational. I've done many an install and have helped many a user, including phone support. Not once have I spoke for others or even suggested that somehow any issues I incurred should immediately be addressed. I've used launchpad and to date I don't believe the issues I presented there have been resolved. Should I come to this section and start ranting because they didn't place my issues at top the the priority list? Really?

Again, I fully agree. It's nonsense to leave stability for the sake of novelty, and then rant about instability and possible loss of functionality.

> **Bios Element said:**
> From my point of view, flame dell; Not ubunbu. Dell is the one who shipped it. Hardy is still supported so I fail to see the issue. Flame me all you want but just because your system doesn't work and dell doesn't have it working (with a yet to be released) update doesn't mean ubuntu is bad.

Another good point. Perhaps the OP needs to redirect his rage at Dell? He makes it sound as if **all** laptops in existence have problems with Jaunty. For all we know, his laptop might be defective, and others of the same model/spec work flawlessly with the installed release.

> **bigbrovar said:**
> On a final note Am just saying that Ubuntu should work to improve the quality of their release, It is  nolonger a distro for geeks and more and more non geek are starting to consider it as a better alternative. and if 
things like sound and bluetooth is still a problem in 2009 then its just arent good enough

Ubuntu is still very much a geek distro. Feel free to be a geek, roll up your sleeves and produce some patches for these issues "we" are facing. "We" would thank you for it. Wouldn't "we"?

---

### Post by ECPCLINUX on 2009-04-21
I know what your feeling. I to use Skype, it saves me a bundle on Long distance calls. What I did at first after try after try to make it work well, was to install Windows back on two out of three computers at home. My next target was Skype, I wrote customer support and told them how I felt that they do not support PulseAudio. I saw a few people complaining at the Skype forum and I joined them, that was March 12.
In the Forum I wrote:
"Well, I'm frankly tired of not having support for pulse audio in Ubuntu. To the point that I'm searching for alternatives. 8 month or so is more than enough to wait. If your limited, for lack of Linux programers, you should concentrate on the audio part first. I read that you are caught-up as far as features on linux vs. Windows. But honestly, would you not say that sound is the most important feature on Skype? If Skype is not compatible with Pulse Audio it renders it useless regardless of how many features it may have included in newer versions." 

Well...I wrote a few more words, but you get the idea. If I seemed rude,???? well maybe I was but I was not happy at the moment, I had to consider going to Windows on two of my three computer.

I went today and saw this update from Skype:

[http://share.skype.com/sites/linux/2009/01/skype_for_linux_updates.html](http://share.skype.com/sites/linux/2009/01/skype_for_linux_updates.html)

 My second solution was to buy a Skype phone for which I do not need a computer to use it, just a router. It work wonderfully. Only problem, the wife won't let go of it. When I got it I paid $26.66 out the door at Amazon, incredibly I looked at it now and it's going between 199 to 250 Dollars!!!, not a good alternative for many anymore. I will try later to place another complaint at Skype, maybe more of us should do as well. Anyway, now I will install Ubuntu 9.04 (once it comes out on the 23rd.)on my second system. PS Skype has vacancies for Linux techs. Anybody?;)

---

### Post by bigbrovar on 2009-04-21
> **rozilla said:**
> My sentiments exactly. There is no logic to upgrading from an LTS release that "just worked" to an RC release and then whine about this bug and that bug. What do you expect? The only real reason to upgrade would be due to an existing issue that is being experienced by the user, and is **solved** by upgrading. I think most people just slap on the latest Ubuntu beta whatever, simply because of nothing more than fanboyism and the need to have a shiny new toy.

You know what they say, if it ain't broke, don't fix it. how about if its broken don't release it .. which is my point. how is ubuntu techically then better than windows or Mac when releases ship with known bugs that might break functionality?



> Again, I fully agree. It's nonsense to leave stability for the sake of novelty, and then rant about instability and possible loss of functionality.
 agreed that does not address my point which is ubuntu should ship stable tools that worked in previous releases, at least dont ship the latest buggy version. focus should be on stability.

> 
Another good point. Perhaps the OP needs to redirect his rage at Dell? He makes it sound as if **all** laptops in existence have problems with Jaunty. For all we know, his laptop might be defective, and others of the same model/spec work flawlessly with the installed release. so dell is to be blamed for bugs in hal, pulse audio, the buggy GMA965 driver, etc. as an OEM dell did what every reasonable OEM that wants to ship linux would do, it uses hardwares that are open and adhere to open standard.. beside most of the issues i spoke about doesnt just affect dell.



> Ubuntu is still very much a geek distro. Feel free to be a geek, roll up your sleeves and produce some patches for these issues "we" are facing. "We" would thank you for it. Wouldn't "we"?
 check my blog i play my part [http://www.bigbrovar.wordpress.com]("www.bigbrovar.wordpress.com")

---

### Post by Thanh-BKK on 2009-04-21
Hi.

Well it's got to be Dell, because i do NOT experience those Jaunty-bugs in my home-made computer made of Asus, AMD, Kingston, Western Digital and many other brand's parts. My sound works, the machine doesn't hang etc, so if you got a bug while using one particular computer model it can very well be that particular computer model.

One of my colleagues has an Acer that also has such finger-print thingy. It works fine in Vista - and no power in the world can make it work in XP, despite a driver being available and installed - it just doesn't. Neither does the integrated web cam (which, too, worked in Vista). My boyfriend has a different model of Acer - and HIS web cam works just fine in XP (and Ubuntu Hardy for that matter, from a live CD!!)

Best regards....

Thanh

---

### Post by Bios Element on 2009-04-21
> **bigbrovar said:**
> how about if its broken don't release it .. which is my point. how is ubuntu techically then better than windows or Mac when releases ship with known bugs that might break functionality?



 agreed that does not address my point which is ubuntu should ship stable tools that worked in previous releases, at least dont ship the latest buggy version. focus should be on stability.

 so dell is to be blamed for bugs in hal, pulse audio, the buggy GMA965 driver, etc. as an OEM dell did what every reasonable OEM that wants to ship linux would do, it uses hardwares that are open and adhere to open standard.. beside most of the issues i spoke about doesnt just affect dell.


It isn't broken. Works 150% PERFECTLY fine on my system. So do everyone a favor and quit calling it broken just because it doesn't work on your system. If you don't think ubuntu is better do everyone a favor and just don't use it. Because you have better things to do then hash over the same complaints and we have better things to do then respond to your pointless complaints. This is not a help sub-forum and what you need is help. Complaining here isn't going to get anything done.

Oh, and remember XP when it came out? A mess. Vista? I shouldn't even have to point this out...

Ubuntu doesn't ship anything. They release it and you download it. (although volunteers 'do' ship cd's but that's a different matter.) 

Yes, Dell **IS** to be blamed. We've been over this several times already. EVERY single problem you've listed is **HARDWARE** related. You don't seem to understand this. Heck, you admit it yourself. *"the buggy GMA965 driver"*. It's Dell's problem to make sure the driver works with their hardware since they're installing ubuntu on it.

What, you mean they did more then grab a laptop and flash ubuntu onto the HD? I can't see their hardware being anything different then most laptops but they didn't configure/test it with the latest version.

Dell's fault, not ubuntu's. *"it uses hardwares that are open and adhere to open standard.. beside most of the issues i spoke about doesnt just affect dell."* Hardware that is open and open standards? I've no idea what your talking about but I fail to see how that matters.

_**If you install and ship an OS on a system, it is the person/company who ships it to make sure that it works on the system.**_

They did, with **Hardy**. Not with Intrepid or Jaunty. How is that ubuntu's fault? Every tired to upgrade from XP to vista? It didn't always work. That must mean vista's broken! *(Well...It 'is' but that's beside the point.)*

Oh, so it affects other systems you personally have tried? I didn't notice you saying you'd tried another system before. Care to refresh my memory? Or is that just you trying to shift the flaming back to ubuntu?

---

### Post by bigbrovar on 2009-04-21
so dell is responsible for the bluetooth regression in hardy, and the state of pulse audio? and the hal bug that broke thinkfinger support? and the regression in the intel-xserver driver that causes screen corruption in ibex? and causes systems to freeze in jaunty.. wow this is cheer leading at its best. i even posted the launchpad bug report of these issues so u know that these are bugs in vital packages that shipped with ubuntu and not only my hardware is affected. how is dell responsible for a problem with HAL .. come on, is your life soo tired to technology that its gets to you when someone criticizes you beloved ubuntu? read my last post again and perhaps take time to visit the launchpad pages for the bugs i linked before you reply saying its my hardware that is at fault. hardwares that worked on hardy and even fedora 10/11 beta

---

### Post by Bios Element on 2009-04-21
> **bigbrovar said:**
> so dell is responsible for the bluetooth regression in hardy, and the state of pulse audio? and the hal bug that broke thinkfinger support? and the regression in the intel-xserver driver that causes screen corruption in ibex? and causes systems to freeze in jaunty.. wow this is cheer leading at its best. i even posted the launchpad bug report of these issues so u know that these are bugs in vital packages that shipped with ubuntu and not only my hardware is affected. how is dell responsible for a problem with HAL .. come on, is your life soo tired to technology that its gets to you when someone criticizes you beloved ubuntu? read my last post again and perhaps take time to visit the launchpad pages for the bugs i linked before you reply saying its my hardware that is at fault. hardwares that worked on hardy and even fedora 10/11 beta

Bluetooth works just 150% fine for me as well. Dell's HARDWARE is responsible for it. PulseAudio is better then ever in Intrepid/Jaunty and I've got a Dell intel laptop which works just fine.

And like I said, go right on ahead and flame me. Your wasting your time insulting me.

And as several people have said, If ubuntu is so horrid, Don't use it.

---

### Post by karellen on 2009-04-21
> **bigbrovar said:**
> so dell is responsible for the bluetooth regression in hardy, and the state of pulse audio? and the hal bug that broke thinkfinger support? and the regression in the intel-xserver driver that causes screen corruption in ibex? and causes systems to freeze in jaunty.. wow this is cheer leading at its best. i even posted the launchpad bug report of these issues so u know that these are bugs in vital packages that shipped with ubuntu and not only my hardware is affected. how is dell responsible for a problem with HAL .. come on, is your life soo tired to technology that its gets to you when someone criticizes you beloved ubuntu? read my last post again and perhaps take time to visit the launchpad pages for the bugs i linked before you reply saying its my hardware that is at fault. hardwares that worked on hardy and even fedora 10/11 beta

man, take my advice and stop getting into these disputes with Ubuntu's fans. it will save you from headaches. there's no point in appealing to reason when talking about something so "religious" as an OS on a Linux forum ;)

---

### Post by bigbrovar on 2009-04-21
> **Bios Element said:**
> Bluetooth works just 150% fine for me as well. Dell's HARDWARE is responsible for it. PulseAudio is better then ever in Intrepid/Jaunty and I've got a Dell intel laptop which works just fine.

And like I said, go right on ahead and flame me. Your wasting your time insulting me.

And as several people have said, If ubuntu is so horrid, Don't use it.

oh great .. dell hardware was good and dandy in hardy right? but all of a sudden became crap in ibex.. yeah maybe you are right my dell hardware which shiped ubuntu hardy heron and worked flawlessly on hardy fedora 10 and 11 must be at fault.. anyway... i have made my point .. its there for all to see. even though i started this i see no reason to continue replying any longer.. u dont have to agree with me but its says ubuntu experience and testimonies . i have stated my story and offered my opinion. i love FOSS and would continue to work towards making it better. the best way i can

 cheers

---

### Post by bigbrovar on 2009-04-21
> **karellen said:**
> man, take my advice and stop getting into these disputes with Ubuntu's fans. it will save you from headaches. there's no point in appealing to reason when talking about something so "religious" as an OS on a Linux forum ;)

good point ;)

---

### Post by ddrichardson on 2009-04-21
> **bigbrovar said:**
> how about if its broken don't release it .. which is my point. how is ubuntu techically then better than windows or Mac when releases ship with known bugs that might break functionality?[]("http://www.bigbrovar.wordpress.com")
Are you suggesting that Windows ships without any known bugs?

---

### Post by wolfen69 on 2009-04-21
> **ddrichardson said:**
> Are you suggesting that Windows ships without any known bugs?

as we all know, windows is perfect.  ;)

btw, what was the OP hoping to accomplish? perhaps vista is more suited for this person. i could always use another windows customer anyway.

seriously bigbrovar, did you do any hardware diagnostics? hardware is not perfect either, ya know. when a windows customer has unexplained problems, i always do diagnostics first. you would be surprised how many times hardware is broken. but people always assume hardware is perfect. go figure.

---

### Post by reis.tiago on 2009-04-21
I really don't get it.

This is a section to tell your personal experience and the OP was telling his experience. 

Also he provided an explanation how it could be better, at least in his own opinion, and most of you guys decide to flame him? 

If he had a computer that worked with a previous version, and decided to try a new version and it had regression problems should he be happy with it?

He also posted solutions on a public available blog. 

If he believes that the quality of the releases could be better why not state it in a place where it is supposed that one leaves his own opinion?

And I agree with him, that if in 6 months ubuntu had so many regressions in his system, something is not going ok. 

I wish I new enough to help and develop Pulse Audio, because in my system it's also half broken.

---

### Post by ddrichardson on 2009-04-21
I certainly haven't "flamed" him but if you state opinion on any public forum then you can't expect people not to voice their opinion, right or wrong. He has been perfectly capable of defending his arguments and has done so.

---

