---
title: "odd xserver experience"
date: 2008-01-11
forum: Ubuntu Brainstorm
---

### Post by spayced on 2008-01-11
This is mainly an observation and a suggestion about something that sort of puzzled me.
So I'm messing around on the services getting rid of the ones I don't use to speed up my ubuntu. I got to

 Graphical Login Manager
Allows users to login graphically

I figured it gets rid of the login window, I use automatic login anyway so I might as well get rid of loading it for no reason.

I unchecked and I get the message, "This may affect your system behavior in various ways, data loss may occur." Well that's too vague to scare me. It affects my system? Well I hope changing settings affects it, otherwise putting check boxes that don't do anything is just a sick joke. I click Ok.

It immediately is apparent to me that me and ubuntu have very different ideas of what 'allows users to login graphically" mean. 

Xserver shuts down and I spend a couple minutes figuring out how to turn it back on. Here's where I get a little puzzled. I can't start xserver without being root. So I sudo startx and it starts but now I'm running full ubuntu as root!
  I didn't think you were supposed to be able to do that. So if you turn this setting off it's really impossible to login with a GUI, correct? 

 I think the service description needs to be a lot more clear, it was way too easy for me to render my computer useless and 'unbootable'. (don't start talking about how command line is awesome you know what I mean) Maybe it needs to say something like

title: "Gnome Display Manager" *note what it actually is happens to be more clear
description: "If you turn this off you will have no graphics"

Just to make it clear to the people poking around in there. Or just get rid of it altogether, banishing such computer crippling debugging to command line. 

Just some thoughts....

---

### Post by maybeway36 on 2008-01-11
Login with your username and password, then run startx without sudo.
It does, however, need renaming. You don't need to be generic with everything. You wouldn't say "Click here to install Computer Operating System on your Storage Device."

---

### Post by coolen on 2008-01-16
Just wondering: why is the ability to stop gdm included in the GUI? What's the use case for this? If someone really wants to stop gdm, they can do so from a terminal (and obviously, they have little fear of the CLI).

---

