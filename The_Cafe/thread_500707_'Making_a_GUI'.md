---
title: "'Making a GUI'"
date: 2007-07-14
forum: The Cafe
---

### Post by Shellfish-os on 2007-07-14
Hello dear Ubuntu users,


I am currently trying to make my own GUI for my own operating system, and/ have ran in to problems.

Resone for making an Operating system; To make my mum happy, in life, becasue i've been ****ing her around latly. OS will be non-sold, just for my family. and friends.

I am trying to build a GUI ( Grapthical user interface) like windows , Ubuntu.

But I don't really know where to start.

So in C++ I have all my head files, ect ect but how do I start? please help me for me and my family!

Many thanks,
Nick.

---

### Post by %hMa@?b&lt;C on 2007-07-14
I would start by looking through the source for small GUI projects,  like sugar
[http://en.wikipedia.org/wiki/Sugar_(GUI](http://en.wikipedia.org/wiki/Sugar_(GUI))

---

### Post by Feba on 2007-07-14
Do you mean operating system as in building your own from the ground up, or do you mean you're making a linux distro?

If you're building your own from the ground up, this should be the least of your worries. If you're making a linux distro, I don't see why you can't use an existing WM like KDE, GNOME, xfce, etc. etc.- to be honest with you, you're probably getting in way over your head. You'd probably be better off programming something that could be useful and nice for her, or configuring an already existing distro to work just right and setting up everything she will need.

---

### Post by Shellfish-os on 2007-07-14
Aritcal not found. but thanks for your help.

---

### Post by %hMa@?b&lt;C on 2007-07-14
> **Shellfish-os said:**
> Aritcal not found. but thanks for your help.

add the last bracket on the end of the link it should be like Sugar_(GUI)
for some reason the link doesnt think that the last bracket is a part of it.

---

### Post by Shellfish-os on 2007-07-14
> **jeffc313 said:**
> add the last bracket on the end of the link it should be like Sugar_(GUI)
for some reason the link doesnt think that the last bracket is a part of it.
Many thanks.

CAn anybody check if my files are alright also?

Suger isnt what I am looking for,

I wanted to build it myself, but just confused what to build it on, I don't want it to be based on Linux either.

---

### Post by %hMa@?b&lt;C on 2007-07-14
what are your files? also, even if you don't release the operating system, at least release the code for the gui.

---

### Post by Shellfish-os on 2007-07-14
> **jeffc313 said:**
> what are your files? also, even if you don't release the operating system, at least release the code for the gui.
Yes, I will, See, I only have soruce code for it, and I don't know how to make a bootable install or put it together my dad put the code in, told me to put it together make a GUI, and make it bootable!

---

### Post by Shellfish-os on 2007-07-14
> **Shellfish-os said:**
> Yes, I will, See, I only have soruce code for it, and I don't know how to make a bootable install or put it together my dad put the code in, told me to put it together make a GUI, and make it bootable!
Anymore help on what I just said?

---

### Post by stepan2 on 2007-07-14
i cant quite understand what you want. are you making an OS or are you making a program?

---

### Post by Shellfish-os on 2007-07-14
> **stepan2 said:**
> i cant quite understand what you want. are you making an OS or are you making a program?
I am making my own operating system for my fmaily, if that is alright with everybody?

---

### Post by Shellfish-os on 2007-07-14
> **Shellfish-os said:**
> I am making my own operating system for my fmaily, if that is alright with everybody?
So does everybody get where I am coming from?

---

### Post by Feba on 2007-07-14
to be brutally honest with you, I think you're in over your head. You should probably get experience modifying an existing OS/Distro/Whatever you're wanting to build before you jump in doing it yourself.

Even Linux itself was based on another OS.

---

### Post by phrostbyte on 2007-07-14
An operating system from scratch?

---

### Post by stepan2 on 2007-07-14
shellfish-os , this is what you do. download ubuntu and isntall it , remove and add the programs you want . Then get a program called remastersys. before u remaster , do export HOME=/etc/skel and mak ehte the customizations u want , then do remastersys dist

---

### Post by Shellfish-os on 2007-07-14
> **phrostbyte said:**
> An operating system from scratch?
Already made most of it, I just need to build a GUI.

---

### Post by Shellfish-os on 2007-07-14
> **stepan2 said:**
> shellfish-os , this is what you do. download ubuntu and isntall it , remove and add the programs you want . Then get a program called remastersys. before u remaster , do export HOME=/etc/skel and mak ehte the customizations u want , then do remastersys dist
No, becsaue then it is no point, I want to build it myself, not nick anybody else code..

---

### Post by stepan2 on 2007-07-14
i dont look at it as nicking someones code when you completely recompile everything.if u wanna make it from scratch use linuxfromscratch.org

---

### Post by Shellfish-os on 2007-07-14
> **stepan2 said:**
> i dont look at it as nicking someones code when you completely recompile everything.if u wanna make it from scratch use linuxfromscratch.org
I don't want to use anything to do with Linux, but thanks.

---

### Post by Shellfish-os on 2007-07-14
Any one going to help me?

---

### Post by DoctorMO on 2007-07-14
> So does everybody get where I am coming from?

It'll take you 20 years to do right, I used to dabble in creating simple guis in assembler back when we had access to bios int calls,  int-21h is where all the gui stuff is if I remember correctly, you know push 21h to ax, data to bx etc.

Anyway you won't get much help here because a) you havn't specified a reason for undertaking such a huge endever b) not many people will likely agree with your reason when you present one c) this is a user forum not a developers forum.

The whole point of open source is that as programmers we are able to read the code that has gone before and use it for what ever we want in order that our projects not take us years and millions of dollars to complete. when you reject other peoples work then I belive as a human you have failed, since one of a humans greatest strengths is co-operation.

---

### Post by xfile087 on 2007-07-14
> **Shellfish-os said:**
> I don't want to use anything to do with Linux, but thanks.

I'm not trying to funny here but if you don't want to use anything to do with Linux... How can we help you? We use Linux...

---

### Post by argie on 2007-07-14
I think that you've set yourself an unrealistic goal, there doesn't seem to be much point in achieving it. Good luck to you on your try, but other people have done quite a lot of work in these fields, why reinvent the wheel?

---

### Post by lzfy on 2007-07-14
I think it's a joke... I mean look at his nickname :/

---

### Post by Shellfish-os on 2007-07-14
> **lzfy said:**
> I think it's a joke... I mean look at his nickname :/
Its not a joke.

And it iwll happen, all i need to do is build a gui..

---

### Post by fyllekajan on 2007-07-14
Rofl

---

### Post by noenter1 on 2007-07-14
If you want people to help you then first thing you need to do is find and goto a developer forum. Also if you ever want help with making any part of a brand new OS, then you are going to have to post your source code. Remember developers aren't telepathic, they actually need to see what you are doing in order to help, especially if your OS isn't like Linux like you claim.

---

### Post by lzfy on 2007-07-14
> **Shellfish-os said:**
> Its not a joke.

And it iwll happen, all i need to do is build a gui..

So all you need is to build a GUI? So basically the kernel etc... are done? Did you build it from scratch? if so how long did it take?
Is it compatibal with Linux? if not will you build new applications like a webbrowser/media player/cd- burning app etc...? How about flash/java and codecs?

---

### Post by bastiegast on 2007-07-14
So you want a windows like gui for an operating system you are going to build yourself(you claim you already did most of it).
Building a gui that is only 50% like windows gui is going to take you years, building an operating system that runs on modern hardware? Man, you are not going to find any help for that not here, not in a developers forum, nowhere.
Of course linus kind of created his own operating system more or less from scratch. But it had no capability to run anything that comes close to a gui.
Building a operating system that runs on todays hardware and can do GCC and run for example X(or do you want to build your own window system from scratch too). It's just not possible, get over it. Don't tell me your going to write your own C compiler too.

Ok this probably is one of the most useless responses I have ever written. You can't say you want to build your own OS and come to ubuntuforums to ask what *programming language* you should use.

If you really have ambitions to do this, then I'm sorry to be so cynical but you should really start buying reading some books, LOTS of books, then start coding, gain experience and gain more experience and even then writing an operating system is probably beyond your reach.

---

### Post by Shellfish-os on 2007-07-14
> **bastiegast said:**
> So you want a windows like gui for an operating system you are going to build yourself(you claim you already did most of it).
Building a gui that is only 50% like windows gui is going to take you years, building an operating system that runs on modern hardware? Man, you are not going to find any help for that not here, not in a developers forum, nowhere.
Of course linus kind of created his own operating system more or less from scratch. But it had no capability to run anything that comes close to a gui.
Building a operating system that runs on todays hardware and can do GCC and run for example X(or do you want to build your own window system from scratch too). It's just not possible, get over it. Don't tell me your going to write your own C compiler too.

Ok this probably is one of the most useless responses I have ever written. You can't say you want to build your own OS and come to ubuntuforums to ask what *programming language* you should use.

If you really have ambitions to do this, then I'm sorry to be so cynical but you should really start buying reading some books, LOTS of books, then start coding, gain experience and gain more experience and even then writing an operating system is probably beyond your reach.
it might be a uselass respones but me and my dad are determaned, as he told me a couple of months ago what we should do and should not,

and no i don't want like windows, we just need a basic one so our family can use it.

---

### Post by smartboyathome on 2007-07-14
If you would like to port something from Linux, you might want XPde. I (unlike most) understand WHY you might want to build it. I also understand that it won't need a lot of hardware testing (just enough for your family or friends). You may want to build a compatability with linux, windows, etc, until you have enough packages to make all the programs you need. I hope this helps you somewhat.

---

### Post by Shellfish-os on 2007-07-14
> **smartboyathome said:**
> If you would like to port something from Linux, you might want XPde. I (unlike most) understand WHY you might want to build it. I also understand that it won't need a lot of hardware testing (just enough for your family or friends). You may want to build a compatability with linux, windows, etc, until you have enough packages to make all the programs you need. I hope this helps you somewhat.
Thank you for your understanding, it's just the fact that the GUI is bugging me, and if anybody wants to help sort my files our from my dad? we dont think we got them right..

we only want a basic system

---

### Post by fyllekajan on 2007-07-14
> **bastiegast said:**
> Ok this probably is one of the most useless responses I have ever written. You can't say you want to build your own OS and come to ubuntuforums to ask what *programming language* you should use.
Sure you can, people do it all the time

---

### Post by regomodo on 2007-07-14
i'd like to see the finished project. personally i wouldn't bother and go with linuxfromscratch

i forgot to add

good luck on not making a complete bag of shite in the time you think it takes to complete a "gui", as you call it. seriously. good luck.

---

### Post by DoctorMO on 2007-07-14
> we only want a basic system

You could use linux for a basic system, what is the reason for doing all this work? really?

---

### Post by Shellfish-os on 2007-07-14
> **fyllekajan said:**
> Sure you can, people do it all the time
i havnt even asked what language to use i am using C++ / C

---

### Post by Feba on 2007-07-14
Why in the world do you think a forum meant to *help people use a specific linux distro* is going to know how to help you build a GUI for a COMPLETELY UNRELATED, PROPRIETARY OS we have NEVER seen code for?

If your concern has nothing at all to do with linux, it shouldn't be here.

---

### Post by Hex_Mandos on 2007-07-14
1) Why are you doing all the work that's already been done? You could just take BSD code for most stuff, as BSD is permissively licensed. 

2) Why is a Linux users forum (from a relatively newbie friendly distro, might I add) a good place to ask this? It's really far from the intent of this forum.

3) Why should anybody help you, if you're not going to share your OS beyond your close relatives and acquaintances?

---

### Post by Shellfish-os on 2007-07-14
> **Hex_Mandos said:**
> 1) Why are you doing all the work that's already been done? You could just take BSD code for most stuff, as BSD is permissively licensed. 

2) Why is a Linux users forum (from a relatively newbie friendly distro, might I add) a good place to ask this? It's really far from the intent of this forum.

3) Why should anybody help you, if you're not going to share your OS beyond your close relatives and acquaintances?
i never said that i would share them or not have i? i wouln't mind... and i qouldnt mind first off.

---

### Post by Hex_Mandos on 2007-07-14
Well, you said it was just for your family. If you're planning to share it, you could make a source code repository for people to help you out. You could also explain what niche your OS is trying to fill that can't be better served by Linux, BSD, Haiku, ReactOS, Minix, OpenSolaris or several other free OSes.

---

### Post by fyllekajan on 2007-07-14
> **Shellfish-os said:**
> i havnt even asked what language to use i am using C++ / C

i never said you did ;)

---

### Post by Shellfish-os on 2007-07-14
> **Hex_Mandos said:**
> Well, you said it was just for your family. If you're planning to share it, you could make a source code repository for people to help you out. You could also explain what niche your OS is trying to fill that can't be better served by Linux, BSD, Haiku, ReactOS, Minix, OpenSolaris or several other free OSes.
alright

if everybody want's me to give it once it will be fianshed then i can do that and it was just going to be for home users.. and it wasnt going to be sold either..

bit typo there sorry.

---

### Post by Hex_Mandos on 2007-07-14
And how will it be better than those above for home users? Linux, Solaris and BSD are decent desktop OSes right now.

And you should really consider making your project open source. You can't expect to be helped if you don't give us the source code or a better description. Seriously, if I found the concept interesting, I could help you out with translations (as I'm no hacker). I personally don't see the point in what you're doing right now, but if you gave us a better explanation on what you're trying to achieve you could get me interested.

---

### Post by Feba on 2007-07-14
yes, but you still haven't explained why in the world you wanted to build yet ANOTHER OS, from SCRATCH, just for your family. Especially considering that it will probably not run for all your family, considering I highly doubt you've done much in the way of driver support

---

### Post by stepan2 on 2007-07-14
dude you have no idea what you are saying. I suggest you learn  a little more before you dive into this project. You can not make a linux OS without using a base Linux OS.!.

---

### Post by DalekClock on 2007-07-14
He's not making a Linux OS, stephan2. He's doing it completely from scratch.

---

### Post by smartboyathome on 2007-07-14
> **stepan2 said:**
> dude you have no idea what you are saying. I suggest you learn  a little more before you dive into this project. You can not make a linux OS without using a base Linux OS.!.

He has said several times, he is not making a Linux OS. He is trying to make his own (and he has reasons).

edit: sorry, DalekClock got there first.

---

### Post by stepan2 on 2007-07-14
o i didnt see. Then he has even more of a no idea on what he is doing..

---

### Post by tehkain on 2007-07-14
So you have coded the core of your OS from scratch? Unless it is made to run on a tamagotchi I doubt it. The simple fact is if you could code a core on your own that will boot you would not be here asking how to craft a GUI. 

Why do you not just do BSD or Linux from scratch? It will still be hell of hard so do not think this is the easy way out. Crafting your own OS is a process that wil take years for even the most basic functions.

---

### Post by smartboyathome on 2007-07-14
> **stepan2 said:**
> o i didnt see. Then he has even more of a no idea on what he is doing..

Just because he is doing something that not many people usually do, doesn't mean he doesn't know what he is doing. It just means it is something that most people do not want to do.

---

### Post by Shellfish-os on 2007-07-14
> **Hex_Mandos said:**
> And how will it be better than those above for home users? Linux, Solaris and BSD are decent desktop OSes right now.

And you should really consider making your project open source. You can't expect to be helped if you don't give us the source code or a better description. Seriously, if I found the concept interesting, I could help you out with translations (as I'm no hacker). I personally don't see the point in what you're doing right now, but if you gave us a better explanation on what you're trying to achieve you could get me interested.
To understand more, To help my family out, I will give soruce code, I will get it open soruce if needed be..

---

### Post by smartboyathome on 2007-07-14
> **Shellfish-os said:**
> To understand more, To help my family out, I will give soruce code, I will get it open soruce if needed be..

I support you 100%. I can't program, so I can't help there, but if you would ever need graphics, I can do my best (I am not the world's best graphics designer, just a pixel mapper).

---

### Post by Shellfish-os on 2007-07-14
> **smartboyathome said:**
> I support you 100%. I can't program, so I can't help there, but if you would ever need graphics, I can do my best (I am not the world's best graphics designer, just a pixel mapper).
Ive 'kind' of got a desktop sorted out.

But the fact is I just having problems starting on a GUI.

---

### Post by PatrickMay16 on 2007-07-14
Shellfish-os, what programming languages do you know? How much work have you done on your OS so far?

---

### Post by Shellfish-os on 2007-07-14
PHP, JS C++ and little java.

Do you want me to post link to it or somthing? kernal, a-memory semaphores and some apps.

---

### Post by smartboyathome on 2007-07-14
Have you thought of looking at how other Gui's (GNOME, Xfce, KDE, etc) are programmed? It may help you immensely.

---

### Post by Shellfish-os on 2007-07-14
> **smartboyathome said:**
> Have you thought of looking at how other Gui's (GNOME, Xfce, KDE, etc) are programmed? It may help you immensely.
Were would I found this from?

---

### Post by Shellfish-os on 2007-07-14
Simple Shellfish OS this is just a bit of the code by the way.

---

### Post by PatrickMay16 on 2007-07-14
STOP! Don't post any more code! Ask your dad if the lisence your code is under allows this.

---

### Post by Shellfish-os on 2007-07-14
> **PatrickMay16 said:**
> STOP! Don't post any more code! Ask your dad if the lisence your code is under allows this.
I think im old ennught to put my own choose but o well.

So what next? i'm getting a desktop disigned now.

---

### Post by bastiegast on 2007-07-14
> **Shellfish-os said:**
> I think im old ennught to put my own choose but o well.

So what next? i'm getting a desktop disigned now.

I still don't get it, you say: I have a kernel or you making one, no problem but you can't make your own gui??

Since your system is neither unix or linux based and as you say written completely from scratch it is not probably is not binary compatible with linux which means you will have to write your own device drivers.
Starting on the gui of your OS means that you have at least completed:

Kernel:
   Memory management
   Device drivers
       Input devices, video, harddisk etc
   Filesystems
   etc.
Compiler:
   How are you going to get your code stuff running? Port GCC?
Shell:
   Linux uses the GNU shell, you must have developed your own shell?
Window system:
    X windows won't run are you going to port it to your OS? or wright your own?
   
Lots of other stuff probably, I'm no expert.

You can confirm that this stuff is all nearly finished? Because it is all needed if you want to run a gui on a PC.

---

### Post by mthakur2006 on 2007-07-14
riiiiiight.....i guess i support you, and my advice would be to look at how gnome, kde, xfce etc's codes and see the logic behind it, i.e. how they work. then port it to your own.

but i can't help but thinking that you could easily use their code as well (my personal response and i HAVE read all the posts, thank you. :)

thanks.

---

### Post by Shellfish-os on 2007-07-15
SO what do I do? look at someone elses coding and then put it to my own use?

---

### Post by kinematic on 2007-07-15
just out of interest,what kind of kernel have you written....is it monolithic?
have you written all the device drivers you need as well as all the kernel/user-space programs?
what kind of file system layout are you using and have you written your own toolkit for your gui?
and what about security,do you use root like on linux?

---

### Post by EdThaSlayer on 2007-07-15
Well, good luck. You still have loads of work to do. :)

---

### Post by Shellfish-os on 2007-07-15
[IMG]http://www.uploadz.co.uk/840backgroundpsd.jpg[/IMG]

if anybody really cares, I made a desktop background.

---

### Post by Feba on 2007-07-15
Ok, you say you're doing this for you family, but how in the world is coding an OS from scratch, which is no doubt going to be buggy, have driver problems, and going to be a PITA to support more worthwhile than using an existing OS and customizing it or working out whatever kinks you have?

I STILL don't see why you think that a linux forum- for a 'newb friendly' distro at that- would have any idea how 'your' OS works, let alone how to program a GUI for it. 

And about the code- It's not a matter of age, it's a matter of copyright law. If your dad contributed code to it, and he doesn't want it to be open source, it can't be.

---

### Post by mthakur2006 on 2007-07-15
> **Shellfish-os said:**
> SO what do I do? look at someone elses coding and then put it to my own use?

yup :D

---

### Post by Shellfish-os on 2007-07-15
> **mthakur2006 said:**
> yup :D
Will look into it.

---

### Post by mthakur2006 on 2007-07-15
> **Shellfish-os said:**
> Will look into it.

now you are starting to make sense....rock on
and my best wishes.

---

### Post by kinematic on 2007-07-15
to be honest.i think you're full of bs.
it's nearly impossible for you and your dad to write a complete fully functioning OS unless the two of you started this endavour like 25 yrs ago.
just take a look at a random GNU/Linux distro,it has taken some 15 yrs and developers from all over the world to get were we are today.
the amount of code that goes into something like this is just too much for two people to handle in a reasonable amount of time.

---

### Post by maniacmusician on 2007-07-15
you said that you were going to release the source code; where is it? 

Personally, I don't think that it is possible to you have written even half a kernel in two months. At least not one that will do anything. and I definitely won't believe it until I see it. You built a network stack, wrote hardware drivers, etc? I mean, you said that everything except the 'GUI' was done, so let's see it. 

And for the GUI you'll need to build an X server of sorts; something that can draw windows on screen. Paired with that has be an extended system that can deal with hardware drivers to enable video cards to use the X interface and draw things. Furthermore, you would have to write the drivers for a specific video card to actually be able to do this effectively. That alone would take months, unless you do nothing but eat, sleep, and code. I don't see how you could have already coded a complete kernel, which is must more complicated than this.

---

### Post by aks44 on 2007-07-15
You guys are just a bunch of unbelievers.

Look, the desktop wallpaper is already ready for production, I don't need any other proof!

And concerning kinematic's comment:
> just take a look at a random GNU/Linux distro,it has taken some 15 yrs and developers from all over the world to get were we are today.
Come on, it's a well known fact that free software developpers are lazy, bearded communists, so how can you ever expect then to be even close to productive?

</irony>

@OP: funny troll BTW...

---

### Post by proalan on 2007-07-15
and assuming that you'd have done all of the above, you'd still need to write a set of APIs similar to GTK, opengl, which are huge projects themselves, then further more build your own applications like office, internet browsers ... 

In short it has taken a global effort from the open source community to take linux this far. Are you sure what you've done is actually an operating system?

---

### Post by aks44 on 2007-07-15
> **proalan said:**
> Are you sure what you've done is actually an operating system?

Now I see the light... he's in fact designing a GNOME theme.

LMAO

---

### Post by mostwanted on 2007-07-15
People here need to readjust their troll detectors. Eight pages and counting...

---

### Post by kiddo on 2007-07-15
yeah but does it run on an iPhone?

---

### Post by Shellfish-os on 2007-07-15
So now how do I get my desktop in to it?

---

### Post by smartboyathome on 2007-07-15
> **kiddo said:**
> yeah but does it run on an iPhone?

Not every Linux distro does. ;)

---

### Post by smartboyathome on 2007-07-15
> **Shellfish-os said:**
> So now how do I get my desktop in to it?

You will have to do that on your own, unless you can set up a site for your OS, with a forum and such. Then people can help you.

---

### Post by insane_alien on 2007-07-15
Did you and your dad actually write the code or did your dad just give you things to compile?

from the way you sound its like you haven't done anything near programming an OS otherwise you would have given us much much more information. actually, you would never have posted here in the first place, you would have bought a book on the subject.

---

### Post by maniacmusician on 2007-07-15
> **insane_alien said:**
> Did you and your dad actually write the code or did your dad just give you things to compile?

from the way you sound its like you haven't done anything near programming an OS otherwise you would have given us much much more information. actually, you would never have posted here in the first place, you would have bought a book on the subject.
no, if he was building a real OS from scratch; he wouldn't have been stupid enough to try in the first place.

---

### Post by stepan2 on 2007-07-15
> **insane_alien said:**
> Did you and your dad actually write the code or did your dad just give you things to compile?

from the way you sound its like you haven't done anything near programming an OS otherwise you would have given us much much more information. actually, you would never have posted here in the first place, you would have bought a book on the subject.

I agree with you 100 percent

---

### Post by Feba on 2007-07-15
> **aks44 said:**
> Now I see the light... he's in fact designing a GNOME theme.

LMAO

At first I laughed. Then with a creeping horror, I realized you probably aren't far off.

---

### Post by kinematic on 2007-07-15
> **Shellfish-os said:**
> So now how do I get my desktop in to it?

if you've already written the entire OS and just need to integrate the gui this should be a piece of cake for a super coder like you ;-)

in fact,the ubuntu team should hire you since you've clearly done what no other programmer has ever been able to do ;-)

all hail Shellfish-os,all hail the super coder !

(and furthermore,since it's not linux based stop asking for help on a linux forum,go bother someone else you super coder you)

---

### Post by stepan2 on 2007-07-15
lol. i saw a post by lzfy asking him if he finished building the kernel and etc.. but he hasnt replied. So shellfish? you made the kernel and everyhting?

---

### Post by M$LOL on 2007-07-15
> **maniacmusician said:**
> no, if he was building a real OS from scratch; he wouldn't have been stupid enough to try in the first place.

Personally, I disagree with that, if everyone thought like that then nobody would ever get anywhere. I think that making an OS from scratch is a little unrealistic for somebody to take on themselves unless they have a lot of expertise in the area and have worked on similar projects before. Even then it would be a huge task and would require dedication and determination. IMO a more practical approach would be to take on a specific part yourself, maybe with some help, or form a team where everyone can do a specific part.

---

### Post by ssam on 2007-07-15
lots of people write operating systems look at [http://en.wikipedia.org/wiki/List_of_operating_systems#Hobby](http://en.wikipedia.org/wiki/List_of_operating_systems#Hobby)

its a big job, but an OS does not need to be a big and complex as Linux.

if you just want something very customised then you can probably do it more easily by modifing an existing system, or building it on top of linux and Xorg. but i understand that sometimes it is nice to see what you can do on your own.

i suggest than you look at other systems, and see how they work. make sure you respect licences and copyright.

---

### Post by Shellfish-os on 2007-07-15
[IMG]http://www.uploadz.co.uk/436backgroundpsd(1).jpg[/IMG]

act # 2

---

### Post by Kimm on 2007-07-15
> **Shellfish-os said:**
> [IMG]http://www.uploadz.co.uk/436backgroundpsd(1).jpg[/IMG]

act # 2

No offense, but that looks very Windows-ish (look at the fonts).

Are you sure your not talking about a shell for Windows? Because I've seen lots of people making that mistake.

---

### Post by urukrama on 2007-07-15
Shellfish-os, are you the person behind [this]("http://shellfish-os.com/forums/index.php") site, and [this]("http://forums.digitalpoint.com/showthread.php?t=384128") thread on another forum?

---

### Post by forrestcupp on 2007-07-15
Here's a quote from [his post](http://forums.digitalpoint.com/showpost.php?p=3633196&postcount=47) in the other thread.
> Windows Vista has 60million lines of code, Shellfish only has 100 lines.
How can you make a complete kernel and OS minus the GUI with only 100 lines of code?

---

### Post by insane_alien on 2007-07-15
100 lines of code possible, if it is for a calculator.

---

### Post by PatrickMay16 on 2007-07-15
Alright, I can help you with this now. You want to 'get your desktop into it' right? OK. Get some hammars and nails and hammar the desktop in with the nails. Make sure it a tight fit. DENIS DENIS DENIS.

---

### Post by Feba on 2007-07-15
uuuuuh. I think my *wristwatch* has more code in it than that.

and it's not even one of them nifty casio dealies.




(well ok, It's a casio, but it's a waveceptor, not a calculator watch)

---

### Post by pumpum on 2007-07-15
<sarcasm> *to the OP* You've got friends! </sarcasm> :-({|=

---

### Post by mthakur2006 on 2007-07-15
> **pumpum said:**
> <sarcasm> *to the OP* You've got friends! </sarcasm> :-({|=

u r polite!

---

### Post by fyllekajan on 2007-07-15
Shellfish people have feelings too you know! ...not sure how many friends though 
yea anyway what's up with the ad thingy? I'm tired...

---

### Post by regomodo on 2007-07-15
a quote from the op at that other site

"Pure old C? what is this?"

i don't program and even i know what that is.

it's sounding more and more like a shell for windows

---

### Post by forrestcupp on 2007-07-15
Well, the only thing I've seen so far is a wallpaper graphic.  Anybody can make that with the GIMP.

---

### Post by ice60 on 2007-07-15
maybe you can get some ideas from this thread :confused: lol
[http://www.binrev.com/forums/index.php?showtopic=28993](http://www.binrev.com/forums/index.php?showtopic=28993)

---

### Post by M$LOL on 2007-07-16
> **insane_alien said:**
> 100 lines of code possible, if it is for a calculator.
Maybe they're really long lines :lol:
> **ice60 said:**
> maybe you can get some ideas from this thread :confused: lol
[http://www.binrev.com/forums/index.php?showtopic=28993](http://www.binrev.com/forums/index.php?showtopic=28993)

Oooh, I love the green IPB skin.

---

### Post by runningwithscissors on 2007-07-16
This thread is f*cking epic.

---

### Post by wersdaluv on 2007-07-16
I love the OP.

**Edit: This should be on digg!!!!!!!**

---

### Post by olejorgen on 2007-07-16
wow, that's 5 minutes of my life I'll never get back :P

---

### Post by stepan2 on 2007-07-16
lol , he never replies to the questions we ask him as he is afraid to say anyhting. Now that we found out he only has 100 lines of ode i think he left.

---

### Post by cogadh on 2007-07-16
> **olejorgen said:**
> wow, that's 5 minutes of my life I'll never get back :P
Ditto, what a waste.

---

### Post by stepan2 on 2007-07-16
man i just want to hear a reply by him so bad

---

### Post by neoflight on 2007-07-16
> **Shellfish-os said:**
> it might be a uselass respones but me and my dad are determaned, as he told me a couple of months ago what we should do and should not,

and no i don't want like windows, we just need a basic one so our family can use it.

why dont you take kde, or Gnome, or xfce, E, codes and see how its written? may be that will help. if you cannot understand a chunk of code in those then ask some devs...

i think most people are responding the way they are now is because we are not clear exactly what you meant by "making GUI"....its already been done, as in, making a UI wrapper around the kernel...

take the source codes of one of the WM  and study the code....if you do not want to use them. or clone them then take the science and build you own code from scratch....

good luck...

and people..do not just say that its impossible (though extremely tough, i agree) to write an OS from scratch...it could be that the OS is not for PC's ... in the past talents have been severely underestimated....:popcorn:

---

### Post by stepan2 on 2007-07-16
good reply neoflight but we hsve a right to tell HIM it is impossible as he basically ridiculed the idea of basing an OS on another when when he has only written 100 lines of code

---

### Post by neoflight on 2007-07-16
> **stepan2 said:**
> good reply neoflight but we hsve a right to tell HIM it is impossible as he basically ridiculed the idea of basing an OS on another when when he has only written 100 lines of code

yea...sorry....i just failed to read the 100 line of code messages before i posted...i was excited to see the responses on the first page and started posting...
i think he is gone, frustrated...

---

### Post by ThinkBuntu on 2007-07-16
Find out what that guy at SymphonyOS is doing these days...maybe you can grab his source code and use it as a model.

---

### Post by kiddo on 2007-07-16
I just looked at the shellfish-os forums and that other thread. Hm. It's too hard to resist:

[SIZE="6"]The Great Scale of Credibility and Trustworthiness ;)[/SIZE] (more is better)
<=======1============2==========3=============4========5=====>
[LIST=1]
[*]shellfish-os
[*]duke nukem forever
[*]Fox News
[*]underpant gnomes
[*][Altimit OS]("http://www.altimit-os.net")
[/LIST]

---

### Post by tbroderick on 2007-07-16
This thread should be locked.

---

### Post by regomodo on 2007-07-16
> **tbroderick said:**
> This thread should be locked.

this thread should be archived for prosperity

{edit} - yeah @ kiddo. I was wrong. It didn't look right at the time. I'll leave it as it is. The OP is definitely going to prosper with our help for a "gui"

---

### Post by kiddo on 2007-07-17
*[posterity]("http://www.google.com/search?q=define%3Aposterity")* you mean? Otherwise, if you really did mean prosperity.. hmm. I guess it would go like the usual: 
[LIST=1]
[*] Start archiving threads 
[*] ??? 
[*] Prosperity!!!
[/LIST]

Ok, enough slashdot-style-nonsense-flooding for now, I'll go get some sleep :-D sorry!

---

### Post by user1397 on 2007-07-17
How about nobody posts again unless it's the OP.  Yes? No?

---

### Post by steven8 on 2007-07-17
> **ubuntuman001 said:**
> How about nobody posts again unless it's the OP.  Yes? No?

Make a poll!!  :)  I don't want to answer you because that would be posting again. . . .

---

### Post by runningwithscissors on 2007-07-17
> **regomodo said:**
> this thread should be archived for prosperity
not for prosperity but for great justice.

---

