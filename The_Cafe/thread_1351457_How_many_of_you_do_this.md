---
title: "How many of you do this?"
date: 2009-12-10
forum: The Cafe
---

### Post by jwbrase on 2009-12-10
Quite a few times, I've come across GPL programs where only the source was available for Linux, but there was a Windows binary. I've compiled from source once or twice, but for every downloaded program I've tried to compile, there's probably two or three that I couldn't seem to get working. So oftentimes I've just downloaded the Windows binaries and run them in Wine. Anyone else do that?

---

### Post by SuperSonic4 on 2009-12-10
Nope, on Kubuntu I compiled from source with ~90% success rate. Those error messages tell you a lot.

Now, however, I just grab them from the AUR

---

### Post by dragos240 on 2009-12-10
> **jwbrase said:**
> Quite a few times, I've come across GPL programs where only the source was available for Linux, but there was a Windows binary. I've compiled from source once or twice, but for every downloaded program I've tried to compile, there's probably two or three that I couldn't seem to get working. So oftentimes I've just downloaded the Windows binaries and run them in Wine. Anyone else do that?

No...... not  really.

---

### Post by NoaHall on 2009-12-10
> **jwbrase said:**
> Quite a few times, I've come across GPL programs where only the source was available for Linux, but there was a Windows binary. I've compiled from source once or twice, but for every downloaded program I've tried to compile, there's probably two or three that I couldn't seem to get working. So oftentimes I've just downloaded the Windows binaries and run them in Wine. Anyone else do that?

No. Never. I never use wine. Never install it, either. Always compile.

---

### Post by ZankerH on 2009-12-10
> **jwbrase said:**
> Quite a few times, I've come across GPL programs where only the source was available for Linux, but there was a Windows binary. I've compiled from source once or twice, but for every downloaded program I've tried to compile, there's probably two or three that I couldn't seem to get working. So oftentimes I've just downloaded the Windows binaries and run them in Wine. Anyone else do that?

I don't use wine, and on the few occasions I had to compile from source in ubuntu, it worked perfectly.

On Arch, which has a much more intuitive and streamlined compiling process, I've had a 100% success rate so far, and I use the AUR a lot.

---

### Post by t0p on 2009-12-10
> **jwbrase said:**
> Quite a few times, I've come across GPL programs where only the source was available for Linux, but there was a Windows binary. I've compiled from source once or twice, but for every downloaded program I've tried to compile, there's probably two or three that I couldn't seem to get working. So oftentimes I've just downloaded the Windows binaries and run them in Wine. Anyone else do that?

Not me.  Generally, I get Linux binaries.  If no Linux binary is available, I tend to look for an alternative program.

I have been known to compile from source; but only smaller utlilities, not a "full scale" application.  I've also been known to use an application that comes only in a Windows binary by running it in a virtual XP in VirtualBox.  But that isn't my usual approach.

---

### Post by gnomeuser on 2009-12-10
I used to do Gentoo and before that Linux From Scratch, I've compiled my fair share of applications.

I find that normally the problems stem from incompatible libraries (say like depending on unreleased code, patched code or outdated code). Aside that there can be problems with incompatible toolchain components.

That being said, failing to compile is common, most distributions have FTBFS (Fails To Build From Source) detection in their buildsystems for a reason. 

You shouldn't be put off by it, most well maintained projects will have packages available and even if you still wish to build your own you know that the dependencies are there and confirmed as working for that version.

---

### Post by squilookle on 2009-12-10
I tend to use binaries, I've compiled one or two things from source, I've had a few that didnt work either cause I didn't bother to read the instructions properly. 

I have Wine installed, but only for Spotify. :)

---

### Post by Physical Hook on 2009-12-10
Haven't used Wine for a while now. Most of the things I have here have been compiled *by hand*.

---

### Post by SuperSonic4 on 2009-12-10
I'm compiling VLC as I'm typing this :popcorn: x264 has already been done

---

### Post by Exodist on 2009-12-10
> **jwbrase said:**
> Quite a few times, I've come across GPL programs where only the source was available for Linux, but there was a Windows binary. I've compiled from source once or twice, but for every downloaded program I've tried to compile, there's probably two or three that I couldn't seem to get working. So oftentimes I've just downloaded the Windows binaries and run them in Wine. Anyone else do that?

**Nope**, unless the source code is screwed up I can get them configured and compiled every time. Watch your config file, it will tell you whats missing or if it requires another version of something needed.

---

### Post by murderslastcrow on 2009-12-10
I used to do this a lot when I was too wimpy to find dependencies for source packages. This is why it's a good idea to package more software for Ubuntu if it has a source package, instead of whining that it's not in there.

PCSX2 and Dolphin emulators are great examples of this. It is by far easier to install them in Wine than compile them in the appropriate fashion, as they're not very well documented.

I think this all comes down to people making half-arsed ports and not taking the time to make deb/rpm packages for distros. I mean, if I made a piece of software that was worth having, I would maintain it at least that much. It's not exactly time-consuming.

Sometimes I run stuff in Wine just for bug testing, though, since it's easier to debug an open source program than a closed one.

---

### Post by HappyFeet on 2009-12-10
I used to geek out and compile some stuff, but as I get older, I have less interest in these things. If it is not in synaptic, available as a PPA, or on getdeb.net, I don't use it. My life has not degraded because I don't compile stuff. 

Btw, I have a drive with XP on it for gaming, and gaming only. I'm done fighting with computers. I have no need for windows, other than the 2 games I play. And even then, it's only once every 2 weeks or so that I play.

---

### Post by phrostbyte on 2009-12-10
But the only issue is dependencies. Arch does kind of make this easier though by bundling header files with every library, something Debian/Ubuntu doesn't (they are in -dev packages).

---

### Post by Ji Ruo on 2009-12-11
> **Physical Hook said:**
> Most of the things I have here have been compiled *by hand*.

Try-hards compile from source. The hardcore use binary, a steady hand and a magnetised needle...

---

### Post by purgatori on 2009-12-11
> **jwbrase said:**
> Quite a few times, I've come across GPL programs where only the source was available for Linux, but there was a Windows binary. I've compiled from source once or twice, but for every downloaded program I've tried to compile, there's probably two or three that I couldn't seem to get working. So oftentimes I've just downloaded the Windows binaries and run them in Wine. Anyone else do that?

No.

---

### Post by ankspo71 on 2009-12-11
Hi,
Yes I have done it before.

There are a few packages that have missing dependencies on my system. I think two of them are openbve and funguloids. There was another program too, but I can't recall the name of it.

Synaptic reports:
> funguloids:
 Depends: ogre-plugins-cgprogrammanager  but it is not installable

> openbve:
  Depends: libtaoframework-openal1.1-cil (<2.0.0.svn20071028) but 2.1.svn20090801-1build1 is to be installed
 Depends: libtaoframework-opengl2.1-cil (>=2.0.0.svn20071027) but it is not installable
 Depends: libtaoframework-opengl2.1-cil (<2.0.0.svn20071028) but it is not installable
  Depends: libtaoframework-sdl1.2-cil (<2.0.0.svn20071028) but 2.1.svn20090801-1build1 is to be installed


funguloids-win32-1.06.exe runs nicley in Wine on my computer (Karmic). I can't compile the linux source files either because of the lack of dependencies.

I haven't tried compiling openbve yet, but your post reminded me to do that, so I am downloading it now. I have about a 95% success rate at compiling from sources.
James

---

### Post by BrokenKingpin on 2009-12-11
Nope, I never use wine. If I absolutely need to use a program that is only for Windows, I just use Windows. As far as compiling programs I have a pretty decent success rate, but for most things I use these days a .deb package is available.

---

### Post by speedwell68 on 2009-12-11
Nope never.  Wine is a cop out.

---

