---
title: "Why wouldn't it be possible to make programs work natively in gnome and kde?"
date: 2007-05-06
forum: The Cafe
---

### Post by Mateo on 2007-05-06
Why wouldn't it be possible to make the two compatible so that a program looks like a KDE program in KDE and looks like a gnome program in gnome?  I'm not a programmer so I don't know.  Why couldn't you create a "standards" similar to what they do with web standards, so that all of the code is the same and just looks differently depending on where it is being run.

---

### Post by igknighted on 2007-05-06
> **Mateo said:**
> Why wouldn't it be possible to make the two compatible so that a program looks like a KDE program in KDE and looks like a gnome program in gnome?  I'm not a programmer so I don't know.  Why couldn't you create a "standards" similar to what they do with web standards, so that all of the code is the same and just looks differently depending on where it is being run.

It is, it's done with themes.  The problem is the backend libraries.  It could LOOK native, but there will always be more backend libraries to load, so the performance will never be the same.

---

### Post by Whiffle on 2007-05-06
They have standards, KDE uses Qt, gnome pretty much uses GTK.  The two standards aren't entirely compatable.  However, I'm using the Qtcurve style under KDE and it does a wonderful job of imitating GTK, so pretty much my KDE looks like gnome, but runs like KDE, and I like that.

---

### Post by Mateo on 2007-05-06
> **Whiffle said:**
> They have standards, KDE uses Qt, gnome pretty much uses GTK.  The two standards aren't entirely compatable.  However, I'm using the Qtcurve style under KDE and it does a wonderful job of imitating GTK, so pretty much my KDE looks like gnome, but runs like KDE, and I like that.

Those are separate standards.  They should make a linux-wide standards so that they look native no matter what DE a person uses.

---

### Post by Whiffle on 2007-05-06
Maybe.  But, a big draw to linux is the choices you get to make.  Developers can choose whether or not they want to use GTK, Qt, mono, etc, there are advantages and disadvantages to each.  If it was one big standard, everyone would have to use the same thing, and then it starts to look alot like windows.

---

### Post by Tomosaur on 2007-05-06
There's no need to. KDE apps run on Gnome, Gnome apps run on KDE. As long as you have the correct dependencies installed (which any decent package manager will do), there's no problem.

---

### Post by bikeboy on 2007-05-06
You might also be interested in the Portland Project.

[http://portland.freedesktop.org](http://portland.freedesktop.org) (seems to be down atm for me)
[http://en.wikipedia.org/wiki/Portland_project](http://en.wikipedia.org/wiki/Portland_project)

[ Google hits on Portland Project](http://www.google.com/search?q=portland+project&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by RAV TUX on 2007-05-06
I currently use both Gnome and KDE in the same desktop:

see this thread(@ the CafeLinux.org Forum): [KDE or Gnome? I choose both at the same time.]("http://cafelinux.org/forum/index.php/topic,214.0.html")

---

### Post by RAV TUX on 2007-05-06
> **RAV TUX said:**
> I currently use both Gnome and KDE in the same desktop:

see this thread(@ the CafeLinux.org Forum): [KDE or Gnome? I choose both at the same time.]("http://cafelinux.org/forum/index.php/topic,214.0.html")

I should also state there is zero performance loss running both KDE and Gnome at the same time. :)z

---

### Post by Polygon on 2007-05-07
> **RAV TUX said:**
> I should also state there is zero performance loss running both KDE and Gnome at the same time. :)z

yeah there is

instead of just gnome libs you also have kde libs. So if you have a gnome and a kde program running at the same time, then you are using both sets of libraries

you might not notice a performance difference, but you are using more libraries then the normal joe user would be using, and on slower computers that might cause a problem,

---

### Post by mech7 on 2007-05-07
> **Whiffle said:**
> Maybe.  But, a big draw to linux is the choices you get to make.  Developers can choose whether or not they want to use GTK, Qt, mono, etc, there are advantages and disadvantages to each.  If it was one big standard, everyone would have to use the same thing, and then it starts to look alot like windows.

It would be allot easier to develop for linux then and if there was a standard maybe one day commercial software will be written for it.

---

### Post by Arathorn on 2007-05-07
Well there was the [Metatheme](http://www.metatheme.org/) project but it seems to have died two years ago for some reason. Maybe some people can pick it up?

---

### Post by forrestcupp on 2007-05-07
The OP has a point, though.  I use Gnome.  I can run KDE programs in Gnome, but the interface looks like KDE (other than the themed title bar).  It might be kind of cool if the same program would look like Gnome in Gnome, but look like KDE in KDE.  But it won't happen because people are pretty partial to either QT or GTK. 

I think wxWidgets is along those lines, though.  If you program in wxWidgets, there is one source code that compiles to use whatever the native controls are.  I could program one source in wxWidgets, and compile it for Linux, Mac and Windows and each looks native.  I really don't know if it will distinguish between KDE and Gnome, though.  It may just use GTK for Linux.

---

### Post by Mateo on 2007-05-07
> **Tomosaur said:**
> There's no need to. KDE apps run on Gnome, Gnome apps run on KDE. As long as you have the correct dependencies installed (which any decent package manager will do), there's no problem.

Looks like garbage, that's a problem in my opinion.

---

### Post by fuscia on 2007-05-07
corraling everything into one standard just makes everyone miserable. it's better to have comperable apps in each standard, allowing people to have something they like from the standard they prefer.

---

### Post by RAV TUX on 2007-05-09
> **Polygon said:**
> yeah there is

instead of just gnome libs you also have kde libs. So if you have a gnome and a kde program running at the same time, then you are using both sets of libraries

you might not notice a performance difference, but you are using more libraries then the normal joe user would be using, and on slower computers that might cause a problem,

You have a point.

In all honesty I prefer to use [SIZE=-1][e17]("http://www.google.com/url?q=http://www.enlightenment.org/Enlightenment/DR17/&sa=X&oi=smap&resnum=1&ct=result&cd=2&usg=AFrqEzcztjStdrlFJXKt_N0qEptmQ4iN2w") or [/SIZE][**fluxbox**]("http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Ffluxbox.sourceforge.net%2F&ei=5I1CRqyGE4mEgATO7IiVDw&usg=AFrqEzcplPnq1-TPg2buG2uGnwYiM3UPeA&sig2=tEsiJxVuIdlPp2M9O9SdTQ") over Gnome, KDE, or XFCE.

Has anybody built an e17 version of Ubuntu? not just e17 on Ubuntu but e-buntu

like kubuntu, xubuntu, fluxbuntu, etc

EDIT: it looks like elbuntu is taking a hack it:

[http://www.ebuntu.org/](http://www.ebuntu.org/)

but it seems to be a bit stagnant?

[http://translate.google.com/translate?hl=en&sl=de&u=http://www.ebuntu.org/&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3De-buntu%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26hs%3DwcJ](http://translate.google.com/translate?hl=en&sl=de&u=http://www.ebuntu.org/&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3De-buntu%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26hs%3DwcJ)

---

### Post by G Morgan on 2007-05-10
I think the biggest problem isn't choice here, it's the fact we have two flawed standards with advantages and disadvantage. People don't choose to use GTK+ over QT or vice versa. If they use C++ they will generally use QT which is easier to develop for and technically superior. If they don't use C++ then they practically have no option but GTK+.

QT performs better and has more features but is almost completely tied to C++. GTK+ is technically inferior but is fortunate enough to be written in C so can easily be bound elsewhere so can be used in practically any language. What we need is a library with the technical merits of QT but written in C. If such a toolkit is powerful enough to emulate the previous two libraries then all the better. If such a toolkit ever came about I think we would see both projects move in that direction long term.

---

