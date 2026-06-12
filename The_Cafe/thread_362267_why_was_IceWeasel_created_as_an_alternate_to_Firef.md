---
title: "why was IceWeasel created as an alternate to Firefox??"
date: 2007-02-15
forum: The Cafe
---

### Post by billdotson on 2007-02-15
I hear it was because Firefox was not completely free.  What in the world does that mean.. firefox is free to modify, distribute, etc.  what is not free about Firefox?.. because I haven't noticed anything that required money.

---

### Post by nandasunu on 2007-02-15
The debian guys created IceWeasel because the Firefox logo is not open source, Debian is very fanatic about open source to that level and wants 100% no closed source stuff in their distro, hence IceWeasel was created, only difference is an open source logo.

---

### Post by Nakkis on 2007-02-15
I'm not completely sure but I think it was because Ubuntu's/Debian's Firefox was slightly modified, and Mozilla only lets 100% non-modified versions to be called Firefox.

---

### Post by K.Mandla on 2007-02-15
[quote=Gnuzilla Web site]IceWeasel is the GNU version of the Firefox browser. Its main advantage is an ethical one: it is entirely free software. While the source code from the Mozilla project is free software, the binaries that they release include additional non-free software. Also, they distribute non-free software as plug-ins. (IceWeasel does keep the triple licensing used by Firefox to facilitate the reuse of code.)[/quote]
[http://www.gnu.org/software/gnuzilla/](http://www.gnu.org/software/gnuzilla/)

---

### Post by billdotson on 2007-02-15
ah I see, but people can create their own firefox icons, they just can't modify the existing one (legally anyway)

---

### Post by nandasunu on 2007-02-15
> **billdotson said:**
> ah I see, but people can create their own firefox icons, they just can't modify the existing one (legally anyway)

thats the point, open source means that they should be allowed to freely modify anything.

---

### Post by Mateo on 2007-02-15
that's what we call zealotry, folks, when you fork a program over an icon.

---

### Post by shining on 2007-02-15
> **Mateo said:**
> that's what we call zealotry, folks, when you fork a program over an icon.

It isn't (really) a fork imo. A fork wouldn't only track the original branch, it would go a different way, because its developers have different ideas (technical, not political). Like dragonfly bsd which forked from freebsd.
And iceweasel isn't an alternative to firefox either, it is firefox, just a free version of it.
It might still be zealotry though, I'm not denying that (but I didn't like mozilla's attitude neither).

---

### Post by LindsM on 2007-02-15
IceWeasel is not really an alternative to Firefox; it's the same program with a new icon and name. If you take your Firefox and change the icon and name to IceWeasel, you'll basically have IceWeasel. It's only a legal issue, not a technical one.

---

### Post by tageiru on 2007-02-15
> **nandasunu said:**
> The debian guys created IceWeasel because the Firefox logo is not open source, Debian is very fanatic about open source to that level and wants 100% no closed source stuff in their distro, hence IceWeasel was created, only difference is an open source logo.

Iceweasel was created because Mozilla has strict guidelines for the Firefox trademark. It is illegal to compile Firefox with external patches and call it Firefox without explicit permission from Mozilla. Mozillas requirements are bizarre because no other free software project acts like this. You can apply patches to Linux, GNOME, KDE... and still keep their brand name.

The icon issue is just a small part of this.

---

### Post by Arathorn on 2007-02-15
The reason for this licensing of the Mozilla names and logos is because they want their products to have one version for the outside world. By keeping the name and logo trademarked they can make sure their products won't be confused with possibly bad changes people make in offered builds. For example, I could buy the domain [www.fyrefox.com]("http://www.fyrefox.com") and offer a compiled version with added spyware, and a lot of unknowing people will download it and complain to Mozilla. If you think this doesn't happen, do a search for eMule on Google, you'll find dozens of sites selling eMule versions to unknowing people. Then when you go to the eMule forum at [www.emule-project.net](www.emule-project.net) you'll see a lot of threads from people complaining.

---

### Post by Anthem on 2007-02-15
If I was a Firefox developer, I would hate Ubuntu and (I'm guessing) Debian.  We DESTROY Firefox with our builds, using all our own patches.

Try the default Firefox sometime, then try one downloaded from [www.getfirefox.com](www.getfirefox.com).  You'll notice a big difference.  The Ubuntu Firefox is far inferior to the stock one.  Lots of people complain about the speed of Firefox vs. (for example) Epiphany, but this speed difference is negligible using the "real" Firefox.  It's only noticeable using Ubuntu's Firefox.

And yet we use the icon and name and they're not mad at us.  The whole thing is a tempest in a teapot between some Debian developers and Firefox-legal.

---

### Post by Arathorn on 2007-02-15
I haven't used the Mozilla Firefox on Ubuntu, but I feel no difference between the Ubuntu Firefox and Firefox on Windows.

---

### Post by Kernel Sanders on 2007-02-15
I agree with Mozilla's stance. If I make my own version of firefox and fill it with all sorts of junk, why should I be free to call it firefox and confuse others?

I also dont understand why Ubuntu/Debian need to modify it. Why not use the standard Firefox for linux build? :confused:

---

### Post by Mateo on 2007-02-15
^^ zealotry.

---

### Post by Bloodfen Razormaw on 2007-02-15
It's not just that the logo isn't free, although that is a part of it.  If the logo isn't free then the software isn't free, anymore than a video game using a free engine and non-free content would be free.  But it is much worse.  Firefox's *code* is also not free.  Firefox uses proprietary code for its bug reporting.  There are also practical reasons that is necessary, such as Firefox's practice of targetting Windows.  The extension system does not work properly in a multiuser environment, and the Mozilla Corporation refused to allow Debian to fix that.  Most distributions got around those flaws by applying their own patches and not using the logo or name.  Iceweasel will provide a single upstream source for patches so that work is not duplicated.

---

### Post by agurk on 2007-02-15
> **Mateo said:**
> ^^ zealotry.

Well, don't blame Debian, read [this](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=354622) for the full picture.
The thread also clearly explains the several reasons why Debian needs to patch Ff themselves. My taking is that Moz made a bad call here.

---

