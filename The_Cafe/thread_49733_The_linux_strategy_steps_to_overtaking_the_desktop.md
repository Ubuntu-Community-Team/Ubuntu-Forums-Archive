---
title: "The linux strategy: steps to overtaking the desktop"
date: 2005-07-17
forum: The Cafe
---

### Post by NoTiG on 2005-07-17
This post assumes that linux has 4 major weak areas, and I will be imagining myself as a military commander who was in control somewhat of an arbitrary amount of resources that I could throw in strategic spots to secure a foothold in the market.

(in order of importance)
Software
Drivers
Codecs
Installing programs

**Software** 

This is the leading issue with linux... it includes entertainment software, productive software, game software

The reason why this is even a problem is because of proprietary microsoft API's.. namely : Visual basic, and directx. If it were not for these, programs would probably be written with free portable languages so that porting software would be a simple process. Therefore I name microsoft proprietary API's as linux's worst enemy

How to solve: 
                    1. you can either wait for more users, which might entice 
                    developers.... 
                    2. or you can encourage developers to use free open API's . For                         example... the open free alternative to DirectX is opengl and SDL. Now I don't think
throwing manpower/resources at opengl will make it go any faster since it relies on a committee before making any changes. But [SDL](http://www.libsdl.org/faq.php?action=listentries&category=1) 2.0 is coming... 

> 2.0 will be a full redesign of the SDL functionality, based on what we've learned over the past four years. The architecture design is partially done, and we'll start prototyping the design soon. As soon as there's a working framework, we'll make it publicly available for comment and contributions. This new framework has about a year or so before we anticipate it being ready for stable release. 

this same logic can be applied to Visual basic. FOr instance... what is the typical language a developer chooses if they dont use VB? Maybe java? Then perhaps send resources to eclipse to help its development?  The option is either to improve the API so they will want to use it, or advertise it more (maybe books? ).

                  3. Improve wine and allow linux to emulate more programs with less errors.

                  4. let the alternative programs naturaly evolve to achieve a state of equivalent functionality (for instance gaim is getting better and better) . A strategy in this area would be to figure out exactly which program would bring the most users. Games dont fit here... so what you have are regular user apps and productive apps. The most imporant app is probably Openoffice, and as it progresses, linux will make inroads in the corporate market.

Drivers

                This mainly includes peripheral devices... but it also includes for instance graphics cards (ATI, and wifi cards(broadcom) etc....

                1. The goal is to somehow improve driver support. The only way i can see is by getting more users, forcing the companies to support their product on linux.  

                2. A database showcasing what peripherals are supported, and which dont work would be nice for the New user, and should be linked to on every distribution site.

               3. Relevant links : [http://tuxmobil.org/pda_linux.html](http://tuxmobil.org/pda_linux.html)
                                           [http://www.linuxprinting.org/](http://www.linuxprinting.org/)
                                           [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

Codecs
             Most new users , after they install ubuntu are left with a crippled media system, because of proprietary codecs. There is a simple work around this... the [automate](http://www.ubuntuforums.org/showthread.php?t=22646) script for new users solves this problem. However, ubuntu is rather devout in a religious zealot sort of way.. about free software and even though the solution can be to simply include this script on the desktop... or even a link to this script.. it regards any instance of non-free software with contempt.

              1. Other distributions have somewhat solved this.. for instance linspire supports media out of the box, but you gotto pay for it.

              2. One of the most convenient features of Mandriva Linux is the way it handles commercial DVD movies. Put an encrypted DVD into your DVD-ROM and the Kaffeine video player pops up a window that checks for the required libraries and codecs. If some are not found -- Win32 and libdvdcss are not installed with the distribution because of legal issues in some countries -- you're told where to go to get them. Click the provided links, download the RPMs, install them using Mandriva's software installer, and within five minutes you have DVD and Windows media file playback capabilities.

             3. At the very least, the user should be informed of this before or during installation... so they are not surprised and know the situation... 

Installing software

              This is one of the pitfallls of linux, and the thing is that we have control over it unlike the other problems. What most new users dont know is that installing software can be **easier** than windows(if its in a repository) , or harder(dependency problems)

              1. The repository file is so important.... Almost everyone has to update their sources.list to have some basic functionality. If there was 1 single howto that was included with the ubuntu desktop... it should be about repositories, and to use synaptic if they can... and provide an easy way to update the sources file.

              2. Repositories are nice... THey provide a central verifiable and easy way to install free software.. which helps prevent spyware/malware...but they do have a caveat: In the future if linux does become more widespread... there is no way that ALL programs will be able to become distributed through the repositories(especially commercial software). Secondly, sometimes the programs that are in the repositories arent updated fast enough... for bleeding edge stuff you need an installer.  

              3. The solution is to take the best of both worlds... continue with a synaptic like utility... but also use **autopackage** . They need to work together, so no dependency problems develope, and so that the system remains stable, and easily updatable.

             4. Linux will not be ready for the average user until [this happens](http://autopackage.org/ui-vision.html)  . The important points are thus:


>  A fundamental assumption of this article is that the concept of installers have flawed usability. Firstly, their usefulness is limited: you typically download them or get them on CD, use them, then throw them away. If you don't throw them away you now have two representations of the application on your system: the installer icon, and the launcher for the app itself. It is a user error to click the installer icon at this point, but that's perhaps not obvious to somebody who doesn't really understand what's going on behind the scenes 

>  So, what would our ideal software installation UI look like? Something similar to the appfolders approach, but with an implementation that lets us take it further would be good. For instance, we should be able to launch software directly from an icon embedded in a web page, decide we like the program and drag it to a panel and send it to a friend by dropping it into an email or IM conversation. This should all transfer the minimum amount of data required, deal with dependencies, and the icon name and appearance should be themable and localised into the users language. 

>  You may be thinking that being able to install and run software direct from a web page is rather bad security, but really it's little different to the user downloading and running a .package, RPM or Windows installer normally. Once the user has chosen to give some software access to their system, we should be making it as easy as possible for them to act upon their decisions. Security therefore becomes a matter of how to aid the user in making the correct decisions rather than making their lives inconvenient.



This remains one of the most important issues in linux as far as the desktop goes... and we have the control. I dont see why google didnt include autopackage in the "summer of code" :/

---------------------------------------------------------------------------------------------

Once these issues become resolved over time... the user needs a reason to switch in the first place. Now I have been trying to think of all the benefits of using linux such as:

customization, virtual desktops, free, networking, stability? security?, better performance on same hardware?, easy keeping the system up to date, better multi-tasking

And while alot of these are nice... what we really need are **dealbreakers** . Firefox garnered its share of users because it featured things people really wanted: tabs, and popup blocking.

Now if I was going to advertise linux somehow... i would have to play its greatest strengths... Virtual desktops for instance, are really handy .. but they are not a _Must-have_  for most people. The greatest strengths of linux for the avg user are IMO(feel free to add your own)

            1. The lack of adware and spyware. Now granted this is partially because they dont target us since we are not as populare. But linux does have a couple of security strengths: passwording , keeping programs from being run as root, the distribution of software by repositories allowing control... and the fact that most software comes with source code. ANy other?

            2. The next biggest strength IMO , that there may be alot who will really want this is: a hardware accelerated desktop. [exa](http://lists.freedesktop.org/archives/xorg/2005-June/008356.html) is a temporary solution. We really need xgl.

            >   Note that you don't have to be a driver 
developer to switch any of those drivers. Note that this also means 
that we can easily give the useless, but oh-so-wanted transparent 
windows to everyone right now. Not next year, not when library X will 
be ready - now, as in today. 
5) Implementing the download/upload/composite hooks will give us enough 
power to have very fancy effects that will let us compete with 
Microsoft/Apple desktops while we work on Xgl.  

The road to the desktop can be won through other avenues. :

Education (edubuntu is working on this)
government
corporate
third world

So what i would do: 

*Greatly help autopackage and just "get there" when it comes to installing applications.([here](https://bugzilla.ubuntu.com/show_bug.cgi?id=8308)  is what ubuntu says in regards to integrating autopackage)
*Greatly help Xgl or whatever it takes for hardware acceleration (on Nvidia, and ATI)
It is more than just eye candy.... alot of people with so-so computers would be greatly helped with "snappiness" if their graphics card helped.....
*help wine. 
*help Openoffice
*help sdl , and advertise sdl + opengl (maybe write a book ? ) for game developers
*Help whatever API will compete with microsofts VB... Maybe mono?
educate/make aware to someone before they install ubuntu maybe about Codecs, where they will have to go to get them if they want them..... About software issues.... and peripheral (printer , pda etc.....) issues.... and maybe some kind of simple database showing what works? I saw on the linspire site they had one but it was kind of slow. 

I think most everything is being done that can be done.. I am just writing this to set straight what i think the main problem areas are (maybe it will help?) and what I would contribute (code) to if i could.

---

### Post by Gnobody on 2005-07-17
There is so much anti-linux fud being thrown around right now, it is even turning the pro-f/oss pesimistic towards desktop linux.  Go on the OSnews or Slashdot, there are now hundreds of Solaris/BSD/Microsoft/Apple trolls everywhere.  Nothing good is said about Desktop Linux or even Gnome anymore.  Even Firefox isn't stealing marketshare as fast as I would have hoped two years ago.  It's sad, desktop Linux isn't even vastly larger than the Mac crowd and there is a BIG price difference.  Game companies like Blizzard and Valve are purposefully ignoring Linux. Microsoft has their "Get the facts" campaign which is even hurting the Linux server market.  Will the Linux community even be as large as it is today in a few years?

---

### Post by NoTiG on 2005-07-17
Well one piece of fud is alll of the articles calling for "time for consolidation" . Unwittingly saying that fragmentation creates to much choice... while it is true that developers end up working on the same things for different situations... fragmentation actually helps the desktop. Here was one slashdotters comment:

> "Pulling together is the aim of despotism and tyranny. Free men pull in all kinds of directions." - Terry Pratchett, "The Truth".

Awesome quote! The problem with the Free Software community is that too few people understand what "free" means. Everytime someone says we need consolidation, or that KDE and GNOME need to merge, or that we have too many text editors and package managers, all they are doing is admitting that they don't know the first thing about freedom. 

> With dozen of different distributions the Linux community is so diffuse that the power or significance of any specific entity is severally limited.

The author clearly missed the point of Open-Source. *The power or significance of any specific entity is severally[sic] limited* so the users have control. That is *why* people want to use Open-Source. Indeed there are few reasons apart from that one. 

> am a windows apologist - look at my history and you will see I entirely willing to point out the failings of Linux to the Zealots as the next guy.

But even I can see that the diversity of Linux is one of its strengths, as well as its weakness right now. Thanks to the sheer variety of work done in exploring slightly different approaches to the same task, we get to experiment with a multitude of approaches and ideas.

While that may not be a truly better product now, it can only lead to an excellent one in the future.

---

### Post by Gnobody on 2005-07-17
[QUOTE=NoTiG]Well one piece of fud is alll of the articles calling for "time for consolidation" . Unwittingly saying that fragmentation creates to much choice... while it is true that developers end up working on the same things for different situations... fragmentation actually helps the desktop. Here was one slashdotters comment:[/QUOTE]
 I agree that autopackage should be used for cross-distro software installation.  People could post their applications on their websites in a .package like they would a .exe for Windows.  And apt/portage/ports/yum work well for packages that are more distro specific.   The problem is way to many people are ignoring autopackage thinking that their specific form of package management is superior and this is some kind of compition.  Autopackage works better than using alienizing things but yet Debian/Ubuntu won't adopt it, why?

---

### Post by UbuWu on 2005-07-17
[QUOTE=NoTiG]Well one piece of fud is alll of the articles calling for "time for consolidation" . Unwittingly saying that fragmentation creates to much choice... while it is true that developers end up working on the same things for different situations... fragmentation actually helps the desktop. Here was one slashdotters comment:[/QUOTE]

Fragmentation helps to a certain extend... but with the massive amount of linux distro's available today which all have some smart people working on them, but almost none have enough developers to reach all the goals they want, some consolidation could really speed up the development process...

---

### Post by poptones on 2005-07-17
First, could you **please** resize that screenshot? It screws up the formatting of the page and makes the article and the replies very hard to read. Your message would be a lot more clear to everyone if you would make the picture smaller.


Now...it's not "zealotry" about liberty (although if there were one thing to be a zealot about, it is that) that prevents those "simple links" - it's the objective fact that, in the US, decss is illegal and even *links to the program* have been ruled libelous. So putting a "harmless link on the desktop" to a decss installer would mean direct liability on the part of Canonical. 

Why do you think linux relies so heavily on support "forums" like this one? **They** don't host the content and are not directly responsible for anything we say. Now, the fact that this forum has "moderators" is potentially troubling for some if anyone wants to be hard nosed about it, but it's still a better shield from liability than none at all.

Mandriva is able to do what it does because it charges money for its distribution. Those DVD players and MP3 and such are not free. Of course some folks will make the "non free" version of mandriva available to the public, but it's not the folks at Mandriva who are doing it. 

Linspire has their "click and run warehouse" for installing software. This does little to address the "problem" of libraries. There is nothing at all stopping me from, right now, creating a program and compiling it complete with all the libraries it needs to run. Except when I do that my 500K program may have grown into a 30MB download. There is little to be done to prevent this except to require all distributions to include certain libraries and certain version of those libraries - and when you do that you have created a widespread target of attack and you have limited everyone's potential for choice because some libraries may not be compatible with others.

There is NOITHING that needs to be done to "help spread linux" that is not being done now. People are talking about it, giving linux to their friends, paying for ads and contributing code and documentation. This doesn't need to be "focused" at all - it needs to be as **diverse** as possible. The entire point of free software is to make something that everyone can use and to enable **the user** to craft it in the manner they like. That is not just a matter of downloading widgets so they can watch reruns of Dawson's Creek. Anyone who just wants a linux VCR can **buy** a linux VCR - it's called a tivo. If that tivo doesn't do exactly what you want it to do then now you have an objective: **learn** to make it dance your dance. It's not my responsibility - or anyone else's - to become a partner to your dance. That doesn't mean, however, I may not *choose* to dance along with you.

Oh, and when you learn that tivo you want will be unable to play hollywood films? Is that the fault of linux or of me? No! It is the fault of you for supporting those hollywood folks and allowing them to exploit the law as they are. So at that point you have a choice to make, don't you? Do you support the hollywood films and go buy another tivo, or do you take a minute to write your representatives and demand they help you in your quest to build the perfect tivo?

This is how change happens. Linux needs to appeal to as diverse a group of people as possible. But the folks who want canned solutions - who want **only** click and run warehouses and rerurns of Dawson's Creek.... they don't care about the rest of it. They're not going to help anyway, their absense at this party is not a liability. 

That's what it's about. The windows installer sucks, synaptic does a far better job right now. The Windows desktop is cartoonishly colorful but underneath it's still that same grey, drab creation it always was, and underneath beats the soulless heart of the undead. The mac desktop is cool but in a really fascist sort of way and I ain't about to dance Steve Jobs' corporate goose step. I've tried a dozen different linux distributions and I found them all poor dance partners. Mandriva looks kinda nice once you put some decent clothes on her, but she wants to lead all the time and I can't deal with that snotty French attitude. Red Hat is... man, just way too corporate and geeky. It's like being stuck on the dance floor with a retired IBM engineer. Gentoo is full of youth and exhuberance and there's some really good work being done by those kids but I'm not willing to make the educational commitment to attend MIT. More power to them that do; I'll look forward to reading the reports and watch in awe from the sidelines. 

As a politically zealous Libertarian conservative, Ubuntu is where I am happy. I am totally digging ravin' with all the hippies. After all, the Free Software Foundation was founded by hippies.

---

### Post by aysiu on 2005-07-17
[QUOTE=poptones]Linux needs to appeal to as diverse a group of people as possible. But the folks who want canned solutions - who want **only** click and run warehouses and rerurns of Dawson's Creek.... they don't care about the rest of it. They're not going to help anyway, their absense at this party is not a liability. [/QUOTE] Who are these folks? I think Linspire's great for migrating people. I recommend Mepis as well. But I use Ubuntu for my primarily OS. What's the big deal? Who are you getting angry with?

I like this article. Just found it through Google News:

[http://www.free-bees.co.uk/software/articles/linuxwindowsalternative.php](http://www.free-bees.co.uk/software/articles/linuxwindowsalternative.php)

---

### Post by NoTiG on 2005-07-17
[QUOTE=poptones]

Now...it's not "zealotry" about liberty (although if there were one thing to be a zealot about, it is that) that prevents those "simple links" - it's the objective fact that, in the US, decss is illegal and even *links to the program* have been ruled libelous. So putting a "harmless link on the desktop" to a decss installer would mean direct liability on the part of Canonical. [/quote]

How about a link to a link?

> 
Mandriva is able to do what it does because it charges money for its distribution. Those DVD players and MP3 and such are not free. Of course some folks will make the "non free" version of mandriva available to the public, but it's not the folks at Mandriva who are doing it. 

Are you saying that a portion of mandrivas money goes to pay licensing issues on being able to play dvd's ? I doubt this... because as i just posted, they lead you toward DeCss... if they had a solution like linspire they wouldnt need to do that.


> 

There is NOITHING that needs to be done to "help spread linux" that is not being done now. People are talking about it, giving linux to their friends, paying for ads and contributing code and documentation. This doesn't need to be "focused" at all - it needs to be as **diverse** as possible. 


I agree... all of the things i listed are being worked on . If i had resources then the areas where i would put them in would be those listed. mainly:

autopackage
openoffice
edubuntu
SDL
(whatever API will compete with microsofts best alternative (mono?)
wine
edit: oh and i just noticed... im not sure if exa is for hardware excelleration or just eyecandy. but if its just accelleration  I would deploy resources into making hardware acceleration (xgl, cario? ) come to being asap.
I feel that some are being adequately developed.. but i think that autopackage really needs some loving.

Whats funny about all these proprietary codecs.. is that they arent even good or innovative... there are open standards which are better. Like how ogg is better than mp3... yet its sort of forced upon us.

As a commander... i wouldnt be interested in you telling me what i cant do... but what i can do. Can i put an auto script link on the desktop? if not.. how about a link to a link? how a bout a small howto telling the user how to enable repositories (including the one that contains decss) . OR ... how about a link to the unofficial forums? they help alot.(would endorsing the unofficial forums make them official? lol)

---

### Post by poofyhairguy on 2005-07-17
[QUOTE=Gnobody] Autopackage works better than using alienizing things but yet Debian/Ubuntu won't adopt it, why?[/QUOTE]

Same reason we don't have SE Linux. Its not ready yet. Ubuntu is not a bleeding edge distro (aka Fedora).

When it is att a certain level (can use apt-get for dependancies) then Ubuntu might have a way to install it.

---

### Post by poofyhairguy on 2005-07-17
[QUOTE=UbuWu]Fragmentation helps to a certain extend... but with the massive amount of linux distro's available today which all have some smart people working on them, but almost none have enough developers to reach all the goals they want, some consolidation could really speed up the development process...[/QUOTE]

Problem is that many would stop developing on Linux if they couldn't do their own thing. People that ask for consolidation of Linux don't understand what drives it.

---

### Post by poofyhairguy on 2005-07-17
[QUOTE=NoTiG]
As a commander... i wouldnt be interested in you telling me what i cant do... but what i can do. Can i put an auto script link on the desktop? if not.. how about a link to a link? how a bout a small howto telling the user how to enable repositories (including the one that contains decss) . OR ... how about a link to the unofficial forums? they help alot.(would endorsing the unofficial forums make them official? lol)[/QUOTE]

You can do that all you want. Ubuntu will NEVER come like that by default though. From the backroom things I have heard...I can promise you that there will probably never have scripts to add dss and codecs and java or whatever non free stuff people want. Most  of the Ubuntu devs (and Mark, the guy paying) care A LOT about free software.

If people really want this, the general idea is "they can fork Ubuntu and do it." Roll out a third party Ubuntu.

The forums are official. Soon backports might be official, but I kinda don't want that to happen because then it might have to drop extras (dss, w32codecs, all that Marillat stuff) for legality.

---

### Post by poptones on 2005-07-17
> **NoTiG]How about a link to a link?

Are you saying that a portion of mandrivas money goes to pay licensing issues on being able to play dvd's ? I doubt this... because as i just posted, they lead you toward DeCss... if they had a solution like linspire they wouldnt need to do that.[/quote]

Yes, they pay for it. I have not used an OOTB Mandriva since it was Mandrake, and at that time they did NOT lead you to it. In fact it was fairly hard to find decss - I found it only by googling for the penguin liberation front (PLF) and I only knew to do that after reading someone else mention "the plf repositories" on a forum. I have no idea if it was a mandrake forum or not - one of the things I hated most was that ridiculously confusing and inconvenient "support forum" they operate. I once had a problem I was willing to pay for, and even AFTER giving them a credit card number I could not locate a link to someone who could give me an answer. That was when I started seriously looking for something better. 

MPEG2 is not a free codec. MP3 is not a free codec. Both require license to distribute, and those licenses aren't free, either. If there is some sort of popup now with a quick link to download and install decss I have no idea how they are getting away with it, except perhaps by making that part of a "world edition" that isn't stocked directly in the US. Mandriva is, after all, a French distro and those French are known for doing their own thing.  

> I feel that some are being adequately developed.. but i think that autopackage really needs some loving.

It is a non solution. It only iomplies a solution. There is simply nothing, given the present structure of linux, that will allow a universal "click and run install." It has nothing to do with the difference between RPM and DEB and everything to do with compiler versions and installed libraries. 

Example: Ubuntu is on OOTB lightweight install that easily fits on a CD and that is one of the things I like most about it. I can put a complete desktop on my laptop with the 3GB hard drive and still have 2.5GB left over for data. If ubuntu included all the crap to run kde (because so many apps require those libraries) now it's grown about 100MB and hasn't bought me a thing - it's just more crap I have to delete. And soon as I do that now that "click and run" installer is broken... taking what else with it? With all those other libraries installed OOTB now developers are going to become more reliant on them, which means it may also break my control panel (try running mandriva without kde installed said:**
> Whats funny about all these proprietary codecs.. is that they arent even good or innovative... there are open standards which are better. Like how ogg is better than mp3... yet its sort of forced upon us.

No, it's NOT forced upon you. If you own the CDs you want to listen to or can borrow them you can rip every last one of them perfectly to flac or ogg with an OOTB ubuntu desktop. If you have an ipod and you want to use them there you can either install an ogg codec or you can rip to flac which, as I understand it, works on ipods without any revision. There are other portables that support ogg and other open formats OOTB, perhaps they would be better solutions than an ipod. 

No one is "forcing" media upon anyone. Media is there as a diversion. It's a distraction from reality. If, in reality, you are forced to deal with an overbearing publisher then perhaps you will decide their distraction is less important to you than ceding to their (lack of) ethic. Again, this is how societies evolve.

> As a commander... i wouldnt be interested in you telling me what i cant do...

Well "commander" I play in no man's army, just so ya know. But if you were "commander" then would you even care if someone told you what you can't do? 

Of course not. So get on the horn and rally the troupes to lobby for some sensible laws. People get pissed at me when they talk about "their rights" and I tell them **the law says this** and you are wrong - but people **need** to hear that. It's the only way to empower them. If the law sucks, work to change the law. Don't piss and moan about being a victim and boo hoo and woe is me. Change the laws so that everyone can link to decss and you solve the problem at the root. 

Of course by doing that you have also **helped those publishers** retain their control over so much of our society. So, Dorothy... are you a good witch, or a bad witch?

---

### Post by poofyhairguy on 2005-07-17
[QUOTE=poptones] People get pissed at me when they talk about "their rights" and I tell them **the law says this** and you are wrong - but people **need** to hear that. It's the only way to empower them.?[/QUOTE]

I 100% agree.

Laziness leads to servitude.

---

### Post by Gnobody on 2005-07-17
Well the iPod doesn't support OGG Vorbis (well almost if you count iPod linux but it still studders on OGG Vorbis playback), and FLAC is overkill for most.  Most of the music/movie services out there are using heavily DRMed formats like WMA/WMV and Apple, the market leader, using their Fairplay DRM on AAC. Mpeg2 is forced on everyone who buys a DVD.  Non-free formats are everywhere and the average computer user is oblivious to this, and they think Ubuntu is inferior because it doesn't play their non-free stuff out of the box.  When will people rise against propriatary formats?

---

### Post by Stormy Eyes on 2005-07-17
Oh jeez, not this crap again. "Linux isn't ready for the average user, blah-blah-blah..." Quite frankly, Linux isn't going to really progress until Linus, Miguel de Icaza, Rasterman, and all the rest give Grandma the finger.

My father knows next to nothing about Linux, but I installed Knoppix on his machine last week, showed him how to pull pictures off his digital camera, use the GIMP OpenOffice, browse the web, and get his email. If he isn't an "average user", then who is?

Grandma doesn't matter. She'll be dead in ten years, twenty at most. Let Bill Gates deal with the past, and take the future for ourselves.

If this makes me an elitist pig, then so be it. But I'm tired of everybody saying we should cater to the lowest common denominator. That's the kind of thinking that made Britney Spears a household name. To hell with the lowest common denominator.

---

### Post by poptones on 2005-07-17
[QUOTE=Gnobody]Well the iPod doesn't support OGG Vorbis (well almost if you count iPod linux but it still studders on OGG Vorbis playback), and FLAC is overkill for most.  Most of the music/movie services out there are using heavily DRMed formats like WMA/WMV and Apple, the market leader, using their Fairplay DRM on AAC. Mpeg2 is forced on everyone who buys a DVD.  Non-free formats are everywhere and the average computer user is oblivious to this, and they think Ubuntu is inferior because it doesn't play their non-free stuff out of the box.  When will people rise against propriatary formats?[/QUOTE]
 LOL stormy eyes. I like the sentiment of the last part, not sure I agree at all with the first.

If "joe user is trapped by the man" then duhhhhhh... we need to educate "joe user" on how this has happened! You don't do that by playing Steppin Fetchett to the massa, you do it by providing a compelling alternative to plantation life. There is a buttload of **really good artwork** available in the Free world. 

This is a cultural issue. Do you want a culture of the Free, or a culture of the owned? You can play both sides at once, but wheere the rubber meets the road you **do** have to pick a side.

---

### Post by Stormy Eyes on 2005-07-17
[QUOTE=poptones]If "joe user is trapped by the man" then duhhhhhh... we need to educate "joe user" on how this has happened![/quote]

Stop trying to save Joe User from himself. Joe User wanted what he's got: his culture of the owned. Don't bother trying to educate those content with ignorance. Don't bother trying to set free those content with bondage. Don't try to save those bent on destroying themselves. You'll only annoy them and waste your time.

Let Joe User have his Windows. Let him have his proprietary formats. Let him have his perpetually copyrighted culture. Let him have his slavery, and let him be damned.

Save yourself instead of trying to save others. Do as you will, take what you want, and pay the consequences.

[QUOTE=poptones]you **do** have to pick a side.[/QUOTE]

I already did: I am on *my* side, serving no cause other than my own happiness.

---

### Post by MetalMusicAddict on 2005-07-17
[QUOTE=Gnobody]Well the iPod doesn't support OGG Vorbis (well almost if you count iPod linux but it still studders on OGG Vorbis playback), and FLAC is overkill for most.  Most of the music/movie services out there are using heavily DRMed formats like WMA/WMV and Apple, the market leader, using their Fairplay DRM on AAC. Mpeg2 is forced on everyone who buys a DVD.  Non-free formats are everywhere and the average computer user is oblivious to this, and they think Ubuntu is inferior because it doesn't play their non-free stuff out of the box.  When will people rise against propriatary formats?[/QUOTE]
I dont mind propriatary formats that just work, let you do what you will with themand are free. DRMed formats as they are now seem to restrictive. My entire 1000+ CD collection is in high quality VBR MP3s. Ogg is awesome but Im OCD and Im not about to re-rip everything. Unfortunately lack of support for other formats has also made my hesitant on some hardware. I was delighted when I found the iRiver Hxxx series. I bought a H340 which supports Mp3, WMA, WAV and Ogg Vorbis.

Part of why I dont mind propriatary goes into the above posts.

"Too many bosses" Its something Ive heard in my working life. Too many people having a say over something. Which is how Ive seen alot of open-source apps go. Too many people having a say in something can slow a project to a crawl.

Ive seen also where If people have differing opinions on projects fork them and do well. Thats whats great about open source. But it can be bad also. Some developers dont like it at all. I thought thats whats its all about making it your own and sharing it. I have over the last couple of months watched [GIMPshop](http://plasticbugs.com/index.php?p=241) take shape. Theres also a [Windows version](http://blog.yumdap.net/archives/20-GIMPshop-for-Windows.html) now. But Sven a GIMP team member was so pissed about it. Read [HERE](http://gug.sunsite.dk/forum/?threadid=2721&PHPSESSID=421d910149220317b675a49cb01fedd4). 

I understand alot of the arguments in the link but I have always been under the impression that the biggest strength was choice? 

I actually dont believe this. As a user I dont mind closed as long as its free and plays well with others. A lack of focus is what I think some apps really lack. Sometimes focus can only be achieved by having a couple of bosses only.

Im prepaired for the lashing. :)

---

### Post by poptones on 2005-07-17
> I dont mind propriatary formats that just work, let you do what you will with themand are free.

Like water that isn't wet? Proprietary means "not free." There is no such thing as "free and proprietary." There is free as in beer, but that's not free that's just free of charge. The english language has been corrupted by this vaguary. 

> Too many people having a say over something. Which is how Ive seen alot of open-source apps go. Too many people having a say in something can slow a project to a crawl.

This is why code talks. The "gimp shop" project is a great example. It's not too many cooks, it's just two different expressions of the same idea. It's bloody fantastic, it makes Liberty an even more savory boufe' to draw out those too afraid to leave the plantation. 

> As a user I dont mind closed as long as its free and plays well with others. 

But you have no way of ensuring "closed" will play nice. It might be a nice massa now, but you are owned and you have no recourse if things turn bloody. Any corporation or company has the tendency to be all fuzzy and cozy until it gets enough mass to draw in investors. Soon as that happens, you have no defense against the strap.

---

### Post by dickohead on 2005-07-17
[QUOTE=MetalMusicAddict]I dont mind propriatary formats that just work, let you do what you will with themand are free. DRMed formats as they are now seem to restrictive. My entire 1000+ CD collection is in high quality VBR MP3s. Ogg is awesome but Im OCD and Im not about to re-rip everything. Unfortunately lack of support for other formats has also made my hesitant on some hardware. I was delighted when I found the iRiver Hxxx series. I bought a H340 which supports Mp3, WMA, WAV and Ogg Vorbis.

Part of why I dont mind propriatary goes into the above posts.

"Too many bosses" Its something Ive heard in my working life. Too many people having a say over something. Which is how Ive seen alot of open-source apps go. Too many people having a say in something can slow a project to a crawl.

Ive seen also where If people have differing opinions on projects fork them and do well. Thats whats great about open source. But it can be bad also. Some developers dont like it at all. I thought thats whats its all about making it your own and sharing it. I have over the last couple of months watched [GIMPshop](http://plasticbugs.com/index.php?p=241) take shape. Theres also a [Windows version](http://blog.yumdap.net/archives/20-GIMPshop-for-Windows.html) now. But Sven a GIMP team member was so pissed about it. Read [HERE](http://gug.sunsite.dk/forum/?threadid=2721&PHPSESSID=421d910149220317b675a49cb01fedd4). 

I understand alot of the arguments in the link but I have always been under the impression that the biggest strength was choice? 

I actually dont believe this. As a user I dont mind closed as long as its free and plays well with others. A lack of focus is what I think some apps really lack. Sometimes focus can only be achieved by having a couple of bosses only.

Im prepaired for the lashing. :)[/QUOTE]
 Just a few things in response to this fantastic thread!

1. - If the IPod doesn't support OGG - buy something else? They're really not that great!

2. - Diversity is exactly what we need, I know so many Windows users who are so sick and tired of the same old crap, and the second I show them just how vast one area of the OSS community is, they almost die with excitement - granted most of them stay on Windows because of gaming, they do all show great interest and begin using OSS on Windows.

3. - "Joe User" is you, me and the other guy before we knew better - if *we* don't show people there is an alternative, the alternative will never exist.

4. - I know this isn't a very popular opinion, but Linux/OSS DOES need some form of uniformism, but why do you all assume this doesn't already exist? People are drawn to Linux/OSS by the likes of SuSE, Fedora, Linspire etc, from there they can do what they want, will they choose Mandriva, Slackware, Gentoo, Ubuntu or Debian, either way THEY are making that choice, which is what freedom is all about - the freedom to choose what YOU want, Linux/OSS already gives people that power, but with anything "free" there are always strings attatched, the strings here are vast, vary in length and don't always lead to the same result, but they do all lead somewhere.... I'l stop talking with metaphores and use this example:

Gaming: Wine, Transgaming or native ports(Quake) - you DO have choices.
Office software: Wine, OpenOffice, KOffice, StarOffice etc etc - yet again - choices!
Support: Forums, Distribution Support, 3rd Party Support, Google etc etc - looky here - choices!!!

If you haven't got my drift already, there are so many choices that a Linux user can make it makes my head hurt, but there are always 2 main choices you make: are you prepared to learn? or are you prepared to pay? For the vast majority of us in this forum, we chose to learn, which is how we found Ubuntu, for those using Linspire/RH/SLE/Mandriva etc, they chose to pay -but who cares, they chose! In a windows world.... you Pay or you illegally obtain..... what a choice!

So are you getting the picture? If we can manage to point out to people that the only power we really have is choice, then pretty soon we will see that Linux/OSS IS for "Joe User" we just need to make them aware that there is a choice. If they want to pay for Windows - good for them, I wish them luck, and hope support and stability get better, but if they choose something else - I hope they do it for their own reasons because they were well educated enough to make a decision.

---

### Post by poofyhairguy on 2005-07-17
[QUOTE=Stormy Eyes]Stop trying to save Joe User from himself. Joe User wanted what he's got: his culture of the owned. Don't bother trying to educate those content with ignorance. Don't bother trying to set free those content with bondage. Don't try to save those bent on destroying themselves. You'll only annoy them and waste your time.

Let Joe User have his Windows. Let him have his proprietary formats. Let him have his perpetually copyrighted culture. Let him have his slavery, and let him be damned.

Save yourself instead of trying to save others. Do as you will, take what you want, and pay the consequences.
[/QUOTE]

You say that now stormy...and I kinda agree with you. But life will suck when my broadband gets cut off because I "don't have a trusted (computing) OS."

Marketshare is a good thing.

---

### Post by MetalMusicAddict on 2005-07-17
[QUOTE=poptones]But you have no way of ensuring "closed" will play nice. It might be a nice massa now, but you are owned and you have no recourse **if** things turn bloody. Any corporation or company has the tendency to be all fuzzy and cozy until it gets enough mass to draw in investors. Soon as that happens, you have no defense against the strap.[/QUOTE]

**If** things turn bloody. You end up with the same choice if the "open" format you use suddenly tanks. Use something else. You cant go through life expecting the worst of things. Youll just end up making that crappy life come true. "The Man" is not always out to get you. ;)


Also, lay off all the "massa" references. I get the way you mean it but in a public fourm you never know who your talking to and some people find it more than mildly offensive.

Isnt this getting just a little off topic. NoTiG has had alot of points that havnt been touched on.

---

### Post by dickohead on 2005-07-17
[QUOTE=MetalMusicAddict]**If** things turn bloody. You end up with the same choice if the "open" format you use suddenly tanks. Use something else. You cant go through life expecting the worst of things. Youll just end up making that crappy life come true. "The Man" is not always out to get you. ;)


Also, lay off all the "massa" references. I get the way you mean it but in a public fourm you never know who your talking to and some people find it more than mildly offensive.

Isnt this getting just a little off topic. NoTiG has had alot of points that havnt been touched on.[/QUOTE]
 Not intending to sound ignorant, but i know i just have - what is "massa" anyway? and don't tell me it's a nomad tribe from babylon - cos that would make no sense in this context!

---

### Post by poptones on 2005-07-18
Some people just **have** to take offense at anything. They take the mere mention of slavery or sharecropping or even plantations into some sort of racist remark. Sorry, I don't play the PC game. the analogy is entirely valid and I am by no means the first to employ it.

Many people in my family have been sharecroppers in my lifetime. I have every right to speak about things in this context. Do you? Maybe I am offended by your indignance.

---

### Post by aysiu on 2005-07-18
[QUOTE=dickohead]Not intending to sound ignorant, but i know i just have - what is "massa" anyway? and don't tell me it's a nomad tribe from babylon - cos that would make no sense in this context![/QUOTE] No, it's not a nomad tribe in Babylon.

According to [Wikipedia](http://en.wikipedia.org/wiki/Massa):>  Massa is a town in Italy. It forms, with the town of Carrara, the province of Massa-Carrara of which, it is the capital, in the north of Tuscany.

Most likely, though, the [Urban Dictionary](http://www.urbandictionary.com/define.php?term=massa) definitions are more on target for this particular context: "how the old school black dudes said master"

---

### Post by TravisNewman on 2005-07-18
"Soon backports might be official, but I kinda don't want that to happen because then it might have to drop extras (dss, w32codecs, all that Marillat stuff) for legality."

Bit of a correction here, backports is sanctioned by Ubuntu, not sure if it's flat out official, but regardless, hoary-extras (and breezy-extras, etc) will continue as a separate project not sanctioned by Ubuntu, so we don't have to worry about losing it.

---

### Post by poptones on 2005-07-18
> You say that now stormy...and I kinda agree with you. But life will suck when my broadband gets cut off because I "don't have a trusted (computing) OS."

Why would you not employ a TCPA-enabled OS? The hardware is coming; apparently you think that technology won't make it into linux?

TCPA will be part of linux as soon as the platform is well enough defined for the hardware to become reasonably pervasive. The internet has Billions of devices talking across it, most of which could never be made "trusted" because the hardware is too minimal to support it. These devices are not going to be barred from the network. 

At worse you would have to find someone in the neighborhood running a "Free" wireless port or pay a little extra for an "insecure connection" from your ISP.

---

### Post by NoTiG on 2005-07-18
[QUOTE=poptones]

 People get pissed at me when they talk about "their rights" and I tell them **the law says this** and you are wrong - but people **need** to hear that. It's the only way to empower them. If the law sucks, work to change the law. Don't piss and moan about being a victim and boo hoo and woe is me. Change the laws so that everyone can link to decss and you solve the problem at the root. 

[/QUOTE]

I see what you are saying... but you cannot rely on everyone to act the way you are, and do the right thing. most people don't care. So... rather than being so rigid on an issue like this... FIRST get users... and once you have a larger base of people... then the issue can transgress, because then people are forced to care. If you told them "oh you cant do this on linux  because of these proprietary reasons" they might never switch... but if you make an automate script that does it for them.. then further down the road the people can make a stand.

---

### Post by poptones on 2005-07-18
Huh? One has little to do with the other except through coincidence. It's not just linux users who are screaming about "rights being taken away" via DRM and copy protected CDs and such. It doesn't matter if they use linux or a mac or a subaru, hating on media corporations is the thing to do now and most folks I encounter don't know the first thing about their "rights" according to the law, only what they *imagine* because that gaping "analog hole" made encforcement of the **actual law** nearly impossible to police. People love waxing on poetic about the exciting new possibilities of this realm and all that, but when the same technology is used in a way **they don't like** it's suddenly all just one big conspiracy against them. Just look at the way folks here tend to view DRM and TCPA.

I doubt many folks would argue we as individuals should not have the right to protect our data by locking it up however makes us feel most secure - but where are they when that same technology is used to protect the rights of *others* they don't happen to agree with? This is no strawman... start a new discussion and speak up, I'm curious.

I don't care if people use linux. I will point and laugh at those who refuse to even try it and will listen with only moderate disdain to those who care to explain why they tried it and gave it up. But whether or not someone uses linux, odds are pretty good they have a TV and they listen to music if even just occasionally. Maybe it works the other way for them? I know a few who are like that - it's not MS they have the problem with, it's Disney and FOX and MTV. There are alternativs for them, too. And maybe when they start spending time at Magnatune they find themselves exploring other CC sites and *that* convinces them to give linux a try...

---

### Post by NoTiG on 2005-07-18
> It doesn't matter if they use linux or a mac or a subaru, hating on media corporations is the thing to do now and most folks I encounter don't know the first thing about their "rights" according to the law 

That crusade is secondary to me. what i meant by force.... was that the difference is on wndows... you may not be able to Copy a protected dvd.... but at least you can **watch **  it. Now imagine if you converted a bunch of ppl to linux. Then all the sudden... if they couldnt simply watch a dvd.. they would be forced to take a stand :P

is decss illegal because... they dont get a small sum of money for their proprietary decoder? or because it allows you to make copies? I noticed that on windows... I was trying to take a screenshot of the round door in the Lord of the rings hobbit house... and it wouldnt let me >< somethiing i could do easily with linux , decss.... pffffft. Oh yea it also lets you skip advertisements. I think the majority of the population would vote to legalize decss if they even knew about it (or if there was a vote) .. I also noticed that you can get a dvd player really cheap... like around 30-40 bux, and theres not much of a price difference between that and a skeleton drive (which should be cheaper because it has no casing/less parts) for a computer. I bet the cost of the actual decoder is like 5 cents. ANd people shouldnt be forced to use a hardware decoder... and if one can be developed for free then why should they have to pay for a proprietary one.

---

### Post by poptones on 2005-07-18
Decss is illegal because it infringes a patented technology. It's not authorized by the patent holder AND because it is a tool that has no other purpose than to allow individuals to defeat encryption and that was made illegal. 

And DVD players are so cheap because the publishers want everyone to have cheap dvd players - but dvd players that are "authorized" by them. It's not about money - if they had to they would give you the DVD players. It's about control. The CD format is insecure and it is going to be killed just as soon as the publishers can get DVD-audio capable players in the living rooms of america. Those DVD players you buy now for forty bucks are gonna be good for a couple more years, maybe.

---

### Post by dickohead on 2005-07-18
[QUOTE=poptones]Decss is illegal because it infringes a patented technology. It's not authorized by the patent holder AND because it is a tool that has no other purpose than to allow individuals to defeat encryption and that was made illegal. 

And DVD players are so cheap because the publishers want everyone to have cheap dvd players - but dvd players that are "authorized" by them. It's not about money - if they had to they would give you the DVD players. It's about control. The CD format is insecure and it is going to be killed just as soon as the publishers can get DVD-audio capable players in the living rooms of america. Those DVD players you buy now for forty bucks are gonna be good for a couple more years, maybe.[/QUOTE]
 Then perhaps we need another alternative to DECss, one that will allow us to watch DVD's, one that is also authorized by those holding the patent? Or why can we not use the existing patented technology on Linux? Surely it's in their best interest, especially if it is in fact about control, those wishing to do the "wrong" thing will do so anyway by utilising DECss, but those only wishing to do what is "right" should be allowed to do so regardless of operating system..... in my ideal world anyway!

---

### Post by poofyhairguy on 2005-07-19
[QUOTE=dickohead]Then perhaps we need another alternative to DECss, one that will allow us to watch DVD's, one that is also authorized by those holding the patent?[/QUOTE]

So...a legal way? I think the closest you can get to legal dvd playing in Ubuntu is PowerDVD in Wine.

---

### Post by Knome_fan on 2005-07-19
1. I don't think patents are an issue with dcss, but breaking protection is.
2. The solution is quite simple, have a company sell a media player for linux with all the codecs and with dcss.

---

### Post by poofyhairguy on 2005-07-19
[QUOTE=Knome_fan]
2. The solution is quite simple, have a company sell a media player for linux with all the codecs and with dcss.[/QUOTE]

Sounds good to me.

---

### Post by agger on 2005-07-19
[QUOTE=poptones]Decss is illegal because it infringes a patented technology. It's not authorized by the patent holder AND because it is a tool that has no other purpose than to allow individuals to defeat encryption and that was made illegal. 

[/QUOTE]

But that observation is a many-edged sword.

Not too long ago, Richard Stallman wrote in The Guardian, in an article about software patents:

"A 2004 study of Linux, the kernel of the GNU/Linux operating system, found that it infringed 283 different US software patents."

(cf. [http://www.guardian.co.uk/online/comment/story/0,12449,1510566,00.html](http://www.guardian.co.uk/online/comment/story/0,12449,1510566,00.html)  )

I am pretty sure the same thing might apply to FreeBSD or OS/X - the whole patent scene has become so "fuzzy" because of the ease with which patents are granted, that *everybody's* infringing patents all the time - at least in the software business.

---

### Post by poptones on 2005-07-19
It doesn't matter if linux infringes ten thousand patents - if the patents are so precarious (which they most likely are) they cannot be adequately defended. And who would one file suit against? Any infringement action would be only against the developer or small team centered around any particular technology. This is a reasonably effective shield provided by OSS (but it is also the liability that hold back so many licensing issues). 

When infringements are identified they are generally targeted for revision. This has happened with linux in a couple of very high profile cases centered around actions brought by SCO back when that tiger was so on the prowl. The targeted code was removed and replaced in a matter of days -  as would happen the instant anyone else brought suit, thus rendering any such action moot. This is an endemnity issue for corporate users, but it's effectively a non issue for individuals.

There's nothing preventing someone from offering a binary only linux DVD player - except that most likely no one would buy it. If someone like Linaire or whatever they're called wanted to bundle a dvd player that might be an effective option, but for personal desktops it would be a pointless effort, since everyone already has that capability and most don't seem to know (or care) they are violating US law. 

Seriously... just watch. You are going to see a significant hyping of "HD technology" in the very near future. Manufaturers of course want nothing else more than to sell boatloads of new hardware, and publishers are going to do all they can to help hype this technology - because it is "secure." It has little to do with quality so much as with making the hardware as pervasive as possible as ASAP so they can begin killing off the DVD and the music CD. Ready or not, you're soon going to have to start making that tough choice... who are you going to support?

---

### Post by Knome_fan on 2005-07-19
1. Even stupid and precarious patents are enforcable, at least in the US.
2. Patents matter a whole lot to linux. Developers, distributors and users could be sued.
3. The SCO isn't about patents, but about a breach of contract.
4. As SCO still was unable to show that there was any code in Linux that they hold rights to no code had to be rewritten.
5. Linspire already sells a DVD player with dcss to its users.

---

### Post by poptones on 2005-07-19
1. Patents are enforced via lawsuits. Decss is illegal and anyone using it could be sued. The logistics of actually doing this make it impossible. Ergo, decss is illegal and libelous and yet it continues to be readily available. Developers outside the counties of jurisdiction maintain the technology and life goes on. Call it distributed IP. 

2. I pointed this out already in my own post. I also explained why it's a non issue. Individual developers are not deep pockets and most developers take great pride in avoiuding proprietary technology whenever it is pointed out to them. Any infringing technology is pretty readily replaced which renders any further action moot.

3. Yes, "the SCO" WAS about about patents at least so far as one prong of their attack was to try to point out how the linux kernel was "blatanty violating IP laws" and they pointed to some code in the multiprocessing kernel. The code was removed and replaced within a mater of days. Perhaps you know more about this than me and can explain it in more detail; I'd google it but I'm too lazy, I've been up now about 40 hours and am just having a larf before bed...
5. I believe that point has been made repeatedly. Do you have something to add?

---

### Post by MetalMusicAddict on 2005-07-19
I really doubt CDs will start to die off soon. I think their too entrenched and too widely used to be ousted any time soon. There is just nothing that attractive as an alternative. SACD and DVDA just arent worth it. Their just not that much better. People just dont really get/hear the difference between the 2 and multichannel music is, well IMHO not that neat. At least not enough to get rid of the 4 CD players I have. :) As a trained audio engineer I look into new formats often.

Now DVD movies I think will be different. Ive seen demos of Blue-Ray and HD-DVD on HDTVs. That is a BIG step up in quality/experence. Not so much the audio but the picture. Jesus. It was nice.

---

### Post by MetalMusicAddict on 2005-07-19
EDIT: Actually when I thought about it I dont care. :EDIT

---

### Post by Knome_fan on 2005-07-19
> **poptones]1. Patents are enforced via lawsuits. Decss is illegal and anyone using it could be sued. The logistics of actually doing this make it impossible. Ergo, decss is illegal and libelous and yet it continues to be readily available. Developers outside the counties of jurisdiction maintain the technology and life goes on. Call it distributed IP. 
[/quote]
Again. Dcss is not a patent issue and if you think nobody got sued over it you must have lived on a different planet the last 5 years. 
But one of the reasons why nobody is sued at the moment is because nobody is officially distributing it, apart from linspire, but they do have a license.

[QUOTE=poptones]
2. I pointed this out already in my own post. I also explained why it's a non issue. Individual developers are not deep pockets and most developers take great pride in avoiuding proprietary technology whenever it is pointed out to them. Any infringing technology is pretty readily replaced which renders any further action moot.
[/quote]
Again, just because you think it is a non-issue doesn't make it a non-issue. And you don't seem to understand what patents are about. This is not about avoiding propietery code, it's about avoiding things like the double click on small devices, the progress bar, having preview pictures on your web page or comparing variables with IsNot when programming. (Yes, all this stuff is patented or about to be patented). 
Further, the whole free software movement, for example the FSF, is in absolut disagreement with your position.

[QUOTE=poptones]
3. Yes, "the SCO" WAS about about patents at least so far as one prong of their attack was to try to point out how the linux kernel was "blatanty violating IP laws" and they pointed to some code in the multiprocessing kernel. The code was removed and replaced within a mater of days. Perhaps you know more about this than me and can explain it in more detail said:**
> 
Patents are not the same as IP laws and though SCO probably alleged at one time that Linux was infringing patents, they also alleged that free software was unconstitutional, which proves that SCO talk a lot of crap, but not that the SCO case is about Patents, which it is not. And please show me the code that was pointed out and removed, thanks, I'm certain you are wrong here.


[QUOTE=poptones]
5. I believe that point has been made repeatedly. Do you have something to add?
Huh?

---

### Post by poptones on 2005-07-19
Ummm... I was responding to another post. So how is it **I** "pulled" *anything*?

---

### Post by poptones on 2005-07-19
[QUOTE=Knome_fan]Again. Dcss is not a patent issue and if you think nobody got sued over it you must have lived on a different planet the last 5 years. [/quote]

Decss was oringially a "trade secret." However that wasn't enough to keep an injunction in effect and so the plaintifs "reframed" the case as a stopgap while the whole DMCA issue was resolved. Encrypted DVDs, however, *are* very much protected by patent - numerous patents, in fact. No license, no encrypted DVD playback capability. The rest of the chain was covered the usual way - for example, when you buy a DVD carriage a portion of the money spent goes to those who own patents on various parts of the mechanical playback process. But to sell a player that can play *encrypted* DVDs in the US one is supposed to be licensed, and the licensor has all sorts of rules governing what is an acceptable device - for example, no RGB outputs. Thus we have YPbPr "component" transmission for "consumer" video even when that actually requires extra circuitry in the device to convert it from the more commonly used internal RGB format. 

And I never said "no one got sued." I said it was impractical if not downright impossible to sue linux, decss or any other information out of existence. The very fact we are here discussing the ethics of using this tool that folks have been "sued over" is proof that assertion is, in fact, correct. Decss is a libelous bit of information, and yet it's just a click away from anyone wishing to utilize it.

> But one of the reasons why nobody is sued at the moment is because nobody is officially distributing it, apart from linspire, but they do have a license.

But the linspire player, last I looked, did not use "decss." That DVD player is a binary only, not open source, not open in any way standalone player. It's not like if you pay for Linspire you get *legal* command line tools that let you rip unencrypted VOBs from encrypted discs. 

> Again, just because you think it is a non-issue doesn't make it a non-issue. And you don't seem to understand what patents are about. This is not about avoiding propietery code,

Ummm.. no that would be copyright infringement. Patents protect devices or methods - like FAT32 or those widgets you mentioned. Where did I state otherwise?

SCO has *often* added "patent" to its list of offenses - much of the time the case they ried to make was *entirely* about patents on various UNIX methods (which linux of course supports) which they claimed they purchased and still owned. 

> Patents are not the same as IP laws

Well, far be it from me to disagree with [The World Trade Organization.](http://www.wto.org/english/tratop_e/trips_e/intel1_e.htm) What do you think "IP" means, anyway? Rusty Bedsprings?

> And please show me the code that was pointed out and removed, thanks, I'm certain you are wrong here.

[url=http://lwn.net/Articles/36164/
]Here's an article on the RCU business.[/url] I never said SCO had a defensible claim - *what I said* was there was a *claim made* - as SCO often did at the time - and that particular code was exorcised from the system... which it was, and in a matter of days. There was quite a bit of press surrounding this action as well, it was hyped as a real world example of the frequent claims of the "self healing" nature of linux - claims made within "this community" which you likewise claim "totally disagrees with my position."

Since this part of the discussion seems to be annoying some nonparticpants I'll make this my last comment in this thread on the matter - but after pointing out this is *entirely* relevant to "linux overtaking the desktop." If multimedia capability were not so widely regarded by the public as something "they" create rather than something **we all create** those laws which regulate "IP" would never have been allowed to evolve with such unfairness. 

Information *can* be controlled, at least to the point that it becomes so inconvenient to not follow the rules that most folks will just reach for their wallet -   and it was the apathy perpeptuated in a naive atmosphere of "we'll just take what we want because we can" that *allowed* things to come to this. Do you really think it's in our best interest to continue along the footworn path that first led our culture into this sort of trap?

---

### Post by NoTiG on 2005-07-19
So when blu-ray comes out is linux going to be left out? is it going to be proprietary? are we going to have another Decss for it or are we screwed?

also.. what is the video codeca alternative to mpeg , like ogg is to mp3?

---

### Post by Knome_fan on 2005-07-19
> **poptones]Decss was oringially a "trade secret." However that wasn't enough to keep an injunction in effect and so the plaintifs "reframed" the case as a stopgap while the whole DMCA issue was resolved.[/quote]
So?

[QUOTE=poptones]
Encrypted DVDs, however, *are* very much protected by patent - numerous patents, in fact.[/quote]
While this might be the case, we are talking about playback, not manufacturing a DVD, so this is a non-issue.

[QUOTE=poptones]
No license, no encrypted DVD playback capability.[/quote]
Indeed, but not because of patents.

[QUOTE=poptones]
But the linspire player, last I looked, did not use "decss." That DVD player is a binary only, not open source, not open in any way standalone player. It's not like if you pay for Linspire you get *legal* command line tools that let you rip unencrypted VOBs from encrypted discs. [/quote]
It's totem with decss.

[QUOTE=poptones]
SCO has *often* added "patent" to its list of offenses - much of the time the case they ried to make was *entirely* about patents on various UNIX methods (which linux of course supports) which they claimed they purchased and still owned. [/quote]
Again, no it's not about patents, it's about trade secrets and breach of contract. You are aware that SCO actually filed a suit and that patents don't play a role in it?

[QUOTE=poptones]
Well, far be it from me to disagree with [The World Trade Organization.](http://www.wto.org/english/tratop_e/trips_e/intel1_e.htm) What do you think "IP" means, anyway? Rusty Bedsprings? [/quote]
Jesus, no patents are not the same as IP laws, patents are a part of IP laws, but IP laws cover a lot more than patents, which was my point. It isn't that hard to understand, is it?

[QUOTE=poptones]
[url=http://lwn.net/Articles/36164/
]Here's an article on the RCU business.[/url] I never said SCO had a defensible claim - *what I said* was there was a *claim made* - as SCO often did at the time - and that particular code was exorcised from the system... which it was, and in a matter of days. There was quite a bit of press surrounding this action as well, it was hyped as a real world example of the frequent claims of the "self healing" nature of linux - claims made within "this community" which you likewise claim "totally disagrees with my position." [/quote]
Huh? Nowhere does the article mention what you claim.
[quote]
RCU is used in several places in the 2.5 kernel. It has, in general, been retrofitted into existing areas of code as a performance improvement. If need be, those patches could certainly be reversed and RCU removed from the kernel. It would slow down 2.6, and have a small performance impact, but it would not be that big of a problem. But that is an issue for the future said:**
> 

Oh and would you please stop to quote me out of context. I said that the whole free software movement totally disagreed with you when it comes to patents being a threat for linux, an issue which you now chose to avoid. 
So please tell me, why did the FSF, the FFII and about every open source project in Europe fight and lobby against software patents in Europe for months now if they agreed with you?

[QUOTE=poptones]
Since this part of the discussion seems to be annoying some nonparticpants I'll make this my last comment in this thread on the matter

...

---

### Post by poptones on 2005-07-19
[QUOTE=Knome_fan]While this might be the case, we are talking about playback, not manufacturing a DVD, so this is a non-issue.[/quote]

Man, I knew it was a waste of time to reply to you. I'm sorry you jsut don't get it, but I'm not going to waste time trying to educate someone who is so obviously only in this to try pushing an argument. Playback of DVDs is absolutely a patent issue. It is *not* simply a matter of authoring DVDs.  That is a ridiculously naive assertion. 


> It's totem with decss.

Funny, that's not what [the linspire folks say.](http://www.linspire.com/lindows_products_details.php?product_id=11804) It also seems they don't have **all** the licenses they need...

* Note: xine does not support locked/encrypted DVDs, as there seem to be legal problems in that area. At this point it is unclear what the legal implications of providing that functionality are.*

That decss ain't in the box. 

If you want to continue this, start a new thread. But do yourself a favor and do some research first, because I'm not going to continue doing it for you.

---

### Post by agger on 2005-07-19
[QUOTE=poptones] Decss is a libelous bit of information, and yet it's just a click away from anyone wishing to utilize it.
[/QUOTE]

Libelous - *libelous*? Libel means defamation, and that can't possibly be what you mean. 

But, sorry, poptones: IP is obviously somehow a very holy cow to you. I think - *I THINK*, just me for myself, that you're trolling.

---

### Post by poptones on 2005-07-19
Ummm.. you're welcome to think whatever you like (of course) but I'mnot the troll here. Unfortunately, I did make the mistake of replying to one.

Libel/liable, they're/their... Like I said: sleep deprivation.

---

### Post by Knome_fan on 2005-07-20
[QUOTE=poptones]Man, I knew it was a waste of time to reply to you. I'm sorry you jsut don't get it, but I'm not going to waste time trying to educate someone who is so obviously only in this to try pushing an argument. Playback of DVDs is absolutely a patent issue. It is *not* simply a matter of authoring DVDs.  That is a ridiculously naive assertion. 
[/quote]
Thanks for not getting personal, I love your style. And I never talked about authoring DVDs, I just said that Decss was not a patent issue. But feel free to provide me with information that contradicts my assertion. Thanks.

[QUOTE=poptones]
Funny, that's not what [the linspire folks say.](http://www.linspire.com/lindows_products_details.php?product_id=11804) It also seems they don't have **all** the licenses they need...

* Note: xine does not support locked/encrypted DVDs, as there seem to be legal problems in that area. At this point it is unclear what the legal implications of providing that functionality are.*

That decss ain't in the box. 
[/quote]
Yes, that's why I said they sell it to their customers. You can buy it at their click and run warehouse. Oh, and I wanted to write its xine + decss, not totem + decss.

[QUOTE=poptones]
If you want to continue this, start a new thread. But do yourself a favor and do some research first, because I'm not going to continue doing it for you.[/QUOTE]

There's no need to continue this, if you stop making stupid assertions and start to educate yourself before posting.
So let's see.

- You claimed Decss is a patent issue, yet you provided no prove for that whatsoever.

- You claimed that patents are no problem for free software, yet you fail to provide anything resembling an argument for your assertion and you still can't explain why the whole free software movement is wrong on this subject but you are right.

- You claimed that the SCO case was about patents, yet patents are absolutely no issue in the court case and you still failed to provide anything that shows that they do play a part in it.

- You claimed that dubious code was found in the linux kernel during the whole SCO mess and promptly removed, yet you still were unable to provide any evidence for this assertion.

And no, calling me a troll will not make this go away.

---

### Post by DarthBagel on 2005-07-20
> - You claimed Decss is a patent issue, yet you provided no prove for that whatsoever.


[http://www.webopedia.com/TERM/D/DeCSS.html](http://www.webopedia.com/TERM/D/DeCSS.html) 

The DeCSS package is in violation of the DMCA making it illegal in the US.  Google it, there are many places that will say the same.  I don't mean to troll, just thought the info would be useful  :-)

---

### Post by Knome_fan on 2005-07-20
[QUOTE=DarthBagel][http://www.webopedia.com/TERM/D/DeCSS.html](http://www.webopedia.com/TERM/D/DeCSS.html) 

The DeCSS package is in violation of the DMCA making it illegal in the US.  Google it, there are many places that will say the same.  I don't mean to troll, just thought the info would be useful  :-)[/QUOTE]

You are of course right. But violating the DMCA is something totally different from a patent issue, which was my point.

---

### Post by poofyhairguy on 2005-07-20
[QUOTE=NoTiG]So when blu-ray comes out is linux going to be left out? is it going to be proprietary? are we going to have another Decss for it or are we screwed?[/QUOTE]

Screwed at first till its hacked (last time it was because of a crappy software Dvd player). Might be years....

> also.. what is the video codeca alternative to mpeg , like ogg is to mp3?

Xvid

---

### Post by poofyhairguy on 2005-07-20
[QUOTE=MetalMusicAddict]There is just nothing that attractive as an alternative.[/QUOTE]

How about ACC or Windows media files. The plastic disks will be made irrelevent.

---

### Post by MetalMusicAddict on 2005-07-20
[QUOTE=poofyhairguy]How about ACC or Windows media files. The plastic disks will be made irrelevent.[/QUOTE]
I think digital only music is a long way off. Especially for those people who actually buy music nowadays. I like to have something physical in my hand. Ive downloaded alot of music but it was always as a preview. If I liked it I bought it. Also CDs are so cheap to produce now smaller labels are doing pretty well. It would put a hurting on them to another (plastic) format because CDs are so widely used.

On the Blue-Ray topic. Wont we be able to get it as a storage medium?

---

### Post by DarthBagel on 2005-07-20
[QUOTE=Knome_fan]You are of course right. But violating the DMCA is something totally different from a patent issue, which was my point.[/QUOTE]

Sorry, guess I misunderstood  :razz:

---

### Post by poptones on 2005-07-20
> **Knome_fan]I just said that Decss was not a patent issue. But feel free to provide me with information that contradicts my assertion.[/quote]

This is why I didn't respond to you the first time you appeared in this thread and why I regret not having noticed who I was replying to the second time. Your comprehension skills are absolutely nil said:**
> Yes, that's why I said they sell it to their customers. You can buy it at their click and run warehouse. Oh, and I wanted to write its xine + decss, not totem + decss.

Too bad you 'wanted to" but didn't. Doesn't matter it's still incapable of playing css protected movies legaly in the US and is not - contrary to what you said - in any way shape or form, distributed with decss. If you add decss after the fact it's no different than adding it to mandrake or ununtu or redhat.. it's still an unauthorized use.

> There's no need to continue this, if you stop making stupid assertions and start to educate yourself before posting.

I agree there is no need to continue it. So why do you bother? Takes two to tango, champ. And it seems quite evident I am not the one so in need of "edcuation" in the matter. I suggest you start with a good english comp course, perhaps that would help you to better *comprehend* the printed word.

>  You claimed Decss is a patent issue

No, *you said* I claimed decss was a patent issue. I said it was a *licensing* issue regarding patented technology *and* it allows unauthorized use by that license holder. IOW it's nothing to do directly with decss, but the *unauthorized use* of that DVD you are decrypting. Do you get it **yet?**

> You claimed that patents are no problem for free software

No, I did not. stop interpreting and read what I said. Quote it here again if you like, this will be my last response to you before you become the first entry in my ubuntu twit list.

> You claimed that the SCO case was about patents

Again, **I** claimed nothing of the sort. I said *this was claimed*. If I tell you "my friend says you are a jackass" have **I** called you a jackass? Have **I** said "you are a jackass?"

Learn to read.

> You claimed that dubious code was found in the linux kernel

Again, See above; LEARN TO READ.

> And no, calling me a troll will not make this go away.

Seem that sabot fits you quite well...

Adios!

---

### Post by MetalMusicAddict on 2005-07-20
Dude why couldnt you just let it go or move this to a PM. Theres no need to continue this in a public fourm. Its childish.

---

### Post by poptones on 2005-07-20
> I think digital only music is a long way off. Especially for those people who actually buy music nowadays. I like to have something physical in my hand.

Exactly, MMA. Lots of folks feel that way. A CD is a convenient way to "back up" your music. Buying a CD is almost like buying a well dressed backup that you can 'restore" onto any device. Unfortunately that's going to come to an end as soon as the DVD transport becomes ubiquitous. If China can make a boombox DVD player as cheaply as a CD player (and essentially, they can) then distributing music on DVDs - with new, proprietary copy protection - becomes the new industry standard. 

This is what consumerism buys you: everything is cheaper, but because it doesn't last and will have to be replaced anyway, platform migration isn't an issue. The upgrade cycle is built in. Obsolescence becomes a feature: it saves us from having to dispose of what would otherwise be **functional** appliances.

I'll say it again: linux doesn't need to "overtake" the desktop. The desktop is increasingly going ot be a **tin fraction** of the computing realm. Linux, the platform, is pervasive and growing. Consumers may not realize what operating system is running their PDA or their cellphone or their blender - but so what? Manufacturers like it and many exploit its openness as a feature; their customers are able to "upgrade" the device themselves; the users themselves create new markets for the product. This is *the good side* of capitalism.

[Look at this](http://linuxdevices.com/news/NS8811342597.html). It can record video via that "analog hole" at up to 512x384. I don't know about you, but if I am watching video on a small screen like that 512x384 seems perfectly adequate. And nothing is to stop you from plugging a blu-ray DVD player into that "analog hole" and it will still be getting higher resolution video than you can record. In fact, if you plug that newfangled HD DVD player into a capture card on a PC it will still get video of about 720x480 resolution, which is all that video port **ever** was able to capture. The fact the video on the DVD itself is encrypted in cca or WMV or PGP - it doesn't matter. It still spits out "standard video" via "standard video ports." All you **don't** get from the "trusted platform" is the built-in capability of legally copying **high resolution video** - which, before the new platform came out, *you never had anyway*. You haven't lost a thing, but you have gained a higher quality program source. 

How people can construe any of this as a bad thing can only be attributed to one factor: they don't care about being free... they just want a free ride.

---

### Post by MetalMusicAddict on 2005-07-20
> **poptones]Exactly, MMA. Lots of folks feel that way. A CD is a convenient way to "back up" your music. Buying a CD is almost like buying a well dressed backup that you can 'restore" onto any device. Unfortunately that's going to come to an end as soon as the DVD transport becomes ubiquitous. If China can make a boombox DVD player as cheaply as a CD player (and essentially, they can) then distributing music on DVDs - with new, proprietary copy protection - becomes the new industry standard.[/QUOTE]
Just for people who missed it. said:**
> I really doubt CDs will start to die off soon. I think their too entrenched and too widely used to be ousted any time soon. There is just nothing that attractive as an alternative. SACD and DVDA just arent worth it. Their just not that much better. People just dont really get/hear the difference between the 2 and multichannel music is, well IMHO not that neat. At least not enough to get rid of the 4 CD players I have.  As a trained audio engineer I look into new formats often.

Now DVD movies I think will be different. Ive seen demos of Blue-Ray and HD-DVD on HDTVs. That is a BIG step up in quality/experence. Not so much the audio but the picture. Jesus. It was nice.
[HERES](http://addict3d.org/index.php?page=viewarticle&type=news&ID=944)  a nice link on CDs vs. SACD/DVD-A

> This is what consumerism buys you: everything is cheaper, but because it doesn't last and will have to be replaced anyway, platform migration isn't an issue. The upgrade cycle is built in. Obsolescence becomes a feature: it saves us from having to dispose of what would otherwise be **functional** appliances.
Planned obsolescence.

> [Look at this](http://linuxdevices.com/news/NS8811342597.html). It can record video via that "analog hole" at up to 512x384. I don't know about you, but if I am watching video on a small screen like that 512x384 seems perfectly adequate. And nothing is to stop you from plugging a blu-ray DVD player into that "analog hole" and it will still be getting higher resolution video than you can record. In fact, if you plug that newfangled HD DVD player into a capture card on a PC it will still get video of about 720x480 resolution, which is all that video port **ever** was able to capture. The fact the video on the DVD itself is encrypted in cca or WMV or PGP - it doesn't matter. It still spits out "standard video" via "standard video ports." All you **don't** get from the "trusted platform" is the built-in capability of legally copying **high resolution video** - which, before the new platform came out, *you never had anyway*. You haven't lost a thing, but you have gained a higher quality program source.
HCMI/HDCP is one way they are trying to plug the hole. 

"HDCP is a content protection technology available for use in connection with HDMI that was developed by Intel Corporation (with input from Silicon Image)."

More info [HERE](http://www.hdmi.org/consumer/faq.asp).

I think you would be able to get higher than 720x480 with [THIS](http://www.pchdtv.com/hd_3000.html) through a s-video cable. Cant quite see all the inputs.

---

### Post by poptones on 2005-07-21
> HCMI/HDCP is one way they are trying to plug the hole.

Plug what hole? HDMI is a digital interface. It has nothing to do with that s-video port or the composite.

> I think you would be able to get higher than 720x480 with THIS through a s-video cable. Cant quite see all the inputs.

720x480 is about all the resolution you're going to get from NTSC, period. Most capture cards have the abilioty to turn off the comb filter on the chrominance line which enables you better than NTSC color detail, but that's about it.

Is it as convenient as ripping at high speed straight from another media? If you're a geek, no. But with tivos being pretty much given away, and the fact most consumers "rip" video by hitting buttons on the remote, the only thing that changes is they now get a *really* good picture and sound from their home theater system.. just so long as it's the media they are authorized for. No one has prevented anyone from making copies... only original quality copies. 

Have you downloaded the Battlestar Gallactica videos? Last season I did like everyone else and downloaded them at the library rather than waiting for their TV appearance. The picture quality may not be HD, but the video and sound quality far exceeds anything available OTA in my area. DRM doesn't make *any* of that go away.

---

### Post by Knome_fan on 2005-07-21
> **poptones]This is why I didn't respond to you the first time you appeared in this thread and why I regret not having noticed who I was replying to the second time. Your comprehension skills are absolutely nil said:**
> 
[http://en.wikipedia.org/wiki/Politeness](http://en.wikipedia.org/wiki/Politeness)

[QUOTE=poptones]
I said decss infringes patented technology. and it bloddy well does, go read that FAQ at dvdcca.org if you doubt it. 

Ehm, it doesn't even mention the word patent...
Try again.

[QUOTE=poptones]
Too bad you 'wanted to" but didn't.
[/quote]
Why? What's so terrible of making the mistake of writing totem instead of xine?

[QUOTE=poptones]
Doesn't matter it's still incapable of playing css protected movies legaly in the US and is not - contrary to what you said - in any way shape or form, distributed with decss. If you add decss after the fact it's no different than adding it to mandrake or ununtu or redhat.. it's still an unauthorized use.
[/quote]
To quote your own link:
> 
How is the Linspire DVD player different from Xine and other DVD players available for Linux?
The Linspire DVD player is actually based on the Xine player, but there are three main differences: First, the Linspire DVD player includes a commercial license for the DVD playback decoding so you don't have to find, buy and install this on your own (this can be expensive and a tricky, complicated process). 


[QUOTE=poptones]
I agree there is no need to continue it. So why do you bother? Takes two to tango, champ. And it seems quite evident I am not the one so in need of "edcuation" in the matter. I suggest you start with a good english comp course, perhaps that would help you to better *comprehend* the printed word.
[/quote]
Sorry dude, I won't let you insult me without responding and I won't let you make false claims without responding.

----------------------------------------------------------------------------------------------------------
[QUOTE=poptones]
No, *you said* I claimed decss was a patent issue. I said it was a *licensing* issue regarding patented technology *and* it allows unauthorized use by that license holder. IOW it's nothing to do directly with decss, but the *unauthorized use* of that DVD you are decrypting. Do you get it **yet?**
[/quote]
[QUOTE=poptones]
Decss is illegal because it infringes a patented technology.
[/quote]

-------------------------------------------------------------------------------------------------------------
[QUOTE=Knome_fan] You claimed that patents are no problem for free software (, yet you fail to provide anything resembling an argument for your assertion and you still can't explain why the whole free software movement is wrong on this subject but you are right.) [/quote]
[QUOTE=poptones]
No, I did not. stop interpreting and read what I said. Quote it here again if you like, this will be my last response to you before you become the first entry in my ubuntu twit list.[/quote]
[QUOTE=poptones]
It doesn't matter if linux infringes ten thousand patents - if the patents are so precarious (which they most likely are) they cannot be adequately defended. And who would one file suit against? Any infringement action would be only against the developer or small team centered around any particular technology. This is a reasonably effective shield provided by OSS (but it is also the liability that hold back so many licensing issues).[/quote]
[QUOTE=poptones]I pointed this out already in my own post. I also explained why it's a non issue. Individual developers are not deep pockets and most developers take great pride in avoiuding proprietary technology whenever it is pointed out to them. Any infringing technology is pretty readily replaced which renders any further action moot.[/quote]

------------------------------------------------------------------------------------------------------------------------
[quote=Knome_fan] You claimed that the SCO case was about patents (, yet patents are absolutely no issue in the court case and you still failed to provide anything that shows that they do play a part in it.][/quote]
[QUOTE=poptones]
Again, **I** claimed nothing of the sort. I said *this was claimed*. If I tell you "my friend says you are a jackass" have **I** called you a jackass? Have **I** said "you are a jackass?" [/quote]
[QUOTE=poptones]
When infringements are identified they are generally targeted for revision. This has happened with linux in a couple of very high profile cases centered around actions brought by SCO back when that tiger was so on the prowl. The targeted code was removed and replaced in a matter of days - as would happen the instant anyone else brought suit, thus rendering any such action moot.[/quote]

-----------------------------------------------------------------------------------------------------------------------
[quote=Knome_fan] You claimed that dubious code was found in the linux kernel (during the whole SCO mess and promptly removed, yet you still were unable to provide any evidence for this assertion.)[/quote]
[QUOTE=poptones]Learn to read. [/quote]
1. See above.
[QUOTE=poptones]
Here's an article on the RCU business. I never said SCO had a defensible claim - what I said was there was a claim made - as SCO often did at the time - and that particular code was exorcised from the system... which it was, and in a matter of days. There was quite a bit of press surrounding this action as well, it was hyped as a real world example of the frequent claims of the "self healing" nature of linux - claims made within "this community" which you likewise claim "totally disagrees with my position."[/quote]
And just as a reminder, your link about this matter didn't support your story.

---

### Post by MetalMusicAddict on 2005-07-21
[QUOTE=poptones]Plug what hole? HDMI is a digital interface. It has nothing to do with that s-video port or the composite.[/QUOTE]

Come on man, I know. Thats why I posted it. Its a new standard they are trying to replace the analog ones with. A digital/copy-protectable interface to plug the analog hole.

> 720x480 is about all the resolution you're going to get from NTSC, period. Most capture cards have the abilioty to turn off the comb filter on the chrominance line which enables you better than NTSC color detail, but that's about it.
Take your own advice man, read the posts/links. :) The card I posted a link to is a Hi-Def card. The new HD-DVD/Blue-Ray players have analog outputs also. Run 'em to this card with a Macrovision filter and you should be able to record the Hi-Def output. Also the card doesnt detect [broadcast flags](http://bpdg.blogs.eff.org/archives/000148.html).

Knome fan dont worry about it man. Let it go. ;)

---

### Post by poptones on 2005-07-21
> The card I posted a link to is a Hi-Def card. The new HD-DVD/Blue-Ray players have analog outputs also. Run 'em to this card with a Macrovision filter and you should be able to record the Hi-Def output.

It doesn't matter. You cannot get "hi def video" over NTSC (composite/svideo) lines. NTSC is inherently bandwidth limited. The closest you can get to "hi def" over NTSC is to run anamorphic higher aspect ratio video, but that still won't get you progressively scanned video or higher pixel bandwidth. A card with *component* inputs might be able to capture high definition video, but I saw no mention of this card having YPbPr analog inputs. There are capture cards like that, but they are not available for $69.95 at the local Fry's and they are not at all common, nor very likely to become common. 

Replacing the "analog hole" with HDMI *might* be possible in another decade or two. Composite video is well established and it's cheap. Most people are not going to buy HD  players if they have to buy a new monitor as well. This is what the FCC has been contending with a decade now in trying to "upgrade" our technical TV broadcast standards.

---

### Post by dataw0lf on 2005-07-21
Let's calm this thread down.  Everyone take a breather. 
Right.  Now.

---

### Post by Knome_fan on 2005-07-21
[QUOTE=dataw0lf]Let's calm this thread down.  Everyone take a breather. 
Right.  Now.[/QUOTE]
Seeing that this thread has totally gone off topic and that a certain poster seems to be very keen to take even the off topic discussions off topic yet again, how about simply closing this thread? 

I'm sure that this would also be fine for the original poster, to whom I'd like to apologize btw. for playing my part in carrying this thread off topic, but I hope he understands what provoked me to do so.

---

### Post by MetalMusicAddict on 2005-07-21
[QUOTE=poptones]It doesn't matter. You cannot get "hi def video" over NTSC (composite/svideo) lines.[/QUOTE]
This is true. The card also has a coax input. I run my plasma over component. The card is ment for over-the-air Hi-Def.

I second the closing of the thread.

---

### Post by TravisNewman on 2005-07-21
It shall be done.

---

