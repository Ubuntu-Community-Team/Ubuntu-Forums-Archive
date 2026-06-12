---
title: "Ubuntu or Windows (Please, just an advice, no holy war)"
date: 2009-10-06
forum: The Cafe
---

### Post by vadimy on 2009-10-06
I was working as a web developer on Windows XP and Windows 7 machines for a while. Used XP for about 5 years and Windows 7 for about half a year. New version is pretty cool, usable and, what's probably most important for me, it's "friendly".

I'm now on Ubuntu 9.10 Beta and I love it too. I love it because, as an Apache/MySQL/PHP developer, there's a similar environment to Linux systems running on the servers of tons of hosters. Actually, I switched to Ubuntu only because of it. And it's pretty easier to develop and deploy right on my Linux box. But...

The reason is that even if I'm on tuned and polished Ubuntu right now, I miss Windows... That's the problem I've encountered even 2 years ago when I installed Ubuntu for the first time. After that time I was working on Windows, however, as I've said, I wanted to work on Linux because of its environment, and, moreover, it's a good braintraining :)

So, everything that I said points to that I feel very uncomfortable here. Yes, I wished a good environment for web development, and I got it. But what's wrong, lol, I don't know...

Don't know what to ask for, maybe an advice, maybe a similar story of your own... How to completely LOVE this system? Or how to feel comfortable working on it? Now it takes me 2 times longer to handle different actions in Ubuntu than in Windows XP/7.

---

### Post by fela on 2009-10-06
You could try a different desktop environment, although I always found gnome very easy to use.

If you prefer Ubuntu/Linux's environment to Windows', then I suggest you stay with it. Just persevere, and make sure to learn at least the basics of the command line as it'll make your tasks in Linux soooooooooo much faster than either Ubuntu/Linux with no command line, or Windows. In fact, on Linux I've found that you're more limited without the command line than on Windows, as windows is a more GUI-centric operating system.

Also, putting the name of both a Linux distro and Windows in the same thread title is a sure way to start a flame war...even if that wasn't your original intention! But yeah back on topic, **stay with Linux and learn the CLI if you haven't already.**

---

### Post by unknownPoster on 2009-10-06
I'd use Windows as my primary OS and use Ubuntu in VirtualBox. There's no point in forcing yourself to love an Operating System that doesn't meet your needs. This will work really well after you get Guest Additions installed in the Ubuntu VM.

---

### Post by dragos240 on 2009-10-06
Well. You can dual boot systems, meaning you can run 2 operating systems at once. It's pretty straightforward. And since Linux is open source, you could make it look like XP or 7 very easily. Any theme you ever wanted could be downloaded from gnome look.

---

### Post by unknownPoster on 2009-10-06
> **dragos240 said:**
> Well. You can dual boot systems, meaning you can run 2 operating systems at once. It's pretty straightforward. And since Linux is open source, you could make it look like XP or 7 very easily. Any theme you ever wanted could be downloaded from gnome look.

I've never understood why someone would want to make Linux look like something that it's not...you're better off just using the real thing.

---

### Post by dragos240 on 2009-10-06
Eh, the feel of using Linux and the look of something you're used to. That's all.

---

### Post by -grubby on 2009-10-06
> **dragos240 said:**
> you can run 2 operating systems at once.

lolwut?

---

### Post by hoppipolla on 2009-10-06
owh we're not allowed our usual holy war? ._.

lol :)

---

### Post by dragos240 on 2009-10-06
> **-grubby said:**
> lolwut?

Sorry, tired. You can have 2 dedicated operating systems that can run side by side.

---

### Post by fillintheblanks on 2009-10-06
I've been windows free now for almost 2 years. I no longer have to pirate software, it feels great :P

---

### Post by tcoffeep on 2009-10-06
You're gonna pay for mentioning microshite winblows in this forum. I declare an unholy open-sourced jihad on your blaspheming behind. (am i doing it right?)

---

### Post by unknownPoster on 2009-10-06
> **fillintheblanks said:**
> I've been windows free now for almost 2 years. I no longer have to pirate software, it feels great :P

You don't have to pirate software in Windows. That was your choice, not the choice of your operating system. In addition many open-source programs run on Windows, such as Firefox, GIMP, Chrome, VirtualBox, etc.

---

### Post by hoppipolla on 2009-10-06
> **unknownPoster said:**
> You don't have to pirate software in Windows. That was your choice, not the choice of your operating system. In addition many open-source programs run on Windows, such as Firefox, GIMP, Chrome, VirtualBox, etc.

lol he has a point though, it is a nice feeling getting a plentiful and easy supply of free, quite competent software :)


As for the Linux/Windows comparison... use what you like to use man. Or dual boot... or just use KDE as that feels pretty much like Windows anyway (in a good way lol)! :)

---

### Post by Giant Speck on 2009-10-06
> **tcoffeep said:**
> You're gonna pay for mentioning microshite winblows in this forum. I declare an unholy open-sourced jihad on your blaspheming behind. (am i doing it right?)

You didn't use any dollar signs.

I am disappoint.

---

### Post by stinger30au on 2009-10-07
if you must you windows for certain programs that dont work in linux, then so be it



i have setup a number of clients with dual boot windows ubuntu pc's

they use ubuntu for send/recive emails and surf the net and thats it

they use windows for everything else

user +1
virus/callouts 0

ubuntu wins!

---

### Post by bigboy_pdb on 2009-10-07
If you're only using Ubuntu as a LAMP (Linux, Apache, MySQL & PHP) web server, as was suggested before, you may want to install it in a virtual machine. I'm running Ubuntu server in a virtual machine with LAMP and BIND (as a name server) and I'm connecting to it using a software bridge. You should be able to do the same thing in Windows. The only issue with using Ubuntu server is that it's command line based (although you could install a desktop).

If you're using other development tools or software within Ubuntu, but you're more comfortable with Windows, you may want to install the desktop version in a virtual machine in Windows.

If you use the command line or other power tools (ie. grep, sed, awk, etc.) in Ubuntu, you can look into installing [cygwin]("http://www.cygwin.com/") in Windows (although you'll probably run into problems with the newlines being different between the two OSes). An alternate route is to install Windows in a virtual machine within Ubuntu.

If you rely on a lot of software within Ubuntu or you think that this may become the case, you can install Windows in a virtual machine instead.

I'm a developer and I switched to using Ubuntu for it's powerful command line and scripting capabilities (among many other reasons). I run Windows in VirtualBox for cross browser (and OS) testing. Lately, I've been learning to develop using C# within Windows. I've never had any problems with running Windows from a virtual machine so far. However, if your hardware isn't well supported or it is older, if you run software that's resource intensive, or if you need direct access to your hardware, you probably won't want to use this sort of set up.

**EDIT**: I know that dual booting is often suggested, but it isn't very productive since you have to restart your computer to use the other OS. Also, Windows can't read ext3/ext4 file systems by default, meaning you'll have to have install software to read those partitions or move files to a partition that Windows can read and has access to (unless Wubi uses a Windows folder as a partition or something).

---

### Post by starcannon on 2009-10-07
> **vadimy said:**
> 

The reason is that even if I'm on tuned and polished Ubuntu right now, I miss Windows... That's the problem I've encountered even 2 years ago when I installed Ubuntu for the first time. After that time I was working on Windows, however, as I've said, I wanted to work on Linux because of its environment, and, moreover, it's a good braintraining :)

So, everything that I said points to that I feel very uncomfortable here. Yes, I wished a good environment for web development, and I got it. But what's wrong, lol, I don't know...

You can have your cake and eat it too. Just dual boot; now you have the best of both worlds. Don't want to be bothered with rebooting the computer to get from Windows<->Linux? Then run Linux in a virtual machine on Windows, or run Windows in a virtual machine on Linux. You don't have to choose one or the other, you can have it your way.

GL and HF

---

### Post by stwschool on 2009-10-07
When I install Ubuntu for people I dual-boot them for this very reason. It means you get the best of both worlds. But, honestly, if Ubuntu's not for you, then use Windows. You can get Apache, PHP and MySQL working in Windows (as I used to) though it's not suitable for live production use, and you can get caught out with case sensitivity that way, but it can be done. Use the best tool for the job. Be it windows, mac, linux, BSD, AmigaOS, UNIX or whatever you choose. It's your computer after all.

---

### Post by Sand &amp; Mercury on 2009-10-07
My advice is to customise. Make it your own! You can change ANYTHING.

---

### Post by tcoffeep on 2009-10-07
> **Giant Speck said:**
> You didn't use any dollar signs.

I am disappoint.

:( I'll try harder next time. I promise, boss.

---

### Post by OpenGuard on 2009-10-07
As a web developer and graphics designer, I use Windows on my main machine ( Photoshop, NetBeans, etc. ) and Linux on my laptop ( e-mail and similar, non-OS dependent activities ). If you feel the need to use Windows, it's nothing you should hide - use it ( I do :) ).

---

### Post by wersdaluv on 2009-10-07
> **vadimy said:**
> I was working as a web developer on Windows XP and Windows 7 machines for a while. Used XP for about 5 years and Windows 7 for about half a year. New version is pretty cool, usable and, what's probably most important for me, it's "friendly".

I'm now on Ubuntu 9.10 Beta and I love it too. I love it because, as an Apache/MySQL/PHP developer, there's a similar environment to Linux systems running on the servers of tons of hosters. Actually, I switched to Ubuntu only because of it. And it's pretty easier to develop and deploy right on my Linux box. But...

The reason is that even if I'm on tuned and polished Ubuntu right now, I miss Windows... That's the problem I've encountered even 2 years ago when I installed Ubuntu for the first time. After that time I was working on Windows, however, as I've said, I wanted to work on Linux because of its environment, and, moreover, it's a good braintraining :)

So, everything that I said points to that I feel very uncomfortable here. Yes, I wished a good environment for web development, and I got it. But what's wrong, lol, I don't know...

Don't know what to ask for, maybe an advice, maybe a similar story of your own... How to completely LOVE this system? Or how to feel comfortable working on it? Now it takes me 2 times longer to handle different actions in Ubuntu than in Windows XP/7.
I'm no developer, but I'm into the design of the desktop user experience.

I don't know what it is that you aren't comfortable with. Is it with Ubuntu as a desktop? Since it's good enough for your development, it must be that. If so, please tell us what you mostly do on your desktop OS. Some users encounter problems because of multimedia, apps that aren't available or of a lower quality for Linux, etc. Other than those, it could be your being uncomfortable with the Linux way of doing desktop things like installing software (which we love), window manager conventions, look and feel, etc.

Please tell us what you mostly do on your desktop OS :)

---

### Post by howefield on 2009-10-07
> **unknownPoster said:**
> You don't have to pirate software in Windows. That was your choice, not the choice of your operating system. In addition many open-source programs run on Windows, such as Firefox, GIMP, Chrome, VirtualBox, etc.

Hmmm,  choice... ?

More like a Morton's Fork.

Though, a good point on the open source alternatives.

---

### Post by jonian_g on 2009-10-07
> **unknownPoster said:**
> You don't have to pirate software in Windows. That was your choice, not the choice of your operating system. In addition many open-source programs run on Windows, such as Firefox, GIMP, Chrome, VirtualBox, etc.

Some people have to. Why? Money. Not everyone has plenty of them. And the most pirated software are not Web Browsers, Photoshop (many people, believe it or not, don't know what photoshop is) or virtual machines, but are games.

Do you have any idea how much a game costs. And considering the quality of games these days, do they worth that amount of money?

Example. I bought a game for PS3, which looked very good, but wasn't that good. And on top of that it lasted 2 days. And now I wonder why the hell I spent 40 euros on that. I would have preferred to pirate it (the problem is, I don't have windows, so I would have to pirate that too).

PS: You have bought the codecs to play your media files on ubuntu, right?

---

### Post by howefield on 2009-10-07
> **jonian_g said:**
> Some people have to. Why? Money. Not everyone has plenty of them...... *[snip excuses]*

You can't use money as an excuse, not when there are so many free alternatives.

---

### Post by RiceMonster on 2009-10-07
> **jonian_g said:**
> Some people have to. Why? Money. Not everyone has plenty of them. And the most pirated software are not Web Browsers, Photoshop (many people, believe it or not, don't know what photoshop is) or virtual machines, but are games.

Do you have any idea how much a game costs. And considering the quality of games these days, do they worth that amount of money?

Example. I bought a game for PS3, which looked very good, but wasn't that good. And on top of that it lasted 2 days. And now I wonder why the hell I spent 40 euros on that. I would have preferred to pirate it (the problem is, I don't have windows, so I would have to pirate that too).

Are you honestly suggesting people have to pirate games?

"OMG how will I live without crisis? I guess I'll have to pirate it so I can make a living!"

---

### Post by jonian_g on 2009-10-07
> **RiceMonster said:**
> Are you honestly suggesting people have to pirate games?

"OMG how will I live without crisis? I guess I'll have to pirate it so I can make a living!"

I'm giving the excuse to the people that do it.

Pay attention, I play games on PS3 and I don't have windows. There are no pirated games on PS3.

Comprende?

---

### Post by jonian_g on 2009-10-07
> **howefield said:**
> You can't use money as an excuse, not when there are so many free alternatives.

The ones that have money, don't consider it as an excuse.
The ones that don't have, don't give a crap on what the former say.

BTW: I was talking about games. So the mention of alternatives doesn't fit.

---

### Post by RiceMonster on 2009-10-07
> **jonian_g said:**
> I'm giving the excuse to the people that do it.

Pay attention, I play games on PS3 and I don't have windows. There are no pirated games on PS3.

Comprende?

I never accused you of pirating games. 

However, my point still stands. You're suggesting people have to pirate games. No they don't. If they can't afford it/don't want to spend the money, then they don't get to have said games. That's not the end of the world because games aren't something people need.

---

### Post by jonian_g on 2009-10-07
> **RiceMonster said:**
> I never accused you of pirating games. 

However, my point still stands. You're suggesting people have to pirate games. No they don't. If they can't afford it/don't want to spend the money, then they don't get it, and that's not the end of the world because games aren't something people need.

I don't care. I'm not the one to judge them. I don't care if multinational companies lose money from pirated software.

---

### Post by howefield on 2009-10-07
> **jonian_g said:**
> The ones that have money, don't consider it as an excuse.
The ones that don't have, don't give a crap on what the former say.

BTW: I was talking about games. So the mention of alternatives doesn't fit.

So your excuse isn't about money then.....

And the alternatives very much do fit.

---

### Post by jonian_g on 2009-10-07
> **howefield said:**
> So your excuse isn't about money then.....

And the alternatives very much do fit.

Buying a game once or twice in a year doesn't mean I have lots of money.

BTW: We are of topic, so lets not bother the other people that read the thread.

---

### Post by Tristam Green on 2009-10-07
> **jonian_g said:**
> I don't care. I'm not the one to judge them. I don't care if multinational companies lose money from pirated software.

You're not judging the companies, but you're lending your somewhat-roundabout-approval for the pirating of games by attempting to legitimize it in a Devil's Advocate scenario.

---

### Post by jonian_g on 2009-10-07
> **Tristam Green said:**
> You're not judging the companies, but you're lending your somewhat-roundabout-approval for the pirating of games by attempting to legitimize it in a Devil's Advocate scenario.

If you're in economics, you'll see that pirating is being done with those companies blessings.

---

### Post by blur xc on 2009-10-07
> **tcoffeep said:**
> You're gonna pay for mentioning microshite winblows in this forum. I declare an unholy open-sourced jihad on your blaspheming behind. (am i doing it right?)



:lolflag:

That's some good stuff right there...

BM

---

### Post by gordintoronto on 2009-10-07
> **vadimy said:**
> ... How to completely LOVE this system? Or how to feel comfortable working on it? Now it takes me 2 times longer to handle different actions in Ubuntu than in Windows XP/7.

I have had very similar feelings!  One of the things which helped me was to print a cheat-sheet of common command-line commands, such as at [http://ss64.com/bash/](http://ss64.com/bash/)  

When I was in the terminal, I often wasted a lot of time with, "what darned command will do such-and-such."  I used DOS for a lot of years, and that experience is counter-productive.  "How do I TYPE a file?  Oh, 'they' decided CAT was more appropriate.  How annoying."  And yes, "CAT" won't work, it must be lower case...

My suggestion for a good environment for you: Windows 7, install Virtualbox, install Linux Mint in a box, then install LAMP under Mint.  Sounds a lot more complicated than it really is.  It's a gang-busters web development/testing setup.

---

### Post by ElSlunko on 2009-10-07
It will probably take as many years in Ubuntu to become comfortable as it took in Windows. It's not impossible to get that comfy in Ubuntu, many of us have!

---

### Post by Exodist on 2009-10-07
> **vadimy said:**
> I was working as a web developer on Windows XP and Windows 7 machines for a while. Used XP for about 5 years and Windows 7 for about half a year. New version is pretty cool, usable and, what's probably most important for me, it's "friendly".

I'm now on Ubuntu 9.10 Beta and I love it too. I love it because, as an Apache/MySQL/PHP developer, there's a similar environment to Linux systems running on the servers of tons of hosters. Actually, I switched to Ubuntu only because of it. And it's pretty easier to develop and deploy right on my Linux box. But...

The reason is that even if I'm on tuned and polished Ubuntu right now, I miss Windows... That's the problem I've encountered even 2 years ago when I installed Ubuntu for the first time. After that time I was working on Windows, however, as I've said, I wanted to work on Linux because of its environment, and, moreover, it's a good braintraining :)

So, everything that I said points to that I feel very uncomfortable here. Yes, I wished a good environment for web development, and I got it. But what's wrong, lol, I don't know...

Don't know what to ask for, maybe an advice, maybe a similar story of your own... How to completely LOVE this system? Or how to feel comfortable working on it? Now it takes me 2 times longer to handle different actions in Ubuntu than in Windows XP/7.

If WebDev is your money maker, stick to what feels/works for you. If its Windows, then stay windows. If Ubuntu is very intriguing to you, then start using it for personal stuff and set small goals to do with it. Like your own personal web page and so forth using only linux tools like GIMP and Coffe Cup HTML editor. When you've got to where you can do very very good with your own stuff then thats when it would be a good time to start converting your business over. 

Hope this helps.

- Exo

---

