---
title: "Installed Ubuntu, reformatted partition 4 days later"
date: 2005-06-07
forum: The Cafe
---

### Post by bleakcabal on 2005-06-07
Hi, I was a long time Gentoo user ( and a Red Hat user before that ).

When my HD crashed after years of use I decided to reinstall my windows and linux partitions but I decided it was time for a change. 

Gentoo had a long and complicated install process and I didn't want to go through that again.

I browsed the net looking for another distro that would be simpler and less time consuming to work with.

I found Ubuntu.

The installation is really a smooth process that executes quickly and required very little input from my part. Just what I was looking for I tought.

Soon afterwards came the problems.

I had no sound, didn't know how to tell Ubuntu to use my sound blaster instead of onboard sound. Couldn't play video and spent days on the forums looking for help on how to install codecs. XMMS crashed on it's first use after I installed it from Synaptic. Network windows shares worked until I apt-get Samba. Adding repositories is crucial while being cryptic to a new user.

Synaptic on it's first use after installation of Ubuntu gave me error messages that child process were left open and such.

I find that to make anything work is a pain in the butt, particularly when I have to manually compile things. 

Gentoo takes longer to install but after my experience with Ubuntu is far easier to use not only because you have more control but because the packages Just Work   after you install them. When I emerge XMMS under gentoo I can load an mp3 right away and have it play. I don't have to look on the boards to know how to make XMMS work. There are also more packages. 

Ubuntu worked nicely for some things out of the box, but other things did not even work. And when it came time to correct these problems I had to wade through barriers intentionally put there from letting me use my system correctly. I see no reasons why when I install automake it can't set the PATH variables itself or why automake isn't even installed by default.

Also this was the first time I had used Gnome. I found it very amateurish and quickly proceeded to install KDE.

If I could give recomandations to Ubuntu dev :
1- Give the user the choice between KDE and Gnome during install ( having to use Kubuntu instead of Ubuntu is very akward ).
2- Give the user to choose which sound interface ( onboard, sound card ) to use like you do for network interface during install
3- A new user should know that he can add repository in Synaptic ( make it more intuive to someone who doesn't even know what a repository is )
4- Sound should work out of the box, there are many posts on the forums about sound not working, that is totally unaceptable for a major distro.
5- More codecs should be installed out of the box, and when you use Synaptic to install something like Kaffeine it should fetch some codecs, rather than installing Kaffeine and then letting to user have a Kaffeine that can't play any major video format.

---

### Post by vega44 on 2005-06-07
i agree.

---

### Post by Gtaylor on 2005-06-07
Generally it's a good idea to disable your onboard sound via the bios if you have a PCI based card sitting in there. I've had Windows blow chunks at me for having a PCI and Onboard device running at the same time.

Ubuntuguide.org has a lot of good info about repositories and sources and so does the wiki (wiki.ubuntulinux.org).

The choice between KDE or Gnome is done by download Kubuntu or Ubuntu :) Can't get more simple than that. You can also have both by installing Ubuntu and doing an **apt-get install kubuntu-desktop**.

Many codecs can't be installed due to legal issues.

I'm sorry you had problems but you still can't expect to jump right into Linux without doing some reading! It hasn't quite reached that point in development and Ubuntu is still very young. 

Good luck!

---

### Post by oddabe19 on 2005-06-07
Many of those questions are always brought up.

A. The developers want to keep a 1 cd distro (small install). You can't do that having to install 2 desktops, so they give you a choice. Kubuntu or Ubuntu.
B. There are MANY patent issues with many codecs.... which doesn't go with the Ubuntu philosophy by stealing them.
C. The developers want an All-Free distro. If you want to include MP3 you have to pay royalties, etc...
D. Sound problems are consistant with many distros, not just ubuntu. Alsa-base 1.0.8 is very problematic.

---

### Post by Optimal Aurora on 2005-06-07
Well at least in the on board sound department Ubuntu gives you the choice of using it right from the get go (set the bios to use on board sound) or dont use it (by setting it in the bios) unlike other distros... I have to agree though, you have to go in there and set it in the bios and then you might as well reinstall because the setting up phase after the installation is where and when the on-board sound card is originally detected and setup... Other than that, thats about it...

A thing I like is going into apt/sources.lst and changing the hoarys to breezy and doing sudo apt-get dist-upgrade... that is so cool and less time consuming than having download 4 or 5 CDs worth of files just to install fedora or some other distros...

---

### Post by minimidgy on 2005-06-07
Well, Ubuntu sent me 7 install cds for various platforms.  So far I'm quite impressed.  It took me a little bit to figure out how to get my wireless card working.  Actually, for some reason I find it kinda fun tinkering around with the programs to make them work properly.  Also, I can't complain when I get an OS for FREE!

---

### Post by Gtaylor on 2005-06-07
[QUOTE=minimidgy]Well, Ubuntu sent me 7 install cds for various platforms.  So far I'm quite impressed.  It took me a little bit to figure out how to get my wireless card working.  Actually, for some reason I find it kinda fun tinkering around with the programs to make them work properly.  Also, I can't complain when I get an OS for FREE![/QUOTE]
And it will **ALWAYS** be free, what more could you ask for? :)

---

### Post by minimidgy on 2005-06-07
[QUOTE=Gtaylor]And it will **ALWAYS** be free, what more could you ask for? :)[/QUOTE]
Oh, I know. I've always wanted to try linux, and then boom, I ordered some cds of Ubuntu, and it's great! speaking of free stuff, I just got a free bottle of ensure (nutrition drink). I ordered strawberry but those fools gave me VANILLA! oh well, once again, it was free, so I cannot complain.

---

### Post by sapo on 2005-06-07
I think you are blaming ubuntu instead of looking at you...

You are a ubuntu newbie and thats the truth...

if you dont know how to configure your sound card its not ubuntu fault, install codec is one of the easiest things in the world...

you said that xmms and other stuff crashed... maybe its because you used another repositories instead of the ubuntu ones..

i have ubuntu here, just after installing it 3 times and LEARNING it that i could make it work perfectly.

And when i learned it, i saw that all things that didnt work in the past installs was because of MY MISTAKES.

Just an example..

FIrst time i ve installed my 9800pro didnt work cause i tried to install the ATI driver from their website and messed everything

Second time i had a lot of problems cause i used the marillat repositories instead of the ubuntu ones...

And it always ubuntu's faul... :roll:

---

### Post by Lovechild on 2005-06-08
[QUOTE=bleakcabal]
1- Give the user the choice between KDE and Gnome during install ( having to use Kubuntu instead of Ubuntu is very akward ).
2- Give the user to choose which sound interface ( onboard, sound card ) to use like you do for network interface during install
3- A new user should know that he can add repository in Synaptic ( make it more intuive to someone who doesn't even know what a repository is )
4- Sound should work out of the box, there are many posts on the forums about sound not working, that is totally unaceptable for a major distro.
5- More codecs should be installed out of the box, and when you use Synaptic to install something like Kaffeine it should fetch some codecs, rather than installing Kaffeine and then letting to user have a Kaffeine that can't play any major video format.[/QUOTE]

Okay let's take these on:

1. there are good and valid reasons for maintaining a standard desktop, it provides a higher quality product, KDE users are most welcome to use Kubuntu which also happens to be a quality product (I do believe you can install KDE on standard Ubuntu as well). There are few Ubuntu developers and providing a polished KDE at the same level as GNOME would take away valuable development time, that is why we have kubuntu for those who prefer KDE, there are people willing to spend their time providing you with an excellent KDE distribution, why knock their effort?

2. This is a gstreamer setting, before you give me crap, gstreamer is supported in current KDE and as I understand will be the default for KDE4 - common architechture is a good thing let's use that. I do however agree that an easy to use tool to detect and select sound cards might be a good idea - Fedora ships one that works rather nicely, maybe we should look at that. I also assume HAL will eventually make such things a lot easier to work with, detection wise at least.

3. There are guides in the wiki, and the user interface does allow for easy alteration of the repo settings - however 99% of all people probably won't ever bother with that in real life, the real issue here is to promote open standards that we can ship and support instead of relying on MP3, xvid, wma and so on.. what have you done to promote these formats. Look at how Fedora is managing Extras, it's enabled be default and is cleansed of questionable packages, giving you the user a wide spectrum of software to choose from. Maybe we should have universe enabled by default and clean out all the questionable packages (of course we could put these in a seperate repo - let's call it the cracktastic patent and license violation repo)

4. I personally haven't had any issues with sound, but Breezy is switching to dmix which should fix most of the problems that are reports, which really aren't missing sound issues or badly configured soundcards, it's mixing that's just horrid. I would suggest donating money to the ALSA team to get better drivers for shuddy cards maybe? or filing bugs?

5. I here assume you want to violate the GPL, break the law and expect to get away with it? Again and again I am forced to explain how patent law works, basically large companies are granted broad trivial patents, which means to the end user that he is asked to bend over and take it up the butt.. 
There is no option of paying to get support since that would violate the GPL (which requires RANT + Royalty free redistribution). So please support open formats instead of complaining about a situation that is out of our hands, I don't doubt that everyone would love to support all these cracktastic formats out of the box, but for now we can't legally do so. Get the laws changed and convince the patent/license holders to work with the FOSS community or start using and promoting open standards.. I personally do the latter as it's more feasable.

---

### Post by allforcarrie on 2005-06-08
Everything worked out of the box for me shure, i had to look around for codecs but with apt-get it was easy.

---

### Post by UbuWu on 2005-06-08
[QUOTE=Gtaylor]Generally it's a good idea to disable your onboard sound via the bios if you have a PCI based card sitting in there. I've had Windows blow chunks at me for having a PCI and Onboard device running at the same time.[/QUOTE]

I use two soundcards in Windows all the time. One connected to the pc speakers for games and other sounds and one connected to my stereo for playing mp3's at the same time. Now because of ubuntu, I had to disable the onboard soundcard so those days are gone....  ](*,)

---

### Post by kleeman on 2005-06-08
This looks awfully like a gentoo troll. Why anyone would complain about Ubuntu after using gentoo is beyond me. I tried gentoo and the documentation is quite good BUT you certainly need to read an awful lot of it ;-) The unofficial Ubuntu Starter Guide:
[http://ubuntuguide.org/#acknowledgements](http://ubuntuguide.org/#acknowledgements)

would seem to solve most of the problems mentioned and is certainly less volume than a gentoo manual  :-P  :-P  :-P

---

### Post by carlc on 2005-06-08
> This looks awfully like a gentoo troll. Why anyone would complain about Ubuntu after using gentoo is beyond me. I tried gentoo and the documentation is quite good BUT you certainly need to read an awful lot of it  The unofficial Ubuntu Starter Guide:
[http://ubuntuguide.org/#acknowledgements](http://ubuntuguide.org/#acknowledgements)

would seem to solve most of the problems mentioned and is certainly less volume than a gentoo manual 

I think that you have nailed it. Ubuntu is a walk in the park compared to Gentoo and the Unofficial Ubuntu Starter Guide should have solved most of the problems. Ubuntu (with the help of the sacred started guide) is smooth and almost flawless in my opinion.

---

### Post by az on 2005-06-08
People should complain less to those who cannot do anything about the problem and file more bug reposts.

This person's input is pretty much useless.

---

### Post by kleeman on 2005-06-08
Hear Hear azz! I have filed several bug reports and found the Ubuntu devs very responsive usually.

---

### Post by aysiu on 2005-06-08
Hm, spending several days during installation getting Gentoo to "just work" or spending a couple of hours after installation to get Ubuntu working... ? Tough choice. If the original post-er likes Gentoo so much, s/he can go back to Gentoo. Use whatever works for you. Personally, I prefer Mepis, but I'm not going to go around bashing Ubuntu.

---

### Post by poofyhairguy on 2005-06-08
[QUOTE=bleakcabal]
If I could give recomandations to Ubuntu dev :
1- Give the user the choice between KDE and Gnome during install ( having to use Kubuntu instead of Ubuntu is very akward ).[/QUOTE]

Only one or the other will fit on a single CD. If you want both, get the DVD. 

> 
2- Give the user to choose which sound interface ( onboard, sound card ) to use like you do for network interface during install

Better Hal support in the future should work out some of the sound problems.

> 
3- A new user should know that he can add repository in Synaptic ( make it more intuive to someone who doesn't even know what a repository is )

New users can also add repos via the command-line. I give that advice to anyone that asks it here. The devs don't want it too easy to get into the universe/multiverse/backports because they don't support any of these things.

> 
4- Sound should work out of the box, there are many posts on the forums about sound not working, that is totally unaceptable for a major distro.

That is a real problem that will hopefully be fixed in Breezy. It would help if you can lay out your problem in bugzilla as well.

> 
5- More codecs should be installed out of the box, and when you use Synaptic to install something like Kaffeine it should fetch some codecs, rather than installing Kaffeine and then letting to user have a Kaffeine that can't play any major video format.

Hey, those codecs are illegal to possess in many parts of the world. Ubuntu can't include them because of legal liability.

---

### Post by Curlydave on 2005-06-08
I agree with all of the suggestions, but some aren't feasable for liability reasons that have been pointed out, or storage reasons (kde/gnome on one CD)

I'd just like to expand on the sound issue, and clarify: The user should be able to toggle the default output device through a common-sense control that is set up properly. Applications should then let you adjust which device to output if you wish to override the default. I use this for windows to have some apps play to my speakers, some to my headphones. I can't get my sound card to work without disabling onboard, which I do not want to do as I use both.

---

### Post by Curlydave on 2005-06-08
[QUOTE=UbuWu]I use two soundcards in Windows all the time. One connected to the pc speakers for games and other sounds and one connected to my stereo for playing mp3's at the same time. Now because of ubuntu, I had to disable the onboard soundcard so those days are gone....  ](*,)[/QUOTE]


Same situation exactly!!!! (well, not exactly. It's reverse for me as I want games through the phones for mic/surround sound phones purposes and music through the speakers.) Linux is not cooperating here, and I don't think it's doable as you can't even select a device with teh music players. :(

Those days aren't gone for me though, as Windows is my main OS for this among other reasons.

---

### Post by gil-galad on 2005-06-08
The easiest way to set up multiple sound cards:

Edit /etc/modules and put in the sound card modules in the order you want.  The one in the list first will load up first and be the default sound card.    

For example:

snd_emu10k1
snd_intel8x0

---

### Post by defkewl on 2005-06-09
I think it is much better if you post this in ubuntu-dev mailing list. I don't know if there are any ubuntu developer in this forum.

---

### Post by Lovechild on 2005-06-09
I know DanielS (He's an X.org hero) and this Corey guy (dunno what he does, he never tells us) are both labelled Developer on the forum, surely that would mean that they are involved in some way or form

---

### Post by weekend warrior on 2005-06-09
> **bleakcabal** wrote: 
Gentoo takes longer to install but after my experience with Ubuntu is far easier to use 
I'm sorry but I just can't resist after reading this....   :wink: 

[IMG]http://img267.echo.cx/img267/6287/gentoosm0ve.gif[/IMG]


Have fun!  :razz:

---

### Post by desdinova on 2005-06-09
A year ago I was on MDK, then Suse - I've just come to Ubuntu and I'm seriously impressed - took me a day to get everything as it should (things like courier-imap and the like) but this is a keeper.

I sympathize and agree with Ubuntu on the codec front - they're not Free codecs and besides its not really some hassle to install - plus Apt/Synaptic blows everything out of the water.

And Gnome cartoonish and amateur? I dont think so anymore. I have been using KDE since 1.x and been a huge fan of it but 2.10 has made me swap over - I now have no KDE/QT apps on this machine - its Gnome only.

---

### Post by Brunellus on 2005-06-09
[QUOTE=weekend warrior]I'm sorry but I just can't resist after reading this....   :wink: 

[IMG]http://img267.echo.cx/img267/6287/gentoosm0ve.gif[/IMG]


Have fun!  :razz:[/QUOTE]
 Good God.  I hope I don't get in trouble for checking this at work.

---

### Post by poofyhairguy on 2005-06-09
Lego stuff can be funny:

[IMG]http://drew.corrupt.net/bp/blockporn6-13.jpg[/IMG] 

[http://drew.corrupt.net/bp/](http://drew.corrupt.net/bp/)

---

### Post by bored2k on 2005-06-09
That hurts..

P.S. Isn't that.. pr0n lol.

---

### Post by weekend warrior on 2005-06-09
> That hurts.. heh yeah... well Gentoo *can* be a royal **PITA**!  :wink:

---

### Post by weekend warrior on 2005-06-09
Speaking of LEGOs, here's someone with plenty of time on their hands...  how about a [Lego Tux](http://www.ericharshbarger.org/lego/penguin.html)?

---

### Post by compmodder26 on 2005-06-09
Wow

---

### Post by Lovechild on 2005-06-10
[The bible explained in LEGO](http://www.thebricktestament.com/)

---

### Post by Magadass on 2005-09-09
[QUOTE=oddabe19]Many of those questions are always brought up.

A. The developers want to keep a 1 cd distro (small install). You can't do that having to install 2 desktops, so they give you a choice. Kubuntu or Ubuntu.
B. There are MANY patent issues with many codecs.... which doesn't go with the Ubuntu philosophy by stealing them.
C. The developers want an All-Free distro. If you want to include MP3 you have to pay royalties, etc...
D. Sound problems are consistant with many distros, not just ubuntu. Alsa-base 1.0.8 is very problematic.[/QUOTE]

I would personally like to see a version of Ubuntu that is polished to high heaven that is released onto a DVD and the current version of Ubuntu kept how it on remaining on one CD.  When I say polished I dont mean overbloat with 6 instant messenger clients like Mandriva does but I mean with very high resolution fonts, icons, and all the necessary packages such as codecs.  But I realize due to legal reasons they cant include these but downloading them from their repositories isnt just as illegal?  Why cant you agree to the exact same EULA before you download the ISO saying that you Own a copy of Windows and that you downloading a Microsoft poprietary codec or font or whatever is perfectly legal....

These are the small things that erk me a little bit in Windows, if very experienced computer geeks have problems gettings things to work I could only imagine how many problems the not so talented would have....

In any case my sound still doesnt work on my A7N8X, but I bookmarked a couple of forum threads and emailed them to myself to give a try when I get home to see how those go, if all fails ill just buy a new soundcard....But Sound should just work on Linux, I have always had problems with sound and linux for nearly 4 years now....Since OSS, now ALSA, it still sorta sucks....

---

### Post by tseliot on 2005-09-09
Sound works flawlessly for me in Breezy (out of the box). I had some minor problems in Hoary though (which could be solved with a good HOWTO).

---

### Post by Kyral on 2005-09-09
*wonders why a dead two month old thread was suddenly revived....*

Though I will agree on the sound issue. That is one of Linux's big weak points. I mean how many sound systems are there? OSS, ALSA, ESD, aRts, Polywhatever...Makes my head hurt and I've been around for 3 years :P Gimme ALSA :D

---

### Post by bob_c_b on 2005-09-09
Well coming from RedHat 7/8/9 and Mandrake 9/10 I find Ubuntu pretty refreshing. A minimalist install, a clean interface, good hardware support and an "unofficial" guide to get all that "other stuff" you need. In fact, Ubuntu was so easy to set up and get massaged into something totally ready for primetime I actually found myself missing those days of tinkering to get everything "just right". I have a couple sound issues as well (basic sound is great, media player sound is basically okay, games are another issue) but with Breezy just around the corner I think I will just wait it out. 

YMMV, but so far Ubuntu has blown me away.

---

### Post by poofyhairguy on 2005-09-09
[QUOTE=Magadass]  But I realize due to legal reasons they cant include these but downloading them from their repositories isnt just as illegal? [/QUOTE]

Those that host those repositories are not connect to Ubuntu in any legal way.

---

### Post by angkor on 2005-09-09
[QUOTE=Magadass]I have always had problems with sound and linux for nearly 4 years now....Since OSS, now ALSA, it still sorta sucks....[/QUOTE]

With Debian I've always had to change some alsa settings to get sound to work properly. None of this with Ubuntu, sound out of the box for the first time..with Hoary as well as Breezy.

As for the original poster. Why not re-install Gentoo, you're used to it and know how it works. I can hardly believe a Gentoo power user could have _that_ much trouble setting up an Ubuntu box.

---

### Post by xequence on 2005-09-09
[QUOTE=bleakcabal]Hi, I was a long time Gentoo user ( and a Red Hat user before that ).

When my HD crashed after years of use I decided to reinstall my windows and linux partitions but I decided it was time for a change. 

Gentoo had a long and complicated install process and I didn't want to go through that again.

I browsed the net looking for another distro that would be simpler and less time consuming to work with.

I found Ubuntu.

The installation is really a smooth process that executes quickly and required very little input from my part. Just what I was looking for I tought.

Soon afterwards came the problems.

I had no sound, didn't know how to tell Ubuntu to use my sound blaster instead of onboard sound. Couldn't play video and spent days on the forums looking for help on how to install codecs. XMMS crashed on it's first use after I installed it from Synaptic. Network windows shares worked until I apt-get Samba. Adding repositories is crucial while being cryptic to a new user.

Synaptic on it's first use after installation of Ubuntu gave me error messages that child process were left open and such.

I find that to make anything work is a pain in the butt, particularly when I have to manually compile things. 

Gentoo takes longer to install but after my experience with Ubuntu is far easier to use not only because you have more control but because the packages Just Work   after you install them. When I emerge XMMS under gentoo I can load an mp3 right away and have it play. I don't have to look on the boards to know how to make XMMS work. There are also more packages. 

Ubuntu worked nicely for some things out of the box, but other things did not even work. And when it came time to correct these problems I had to wade through barriers intentionally put there from letting me use my system correctly. I see no reasons why when I install automake it can't set the PATH variables itself or why automake isn't even installed by default.

Also this was the first time I had used Gnome. I found it very amateurish and quickly proceeded to install KDE.

If I could give recomandations to Ubuntu dev :
1- Give the user the choice between KDE and Gnome during install ( having to use Kubuntu instead of Ubuntu is very akward ).
2- Give the user to choose which sound interface ( onboard, sound card ) to use like you do for network interface during install
3- A new user should know that he can add repository in Synaptic ( make it more intuive to someone who doesn't even know what a repository is )
4- Sound should work out of the box, there are many posts on the forums about sound not working, that is totally unaceptable for a major distro.
5- More codecs should be installed out of the box, and when you use Synaptic to install something like Kaffeine it should fetch some codecs, rather than installing Kaffeine and then letting to user have a Kaffeine that can't play any major video format.[/QUOTE]

Isnt gentoo very very technical? You should be able to know how to get these things to work :P Heh... Number one, the isntaller would be to big for a CD if the extra 180 MB for KDE was added. Yes, KDE is 180 MB. I used apt-get to install it. And I uninstalled it in a week.

2. I have no idea about this since my sound only messed up once and for a short time. I to this date havnt gotten sound to work in windows XP.

4. Sound does work out of the box for me.

5. MP3 codecs cost money to come pre installed. Its best to keep ubuntu free and make people copy and paste a command ;)

---

### Post by davidgypsy on 2005-09-11
[QUOTE=bleakcabal]Hi, I was a long time Gentoo user ( and a Red Hat user before that ).
.[/QUOTE]

I consider Ubuntu to be for intermediate-advanced users, for ease of use you should try Mepis or PCLinuxOS. Both are fine distros that come with a good range of programs, including a number of propriety ones.

However, in my opinion, Ubuntu just does stuff a whole lot better! I have installed it on 6 computers now, including a laptop, without any major problems. It is smooth and polished, and the money that is being pumped into it by my favourite multimillionaire shows. Anything I am lacking to play DVD's, MP3's etc. is made superbly easy by Synaptic.

I tried Gentoo once, and gave up very quickly when I couldn't get the install to even start! Probably my fault though... That's the beauty of Linux, it gives me the freedom to choose the distro that suits me!

---

### Post by benplaut on 2005-09-11
[QUOTE=Kyral]*wonders why a dead two month old thread was suddenly revived....*[/QUOTE]

yeah... me too  :roll:

---

