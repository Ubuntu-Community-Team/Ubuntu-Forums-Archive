---
title: "Macs not proprietary???"
date: 2009-05-12
forum: The Cafe
---

### Post by Matthewthegreat on 2009-05-12
I was looking at this page on apple.com: 
[URL="http://www.apple.com/science/whymac/myths.html"]
http://www.apple.com/science/whymac/myths.html[/URL]

and I seen this part:

> Myth: Macs are proprietary.
Fact: Mac OS X is an open architecture, based on industry standards.

It’s based on an open source variant of FreeBSD UNIX and developed entirely with openness and interoperability in mind. Mac OS X incorporates the major open standards for directory services, programming and scripting languages, interprocess communications and arithmetic libraries.
 
The wikipedia says this about the BSD license:

[URL="http://en.wikipedia.org/wiki/BSD_license"]
http://en.wikipedia.org/wiki/BSD_license[/URL]

> Proprietary software licenses compatibility

The BSD License allows proprietary commercial use, and for the software released under the license to be incorporated into proprietary commercial products. Works based on the material may be released under a proprietary license or as closed source software. This is the reason for widespread use of the BSD code in commercial products, ranging from Juniper Networks routers to Mac OS X.


From what I understand the BSD license, unlike the linux license, with allow it to be relicensed under proprietary licenses. So OS X uses FreeBSD under a proprietary license, right? So wouldn't this mean macs ***are*** proprietary? or am I missing something?

---

### Post by schauerlich on 2009-05-12
A lot of the underpinnings are true FOSS and licensed either under BSD or [Apple's Public Source License](http://www.opensource.apple.com/license/apsl/), and packaged into something called ["Darwin."](http://developer.apple.com/referencelibrary/Darwin/) Pretty much everything above the base system is in house and proprietary. There are two main projects to port FOSS software to OS X, [MacPorts](http://developer.apple.com/mac/articles/opensource/workingwithmacports.html) and [Fink](http://www.finkproject.org/)

---

### Post by monsterstack on 2009-05-12
They can go right ahead and take BSD code and license it any way they wish. That's the point of BSD licences. Apple uses a mixture of closed- and open-source components.

---

### Post by glotz on 2009-05-12
That's just Apple marketing lies.

Macs are every bit as proprietary as windoze, actually even more so as the EULA says you can only run OS X on Apple hardware...

---

### Post by tjwoosta on 2009-05-12
[http://en.wikipedia.org/wiki/Proprietary]("http://en.wikipedia.org/wiki/Proprietary")

> The word proprietary indicates that a party, or proprietor, exercises private ownership, control or use over an item of property.

Does mac not exercise private ownership?

Can I make changes to osx and redistribute it?

I can't even legally install osx on non-mac hardware and their saying its not proprietary?

---

### Post by monsterstack on 2009-05-12
Nope.

---

### Post by LightB on 2009-05-12
Mac users don't care about open or closed. They're the comfort seeking rabble, often they fail, too. 







Still smarter than Windows users by a mile, though. :)

---

### Post by HappyFeet on 2009-05-12
Does it matter? This world has a lot of problems.

---

### Post by Ocxic on 2009-05-12
OS X as an entire system is and can be controlled by Apple, however a there are many components that are open source and can be changed and redistributed without Apple being able to do anything.
OS X is a mix of open and closed source software, Apple controls the closed source stuff and can do as they wish, including applying there own EULA

However IMHO Apple although they are trying, Apple is currently in an anti-trust case due to the "You can only use OS X w/ Apple Hardware" clause in the EULA. 
Brought upon by the Hackintosh peoples cry of foul play.

---

### Post by Tibuda on 2009-05-12
The Darwin kernel is open source. You can download its sources or binary ISO image from [http://developer.apple.com/Darwin/](http://developer.apple.com/Darwin/) and install it in any computer you want. But you'll only have a console screen, which you can install a X Server, and you favorite open source desktop environment (Gnome, KDE, etc). You won't be able to run any Mac GUI application like Photoshop and iWork, because the Aqua/Cocoa toolkits are proprietary. You better stick with Linux and Ubuntu, as that's a lot easier to setup than Darwin. If you want a Mac, buy it. If you can't afford it, get some money.

---

### Post by subdivision on 2009-05-12
:roll:> **LightB said:**
> Mac users don't care about open or closed. They're the comfort seeking rabble, often they fail, too. 
 
 
 
 
 
 
 
Still smarter than Windows users by a mile, though. :)
 
Yeah, those stupid Windows users and their less expensive PCs with more support from 3rd party software developers. :roll:

---

### Post by subdivision on 2009-05-12
meh

---

### Post by schauerlich on 2009-05-12
> **LightB said:**
> Mac users don't care about open or closed. They're the comfort seeking rabble, often they fail, too. Still smarter than Windows users by a mile, though. :)

Linux users make stereotyped, sweeping generalizations about users of other operating systems.

---

### Post by calrogman on 2009-05-12
> **LightB said:**
> Still smarter than Windows users by a mile, though. :)

This is arguable, I used the terminal in Windows to do plenty of things, from defragging to changing the power scheme, most Mac users never open the terminal.

---

### Post by init1 on 2009-05-12
The core of the system is FOSS, but most of it is proprietary.

---

### Post by Matthewthegreat on 2009-05-12
That makes sense. So this is just a advertising lie. Macs are proprietary but the core is FOSS.

Just a few more questions, the linux license is different from the BSD license, right?  What is the differences?  Could mac have used the linux code instead of BSD?

---

### Post by LightB on 2009-05-12
> **calrogman said:**
> This is arguable, I used the terminal in Windows to do plenty of things, from defragging to changing the power scheme, most Mac users never open the terminal.

Well, not the kind of smart I'm talking about, not knowing a trick or two. Smarter in the bigger picture. I can only assume that only a fool would choose to deliberately play along with the MS cartel, often neck deep in delusion. I can understand if children or people without much time would just use whatever is available, but to go out of your way to defend the act does not point to a lack of time but to a specific and deliberate choice and to seemingly a fool if the person is not new.

---

### Post by schauerlich on 2009-05-12
> **Matthewthegreat said:**
> Just a few more questions, the linux license is different from the BSD license, right?  What is the differences?  Could mac have used the linux code instead of BSD?

[http://www.linfo.org/bsdlicense.html](http://www.linfo.org/bsdlicense.html)

Scroll down to "BSD Licenses Versus the GPL"

The gist of it is, GPL requires you to distribute any changes you make to the code, whereas the BSD license doesn't. They could have used Linux code, but they would have had to open source any programs that they made that relied on Linux code.

Besides licensing, the main reason Mac OS X is based on FreeBSD and not Linux is that Mac OS X is based on NeXTSTEP, which in turn was based off of Mach and BSD. When NeXTSTEP was created, Linux did not exist.

---

### Post by I-75 on 2009-05-12
> **glotz said:**
> That's just Apple marketing lies.

Macs are every bit as proprietary as windoze, actually even more so as the EULA says you can only run OS X on Apple hardware...

 But it is OK to run Linux on a Mac machine.

---

