---
title: "Better intergration of vitual environments"
date: 2007-05-26
forum: The Cafe
---

### Post by corvax on 2007-05-26
Not sure if this is the proper place for this but......Id like to see somthing using zen or kqemu or any free open virtualization implimentations in ubuntu that would let you install xp vista etc etc and customize it so that any windows apps games etc that are installed create a shortcut in the menu or on desktop or both (your choice?) in ubuntu and when clicked on within the linux environment from the desktop etc launches the app/game etc full sceen within xp or vista in vm  and make running windows apps from he linux desktop seem seemless. What im talking about is integration here.
what do you guys think?
Edit/Delete Message

---

### Post by Ireclan on 2007-05-26
Sounds cool. Not sure how hard it would be to implement, though. It would DEFINITELY make the integration of virtualization seamless, as you suggest. However, I would say that, in order to avoid confusion over which applications are native and which run in virtualization, the shortcuts for such applications should be placed in a different sub menu from the native applications. On a side note, you need to slow down when you type- I'm sure you didn't intend it, but your current typing style brings to mind someone very hyper talking super fast!

---

### Post by corvax on 2007-05-26
Thanks for the response. A different submenu as you suggested is what is used for wine and would be great.
I think that this would be all that ubuntu needs to truly gain alot of mind/marketshare. This would ease the transition to linux and make it so those one or two legacy apps that some people have will be able to be used untill there is a suitable replacement. It would be one less excuse taken from those who say they cant use ubuntu because (insert excuse here).

---

### Post by starcraft.man on 2007-05-26
Ubuntu's mission statement is not to provide easy virtualization (it is [here).]("http://www.ubuntu.com/products/WhatIsUbuntu") It is to make a distribution of Linux so that everyone can use it, learn and be supported on it well and employ native linux applications in a transition away from proprietary products ( thats how I see it).

That said, virtualization is already as easy as I think it can get. You can install vmware and vbox real easy, and install any linux/windows OS really easy. Then you open them up and open the program. You can't (at least I don't think the way VMs work) just launch an app from a window, the VM has to be open and the very idea of a Virtual machine isolates it from direct interaction with your primary OS (which is what it would be doing, if it was integrated with the menu). What you want is [WINE,]("http://www.winehq.com/") and it is already existing.

In the end, Ubuntu's job is not to easily run windows applications, its to be a Linux distribution that everyone can use. If people require all windows applications (like PS and Office 2007) they have an OS for that, its called Windows.

Thats my opinion, and if you really want it, put it in the gutsy gibbon dev section.

---

### Post by AndyCooll on 2007-05-26
[QUOTE=starcraft.man;2725805]What you want is [WINE,]("http://www.winehq.com/") and it is already existing./QUOTE]

And continuing what startcraft man has said, you can manually create a launcher for a game (for instance). I have one for Football Manager. I click on it and it launches FM using Wine.

:cool:

---

### Post by corvax on 2007-05-26
I dont think something like what i suggested should be part of ubuntu and doesnt even have to be in their repos neccesarily.  Wine is good for some things but it doesnt cut it for many.  I use wine when i need to but once in a while i have to use win xp in vm because theres somthing i cant do with it. For instance i used to use the paltalk plugin for gaim , paltalk  shut it down it no longer works. I tried to get it going in wine. It loads i login but the chat room menu doesnt show the rooms so i have to use winxp in vm. I have a launcher to load xp but how do i make it so i can launch paltalk directly via a launcher? I guess i could have it run on startup but thats kinda lame.
If i have xprunning in vm in the background what would be the command to launch the application from the cli?

---

### Post by starcraft.man on 2007-05-26
> **corvax said:**
> I dont think something like what i suggested should be part of ubuntu and doesnt even have to be in their repos neccesarily.  Wine is good for some things but it doesnt cut it for many.  I use wine when i need to but once in a while i have to use win xp in vm because theres somthing i cant do with it. For instance i used to use the paltalk plugin for gaim , paltalk  shut it down it no longer works. I tried to get it going in wine. It loads i login but the chat room menu doesnt show the rooms so i have to use winxp in vm. I have a launcher to load xp but how do i make it so i can launch paltalk directly via a launcher? I guess i could have it run on startup but thats kinda lame.
If i have xprunning in vm in the background what would be the command to launch the application from the cli?

I think your missing the point. The nature of a _Virtual Environment_ forbids what you want to do. A VM (Virtual Machine, it is the software you emulate with, virtualbox for instance) is only designed to create a self contained and seperate environment from the Host OS (Ubuntu for us, Host OS is whatever you install the VM software on). They all operate by mapping out exactly how actual hardware responds to software, and replicating it through software means (taking x request from software, and mapping Y response from hardware back into the VM). There are many good reasons why it is self contained, most importantly is so that if a person is testing (I know people who run all versions of WIndows (98 to Vista) for testing) get a virus or a cascading problem (critical errors and other serious exploits/crashes), it cannot spill over into the Host OS and crash/corrupt your OS. There are even likely such problems that could occur on Ubuntu, even if its not likely to be a virus. 

You want a launcher to be put into the Menu, which will not only launch your VM but also send a command within the Virtual Environment, that violates the principle of separation of the Host OS from the VM OS. None of the products want this interaction, because it can then allow coders to find the means by which they bypass the container and allow malicious code to be inserted into the host computer. Thus, what you want, won't happen ever. It goes against the interests of almost all VM users and makes it insecure. You can tell the OS in the VM to launch the app at startup, or you can hack an open source VM until you have created a means for code injection from host to VM OS.

I hope that helps understand how VM works, WINE is different and can make a launcher because it is simply an application layer, it runs in between the OS and the App and makes sure all singals are translated on the fly. It is also very dumb (no offence WINE devs and folk) as it only implements the API and protocols needed for certain apps, rather than programming a complete environment (which is both time consuming and unnecessary since VMs provide complete implementation).

Thats it for VM explanations, I hope you understand how it all works now. I also hope I was clear in my explanation, on to other things now :D. I suggest setting the app to startup, thats the easiest means.

Oh and thanks for catch andy, I forgot to mention that. :)

---

### Post by YokoZar on 2007-05-26
> **starcraft.man said:**
> I hope that helps understand how VM works, WINE is different and can make a launcher because it is simply an application layer, it runs in between the OS and the App and makes sure all singals are translated on the fly. It is also very dumb (no offence WINE devs and folk) as it only implements the API and protocols needed for certain apps, rather than programming a complete environment (which is both time consuming and unnecessary since VMs provide complete implementation).Note that this "dumbness" is very intentional on Wine's part, since the lack of having to create an entire virtual environment will allow the application to run at native speeds - sometimes even faster than in Windows itself.

---

### Post by starcraft.man on 2007-05-26
> **YokoZar said:**
> Note that this "dumbness" is very intentional on Wine's part, since the lack of having to create an entire virtual environment will allow the application to run at native speeds - sometimes even faster than in Windows itself.

Course, I was kinda implying that I guess. I mean it would be folly for WINE to reverse engineer all of Windows, and take a really long time, and not only would it make it slower, it would allow any virus to run in WINE (whereas now only select viruses that target the specific API/protocols implemented in WINE or the Apps running in wine themselves work).

Just curious from your avvy, you a WINE dev? Just an avid WiNE user?

---

### Post by Adrenal on 2007-05-26
Hmm, it's a nice idea, but surely the system requirements would be bordering on absurd.

---

### Post by starcraft.man on 2007-05-26
> **Adrenal said:**
> Hmm, it's a nice idea, but surely the system requirements would be bordering on absurd.

The system requirements to run a VM? I run a fully functional even fast XP Pro(inside Ubuntu, while browsing and other things) on an old 2.4 P4 with 512 GB ram (I limit the VM to 512, I have 1 GB total on the mobo).  VMs don't require that much power.

If your referring to how much effort it would take to create a secure path into the VM via the Host OS, I don't think the problem is that its difficult, but that it defeats the purpose of creating an isolated VM, it exposes you to unnecessary threats if a hacker coded a virus to somehow become aware of the VM and tunnel out into Host. I don't think it'll happen unless someone writes their own hack, most VM devs are interested in increasing the power of the VM, not interaction with the Host.

---

### Post by maniacmusician on 2007-05-26
> **starcraft.man said:**
> The system requirements to run a VM? I run a fully functional even fast XP Pro(inside Ubuntu, while browsing and other things) on an old 2.4 P4 with 512 GB ram (I limit the VM to 512, I have 1 GB total on the mobo).  VMs don't require that much power.

If your referring to how much effort it would take to create a secure path into the VM via the Host OS, I don't think the problem is that its difficult, but that it defeats the purpose of creating an isolated VM, it exposes you to unnecessary threats if a hacker coded a virus to somehow become aware of the VM and tunnel out into Host. I don't think it'll happen unless someone writes their own hack, most VM devs are interested in increasing the power of the VM, not interaction with the Host.
I would  be very envious indeed, if you really had 512 GB of RAM :)

---

### Post by starcraft.man on 2007-05-26
> **maniacmusician said:**
> I would  be very envious indeed, if you really had 512 GB of RAM :)

ROFL!!! M M MMM MMM... ha, was in 5 different aMSN convos and an old friend. Silly me, no mobo can support half a terrabyte of RAM :p Though I too would be happy if my Mobo could support GB sticks of ram, but its a 6 year old card, I think it maxes at 1 GB. I need a new comp some time.

---

### Post by Adrenal on 2007-05-27
VM's don't take much, but a seperate vm for each app(which was how i read it) would quickly take its toll

---

