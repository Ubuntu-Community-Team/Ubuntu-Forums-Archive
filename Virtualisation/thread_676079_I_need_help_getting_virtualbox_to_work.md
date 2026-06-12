---
title: "I need help getting virtualbox to work"
date: 2008-01-23
forum: Virtualisation
---

### Post by boriquajake on 2008-01-23
I have installed Virtual box (see screenshot) and I understand that the next step is to install an OS on the virtual machine I have created. The problem is that when I hit "start" I get an error message. (see below)

As I am sure is obvious I am pretty new to Linux and I don't consider myself any sort of computer expert to start off with, but I am capable of cutting and pasting things into terminal. ;-)

Any help would be very much appreciated. I know that this forum is probably mainly for people with a little more expertise than I have but if someone with some knowhow could give me a hand I would be very grateful.

Oops, I closed the attachment window before it was done.

---

### Post by RebounD11 on 2008-01-23
> **boriquajake said:**
> I have installed Virtual box (see screenshot) and I understand that the next step is to install an OS on the virtual machine I have created. The problem is that when I hit "start" I get an error message. (see below)

As I am sure is obvious I am pretty new to Linux and I don't consider myself any sort of computer expert to start off with, but I am capable of cutting and pasting things into terminal. ;-)

Any help would be very much appreciated. I know that this forum is probably mainly for people with a little more expertise than I have but if someone with some knowhow could give me a hand I would be very grateful.

Where's the screenshot and the error?

EDIT: How new are you to Linux... You have more beans than I do :D

---

### Post by boriquajake on 2008-01-23
I have a lot of beans because I post a lot of questions. Usually my questions are kind of lame and sort of beneath most Linux users, I am probably not quite bright enough to do this but I like it so I keep trying.

---

### Post by boriquajake on 2008-01-23
I have a lot of beans because I post a lot of questions. Usually my questions are kind of lame and sort of beneath most Linux users, I am probably not quite bright enough to do this but I like it so I keep trying.

---

### Post by RebounD11 on 2008-01-23
OK, I went through this before so I think I can help :D

First, I can see you were/are a Windows user, because you didn't read the instructions when you installed, you just clicked Next/Forward. You need to add your user to the virtualbox user-group. To do this go to System -> Administration -> Users and Groups. There click Manage Groups and search for group vboxusers. Then click Properties and check the box beside your user-name. then OK, Close, Close. Now everything should be OK.

Another advice: when you take a screenshot either use the PrintScreen button or move the screenshot dialog out of the way (you might want to give the shot a 2-3 second delay to do that).

Hope this helps :D

PS: Noone is to stupid to use Linux, the really dumb ones refuse to give it a chance :D

---

### Post by FrankVdb on 2008-01-23
You just need to add yourself to the list of VirtualBox users. In other words: it's a permission problem.

Open your terminal and type

sudo adduser frank vboxusers

Replace 'frank' with your user name.

No need to apologise for not knowing much about Linux. We are all in various states of ignorance. You may be much more knowledgible in other areas. Personally I started with Linux only two years ago.

As regards VirtualBox: I run XP in VirtualBox and on my laptop it only takes 7 to 8 seconds to restart it with all the applications I was using the time before.

---

### Post by RebounD11 on 2008-01-23
> **FrankVdb said:**
> You just need to add yourself to the list of VirtualBox users. In other words: it's a permission problem.

Open your terminal and type

sudo adduser frank vboxusers

Replace 'frank' with your user name.

I was trying to help him use the terminal less. It's a known fact that the terminal scares users from Linux. Anyway that is the short and easy way :) and I totally forgot about it :D

---

### Post by boriquajake on 2008-01-23
> **RebounD11 said:**
> OK, I went through this before so I think I can help :D

First, I can see you were/are a Windows user, because you didn't read the instructions when you installed, you just clicked Next/Forward. You need to add your user to the virtualbox user-group. To do this go to System -> Administration -> Users and Groups. There click Manage Groups and search for group vboxusers. Then click Properties and check the box beside your user-name. then OK, Close, Close. Now everything should be OK.

Another advice: when you take a screenshot either use the PrintScreen button or move the screenshot dialog out of the way (you might want to give the shot a 2-3 second delay to do that).

Hope this helps :D

PS: Noone is to stupid to use Linux, the really dumb ones refuse to give it a chance :D

OK I added my user to the virtualbox user group. I am pretty sure I did it successfully because after I followed your gui instructions I typed what Frankvb said to type into terminal and I was told that I was already a member of the virtualbox usergroup.

Anywhoo.. this is what happened when I tried to once again add an OS to my virtualbox machine.

p.s. I appreciate the advice on screenshots. I added a two second delay to the process. ;-)

---

### Post by MONODA on 2008-01-23
Did you read the manual that came with it? You should always do that when usign software like virtualbox.

---

### Post by boriquajake on 2008-01-23
I really appreciate you looking out for us n00bs. In my case the terminal is only scary when I don't have any detailed instructions to follow. I actually like having two ways to do things, it helps me understand a little bit better what the cli is doing.

---

### Post by MONODA on 2008-01-23
try crtl+alt+backspace, it will restart X window

---

### Post by boriquajake on 2008-01-23
> **MONODA said:**
> Did you read the manual that came with it? You should always do that when usign software like virtualbox.

I'm sorry. I guess I didn't make the fact that I am a 32 year-old American male clear.

pshaw, "read the manuel"? What country are you from?

:)

p.s. Just in case I am not as funny as I think I am I mean no disrespect and I was in fact mocking myself for my ignorance not trying to insult anybody.

---

### Post by MONODA on 2008-01-23
:P no offense taken. I guess im a super dork XD... Guess that just me. But really the manual has some really helpful stuff and you can find the info faster than on the forums. Just some advice.

---

### Post by MONODA on 2008-01-23
so did it work???

---

### Post by boriquajake on 2008-01-23
> **MONODA said:**
> so did it work???

Wow, it sure seemed to. I mean I am now in the process of installing Windows XP on the virtual machine. 

Do I need to worry about anything like the the amount of disc space windows will take up? Actually now that I think back that was taken care of when I set up the virtual machine, right? Anyway, without reading the manual I am just going to keep on hitting "enter" until something works or it brakes. Heh heh

---

### Post by RebounD11 on 2008-01-23
> **boriquajake said:**
> Wow, it sure seemed to. I mean I am now in the process of installing Windows XP on the virtual machine. 

Do I need to worry about anything like the the amount of disc space windows will take up? Actually now that I think back that was taken care of when I set up the virtual machine, right? Anyway, without reading the manual I am just going to keep on hitting "enter" until something works or it brakes. Heh heh

Don't forget to mark where it borke down so you don't do it again :P

You should worry about the amount of disk space, if you setup an expanding HD image file, it won't grow above the limit you set but if you have less space on your hard drive than that limit you might find your partition full because of Windows :D.

Otherwise enjoy... and if you want USB support in your virtual machine there is another thread about that:

[http://ubuntuforums.org/showthread.php?t=657191&highlight=virtualbox+usb](http://ubuntuforums.org/showthread.php?t=657191&highlight=virtualbox+usb)

I followed the instructions here and it works :D

---

### Post by boriquajake on 2008-01-23
> **RebounD11 said:**
> Don't forget to mark where it borke down so you don't do it again :P

You should worry about the amount of disk space, if you setup an expanding HD image file, it won't grow above the limit you set but if you have less space on your hard drive than that limit you might find your partition full because of Windows :D.

Otherwise enjoy... and if you want USB support in your virtual machine there is another thread about that:

[http://ubuntuforums.org/showthread.php?t=657191&highlight=virtualbox+usb](http://ubuntuforums.org/showthread.php?t=657191&highlight=virtualbox+usb)

I followed the instructions here and it works :D

Dude, thank you so much!

About that USB support, is that what I will need for a PCMCIA card to be recognized by the virtual machine?

---

### Post by mohnkern on 2008-01-23
Also make sure that after you've added yourself to the vboxusers group that you set up your vm so that it either mounts the CD or it mounts an ISO of a cd, otherwise, you'll start up to a big black screen with nothing.

---

### Post by RebounD11 on 2008-01-23
I don't know much about PCMCIA... if ituses the USB hub yes that's all... if not I don't know...

As much as I know you can only use Serial and USB ports in the Guest OS. 
Besides all I found that's clear on it is this ... 

[http://www.virtualbox.org/discussion/1/286](http://www.virtualbox.org/discussion/1/286)

Sorry :(

---

### Post by boriquajake on 2008-01-23
OK, I thought I was all cool but just when I thought I had Windows installed I get this wierdness. Does this look like anything anyone else has seen?

---

### Post by RebounD11 on 2008-01-23
It looks like a blue screen :D... seriously now I don't know !? try running virtualbox from the terminal and see what it says when it gets there...

---

