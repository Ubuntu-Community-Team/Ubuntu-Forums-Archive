---
title: "Prioritise developers for 9.04 (brainstorm idea)"
date: 2008-09-24
forum: Ubuntu Brainstorm
---

### Post by JeevesBond on 2008-09-24
I did a search, but it seems no-one on the forums is discussing this brainstorm idea on [prioritising developers for 9.04](http://brainstorm.ubuntu.com/idea/13596/):

[quote=brainstorm]Canonical currently has a big problem. It needs developers. Its a vicious cycle, developers are needed to improve development, yet to increase the number of developers, we need better development programs. 

The sad reality is that whilst Canonical has a wealth of development tools available, they are barely officially supported, out of date, or have no easy way of using them (like systemtap). 

We need Canonical to step up and make the development environment for 9.04 a priority, so that first time linux developers, and long time developers have a powerful environment, that is officially supported by Canonical.[/quote]

This seems like a very worthwhile idea, if not for 9.04 then for the next release. Personally I see this as taking the form of a meta-package, depending on a bunch of dev tools, and some documentation. As it seems the dev tools in the repos are out of date, these would need to be updated too.

Well what do you think, ladies and gentlemen? :)

---

### Post by smartboyathome on 2008-09-24
I think this would be a financial problem for Canonical. Right now, they are barely able to get a few paid developers to work on Ubuntu. Trying to hire more might be stretching the wallet.

And the reason that the stuff in the repos is out of date is because Ubuntu is not a rolling release distro, and instead includes a lot of tested stable software which are frozen when Ubuntu is released. Trying to get Ubuntu to change that is like trying to get an elephant to be carnivorus (I know, weird analogy, but oh well :p).

---

### Post by JeevesBond on 2008-09-24
> I think this would be a financial problem for Canonical.
You misunderstand the idea. We're **not** asking Canonical to hire more developers, but to provide a meta-package for people who want to hack on Ubuntu.

Basically: sudo apt-get install ubuntu-sdk

> And the reason that the stuff in the repos is out of date is because Ubuntu is not a rolling release distro, and instead includes a lot of tested stable software which are frozen when Ubuntu is released.
But the Eclipse package is not just package import freeze out-of-date, it's [over a year](http://www.eclipse.org/eclipse/development/readme_eclipse_3.2.2.html) out-of-date!

The idea is to update, and make easily available, the tools needed to develop for the Ubuntu platform. This does not require large expenditure, however it probably will need to be the object of a non-LTS release.

---

### Post by bruce89 on 2008-09-24
> **JeevesBond said:**
> This seems like a very worthwhile idea, if not for 9.04 then for the next release. Personally I see this as taking the form of a meta-package, depending on a bunch of dev tools, and some documentation. As it seems the dev tools in the repos are out of date, these would need to be updated too.

See ubuntu-dev-tools

> **smartboyathome said:**
> Trying to get Ubuntu to change that is like trying to get an elephant to be carnivorus (I know, weird analogy, but oh well :p).

You could be the next Andrew Marr! (British political commentator, once said "it would be like a salmon bringing down an oil rig")

---

### Post by JeevesBond on 2008-09-24
> **bruce89 said:**
> See ubuntu-dev-tools

[quote=synaptic]useful tools for Ubuntu developers
This is a collection of useful tools that Ubuntu developers use to
make their packaging work a lot easier. Such tools can include bug
filing, packaging preparation, package analysis, etc.[/quote]
Good package name, but it's hardly what the idea is specifying. Looking at the dependencies and the description above, it seems this is just for making packaging easier. Not an easy way for developers to get started with Ubuntu development.

This brainstorm idea has been marked 'in development', although they seem to be refusing to include an IDE. 

Also, a message in the mailing list [confirms that Eclipse is very out of date](https://lists.ubuntu.com/archives/ubuntu-devel/2008-August/026004.html).

---

### Post by bruce89 on 2008-09-24
> **JeevesBond said:**
> Good package name, but it's hardly what the idea is specifying. Looking at the dependencies and the description above, it seems this is just for making packaging easier. Not an easy way for developers to get started with Ubuntu development.

There is no such thing as Ubuntu development. Ubuntu is all about packaging.

Anyway, here's a soundbite for you - "Geany's UI is a shambles".

---

### Post by smartboyathome on 2008-09-24
The reason most packages are out of date when it has been more than 1 release since it's update is because of the lack of package maintainer. If someone took up the job of packaging Eclipse using meathods in accordance with the MOTU, I am sure that it would be accepted.

---

### Post by JeevesBond on 2008-09-25
> **bruce89 said:**
> There is no such thing as Ubuntu development. Ubuntu is all about packaging.

Firstly, that is not entirely true. There's [Bazaar](http://bazaar-vcs.org/) (not really a part of the desktop, but it is an important part of tools used to put together the distro), [Upstart](http://upstart.ubuntu.com/) and [Ubiquity](https://wiki.ubuntu.com/Ubiquity).

Secondly, that's not what I meant, sorry if it wasn't clear. However, when I say Ubuntu development, I mean patches to upstream packages that are included in Ubuntu. Canonical [already does this](http://arstechnica.com/news.ars/post/20080911-canonical-to-fund-upstream-linux-usability-improvements.html), I believe we should make it easier for non-Canonical-sponsored developers to hack on packages included in Ubuntu.

Not only that but I mean using Ubuntu as a development platform, like the term "Windows development" doesn't mean hacking on the Windows source code, it means using Windows as a development environment.

ubuntu-dev-tools does not cover this, which is why the idea is in development. :)

---

