---
title: "Super slim web only Ubuntu"
date: 2006-06-29
forum: The Cafe
---

### Post by g7kse on 2006-06-29
So I'm having a look at Linux and I agree with the Ubuntu Philosophy and am very keen to make the change.....theres always a but.

I've evaluated my IT use and I'm interested in radically changing the way I use my 'puter. With applications like web based mail and document packages like writley etc etc becoming more and more advanced. I would like to investigate the possibility of having no applications the hard disk, in fact maybe no hard disk at all. What is the possibility of something a little like this....?

My wish list would be something like this:

1. Fast booting (a few seconds at most). Minimal disk space needed (flash card OS? alternatives?)
2. On Ubuntu start up, start up web browser (Ubuntu flavoured Firefox). 
3. USB support for camera, portable media player, printer and scanner only
4. Support for ethernet connection to router

I appreciate that other distros such as damn small linux exist but these still come with applications on them and they still take their time to boot up. 

Can it be done? how is it done? bear in mind I'm a user not a IT guru.

Consider the gaunlet thrown

---

### Post by mozetti on 2006-06-29
I exist somewhere between 'user' and 'guru' and I really like this idea. For me, it would be a neat gimmick to try out, but it wouldn't replace my standard computer use/setup. But, I'd definitely use it whenever I could, just to see how it worked. I think it can be done, but your requirement of a "few seconds at most" bootup time is a bit unreasonable, I think. The browser can be started automagically using the Ubuntu/Gnome sessions settings.

This is a very cool idea, especially with the availability of online storage services, as long as you have an internet connection you could walk around with you computer in your pocket (USB flash drive).

---

### Post by minden on 2006-06-29
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by g7kse on 2006-06-29
That was a bit quicker than I expected. 

The start up time might be a bit unreasonable, but its aspirational. If you can do it with a pocket pc / palm pda. Then why not on a desktop?

Thanks for the pendrive link as well. I'll give it a look

I can't help think that this kind of thing will have a place in the future although it's a major step change for most people. I like to play about but sorely lack the skills to even understand what is going on in the background.

The trouble with this is that other users might want this or that added in and before you know it yuo're back to a full distro. Still worth a think.

---

### Post by bluenova on 2006-06-29
Why not do a server install (basic install) from the alternative disk, and then just install the few things you need like, a desktop manager, web browser and plugins.

---

### Post by g7kse on 2006-06-29
Is a server installation going to add services that wouldn't be needed to fit in with the criteria? Extras such as customisations for gnome,

---

### Post by Kvark on 2006-06-29
[QUOTE=g7kse]Is a server installation going to add services that wouldn't be needed to fit in with the criteria? Extras such as customisations for gnome,[/QUOTE]
The server install will add everything that is needed for a comfortable command line environment, such as apt-get, nano and so on. And nothing else.

I have never done this but I think that if you do a server install and then install a web browser plus a minimalistic window manager (not a full desktop environment such as gnome or xfce, that would be way too fat and bloated for what you want) then you should have everything you need. So depending on which web browser and window manager you choose you'd do something like this the first time you log into the server install:
```
sudo apt-get install fluxbox firefox
startx
```
...and then start surfing.

---

### Post by g7kse on 2006-06-29
Thank you all very much for the advice. I think I'll give it a go with a server installation and see where that gets me. I'll report back when I get somewhere or may end asking a load more questions.

Either way I'm very grateful for your very quick help

---

### Post by bluenova on 2006-06-29
yea, let us know how it goes, it sounds like an interesting project.

---

### Post by g7kse on 2006-06-29
Any suggestions for the window manager?

---

### Post by Kvark on 2006-06-29
I'd personally pick Ratpoison. It works like screen, the window manger for the command line.

Once it's configured correctly you'll start with a Firefox window in fullscreen, no panel, no window border, nothing, just Firefox in fullscreen. Which seems perfect for this. But there are 3 special perks to Ratpoison that you'll either love or hate.

1. Since there is no panel or menu everything involving the window manager is done with keyboard shortcuts. You start additional programs, switch between windows and so on with keyboard shortcuts. I guess this is a huge turnoff for those who want point and click.

2. Ratpoison is 'special' when you want to see multiple windows at once instead of one at a time in fullscreen. It doesn't use normal overlapping windows that you can drag around and resize. Instead you can split the screen between windows so you can have one window on the left half and another on the right, 4 windows taking one quarter of the screen each or any other split screen combination. I guess most people think this is a bit too weird. I think it's easier to press one keyboard shortcut that gives two windows half the screen each then to drag around the two windows until I have a good view of both.

3. You'll need to edit text config files a little to get comfortable with Ratpoison. For example by default Ctrl+T switches focus to Ratpoison so "Ctrl+T then 3" switches to the third window. This overrides Ctrl+T for new tab in Firefox so at least change this to the Super(Windows logo) buttons so it becomes "Super then 3" for 3rd window.



PS. I hope you keep your current system, at least until you are sure that you are comfortable with your new system.

---

### Post by bluenova on 2006-06-29
hmm, never heard of ratpoison. Sounds like it would be good for a kiosk or something too. One to add to my list of apps to play with.

---

### Post by John.Michael.Kane on 2006-06-29
[**ratpoison**]("http://www.nongnu.org/ratpoison/") info
Also is you have the time you can roll your own [**distro**]("http://www.linuxfromscratch.org/")

---

### Post by hizaguchi on 2006-07-01
You don't have to worry about the boot time if you never turn the computer off.  Just suspend to ram instead.  My laptop battery holds a charge for about 10 minutes while in use, but it lasts like a week if it's suspended, so energy usage-wise it's about as good as shutting it down completely.

---

### Post by prizrak on 2006-07-01
There have been projects like this in the past. They were called internet appliances and never really caught on. The best distro for what you want is Gentoo, it will let you have full control over everything you want.

---

### Post by K.Mandla on 2006-07-01
[QUOTE=g7kse]Any suggestions for the window manager?[/QUOTE]
I like Openbox over Fluxbox or IceWM, but I might be in a minority on that one. And I only like Openbox if you're not going to install XFCE.

You might pick the brains of the Damn Small Linux crowd. I know they talk of machines that boot from CF card and/or USB drive, which might gratify your desire for a hard-drive-less box. I'm not suggesting you switch to DSL -- just see how they did it and then transfer the concept to Ubuntu.

Good luck!

---

### Post by Chimes on 2006-07-01
totally IceWM for me. I use it all the time. I keep Kubuntu's KDE for the apps (I can't resist Adept... it's just so neat-o! ;) , also, knetworkmanager is pretty much the only way I can get my wireless card to work.) but other than that, it's all icewm. I use mocp for playing music, xfe for file exploration, etc. my computer is rarely at more than 5% of cpu usage unless I'm doing an updatedb or playing FLAC music.

Fluxbox and Blackbox and so on I'm sure would work just as well for the task. I just like IceWM because some of its themes are so gol-darned clean cut, and because I really, really don't like the way fluxbox handles its menus. (I don't know why... :-\" )

---

### Post by RAV TUX on 2006-07-01
[quote=g7kse]

My wish list would be something like this:

1. Fast booting (a few seconds at most). Minimal disk space needed (flash card OS? alternatives?)


I appreciate that other distros such as damn small linux exist but these still come with applications on them and they still take their time to boot up. 

Can it be done? how is it done? bear in mind I'm a user not a IT guru.

Consider the gaunlet thrown[/quote] 
The fastest boot I have seen is on PC-BSD, perhaps a Ubuntu/BSD hybrid would be nice both Gentoo and Debian are working on these projects and I am downloading "[**Ging**]("http://glibc-bsd.alioth.debian.org/ging/")" now, developed by Debain (a Debain/FreeBSD hybrid).

[http://glibc-bsd.alioth.debian.org/ging/]("http://glibc-bsd.alioth.debian.org/ging/")

Ging Gnome
[[IMG]http://img332.imageshack.us/img332/6756/ging0019kj.th.jpg[/IMG]]("http://img332.imageshack.us/my.php?image=ging0019kj.jpg")

Ging KDE
[[IMG]http://img332.imageshack.us/img332/4342/ging010rc17rw.th.png[/IMG]]("http://img332.imageshack.us/my.php?image=ging010rc17rw.png")


>      Ging is a Live system that you can burn on a CD. It is based on     [Debian GNU/kFreeBSD]("http://www.debian.org/ports/kfreebsd-gnu")     (which, as its time, is based on [Debian]("http://www.debian.org/"),     [GNU]("http://www.gnu.org/") and the kernel of     [FreeBSD]("http://www.freebsd.org/")).   
         Ging consists entirely of free software (as per Debian Free Software     Guidelines) and has a commitment to remain this way.
   

So your dream of an operating System not having to be installed on your hard drive has come true. As a live System you can just boot from CD.

---

### Post by g7kse on 2006-07-04
Seeing as all this seems to have been done before. Any clues as to why it never really caught on? was it that there weren't any web based applications that could replace dektop ones at the time or was it something else?.

I intended this to be a bit of a medium term project (few months) to get an understanding as to the pro's and con's to see if it was viable and i really appreciate the advice and support.

thanks

---

### Post by g7kse on 2006-07-05
I'm having a bit of difficulty in getting a window manager to install and start.

type sudo apt-get install fluxbox 

get no repository found return

firefox installed aok but not the window manager. Any suggestions

---

