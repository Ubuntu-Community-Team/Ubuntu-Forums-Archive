---
title: "Needed file manager improvement"
date: 2010-06-05
forum: The Cafe
---

### Post by screaminj3sus on 2010-06-05
One thing that has always bothered me about linux. When you want to copy something to a folder that requires root access it simply does not let you, you must open a terminal and open the file manager as root to do it. This is ridiculously un user friendly and cant believe it has yet to be addressed. why does it not siply prompt for your password and let you do it? 

Windows vista/7 with uac enabled does this. If you copy something you program files it'll give you a prompt and let you do it.

Things like this is something ubuntu should address to truly make it the most userfriendly and easy to use distro :)

---

### Post by dv3500ea on 2010-06-05
Windows is also more user messupable. Only experienced users need to do anything with the files that are read only. They are read only because messing with them can harm the system. For users who need root access of files there is the option of creating a launcher or menu entry with the command ```
gksudo nautilus
```. I think there is also a nautilus script for this.

---

### Post by screaminj3sus on 2010-06-05
> **dv3500ea said:**
> Windows is also more user messupable. Only experienced users need to do anything with the files that are read only. They are read only because messing with them can harm the system. For users who need root access of files there is the option of creating a launcher or menu entry with the command ```
gksudo nautilus
```. I think there is also a nautilus script for this.

Its the same with windows but it prompts you than elevates permissions for you automating the process instead of having to go and open the file manager as root...

Nautilus should prompt you for your password when you try and do anything to folders needing root access. If anything opening the whole file manager as root is just as dangerous if not moreso.

At the very least there should be an "open folder as root" right click option or something!

---

### Post by ranch hand on 2010-06-05
Much easier to install "nautilus-gksu".  Right click on directory choose the option "open as administrator".

Kind of the same as folks who like to be able to open a directory in terminal like in Thunar.  Install "nautilus-open-terminal" and that is in your right click menu too.

I do not know if this is as easy as in MS, it does take 2 clicks and you need a password.  I do know that if all this needed done in terminal it would still be a lot easier than living with "Hey bozo you are an idiot so we will give you another 42 boxes to click on to approve doing this stupid thing" boxes in MS.

---

### Post by screaminj3sus on 2010-06-05
> **ranch hand said:**
> Much easier to install "nautilus-gksu".  Right click on directory choose the option "open as administrator".

Kind of the same as folks who like to be able to open a directory in terminal like in Thunar.  Install "nautilus-open-terminal" and that is in your right click menu too.

I do not know if this is as easy as in MS, it does take 2 clicks and you need a password.  I do know that if all this needed done in terminal it would still be a lot easier than living with "Hey bozo you are an idiot so we will give you another 42 boxes to click on to approve doing this stupid thing" boxes in MS.

The prompts in vista/7 aren't any worse than in linux... The only real difference is they say yes/no instead of a password prompt. You are more describing 3rd part application installers which love to have lots of boxes to click.

And thanks for the nautilus gksu tip, something like that is a lot better than it is by default. I dont understand why something like that isnt included by default.

---

### Post by ranch hand on 2010-06-05
It is not included because you can do real damage using it.

If, for instance, you just switched from MS where you can't get to the source code, you are likely to get into some real serious problems.

---

### Post by screaminj3sus on 2010-06-05
You can mess up windows deleting important crap too, but they include it by default and they have more of a reputation of "babying" users than linux! You have to have a balance between usability and protecting users from themselves.

Simple things like installing a theme are a PIA right now by default (YES I know you can use the themes dir in the home folder but that doesnt skin stuff like synaptic)

A password prompt and a warning that these could be important system files would be more than sufficient.

---

### Post by donniezazen on 2010-06-05
> **screaminj3sus said:**
> one thing that has always bothered me about linux. When you want to copy something to a folder that requires root access it simply does not let you, you must open a terminal and open the file manager as root to do it. This is ridiculously un user friendly and cant believe it has yet to be addressed. Why does it not siply prompt for your password and let you do it? 

Windows vista/7 with uac enabled does this. If you copy something you program files it'll give you a prompt and let you do it.

Things like this is something ubuntu should address to truly make it the most userfriendly and easy to use distro :)

+1 You can messup system anyhow if you have administrative rights. If you going to copy something to /root how can doing it sudo nautilus way will prevent it. OP has a valid point.

---

### Post by Longinus00 on 2010-06-05
Why are you trying to copy files into a folder owned by root?

---

### Post by ronacc on 2010-06-05
there are many valid reasoms for copying files into a folder owned by root and even **GASP** hacking them .

---

### Post by aysiu on 2010-06-05
For more details, see this bug report:
[Nautilus should have a superuser mode](https://bugs.launchpad.net/nautilus/+bug/12154)

and this forum post:
[Re: Still don't get the point of sudo](http://ubuntuforums.org/showthread.php?p=9394859#post9394859)

---

### Post by kahumba on 2010-06-05
> **screaminj3sus said:**
> You can mess up windows deleting important crap too, but they include it by default and they have more of a reputation of "babying" users than linux! You have to have a balance between usability and protecting users from themselves.

Simple things like installing a theme are a PIA right now by default (YES I know you can use the themes dir in the home folder but that doesnt skin stuff like synaptic)

A password prompt and a warning that these could be important system files would be more than sufficient.
I agree. And when you report to the forum an issue like this that requires an enhancement there's almost always people questioning it with a combination of (at best) half-truths like:
- it's not window$
- you shouldn't copy files to folders owned by root
- ok, sometimes you should copy to root, but (whatever noble excuse)
- that's a minor issue which doesn't deserve the time being fixed
- what you're saying would make things worse.
- write the patch yourself and manage to convince the upstream project to adopt it (almost zero chances unless you're working in a Red Hat/Canonical type companies and insist a lot).
- whatever else
And when a new post like this happens once in a while and when you read the comments you think like, there we go, the same attitude over and over again and when the Linux market share keeps at 1% for years we often blame/imply "the masses" for being "unwashed" and not appreciating the "cool" stuff (Linux), but it's often us having to be responsive to positive changes in the first place - to **have** a better product in the long run, not just to claim having a better one.

---

### Post by Sennaista on 2010-06-05
While we are at it, can we also have the possibility to change the file view in, for example, an application's open dialogue? Try opening a file in Gimp from the open dialogue, without being able to change the view to thumbnails it's very hard to find the exact file you want amongst many files.

---

### Post by Artemis3 on 2010-06-05
I would love the day nautilus stopped copying stuff backwards (select files in order named 1 to 10, drag to folder and see file 10 copied first, then 9, then 8, etc).

---

### Post by seeker5528 on 2010-06-05
> **screaminj3sus said:**
> One thing that has always bothered me about linux. When you want to copy something to a folder that requires root access it simply does not let you, you must open a terminal and open the file manager as root to do it. This is ridiculously un user friendly and cant believe it has yet to be addressed. why does it not siply prompt for your password and let you do it? 

Can't really think of a reason why this is a problem.

Either people don't know in which case you don't want it to be too automated, otherwise it invites them to become complacent about the risks, or people do know in which case it shouldn't be a big deal.

Installing nautilus-gksu seems pretty simple.

Creating a menu item that uses the command ```
gksudo "nautilus --no-desktop"
``` seems pretty easy.

Later, Seeker

---

### Post by 101011010010 on 2010-06-05
Hi there,> Much easier to install "nautilus-gksu".  Right click on directory choose  the option "open as administrator". I wish I'd found this a bit earlier. Thanks ranch hand.[:popcorn:]("http://ubuntuforums.org/member.php?u=647614")

---

### Post by screaminj3sus on 2010-06-05
> **Longinus00 said:**
> Why are you trying to copy files into a folder owned by root?

I already mentioned one example... /usr/share/themes or /usr/share/icons so apps like synaptic get skinned properly when I install custom skins.

> **kahumba said:**
> I agree. And when you report to the forum an issue like this that requires an enhancement there's almost always people questioning it with a combination of (at best) half-truths like:
- it's not window$
- you shouldn't copy files to folders owned by root
- ok, sometimes you should copy to root, but (whatever noble excuse)
- that's a minor issue which doesn't deserve the time being fixed
- what you're saying would make things worse.
- write the patch yourself and manage to convince the upstream project to adopt it (almost zero chances unless you're working in a Red Hat/Canonical type companies and insist a lot).
- whatever else
And when a new post like this happens once in a while and when you read the comments you think like, there we go, the same attitude over and over again and when the Linux market share keeps at 1% for years we often blame/imply "the masses" for being "unwashed" and not appreciating the "cool" stuff (Linux), but it's often us having to be responsive to positive changes in the first place - to **have** a better product in the long run, not just to claim having a better one.

QFT.

I will install nautilus-gksu as suggested it will certainly makes things easier but I still maintain the opinion we should have something like this by default.

---

### Post by kerry_s on 2010-06-05
i use a nautilus script.

```

#!/bin/bash
gksudo nautilus "$NAUTILUS_SCRIPT_CURRENT_URI" &
exit 0

```

---

### Post by handy on 2010-06-05
I use Worker. It is highly configurable, comes with a great config to start with that you can modify to suit yourself. It has a huge range of built in commands that you can choose from its configuration page, it has no dependencies apart from X, it is fast & as far as needing root access goes I just have button configured "sudo Worker" where I get asked for my root password before another Worker pops up which is configured how I want it to be, right down to 1 file/directory list window or 2, what is on all of the buttons, how many buttons & how many pains of buttons, LMB/RMB (they are the dog eared buttons in the image below) & the colours that your eyes prefer.

Worker was inspired by Jonathan Potter's Directory Opus v4 (DOpus) that won the hearts & minds of Amiga users all those years ago. Though these days he develops DOpus for windows.

---

