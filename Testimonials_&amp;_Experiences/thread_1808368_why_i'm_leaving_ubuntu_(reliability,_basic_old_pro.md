---
title: "why i'm leaving ubuntu (reliability, basic old problems)"
date: 2011-07-20
forum: Testimonials &amp; Experiences
---

### Post by klaasklever on 2011-07-20
hello,

i'm using ubuntu for years, i started with dapper drake and i had a lot of fun with it. but since, let's say, lycid lynx, the fun is gone away.

i had problems everytime, things weren't working, i had to search solutions, to learn using the terminal and applied workarounds. all ok, that's linux and with every success and progress, the work with ubuntu got better. and i could be sure, the next version will fix some of the issues and will be better than the old.

but there was the moment, this wasn't right anymore. in my special case, these are problems with standby/hibernate and wireless lan. connection problems, solved by canonical out of the box years ago, re-appeared in newser versions (i think, lycid in my case) - on the same netbook with well known hardware. ([http://ubuntuforums.org/showthread.php?t=1709349](http://ubuntuforums.org/showthread.php?t=1709349)). and no, i'm tired of fix such old stuff after every install/upgrade.

for me, that's not understandable. if one device is supported well, this should stay in newer version of a system. this is not the way to hold users. i'm not willing to fix old problems in new ubuntu versions every time. additionally there are other annoying issues, which kill the fun. the old keyring with wlan-problem e.g.. or, why do i STILL have to install samba by hand (if i even understand at all, what's wrong. the error messages are poor, no hints) - in the year 2011, when our parents own a nas or a small home server? why does i still have trouble with installing lighting for thunderbird (fight vs. distro and separate install)? why does the interface/menu change with every version and i have to search used, preinstalled applications (system, preferences)? i don't mean unity or netbook interface, i mean the base structure.

i have to choose a lts version, to reach peace? than i'm not able to use new features beside the reps. and at last after 1 one year i'm not profiting of new features, still.

my conclusion is: ubuntu wants to much and forgets/ignores the habits of the user. every half year too many things changes and i have to get a new orientation. (for such purposes, i would get fedora...). i'm missing a good compromise between progress and groundstanding developement for productive use.

so, for me ubuntu seems to be more a colorful popcorn with all the new interface stuff, but behind the scenes problems are still unsolved, the structure is still complicated like years before. i'm disappointed after all the time. i'm alway open for new features, i'm not longing for the good ol' times. but where is reliability?

yes, ubuntu got better and better over the years. it's a good distro, yes, but only if you don't get problems or deeper wishes for using it. for sad, there are not many alternatives for use on a netbook, but at least, for my peace, i will make compromises, as long as the basic stability is provided.

for me, ubuntu isn't reliable anymore and i couldn't recommend ubuntu to others anymor. i'm frustrated and i'm feeling left behind as a user, who at first simply wants to work with the system.

this as my general thoughts and as a public feedback to developers. remember, it's not a thing of the detailed problems above, every one is fixable i think. it's a question of the strategie and the future line of ubuntu.

your feedback is welcome.

---

### Post by ghostborg on 2011-07-20
I would consider one of the flavours of Linux Mint, Linux Mint 11 is Ubuntu based. LMDE and XFCE are Debian based and are rolling distributions.

[http://www.linuxmint.com/]("http://www.linuxmint.com/")

---

### Post by ericartman on 2011-07-20
Yeah I am considering if I should build another box for Linux. I made the mistake switching from Nvidia to ATI on my dual boot game system I built. ATI just gave way better bang for my buck playing games in windows. Problem is the ATI board has no way to control the fan speed in Linux. Yeah I know, ATI blames Linux, Linux points back at ATI, whatever, it just doesn't work. Now I have to start digging around and build another dedicated Linux box, find space for it, split my router so I can get enough ports for another box.I know there are plenty of people who fixed the ATI fan speed but none of the fixes I found works for me, just like I have never gotten wow to work in Linux, though many have. Wish I had the time to invest and figure all this out but I just don't. So maybe when I get some free time (lol), I'll build something new just for Linux but for now I am sadly removing Ubuntu and moving on.

---

### Post by mastablasta on 2011-07-20
you want to have new things that were only slightly tested and then want stability? that just doesn't make sense.
 
i am totally with this recurring bugs. if buges were solved or if solution is provided then they should be patched. and never again resurface. ok Linux Mint has some bugs patched.
 
but Mint is moving more and more into debian testing sphere and Debian testing has it's own issues. as does LMDE (the debian based version). hopefullyl they will solve it with 1 month upgrade that are patched and cosidered safe first. lets see if they can realyl do it. a stable yet rolling ditribution.

---

### Post by Arthur_D on 2011-07-20
Seems like you don't understand how kernel development works. If noone works on a device driver to keep it up-to-date, they have to drop it from the kernel. Otherwise it will be incompatible as the kernel API changes all the time, and in some extreme cases a bad driver can be far worse than no driver at all, since it can break the device.

So yes, regressions can happen.

---

### Post by klaasklever on 2011-07-21
thx for your suggestions. i heard of mint, i will take a closer look now!

@mastablasta
i didn't make the point clear enough, sorry: i want to be able to install newer stuff or to take part in progress of software. if i do, it's my own risk, of course. but with lts versions, as far as i know, this is limited. lts is too old after some months, the half-year-changing are too new...

@Arthur_D maybe, operating systems are difficult things. but at least the user shouldn' be confrontated again every year (or half) with known problems. how this is done - i don't know and, if i have to work with a system, i don't care. i appreciate developers work, but recurrings problems are too bad. and, it seems to me, other distros doesn't have the wireless problem, for example (suse, fedora).

best greets

---

### Post by mastablasta on 2011-07-22
> **klaasklever said:**
>  
@mastablasta
i didn't make the point clear enough, sorry: i want to be able to install newer stuff or to take part in progress of software. if i do, it's my own risk, of course. but with lts versions, as far as i know, this is limited. lts is too old after some months, the half-year-changing are too new... 

 
no it's not really limited. you just need to use PPA if newer software is what you need.
 
LTS is just a develpment snapshot frozen in time. For example i use Kubuntu 10.10. BUt i had some KDE issues that i was hoping newer KDE would solve it so i added PPA for this new KDE and now i have it like 11.04 :-) sure enough plenty of issues were solved (though not all), however this might cause problems on the next upgrade. we'll see. 
 
i also added Firefox PPA so that i have new version of the browser. And a few other porgrammes that were updated and had some bugs patched. all in all PPA's work for the most part.
 
As a spirit lift i should tell you that my bro who uses it for production and does all his programming in it had version 9.10 untill recently. and he wouldn't change it yet but the disk went bust. he stays with same version because in order to find and solve all dependancies and to install everything he uses it takes him about 1-2 working days. new version can break dependancies and other stuff, so he needs to just have a stable OS. some programmes he has up to date, for some he needs older versions.

---

### Post by Thewhistlingwind on 2011-07-24
"I see a lot of people on the Ubuntu forums screaming out for less bloat, more stability, less regression, longer time between releases, more bug fixes, practical values, they don't want Ubuntu, they want Debian, they just don't know it yet." - Seriously, where is this from? i can't remember.

It's funny though, I never could figure out how to get my wireless to work in Debian, I never sunk that much time into it anyway.

---

### Post by XubuRoxMySox on 2011-07-24
It took me awhile to figure out "how Ubuntu does things," but it didn't have to. 

I think it would be really helpful if Canonical marketed the LTS versions as "better for beginners" because they have been much more stable and longer supported. 

Newcomers to Debian are urged on their web site and press releases to install the current *Stable* release. More experienced Linuxers and tinkerers are encouraged to try "Testing" and "Unstable."

Canonical should do the same thing, IMO. 

**"New to Ubuntu and Linux? Download our current stable release [COLOR="Purple"]here[/COLOR]... Experienced users who enjoy testing the latest stuff, click [COLOR="Red"]here[/COLOR] to download the latest release based on Debian Unstable..." etc.**

Just say'n.
Robin

---

### Post by wolfen69 on 2011-07-24
> **klaasklever said:**
> 
for me, ubuntu isn't reliable anymore and i couldn't recommend ubuntu to others anymor. i'm frustrated and i'm feeling left behind as a user, who at first simply wants to work with the system.



This is how I feel about windows, and why I use linux. It *always* runs great, and is rock solid. If windows was all that and a bag of chips, I'd probably still be using it. But hey, that's just *my* experience.

---

### Post by mastablasta on 2011-07-25
> **Thewhistlingwind said:**
> "I see a lot of people on the Ubuntu forums screaming out for less bloat, more stability, less regression, longer time between releases, more bug fixes, practical values, they don't want Ubuntu, they want Debian, they just don't know it yet." - Seriously, where is this from? i can't remember.
 
It's funny though, I never could figure out how to get my wireless to work in Debian, I never sunk that much time into it anyway.
 
 
Debain has it's own share of issues. stuff doesn't work out of the box. for example touchpad. it works in all distroy i threw on it but debian stable. it even worked on Chrunchbang based on debian stable. debian said i should install somehting, configure something... why? do i look like person that has time configuring basic stuff that should be plug and play? imagine you had to fist configure every key on keyboard. 
 
you CAN have improvements AND stability at the same time. debian can drop improvements as they claim stability eventhough imporved version might be stable just as well.

---

### Post by Arthur_D on 2011-07-25
Debian aims for being strictly Free Software. That's why some peripherals doesn't work out of the box. If you don't like it, use another distro.

---

### Post by arunb on 2011-07-26
funny why LTS did not work for the OP. Are you sure the hardware is not the problem ??

Generally LTS is considered to be the best option.

---

### Post by tora201 on 2011-07-26
Hey man.. welcome to the forums! If you have been using Ubuntu for "years" and had problems since Lucid, then you could have perhaps joined the forums earlier and asked for help with your problems. Hey, I did that, and I have always received a lot of help from people - and I even posted some solutions to problems I managed to solve myself!

Anyway, since you joined now, why not list up your problems, put them on the board and see what happens? I'm sure they can be solved! As someone mentioned, if you don't like interface changes you could go the Mint direction... but if you do thgat, could I suggest 10 ?  have it on a box in my office and its absolutely purring along..... other have said the same thing. 11 though, is more problematic - Compiz doesn't seem to like it and neither does Skype, although both can be "solved" if you do some searching...

By the way, my little testimonial (off topic, but can't be bothered starting a new post.. LOL)

I put Mint LXDE on a my friends old IBM TX40 hinkPad Notebook (with mobile M chip) which has just 512 megs of ram with shared video, and it "flies" compared to Windows XP (I wiped XP off in disgust as soon as he gave it to me to "fix") The difference in terms of performance was incredible. Windows was an absolute dog on it. The thing was full of viruses when I got it too.... 

Anyway, my mate says he is loving it. and the machine is like a "new" one. And, he has never ever used Linux before...god he doesn't even know what a "file manager" is. All he wanted was a broswer/word processor/skype and ability to watch movies/play music (which I suspect 99% of people would be happy with. So for them, Linux is better because it doesn't get viruses (yet) and is more stable/faster than Windows, especially on older machines. Hah. Next in line is my mother! XP will be "going out the door".:P

Anyway, cheers and good luck!

> **klaasklever said:**
> hello,

i'm using ubuntu for years, i started with dapper drake and i had a lot of fun with it. but since, let's say, lycid lynx, the fun is gone away.

i had problems everytime, things weren't working, i had to search solutions, to learn using the terminal and applied workarounds. all ok, that's linux and with every success and progress, the work with ubuntu got better. and i could be sure, the next version will fix some of the issues and will be better than the old.

but there was the moment, this wasn't right anymore. in my special case, these are problems with standby/hibernate and wireless [SNIP] 

---

### Post by ciscoboy on 2011-07-27
[SIZE=3]the thing I like about ubuntu is the fact that when downloaded from a good source (in my case unetbootin), all you need to do is load it on a usb drive, set your PC to boot primarily on your USB ports and off you go; which i suppose might be true for alot of the linux versions out there. The one thing that's missing that in my opinion they should add as part of the original package is an adobe flash player package or a linux equivalent. In fact, because I screwed-up with the linux version on my laptop (lubuntu), I've been using a live version with 3 GB of system memory for like 3 weeks now, and it still works like a charm. So since I've only experienced two linux versions, i'm not really qualified to give-out an opinion and since i'm still rather new with linux, I still find ubuntu as a good overall Operating system. Plus, unlike lubuntu, ubuntu gives you a desktop that you can actually use, even though you pay it with ubuntu being bigger. 
[/SIZE]

---

### Post by XubuRoxMySox on 2011-07-27
> **ciscoboy said:**
> [SIZE=3]... unlike lubuntu, ubuntu gives you a desktop that you can actually use, even though you pay it with ubuntu being bigger. 
[/SIZE]

Hi!

I find that **[COLOR="Blue"]X[/COLOR]**ubuntu provides a sweet balance between LXDE's miserly use of resources and Gnome's superb versatility and functionality. It's also simple enough, like LXDE is, for this simple kid to use! Just for grins, you might give it a try.  

Enjoy!

[FONT="Comic Sans MS"]-Robin[/FONT]

---

### Post by Tamlynmac on 2011-07-27
> dixiedancer
I find that **[COLOR=Blue]X[/COLOR]**ubuntu provides a sweet  balance between LXDE's miserly use of resources and Gnome's superb  versatility and functionality. It's also simple enough, like LXDE is,  for this simple kid to use! Just for grins, you might give it a try.  

My family & I have also found Xubuntu (xfce) easily configurable. It's very user friendly and fast. I've not seen any increase in ram or CPU usage. We will switch all five of our systems over prior to 10.04 support running out in 2013.

As an alternative option, IMHO Xubuntu definitely ranks at the top.

---

### Post by ciscoboy on 2011-07-27
[SIZE=4]I also like ubuntu over lubuntu because of a good long-tem 

support. So how does Xubuntu do for long-term support 

compared to ubuntu?[/SIZE]

---

### Post by XubuRoxMySox on 2011-07-27
> **ciscoboy said:**
> [SIZE=4]How does Xubuntu do for long-term support 
compared to ubuntu?[/SIZE]

Identical! I'm using Xubu 10.04 (Lucid) and it is supported for another 2 years - just like Ubu and Kubu.

:KS  Long live Xubu!! :KS

-Robin

---

### Post by CastleD on 2011-07-28
Ubuntu saved me when I couldn't boot XP. Couldn't reinstall. couldn't recover, couldn't do anything. I put in the Ubuntu iso and it installed nicely and had me back up and running again. So for that I'll always be thankful for Ubuntu.

That said, The XP setup disk is calling my name because for a week I've had annoying problems with Ubuntu. I'm getting tired of it. Maybe we can chalk up some of my problems to my old computer. I couldn't change my screen refresh rate from 0 hz. My display is a bit blurry. I spent hours looking into the problem. Tried to fix it in the terminal and got a black screen on restart. I figured I wanted to switch to Xubuntu anyway so I did a fresh install of that. It runs faster and I really like it. Still had the 0 hz problem. Finally fixed it, or so I thought. Xubuntu started freezing, and it froze in the middle of updating software. I have no idea what happend to those updates and if they're okay, they're not there anymore.

 I erased my monitor changes and I'm ok again, still have the 0 hz problem though.

I downloaded the Epiphany browser. Wow, nice and fast, I like it. Wait, they use a ridiculously outdated ad filter list. Spent an hour fixing that. Did it! Cool. But wait, you can't copy and paste text from a web page! Amazing, the most fundamental of things and you can't do it. Looked it up, known bug, no solution. Back to Firefox.

Tried to play a video in Parole. I like Parole, cute little player. Nope, couldn't play an MP4 video. Downloaded VLC, which of course I used for years, and it worked. Again though, it's one problem after the next.

I'm tired of it. Not that XP is wonderful either, we all know that. But I had less problems with XP than this. I don't know, we'll see what happens. So many things I like about Ubuntu, I want to stick with it... I'm frustrated. My damn screen is blurry!

---

### Post by Tamlynmac on 2011-07-28
> CastleD
I'm tired of it. Not that XP is wonderful either, we all know that. But I  had less problems with XP than this. I don't know, we'll see what  happens. So many things I like about Ubuntu, I want to stick with it...  I'm frustrated. My damn screen is blurry! 	

Since this isn't a support section of the forums (per the sectional guidelines and this [sticky]("http://ubuntuforums.org/showthread.php?t=1343965")), I must assume you are simply stating your opinion and sharing your frustration.

I believe that one should use what works for them and that 
Ubuntu may not be for everyone. It requires an investment in the learning curve and a certain level of commitment. There's no entitlement associated with it and IMHO some users who try and migrate to Linux struggle with certain expectations. Hardware compatibility is one of them, as not all hardware is compatible with Linux.

Some mfgs refuse to acknowledge Linux and choose to only support Windows/Mac. When switching from one OS to another, one should endeavor to confirm that their system hardware is compatible with the new OS by testing and/or investigating. They should also invest in assuring any new hardware they purchase is compatible. I'm not suggesting that your issue is one of compatibility, only that it's part of the decision.

It's been my experience that some users migrate thinking Ubuntu/Linux is a Windows clone and that everything they did in Windows will work in Ubuntu. Prior to helping anyone test and install Ubuntu, I always notify them that the transition can only be made successfully if they're willing to accept the differences and invest in the learning curve. It's sad your struggling, but one must accept the responsibility of learning and investigating prior to installing.

The solution is to either purchase a system designed/built for Ubuntu/Linux, ask or pay for assistance in installing Ubuntu from a local experienced user or spend the time confirming that one's existing hardware will work and learning about the OS prior to attempting the install.

Good Luck

Just my $0.02

---

### Post by beew on 2011-07-29
> **CastleD said:**
> ...
I'm tired of it. Not that XP is wonderful either, we all know that. But I had less problems with XP than this. I don't know, we'll see what happens. So many things I like about Ubuntu, I want to stick with it... I'm frustrated. My damn screen is blurry!

Without knowing the specifics it seems that you have only two problems, both easily fixed. 1) you may need to install the proprietary graphic driver for your card, in Ubuntu it is usually a one click operation by running "Additional Drivers". 2) You need to install media codecs. That would be Ubuntu (xubuntu.. Kubuntu whatever) restricted extra plus 2 packages from Medibuntu (w32 codecs and nonfree condecs)

---

### Post by x-D on 2011-08-06
> **klaasklever said:**
> thx for your suggestions. i heard of mint, i will take a closer look now!

@mastablasta
i didn't make the point clear enough, sorry: i want to be able to install newer stuff or to take part in progress of software. if i do, it's my own risk, of course. but with lts versions, as far as i know, this is limited. lts is too old after some months, the half-year-changing are too new...

@Arthur_D maybe, operating systems are difficult things. but at least the user shouldn' be confrontated again every year (or half) with known problems. how this is done - i don't know and, if i have to work with a system, i don't care. i appreciate developers work, but recurrings problems are too bad. and, it seems to me, other distros doesn't have the wireless problem, for example (suse, fedora).

best greets

Sorry, but for me, Ubuntu's Wireless Card support is fantastic, all of the Wireless Cards I have work (not only plug-in ones, but built in Laptop ones). In Fedora, however, it is a VERY different story. In Fedora NONE of my Wireless Cards can pick up the Internet, and moreover a lot of the features of Gnome 3 Shell, are far buggier than Ubuntu's Natty's Unity Bugs!

x-D :guitar:

---

### Post by overdrank on 2011-08-06
Thanks for sharing, Thread closed.

---

