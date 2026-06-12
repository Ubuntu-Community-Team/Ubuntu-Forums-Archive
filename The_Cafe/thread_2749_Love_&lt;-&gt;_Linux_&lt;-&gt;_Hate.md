---
title: "Love &lt;-&gt; Linux &lt;-&gt; Hate"
date: 2004-10-31
forum: The Cafe
---

### Post by HiddenWolf on 2004-10-31
Once, I really really need to make a piont here about my major problem with Linux in general.

What is great, is that there is a lot of choice, however, this makes it very hard to keep the system lean and mean.

Most of the time if you install a package, it needs another package or library. So you install 3, 4, or more packages, then figure out you don't like the program, it's interface, or it doesn't do exactly what you wanted.
Then however, if you uninstall the package, you will still have some, if not most of it's dependancies on your system.
Unless you write down the name of every package you install, there is little chance of ever getting your system as lean as it was before you installed the useless package.

The same goes for programs in general, and especially display managers like Gnome. While I believe it's gotten leaner since, I can still remember fondly my suprize when I found out that Gnome depends on the massive Mozilla suite libraries, but also packed two other browsers, another mail client, two or three irc-clients, and a broad range of other redundant packages.

While I agree browsing/mailing/printing/sound are essential for any desktop, and thus should be required, I would think that it is far better to take one good, (and small) package, in stead of depending on a massive program like Mozilla. 

Isn't the best philosofy here to take one package that most acknowledge to be good, or 'good enough', say Thunderbird for mail, and allow it to be replaced by a more comprehensive suite as Mozilla-mail or Evolution?

Again, here, if I'd have to install them side by side, I'd get unhappy.
IMHO system functions should depend on libraries and small packages, or dummies, not on other packages
This would allow the system more flexibility while still allowing for a lean system..

---

### Post by nuopus on 2004-10-31
[QUOTE=HiddenWolf]Once, I really really need to make a piont here about my major problem with Linux in general.

What is great, is that there is a lot of choice, however, this makes it very hard to keep the system lean and mean.

Most of the time if you install a package, it needs another package or library. So you install 3, 4, or more packages, then figure out you don't like the program, it's interface, or it doesn't do exactly what you wanted.
Then however, if you uninstall the package, you will still have some, if not most of it's dependancies on your system.
Unless you write down the name of every package you install, there is little chance of ever getting your system as lean as it was before you installed the useless package.

The same goes for programs in general, and especially display managers like Gnome. While I believe it's gotten leaner since, I can still remember fondly my suprize when I found out that Gnome depends on the massive Mozilla suite libraries, but also packed two other browsers, another mail client, two or three irc-clients, and a broad range of other redundant packages.

While I agree browsing/mailing/printing/sound are essential for any desktop, and thus should be required, I would think that it is far better to take one good, (and small) package, in stead of depending on a massive program like Mozilla. 

Isn't the best philosofy here to take one package that most acknowledge to be good, or 'good enough', say Thunderbird for mail, and allow it to be replaced by a more comprehensive suite as Mozilla-mail or Evolution?

Again, here, if I'd have to install them side by side, I'd get unhappy.
IMHO system functions should depend on libraries and small packages, or dummies, not on other packages
This would allow the system more flexibility while still allowing for a lean system..[/QUOTE]
 Why don't you just install debfoster? You can run debfoster and say yes to everything at first ... what it is doing is flagging all of the packages you want to keep.

After that, install as many packages as you like! When you run debfoster again it will ask for every package and even groups the dependencies with them (so if you are removing a package it will tell you the package is keeping some dependencies and get rid of those as well).

Whatever you don't say yes to will be removed! Great way of keeping system clean.

---

### Post by danomatika on 2007-01-17
Keep in mind, all of these programs usually depend on the same set of libraries.  There may be 3-4 redundant apps installed, but they don't really take *that* much space.

I just finished switching from Windows XP and noticed quite a difference in size.  Both OS's were/are setup with a C: / root partition and a separate /home partition so  I don't much up myself tooooo quickly.  Here's what I noticed:

Ubuntu with all the apps I need: Little over 4 GB
Windows XP with all the apps I need: at least 8-9 GB

I mean, we are talking MS Visual Studio, .NET, Adobe Premiere, etc ... with each proprietary app including redundant code in a sense the space begins to add up.

Basically, what I mean is that even with all these extra packages you are complaining about ... a Linux installation is still lean and mean.  Keep in mind that with all this power it becomes really easy to get obsessed over mincromanaging your packages ... Jesus Christ, if you have to have 15 MB extra, dont worry about it.

---

### Post by maniacmusician on 2007-01-17
> sudo apt-get autoremove?

---

### Post by meng on 2007-01-17
You could use smarter package management like aptitude to install and remove applications. aptitude will remove the orphaned dependencies for you.

---

### Post by speedwell68 on 2007-01-17
[QUOTE=maniacmusician]sudo apt-get autoremove[/QUOTE]

Worked a treat, 51mb of unused stuff removed from my system, learn something new every day, thanks dude.:mrgreen:

---

### Post by TBOL3 on 2007-01-17
I have an idea.

I like the graphical package list (when looking for a new package, say a game)

But I like aptitude becouse it removes the dependinseas.  So I have to open the terminal.  And  figure out what the magic keyword is.  I would much prefer to just click on install.

---

### Post by Pitbull11188 on 2007-08-12
You could always use

```
sudo apt-cache search 'program or category'
```

to do the same thing. ;)

---

### Post by ubuntu27 on 2007-08-12
> **TBOL3 said:**
> I have an idea.

I like the graphical package list (when looking for a new package, say a game)

But I like aptitude becouse it removes the dependinseas.  So I have to open the terminal.  And  figure out what the magic keyword is.  I would much prefer to just click on install.

```
aptitude search name-of-package
```

---

### Post by starcraft.man on 2007-08-12
Wow, this threads been doubly resurrected and it's three years old. Geez.

Oh, that's about it, nothing else to add.

---

### Post by init1 on 2007-08-12
> **HiddenWolf said:**
> Once, I really really need to make a piont here about my major problem with Linux in general. What is great, is that there is a lot of choice, however, this makes it very hard to keep the system lean and mean. Most of the time if you install a package, it needs another package or library. So you install 3, 4, or more packages, then figure out you don't like the program, it's interface, or it doesn't do exactly what you wanted. Then however, if you uninstall the package, you will still have some, if not most of it's dependancies on your system. Unless you write down the name of every package you install, there is little chance of ever getting your system as lean as it was before you installed the useless package. The same goes for programs in general, and especially display managers like Gnome. While I believe it's gotten leaner since, I can still remember fondly my suprize when I found out that Gnome depe...Don't like apt? Don't use it. Don't like Gnome? Don't use it. There are other options.

---

### Post by @trophy on 2007-08-13
> **nuopus said:**
> Why don't you just install debfoster? You can run debfoster and say yes to everything at first ... what it is doing is flagging all of the packages you want to keep.

After that, install as many packages as you like! When you run debfoster again it will ask for every package and even groups the dependencies with them (so if you are removing a package it will tell you the package is keeping some dependencies and get rid of those as well).

Whatever you don't say yes to will be removed! Great way of keeping system clean.

That sounds like a cool program, but I do find it ironic that the guy is complaining about having too many random packages installed, and the solution offered is to install another one!  Anyway yeah just thought that was funny... nothing more to see here, folks.  Move along.

---

### Post by bapoumba on 2007-08-13
I'm closing here, the OP started this thread, hmm, in October 2004. Couple things have changed since then ;)

---

