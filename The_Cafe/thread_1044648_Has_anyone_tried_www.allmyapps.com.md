---
title: "Has anyone tried www.allmyapps.com?"
date: 2009-01-19
forum: The Cafe
---

### Post by SonicSteve on 2009-01-19
I just found it, I don't know how many of you know of it or how long it's been around. 

[http://www.allmyapps.com/](http://www.allmyapps.com/)

While I haven't let it install any apps for me yet I did click on an app to see what would happen. Well... it started the synaptic install process, asked for my password etc. I didn't give it my password and canceled the install, but it seems interesting.

Is it secure, is there a way for this site to sniff the password or install extra behind your back during the install of the app you chose?

I may seem paranoid but the web is not a safe place these days. Has anyone tried this and what do you think? Does it have a place, does it offer more than the normal Applications>add/remove interface?

---

### Post by thegreenblob on 2009-01-19
Any time I click install my browser freezes and I get the "Stop Script" popup. lol.

But I did look at the script it's trying to run when installing an app. It seems to be a standard apt:// link. So it *should* be safe to use. But everything you can get there you can get in synaptic by your self :)

---

### Post by FuturePilot on 2009-01-19
Yes it's just a bunch of apt-url links. So it doesn't offer anything more than what's in the Ubuntu repos, because that's where it's pulling everything from. And yeah, something is wrong with their javascript because it keeps making Firefox popup the Unresponsive Scrip dialog.

---

### Post by SonicSteve on 2009-01-19
I know this is a dumb question to ask but... are you using no-script? The site works for me. I just haven't let it install yet.

---

### Post by Joeb454 on 2009-01-19
Looks like apt:// links as stated above.

[http://appnr.com](http://appnr.com) is a similar thing :)

---

### Post by Paul Miller on 2009-01-19
So, basically, this site doesn't have anything more than you can get just by running synaptic, right?

---

### Post by Joeb454 on 2009-01-19
> **Paul Miller said:**
> So, basically, this site doesn't have anything more than you can get just by running synaptic, right?

Pretty much, it's just a nice web-based front end to it with pretty logo's :)

---

### Post by Thirtysixway on 2009-01-19
Needs screenshots imo

---

### Post by SonicSteve on 2009-01-19
> **Joeb454 said:**
> Looks like apt:// links as stated above.

[http://appnr.com](http://appnr.com) is a similar thing :)


After seeing appnr.com I'd say it offers the better package list. Though allmyapps.com offers better searching choices with the expandable tree / catagory view on the left.

---

### Post by thibs on 2009-01-20
Hello, I'm one of the 2 guys behind allmyapps. I'm glad someone posted about it here! Thank you for your comments:
@SonicSteve -> the process of installation is completely secure as it is handled locally. It is your system who ask for your administrative password and apt that fetches and installs packages from the official ubuntu repositories. So there's absolutely no risks.
@thegreenblob @FuturePilot -> this was definitely not intended :/ Can you tell me more about the webbrowser you're using and with which extensions ? I've never seen it happen so I wonder what causes it! If you have any ideas, please let me know...
@Thirtysixway -> I cannot agree more! Screenshots are coming :) At first, I tried to have a script running in a WM to automatically take screenshots but the results were not to good so we will add them manually, it will be a lot nicer!
@Joeb454 -> we're definitely is the same spirit as appnr. But I think we try to focus more on usability though... It is also true that, compared to appnr, we only make official ubuntu repositories available yet but we working on adding more repositories. The only thing is that we would like to come up with a method that is user-friendly and secure for the user to add these repositories. We'd like as much as possible to avoid him typing command lines. We'll see if you can work that out.. any idea is welcome by the way :)

Now to tell a bit more about the project (I should blog about it soon if I can find some time). The main idea is to innovate in terms of user interface to help newcomers (read: with a limited or inexistent linux knowledge) search and install new applications. This is why we took a special care in creating the categories (replicating the default application menu), implementing a search feature that is both powerful and relevant... We like to see it as a web powered synaptic on steroids! For more advanced users, it is also a fun way to explore the ubuntu repositories :)

Now, I agree the project is still very young (we've put the first version online only ~2 weeks ago) but we will be adding new features on a regular basis! I don't know if any of you will be at FOSDEM in february but I'll be there so, if you're interested, it could a good opportunity to discuss more about the project around a real life beer!

---

### Post by thibs on 2009-01-20
I fixed the bug with the infinite loop... it was such an enormous and trivial bug (forgot the i++ in the while loop!) that I'm ashamed. I don't even understand how it could have worked before! Sorry for this... I promised to myself never to rush a release anymore.

---

### Post by SonicSteve on 2009-01-20
Thibs,
It's nice to hear from you. I hope the next thing you try to implement are things like; Medibuntu
Codecs

I know there are likely more things to add but those are my current wish list items.

---

### Post by Mr. Picklesworth on 2009-01-20
> Sorry but your system is not (yet) supported...

allmyapps currently supports systems based on:

    * Ubuntu Linux 8.04 (Hardy Heron)
    * Ubuntu Linux 8.10 (Intrepid Ibex)I am using 8.10, with the Epiphany web browser.

UserAgent reliance for the lose.

The site looks good, though. It would be cool if, in the future, it hosted different types of packages (eg: for Suse and Fedora) under that same interface... which, judging by the operating system check, looks like it may be the case.


Edit:
Woah, I love their feedback form! It's working in the exact opposite direction of any other I've seen, but somehow feels way more natural. First it asks for the description, then a title (which really helps to get sensible titles), then what kind of information you have just submitted... and it doesn't bother you with email and login information until the last page, since the actual feedback is the important part.
Awesome.

---

### Post by billgoldberg on 2009-01-20
Those sites are useless, use your package manager.

---

### Post by Mr. Picklesworth on 2009-01-20
> **billgoldberg said:**
> Those sites are useless, use your package manager.

This is using the package manager. It's essentially a glorified gnome-app-install, with apt: links.

And even if it wasn't, that's what deb files are for. There is absolutely nothing wrong with downloading a lone debian package outside of a repository, just so long as its packagers know what they are doing. The package is still completely managed by the package system.
I do it for Crossover all the time.

The repositories are there as a resource to resolve dependencies and it definitely helps to count on them where possible, especially for low level stuff where there are multiple applications relying on the same packages. However, it is completely acceptable -- and in fact often necessary -- to distribute high level applications in a simpler way.

---

### Post by billgoldberg on 2009-01-20
[QUOTE=Mr. Picklesworth;6585373]This is using the package manager. It's essentially a glorified gnome-app-install, with apt: links.

And even if it wasn't, that's what deb files are for. There is absolutely nothing wrong with downloading a lone debian package outside of a repository, just so long as its packagers know what they are doing. The package is still completely managed by the package system.
I do it for Crossover all the time.
/QUOTE]

I know it's using apt:url that's why I make the comment.

That site doesn't have .deb packages.

---

### Post by SonicSteve on 2009-01-20
> **billgoldberg said:**
> Those sites are useless, use your package manager.


Where a site like this can be useful will be adding in extra apps that aren't in the repos, such as medibuntu, although  I now how to add the medibuntu sources and install their stuff I can see an appeal to having easier access to it.  
If it could install a game that is only available as source, that would be nice also. Some of the best looking games can also be some of the most difficult to get working. If something like this could be done it may just find a niche.

---

### Post by doorknob60 on 2009-01-21
> Sorry but your system is not (yet) supported...

allmyapps currently supports systems based on:

    * Ubuntu Linux 8.04 (Hardy Heron)
    * Ubuntu Linux 8.10 (Intrepid Ibex)



"Find and install the best Linux applications!" Linux =/= Ubuntu

---

### Post by Endolith on 2009-09-13
> **Paul Miller said:**
> So, basically, this site doesn't have anything more than you can get just by running synaptic, right?

They've pretty much made AptURL as confusing as possible, haven't they?  A window just pops up out of nowhere and asks to install software.  Here's my proposal for improving it, but it's been pretty ignored:

[https://bugs.launchpad.net/apturl/+bug/325358](https://bugs.launchpad.net/apturl/+bug/325358)

> **billgoldberg said:**
> Those sites are useless, use your package manager.

Actually, they're better than the package manager, because they load faster, show screenshots, and the search actually works.  :D  Funny how the web can do something that open source programmers can't.

---

### Post by Mustard on 2009-09-13
An interesting project.  I hope it goes well. :)

---

### Post by tanyeun on 2011-03-22
interesting project++

although I mostly use deb / apt / buil from src

but this will be definitely a catch for newbies

---

