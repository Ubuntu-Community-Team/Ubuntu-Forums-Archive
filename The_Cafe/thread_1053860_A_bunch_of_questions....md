---
title: "A bunch of questions..."
date: 2009-01-29
forum: The Cafe
---

### Post by sharathpaps on 2009-01-29
Ok, I have a bunch of questions that are varied in topic and I'm sure all of them are pretty basic and even stupid. But then, I'm new to Linux and I'd like to have my basics straight...I don't know if this is the right place for this thread in the forum.

Q.No.1> What is a Desktop Manager? I know that Gnome & KDE are desktop managers, but what do they actually do? What other options exist?

Q.No.2> I'm confused about Window Managers. What does a window manager do? I know that 'X' is a window manager. What other options exist?

Q.No.3> What in the world is 'Compiz' ? Everyone seems to mention it sometime or the other. Is there an alternative to Compiz?

Q.No.4> Where does Nautilus fit in? What is Nautilus in the first place? What other options exist?

Q.No.5> Is it possible to play mix n match with all these managers on every distro?

Q.No.6> What is a Repository? Who maintains these repositories? 

Q.No.7> O.K, This last one might be personal. If all these companies give away whole OS'es and so much of software away for free, how do they make money? How do they feed their families? I mean Micro$oft can't seem to have enough of it and the Linux community is doing a wonderful job for free!! Please don't get me wrong, I love the brotherhood that comes bundled with the OS :biggrin: and I really wish there was something I can do to help.

I do have more questions and I'll put them down here soon as I make sense of them myself...

Thanks

---

### Post by lisati on 2009-01-29
1-6) Short and possibly not too helpful answer: these are all parts of the overall system for managing what's shown on your screen and finding your way around what's on your computer and/or network

7) A repository is a collection of files, usually on a server, that Ubuntu can use to add new software and update itsself.

---

### Post by jespdj on 2009-01-29
Wikipedia and Google know the answer to almost any question you can imagine:

[http://en.wikipedia.org/wiki/Desktop_manager](http://en.wikipedia.org/wiki/Desktop_manager)
[http://en.wikipedia.org/wiki/Window_manager](http://en.wikipedia.org/wiki/Window_manager)
[http://en.wikipedia.org/wiki/Compiz_Fusion](http://en.wikipedia.org/wiki/Compiz_Fusion)
[http://en.wikipedia.org/wiki/Nautilus_(file_manager)](http://en.wikipedia.org/wiki/Nautilus_(file_manager))

[What are Repositories?](https://help.ubuntu.com/community/Repositories/Ubuntu)

[http://en.wikipedia.org/wiki/Free_software](http://en.wikipedia.org/wiki/Free_software)

---

### Post by mcduck on 2009-01-29
1. You probably mean Desktop environment? It's a collection of everything you need for  usable computer desktop. Window Manager, File Manager, collection of configuration tools, panels, menus, and programs to do different things. Gnome, KDE and XFCE are popular desktop environments.

2. Window Manager allows your running programs to display inside windows, and makes it possible to move these windows around, minimize them etc. Window manager is also responsible of drawing the window borders (X is not a window manager!). Commonly used window managers are MEtacity (Gnome's default). 

3. Compiz is a window manager that has some extra features (mainly compositing, which allows using all kinds of desktop effects). If you enable the "Desktop Effects" in Gnome you enable using Compiz as windw manager instead of Gnome's own WM, Metacity.

4. Nautilus is the file manager used in Gnome. Every time you open a directory to view it's contents you do it with Nautilus. Nautilus also manages Gnome's desktop ivons and right-click menu.

5. Yes, it is.

6. Repository is an internet server that distributes software packages for your package manager. Anybody can maintain a repository.

7. Some don't make money, others make it by providing support and other services. Also there's no rule against selling open source software, many Linux distributions have commercial versions.

---

### Post by RichardLinx on 2009-01-29
[B]Q.No.1> What is a Desktop Manager? I know that Gnome & KDE are desktop managers, but what do they actually do? What other options exist?
[/B]
In graphical computing, a desktop environment (DE) commonly refers to a style of graphical user interface (GUI) that is based on the desktop metaphor which can be seen on most modern personal computers today.
A desktop environment typically consists of icons, windows, toolbars, folders, wallpapers, and desktop widgets.

**Q.No.2> I'm confused about Window Managers. What does a window manager do? I know that 'X' is a window manager. What other options exist?**
A window manager is computer software that controls the placement and appearance of windows within a windowing system in a graphical user interface.
[http://en.wikipedia.org/wiki/Window_Manager](http://en.wikipedia.org/wiki/Window_Manager)

**Q.No.3> What in the world is 'Compiz' ? Everyone seems to mention it sometime or the other. Is there an alternative to Compiz?**
Compiz is a compositing window manager.
[http://en.wikipedia.org/wiki/Compiz](http://en.wikipedia.org/wiki/Compiz)

**Q.No.4> Where does Nautilus fit in? What is Nautilus in the first place? What other options exist?**
Nautilus is the official file manager for the GNOME desktop.
[http://en.wikipedia.org/wiki/Nautilus_(file_manager](http://en.wikipedia.org/wiki/Nautilus_(file_manager))
[B]
Q.No.5> Is it possible to play mix n match with all these managers on every distro?[/B]
Yes.

**Q.No.6> What is a Repository? Who maintains these repositories? **
Think of the repositores in Linux as digital software libraries.

[B]
Q.No.7> O.K, This last one might be personal. If all these companies give away whole OS'es and so much of software away for free, how do they make money? How do they feed their families?[/B]
Some people are payed to actively develop for Linux. For example: Canonical hire people to develop for Ubuntu, those developers get payed. Canonical hope to make money in the future with Ubuntu by selling support. This is just one of many ways, a large part of the work is just free volunteer work that people do in there spare time.

Source: [http://en.wikipedia.org/wiki/Main_Page](http://en.wikipedia.org/wiki/Main_Page)

---

### Post by sharathpaps on 2009-01-29
Thank You guys for your patience to answer all those questions... A lot of things are suddenly beginning to make sense... :p

---

### Post by xpod on 2009-01-29
[http://xwinman.org/](http://xwinman.org/)

That`s quite a good site for the Desktop Environment/Window Manager questions.

---

### Post by billgoldberg on 2009-01-29
**Q.No.1> What is a Desktop Manager? I know that Gnome & KDE are desktop managers, but what do they actually do? What other options exist?**

A DE (desktop enviroment) like gnome and kde offer a window manager, and lots of applications (panel, IM client, config tools, browser, ...)


**Q.No.2> I'm confused about Window Managers. What does a window manager do? I know that 'X' is a window manager. What other options exist?**

X isn't a window manager. 

A windows manager (metacity in gnome, kwin in kde, compiz fusion, fluxbox, ...) manages the windows. You can move them, close them, minimize them, drag them, ...

**Q.No.3> What in the world is 'Compiz' ? Everyone seems to mention it sometime or the other. Is there an alternative to Compiz?**

Compiz is a fancy compositing windows manager. It provides loads of nice little effects. Youtube them.

Metacity, the default WM in Gnome has a compositing mode, as does kwin.

**Q.No.4> Where does Nautilus fit in? What is Nautilus in the first place? What other options exist?**

Nautilus is the file manager (think explorer in windows or finder in osx). Besides a file manager, it can handle ftp, ssh, smb, ... and it draws the desktop.

**Q.No.5> Is it possible to play mix n match with all these managers on every distro?**

Some yes, you can use Fluxbox with Nautilus.

**Q.No.6> What is a Repository? Who maintains these repositories?**

A repo is the place all the software you can install using the package manager (add/remove, synaptic, apt, aptitude). Basically it's a large list of software you can download and install, from one place.

It's maintained by Canonical, the corporation behind Ubuntu.

**Q.No.7> O.K, This last one might be personal. If all these companies give away whole OS'es and so much of software away for free, how do they make money? How do they feed their families? I mean Micro$oft can't seem to have enough of it and the Linux community is doing a wonderful job for free!! Please don't get me wrong, I love the brotherhood that comes bundled with the OS :biggrin: and I really wish there was something I can do to help.**

They make money from support (mostly for corporations) and the selling of merchandise and donations.

Also Canonical is created and funded by Mark Shuttleworth. He's a dot com millionaire.

---

### Post by sharathpaps on 2009-01-29
thanks bill... :-)

appreciate the trouble you're taking to help out a noob... Thanks..

I'm really missing the thanks button here... A lotta people here I owe thanks too...

---

