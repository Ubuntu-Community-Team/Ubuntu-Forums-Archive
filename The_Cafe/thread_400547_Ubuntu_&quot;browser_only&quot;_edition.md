---
title: "Ubuntu &quot;browser only&quot; edition?"
date: 2007-04-03
forum: The Cafe
---

### Post by aNt1X on 2007-04-03
Hi guys,
i have do build up some internet access device.
Basically, they are full PCs, and they have to provide a web browser, and nothing else.
I like ubuntu very much, it's a useful and simple distro, so i'd like to use ubuntu to build these machines.
How can i realize this?

1st idea:
Ubuntu Server + Links web browser ?

2nd idea:
There is a way to install Ubuntu Server, then X server+something else and Firefox only, locking all the user interaction with the operating system, so that they can only browse and nothing else? (If i want to manage the machine, i'll login via SSH).

Thank you i.a. for the suggestions,

aNt1X

---

### Post by DoctorMO on 2007-04-03
You can do this, the best way is to prepare an ubuntu image to install it on many machines.

Have x-windows installed, perhaps XFC or some other light weight gui manager and just install firefox or galleon or what have you on top. should be a problem to disable all the various options.

The best thing is to get a pro in to do it for you and do all the research; the pay will pay off in the end with stability and security esp' if the browser user doesn't have access to run normal programs etc.

The other option is to become a pro if your on a tight budget. you'll be reading lots of how-to guides :-)

---

### Post by justin whitaker on 2007-04-03
You can set up Firefox as a Kiosk....it takes a bit of doing, but basically just editing a few config files. 

You can also install OpenKiosk.

[http://openkiosk.sourceforge.net/](http://openkiosk.sourceforge.net/)

---

### Post by aNt1X on 2007-04-03
Thank you for you answer!

> **DoctorMO said:**
> The other option is to become a pro if your on a tight budget. you'll be reading lots of how-to guides :-)

Of course, I'd like to build something on my own. Perhaps i'll ask someone expert's help if i'll never reach something secure and stable :)
Do you have some how-to or other links to suggest?

Thank you i.a.,
aNt1X

---

### Post by Bloodfen Razormaw on 2007-04-03
I assume you want some sort of kiosk you want secured and locked down for just web use?  The second option is viable, but trusting Firefox to be locked down is probably not a great idea.  If you want a secure kiosk you want the whole desktop locked down, not just the browser.  Your best option is to create a Konqueror kiosk, using the Kiosk system in KDE, which is very mature and developed.  An alternative is the newer but still usable Pessulus + Epiphany.

In fact, you should probably stay away from Ubuntu entirely and go with Debian Stable.  Any bugs that are left unresolved are going to be a risk to the lockdown.

---

### Post by aNt1X on 2007-04-03
> **justin whitaker said:**
> You can set up Firefox as a Kiosk....it takes a bit of doing, but basically just editing a few config files. 

You can also install OpenKiosk.

[http://openkiosk.sourceforge.net/](http://openkiosk.sourceforge.net/)


Ok man, thank you very much, i'll take a look at this!

---

### Post by aNt1X on 2007-04-03
> **Bloodfen Razormaw said:**
> If you want a secure kiosk you want the whole desktop locked down, not just the browser.  Your best option is to create a Konqueror kiosk, using the Kiosk system in KDE, which is very mature and developed.  An alternative is the newer but still usable Pessulus + Epiphany.

In fact, you should probably stay away from Ubuntu entirely and go with Debian Stable.  Any bugs that are left unresolved are going to be a risk to the lockdown.

Yes, this is the idea. the whole desktop looked down. I'd prefer using ubuntu, but perhaps that  Debian Stable will be the right choice to prefer stability and security, but i'm not so sure. Do u think that there are so many differences between the two, in terms of security?

---

### Post by Bloodfen Razormaw on 2007-04-03
There will be a big difference.  Debian Stable's interesting feature is that not only is it stable in terms of Debian's packaging work but in terms of the software itself.  Debian Stable has a maximum limit on the number of bugs that the entire package repository (in the upcoming Etch release: [http://bugs.debian.org/release-critical/](http://bugs.debian.org/release-critical/)  That's the total number of known bugs in over 20,000 packages).  Since Debian Etch will be Stable soon, you will be able to get some recent software that has been thoroughly vetted for bugs, so you can be sure there is a minimal risk of the lockdown being violated by something like an application crashing.

If you do go with Ubuntu, go with a long-term support version, so that, like Debian Stable, you will get security updates without introducing new features that might introduce new bugs.

---

### Post by user1397 on 2007-04-03
what about just installing regular ubuntu, and removing both panels of the gnome desktop, and leave only the firefox launcher icon on the desktop itself?

even if the user were to log out and go to recovery console or something like that, he wouldnt be able to because he wouldnt know that user's password, and he wouldnt be able to make a new one.

---

### Post by Bloodfen Razormaw on 2007-04-03
That allows malicious user to ruin the kiosk for everyone else and opens up all sorts of incomplete mediation attacks.  Even just an empty desktop with a launcher is enough for most people to avoid the kiosk.  There can be a ton of ways to functionality you don't want the users to have; just trying to hide it doesn't mean it can't be used.  If you have lockdown functionality you can disable the function entirely and be sure that there is no way to use it, even if you didn't forsee how they got to it.

---

### Post by ssam on 2007-04-03
install the server, install xorg, install firefox

write an .xinitrc that just has
```
exec firefox
```

run startx

that way X should start with just firefox running (look at man firefox if you need to set its resolution)

there is a way to get a process to respawn if it die (used for servers) which i cant remember, use that to run startx.

---

### Post by Albi on 2007-04-03
> **ssam said:**
> install the server, install xorg, install firefox

write an .xinitrc that just has
```
exec firefox
```

run startx

that way X should start with just firefox running (look at man firefox if you need to set its resolution)

there is a way to get a process to respawn if it die (used for servers) which i cant remember, use that to run startx.

How will he lock it, etc?

I say get an expert to look into it, I'm pretty sure Linux is very capable of doing this, better than windows, since you don't have to worry about maintenance.

Edit:
I got an idea...
How about it boots into a blank screen with no priveleges by default, and it's hooked up to a network that he can send commands to.  He can run a shell script that asks him how many minutes to give, basically something like

exec firefox
sleep $TIME;
exit

And then use xinitrc to run the script?

Edit2: Ooh, look what I found:

[http://kiosk.mozdev.org/](http://kiosk.mozdev.org/)

Or better yet, a full guide:
[http://www.dnalounge.com/backstage/src/kiosk/](http://www.dnalounge.com/backstage/src/kiosk/)

Edit3: Google "linux kiosk" lots of resources

---

### Post by Nonno Bassotto on 2007-04-03
I'd like to do something similar, that is running a couple of machines with browser only. I'm not interested in security, since my family will be the only users, but I'm very interested in achieving the lowest possible specs for running it.

Basically I just need firefox and audio decoding, and I want the machine to cost the least possible and occupy the least possible space. How do I get a minimal browser only version of Linux?

EDIT: Well not exactly browser only. I will also need the ability to play streamed music, and of course to connect to a wireless LAN. The browser should be a modern one, with full javascript+DOM and CSS2 support.

---

### Post by koenn on 2007-04-04
I've been looking into this myself a while ago. There's quite a few things to pay attention to. Like - when you're running firefox, how do you stop the user from  downloading and installing extensions ? :-) or use it to brows the filesystem (possibly looking for flaws in the configuration that can be exploited ...)

Here are some (not 100% succesfull) attempts. 
[http://users.telenet.be/mydotcom/howto/linuxkiosk/intro.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/intro.htm)
[http://users.telenet.be/mydotcom/howto/linuxkiosk/webterm.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/webterm.htm)
[http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm)

I'm thinking of picking this up later this year, this time with Ubuntu+Fluxbox. Gnome is overkill and the more features, the harder the lockdown effort. 
I also had a go at packing the config in a .deb package so that it can be installed on a base (server) Ubuntu install (install a server, add X, add a browser, insert customized config files, done) for a rollout on multiple machines (I don't like cloning (images) because they're too hardware-dependent)

---

### Post by Bloodfen Razormaw on 2007-04-04
> I'm thinking of picking this up later this year, this time with Ubuntu+Fluxbox. Gnome is overkill and the more features, the harder the lockdown effort. 
If you are trying to use GNOME or Fluxbox that would explain your problem.  The only mature lockdown mechanism in the Linux desktop world is KDE's Kiosk system.  In addition to Kiosk, KConfig allows lockdown of any KConfig key at multiple policy levels to prevent any arbitrary setting from being changed.

---

### Post by koenn on 2007-04-04
> **Bloodfen Razormaw said:**
> If you are trying to use GNOME or Fluxbox that would explain your problem.  The only mature lockdown mechanism in the Linux desktop world is KDE's Kiosk system.  In addition to Kiosk, KConfig allows lockdown of any KConfig key at multiple policy levels to prevent any arbitrary setting from being changed.
I've had a look at KDE Kiosk as well  : [http://users.telenet.be/mydotcom/howto/linuxkiosk/kdedesk.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/kdedesk.htm)

It's, in concept, not very different frome gconf and gconf-lockdown (eg with Sabayon) although the implementation looks less complex. But (ubuntu) gnome has a cleaner, leaner appereance and it's my personal preference so I had a go at it anyway.

The point is that for a browser-only system, both KDE and Gnome are overkill. You setup a full-blown desktop (with all the menus, icons, launchers, pannels, widgets, ...  etc that come with it), and then you start locking down each and every feauture that the desktop environment offers,  untill all the user can do is use a web browser. Bad strategy. 

Better strategy : don't use a desktop environment,  just run a window manager, cause all you need is a window to display Firefox. You could even try to do without a window manager - windows allow the user to resize them, move them, close them (and the application in it) so even that might be too much for a browser-only kiosk. 
The point is : only install what you need, then take away the user's ability to modify what you've set up. Therefore, the less you install, the easier the lockdown.

---

### Post by Bloodfen Razormaw on 2007-04-04
> Better strategy : don't use a desktop environment, just run a window manager, cause all you need is a window to display Firefox.
That is a much worse strategy.  It's no different than the guy who just wanted to run Firefox without gnome-panel.  It opens you up to a ton of incomplete mediation or denial of service attacks.  Other window managers are going to have its own features, yet without lockdown capabilities.  With KDE or GNOME, you can still have just a window manager, but with the certainty that there is no way to get around that.

---

### Post by kiddo on 2007-04-04
Use Epiphany, the official GNOME browser. This thing seems to be made to be locked down! (this is not a joke or an insult, I love epiphany and use it everyday as a "power user")

in gconf I see a lot of keys that govern this, for example not allowing to change certain settings, not allowing to exit the fullscreen mode (forcing the fullscreen mode actually).

To edit these settings easily, you could, as suggested previously, use "Pessulus".

---

### Post by koenn on 2007-04-05
> **Bloodfen Razormaw said:**
>  [ koenn: "don't use a desktop environment, just run a window manager, cause all you need is a window to display Firefox"] .
That is a much worse strategy (...).  It opens you up to a ton of incomplete mediation or denial of service attacks.  .
That sounds interesting. I'd be interested to know what you mean by "incomplete mediation" and how a desktop environment prevents denial of service attacks. Can you explain that ? I fail to see the logic behind it.

---

### Post by koenn on 2007-04-05
> **kiddo said:**
> Use Epiphany, the official GNOME browser. This thing seems to be made to be locked down! (this is not a joke or an insult, I love epiphany and use it everyday as a "power user")

in gconf I see a lot of keys that govern this, for example not allowing to change certain settings, not allowing to exit the fullscreen mode (forcing the fullscreen mode actually).

To edit these settings easily, you could, as suggested previously, use "Pessulus".
I haven't tried it, but as it is gnome's browser of choice, I imagine it integrates better into the desktop and it will be easier to configure it (ie lock it down) using gconf.

---

### Post by Bloodfen Razormaw on 2007-04-05
> That sounds interesting. I'd be interested to know what you mean by "incomplete mediation" and how a desktop environment prevents denial of service attacks. Can you explain that ? I fail to see the logic behind it.
Incomplete mediation means you didn't perform a security check at the point where you were trying to secure something.  If you use a security policy to tell a function to be disabled, then the function will check that every time there is an attempt to use it.  As opposed to just trying to disable the *path to it*, which allows the attacker to simply work to find another route.  If you rely on only the former, you are saying that you are sure you covered every possibility, and if you didn't, the attacker is free to do what he wants.  If you find out you missed something, or the attacker knows of a bug to exploit, you want the attacker to still find he can't do anything.

Denial of service attacks are attacks which prevent the use of the service.  If the attacker finds a new path to a function you did not intend him to have he may be able to bring down the kiosk.  Such as when someone said you could just use a desktop with only a Firefox launcher and if they log out they just can't log back in (which still makes the kiosk unusable to anyone else).  In fact, in kiosks a DoS can be as simple as minimizing the browser window, which is more than enough to confuse most people into not using it.  As an example, I used to work in a store and we did our work in a web app on a browser kiosk in the office.  It was supposedly only capable of running IE, yet they forgot that you can run something from IE by entering its local URI in the address bar.  There are a billion ways to do that and many other dangerous functions, and it is a bad idea to assume you will cover all of them.

---

### Post by koenn on 2007-04-05
OK, I see what you mean, but I still don't see how using a desktop environment (s.a. Gnome, KDE) whould contribute to that while a window manager wouldn't, or how a window manager would be "the worst possible strategy" in this context. 

The way I see it :
either you install a base system, add x-system, add a window manager, add a webbrowser, then
- secure the base system (eg. limit/refuse shell access, set filesystem security, etc)
- secure the window manager (eg. fixed size window, fixed window position, no close/minimize buttons, no menu's; auto-(re-)start application of choice (i.e. the webbrowser), and so on )
- secure the browser (eg block file:// uri's etc)

whit a desktop environment, you would
- do all of the above
- add gnome or kde
- try to secure the desktop, including but not limited to
[INDENT]* remove/disable alll default applications that came with the DE, such as mail client and file browser, terminals emulators, ...
* lock all user customization
* prevent user from creating desktop shortcuts / launchers to arbitrary commands or apps
* prevent user to modify existing launchers / panel items / menu items to point to arbitrary commands or apps
* prevent use of apps that can be used to read files / browse file system (eg the default gnome text editor, gedit, ...)
* and so on, and on, and on ...
[/INDENT]
all the while, risking you forget an exploitable feature. As you say "There are a billion ways ... , and it is a bad idea to assume you will cover all of them."

So then how 's the "just a window manager" scenario worse than a desktop environment for this browser only system ?

---

### Post by Bloodfen Razormaw on 2007-04-05
> OK, I see what you mean, but I still don't see how using a desktop environment (s.a. Gnome, KDE) whould contribute to that while a window manager wouldn't
The desktop environment can still be run as only a window manager, but that window manager can ensure safety through a lockdown policy.  You can also apply security policies to the browser itself in Konqueror or Epiphany.  Most window managers don't come with security systems that allow for policy-based lockdown.  KWin/Konqueror or Metacity/Epiphany have no more features than Fluxbox/Firefox, but that later doesn't have a security system that lets you be certain you have locked the system down.

---

### Post by koenn on 2007-04-05
> **Bloodfen Razormaw said:**
> The desktop environment can still be run as only a window manager,  ... 
We might be having some misunderstanding here. I understand a window manager to be an application that controls the placement and appearance of windows, while a Desktop Environment is an integrated graphical user interface, providing icons, windows, toolbars / taskbars / menubars, wallpapers, and usually a number of utilities : the g-apps (gedit,gcalctool,..) in Gnome, the k-apps (konsole, ...) in KDE . Granted, you could limit the install of gnome to metacity (window manager) and a login manager or so.

> Most window managers don't come with security systems that allow for policy-based lockdown. KWin/Konqueror or Metacity/Epiphany have no more features than Fluxbox/Firefox, but that later doesn't have a security system that lets you be certain you have locked the system down.
I haven't found much policy-based lockdown in Gnome or KDE either. KDE Kiosktool, last time i checked (granted, over a year ago) and the Gnome gconf frontends (Pessulus, Sabayon),  serve  to lock a given config i.e. disallow the user to change they config after you've set it. That still leaves it up to you to decide _how_ to secure the system (and the possibility of overlooking the alternative routes an inventive user can come up with). 
Closest thing to policies I found was (in Pessulus, I think) : 
[IMG]http://users.pandora.be/mydotcom/howto/linuxkiosk/graph/ubu_userprop.png[/IMG]
and although it says "(don't) allow user to execute system administration tasks" (without me having to wonder how to implement that ) it still doesn't tell me that user can't fire up a terminal and start some other app (while i want them to just use the browser and nothing else), or shut down the browser and/or write some mean busy loop statement in the terminal (re the DOS attacks you meantioned).

For a browser-only system, I'd still go for a (well configured, then locked down) window manager with a browser - nothing else.

---

### Post by Bloodfen Razormaw on 2007-04-05
> We might be having some misunderstanding here. I understand a window manager to be an application that controls the placement and appearance of windows, while a Desktop Environment is an integrated graphical user interface, providing icons, windows, toolbars / taskbars / menubars, wallpapers, and usually a number of utilities : the g-apps (gedit,gcalctool,..) in Gnome, the k-apps (konsole, ...) in KDE . Granted, you could limit the install of gnome to metacity (window manager) and a login manager or so.
The desktop environment is nothing special, just a collection of applications.  You don't have to run Kicker with KDE, or Nautilus with GNOME, etc.

> I haven't found much policy-based lockdown in Gnome or KDE either. KDE Kiosktool, last time i checked (granted, over a year ago) and the Gnome gconf frontends (Pessulus, Sabayon), serve to lock a given config i.e. disallow the user to change they config after you've set it. That still leaves it up to you to decide how to secure the system (and the possibility of overlooking the alternative routes an inventive user can come up with). 
The difference is when you tell it to lockdown a feature, it locks down the feature itself.  Without these policy-based lockdown systems, you just try to make the feature inaccessible.  In both cases you will hide the feature.  But with the feature locked down, it doesn't matter if they get around your attempt to hide it.  It still won't work.  Without the lockdown functionality, if someone finds a way to the feature, you're screwed.

---

### Post by koenn on 2007-04-05
neither KDE nor Pessulus show me how to set a policy along the lines of "do not allow the user access to any form of command prompt". You'd still have to implement that yourself, and make sure the user can't change or circumvent the implementation., like by making gdm crash by hitting ctrl alt backspace repeatedly until it fallsback to "failsafe terminal'. neither KDE nor Pessulus show me how to set a policy along the lines of 'allow user to run  approved applications only" - approved applications in this case being firefox and nothing else. 

I agree that a policy-based approach is more secure and more effective for the reasons you explained, but, to my knowledge, the available tools today lack the necessary functionality.

On the other hand : set up your window manager, configure it in a resonable way (full screen, no buttons, no menus) and   make the config files accessible only to root (or a group that the kioskuser is not a member of) and there is very little that kioskuser is going to do about it. It's not a matter of hiding stuff, it's a matter of : if there is no action such as "close window" assigned to the close button, nothing's gonna happen when you click it. Period. There may be other ways to close a window, like keyboard shortcust, but you can disable those as well. There is no infinite number of ways to close a window / an application.  And you could also make FF restart everytime its closed - creating it's own window as needed. It's the best you've got untill someone implements a "don't allow users to change window appearance" policy and a 'allow user to run  approved applications only". 

So, I'm still in favor of the window manager approach.

---

### Post by Bloodfen Razormaw on 2007-04-05
> neither KDE nor Pessulus show me how to set a policy along the lines of "do not allow the user access to any form of command prompt". You'd still have to implement that yourself, and make sure the user can't change or circumvent the implementation., like by making gdm crash by hitting ctrl alt backspace repeatedly until it fallsback to "failsafe terminal'. neither KDE nor Pessulus show me how to set a policy along the lines of 'allow user to run approved applications only" - approved applications in this case being firefox and nothing else. 
This policy already exists in the OS, both in mandatory and discretionary control.  With Kiosk you can do things like disable window manager features that would let you minimize the browser that Fluxbox won't let you do.  You can choose how the window will behave.  You can control what features the browser will let you use.  Firefox doesn't have a secure way to do this.  What will you do when you think you disabled the shortcuts that would let you minimize the window, then one day you update and Fluxbox has added mouse gestures with a default gesture for minimizing the window?  What will you do when someone finds a bug that lets them trigger the feature?  What happens when a javascript exploit in Firefox lets someone control the window from the browser?  You are just trusting that none of those things will ever happen.  In fact they happen all the time.  Not having a close button on the window is very, *very* far from not being able to close the window.

> There is no infinite number of ways to close a window / an application
Actually, there potentially is an infinite number of ways to close a window.  Anything that can execute code can make a window close.  Even if there was only a limited number of ways, its foolish to just trust you got them all and say to yourself "If someone is good enough to outsmart me, that guy deserves the right to destroy the system."

The problem is you are still talking about just using a window manager when you can do that anyway, but WITH lockdown features.  You can have a choice of which window manager.  Fluxbox, with no lockdown security features.  Or KWin/Metacity, which come with those features. In both cases you have just a window manager and a browser.  Why would you pick the one that doesn't offer security?

---

### Post by koenn on 2007-04-06
Good points. 
Now, practically - I want a PC that only allows the user to run a webbrowser, and I follow your suggestion to use a desktop environment so I can implement a policy of "user can only use firefox" and, to avoid DOS etc, "user can not change anything about windows". The window manager sollution is insufficient, as you point out : a new feature in the window manager can ruin me (if I was careless enough the upgrade without testing), and the javascript trick is a serious threat, so we go for the DE and policy approach. 
How exactly do I make gnome (or kde, but preferably gnome) enforce those policies - say "user can only use firefox", "user can not stop a running application" and/or "firefox should always be running" ? 
And, if possible, i'd like that policy reproduced on 15 pc's so I have a strong preference towards reproducable (semi-) automatic sollutions, such as installing a customized .deb or a script that can run unattended.

---

### Post by UbuWu on 2007-04-07
> **aNt1X said:**
> Hi guys,
i have do build up some internet access device.
Basically, they are full PCs, and they have to provide a web browser, and nothing else.
I like ubuntu very much, it's a useful and simple distro, so i'd like to use ubuntu to build these machines.
How can i realize this?


I think this is exactly what you want: [Kiosk Appliance]("https://launchpad.net/kiosk/")

It is not based on Ubuntu but I think it gives you exactly the result you want: rPath Linux and FVWM running a locked down version of Firefox. Firefox is also pre-configured to automatically reset after each used so that personal information is never stored permanently. No login or password is required, the livecd will boot directly into FVWM and automatically start Firefox in full-screen mode. It also ensures that: 1) Firefox is the only application running; 2) That's the only application that can be run. There is also an installable CD/DVD.

:KS

---

