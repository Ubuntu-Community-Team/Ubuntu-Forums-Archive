---
title: "Is there any way to &quot;lock down&quot; Ubuntu Linux 10?"
date: 2011-04-29
forum: Security
---

### Post by Learning Linux 2011 on 2011-04-29
Is there a way to put a Linux computer in a public place (like a library for example) and lock it down so much that users could do just the bare minimum like browse the web and use Office for example?  
And they couldn't do much of anything else like open a terminal, install software, copy discs, etc.?
Can Linux be locked down like that?

---

### Post by lykwydchykyn on 2011-04-30
Yes.

I believe Gnome has a tool called pessulus which can do this.  I haven't used it myself; years ago when I first started using Linux for kiosk applications, I tried many different things (KDE 3 had a kiosk tool, for example).

I came to the conclusion that the best approach is to start with a very simple, minimal environment and only add what you need.  I combined this with a script that refreshed the kiosk user's home directory on logout or whenever the browser was closed, and the result has been pretty bullet proof.

---

### Post by Lars Noodén on 2011-04-30
[KDE](http://www.google.com/search?hl=en&q=kiosk+mode+-site:microsoft.com+kde) has a [kiosk mode](http://extragear.kde.org/apps/kiosktool/).  Some applications (IIRC Opera and Lynx) can also be locked down.

---

### Post by timothy48342 on 2011-04-30
> **Lars Noodén said:**
> [KDE]("http://www.google.com/search?hl=en&q=kiosk+mode+-site:microsoft.com+kde") has a [kiosk mode]("http://extragear.kde.org/apps/kiosktool/").  Some applications (IIRC Opera and Lynx) can also be locked down.

I'm still on my "First Cup of Ubuntu", so you don't need to listen to me at all, but I just had a though on this.

What about running from a slightly modified liveCD that wipes the entire hard drive either on shutdown or on boot. Give them free reign to do whatever they want while it's runing, but everything gets cleared between users.

--tim

---

### Post by bodhi.zazen on 2011-04-30
google search "kiosk" 

There are several distros that do this specifically.

IMO the "best" out of the box option is Fedora + install the so called xguest package. This creates a guest account , with no password. The guest account is locked down like a kisok and is protected from bad behavior by selinux. Probably as easy and secure as it gets "out of the box".

---

### Post by BobHicks on 2012-04-30
There are a couple of thisng you can do. As mentioned pessulus supplies a number of good lockdown tools. In addition I use Lethe wich is a "DeepFreeze" type of program. The gconf-editor is another usefull tool that I use. I set up Ubuntu 10.04 labs in my hight school and they have been up and running without a problem since September.

---

### Post by oldos2er on 2012-04-30
Old thread closed.

---

