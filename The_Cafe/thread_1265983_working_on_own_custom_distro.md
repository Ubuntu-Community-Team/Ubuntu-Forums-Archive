---
title: "working on own custom distro"
date: 2009-09-14
forum: The Cafe
---

### Post by OneLine on 2009-09-14
Hi :KS

I switched to Ubuntu 6 months ago from Windows, and I have to say I'm glad I made the switch.

I am now working on my own custom distro based on ubuntu, I would like to release it at some stage, I was wondering what advice does anyone have for me please

Thanks Very Much :)

---

### Post by schauerlich on 2009-09-14
Make it good.

---

### Post by joey-elijah on 2009-09-14
I'm starting to feel left out; am i the only person who hasn't made my own distro?! 

BTW @ OP: changing the wallpaper and the GTK theme does not a new distro make. Think about applications installed, services etc.

---

### Post by Naiki Muliaina on 2009-09-14
Do something different :) Innovation is yays!

---

### Post by Exodist on 2009-09-14
> **OneLine said:**
> Hi :KS

I switched to Ubuntu 6 months ago from Windows, and I have to say I'm glad I made the switch.

I am now working on my own custom distro based on ubuntu, I would like to release it at some stage, I was wondering what advice does anyone have for me please

Thanks Very Much :)

I am glad to see you have taken a keen interest in Linux and Ubuntu, but what makes you want to produce your own distro other then helping contribute to Ubuntu or another existing distro?

---

### Post by praveesh on 2009-09-14
I have made one with kde 4.3, xbmc media centre, a theme made by me etc. Two best tools are reconstructor and remastersys . But the reconstructor version 2.9 has a serious bug which wipes out every data in the root partition(occurs while customising the kde 4.3 in jaunty) . The version 3 is a web only application. Remastersys is also an awesome tool , but I didn't find a way to change the theme with it.

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-09-14
Add restrictedextras by default please

---

### Post by gjoellee on 2009-09-14
I made an Ubuntu based distro one time. I made it VERY light. I somehow made GNOME run in 71mb RAM, but I lost the ISO so it is discontinued. 

You should do like me. Make something fully featured, not in a lightweight desktop environment, but make it use as little resources as possible. This will result in a fully featured, yet very snappy distro.

---

### Post by OneLine on 2009-09-14
> **Exodist said:**
> I am glad to see you have taken a keen interest in Linux and Ubuntu, but what makes you want to produce your own distro other then helping contribute to Ubuntu or another existing distro?

 I think Ubuntu has grown so big, it's trying to help more or less everyone by bloating the Ubuntu distro, and I have a few ideas of my own, :)  Plus I like to learn as well,  I noticed Linux Mint has it's own repository, could I setup my own for my distro?

---

### Post by megamania on 2009-09-14
> **OneLine said:**
> I think Ubuntu has grown so big, it's trying to help more or less everyone by bloating the Ubuntu distro, and I have a few ideas of my own, :)  
A distro which fits on a cd is definitely not bloated. Pre-installed games and other applications (which I don't like either) aren't bloat.

And if you have a few ideas, why don't you share them?

---

### Post by Tibuda on 2009-09-14
> **OneLine said:**
> I think Ubuntu has grown so big, it's trying to help more or less everyone by bloating the Ubuntu distro, and I have a few ideas of my own, :)  Plus I like to learn as well,  I noticed Linux Mint has it's own repository, could I setup my own for my distro?

Yes. Move a lot of deb files to a folder, and run this command in that folder:
```
dpkg-scanpackages ./ /dev/null | gzip > Packages.gz
```
It will create a Packages.gz file in that folder. Upload it and all your deb files to a HTTP server, and you got an APT repository.

To see how to set up a repository using Dropbox, see [http://wiki.getdropbox.com/TipsAndTricks/HostDebRepository](http://wiki.getdropbox.com/TipsAndTricks/HostDebRepository)

---

### Post by XubuRoxMySox on 2009-09-14
Too many Ubuntu-based distros already IMO, and too many of them duplicate each other's goals.

I made my own "remix" too but I won't release it as a "distro." It's just my own little custom minimal Ubuntu with the LXDE desktop, codecs, and favorite apps. There are a half-dozen "distros" that are almost exactly like it. The best of them is probably [Masonux]("http://sites.google.com/site/masonux/"). 

I really think it's far more beneficial for the entire Linux/Ubuntu community to contribute to the existing Ubuntu/Debian base than it is to add yet another "distro" to the confusing and overcrowded field of duplicates.

This "distro duplication" phenomenon was even the subject of [a recent rant]("http://robinzrantz.xanga.com/711717546/more-on-lightweight-linux/") on my blog. Customize your Ubuntu like everyone else, share your results with friends and neighbors, but give back to the community whose years of hard work has made it possible! Let's make Ubuntu better instead of taking their work and releasing it as an alternative to Ubuntu.

Just my opinion,
Robin

---

### Post by OneLine on 2009-09-14
> **dixiedancer said:**
> Too many Ubuntu-based distros already IMO, and too many of them duplicate each other's goals.

I made my own &quot;remix&quot; too but I won't release it as a &quot;distro.&quot; It's just my own little custom minimal Ubuntu with the LXDE desktop, codecs, and favorite apps. There are a half-dozen &quot;distros&quot; that are almost exactly like it. The best of them is probably [Masonux]("http://sites.google.com/site/masonux/"). 

I really think it's far more beneficial for the entire Linux/Ubuntu community to contribute to the existing Ubuntu/Debian base than it is to add yet another &quot;distro&quot; to the confusing and overcrowded field of duplicates.

This &quot;distro duplication&quot; phenomenon was even the subject of [a recent rant]("http://robinzrantz.xanga.com/711717546/more-on-lightweight-linux/") on my blog. Customize your Ubuntu like everyone else, share your results with friends and neighbors, but give back to the community whose years of hard work has made it possible! Let's make Ubuntu better instead of taking their work and releasing it as an alternative to Ubuntu.

Just my opinion,
Robin

 Hi, so what your saying is, everyone should use only one distro (i.e. ubuntu) and not any spin-off's of it, so you want to limit people's choice?

---

### Post by petrus4 on 2009-09-14
Things I'd (at least want to, although some of them would be a lot of work) do, if I was going to do it...

Use Ubuntu primarily for its' hardware support, and probably rewrite almost everything else, at least in terms of stuff that I've actually seen.

I'd scrap Upstart, and use the udev/devd and hal/dbus combo that everyone else seems to.  I'd also use a bootscript setup which was more like FreeBSD's.

I'd get rid of the general, Debian-inherited mentality of, "let's change, and render opaque, non-standard, and incompatible, literally everything possible, purely because we can."  That would primarily mean getting rid of Upstart and the non-standard module loading system, as mentioned.

I'd also get rid of the concept of installing several different things which all fundamentally do the same job.  In this case, I'm primarily taking about HAL and udev.  From everything I've ever seen, udev can do everything HAL can do, when used in conjunction with the kernel's own notification.

That would lower complexity, and raise stability, without affecting usability.

If I could figure out how to make it work with the existing hardware detection/symbols system, I'd also scrap the custom module loading scenario/DKMS, and use a less convoluted system based on the conventional module tools.

I'd scrap inclusion of the /media directory.  (Yes, I know about the FHS, and in this case I don't give a crap about it)

Extra partitions/drives would mount in /mnt, like they're supposed to. :P

I'd remove "quiet splash" from the default grub menu.lst, and truthfully I'd like to give a proverbial Three Stooges slap to whichever genius decided to include that option in the first place.  It's the reason why the help forum here gets the usual, "black screen of death," complaints.

All mounted file systems would be given entries in /etc/fstab; even temporary ones where hal had to be told to remove the entry once the device was unmounted.  That way someone could go into the fstab and, if they needed to, be able to see everything that was mounted on the system at once.

I'd dump Gnome.  It's ugly, it's horribly designed, it's deliberately opaque and non-configurable, it's bloated, and it has a dependency list as long as my arm.  I suspect its' affiliation with the cult of the GNU is the only real reason why most people put up with it at all.

If I didn't care about bloat, I'd use KDE, or if I did, I'd use Enlightenment.  If he is smart, Mr Shuttleworth will notice how many downstream Ubuntu derivatives are using E as their own default window manager, and take the hint. :P

I'd create my own metapackage, in order to have all of the usual base toolchain  installed by default, rather than having to add those later.  GCC would also possibly use buffer overflow protection.  Build-essential and Ubuntu's default misses a couple of those.  I'd probably also write my own spec files for dpkg for that metapackage as well, in order to avoid library subpackaging, which I generally don't like.

I'd identify hopefully less than half a dozen other end-user apps for desktop use, (Firefox, Xine for multimedia viewing, OpenOffice, Claws Mail, Pidgin, and Wine) write my own dpkg spec files for those which again would avoid subpackaging, and stick to only those, so that I could keep up with the patches released by those specific projects by themselves, and could patch things more quickly than the repo maintainers could, and thus have a more secure system than Ubuntu's default usually is.

I'd also dump ALSA, and switch back to the new, entirely FOSS version of OSS.

---

### Post by nmccrina on 2009-09-14
> **OneLine said:**
> Hi, so what your saying is, everyone should use only one distro (i.e. ubuntu) and not any spin-off's of it, so you want to limit people's choice?

I don't thinks that's what he's saying at all! If you want choice, you have Fedora, Mandriva, Suse, Arch, etc. etc. etc. These are all very different distros. No need to have a dozen distros all based on Ubuntu; what is really accomplished here that couldn't be done by changing a theme, adding/removing a few applications, or adding/removing repositories?

---

### Post by OneLine on 2009-09-14
> **nmccrina said:**
> I don't thinks that's what he's saying at all! If you want choice, you have Fedora, Mandriva, Suse, Arch, etc. etc. etc. These are all very different distros. No need to have a dozen distros all based on Ubuntu; what is really accomplished here that couldn't be done by changing a theme, adding/removing a few applications, or adding/removing repositories?

 Maybe I should look at this from a different angle, maybe I should write some tutorials on a blog instead?

---

### Post by MarcusW on 2009-09-14
> **OneLine said:**
> Maybe I should look at this from a different angle, maybe I should write some tutorials on a blog instead?

I would agree that's a better idea, or you could try to get your ideas to the Ubuntu devs if you think it'll help. :)

---

### Post by OneLine on 2009-09-14
> **MarcusW said:**
> I would agree that's a better idea  Well this is a turn up for the books, (that was an expression), "/me starts to think from a different angle"  > **MarcusW said:**
> or you could try to get your ideas to the Ubuntu devs if you think it'll help. :)  Do the ubuntu dev's listen to us small people? :)

---

### Post by Sporkman on 2009-09-14
> **OneLine said:**
> Maybe I should look at this from a different angle, maybe I should write some tutorials on a blog instead?

You you can write a "configure ubuntu to be better" script that a user could run after a fresh install, which would make the mods you have in mind.

---

### Post by OneLine on 2009-09-14
> **Sporkman said:**
> You you can write a &quot;configure ubuntu to be better&quot; script that a user could run after a fresh install, which would make the mods you have in mind.

 Thanks, I like the sound of that :)

---

### Post by Tibuda on 2009-09-14
> **OneLine said:**
> Do the ubuntu dev's listen to us small people? :)

Start here: [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

### Post by XubuRoxMySox on 2009-09-14
> **OneLine said:**
> Hi, so what your saying is, everyone should use only one distro (i.e. ubuntu) and not any spin-off's of it, so you want to limit people's choice?

Pft. **Of course not.** All I'm say'n is that too many distros are practically carbon copies of each other, and we just don't need to flood the field with more carbon-copy distros. It's confusing enough already.

I'm *also* say'n that Ubuntu is already so customizable that **anyone can "build their own Ubuntu"** with relative ease, and share it with friends and neighbors and whatever... but to add yet another carbon-copy distro to the already overcrowded and confusing ocean of Ubuntu derivatives is not helpful in the larger picture *in my opinion*. The only difference between Ubuntu and many (but not all) of its spin-off "distros" is a few minutes of time spent adding and removing artwork, themes, desktop environments, and a handful of applications. All things that can be done easily by most casual users of Ubuntu.

I'm certainly not suggesting that everyone use all the same distro and all the same customizations and applications. Nothing I wrote here remotely suggests any such thing.

-Robin

---

### Post by Exodist on 2009-09-14
> **OneLine said:**
> I think Ubuntu has grown so big, it's trying to help more or less everyone by bloating the Ubuntu distro, and I have a few ideas of my own, :)  Plus I like to learn as well,  I noticed Linux Mint has it's own repository, could I setup my own for my distro?

I will admit the kernel is loaded down and is not optimized. But thats why I just compile my own when new one is out and optimize it for my PCs hardware and my needs. 
But having a huge repository is almost endless programs for download without having to hunt for them and/or compile them from scratch just to try something out is priceless. 

Speaking of compiling, I can compile just about anything that isnt screwed up. But wait till you try to compile gnome from scratch. hehe..  There is way to many fingers in that cookie jar and each want their own special cookie recipe.

---

### Post by Sporkman on 2009-09-14
> **OneLine said:**
> Thanks, I like the sound of that :)

We could call it a "post-installation customization", or maybe an "after-distro", or a "quasi-distro".

Also, maybe at each step of the configuration your script does, you can have it print a short explanation of the pros & cons, and let the user select or deselect it.

---

### Post by perspectoff on 2010-05-25
> **Sporkman said:**
> You you can write a "configure ubuntu to be better" script that a user could run after a fresh install, which would make the mods you have in mind.

You mean like:

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

### Post by Sporkman on 2010-05-25
> **perspectoff said:**
> You mean like:

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

No - I mean the user can do a standard installation, then use a script to select & implement the customizations the OP has in mind.

---

