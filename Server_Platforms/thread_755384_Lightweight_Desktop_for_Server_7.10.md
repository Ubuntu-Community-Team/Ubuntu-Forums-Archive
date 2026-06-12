---
title: "Lightweight Desktop for Server 7.10"
date: 2008-04-14
forum: Server Platforms
---

### Post by snorkytheweasel on 2008-04-14
[LIST]
[*]I have to have a GUI for my server - boss's orders.
[*]I need to join the Windows domain
[*]I want to use Dolphin because it's the graphical file manager that has worked best for me, but I am open to suggestions
[/LIST]

I have used 3 different approaches to this:
[LIST=1]
[*]xubuntu-desktop
[*]kubuntu-desktop
[*]kubuntu-desktop installed after installing xubuntu-desktop
[/LIST]

*[ As an aside , I join the windows domain by tweaking* [FONT="Courier New"]**/etc/samba/smb.conf**[/FONT] *and using the*  [FONT="Courier New"]**net join**[/FONT] *command ]*.

Kubuntu gives me the ability to use Dolphin so I can browse the windows domain. However, I'd prefer something that uses less resources.

Xubuntu seems quicker than Kubuntu, and would probably be a good choice, since it allows using Dolphin on local files. However, if I attempt to browse the domain using Dolphin, the system throws an error and prevents access to the domain: 

[FONT="Courier New"][B]Error- Dolphin
Malformed URL
Remote :/[/B][/FONT]

If I install kubuntu desktop over xubuntu/xfce:
[FONT="Courier New"][B]
sudo apt-get update
sudo apt-get install kubuntu-desktop[/B]
[/FONT]
I get a hybrid desktop that has features of both xubuntu and kubuntu. It adds KDE programs to the menus for Office, Multimedia, Graphics, Games, and Accessories, but somewhat maintains the look of xubuntu. What's important is that it still seems quicker than a full-blown Kubuntu installation, and it allows Dolphin to access the domain.

Note: after creating the hybrid desktop, the "About" menu item discusses xfce (as does xubuntu) and makes no reference to KDE (as does Kubuntu).

I guess I could leave well-enough alone, but...
[LIST=1]
[*]Is there a better way to keep a lightweight GUI desktop AND be able to access the domain using Dolphin or some other GUI file manager?
[*]How do I remove the unneded bloatware added by Kubuntu/KDE?
[/LIST]

---

### Post by kerry_s on 2008-04-14
dolphin suppose to be the lighter version of konqueror, right?
so you can actually use just konqueror with a light wm.
or you could just not install desktop meta packages and just use the environment.
example: xfce4 instead of xubuntu-desktop
example: kde-core instead of kubuntu-desktop

so something like:
server install
sudo apt-get install xorg kdm kde-core
or
something like:
server install
sudo apt-get install xorg gdm xfce4 konqueror

konqueror can do both file manager and web browser.
dolphin is a young program, still working out the bugs.

---

### Post by snorkytheweasel on 2008-04-22
Konqueror konquered the dilemma that nearly konquered me.

THX

---

