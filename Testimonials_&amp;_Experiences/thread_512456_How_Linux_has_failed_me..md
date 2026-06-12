---
title: "How Linux has failed me."
date: 2007-07-29
forum: Testimonials &amp; Experiences
---

### Post by Slavedriver on 2007-07-29
First of all, a little disclaimer.
1) I am not trying to start a flamewar. Merely pointing out what I didn't like in a system being pushed so hard in my face (yes Slashdot, I am talking about you)
2) I am NOT trying to start a flamewar. No, really. I may be overly critical, ironic, maybe a bit offending to some people, heck, I know I WILL offend someone, but that's how I am. Not a troll. Not as green as a troll at least.
3) I am programmer by trade who works with both Windows and Mac OS a lot and has to use console in his daily work more than GUI. That means I am really OK with the console, not afraid of it and sometimes even prefer it to GUI.
4) While I prefer Windows XP to all OSes I tried a lot of other OSes out there to form an opinion of what a perfect OS should be (and that were all flavors of Win starting from 3.11, all flavors of Mac OS X starting from 10.1 and a few flavors of Linux).
5) This is my opinion, biased, subjective, but mine. If you can't cope with somebody expressing a different opinion from your own - please deal with it in a civil manner.

So let's start...

Truth be told I had to try Linux recently because my few-years-old XP install is going haywire (you know like it becomes after a few years of extensive use) and all movies I tried to watch started to lag like hell. So, after reading another portion of "Linux is superior to everything" on Slashdot (really, guys, at lest try to be less biased) I decided to install latest version of Kubuntu (I had 6.06 installed prior to that just to try it out but I haven't used it a lot).

Seeing that 7.04 was supposed to come with a nifty app to install the drivers I was quite please because the horror of trying to get my NVidia to work on 6.06 was still fresh. First thing I noticed when booted to LiveCD is that my external USB HDD wasn't visible. Oh well, I though, I'll browse the web without listening to music while waiting it to install. So I fired up the installation app, sniped my town from the world map (really guys add the zoom feature from Ubuntu's installer) to select the timezone and moved on with the installation. Meanwhile I tried looking for this driver install app because I remember seeing it on one of Ubuntu screenshots (not Kubuntu one though). Haven't found it. Oh well, maybe it'll become available after I boot into the real system.

So after trying to break my CD drive rack once more (still don't understand why the system requires me to eject the CD when I reboot\shutdown. I have a door which closes the part where my CD drive is so it will simply won't open if the door is closed damaging the fragile plastic gears used in the tray mechanism.) I rebooted into the real system. First thing - my USB HDD *still* wasn't there. Nowhere to be found and mounter manually. Second, driver install app wasn't there too. No external HDD basically meant a useless system to me because I store all my media files and documents there. So goobye Kubuntu, hello Ubuntu.
Boot to LiveCD, find my USB HDD already discovered, find driver install app, install the system, reboot. Sigh, HDD is still there. Install drivers, download 100+ updates including new kernel, reboot.

Try playing a movie. Alert appears saying codecs are not installed. OK, let's install some codecs then. And here's the part I don't like - the scary "Restricted app" message. While I don't really care about it I know 100% that any average user will be. And that will be an end for the media playback for him if some geek won't come and set it up for him.
Next stop - install Amarok, it being quite good media player. After installing it and building my collection I tried playing some MP3 files knowing what to expect - a pop-up asking to install MP3 codec because it's "restricted'. Boo, scary. Instead Amarok hanged... Restart, select a track, click play, boom, hang again. This time I actually see the pop-up but without any text or buttons. After a few seconds I am told that KNotify crashed.

Oh well, no music for now, let's actually watch a movie. And now here comes another bad thing - movies that played fine on Win on Linux play with huge amount of artifacts and, sometimes, don't play at all looking corrupted. Reboot to Win - plays OK, reboot to Linux - artifacts and corruption.

The rest of the concerns won't come up in a long, unreadable lame story-like way but more in a way of a nicely organized, but still unreadable, list:

1) Kubuntu doesn't offer the same functionality only in KDE like Ubuntu does. And I mean core functionality like USB HDD support
2) An average user WILL be scared by "restricted" stuff no matter what. "Restricted" means dangerous. And dangerous means bad.
3) There is no centralized place to set up a system to your liking. In Mac OS there's System Preferences, in Win there's Control Panel, in Ubuntu there are dozen of little apps scattered through whole menu structure. NOT intuitive, NOT easy to use, NOT good.
4) You absolutely canNOT set your system up without using the console. And console is what an average user is afraid of. Installed drivers ? Cool. But desktop resolution is still 1024x768. Now here comes two options: one of the involve editing xorg.conf manually and another launching nvidia-settings with sudo. Obviously both ways are NOT acceptable to an average user.
5) The system itself is tuned up for terminals of the 80s. If I am using a modern graphical card and LCD display I will have to cope up with extreme ugliness. Heck, even Win2k looked better than modern GNOME and KDE environments. Remember what made Vista and Mac OS successful ? Beautiful GUI, not scary word like "secure".
6) While I already told it I think it deserves it's own number - use of console. It is completely NOT acceptable to the average user. If at least ONCE Joe Smith must use the console to get some basic (and basic involve installing drivers and configuring the system) thing = BAD, very BAD.
7) Some settings are sometimes illogically placed, hard to find and navigate to. 
8) Scary way to install apps. While it really beats anything on Win (because Win doesn't have anything like that) for an experienced user, an average Joe will be shocked when he sees Synaptics screen. "Add\Remove" is a definite step forward but still it is not enough. For example I would personally like to see some codec packs (like CCCP or K-Lite or Vista Codec Pack on Win) being installable from there. Basically a metapackage but what an easy and simple way to add all needed codecs to enjoy the music and video.
9) OS structure is scary. While personally I don't care about all /etc/ /var/ and the rest it can scare the living poo out of an average Joe while he's just trying to find his D: drive (especially if he never bothered to give any labels to his partitions because hdc1 is NOT intuitive (not that I can thing of a better way to represent an unnamed partition)). I suggest to do what Mac OS does - hide all scary folders. I understand it's not possible to put them all in one neat and tidy System folder but at least hide them. Live only the ones user will use on daily basis (like home folder and media folder), the rest are just confusing.

While that's really not the whole list of my concerns those presented here are the ones I think the end user will benefit from. And if anything - read the disclaimer again :)

---

### Post by tenn on 2007-07-29
I feel the fact that you feel you needed to post this post is an indicator of how little you know about Ubuntu but what ever turns you on, this is the Ubuntu forums.

---

### Post by seshomaru samma on 2007-07-29
with respect , I think the talk of an 'average Joe' is inappropriate here.
the 'average Joe' will never install Linux , if he does then he will cease to be average
the 'average Joe' never installs Windows and certainly wouldn't know how to install drivers when Windows fails to detect them and if you ever installed Windows , that often happens. Is right clicking 'my computer' choosing properties and looking for the 'device manger' intuitive?
I think people who install Ubuntu should expect it to be different from Windows , so should you.
The aim of Ubuntu is not to be an OS for idiots , this niche is already taken , it aims to give an easy well supported cutting edge version of Linux and that involves the dreaded terminal. 
I think the average Joe can buy an Ubuntu laptop from Dell and would probably never need to use the terminal. I don't know if that's is such a good thing.

---

### Post by GerryB on 2007-07-29
If Ubuntu is not what you want, there are a lot of Linux OS's out there. You can install over what you have anytime. Try Mint, or Mepis, or Slackware. I'm posting from Sabayon Live DVD - awsome - recognizes everything. (If you want to try this one, download it from an Australian mirror). I sincerely wish you all the luck in the world. Installing an operating system is a challenge but not insurmountable - witness the thousands on this forum.

---

### Post by coffeecat on 2007-07-29
You say that you are not a troll and that you're not trying to start a flamewar, but your post comes over as whiny and very negative. It will be no surprise if other forum members respond in a negative manner.

So I will attempt to be positive and state that you make a number of points that could be the foundation for a constructive and interesting debate. It is a pity, therefore, that your manner is unlikely to be conducive to such a debate.

Let me give but one example.

> **Slavedriver said:**
> 9) OS structure is scary. While personally I don't care about all /etc/ /var/ and the rest it can scare the living poo out of an average Joe while he's just trying to find his D: drive (especially if he never bothered to give any labels to his partitions because hdc1 is NOT intuitive (not that I can thing of a better way to represent an unnamed partition)). I suggest to do what Mac OS does - hide all scary folders. I understand it's not possible to put them all in one neat and tidy System folder but at least hide them. Live only the ones user will use on daily basis (like home folder and media folder), the rest are just confusing.


I have a Mac. I like the OS very much and have much respect for it, but the one thing that really irritates me about MacOS is the way it obfuscates the directory structure. I like to use the GUI as much as possible, but I also like to know what is going on and if I want to dive into the directory structure I want to see it presented the way it is. Linux does this for me.

By the way - let the average Joe speak for himself. You speak for yourself. Trying to run other people's lives for them always leads to trouble. Is there a hidden significance to your username? :roll:

---

### Post by M$LOL on 2007-07-29
> **Slavedriver said:**
> First of all, a little disclaimer.
1) I am not trying to start a flamewar. Merely pointing out what I didn't like in a system being pushed so hard in my face (yes Slashdot, I am talking about you)
2) I am NOT trying to start a flamewar. No, really. I may be overly critical, ironic, maybe a bit offending to some people, heck, I know I WILL offend someone, but that's how I am. Not a troll. Not as green as a troll at least.
3) I am programmer by trade who works with both Windows and Mac OS a lot and has to use console in his daily work more than GUI. That means I am really OK with the console, not afraid of it and sometimes even prefer it to GUI.
4) While I prefer Windows XP to all OSes I tried a lot of other OSes out there to form an opinion of what a perfect OS should be (and that were all flavors of Win starting from 3.11, all flavors of Mac OS X starting from 10.1 and a few flavors of Linux).
5) This is my opinion, biased, subjective, but mine. If you can't cope with somebody expressing a different opinion from your own - please deal with it in a civil manner.

So let's start...

Truth be told I had to try Linux recently because my few-years-old XP install is going haywire (you know like it becomes after a few years of extensive use) and all movies I tried to watch started to lag like hell. So, after reading another portion of "Linux is superior to everything" on Slashdot (really, guys, at lest try to be less biased) I decided to install latest version of Kubuntu (I had 6.06 installed prior to that just to try it out but I haven't used it a lot).

Seeing that 7.04 was supposed to come with a nifty app to install the drivers I was quite please because the horror of trying to get my NVidia to work on 6.06 was still fresh. First thing I noticed when booted to LiveCD is that my external USB HDD wasn't visible. Oh well, I though, I'll browse the web without listening to music while waiting it to install. So I fired up the installation app, sniped my town from the world map (really guys add the zoom feature from Ubuntu's installer) to select the timezone and moved on with the installation. Meanwhile I tried looking for this driver install app because I remember seeing it on one of Ubuntu screenshots (not Kubuntu one though). Haven't found it. Oh well, maybe it'll become available after I boot into the real system.

So after trying to break my CD drive rack once more (still don't understand why the system requires me to eject the CD when I reboot\shutdown. I have a door which closes the part where my CD drive is so it will simply won't open if the door is closed damaging the fragile plastic gears used in the tray mechanism.) I rebooted into the real system. First thing - my USB HDD *still* wasn't there. Nowhere to be found and mounter manually. Second, driver install app wasn't there too. No external HDD basically meant a useless system to me because I store all my media files and documents there. So goobye Kubuntu, hello Ubuntu.
Boot to LiveCD, find my USB HDD already discovered, find driver install app, install the system, reboot. Sigh, HDD is still there. Install drivers, download 100+ updates including new kernel, reboot.

Try playing a movie. Alert appears saying codecs are not installed. OK, let's install some codecs then. And here's the part I don't like - the scary "Restricted app" message. While I don't really care about it I know 100% that any average user will be. And that will be an end for the media playback for him if some geek won't come and set it up for him.
Next stop - install Amarok, it being quite good media player. After installing it and building my collection I tried playing some MP3 files knowing what to expect - a pop-up asking to install MP3 codec because it's "restricted'. Boo, scary. Instead Amarok hanged... Restart, select a track, click play, boom, hang again. This time I actually see the pop-up but without any text or buttons. After a few seconds I am told that KNotify crashed.

Oh well, no music for now, let's actually watch a movie. And now here comes another bad thing - movies that played fine on Win on Linux play with huge amount of artifacts and, sometimes, don't play at all looking corrupted. Reboot to Win - plays OK, reboot to Linux - artifacts and corruption.

The rest of the concerns won't come up in a long, unreadable lame story-like way but more in a way of a nicely organized, but still unreadable, list:

1) Kubuntu doesn't offer the same functionality only in KDE like Ubuntu does. And I mean core functionality like USB HDD support
2) An average user WILL be scared by "restricted" stuff no matter what. "Restricted" means dangerous. And dangerous means bad.
3) There is no centralized place to set up a system to your liking. In Mac OS there's System Preferences, in Win there's Control Panel, in Ubuntu there are dozen of little apps scattered through whole menu structure. NOT intuitive, NOT easy to use, NOT good.
4) You absolutely canNOT set your system up without using the console. And console is what an average user is afraid of. Installed drivers ? Cool. But desktop resolution is still 1024x768. Now here comes two options: one of the involve editing xorg.conf manually and another launching nvidia-settings with sudo. Obviously both ways are NOT acceptable to an average user.
5) The system itself is tuned up for terminals of the 80s. If I am using a modern graphical card and LCD display I will have to cope up with extreme ugliness. Heck, even Win2k looked better than modern GNOME and KDE environments. Remember what made Vista and Mac OS successful ? Beautiful GUI, not scary word like "secure".
6) While I already told it I think it deserves it's own number - use of console. It is completely NOT acceptable to the average user. If at least ONCE Joe Smith must use the console to get some basic (and basic involve installing drivers and configuring the system) thing = BAD, very BAD.
7) Some settings are sometimes illogically placed, hard to find and navigate to. 
8) Scary way to install apps. While it really beats anything on Win (because Win doesn't have anything like that) for an experienced user, an average Joe will be shocked when he sees Synaptics screen. "Add\Remove" is a definite step forward but still it is not enough. For example I would personally like to see some codec packs (like CCCP or K-Lite or Vista Codec Pack on Win) being installable from there. Basically a metapackage but what an easy and simple way to add all needed codecs to enjoy the music and video.
9) OS structure is scary. While personally I don't care about all /etc/ /var/ and the rest it can scare the living poo out of an average Joe while he's just trying to find his D: drive (especially if he never bothered to give any labels to his partitions because hdc1 is NOT intuitive (not that I can thing of a better way to represent an unnamed partition)). I suggest to do what Mac OS does - hide all scary folders. I understand it's not possible to put them all in one neat and tidy System folder but at least hide them. Live only the ones user will use on daily basis (like home folder and media folder), the rest are just confusing.

While that's really not the whole list of my concerns those presented here are the ones I think the end user will benefit from. And if anything - read the disclaimer again :)

I'm going to reply in a negative way, because that list is a just opinionated moaning, not really something I'm going to respond in a nice manner to.

Get it into your head that Linux isn't designed to be a "just click and go" affair for n00bs, if you want that then go and buy Vista. Ubuntu is a million times more user friendly and intuitive than, say, BSD, so just because you expect everything to be sitting on a plate for you and you don't want to learn a new system doesn't meant that the OS is at fault.

If you want to troll - and that's exactly what you're doing - about how scary a message box saying "Restricted" is, then go to somewhere with other trolls, don't come to the Ubuntu forums. We'll help you with your problems if you're polite about it, and we'll encourage you to learn about the OS if you're open minded, but if you come along on a big rant about how crap you think Ubuntu is, you're not exactly going to get a great response.

---

### Post by Warren Watts on 2007-07-29
It has more or less been said already in the previous replies, but I want to throw in my two cents anyway. :D

It sounds to me like what you want Ubuntu to be is "The Perfect OS".  There is no such thing.  It looks to me like you set your expectations pretty high when you installed Ubuntu, and now that it doesn't meet your expectations, all you see is flaws.

Ubuntu isn't "Linux for Dummies".  The console and CLI are an integral part of any Linux OS, and offer the user easy access to all of its internal workings.  As a seasoned programmer, you have never opened the console in Windows?  

It is obvious from reading threads posted by Ubuntu Newbies that yes, LOTS of people new to Ubuntu and Linux struggle with the console, but the vast majority of them WANT TO learn to use it and the power that lies within.  That's why they tried Ubuntu in the first place; they wanted something different, something they could learn and grow from.

You are a programmer, right?  Use your programming skills to FIX some of the flaws you see in Ubuntu.  It's all Open Source..  In the spirit of the Ubuntu Community, help make Ubuntu better for everyone.  

Ok, I'll step down off my soapbox now...

Warren

---

### Post by Steveway on 2007-07-29
Works fine here thanks for asking.
There seems to be a Userproblem on your side.

---

### Post by ticopelp on 2007-07-29
If an "average user" is "afraid" to learn even the most basic functions of a new OS, he shouldn't bother learning a new OS. 

Switching to a new operating system requires informing oneself. Period. You seem to be blaming the operating system for your fundamentally wrongheaded assumption that an end user should never have to learn or acquire new knowledge.

---

### Post by Nekiruhs on 2007-07-29
> **Steveway said:**
> Works fine here thanks for asking.
There seems to be a Userproblem on your side.
XD! BEST POST EVER!

---

### Post by wolfen69 on 2007-07-29
he sure likes to use the word "scary" alot. sir, you are wrong on so many levels, i dont know where to begin. i wont.

---

### Post by wolfen69 on 2007-07-29
> **ticopelp said:**
> If an "average user" is "afraid" to learn even the most basic functions of a new OS, he shouldn't bother learning a new OS. 

Switching to a new operating system requires informing oneself. Period. You seem to be blaming the operating system for your fundamentally wrongheaded assumption that an end user should never have to learn or acquire new knowledge.

very well said.

---

### Post by evolving_monkey on 2007-07-29
Hello all,
I am new to Ubuntu. In fact, up until a few months ago I knew only the Linux name. Where Windows is concerned I have used it for years. I guess I got a little board. I'm not sure if am necessarily 'Joe average user" but I am probably closer to that description than many of you. 

This is not a flame job. I don't feel I know enough to correct anyone. From what i read in your post about your credentials I am sure you know far more than I in general. I just wanted to give my thoughts as a new Ububtu/Linux user. 

I dual boot Ubuntu and XP. I still use XP for work (because of work related programs only released for Windows. I realize this is not the fault of Ubuntu.) Since I've loaded virtual machine I've been able to use those programs in Ubuntu via a virtual XP box. I know you might be thinking why not just use windows. The answer to that is that now I have the best of both worlds. I keep an extra copy of my XP virtual box that is activated and updated. If windows scrambles I can simply pull a new working copy and start in VMWare, not reload a system. (that might sound lazy but sometimes you need it to happen fast, just no time to fix or reload.) If I would need to reload Ubuntu it takes about half an hour to get it all back up. Windows is not that convenient. I also have access to all of the stuff in Ubuntu's repositories while using windows. There are actually some programs in those repositories that I have incorporated into my work environment that have really helped me out. For personal use at home I do the same thing(do most testing here). Terminal is slowly becoming my friend.

When I started using Ubuntu I realized that there would probably be a fair amount of learning to do and there has been. For me, however, that's been one of the draws. I'm not afraid of learning especially when what you gain makes it worth the time. Because of Ubuntu I have learned more about Microsoft Windows and operating systems in general. My knowledge of networking and network security has also improved greatly. I now feel I have a computer that comes much closer to meeting my needs and I've learned much in a short amount of time. On top of all that , it hasn't cost me a single cent and I'm not forced to stare at advertisements. That part still blows me away.

Don't get me wrong. I haven't developed the idea that Ubuntu or Linux for that matter are 'bullet proof' or the 'perfect operating system'. So far though, it has been very stable (unless I noob out and get click happy). Sometimes it's gotten frustrating but also very rewarding when I figure it out. Usually the frustration has been the result of 'user error'.

If you are having trouble with media type stuff try adding the medibuntu repositories. There are some additional options there that can't be included in the normal Ubuntu install because of licensing. I read about that in the forums.

That's another plus, the forums. I like the forums here.

I have really enjoyed using Ubuntu. It might not be for everybody but it does give those of us that are interested another good choice.

This is just my opinion. Thanks for reading.

---

### Post by Slavedriver on 2007-07-29
> **seshomaru samma said:**
> with respect , I think the talk of an 'average Joe' is inappropriate here.
the 'average Joe' will never install Linux , if he does then he will cease to be average

The talk about "average Joe" started because of "year of desktop Linux" and such. If Linux aims to become a major competition to Mac or Win it must aim at the average Joe.
> 
the 'average Joe' never installs Windows and certainly wouldn't know how to install drivers when Windows fails to detect them and if you ever installed Windows , that often happens. 

Actually it never happened in my more than long "career" of installing Windows. Maybe I was lucky or didn't use some obscure hardware.
> Is right clicking 'my computer' choosing properties and looking for the 'device manger' intuitive?
Nope, and I agree that Ubuntu's driver app is more intuitive.
> 
I think people who install Ubuntu should expect it to be different from Windows , so should you.
I do expect it to be different. What I also expect it to be at least as easy to use as Windows (and that, by no means, is the ultimate easiness of use).
> If Ubuntu is not what you want, there are a lot of Linux OS's out there.
It's not that Ubuntu is not what I want. I honestly hope it will become a competitive force on the market because it will be good for both Windows and Mac users too because that'll be another OS to steal ideas from...I mean compete with :)
> You say that you are not a troll and that you're not trying to start a flamewar, but your post comes over as whiny and very negative.
As I said - read the disclaimer :) I said that I will probably offend someone but I really didn't mean to. Just bringing my point of view to the masses. That's what the forums are for, I think.
> I have a Mac. I like the OS very much and have much respect for it, but the one thing that really irritates me about MacOS is the way it obfuscates the directory structure. I like to use the GUI as much as possible, but I also like to know what is going on and if I want to dive into the directory structure I want to see it presented the way it is. Linux does this for me.
It is easily fixeable on Mac by enabling Finder to show hidden folders. Basically, if you want it to be seen - you can enable it. Most of the time you don't. At least from GUI file manager. Console, of course, is no limits for restrictions.
> Is there a hidden significance to your username?
Not at all :) It's a long story and basically was a prank on another person which turned into my secondary nickname.
> It sounds to me like what you want Ubuntu to be is "The Perfect OS". There is no such thing. It looks to me like you set your expectations pretty high when you installed Ubuntu, and now that it doesn't meet your expectations, all you see is flaws.
The flaws is not all I see, they just get in the way when I really want to love this OS. Flaws are just obvious because I haven't used this OS a lot and haven't yet learned to counter all of them. With Win or Mac, which are not flawless by any means, I'm just used to ignore them or overcome them. Here I'm not. Yet. And I think sharing my ideas of what OS could (or should) be is beneficial for both me and Ubuntu team because even negative input is better than no input, right ?
> You seem to be blaming the operating system for your fundamentally wrongheaded assumption that an end user should never have to learn or acquire new knowledge.
Have your ever worked as admin in a company any big ?
> If you want to troll - and that's exactly what you're doing - about how scary a message box saying "Restricted" is, then go to somewhere with other trolls, don't come to the Ubuntu forums. We'll help you with your problems if you're polite about it, and we'll encourage you to learn about the OS if you're open minded, but if you come along on a big rant about how crap you think Ubuntu is, you're not exactly going to get a great response.
I always afraid that such people as you will come up and ruin a conversation. You just can't understand that the OS, no matter how good it may look from your side, still has its flaws. If those flaws are fixed it will benefit both sides - yours and mine. Plus, I always thought trolling and whining is just being negative over everything and not providing constructive criticism. Probably I was wrong and you consider trolling every reaction which is not the same as yours. Oh well, at least I tried.

I just hope that one day you will realize that if you want successful Linux on desktop (and successful with the masses, not us, geeks) you will simply **have** to listen to those masses.

---

### Post by Steveway on 2007-07-29
But the problem is that Linux doesn't want to be an OS for the dumb masses.
It's an OS for those who bother to use it and learn howto do it.
Those "Articles" you read on those sites with Linux beeing the Perfect OS for everyone blah blah... that are misconceptions and fanboiism.
If those things disturb you and you can't get away with it than don't use it.
And the only possible way for you to don't start a flamewar here were if you never started this thread, it was a flamewar allready when you thought about writing such a thread.

---

### Post by Slavedriver on 2007-07-29
> i wont. now go away.
Thank you, you just showed me what to expect from helpful Ubuntu community.

> Hello all,
I am new to Ubuntu. In fact, up until a few months ago I knew only the Linux name. Where Windows is concerned I have used it for years. I guess I got a little board. I'm not sure if am necessarily 'Joe average user" but I am probably closer to that description than many of you.

This is not a flame job. I don't feel I know enough to correct anyone. From what i read in your post about your credentials I am sure you know far more than I in general. I just wanted to give my thoughts as a new Ububtu/Linux user.

I dual boot Ubuntu and XP. I still use XP for work (because of work related programs only released for Windows. I realize this is not the fault of Ubuntu.) Since I've loaded virtual machine I've been able to use those programs in Ubuntu via a virtual XP box. I know you might be thinking why not just use windows. The answer to that is that now I have the best of both worlds. I keep an extra copy of my XP virtual box that is activated and updated. If windows scrambles I can simply pull a new working copy and start in VMWare, not reload a system. (that might sound lazy but sometimes you need it to happen fast, just no time to fix or reload.) If I would need to reload Ubuntu it takes about half an hour to get it all back up. Windows is not that convenient. I also have access to all of the stuff in Ubuntu's repositories while using windows. There are actually some programs in those repositories that I have incorporated into my work environment that have really helped me out. For personal use at home I do the same thing(do most testing here). Terminal is slowly becoming my friend.

When I started using Ubuntu I realized that there would probably be a fair amount of learning to do and there has been. For me, however, that's been one of the draws. I'm not afraid of learning especially when what you gain makes it worth the time. Because of Ubuntu I have learned more about Microsoft Windows and operating systems in general. My knowledge of networking and network security has also improved greatly. I now feel I have a computer that comes much closer to meeting my needs and I've learned much in a short amount of time. On top of all that , it hasn't cost me a single cent and I'm not forced to stare at advertisements. That part still blows me away.

Don't get me wrong. I haven't developed the idea that Ubuntu or Linux for that matter are 'bullet proof' or the 'perfect operating system'. So far though, it has been very stable (unless I noob out and get click happy). Sometimes it's gotten frustrating but also very rewarding when I figure it out. Usually the frustration has been the result of 'user error'.

If you are having trouble with media type stuff try adding the medibuntu repositories. There are some additional options there that can't be included in the normal Ubuntu install because of licensing. I read about that in the forums.

That's another plus, the forums. I like the forums here.

I have really enjoyed using Ubuntu. It might not be for everybody but it does give those of us that are interested another good choice.

This is just my opinion. Thanks for reading.

I am not afraid of learning new OS, mind you. It's just that every time I was about to say "This OS actually rocks" it threw a dirty sock in my face. It was either a dead X server which died after me trying to install NVidia drivers following the install guide step-by-step (although it was a random issue it still wasn't very pleasant one having to restore X server manually), buggy media playback (and not codec installing, I, personally, am not afraid of it :)) or Amarok freaking out (BTW if you know the problem I would be glad to hear out the solution to it). I really **want** to like this OS. It's just that it seems it has an endless supply of dirty socks, even more with Mac OS's "think different" stuff.

---

### Post by Slavedriver on 2007-07-29
> And the only possible way for you to don't start a flamewar here were if you never started this thread, it was a flamewar allready when you thought about writing such a thread.
Sorry for me misunderstanding the title of the forum (which is "Ubuntu Testimonials and Experiences" by the way, probably meant "Positive Ubuntu Testimonials and Experiences") and the purpose of forums in general. I think I will stop posting because I really don't want to start a flamewar.

---

### Post by Paul820 on 2007-07-29
Ubuntu isn't perfect, far from it, there is a lot of work still to be done. Most of the guys and girls on the forum want to use ubuntu for their various reasons, they take the time to make it work, me included. Linux isn't windows, things are going to be different from what you are used to. If you had problems you can always ask.

 Hardware is difficult to get going for some, companies won't make them, the ubuntu developers are trying their best to please everyone, it can't be easy. It will get easier to have your hardware detected in the future it's just going to take some time. Have you tried doing a clean install of windows and trying to get all your peripherals working without the drivers? Impossible. You can't even get sound without a sound driver CD. Ubuntu got all mine working without any drivers. That's more than windows can do.

For me, ubuntu works well with all my hardware, wireless etc out of the box. Guess i'm one of the lucky ones.

---

### Post by angryfirelord on 2007-07-29
Weeding out through the words, I tried to put a nice little list of what went wrong:

- usb HDD not detected (fixed with regular Ubuntu)
- install amaroK, mp3s failed (can be fixed with using xmms or totem with the proper gstremer packages installed)

> 1) Kubuntu doesn't offer the same functionality only in KDE like Ubuntu does. And I mean core functionality like USB HDD support
To each is his own. Never had USB issues with Kubuntu. I assumed you went to dmesg and tried to see if ti was detected?
> 2) An average user WILL be scared by "restricted" stuff no matter what. "Restricted" means dangerous. And dangerous means bad.
An average user won't know the difference. A message doesn't appear with big, flashing red letters saying DON'T USE THIS!!!!!!! 
> 3) There is no centralized place to set up a system to your liking. In Mac OS there's System Preferences, in Win there's Control Panel, in Ubuntu there are dozen of little apps scattered through whole menu structure. NOT intuitive, NOT easy to use, NOT good.
You mean going to System-->Preferences & System-->Administration is too hard for you? If you really want, you can enable a gnome control panel by going tinto your menu editor, and enabling it under System-->Preferences.
> 4) You absolutely canNOT set your system up without using the console. And console is what an average user is afraid of. Installed drivers ? Cool. But desktop resolution is still 1024x768. Now here comes two options: one of the involve editing xorg.conf manually and another launching nvidia-settings with sudo. Obviously both ways are NOT acceptable to an average user.
sudo dpkg-reconfigure xserver-xorg. 

The console is not that hard & the belief to be afraid of it is soon gone when it is introduced nicely. Most how-tos involve copy-pasting into the terminal.
> 5) The system itself is tuned up for terminals of the 80s. If I am using a modern graphical card and LCD display I will have to cope up with extreme ugliness. Heck, even Win2k looked better than modern GNOME and KDE environments. Remember what made Vista and Mac OS successful ? Beautiful GUI, not scary word like "secure".
I disagree. Linux can be easily customized to look great (ever hear of beryl?) and is flexible in both the GUI and CLI.

Mac OS, compared to Windows, wouldn't be considered successful and Windows is only considered successful because it's installed on every computer.
> 6) While I already told it I think it deserves it's own number - use of console. It is completely NOT acceptable to the average user. If at least ONCE Joe Smith must use the console to get some basic (and basic involve installing drivers and configuring the system) thing = BAD, very BAD.
Again, not if he's shown it nicely. The console IS NOT A BIG SCARY THING!!! 
> 7) Some settings are sometimes illogically placed, hard to find and navigate to. 
Like what?
>  8 Scary way to install apps. While it really beats anything on Win (because Win doesn't have anything like that) for an experienced user, an average Joe will be shocked when he sees Synaptics screen. "Add\Remove" is a definite step forward but still it is not enough. For example I would personally like to see some codec packs (like CCCP or K-Lite or Vista Codec Pack on Win) being installable from there. Basically a metapackage but what an easy and simple way to add all needed codecs to enjoy the music and video.
Synaptic isn't that hard to use. I think joe can handle using the search button.
> 9) OS structure is scary. While personally I don't care about all /etc/ /var/ and the rest it can scare the living poo out of an average Joe while he's just trying to find his D: drive (especially if he never bothered to give any labels to his partitions because hdc1 is NOT intuitive (not that I can thing of a better way to represent an unnamed partition)). I suggest to do what Mac OS does - hide all scary folders. I understand it's not possible to put them all in one neat and tidy System folder but at least hide them. Live only the ones user will use on daily basis (like home folder and media folder), the rest are just confusing.

Why? It's just that he has to get used to it being different, not confusing.
> And if anything - read the disclaimer again
Yup, I think you should read it too.

---

### Post by tashmooclam on 2007-07-29
The original post has a lot of validity. There are several reasons for this. 
The average professional or educated person is NOT a computer professional. 
The purpose of this forum, according to Ubuntu, is to serve as a help tool for anyone. This the intent of the forum, not to exclude "dopes" who happen to have other things to learn about in life than why software critical for funcionality of their computer is missing. "Open source"?? This is jargon to 90% of the people. 
I personally like my Ubuntu now, but it's been a struggle. I still find the font rendering very unatractive. I know there are fixes, but I can't do it myself yet. 
A complete Linux virgin will browse magazine racks and see "Ubuntu is #1!" They will also see that Dell sells computers with Ubuntu on them. They will see this forum touted as the perfect way to learn about using Ubuntu. 
But, I am very pleased now and await future events. I also know that the various "flavors" of Linux will be improvements, like maybe Linux Mint, or Sabayon. 
If the guys who really know about Linux and Ubuntu made the slightest effort at it, they have money making opportunities galore.
I would have paid for a little pamphlet about getting started, how to use the Add/Remove, Synaptic manager, file management, etc. I would have sent a paypal for a pdf about it.
I would have paid for a CD-Rom with some mpeg videos about how to use this.
I would have paid a few bux for Ubuntu to come with everything you need already on it.
I would have paid a few bux for a version of Ubuntu with decent font rendering so I don't get double vision using Openoffice Writer. I'm tearing my hair out trying to figure out how to make my crazy trackpad behave, there's no menu for it!
I would have paid the cost of one of those overpriced books about Ubuntu, total about $30. 
Maybe someday I'll figure it out and get my friends to use Linux and they'll pay me a few bux to "customize" Linux and everyone will be happy. 
Linux and Mac are the future, but to be honest, it can be a real pain in the butt to move from Windows to Linux, and that's not the way it should be. 
I recommend the first poster give it a try with Linux Mint and see how it goes. 
Viva Linux!

---

### Post by Steveway on 2007-07-29
I once read an article, it told about some years ago when the only persons using computers were people who knew what they did.
Then Microsoft came with it's Windows-operatin-system and made those computers avaiable to everyone by dumbing everything and everyone down.
Those users now think that an operating-system has to be easy and should do everything for them, they even expect beeing spyed and getting Viruses is a normal thing in every OS.
Those people are your "average joeys" and normally they are not meant to even use a Pc.
I myself even go that far to say that this slowed down development(Sub-Pixel-rendering anyone?).
Sometimes I really wish to be back in those times without dumbed down people beeing able to use Pc's.
And Slavedriver, there is no need to stop posting now, after you allready started this Thread, now finish it hounorfull.

---

### Post by dasunst3r on 2007-07-29
Sorry that Ubuntu didn't work out for you.  Taking the step of at least giving Linux a chance, I will say, takes some guts.  I remember taking the leap three years ago: Wired networking was a pain, I had to use the console to mount a USB drive, and dependencies were heck!

To add on to what everybody else said, please come back in six months.  We'll have a new release waiting for you.  Even if you won't come back, thanks for having tried it.

---

### Post by Slavedriver on 2007-07-29
> 
- usb HDD not detected (fixed with regular Ubuntu)
- install amaroK, mp3s failed (can be fixed with using xmms or totem with the proper gstremer packages installed)
Withing the recent time interval - yes. And mp3s work fine with Totem\Rythmbox, I just wanted to use Amarok (especially seeing that it has a label "Works with this distro").
> To each is his own. Never had USB issues with Kubuntu. I assumed you went to dmesg and tried to see if ti was detected?
Nope, didn't bother plus didn't know the way to do it.
> An average user won't know the difference. A message doesn't appear with big, flashing red letters saying DON'T USE THIS!!!!!!! 
Just tried it on my mom asking what button she would click. The answer was "I will click no, like you told me to click on all suspicious messages". And no, I didn't tell her that just before showing in to her.
> sudo dpkg-reconfigure xserver-xorg
Ehem. The quoted post says about not using the console to configure stuff yet you post a line to be executed in the terminal. I think putting NVidia preferences in the menu would solve the problem even more easily.
> I disagree. Linux can be easily customized to look great (ever hear of beryl?) and is flexible in both the GUI and CLI.
Not even heard but use it. Again, we are talking about customization. I can customize every system like there's no tomorrow. But I was talking about out of the box experience.
> Mac OS, compared to Windows, wouldn't be considered successful and Windows is only considered successful because it's installed on every computer.
I would partially disagree with Windows part but only partially.
> Why? It's just that he has to get used to it being different, not confusing.
Lot's of system folders are confusing. With Windows you know that Windows folder is no touchie. With Mac you know that System folder is no touchie. This, of course, does not apply to the geek users who are the current auditory of Linux anyway but IMO (and only IMO) it would be a nice touch. At least it will make me scroll less :)
> You mean going to System-->Preferences & System-->Administration is too hard for you?
Not hard, inconvenient. Taking stairs to 5th floor is also not hard. But inconvenient as hell.
> I once read an article, it told about some years ago when the only persons using computers were people who knew what they did.
Then Microsoft came with it's Windows-operatin-system and made those computers avaiable to everyone by dumbing everything and everyone down.
Those users now think that an operating-system has to be easy and should do everything for them, they even expect beeing spyed and getting Viruses is a normal thing in every OS.
Those people are your "average joeys" and normally they are not meant to even use a Pc.
I myself even go that far to say that this slowed down development(Sub-Pixel-rendering anyone?).
Sometimes I really wish to be back in those times without dumbed down people beeing able to use Pc's.
You don't have to know how internal combustion engine works to drive a car.
> To add on to what everybody else said, please come back in six months. We'll have a new release waiting for you. Even if you won't come back, thanks for having tried it.
First of all, I just won't leave :) I will try to continue using Ubuntu (at least as long as I won't get off my butt and fix my Win) and I am really awaiting the release of Gutsy.

---

### Post by Geekkit on 2007-07-29
Sorry to hear it didn't work out for you. Take the blue pill and all will return to normal.

---

### Post by Lord Illidan on 2007-07-29
Not a bad post. Between me and you, I agree with most of what you say. There are usability problems, software problems, and hardware problems.

>  Truth be told I had to try Linux recently because my few-years-old XP install is going haywire (you know like it becomes after a few years of extensive use) and all movies I tried to watch started to lag like hell. So, after reading another portion of "Linux is superior to everything" on Slashdot (really, guys, at lest try to be less biased) I decided to install latest version of Kubuntu (I had 6.06 installed prior to that just to try it out but I haven't used it a lot).

Fanboyism is rampant on Slashdot, and most other tech/geek sites. However, a linux installation, configured correctly, is a thing of beauty in my opinion. Stable, secure, and can look very nice.

>  Seeing that 7.04 was supposed to come with a nifty app to install the drivers I was quite please because the horror of trying to get my NVidia to work on 6.06 was still fresh. First thing I noticed when booted to LiveCD is that my external USB HDD wasn't visible. Oh well, I though, I'll browse the web without listening to music while waiting it to install. So I fired up the installation app, sniped my town from the world map (really guys add the zoom feature from Ubuntu's installer) to select the timezone and moved on with the installation. Meanwhile I tried looking for this driver install app because I remember seeing it on one of Ubuntu screenshots (not Kubuntu one though). Haven't found it. Oh well, maybe it'll become available after I boot into the real system.

I'd like to hear more about the External USB HDD not being detected in Kubuntu. Can you open a separate thread, and give the details of the usb hdd, and about your computer. It could very well be a legitimate bug. Regarding drivers, I guess they come in when you boot from harddrive, as I believe the nvidia driver requires you to reboot in Ubuntu. (Really, you could probably use CTRL ALT X to restart X, but rebooting is preferred).

>  So after trying to break my CD drive rack once more (still don't understand why the system requires me to eject the CD when I reboot\shutdown. I have a door which closes the part where my CD drive is so it will simply won't open if the door is closed damaging the fragile plastic gears used in the tray mechanism.) I rebooted into the real system. First thing - my USB HDD *still* wasn't there. Nowhere to be found and mounter manually. Second, driver install app wasn't there too. No external HDD basically meant a useless system to me because I store all my media files and documents there. So goobye Kubuntu, hello Ubuntu.

System requires you to eject CD because if you leave it there you'll probably reboot straight into the live cd again. Countless newbies could make this mistake :P All you have to do is leave that door open.
> 
Boot to LiveCD, find my USB HDD already discovered, find driver install app, install the system, reboot. Sigh, HDD is still there. Install drivers, download 100+ updates including new kernel, reboot.

Try playing a movie. Alert appears saying codecs are not installed. OK, let's install some codecs then. And here's the part I don't like - the scary "Restricted app" message. While I don't really care about it I know 100% that any average user will be. And that will be an end for the media playback for him if some geek won't come and set it up for him.
Next stop - install Amarok, it being quite good media player. After installing it and building my collection I tried playing some MP3 files knowing what to expect - a pop-up asking to install MP3 codec because it's "restricted'. Boo, scary. Instead Amarok hanged... Restart, select a track, click play, boom, hang again. This time I actually see the pop-up but without any text or buttons. After a few seconds I am told that KNotify crashed.

Regarding Restricted app, it's actually important, because of numerous probable patent issues with the mp3 codecs and others. Regarding Amarok..interesting, can you start a new thread about it. Also, start it from the terminal ```
amarokapp
```, and paste the output. Probably it is a codec issue..since Amarok uses a different engine, xine. Try installing libxine-extracodecs (enable multiverse and universe).

>  Oh well, no music for now, let's actually watch a movie. And now here comes another bad thing - movies that played fine on Win on Linux play with huge amount of artifacts and, sometimes, don't play at all looking corrupted. Reboot to Win - plays OK, reboot to Linux - artifacts and corruption.

Again..what kind of movies? I can play .divx, .mov, .wmv (not DRM encrypted though), .mpg, .avi perfectly well. It could be a problem with Totem..in that case try installing vlc from the repositories.

The rest of the concerns won't come up in a long, unreadable lame story-like way but more in a way of a nicely organized, but still unreadable, list:

>  1) Kubuntu doesn't offer the same functionality only in KDE like Ubuntu does. And I mean core functionality like USB HDD support

I'm pretty certain that was a one-off..probably a bug.

>  2) An average user WILL be scared by "restricted" stuff no matter what. "Restricted" means dangerous. And dangerous means bad.

There is a bit of a danger, regarding legal problems...

>  3) There is no centralized place to set up a system to your liking. In Mac OS there's System Preferences, in Win there's Control Panel, in Ubuntu there are dozen of little apps scattered through whole menu structure. NOT intuitive, NOT easy to use, NOT good.

Hmm, this is a matter of taste. There is a control panel for Ubuntu, called Gnome Control Center. To enable it, rightclick on the menu, choose Edit menus, go on Preferences and chose Control Center.

> 4) You absolutely canNOT set your system up without using the console. And console is what an average user is afraid of. Installed drivers ? Cool. But desktop resolution is still 1024x768. Now here comes two options: one of the involve editing xorg.conf manually and another launching nvidia-settings with sudo. Obviously both ways are NOT acceptable to an average user.

I have to agree with you there about the resolution..probably Xorg 7.3 should fix it, but yes, it's quite a bug..given that Fedora gave me full resolution automatically..without even installing the drivers (nv).


>  5) The system itself is tuned up for terminals of the 80s. If I am using a modern graphical card and LCD display I will have to cope up with extreme ugliness. Heck, even Win2k looked better than modern GNOME and KDE environments. Remember what made Vista and Mac OS successful ? Beautiful GUI, not scary word like "secure".

Taste is subjective...I wonder why it looks ugly to you? KDE, I can understand, the kicker is pretty ugly (without customisation). Gnome looks nice to me though. Also, there are cool programs like Compiz which can really snazz up your system.

>  6) While I already told it I think it deserves it's own number - use of console. It is completely NOT acceptable to the average user. If at least ONCE Joe Smith must use the console to get some basic (and basic involve installing drivers and configuring the system) thing = BAD, very BAD.

Well, I agree and disagree.

The console is great for many things. Fast, and in the hands of an experienced user, very easy to use.

However, I agree that newbies will have problems with it. When I started Linux, I couldn't even locate it from the menu. However, with the latest Ubuntu, can't say I really needed to use the console that much.


>  7) Some settings are sometimes illogically placed, hard to find and navigate to. 

Which ones?

>  8) Scary way to install apps. While it really beats anything on Win (because Win doesn't have anything like that) for an experienced user, an average Joe will be shocked when he sees Synaptics screen. "Add\Remove" is a definite step forward but still it is not enough. For example I would personally like to see some codec packs (like CCCP or K-Lite or Vista Codec Pack on Win) being installable from there. Basically a metapackage but what an easy and simple way to add all needed codecs to enjoy the music and video.

Codec Pack is automatically installed when you play an mp3, for example..With regard to Synaptic...well, it is very userfriendly in my opinion. I wonder if an average joe would really be shocked. My friends liked the look of it..

>  9) OS structure is scary. While personally I don't care about all /etc/ /var/ and the rest it can scare the living poo out of an average Joe while he's just trying to find his D: drive (especially if he never bothered to give any labels to his partitions because hdc1 is NOT intuitive (not that I can thing of a better way to represent an unnamed partition)). I suggest to do what Mac OS does - hide all scary folders. I understand it's not possible to put them all in one neat and tidy System folder but at least hide them. Live only the ones user will use on daily basis (like home folder and media folder), the rest are just confusing.

IMHO, C: is more confusing than hdc1...

Here, I both agree and disagree. I never use the folders /etc /usr in a gui, just in a terminal..so if they were hidden, I wouldn't care. But..scary? Hmm...

---

### Post by Lord Illidan on 2007-07-29
> **Geekkit said:**
> Sorry to hear it didn't work out for you. Take the blue pill and all will return to normal.

Being snarky is not going to help anyone here. Let's show what a great community we are by helping this guy, and the people who also share his problems.

---

### Post by xpod on 2007-07-29
Can i  just say that i`ve only read as far as the very first paragraph in the OP and without reading another word i can pretty much imagine the rest.....

I`ll sum it up in one single phrase shall i..."if i cant mange it then how the hell are mom or pop ever going to manage it"......or words to that effect??
Am i far wrong????

I do get pretty sick of repeating my own experience nowadays but it can have a lasting effect on many a self-proclaimed expert i`ve found......plus it`s about all i can do to help a user on in most cases of course:)

I AM pop here in my little world slavedriver and Prior to discovering Ubuntu last July i`d used a computer for all of 4 months.
Windows of course.One year on me and  my kids all use Ubuntu like it was second nature......I *know* how little i know about computers compared to some of the whizkids,geeks & gamers on this place but boy have i heard my fill of so called experts complaining about how complicated & difficult it is.

Darn right it`s complicated & difficult but it`s not that hard to figure out given a bit of time & paitence surely?l
In hindsight i actually cringe at some of the stupid questions i asked last year but as they say theres no such thing as  a stupid question.......only stupid answers eh

I`m sure everything seems uber difficult & over complicated just now but you have to understand that this is mostly years of Windows making it seem that way.It`s only your unfamiliarity speaking for sure......Hell,I know how hard it was for me after only months with Windows so i can only imagine it from your point of view.

I started with computers quite late in life myself but i`m ever so thankfull i arrived when i did and never had the clouded judgement that many seem to arrive here with....so to speak.

Whatever your problems slavedriver i`m sure you`ll overcome them......i`ll have faith in you pal even though you`ve none in yourself at the momen okt:wink:

After all,are you really going to let some stupid box of wires get the better of you????????

---

### Post by Lord Illidan on 2007-07-29
It is difficult at first. However, preservation is the name of the game. Heaven knows how much I swore at my old Fedora Core install...dependency hell!

---

### Post by Geekkit on 2007-07-29
> **Lord Illidan said:**
> 
There is a bit of a danger, regarding legal problems...


Technically the only danger is to Canonical and not to the end user. For those few countries that actually have laws such as the United States with their Digital Millennium Copyright Act (DMCA), there are back doors. Section 1201(f) allows users to have/use software used to decrypt so long as the user is doing so to achieve interoperability of open source operating systems with proprietary operating systems.

However Canonical cannot know what Ubuntu end users are using the software for and so they would be putting themselves at risk (and hence liability and endless years of mitigation). Canonical could put a license agreement in place that forced users to take responsibility and agree that they're not going to use the encryption bypass mechanism for encoding, only for decoding. But that would fly in the face of what Ubuntu is all about so instead they let the end user download what's needed and make up their mind themselves. Power to the people and all that.

Most people just see "Restricted" and blindingly and narrow-mindedly say to themselves that downloading the software is "illegal" or "immoral" or worse ... must be supporting communism or something silly like that.

---

### Post by Geekkit on 2007-07-29
> **Lord Illidan said:**
> Being snarky is not going to help anyone here. Let's show what a great community we are by helping this guy, and the people who also share his problems.

You misread my response - there's nothing snarky in it. He's already made his mind up and so my implication was to simply go back to Windows where the feelings of defensiveness will go away and so will all his frustration and life will return to normal.

---

### Post by evolving_monkey on 2007-07-29
I wanted to add a few things that helped me out. I had to switch computers. I was playing on my slop system and I realized I didn't have the bookmarks.

Here are a few links:
[http://ubuntuforums.org/showthread.php?t=382137&highlight=desklets](http://ubuntuforums.org/showthread.php?t=382137&highlight=desklets)

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[http://ubuntuforums.org/showthread.php?t=202605&highlight=file+sharing](http://ubuntuforums.org/showthread.php?t=202605&highlight=file+sharing)

[http://www.vmware.com/](http://www.vmware.com/)

[http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php)

[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html#more-143](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html#more-143)

[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

I hope a few of those help ease some of your frustration. Good Luck. 

(Maybe everyone could post a few sites that helped them figure things out. I'm curious myself.)

---

### Post by justin whitaker on 2007-07-29
You know what, I'm going to try to be helpful.

> **Slavedriver said:**
> First of all, a little disclaimer.
1) I am not trying to start a flamewar. Merely pointing out what I didn't like in a system being pushed so hard in my face (yes Slashdot, I am talking about you)

Yes, you are right. There is a vehemently pro-Linux group on Slashdot that seem to mod each other up...so everything there makes Linux look like a panacea for the technology world....I fell to that line of bull too, so don't feel bad. 

Linux is by no means perfect, and takes alot of learning. I've been dabbling for years, so I have more experience than the average noob, but there are big scarey areas still that I am convinced are inhabited by Grues.

> 2) I am NOT trying to start a flamewar. No, really. I may be overly critical, ironic, maybe a bit offending to some people, heck, I know I WILL offend someone, but that's how I am. Not a troll. Not as green as a troll at least.

For future reference, most people that say they aren't trolls usually are in my experience. 

> 3) I am programmer by trade who works with both Windows and Mac OS a lot and has to use console in his daily work more than GUI. That means I am really OK with the console, not afraid of it and sometimes even prefer it to GUI.

Console FTW! Ok, that's not a helpful comment really.

> 4) While I prefer Windows XP to all OSes I tried a lot of other OSes out there to form an opinion of what a perfect OS should be (and that were all flavors of Win starting from 3.11, all flavors of Mac OS X starting from 10.1 and a few flavors of Linux).

If you build the perfect OS, let us know. 

> 5) This is my opinion, biased, subjective, but mine. If you can't cope with somebody expressing a different opinion from your own - please deal with it in a civil manner.

Well, that's a bit redundant...we have a CoC here, and it is enforced. 

> Truth be told I had to try Linux recently because my few-years-old XP install is going haywire (you know like it becomes after a few years of extensive use) and all movies I tried to watch started to lag like hell. So, after reading another portion of "Linux is superior to everything" on Slashdot (really, guys, at lest try to be less biased) I decided to install latest version of Kubuntu (I had 6.06 installed prior to that just to try it out but I haven't used it a lot).

We've all been there. Some of us are here because of licensing, some for politics, some because XP got all wonky on us....that said, Kubuntu is good, but is significantly different from Ubuntu in several ways, and lacks some of the fit and finish of the main distro. So starting there, and judging the entire project by that is saying that the apples suck when you are eating a pear. :)

> Seeing that 7.04 was supposed to come with a nifty app to install the drivers I was quite please because the horror of trying to get my NVidia to work on 6.06 was still fresh. First thing I noticed when booted to LiveCD is that my external USB HDD wasn't visible. Oh well, I though, I'll browse the web without listening to music while waiting it to install. So I fired up the installation app, sniped my town from the world map (really guys add the zoom feature from Ubuntu's installer) to select the timezone and moved on with the installation. Meanwhile I tried looking for this driver install app because I remember seeing it on one of Ubuntu screenshots (not Kubuntu one though). Haven't found it. Oh well, maybe it'll become available after I boot into the real system.

I find USB on Feisty to be problematic. One of the issues is that HAL finds it, but doesn't always keep it connected, especially if your External USB drive is NTFS formatted. The ways around this is to add the eternal drive to your FSTAB file (there is a big thread on that here somewhere), and making sure that ntfs-3g is enabled.

For Nvidia drivers, there are several options. One is via add/remove in the start menu. You have to switch it so that All Available Applications are being shown.

You can also use Easy Ubuntu, Automatix, or Envy to install the drivers in an easy, automated, way.

> [quote]So after trying to break my CD drive rack once more (still don't understand why the system requires me to eject the CD when I reboot\shutdown. I have a door which closes the part where my CD drive is so it will simply won't open if the door is closed damaging the fragile plastic gears used in the tray mechanism.) I rebooted into the real system. First thing - my USB HDD *still* wasn't there. Nowhere to be found and mounter manually. Second, driver install app wasn't there too. No external HDD basically meant a useless system to me because I store all my media files and documents there. So goobye Kubuntu, hello Ubuntu.

See above. Also, under System>Administration there is the Restricted Driver manager. I think that is what you are looking for. 

> Boot to LiveCD, find my USB HDD already discovered, find driver install app, install the system, reboot. Sigh, HDD is still there. Install drivers, download 100+ updates including new kernel, reboot.

Yep, lots of security fixes, some bug fixes, and a flashy new kernel. You don't need to update all of them, if you do not want to, it's more of a suggestion.

> Try playing a movie. Alert appears saying codecs are not installed. OK, let's install some codecs then. And here's the part I don't like - the scary "Restricted app" message. While I don't really care about it I know 100% that any average user will be. And that will be an end for the media playback for him if some geek won't come and set it up for him.

Yep, that's a scarey message, and I dislike it. I get the whole reason why the codecs are not included by default, but the whole "you can go to jail for this you lawbreaker" thing has got to go.

> Next stop - install Amarok, it being quite good media player. After installing it and building my collection I tried playing some MP3 files knowing what to expect - a pop-up asking to install MP3 codec because it's "restricted'. Boo, scary. Instead Amarok hanged... Restart, select a track, click play, boom, hang again. This time I actually see the pop-up but without any text or buttons. After a few seconds I am told that KNotify crashed.

I love Amarok, but it crashes on Ubuntu quite a bit, for no apparent reason. If you have space, install Kubuntu alongside Ubuntu, and this fixes it. It's about 300+ mb for the ability to use KDE apps without them crashing.

> Oh well, no music for now, let's actually watch a movie. And now here comes another bad thing - movies that played fine on Win on Linux play with huge amount of artifacts and, sometimes, don't play at all looking corrupted. Reboot to Win - plays OK, reboot to Linux - artifacts and corruption.

Try Mplayer, or VLC. Both are better than the default Movie Player, and essential Linux apps. 

> 1) Kubuntu doesn't offer the same functionality only in KDE like Ubuntu does. And I mean core functionality like USB HDD support

You are absolutely correct. 

> 2) An average user WILL be scared by "restricted" stuff no matter what. "Restricted" means dangerous. And dangerous means bad.

Again, you are correct, but I think legally they have to say something....maybe there is a better spin that can be put on it?

> 3) There is no centralized place to set up a system to your liking. In Mac OS there's System Preferences, in Win there's Control Panel, in Ubuntu there are dozen of little apps scattered through whole menu structure. NOT intuitive, NOT easy to use, NOT good.

Actually, there is a Control Center in KDE where you can manipulate your system to your heart's content. There are 3rd party projects that bring all that functionality to Gnome...but most of it is under "System" anyway.

> 4) You absolutely canNOT set your system up without using the console. And console is what an average user is afraid of. Installed drivers ? Cool. But desktop resolution is still 1024x768. Now here comes two options: one of the involve editing xorg.conf manually and another launching nvidia-settings with sudo. Obviously both ways are NOT acceptable to an average user.

I am of two minds about this: first, the system should be as console free as possible, but I also think that if you aren't going to learn the CLI, then you are missing out on one of the most powerful features of Linux and Unix as a whole. 

There is a balance to be achieved there too, I think. 

> 5) The system itself is tuned up for terminals of the 80s. If I am using a modern graphical card and LCD display I will have to cope up with extreme ugliness. Heck, even Win2k looked better than modern GNOME and KDE environments. Remember what made Vista and Mac OS successful ? Beautiful GUI, not scary word like "secure".

On my Gutsy Gibbon Tribe 3 desktop, it is nothing short of beautiful. Wobbly windows and all. Have you seen what people are doing in the Monthly Desktop threads? 

> 6) While I already told it I think it deserves it's own number - use of console. It is completely NOT acceptable to the average user. If at least ONCE Joe Smith must use the console to get some basic (and basic involve installing drivers and configuring the system) thing = BAD, very BAD.

Agreed, as discussed above.

> 7) Some settings are sometimes illogically placed, hard to find and navigate to. 

Go over to Launchpad, and submit the suggestions as a bug. The more input the developers have, the better it is for all of us.

> 8) Scary way to install apps. While it really beats anything on Win (because Win doesn't have anything like that) for an experienced user, an average Joe will be shocked when he sees Synaptics screen. "Add\Remove" is a definite step forward but still it is not enough. For example I would personally like to see some codec packs (like CCCP or K-Lite or Vista Codec Pack on Win) being installable from there. Basically a metapackage but what an easy and simple way to add all needed codecs to enjoy the music and video.

They pretty much have this in Gutsy. Just wait a while. 

> 9) OS structure is scary. While personally I don't care about all /etc/ /var/ and the rest it can scare the living poo out of an average Joe while he's just trying to find his D: drive (especially if he never bothered to give any labels to his partitions because hdc1 is NOT intuitive (not that I can thing of a better way to represent an unnamed partition)). I suggest to do what Mac OS does - hide all scary folders. I understand it's not possible to put them all in one neat and tidy System folder but at least hide them. Live only the ones user will use on daily basis (like home folder and media folder), the rest are just confusing.

Most of the time, you only need to muck around in /home. There are some projects, like GoboLinux, that hide everything, but there are technical reasons why Ubuntu has not done it: they are trying to stay compatible with Debian being the first of them, and Debian is not about to change the file system. 

> While that's really not the whole list of my concerns those presented here are the ones I think the end user will benefit from. And if anything - read the disclaimer again :)

Hope I helped in some small way. Again, anything that you think needs to be fixed, submit a bug for it.

---

### Post by xpod on 2007-07-29
> 5) The system itself is tuned up for terminals of the 80s. If I am using a modern graphical card and LCD display I will have to cope up with extreme ugliness. Heck, even Win2k looked better than modern GNOME and KDE environments. Remember what made Vista and Mac OS successful ? Beautiful GUI, not scary word like "secure".

lol
[ATTACH]39303[/ATTACH]   [ATTACH]39304[/ATTACH]   [ATTACH]39305[/ATTACH]

I should have read the thing first after all
You dont have to "cope" with anything in Ubuntu or indeed Linux.*You* can change things till your hearts content if truth be told.All you have to do is give it the time & patience it deserves and you`ll see.
You can make linux look like absoultely anything you`ve ever imagined, i imagine,even your beautiful ole Win2k if you so desire....how about Vista even??......Mac possibly??the choices are indeed endless.

Running all that stuff on my meager resources....with a crappy 64Mb gfx(and broken 512Mb of ram it seems) is not what i usually do to tell the truth but the fact that i can speaks volumes compared with certain other graphical features i could mention on certain other operating systems.
I can only wonder at what your more modern stuff is capable of

Close them dirty Windows & open your mind i say.

---

### Post by ticopelp on 2007-07-30
> You don't have to know how internal combustion engine works to drive a car

No, but you do have to know how to operate the controls. And if the controls are different than the car you're used to, you can either moan that the controls "aren't ready for the driver," or you can stop complaining and start learning.

---

### Post by M$LOL on 2007-07-30
> **justin whitaker said:**
> You know what, I'm going to try to be helpful.



Yes, you are right. There is a vehemently pro-Linux group on Slashdot that seem to mod each other up...so everything there makes Linux look like a panacea for the technology world....I fell to that line of bull too, so don't feel bad. 

Linux is by no means perfect, and takes alot of learning. I've been dabbling for years, so I have more experience than the average noob, but there are big scarey areas still that I am convinced are inhabited by Grues.



For future reference, most people that say they aren't trolls usually are in my experience. 



Console FTW! Ok, that's not a helpful comment really.



If you build the perfect OS, let us know. 



Well, that's a bit redundant...we have a CoC here, and it is enforced. 



We've all been there. Some of us are here because of licensing, some for politics, some because XP got all wonky on us....that said, Kubuntu is good, but is significantly different from Ubuntu in several ways, and lacks some of the fit and finish of the main distro. So starting there, and judging the entire project by that is saying that the apples suck when you are eating a pear. :)



I find USB on Feisty to be problematic. One of the issues is that HAL finds it, but doesn't always keep it connected, especially if your External USB drive is NTFS formatted. The ways around this is to add the eternal drive to your FSTAB file (there is a big thread on that here somewhere), and making sure that ntfs-3g is enabled.

For Nvidia drivers, there are several options. One is via add/remove in the start menu. You have to switch it so that All Available Applications are being shown.

You can also use Easy Ubuntu, Automatix, or Envy to install the drivers in an easy, automated, way.


See above. Also, under System>Administration there is the Restricted Driver manager. I think that is what you are looking for. 



Yep, lots of security fixes, some bug fixes, and a flashy new kernel. You don't need to update all of them, if you do not want to, it's more of a suggestion.



Yep, that's a scarey message, and I dislike it. I get the whole reason why the codecs are not included by default, but the whole "you can go to jail for this you lawbreaker" thing has got to go.



I love Amarok, but it crashes on Ubuntu quite a bit, for no apparent reason. If you have space, install Kubuntu alongside Ubuntu, and this fixes it. It's about 300+ mb for the ability to use KDE apps without them crashing.



Try Mplayer, or VLC. Both are better than the default Movie Player, and essential Linux apps. 



You are absolutely correct. 



Again, you are correct, but I think legally they have to say something....maybe there is a better spin that can be put on it?



Actually, there is a Control Center in KDE where you can manipulate your system to your heart's content. There are 3rd party projects that bring all that functionality to Gnome...but most of it is under "System" anyway.



I am of two minds about this: first, the system should be as console free as possible, but I also think that if you aren't going to learn the CLI, then you are missing out on one of the most powerful features of Linux and Unix as a whole. 

There is a balance to be achieved there too, I think. 



On my Gutsy Gibbon Tribe 3 desktop, it is nothing short of beautiful. Wobbly windows and all. Have you seen what people are doing in the Monthly Desktop threads? 



Agreed, as discussed above.



Go over to Launchpad, and submit the suggestions as a bug. The more input the developers have, the better it is for all of us.



They pretty much have this in Gutsy. Just wait a while. 



Most of the time, you only need to muck around in /home. There are some projects, like GoboLinux, that hide everything, but there are technical reasons why Ubuntu has not done it: they are trying to stay compatible with Debian being the first of them, and Debian is not about to change the file system. 



Hope I helped in some small way. Again, anything that you think needs to be fixed, submit a bug for it.


See, this is the sort of helpful response you'll get from all of us if you ask nicely. But you're not going to get it if you moan at us about how crap you think our OS is.

---

### Post by Slavedriver on 2007-07-30
> But you're not going to get it if you moan at us about how crap you think our OS is
Why pointing out issues is moaning and calling something crap ? The only OS I can call crap is Mac OS but that's not because of objective reasons :)
> Again..what kind of movies? I can play .divx, .mov, .wmv (not DRM encrypted though), .mpg, .avi perfectly well. It could be a problem with Totem..in that case try installing vlc from the repositories.
AVI encoded with DivX.
> There is a bit of a danger, regarding legal problems...
I know of possible legal problems.
> Taste is subjective...I wonder why it looks ugly to you? KDE, I can understand, the kicker is pretty ugly (without customisation). Gnome looks nice to me though. Also, there are cool programs like Compiz which can really snazz up your system.
It's just that antialising, transparency and all other cool stuff comes along with Compiz\Beryl. And I was talking about out of the box experience.
> Well, I agree and disagree.

The console is great for many things. Fast, and in the hands of an experienced user, very easy to use.
Indeed, but the key word here is *experienced*. I love console myself, it's just that I highly doubt my mom will too.
> IMHO, C: is more confusing than hdc1...
Well, C: always denoted the main drive where you system is. HDC1...I don't think it's taht self explanatory to a user coming from Windows (and most users come from Windows AFAIK).
> I`ll sum it up in one single phrase shall i..."if i cant mange it then how the hell are mom or pop ever going to manage it"......or words to that effect??
Am i far wrong????
Like you, I won't read the rest of the post and say "No, you are not". Compiling something from source and tweaking the code to get something to work the way I want it is OK with me. I just won't call it convenient and what I've imagined my daily workflow with an OS.
> If you build the perfect OS, let us know. 
As soon as somebody will implement DWIM - I will :)
> I am of two minds about this: first, the system should be as console free as possible, but I also think that if you aren't going to learn the CLI, then you are missing out on one of the most powerful features of Linux and Unix as a whole.

There is a balance to be achieved there too, I think. 
I do agree. I just think that the initial setup should be as much console free as possible. 
> Have you seen what people are doing in the Monthly Desktop threads?

Have quite a beautiful system myself. Again, I was talking about out of the box experience. While wobbly windows are cool the problem of juggy edges and low res graphics is still there. KDE4 seems to be going in the right direction though...
> Most of the time, you only need to muck around in /home. There are some projects, like GoboLinux, that hide everything, but there are technical reasons why Ubuntu has not done it: they are trying to stay compatible with Debian being the first of them, and Debian is not about to change the file system.
I don't think that hiding some folders will actually change the filesystem. Of course if it won't involve renaming them or such.
> And if the controls are different than the car you're used to, you can either moan that the controls "aren't ready for the driver," or you can stop complaining and start learning.
...and all cars have a common set of controls in common places following some standard... Haven't seen a lot of successful cars with the steering wheel on the back seat (not drawing any parallels here).

---

### Post by wolfen69 on 2007-07-30
can your mom setup a windows machine from scratch?

---

### Post by Slavedriver on 2007-07-30
> can your mom setup a windows machine from scratch?
Nope, not from scratch. But setting up UI stuff, application preferences and alike are quite OK with her. Plus even if she would have to install Windows she won't have to set anything up. People didn't invent nLite just for nothing you know...

---

### Post by heimo on 2007-07-30
> **Slavedriver said:**
> I think I will stop posting because I really don't want to start a flamewar.

Probably a good idea.

---

### Post by xpod on 2007-07-30
> Like you, I won't read the rest of the post and say "No, you are not". Compiling something from source and tweaking the code to get something to work the way I want it is OK with me. I just won't call it convenient and what I've imagined my daily workflow with an OS.

You may well  have some obscure app you might need to compile from source but i reckon even a default installation of Ubuntu would more than suit you moms needs...possibly a printer driver and some codecs mabey??

Over a year now and the only thing i`ve ever *had* to compile were the drivers for my kids eyetoy.......I actually would`nt know a bit of code if it jumped up and bit me on the *** if truth be told.

Anyway,if Ubuntu came pre-installed just as Windows did then i`m 100% positive any new computer users would have a much easier time in the long run..........not so sure about all the pre-installed experts out there though.

Their having a helluva time it seems..
Oh well,good luck either way:-?

---

### Post by aysiu on 2007-07-30
I've never had to compile an application from source... ever.

---

### Post by d13k on 2007-07-30
I read only first two pages but i think what you actually want that there are two Ubuntus one for experienced users and one for that damn average Joe.I just started using Ubuntu or should i say installing i have my problems but i am trying to overcome them and you could say I am that average Joe .

---

### Post by kelvin spratt on 2007-07-30
Ubuntu is simple to use if a 57yr old Dyslexic can use it anybody can, its not windows it does things in a different way once you stop thinking windows, Linux makes sence i broke Linux about ten times in the first 2 weeks but each time i asked myself what did i do wrong i won't do that again, now 8 months on when i go on a windows box it like going backward its so slow to use

---

### Post by Lord Illidan on 2007-07-30
> **aysiu said:**
> I've never had to compile an application from source... ever.

I suggest you try Linux from Scratch, Slackware or Gentoo...

---

### Post by vexorian on 2007-07-30
> 1) Kubuntu doesn't offer the same functionality only in KDE like Ubuntu does. And I mean core functionality like USB HDD support

Spoken like a true unknowing person, KDE is not a kernel for god's ake,

> 2) An average user WILL be scared by "restricted" stuff no matter what. "Restricted" means dangerous. And dangerous means bad.
Restricted drivers and codecs ARE bad, so this would be something "intuitive"

> 3) There is no centralized place to set up a system to your liking. In Mac OS there's System Preferences, in Win there's Control Panel, in Ubuntu there are dozen of little apps scattered through whole menu structure. NOT intuitive, NOT easy to use, NOT good.

Centralization being good is the kind of nonsense only a blind apple/MS fan would believe, it is terrible, there shouldn't be only one way to do anything, that's totally against evolution.

> 4) You absolutely canNOT set your system up without using the console.
I did, 4) is  void.

>  And console is what an average user is afraid of.
The average user can throw himselv from a bridge, I don't care, the console makes my development very efficient.

> 5) The system itself is tuned up for terminals of the 80s. If I am using a modern graphical card and LCD display I will have to cope up with extreme ugliness. Heck, even Win2k looked better than modern GNOME and KDE environments. 
That's a lie, so 5) is void.

> 
Remember what made Vista and Mac OS successful ?

Vista: Free licenses gave away count as installs.
Mac OS: It is not succesful.

> 
 Beautiful GUI, not scary word like "secure".
Silly since MS uses the word secure in the same sentence as Vista once for every 2 things they say about it.


> 
6) While I already told it I think it deserves it's own number - use of console. It is completely NOT acceptable to the average user. If at least ONCE Joe Smith must use the console to get some basic (and basic involve installing drivers and configuring the system) thing = BAD, very BAD.

I did not need the console for any basic stuff. LIE=LIE.


> 7) Some settings are sometimes illogically placed, hard to find and navigate to.


familiar is not friendly.


> 8 ) Scary way to install apps. While it really beats anything on Win (because Win doesn't have anything like that) for an experienced user, an average Joe will be shocked when he sees Synaptics screen. "Add\Remove" is a definite step forward but still it is not enough. For example I would personally like to see some codec packs (like CCCP or K-Lite or Vista Codec Pack on Win) being installable from there. Basically a metapackage but what an easy and simple way to add all needed codecs to enjoy the music and video.


That's a feature, I don't want apps to be easy to install, I want to be able to install the apps I want, and have control over it, that means that if I click on a web popup NO "APP" IS GONNA BE INSTALLED! That means that if I plug an USB disk to my computer NO "APP" IS GONNA BE INSTALLED! That also means that if I click on an attachment NO "APP" IS GONNA BE INSTALLED!

Also, synaptic makes finding software much easier than finding software in windows, what if you want a hex editor for windows? How exactly can you find one that is free (And not shareware), one without adware or malware, etc? In synaptic I just go to search and type hex editor, and voila! I find it!

There's also add/remove which makes things even easier. So 8 ) is void.

> 9) OS structure is scary. While personally I don't care about all /etc/ /var/ and the rest it can scare the living poo out of an average Joe while he's just trying to find his D: drive (especially if he never bothered to give any labels to his partitions because hdc1 is NOT intuitive (not that I can thing of a better way to represent an unnamed partition)). I suggest to do what Mac OS does - hide all scary folders. I understand it's not possible to put them all in one neat and tidy System folder but at least hide them. Live only the ones user will use on daily basis (like home folder and media folder), the rest are just confusing.


That hit the BS limit, familiar is not friendly! And Gnome just places the disks in the desktop, it can't be easier, there is no /hdc1 for average user.

---
Underestimating the intelligence of the user is what make vista and Mac OS/X the lame things they are now. "The user can't play music without avoiding piracy himself, he is not smart enough, let's add DRM!"

---

### Post by homeboy on 2007-07-30
Just a little side note from an ordinary , everyday computer user.
 I started using Ubuntu a couple of years ago in a spirit of curiousity. I have come to respect the improvements that have been made to the operating system in that time frame.
   Although I will have to agree with some of the points made here. Especially where video drivers are concerned. Hopefully this latest release will further simplify the process of getting a video card to work properly.
    Alas, it is true that simplicity would make the linux systems more appealing to the general public. 
  Homeboy:

---

### Post by tashmooclam on 2007-07-30
I have to defend Mac.
Windows was copied from the first Mac in 83 or so. The graphical interface and having "windows" is completely a  Mac idea. I used XP and it's a funny copy of Mac OS9.
Imitation is the sincerest form of flattery. When Apple came out with  OS10, they used a roman numeral X.
So, Microsoft comes out with "XP". And, what does that stand for?
The only Windows idea that has been adopted in Mac and Linux is the top right "minimize/maximize/close" buttons. 
Mac is extremely successful, just as Porsche is. You want their nice Unix-based OS? You must buy their equipment. 
Having said this, I like Linux, I just wish everything were not so blurry and fuzzy.

---

### Post by seshomaru samma on 2007-07-30
> **Slavedriver said:**
> The talk about "average Joe" started because of "year of desktop Linux" and such. If Linux aims to become a major competition to Mac or Win it must aim at the average Joe.

.

I think the salshdont/digg crew are not average joes. they are more people like yourself. in a slashdot context ubuntu is very friendly.
in a grandma context - ubuntu is not. 
this is not because windows in essentially friendlier , its because windows is the standard

as a linux user , i would hope that more people like you would use linux , if more computer experts will use linux ,then it might reach a crtical mass where more drivers and software will be written for it and then perhaps it might be as popular as mac.

but - thank you for your detailed comments
your point of view is welcomed 
(by me at least...)
):P

---

### Post by Geekkit on 2007-07-31
> **tashmooclam said:**
> I have to defend Mac.
Windows was copied from the first Mac

And Apple copied (stole) from PARC. So what's your point?

---

### Post by wolfen69 on 2007-07-31
people are into whatever they are. nice to meet you people.

---

### Post by pofigster on 2007-07-31
It seems like half the posts missed the original posts point.  He didn't say that HE was having a hard time installing or using Ubuntu, he was commenting about the user interface for the average bloke.

And I have to agree, Linux isn't for the faint of heart.  But, that's why they don't use it, right?

---

### Post by wolfen69 on 2007-07-31
linux is very ez for me. i thank god that i finally got over windows. my only regret is not learning linux sooner.

---

### Post by aysiu on 2007-07-31
> **pofigster said:**
> It seems like half the posts missed the original posts point.  He didn't say that HE was having a hard time installing or using Ubuntu, he was commenting about the user interface for the average bloke.

And I have to agree, Linux isn't for the faint of heart.  But, that's why they don't use it, right?
"Average blokes" do not install operating systems.

---

### Post by Lord Illidan on 2007-07-31
> **aysiu said:**
> "Average blokes" do not install operating systems.

Stop the stereotype already. Most of my friends are "average blokes", yet they can install Windows XP very well, yet fall to pieces when trying to install Linux, simply because it is different. It's very easy to install Windows, simply because it is the same each round. You get used to it, you can do it in your sleep. In Linux, nearly every distro has a different installer.

---

### Post by ayenack on 2007-07-31
You know what, I have had problems with every single OS I've ever installed at some point or other.

I've used MS OS's from DOS onwards installing purely MS networks and on the odd occasion purely Unix networks and my own network GNU Linux and MS, there's one thing that can be said about all of them, they all break and when they do it's in most cases a killer to fix them.

The one thing that I would say about GNU Linux is you can easily get into the innards of the system to fix it and once there you can do what you want with it to make it work.

I would also say that without a shadow of a doubt WIN XP/Home/Pro/Server/95/8/ME are in my experience far more susceptible to falling over for no apparent reason than all the other OS's and when you have no idea why something has stopped working it's bloody hard to work out what's going on and how to get it up again.

As for single user desktops if you were to take a theoretical view and are willing to accept that the user has no experience off any OS I would say that they could be as proficient in using GNU Linux as Win XP in about the same time with the same amount of effort. 

When you consider that most of the hardware manufacturers don't write drivers for anything other than MS OS's I consider this to be a blinding success for GNU Linux.

Well that's what I think. If you want to use MS OS's then do so. If you want to put a little time and effort into using K/Ubuntu you will be rewarded with a stable, secure and relatively easy to maintain and upgrade OS.

ayenack.

---

### Post by bowens44 on 2007-07-31
I don't think you give the 'average user' nearly enough credit. I don't think that most users who are willing to attempt to move from windows to Linux are intimidated by the word 'restricted' or by the CLI.

Yes, there's a learning curve. I think that most people realize this will be the case when migrating from one operating system to another , no matter what operating systems are involved. 

That being said, if Linux isn't for you, that's fine. Use the OS that you best suits you.

Good luck, have fun.

---

### Post by M$LOL on 2007-07-31
We're talking about the average user, not the average OS-savvy user. The average user knows barely enough to copy music and photos from one disk to another, they're never going to be installing an OS.

---

### Post by kirios on 2007-07-31
bowens44 said
> I don't think you give the 'average user' nearly enough credit. I don't think that most users who are willing to attempt to move from windows to Linux are intimidated by the word 'restricted' or by the CLI.
[COLOR="DarkRed"]The 'average user' is a person who buys a Dell machine preloaded with Windows and probably isn't even aware that Linux exists. 

Users who switch to Linux need to work a bit harder than the 'average user'. As M$LOL says[/COLOR]
> The average user knows barely enough to copy music and photos from one disk to another, they're never going to be installing an OS.

Lord Illidan said
> Most of my friends are "average blokes", yet they can install Windows XP very well, yet fall to pieces when trying to install Linux, simply because it is different. 
[COLOR="DarkRed"]Many Windows users tend to reinstall the OS annually. Could it be that practice makes perfect?! 

'Average' users never reinstall Windows .... they just ask a friend or co-worker instead! :-)[/COLOR]

---

### Post by ayenack on 2007-07-31
Don't forget also you can only install XP/Vista so many times before it rejects the Product Key.

---

### Post by AnRa on 2007-07-31
> **tashmooclam said:**
> The original post has a lot of validity. There are several reasons for this. 
The average professional or educated person is NOT a computer professional. 
The purpose of this forum, according to Ubuntu, is to serve as a help tool for anyone. This the intent of the forum, not to exclude "dopes" who happen to have other things to learn about in life than why software critical for funcionality of their computer is missing. "Open source"?? This is jargon to 90% of the people. 
I personally like my Ubuntu now, but it's been a struggle. I still find the font rendering very unatractive. I know there are fixes, but I can't do it myself yet. 
A complete Linux virgin will browse magazine racks and see "Ubuntu is #1!" They will also see that Dell sells computers with Ubuntu on them. They will see this forum touted as the perfect way to learn about using Ubuntu. 
But, I am very pleased now and await future events. I also know that the various "flavors" of Linux will be improvements, like maybe Linux Mint, or Sabayon. 
If the guys who really know about Linux and Ubuntu made the slightest effort at it, they have money making opportunities galore.
I would have paid for a little pamphlet about getting started, how to use the Add/Remove, Synaptic manager, file management, etc. I would have sent a paypal for a pdf about it.
I would have paid for a CD-Rom with some mpeg videos about how to use this.
I would have paid a few bux for Ubuntu to come with everything you need already on it.
I would have paid a few bux for a version of Ubuntu with decent font rendering so I don't get double vision using Openoffice Writer. I'm tearing my hair out trying to figure out how to make my crazy trackpad behave, there's no menu for it!
I would have paid the cost of one of those overpriced books about Ubuntu, total about $30. 
Maybe someday I'll figure it out and get my friends to use Linux and they'll pay me a few bux to "customize" Linux and everyone will be happy. 
Linux and Mac are the future, but to be honest, it can be a real pain in the butt to move from Windows to Linux, and that's not the way it should be. 
I recommend the first poster give it a try with Linux Mint and see how it goes. 
Viva Linux!
You may try "Sistem -> Help and Support" or [https://help.ubuntu.com/](https://help.ubuntu.com/) ;)

---

### Post by wolfen69 on 2007-07-31
> Stop the stereotype already. Most of my friends are "average blokes", yet they can install Windows XP very well, yet fall to pieces when trying to install Linux, simply because it is different. It's very easy to install Windows, simply because it is the same each round. You get used to it, you can do it in your sleep. In Linux, nearly every distro has a different installer.

this is where you are wrong. if they install their own OS's, then they are not average blokes. they may be average people, but in the computer world they are a step above most people.  and no, it is not ez for most people to install anything. get over yourself.

---

### Post by yknivag on 2007-07-31
> **xpod said:**
> I AM pop here in my little world slavedriver and Prior to discovering Ubuntu last July i`d used a computer for all of 4 months.
Windows of course.One year on me and  my kids all use Ubuntu like it was second nature......I *know* how little i know about computers compared to some of the whizkids,geeks & gamers on this place but boy have i heard my fill of so called experts complaining about how complicated & difficult it is.

To be honest, the fact that you'd only been using Windows for 4 months was your biggest advantage.

99% of all the problems I hear in feedback can be summed up as "it doesn't do it like Windows does". Or words to that effect.

Learning Linux isn't difficult.  Un-learning Windows (if you've been using it for a long time) is very difficult.

My Grandad is 80. He uses Windows. For simple things that I would do with a mouse click in Windows, he uses the terminal. Why? Because he spent years working in DOS. Now no-one would say that file management in the Windows GUI was difficult, neither would he. Using the command line is just a habit for him. Just like Windows is a habit for many "average Joes".

Take installing programs as an example. On Windows, you download a zip file, extract it, run the setup file, click a million next boxes configuiring things like file path and click to accept the licence, wait until it's finished and reboot. On Ubuntu, you go to "Add/Remove programs", chose what you want and click OK. You don't even have to reboot. Which is easier? The former for someone who does it every day. From an objective perspective probably the latter.

Yes Linux is different to use but that doesn't automically make it harder for the "average Joe". Some of it is much easier.  There are problems with hardware, anyone will admit that, it's got an awful lot better in the 4 or 5 years I've been using Linux and continues to get better. Given another year or so who knows?

---

### Post by aysiu on 2007-07-31
Familiarity trumps empirical "intuitiveness" any day. The principle applies to cooking, language acquisition, computers, driving, just about anything in life that requires repetition.

---

### Post by yknivag on 2007-07-31
> **Slavedriver said:**
> > I don't think that hiding some folders will actually change the filesystem. Of course if it won't involve renaming them or such.

...and all cars have a common set of controls in common places following some standard... Haven't seen a lot of successful cars with the steering wheel on the back seat (not drawing any parallels here).

No, but if you go from driving a car with an automatic gear box to a manual one you need to learn what the clutch pedal does.

In Linux, the clutch pedal is called the terminal. Just as manually changing gear in a car gives you more control of your driving experience, so Linux gives you more control of your computing experience.  You just need to lean how to change gear.

---

### Post by windtalker on 2007-08-01
Hello all! Average Joe here.
  My very first PC had the word TANDY written across the top of the monitor. Since then I've gone through windows 95, 98, XP, XP Pro and Vista. Quite frankly I'm a bit disgusted with having to constantly buy and install programs that keep my operating system secure and am equally disgusted with having to live with a vendor telling me what I can and cannot do with a progam I purchased, this last time to the tune of $400.00. Vista.
 A few months ago I had the pleasure of watching my brand spanking new Vista OS pretty much dissolve before my eyes due to a virus. I had a what I thought was up to snuff firewall running, an up to snuff anti-virus running, anti-spyware running and oodles and gobs off cleaners installed.  I had so much stuff installed  for security that at times I thought the fan for my processor was going to suck my tower off my desktop it was running so hard.Yet POOF! It's all gone in a few days. 
 After the crap of installing it the first time no way was it going back in my box.
  I decided to make my leap to Linux. Scared? Not in the least. I can format a hard drive and will do so in a heartbeat. I'm an experienced windows user remember? If I don't like it it's gone. Afraid to learn something new? Why would I be? I'm an experienced windows user. If one is afraid to learn then one should stay the heck away from all OS's to include windows. Besides, learning is half the fun.
 As far as compatability goes with Ubuntu, in the last few months I've gone through about a dozen Linux based OS's and Ubuntu fills my needs just fine. I'm running Dapper Drake and beleive it or not, I tried out two other Linux OS's today alone. BTW, Ubuntu will not reformat the hard drive when Vectorlinux is installed on it, but PC-BSD will. Todays personal experience. 
 I'm not a programmer yet so I can't speak from that stand point. But there's a brand new book laying here on my desk and the title is, "Learn to program using Python." And golly, I found an IDE in my synaptic. Wow! What will Ubuntu come up with next. 
 I'm not to big on games either, but I found an imtation of my favorite, Doom. And I can't play my new favorite to long, gl-117. My nvidia graphics have me near to falling out of my chair because they're to realisic.  Imagine that! Drivers for an Nvidia Gforce video card. Complete with 3-D even. Thank you Ubuntu. 
 If an experienced programmer doesn't like his/her Linux system, I would think that the programmer is at fault here, not the developers of the system. 
 As I stated above, I'm not a programmer, yet I've adapted my system to suit my needs by doing nothing more than reading and a bit of trial and error as not all the instructions given in the forum fitted my particular set-up. And I would think it would be asking a bit much to expect any developer handing out a free system to take the time to compile instructions on every conceiveable set up out there.
 On a few of the other OS's I tried out i spent days just trying to figure out how to get a JRE in Firefox so I can check my bank account. With Ubuntu it was less than a half hour figuring it out.
 Anyway, just thought an average Joe should speak up. Oh yeah, I used the terminal pretty regular on some of the installs and cleaning up. It wasn't all that hard, I just had to read.

---

### Post by Lord Illidan on 2007-08-01
> **kirios said:**
> 
[COLOR=DarkRed]Many Windows users tend to reinstall the OS annually. Could it be that practice makes perfect?! 

'Average' users never reinstall Windows .... they just ask a friend or co-worker instead! :-)[/COLOR]

Well, I coached my friend through it once, and he caught on quickly :D

---

### Post by Lord Illidan on 2007-08-01
> **ayenack said:**
> Don't forget also you can only install XP/Vista so many times before it rejects the Product Key.

Crack...need I say more.

---

### Post by nick.inspiron6400 on 2007-08-01
Linux didn't fail you...You failed Linux.

People go back to Windows as it's a easy choice.

---

### Post by darksong on 2007-08-01
> **M$LOL said:**
> I'm going to reply in a negative way, because that list is a just opinionated moaning, not really something I'm going to respond in a nice manner to.

Get it into your head that Linux isn't designed to be a "just click and go" affair for n00bs, if you want that then go and buy Vista. Ubuntu is a million times more user friendly and intuitive than, say, BSD, so just because you expect everything to be sitting on a plate for you and you don't want to learn a new system doesn't meant that the OS is at fault.

If you want to troll - and that's exactly what you're doing - about how scary a message box saying "Restricted" is, then go to somewhere with other trolls, don't come to the Ubuntu forums. We'll help you with your problems if you're polite about it, and we'll encourage you to learn about the OS if you're open minded, but if you come along on a big rant about how crap you think Ubuntu is, you're not exactly going to get a great response.

Have you tried PCBSD? to say BSD is un-user friendly is an unfair assupmtion, PBI is a far superior format bieng self contained, making a safer and more secure system. Did i mention it is 1 click install?

---

### Post by ayenack on 2007-08-01
You know I've just read windtalkers post and he makes a very interesting point about using Windows. It's not an easy system to use. When I think back to the people I've had to help who have just set up their brand new PC with WINXP/98/95 and been at a complete loss as to what to do.... well it amounts to every single one of them. 

I can think of a couple of examples for instance a friend who had never used a PC and deleted every single icon on his desktop called me in a panic after doing so,  my brother who after buying a laptop about a year ago could not even connect to the internet without help and there are SOOOoooo many others. 

Windows does not come with a user manual to speak of and support cost money if you don't know someone who's a bit PC savvy. There are some very basic things that are essential to learn in GNU Linux (basic use of the terminal being the most important in my view) you don't need to be a sys admin to learn them just an average user with the ability to read and you're away.

---

### Post by aysiu on 2007-08-01
> **ayenack said:**
> 
I can think of a couple of examples for instance a friend who had never used a PC and deleted every single icon on his desktop called me in a panic after doing so I had a situation like this come up in work a few weeks ago. I was talking to a co-worker, and I noticed that she had a bunch of desktop icons on one side and some others on the other side. I asked her why she separated them. She replied, "Well, the ones on the left are the ones I don't use, and the ones on the right are the ones I *do* use." I asked why she didn't just delete the ones on the left. She was a little taken aback, "What if I need those programs later?" I had to explain to her that the desktop icons were just shortcuts to the program launchers and that deleting the icons wouldn't uninstall the programs.

She is the kind of person of which I speak when I use the phrase *average user*. I am not talking about these "average blokes" who install and configure operating systems themselves.

---

### Post by buntunub on 2007-08-01
You know there is a fairly common stigma attached to Ubuntu throughout the Linux world. Its that Ubuntu is the distro of choice for nubs. This post just proved the point! Man I love posts like this :)

Waawaaa Linux requires people to THINK! OMG Linux will never be good enough for the "average user"!.. Whatever, "average" is. If anyone knows what an "average user" is, please do tell! I was an "average user" about 8 months ago and then took the plunge into Linux. A week after I started, I deleted any trace of anything M$ from all of my computers at home! Yep, ive been using linux a grand total of 8 months, and thats after having been a loyal yet mindless M$ user for about 20 years continuously!.. No experience of any kind with Linux or any OS that required the CLI or any thought, and I fit right into Linux like a kid in a candy store.

So my arguement follows that if an idiot like me can handle Linux, then so can anyone! I seriously have alot of fun with it and have FUN learning. Heck, I want to learn more!! Gimme gimme gimme that linux knowledge lol.

What proves beyond any doubt that this guy is a moron is that he tries to make excuses for people he doesnt even know, and insists that Linux; and in particular Ubuntu!.. is unsuitable for nubs. Well, if thats the case then I better just quit now! Because I am the king of all nubs! Which makes me the master of this moron heheh.

---

### Post by aysiu on 2007-08-01
> **buntunub said:**
> If anyone knows what an "average user" is, please do tell! I just did. And I can assure you she would not be able to install Windows or any desktop Linux distro. Most average users I know don't have any idea how to set the BIOS to boot from CD-ROM.

---

### Post by Druke on 2007-08-01
> **aysiu said:**
> I just did. And I can assure you she would not be able to install Windows or any desktop Linux distro. Most average users I know don't have any idea how to set the BIOS to boot from CD-ROM.

good thing dell is taking care of that now, perfect for the average user eh?

:popcorn:  to dell even though i prolly wont buy a pc from them

---

### Post by tashmooclam on 2007-08-01
This whole discussion is just history repeating itself. In the 70's, people said "You have a computer?!" Today they say "You run Linux?!" I knew just a couple of people who got the Apple II.
Then the IBM PC came out in the workplace, and they were just Lotus 123 spreadsheet machines, no GUI, really no fun. You wouldn't dream of buying one for yourself. ($5,000!) 
The Mac began to make PCs really attractive to more people than before. A consumer computer.
So, today the cycle is repeating. More and more people will know about Linux. People I speak to about it will realize "He's no computer person, maybe it is good desktop OS if he can use it and he likes it. I can try a Live CD too." 
I already have a several people intrigued about Ubuntu and Linux. 

I can remember when I told our boss at the research department that with the new macs, we could more easily write our documents and our spreadsheets, using the friendly desktop and mouse. We had IBMs and DOS.
His response: "I'll buy them, but you must take the responsibility if they don't work out for us!" 
So, the guy was basically saying "I don't like Mac because it's not DOS" (!!??) 
My own Ubuntu problems boil down to being caused almost entirely by being CHEAP and resisting buying the book.

I wish more and more people used Linux so that the guys doing the software may make some money and have the rewards for their labor. I am actually amazed how well this stuff works for being free. 
Viva Linux

---

### Post by wak_wak on 2007-08-03
While I'm not a Windows hater, I certainly prefer Linux.

Windows ABSOLUTELY has it's advantages.  For instance, if my very-old grandmother tried to use Linux, she too would whine.  So, take comfort.  You're not alone.

OK.  I won't make fun of you.

I guess what I'm trying to say is, what's your point?  Are you trying to be negative or are you trying to put something out there that may be of use.

If it's the latter, read over what you wrote before you post it.

It's something like me walking up to you and saying "I'm not trying to be negative but your mom's a fat prostitute and I think she trades **** for crack," and then saying "But I don't mean it negatively.

I'm NOT a Linux expert.  I'm not a Windows expert.  But I believed there was enough use in spending time learning Linux so I could use it and nothing else.  And I have.  I can even have a decent conversation about it with an expert.

But you're obviously not doing that.  

My point is that everyone here is either trying to learn it, or trying to help others.

So quit being negative.  Keep your pointless babble to yourself and try to be constructive.

---

### Post by wolfen69 on 2007-08-03
> **wak_wak said:**
> While I'm not a Windows hater, I certainly prefer Linux.

Windows ABSOLUTELY has it's advantages. ** For instance, if my very-old grandmother tried to use Linux, she too would whine.**  So, take comfort.  You're not alone.

OK.  I won't make fun of you.

I guess what I'm trying to say is, what's your point?  Are you trying to be negative or are you trying to put something out there that may be of use.

If it's the latter, read over what you wrote before you post it.

It's something like me walking up to you and saying "I'm not trying to be negative but your mom's a fat prostitute and I think she trades **** for crack," and then saying "But I don't mean it negatively.

I'm NOT a Linux expert.  I'm not a Windows expert.  But I believed there was enough use in spending time learning Linux so I could use it and nothing else.  And I have.  I can even have a decent conversation about it with an expert.

But you're obviously not doing that.  

My point is that everyone here is either trying to learn it, or trying to help others.

So quit being negative.  Keep your pointless babble to yourself and try to be constructive.

first of all, if your grandmother is whining about using linux vs. windows, i want to meet her. she sounds pretty cool. secondly, i would bet that any pc that i setup for your grandmother will be 10 times less hassle than any windows box you can give her. it's amazing how many instructions i have to give my windows clients. but in linux, it's understood.

---

### Post by wak_wak on 2007-08-03
I can't actually disagree with you on that.  You're right.

My point was that I happen to love Linux and I have nothing against Windows.  I feel that spending time coming in here and knocking Linux is just a negativity which is a waste of time.  Let's just work on being positive and helping those who help us.

I use it and nothing else (except a dual-boot for Counterstrike).  And I happen to be very grateful for that.

---

### Post by kirios on 2007-08-04
> **buntunub said:**
> OMG Linux will never be good enough for the "average user"!.. Whatever, "average" is. If anyone knows what an "average user" is, please do tell! I was an "average user" about 8 months ago and then took the plunge into Linux. A week after I started, I deleted any trace of anything M$ from all of my computers at home! Yep, ive been using linux a grand total of 8 months, and thats after having been a loyal yet mindless M$ user for about 20 years continuously!.. No experience of any kind with Linux or any OS that required the CLI or any thought, and I fit right into Linux like a kid in a candy store.

[COLOR="DarkRed"]If it took you just a week to switch completely to Linux, you're not an 'average user' :-) 

The issue is not whether Linux is 'good enough' but whether the 'average user' would actually take the trouble to learn about installing and running an unfamiliar OS. 

The bottom line is that 'average users' will only start using Linux when it comes pre-installed on more PCs.

One of the early posts in this thread sums it up quite neatly.[/COLOR]
[http://ubuntuforums.org/showpost.php?p=3099724&postcount=3]("http://ubuntuforums.org/showpost.php?p=3099724&postcount=3")

---

### Post by krazyenglishman on 2007-08-08
I personally never had many of the problems this user did when i switched over to Linux, In fact Linux played MORE of my media then windows did out of the box, I never really found the " You need this codec " Messages " Scary " at all, There just telling you there not 100% Supported by them, 99% of the things i installed on Windows isn't supported either,  Example i noticed you said you wanted your nvidia driver experience to be easier, But never mentioned that windows produces a * Hey nvidia never paid for the license so were going to call there drivers unsupported now * message as well.  Ok maybe i slightly twisted the words on that one *lol*

My point is, If something doesn't work in Linux, Fix it! There are plenty of people out there willing to help. Don't Whine.

P.S . I have Linux & WinXP ( Not going to Vista ), So i'm certainly not a "Linux Rules, XP Sucks" kinda person.

---

### Post by nakul on 2007-08-08
well every body has right to his opinion ge dosi make some good and some bad point
1***) Kubuntu doesn't offer the same functionality only in KDE like Ubuntu does. And I mean core functionality like USB HDD support***
 well true because ubuntu is more gnome oriented distribution there have been more problems  reported in upgrading  kbuntu then ubuntu maybe things have changed

***2) An average user WILL be scared by "restricted" stuff no matter what. "Restricted" means dangerous. And dangerous means bad***
 no not scared if so then whole torrent phenomenon would  have died( riaa):)
but more  aware

***3) There is no centralized place to set up a system to your liking. In Mac OS there's System Preferences, in Win there's Control Panel, in Ubuntu there are dozen of little apps scattered through whole menu structure. NOT intuitive, NOT easy to use, NOT good.***
well it maybe due to linux  development different people trying to make small parts and it adds up to make whole linux phenomenon making it modular hence easily to debug and stable but there is control panel in ubuntu though not enabled by default you have to edit menus and also there is process of merging    of different apps in gnome e.g. in 2.20 themes and background  and font have been merged into one item

***4) You absolutely canNOT set your system up without using the console. And console is what an average user is afraid of. Installed drivers ? Cool. But desktop resolution is still 1024x768. Now here comes two options: one of the involve editing xorg.con manually and another launching nvidia-settings with sudo. Obviously both ways are NOT acceptable to an average user.***
 well you hit  right on mark with it well console is bad this is gernal thinking 
about which i agreed coming from dos to windows but after linux i began to appreciate it firstly because of these scripts that can automate any task you  with it well with vista microsoft also wanted to integrate a console  but as you know window was development disaster  and like many feature this was axed  
 but it has now again availiable in win server 2008 one thing laking in linux is automator like app os x which is more like graphical fronend to make script
           ubuntu and wide screen the debate because of this single thing a hack said ubuntu is not suitable for laptop (some reporter) well this will be solved next version of ubuntu {x.org had problems not ubuntu} well no os meant for pc works right out of the box because so many combination of hardware except os x which only has to support limted number of hardware even then latest version of os x10.5 dose not support g3 based machines not becuse they are not powerful enough but hey simply choose not to imagining in pc terms it will mean all the pc before the year 2000 have no upgrade path ( there have  been hacks that alow 10.4 to be installed on g3 based)
           on windows side things are not rosy either atleast ubuntu alows to edit xconfig try using hi end audio card in vista xifi you will not be able to enjoy any 
of the its function for which shed a load  of cash most of the priters do not work in vista and as for hardware support vista is in worse condition then ubuntu (only for the people upgrading thier machine)
           thing i want to say is that xp is not perfect out of the box steps that i took with my xp machine 


well i am tired of writing:mad:

---

### Post by Psychobiker on 2007-08-11
I ported over from Windows about a month ago. Ubuntu wouldn't format my HDD, not recognising file system etc. So I worked around that one. 
Drivers? Thankfully went okay, even my obscure IDE/SATA USB interface made by Goodway (nope...never heard of it either :D) just mounted my 300G sata no problem.
Synaptic is the saviour of all, and I'm slowly getting into CLI, the power in there is nice


L

---

### Post by Old *ix Geek on 2007-08-11
Your experience couldn't be more diametrically opposite mine if it tried!  You can read about my [[color=blue]**_latest installation_**[/color]](http://ubuntuforums.org/showthread.php?t=523088) if you're interested.  The very short version of it is that I bought a new computer yesterday, got home with it late in the evening, started working on it around 1:00am (including the physical stuff, such as installing a wireless card, putting the computer together, putting the monitor together, etc.).  By 3:30am I had a fully working, fully customized system with additional programs I installed and data from other computers copied over.  (By the way, I use KDE and think it's beautiful.)  NVidia? No problem. USB peripherals? No problem. Wireless? No problem.  Flat panel monitor? No problem.  (If you read my thread about the installation, you'll see that vista REQUIRED--as in couldn't proceed without--the CDs for both the wireless card I had installed and the flat panel monitor.)  And on and on...

As for your contention that "You absolutely canNOT set your system up without using the console," what can I say?  I was REALLY tired when I was setting up this computer last night (the one I'm typing on right now), so I'm not going to swear to this, but I don't recall having to do ANYTHING at a command line.
> There is no centralized place to set up a system to your liking. In Mac OS there's System Preferences, in Win there's Control Panel, in Ubuntu there are dozen of little apps scattered through whole menu structure. NOT intuitive, NOT easy to use, NOT good.Really?  Then the "KDE Control Center" I see when I choose [on the main menu] "Settings | Control Center" must be a figment of my imagination. :confused:
> Scary way to install apps. While it really beats anything on Win (because Win doesn't have anything like that) for an experienced user, an average Joe will be shocked when he sees Synaptics screenHuh?  Scary?  You're kidding, right?  What's SCARY about looking at a huge list of available programs, choosing the ones you want, and then clicking 'apply"?  You've totally lost me here.

---

### Post by Nevon on 2007-08-12
> **Slavedriver said:**
> 3) There is no centralized place to set up a system to your liking. In Mac OS there's System Preferences, in Win there's Control Panel, in Ubuntu there are dozen of little apps scattered through whole menu structure. NOT intuitive, NOT easy to use, NOT good.
I don't know if anyone has said this already, but there is actually such a thing. It's called the 'Control Center', and is available in the 'Preferences' menu. Although you might have to enable it by going to your preferences menu -> Main Menu and then add it to the preferences tab.

EDIT: lol, the last three posts all mentioned it xD My bad.

---

### Post by vexorian on 2007-08-13
why does this keeps getting replies? it is 2 weeks old let it go...

---

### Post by danketchpel on 2007-08-13
> **M$LOL said:**
> Get it into your head that Linux isn't designed to be a "just click and go" affair for n00bs,........

I have to ask the question, why not make it "click and go" ??? Why does having to resort to the console seem so appealing to so many? There will always be some "techy niche" (maybe it's really just OLD SCHOOL)  system for those who love to type.

I for one would love for some flavor of Linux to become as straight forward to use as some other operating systems. Especially when it comes to installing new apps and drivers for hardware. I admit that Ubuntu has come a long way from the first few flavors of Linux I tried, that's a really good thing.


On a seperate note, I can't say Linux has "failed" me, more that the very few of the applications I really need won't run on it. I'm going to try out the latest version of wine to see how that's progressed.

When I asked many of the CAD/CAM vendors if they'd offer a Linux release all of them told me, "setting up the required tech support staffing is the road block, porting the software is easy".

Things I really need to run are;

1. business accounting software (preferably Quickbooks Pro)
2. Solidworks and MasterCAM
3. Garmin GPS software
4. PLC programming software
5. preferably iTunes

Music and movies I can do without.

---

### Post by dark_harmonics on 2007-08-13
Let me start by saying that i just recently switched to Ubuntu from being a die-hard windows fan. What finally convinced me was compiz-fusion. OMG this **** is AWESOME! I showed it to a few of my family (yes we are all techies :P ) and they were all scrambling to get it configured and catch up to my cool desktop.

Now having said all that, I agree partially with the first poster. Ubuntu might not have been meant to be an OS for dummies but its DAMN well close to it! It just seems like a few more intuitive tweaks here and there (maybe I can pitch in when I learn enough about how it works) and it could completely remove the need for dropping to the console during every config. Deb packaging is already kinda does this for the user and i think thats cool but it would be nice if others began packaging their apps similarly. 

Essentially the only thing windows has over Ubuntu is the ease of use because of the console. Every edition of Ubuntu moves further and further forward ( i had some of the really old copies a few years back). 

I am ecstatic to be a part of this growing community. I just wish it could come out of the relm of more technical users and into the relm of regular non-technical people. I know that the interface, and support community already blow windows into the next dimension.

How could he talk about VISTA!?!? Microsoft brags about the aero experience and its **** compared to compiz!

---

### Post by dark_harmonics on 2007-08-13
danketchpel ,

Did you actually try plugging in your i-pod? the software that comes up already supports I-Tunes like management of your i-pod. I dont know about your other software needs but that one is pretty easy.

I did read something about using I-Tunes in wine but it looked way to difficult for something i dont even need because Rythmbox takes care of it. :guitar:

---

### Post by inyoka on 2007-08-13
As one of the people who regularly installs ubuntu without using the command line I can assure you it is possible, and that any problems with hardware and codecs are normally caused by the producers of the afformentioned hardware and codecs.

Of course Gnome has got, and has had for a while a central control panel. Simply use the menu editor ('alacarte' from 'alt+f2') to add in Control Panel on the preferences menu.

Your cd-rom drive problem has nothing todo with Ubuntu but cd is ejected because standard bios settings boot from cd then hard-drive, and most sys admins (i.e. me) forget to take the cd out if it isnt done for me. Its strange you want the desktop dumbing down, and yet do not like this dumbing down feature.

Amarok is a great app, but KDE is buggy thats why I use Gnome, unsurprisingly your KDE app is buggy, regardless of with you are running KDE desktop. Try Rhythmbox, at least unsil the next KDE round of updates which look very promising.

Yes codec packs would be nice, but you know why they are not there. Find one of the many codec repos available for ubuntu perhaps medibuntu which has google earth and skype to boot, and just install everything it contains. No you dont have to use the command line, go to Synaptic > settings > repositories >third-party software and add each apt line listed on the web-site.

If you dont like the restricted app message please lobby your gouvernment to ensure codecs are available to all without prejudice. 

If you dont like the command line, bad luck even Windows Server 2008 is re-introducing the command line. To be honest its a lot easier telling someone the open a terminal and copy and paste a script in and press return, than talking them through the gui sometimes.

---

### Post by Alex Fernandez on 2007-08-14
You know whats funny? Most of the things he's mentioned as being "bad", are infact exactly the reasons why I use Linux over Windows.

Console is the best invention since the computer imo, it gives you soooo much control and power over the system, GUI menus for setting things up are a pain, editing config files is sooo much easier.

As for the file system structure, ever looked at Windows? Ever TRIED to find a dll / ini file in WINDOWS dir? Ever tried to find anything in the registry?

---

### Post by angryfirelord on 2007-08-14
> **Alex Fernandez said:**
> You know whats funny? Most of the things he's mentioned as being "bad", are infact exactly the reasons why I use Linux over Windows.

Console is the best invention since the computer imo, it gives you soooo much control and power over the system, GUI menus for setting things up are a pain, editing config files is sooo much easier.

As for the file system structure, ever looked at Windows? Ever TRIED to find a dll / ini file in WINDOWS dir? Ever tried to find anything in the registry?
I never understood why Windows throws all of the critical dll files into the System32 folder. It's a mess!

---

### Post by danketchpel on 2007-08-18
> **dark_harmonics said:**
> danketchpel ,

Did you actually try plugging in your i-pod? the software that comes up already supports I-Tunes like management of your i-pod. 

Good point.

Well I plugged in my iPod and it did bring up Rythembox and recognized my iPod. I'm not sure how to get it to recognize my existing iTunes library but I'll play with it and hopefully I can get it to work also. It does recognize the songs on the iPod, very cool.

Thanks for pointing it out to me. I'm still getting my head around all the new stuff in Ubuntu and I do like what I'm seeing.

I'd be one happy camper if I could completely replace MS Windon't in my daily life. My personal observation is that Vista is going to be a boost to Ubuntu. I personally know a couple people who are loading Ubuntu on their new systems that came with Vista, they hate it so much that they're looking for a new OS. Thanks Microsoft for helping out the Linux cause. ):P

---

### Post by Old *ix Geek on 2007-08-18
> but KDE is buggy thats why I use Gnome, unsurprisingly your KDE app is buggy, regardless of with you are running KDE desktopIt is?!  I hadn't noticed.  I run KDE on all my computers, 24/7, and can't think of any buggy behavior  that was due to KDE itself. In fact, I'm not sure I can think of ANY buggy behavior, just the usual things that need to be tweaked to my liking. :confused:

---

### Post by Dipper on 2007-08-18
> **Slavedriver said:**
> 

Try playing a movie. Alert appears saying codecs are not installed. OK, let's install some codecs then. And here's the part I don't like - the scary "Restricted app" message. While I don't really care about it I know 100% that any average user will be. And that will be an end for the media playback for him if some geek won't come and set it up for him.

Next stop - install Amarok, it being quite good media player. After installing it and building my collection I tried playing some MP3 files knowing what to expect - a pop-up asking to install MP3 codec because it's "restricted'. Boo, scary. Instead Amarok hanged... Restart, select a track, click play, boom, hang again. This time I actually see the pop-up but without any text or buttons. After a few seconds I am told that KNotify crashed.

MP3 and video codecs are things that cannot be incorporated into Ubuntu/Kubuntu out of the box. They are proprietary (and yes, "restricted").  A program called Automatix2 can install all of the goodies which will make these programs run smoothly. There is no way to make this user-friendly since Ubuntu cannot be bundled with Automatix.

Despite the flaming from  other members, the rest of what was posted I am in 100% agreement with:

> **Slavedriver said:**
> 4) You absolutely canNOT set your system up without using the console. And console is what an average user is afraid of. Installed drivers ? Cool. But desktop resolution is still 1024x768. Now here comes two options: one of the involve editing xorg.conf manually and another launching nvidia-settings with sudo. Obviously both ways are NOT acceptable to an average user.

Amen!  Using a console is so pre-Windows, pre-MAC 1980s.  I think it's time to join the 21st century and minimize the role of the console.  I wouldn't say eliminate it, but at least make it an unessential alternative for those who really want to use it.  Average Joe shouldn't have to learn how to type commands any more than you should have to learn morse code to talk on the radio.  In an age of advanced GUI, a console is obsolete.  Perhaps a Ubuntu Old Skool Edition would be a good idea for those who avoid GUI.

> **Slavedriver said:**
> 
6) While I already told it I think it deserves it's own number - use of console. It is completely NOT acceptable to the average user. If at least ONCE Joe Smith must use the console to get some basic (and basic involve installing drivers and configuring the system) thing = BAD, very BAD.

Once again...Amen, brother!

> **Slavedriver said:**
> 7) Some settings are sometimes illogically placed, hard to find and navigate to. 
8) Scary way to install apps. While it really beats anything on Win (because Win doesn't have anything like that) for an experienced user, an average Joe will be shocked when he sees Synaptics screen. "Add\Remove" is a definite step forward but still it is not enough. For example I would personally like to see some codec packs (like CCCP or K-Lite or Vista Codec Pack on Win) being installable from there. Basically a metapackage but what an easy and simple way to add all needed codecs to enjoy the music and video.
9) OS structure is scary. While personally I don't care about all /etc/ /var/ and the rest it can scare the living poo out of an average Joe while he's just trying to find his D: drive (especially if he never bothered to give any labels to his partitions because hdc1 is NOT intuitive (not that I can thing of a better way to represent an unnamed partition)). I suggest to do what Mac OS does - hide all scary folders. I understand it's not possible to put them all in one neat and tidy System folder but at least hide them. Live only the ones user will use on daily basis (like home folder and media folder), the rest are just confusing.

Microsoft's stranglehold on the software industry is unacceptable.  If Linux is to be a viable alternative to Windows, it is going to have to be more user-friendly.  Ubuntu has taken major steps forward with Feisty, and I believe the progammers will continue to do so.  Right now, the Ubuntu series are the best distributions of Linux there are.  But as with everything else, there is always room for improvement.  I see no reason to bash and flame those who point out those areas that need improvement.

---

### Post by Caffeine_Junky on 2007-08-18
[QUOTE=Dipper ........  But as with everything else, there is always room for improvement.  I see no reason to bash and flame those who point out those areas that need improvement.[/QUOTE]

I agree with this statment totaly, as I am sure many others do.   I am sure that there are Open Source software devolopers/coders both profesional and hobbiests that would scout forums such as this one in search of a new project to satisfy there need to create and/or improve software to the bennifit of us all.  I find this very exciting.

---

### Post by angryfirelord on 2007-08-19
[quote="Dipper"]Amen!  Using a console is so pre-Windows, pre-MAC 1980s.  I think it's time to join the 21st century and minimize the role of the console.  I wouldn't say eliminate it, but at least make it an unessential alternative for those who really want to use it.  Average Joe shouldn't have to learn how to type commands any more than you should have to learn morse code to talk on the radio.  In an age of advanced GUI, a console is obsolete.  Perhaps a Ubuntu Old Skool Edition would be a good idea for those who avoid GUI.[/quote]
I disagree. The power of *nix systems comes from the console and it's because of average joe's mentality that he thinks the console is this scary thing. Has he ever used it? Probably not. Ubuntu eases a user into the console and tutorials that require it usually involve copy-pasting commands.

So yes, it is essential.

---

### Post by ukripper on 2007-08-20
Role of console is far more beyond than just to run programs. Command line is heart of linux systems. Try using it you would never get enuff! i know it is 21st century but doesn't make sense why you want to get rid of command line? In 21st century you should start learning to use console probably it will give you more sense of responsibility to control your own system despite getting controlled by it.

---

### Post by gigafish on 2007-08-20
"How linux has failed me" ?

Does a tool fail if I don't use it properly?
Does a wrench fail if it doesn't work as a hammer?

If something is built to do what it does, than how has it failed? 
Can software do more than it is designed to do?

Anyone who says ubuntu linux has failed them, should think about how they've failed ubuntu linux.

---

### Post by aysiu on 2007-08-20
> **gigafish said:**
> "How linux has failed me" ?

Does a tool fail if I don't use it properly?
Does a wrench fail if it doesn't work as a hammer?

If something is built to do what it does, than how has it failed? 
Can software do more than it is designed to do?

Anyone who says ubuntu linux has failed them, should think about how they've failed ubuntu linux.
What you're saying is true only to a certain extent. It is possible for a wrench to fail if it doesn't work like a wrench. And Ubuntu *does* have bugs and shortcomings, even if a lot of its supposed failings are just culture shock.

---

### Post by gigafish on 2007-08-20
Hey, well, now you're using a wrench to split a hair

---

### Post by aysiu on 2007-08-20
> **gigafish said:**
> Hey, well, now you're using a wrench to split a hair
I'm just appreciating that the situation is complex. Linux *can* fail people, and people can fail Linux. It goes both ways.

---

### Post by Old *ix Geek on 2007-08-20
> The power of *nix systems comes from the console and it's because of average joe's mentality that he thinks the console is this scary thing. Has he ever used it? Probably not. Ubuntu eases a user into the console and tutorials that require it usually involve copy-pasting commands.I'm baffled by the myriad of complaints I read about *nix systems' use of the command line.  I can do in **seconds** various functions at the command line that would take **minutes--lots of them**...if not hours--to do via a GUI. 

I don't get why people call the command line archaic, old, last century, etc.  Its power remains, regardless of what century we're in.  There's simply NO comparison between what can be done at a command prompt and a GUI--the command prompt will win every time.  That people moan and groan about it is, in my opinion, an indication that they're REALLY ignorant about why *nix is so much more powerful, versatile, and customizable than windoze will ever be.  Pity, too, because if these complainers would take the time to do a little research, they'd find that they can accomplish everything much quicker and more efficiently using the command line than they'll ever be able to do with a GUI....although GUIs **are** pretty to look at. ;)

---

### Post by aysiu on 2007-08-20
> **Old *ix Geek said:**
> There's simply NO comparison between what can be done at a command prompt and a GUI--the command prompt will win every time. That's not entirely true. It really depends on how often you expect to perform a task. If you are doing a one-time task, the time it takes to do that task in the GUI will probably be shorter than the time it takes to learn how to do that task in CLI. If, however, you are doing a complicated operation once every week for years, it may be worth learning how to do it in the CLI.

I don't think you can make blanket statements about GUI *always* being better or CLI *always* being better (or "winning" every time).

Web browsing with Lynx may be fun for certain things, but I prefer the GUI (Firefox) almost all the time, especially for websites like Flickr.

---

### Post by Old *ix Geek on 2007-08-20
> I don't think you can make blanket statements about GUI always being better or CLI always being better (or "winning" every time).Sometimes I assume that everyone has ESP and will know what's in my head as I'm typing something... Alas, that's not always the case. :rolleyes:  What I **meant** was that in terms of speed and efficiency--yes, once you know how to do it!--the command line is better.  
> Web browsing with Lynx may be fun for certain things, but I prefer the GUI (Firefox) almost all the time, especially for websites like Flickr.I like firing up Lynx...every once in a great while.  Reminds me of the good old days. ;)  But I much prefer SeaMonkey!

---

### Post by Martje_001 on 2007-08-21
> **Slavedriver said:**
> Next stop - install Amarok, it being quite good media player. After installing it and building my collection I tried playing some MP3 files knowing what to expect - a pop-up asking to install MP3 codec because it's "restricted'. Boo, scary. Instead Amarok hanged... Restart, select a track, click play, boom, hang again. This time I actually see the pop-up but without any text or buttons. After a few seconds I am told that KNotify crashed.
What do you expect? You're running a KDE app on GNOME! You had to install xine-ffmpeg btw..

---

