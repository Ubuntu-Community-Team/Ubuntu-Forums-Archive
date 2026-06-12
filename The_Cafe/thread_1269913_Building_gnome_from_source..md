---
title: "Building gnome from source."
date: 2009-09-18
forum: The Cafe
---

### Post by dragos240 on 2009-09-18
I want to see how long it takes, and attempt to use it :p

But where do I get the sources, and what steps should I take?

---

### Post by Tibuda on 2009-09-18
[http://git.gnome.org](http://git.gnome.org)

Good look.

---

### Post by Bachstelze on 2009-09-18
Get gnome-desktop here:

[ftp://ftp.gnome.org/mirror/gnome.org/sources/gnome-desktop/2.26/](ftp://ftp.gnome.org/mirror/gnome.org/sources/gnome-desktop/2.26/)

And follow the README. When you have missing dependencies, build that and try again. See you in a week. :p

---

### Post by kk0sse54 on 2009-09-18
why?

---

### Post by dragos240 on 2009-09-18
> **C!oud said:**
> why?

Why not? ;) Sure, I have a stable version, but I'm going to attempt to run this build version to see if it at all works.

---

### Post by Bachstelze on 2009-09-18
> **C!oud said:**
> why?

> **dragos240 said:**
> I want to see how long it takes, and attempt to use it :p

:<

---

### Post by dragos240 on 2009-09-18
> **Bachstelze said:**
> See you in a week. :p

If I'm successful.
If not, see you in a few months.

---

### Post by phrostbyte on 2009-09-18
[B][U]WARNING: I do not recommend you try this on a production system. Proceed at your own risk.
[/U][/B] 

Build Gnome from source (haven't tested recently):
```
sudo apt-get install gnome-common build-essential doxygen subversion automake1.4 automake1.7 cvs git-core docbook docbook-utils docbook-xsl flex bison texinfo python2.5-dev lynx mono-gmcs libtiff4-dev libxtst-dev libgdbm-dev libxml-simple-perl libelfg0-dev libcupsys2-dev libldap2-dev libexchange-storage1.2-dev libxmu-dev libpam0g-dev libgpgme11-dev libfreetype6-dev libpng12-dev libxrender-dev libxi-dev libexpat1-dev libbz2-dev firefox-dev libxcursor-dev guile-1.8-dev libxdamage-dev libxcomposite-dev libmono-cairo2.0-cil xnest libxft-dev libloudmouth1-0 libloudmouth1-dev libxss-dev libxkbfile-dev gtk-doc-tools libjasper-dev libnl-dev ppp-dev libdv4-dev uuid-dev libpcre3-dev libsqlite3-dev libpurple-dev libcurl4-gnutls-dev libxul-dev libffi-dev liboil0.3-dev
git clone git://git.gnome.org/jhbuild
cd jhbuild
./autogen.sh
make
sudo make install
sudo jhbuild sanitycheck
sudo jhbuild bootstrap
sudo jhbuild build

```

[B][U]WARNING: I do not recommend you try this on a production system. Proceed at your own risk.
[/U][/B]

---

### Post by chris200x9 on 2009-09-18
> **dragos240 said:**
> If I'm successful.
If not, see you in a few months.

what are your specs? When I was running gentoo on a q6600 with 4 gb ram it compiled in like 2 hours :P ( MAKEOPTS="-j5")

---

### Post by dragos240 on 2009-09-18
> **chris200x9 said:**
> what are your specs? When I was running gentoo on a q6600 with 4 gb ram it compiled in like 2 hours :P ( MAKEOPTS="-j5")

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 Network controller: RaLink RT2561/RT61 802.11g PCI
01:06.0 Communication controller: Conexant Systems, Inc. Device 2f40
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)

---

### Post by dragos240 on 2009-09-18
> **phrostbyte said:**
> [B][U]WARNING: I do not recommend you try this on a production system. Proceed at your own risk.
[/U][/B] 

Build Gnome from source (haven't tested recently):
```
sudo apt-get install gnome-common build-essential doxygen subversion automake1.4 automake1.7 cvs git-core docbook docbook-utils docbook-xsl flex bison texinfo python2.5-dev lynx mono-gmcs libtiff4-dev libxtst-dev libgdbm-dev libxml-simple-perl libelfg0-dev libcupsys2-dev libldap2-dev libexchange-storage1.2-dev libxmu-dev libpam0g-dev libgpgme11-dev libfreetype6-dev libpng12-dev libxrender-dev libxi-dev libexpat1-dev libbz2-dev firefox-dev libxcursor-dev guile-1.8-dev libxdamage-dev libxcomposite-dev libmono-cairo2.0-cil xnest libxft-dev libloudmouth1-0 libloudmouth1-dev libxss-dev libxkbfile-dev gtk-doc-tools libjasper-dev libnl-dev ppp-dev libdv4-dev uuid-dev libpcre3-dev libsqlite3-dev libpurple-dev libcurl4-gnutls-dev libxul-dev libffi-dev liboil0.3-dev
git clone git://git.gnome.org/jhbuild
cd jhbuild
./autogen.sh
make
make install
jhbuild sanitycheck
jhbuild bootstrap
jhbuild build

```[B][U]WARNING: I do not recommend you try this on a production system. Proceed at your own risk.
[/U][/B]

You are assuming I am using debian.

---

### Post by phrostbyte on 2009-09-18
> **dragos240 said:**
> You are assuming I am using debian.

The only thing that would be different is the dependencies (the first line). You'll need them to build Gnome.

---

### Post by chris200x9 on 2009-09-18
> **dragos240 said:**
> 00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 Network controller: RaLink RT2561/RT61 802.11g PCI
01:06.0 Communication controller: Conexant Systems, Inc. Device 2f40
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)

...
just your cpu, speed and memory

---

### Post by dragos240 on 2009-09-18
> **chris200x9 said:**
> ...
just your cpu, speed and memory

Sorry, me being lazy. 2gb ram, 64 bit processor. Archlinux.

---

### Post by chris200x9 on 2009-09-18
> **dragos240 said:**
> Sorry, me being lazy. 2gb ram, 64 bit processor. Archlinux.

shouldn't be too bad 64-bit means at least dual core just when you build it make sure you do a MAKEOPTS="-j3" or 2 :popcorn: good luck

---

### Post by CJ Master on 2009-09-18
> **chris200x9 said:**
> shouldn't be too bad 64-bit means at least dual core

False.

---

### Post by chris200x9 on 2009-09-18
> **CJ Master said:**
> False.

yes ok it means you most likely, besides MAKEOPTS="-j2" or 3 would help anyway because it has hyperthreading if single core (unless amd made some single core 64-bit cpu I'm not aware of which may be I'm not a big amd guy)

---

### Post by kk0sse54 on 2009-09-18
> **Bachstelze said:**
> :<

The question is nevertheless still valid.

---

### Post by ~sHyLoCk~ on 2009-09-18
Gnome-meta, i.e. the basic gnome desktop [without even gedit, alacarte,etc.] took me 3hours in my core2duo with -O2 march=prescott mtune=generic -pipe -fomit-frame-pointer , makeopts=-j3 and then after building a few more essential stuffs it took another 2-3hours.

---

### Post by cousinit2 on 2009-09-29
Yep. I'm trying to build the latest GNOME desktop, too. Version 2.28 promises alot of snazzy new things that Karmic won't have if they go with 2.27 :(.

But I'm getting stuck with some dependency issues. Namely libglib2.0-dev. I n00bishly removed this via Synaptic to make way for a newer version as required by gtk+, libunique, and many others, and guess what--they all still scream at me that they can only find GLib version 2.20.1--which is the one I removed, or so I thought.

Any ideas on how to ACTUALLY remove this package and/or replace it with the new one I've built from the GNOME repository?

---

### Post by Exodist on 2009-09-29
> **danielrmt said:**
> [http://git.gnome.org](http://git.gnome.org)

Good look.

+5


Welcome to dependency *HELL!*

---

### Post by CJ Master on 2009-09-29
> **exodist said:**
> 
welcome to dependency *hell!*

+666

---

### Post by itreius on 2009-09-29
Why not just use Gnome from the *gnome-unstable* repo?

Edit: Apologies, didn't see the date on that post :/

---

### Post by FuturePilot on 2009-09-29
> **cousinit2 said:**
> Yep. I'm trying to build the latest GNOME desktop, too. Version 2.28 promises alot of snazzy new things that Karmic won't have if they go with 2.27 :(.

But I'm getting stuck with some dependency issues. Namely libglib2.0-dev. I n00bishly removed this via Synaptic to make way for a newer version as required by gtk+, libunique, and many others, and guess what--they all still scream at me that they can only find GLib version 2.20.1--which is the one I removed, or so I thought.

Any ideas on how to ACTUALLY remove this package and/or replace it with the new one I've built from the GNOME repository?

Karmic has 2.28.

---

### Post by cousinit2 on 2009-09-29
OK. Now I believe everyone. GNOME dependencies are exactly like Windows .DLLs in terms of hellishness.

Gtk+ 2.22 builds and installs fine after adding gnome-devel & all its dependencies. However, libunique still cannot see fit to build itself. The error NOW returns as follows:

```
File "/opt/gnome2/lib64/gobject-introspection/giscanner/transformer.py", line 129, in _find_include
    % (girname, searchdirs))
ValueError: Couldn't find include 'Gtk-2.0.gir' (search path: ['/opt/gnome2/share/gir-1.0', '/opt/gnome2/share/gir-1.0', '/usr/share/gir-1.0', '/opt/gnome2/share/gir-1.0'])
make[4]: *** [Unique-1.0.gir] Error 1
make[3]: *** [all-recursive] Error 1
make[2]: *** [all] Error 2
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2

```

You just try to find the file 'Gtk-2.0.gir' anywhere in the known universe.  gir-repository claims to have it, and also claims to be part of gobject-introspection, but guess what-- they both fail on make with this error: 
```
File "/usr/lib/python2.6/subprocess.py", line 462, in check_call
    raise CalledProcessError(retcode, cmd)
subprocess.CalledProcessError: Command '['/bin/bash', '../libtool', '--mode=link', '--tag=CC', '--silent', 'gcc', '-o', '/home/rtfm/gir-repository-0.6.5/gir/tmp-introspectMGoK4k/DBus-1.0', '-L.', 'libgirepo-DBus-custom.la', '-ldbus-glib-1', '-pthread', '-Wl,--export-dynamic', '-L/usr/local/lib', '-lgio-2.0', '-lgirepository-1.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/home/rtfm/gir-repository-0.6.5/gir/tmp-introspectMGoK4k/DBus-1.0.o']' returned non-zero exit status 1
make[2]: *** [DBus-1.0.gir] Error 1
make[2]: Leaving directory `/home/rtfm/gir-repository-0.6.5/gir'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rtfm/gir-repository-0.6.5'
make: *** [all] Error 2

```

I'm checking python2.6/subprocess.py now, but I have no idea what to do about this error right now.  I'll be very, VERY happy to try most things short of "sudo rm -R /".

Edit: Where was I looking that I saw Karmic had 2.27? Oh, yes I found it here:
[http://www.ubuntu.com/testing/karmic/alpha6](http://www.ubuntu.com/testing/karmic/alpha6)
"Ubuntu Karmic Alpha 6 includes the latest GNOME 2.27.91 development release." I couldn't find a more recent alpha released since September 17, though, so I may be mistaken about that.

---

### Post by jaxxstorm on 2009-09-29
Is there any PPA's for GNOME (I'm going to guess there aren't, but just in case someone knows of one)

---

### Post by directhex on 2009-09-29
> **jaxxstorm said:**
> Is there any PPA's for GNOME (I'm going to guess there aren't, but just in case someone knows of one)

[http://jhdebuild.0d.be/packages.html](http://jhdebuild.0d.be/packages.html) should give you an idea of how many packages would need to be maintained in a PPA to do that

Frankly, nobody bothers, since GNOME releases every 6 months - so when there's a new GNOME release, there's also a new Ubuntu release, and easier to just use that

---

### Post by kevCast on 2009-09-29
Be careful, lest yee lose thy sanity.

---

### Post by PurposeOfReason on 2009-09-29
> **Exodist said:**
> +5


Welcome to dependency *HELL!*

> **CJ Master said:**
> +666
Dependency hell is for the weak and unprepared.

---

### Post by jrusso2 on 2009-09-29
Imagine how glad I was when the distros started to come with KDE instead of having to compile it each time.

Now people want to go back to it.

---

### Post by unknownPoster on 2009-09-29
If one were to judge Gnome and KDE simply by ease and time of compilation, KDE would win every time.

---

### Post by chucky chuckaluck on 2009-09-29
isn't this kind of like making a twinkie from scratch?

---

### Post by cousinit2 on 2009-09-30
So, I've heard "KDE is easier and/or better", "just wait for Ubuntu", and "you should have been prepared/this is a pointless exercise." 

I am of the mind that this is a worthwhile task, if only for the experience of compiling a large & complex UI.  Waiting for the Ubuntu staff to do it all is just putting the burden entirely on them. KDE may be good at some things, but GNOME, in my short experience, is both better and more commonly used. The nice thing about Ubuntu is that you have that choice. I choose GNOME. I'm paying the price, I know. This is why I would like some help from the Ubuntu forums and fellow users who can contribute by sharing what they know about building GNOME.

That being said, I'm still working on getting [FONT="Courier New"]libunique[/FONT] to build properly. There are some people on the Chinese Ubuntu forums that have hit on the same problem and are trying to fix it by compiling the [FONT="Courier New"]gobject-introspection[/FONT] package. This package, in turn, wants the [FONT="Courier New"]gjs[/FONT] package, that wants the latest version of SpiderMonkey from mozilla. Why it needs this, I have no idea.

So now it seems that, to get [FONT="Courier New"]libunique[/FONT] working, I need to compile and install:
1. [FONT="Courier New"]gobject-introspection[/FONT]
2. [FONT="Courier New"]gjs[/FONT]
3. [FONT="Courier New"]libmozjs-dev[/FONT] and [FONT="Courier New"]libidl-dev[/FONT], both a part of [FONT="Courier New"]xulrunner[/FONT].

Clear as mud. Now I find that [FONT="Courier New"]xulrunner[/FONT] requires the Java SDK and java binaries to make properly, so I'm working on getting that. This is the next domino, I guess.

---

### Post by Mr. Picklesworth on 2009-09-30
Doesn't jhbuild handle all this for you?

---

### Post by Bachstelze on 2009-09-30
> **Mr. Picklesworth said:**
> Doesn't jhbuild handle all this for you?

Yes but the dude is an Arch user. You don't want to mess with him, he knows.

---

### Post by dragos240 on 2009-09-30
> **Bachstelze said:**
> Yes but the dude is an Arch user. You don't want to mess with him, he knows.

I got a strange error. It couldn't find the .jhbuilgrc or something.

---

### Post by PurposeOfReason on 2009-09-30
> **Bachstelze said:**
> Yes but the dude is an Arch user. You don't want to mess with him, he knows.
Thanks for getting soda all over my keyboard.

---

### Post by dragos240 on 2009-09-30
> **PurposeOfReason said:**
> Thanks for getting soda all over my keyboard.

What type of keyboard?

---

### Post by PurposeOfReason on 2009-09-30
> **dragos240 said:**
> What type of keyboard?
[http://www.newegg.com/Product/Product.aspx?Item=N82E16823102003](http://www.newegg.com/Product/Product.aspx?Item=N82E16823102003)

I love it to death, somewhat hard to keep clean but it's got good enough tactile response for me.

---

### Post by dragos240 on 2009-09-30
Nice keyboard.

---

### Post by xorg112 on 2009-09-30
Use [Abs.]("http://wiki.archlinux.org/index.php/ABS")  Normally the best way to compile things from source in Arch.
To do that automatically you could use the [Pacbuilder]("http://aur.archlinux.org/packages.php?ID=17216")

---

### Post by dragos240 on 2009-09-30
> **xorg112 said:**
> Use [Abs.]("http://wiki.archlinux.org/index.php/ABS")  Normally the best way to compile things from source in Arch.
To do that automatically you could use the [Pacbuilder]("http://aur.archlinux.org/packages.php?ID=17216")

Thanks :)

---

### Post by cousinit2 on 2009-09-30
OK so I got the [FONT="Courier New"]libunique[/FONT] package to build successfully. I couldn't find a solution anywhere else, so I'll just post what worked for me.
[FONT="Courier New"]libunique[/FONT] needed a file named 'gtk-2.0.gir' that it couldn't find. The [FONT="Courier New"]gir-repository[/FONT] and [FONT="Courier New"]gobject-introspection[/FONT] packages had this file, but they won't build without [FONT="Courier New"]gjs[/FONT]. The [FONT="Courier New"]gjs[/FONT] package, in turn, wants the file 'libmozjs.so' that is in the [FONT="Courier New"]xulrunner[/FONT] package, and [FONT="Courier New"]xulrunner[/FONT] requires a current install of the Java SDK (JDK).

Lucky for me the Ubuntu repositories happen to have the current release of JDK available:
```
sudo apt-get install sun-java6-jdk
```

Now here's where it got "fun and interesting". Even after installing JDK, the [FONT="Courier New"]xulrunner[/FONT] "./configure" couldn't find it. So I edited the configure file like so:

```
JAVA_HOME=
# Check for the Java home directory, if not explicitly set it here
if test "${JAVA_HOME}" = ""; then
  JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.16/"
fi
```

I added this code just above the section JAVA_INCLUDE_PATH in the configure file, and [FONT="Courier New"]xulrunner[/FONT] builds and installs just fine, IF you use this code I found [here]("http://avidemux.org/admWiki/index.php?title=Compile_SpiderMonkey"):
```
./configure \
--enable-application=standalone \
--disable-mailnews \
--disable-ldap \
--disable-gnomevfs \
--disable-gnomeui \
--disable-jsd \
--disable-plugins \
--disable-oji \
--disable-view-source \
--disable-accessibility \
--disable-jsloader \
--disable-composer \
--disable-postscript \
--disable-xtf \
--disable-xpfe-components \
--disable-xpinstall \
--disable-xprint \
--disable-xpcom-obsolete \
--disable-mathml \
--disable-installer \
--disable-updater \
--disable-activex \
--disable-activex-scripting \
--disable-xul \
--disable-profilesharing \
--disable-profilelocking \
--disable-necko-disk-cache \
--disable-cookies \
--disable-v1-string-abi \
make
```
 A quick copy of 'libmozjs.so' to the /usr/lib/ folder and we're back to building [FONT="Courier New"]gjs[/FONT]:
```
sudo cp /usr/lib/xulrunner-1.9.1.3/libmozjs.so /usr/lib/
```

However, [FONT="Courier New"]gjs[/FONT] still could not build. I looked in Ubuntu's repositories again and again got lucky. Searching 'xulrunner-js' turned up these packages likely to help:
```
 sudo apt-get install xulrunner-1.9 xulrunner-1.9-dev xulrunner-dev mozilla-js-debugger 
 xulrunner-1.9.1 xulrunner-1.9.1-gnome-support xulrunner-1.9-gnome-support
```

After installing these packages, [FONT="Courier New"]gjs[/FONT] builds successfully, as does [FONT="Courier New"]gobject-introspection[/FONT]. [FONT="Courier New"]gir-repository[/FONT] still failed, but since I had the files from [FONT="Courier New"]gobject-introspection[/FONT] I didn't have to bother building it anymore.

At this point, re-attempting to build [FONT="Courier New"]libunique[/FONT] failed with the same error as before--'gtk-2.0.gir' not found. A search for this file showed that it was in /usr/share/gir. [FONT="Courier New"]libunique[/FONT]'s Makefile was looking in /usr/local/share/gir-1.0. All I had to do was edit the Makefile and change
```
INTROSPECTION_GIRDIR = /usr/local/share/gir-1.0
```
to:
```
INTROSPECTION_GIRDIR = /usr/local/share/gir
```
and [FONT="Courier New"]libunique[/FONT] builds with warnings, but otherwise installs just fine!

Guess I should be more careful of what experiences I wish for. Gee, it only took two days, four different repositories, 12 other packages, and two hacks to get this thing working, what's next? :)

---

### Post by Tipped OuT on 2009-09-30
What's the point of building GNOME from source? Is it just something else to learn and know?

---

### Post by cousinit2 on 2009-10-01
"Why climb a mountain?"
"Because it's there"
--George Mallory

Those who question why are often found far behind those who question how.

---

### Post by dragos240 on 2009-10-01
When I'm bored, I compile things.

---

### Post by RiceMonster on 2009-10-01
> **dragos240 said:**
> When I'm bored, I compile things.

I think you need a hobby, or you should go out more.

---

### Post by dragos240 on 2009-10-01
True. I do :p

---

### Post by unknownPoster on 2009-10-01
> **Bachstelze said:**
> Yes but the dude is an Arch user. You don't want to mess with him, he knows.

It's an unfortunate attitude that many new Ubuntu to Arch/Gentoo/Slackware converts decide to take. It's quite depressing when you think about it.

---

### Post by cousinit2 on 2009-10-01
But compiling things is fun! :lolflag:
Admit it: there's nothing quite like the feeling that you're creating something from scratch. It's the same feeling you get from rebuilding a car engine--when everything is put together and that baby fires up, you're pumped!
C'mon, who here hasn't worked on some project and thrilled at it's successful completion? Show me this man, and I'll show you a man who has never lived.

---

### Post by dragos240 on 2009-10-01
> **cousinit2 said:**
> But compiling things is fun! :lolflag:
Admit it: there's nothing quite like the feeling that you're creating something from scratch. It's the same feeling you get from rebuilding a car engine--when everything is put together and that baby fires up, you're pumped!
C'mon, who here hasn't worked on some project and thrilled at it's successful completion? Show me this man, and I'll show you a man who has never lived.

+1

Like, I just spent a few hours compiling firefox.

---

### Post by Exodist on 2009-10-01
> **chris200x9 said:**
> yes ok it means you most likely, besides MAKEOPTS="-j2" or 3 would help anyway because it has hyperthreading if single core (unless amd made some single core 64-bit cpu I'm not aware of which may be I'm not a big amd guy)

AMD has made tons of Single Core 64bit chips. I have had 3 or 4 of them.

---

### Post by PurposeOfReason on 2009-10-01
> **dragos240 said:**
> +1

Like, I just spent a few hours compiling firefox.
Hours? You did something wrong. Firefox should take no time to compile, xulrunner shouldn't even take more than an hour with your system.

---

### Post by dragos240 on 2009-10-01
I need to resize my swap, I have 580 mb of swap. 1 GB of ram. This is on my netbook.

---

### Post by PurposeOfReason on 2009-10-01
> **dragos240 said:**
> I need to resize my swap, I have 580 mb of swap. 1 GB of ram. This is on my netbook.
14 and you have a main computer, a server, and a netbook? Damn, I didn't even have my own computer when I was that age.

---

### Post by dragos240 on 2009-10-01
My netbook IS my server. Well. Was.

---

### Post by RiceMonster on 2009-10-01
> **PurposeOfReason said:**
> 14 and you have a main computer, a server, and a netbook? Damn, I didn't even have my own computer when I was that age.

Yeah, I didn't have my own computer until I was 18. I shared a computer with the family up until then.

---

### Post by cousinit2 on 2009-10-06
> **dragos240 said:**
> My netbook IS my server. Well. Was.

+5 Linux usage

Sometimes it's good to have a compact little server handy. I have a couple of larger ones just laying around going to waste because they use too much power to be cost-effective anymore. Well, that and I have no need for a server at the moment... :lol:

---

### Post by bergqvistjl on 2009-10-21
once its actually been downloaded and compiled etc to the opt/gnome2 directory. How do you actually run it?

---

