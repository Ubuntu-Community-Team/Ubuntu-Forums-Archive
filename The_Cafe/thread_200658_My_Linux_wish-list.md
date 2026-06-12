---
title: "My Linux wish-list"
date: 2006-06-20
forum: The Cafe
---

### Post by Sternfan on 2006-06-20
I have spent much of the last year getting familiar with Linux – using mostly FC3, FC4, FC5, Ubuntu and Linspire. I settled on FC, since I had some introductory experience with it years ago in tech school. After experimenting with it in a lab scenario, and then implementing several machines for younger students where I work, I have come up with a few things that could make it easier to get the most out of Linux. I am sending a copy of this to online forums relating to the distros I mentioned, in hopes that someone, somewhere will consider these suggestions in future releases of their particular distro. There are just a handful of them, but if they were implemented, I could see a lot of network admins in similar situations as myself make the move to Linux.

I am also hoping that as a community, we could start a “top ten list” of things that should be added to future distros... I don't have ten items, but I think this is a good start. And please take this as constructive criticism – I want to be able to expand Linux usage in the future.

My List:

Roaming Profiles – my current users have been using roaming profiles for years (win2k) and are genuinely flustered when using a Linux box and their settings do not “follow” them. Please don't misunderstand – I am not asking for a Linux box to use a win2k profile – I just need Linux profiles to follow to other Linux boxes. Setting up logon scripts etc. is a partial solution – but not a real substitute for Roaming Profiles – desktop shortcuts, Firefox bookmarks, email setting in Evolution are all examples of things that need to move with a user.

VNC – I find this particularly frustrating – that a remote Linux PC is not setup by default to have this service enabled at all times. I assumed that it was, and installed several Linux PCs at a remote location across a WAN link, and was not pleased that I could not VNC into any of these boxes to install software, run updates etc. after a reboot. After investigating for a while, there are certain steps that can be taken to remedy this (though I still cannot get this to work) but they are simply not “admin-friendly.” I went to multiple machines to edit a number of .conf files etc – and in the end, it still did not work. This is really something that need to be solved as part of the distro itself.

Joining a Domain – I managed to hose one FC4 box by trying to get it to join a domain with a single-sign on (found an article by Bill Boswell on the internet, worth doing a google for). Odds are I had a typo in winbind or something, and no passwords would work whatsoever – I tried everything I could find on the internet (boot to recovery CD etc) and nothing worked. Dead box.
What's really needed here is a “join a domain” wizard to answer a few questions. What are the Domain Controllers IP addresses? Do you want a single-sign on? Do you want to have to type in the name of the domain – or is it to be assumed? Do you want a home folder created for each user logging on? If you are doing 25 Linux boxes, editing files to enable this is simply impractical.

Evolution – needs a Global Address List import function – or something to pre-populate an address book from a mail server (in this case, Exchange). I tried using Evolution for a few weeks, and for the most part worked OK with my E2K server, except for this minor issue. As a techie, I am ok with this – but for the average user, they have no clue what is going on, and wonder where their address list went.

Software install – this has made strides, but once again needs just a little tweak to be more friendly. My biggest wish here is that the installer ask where a program should be installed. For instance, I prefer to have a partition set aside for just programs (my typical setup has a partition for the OS, the page file, programs and data).

Software Updater – FC5. I love the new software update tool (I'm pretty sure this is just a gui for yum) , but what it needs is a scheduler. It would be nice to have a scheduler as part of this, so that on 3am every saturday the updater is run automatically.

Thanks for reading this,

Rob

PS - please keep in mind that I am a typical admin in that time is always an issue. While I wish I had the time to become more familiar with Linux, there simply isn't enough time in the day to do this. However, with a few tweaks, I think Linux could be made more "admin friendly" so that admins like me could make the jump to Linux. So please don't respond with answers like "you can do this by editing this file, and this additional file" etc. - this is really impractical for multiple machines (for example, I currently have a FC5 lab with 6 boxes - just editing files to get VNC to work on these 6 boxes took a considerable amount of time.)

---

### Post by Brunellus on 2006-06-20
Excellent points, especially the one about roaming profiles. 

> keep in mind that I am a typical admin in that time is always an issue. While I wish I had the time to become more familiar with Linux, there simply isn't enough time in the day to do this. However, with a few tweaks, I think Linux could be made more "admin friendly" so that admins like me could make the jump to Linux. So please don't respond with answers like "you can do this by editing this file, and this additional file" etc. - this is really impractical for multiple machines (for example, I currently have a FC5 lab with 6 boxes - just editing files to get VNC to work on these 6 boxes took a considerable amount of time.)

...although, if you knew what was needed ahead of time, wouldn't it be possible to write it once and "clone" the install multiple times?  Isn't this waht the ubuntu-OEM project was meant to address?

Alternatively, there's always the option of thin clients.

---

### Post by ahave2005 on 2006-06-20
Roaming profiles:
How much more roaming profiles can you get, than a linux home directory?
You allways login to your home directory, with settings and personal data intact.
It stays the same even if you switch from one upgrade to another. Not like the roaming profile 2000-XP-vista, that gives strange issues. At least you can write a script if you find a flaw in linux, since the different configuration files give you a headache. The 2000-xp doesn't give you any chances since, you cant read the binary files.

About VNC:
It's about security. And it's the same in MS, unless your use deployment/RIS including a specific policy.

Joining a domain:
We are talking about two different systems here. One is closed source and the other one are open. No one can know how Server2003 is actually authenticating, since they cant give the details. Sure you can join a domain on a Linux computer. You can access your personal networked drives, you get authenticated to the domain. You cant do much more, since MS cant give out the source, because of their interests. Apple servers have the same issues, they can join a MS domain, but can't do anything remotely as usefull with AD as MS systems. It's impossible to use MS scripts at logon, simply because MS don't want to tell how they relate to the domain server. This is is the problem of you and me, but MS have to keep their interests.

Joining a domain is a MS thing. You can do in Linux in another way, it's excactly the same, but where you actually do the same thing. Even if you have a bunch of XP machines. They wouldn't know the differences anyway. Sure there's things you can't do without group policies with a XP client, but you can have the same effect, just in another way. Where YOU would know what you were doing. AD is a great thing, but sometimes things happens and you have no idea why.

And for scripts, if you have a commandline in Linux, you can script your way out of everything, since everything is very well documented.

Evolution:
I have to semi agree on that one. But again it has more with a Exchange(MS) thing than anything else. Most companys are commited to MS as the only thing in the world. You can do it in Evolution, but its cumbersome. Not Linux fault, has more to do with closed standards. But it is possible.

Software install:
I have to totally disagree on this point. The way MS is doing this thing, is using the last position. Not so savy computerusers just tend to use whatever the installer says. Whereas in Linux you can modify locations in a startup script. I allways hated this part of windows installer.

Software updater:
I'm currently on Ubuntu, it's even more userfriendly than anything I've seen before. It's supported for a given period, right know its 4 years, if you don't upgrade your system, from one version to a newer one. Hence LTS - Long Time Support. And since the product is community based, things actually get fixed, even if it isn't a certain day of the month. More eyes are doing a job of spotting and fixing theese security holes for that reason.

In conclusion:
I'm sure you haven't spend too much time in the Linux enterprise world. The advantages are, that everything is available to you as a superuser. You have the control on your system, and you know what its doing. You can do the same things, but in a different way. It's more or less the same thing on OSX servers. Its all the same but isn't.

All the best.

---

### Post by aysiu on 2006-06-20
> **Sternfan]
Roaming Profiles &#8211 said:**
>  Just copy the home folder--that's where everything lives--emails, Firefox bookmarks, desktop shortcuts--*everything*.

Want to move Mary's profile to another Linux box? Just copy /home/mary to /home/mary on the new box.

> 
VNC &#8211; I find this particularly frustrating &#8211; that a remote Linux PC is not setup by default to have this service enabled at all times. I assumed that it was, and installed several Linux PCs at a remote location across a WAN link, and was not pleased that I could not VNC into any of these boxes to install software, run updates etc. after a reboot. After investigating for a while, there are certain steps that can be taken to remedy this (though I still cannot get this to work) but they are simply not &#8220;admin-friendly.&#8221; I went to multiple machines to edit a number of .conf files etc &#8211; and in the end, it still did not work. This is really something that need to be solved as part of the distro itself. I've had no problems with VNC. Ubuntu has it in System > Preferences > Remote Desktop. I don't think it gets much easier than that... apart from the fact that I need to type ```
ifconfig
``` to find out the local IP address to share, but if you're a sys admin, that should be no sweat.

[quote]Evolution &#8211; needs a Global Address List import function &#8211; or something to pre-populate an address book from a mail server (in this case, Exchange). I tried using Evolution for a few weeks, and for the most part worked OK with my E2K server, except for this minor issue. As a techie, I am ok with this &#8211; but for the average user, they have no clue what is going on, and wonder where their address list went. Have you considered *not* using Evolution? It isn't the only Linux email client around.

> 
Software install &#8211; this has made strides, but once again needs just a little tweak to be more friendly. My biggest wish here is that the installer ask where a program should be installed. For instance, I prefer to have a partition set aside for just programs (my typical setup has a partition for the OS, the page file, programs and data). Make a separate /usr partition. Ta-da!

---

### Post by rai4shu2 on 2006-06-20
I wish FC would switch to Smart and stop using Yum.

---

### Post by G Morgan on 2006-06-20
[QUOTE=aysiu]Make a separate /usr partition. Ta-da![/QUOTE]

Even then though it still doesn't install where you want. What he is asking for is a Linux C:\Program Files\. It's something that is probably being looked at by the LSB team. A lot of 3rd party apps that are coming out allow you to chose your install directory (like Xover office and Google Earth) but I imagine that most distros will continue to use their own directory structures.

---

### Post by bruce89 on 2006-06-20
[QUOTE=rai4shu2]I wish FC would switch to Smart and stop using Yum.[/QUOTE]
Well at least Ubuntu will.

---

### Post by egon spengler on 2006-06-20
[QUOTE=Sternfan] PS - please keep in mind that I am a typical admin in that time is always an issue. While I wish I had the time to become more familiar with Linux, there simply isn't enough time in the day to do this. However, with a few tweaks, I think Linux could be made more "admin friendly" so that admins like me could make the jump to Linux. So please don't respond with answers like "you can do this by editing this file, and this additional file" etc. - this is really impractical for multiple machines (for example, I currently have a FC5 lab with 6 boxes - just editing files to get VNC to work on these 6 boxes took a considerable amount of time.)[/QUOTE]

I'm not sure I understand what you're hoping for then. As an admin sometimes you may well have to do some administration, if someone presents a solution to one of your problems wouldn't it be best to put it into effect? I think you're doomed to be disappointed if you intend to just wait til some Linux distro comes with all default preferences coinciding with the way you would like things set up

---

### Post by aysiu on 2006-06-20
[QUOTE=G Morgan]Even then though it still doesn't install where you want. What he is asking for is a Linux C:\Program Files\. It's something that is probably being looked at by the LSB team. A lot of 3rd party apps that are coming out allow you to chose your install directory (like Xover office and Google Earth) but I imagine that most distros will continue to use their own directory structures.[/QUOTE]
If you're using Ubuntu, it will be in the /usr directory.

And if you get a choice of where to install it, put it in the /usr directory (/usr/local/bin is a good place).

I still don't get what the big deal is.

---

### Post by G Morgan on 2006-06-20
[QUOTE=aysiu]If you're using Ubuntu, it will be in the /usr directory.

And if you get a choice of where to install it, put it in the /usr directory (/usr/local/bin is a good place).

I still don't get what the big deal is.[/QUOTE]

It has to be said that Windows gives you the option of where to install programs by default. Generally Linux distros tend to install to a default without telling you where that default is. Then again you can't activate any program in Windows by entering the command anywhere (unless you mess around with .bat scripts in the system32 folder). If you entered the command firefox into the Windows 'run' dialog you'd get an error. This is a large part of the reason you have default install directories, it allows such power.

Personally I don't have any problem installing to a standard directory, the fact that Linux merges the entire file system means I have little reason to have to change the position anyway. Generally choosing the install directory just means another unnecessary mouse click in Windows but on occassion (like when you dual boot XP and 98 say) it has its uses.

---

### Post by prizrak on 2006-06-20
> think Linux could be made more "admin friendly" so that admins like me could make the jump to Linux. So please don't respond with answers like "you can do this by editing this file, and this additional file" etc. - this is really impractical for multiple machines (for example, I currently have a FC5 lab with 6 boxes - just editing files to get VNC to work on these 6 boxes took a considerable amount of time.)
Why not write a quick script that will just edit the files for you and run it on every machine.

---

### Post by TechHut on 2006-06-20
My solutions to the following are in red.
[QUOTE=Sternfan]I have spent much of the last year getting familiar with Linux – using mostly FC3, FC4, FC5, Ubuntu and Linspire. I settled on FC, since I had some introductory experience with it years ago in tech school. After experimenting with it in a lab scenario, and then implementing several machines for younger students where I work, I have come up with a few things that could make it easier to get the most out of Linux. I am sending a copy of this to online forums relating to the distros I mentioned, in hopes that someone, somewhere will consider these suggestions in future releases of their particular distro. There are just a handful of them, but if they were implemented, I could see a lot of network admins in similar situations as myself make the move to Linux.

I am also hoping that as a community, we could start a “top ten list” of things that should be added to future distros... I don't have ten items, but I think this is a good start. And please take this as constructive criticism – I want to be able to expand Linux usage in the future.

My List:

Roaming Profiles – my current users have been using roaming profiles for years (win2k) and are genuinely flustered when using a Linux box and their settings do not “follow” them. Please don't misunderstand – I am not asking for a Linux box to use a win2k profile – I just need Linux profiles to follow to other Linux boxes. Setting up logon scripts etc. is a partial solution – but not a real substitute for Roaming Profiles – desktop shortcuts, Firefox bookmarks, email setting in Evolution are all examples of things that need to move with a user.

[COLOR="Red"]XDMCP solves this. In Ubuntu, especially Gnome, go into System > Adinistration > Login Screen (I think). Enable XDMCP on your 'server'.[/COLOR]

VNC – I find this particularly frustrating – that a remote Linux PC is not setup by default to have this service enabled at all times. I assumed that it was, and installed several Linux PCs at a remote location across a WAN link, and was not pleased that I could not VNC into any of these boxes to install software, run updates etc. after a reboot. After investigating for a while, there are certain steps that can be taken to remedy this (though I still cannot get this to work) but they are simply not “admin-friendly.” I went to multiple machines to edit a number of .conf files etc – and in the end, it still did not work. This is really something that need to be solved as part of the distro itself.

[COLOR="Red"]Umm... Terminal Server Client does VNC.[/COLOR]

Joining a Domain – I managed to hose one FC4 box by trying to get it to join a domain with a single-sign on (found an article by Bill Boswell on the internet, worth doing a google for). Odds are I had a typo in winbind or something, and no passwords would work whatsoever – I tried everything I could find on the internet (boot to recovery CD etc) and nothing worked. Dead box.
What's really needed here is a “join a domain” wizard to answer a few questions. What are the Domain Controllers IP addresses? Do you want a single-sign on? Do you want to have to type in the name of the domain – or is it to be assumed? Do you want a home folder created for each user logging on? If you are doing 25 Linux boxes, editing files to enable this is simply impractical.

[COLOR="Red"]Creating a script to do this is alot easier, but one thing that worked partially for me was name my workgroup to my domain name (at my school).[/COLOR]

Evolution – needs a Global Address List import function – or something to pre-populate an address book from a mail server (in this case, Exchange). I tried using Evolution for a few weeks, and for the most part worked OK with my E2K server, except for this minor issue. As a techie, I am ok with this – but for the average user, they have no clue what is going on, and wonder where their address list went.

[COLOR="Red"]I don't know[/COLOR]

Software install – this has made strides, but once again needs just a little tweak to be more friendly. My biggest wish here is that the installer ask where a program should be installed. For instance, I prefer to have a partition set aside for just programs (my typical setup has a partition for the OS, the page file, programs and data).

[COLOR="Red"]Just give / it's own partition. Synaptic is easy to use. It is kind of like a web browser, just search. Now, if you waht to keep your current setup, OS, Programs and Data are on / (and a few sub dierectories), so put that on a partition. Page File? Swap Space does that.[/COLOR]

Software Updater – FC5. I love the new software update tool (I'm pretty sure this is just a gui for yum) , but what it needs is a scheduler. It would be nice to have a scheduler as part of this, so that on 3am every saturday the updater is run automatically.

Thanks for reading this,

Rob

PS - please keep in mind that I am a typical admin in that time is always an issue. While I wish I had the time to become more familiar with Linux, there simply isn't enough time in the day to do this. However, with a few tweaks, I think Linux could be made more "admin friendly" so that admins like me could make the jump to Linux. So please don't respond with answers like "you can do this by editing this file, and this additional file" etc. - this is really impractical for multiple machines (for example, I currently have a FC5 lab with 6 boxes - just editing files to get VNC to work on these 6 boxes took a considerable amount of time.)[/QUOTE]

I really hope I have helped you in your strive into the world of Linux, as some times I jsut want to hit my head on the wall ](*,)

---

### Post by Sternfan on 2006-06-21
[QUOTE=Brunellus]Excellent points, especially the one about roaming profiles. 



...although, if you knew what was needed ahead of time, wouldn't it be possible to write it once and "clone" the install multiple times?  Isn't this waht the ubuntu-OEM project was meant to address?

Alternatively, there's always the option of thin clients.[/QUOTE]


I actually did this with my current lab (6 FC5 boxes) - we use Norton's Ghost which really works well if all the hardware is the same, but all my PCs aren't the same.

---

### Post by 3rdalbum on 2006-06-21
[QUOTE=G Morgan]Even then though it still doesn't install where you want. What he is asking for is a Linux C:\Program Files\. It's something that is probably being looked at by the LSB team. A lot of 3rd party apps that are coming out allow you to chose your install directory (like Xover office and Google Earth) but I imagine that most distros will continue to use their own directory structures.[/QUOTE]

I disagree. I like how Synaptic and dpkg don't ask a whole heap of stupid questions, ala Windows installers:

1. Welcome to the wizard. Click Next to continue.
2. Here's the license. If you agree, click Next to continue
3. Where do you want to install the program? Click Next to continue.
4. Where do you want the Start menu item? Click Next to continue.
.... then it installs...
5. Xyz.exe has successfully installed. Click Next.
6. Click "Finish" to exit the installer.

I mean, come on! Just install the bloody thing in the background and stop bothering me with idiotic questions!

---

### Post by Sternfan on 2006-06-21
[QUOTE=aysiu]Just copy the home folder--that's where everything lives--emails, Firefox bookmarks, desktop shortcuts--*everything*.

Want to move Mary's profile to another Linux box? Just copy /home/mary to /home/mary on the new box.

 I've had no problems with VNC. Ubuntu has it in System > Preferences > Remote Desktop. I don't think it gets much easier than that... apart from the fact that I need to type ```
ifconfig
``` to find out the local IP address to share, but if you're a sys admin, that should be no sweat.

I tested this in my lab with my Kubuntu laptop.  If someone is logged onto the laptop, all is well - I can VNC into it just fine.  If no one is logged on, I get nothing.  Having multiple labs in remote locations, I need to get into them when no one is on them to add software, updates etc - which I am having great difficulty with doing right now.

 Have you considered *not* using Evolution? It isn't the only Linux email client around.

From my experience, Evolution is a very nice email client.  My only fault with it was that I open my address book and it is empty.  I would have killed to find a way for it to be automatically populated, but could never figure it out.  In organizations with large numbers of users, this is truly a necessity.

 Make a separate /usr partition. Ta-da![/QUOTE]


Rob

---

### Post by Sternfan on 2006-06-21
Thanks for response.

I've responded to other posters on these issues, and don't want to clog up this thread with multiple answers to the same issues.

Thanks again,
Rob

---

### Post by Sternfan on 2006-06-21
Just a quick note of praise for this forum.

After having posted in other forums, I have yet to come across any condescending attitudes that just don't help the situation.

I am really hopefull that of all the distros, Ubuntu seems to the the one that "gets it" - in the sense of being responsive to the community that actually is trying to use their version of Linux.

Thanks,
Rob

---

### Post by TechHut on 2006-06-21
I guess I could speak for the community by saying that is is curious users like you which drive people to help and better yet, improve.

---

### Post by Brunellus on 2006-06-21
We value civility in Ubuntu, not just 1337ness. At least most of the time.

---

### Post by Sternfan on 2006-06-22
Well, I'm not alone.  As an aside, I work for a non-profit organization helping kids.  I routinely get donated, wiped PCs that need an OS.  While I can get non-profit pricing for windows, looking into Linux is a definite option.

I know at least two more admins in the same boat as me - working in a similar organization & considering Linux.  They have some experience, try it for a bit, struggle & give up.  They don't know anybody that can help, don't have the time to do the research and testing to make it work and just get frustrated.  My wish-list pretty much came out of these conversations, since I have pretty much become the "Linux pusher."

Rob

---

### Post by prizrak on 2006-06-22
[QUOTE=Sternfan]Well, I'm not alone.  As an aside, I work for a non-profit organization helping kids.  I routinely get donated, wiped PCs that need an OS.  While I can get non-profit pricing for windows, looking into Linux is a definite option.

I know at least two more admins in the same boat as me - working in a similar organization & considering Linux.  They have some experience, try it for a bit, struggle & give up.  They don't know anybody that can help, don't have the time to do the research and testing to make it work and just get frustrated.  My wish-list pretty much came out of these conversations, since I have pretty much become the "Linux pusher."

Rob[/QUOTE]
When it comes to Ubuntu they are always welcome to the forums where they will get the help required. There is the documentation project as well as wiki. Also if the time permits some solutions that are posted on Gentoo forums/docs can be adapted to Ubuntu.

---

### Post by Sternfan on 2006-06-27
Tech hut:  A couple replies:

XDMCP - I did this, VNC is still not working.  Here's my issue - if the Linux box is logged on (a user is logged on) - VNC works fine.  No problems.  If the user logs off, VNC no longer works.  In short, I cannot use VNC with a Linux box that is logged off.  My school lab (6 linux boxes) are across a WAN link - in off hours, when I want to to do updates etc, I cannot use VNC to get into these boxes.  

Rob

---

### Post by Sternfan on 2006-06-27
Ahave2005 - my response.

Roaming profiles - I cannot for the life of me find a how-to to explain how to do this like you mentioned.  Got a link?  Would this work with multiple users using the same profile?  I have one student account, shared by multiple students at the same time.  On the Windows side, I use mandatory roaming profiles if that helps any.

Joining a Domain - I was thinking of a wizard (or config screen - I heard Xandros has this already) to simplify the samba, winbind, PAM, etc.) to do what Linux can already do - join a domain.  I've done this with Fedora 4.  It worked.  The big problem?  It took me about an hour to do each machine.  I did three boxes, and hosed one of them so bad I couldn't get back into it (even with the rescue CD etc).  Figure out a way to do this in an efficient manner and I would do jumping jacks of joy.

Rob

---

### Post by prizrak on 2006-06-28
[QUOTE=Sternfan]Ahave2005 - my response.

Roaming profiles - I cannot for the life of me find a how-to to explain how to do this like you mentioned.  Got a link?  Would this work with multiple users using the same profile?  I have one student account, shared by multiple students at the same time.  On the Windows side, I use mandatory roaming profiles if that helps any.

Joining a Domain - I was thinking of a wizard (or config screen - I heard Xandros has this already) to simplify the samba, winbind, PAM, etc.) to do what Linux can already do - join a domain.  I've done this with Fedora 4.  It worked.  The big problem?  It took me about an hour to do each machine.  I did three boxes, and hosed one of them so bad I couldn't get back into it (even with the rescue CD etc).  Figure out a way to do this in an efficient manner and I would do jumping jacks of joy.

Rob[/QUOTE]
I think it might just not be feasible or there isn't enough demand for what you are asking. Why don't you just do one box and then write a small script to do the rest of the machines. That would work much better than a wizard anyway because you won't have to type anything in at all you just type it all in once and run the script on all machines. 

As far as VNC goes, I'm not too sure why you need it if all you do is updates and some administration ssh should be just fine. In fact you can create a root user that uses ssh log in for all the things you need to do.

---

