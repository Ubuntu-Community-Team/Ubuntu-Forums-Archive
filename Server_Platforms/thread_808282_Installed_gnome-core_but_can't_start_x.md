---
title: "Installed gnome-core but can't start x"
date: 2008-05-26
forum: Server Platforms
---

### Post by garethsimpsonuk on 2008-05-26
Hello every1

I've done apt-get install gnome-core and it seemed to install a lot of dependencies but now I can't do start x to start the gui. 
I guess I'm missing the gui login manager. How would I install this?
I think there's a way without the login manager (which I would prefer) by adding something / doing something with /home/username/.xinitrc so the start x command will work.
Any ideas?

thanks

---

### Post by jjgomera on 2008-05-26
its ridiculous, but, did you use **startx** or **start x** to run x?

---

### Post by garethsimpsonuk on 2008-05-26
i tried both i've now done apt-get install x-window-system-core and im regretting it, it's gonna take another 40 mins, i hope it's not bloated. it seems to be adding a lot of x-server stuff which I thought was neccessary. would I have synaptic with this meta package? should I do xterm synaptic

---

### Post by jjgomera on 2008-05-26
ahha, maybe you need too: xserver-xfree86 and x-window-system-core

---

### Post by garethsimpsonuk on 2008-05-26
ok cool ill wait till this is done (20 mins) & see if i can start x and then look into xerver-xfree86. I'm trying to keep it small. I've just found out about openbox on my quest of startx. do you know of it? it seems to be specifically for servers. is it actually a whole gui system? i'm gonna go and find out now. if it is i'm starting again lol

---

### Post by garethsimpsonuk on 2008-05-26
great i've just found this in the ubuntu docs on 'installation on low power systems.

"Remember: If you are using Dapper or earlier, replace "xorg" with "x-window-system-core""

Whats the difference? Shall I run xorg to add anything thats missing? or will add stuff that's unneccessary?

---

### Post by jjgomera on 2008-05-26
not specific, but for a server is better than gnome or kde because its lighter.

its simple but i think fairly complete

but really isn't a [desktop environment]("http://en.wikipedia.org/wiki/Desktop_environment"), it's only a [windows manager]("http://en.wikipedia.org/wiki/X_window_manager")

> "Remember: If you are using Dapper or earlier, replace "xorg" with "x-window-system-core""

Whats the difference? Shall I run xorg to add anything thats missing? or will add stuff that's unneccessary?
Really its the same, xorg its the name in old versions
Startx may be enough to start graphical session.

---

### Post by garethsimpsonuk on 2008-05-26
Gnome is installed startx works and when it boots up i gert this

the panel encountered a problem while loading
"OAFID:GNOME_FastUserSwitchApplet"

Do you want to delete the applet?

What do you reckon?

---

### Post by jjgomera on 2008-05-26
thats is because you have a folder .gnome2 with old configuration, isn't it?  No problem for delete, you could add later if you need that applet

---

### Post by garethsimpsonuk on 2008-05-26
it's a fresh install so i didn't think there would be old config files. nevermind its deleted.
it's very basic can I install openbox straight on top of this? is there an alternative specifically for a server? i.e. has samba/ apache tools?
Thanks for your help by the way

Gareth

edit: i think i was on about ebox. not to sure

---

### Post by jjgomera on 2008-05-26
yes, you can install openbox, its in repository too, but if you have installed gnome too i dont know hoy choose gui, i suppose ask it in user login screen.

Samba, apache, all this tools, really all linux can run with or without x

---

### Post by garethsimpsonuk on 2008-05-26
now when i try to open synaptic i get an error about not being able to create gksu, i don't know if I've gone down the right route here.
if I install ubuntu-desktop can I remove openofficwe etc?
I've tried before using synaptic and it lists dependencies that will also be removed and this includes ubuntu-desktop? will this actually uninstall the gui?

---

### Post by garethsimpsonuk on 2008-05-26
right im starting again because nothing works that way. im prepared to sack gnome now. I need server and gui to fit on 4gb comfortably. will kubuntu or xubuntu do this? I just want to startx when I need to and do the rest using webmin. kde would be nice, I can't seem to find the specs

anyone?

---

### Post by jjgomera on 2008-05-26
and if you write sudo synaptic?

really i don't know what packages are going to uninstall, you can annotate and install later, that packages are in cache so dont have to download one more time

---

### Post by garethsimpsonuk on 2008-05-26
no i meant the gui package manager, i installed it and it didn't work, it's to late now anyway I'm doing the install again (i'm definately an expert at the install part now). I need to decide what approach I will take for a gui.

heres what I'm looking for

- it must fit comfotably + os / swap etc on a 4gb
- it must 'work' i'm impatient, lazy and dumb. the above approach needs loads of extra configuration and I have enough issues with everything else!
- I need basic file management so I can visualise my file trees without having to visualise it + mounting etc.

My Hardy Server disks just popped out so what do you reckon?

---

### Post by garethsimpsonuk on 2008-05-26
I've decided to go with KDE it only takes 3.5 gb according to the Kubuntu specs. Will this be ok on a 4.3 gb harddrive icluding swap space. I will use kubuntu-desktop this time

---

### Post by jjgomera on 2008-05-26
> **garethsimpsonuk said:**
> no i meant the gui package manager, i installed it and it didn't work, it's to late now anyway I'm doing the install again (i'm definately an expert at the install part now). I need to decide what approach I will take for a gui.

heres what I'm looking for

- it must fit comfotably + os / swap etc on a 4gb
- it must 'work' i'm impatient, lazy and dumb. the above approach needs loads of extra configuration and I have enough issues with everything else!
- I need basic file management so I can visualise my file trees without having to visualise it + mounting etc.

My Hardy Server disks just popped out so what do you reckon?

so you need a desktop environment, kde or gnome are similar, in repositories you have too xubuntu-desktop, lighter.

---

### Post by garethsimpsonuk on 2008-05-26
Yea I'm installing kubuntu-desktop now. Thanks for everything m8 you've been very helpful

---

### Post by titus on 2008-09-08
I did a minimal cli install, then installed packages : xorg gdm gnome-core metacity gnome-themes

That worked for me. no need for startx with gdm.

---

