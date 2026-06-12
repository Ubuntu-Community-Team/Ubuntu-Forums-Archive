---
title: "MonoDevelop 1.0 is out!"
date: 2008-03-15
forum: The Cafe
---

### Post by Mr. Picklesworth on 2008-03-15
Hooray! Since its last stable release, MonoDevelop has turned into a really nice all-round IDE, good for way more than just Mono.

Finally the stable 1.0 release is out. I highly recommend playing with it.
[http://monodevelop.org/MonoDevelop_1.0_Released](http://monodevelop.org/MonoDevelop_1.0_Released)
It can be argued that Anjuta also does this stuff, but MonoDevelop has an absolutely top-notch interface where everything feels very clean and consistent. It also doesn't crash every five minutes like a lot of IDEs do, and the "integrated" part is very true thanks to its nicely written Addons system.

I like that MonoDevelop puts its focus on actual editing features, and most extensions have a direct impact on the code or actual compilation parameters, or specifically use information that is readily available via the core parts of an IDE. It is not simply an attempt to have everything to do with software development kept within the same window. (In fact, most of the extra addons I use are kind enough to create their own windows!). This is a nice contrast to a lot of IDEs which think it sufficient to pile in Glade and a terminal, then call the job done. Those are not IDEs; those are miniature window managers.

I'll be playing with this final release a bit more closely soon, but I think it's safe to say I have a new favourite development environment.

---

### Post by klange on 2008-03-15
I was waiting for a new MonoDevelop release. I'm competing in a programming competition in April and they only allow the MS bullcrap languages.

---

### Post by forrestcupp on 2008-03-15
can it do c++?

---

### Post by bruce89 on 2008-03-15
> **forrestcupp said:**
> can it do c++?

This was supposed to be the things for 1.0, and indeed it is the case.

---

### Post by The Fiddler on 2008-03-16
Has anyone managed to build Monodevelop 1.0 from source?

I built mono 1.9 and monodevelop 1.0 (note: needs gtk-sharp 2.10, not 2.8!), but when I try to run it, I get the following message:

"MonoDevelop failed to start. The following error has been reported: The required addin 'MonoDevelop.SourceEditor,1.0.0' is not installed."

It looks like a dll conflict. I tried clearing the install and config directories, but nothing helps. Any ideas?

Edit: Forgot to mention I'm on Ubuntu 7.10 (x86_64).

---

### Post by jargs on 2008-03-16
is there a form editor for visual basic?

edit: Just found out the answer to my question: no :(

---

### Post by NiceGuyUK on 2008-03-16
If anyone can do an idiots guide to getting MonoDevelop 1.0 installed and running on 7.10, I'd appreciate it.

I wish they'd go the extra mile and package it up nicely - I'd rather get on with C# coding than spending the day battling with dependencies.

---

### Post by The Fiddler on 2008-03-16
I wonder why there are no mono/monodevelop updates available on synaptic. Mono 1.2.4 and Monodevelop 0.14 are *way* too outdated, unstable and buggy.

It looks like Ubuntu 8.04 will ship with an outdated Mono runtime too (1.2.6 instead of 1.9) - which is even stranger seeing that Hardy will ship with a beta/RC version of *Firefox*. Will we have to wait another 8 months before we can finally use Mono 1.9 or 2.0 on Ubuntu?

Is this due to a lack of interest, a policy against Mono updates or is it something else entirely?

---

### Post by tiggerthump on 2008-03-16
I'm sure it'll just be that mono and ubuntu development is out of sync.

---

### Post by Mr. Picklesworth on 2008-03-16
This is not really foolproof (entirely untested), but this may help to install it:

-Get MonoDevelop and mono-addins-3.0 sources from the Downloads page.

-Make sure you have the build dependencies. Seemed to work for me just using apt-get build-dep monodevelop libmono-addins0.2-cil, even though it is tad out of date. Keep an eye on error messages to see what else you may need. It wants some extra packages for gtksourceview, which I grabbed by going into Synaptic, searching for "gtk source view" and installing everything related that wasn't installed. (Most importantly, probably, libgtksourceview-dev).

-First install mono-addins using the usual steps (./configure --prefix=/usr ; make ; sudo make install). Watch for any errors outputted by the configure script.

-Now build MonoDevelop with ./configure --prefix=/usr followed by make. There is no need to install it, as you can simply run it from where it is with "make run".

-To quickly run it (if you choose not to use "make install"), you can create a launcher with this as its command: make -C '/path/to/monodevelop-1.0' run


Oooh, I just realized the version of Anjuta I have is way behind! Anjuta 2.4.0 is swell. Miraculous compared to 2.2! It must be the year of the Linux IDE :P

---

### Post by The Fiddler on 2008-03-16
Is it really a good idea to install the updated versions in /usr? Several guides mentioned you should install to /usr/local - not entirely sure why, but it seems it has something to do with keeping the ability to make dist-upgrade in the future.

I more or less followed the steps above, but rebuilt everything from source (completely removed mono through apt-get first). I followed the steps outlined [here](http://www.monodevelop.com/Download), but used the latest packages available from [mono-project.com](http://go-mono.com/sources-stable/).

It looks like Monodevelop 1.0 needs GTK# 2.10.x and will not work with GTK# 2.8.x (keep this in mind if you get errors compiling). It also looks like monodoc compilation is braindead: you'll have to copy the mcs/ folder from mono-1.9/ into monodoc/, else it will not build.

These are the steps I followed for each package:
```

$ tar -xvf [package-name]
$ cd [package-name]
$ ./configure --prefix=/usr/local
$ make
$ sudo make install
$ cd ..

```

I built the packages in the following order:
```

1. libgdiplus
2. mono
3. mono-addins
4. gtk-sharp
5. gtksourceview-sharp
6. monodoc
7. monodevelop

```

GDI+ needs libtiff4, libpng12, libgif and libjpeg. Mono (step 2) relies on bison. Packages 4 and 5 have native dependencies (gtk and gtksourceview respectively), so make sure you apt-get those.

If anything fails while compiling, make sure you are using the latest packages everywhere, and check ./configure for missing dependencies.

Unfortunately, after building and installing everything I wasn't able to launch Monodevelop:
"MonoDevelop failed to start. The following error has been reported: The required addin 'MonoDevelop.SourceEditor,1.0.0' is not installed."

It looks like this error has to do with old versions lying around, but I haven't been able to find a solution yet.

Any ideas?

---

### Post by Mr. Picklesworth on 2008-03-16
Ooops, good point. Thanks, Mr Fiddler.
Indeed, /usr/local would be the sensible place.

Weird that it's working for me. Granted, my Ubuntu installation has enough applications from outside repos to sink a ship. (It will be interesting to see how the upgrade holds up).

---

### Post by rickatnight11 on 2008-03-19
You guides have been great.  Everything builds just fine except for monodevelop 1.0.  It says that mono-addins wasn't found, but I know I built and installed it with the commands you listed above.

---

### Post by mikalh on 2008-03-19
> **The Fiddler said:**
> Is it really a good idea to install the updated versions in /usr? Several guides mentioned you should install to /usr/local - not entirely sure why, but it seems it has something to do with keeping the ability to make dist-upgrade in the future.

It's fine to install MonoDevelop in /usr/local. and indeed /usr/local is generally where you should install things you build yourself. However, you're likely to run into weird Mono problems if you have a Mono in /usr/local and a Mono in /usr. And if you install directly into /usr, you mayl run into problems when the package manager upgrades things.

[http://mjhutchinson.com/journal/2007/11/08/how_not_break_mono](http://mjhutchinson.com/journal/2007/11/08/how_not_break_mono)

A better bet might be to get the Debian packages (when they're available), tweak the dependency version, and build them on Ubuntu. Until then, i'd recommend a parallel install.

---

### Post by HDave on 2008-03-24
Have any of you gotten all the way through getting mono 1.9 and monodevelop 1.0 up and running on Gutsy?

I'm a mono newbie and could really use a step by step guide.  I was going to download the source and compile, but there are over 25 source packages on the mono web site...Yikes!!

[http://go-mono.com/sources-stable/]("http://go-mono.com/sources-stable/")

---

### Post by Tagallo on 2008-03-24
> **HDave said:**
> Have any of you gotten all the way through getting mono 1.9 and monodevelop 1.0 up and running on Gutsy?

I'm a mono newbie and could really use a step by step guide.  I was going to download the source and compile, but there are over 25 source packages on the mono web site...Yikes!!

[http://go-mono.com/sources-stable/]("http://go-mono.com/sources-stable/")

Me too...

I wanna try mono, but the version in repos is too old, and the compilation is too hard: there is no clear indication what packages I need to compile... And I really don't like to compile things myself in Ubuntu, thats why I don't use Slackware anymore.

---

### Post by Mateo on 2008-03-24
does it do ruby yet?

---

### Post by cprofitt on 2008-03-24
> **WindowsSucks said:**
> I was waiting for a new MonoDevelop release. I'm competing in a programming competition in April and they only allow the MS bullcrap languages.
 
Man...
 
I gotta be honest... I am going to be switching soon to Linux for development, but Microsoft has done a good job with their IDE for people who like them.
 
As far as waiting on Mono -- if you run Windows you can download free 'express' editions for programming. They also have a special program that they just announced for students / faculty... I can't find a link right now.

---

### Post by rickatnight11 on 2008-03-24
[Microsoft DreamSpark]("https://downloads.channel8.msdn.com/")

---

### Post by cprofitt on 2008-03-24
> **rickatnight11 said:**
> [Microsoft DreamSpark]("https://downloads.channel8.msdn.com/")
 
+1 you had it -- thanks.

---

### Post by jcornwall on 2008-03-26
> **The Fiddler said:**
> Unfortunately, after building and installing everything I wasn't able to launch Monodevelop:
"MonoDevelop failed to start. The following error has been reported: The required addin 'MonoDevelop.SourceEditor,1.0.0' is not installed."

It looks like this error has to do with old versions lying around, but I haven't been able to find a solution yet.

Any ideas?
Try deleting $HOME/.config/MonoDevelop/addin*. (Not a clever place for its configuration files, I might add. Took me ages to find them!)

Thanks for putting this short build guide together. Needed quite a few additional development packages to get the configure scripts to give nods to all the major features, but it was easy enough to do. Also had to grab gtksourceview2-sharp from Mono's Subversion repository because MonoDevelop 1.0 wouldn't build correctly without it.

I'm really getting into Mono and C#, but Ubuntu's outdated packages in Gutsy and Hardy were a disappointment. Now I can play with the latest and greatest releases. :KS

---

### Post by DerPflanz on 2008-03-28
I tried all kinds of things (compiling, apt-getting, compiling again, changing the order of compiling), and I got monodevelop to build, but it didn't run. Bailed out with some cryptic exception.

Is there any repository that has monodevelop running for Ubuntu 7.10? I stopped using Slackware because I got sick of this build-dependency-try-again-compile-nonsense.

---

### Post by GenuineXP on 2008-03-30
I simply cannot get this to work. I've been using RC1 for some time now but have noticed a few bugs I'm hoping are fixed in 1.0 (including two bugs that lead to the IDE crashing). I'm really excited about this release, but can't get it running!

I've tried the steps above posted by Fiddler, but I can't even compile GDI+! It complains about glib-2 not being installed despite the fact I've installed a bunch of glib-2 packages with apt-get. How can I fix this?

```
checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.2.3) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

Any ideas? Note that I've completed removed Mono and all Mono applications.

Is there *ever* gonna be a DEB package? That would be a dream. I can't seem to find any detailed guides for compiling that include troubleshooting tips either. If anyone knows where a comprehensive guide is, please post!

Also, if someone *has* gotten this to work, please attempt to create a DEB package.

---

### Post by bwhite82 on 2008-03-30
I need a .deb package for Gutsy. I found one for hardy in this repo:

deb [http://ppa.launchpad.net/damoxc/ubuntu/](http://ppa.launchpad.net/damoxc/ubuntu/) hardy main

---

### Post by jcornwall on 2008-03-30
> **GenuineXP said:**
> checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.2.3) were not met:

No package 'glib-2.0' found
Make sure you've installed libglib2.0-dev.

---

### Post by GenuineXP on 2008-03-30
Wow! Somehow I managed to build everything from source and get MonoDevelop running. :)

I pretty much followed Fiddler's instructions, but the order of the packages I installed was slightly different due to dependency errors I got. I also installed a bunch of development libraries so that optional builds were marked as "yes". One exception was the Gtk SourceView 2.0 when building MonoDevelop last, which I couldn't seem to enable even after installed development packages.

I've created a GUI C# test project without a problem. I haven't installed VB support for Mono, so I'm guessing creating a new VB project wouldn't work.

It's a shame though... I just had HD problems and will be installing a new drive soon! All of this is for naught, I guess! :P In the meantime, does anyone have links to a guide for packaging binaries? I think it would be really convenient to DEB all of this stuff.

---

### Post by herorev on 2008-03-31
Why is this so difficult? I've installed lots of software through binary installers, source, etc, and I've never had trouble like this. It seems like somebody must have screwed something up somewhere.

---

### Post by qwerion on 2008-03-31
(subscribing to this thread)

---

### Post by randomstuff on 2008-03-31
In the meantime, don't forget to vote for this idea on ubuntu brainstorm.

[[IMG]http://brainstorm.ubuntu.com/idea/4846/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/4846/)

---

### Post by rickatnight11 on 2008-03-31
Great link; voted.

---

### Post by HDave on 2008-04-01
Somebody has put together a debian package for monodevelop 1.0.  I found it over on the [Debian]("http://packages.debian.org/unstable/devel/monodevelop") website.

However it is complaining about a half dozen dependencies not being satisfied and I don't know how to take it from here.   Anyone?

---

### Post by bigj2632 on 2008-04-08
Yall know that Hardy has monodevelop 1.0 in the repos.  But for some reason they are still using an older mono

---

### Post by rickatnight11 on 2008-04-08
Great info.  Hopefully they'll have that updated soon.

---

