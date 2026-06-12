---
title: "I had an idea that is probably stupid :)"
date: 2006-01-12
forum: The Cafe
---

### Post by prizrak on 2006-01-12
I was wondering if it would be better for Ubuntu to create a standalone app for networking that would be able to run on any DE/WM, handle both wi-fi and wired connections as well as having a GUI to administer WPA and have profiles similar to wireless zero of Windows. I was actually thinking that it might make sense to create a complete stand alone "Control Panel" that would connect to all the underlying services that usually need to be configured by users. I think it would make sense to not rely on the built in tools in KDE/Gnome simply because some people with slower machines might prefer XFCE since it's alot more lightweight but then have to basically relearn everything you learn in the others. Like I said possibly a stupid idea :)

---

### Post by GeneralZod on 2006-01-12
Generally speaking, I personally would like to see pretty much *every* utility written as a pure logic "library" that allows easy bindings to a GUI toolkit of your choice, whether it be ncurses, GTK, Qt, motif or something as yet unheard of - it's simply far better design, and would help cut down on the mammoth re-invention of the wheel you see across all distros.  So yes, your idea is a good one, but I'm not sure if it will ever happen :(

---

### Post by Lovechild on 2006-01-12
It sounds an awful lot like NetworkManager to me

---

### Post by chimera on 2006-01-12
[QUOTE=GeneralZod]Generally speaking, I personally would like to see pretty much *every* utility written as a pure logic "library" that allows easy bindings to a GUI toolkit of your choice, whether it be ncurses, GTK, Qt, motif or something as yet unheard of - it's simply far better design, and would help cut down on the mammoth re-invention of the wheel you see across all distros.  So yes, your idea is a good one, but I'm not sure if it will ever happen :([/QUOTE]

yeah, and than we can make one universal GUI, and than one universal distro with a standard for everything (including viruses) and rename it to windows 95:rolleyes: 

bad idea IMO. Linux is about diversity, not standards.

---

### Post by GeneralZod on 2006-01-12
[QUOTE=chimera]yeah, and than we can make one universal GUI, and than one universal distro with a standard for everything (including viruses) and rename it to windows 95:rolleyes: 

bad idea IMO. Linux is about diversity, not standards.[/QUOTE]

You probably missed the part where I said you could attach any GUI you want to it ;).  Diversity is a noble goal, but all too often the re-invented wheels simply end up doing almost exactly the same thing, just in completely incompatible ways.

prizrak's example is a very good example of this - for a networking configurator, there are a set number of tasks that you could possibly want to accomplish - set WPA; configure a given interface to use either dhcp or a static IP; etc.  If a library can perform all of these tasks, there is simply no need for another one - having a whole menagerie of other libraries that do the exact same thing (or are less feature-packed) really benefits nobody.  The GNOME and KDE camps are then free to wrap all of this functionality in the GUI of their choice - *this* kind of diversity is good, because people have very different tastes when it comes to GUI software.

---

### Post by UbuWu on 2006-01-12
[QUOTE=Lovechild]It sounds an awful lot like NetworkManager to me[/QUOTE]

Indeed. Only WPA is not integrated yet, but they are working on that.

[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

---

### Post by prizrak on 2006-01-12
[QUOTE=Lovechild]It sounds an awful lot like NetworkManager to me[/QUOTE]
Looked at the link, looks pretty nice  but not in Ubuntu currently (possibly Dapper?) Also NetworkManager is a GNOME project it is not independent of everything else. WPA support is IMO pretty important at this point. Another thing that I would love to see addressed is being able to choose your network at boot really annoying that I have to Ctrl+C and then reconnect after I'm booted. 
I like General Zod's idea of one backend that would do all the networking (w/e system administration) stuff that can be accessed via any GUI you feel like writing. 
Chimera, I didn't say anywhere there should be one universal distro in fact I mentioned that I would like something that would work the same way in any GUI you chose. There are things that should be diversified and there are things that should be universal. No one says that all cars shouldn't have a steering wheel, gear lever (they are moving to buttons now tho) and pedals. Having predictable controls across the board is a great thing for useability it makes it alot easier to adopt different GUI's. Using the car example again you have a choice of many cars that will have the familiar controls. My idea is actually a result of XFCE experience, for some weird reason the wlan plug in for XFCE just refused to work with my wireless card even though it uses the same exact driver.

---

