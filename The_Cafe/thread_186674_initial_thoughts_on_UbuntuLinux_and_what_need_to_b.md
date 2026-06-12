---
title: "initial thoughts on Ubuntu/Linux and what need to be improved"
date: 2006-06-02
forum: The Cafe
---

### Post by buppelupp on 2006-06-02
I have never used Ubuntu/Linux before and just installed the Dapper Drake release. I'm impressed and have decided to migrate but there are a few things I'd like to say. 

While setting it up there was a few things that put me off, which I am sure puts of alot of other people new to linux too. If Ubuntu is to be popularized for people migrating from Windows, or people who simply have no technical skills it needs some key "entertainment features" and it needs to *look good* from the very beginning if people are to be motivated or encouraged to explore Ubuntu any further. 

So here are some suggestions that shouldn't be difficult to implement:

1. There should be a GUI at first startup to configure an automatic mount of NTFS volumes with read access if any are detected. (I don't want to start off my ubuntu experience by learning commands I've never heard of and editing config files that can potentially stop my whole system from working)

2. Automatix should either be added in the add/remove programs list as a standard or at least be made extremely available and simple to install. (I tried to install Mp3 support before I discovered Automatix and to someone new to Linux it is a complete nightmare, especially because the basic principles/workings are so different from Windows when it comes to installing stuff.)   

3. The screen resolution dialogue should show resolutions in the list even if the monitor may not handle them. 
It could then revert to standard res after 5 seconds or something if the user does not confirm that the new res is working.

Having to learn commands and editing system files within an OS one has never touched before to make the even the basics work is very discouraging. 

I believe this is extremely important because at the end of the day, all people want/need is a system where the basics function: Mp3/DivX support, and a decent screen resolution from the beginning is what Ubuntu lacks. I'm aware that they (mp3/divx) are proprietary formats, but if Automatix exists surely it can't be that much of a problem.

---

### Post by jobezone on 2006-06-02
Those are good tips, unfortunatelly I'm not a ubuntu developer (I don't really think any one of them hangs around here).
It doesn't do it automatically?? I don't know, as I've just upgrade from breezy, and I thought that it already did it imediatly... Also, many times the instructions people give include line commands, but there is System->Administration->Discs . Perhaps it could be improved to add partitions not detected (but it should, I agree with you!)

2. This one I don't agree, but I understand. I would tell you about the wiki, like the Restricted Formats page, which explains how to do it easily, but, again, it's not an automatic(x) process. In fact, would we want it to be 100% automatic? Shouldn't ubuntu, as a free OS, be divulgating and promoting free formats and codecs, like ogg vorbis and ogg theora? Anyway, lot's of opinios on this, but it's up to the ubuntu developers (or someone showing it to them).

3. That would be a good idea, but _there_ is a way not to automatically detect the monitor (it asks first). If you do that, you can choose more resolutions. Also, you can launch that configuration program (debconf) for any program anytime and anyway, including over serial lines, over ssh, etc., so it wouldn't be allways helpfull to try the new resolution. But again:), that's up to the future of debconf. So far, I think that it even surpasses windows install methods (search for it on the net, and you'll learn: priorities of questions, multiple frontends, asks all questions before packages are installed, etc.)

So, it's good to have you aboard (or something, geeky and weird way of putting it, uh?) and as people like you demand for even more covenience, or even become a part on bringing that convenience, gnu/linux software will keep improving.

---

### Post by TeeAhr1 on 2006-06-02
[QUOTE=buppelupp]I have never used Ubuntu/Linux before and just installed the Dapper Drake release. I'm impressed and have decided to migrate but there are a few things I'd like to say. 

While setting it up there was a few things that put me off, which I am sure puts of alot of other people new to linux too. If Ubuntu is to be popularized for people migrating from Windows, or people who simply have no technical skills it needs some key "entertainment features" and it needs to *look good* from the very beginning if people are to be motivated or encouraged to explore Ubuntu any further. 

So here are some suggestions that shouldn't be difficult to implement:

1. There should be a GUI at first startup to configure an automatic mount of NTFS volumes with read access if any are detected. (I don't want to start off my ubuntu experience by learning commands I've never heard of and editing config files that can potentially stop my whole system from working)

2. Automatix should either be added in the add/remove programs list as a standard or at least be made extremely available and simple to install. (I tried to install Mp3 support before I discovered Automatix and to someone new to Linux it is a complete nightmare, especially because the basic principles/workings are so different from Windows when it comes to installing stuff.)   

3. The screen resolution dialogue should show resolutions in the list even if the monitor may not handle them. 
It could then revert to standard res after 5 seconds or something if the user does not confirm that the new res is working.

Having to learn commands and editing system files within an OS one has never touched before to make the even the basics work is very discouraging. 

I believe this is extremely important because at the end of the day, all people want/need is a system where the basics function: Mp3/DivX support, and a decent screen resolution from the beginning is what Ubuntu lacks. I'm aware that they (mp3/divx) are proprietary formats, but if Automatix exists surely it can't be that much of a problem.[/QUOTE]

#1 I guess I agree with, but I don't see it as a huge deal, as I've reached the point where I don't need to keep any vital stuff in my NTFS partition anymore.  May I suggest that you set up a FAT partition and put data that you wish to share between OS's there?  I realize that sounds like a hassle, but in the long run, you'll save yourself headaches, I promise.  And being able to write to it is worth it by itself.  If you want some help doing this, please private message me, I'd be glad to walk you through it.

#2 is illegal, at least in the United States.  Ubuntu cannot officially support Automatix, or even officially host the codecs themselves.  This is not a technical barrier, but a social and legal one.  Although, for the record, five minutes on the wiki will tell you exactly what you need to download for media codecs, and then it's just a matter of a few clicks in Synaptic or a couple lines in the terminal.  It's not hard.

#3 I completely agree with.  In response to jobezone, you're kinda right, but monitor autodetection, at least for me, was totally useless and left me at 800x600 until I edited xorg.conf.  I haven't installed Dapper yet, so I can't really speak about potential improvements on that front.  As usual, YMMV.

As jobezone said, good to have you here!

---

### Post by prizrak on 2006-06-02
#1 Has worked for me since Breezy, not sure why it doesn't work for you.
#2 Has been explained, I do believe a document on the desktop that explains it would be better.
#3 The resolutions dialog juts plain sux, I don't want Linux to become Windows but I believe that something to the style of Windows display properties dialog would have been better. 

There is always room for improvement and if those are the only problems for a new user I think that Canonical done great.

---

### Post by aysiu on 2006-06-02
It sounds to me as if someone wants Mepis.

---

### Post by Super King on 2006-06-02
[QUOTE=buppelupp]

1. There should be a GUI at first startup to configure an automatic mount of NTFS volumes with read access if any are detected. (I don't want to start off my ubuntu experience by learning commands I've never heard of and editing config files that can potentially stop my whole system from working)[/QUOTE]

Agreed. Getting it to work is easy by copying/pasting commands from the Wiki, but if you're not searching for the right thing finding the Wiki can be difficult. I don't think people would complain if all NTFS drives were mounted as /media/c, /media/d, or whatever.

> 
2. Automatix should either be added in the add/remove programs list as a standard or at least be made extremely available and simple to install. (I tried to install Mp3 support before I discovered Automatix and to someone new to Linux it is a complete nightmare, especially because the basic principles/workings are so different from Windows when it comes to installing stuff.)   

While it isn't technically including illegal codecs with the installation, I'm still not sure if Ubuntu can legally include a link to these out of the box with the CD. It would be nice though, to have an Automatix launcher on the desktop ala' the live CD installer.

> 
3. The screen resolution dialogue should show resolutions in the list even if the monitor may not handle them. 
It could then revert to standard res after 5 seconds or something if the user does not confirm that the new res is working.

So you want it to show all the resolutions that the graphics card supports?

---

### Post by therunnyman on 2006-06-02
Udev must be destroyed (and replaced with anything, I don't care, as long as it's not udev).

---

### Post by buppelupp on 2006-06-02
1. I'm sure there are several ways to get around this like converting the partition to FAT, reading up on Wiki and so on. But unfortunately, this requires some computer expertise and most people don't have that. Things have to be dead simple if the mainstream user is ever going to change his/her habits and migrate to Ubuntu/Linux. Like you say, who would mind if these partitions where automatically mounted? 

2. I'm sure there is either a way to circumvent legal issues, or at least make information on how to make it work available on the desktop. Let's face it, if I have a huge mp3 collection and a divX collection, I'm pretty much lodged to using Windows if I can't play the files in Ubuntu. Idealistically, I agree that free alternatives should be promoted. But the reality is that 90% of people owning computers have minimal, or no knowledge of the underlying processes in an OS or how to install codecs/compile packages etc, and the vast majority of those won't use an OS where they can't play their music or video-collection. 

3. The Sreen Resolution dialogue should show all the resolutions the Video Card supports, yes. If a resolution doesn't work, the user is unable to confirm a working resolution, and Ubuntu would automatically revert to the previous working resolution after a set countdown. 

In general, it should be assumed that the user is a complete vegetable. If not, Ubuntu will only be for those especially interested and the windows hegemony will keep on growing.

---

### Post by Brunellus on 2006-06-02
don't be a menace to ubuntu while drinking your juice in the hood.

Try Mepis.

---

### Post by prizrak on 2006-06-02
Brunellus, aysiu,
I think the things the OP mentioned are small enough to not warrant a distribution change. A simple document explaining where the wiki is or telling people to go to the forum to get Automatix is fairly simple and does not have to be illegal. If it simply tells you to go to the forums How-To section or the 3rd Party Projects section it won't be viewed as illegal. 
#3 I'm not too sure about if it's the issue with GNOME or xorg. It would be fairly trivial to generate a xorg.conf file that contains all resolutions for the given video card, of course the trade off is a fairly big xorg.conf that is hard to get around. At the very least 1024x768 should be included as it is a standard resolution these days.

---

### Post by Brunellus on 2006-06-02
prizak:  OP is already disappointed by Ubuntu;  Mepis will likely suit his needs better. 

Of course he can fix them himself with some help, but the post is of the usual "how do you expect to put Gates & Ballmer out of business" tone.  

Ubuntu is a good distribution, and my favorite.  But I would still classify it as a good "second distribution."

---

### Post by prizrak on 2006-06-02
[QUOTE=Brunellus]prizak:  OP is already disappointed by Ubuntu;  Mepis will likely suit his needs better. 

Of course he can fix them himself with some help, but the post is of the usual "how do you expect to put Gates & Ballmer out of business" tone.  

Ubuntu is a good distribution, and my favorite.  But I would still classify it as a good "second distribution."[/QUOTE]
Really? Didn't really come across as that to me. The issues seem fairly minor and easily fixed (IMO).

---

### Post by buppelupp on 2006-06-02
[QUOTE=Brunellus]don't be a menace to ubuntu while drinking your juice in the hood.

Try Mepis.[/QUOTE]


I don't understand what your talking about. If you drop the gangster talk maybe I can decipher it.. You want me to try Mepis, that much I gather. But what does this have to do with me suggesting improvements to Ubuntu?

---

### Post by aysiu on 2006-06-02
[QUOTE=prizrak]Brunellus, aysiu,
I think the things the OP mentioned are small enough to not warrant a distribution change.[/QUOTE] The next version of Mepis will be based on Ubuntu.

---

### Post by prizrak on 2006-06-02
[QUOTE=aysiu]The next version of Mepis will be based on Ubuntu.[/QUOTE]
You know as well as I do it's doesn't make it the same. Ubuntu is based on Debian and they are hugely different. I really am not sure why #1 doesn't work for the OP it worked fine in Breezy for me, the drive was detected and mounted on first boot.

---

### Post by aysiu on 2006-06-02
[QUOTE=prizrak]You know as well as I do it's doesn't make it the same. Ubuntu is based on Debian and they are hugely different. I really am not sure why #1 doesn't work for the OP it worked fine in Breezy for me, the drive was detected and mounted on first boot.[/QUOTE] But I feel that the ways they're different work in the OP's favor.

And #1 has never worked for me in Ubuntu. In Mepis, you click on a partition (and all partitions show up on the desktop) and it automatically mounts and opens with the correct permissions.

---

### Post by prizrak on 2006-06-03
Guess I'm the lucky one :) Then again it's hardly critical for me as I don't use Windows

---

### Post by disturbed1 on 2006-06-03
1. My ntfs drive was mounted and an icon was placed on the desktop.

2. If people knew how to read the excellant help documentation, this post would of never been made ;)

3. No it shouldn't. Chosing a resolution your monitor doesn't handle can cause serious problems.

---

### Post by helpme on 2006-06-03
First off, hi and welcome to the forums. :-D 

1. I agree. I don't have any way of testing this, as I don't have a windows partition, but if Ubuntu really doesn't do this, this certainly is an area for improvement.

2. As others already mentioned, this is mostly a legal not a technical issue and I doubt Ubuntu can legaly include something like automatix/easyubuntu. 

3. I don't think allowing resolutions that are not supported is a good idea. After all, there's a risk of breaking your hardware, which certainly isn't a good thing. However, I would agree that Ubuntu is really lacking an easy way to configure X, that is the graphical subsystem so to speak. I really hope this will change with the coming releases.

About some of the comments here. I really don't get it. The OP made some, imho, very valid points about where ubuntu could improve and the answer is, try something else? What a weird reaction.
Now pointing out that the issues mentioned are ubuntu rather than linux specific, or making a recomendation about something the OP might also like certainly isn't a bad thing, but that's not how I read the comments.

---

### Post by 3rdalbum on 2006-06-03
[QUOTE=buppelupp]

So here are some suggestions that shouldn't be difficult to implement:

1. There should be a GUI at first startup to configure an automatic mount of NTFS volumes with read access if any are detected.
[/QUOTE]

True, this would be a cinch to implement. I wrote a Python script that does it, albeit not at first startup. And I've never had a lesson in software development in my life :-)
[QUOTE=buppelupp]
2. Automatix should either be added in the add/remove programs list as a standard or at least be made extremely available and simple to install.[/QUOTE]

There's not much more to be said on this, but instructions to get all restricted audio format support are included in the Help program. (the little lifesaver icon in the menubar)
[QUOTE=buppelupp]

Having to learn commands and editing system files within an OS one has never touched before to make the even the basics work is very discouraging.[/QUOTE]

Well, it's not the "basics". If being able to mount partitions from another operating system is one of the "basics", then Windows fails completely. Editing text files is a little intimidating at first, though.

[QUOTE=buppelupp]and a decent screen resolution from the beginning is what Ubuntu lacks.[/QUOTE]

Must be a bug with your particular hardware combination. My screen resolution has been perfect from the get-go on the computers I've installed Ubuntu onto.

---

### Post by buppelupp on 2006-06-03
> **disturbed1]1. My ntfs drive was mounted and an icon was placed on the desktop.

2. If people knew how to read the excellant help documentation, this post would of never been made  said:**
> 


1. I wouldn't have made the thread if my partitions were mounted and everything worked fine. Just to clarify something in case I'm wrong: the drives where visible but not accessible. I therefore had to edit fstab and add a line containing drive information and the desired parameters to get read-only access. 

2. I know how to read the documentation, but you are missing the point. I'm simply suggesting improvements on how Ubuntu could be made more user-friendly and you are replying with an undertone of arrogance implying that if a user doesn't know how to install a codec he shouldnt be using Ubuntu. (some people seem to suggest that I should install a different distro, because of the small improvements I'm suggesting. That's also missing the point or at least replying to a question I never asked)

3. The way I suggested with a time delay where the user can confirm the resolution is working has been done with the windows-drivers for my videocard as long as I can remember, and my monitor still works fine.. After installing in Ubuntu I started off in 800x600 and had to edit xorg.conf, replacing vsync, hsync, +res. Now, I'm fine with that, but I'm sure most novice users are not. If one little mistake is made in the xorg.conf file the xserver fails to start at all.. 

[QUOTE] Of course he can fix them himself with some help, but the post is of the usual "how do you expect to put Gates & Ballmer out of business" tone.

What's the problem with that tone? And why is this what you choose to pick up on? regardless of the tone, surely my suggestions are quite valid and constructive in any case?

---

### Post by buppelupp on 2006-06-03
> 
Well, it's not the "basics". If being able to mount partitions from another operating system is one of the "basics", then Windows fails completely. Editing text files is a little intimidating at first, though.


I agree. I guess what I was trying to get across was that if someone was a typical Windows user, all their partitions were NTFS, their skills with computers were at a minimal, and all the data and multimedia they had were on those drives..: 
If they one bright, sunny day decided to try Ubuntu they'd be put off  because all their stuff suddenly wasn't accessible anymore. I just don't think people are willing to put very much effort into exploring something new unless they have a political, ideological, or a special interest in OS alternatives/technical aspects etc.  I'm migrating for some of these reasons so I'm willing to put some time into this, but most people are noe at that stage (not yet anyway, hopefully the Vista release will change it :)

---

### Post by buppelupp on 2006-06-03
[QUOTE=Brunellus]prizak:  OP is already disappointed by Ubuntu;  Mepis will likely suit his needs better. 

Of course he can fix them himself with some help, but the post is of the usual "how do you expect to put Gates & Ballmer out of business" tone.  

Ubuntu is a good distribution, and my favorite.  But I would still classify it as a good "second distribution."[/QUOTE]

I'm really happy with Ubuntu and will stick to it. I thought these forums were here so people can exchange thoughts and suggest improvements.

---

### Post by prizrak on 2006-06-03
[QUOTE=buppelupp]I'm really happy with Ubuntu and will stick to it. I thought these forums were here so people can exchange thoughts and suggest improvements.[/QUOTE]
Well actually the forums are mostly for tech support here. Cafe is for random chitchat and stuff. Feature requests are handled by the Launchpad system because it goes straight to the developers. 
Just for the record I do agree with you that those are fairly simple things to implement and shouldn't be an issue.
As for the others telling you to go somewhere else. The problem is that many people have really random suggestions and we (the community) just got tired of them so the response is usually more emotional than logical.

---

### Post by aysiu on 2006-06-03
In defense of the "go somewhere else" crowd--which, for the record is more like the "you might want to try" crowd--I don't see any reason to be loyal to Ubuntu.

If another distro does what you want, why wouldn't you use it? If Ubuntu does implement these new features, hurray. If it doesn't... well, you might want to think about finding a distro that does. That's all I'm saying. And I would suspect others in the "you might want to try" crowd would agree with me.

---

### Post by egon spengler on 2006-06-04
[QUOTE=buppelupp]1. I wouldn't have made the thread if my partitions were mounted and everything worked fine. [/QUOTE]

Obviously, but if you make a post saying "Hey, this doesn't work, you better get to fixing it" whereas it *did* work for him it seems pertinent for him to mention that your experience is not necessarily the universal one

---

### Post by briancurtin on 2006-06-04
[QUOTE=therunnyman]Udev must be destroyed (and replaced with anything, I don't care, as long as it's not udev).[/QUOTE]
can you state more than one reason supporting your case for it being destroyed?
id like to hear...

---

