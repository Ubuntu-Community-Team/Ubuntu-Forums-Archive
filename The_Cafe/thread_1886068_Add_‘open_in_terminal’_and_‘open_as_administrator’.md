---
title: "Add ‘open in terminal’ and ‘open as administrator’ to Right Click Menu (11.10)"
date: 2011-11-24
forum: The Cafe
---

### Post by Epinephrin3 on 2011-11-24
I've searched about for this on here but I cant find anywhere else that its been posted so I thought I would post it up myself for anyone who wants their power user options back on 11.10...

I don’t know why they started taking these options out of Ubuntu as  it just makes life harder for some people, so I decided to make a quick step by step on  how to enable them again.
 We  have provided the files for you but you can always obtain the files  yourself from another Linux OS. For example on Linux Mint 11 they are  located in */usr/lib/nautilus/extensions-2.0*.
 
**Installing**
 
For the *‘open in terminal’* option download: [URL="http://www.ivegotavirus.com/blog/wp-content/uploads/libaryFiles/libnautilus-open-terminal.so"]libnautilus-open-terminal.so
[/URL]  
For the *‘open as administrator’* option download: [URL="http://www.ivegotavirus.com/blog/wp-content/uploads/libaryFiles/libnautilus-gksu.so"]libnautilus-gksu.so
[/URL]  
Open your nautilus extensions folder:
 ```
gksu nautilus /usr/lib/nautilus/extensions-3.0
```Copy the file(s) you downloaded into the folder you just opened and restart your computer.
 

That's it, hopefully your life can be a little bit easier now. This tutorial was originally written on [www.ivegotavirus.com]("http://www.ivegotavirus.com").

---

### Post by Epinephrin3 on 2011-12-01
I had a read though that before i posed the thread. Surely my post does class as a tutorial and if not it would be classed as a tip at least...

---

### Post by forrestcupp on 2011-12-01
Are those extensions not even in the repos anymore? I can see why they would stop having it installed by default, but why would they stop making that available?

---

### Post by Epinephrin3 on 2011-12-01
Nop not in the repos as far as i can tell. I really don't know why they removed them, i mean they could at least put an option to enable it not completely remove it altogether. Bit silly really.

All i can think of is that they don't want users messing around with their own system as root in case they break it ?? Remind you of any other popular operating systems...?

---

### Post by jjex22 on 2011-12-01
> **Epinephrin3 said:**
> Nop not in the repos as far as i can tell. I really don't know why they removed them, i mean they could at least put an option to enable it not completely remove it altogether. Bit silly really.

All i can think of is that they don't want users messing around with their own system as root in case they break it ?? Remind you of any other popular operating systems...?

Whilst I'm surprised it's not an option you can turn on, or at the very least in the repo's, You are right on the money - things like this have to be removed from default settings if an operating system is to go to the masses - whilst linux is fantastic in that it is so configurable and the user has so much control - this becomes dangerous when people who don't know what they're doing are given control. 

I have my own issues with Windows, but it's assumption that you don't have the faintest idea what you're doing isn't one of them;  most people (when it comes to windows, myself included) don't - they just want to be able to use the internet and programs they installed. I don't want to see linux disabling it's feature like windows did, and I want to see it and it's descendants become a true mass deployment operating system - and that means limiting the default options in the gui as far as I can see it.

---

### Post by Epinephrin3 on 2011-12-01
I can see what you are saying but at the end of the day if someone is going to mess around with their system they will find a way to do it anyway but, this is also how you learn. By thinking automatically that the majority of users cant be trusted with their own computer is simply wrong! A company should never decide whats best for its users, the users should always have the choice to choose whats best for them and i thought canonical was the sort of company that thought the same way.  

If the option is there to open a folder as root it does not mean that a user with less experience is going to use it or even need it in the first place, they are more than likely not even going to touch it if they don't know what it is. But for someone who wants to use it its there, if they break their system its on them and they know that they only have their self to blame. Shops don't ask if you know how to use a hammer or say you cant have one because you cant be trusted with it and if you go home and put a hole in your wall or put a nail through a water pipe then its your own fault and you know that.

If people are never given a choice in life they will never learn and they wont ever know.


Sorry rant over :lolflag:

---

### Post by vasa1 on 2011-12-01
Open as administrator aka **nautilus-gksu** aka **privilege granting extension for nautilus using gksu** is in the USC.
Version: nautilus-gksu 2.0.2-5-ubuntu2
Updates: Canonical provides critical updates until April 2013.
(Also see [http://ubuntuforums.org/showthread.php?t=1861721](http://ubuntuforums.org/showthread.php?t=1861721))

---

### Post by Epinephrin3 on 2011-12-01
> **vasa1 said:**
> Open as administrator aka **nautilus-gksu** aka **privilege granting extension for nautilus using gksu** is in the USC.
Version: nautilus-gksu 2.0.2-5-ubuntu2
Updates: Canonical provides critical updates until April 2013.
(Also see [http://ubuntuforums.org/showthread.php?t=1861721](http://ubuntuforums.org/showthread.php?t=1861721))

So they do at least provide it through the USC which is good to know even if you do have to move the file to the correct location still. I cant see a reason why they have taken it out of 11.10 though other than whats been discussed above. The bug report in that thread you posed got resolved as "NOTABUG" so it cant be down to that...

---

### Post by jjex22 on 2011-12-01
> **Epinephrin3 said:**
> I can see what you are saying but at the end of the day if someone is going to mess around with their system they will find a way to do it anyway but, this is also how you learn. By thinking automatically that the majority of users cant be trusted with their own computer is simply wrong! A company should never decide whats best for its users, the users should always have the choice to choose whats best for them and i thought canonical was the sort of company that thought the same way.  

If the option is there to open a folder as root it does not mean that a user with less experience is going to use it or even need it in the first place, they are more than likely not even going to touch it if they don't know what it is. But for someone who wants to use it its there, if they break their system its on them and they know that they only have their self to blame. Shops don't ask if you know how to use a hammer or say you cant have one because you cant be trusted with it and if you go home and put a hole in your wall or put a nail through a water pipe then its your own fault and you know that.

If people are never given a choice in life they will never learn and they wont ever know.


Sorry rant over :lolflag:

I'm afraid it isn't a question of control - the options as I said should be there - but not by default; if you know what you are doing, then advanced features should be able to be easily turned on - but not in open view

After university I worked in a tech support call centre for toshiba - you would be amazed at the calls I had - people who shut down explorer.exe, people who thought paint didn't work becuase they had set both colours to white, those that didn't realise their monitor wasn't turned on, printers out of ink, people who couldn't find their own documents - in my documents (not to mention the sheer amount of calls that ended with 'plug it in').

 For Linux to be for the masses it has to be accessible to everyone - break then fix isn't an option, the average user doesn't want or need to know how it works. It's all about finding the balance between letting my 60 year old mother loose on it without me having to spend an hour undoing the damage, but maintaining all the features we all love about linux for the likes of me - how to do that? that's the big question I guess - as a long term OSX User, I quite like the balance they have, no where near the amount of restrictions of windows, but again the Mother hasn't had any trouble and we bought her an Imac in 2007 (to be honest I think she's just happy it 'looks like a flatscreen microwave')

I agree with you the features should be built in, but I don't think it should be a default right click option, but then I agree you should be able to turn it on.

---

### Post by 3rdalbum on 2011-12-01
The switch to Gnome 3 did break a lot of addons and things, but then it did that in all Gnome 3 distros.

Ubuntu has never shipped with nautilus-gksu or nautilus-open-terminal, though. It's always been an optional extra in the repositories.

If either of these are missing from Ubuntu Software Center now, it's because they don't work in Gnome 3 and the newer equivalents haven't been packaged for Ubuntu yet.

---

