---
title: "12 years using windows and 2 days playing with linux"
date: 2010-03-22
forum: Testimonials &amp; Experiences
---

### Post by unpresedented on 2010-03-22
dear all,
I'm a windows power user, I switched to linux ubuntu just before two days, in these two days, I couldn't install a single program correctly (except for something called; wine after it took an hour from me in order to be able to install it), so I found out the following things in the last two days using linux ubuntu 9.10 :
1) installing programs in general is very complicated, it requires terminal many times, I faced things like : add software source then add public key (am i going to hack the whitehouse!!) then sometimes it says there is an error because there is no public key found (although I have provided the right key for it) ... 
some other people say : type something chmod  .. plus some other thing and then you can install any program .. others say : apt-get on terminal ... why all of this headache !!
 
2) installing some hardware drivers is somehow difficult.
 
2.1) system hangs when I try to install some hardware drivers (like dell broadcom wireless card driver) and then all I have to do is press the power button and turn off the machine.
 
3) whenever I try to read tutorials in ubuntu, all of these tutorials requires me to use terminal ... terminal ... terminal ... this is hell !
 
4) it's very hard to fix errors (broken packages for e.g.) , I have to be expert in terminal to do so ... because the graphical option in synaptic (hope I didn't misspelled the word) to fix broken packages does not work (this happened with me and many other users on different machines)
 
5) something vital that I need to test my web pages on, Internet Explorer 8 over Windows 7, I did not find a single tutorial to help me set up IE8 over windows 7 using wine ! you believe it !! two days trying and trying to install that piece of browser (which is consider one of the best browsers) and then ended up with NOTHING ! :(
 
5.5) Linux ubuntu 9.10 does not have a built in rdp protocol, that means I can't log into my windows server using remote desktop unless I install a program that supports it, and 90% of these programs on Linux are considered either buggy or slow, is that right ?
 
I can do everything with Windows 7 very easily, and without having to use terminal (command prompt) except for rare cases ... plus it is stable (no craches at all) and very fast .. plus, what I can do on Linux ubuntu I can do it easily on Windows 7 !!
 
finally, I didn't open this thread to compare linux with windows, I need advice, do you advise me to stay on Linux Ubuntu and forget Windows ? I need somebody to convince me why I should use Linux Ubuntu and leave Windows !! or vice versa ...

---

### Post by bikeboy on 2010-03-22
Linux is not Windows. It does things differently. Someone who has never used Windows wouldn't have a clue how to install software, drivers etc. etc.

You have two options:

1) Learn to use Linux - which is actually very easy.

2) Use Windows.

Honestly, I'd say it would seem you'll be happier with Windows, since it's the so-called 'Power Users' who tend to find themselves the most lost on the easy to use but highly flexible Linux based desktop.

Read this, then decide what you want - [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

As far as some specific issues go:

Installing software is a piece of cake, and far less hit and miss than on Windows. It's generally easier for us to give you instruction for command line methods, since you can just copy and paste. But you can also go to System > Admin > Synaptic. From there, you can search for software to do just about anything. eg. RDP software - try Grdesktop. The pre-installed remote desktop software (Applications > Internet > Remote desktop viewer) doesn't yet support the proprietary RDP protocol but it is planned. Currently it uses VNC instead.

You very rarely install hardware drivers on Linux, they are built into the kernel. It is less effort for most people to buy better hardware that supports Linux than to try compiling new drivers in. And so it should be, it's not the end user's problem to take care of drivers.

Use an online browser shot renderer or Virtualbox with Windows if you need to develop for Internet Explorer. WINE is hit and miss, and not a real solution. For all intents and purposes, Internet Explorer does not work on Linux. And thank god for that!

If you have broken packages, invariably you've gotten out of your depth. Stick to the default software repositories until you at least know a tiny bit about what you're doing. We're all noobs at first (arguably I still am after 5 years :D ), don't be ashamed of it.

Having said all of that, go back to Windows 7. It's shiny and doesn't cause toooo much frustration, even for Windows. Your mindset is ingrained in Windows and you are obviously tied to some of its software. I don't think you're coming to Linux for enough the right reasons to enjoy learning its ways. Better to stick with what you know than get annoyed at not knowing the new platform and then blaming Linux - much to the scorn of those who know how good it is.

---

### Post by bumanie on 2010-03-22
If you don't like terminal, why not use synaptic package manager or as you have 9.10, software centre? That would save you most of the terminal work.
My main suggestion would be to remember this is not windows and things are done differently, this does not mean they are harder to do, just that one needs to take time to learn a new way of doing things.
Most hardware drivers are contained in the kernel and linux has unmatched hardware detection (not sure about broadcom drivers).
Can't comment on windows 7 - other than one time I tried it in virtual box - I found it uninspiring and slow. although I had ram being shared 3 ways, so it is probably not a fair test.
When I first moved to linux, I found everything difficult and was still in the 'windows mind-set', now I find windows painful to use and convoluted. Why is this? Because I have taken the time to learn linux. It is much more functional than windows in many ways.
At the end of the day, linux is not for everyone, but most people who persevere with it, end up preferring it.

---

### Post by SushiR on 2010-03-22
> **unpresedented said:**
> I can do everything with Windows 7 very easily, and without having to use terminal (command prompt) except for rare cases ... plus it is stable (no craches at all) and very fast .. plus, what I can do on Linux ubuntu I can do it easily on Windows 7 !!

Then just why do you use Linux? If Win7 fits your needs, stick with it. There's nothing wrong about that...

---

### Post by ronnielsen1 on 2010-03-22
Excellent post bikeboy! His list of problems surprised me. I didn't have that much trouble in 2004 with linux - let alone now but I'm not a windows power user

---

### Post by carandraug on 2010-03-22
> **unpresedented said:**
> dear all,
I'm a windows power user, I switched to linux ubuntu just before two days, in these two days, I couldn't install a single program correctly (except for something called; wine after it took an hour from me in order to be able to install it), so I found out the following things in the last two days using linux ubuntu 9.10 :
1) installing programs in general is very complicated, it requires terminal many times, I faced things like : add software source then add public key (am i going to hack the whitehouse!!) then sometimes it says there is an error because there is no public key found (although I have provided the right key for it) ... 
some other people say : type something chmod  .. plus some other thing and then you can install any program .. others say : apt-get on terminal ... why all of this headache !!
 
2) installing some hardware drivers is somehow difficult.
 
2.1) system hangs when I try to install some hardware drivers (like dell broadcom wireless card driver) and then all I have to do is press the power button and turn off the machine.
 
3) whenever I try to read tutorials in ubuntu, all of these tutorials requires me to use terminal ... terminal ... terminal ... this is hell !
 
4) it's very hard to fix errors (broken packages for e.g.) , I have to be expert in terminal to do so ... because the graphical option in synaptic (hope I didn't misspelled the word) to fix broken packages does not work (this happened with me and many other users on different machines)
 
5) something vital that I need to test my web pages on, Internet Explorer 8 over Windows 7, I did not find a single tutorial to help me set up IE8 over windows 7 using wine ! you believe it !! two days trying and trying to install that piece of browser (which is consider one of the best browsers) and then ended up with NOTHING ! :(
 
5.5) Linux ubuntu 9.10 does not have a built in rdp protocol, that means I can't log into my windows server using remote desktop unless I install a program that supports it, and 90% of these programs on Linux are considered either buggy or slow, is that right ?
 
I can do everything with Windows 7 very easily, and without having to use terminal (command prompt) except for rare cases ... plus it is stable (no craches at all) and very fast .. plus, what I can do on Linux ubuntu I can do it easily on Windows 7 !!
 
finally, I didn't open this thread to compare linux with windows, I need advice, do you advise me to stay on Linux Ubuntu and forget Windows ? I need somebody to convince me why I should use Linux Ubuntu and leave Windows !! or vice versa ...


1 - This is a common problem from people coming from windows. Did you look in ubuntu software center? It's in the applications menu. Search for applications there, click install and that's it. Installing stuff from other methods is not recommended. Ubuntu has its own repositories exactly to avoid that and other user gently already packaged all for you.

2 - installing modules (drivers in microsoft terminology) if they are nor part of your kernel can be indeed a pain. You have a point here. I usually blame on the manufacturers who don't release modules for linux nor the hardware documentation that would allow users to develop them.

3 - this is very simple to explain and you'll see that it only makes sense to give instructions by the terminal. Linux is about freedom. It's really all about freedom. And you'd be surprised by the ammount of different graphical interfaces you can have. Ubuntu comes with Gnome by default but you could have KDE, Xfce, Lxde, Fluxbox, IceWM (just to name the ones I tried, there's many many more). These are much more than just a different style of colors or organization of menus, they have completely different graphical approaches. Instructions by the command line will always be the same, while graphical ones won't. Also, it's much more easy for me to tell you "sudo apt-get install firefox" than "click on the applications menu in the top left corner. Then click on Ubuntu software center. On the window that just appeared, make sure you have "get free software" selected on the left panel. In the box with the magnifying glass (top right corner of the window) type firefox. Many entries will appear. Now, look for one that says "Firefox web browser" and double click on it. Scroll down and click install. "

4 - you wouldn't have broken packages problems if you didn't try to install stuff outside from the repositories. If you try to install something that has unmet dependencies, then synaptic or aptitude or whatever you choose to use, will install them for you, and remove when they are no longer needed.

5 - what can I say? Microsoft doesn't exactly give a hand when you try to install they software in other operating systems. If you really really need that, I'd rather recommend to have it running inside virtual box

---

### Post by Chame_Wizard on 2010-03-22
> **unpresedented said:**
> dear all,
I'm a windows power user, I switched to linux ubuntu just before two days, in these two days, I couldn't install a single program correctly (except for something called; wine after it took an hour from me in order to be able to install it), so I found out the following things in the last two days using linux ubuntu 9.10 :

1) installing programs in general is very complicated, it requires terminal many times, I faced things like : add software source then add public key (am i going to hack the whitehouse!!) then sometimes it says there is an error because there is no public key found (although I have provided the right key for it) ... 
some other people say : type something chmod  .. plus some other thing and then you can install any program .. others say : apt-get on terminal ... why all of this headache !!
 
1a.Installing software is NOT difficult,use the Ubuntu Software Center/Kpackagekit/Synaptic Manager(gdebi for .deb package files)

1b.Hacking means you understand your computer much better,but the warning was about you were trying to install an PPA,which you only do when you want the newest up to date software.

1c.As for the CLI/Terminal stuff: [http://ubuntuguide.org/wiki/Ubuntu:Karmic]("http://ubuntuguide.org/wiki/Ubuntu:Karmic")


> 
2) installing some hardware drivers is somehow difficult.
 
2.1) system hangs when I try to install some hardware drivers (like dell broadcom wireless card driver) and then all I have to do is press the power button and turn off the machine.

2.Installing hardware drivers is difficult?How about the "Hardware Driver" in the system menu!!!

2.1 Look for the specific hardware driver,1 CLI/terminal access is mostly enough fix it.


> 
3) whenever I try to read tutorials in ubuntu, all of these tutorials requires me to use terminal ... terminal ... terminal ... this is hell !
Well duh,that's the fastest way to do something(instead of the so called  Winblows GUI power user mentality)
 

> 
4) it's very hard to fix errors (broken packages for e.g.) , I have to be expert in terminal to do so ... because the graphical option in synaptic (hope I didn't misspelled the word) to fix broken packages does not work (this happened with me and many other users on different machines)
Fixing broken packages is very easy to fix:```
sudo aptitude safe-upgrade
```,also installing debug symbols/knowing exactly what you are doing helps.


> 
5) something vital that I need to test my web pages on, Internet Explorer 8 over Windows 7, I did not find a single tutorial to help me set up IE8 over windows 7 using wine ! you believe it !! two days trying and trying to install that piece of browser (which is consider one of the best browsers) and then ended up with NOTHING ! :(
 
5.5) Linux ubuntu 9.10 does not have a built in rdp protocol, that means I can't log into my windows server using remote desktop unless I install a program that supports it, and 90% of these programs on Linux are considered either buggy or slow, is that right ?
 
I can do everything with Windows 7 very easily, and without having to use terminal (command prompt) except for rare cases ... plus it is stable (no craches at all) and very fast .. plus, what I can do on Linux ubuntu I can do it easily on Windows 7 !!

Just keep using Winlows 7,if you think that's the best for you,cause not all software are buggy and slow like M$ stuff and 2 days Tux against 12 years of Winblows power user experience mindset is a very stupid way to learn something IMHO.The CLI/Terminal of the Unix family(including the Macs)is a very powerful tool.


> 
finally, I didn't open this thread to compare linux with windows, I need advice, do you advise me to stay on Linux Ubuntu and forget Windows ? I need somebody to convince me why I should use Linux Ubuntu and leave Windows !! or vice versa ...

Before I even used Kubuntu Linux for the first time 3 years ago as a total newbie,I was reading a lot of on line How to's and guides/comparisons,even that I made mistakes about Gnu/Linux.But unlike you,I keep learning a lot of new things these days, start to help out others(since I am now a advanced user for 2 months).


[http://www.howtoforge.com/]("http://www.howtoforge.com/")
[http://psychocats.net/ubuntu/index.php]("http://psychocats.net/ubuntu/index.php")
[http://www.oreillynet.com/linux/cmd/]("http://www.oreillynet.com/linux/cmd/")
[http://www.computerhope.com/unix.htm]("http://www.computerhope.com/unix.htm")
[http://ss64.com/bash/]("http://ss64.com/bash/")
This forum and of course...........[http://en.wikipedia.org/wiki/Linux]("http://en.wikipedia.org/wiki/Linux")

Patience,literacy(a lot of reading/understanding) and don't give up helps a lot(for me at least).:popcorn:

---

### Post by Keith1212 on 2010-03-22
so your saying you had 0 problems the first 2 days you used windows? Thats like driving a car for 12 years and expecting to learn to fly a plane in 2 days. Then you complain that the plane has too many knobs and switches and should be "dumbed down" so anyone can learn it in days.

---

### Post by prodigy_ on 2010-03-22
Belongs to "Testimonials", I believe.

> **unpresedented said:**
> dear all,
I'm a windows power user, I switched to linux ubuntu just before two days, in these two days, I couldn't install a single program correctly (except for something called; wine after it took an hour from me in order to be able to install it)
It gets better when you're used to it. If you didn't know anything about Windows, downloading and installing a program there wouldn't see seem so trivial either.

> **unpresedented said:**
>  installing programs in general is very complicated, it requires terminal many times, I faced things like : add software source then add public key (am i going to hack the whitehouse!!) then sometimes it says there is an error because there is no public key found (although I have provided the right key for it) ... 
Terminal isn't required to install software from repositories. There's Synaptic (System/Administration/Synaptic Package Manager) which is a GUI tool. Software sources/GPG keys can be managed with a GUI tool as well (System/Administration/Software Sources).

The reason why HOWTOs often tell you to use Terminal is because it's usually **simpler and faster** to copy/paste a command from a webpage into teminal window. 

> **unpresedented said:**
> some other people say : type something chmod  .. plus some other thing and then you can install any program .. others say : apt-get on terminal ... why all of this headache !!
Copy-pasting a command is a headache? You don't have to actually type it.

> **unpresedented said:**
> 2) installing some hardware drivers is somehow difficult.
That's valid point. Hardware support is still one of weakest spots of Linux. The situation was **much** worse 2-3 years ago but it's still far from perfect.

> **unpresedented said:**
> Internet Explorer 8 over Windows 7
You could use VirtualBox for that.

> **unpresedented said:**
> 5.5) Linux ubuntu 9.10 does not have a built in rdp protocol, that means I can't log into my windows server using remote desktop unless I install a program that supports it, and 90% of these programs on Linux are considered either buggy or slow, is that right ?
Applications/Internet/Terminal Server Client?

> **unpresedented said:**
> I can do everything with Windows 7 very easily, and without having to use terminal (command prompt) except for rare cases ... plus it is stable (no craches at all) and very fast .. plus, what I can do on Linux ubuntu I can do it easily on Windows 7 !!
Use Windows 7 then.

> **unpresedented said:**
> I need advice, do you advise me to stay on Linux Ubuntu and forget Windows ? I need somebody to convince me why I should use Linux Ubuntu and leave Windows !! or vice versa ...
This depends on what do you want to achieve. If you want to learn *NIX, Ubuntu is a good first step, because it offers the least steep learning curve. Otherwise, if Windows works for you, there's no reason to switch.

---

### Post by unpresedented on 2010-03-22
thank you guys for the prompt response ..
there is a concept in Linux, which new to me, COMPILING ... that's that mean in general ? does it mean intalling something ?

---

### Post by carandraug on 2010-03-22
> **unpresedented said:**
> thank you guys for the prompt response ..
there is a concept in Linux, which new to me, COMPILING ... that's that mean in general ? does it mean intalling something ?

Keep away from that. You are not ready yet. Just install stuff from ubuntu software center.

Compile is to get the source code and make the binarie (the exe file in windows).

---

### Post by mcooke1 on 2010-03-22
If it is only IE8 that you want to use from Windows in your Linux install I would recomend Virtual Box with XP if you have a copy of XP you can use. (By the way rule Number 1 on Linux Forums do not praise Windows.) Good Luck.

---

### Post by johnuk on 2010-03-22
You've had some excellent replies so far, I won't bother trying to better the technical responses, so I will supply some moral support.

I was going to geeky computer clubs from the age of 13, over a decade ago. Now and then, I would have a go at getting Linux going and was always met with problems. I gave up many times figuring "this is just too much effort and for the uber geek".

I've even come on this forum saying "awwwww god dammit, if this doesn't start working today I'm never using it again".

Around a decade later I found Ubuntu and Live CD. 

To cut to the chase, yep, sometimes you'll run into a few annoying problems with a printer or such and such that doesn't work. That aside, I didn't have to configure ANYTHING when installing Ubuntu on a machine this week. I simply dropped into the GUI and everything was working. Quite a change from spending days messing around with network settings in Win 95.

The time of Linux being for the ultra reclusive geek are gone. It WILL take you a few weeks of playing around to get Linux, but it IS worth it. It's so clean running and sensible in how it does things.

**Take heart from the fact that, unlike Windows where you will have to fight to find solutions to things, the majority of guys here really know what they're talking about and will help you out whenever they can; often before you get round to checking your mail for a reply.**

You will be amazed at just how many obscure problems someone else will be able help you with. And when they can't there are bug reporting and tracking systems in place to correct problems in the next update.

So abuse this site. Just remember that repeat questions are common and time consuming, so when you ask a question be 'rude' and put it point blank so people can blast through the chat to the solution. And remember to say thanks.

MCooke is right, VirtualBox is perfect if you want to run the odd thing in Windows. It's a point and click emulator for any OS and it's in Synaptic. You simply tell it how much disk space you want to assign, how much ram and then stick in your XP setup disk. It'll install in a window on your Linux desktop as if it's running on it's own computer. I prefer that to dual boots, which usually cause problems for me and mean I have to drop out of one to get to the other. Oh yea, and my wireless network also required zero setup in the emulated Windows, it just worked straight off, thru Linux and then an emulator.

My advice, ditch IE8. In fact, ditch Firefox as well. I have tried Netscape Navigator, Chrome, IE, Firefox, a bunch of others I've probably forgotten and **Opera** has always come out as the best. Full of features, fast browsing, handles plugins like videos nicely, has a built in mail client...

No one wants to have to put effort in to learn a new OS and Linux seems daunting. But if you're in anyway half computer literate, you'll get it. If it helps, stay on Windows for a while and just muck about in Linux to start with, that's a great way to learn and doesn't involve going cold turkey. I have to agree with the others, expecting to pick up Linux in 2 days is more than optimistic, it's unrealistic. But then it took me months to teach myself aged 10 how to use Windows with any competence, arguably years to know how to deal with network problems and the like.

Once you've got Linux setup how you like it, and despite me not wanting to stereotype Windows with spellings like Windoz, you will start to consider Windows as you do an ugly meth addict hooker.

Soon enough you'll be trying to pass Live CDs off to your friends... "nah! it really is that good!"

Good luck matey

---

### Post by unpresedented on 2010-03-22
> **mcooke1 said:**
> If it is only IE8 that you want to use from Windows in your Linux install I would recomend Virtual Box with XP if you have a copy of XP you can use. (By the way rule Number 1 on Linux Forums do not praise Windows.) Good Luck.
 
it's unreasonable to eat 512 or more of my RAM (running virtual box with windows xp) just to test my web pages on internet explorer 8 !! this issue is driving me crazy
 
sounds you did not read the full original post : i didn't open this post to cmpare windows with linux ...
goodluck for you.

---

### Post by johnuk on 2010-03-22
> **unpresedented said:**
> it's unreasonable to eat 512 or more of my RAM (running virtual box with windows xp) just to test my web pages on internet explorer 8 !! this issue is driving me crazy
 
sounds you did not read the full original post : i didn't open this post to cmpare windows with linux ...
goodluck for you.

Hey now... no fighting, only love on the Ubuntu forum:

[http://www.wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html](http://www.wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html)

Hope that's more of a help :popcorn:

---

### Post by Hikayu on 2010-03-22
> sounds you did not read the full original post : i didn't open this post to cmpare windows with linux ...
goodluck for you.

Actually, (I'm being kind here)

Never praise Windows in ANY Linux forums. You'd get alot more help that way.
Listen, it's difficult for a Windows (particularly *power* users) to switch to Linux.

We could help. But Linux is **The** most well-documented OS in the world. Any problems you have can be found on the web. Also, we dislike people who just CANT use Linux.

Use Google.
If you can't find it, this is your stop. We're more than glad to help.

And btw, you're suffering from the "*X-effect*" where you miss Window's features. Imagine a car and a bus. The bus is easier to utilize. But it sucks. A car is harder. But it's alot more versatile.

Good luck using Linux. I hope you survive. ;)

---

### Post by unpresedented on 2010-03-22
> **johnuk said:**
>  
 
**Take heart from the fact that, unlike Windows where you will have to fight to find solutions to things, the majority of guys here really know what they're talking about and will help you out whenever they can; often before you get round to checking your mail for a reply.**
 
 
thank you Mr. johnuk for your kind reply. I'm not talking about Window 95, I'm talking about Windows 7 that does not crach except for some rare cases .. no problems at all...
but again, a lot of people here asks : why not you stick with windows ??
the answer is : a lot of people told me linux is better !! 
but until now (48 hours - semi continuous reading about linux) windows is easier and better !!
 
> **johnuk said:**
>  
MCooke is right, VirtualBox is perfect if you want to run the odd thing in Windows. It's a point and click emulator for any OS and it's in Synaptic. You simply tell it how much disk space you want to assign, how much ram and then stick in your XP setup disk. It'll install in a window on your Linux desktop as if it's running on it's own computer. I prefer that to dual boots, which usually cause problems for me and mean I have to drop out of one to get to the other. Oh yea, and my wireless network also required zero setup in the emulated Windows, it just worked straight off, thru Linux and then an emulator.
 
 
I run my internet explorer 8   24 hours  a day so it's unreasonable to keep that virtual box opened (killing a huge part of the RAM) .. is there a real solution to this dilemma which drives me crazy ..
 
> **johnuk said:**
>  
My advice, ditch IE8. In fact, ditch Firefox as well. I have tried Netscape Navigator, Chrome, IE, Firefox, a bunch of others I've probably forgotten and **Opera** has always come out as the best. Full of features, fast browsing, handles plugins like videos nicely, has a built in mail client...
 
I'd love doing that .. but 0% of my clients worldwide use Opera .. they use either firefox or IE 8 ...
 
> **johnuk said:**
>  
Soon enough you'll be trying to pass Live CDs off to your friends... "nah! it really is that good!"

what is live CD about (in general) ?
thanks in advance ..

---

### Post by e-Gee on 2010-03-22
You are not power user, power user would figure out for two days that there is software center in ubuntu or synaptic and that Linux is different platform with different apps and works different than windows, that is like you switch from Android to iPhone and say that iPhone is bad because can't run your Android apps . You have to learn a lot to become power user !!

---

### Post by unpresedented on 2010-03-22
> **johnuk said:**
> Hey now... no fighting, only love on the Ubuntu forum:
 
[http://www.wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html](http://www.wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html)
 
Hope that's more of a help :popcorn:
 this one is for windows xp !! by the way, i opened a thread for that !! there are no tutorials for the case of windows 7 .. thanks anyway ...

---

### Post by unpresedented on 2010-03-22
> **e-Gee said:**
> You are not power user, power user would figure out for two days that there is software center in ubuntu or synaptic and that Linux is different platform with different apps and works different than windows, that is like you switch from Android to iPhone and say that iPhone is bad because can't run your Android apps . You have to learn a lot to become power user !!
 
and who said that (not knowing about each single sub menu in Linux ubuntu) ?

---

### Post by johnuk on 2010-03-22
> I run my internet explorer 8   24 hours  a day so it's unreasonable to keep that virtual box opened (killing a huge part of the RAM) .. is there a real solution to this dilemma which drives me crazy ..

I'd love doing that .. but 0% of my clients worldwide use Opera .. they use either firefox or IE 8 ...

Got ya, and understandable regarding the RAM. This might take a little more messing around, but:

[http://www.wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html](http://www.wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html)

WINE is an acronym for 'WINE Is Not an Emulator'. It provides all the library files within Linux for windows applications to run from, rather than truly emulating another whole set of hardware.

> 
what is live CD about (in general) ?
thanks in advance ..

The thing you probably installed your copy of Linux with. It boots Ubuntu into the RAM and lets you try it out without installing it.

---

### Post by johnuk on 2010-03-22
Wow, replies are coming thick and fast now, so sorry if I double posted while you were replying.

First of all, can we stop the bitching and arguing, that's not the linux way is it... and it hasn't solved his problem

Do you HAVE to run Win 7 or do you just need to test your pages in IE8?

---

### Post by unpresedented on 2010-03-22
> **johnuk said:**
> Got ya, and understandable regarding the RAM. This might take a little more messing around, but:
 
[http://www.wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html](http://www.wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html)
 
WINE is an acronym for 'WINE Is Not an Emulator'. It provides all the library files within Linux for windows applications to run from, rather than truly emulating another whole set of hardware.
 
 
 
The thing you probably installed your copy of Linux with. It boots Ubuntu into the RAM and lets you try it out without installing it.
 
 man this tutorial does not describe the case of windows 7 !! I do not want widnows XP anymore

---

### Post by auh2o on 2010-03-22
>  installing programs in general is very complicatedThat's funny. I used Windows for 18 years before switching over to Linux, and I found that installing new programs was even easier, more convenient and intuitive than on Windows. And the instances where you *need* to use the terminal are actually rather rare. Most often there will be a GUI alternative. If I agree with you on one thing as a long-time Windows user, it is that I loathe the terminal. I will always strive not to have to use it.

I may have been a Windows "power user", but in my opinion Windows 7 has nothing on the current main Linux distros, except of course larger 3rd party support; but that isn't the fault of the OS itself. And by switching to Linux I too am helping to change that! Linux is a much more intelligently built OS. Just getting rid of the godawful Windows registry, the horrible NTFS file system, and all the security holes and viruses is reason enough to ditch Windows and never look back. There are Linux programs for pretty much your every need, and if there isn't, there's always Wine or VirtualBox. You will have to learn your way around the new OS of course, but that would be the case if you had spent 12 years on Linux and switched over to Windows as well. It doesn't have to take too long, but it's well worth the investment.

I'm keeping a copy of Windows 7 on my drive for now, but the instances where I actually choose it in Grub are very rare. And I doubt I will ever even bother to install Windows 8. Having used Windows since 3.1 I feel like I'm finally free!! :P

---

### Post by unpresedented on 2010-03-22
> **johnuk said:**
> Wow, replies are coming thick and fast now, so sorry if I double posted while you were replying.
 
First of all, can we stop the bitching and arguing, that's not the linux way is it... and it hasn't solved his problem
 
Do you HAVE to run Win 7 or do you just need to test your pages in IE8?
 
I need to test my page in firefox and IE 8 (using Windows 7); because : there is no single PC here got windows xp installed on, do not tell me to download or buy a new windows xp CD and install it somewhere to take the DLLs for the sake of the tutorial ... 
thank you for the link anyway ....

---

### Post by Hikayu on 2010-03-22
Ok :

In short : Learn the terminal.

Know that and you have COMPLETE control over Linux. That's when you can utilize Linux's raw power.

---

### Post by Grenage on 2010-03-22
Linux life is generally easy, once you fully realise that Linux is not Windows in any shape or form - and that Windows applications are just that.

If you run Linux with the assumption that you can run MS apps (IE, in this case) _and_ you are not happy with alternatives - **walk away**.

Someone who has never used a computer before would probably find Debian/Ubuntu as easy as Windows, at least initially.  Long term, I believe Linux is more manageable; I find it more logical.

---

### Post by nikhilbhardwaj on 2010-03-22
> **unpresedented said:**
> man this tutorial does not describe the case of windows 7 !! I do not want widnows XP anymore

are you sure you're a power user.

what has windows 7 got to do with testing a web page.
you want IE8.

install IE8 with wine.
(you wont install either windows xp or windows 7 to install IE)
the idea is that wine emulates windows applications and can run windows executables 

so your crying about win xp/7 makes absolutely no sense, atleast not to me.

one more thing
you really dont seem keen to learn about linux and need windows apps
so you'd be better of using windows, if however you change your mind we'd be glad to help.

---

### Post by lotharmat on 2010-03-22
After reading this thread and watching it develop; I have come to a few conclusions:

[LIST]
[*]Your friend who said that Linux was better than windows should have added the caveat - 'for me'
[*]It seems that you have tried Ubuntu and not got on with it. - Cut your losses and keep Windows 7
[*]There are a few linux zealots posting in this thread who refuse to contemplate the fact that windows could be better at some things than linux
[/LIST]

Remember - It has taken you 12 years to become a 'power user' with windows. You will not learn ubuntu / linux overnight (or even over two nights :wink: )

Personally I'd recommend dual booting Ubuntu with Windows, use windows to get the things done that you need to get done and log into Ubuntu to learn it.

---

### Post by Riffster on 2010-03-22
Welcome to the linux community.

I'm a windows and a linux user. Both have their places (which some might see as a controversial statement, but meh) and both do stuff. 

I use 2 flavours of Linux so far, Ubuntu and Fedora. 

If you've learned to be a Windows power user then you've obviously got teh ability to learn stuff, and you *will need to learn stuff to get the most out of Linux.* 

For me, that's part of the enjoyment. It's tricky and frustrating at times sure, but it's rewarding and generally the community is very helpful. 

Don't expect to run before you can walk and enjoy the learning curve.

---

### Post by johnuk on 2010-03-22
righty ho, dual boot?

depends how confident you are with coding and how regularly you need to check them in IE.

personally, when I was using dreamweaver I wasn't particularly great at it and would be pressing f12 every few minutes.

if you're good enough that you only need to check them once or twice before sending them off to the client, dual boot might be fine for you.

if you need to code and repeatedly check your work in something like dreamweaver and IE8 then I'm afraid my ability to help starts expiring around this point, as neither are native to linux.

i don't know what you use to code with, there may be a native solution in linux you could move to.

but as i say, how to go about the IE problem is all down to how regularly you test. 

if it's not all the time, burning up some ram using virtual box wouldn't be an issue, as it'd just be to check the thing was working. but I can understand if you were doing coding and graphical work and didn't want to loose all your ram in emulation

my next suggestion, if none of the above is of any help, is to ask more specific groups of users, remembering we're just chatting general problems. you may get what you're after by asking people more dedicate to web design who also use linux. i use it, and have done a bit of design, but would never say I'm an expert on merging the two

---

### Post by unpresedented on 2010-03-22
> **nikhilbhardwaj said:**
> are you sure you're a power user.
 
what has windows 7 got to do with testing a web page.
you want IE8.
 
install IE8 with wine.
(you wont install either windows xp or windows 7 to install IE)
the idea is that wine emulates windows applications and can run windows executables 
 
so your crying about win xp/7 makes absolutely no sense, atleast not to me.
 
one more thing
you really dont seem keen to learn about linux and need windows apps
so you'd be better of using windows, if however you change your mind we'd be glad to help.
are you sure that you understand english ?
the tutorial requires me to grab some DLLs from a windows XP installation, which is NOT available here for now ..

---

### Post by Hikayu on 2010-03-22
> **unpresedented said:**
> are you sure that you understand english ?
the tutorial requires me to grab some DLLs from a windows XP installation, which is NOT available here for now ..

Ahem, we have winetricks.

Type:
```

wget http://www.kegel.com/wine/winetricks
```

Then change it's permissions:

```
sudo chmod 775 winetricks
```

After that:

```
./winetricks
```


And install whatever dlls you need.

---

### Post by unpresedented on 2010-03-22
> **Hikayu said:**
> Ahem, we have winetricks.
 
Type:
```

wget http://www.kegel.com/wine/winetricks
```
 
Then change it's permissions:
 
```
sudo chmod 775 winetricks
```
 
After that:
 
```
./winetricks
```
 
 
And install whatever dlls you need.
thank you Hikayu for this important reply .. i will review it once i get back home and reboot my machine into ubuntu ...

---

### Post by unpresedented on 2010-03-22
thank you guys for your kind replies (noticed some unrespectful phrases from some users here) ... 
**@johnuk** yes it keep testing web pages every second on IE 8; but it's not the issue here, i will re-open my dead thread about this thing later. (i use Zend Studio to develop php pages and this editor is natively supported in linux) ..
 
> **auh2o said:**
> That's funny. I used Windows for 18 years before switching over to Linux, and I found that installing new programs was even easier, more convenient and intuitive than on Windows. And the instances where you *need* to use the terminal are actually rather rare. Most often there will be a GUI alternative. If I agree with you on one thing as a long-time Windows user, it is that I loathe the terminal. I will always strive not to have to use it.
 
I may have been a Windows "power user", but in my opinion Windows 7 has nothing on the current main Linux distros, except of course larger 3rd party support; but that isn't the fault of the OS itself. And by switching to Linux I too am helping to change that! Linux is a much more intelligently built OS. Just getting rid of the godawful Windows registry, the horrible NTFS file system, and all the security holes and viruses is reason enough to ditch Windows and never look back. There are Linux programs for pretty much your every need, and if there isn't, there's always Wine or VirtualBox. You will have to learn your way around the new OS of course, but that would be the case if you had spent 12 years on Linux and switched over to Windows as well. It doesn't have to take too long, but it's well worth the investment.
 
I'm keeping a copy of Windows 7 on my drive for now, but the instances where I actually choose it in Grub are very rare. And I doubt I will ever even bother to install Windows 8. Having used Windows since 3.1 I feel like I'm finally free!! :P
 
this is a cool reply .. but what do you mean by :".. but in my opinion Windows 7 has nothing on the current main Linux distros, except of course larger 3rd party support; but that isn't the fault of the OS itself. .." .. ?!?!

---

### Post by DrMelon on 2010-03-22
Unpresedented, please help me to understand you - use a spellchecker, and proper grammar - it is hard for me to give you any help if I cannot understand what you are trying to say.

---

### Post by unpresedented on 2010-03-22
> **DrMelon said:**
> Unpresedented, please help me to understand you - use a spellchecker, and proper grammar - it is hard for me to give you any help if I cannot understand what you are trying to say.
simply: I want good reasons to switch from windows to linux as a lot of people advise me to do so . 
but do not answer like this : linux is more flexible, more intuitive, more .. more ...
be more specific .. 
thank you in advance ...

---

### Post by my_wan on 2010-03-22
I agree with the OP. I'm sticking with it and not going back to windows. Yet the desktops and GUIs suck out of the box. TreeLine, using exec, has been a far more valuable GUI than any GUI I've found yet. I feel for you unpresedented.

Yes GUIs can be done as well and better on Ubuntu than in windows even. Yet even most GUIs on Ubuntu expect you to use the keyboard, and implement GUI strategies that are too rigid. Even addon programs like Geeqie, which I'm working on the source to fix, in which a nearly perfect implementation was entirely ruined in less than 10 lines of source code. Never used it in windows because it simply failed to be usable with a mouse. People say learn it. Well duh, then quit advertising as a user friendly desktop GUI environment.

The stupidity of most of the GUI stuff on Ubuntu boggles my mind. I'm sticking with it because Ubuntu has provided an environment where I can develop a GUI to my satisfaction, as I go down this learning curve.

Yes I understand why the CL is so much more useful giving instructions on the internet, and more powerful in general. Same is true in windows to only a somewhat lesser extent. Yet out of the box it's just plain silly to ask people to try this desktop centric Ubuntu then rail about complaints of people having trouble with the CL. Much of it I think can be chalked up to programmers being keyboard centric, even when a few clicks could do the same thing.

---

### Post by Hikayu on 2010-03-22
> **unpresedented said:**
> simply: I want good reasons to switch from windows to linux as a lot of people advise me to do so . 
but do not answer like this : linux is more flexible, more intuitive, more .. more ...
be more specific .. 
thank you in advance ...

No problem :

Actually. Big problem. The " linux is more flexible, more intuitive, more .. more ..." is the *simplest* way to explain. Are you sure you want 100 pages of advantages?

---

### Post by philinux on 2010-03-22
> **lotharmat said:**
> 
Remember - It has taken you 12 years to become a 'power user' with windows. You will not learn ubuntu / linux overnight (or even over two nights :wink: )

[COLOR="Red"]**Personally I'd recommend dual booting Ubuntu with Windows, use windows to get the things done that you need to get done and log into Ubuntu to learn it.**[/COLOR]

+1 good advice.

---

### Post by Hikayu on 2010-03-22
> **lotharmat said:**
> 
[COLOR="Red"]Personally I'd recommend dual booting Ubuntu with Windows, use windows to get the things done that you need to get done and log into Ubuntu to learn it.[/COLOR]

Agreed
+ 2 for advice.

UbuntuForums should implement voting for replies. The way YouTube does it.

---

### Post by Jose Catre-Vandis on 2010-03-22
Web design is a PITA, which ever platform you work from, epseciaslly if you need to test all browsers, even if your code is compliant.

I eventually ended up working on an XP laptop, checking IE7 and Firefox (Windows), then also running a desktop with Windows for IE8/9 and a virtual machine for Linux Firefox. ( I do all my coding by hand, using Geany in XP)

If your only compliant need is IE8, I would recommend you stick with Windows as your platform.

To answer your query about why switch to Linux, for me it is about a state of mind, a need and willingness to learn, a need to have more control and access over your OS, and the ability to do things you can't do in Windows.

I have just spent the last few weeks trying to get Windows 7 to do all the things I can do in Xubuntu, but the 80% / 20% rule seems to kick in. No doubt its much the same the other way round.

---

### Post by johnuk on 2010-03-22
Right, I'm bailing out on this discussion as, like I say, there are people here better qualified to help you with the specifics of DLLs and WINE. And equally important, my inbox is getting hammered with replies. :p

There WILL be other web designers who've solved the problems you're having. It's simply a matter of finding the gimps - gimp in the most respectable way of course (all hail the gimp!)

No fighting people

---

### Post by hsoulen on 2010-03-22
Unprecedented,

You have asked for reasons to switch from Windows to Linux but I am not sure you have a reason to do this.

You began your thread with several reasons why you prefer Windows to Linux, including support for Internet Explorer, why blame Linux for why you cannot use a proprietary browser? If Microsoft wanted you to use IE8 on Linux they would release a port for just that purpose.

You obviously prefer Windows 7 to Linux and there is absolutely nothing  wrong with that if you like it and it does what you need stick to Windows! But do yourself a favor and keep a dual-boot with Ubuntu on it, keep playing and who knows maybe one day you will be a convert?

The only piece of advice I can offer is this: Ask questions frequently and the community will answer (we all look out for each other here) but please refrain from comparing alternate operating systems to Linux as we are here to help you with Linux not to compare apples to steak.

To the community, well done. Great advice and way to keep your cool. Makes me proud to be a member of the "terminal" club.

Hank.

---

### Post by johnuk on 2010-03-22
> **Hikayu said:**
> Agreed
+ 2 for advice.

UbuntuForums should implement voting for replies. The way YouTube does it.

and a means of saying thanks and giving people respect points for help, as i've seen elsewhere. unless i'm just missing the button on here. but now im thread jacking, so pm me if such a button does exist, and i'll click it for the first to reply

negative replies will receive abuse... j/k'ing :p

---

### Post by auh2o on 2010-03-22
> **unpresedented said:**
> this is a cool reply .. but what do you mean by :".. but in my opinion Windows 7 has nothing on the current main Linux distros, except of course larger 3rd party support; but that isn't the fault of the OS itself. .." .. ?!?!

What I mean is that the reason that there are more drivers and more hardware support for Windows than for Linux (though the gap is slowly closing) is not that Windows is necessarily a better OS from an objective standpoint - simply that it has a bigger user base. The reason for that is of course debatable, but I chalk it up more to Microsoft's business tactics than to quality of coding.

---

### Post by quinnten83 on 2010-03-22
> **mcooke1 said:**
> (By the way rule Number 1 on Linux Forums do not praise Windows.) Good Luck.

I think I missed that memo.
I also think this is either serious flamebait, or a seriously uninformed user jumping in waaaaaaaaaay to deep without learning how to swim and then complaining that the ocean is so deep. 
Either very annoying. Sorry if I am being too blunt.
Also him saying he can't install software, I wonder if he is not trying to doubleclick on a .exe file....
Anyway... on to more interesting things.

---

### Post by quinnten83 on 2010-03-22
> **lotharmat said:**
> 

[LIST]

[*]There are a few linux zealots posting in this thread who refuse to contemplate the fact that windows could be better at some things than linux
[/LIST]



I think plenty of people here keep telling him to stick to windows because it fulfills his needs...

I do feel that the OP is becoming a bit too snarky as the thread progresses.
I don't think anybody will want to help him of he keeps like this.

---

### Post by 2hot6ft2 on 2010-03-22
> **unpresedented said:**
> 
plus it is stable (no craches at all)
Everyone has already made great comments on everything else so to this I'll add that although I have only used win 7 a few times I have been the proud recipient of the glorious blue screen of death twice so far in win 7. Where's all that stability?
Matter of fact just yesterday I was searching for a file using file finder in win 7 and the file finder crashed.

If you prefer win 7 then use it. I've been considered a windows power user for about 30 years and I love Ubuntu and I love learning more about it and how it works.

P.S. Have you enabled God Mode on win 7 yet? What am I thinking if you're a power user of course you have.

---

### Post by unpresedented on 2010-03-23
thank you guys for your replies ... I really appreciate your efforts to write down some important things about Linux Ubuntu ...
from the other side, server side, also a lot of people say : Linux has the best server operating system distributions, much better than Micorosft windows server, and Linux servers do run the biggest 5 super computers in the globe, is that also right ?

---

### Post by Chronon on 2010-03-23
> **unpresedented said:**
> I need to test my page in firefox and IE 8 (using Windows 7); because : there is no single PC here got windows xp installed on, do not tell me to download or buy a new windows xp CD and install it somewhere to take the DLLs for the sake of the tutorial ... 
thank you for the link anyway ....

You can use [this site](http://browsershots.org/) to show the rendered version of any URL.  I don't know if this is sufficient for your needs, but perhaps it lessens your need to have another OS just to run IE8.

---

### Post by Chame_Wizard on 2010-03-23
> **Chronon said:**
> You can use [this site](http://browsershots.org/) to show the rendered version of any URL.  I don't know if this is sufficient for your needs, but perhaps it lessens your need to have another OS just to run IE8.

Nice site(bookmarked).:P

---

### Post by Tom.Gee on 2010-03-23
12 years using windows? My how Windows has changed over the past 12 years or so...  Just try to picture how much more advanced Ubuntu and other Linuxes will become over the next 12 years?  Keep your Win 7 system.  It works happily for you.  Keep an Ubuntu on the side and give yourself the opportunity to learn and grow with it as you obviously have in Windows over the years. I find it funny that you mention the Terminal / CLI.  Being a windows power user myself I just had the opportunity to comment on the CLI in another thread: [http://ubuntuforums.org/showthread.php?p=9005221#post9005221](http://ubuntuforums.org/showthread.php?p=9005221#post9005221)   I have yet to meet the windows power user that doesn't find himself on the command line daily.  Just remember how often you've used "C:>Copy CON: ClickMe.htm" to write a quick and dirty web page.  We all do it.  Surely you underestimate your own use of the command line.  That coupled with the fact that Linux command lines look very alien to Windows power users could put you off to their use.  Learn them the way you learned the windows command prompt - one command at a time, one switch at a time.

---

### Post by egalvan on 2010-03-23
> **mcooke1 said:**
> (By the way rule Number 1 on Linux Forums do not praise Windows.) Good Luck.

> **Hikayu said:**
> Actually, (I'm being kind here)

Never praise Windows in ANY Linux forums. You'd get alot more help that way.

Actually, *nix geeks admire **any** piece of well-written code.
No matter where it's from.
No true *nix user would refuse to help a newbie just because said newbie also liked Windows.

> 
Also, we dislike people who just CANT use Linux.

No, we dislike people who just **cant** be open-minded, or who 
make assumptions before getting all the facts.
Or who refuse to help themselves.

see this link for a far-better explanation...
[http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html)

And this link has been refered to, but here it is again...

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)


> Good luck using Linux. I hope you survive. ;)

+1

---

### Post by prodigy_ on 2010-03-23
> **Grenage said:**
> Linux life is generally easy, once you fully realise that Linux is not Windows in any shape or form - and that Windows applications are just that.

If you run Linux with the assumption that you can run MS apps (IE, in this case) _and_ you are not happy with alternatives - **walk away**.

Someone who has never used a computer before would probably find Debian/Ubuntu as easy as Windows, at least initially.  Long term, I believe Linux is more manageable; I find it more logical.
The problem with Ubuntu is that it offers no middle ground for the so-called power users. The learning curve starts out nearly flat (as long as you're happy with your default apps package) but as soon as you want to do anything advanced, you suddenly need to be a pro. You need to be comfortable with CLI and you need to know exactly what you're doing.

So you're right, short-term it's nice and long-term it's nice. But when you're already more than a newbie but still less than a geek, Linux (including Ubuntu) is a nightmare

---

### Post by kelvin spratt on 2010-03-23
Windows7 is a fine OS the best to date from Ms, I have it on Several Comps I also have Linux on every comp as well the problem is win7 only gets used to get updates. and the occasional thing we can't do in Linux. I use a little firefox app  called "default user agent"  to make Firefox complaint with ie. It may not help you but it does help me. You could also use Ubuntu in "wubi" that way you use Ubuntu as a program in win7 and test it out that way you can then just delete it when you are fed up or duel boot

---

### Post by anantshri on 2010-03-23
My concious will not let me say this being one of the linux fanboys.

but my brain says that you are right prodigy_ the learning curve is straight out flat.

the concern here is there should be some easy way to add more repository something like suse installer links or getdeb apt_url in ubuntu website. which let you install pacakges by browsing website. and attempt to search any unknown package can also search the same in ubuntu repo and report it in synaptic.

also i used to refer a unofficial list of apt repo's sometimes back when i used to work on debian. i think a simillar application providing this kind of info coupled with user rating system can help easing the software installation.

Seems like a Good Idea Off to post the same at brainstorm section.

as far as OP's concern are there. 

I would also suggest dual boot and i agree that at times windows do things nicely which should be done in linux too.

IE8 for Windows XP or for Windows 7 i don't think will make any difference. and ya wine tricks and simmialr tools definetely make the life lot easy and if you find it difficult to work it this way then at any point you  can purchase codeweaver crossover office to get things going in point and click format.

---

### Post by Grenage on 2010-03-23
> **prodigy_ said:**
> So you're right, short-term it's nice and long-term it's nice. But when you're already more than a newbie but still less than a geek, Linux (including Ubuntu) is a nightmare

You wrote that better than I. :)

I do remember the interim period (I'm arguably still in it), and it can require a lot of effort.  I think a user could get away with just using the package manager and staying out of the terminal, but they would be using their computer in a very basic way.  Those kinds of people are probably already using macs, and I don't mean that in a derogatory way.

---

### Post by unpresedented on 2010-03-23
> **Hikayu said:**
> Ahem, we have winetricks.

Type:
```

wget http://www.kegel.com/wine/winetricks
```Then change it's permissions:

```
sudo chmod 775 winetricks
```After that:

```
./winetricks
```And install whatever dlls you need.
I done what you wrote here .. but I only see ie6 and ie7 but not the one i need (ie 8 .. can you help me to install it .. thank you in advance. ..

---

### Post by El_Shrander on 2010-03-23
> **prodigy_ said:**
> So you're right, short-term it's nice and long-term it's nice. But when you're already more than a newbie but still less than a geek, Linux (including Ubuntu) is a nightmare

I guess I'm still on the newbie phase, but I have the feeling I could stay like this forever, if it so suited me. I use a maximum of ten applications (email, internet browser, text editor, music, etc., nothing fancy), and I don't foresee any immediate need for more. My computer runs impeccably and doesn't give me any trouble unless I ask for it (installing stuff I don't really know what's about, messing with folders locations just for the sake of it, etc.).

In a life worth of using Windows, my experience would never stop growing more and more vexing and frustrating, to the point where I just had to bail out. While using my same ten applications (or their Windows equivalents), there was always something being installed in the background without my acquiescence, or uninstalled, or relocated, or just plain corrupted... by whom or what, I guess I'll never find out now.

I was never a power-user in Windows, and most likely I will never be one in Linux either, but at least with Linux I know I can play it small and still be happy for as long as I want.

---

### Post by dosox on 2010-03-23
It took me at least a week to get the taste of Ubuntu. So stay longer.. I don't know any commands.. all i do is search the net & copy paste it in the terminal :D and that's how I'm learning more.

---

### Post by MoarningSun on 2010-03-23
I also tried Ubuntu for some time and I really liked to play around with it. I preffer it over windows especially because it's open-source, free and very customizable. But I wanted to use the 'official' Live Messenger client from microsoft, because the clients on Ubuntu couldn't do photo sharing and fast file transfer or were stupendously ugly (aMSN).. So I'm back to windows xp's ancient logic again:D (that is untill the clients like emesene or msn-pecan have improved enough to give it another try)

It's the same in your case. Most of the issues you're having could be dealt with if spent enough time on, but the problem really is IE8, which you need specifically. Others already mentioned ways to test on IE8 when on Linux, but if those don't cut it, you'd probably be better off with windows (for now at least).

Offcourse these problems would disapear if everyone would just start to use unix stuff or similar, but that day is not in the near future it seems......

---

### Post by pcjunkie on 2010-03-23
aMSN has themes that make it look 1000 times better, also it does do file transfer. If you want to get nuts and bolts with it and hit the XML style sheet and really make it look wicked...


Stay with it, I was the same. I used Amiga then Win4 then win 95 until I found Ubuntu even after experimenting with other installs. 

I have not gone back, not once!

I have XP slaved on a second PC and also in VM for quick docx or PSD edits.
(So yes I still use windows but not as the main pc. Windows does not connect to the Internet here, not for a second).

I also have OSX running but thats another story unto itself. 

I find installing Ubuntu (any debian flavour) is really easy. In the space of 6 hours I can wipe my PC, start clean and have everything I use up and running again with ease. If you use synaptic and simply search for what you need you can tick boxes all day long and then when you are done, press install. Go make coffee and chat on the phone. Come back and you are ready to go. Windows can't do that! It never will do that. Apple and linux - Linux in particular do do that (app store). 

I find that by the time I install the chipset drivers for windows, Ubuntu has already updated and I am searching synaptic. By the time I have word in Windows, synaptic has finished and my PC is ready to go..
In Windows I still need to install VM, photoshop, antivirus etc etc etc...

And there is the thing of CD keys...my pet hate, do you have a collection? I did. What about those yearly subscriptions that milk your bank account from time to time. Add it all up! See how much windows really costs for a year.

Now consider that time hours paid, then consider how much you will save using open source. If that time required to learn a new OS is less than what you would get paid in time on a job then you have saved money and gained an insight into how an OS really works. Once you know these things, they are not hard, you will be free from subscriptions and advertised "computer fix alls" forever..

Follow what Yoda said. Unlearn what you have learned, do or do not! There is no try...

[[IMG]http://img687.imageshack.us/img687/576/35163179.th.jpg[/IMG]](http://img687.imageshack.us/i/35163179.jpg/)

Anything is possible.

---

### Post by Mark Phelps on 2010-03-23
> **unpresedented said:**
> I done what you wrote here .. but I only see ie6 and ie7 but not the one i need (ie 8 .. can you help me to install it .. thank you in advance. ..

Nearly 60 posts, and pages of responses, from folks all trying to help you .. and all you can do with all of that is whine about not finding IE8!

OK ... soapbox mode ON:

MS makes a point of NOT sharing their internals with the rest of the computing community, so developers in outfits like CodeWeavers have to guess the best they can when trying to implement an environment in Linux that will run SOME MS Apps. Personally, I think they have done an amazingly good job given the difficulty of what they have to do.

Notice that word -- SOME.  

Linux will NEVER run ALL MS Widows apps; there will always be newer versions of MS Apps that will not work with Wine, or Crossover, or whatever other "emulator" you choose to run.

We're not here to provide you a free version of MS Windows; we're here to provide you a free Alternative to MS Windows. 

So, I'll be blunt -- if you need bleeding edge MS Windows stuff (like IE v8 ), STAY with MS Windows -- or come over to Linux and learn to use Alternatives.

OK -- soapbox mode OFF.

---

### Post by e24ohm on 2010-03-23
Stick with a distro you like, and work/learn it. I am having a hard time right now, becuase I am trying to learn Fedora Core, and everything is called something different, from what it is called in Ubuntu.

Some items are the same, but so much more is different, and in different locations.

2 days is not enough time to learn Linux or anything about it. Try to build and use the machine for something in a production environment. For example: I am running a mysql/php server for Drupal, which is hosting my home intranet on it.

Soon i will be playing with sendmail/postfix or even Zimbra to build a mail server.
//
you might want to start out with something small like a SAMBA server, and connect it to your local LAN, and share files/folders up to your Windows machines.

---

### Post by e24ohm on 2010-03-23
> **pcjunkie said:**
> aMSN has themes that make it look 1000 times better, also it does do file transfer. If you want to get nuts and bolts with it and hit the XML style sheet and really make it look wicked...


Stay with it, I was the same. I used Amiga then Win4 then win 95 until I found Ubuntu even after experimenting with other installs. 

I have not gone back, not once!

I have XP slaved on a second PC and also in VM for quick docx or PSD edits.
(So yes I still use windows but not as the main pc. Windows does not connect to the Internet here, not for a second).

I also have OSX running but thats another story unto itself. 

I find installing Ubuntu (any debian flavour) is really easy. In the space of 6 hours I can wipe my PC, start clean and have everything I use up and running again with ease. If you use synaptic and simply search for what you need you can tick boxes all day long and then when you are done, press install. Go make coffee and chat on the phone. Come back and you are ready to go. Windows can't do that! It never will do that. Apple and linux - Linux in particular do do that (app store). 

I find that by the time I install the chipset drivers for windows, Ubuntu has already updated and I am searching synaptic. By the time I have word in Windows, synaptic has finished and my PC is ready to go..
In Windows I still need to install VM, photoshop, antivirus etc etc etc...

And there is the thing of CD keys...my pet hate, do you have a collection? I did. What about those yearly subscriptions that milk your bank account from time to time. Add it all up! See how much windows really costs for a year.

Now consider that time hours paid, then consider how much you will save using open source. If that time required to learn a new OS is less than what you would get paid in time on a job then you have saved money and gained an insight into how an OS really works. Once you know these things, they are not hard, you will be free from subscriptions and advertised "computer fix alls" forever..

Follow what Yoda said. Unlearn what you have learned, do or do not! There is no try...

[[IMG]http://img687.imageshack.us/img687/576/35163179.th.jpg[/IMG]](http://img687.imageshack.us/i/35163179.jpg/)

Anything is possible.
wow Amiga...I went from the C-64 to the Amiga back in the early 90s....nice to see one else used Amiga....

Cheers!!!

---

### Post by nothingspecial on 2010-03-23
@ unpresedented

I see where you are coming from entirely. I started with linux and have tried windows on a number of occasions. I have given up each time.

I even bought a new computer this week with both vista and windows 7 pre-loaded. It lasted 2 days. It now runs 2 flavours of linux.

I`m not linux power user, but it`s all I know and windows just confuses the hell out of me.

It seems to me that you need windows to do your job, so stick with it.

Maybe use Ubuntu as a hobby if that sort of thing interests you, but like someone has said before, don`t try to make a car fly. You might manage it but you wont get much else done in the mean time.

---

### Post by pcjunkie on 2010-03-23
Amiga......sigh...an OS way ahead of its time..

I loved that thing, rendering 3d through an app off a tape drive. lol..

64kb and I could render 3D in 16 bit colour. 

It took windows 7 years to do that and Apple 5..

---

### Post by Irihapeti on 2010-03-23
Saying that "Linux/Ubuntu is better" is too generalised.

I like to ask, "How, specifically, is it better? Better for whom? Better for what?"

If the answers don't satisfy or make sense to you, then there should be no shame in not trying it.

No one has unlimited time, and if trying Linux isn't that important, then I see no problem in leaving it alone.

I see this as one of the big problems with zealotry in any field. You have people doing something because someone else said it was a good idea, but they themselves aren't quite sure what they think about it.

I say make a decision, and unless it directly affects other people, never mind what anyone else says.

---

### Post by pcjunkie on 2010-03-23
It really boils down to what you need as tools and what OS those tools run on but its not a limitation. 

I love my Ubuntu but I have no choice but to use windows for Adobe and only for Adobe. Having said that windows does not connect to the Internet, it connects to my desktop and the USB drive. That's all. If only Adobe made its CS native...(sigh)

No point trying to hammer a nail in with paint brush...

---

### Post by bpalone on 2010-03-23
A little late to this, but the REAL BOTTOM LINE is:

Either is just an operating system.  Pick one or both.  But pick one that allows you to get done what you need to do.  

You can always, take the other one and install on another machine, dual boot or run it in a virtual machine, and from there learn more about it.  Learning should be fun and not trying to be done while doing production work that needs your attention to detail at hand in the project.

Good luck, and I hope you decide to keep Linux around and take the time to learn it.  But, remember it is just an OS.

---

### Post by J_Stanton on 2010-03-23
> **Keith1212 said:**
> so your saying you had 0 problems the first 2 days you used windows?

o god, don't remind of my first days on windows. i was ready to throw my pc out the window. either have some patience and learn linux, or stay with windows. good luck to you. im glad i took a month to learn linux, and will never go back to windows. freedom.

---

### Post by J_Stanton on 2010-03-23
> **bpalone said:**
> Learning should be fun and not trying to be done while doing production work that needs your attention to detail at hand in the project.



good point, as i think some people think they can just dive into linux and not miss a beat. try wubi (ubuntu inside of windows) or dual boot. that way you can take your time and learn, while still having the crutch of windows there.

---

### Post by opethfan89 on 2010-03-24
This thread is interesting, because I too was (am?) a windows "power-user" and I've been on Ubuntu for the past week and have had nothing but pleasant experiences. I've used windows for upwards of 15 years, including windows 7, and there is no doubt that it is a good operating system, but the Ubuntu philosophy and style just fit more to my personality. I have customized my Ubuntu so quickly, and so easily, in ways that I could only imagine in Windows.

It's unfortunate that you've had a bad experience, unprecedented, but don't let it get you down. I was -extremely- frustrated when I first start using Linux (which, admittedly, was just a handful of weeks ago), and I quickly learned that Google, and the Ubuntu Forums are my two best friends is figuring out this lovely OS. Coming from windows, everything DOES seem a bit harder, I know exactly how you feel, however its all about perserverance. Neither of us knew exactly how to tweak the registry, or do more of the advanced windows concepts until YEARS of constant, daily usage. That same commitment will be necessary if you want to have a good experience on this OS. Just sit down, and force yourself to use Ubuntu for whatever you need to do, whether that is web browsing, emails, photo/video editing, IMing, or whatever you may need to do. There are a TON of blogs and other websites that list, in plain english, step-by-step instructions on how to install many software in Linux. An example of this is a blog I used to help me install compiz-fusion (the software responsible for the "cube" and all the cool visual effects you see) as well as Adobe AIR (cross-platform development software that I use to run the Pandora ONE desktop app). And a kudos to all the amazing people on this forum, because no matter how many times the same question is asked, they will answer it without losing their temper, or without using the monotonous "use the search function" response you find on many other forums.

Ahh, it seems I've gotten ahead of myself in my response. Sorry for the mini-book to anyone who reads this post.

Unprecedented, I urge you to persevere and give Ubuntu another shot. Don't give up, and you will quickly find that Ubuntu is an easy and user-friendly OS, with a great community standing behind it, and the best price tag of all (free!)

---

### Post by unpresedented on 2010-03-24
> **opethfan89 said:**
> This thread is interesting, because I too was (am?) a windows "power-user" and I've been on Ubuntu for the past week and have had nothing but pleasant experiences. I've used windows for upwards of 15 years, including windows 7, and there is no doubt that it is a good operating system, but the Ubuntu philosophy and style just fit more to my personality. I have customized my Ubuntu so quickly, and so easily, in ways that I could only imagine in Windows.

It's unfortunate that you've had a bad experience, unprecedented, but don't let it get you down. I was -extremely- frustrated when I first start using Linux (which, admittedly, was just a handful of weeks ago), and I quickly learned that Google, and the Ubuntu Forums are my two best friends is figuring out this lovely OS. Coming from windows, everything DOES seem a bit harder, I know exactly how you feel, however its all about perserverance. Neither of us knew exactly how to tweak the registry, or do more of the advanced windows concepts until YEARS of constant, daily usage. That same commitment will be necessary if you want to have a good experience on this OS. Just sit down, and force yourself to use Ubuntu for whatever you need to do, whether that is web browsing, emails, photo/video editing, IMing, or whatever you may need to do. There are a TON of blogs and other websites that list, in plain english, step-by-step instructions on how to install many software in Linux. An example of this is a blog I used to help me install compiz-fusion (the software responsible for the "cube" and all the cool visual effects you see) as well as Adobe AIR (cross-platform development software that I use to run the Pandora ONE desktop app). And a kudos to all the amazing people on this forum, because no matter how many times the same question is asked, they will answer it without losing their temper, or without using the monotonous "use the search function" response you find on many other forums.

Ahh, it seems I've gotten ahead of myself in my response. Sorry for the mini-book to anyone who reads this post.

Unprecedented, I urge you to persevere and give Ubuntu another shot. Don't give up, and you will quickly find that Ubuntu is an easy and user-friendly OS, with a great community standing behind it, and the best price tag of all (free!)

thank you so much Mr. opethfan89 for your nice post, you do really feel with me nowadays ... however, I've done the big thing yestreday, I installed ubuntu dual boot with Windows 7, and also installed windows 7 on Sun Virtual Box that runs on ubuntu, so I can secure myself if something went wrong, I can now test my webpages very frequently while keeping the virtual machine opened, I tried some basic things in SAMBA, accessed shared files on windows domain, opened FTP connection from "connect to server" application and through another app called "Zend Studio", opened a remote desktop with a windows server 2003 machine and tried cross way copy-paste between the remote desktop and my newly-born child (ubuntu :) ) ... everything goes very well without problems ...

but some poeple advised me to remove ubuntu 9.10 and install 9.04, because 9.10 is buggy as they told me !! is that right ?

one more thing, I need your tutorial about setting up the cube visualization in ubuntu ..
thanks a lot in advance ...

---

### Post by e24ohm on 2010-03-24
> **unpresedented said:**
> thank you so much Mr. opethfan89 for your nice post, you do really feel with me nowadays ... however, I've done the big thing yestreday, I installed ubuntu dual boot with Windows 7, and also installed windows 7 on Sun Virtual Box that runs on ubuntu, so I can secure myself if something went wrong, I can now test my webpages very frequently while keeping the virtual machine opened, I tried some basic things in SAMBA, accessed shared files on windows domain, opened FTP connection from "connect to server" application and through another app called "Zend Studio", opened a remote desktop with a windows server 2003 machine and tried cross way copy-paste between the remote desktop and my newly-born child (ubuntu :) ) ... everything goes very well without problems ...

but some poeple advised me to remove ubuntu 9.10 and install 9.04, because 9.10 is buggy as they told me !! is that right ?

one more thing, I need your tutorial about setting up the cube visualization in ubuntu ..
thanks a lot in advance ...
You might find it interesting, but play around with SSH and PUTTY to tunnel your remote desktop/vnc connections through.

---

### Post by unpresedented on 2010-03-24
> **e24ohm said:**
> You might find it interesting, but play around with SSH and PUTTY to tunnel your remote desktop/vnc connections through.
hi e24ohm, I used putty before a while when I was on windows to authenticate my account with remote GIT host (GitHub.com in my case) but it was really annoying to use (maybe because I didn't used to learn it before) .. what about SSH thing ?

and should i use SSH + PuTTY instead of remote desktop terminal ? is it more powerful ? is there any extra features ?

---

### Post by opethfan89 on 2010-03-24
> **unpresedented said:**
> thank you so much Mr. opethfan89 for your nice post, you do really feel with me nowadays ... however, I've done the big thing yestreday, I installed ubuntu dual boot with Windows 7, and also installed windows 7 on Sun Virtual Box that runs on ubuntu, so I can secure myself if something went wrong, I can now test my webpages very frequently while keeping the virtual machine opened, I tried some basic things in SAMBA, accessed shared files on windows domain, opened FTP connection from "connect to server" application and through another app called "Zend Studio", opened a remote desktop with a windows server 2003 machine and tried cross way copy-paste between the remote desktop and my newly-born child (ubuntu :) ) ... everything goes very well without problems ...

but some poeple advised me to remove ubuntu 9.10 and install 9.04, because 9.10 is buggy as they told me !! is that right ?

one more thing, I need your tutorial about setting up the cube visualization in ubuntu ..
thanks a lot in advance ...

Glad to see you liked my post, because I assure you I felt exactly the same as you did when I first started using Linux. As far as a tutorial for setting up the cube effect, I just followed the steps [here]("http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion"). it's basically installing + enabling compiz-fusion, and then configuring it to your liking. Best of luck in setting everything up, and I hope you decide to stick to Linux. As far as 9.10 being buggy, I don't share that opinion because its worked just fine for me, and I don't think I'll update to 10.04 anytime soon.

---

### Post by DeusExM1 on 2010-03-24
i dont know what windows power user would say that IE is "one of the best browsers out there"...Not really.

And stick with linux... give it a week or two. You didnt start out knowing everything in windows did you? You accumulated that knowledge over time. Linux wont take as long, but you cant expect to do it in 2 days! Its like having a liscence to drive a motorcycle, and trying to drive a truck... Its not the same thing! 

Keep at it...

---

### Post by Riffster on 2010-03-24
I'd just like to add I only managed to get into linux "properly" (ie to use it on a day to day basis as a user) about a year ago. I first tried to install it in 1999 -so it took me a decade (obviously I need a faster PC ;))

One of the striking differences between Windows and Linux from my point of view is simply this: 

Windows tries to make iteself "idiot proof" and do the tricky stuff for you, working on the assumption that you know nothing. 

Linux is far more empowering *but you have to find out how to do the tricky stuff for yourself. *

But with net forums so prevalent and so many able Linux users I'm now finding it significantly easier to solve problems in Linux than I do in Windows. I am now only using Windows for gaming and DJing and I plan on changing the latter but time is the factor there. 

Reading most of the responses here - and I'd agree with them in general - is this; you clearly have enough "PC savvy" to be able to make Linux work for you, but if you want to get the best out of it, you need to give it a fair crack of the whip. 2 days isn't enough, but I think you recognise that from your later posts anyhow.

---

### Post by opethfan89 on 2010-03-24
> **Riffster said:**
> I'd just like to add I only managed to get into linux "properly" (ie to use it on a day to day basis as a user) about a year ago. I first tried to install it in 1999 -so it took me a decade (obviously I need a faster PC ;))

One of the striking differences between Windows and Linux from my point of view is simply this: 

Windows tries to make iteself "idiot proof" and do the tricky stuff for you, working on the assumption that you know nothing. 

Linux is far more empowering *but you have to find out how to do the tricky stuff for yourself. *

But with net forums so prevalent and so many able Linux users I'm now finding it significantly easier to solve problems in Linux than I do in Windows. I am now only using Windows for gaming and DJing and I plan on changing the latter but time is the factor there. 

Reading most of the responses here - and I'd agree with them in general - is this; you clearly have enough "PC savvy" to be able to make Linux work for you, but if you want to get the best out of it, you need to give it a fair crack of the whip. 2 days isn't enough, but I think you recognise that from your later posts anyhow.

I agree completely. Windows really does assume that the end-user knows nothing (which is sadly true in the target audience for windows products), whereas linux requires you to take a proactive stance and actually take the time to learn, time to use google extensively, and time to learn how to use the search function on this great forum to find the answer to your questions.

> **DeusExM1 said:**
> i dont know what windows power user would say that IE is "one of the best browsers out there"...Not really.

And stick with linux... give it a week or two. You didnt start out knowing everything in windows did you? You accumulated that knowledge over time. Linux wont take as long, but you cant expect to do it in 2 days! Its like having a liscence to drive a motorcycle, and trying to drive a truck... Its not the same thing! 

Keep at it...

I don't think I've ever actually used IE other than on the computers at school....I've been using Firefox since at least 03-04, and I will refuse to talk to my friends until they install Firefox on their computers. Happily, all of them use firefox now ;)

I agree, and I think the OP needs to stick with linux. Nothing I learned was hard, but it wasn't easy either, but it really forced me to become *very* comfortable using the terminal. In fact, I **prefer** bash commands over a GUI interface now.

---

### Post by Methuselah on 2010-03-25
I stopped reading once the OP said programs are very complicated to install.
Because if he had even googled 'how to install programs in Ubuntu' I don't see how he could come to that conclusion.
Instead, I bet he is running around downloading source-code and compiling it and complaining about that.
If you are using something new you need to do some homework...period.

---

### Post by unpresedented on 2010-03-25
> **DeusExM1 said:**
> i dont know what windows power user would say that IE is "one of the best browsers out there"...Not really.

And stick with linux... give it a week or two. You didnt start out knowing everything in windows did you? You accumulated that knowledge over time. Linux wont take as long, but you cant expect to do it in 2 days! Its like having a liscence to drive a motorcycle, and trying to drive a truck... Its not the same thing! 

Keep at it...
yes I didn't start windows knowing everything about it ... I will try to stick to linux as much as i can ...

> **Methuselah said:**
> I stopped reading once the OP said programs are very complicated to install.
 Because if he had even googled 'how to install programs in Ubuntu' I don't see how he could come to that conclusion.
 Instead, I bet he is running around downloading source-code and compiling it and complaining about that.
 If you are using something new you need to do some homework...period.

OP ? what does it stand for ?
and yes, I've tried to compile source files to install programs, I'm not fool to ask you how to press the mouse key to open the software center in ubuntu as this is straight forward ...
thank you for stopping reading ..


> **opethfan89 said:**
> Glad to see you liked my post, because I assure you I felt exactly the same as you did when I first started using Linux. As far as a tutorial for setting up the cube effect, I just followed the steps [here]("http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion"). it's basically installing + enabling compiz-fusion, and then configuring it to your liking. Best of luck in setting everything up, and I hope you decide to stick to Linux. As far as 9.10 being buggy, I don't share that opinion because its worked just fine for me, and I don't think I'll update to 10.04 anytime soon.
 thank you bro so much for this tutorial, i will follow the instructions today and feedback you asap ... take care ;)

---

### Post by bvanaerde on 2010-03-25
> **unpresedented said:**
> it's unreasonable to eat 512 or more of my RAM (running virtual box with windows xp) just to test my web pages on internet explorer 8 !! this issue is driving me crazy

There's an excellent website for testing sites in different browsers:
[http://browsershots.org](http://browsershots.org)

Really nice, as you'll never be able to test all browsers, when you're only using one operating system.

---

### Post by mastablasta on 2010-03-25
> **opethfan89 said:**
> I agree completely. Windows really does assume that the end-user knows nothing (which is sadly true in the target audience for windows products), whereas linux requires you to take a proactive stance and actually take the time to learn, time to use google extensively, and time to learn how to use the search function on this great forum to find the answer to your questions.
.
 
And we all know how modern humans have more and more time on thier hands. In fact no one rushes to work these days for example.... We all have plenty of time to spend on learning & searching & posting on how to get the darn Tv Tuner working (eventhough no one replies and the searches don't offer any good instructions...)

---

### Post by steveneddy on 2010-03-26
To the OP:

you may get some use from the links in mt sig.

Hope that helps.

Good to see you found VirtualBox - great software.

---

### Post by Arthur_D on 2010-03-26
Hey folks, please do not drown the guy in posts.
As a matter of fact, I almost feel guilty for making another useless post.... :p

---

### Post by entikryst on 2010-03-26
This wallpaper may help you when using the terminal.

[http://bharatikunal.files.wordpress.com/2008/10/linux-wallpaper-for-beginners.jpg](http://bharatikunal.files.wordpress.com/2008/10/linux-wallpaper-for-beginners.jpg)

---

### Post by juancarlospaco on 2010-03-26
Dont use Wine.
Dont use Terminal.

/FIXED

---

### Post by Gixxy on 2010-03-26
Sounds to me like a Microsoft employee trolling our forums.... [-X

Yes, I agree that linux is not as easy to use as windows but if you want a secure, stable OS that just works you can't beat linux. My girlfriend runs ubuntu with no problems. (And really likes it BTW) It isn't difficult it just takes some getting used to... :)

---

### Post by steveneddy on 2010-03-26
> **entikryst said:**
> This wallpaper may help you when using the terminal.

[http://bharatikunal.files.wordpress.com/2008/10/linux-wallpaper-for-beginners.jpg](http://bharatikunal.files.wordpress.com/2008/10/linux-wallpaper-for-beginners.jpg)

Thanks - I DLed this for future use.

I don't think that the OP is a troll, just confused. We see that a lot with "power users" coming from the Windows world.

To the OP:

Before you go and jump in to this new OS, read a little about it and just play around with it. Touch all of the buttons and simply look around so you get a good feel for it, and before you try something, post a thread on the forums asking the best way to accomplish your task.

Many of the things you tried had very simple solutions instead of the advanced or complicated ways that you attempted.

Good luck - keep hacking.

---

### Post by unpresedented on 2010-03-27
> **entikryst said:**
> This wallpaper may help you when using the terminal.
 
[http://bharatikunal.files.wordpress.com/2008/10/linux-wallpaper-for-beginners.jpg](http://bharatikunal.files.wordpress.com/2008/10/linux-wallpaper-for-beginners.jpg)
 
thank you very much for this nice wallpaper ..
 
 
> **Gixxy said:**
> Sounds to me like a Microsoft employee trolling our forums.... [-X
 
Yes, I agree that linux is not as easy to use as windows but if you want a secure, stable OS that just works you can't beat linux. My girlfriend runs ubuntu with no problems. (And really likes it BTW) It isn't difficult it just takes some getting used to... :)
 
no I'm not Microsoft employee ...
<snip>
I was trying to install some vital programs on ubuntu, non of them installed successfully, this came after tens of workarounds and trys ... 
one of these programs, IE8, 3 days trying to install it without a luck, the thread poster himself couldn't help me in my case, and when successfully installed IE8 on his machine, he posted tons of issues with it : no search, no options ... 
this is really hell !!
another application is the MSN messenger, i tried one called aMSN but far away like the real one !! it's interface really sucks plus it does not contain what I want to do with my regular messenger !!
and many other apps I couldn't install it before it's unsupported on linux ubuntu !!
before couple hours, I restarted my machine and switched back to windows 7 untill i find a good reason to go back to linux ubuntu .. I do not know why people tell me it's better than windows !!
 
 
> **steveneddy said:**
> Thanks - I DLed this for future use.
 
I don't think that the OP is a troll, just confused. We see that a lot with "power users" coming from the Windows world.
 
To the OP:
 
Before you go and jump in to this new OS, read a little about it and just play around with it. Touch all of the buttons and simply look around so you get a good feel for it, and before you try something, post a thread on the forums asking the best way to accomplish your task.
 
Many of the things you tried had very simple solutions instead of the advanced or complicated ways that you attempted.
 
Good luck - keep hacking.
 
I've read many tutorials about it (continuous reading for 7 days now), it made my life harder !! so confused !! I swear that I suffered headache from linux ubuntu ..
it's advanced visualization options are cool ...
but the programs that I must use on a daily basis can't be installed successfully on this OS !! 
I'm completely confused now :(

---

### Post by Austin25 on 2010-03-27
> **unpresedented said:**
> 
...3)whenever I try to read tutorials in ubuntu, all of these tutorials requires me to use terminal ... terminal ... terminal ... this is hell !...
Terminal is just the easiest way to help someone over the forum because you can just copy and paste rather than saying click here, then click here, the click there.

---

### Post by unpresedented on 2010-03-27
> **Austin25 said:**
> Terminal is just the easiest way to help someone over the forum because you can just copy and paste rather than saying click here, then click here, the click there.
 but if you were offline (no internet connection) then that terminal is useless for novices like me !! but the "clicks" thing would be useful in this case !

---

### Post by craig10x on 2010-03-27
After years of running with internet explorer in windows, it was only when i started using ubuntu that i started using Firefox...It's actually a  lot nicer to use the IE and is more secure and faster then IE as well....and the best part is that i have found that it is as compatible with all websites as IE is...I've never run in to a single site that didn't work with it...

---

### Post by ownasaur on 2010-03-30
Use what works best for you. In my case I use linux for everyday things, and windows exclusively for gaming.

I'd suggest you dual boot or play with the live cd to learn how things work. Jumping into linux at once will be a bit rough but it is worth it.

Good luck.

---

### Post by javyn999 on 2010-03-30
I'm a former Windows "power user" and love Linux.  *shrug.  I've only been using it about a year, and have much to learn still, but it's knowledge that will never be out of date.

I'm not quite sure why a Windows power user would make a poor Linux candidate, quite the opposite really.  It[Linux] is a tinkerer's dream.

Installing software is incredibly easy.  Either find it in syntapic/software center, apt-get install it, find a debian package off the web (most similar to installing a Windows app), or grab a tarball.

---

### Post by ramin1983 on 2010-03-31
Hello Everyone;
well, I found this topic really interesting, because the same thing happened to me but a bit differently!
I've been using Microsoft OS for a long time, started with DOS 3.sth(!), when windows came I thought "Ok! I prefer my Norton Commander (NC) to this slow and stupid thing!". DOS was really good, I loved it, of course it was really simple and whatever you wanted to do, you had to start programming yourself! There was nobody to help you! But anyway it was sweet and I loved the fact that I have to type, somehow it feels like you are actually talking to the machine. Then windows 95 (CRAP) came, still stayed with DOS, until windows 98, it was running faster and smoother but still lots of bugs, I had to migrate to this GUI of new OS and there was no other way. From then I was loyal to Windows, and never thought about testing a new OS, when everything is fine, why change? so I never bothered myself changing my platform to anything else ( I didnt even like to try Mac! ), although it was boring ,just clicking, you have to install softwares with all the craps they offer,  after installing each software you may find many unuseful parts which you have to clean urself, and PRICES! So working with computer was no longer fun, it was just "trying to survive"!

About three days ago, I wanted to reinstall my windows and I thought ok, lets have some fun, lets try this linux everybody talks about! After finding out about distributions and using a website to suggest one to me, I downloaded ubuntu! and guess what, although I didnt know what i was doing in some parts but I was feeling sth I had forgot for a long time, YES You guess right, suddenly working with my computer was FUN again, it was challenging and I had to type! I had to think! I had to LEARN!
In these three days I've installed ubuntu 6 times, because everytime I tested many things and somehow made alot of errors in it and surprisingly, even with errors I could use the other parts, not like windows!
last night I reinstalled it, customized everything, downloaded some cool softwares and now it looks like the best OS ever! It's fast, its smooth, its nice and its challenging! I really LOVE TERMINAL and I love that its possible to do almost everything with terminal!

I don't call myself Power-User, I'm just a regular experienced user who has worked with computers alot, but after 3days I don't have any problems with this new platform and I'm having ALOOOOOOOOOOOT of fun, thnx to ubuntu.

I will stay with it, and I cant wait for the next ubunto...

---

### Post by mastablasta on 2010-03-31
what crap do windows install that you need to clean up later? there is usually always an option during instalation if you want to do a cusotm one and then you sleect only the things you need and elave the "crap" outside. I never had any problems with windows. except for that one virus attack which was resolved quite fast by searching the web. files were saved and the darn commercials stopped popping up (it was my fault getting the virus using IE instead of Netscape)

---

### Post by ramin1983 on 2010-03-31
You cant fully customize windows installation, you could with windows 98, but not with today's windows, so after installation you should turn some features on or off...
second one is about applications, although you can customize most of the installations, after that you need to disable or uninstall some of the features.
The other thing is the services, some services like Windows Security Agent (which is not usable at all) use alot of resources which you have to disable them later when you are finished with installation.
Resources are limited on computer systems, so you have to run only the programs which you really want and use, so your computer could run faster and smoother and you can get the best performance possible with your resources.
If you're running vista, take a look at the total number of processes in task manager, how many do you see? a normal user with some light weight applications installed may see some of about 60 processes running, of course they fixed this number in Windows 7, they removed some of the not needed features, and that is one the reasons Win7 is much more better than Vista...
I've been Assembling and Programming computers for many years, everytime you install a windows you have to customize it, you have to remove some of the services and you have to install many basic applications for everyday use... each programming takes at least 30 minutes for windows, about 30 minutes for full customization and about an hour or so for applications, so thats something about 2 hours.
How long does ubuntu take to install with all the updates and customizations? less than an hour!

---

### Post by mastablasta on 2010-03-31
I never did much customization on my Windows (except for turnin off some things which i did through tweak utilities instead of searching them arround...) and never really had an issue with low resources (except for the disk size which indeed kept getting bigger and bigger but not all Windows fault).
 
I count 27 processes including KasperskyAV (i think it's there). WSA never created any issues with me i have original windows. everything on computer works as it should. 
 
2 GB RAM it runs fast, also 1GB RAM, 256 MB Ram it runs slow, but it runs....
 
Yes Ubuntu install is fast indeed. However updating is slow. I have a slow connection so when i decide to do updates (which it does them every week) it takes eachtime about 1 hour and then i also need to reboot.
 
Ubuntu doesn't take so many resources, but then again it also can not give you DirectX for example. So you can't really play the big titles for example. Easy to be light when you don't have certain features... ALso the number of Hardware working with Linux is low (not Linux fault, but doesn't change the fact). Again easy to be light since you don't have so many drivers (ups, modules).
 
I am not sure how it is with win7 but i think it's less resource hungry than Vista. Never tried Vista or Win7 as for now XP is doing it's job. 
 
One computer though is running Ubuntu. But still not everything works on that one...

---

### Post by WannabeFantasma on 2010-03-31
At above;
I tried win 7 and it does use a less resources than Vista but not to say WOOOW
That's I keep my vista, it works just fine for me (+ I don't want to spend 100 Euro on another "upgraded" OS that's almost the same)

---

### Post by mastablasta on 2010-03-31
well it works on netbooks with 512 MB ram while vista strugles with 1 GB.
 
yeah 100 EUR seems a lot if you can make Ubuntu run well on your computer :-). For office and home Ubuntu really rocks. If only there was more of certain software support here (e-banking, e.taxes etc.) and more hardware support.

---

### Post by motorcity909 on 2010-03-31
> <snip> I can't believe that remark has been uncommented upon. 

<snip>

---

### Post by Swagman on 2010-03-31
> **motorcity909 said:**
> I can't believe that remark has been uncommented upon. 

Wow, just an extraordinary level of sexism that you don't see very often nowadays.

Indeed.

I stated elsewhere on this site that my three daughters all use Ubuntu. In fact they have been using Ubuntu practically just as long as I have.

My daughters are now, 21, 16 and 13

I've also installed Ubuntu on ..The sister in laws machine and three other female friends machines.

They very rarely have any problems using it or understanding how to get what they want accomplished with it. 

He really should check out [**Ubuntu Women**](http://ubuntuforums.org/forumdisplay.php?f=76) to see just how many are using it.

By the Way.

OP means = **O**riginal **P**oster = Presedented

---

### Post by ramin1983 on 2010-03-31
Well I do customize alot, its not about how it looks, its all about services and applications features which use lots and lots of resources, if you use another program to do the customization, you add more problems because even those applications use ur resources. Yes, its possible to run win xp or even 98 on a pc with no problem and still it does everyday tasks! While I was using vista, I always used the classic windows theme, nobody could even tell its vista, it was as simple as win95! Another thing is that with all that windows offer, people change everything in it, like they use firefox instead of IE, or they use other media players (VLC or mdp classic) instead of windows media player, so its better to have a platform without any of those applications and add what you like inside it instead...
For me, I prefer to be up to date, Before 3 days ago I was always using the latest windows 7 and always latest softwares, but now that I've seen ubuntu, I think Ill stick to it.

I don't think that running directx can be a positive point for windows, if it is used for playing games, i have a better suggestion, buy a ps3 or wii or xbox, and if for some other purposes I dont think that normal pcs with up to 2 gb ram are suitable for that. for me, I dont need graphics, I prefer terminal commands to all these GUI... 

After 3days of testing linux and comparing these two platforms, if I want to give you an example, just think of mac and windows as very modern cars like BMW 2010, you open the hood, there is nothing but some boxes which even if you know things about engine you cant do anything unless you go to a bmw service! Linux in the other hand is like a modern but still old fashioned car, you can tune it, you can add customized and high performance parts and its possible for almost everybody with some computer knowledge and then you can drive even faster and safer than modern cars(win and mac)!

About updates I think you have the same problem with windows update every month... updating ubuntu took about 10 minutes for me every time... every service pack for windows which usually comes out every year is about 500mb and everytime you reinstall ur windows you have to download them, dont forget about updates everymonth, each month about 50mb! total ubuntu update was sth less than 300mb for me...

About drivers, its not only ubuntu that has this problem, earlier windows like xp and 98 were worse and still you will face problems with different hardwares on vista and 7. I remember the time which I couldnt install XP on some of the mainboards, no matter what, after setup it showed the blue screen error and nothing could be done! so they had to run 98!

About the drivers I think its manufacturers fault, if they could use somekind of standard for all of their hardwares it was easier for everybody!

> **mastablasta said:**
> I never did much customization on my Windows (except for turnin off some things which i did through tweak utilities instead of searching them arround...) and never really had an issue with low resources (except for the disk size which indeed kept getting bigger and bigger but not all Windows fault).
 
I count 27 processes including KasperskyAV (i think it's there). WSA never created any issues with me i have original windows. everything on computer works as it should. 
 
2 GB RAM it runs fast, also 1GB RAM, 256 MB Ram it runs slow, but it runs....
 
Yes Ubuntu install is fast indeed. However updating is slow. I have a slow connection so when i decide to do updates (which it does them every week) it takes eachtime about 1 hour and then i also need to reboot.
 
Ubuntu doesn't take so many resources, but then again it also can not give you DirectX for example. So you can't really play the big titles for example. Easy to be light when you don't have certain features... ALso the number of Hardware working with Linux is low (not Linux fault, but doesn't change the fact). Again easy to be light since you don't have so many drivers (ups, modules).
 
I am not sure how it is with win7 but i think it's less resource hungry than Vista. Never tried Vista or Win7 as for now XP is doing it's job. 
 
One computer though is running Ubuntu. But still not everything works on that one...

---

### Post by mastablasta on 2010-04-01
Ok so first of what you are saying is not OS customization it's adding new programmes and functionalities. And if the system get's bloated because of that then i have news for you - it's the same in Ubuntu.
 
> **ramin1983 said:**
>  
I don't think that running directx can be a positive point for windows, if it is used for playing games, i have a better suggestion, buy a ps3 or wii or xbox, and if for some other purposes I dont think that normal pcs with up to 2 gb ram are suitable for that. for me, I dont need graphics, I prefer terminal commands to all these GUI... 
 
Consoles are bad idea as you do not own them the company does. Latest issue was when PS3 decided to drop Other OS feature eventhough people payed for it. Or Xbox locking out hardware "hackers" who used the console for other thigns. Another thing they close the servers and you can't play the game (online and sometimes even offline) no more. While i like old games (i have some spectrum simulators instaleld on my computer, try doing that on console...)
> 
After 3days of testing linux and comparing these two platforms, if I want to give you an example, just think of mac and windows as very modern cars like BMW 2010, you open the hood, there is nothing but some boxes which even if you know things about engine you cant do anything unless you go to a bmw service! Linux in the other hand is like a modern but still old fashioned car, you can tune it, you can add customized and high performance parts and its possible for almost everybody with some computer knowledge and then you can drive even faster and safer than modern cars(win and mac)!

Car comparison again... as my borther tells me Linux can create quite a few problems, if when you update and find out hardware is suddenly not supported anymore and you need to update because you need porgramme updates and security updates. I am not sure i quite understand him, but i know he uses Linux at work and knwos a lot about it, yet still thinks how good and long term MS windows support is.
> 
About updates I think you have the same problem with windows update every month... updating ubuntu took about 10 minutes for me every time... every service pack for windows which usually comes out every year is about 500mb and everytime you reinstall ur windows you have to download them, dont forget about updates everymonth, each month about 50mb! total ubuntu update was sth less than 300mb for me...
 
If you updates regularly (every month) updates are very small. Usually there is about 8 updates 256kb-512 MB in size. Except Internet explorer updates which are about 2.5-3 MB. Linux updates i am receiveing about every week and are close to 50 MB every time. Maybe i am doing something wrong - i just clik install updtaes.
> 
About drivers, its not only ubuntu that has this problem, earlier windows like xp and 98 were worse and still you will face problems with different hardwares on vista and 7. I remember the time which I couldnt install XP on some of the mainboards, no matter what, after setup it showed the blue screen error and nothing could be done! so they had to run 98!
About the drivers I think its manufacturers fault, if they could use somekind of standard for all of their hardwares it was easier for everybody!
 
They can't use standards, as each is made differently. But what they could do is to give the source out so that community can make opensource drivers. Or they could work with community and devlope them themselves (as was sort of the case with ATI in beginning). 
You are quite right. WinXP could not load on certain laptops with Vista sign on them. What manufacturers could do is they could mark which parts are supported by Linux (so far there are only very rare examples when they do this).

---

### Post by motorcity909 on 2010-04-01
It seems my comment (#103) on the OPs statement about girls and Linux has been removed but that original statement is still in there - #91.

---

### Post by manzdagratiano on 2010-04-03
> **unpresedented said:**
> 
1) installing programs in general is very complicated, it requires terminal many times, I faced things like : add software source then add public key (am i going to hack the whitehouse!!) then sometimes it says there is an error because there is no public key found (although I have provided the right key for it) ... 
some other people say : type something chmod  .. plus some other thing and then you can install any program .. others say : apt-get on terminal ... why all of this headache !!
 
2) installing some hardware drivers is somehow difficult.
 
2.1) system hangs when I try to install some hardware drivers (like dell broadcom wireless card driver) and then all I have to do is press the power button and turn off the machine.
 
3) whenever I try to read tutorials in ubuntu, all of these tutorials requires me to use terminal ... terminal ... terminal ... this is hell !
 
4) it's very hard to fix errors (broken packages for e.g.) , I have to be expert in terminal to do so ... because the graphical option in synaptic (hope I didn't misspelled the word) to fix broken packages does not work (this happened with me and many other users on different machines)
 
5) something vital that I need to test my web pages on, Internet Explorer 8 over Windows 7, I did not find a single tutorial to help me set up IE8 over windows 7 using wine ! you believe it !! two days trying and trying to install that piece of browser (which is consider one of the best browsers) and then ended up with NOTHING ! :(
 
5.5) Linux ubuntu 9.10 does not have a built in rdp protocol, that means I can't log into my windows server using remote desktop unless I install a program that supports it, and 90% of these programs on Linux are considered either buggy or slow, is that right ?
 
I can do everything with Windows 7 very easily, and without having to use terminal (command prompt) except for rare cases ... plus it is stable (no craches at all) and very fast .. plus, what I can do on Linux ubuntu I can do it easily on Windows 7 !!

Installing programs is easy as hell! For majority of them, a sudo apt-cache search followed by a sudo apt-get install is sufficient! Not like Windows where you hunt the web for executables and/or drivers - apt takes care of dependencies. To quote an example - when I installed LaTeX on my Windows XP for the first time (when I had that abomination!), it whined that Microsoft Script Debugger was not installed - I had to track it down on Microsoft's website! And as if that was not enough, of course, I should have expected - it whined in turn that Microsoft script was not installed! That was some ride.

Most of the hardware drivers you need are installed by default and work out of the box. Others where the proprietary world is needed - that, well, that is just the way the Free Software community is developing; if things were open source, that problem would not be there in the first place. But no, some people think they can invent a technology and sell it to people, and then have the gall to arrest the development of that technology unless they do it themselves. If Newton had said to the world - give me the force and I will give you the acceleration, but I won't tell you how I do it, look where we would be today! (And even if you say somebody would have figured it out - they did even in the Free Software world). And in spite of all these things, Ubuntu offers you a middle path - take for instance nvidia - their drivers are better if you have a GeForce (I do), but Ubuntu tells you that there are proprietary drivers available for your machine, and you can choose to install them. Not like Windows, where if you once inserted a Debian CD, it would say that the disk contains software that could potentially harm your computer. The audacity!!!

The terminal is the way of GNU/Linux - it is all powerful. If your system was built in a programming language, should not the way it operates be close to it? Windows API's are all written in  C++, yet it does not even have a default C++ compiler installed. The command prompt in windows is a joke. All it is good for is telnet, which is now outdated by ssh - which it cannot even run (you must get puTTy). The terminal is the key to unlocking the inner workings of the system, which is impossible in Winblows thanks to Microsoft!

Broken packages would not normally arise within the realm of a stable system, unless one chose to put something from an unstable branch. But if they do arise, the procedure is the same as it is in windows - uninstall the problematic programs, and install the stable ones. One may have to resort to a terminal to do certain things, but in Winblows, you are also asked many a time to delete some DLL in some obscure folder, or to change a weird registry setting that you have no idea what means - trust me I have had my share plenty. For instance, to be able to add wordpad to the right click menu, I had to go on an insane registry search. It is NO better than opening a terminal and spewing a few commands.

An who considers IE8 to be one of the best browsers around? Serfs of Microsoft? It is slow and bulky, it is vastly unsecure, its privacy features are a mockery, and it REQUIRES that Windows be installed for it to run (thankfully you can cheat with wine). I understand that one might need to check how pages render on IE when they make them, but for such a purpose, IE6 should be good enough, which can be installed quite easily using IEs4linux (I refuse to however). In any other aspect, Mozilla would blow it out of the water.

And yes, Ubuntu DOES have a remote desktop client.

Anything you can do on Windows you can on Linux, and vice versa, with a few inevitable exceptions on either side. However, consider that if you were to buy a Vista computer, like I did, you would not be entitled for a free upgrade to Windows 7. Why should you not be? You already paid for it once!!! There is a certain important thing you shall NEVER get with windows - the conviction that you are running a system which you can change as and when you want and how you want, without worrying about it. You shall never have to be a slave to Microsoft's ideas and evil practices. Corporations like Microsoft and Apple are trying to put a hold on how people think about computing, and curb what they can and cannot do on their machines. I vehemently protest against this pure evil - and everyone better realize soon how dangerous this mind control is going to be for the future!

---

### Post by hsoulen on 2010-05-05
:lolflag:

I cannot believe this thread is still alive.

Troll-bait.

You like Windows - AWESOME! Use it and be happy.

I like Linux - AWESOME! I am happy.

You want to try a new OS - AWESOME! 

There are forums for every distro, there to help you should you need it, same for Windows. Try it, if you find it does not suit your needs, use something else.

If you try Ubuntu (or Gentoo, or SUSE, Slackware, Fedora... List goes on) and you need some help just post and you will see that soooo many people want to help. We love our OS and we want others to enjoy it as well. But if you just want to flame it, go away.

Cheers,

Hank

---

### Post by Grenage on 2010-05-05
> **hsoulen said:**
> I cannot believe this thread is still alive.

It _had_ died, sir necromancer. ;)

---

### Post by scottuss on 2010-05-05
> **Keith1212 said:**
> so your saying you had 0 problems the first 2 days you used windows? Thats like driving a car for 12 years and expecting to learn to fly a plane in 2 days. Then you complain that the plane has too many knobs and switches and should be "dumbed down" so anyone can learn it in days.

I like this analogy :p

P.S Nice resurrection! lol

---

### Post by hsoulen on 2010-05-05
> **Grenage said:**
> It _had_ died, sir necromancer. ;)

DOH!

"These are not the trolls you are looking for"

My Bad.

Hank.

---

### Post by ade234uk on 2010-05-05
> **unpresedented said:**
> dear all,
I'm a windows power user, I switched to linux ubuntu just before two days, in these two days, I couldn't install a single program correctly (except for something called; wine after it took an hour from me in order to be able to install it), so I found out the following things in the last two days using linux ubuntu 9.10 :
1) installing programs in general is very complicated, it requires terminal many times, I faced things like : add software source then add public key (am i going to hack the whitehouse!!) then sometimes it says there is an error because there is no public key found (although I have provided the right key for it) ... 
some other people say : type something chmod  .. plus some other thing and then you can install any program .. others say : apt-get on terminal ... why all of this headache !!
 
2) installing some hardware drivers is somehow difficult.
 
2.1) system hangs when I try to install some hardware drivers (like dell broadcom wireless card driver) and then all I have to do is press the power button and turn off the machine.
 
3) whenever I try to read tutorials in ubuntu, all of these tutorials requires me to use terminal ... terminal ... terminal ... this is hell !
 
4) it's very hard to fix errors (broken packages for e.g.) , I have to be expert in terminal to do so ... because the graphical option in synaptic (hope I didn't misspelled the word) to fix broken packages does not work (this happened with me and many other users on different machines)
 
5) something vital that I need to test my web pages on, Internet Explorer 8 over Windows 7, I did not find a single tutorial to help me set up IE8 over windows 7 using wine ! you believe it !! two days trying and trying to install that piece of browser (which is consider one of the best browsers) and then ended up with NOTHING ! :(
 
5.5) Linux ubuntu 9.10 does not have a built in rdp protocol, that means I can't log into my windows server using remote desktop unless I install a program that supports it, and 90% of these programs on Linux are considered either buggy or slow, is that right ?
 
I can do everything with Windows 7 very easily, and without having to use terminal (command prompt) except for rare cases ... plus it is stable (no craches at all) and very fast .. plus, what I can do on Linux ubuntu I can do it easily on Windows 7 !!
 
finally, I didn't open this thread to compare linux with windows, I need advice, do you advise me to stay on Linux Ubuntu and forget Windows ? I need somebody to convince me why I should use Linux Ubuntu and leave Windows !! or vice versa ...

If Windows 7 is better for you use that. You need to take time and learn Ubuntu just like you when you encountered Windows.

---

### Post by Linuxforall on 2010-05-05
sudo apt-get install nautilus-gksu you can also install it via GUI synaptic, gives you ability to copy, delete, paste into system folder, absolutely no terminal is ever needed but do bear in mind, when you remove something in system folders, don't come crying that your installation is hosed.

Since you mentioned stable Windows 7, it just got a stability update ;) some of the issues being

Windows Explorer crashes and then restarts when you access a third-party Control Panel item.
You cannot connect to an instance of SQL Server Analysis Services from an application in Windows 7 or in Windows Server 2008 R2 after you install Office Live Add-in 1.4 or Windows Live ID Sign-in Assistant 6.5.
Windows Explorer may stop responding for 30 seconds when a file or a directory is created or renamed after certain applications are installed.
The Welcome screen may be displayed for 30 seconds when you try to log on to a computer if you set the desktop background to a solid color.
You are not warned when you delete more than 1000 files at the same time. Then, the files are deleted permanently and are not moved to the Recycle Bin.

They sure took their time fixing them being a paid OS and that too quite costly.

[http://www.ghacks.net/2010/05/04/windows-7-stability-and-reliability-update-april-2010/#more-25149](http://www.ghacks.net/2010/05/04/windows-7-stability-and-reliability-update-april-2010/#more-25149)

---

### Post by Ms_Angel_D on 2010-05-05
This thread has moved beyond being a testimonial or experience and into support, this section of the forums is not for support.

unpresedented,

If you have a need for support please feel free to utilize the other sections of the forums.

Thank you all for participating, thread closed.

---

