---
title: "Newb: Running Fluxbox as root?"
date: 2007-12-15
forum: Server Platforms
---

### Post by Smartin on 2007-12-15
Hi,

I'm still experimenting with various flavours of Ubuntu, I'm an OSX refugee.

If I'm using the Nautilus file manager in gnome and I want to run it as root in order to navigate downwards in the filesystem from my Home folder, I would go to the terminal and do 
```

gksudo nautilus

```

This would open another nautilus window with root permissions.

How do I do this in Fluxbox?

gksudo fluxbox doesn't seem to work.

Thanks

Simon

---

### Post by koenn on 2007-12-15
interesting question. I'm trying to think of what would be the benefit of that, and I can't think of anything. 
What are you trying to do ?

---

### Post by Smartin on 2007-12-15
> **koenn said:**
> interesting question. I'm trying to think of what would be the benefit of that, and I can't think of anything. 
What are you trying to do ?

koenn,

Thanks for the lightning reply...

I'm still pretty hopeless in the terminal so running the filemanager as root helps me navigate the file system way quicker and I can drag and drop stuff into the www directory easily.

Silly I know... I am trying to learn the ways of the CLI as well though :-)

Simon

---

### Post by finferflu on 2007-12-15
```
sudo nautilus
```

should do the trick...

---

### Post by Smartin on 2007-12-15
> **finferflu said:**
> ```
sudo nautilus
```

should do the trick...

finferflu

```

command not found

```

I thought Nautilus was strictly a gnome file manager? No?

Simon

---

### Post by finferflu on 2007-12-15
Ah, I though you had Gnome installed, but thinking about it... gksudo didn't work.. nevermind :P

Well, I suggest you to use Thunar, it's a lightweight alternative to Nautilus, and it doesn't depend on Gnome. 

```
sudo apt-get install thunar
```

Then you can use plain sudo to run it as root:

```
sudo thunar
```

---

### Post by Smartin on 2007-12-15
> **finferflu said:**
> Ah, I though you had Gnome installed, but thinking about it... gksudo didn't work.. nevermind :P

Well, I suggest you to use Thunar, it's a lightweight alternative to Nautilus, and it doesn't depend on Gnome. 

```
sudo apt-get install thunar
```

Then you can use plain sudo to run it as root:

```
sudo thunar
```

finferflu,

Does Thunar replace fluxbox?

Simon

---

### Post by koenn on 2007-12-15
> **Smartin said:**
>  running the filemanager as root helps me navigate the file system way quicker and I can drag and drop stuff into the www directory easily.
Oops, I understood you were trying to "start fluxbox as root" the same way you'd do with eg nautilus. So much for lightning replies. 

yes, sudo nautilus from a terminal might work. 
an other way is probably to to set ownership on /var/www so that you can write to it directly. I don't run a webserver so I don't know how this is handled usually.

---

### Post by koenn on 2007-12-15
> **Smartin said:**
> finferflu,

Does Thunar replace fluxbox?

Simon
thunar replaces nautilus

---

### Post by finferflu on 2007-12-15
Thunar is only a file manager and it's used to manage the files on your system, while Fluxbox is a windows manager, which manages your windows (resize, maximize, minimize, move, and so on).

---

### Post by Smartin on 2007-12-15
> **koenn said:**
> Oops, I understood you were trying to "start fluxbox as root" the same way you'd do with eg nautilus. So much for lightning replies. 

yes, sudo nautilus from a terminal might work. 
an other way is probably to to set ownership on /var/www so that you can write to it directly. I don't run a webserver so I don't know how this is handled usually.

koenn,

My fault... I meant I wanted to open a new window in fluxbox with root permissions.

I'm beginning to think I have misunderstood the Nautilus/Fluxbox relationship...

Isn't Nautilus the Gnome desktop filemanager?

Is fluxbox a replacement for the Gnome desktop? What is the fluxbox filemanager then?

Simon

---

### Post by finferflu on 2007-12-15
That's where the distinction between Windows Manager and Desktop Environment comes about. 

Gnome is a Desktop Environment, which not only manages your windows, but also provides some other tools, such as a file manager, and a whole lot of tools to manage the system. 

Fluxbox is a Windows Manager, which only manages your windows (it also has a panel and a menu, but that's all you will find). 

Gnome has its own Window Manager, called Metacity, but you can change it if you wish. 

In conclusion, a Window Manager hasn't got its own file manager most of the times, so you have to pick it up yourself. I suggest you Thunar since it's the closest to Nautilus as for look and feel.

---

### Post by Smartin on 2007-12-15
> **finferflu said:**
> That's where the distinction between Windows Manager and Desktop Environment comes about. 

Gnome is a Desktop Environment, which not only manages your windows, but also provides some other tools, such as a file manager, and a whole lot of tools to manage the system. 

Fluxbox is a Windows Manager, which only manages your windows (it also has a panel and a menu, but that's all you will find). 

Gnome has its own Window Manager, called Metacity, but you can change it if you wish. 

In conclusion, a Window Manager hasn't got its own file manager most of the times, so you have to pick it up yourself. I suggest you Thunar since it's the closest to Nautilus as for look and feel.

finferflu,

Ok mate. Thanks for all that. I'll give it a shot. :-)

Simon

---

### Post by finferflu on 2007-12-15
No problem, have fun! :D

---

### Post by Smartin on 2007-12-16
> **finferflu said:**
> Thunar is only a file manager and it's used to manage the files on your system, while Fluxbox is a windows manager, which manages your windows (resize, maximize, minimize, move, and so on).

finferflu,

Thunar is great. I think I'm getting the hang of it...

Thanks!

Simon

---

### Post by RedSquirrel on 2007-12-16
I would advise you to use gksudo when you want to run graphical applications with root privileges.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by koenn on 2007-12-16
> **RedSquirrel said:**
> I would advise you to use gksudo when you want to run graphical applications with root privileges.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

obviously, you go around handing out sollutions without knowing or understanding the problem.

---

### Post by RedSquirrel on 2007-12-16
> **koenn said:**
> obviously, you go around handing out sollutions without knowing or understanding the problem.

Actually, I understand the problem very well, and the recommendation of thunar is reasonable. 

Several times in this thread, it was recommended that the user run graphical programs with sudo, when **gksudo** is preferred for that sort of thing. Perhaps if I had quoted the posts with the use of sudo, it might have made my point a little clearer. ;)

---

### Post by koenn on 2007-12-17
Hmm ... the OP's problem is that he tried gksudo and it didn't work
(by lack of gnome in a fluxbox desktop ...)

---

### Post by jviscosi on 2007-12-17
As long as Gnome is installed on the machine, nautilus should work in Fluxbox, as far as I know.  Is an error occurring when trying to run it?  If so, what's the error?

By the way, nautilus will hijack your desktop if you run it straight up. You might want to use the "--no-desktop" argument with it (**nautilus --no-desktop**).

If Gnome isn't installed, then never mind all that stuff I just said.

FWIW, I also prefer thunar as the file manager when running Fluxbox.

---

### Post by RedSquirrel on 2007-12-17
> **koenn said:**
> Hmm ... the OP's problem is that he tried gksudo and it didn't work
(by lack of gnome in a fluxbox desktop ...)

My understanding is that the OP was uncertain about how to run a file manager with root privileges in Fluxbox.

That seems to be more or less resolved now that the OP is using thunar, but I wanted to suggest using gksudo instead of sudo when running graphical programs:

```
gksudo thunar
```gksu is the package that provides gksudo. If that wasn't already installed, for instance, as a dependency of some other package, then one can install it:

```
sudo apt-get install gksu
```Once installed, the user can run 'gksudo <graphical-program-of-choice>', for example,

```
gksudo leafpad /etc/X11/xorg.conf
```Running graphical programs with sudo apparently has some issues associated with it. Hence, users are encouraged to use gksudo. See the link I provided above.

---

