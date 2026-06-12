---
title: "An equivalent to OpenSUSE's &quot;1-Click&quot; Install system in Ubuntu..."
date: 2009-10-08
forum: The Cafe
---

### Post by hoppipolla on 2009-10-08
I was talking about this with an OpenSUSE-usin' friend of mine earlier today on the phone - the 1-Click install system currently implemented on OpenSUSE.

It seems like a really cool system, and one that would be great for Ubuntu, I am tempted to suggest it on Brainstorm etc etc, but I think it's basically what they have in mind in the near future anyway right? Isn't this the kind of thing they were talking about for Karmic or Lucid?

For people who don't know, the way it works is that a project includes the installer on it's site, and in one click of a button the .ymp file is downloaded and set up complete with repositories and everything, kinda like Chrome does on Ubuntu I guess! :)

Examples are on this page: [http://en.opensuse.org/KDE4](http://en.opensuse.org/KDE4)


I was just wondering if anyone knows how plans for Ubuntu compare to this 1-Click system and whether it's worth bringing it up anywhere or if it's already in consideration/implementation anyway?

And pleeeaaaase could no-one turn this into a thread about whether or not it's a good idea, or how the current system is just fiiiiine how it is... changes like this I'm afraid are probably going to happen anyway (and I think they will be fantastic!) - I really just wanted to discuss whether what we will have might be comparable to 1-Click!

Thanks guys,

Hoppi :)

---

### Post by Xbehave on 2009-10-08
Apparently its been done for PPAs (and probably 3rd party repos) in 9.10.

---

### Post by SunnyRabbiera on 2009-10-08
Linux mint has something similar with its one click install.
But there is one big issue I have with the openSUSE one click install, is that it often duplicates repositories you have already, or sometimes it will give you a repostitory that gives you unstable packages that make it into the updates.

---

### Post by FuturePilot on 2009-10-08
[AptURL?]("https://help.ubuntu.com/community/AptURL")
[more]("https://wiki.ubuntu.com/AptUrl")

---

### Post by OpenGuard on 2009-10-08
Hmm .. [1-Click-Install]("apt:apache2") :rolleyes:

---

### Post by RichardLinx on 2009-10-08
> **OpenGuard said:**
> Hmm .. [1-Click-Install]("apt:apache2") :rolleyes:

Broken link.

---

### Post by OpenGuard on 2009-10-08
> **RichardLinx said:**
> Broken link.

It's not broken. See post #4 ( by FuturePilot ).

---

### Post by RichardLinx on 2009-10-08
> **OpenGuard said:**
> It's not broken. See post #4 ( by FuturePilot ).

Nevermind, it just doesn't work in Opera for some reason:
> You tried to access the address apt:apache2, which is currently unavailable. Please make sure that the Web address (URL) is correctly spelled and punctuated, then try reloading the page.
Make sure your Internet connection is active and check whether other applications that rely on the same connection are working.

In firefox it gives me the option to install Apache2. Why doesn't it work in Opera, anyone know?

---

### Post by kevin11951 on 2009-10-08
Apturl is not one click install, 1ci in open suse adds a repo for software, apturl just installs a program from repos you already have.

---

### Post by OpenGuard on 2009-10-08
> **RichardLinx said:**
> 
In firefox it gives me the option to install Apache2. Why doesn't it work in Opera, anyone know?

> If you use [Opera]("https://help.ubuntu.com/community/OperaBrowser"), you just need to go in the menu *Tools* then *Preferences*. Clic on the tab *Advanced* then *Programs*, and choose *Add*. In *Protocol*, enter **apt** and in *Open with another application*, enter **apturl**. Clic on the button OK and restart Opera. 

As stated above.

---

### Post by hoppipolla on 2009-10-08
> **kevin11951 said:**
> Apturl is not one click install, 1ci in open suse adds a repo for software, apturl just installs a program from repos you already have.

Oh really? So what is it that Chrome and that do that allows the install to be effectively "one click" on Ubuntu? :)

---

### Post by OpenGuard on 2009-10-08
> **kevin11951 said:**
> Apturl is not one click install, 1ci in open suse adds a repo for software, apturl just installs a program from repos you already have.

OpenSUSE adds repos, Ubuntu already have them. If apturl is not some kind of 1-click-install, it's aint possible at all.

---

### Post by Tibuda on 2009-10-08
> **hoppipolla said:**
> Oh really? So what is it that Chrome and that do that allows the install to be effectively "one click" on Ubuntu? :)

Chrome is just a simple deb file which installs the software source to /etc/apt/sources.list.d. Opera also does the same.

---

### Post by hoppipolla on 2009-10-08
> **OpenGuard said:**
> OpenSUSE adds repos, Ubuntu already have them. If apturl is not some kind of 1-click-install, it's aint possible at all.

o.O What ARE you talking about?

---

### Post by hoppipolla on 2009-10-08
> **danielrmt said:**
> Chrome is just a simple deb file which installs the software source to /etc/apt/sources.list.d. Opera also does the same.

ah awesome. Does 1-Click do any more than this, or are they effectively doing the same thing? It's an important topic I think, as it does make software installation (of things that aren't in the default repositories) much easier and quicker for the user.

---

### Post by FuturePilot on 2009-10-08
> **hoppipolla said:**
> ah awesome. Does 1-Click do any more than this, or are they effectively doing the same thing? It's an important topic I think, as it does make software installation (of things that aren't in the default repositories) much easier and quicker for the user.

Essentially, it accomplishes the same thing.

---

### Post by OpenGuard on 2009-10-08
> **hoppipolla said:**
> o.O What ARE you talking about?

Disneyland :twisted:

---

### Post by juancarlospaco on 2009-10-08
**What about the digital PGP signatures...?**
*i can trick DNS to install a specially crafted package on opensuse, and opensuse PWN[I]ed*.[/I]

---

### Post by hoppipolla on 2009-10-08
> **juancarlospaco said:**
> **What about the digital PGP signatures...?**
*i can trick DNS to install a specially crafted package on opensuse, and opensuse PWN[I]ed*.[/I]

ah yes I think these can currently be done too, I think Chrome did that for me...

What we may currently be missing is the actual IMPLEMENTATION, as not many programs seem to support this kind of system, certainly not for Ubuntu. Maybe it just needs to be given a cool name, like 1-Click has! hehe :)

Fingers crossed it's on the cards for Karmic or Lucid! ^_^

---

### Post by juancarlospaco on 2009-10-08
i prefer a .deb,
it can install PGP key, Repo, and program :)
and can be used by APTurl, just add "*?refresh=yes*" at the end of an apturl link

*BTW the 1-click "working-method" is pretty similar to ZeroInstall*

---

