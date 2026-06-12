---
title: "How do I find Ubuntu-specific UX / UI developers?"
date: 2017-08-29
forum: Ubuntu Application Development
---

### Post by s3w47m882 on 2017-08-29
[COLOR=#333333][FONT=Ubuntu]I would like to employ someone to develop a section in Settings for Ubuntu to manage all aspects of Apple's Magic Mouse v1 and v2.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I don't know what type of developer I'm looking for though or where to find them.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]So my questions are:[/FONT][/COLOR]

[LIST]
[*]What types of developers fall under the categorization of "Ubuntu" developers?
[*]What are the most common places to locate these types of developers?
[/LIST]

---

### Post by TheFu on 2017-08-30
Welcome to the forums.

I'd start here: [https://github.com/biggreenogre/mm2](https://github.com/biggreenogre/mm2)
and
[https://github.com/entrope/linux-magicmouse](https://github.com/entrope/linux-magicmouse)
and
[https://help.ubuntu.com/community/AppleMagicMouse](https://help.ubuntu.com/community/AppleMagicMouse)
 
You'll need to be very clear on what you want. 
"manage all aspects of Apple's Magic Mouse v1 and v2" is vague.  If you just want a GUI to handle things the driver can already do, that shouldn't be hard.  OTOH, for things that do not work, those may not be possible to fix for a normal GUI person.  A mouse kernel driver expert will be needed.  That's 2 people usually.  Driver people generally don't touch GUI code.

You'll also need to be very clear on the exact versions of Ubuntu/Debian you want to support with which GUI libraries.

BTW, you know that Canonical has decided to stop developing Unity, right? [https://arstechnica.com/information-technology/2017/04/ubuntu-unity-is-dead-desktop-will-switch-back-to-gnome-next-year/](https://arstechnica.com/information-technology/2017/04/ubuntu-unity-is-dead-desktop-will-switch-back-to-gnome-next-year/)  Basically, you should target either Gnome or KDE desktops and look to having the developer merge any work into one of those existing F/LOSS projects.

You'll need to be clear. The choice of which library is picked will determine which type of GUI dev you need.  There are many more of these people, BTW.

I'm not qualified. Back when I wrote code, it was $75/hr. I think $100+/hr is more common for specific experts now.  Also, there isn't any need to stick with only Ubuntu. Any Linux system can run KDE or Gnome, so any person familiar with those libraries and how to integrate into the _control panel_ would be a nice choice.  gnome has a feature tracker somewhere. I suspect KDE does too.  
Gnome: [https://help.gnome.org/users/gnome-help/stable/mouse-sensitivity.html.en](https://help.gnome.org/users/gnome-help/stable/mouse-sensitivity.html.en) has some names.  I looked for a KDE subproject and wasn't able to find it.  Kcontrol appears to be the higher project, but never found it.  These are outside the Ubuntu stuff, since they are used by 20+ distros, not just 1.

---

### Post by Bucky Ball on 2017-08-30
Welcome. All of the above, but with the caveat:

> **TheFu said:**
> Basically, you should target either Gnome or KDE desktops ...

... or xfce. Xubuntu and the xfce desktop are going strong and not about to disappear anytime soon. A Ubuntu official flavour. ;)

---

### Post by s3w47m882 on 2017-09-04
Thank you everyone.

I am aware Unity is no longer being developed and will plan on GNOME first, but also Unity just because there are a lot of people running 16.04 / 16.10 so I want to help them out.

I'll look into those developers and if I locate someone who gets the job done I'll be sure to repost a link to the application here!

---

