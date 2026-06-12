---
title: "Virtualbox won't start"
date: 2009-02-15
forum: Virtualisation
---

### Post by sprogmeister on 2009-02-15
Running Intrepid and have installed virtualbox in order to put XP on here. It shows up in the Applications Accessories and System tools menus but fails to start. Any ideas?

---

### Post by bgates on 2009-02-15
How about if you open a terminal and type VirtualBox ?  If that will work, something is just off about the menu item, which you can edit the menu and add a new one.

---

### Post by namegame on 2009-02-15
Actually, I'm pretty sure your problem is that you haven't added yourself to the vboxusers group.

```
sudo adduser $USER vboxusers
```

Then logout, log back in, and try it again. :)

---

### Post by sprogmeister on 2009-02-15
From terminal I get:

*Could not find VirtualBox installation. Please reinstall.*

and I have re-installed and then added:

*sudo adduser $USER vboxusers*

Which added me, but then no change. Thanks for the help thus far, anymore ideas?

---

### Post by cerealtx on 2009-02-15
> **sprogmeister said:**
> From terminal I get:

*Could not find VirtualBox installation. Please reinstall.*

and I have re-installed and then added:

*sudo adduser $USER vboxusers*

Which added me, but then no change. Thanks for the help thus far, anymore ideas?

how are you installing it? source? synaptic? and what ver 2.1?

---

### Post by diablo75 on 2009-02-15
I've written a pretty good guide for installing Virtualbox (not the Open-Source edition).  See my signature, and scroll down to item 10.

---

### Post by sprogmeister on 2009-02-16
Thanks Diablo75 I've got it installed. However, I have loaded the CD I want to boot from and it is not being seen. Can I get it to boot and load the OS as I would normally? Or can I use the OS that exist on another partition? thanks for the help!

---

### Post by sprogmeister on 2009-02-16
Got that working. Has anyone got any tips or advice for use of Virtualbox?

---

### Post by sprogmeister on 2009-02-16
I have the OS installed but VB steals sound. Has anyone got any ideas please?

---

### Post by Cresho on 2009-02-16
ya, you need to tell it to use pulseaudio. on the operating system of choice.

in your system sound in ubuntu, use automatic.

---

### Post by howefield on 2009-02-16
> **sprogmeister said:**
> Got that working. Has anyone got any tips or advice for use of Virtualbox?

Learn how to use the clonevdi command to back up your installs.
```

VBoxManage clonevdi source destination
```

---

### Post by sprogmeister on 2009-02-16
Thanks Cresho I will give it a go

---

### Post by bodhi.zazen on 2009-02-16
> **sprogmeister said:**
> Running Intrepid and have installed virtualbox in order to put XP on here. It shows up in the Applications Accessories and System tools menus but fails to start. Any ideas?

I see you are getting assistance.

May I suggest you try to be more descriptive with your problems.

"Virtualbox won't start" does not tell us much.

You can help us to help you if you :

1. Tell us what version of Ubuntu you are using.

2. Version of virtualBox.

3. Run virtualbox from the command line and pst any error messages.

---

### Post by sprogmeister on 2009-02-17
I am using Intrepid
It's the latest version of virtual box
The last point, I apoologise, I am slightly lost on. It's more a case of trying to configure virtual box, for instance the screen appears like a movie screen ( long and thin), how might I rectify this? I am not trying to be vague and your points are gladly received.

---

