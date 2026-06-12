---
title: "Ubuntu 16.04.3 LTS - Optimizing (drivers on) new desktop?"
date: 2017-08-14
forum: Ubuntu, Linux and OS Chat
---

### Post by funked up on 2017-08-14
Hello there, I just bought a new medion desktop:
i7-7700 CPU @ 3.60GHz × 8
GPU GTX 1060 - 6GB
RAM 16GB
SSD 240
HDD 2TB

It was pre-installed with windows 10 and after struggling with UEFI I finally got it to dual boot with ubuntu 16.04.3 LTS.
I've noticed that on windows some HD videos play more smoothly than with ubuntu. I have made all the updates I was prompted to and that's all.

Any suggestions on what to do so I can fully use the desktops potentials? Do I need to download any nvidia drivers?
I'm not a gamer. I need my computer for music and video editing and I use Ardour, Audacity, Blender, Kdenlive, Gimp, Darktable etc

There are a lot of things I love about Linux but there are a few things that sometimes make me think about switching to windows or mac after 6, 7 years.
1. Some drivers issues.
2. Printing and scanning issues. 
3. Music and AutoDesk programs.
4. The all time problem with the high running non stopping fan even when nothing no program is running.
Actually the last one is the most annoying considering the specs of my new desktop. When I boot with windows 10 there is no fan issue.

Thanx in advance for any help,
George.

---

### Post by Futant on 2017-08-15
One of the things about having brand new tech and using linux is that it may take a while for your hardware to be fully supported, and you might have to be patient or even helpful - identifying problems and helping to fix them. Remember that linux is a constantly evolving, collaborative effort!  Try using different drivers, or newer kernel versions, use what works best. In time you'll probably see things improve.

For help with specific issues, make one post for each issue and provide relevant details so people can help.

---

### Post by funked up on 2017-08-16
Thank you for your reply Futant.
You are right about me not making a specific post about the problems I have stumbled on. 
The thing is that I've been searching the internet for all of those issues I mentioned and it seems that these are very common problems among ubuntu users.

Let me give you some more info on what I mean:
- fan problem: When I boot with ubuntu my desktop's fan is running very high all the time. 
  Even when I don't do nothing and the screen saver takes over. It doesn't make a difference if I have 10 programs running or none. This is not happening when I boot with windows 10.
- printing and scanning: There is a well known problem with scanners and ubuntu. You may have a plug and play scan and print device where printing works fine and as a scanning device it is not even detected.
  By the way, printing high quality photos is another weak point. You need to spent hours or days on the internet to make it work just fine. But "just fine" isn't good enough for most people who have not the knowledge nor the time to make things work. 
  With windows or mac it's almost like plug and play.
- driver issues: I'm a musician and with my instruments I use some REALLY ridiculously basic software to import and export sounds to and from my keyboards (I mean instrument keyboards, not computer keyboards). 
  I've tried wine and the software worked fine, BUT the usb drivers could not recognize/connect with my instruments. Again in windows or mac it is a matter of plug and play.

The problem is that these issues are not new. They are known issues for years now, and it is not nice to see all these new versions every half year with discussions about the end of unity or what flavour looks better.
There are even screen saver contest!

Please don't get me wrong, I love Linux but sometimes these issues are frustrating. 
Believe me when I say that most people just want a computer that just works as you expect it to do!

So my question is: Are there any suggestions or guidelines on how to optimize my desktop with the specs I mentioned in the initial post?
If someone has a solution to the other issues I mentioned please feel free to give me some light.

---

### Post by Mark Phelps on 2017-08-16
I understand your frustrations with stuff not working in Linux -- but consider that companies PAY folks to write and test Windows drivers for their new hardware;  they do NOT pay folks for Linux drivers.  

So, you're at the mercy of a community largely composed of volunteers when it comes to stuff working in Linux.  That's one reason it' so critical to post individual concerns one at time -- so the community member who have experience with that concern can response.  When you say "driver issues", no one can respond because that it too vague to be useful.  You have to provide specifics of the make and model hardware to get detailed help.

Furthermore, these issues will continue to be frustrating -- as new hardware is coming out all the time, and WITHOUT Linux drivers for it.

Eventually, the Linux community will probably catch up, but no one can say when that will happen for any particular hardware.

---

### Post by wildmanne39 on 2017-08-16
*Thread moved to **Ubuntu, Linux and OS Chat since it is not as support request.**.*

To get help with each issue start a separate thread for each issue in the most appropriate forum with a descriptive title please. If you just want to discuss the issues you can do that in this thread.

Thanks

---

### Post by vocx on 2017-08-16
> **Mark Phelps said:**
> I understand your frustrations with stuff not working in Linux -- but consider that companies PAY folks to write and test Windows drivers for their new hardware;  they do NOT pay folks for Linux drivers.  
...

Very well said. Basically, the market dictates what software the manufacturers support. If there is particular USB device that is specialized, and the manufacturers know only a few select Windows users will need it, then they won't bother creating necessary drivers for the Linux kernel. They don't have a particular mandate to support all possible computer systems, they only care about keeping their current Windows and Mac paying customers happy, so that's what they would support.

In my opinion such companies take the wrong approach, because if they provided Linux kernel drivers that are open source, their device could be supported in a multitude of different systems that run Linux. So, for example, if there is a Linux kernel running inside a smart TV, smart house, smart refrigerator, smart telepresence robot, or whatever, your specialized USB device is immediately supported there as well, which gives you a bigger market and possibly even bigger revenue. But the hardware manufacturers don't see it that way.

Linux wants to support as many devices as possible. There is not a single guy at the top laughing and saying "ha ha, I won't develop a driver for funked up's fancy USB device, ha ha, I'm evil." Either the manufacturers help with the drivers or they don't.

---

### Post by mastablasta on 2017-08-17
> **funked up said:**
> Thank you for your reply Futant.
You are right about me not making a specific post about the problems I have stumbled on. 
The thing is that I've been searching the internet for all of those issues I mentioned and it seems that these are very common problems among ubuntu users.

no they are not common. also if you want to run ubuntu but have problme on install , then getting a PC preinstalled with it makes sense. you dont' get any issues on windows preinstalled PC and on OSX preinstalled PCs.

> 
- fan problem: When I boot with ubuntu my desktop's fan is running very high all the time. 
  Even when I don't do nothing and the screen saver takes over. It doesn't make a difference if I have 10 programs running or none. This is not happening when I boot with windows 10.


it is still not too helpful. you can install psensor to see what is going on. i think it could likely be nvidia card running on reverse enginered drivers. for starters use additional drivers application to install nvidia drivers.


> 
- printing and scanning: There is a well known problem with scanners and ubuntu. You may have a plug and play scan and print device where printing works fine and as a scanning device it is not even detected.
  By the way, printing high quality photos is another weak point. You need to spent hours or days on the internet to make it work just fine. But "just fine" isn't good enough for most people who have not the knowledge nor the time to make things work. 
  With windows or mac it's almost like plug and play.


hard to troubleshoot sicne we do not know what printer you have. it is also plug and play in linux if printer has the linxu drivers. HP printers have them, samsung priners and i think brother has them as well. you plug in an HP printer and it just works. 

> 
- driver issues: I'm a musician and with my instruments I use some REALLY ridiculously basic software to import and export sounds to and from my keyboards (I mean instrument keyboards, not computer keyboards). 
  I've tried wine and the software worked fine, BUT the usb drivers could not recognize/connect with my instruments. Again in windows or mac it is a matter of plug and play.

Do the instruments have any linux drivers available? if they don't then the OS cant recognies them. but let's say they are just USB storage and is recognised by program in WINE. wine is not widnows it is a ocmpatibility layer that help you run some windows programs in linux.  if you use mostly windows based programs then it is better to use windows as an OS.

the issue does not exists in windows because:
- somoene loaded drivers for windows to windows (possibly payed Microsoft to include them in OS) 
- somoene tested drivers and reported bugs and then the company resolved the bugs
- the program for using the device was made for widnows and with windows in mind

if they did all that for linxu as wlel the issue owuld not be here. but they didn't. why they didn't do it for linux? we'll you should ask the company that makes the device, not the OS makers. but porbably they didn't make it because desktop linux is less than 2 % of the market.

> 
The problem is that these issues are not new. They are known issues for years now, and it is not nice to see all these new versions every half year with discussions about the end of unity or what flavour looks better.
There are even screen saver contest!


you probably think that we discuss some offtopic things rather than getting to work and solving the problems in linux. but you missunderstood it completelly.

1. we are just users like you. for example i do not have any programing knowledge. maybe i can help you troubleshoot some issues. but i do have certian visual preferences which i then discuss (sometimes) with other users here. e.g. like how KDE And XFCE are better than Gnome or Unity :P

2. developers are elsewhere and they focus on OS or their particlular project. some even do amazing stuff like reverse engineer drivers. it's like you see a TV in show, now go make one in your room from sratch using stone tools. of course end product won't be perfect.

3. companies that make devices should create drivers for OS

4. users can help developers by posting about issue in the propper place (= Launchpad in case of Ubuntu). there you can say with correct error reports and logs to developers: "Hey i have an issue / bug that needs to be fixed. anyone out there that can help?" sometimes the issue remains unresolved. but many times they solve it. it might take time. last year i posted about a very specific issue that most people would not see in Libre office. this year someone with knowledge picked it up and resolved it. solution was rather simple, but some expert needed to be alerted to the issue and they had to get as much data as possible on it. 5 or 6 other people contributed to the bug report until finally they found the culprint and resolved it. point it i often can't solve it but i can help others solve it.

5. think of linux as castle made from bricks. it's modular. things can be added or removed almost at will. many times developers focus on one part (one brick). if oyu know what brick is causing issues you can get help easier. e.g. in your case you have power management issue. if you can narrow it down to either motherboard or GPU you will have a lot greater chances of solving it.

6. if you want to use Linux but do not want to battle it all the time: [https://linuxpreloaded.com/](https://linuxpreloaded.com/) 

7. linux give you great power over computer. you should embrace it. and start exploring it. everytime you resolve an issue you learn something from it and you personally grown. it is then even better if oyu post about it so others with same issue can find it and resolve it as well.

8. Windows 10 is a good OS. i use it at work. we use widnows based apps. if you have too much issues with linux just use windows. use what works best for you.

---

### Post by gordintoronto on 2017-08-17
With new hardware, you should use 17.04. Then install an "additional driver" for your GPU.

---

