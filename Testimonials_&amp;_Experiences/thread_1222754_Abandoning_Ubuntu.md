---
title: "Abandoning Ubuntu"
date: 2009-07-25
forum: Testimonials &amp; Experiences
---

### Post by Stugol on 2009-07-25
I've stuck with Ubuntu now for a few months on my server machine, but I've finally decided to replace it with Windows.

Why? I'll explain.

1) MySQL doesn't work properly and the author doesn't consider Linux to be a "supported platform".

2) Firebird database doesn't work properly.

3) MPlayer crashes when presented with a media file it doesn't happen to like.

4) Ubuntu crashes randomly several times a day for no apparent reason.

5) Samba is unstable - suddenly the network shares are inaccessible for no reason; or I try to access them and Windows will only let me access them as "Guest", even though "simple file sharing" is turned off.

6) Wine only works with a small subset of applications. It doesn't work with Explorer, Trillian, Worms World Party, Treesize Professional, or dozens of other applications I've tried it with. It also won't let you replace TCPIP.SYS in the System32 folder; rendering uTorrent COMPLETELY USELESS under Wine.

7) No USABLE multi-platform instant messenger seems to exist for Linux. That is, ALL of them suffer from a bug - the SAME bug - wherein the "don't make a stupid noise when I SEND a message" option doesn't work. It seems that EVERY SINGLE MESSENGER PROGRAM is based on the SAME buggy library. Even the console-based one has the EXACT same bug.

8) The "Disk Usage Analyser" doesn't work correctly; reporting incorrect sizes for many of my folders, and (incorrectly) claming that they contain dozens of "hardlinks" instead of files and folders.

9) Getting hardware drivers for Linux is almost impossible.

10) In order to get online, you need drivers for your modem, because when you bought it, it only came with Windows drivers. But, to download them, you need to be online. Catch-22.

11) Every time something goes wrong with Linux, you have to scour forums and ask for help. Which is difficult to do when you DON'T HAVE A COMPUTER anymore.

12) I installed a new PCI SATA card, and plugged a drive into it. Now that drive shows up in Ubuntu as "SDA", screwing up GRUB, and all my startup scripts for mounting other partitions. If I put my boot drive on the SATA card, I can't boot off it.

13) If I plug in an IDE or SATA drive after Ubuntu loads - or, even, set the BIOS to ignore it - there is no easy or obvious way to tell Ubuntu to detect it. In Windows, you just bring up Device Manager and tell it to detect.

14) KTorrent refuses to accept "malformed" torrents (whereas most other clients will accept them) and the source code for the new version will not compile. (Okay, so the torrents shouldn't be malformed. Thing is, they ARE.)

15) Deluge (torrent client) slows the computer down for no reason.

16) Trying to burn files to a CD or DVD is an exercise in futility. Try 0.3k/s write speed; and the drive LOCKING UP when I abort the process. Plus you get no "verify" option like you do in Nero, or ImgBurn, or EVERY OTHER Windows-based burning software.

17) Internet connection sharing is a complete SOD to set up.

18) You can't "Remote Desktop" a Vista machine from Ubuntu; or Ubuntu from any Windows machine. And no, "VNC" just isn't good enough.

19) TrueCrypt doesn't support operating system encryption on Ubuntu, so encrypting my entire system is almost impossible. Yes, I'm aware that it CAN be done, but it's risky, and requires [a] a fresh installation of Ubuntu and [b] spare partitions on the harddrive. (AFAIK)

20) UPnP doesn't seem to work.

21) If you abort a copy or move operation - or it fails - the truncated destination file remains. Under Windows, if that happens, the failed copy is automatically deleted. Having it stick around can only cause problems.


Of course, half of these objections will turn out to be due to my ignorance; I fully expect that. But surely SOME of these problems are real; and valid.

If Wine worked with all Windows software (perhaps by making use of Windows system files from a licenced Windows install CD); and if the system was a little more reliable - i.e. if I didn't have to post on forums all the damn time just to use my operating system! - maybe it'd be a bit more useful. But as things stand, I'm sick of all the crashes, the network problems, the configuration issues, and all the applications that are source-code-only and DON'T BLOODY COMPILE even when you follow the damn TUTORIAL on the author's homepage!

Just my two cents. I've tried, and I've tried, and I've tried; and it's just more damn trouble than it's worth. I need a STABLE server here - and that's just not happening with Linux.

---

### Post by DeMus on 2009-07-25
> **Stugol said:**
> I've stuck with Ubuntu now for a few months on my server machine, but I've finally decided to replace it with Windows.

Why? I'll explain.

1) MySQL doesn't work properly and the author doesn't consider Linux to be a "supported platform".

2) Firebird database doesn't work properly.

3) MPlayer crashes when presented with a media file it doesn't happen to like.

4) Ubuntu crashes randomly several times a day for no apparent reason.

5) Samba is unstable - suddenly the network shares are inaccessible for no reason; or I try to access them and Windows will only let me access them as "Guest", even though "simple file sharing" is turned off.

6) Wine only works with a small subset of applications. It doesn't work with Explorer, Trillian, Worms World Party, Treesize Professional, or dozens of other applications I've tried it with. It also won't let you replace TCPIP.SYS in the System32 folder; rendering uTorrent COMPLETELY USELESS under Wine.

7) No USABLE multi-platform instant messenger seems to exist for Linux. That is, ALL of them suffer from a bug - the SAME bug - wherein the "don't make a stupid noise when I SEND a message" option doesn't work. It seems that EVERY SINGLE MESSENGER PROGRAM is based on the SAME buggy library. Even the console-based one has the EXACT same bug.

8) The "Disk Usage Analyser" doesn't work correctly; reporting incorrect sizes for many of my folders, and (incorrectly) claming that they contain dozens of "hardlinks" instead of files and folders.

9) Getting hardware drivers for Linux is almost impossible.

10) In order to get online, you need drivers for your modem, because when you bought it, it only came with Windows drivers. But, to download them, you need to be online. Catch-22.

11) Every time something goes wrong with Linux, you have to scour forums and ask for help. Which is difficult to do when you DON'T HAVE A COMPUTER anymore.

12) I installed a new PCI SATA card, and plugged a drive into it. Now that drive shows up in Ubuntu as "SDA", screwing up GRUB, and all my startup scripts for mounting other partitions. If I put my boot drive on the SATA card, I can't boot off it.

13) If I plug in an IDE or SATA drive after Ubuntu loads - or, even, set the BIOS to ignore it - there is no easy or obvious way to tell Ubuntu to detect it. In Windows, you just bring up Device Manager and tell it to detect.

14) KTorrent refuses to accept "malformed" torrents (whereas most other clients will accept them) and the source code for the new version will not compile. (Okay, so the torrents shouldn't be malformed. Thing is, they ARE.)

15) Deluge (torrent client) slows the computer down for no reason.

16) Trying to burn files to a CD or DVD is an exercise in futility. Try 0.3k/s write speed; and the drive LOCKING UP when I abort the process. Plus you get no "verify" option like you do in Nero, or ImgBurn, or EVERY OTHER Windows-based burning software.

17) Internet connection sharing is a complete SOD to set up.

18) You can't "Remote Desktop" a Vista machine from Ubuntu; or Ubuntu from any Windows machine. And no, "VNC" just isn't good enough.

19) TrueCrypt doesn't support operating system encryption on Ubuntu, so encrypting my entire system is almost impossible. Yes, I'm aware that it CAN be done, but it's risky, and requires [a] a fresh installation of Ubuntu and [b] spare partitions on the harddrive. (AFAIK)

20) UPnP doesn't seem to work.

21) If you abort a copy or move operation - or it fails - the truncated destination file remains. Under Windows, if that happens, the failed copy is automatically deleted. Having it stick around can only cause problems.


Of course, half of these objections will turn out to be due to my ignorance; I fully expect that. But surely SOME of these problems are real; and valid.

If Wine worked with all Windows software (perhaps by making use of Windows system files from a licenced Windows install CD); and if the system was a little more reliable - i.e. if I didn't have to post on forums all the damn time just to use my operating system! - maybe it'd be a bit more useful. But as things stand, I'm sick of all the crashes, the network problems, the configuration issues, and all the applications that are source-code-only and DON'T BLOODY COMPILE even when you follow the damn TUTORIAL on the author's homepage!

Just my two cents. I've tried, and I've tried, and I've tried; and it's just more damn trouble than it's worth. I need a STABLE server here - and that's just not happening with Linux.

Okay, points taken. Bye.

---

### Post by Iowan on 2009-07-25
Good luck with Windows.

---

### Post by Stugol on 2009-07-25
Oh, and:
22) Firebird inserted itself into my startup, and then FAILED TO LOAD, hanging the system mid-startup before I even got into Gnome. How incredibly USEFUL. I had to drop to a command prompt and delete the startup script from init.d.

---

### Post by Penguin Guy on 2009-07-25
I'm confused about exactly what you're trying to run Ubuntu on - a server or a desktop? Anyway, thanks for at least telling us why you're leaving :KS I expect quite a lot of users in your situation just leave without even posting a message.

---

### Post by Stugol on 2009-07-25
Odd. If *I* was the Linux addict, and *you* posted the original message, I would've at least tried to advocate it a bit, solve a problem or two, that kind of thing. But you guys seem to be just "okay, you don't like it, well **** off then."

That's another thing.
23) Half the people who post on this forum seem to be unhelpful bastards who don't even TRY to help. I've encountered this before.

---

### Post by Whiffle on 2009-07-25
I applaud your use of a numbered list, instead of the usual WoT (Wall of Text).

I don't agree with all your points, some of which I have yet to experience even though I'm using some of the same programs.  But, if they're not working for you then I guess thats that. 

I would suggest you give a different version of linux a shot, such as CentOS or debian, at least for your server needs.

---

### Post by Stugol on 2009-07-25
> **Penguin Guy said:**
> I'm confused about exactly what you're trying to run Ubuntu on - a server or a desktop? Anyway, thanks for at least telling us why you're leaving :KS I expect quite a lot of users in your situation just leave without even posting a message.

Well, it's a desktop machine that I'm using primarily as a file and print server. I mean, where do you draw the line?

And yes, I was *trying* to give constructive criticism on my way out. Some of you guys don't seem to appreciate it.

---

### Post by Stugol on 2009-07-25
> **Whiffle said:**
> I applaud your use of a numbered list, instead of the usual WoT (Wall of Text).

I don't agree with all your points, some of which I have yet to experience even though I'm using some of the same programs.  But, if they're not working for you then I guess thats that. 

I would suggest you give a different version of linux a shot, such as CentOS or debian, at least for your server needs.

I've tried all those. Like, a dozen different flavours. Ubuntu is the ONLY version of Linux that I find even *remotely* useful.

If it'd stop damnwell crashing, I might stick with it. But I can't continue to put up with this instability on my network server.

---

### Post by DeMus on 2009-07-25
> **Stugol said:**
> Odd. If *I* was the Linux addict, and *you* posted the original message, I would've at least tried to advocate it a bit, solve a problem or two, that kind of thing. But you guys seem to be just "okay, you don't like it, well **** off then."

That's another thing.
23) Half the people who post on this forum seem to be unhelpful bastards who don't even TRY to help. I've encountered this before.

Excuse me. But to call us "unhelpful bastards" is something nobody here likes to hear.
I join this forum day in-day out and try to help as good as I can. I am also still learning Ubuntu and Linux and I also need help now and then.
If you really think about us the way you described then yes, nobody is sorry to see you go.
I wrote my first post since your list of complaints was so long, there is nothing to do about it anyway. You seem to be doing things differently and thus are getting problems with programs which for others run fine.
You better join a Windows forum and ask for help there - as if you will get any.
Good luck with your Windows system, spend all your money on that crap. Or are you using it illegally?

---

### Post by Whiffle on 2009-07-25
> **Stugol said:**
> I've tried all those. Like, a dozen different flavours. Ubuntu is the ONLY version of Linux that I find even *remotely* useful.

If it'd stop damnwell crashing, I might stick with it. But I can't continue to put up with this instability on my network server.

Yeah thats weird.  If ya ask me, I think there is either something wrong with your hardware (flaky power supply maybe), or a driver issue.  Linux can be *extremely stable*.  For example:

 00:03:02 up 104 days,  6:33,  0 users,  load average: 0.16, 0.03, 0.01

is the uptime of a computer that I have setup doing data logging in a house, and its built out of an old laptop that I completely dismembered. Granted, it doesn't have to do much, but it runs just fine.  The last time it had to be rebooted, was a power failure.  It has never crashed.  I've seen my own desktop go 40+ days though without an issue as well.  

I don't get your issue with the IM program making sounds on send either, because that is the first thing I turn off on pidgin and it actually turns off.  

Also, what drivers are you having trouble finding?  

Finally, modems.  I hate winmodems.  I have yet to make the one work in my laptop.  For that project above, the laptop was also equipped with a winmodem.  I spent $10 on ebay to buy a real hardware modem, and couldn't be happier.


EDIT:  Oh and about these other nuts who aren't being helpful.  Do what my mom always said, "if you don't have anything nice to say, don't say anything at all" ;)   I'd have about 10x the posts if I didn't follow that rule :)

---

### Post by mCion on 2009-07-25
Sorry about your bad experience.  Maybe you can try it in the future.  The first time I installed ubuntu I could not get my wireless working (searched for many hours everywhere).  I waited a few months then got fed up with windows again, tried Ubuntu again, and because it's a growing project, everything finally worked.

Also I have to note something.  You said
> 23) Half the people who post on this forum seem to be unhelpful bastards who don't even TRY to help. I've encountered this before.

That's looking at a glass that's half empty.  There are many helpful people here.  Who knows how many problems, simple or advanced, have been solved by the community.

---

### Post by aj_the_first on 2009-07-25
I think there are a lot of valid points here. I have been having problems non-stop with Ubuntu, but then I feel that all I have to do is post on a forum and I usually get a simple answer within a few hours. With windows... I am just screwed.
 
As for things not compiling and installing: AMEN!! Even when I follow the exact instructions in the readme files, I still get all sorts of errors that aren't covered anywhere in the troubleshooting guide. In fact, I have not yet successfully installed a SINGLE tarball. Only .deb packages. It has gotten to the point that if all that is available is a tarball, then I just walk away and don't use it.
 
But as for me, when it comes to Windows: WHOA! At least I don't have to deal with that headache anymore!
I prefer the linux headache to the Windows headache because I feel empowered instead of helpless when the inevitable problems do arise.
 
Now if I can't get this most recent ubuntu wireless issue resolved soon, then maybe I am leaving too...

---

### Post by Stugol on 2009-07-25
> **DeMus said:**
> I wrote my first post since your list of complaints was so long, there is nothing to do about it anyway.

Huh? You mean "you're having so many problems that there's nothing to fix" ????

The most important thing is the crashes. Obviously.

> **DeMus said:**
> You seem to be doing things differently

Ah. You mean I'm dunking my PC in orange juice, perhaps? Or typing with my feet?

> **DeMus said:**
> and thus are getting problems with programs which for others run fine.

Oh, I see. It's all MY fault. Gotcha.

OBVIOUSLY it must be my fault. After all, nobody else EVER has any problems with Linux. That's why there's a MASSIVE HONKING GREAT HUGE FORUM here, with hundreds of people yelling "HELP!! My system doesn't work!!!"

Do you people ever listen to yourselves when you speak?

> **DeMus said:**
>  You better join a Windows forum and ask for help there - as if you will get any.

That's just it: I don't NEED a Windows forum. Sure, Windows is riddled with bugs, but they're usually more "annoying" than "catastrophic". Yeah, okay, there's the blue screen of death; but I don't often get that. What I *do* get is Ubuntu completely freezing up several times a day.

> **DeMus said:**
> Good luck with your Windows system, spend all your money on that crap. Or are you using it illegally?

Now you're just trying to start a fight by calling me a thief.

---

### Post by Stugol on 2009-07-25
> **Whiffle said:**
> Yeah thats weird.  If ya ask me, I think there is either something wrong with your hardware (flaky power supply maybe), or a driver issue.  Linux can be *extremely stable*.

I identified a previous instability as something to do with my hard drive, but I solved that one by moving Ubuntu to a different drive.

I have no idea what could be causing this problem. If it was a power supply problem - or other hardware - then Windows would be just as unstable, wouldn't it?

> **Whiffle said:**
> I don't get your issue with the IM program making sounds on send either, because that is the first thing I turn off on pidgin and it actually turns off.

Odd. None of 'em work properly on here.

> **Whiffle said:**
> Also, what drivers are you having trouble finding?

Currently, none. But I had a hell of a time a few weeks back with modems and wifi cards.

> **Whiffle said:**
> EDIT:  Oh and about these other nuts who aren't being helpful.  Do what my mom always said, "if you don't have anything nice to say, don't say anything at all" ;)   I'd have about 10x the posts if I didn't follow that rule :)

Well, I did say that only HALF of the posters were unhelpful. The other half - such as you - are genuinely helpful. Only the unhelpful ones should be offended by my statement - therefore, by extension, the ones who express the most offence are likely to be the unhelpful ones.

Thus far, my theory seems accurate.

---

### Post by Stugol on 2009-07-25
> **mCion said:**
> There are many helpful people here.  Who knows how many problems, simple or advanced, have been solved by the community.

Again, I would point out that I merely referred to HALF of the population. I've asked for help before, and got a load of stupid suggestions that would've made things worse; and a bunch of trolls and the like. There are a couple on this thread, I notice.

Look, if anyone can help me find why it keeps crashing all the time, maybe I'll stick with it for a while. But all I'm seeing is an unstable OS that's more difficult to use and configure than what I had before. Is it any wonder that I'm a little tetchy?

---

### Post by utUtu on 2009-07-25
Why are you still here?

---

### Post by Stugol on 2009-07-25
> **aj_the_first said:**
> I think there are a lot of valid points here. I have been having problems non-stop with Ubuntu ... As for things not compiling and installing: AMEN!! Even when I follow the exact instructions in the readme files, I still get all sorts of errors that aren't covered anywhere in the troubleshooting guide. In fact, I have not yet successfully installed a SINGLE tarball. Only .deb packages. It has gotten to the point that if all that is available is a tarball, then I just walk away and don't use it.

See? SEE? It's not just me!

Whenever I post any criticism on these forums, I get a bunch of trolls telling me to sod off and pirate Windows instead. Is it any wonder I consider half of these guys to be unhelpful?

Thanks for your supporting voice.

---

### Post by philcamlin on 2009-07-25
> **utUtu said:**
> Why are you still here?

+1 i thought you wanted to leave???

** ubuntu doesnt work with everyones hardware and your pc is probably one of them. ubuntu is great but only when it works right :D **

---

### Post by Whiffle on 2009-07-25
> **Stugol said:**
> I identified a previous instability as something to do with my hard drive, but I solved that one by moving Ubuntu to a different drive.

I have no idea what could be causing this problem. If it was a power supply problem - or other hardware - then Windows would be just as unstable, wouldn't it?



Pretty much, then I'd blame a driver issue.

> **Stugol said:**
> 
Well, I did say that only HALF of the posters were unhelpful. The other half - such as you - are genuinely helpful. Only the unhelpful ones should be offended by my statement - therefore, by extension, the ones who express the most offence are likely to be the unhelpful ones.

Thus far, my theory seems accurate.

Yeah actually that part of my post was intended to be addressed at other people, but I failed to word it correctly.  Oh well, its Saturday and my levels of "care" are pretty low.

---

### Post by Stugol on 2009-07-25
> **utUtu said:**
> Why are you still here?

Two reasons. Firstly, TROLLS LIKE YOU keep insulting me, and I thought I'd stick around for a minute to defend myself.

Secondly, a couple of people are actually being helpful.

---

### Post by philcamlin on 2009-07-25
> **Stugol said:**
> Two reasons. Firstly, TROLLS LIKE YOU keep insulting me, and I thought I'd stick around for a minute to defend myself.

Secondly, a couple of people are actually being helpful.

please ignore things like that that annoy you were here to help not insult or fight :popcorn:

---

### Post by DeMus on 2009-07-25
In my first post after your long list of complaints I wrote: Bye.
It looked to me you had so many issues, I could understand very well you decide to return to Windows.

Yes, you are doing things differently then others (and no wise guy, I don't mean typing with your feet or dunk the PC in orange juice) since the programs you mentioned do work for others. First of all you seem to use a server for desktop things, or is it a desktop system which acts as a server?

I am not talking about your fault or the system's fault, it's just a fact you have lots of problems, hence your long list.  The fact we have a large forum here is because there are a lot of new Linux users here asking for help since their Ubuntu system is different from their Windows system. You should know that Linux is not Windows. It's not as well known as Windows, but people like to try it since they are all fed up with Microsoft and their Windows, but they need help to get started, to get things done.

Ah, the BSOD's are not as bad as your crashing Ubuntu. That's one way of putting it.

About using the Windows programs, using it legit or not is something I don't know. It would surprise me however if you have a legit Windows server software at home and while having it, go for the free (as in charge) Linux server. Not to mention all the other programs you need to buy to do the same as you do now in Ubuntu.

If you really are that annoyed about Ubuntu then please go to your favorite Windows, but don't come here and call us unhelpful bastards. You should know that here on the forum nobody gets paid for helping others. We are all Ubuntu users, loving the system because it is free (not only in price) and we do try to help as many people as possible. If you can't see that then you should not be here. Hence: Bye.

---

### Post by Stugol on 2009-07-25
> **philcamlin said:**
> +1 i thought you wanted to leave???

** ubuntu doesnt work with everyones hardware and your pc is probably one of them. ubuntu is great but only when it works right :D **

Correction: I want to stop using Ubuntu because it keeps crashing.

If someone can tell me how to stop it crashing, well, fair enough.

But yes, if enough of you act like jerks - and well done for adding to that number - I'll just give up here.

---

### Post by Rocket2DMn on 2009-07-25
Moved to Ubuntu Testimonials & Experiences.  Sorry Ubuntu didn't work out for you.

---

### Post by philcamlin on 2009-07-25
> **Rocket2DMn said:**
> Moved to Ubuntu Testimonials & Experiences.  Sorry Ubuntu didn't work out for you.

+1 ubuntu has very good support for pc's 

2 in maybe 150 have a tiny issue and thats it but this one looks like hes got really incoompatible hardware :(

---

### Post by Stugol on 2009-07-25
> **DeMus said:**
> Yes, you are doing things differently then others (and no wise guy, I don't mean typing with your feet or dunk the PC in orange juice) since the programs you mentioned do work for others.

Your logic is flawed.

"You are having problems that I am not having, therefore you are doing things in an unusual way"

Or, perhaps, Ubuntu just doesn't like my computer, or the combination of software I'm using, or just doesn't like my face.

> **DeMus said:**
> First of all you seem to use a server for desktop things, or is it a desktop system which acts as a server?

I'm using a desktop machine as a file and print server, and to download torrents. It's not a stupid idea.

> **DeMus said:**
> Ah, the BSOD's are not as bad as your crashing Ubuntu. That's one way of putting it.

No, that isn't what I said. I said that I don't get many BSODs, but I *do* get plenty of Ubuntu crashes. Are you being deliberately obtuse, or do you have some kind of mental deficiency?

> **DeMus said:**
>  About using the Windows programs, using it legit or not is something I don't know. It would surprise me however if you have a legit Windows server software at home and while having it, go for the free (as in charge) Linux server. Not to mention all the other programs you need to buy to do the same as you do now in Ubuntu.

I wanted a more stable system, and a little bit of a challenge.

What I got was a less stable system, and a whole host of problems that exceeded my definition of "challenge".

---

### Post by Arthur_D on 2009-07-25
Hey, everybody, can we just calm down a little bit?
Over-reacting on every hint of sarcasm doesn't help anybody in any way.

---

### Post by viralmeme on 2009-07-25
TROLL .. :popcorn:

---

### Post by UranUtan on 2009-07-25
Hi,

I am in a kind of same situation. Except that whenever I have an issue under Linux, I try to solve it at any cost. I am still not comfortable with Linux but I try to accommodate. Most of the time, the cause is lack of knowledge and some buggy programs indeed. But there is always a solution or an acceptable workaround. Providing you spend enough time to seek for help or to learn.

You are right, however, saying that you are stuck if you have only one computer. But this is a minor problem in my opinion. People throw away plenty of old P3 and P4 machines, or you can get a decent used computer for $20. 

Among the issues you mentioned, some I don't have, some I can live with (the little noise when sending). I think you may have some hardware issues. Therefore some of the problems will likely show up under Windows.

There are definitely a solutions you some of your issues but as you have already made up your mind so I would just say that Windows seems easier simply because most of people spent time to learn it since so many years. Your Linux experience will be hindered if you don't accept that Linux is different.

---

### Post by thelaughingbuddha on 2009-07-25
Hi Stugol!
I can understand your frustration. I have tried using Ubuntu from the past four years and given up facing some very irritating problems similar to yours. But from the past one week its my primary OS (Jaunty), primarily because I have a fast internet connection. You need it to get fixes and updates and try a lot of stuff.
I can suggest a few possible fixes to some of your problems. I am no expert and I welcome any comments from anyone regarding them.

Possible Solution for the issue number:

3) You can try using VLC or/and (I am not sure if VLC needs any codecs even in Linux. anybody?) install the foll. plugins listed in this nice thread [http://ubuntuforums.org/showthread.php?t=1181327](http://ubuntuforums.org/showthread.php?t=1181327)

7) Pidgin is a multi-platform messenger (atleast Windows and Linux) and I tried muting the sounds using the option TOOLS -> MUTE SOUNDS. It works for me.

9) Most relatively new and common devices do have drivers provided by the linux community if not the manufacturer. Exotic H/W may not.

10) Try using a cyber cafe to troubleshoot if your linux m/c is not able to connect.

16) Using Brasero Disc burner, I can get quite high write speeds. More importantly, it computes a pre-image checksum for an ISO image and a post-image checksum after burning it. But I COULDN'T find any option to VERIFY the files after burning a data CD/DVD. Anybody knows of any plugin for this functionality?

Well, I hope you are going to stick around Linux but if not then Good Luck with Windows. You should go along with whatever gets your work done efficiently.

---

### Post by running_rabbit07 on 2009-07-25
> **Stugol said:**
> Odd. If *I* was the Linux addict, and *you* posted the original message, I would've at least tried to advocate it a bit, solve a problem or two, that kind of thing. But you guys seem to be just "okay, you don't like it, well **** off then."

That's another thing.
23) Half the people who post on this forum seem to be unhelpful bastards who don't even TRY to help. I've encountered this before.

Your weren't asking for help. When people come here and say they are leaving it is usually understood as you don't want help. If you still want help edit your original post and ask if anybody would like to help you. There are some really intelligent people here that can help with your problems. 

Please remember that if you are not paying someone for help, you can't demand or expect it. If you ask nicely though people usually will help. When someone says they are leaving for the other OS, that is taken like a slap in the face by some users.

---

### Post by aysiu on 2009-07-25
> **running_rabbit07 said:**
> If you still want help edit your original post and ask if anybody would like to help you. Actually, I would suggest starting a new support thread.

Changing the original post to suddenly ask for help would just make this thread more confusing.

---

