---
title: "Linux missing Dual Mon GUI"
date: 2006-01-10
forum: The Cafe
---

### Post by Sionide on 2006-01-10
I can only really think of one thing which Linux doesn't have - which Windows does really well.

A GUI to sort out Dual Monitors. Windows does it in a jiffy, right-click Desktop, advanced, blah, takes maybe 5 or 6 clicks - with other software installed (Ultramon etc) you get extra control over the 2nd monitor, such as stretching the task bar across both screens etc.

So far, on Linux, I've found nothing for setting up dual monitors.. Hacking about with xorg.conf makes it difficult and time consuming to set up Dual Monitors... Pretty impossible in my particular case. I have a laptop and I was hoping to set up dual monitors with it but have so far been unsuccessful.

Maybe someone will say 'duh, you're looking for <package name>' - as is usually the case with such questions ;) Hopefully anyway... [-o<

---

### Post by Arktis on 2006-01-10
Agreed.  Same gripe here.  It would be nice if someone came along to this thread, waved their fingers over the keyboard and *poof!*.

---

### Post by MetalMusicAddict on 2006-01-10
Im damn sure the last time I used Mandrake (shows how long) it had a dual-mon GUI. I wished they had one yesterday but I have my 24" Dell widescreen commin' tomorrow so I care a little less now. :)

---

### Post by poofyhairguy on 2006-01-10
[QUOTE=Arktis]*poof!*[/QUOTE]

I'm here. 

On the topic, I LOVE my dual monitor setup in Linux. Both Gnome and KDE do better with dual desktops than Windows (I NEVER have an application try to maximize over both...and that sometimes happens in Windows). 

I also love having a Gnome Panel and Taskbar for each desktop. Its great- as I drag applications from one monitor to the other it goes from the taskbar on that first monitor to the taskbar on the second one. I would take that over having one big taskbar (ala XP) anyday.

And I LOVE how with my Nvidia card I can use Composite AND dual head. The normal Xinerama that was developed by the free software community does not do well with composite at ALL. It HATES it. For dual head in Linux with the modern eye candy toys, Nvidia is the only option.

Of course this thread was not about how cool dual head is in Ubuntu, but how hard it is to set up. This is true- the Xorg.conf file is the most important file on my computer in my opinion. I put it on this forum just to have a backup- its that important. Why? Because it took me four hours to get it to work how I want. 

The Xserver is Linux is by far its most primative part. Its not just about dual head- its more. Its almost impossible to "extend your desktop" on a laptop using the external vga connector like Windows and OSX can do. You are lucky if it will mirror your desktop. Also it can be VERY hard to setup TV Out correctly. And if your Xserver is not configured correctly on boot you have to edit the file to fix it. Finally its almost impossible to dual more than two heads....I refuse to even try.

And this problem with Desktop Linux is one of the more depressing problems. Why? Lets just put it this way- Mr. Stone (the guy who does the Xorg stuff for Ubuntu) is a REALLY optomistic guy when it comes to Xorg. When Jon Smirl claimed that the Xserver Team would release a hardware accerated Xserver after Windows and OSX released theirs (well...just Windows...OSX has done this stuff from the beginning) Mr. Stone was the sole person that thought he was wrong. It seemed to me that he really believed that Xegl would be ready before Vista was released.

Yet when I read someone ask him about "desktop spanning" on a laptop, even the ever optomist Mr. Stone said not that long ago it would be a year before it could even possibly happen in most cases. That means like two or three years in less optomistic terms (I am ever the realist). What it would take to get that working is what it would take to get dual head working easily. 

And if you look into it, its easy to see why its such a difficult thing. Nvidia has the best Xinerama like thing, but because they do not use the standard Xinerama no GUI tool for Xorg could ever work. In fact, there is a good reason that the Xorg.conf has only one GUI tool for it in existance as far as I know (SUSE's SAX)- its because its an absolute mess.

This is yet another reason for those of us the in the crowd to be honest about Ubuntu. It really does not fit middle of the road Windows users (aka the people who use dual head among other things) now or in the near future. It sucks that such it the truth, but hey life is what it is.

Of course for us more geeky people, the solutions do exist. The single best source on this stuff is found here:

[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

I used that to set up mine. Still took four hours, but I am a little slow sometimes.

One you get it done multi monitor support on Linux is GREAT. Even my new favorite application (Skippy) works good with two monitors. Its just getting there...

---

### Post by Sionide on 2006-01-10
[QUOTE=poofyhairguy]Yet the point of the thread wa[/QUOTE]

wa...?

---

### Post by poofyhairguy on 2006-01-10
[QUOTE=Sionide]wa...?[/QUOTE]

Mistake I forgot to take out before I posted.

When you rant like me, you don't always get it right on the first try (or the last).

---

### Post by Arktis on 2006-01-11
So true.  God bless the edit button.

It took me forever to get my xorg.conf to where I could have a good 4 screens setup (two monitors and two tv screens).  Once I got there, my xorg.conf basicly hasn't been touched even though I don't use four screens, just two (I'd need another TV for that anyways).  I also don't like how in Gnome (but not in KDE for some reason) I can't have app windows span across both screens at the same time or move them back and forth because I'm using two cards instead of one dual head card.  I'm stuck with two isolated desktop spaces.  It's really not that bad actually and I like it because there are advantages, but I'd just prefer the ability to also have it the other way.  In other words, I feel restricted.

Oh, and there doesn't seem to be a way to adjust the x and y position of the screens relative to eachother.  That strikes me as a glaring omission.

---

### Post by poofyhairguy on 2006-01-11
[QUOTE=Arktis] I also don't like how in Gnome (but not in KDE for some reason) I can't have app windows span across both screens at the same time or move them back and forth because I'm using two cards instead of one dual head card.  I'm stuck with two isolated desktop spaces.  It's really not that bad actually and I like it because there are advantages, but I'd just prefer the ability to also have it the other way.  In other words, I feel restricted.[/QUOTE]

I had the same problem. Two seperate desktops are not as fun. Turns out the problem was that one of my monitors had a different resolution than the other. They have to use the EXACT same resolution to span the desktop across both.

So I bought a new monitor with the same resolution as my best one.

---

### Post by CompShrink on 2006-01-27
I am NOT sorry to say, you are both wrong:

I ran a dualscreen setup, with a PCI and an AGP card, on which I could move windows between the two screens just fine. And one was at 1600x1200, the other at 1024x768. You can have two different cards, with two different resolutions, and have one connected desktop span both.

That old 1024x768 monitor fried however, and I now have 2 1600x1200 monitors. In the US that is. I'm not in the US right now... so I cannot give you my xorg.conf, unfortunately.

I might be able to get someone to stick an UBUNTU live CD in and copy the xorg.conf file, but the system is unbootable ATM, as I took the hdd with the MBR&grub with me, but it's not the hdd with my Ubuntu install.

I'll do my best to help you. For now, I'll just tell you there is in fact a solution out there to get them fully cooperative.

And i used SuSE before myself, and really, really missed SaX2 when I moved to Ubuntu. Anyone know if SaX can be made run on a debian based? Or does Novell keep that as proprietary?

---

### Post by tseliot on 2006-01-27
[QUOTE=Sionide]I can only really think of one thing which Linux doesn't have - which Windows does really well.

A GUI to sort out Dual Monitors. Windows does it in a jiffy, right-click Desktop, advanced, blah, takes maybe 5 or 6 clicks - with other software installed (Ultramon etc) you get extra control over the 2nd monitor, such as stretching the task bar across both screens etc.[/QUOTE]

I'm sorry to contradict you but Fedora Core 4 has a GUI for that. Therefore the problem is Ubuntu's.

BTW I'm using FC4 and I find it great!

---

### Post by curuxz on 2006-01-27
[QUOTE=CompShrink]I am NOT sorry to say, you are both wrong:

I ran a dualscreen setup, with a PCI and an AGP card, on which I could move windows between the two screens just fine. And one was at 1600x1200, the other at 1024x768. You can have two different cards, with two different resolutions, and have one connected desktop span both.[QUOTE]

Im in ubuntu and I too have tihs kind of setup, but chose to run them both in equal res. I agree there are slight manaul parts of the process HOWEVER... KDE 3.5 Addresses this with a fantastic dual monitor support package and I think gnome is going down the same route. I agree that more support is needed for a gui version (which I think is comming). But should point out that if we go down that route I think we should have a Ubuntu control centre (along the lines of the graphical YAST tool from suse). 

A GUI that could control all apects of your ubuntu box would kick ***! 

Maybe its already in the pipe i dont know...

---

### Post by poofyhairguy on 2006-01-27
[QUOTE=CompShrink]I am NOT sorry to say, you are both wrong:

I ran a dualscreen setup, with a PCI and an AGP card, on which I could move windows between the two screens just fine. And one was at 1600x1200, the other at 1024x768. You can have two different cards, with two different resolutions, and have one connected desktop span both.
[/QUOTE]

Yeah, since I first posted I found a laptop Xorg.conf that does that. Seems useful.

---

### Post by poofyhairguy on 2006-01-27
[QUOTE=tseliot]I'm sorry to contradict you but Fedora Core 4 has a GUI for that. [/QUOTE]

I would love to see a screenshot of that....

---

### Post by tseliot on 2006-01-27
[QUOTE=poofyhairguy]I would love to see a screenshot of that....[/QUOTE]
Here you go:
[[IMG]http://img78.imageshack.us/img78/3264/dualhead2qq.th.png[/IMG]](http://img78.imageshack.us/my.php?image=dualhead2qq.png)

---

### Post by curuxz on 2006-01-27
Nice screen shot but im pretty sure that your showing the new KDE 3.5 menu not something fedora specfic (see my post where I mention its on its way to ubuntu in dapper). I may be wrong on this, since I cant check atm (I have not got 3.5 installed or even kde for that matter due to dapper testing).

Could a kubuntu user please check if this menu is in KDE (and please check your using KDE 3.5!!!)

---

### Post by tseliot on 2006-01-27
[QUOTE=curuxz]Nice screen shot but im pretty sure that your showing the new KDE 3.5 menu not something fedora specfic (see my post where I mention its on its way to ubuntu in dapper). I may be wrong on this, since I cant check atm (I have not got 3.5 installed or even kde for that matter due to dapper testing).

Could a kubuntu user please check if this menu is in KDE (and please check your using KDE 3.5!!!)[/QUOTE]
That utility is not included in KDE control centre but perhaps this  is not that relevant.

---

### Post by poofyhairguy on 2006-01-27
[QUOTE=tseliot]Here you go:
[[IMG]http://img78.imageshack.us/img78/3264/dualhead2qq.th.png[/IMG]](http://img78.imageshack.us/my.php?image=dualhead2qq.png)[/QUOTE]

Thanks a bunch. That looks neat. Can I have screenshots of the other tabs of that GUI?

I might learn python this year just to steal that from the Fedora project.

---

### Post by tseliot on 2006-01-28
[[IMG]http://img22.imageshack.us/img22/6127/dualhead18cx.th.png[/IMG]]("[URL=http://img22.imageshack.us/my.php?image=dualhead18cx.png)"][[IMG]http://img22.imageshack.us/img22/6127/dualhead18cx.th.png[/IMG]](http://img22.imageshack.us/my.php?image=dualhead18cx.png)[/URL]

---

### Post by tseliot on 2006-01-28
[[IMG]http://img22.imageshack.us/img22/3286/dualhead26ep.th.png[/IMG]]("[URL=http://img22.imageshack.us/my.php?image=dualhead26ep.png)"][[IMG]http://img22.imageshack.us/img22/3286/dualhead26ep.th.png[/IMG]](http://img22.imageshack.us/my.php?image=dualhead26ep.png)[/URL]

[[IMG]http://img22.imageshack.us/img22/5310/dualhead39la.th.png[/IMG]]("[URL=http://img22.imageshack.us/my.php?image=dualhead39la.png)"][[IMG]http://img22.imageshack.us/img22/5310/dualhead39la.th.png[/IMG]](http://img22.imageshack.us/my.php?image=dualhead39la.png)[/URL]

I was thinking of learning Phython to make nice GUI for the topics dealt in my guides. You're not the only one ;)

---

### Post by Randomskk on 2006-01-28
[QUOTE=poofyhairguy]
I also love having a Gnome Panel and Taskbar for each desktop. Its great- as I drag applications from one monitor to the other it goes from the taskbar on that first monitor to the taskbar on the second one. I would take that over having one big taskbar (ala XP) anyday.[/QUOTE]

I've got dual head setup, it's got a taskbar for each screen (KDE), mouse moves between them, but I can't yet get windows to move from screen to screen...
If I try and drag a window, it (when it reaches the edge) snaps to the other edge of the same screen, and the mouse continues on into the second screen.

I don't suppose there's an easy line in xorg.conf to get the window to go the other screen? Or any way to send them accross screens? I kinda miss that.

My [xorg]("http://randomskk.net/RANDOM/xorg.conf")

---

### Post by el3ktro on 2006-01-30
For me dual head setup just sucks. I basically just want to have videos played on the connected TV fullscreen, but I don't want to have a complete desktop on the 2nd screen, it's just resource consumption. A GUI for this and better support in X.Org would be great.

Tom

---

### Post by UbuWu on 2006-01-31
[QUOTE=curuxz]Nice screen shot but im pretty sure that your showing the new KDE 3.5 menu not something fedora specfic.[/QUOTE]

It is Fedora specific, not KDE:

[http://fedora.redhat.com/projects/config-tools/redhat-config-xfree86.html](http://fedora.redhat.com/projects/config-tools/redhat-config-xfree86.html)

But there has been some discussion on the development mailing lists about including it in Ubuntu :KS

---

### Post by UbuWu on 2006-01-31
It would be nice if someone could at least package that for Universe by the way.

---

### Post by CompShrink on 2006-02-07
Wait... that says Xfree86!?

Fedora still uses XFree86? Heh... allt he dualmonitor settings I've seen are the same for both anyway. Is there any syntax differences at all between xorg and xfree86 conf files?

Anyway, I agree it deffinately needs to be packaged for Ubuntu. I also wish for a Gnome version...

---

### Post by TMBridge on 2006-09-06
> I also love having a Gnome Panel and Taskbar for each desktop. Its great- as I drag applications from one monitor to the other it goes from the taskbar on that first monitor to the taskbar on the second one. I would take that over having one big taskbar (ala XP) anyday.

How are you accomplishing this?  With my current configuration, I can move windows freely from monitor to monitor, but I have only 1 gnome panel with the windows list.  If i try to add another panel on the secondary monitor, the current one is removed.  Thanks for your help.

Tim

---

### Post by xhaan on 2006-09-06
I somehow ended up with an ATI control panel that works the same as the one I have in Windows, including dual monitors with spanning desktop... I'm not even sure how or when I got that feature though. Must have gotten added when I installed ATI drivers.

---

### Post by raublekick on 2006-09-06
My dual monitor setup was kinda spoiled when I first tried it in Windows. I have my 17" laptop at 1920x1200 and a 19" LCD at 1440x900. But in Windows on my laptop I have Dell's 120DPI fonts used, so everything looks bigger, and it's necessary too. So then when I drag something to my other monitor it looks nasty and huge. 

But in KDE I don't need 120 DPI fonts, because everything looks fine as-is. I haven't tried to set up my other monitor with it yet, though, because I borked my system when I installed the nvidia driver last, and haven't tried it again since.

---

### Post by Randomskk on 2006-09-06
Kubuntu Edgy has this:
[IMG]http://randomskk.net/uploads/screenshots/screenshot67.jpg[/IMG]

---

### Post by Brunellus on 2006-09-06
So when will GNOME follow suit with a similarly gnarly implementation?  Kan't let KDE keep the kool toys to itself.

---

