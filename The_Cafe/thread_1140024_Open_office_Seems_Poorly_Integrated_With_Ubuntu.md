---
title: "Open office Seems Poorly Integrated With Ubuntu"
date: 2009-04-27
forum: The Cafe
---

### Post by Penguin Guy on 2009-04-27
There are a number of things about Open Office that don't seem to be integrated with Ubuntu:

[LIST]
[*]Tabs appear rainbow-coloured
[*]Linux 'Preferences' are accessed through the Windows-style Tools -> Options...
[*]Stores info at /home/<user>/ instead of simply ~/
[*]There is a 'User Data' section - if Ubuntu is as good as most people say then shouldn't Open Office load this data from an XML file stored at ~/.user-data for example?
[/LIST]

The above are just a few examples of how badly integrated Open Office is with Ubuntu. It seems like a wise idea for some Ubuntu programers to work on integration. Please post your comments.

---

### Post by blade1950 on 2009-04-27
I noticed that in the add/remove programs and in synaptic Open Office is showen as not installed. I wonder if what comes with Ubuntu is just a "promo"?

---

### Post by rzrgenesys187 on 2009-04-27
> **blade1950 said:**
> I noticed that in the add/remove programs and in synaptic Open Office is showen as not installed. I wonder if what comes with Ubuntu is just a "promo"?

I'm not sure about now, but previously it was a recompiled OpenOffice.org from which all of the components that depended on Java were removed.  However since Java has been open sourced this shouldn't be an issue any more.

---

### Post by ashmew2 on 2009-04-27
<whine> Well not only OO , but also Firefox etc seem to be integrated not so well. I mean if you click the IE6 icon on an XP machine , it opens instantly ,  but with Ubuntu and Firefox there is always a time lag between the clicking of the icon and the loading of the firefox main Window..</whine>

I second the fact that the OO integration should be looked into by someone capable enough like the Ubuntu Devs!

---

### Post by SunnyRabbiera on 2009-04-27
> **Penguin Guy said:**
> There are a number of things about Open Office that don't seem to be integrated with Ubuntu:

[LIST]
[*]Tabs appear rainbow-coloured
[*]Linux 'Preferences' are accessed through the Windows-style Tools -> Options...
[*]Stores info at /home/<user>/ instead of simply ~/
[*]There is a 'User Data' section - if Ubuntu is as good as most people say then shouldn't Open Office load this data from an XML file stored at ~/.user-data for example?
[/LIST]



I dont know what you are talking about, OO seems fine.
The menu thing doesnt bother me as hey OO is a MS office comeptitor so it having MS like menu's kind of makes sense...
Heck it makes more sense then MS office 2007

as for its storing stuff to /home, every linux app does this.
This is because in linux all users are separated from the core of the OS, so profiles dont conflict and no issues arise.
Linux is a multi-user operating system, while in Windows its "one size fits all"
This is both good and bad at the same time, the linux way isnt perfect either but keeping profiles separate is one of the reasons linux is secure.

as for you last one, what the #*%^$%???
If anything this might be more of a OO issue then a Ubuntu one...

> **ashmew2 said:**
> <whine> Well not only OO , but also Firefox etc seem to be integrated not so well. I mean if you click the IE6 icon on an XP machine , it opens instantly ,  but with Ubuntu and Firefox there is always a time lag between the clicking of the icon and the loading of the firefox main Window..</whine>


Personally I see no difference between the load of firefox on windows and linux, the only time my firefox hangs is if I have too many tabs saved.

---

### Post by benj1 on 2009-04-27
the version in add/remove just adds base? the database access program. also its proper open office as opposed to the novell sponsored go open office i think.
proper open office is even less integrated it uses different icons and everything.
thats probably the issue, the open office guys don't seem to be up on doing things the standard way, and ubuntu have already made quite a few changes to integrate it already.

---

### Post by Mr. Picklesworth on 2009-04-27
OpenOffice cannot really be integrated much better because it is written with a foreign UI toolkit and built to be practically a clone of Microsoft Office; warts and all. It's somewhat miraculous they got it as far as they have, appearance wise.

Firefox has the same problem: Wrong UI toolkit, etc. thus tons to load when it starts up. It happens to be a bit tidier in design so generous people can contribute patches making it *look* sane in GNOME, but it is still a tad out of place. Epiphany is a browser that uses GTK and fits in GNOME smoothly -- and the Webkit version performs pretty nicely, too. (Watch for it in Ubuntu 9.10). Midori is also a good choice.


If you want office tools that are smoother and better integrated, there's Abiword for writing, Gnumeric for spreadsheets, Planner for project management and Glom for databases.

Lyx is another one worth looking into, although it uses Qt (and thinks like KDE) so still isn't perfect on the integration front. It's a nice application for LaTeX, which is really a lot smarter than today's mainstream word processors. Especially for large documents.



My opinion is that the world lacks decent word processors. Looking forward to someone taking the opportunity...

---

### Post by wolfen69 on 2009-04-27
> **ashmew2 said:**
> I mean if you click the IE6 icon on an XP machine , it opens instantly

maybe on your computer, but every time i'm on a windows machine, IE takes at least 5-10 seconds to open. firefox for me, takes about 2 seconds to open.

---

### Post by MaxIBoy on 2009-04-27
> **ashmew2 said:**
> <whine> Well not only OO , but also Firefox etc seem to be integrated not so well. I mean if you click the IE6 icon on an XP machine , it opens instantly ,  but with Ubuntu and Firefox there is always a time lag between the clicking of the icon and the loading of the firefox main Window..</whine>

I second the fact that the OO integration should be looked into by someone capable enough like the Ubuntu Devs!This is because OO and Firefox are both primarially Windows programs, and are centrally designed to fit in with Windows. The Linux ports are secondary in priority. Hey, I don't like it either.

---

### Post by swoll1980 on 2009-04-27
> **wolfen69 said:**
> maybe on your computer, but every time i'm on a windows machine, IE takes at least 5-10 seconds to open. firefox for me, takes about 2 seconds to open.
IE 6 Is like grease lighting on my computer. As soon as I click it, it's  open. If you blinked, you would miss it. I don't use the piece of crap though. so it doesn't matter all that much.

---

### Post by jmszr on 2009-04-27
ashmew2,

If you want Firefox (and other apps) to load faster: [http://ubuntu-tutorials.com/2008/07/08/improve-application-startup-times-with-preload/](http://ubuntu-tutorials.com/2008/07/08/improve-application-startup-times-with-preload/). If you actually use IE6 you sure do like to live dangerously.

What the preload will do to your boot time I do not know.

---

### Post by mcduck on 2009-04-27
> **ashmew2 said:**
> <whine> Well not only OO , but also Firefox etc seem to be integrated not so well. I mean if you click the IE6 icon on an XP machine , it opens instantly ,  but with Ubuntu and Firefox there is always a time lag between the clicking of the icon and the loading of the firefox main Window..</whine>

I second the fact that the OO integration should be looked into by someone capable enough like the Ubuntu Devs!

That is because Windows loads IE into memory at boot time, no matter if you use it or not. So the boot time takes longer but once you finally get to desktop IE starts quick. Of course if you happen to use some other browser instead you only get the longer boot time but no benefits.. ;)

---

### Post by ashmew2 on 2009-04-28
> **jmszr said:**
> ashmew2,

If you want Firefox (and other apps) to load faster: [http://ubuntu-tutorials.com/2008/07/08/improve-application-startup-times-with-preload/](http://ubuntu-tutorials.com/2008/07/08/improve-application-startup-times-with-preload/). If you actually use IE6 you sure do like to live dangerously.

What the preload will do to your boot time I do not know.
Thanks for the help jmszr and all the others :)
I do not use IE lol..Ive been sticking with firefox for about 3 years now. I just put forth a comparison and yes i think i have found the answer to that. I dont really mind a little longer boot up time if i can click and instantly open Firefox etc. Thanks! :D

---

### Post by ashmew2 on 2009-04-28
> **mcduck said:**
> That is because Windows loads IE into memory at boot time, no matter if you use it or not. So the boot time takes longer but once you finally get to desktop IE starts quick. Of course if you happen to use some other browser instead you only get the longer boot time but no benefits.. ;)

Yeah well thats there..But Since i AM going to use Firefox , Nautilus and Deluge , i might as well add them to load on bootup so i dont have to live with the time lag. And i think i have enough RAM to accomodate that (3 GB right now). Thanks for the info :)

---

### Post by bryncoles on 2009-04-28
> **Mr. Picklesworth said:**
> Lyx is another one worth looking into, although it uses Qt (and thinks like KDE) so still isn't perfect on the integration front. It's a nice application for LaTeX, which is really a lot smarter than today's mainstream word processors. Especially for large documents.

+1 for LaTeX, though rather than installing lyx (which is a rather poor implementation of LaTeX IMHO - i understand it changes some of the implementations), id recommend texmaker. you'll learn more about LaTeX using that, and its cross-platform!

texmaker is built on QT, which means it wont solve your integration issue off the bat, but combine using texmaker with reading 'a not so short introduction to latex' (google for the free pdf) and you'll be able to write your documents in gedit, with LaTeX markup, then you'll have perfect integration. 

in fact, why not use the gedit LaTeX plugin?

---

### Post by Penguin Guy on 2009-04-28
So there is no way that the Ubuntu programmers could convert Firefox and OO into a Linux-compatible UI?

---

### Post by LowSky on 2009-04-28
Linux compatable UI?

What for? Why does everything have to conform?

Personally I like that OpenOffice and Firefox work the same in Linux as in Windows, as I use both, having to remember different way to run an application is confusing to the user and ruins the experience. So having a similar experience is a better idea.  Having them conform to  the GUI settings is not really needed. Why does it really matter if the icons are the same as the ones you have for you windows manager?

As for Firefox/Openoffice being slow, it all depends on your hardware, and your personal settings. On my machine both open quickly, an I mean my Intel Atom based netbook, as that is what I'm typing on now. My desktop is blindingly faster so doing anything on it will seem super quick.

---

### Post by Rackstar on 2009-04-28
Those are some good points. But I have more issues with the fact that OO in Ubuntu doesn't "refresh" it's GUI enough. I need to minimize/maximize often to get the view to refresh.

---

### Post by NightwishFan on 2009-04-28
Internet Explorer is an integral part of Windows. You can consider it to be always running or cached. The cold execution of the program with it or none of it's shared libraries caches is essentially impossible.

(Simple way to prove this)

On Windows Vista, with superfetch enabled, log in and open IE and WMP. They should open instantaneously. This is due to active preloading of them, and the fact Windows is designed around them.

Disable superfetch service and delete the superfetch cache folder (I forget where it is). Then reboot, and judge the appropriate times in comparison.

The only problem with this comparison is that modern computers have resources to spare, and that most Microsoft programs are preloaded regardless of your settings. (Office 2003)

---

### Post by Sukarn on 2009-04-28
> **MaxIBoy said:**
> This is because OO and Firefox are both primarially Windows programs, and are centrally designed to fit in with Windows. The Linux ports are secondary in priority. Hey, I don't like it either.

The development of Firefox started on a *nix system, not on Windows.

---

### Post by gnomeuser on 2009-04-28
> **Mr. Picklesworth said:**
> OpenOffice cannot really be integrated much better because it is written with a foreign UI toolkit and built to be practically a clone of Microsoft Office; warts and all. It's somewhat miraculous they got it as far as they have, appearance wise.

Firefox has the same problem: Wrong UI toolkit, etc. thus tons to load when it starts up. It happens to be a bit tidier in design so generous people can contribute patches making it *look* sane in GNOME, but it is still a tad out of place. Epiphany is a browser that uses GTK and fits in GNOME smoothly -- and the Webkit version performs pretty nicely, too. (Watch for it in Ubuntu 9.10). Midori is also a good choice.

If you want office tools that are smoother and better integrated, there's Abiword for writing, Gnumeric for spreadsheets, Planner for project management and Glom for databases.

Lyx is another one worth looking into, although it uses Qt (and thinks like KDE) so still isn't perfect on the integration front. It's a nice application for LaTeX, which is really a lot smarter than today's mainstream word processors. Especially for large documents.

My opinion is that the world lacks decent word processors. Looking forward to someone taking the opportunity...

you and others might enjoy [this](http://davidnielsen.wordpress.com/2008/12/30/on-firefox-as-the-free-software-mascot/) little rant on why it is dangerous let OpenOffice and Firefox be the poster boys for Open Source.

Integration is important, and not just with Linux, with every platform you run on. OpenOffices solution to being cross platform in it's most basic form precludes proper integration.

---

### Post by MaxIBoy on 2009-04-28
> **Sukarn said:**
> The development of Firefox started on a *nix system, not on Windows.The development of Windows itself started on a *nix system. So what?

---

