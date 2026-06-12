---
title: "Windows and Linux Together"
date: 2008-02-18
forum: The Cafe
---

### Post by darrensnospam on 2008-02-18
Just a thought I'd like some feedback on.

I've been playing with Linux for about 3 years now. Today, I downloaded the Alpha version of KDE and installed it on my Windows machine.

I've played with WINE and virtualization and dual boots and so forth.

I am primarily a Windows user, today.

It appears that there are a lot of folks that want to run Windows apps but like Linux and the open source set of beliefs.

If I could have my druthers, I would like to 'run' Linux and be able to run Windows programs.

Is there a Linux installation that can be performed on top of Windows that will give the user the Linux User Interface and the ability to do everything with Linux and run Windows programs?

I could see that someone could create an install that would rewrite major portions of a Windows installation and create a Windows/Linux environment where everything works.

Microsoft has this Vista Basic out now. It's really quite limited in features. Linux has the ability to do most (all?) of the networking features that Ultimate can do. What if a person could purchase a machine with Vista basic and then load Linux on top of it? The user could then have Compiz and also have all the advanced networking features and could run Linux and Windows programs. They could run xfce as the gui window and then run the Windows programs as needed. 

I'm thinking that these oses would run side by side rather than a virtualization scenario.

Thoughts?

---

### Post by billgoldberg on 2008-02-18
You can run alot of windows programs on linux. 

To run those programs you will need "wine", it's in the repo's.

And I believe kde4 is now available for windows xp.

Loading linux on top of windows would be impossible.

---

### Post by bobbybobington on 2008-02-18
Try Cedega, or Virtualization, web apps are also becoming more prominent.

---

### Post by aktiwers on 2008-02-18
Maybe if you install KDE on Winodws and Linux seamless in VMware or Virtualbox.

But why use Windows as host? Because of games?

If I was to run such setup, Linux would be a better host IMO.

---

### Post by akiratheoni on 2008-02-18
You could virtualize... with the exception of programs that use 3D acceleration, you can run almost every Windows program under the sun -- Photoshop, Flash, Office, and tons of other ones. It's probably the best solution if you virtualize WIndows under Linux.

---

### Post by phrostbyte on 2008-02-18
[http://www.youtube.com/watch?v=Kxk6oFqMJVY](http://www.youtube.com/watch?v=Kxk6oFqMJVY)

---

### Post by darrensnospam on 2008-02-18
Thanks for the thoughts.

It seems reasonable that since most pre-built computers come with Windows, a Linux installation could be made that would marry the two capabilities.

It could be marketed to folks as a way to upgrade their Windows installations.

Linux could be the base for the OS but then Windows apps and all the Windows sub-structure could be used for Windows applications.

Games would be one thing that I would be looking for. In virtualization, 3d runs a bit differently.

Also, I wouldn't want to be looking at a windows start menu in addition to my Linux start menu. I would want to just have gnome or KDE or xfce as my windowing system and click on the shortcut and go.

---

### Post by Jimmey on 2008-02-18
[http://www.cygwin.com/](http://www.cygwin.com/)

try that?

---

### Post by phrostbyte on 2008-02-18
> **darrensnospam said:**
> Thanks for the thoughts.

It seems reasonable that since most pre-built computers come with Windows, a Linux installation could be made that would marry the two capabilities.

It could be marketed to folks as a way to upgrade their Windows installations.

Linux could be the base for the OS but then Windows apps and all the Windows sub-structure could be used for Windows applications.

Games would be one thing that I would be looking for. In virtualization, 3d runs a bit differently.

Also, I wouldn't want to be looking at a windows start menu in addition to my Linux start menu. I would want to just have gnome or KDE or xfce as my windowing system and click on the shortcut and go.

You can modify Windows XP to not show the taskbar. I believe there is also a way to make Virtualbox launch specific applications. 

The most seamless solution currently however is Wine. Windows applications literarly run on Linux, no emulation, no virtualization, the Wine project basically attempts to create a Windows compatability layer. You don't even need a copy of Windows.

There is no perfect solution yet however. But it's not hopeless. This may change. Just less then a year ago seamless virtualization wasn't possible, and Wine couldn't handle Photoshop and iTunes. Wine is improving rapidly. Virtualization is improving rapidly, in fact AMD is working on a solution to the video card problem (graphics card virtualization). I think life is going to get easier for people who want to use both Linux and Windows apps at the same time.

---

### Post by k2t0f12d on 2008-02-18
Thanks, this reminded me to do a fetch for the lastest git from WINE.

---

### Post by akiratheoni on 2008-02-18
> **darrensnospam said:**
> Thanks for the thoughts.

It seems reasonable that since most pre-built computers come with Windows, a Linux installation could be made that would marry the two capabilities.

It could be marketed to folks as a way to upgrade their Windows installations.

Linux could be the base for the OS but then Windows apps and all the Windows sub-structure could be used for Windows applications.

Games would be one thing that I would be looking for. In virtualization, 3d runs a bit differently.

Also, I wouldn't want to be looking at a windows start menu in addition to my Linux start menu. I would want to just have gnome or KDE or xfce as my windowing system and click on the shortcut and go.

I don't want to sound harsh or anything but of course it's been tried. And it's not as easy as it sounds... Wine developers have been at it for more than ten years but Microsoft keeps hiding some of their documentation so Wine developers either have to guess or reverse engineer Windows to learn of some of the system calls and such.

---

### Post by Countryboy123 on 2008-02-18
You wrote: Is there a Linux installation that can be performed on top of Windows that will give the user the Linux User Interface and the ability to do everything with Linux and run Windows programs?

I Think the answer is Wubi, it makes a Ubuntu os into a Wndows program.( Please note - I have not used it personally. It  just seemed to answer your question.)  [http://wubi-installer.org/index.php](http://wubi-installer.org/index.php) .

---

