---
title: "MonoDevelop 2.2 Beta 1:  release"
date: 2009-09-11
forum: The Cafe
---

### Post by argor on 2009-09-11
MonoDevelop 2.2 Beta 1:  release
for info go here [http://tirania.org/blog/archive/2009/Sep-09.html](http://tirania.org/blog/archive/2009/Sep-09.html)

---

### Post by ukblacknight on 2009-09-12
Does anyone know if there is a .deb release for this?

Why the hell MonoDevelop 2.0 is in the Ubuntu repo's I will *never* know, I have never used anything that is so unstable!  Want to put a menubar into your gtk project?  MD will crash.  Want to save your project? MD will crash.  Want to put some actions on your buttons? MD will crash.

I've tried compiling MD Beta 2.2 from the anon svn, however it keeps asking me for dependencies and I'm getting tired of it.

Whilst I'm on my rant - when compiling and a dependency is required, why doesn't it just fetch and install the dependency?  Or at least provide the exact package name so we can easily find it and install it. :confused:

---

### Post by Colonel Kilkenny on 2009-09-12
Perhaps "sudo apt-get build-dep monodevelop" helps.

---

### Post by ukblacknight on 2009-09-12
I just ran that now, however it didn't help me :(

The message I'm getting is:

```

Checking for package 'gecko-sharp-2.0'.. ERROR: Package named 'gecko-sharp-2.0' >= 0.10 not found.

```

I've looked in synaptic and can't seem to find anything related.

---

### Post by argor on 2009-09-12
> **ukblacknight said:**
> Does anyone know if there is a .deb release for this?

Why the hell MonoDevelop 2.0 is in the Ubuntu repo's I will *never* know, I have never used anything that is so unstable!  Want to put a menubar into your gtk project?  MD will crash.  Want to save your project? MD will crash.  Want to put some actions on your buttons? MD will crash.



well for me MonoDevelop 2.0 is very staple for me but MonoDevelop 1 did crash sometimes

---

### Post by ukblacknight on 2009-09-12
> **argor said:**
> well for me MonoDevelop 2.0 is very staple for me but MonoDevelop 1 did crash sometimes

It's terrible for me, such a shame, because it seems to be a very capable IDE.  There is a bug report for it where others experience the issues I do, and it is confirmed, so I hope that 2.2 addresses these problems.

---

### Post by yabbadabbadont on 2009-09-12
> **ukblacknight said:**
> I just ran that now, however it didn't help me :(

The message I'm getting is:

```

Checking for package 'gecko-sharp-2.0'.. ERROR: Package named 'gecko-sharp-2.0' >= 0.10 not found.

```

I've looked in synaptic and can't seem to find anything related.

Your search-fu is weak...  :D

```
/home/daffy $ aptitude show libgecko2.0-cil 
Package: libgecko2.0-cil
State: not installed
Version: 0.13-1ubuntu4
Priority: optional
Section: universe/libs
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 258k
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libgcc1 (>= 1:4.1.1), libglib2.0-0
         (>= 2.16.0), libgtk2.0-0 (>= 2.15.0), libpango1.0-0 (>= 1.22.0), libstdc++6 (>= 4.1.1), zlib1g (>= 1:1.1.4), cli-common (>= 0.5.1), libglib2.0-cil
         (>= 2.12.7), libgtk2.0-cil (>= 2.12.7), libmono-corlib2.0-cil (>= 1.2.2.1), xulrunner-1.9
Description: CLI binding for the GtkMozEmbed library, unstable version
 This package provides assemblies that allow CLI (.NET) programs to use the GtkMozEmbed library.

```

---

### Post by phrostbyte on 2009-09-12
If you do you use this, please report any bugs you encounter to Novell's Bugzilla.

---

### Post by ukblacknight on 2009-09-12
> **yabbadabbadont said:**
> Your search-fu is weak...  :D

```
/home/daffy $ aptitude show libgecko2.0-cil 
Package: libgecko2.0-cil
State: not installed
Version: 0.13-1ubuntu4
Priority: optional
Section: universe/libs
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 258k
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libgcc1 (>= 1:4.1.1), libglib2.0-0
         (>= 2.16.0), libgtk2.0-0 (>= 2.15.0), libpango1.0-0 (>= 1.22.0), libstdc++6 (>= 4.1.1), zlib1g (>= 1:1.1.4), cli-common (>= 0.5.1), libglib2.0-cil
         (>= 2.12.7), libgtk2.0-cil (>= 2.12.7), libmono-corlib2.0-cil (>= 1.2.2.1), xulrunner-1.9
Description: CLI binding for the GtkMozEmbed library, unstable version
 This package provides assemblies that allow CLI (.NET) programs to use the GtkMozEmbed library.

```

Excellent!  So now I've installed that, and it's asking me for 'mono-addins' >= 0.5.  Will need to root around for that now... and compile that :P

The joys of compiling from source... would be nice to just... drop a package into a package manager and it would get all dependencies, compile it and install it!

---

### Post by directhex on 2009-09-12
Patience is a virtue.

---

### Post by yabbadabbadont on 2009-09-12
> **ukblacknight said:**
> Excellent!  So now I've installed that, and it's asking me for 'mono-addins' >= 0.5.  Will need to root around for that now... and compile that :P

The joys of compiling from source... would be nice to just... drop a package into a package manager and it would get all dependencies, compile it and install it!

I laugh at your search-fu.  My Dragon style conquers all!  :D

```
/home/daffy $ aptitude search -- "-cil" | grep addin
p   libmono-addins-gui0.2-cil       - GTK# frontend library for Mono.Addins     
p   libmono-addins0.2-cil           - addin framework for extensible CLI applica

```
Basically, most mono related packages have "-cil" in the name.

---

### Post by ukblacknight on 2009-09-12
> **yabbadabbadont said:**
> I laugh at your search-fu.  My Dragon style conquers all!  :D

```
/home/daffy $ aptitude search -- "-cil" | grep addin
p   libmono-addins-gui0.2-cil       - GTK# frontend library for Mono.Addins     
p   libmono-addins0.2-cil           - addin framework for extensible CLI applica

```
Basically, most mono related packages have "-cil" in the name.

Been there done that - they're out of date :P

---

### Post by directhex on 2009-09-12
[http://svn.debian.org/wsvn/pkg-cli-apps/packages/monodevelop/trunk/debian/changelog](http://svn.debian.org/wsvn/pkg-cli-apps/packages/monodevelop/trunk/debian/changelog)

dum de dum

---

### Post by Frak on 2009-09-12
I'm building new versions of Mono and MonoDevelop and plan on uploading them to my PPA later.

---

### Post by Jimleko211 on 2009-09-12
Monodevelop is a fine IDE, but I can't stand the mono platform...every GTK# object I try to use I can't use it because the documentation is lacking in helpfullness, and the calls are just like..."how the hell do I display a message?"

Mono would be a lot better if it, honestly, attempted to be a clone of .NET, not just something like it that's compatible.

---

### Post by Frak on 2009-09-12
> **Jimleko211 said:**
> Monodevelop is a fine IDE, but I can't stand the mono platform...every GTK# object I try to use I can't use it because the documentation is lacking in helpfullness, and the calls are just like..."how the hell do I display a message?"

Mono would be a lot better if it, honestly, attempted to be a clone of .NET, not just something like it that's compatible.
Amen

---

### Post by ukblacknight on 2009-09-13
> **Frak said:**
> I'm building new versions of Mono and MonoDevelop and plan on uploading them to my PPA later.

Great :D  I'll be using that then, instead of trying to find these dependencies!

---

### Post by directhex on 2009-09-13
> **Frak said:**
> I'm building new versions of Mono and MonoDevelop and plan on uploading them to my PPA later.

That totals about 15 source packages

Why would you do such a thing independently of the package's maintainers? Why do all the work & auditing required patching, then have the package's maintainers duplicate that work? Why not cooperate?

---

### Post by Frak on 2009-09-13
> **directhex said:**
> That totals about 15 source packages

Why would you do such a thing independently of the package's maintainers? Why do all the work & auditing required patching, then have the package's maintainers duplicate that work? Why not cooperate?
Because I hate the packagers. Nuff said.

---

### Post by ukblacknight on 2009-09-13
> **directhex said:**
> That totals about 15 source packages

Why would you do such a thing independently of the package's maintainers? Why do all the work & auditing required patching, then have the package's maintainers duplicate that work? Why not cooperate?

As far as I know, MonoDevelop doesn't have a Ubuntu, Debian or Fedora package for its Beta build.  Seems strange not creating a package for the most popular distro's.  How hard can it be to simply provide a package for them?

---

### Post by directhex on 2009-09-13
> **ukblacknight said:**
> As far as I know, MonoDevelop doesn't have a Ubuntu, Debian or Fedora package for its Beta build.  Seems strange not creating a package for the most popular distro's.  How hard can it be to simply provide a package for them?

Pretty hard. Not every distro arranges its packages in the same way, and patching is often needed to better integrate into a distro

---

### Post by NeonRush on 2009-09-17
Hi Frak, I'm not a huge help asker out here, but I was really curious if you managed to package the new monodevelop source? I've been trying to compile it myself for a few days now and all I've managed to do is hose my old mono stuff. Any help would make you my savior. Thanks

---

### Post by Mateo on 2009-09-17
so... does it debug again yet?

---

### Post by Frak on 2009-09-18
> **NeonRush said:**
> Hi Frak, I'm not a huge help asker out here, but I was really curious if you managed to package the new monodevelop source? I've been trying to compile it myself for a few days now and all I've managed to do is hose my old mono stuff. Any help would make you my savior. Thanks
No, I haven't. When it builds, the binary is unusable.

---

### Post by directhex on 2009-09-18
> **NeonRush said:**
> Hi Frak, I'm not a huge help asker out here, but I was really curious if you managed to package the new monodevelop source? I've been trying to compile it myself for a few days now and all I've managed to do is hose my old mono stuff. Any help would make you my savior. Thanks

I did it back on the same day Frak announced his insurgency, but I like to have my work double-checked before exposing it to the public.

---

### Post by ukblacknight on 2009-09-18
> **NeonRush said:**
> Hi Frak, I'm not a huge help asker out here, but I was really curious if you managed to package the new monodevelop source? I've been trying to compile it myself for a few days now and all I've managed to do is hose my old mono stuff. Any help would make you my savior. Thanks

When I tried compiling my own, it kinda damaged my mono stuff too.  When I start Banshee, it crashes several times, until about the 5th time it will eventually stay open!

---

### Post by Murrquan on 2009-09-19
> **directhex said:**
> I did it back on the same day Frak announced his insurgency, but I like to have my work double-checked before exposing it to the public.

I look forward to seeing it. ^.^ Especially with the new ability to start Moonlight projects straight from the IDE. Developing Silverlight web games with Free Software FTW!

Oh, and I'm sorry about how they replaced Silverlight with Flash on that one TV website, in your blog. >.>

---

### Post by cb951303 on 2009-10-12
hi jo, whats the status on monodevelop beta packages?
I've take a look on your PPA but it's not there?

---

### Post by directhex on 2009-10-12
> **cb951303 said:**
> hi jo, whats the status on monodevelop beta packages?
I've take a look on your PPA but it's not there?

I forgot about it, truth be told. I've made the change I was asked to make (sorry Murrquan, disabling Moonlight support until we have the required Moonlight SDK in Debian/Ubuntu), so it needs one last double-check before I can upload it to Debian/PPA

---

### Post by cb951303 on 2009-10-12
thanks.

btw, monodoc-browser doesn't work in karmic. any ideas?

---

### Post by Frak on 2009-10-12
> **cb951303 said:**
> thanks.

btw, monodoc-browser doesn't work in karmic. any ideas?
It's broken.

---

### Post by directhex on 2009-10-12
> **cb951303 said:**
> thanks.

btw, monodoc-browser doesn't work in karmic. any ideas?

Working on it.

---

### Post by directhex on 2009-10-12
[http://paste2.org/p/465799](http://paste2.org/p/465799)

4 hours of work for a fix, but it DOES fix it. I'll upload an ubuntu2 package, plus a fix for Debian too.

---

### Post by cb951303 on 2009-10-13
thanks jo, really appreciated.

---

### Post by directhex on 2009-10-13
> **cb951303 said:**
> thanks jo, really appreciated.

Subject: 	[ubuntu/karmic] mono-tools 2.4.2-1ubuntu2 (Accepted)

---

### Post by Brezhonneg on 2009-10-27
Hi directhex,

I see that monodevelop 2.2 beta 2 made it to your PPA. Does it include the version control plugin, or will that be packaged separately?

Thanks!

---

### Post by jaxxstorm on 2009-10-27
I've got a fairly decent grounding in PHP/MySQL and other web technologies, as well as being pretty up to scratch with VB.NET and shell scripting.

How hard would I find it to develop an application with Mono/MonoDevelop?

---

### Post by directhex on 2009-10-27
> **Brezhonneg said:**
> Hi directhex,

I see that monodevelop 2.2 beta 2 made it to your PPA. Does it include the version control plugin, or will that be packaged separately?

Thanks!

monodevelop-versioncontrol is a binary package produced as part of the monodevelop source package.

---

### Post by directhex on 2009-10-27
> **jaxxstorm said:**
> I've got a fairly decent grounding in PHP/MySQL and other web technologies, as well as being pretty up to scratch with VB.NET and shell scripting.

How hard would I find it to develop an application with Mono/MonoDevelop?

Depends on what you want to do. MD has VB.NET support (although no GUI designer for it). Generally, think of it as fully featured for C#, and merely a souped up text editor for other languages

---

### Post by directhex on 2009-10-27
Boo and Python addins still need to be done, btw. Boo addin requires post-Karmic Boo, and Boo is pretty badly behaved when it comes to updates (i.e. need to discuss policy with others before it can happen)

---

### Post by gpnet on 2009-11-12
Hi to all guys.

I am new here. I was reading about having monodevelop 2.2 beta2. I was just looking for that but i didn't find anything for my ubuntu 9.10.

Someone of you mentioned about a package on PPA. Could I have a link to download this package ?

Also I didn't see what mono version package is installed on ubuntu 9.10. Do you think I have to update or install the last version of mono ?
 
Thanks to all.
Joss

---

### Post by Brezhonneg on 2009-11-12
To check what is installed on my system, I like to use dpkg. For instance, you could do 'dpkg -l mono\* | grep ii'. Use the dpkg man page for more info.

If mono is not installed, use apt-get to install it (see apt-get man page for more info).

As for the PPA, here is the link:
[https://launchpad.net/~directhex/+archive/monoxide](https://launchpad.net/~directhex/+archive/monoxide)

You will also find installation instruction on that page.

Hope that helps...

---

### Post by gpnet on 2009-11-12
thank you Brezhonneg now I check with the command you suggest me.

About the monodevolop i check the link you told me , bu it is not for monodevelop but just for mono.
This is not what I was looking for.

Do you have another link ? or this is the only one ?.

Thanks

EDIT :
Sorry , I didn't the filter OS button. Now I see the monodevelop package. Thanks again

---

