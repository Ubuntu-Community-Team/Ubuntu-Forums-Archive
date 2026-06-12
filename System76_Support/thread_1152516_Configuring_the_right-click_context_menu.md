---
title: "Configuring the right-click context menu"
date: 2009-05-07
forum: System76 Support
---

### Post by glacialfury on 2009-05-07
Has anyone ever heard of a way to change the default behavior of the right-click context menu in gnome?  I'm interested in finding a mouse-based window selector.

---

### Post by thomasaaron on 2009-05-08
I've not heard of a way. I imagine the context menus are hard coded into the operating system, just as they are in any particular piece of software. But I could be wrong.

But when you say "window selector," do you mean switching from desktop to desktop or do you mean a right-click way to open various minimized programs?

Basically you can do both of those things with the click of a mouse already. So, I'm not completely sure what you are getting at.

---

### Post by glacialfury on 2009-05-11
I was looking for a way to open (restore if needed, bring to front) any program on that particular workspace via right-clicking on the desktop.  There would be a submenu or list of open applications/windows like that in the Window Selector panel applet, specific to that workspace.

The goal would be to eliminate the need for a panel-based window switcher; ALT-TAB, requiring you either to cycle through windows or view small screenshots of them, is also something I'd like to avoid.

It would be useful on a minimalist desktop with no panels.

---

### Post by thomasaaron on 2009-05-11
Yes, that would be a cool feature. You'd have to modify Ubuntu itself to do something like that, I think.

There are some similar keybindings in System > Preferences > Keyboard Shortcuts.

---

### Post by jdb on 2009-05-11
> **glacialfury said:**
> I was looking for a way to open (restore if needed, bring to front) any program on that particular workspace via right-clicking on the desktop.  There would be a submenu or list of open applications/windows like that in the Window Selector panel applet, specific to that workspace.

The goal would be to eliminate the need for a panel-based window switcher; ALT-TAB, requiring you either to cycle through windows or view small screenshots of them, is also something I'd like to avoid.

It would be useful on a minimalist desktop with no panels.

I use a minimal desktop called fluxbox.
Spinning the scroll wheel while the mouse
is on the desktop cycles through workspaces.

[My Desktop]("http://jdbowman.com/links/fluxbox.jpg")

Edit:

I just noticed that the scroll wheel does the same thing on Xubuntu which uses an XFCE4 desktop.
I don't have a copy of Gnome loaded right now so I don't know if it does or not.

One more Edit:

I just loaded Jaunty in Virtualbox, I've been meaning to do that anyhow :)
Scrolling doesn't change workspaces in Gnome.

[Virtualbox is cool]("http://jdbowman.com/links/Desktop2.jpg")

jdb

---

### Post by Cygnia on 2009-05-11
> **jdb said:**
> 
Scrolling doesn't change workspaces in Gnome.


Yes it does, on my Pangolin upgraded to Jaunty. I'm a newly returned Linux user of only the last several weeks and I don't remember changing anything other than installing Compiz.

---

### Post by jdb on 2009-05-11
> **Cygnia said:**
> Yes it does, on my Pangolin upgraded to Jaunty. I'm a newly returned Linux user of only the last several weeks and I don't remember changing anything other than installing Compiz.

It changes workspaces when I scroll with the mouse on the workspace applet in the task bar but not if the mouse is elsewhere on the desktop.

jdb

---

### Post by Cygnia on 2009-05-11
> **jdb said:**
> It changes workspaces when I scroll with the mouse on the workspace applet in the task bar but not if the mouse is elsewhere on the desktop.


For kicks and giggles I just tried to scroll on the panel applet but it won't change the workspace, only when scrolling on the desktop! It must be some hidden away setting either in Compiz or the regular prefs that switches between the two modes. Funny.

---

### Post by jdb on 2009-05-11
> **Cygnia said:**
> For kicks and giggles I just tried to scroll on the panel applet but it won't change the workspace, only when scrolling on the desktop! It must be some hidden away setting either in Compiz or the regular prefs that switches between the two modes. Funny.

This stuff will drive a guy nuts after a while ](*,)

jdb

---

### Post by jdb on 2009-05-13
> **jdb said:**
> This stuff will drive a guy nuts after a while ](*,)

jdb

I found out what the deal was.
I was using Jaunty from Virtualbox, visual effects are off by default and can't be turned on because there is no direct access to the video card.
I've now got Jaunty installed on a partition on my hard drive, visual effects are on by default & mouse scrolling changes desktops :rolleyes:

I noticed I drifted way off subject talking about switching workspaces when I think glacialfury really wanted to switch applications.
I might play around with that if I get a chance.

jdb

---

