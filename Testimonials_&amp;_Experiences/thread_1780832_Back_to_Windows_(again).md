---
title: "Back to Windows (again)"
date: 2011-06-12
forum: Testimonials &amp; Experiences
---

### Post by voney on 2011-06-12
Let me start by saying that I'm by no means a novice when it comes to Lunux/Ubuntu, I know how to use the command line and compile my own kernel (with some reading) and have used various Linux based OSs on an off for years.

Now, every six months or so I get the urge to give Ubuntu another go as either my main desktop OS or the primary OS for one of my laptops. I grab the latest ISO and spend several hours setting it up and configuring it how I like it. But then I inevitably come across some functionality which is just inexplicably broken. Now I'm not talking little things that can be solved by using a different program or spending an hour reading config files either, I'm talking about fundamental problems with the way things are done in the OS that inevitably drive me back to using Microsoft products (or hackintosh if the hardware supports it).

All of the problems that end up being show stoppers for me have been related to how Linux deals with peripherals (screens, input devices, sound etc). Todays problem has to do with how Ubuntu deals with screens... or more specifically, how it doesn't. 

I have two screens hooked up to my NVidia GPU running side by side, one in landscape and the other in portrait. After installing Ubuntu and the NVidia drivers I found that my desktop was only on the rotated screen (without rotation), "Thats OK!" I thaught "I'll just pop open the 'Monitors' preferences and fix everything!"... But the 'Monitors' preferences application only showed me one screen attached, and wouldn't allow me to rotate it. So I hunt around for the nvidia-settings app, it detects the second screen and allows me to set my monitor up in "Twinview" mode. At this point everything would be fine, except I still needed to figure out how to rotate the second screen. There's no option to rotate screens in the nvidia-settings app, but that's ok what about back in 'Monitors' where I saw the option before? Surely now that I've got the screens detected and set up it will work... Nope, In fact the NVidia "TwinView" option is just fooling whatever the 'Monitors' app is looking at and it still only see's one screen (just with a really big horizontal res).

So off to the Internet I go, and find out about a thing called xinerama, an option in the xorg configuration that allows multiple monitor spanning AND as a by-product of treating the screens separately in the xorg.conf file i get rotation too. I set it up and and log out/in and... nothing. Just a lovely purple background without and of the fancy new Unity or anything. So i restart and this time I thing, I'll use classic just in case the Unity is breaking it. This time I get the output from the first screen on the second (black on the first) with the mouse still mapped to the co-ordinated on the black screen, very difficult to use I assure you.

So back to the Internet I go and do a little bit of reading. It turns out that xinerama is incompatible with compositioning (ie Compiz/Unity)... and has been FOR YEARS, the best tool for using a desktop across monitors and it's incompatible with all the fancy desktop effects that Canonical has been pimping these last few releases. 

So I'm at an impasse, either completely change the way I use my computer because Ubuntu is incompatible with how I want it or just change back to an OS that does it with a couple of clicks. 

Now people are going to read this and tell me "But Voney, It's not ubuntu's fault that the drivers don't support rotation", but this isn't the drivers causing the problem they clearly support rotation because I have the screen rotated right now (Classic mode with no effects). 

No the problem is that Ubuntu is unfortunately "not done yet" when it comes to desktop fundamentals, the problems I've described today are not the first time I've run into issues with the way Ubuntu handles screens or other basic Input/Output peripherals. The simple fact is that the functionality I'm looking for is not a big ask of a modern OS, Windows XP was able to do it YEARS ago and OSX wasn't far behind it. If I want to hook up 8 screens to 4 video cards and have some rotated and some not and want to stretch a window across them all I should be able to OUT OF THE BOX (obviously after drivers), when I open the Monitors section of preferences it should show me all the monitors detected across all the video cards and allow me to do with them what I will. If i have a TOUCH SCREEN it shouldn't feel like pulling teeth getting it calibrated and associated with the correct screen (god help me if i want to rotate that screen too). 

So there, that's my rant and that's why I'm going back to Windows on my desktop for another 6 months, if canonical spent half as much fixing these basic issues with how screens are dealt with that they did on Unity then this wouldn't be an issue. But when it comes to Peripherals, Windows and OSX got to the "It Just Works" point years ago.

---

### Post by trekrem on 2011-06-12
There are other Linux distributions you know. By the way, did you search the forum, or ask for help on all these issues you are having?

Edit: No, just as a suspected, you didn't even try. Thanks for playing, enjoy Windows.

---

### Post by voney on 2011-06-12
> **trekrem said:**
> There are other Linux distributions you know?

I'm well aware of that, the issues I've stated are mainly issues with Linux in general. But frankly Ubuntu is the only distro that's even close to being able to play with the big boys. So if they want to be taken seriously as a viable alternative to the commercial OSs they will need to fix these things, even if that means dragging the rest of the linux community with them.

---

### Post by voney on 2011-06-12
> **trekrem said:**
> By the way, did you search the forum, or ask for help on all these issues you are having?

Edit: No, just as a suspected, you didn't even try. Thanks for playing, enjoy Windows.

Here we go... *sigh*

Yes I did search the forums, did you not read my post? I searched the whole INTERNET. And I found answers to my questions because I'm not the only person with this issue. Why on earth would I post a new thread if I already had the answer?

---

### Post by trekrem on 2011-06-12
> **voney said:**
> Here we go... *sigh*

Yes I did search the forums, did you not read my post? I searched the whole INTERNET. And I found answers to my questions because I'm not the only person with this issue. Why on earth would I post a new thread if I already had the answer?

You didn't find answers though, did you?

I suggest you start new threads in the appropriate forums and ask for help.

My suggestion is don't use Ubuntu (at least not 11.04, I am still using 10.04.2 with the 10.10 kernel and backports and PPA etc to keep up to date on my Ubuntu machine) and don't use Compiz (a waste of resources anyway!).

---

### Post by desktorp on 2011-06-12
You're receiving friction because you're being a little bit impatient.  I realize I have no clue how long you actually sat there and tried to hammer things out, but the fact remains that you did not come here to calmly try to get the help you need - you came to tell us how inferior you believe Linux to be, while you storm out.  Knowing Linux as you claim to, you should know that problem solving is part of the territory and that generally, people are going to want to help you, if you give them the chance.  You know that.

---

### Post by voney on 2011-06-12
> **trekrem said:**
> You didn't find answers though, did you?

I suggest you start new threads in the appropriate forums and ask for help.

I'm sorry trekrem, I'm not here to have an argument. 

Yes I did find answers, the answers were NO.

xinerama is fundamentally incompatible with RandR and compositioning, you can't use one and the other at the same time. At all. 

Regardless of that, the point of my post was more general than todays issue, it was pointing out that there are still fundamental flaws with the way Ubuntu/Linux handles screens and other peripherals and that I believe they should be seen as priorities above making the thing pretty and shiny.

---

### Post by wolfen69 on 2011-06-12
Use what works for you. I do, and that's linux. I built a linux compatible computer, so needless to say it runs pretty much perfect. Much better than windows ever did, that's for sure. We all need to just be happy that we have so many choices. Whether it's windows, mac, linux, use whatever gets the job done.

Feel free to stick around here in the community cafe or whatever, as there are a lot of great people here that just like to chat and have a good time. There are actually a lot of windows and mac users that hang out here. Have fun!

---

### Post by ventrical on 2011-06-12
Iv'e worked with Unity/Natty and Mint 11. Mint 11 warns from there opening webpage to "be aware" of upstream changes that will affect 'compiz'. In fact, in my own opinion, (and has been reported by others) that the flaw is not with Ubuntu per se, but, rather with the Unity Plug in and Compiz. Even in Gnome Classic, if a COMPIZ setting is changed the system will pretty well bust. It's happened to me a few times already. I can understand your frustration. And yes.. there is substantial down_time searching for answers but I pressume that this is part of the learning curve. I more or less had to decide to perservere and try to solve the problems. If I can then backstep to a stable release.

With all my PCs I can get the 'cube' working just great until as soon as I install or try to run Unity/Natty then I more or less have to accept that the 'cube' is just not happening.. at least for slightly older machines.

So it is no secret that there are 'known bugs' with natty and compiz and most likely this may be the cause of your screen probs. I can only wonder if you were able to achieve the required results with an earlier version.

---

### Post by 23dornot23d on 2011-06-12
I must admit you usually get a good feel for a situation by doing a [**quick search**]("http://www.google.com/search?client=ubuntu&channel=fs&q=xrandr+rotating+screens+linux&ie=utf-8&oe=utf-8")
and as you say most responses are negative ..... also [B][search on solved]("http://www.google.com/search?client=ubuntu&channel=fs&q=xrandr+rotating+screens+linux&ie=utf-8&oe=utf-8#sclient=psy&hl=en&client=ubuntu&channel=fs&source=hp&q=xrandr+rotating+screens+linux+solved&aq=f&aqi=&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=5014d35bb6efb157&biw=946&bih=489")[URL="http://www.google.com/search?client=ubuntu&channel=fs&q=xrandr+rotating+screens+linux&ie=utf-8&oe=utf-8"]
[/URL][/B] 
I too had similar problems ....  especially with xinerama ... could get the mouse on one screen but would not jump to the other one .... even tried scripts to do it .... no luck ..... but not to say it cannot be done as I have seen other reports of people having success with it. ( just its hard to find there xorg.conf 's ..... and even with them chances are our hardware will be different - but I prefer to stay positive - at some point this may become a lot easier to set up ..... but it needs users 
like us to take time out and try things out )

I run 3 screens on Nvidia ... but I do not rotate them ..... but I did find similar to the 
original poster that many problems still exist - but as with anything if they are ever going to
get solved we need to take the first steps to work the solutions out.

The thing that I have always understood with Linux though is the more people that are 
affected - the more chance of a solution.

I doubt we have many people on here wanting to do what you want with 2 screens .... but
that is not to say that the task is impossible to solve .....

It just takes time .....

But as said .... use whatever works .......

---

### Post by Shibblet on 2011-06-12
I somewhat understand what he is going through.  Sometimes we find answers to our questions of why this doesn't work, and why this does, but here's a workaround, or a fix.

When you know that there is a simple solution with Windows, sometimes is just less time consuming to do it that way.  For example:  I dual boot Ubuntu and Windows 7.  I use Windows 7 for playing games with Steam, and Ubuntu for everything else.

Now, I know you can get Steam to work in Ubuntu, and get my games to work in Ubuntu as well... but HOLY CRAPSTAINS ON A TURTLE, I don't have the patience to screw with making Wine get games to work correctly.

Wherein Windows, I just have to run the game.  No fiddling, to futzing, just run the game.

My suggestion to you, is to set up a dual boot system.  This will give you the time to learn Ubuntu's strengths.  If having a partitioned drive doesn't work for you, use Wubi to to install Ubuntu.  That allows Windows to be your primary OS, and you can boot to either OS with the Windows Bootloader.  If you get sick of Ubuntu, then just delete it inside your Windows Add/Remove Programs.

---

### Post by voney on 2011-06-14
Thanks guys, I appreciate the comments.

@ wolfen, I'm a lurker and have been for years. Thanks for the invite though, I've never really looking in the community cafe section...

@ 23dornot23d thanks for the links, I actually have my screens set up exactly how I want them and did have when I wrote the first post. It's the incompatibility with unity/compiz that's still an issue.


And thankyou to all the statements that are saying "use what works for you", that is really the phole point of this thread in the first place isn't it? I stand by my statement that Cannonical are focussing in the wrong places. The difference between Ubuntu and say Debian or Gentoo is that Cannonical is trying to present the OS as an amalgamous whole that is supported by the open source community with additional apps and functionality. If it wasn't trying to do that then you could just call Ubuntu a re-skin of Debian, but you can't because of all the extra work Cannonical puts in to get all the apps and installers to play nicely together so from the users point of view it's all easy.

My point at the end of the day is that the focus is in the wrong place. It's useless making an OS look fancy if the core userspace functionality isn't there. Windows 7 isn't better than XP (we'll forget Vista) because it's prettier or because it has gadgets and themes, It's better because Microsoft put a huge amount of work into making it easier for the user to configure things the way they wanted, the biggest leap being in the way devices/drivers are handled. Similarly the jump from OS9 to OSX removed a whole lot of basic userspace device/settings configuration headaches.

---

### Post by NightwishFan on 2011-06-14
Yeah feel free to stick around. :) I am a Debian user full time now but I also like Ubuntu. I know a lot of folks and am familiar here so I post and help Ubuntu users as well.

I advise if you would like to use Ubuntu to stick to the LTS releases. They have always been fantastic for me. Upgrade every 2 years. :)

---

### Post by wolfen69 on 2011-06-14
> **voney said:**
> 
My point at the end of the day is that the focus is in the wrong place. It's useless making an OS look fancy if the core userspace functionality isn't there. Windows 7 isn't better than XP (we'll forget Vista) because it's prettier or because it has gadgets and themes, It's better because Microsoft put a huge amount of work into making it easier for the user to configure things the way they wanted, the biggest leap being in the way devices/drivers are handled. Similarly the jump from OS9 to OSX removed a whole lot of basic userspace device/settings configuration headaches.

I'm sure a lot of people will disagree with you. I guess we see things as we do, and in the end you or I are not going to change people's minds. So basically, arguing is a waste of time. We all need to go our separate ways and keep doing what we do. Good luck.

---

### Post by mastablasta on 2011-06-14
> **voney said:**
>  Windows 7 isn't better than XP (we'll forget Vista) because it's prettier or because it has gadgets and themes, It's better because Microsoft put a huge amount of work into making it easier for the user to configure things the way they wanted, the biggest leap being in the way devices/drivers are handled. Similarly the jump from OS9 to OSX removed a whole lot of basic userspace device/settings configuration headaches.
 
you are quite right. 
 
And i get the point - the point is things should be easy to set up. users shouldn't be searching the web for solutions, compiling codes/kernels etc. basic things in OS should work. there is no excuse for this. and "selling" (ok offering) an OS like a good OS, like people do on Ubuntu site bragging what things you can do with it and how modern it is and then it fails in tasks present in windows OS for some time now.
 
Whatever you say windows is user friendly and more so than Ubuntu. side product is that being user friendly also makes it malware friendly.

---

### Post by 3rdalbum on 2011-06-14
So few users have multiple monitors, so it's certainly not an issue that's holding many people back from Ubuntu.

You are correct though, multi-monitor support and configuring X needs to be totally redesigned and rewritten.

However, it is also fair to say that Xorg has some features that Windows 7 and Mac OS X still do not have, that are just as useful as multiple monitors.

---

### Post by Tamlynmac on 2011-06-14
> 3rdalbum
So few users have multiple monitors, so it's certainly not an issue that's holding many people back from Ubuntu.

I sincerely don't wish to be argumentative and respect all you've done.  However, you made a statement that infers you have knowledge that may  enlighten others. I have no idea how many Ubuntu users use multiple  monitors, if I may ask - where did you find that data? Or, is that just  your assumption based on your own experience?

As I said, I'm not attempting to imply that you don't know. I'm only  interested where you acquired said data. IMHO, all to often statements  are made in this section that aren't substantiated. It's been my  experience that numerous users I've assisted with installing Ubuntu do  use multiple monitors. Especially, those who have laptops.

---

### Post by wolfen69 on 2011-06-14
> **Tamlynmac said:**
> I have no idea how many Ubuntu users use multiple  monitors

I can't speak for ubuntu users specifically, but in my experience as someone who has a computer repair business and makes house calls frequently, I can say that very few people have multiple monitors. As a matter of fact, I can only recall one customer that had 2 monitors. So I'm being lead to believe that it is not that common for people to have such a setup. But there's no way I can give hard figures on what % do.

---

### Post by Tamlynmac on 2011-06-14
> wolfen69
But there's no way I can hard figures on what % do. 	  	

Which was exactly my point. If we make statements that can't be substantiated, we should (at the least) point out that said statement reflects one's own opinion or is based on one's own experience.

As I said, I don't wish to be argumentative or to debate in this section. My only concern is that when a statement is made and left unchallenged, it may appear as a truth - even if it's wrong or contains an error.

As I indicated, my experience has been quite different and I provide assistance to >28 personal Ubuntu PC systems owned by friends, family and associates - on a regular basis (5 of which are owned by my family). Not to mention, helping some local centers. As you know I'm limited by my disability, but that doesn't seem to slow them down any. :D

---

### Post by Rasa1111 on 2011-06-14
> **wolfen69 said:**
> Use what works for you. I do, and that's linux. 

+1
Same here.

Ubuntu has not failed me yet, on all of the machines Ive installed it on. 
Not even on my _*old*_ machines. 

Windows however, Often failed me. 

Back to windows... never. :p

---

### Post by misterbiskits on 2011-06-14
This is a good thread.  I have similar feelings/experiences about some of Ubuntu's shortcomings. 
I use multiple monitors.  An operating system should take care of the messy business of installing drivers and making available the options one would expect.
Instead of fixing up the fundamentals, "Look!  Unity!  This will attract more new users to try out ubuntu!"  And once the glitz wears off the pesky fundamental problems will become apparent.

---

### Post by wolfen69 on 2011-06-14
> **misterbiskits said:**
> 
I use multiple monitors.  An operating system should take care of the messy business of installing drivers and making available the options one would expect.


Well to be fair, most people I know would have a hard time configuring dual screens in *any* OS. 

But it helps if you make sure your computers are linux friendly to begin with. I've  had  at least 5 different video (Nvidia) cards in the last 7 years, (yes, I've upgraded the mobo a few times also) and each one was *very* easy to get dual monitors going. 

If one went into linux with the same mindset as they would when buying a windows or mac computer, there would be a lot less problems. Build your own, or buy preinstalled. But it's the truth. If you want the best linux experience, you need to buy compatible hardware. And actually, windows with a custom pc is also a good thing in the right hands. Pre-built win machines can be, uh, a pain in the butt.

How many people get OS X on a non-apple computer? If you want a mac/OSX, it comes with hardware already matched. If you go to BestBuy® and buy a windows computer, guess what? You're hardware is matched up with the OS.

Without building your own computer, or buying preinstalled with linux, it's just a roll of the dice. I do it the easy way and only choose linux friendly hardware. I urge everyone to do the same. It's a nice feeling when you can run *any* OS, and they all run great. 

Otherwise, good luck to you. :P
:guitar:

---

### Post by mastablasta on 2011-06-15
> **wolfen69 said:**
> Well to be fair, most people I know would have a hard time configuring dual screens in *any* OS. 
 

 
i don't have a monitor, but i do have a HDTV hooked up to my computer so i can watch DVD movies and all from computer. A few of my colleagues have it doen liek that too. thoguht really only a few.
 
here is for example how you do it in WindowsXP with ATI card. you plug in the second monitor, you go to ATI control centrer and say clone desktop or whatever you want to do and click ok. BOOM! two monitors.
 
want to rotate one? well there is ATI icon in tasbard you click on it a menu pops up, select which one and how much you want to rotate and BOOM! it's rotated. or whatever you want to do with it. easy peasy.
 
though i don't have need for rotation seting up two monitors has been as easy as that since windows98. i remember i set up S-video to my TV when i bought my first card with tv output. it was just like that. hook it up two click later we were watching movies on (at the time) large TV set (still no plasma and LCD back then).
 
and Woflen is completelyl right when he says that computer needs to be OS compatibel to begin with, however too many times we see regression bugs in Ubuntu linux. so a thing may work now but stop working after an update. to me it happened with Opensource graphics drivers. ok things were fixed 2 weeks later but these kind of things shouldn't happen in the first place. if something works it works.

---

### Post by NightwishFan on 2011-06-15
I do not have a second monitor but if I want to rotate mine. Click rotate BOOM it works. :)

---

### Post by iponeverything on 2011-06-15
I fail to see how missing functionality in a third party driver is a "desktop fundamental" 

regardless, you gave it good go..

---

### Post by mastablasta on 2011-06-15
because in windows this is actualyl sort of built into the system where you manage desktop. also the system needs to be capable of funcitoning in a flipped desktop, no?

---

### Post by iponeverything on 2011-06-15
> **mastablasta said:**
> because in windows this is actualyl sort of built into the system where you manage desktop. also the system needs to be capable of funcitoning in a flipped desktop, no?

indeed - and it can, but not with every combination of hardware.

I like Linux, I use linux - but I am all about choice..  

I choose linux because I get a little tweaked when the an OS balks on HDMI output or playing an legit image file because of vendor imposed restrictions that require a special DRM blessing in order to function. --

---

### Post by misterbiskits on 2011-06-15
I understand that it is preferred to custom build a computer specifically for ubuntu.  I can accept that.  
What I can't accept is that while ATI offers a driver for each of four different cards (on three computers), ubuntu doesn't properly install them when I click 'activate'.  
That button should instead read: "destroy my video and make me have to mess around to get it back".
All of these cards are supported with drivers, how can it be a hardware issue.  It's just plain bugginess and it's that kind of bugginess which turns people off.
I like Ubuntu.  It lets me tinker around and play computer-geek.  But when it forces me to tinker around I get annoyed.

disclaimer: To be fair, that was about 2 months ago.  It may (or may not) have been fixed since (and I've found my own solution).

---

### Post by arunb on 2011-06-15
I never had problem with dual monitors on Ubuntu 10.04.

If you are serious about using Ubuntu, use a version that is tried and tested and also use hardware that is supported by Linux.

I confess I did not read your post entirely but from the sound of it, you need to do more research on the hardware/software you are using. 

Are the features you mention supported by Linux ??

---

### Post by Jacobonbuntu on 2011-06-15
...it is said before, but apparently not enough....
 

 It is a great accomplishment that (far) most hardware works out of the box with Ubuntu-Linux. Just imagine the immense amount of work to be done and to maintain, that Microsoft or Apple can just delegate. Meanwhile be aware of the fact that these companies have much bigger (commercial) budgets for their work.  
 Altogether one can conclude that Ubuntu/Linux and the open source community is doing an unbelievable job with the soft- and hardware in general. Exotic exceptions will always be.

---

### Post by coolglobal on 2011-06-15
Referring to the first post, it sounds like you want portrait and landscape monitors? This is a very productive arrangement. Yeah, there needs to be an easy way to do this. I've just organised 2 monitors landscape landscape, it took 5 minutes with the Nvidia app. Landscape portrait is useful for all kind of stuff. Photo editing, charts, writing and so on. Uncommon though.

---

### Post by misterbiskits on 2011-06-15
> **Jacobonbuntu said:**
> ...it is said before, but apparently not enough....
 It is a great accomplishment that ... the immense amount of work to be done and to maintain, that Microsoft or Apple can just delegate.
Yes, yes - excellent work devs everyone gets a pat on the back and all that.  No one is saying they aren't doing a great job and providing a much appreciated service.
The question is why is it so difficult to follow and apply the standard that microsoft and mac delegate?  Is it secret information?

---

### Post by Shibblet on 2011-06-15
> **iponeverything said:**
> I fail to see how missing functionality in a third party driver is a "desktop fundamental"

It's the age old argument.  If Ubuntu (Linux) doesn't work out of the box, then it's the OS that has problems.  People think Windows works flawlessly.  But no one can do a Windows install and not have to install drivers.  Windows doesn't work "Out of the box" either.  

Windows and Linux are about equal at detecting hardware.  Linux actually seems to be better at detecting newer hardware, from what I've seen.

But to answer your quote, third party driver functionality is better in Windows, mainly because it's there.  Every hardware manufacturer writes a Windows driver, not all of them write Linux drivers.

It's funny... if all of the hardware manufacturers wrote drivers for Linux, or at least open sourced their drivers, Linux would be near flawless.

---

### Post by el_koraco on 2011-06-15
Did I yawn at this thread yet? if not, I'm yawning now.

---

### Post by overdrank on 2011-06-15
On that note thread closed :)

---

