---
title: "Console Display Manager"
date: 2009-12-09
forum: The Cafe
---

### Post by ghost1227 on 2009-12-09
I'm not entirely sure this is the right place for this, but I suppose it's a good place to start...

Fed up with the overhead of gdm and kdm, and the instability of qingy and slim, I sat down recently and began working on a project dubbed CDM - the Console Display Manager. CDM is a (relatively) full-featured display manager written in pure bash. But how many features can you put in a bash display manager? Surprisingly, quite a few!

CDM Supports:
*Multiple X sessions (user logins are all handled through tty1)
*Any DE/WM
*Configurable console logins
*Users restricted to a single environment bypass the menu on login
*Root is automatically dropped to console
*Theming
*All settings are configurable on a per-user basis

Granted CDM is far from perfect, but it's come a long way already and is still being improved as quickly as I can find and repair bugs and add features. CDM is available via [github](http://github.com/ghost1227/cdm) and has a bugtracker [here](http://bugs.archuser.com/index.php?project=2&do=index&switch=1). If you're looking for a minimalistic display manager, please try it out and tell me what you think!

If anyone would like to package CDM for Debian/Ubuntu, please let me know.

---

### Post by VCoolio on 2009-12-18
I'd like to give it a shot. Just did it the lazy way: download, sudo ./install; edited /etc/default-display-manager to /usr/bin/cdm and reboot. Got a prompt on tty1 that didn't accept my username and password, so had to alt-sysrq-reisub and boot in special mode (what's it called again?) to undo.

So, a little documentation or howto wouldn't hurt. I guess I need to properly edit /etc/cdmrc? But where do I find a list of login scripts for my different wm's (where is the list gdm uses for example, so I can copy from it)?

---

### Post by lastpook on 2010-01-07
> **VCoolio said:**
> I'd like to give it a shot. Just did it the lazy way: download, sudo ./install; edited /etc/default-display-manager to /usr/bin/cdm and reboot. Got a prompt on tty1 that didn't accept my username and password, so had to alt-sysrq-reisub and boot in special mode (what's it called again?) to undo.

So, a little documentation or howto wouldn't hurt. I guess I need to properly edit /etc/cdmrc? But where do I find a list of login scripts for my different wm's (where is the list gdm uses for example, so I can copy from it)?

I did the same, too, and when entered login/pass just got another prompt for entering login/pass. I think this stuff have problems with ubuntu/gnome. 
My cdmrc file differs by following lines from default:

```
# List all WM binary names
wmbinlist=(awesome gnome-session)

# List all WM display names
wmdisplist=(Awesome Gnome)
```

and 

```
# Set configuration for specific users?
userconfig=(lastpook)

##########################
### USER CONFIGURATION ###
##########################

lastpook() {
	# Set CDM theme
	theme=lime

	# List user allowed WM binary names
	wmbinlist=(gnome-session awesome)

	# List user allowed WM display names
	wmdisplist=(Gnome Awesome)
```

---

### Post by VCoolio on 2010-01-07
> **lastpook said:**
> I did the same, too, and when entered login/pass just got another prompt for entering login/pass. I think this stuff have problems with ubuntu/gnome. 


There is some discussion on cdm [here]("http://bbs.archlinux.org/viewtopic.php?id=84408&p=6"); it seems there is going to be a .deb for it soon. So let's be patient. 

My 'howto' is not right btw; in the thread the link leads you to I've posted what else I did. That is at least better, although maybe still not right and it doesn't log you into X. But you get to cdm at least :P.

---

