---
title: "How would I disable Compiz completely?"
date: 2010-02-22
forum: The Cafe
---

### Post by Woolio1 on 2010-02-22
Hello! It's me again, Sir Henry.... Yes. Anyway, I want to disable Compiz completely. I've found out how to use Metacity as a compositing manager, so Compiz is no longer needed. It's bloaty, slow, and it's even crashed my computer twice. So I want to switch over to Metacity. 

However, it's required by The gnome session manager, and Opengl window and compositing manager. 

Is it safe to remove those as well? Is it even possible? Am I wasting my time?

Please help me. 

Henry Ericson

---

### Post by dragos240 on 2010-02-22
Erm. It's not needed at all. If you don't like it, uninstall it.

---

### Post by Woolio1 on 2010-02-22
> **dragos240 said:**
> Erm. It's not needed at all. If you don't like it, uninstall it.

Yes, but are the Gnome Session Manager, and the OpenGL Compositing... Whatever... Are those needed?

---

### Post by dragos240 on 2010-02-22
> **Woolio1 said:**
> Yes, but are the Gnome Session Manager, and the OpenGL Compositing... Whatever... Are those needed?

Gnome session manager? Sorry never heard of it, you mean in GDM when you startup? I don't think so. Nothing actually 'depends' on it. You can uninstall it without issue. I like compiz, some people don't. If you want, sudo apt-get remove compiz.

---

### Post by xpod on 2010-02-22
You could just disable it...System>preferences>appearance>visual effects>>>>>none.

---

### Post by wojox on 2010-02-22
Just go into Appearance > Visual Effects and set to none. Unless you want to uninstall it from the entire system?

---

### Post by Woolio1 on 2010-02-22
> **dragos240 said:**
> Gnome session manager? Sorry never heard of it, you mean in GDM when you startup? I don't think so. Nothing actually 'depends' on it. You can uninstall it without issue. I like compiz, some people don't. If you want, sudo apt-get remove compiz.

Go into the Ubuntu Software Center, pull up Compiz in your installed programs, and try to uninstall it. You'll get two packages that depend on it, and you have to uninstall those too. 

And I'm worried I'll botch my install if I remove Compiz.

---

### Post by dragos240 on 2010-02-22
> **Woolio1 said:**
> Go into the Ubuntu Software Center, pull up Compiz in your installed programs, and try to uninstall it. You'll get two packages that depend on it, and you have to uninstall those too. 

And I'm worried I'll botch my install if I remove Compiz.

Does it ask for ubuntu-desktop? Those packages are probably meta-packages, and if not, who cares, they're probably useless anyway.

---

### Post by Post Monkeh on 2010-02-22
> **Woolio1 said:**
> Go into the Ubuntu Software Center, pull up Compiz in your installed programs, and try to uninstall it. You'll get two packages that depend on it, and you have to uninstall those too. 

And I'm worried I'll botch my install if I remove Compiz.

strange. it doesn't do that if you try to remove it through synaptic package manager (system > administration > synaptic)

i didn't know metacity had its own compositor.

---

### Post by NoaHall on 2010-02-22
> **Post Monkeh said:**
> strange. it doesn't do that if you try to remove it through synaptic package manager (system > administration > synaptic)

i didn't know metacity had its own compositor.

Yeah, it does.
```
gconf-editor
```
Then look under metacity settings.

---

### Post by Post Monkeh on 2010-02-22
heh, every day's a school day.

---

### Post by litemirrors on 2010-02-22
I'd suggest you are not entirely correct about Compiz.

It is completely stable in my experience provided the hardware that Linux is running has correctly supported drivers. You can't suggest an EeeBox B202 with it's very low specs but runs Compiz perfectly is in some way MAGICAL. Compiz is implemented flawlessly and not buggy, if the drivers on your system were not buggy then neither would Compiz be.

So really it's down to drivers :|

---

### Post by NoaHall on 2010-02-22
> **litemirrors said:**
> I'd suggest you are not entirely correct about Compiz.

It is completely stable in my experience provided the hardware that Linux is running has correctly supported drivers. You can't suggest an EeeBox B202 with it's very low specs but runs Compiz perfectly is in some way MAGICAL. Compiz is implemented flawlessly and not buggy, if the drivers on your system were not buggy then neither would Compiz be.

So really it's down to drivers :|

Compiz does not work to his satisfaction. That is 100% correct, and no one can claim otherwise.

---

### Post by Woolio1 on 2010-02-22
> **litemirrors said:**
> I'd suggest you are not entirely correct about Compiz.

It is completely stable in my experience provided the hardware that Linux is running has correctly supported drivers. You can't suggest an EeeBox B202 with it's very low specs but runs Compiz perfectly is in some way MAGICAL. Compiz is implemented flawlessly and not buggy, if the drivers on your system were not buggy then neither would Compiz be.

So really it's down to drivers :|

Right, well, I just want to get rid of it. Completely. For good. 

I don't want to have to worry about it crashing my Dell Mini 10 anymore.

---

### Post by Woolio1 on 2010-02-22
Also, how would I go about reducing the number of active workspaces? I have four. I only want one. 

Any ideas?


EDIT: A clarification of what's happened to crash my Dell. Compiz gets a memory leak, and proceeds to suck up all my system resources. This, in turn, leads to my Dell having a kernel panic. No permanent damage is done, but it gets annoying to have to reboot every day because of a flaw in a program.

---

### Post by gn2 on 2010-02-22
> **Woolio1 said:**
> Also, how would I go about reducing the number of active workspaces? I have four. I only want one.

Right-click on the panel workspace switcher icon, select Preferences and set number of workspaces to 1.

---

### Post by Woolio1 on 2010-02-22
> **gn2 said:**
> Right-click on the panel workspace switcher icon, select Preferences and set number of workspaces to 1.

Okay, thanks.

---

### Post by Simon17 on 2010-02-22
> **litemirrors said:**
> Compiz is implemented flawlessly and not buggy
> **litemirrors said:**
> [SIZE="5"]Compiz is implemented flawlessly and not buggy[/SIZE]
lawl.

---

### Post by mkvnmtr on 2010-02-22
When ever I install from the full Ubuntu disk I remove all compiz packages and a lot of other stuff also. I open Synaptic type compiz in the search box and proceed to remove all of thenpackages that are installed. Done it at least 10 times over 5 or 6 releases and never had a problem. It does give you a chance to look at everything that might be removed with it. Never had to do it on a compiz package but on others if I loose something I just reinstall it.

---

### Post by Woolio1 on 2010-02-22
> **mkvnmtr said:**
> When ever I install from the full Ubuntu disk I remove all compiz packages and a lot of other stuff also. I open Synaptic type compiz in the search box and proceed to remove all of thenpackages that are installed. Done it at least 10 times over 5 or 6 releases and never had a problem. It does give you a chance to look at everything that might be removed with it. Never had to do it on a compiz package but on others if I loose something I just reinstall it.

I'm using a netbook with a 160gb Hard Disk. I can't afford to waste 30gb of that on bloaty stuff that comes with the OS.

---

### Post by the yawner on 2010-02-22
I don't think Compiz would need that much disk space. Also, I'm not sure about the dependencies, but just turning Compiz (Desktop Effects) off is enough to prevent Compiz from ever running.

---

### Post by koleoptero on 2010-02-22
> **Woolio1 said:**
> I'm using a netbook with a 160gb Hard Disk. I can't afford to waste 30gb of that on bloaty stuff that comes with the OS.

I doubt that compiz will save you much space, but I can also understand it might be redundant in such a small screen.

---

### Post by gn2 on 2010-02-23
> **Woolio1 said:**
> I'm using a netbook with a 160gb Hard Disk. I can't afford to waste 30gb of that on bloaty stuff that comes with the OS.

Don't use Vista then.

---

### Post by Tristam Green on 2010-02-23
> **Woolio1 said:**
> Go into the Ubuntu Software Center, pull up Compiz in your installed programs, and try to uninstall it. You'll get two packages that depend on it, and you have to uninstall those too. 

And I'm worried I'll botch my install if I remove Compiz.

Only one way to find out if it will botch the install.  Take an image, make backups, and go to town :)

You can uninstall it, but really I'd just go the route outlined previously and disable it.  Uninstallation won't really save you that much space, especially on a 160gb drive ;-)

> **gn2 said:**
> Don't use Vista then.

Now that's not called for.

---

### Post by Post Monkeh on 2010-02-23
> **Tristam Green said:**
> 
You can uninstall it, but really I'd just go the route outlined previously and disable it.  Uninstallation won't really save you that much space, especially on a 160gb drive ;-)



i went into synaptic and opted to uninstall everything to do with compiz and it came in at 40mb (and i've installed all the extra stuff too, so a default install would be far less than that)

funny though, it still doesn't want to remove anything else like the ubuntu software centre seems to want to.

---

### Post by swoll1980 on 2010-02-23
> **litemirrors said:**
> I'd suggest you are not entirely correct about Compiz.

It is completely stable in my experience provided the hardware that Linux is running has correctly supported drivers. You can't suggest an EeeBox B202 with it's very low specs but runs Compiz perfectly is in some way MAGICAL. Compiz is implemented flawlessly and not buggy, if the drivers on your system were not buggy then neither would Compiz be.

So really it's down to drivers :|

Wow thanks for the post. I needed a good laugh today.

---

### Post by litemirrors on 2010-02-23
> **swoll1980 said:**
> Wow thanks for the post. I needed a good laugh today.

I'm smiling inside :)

---

