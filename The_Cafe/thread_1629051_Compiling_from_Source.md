---
title: "Compiling from Source"
date: 2010-11-23
forum: The Cafe
---

### Post by Oxwivi on 2010-11-23
Tell me everything about it.

---

### Post by Swagman on 2010-11-23
It's possible !!

---

### Post by Spice Weasel on 2010-11-23
It's a hell of a lot easier than most people seem to think, most of the time it just takes two commands (and sometimes googling for an error message to see which lib you need).

---

### Post by Oxwivi on 2010-11-23
Yeah, I did tried it myself. I just want to know all the issues and everything about it.

---

### Post by LowSky on 2010-11-23
> **Oxwivi said:**
> Yeah, I did tried it myself. I just want to know all the issues and everything about it.

um... ok?

if you compile from source you need to know all dependencies beforehand are taken care of. If they are not the app may not install correctly or not run. Compiled applications may run a bit quicker do to being set up for the equipment they will run on and not a generic setup that pre-made packages are made for.

---

### Post by Oxwivi on 2010-11-23
Will there be problems of compiling the same thing on different distro?

And dependencies of compilation tools or the software/package?

---

### Post by Spice Weasel on 2010-11-23
There won't be problems on other distros unless the filesystem layout is different (like GoboLinux) or some libraries or dependencies of the program you are compiling are missing.

---

### Post by cariboo on 2010-11-23
Compiling from source can be easy, or it can be a big pain in the derrier. If you are trying to compile bleeding edge stuff, you can go days, or even weeks before you get a successful compile. Have a look at [the gnome-shell]("http://ubuntuforums.org/showthread.php?t=1603874") thread, for an example of a program that is a large problem for a lot of folks.

---

### Post by Oxwivi on 2010-11-23
How does filesystem affect compiling?

---

### Post by Oxwivi on 2010-11-23
What is the problem with compiling gnome-shell?

---

### Post by Oxwivi on 2010-11-23
Oh, and does different software compilation need different tools, possibly?

---

### Post by I'mGeorge on 2010-11-23
First of all source folders, which contains the data that needs to be compiled, usually comes as a tar.gz archive.Compiling from source could be something really tedious when you wanna install a software with a lot of dependencies, 'cause you have to find every one of them,if you don't have them already installed, but the process itself it's easy and not that hard to understand.
In the classic way it resumes to 2 or 3 commands executed inside the source folder    
```

./configure
make
make install (optional)

```
There are of course some other ways to compile from source, using scons for example. 

I strongly recommend for the file browsers to be compiled from source 'cause they perform a little bit faster, but the thing it's generally speaking, compiling from source ain't something for those without a lot of patience.  

Another thing about compiling from sources it's that you have to keep your source folder, 'cause you need it if you wanna uninstall the compiled software later. If you don't keep it, uninstalling a compiled from source software can also be something really annoying as you would have to remove the program manually, and in linux this ain't something really practical.

---

### Post by cariboo on 2010-11-23
> **Oxwivi said:**
> What is the problem with compiling gnome-shell?

Read the thread.

---

### Post by Spice Weasel on 2010-11-23
> **Oxwivi said:**
> How does filesystem affect compiling?

The program you are compiling has instructions to send files to /usr/share/.

What if /usr doesn't exist, and instead there is /System, /Programs and /Shared (for example in GoboLinux)?

---

### Post by Simian Man on 2010-11-23
> **LowSky said:**
> Compiled applications may run a bit quicker do to being set up for the equipment they will run on and not a generic setup that pre-made packages are made for.
That is almost never the case in practice.

> **Spice Weasel said:**
> The program you are compiling has instructions to send files to /usr/share/.

What if /usr doesn't exist, and instead there is /System, /Programs and /Shared (for example in GoboLinux)?
Actually GoboLinux uses symlinks to map standard locations to there file layout, so even that shouldn't cause problems.

---

### Post by forrestcupp on 2010-11-23
> **LowSky said:**
> Compiled applications may run a bit quicker do to being set up for the equipment they will run on and not a generic setup that pre-made packages are made for.Sometimes you have to set the right flags for it to be optimized for your system, or it will just end up running the same as the generic pre-made packages.

> **Oxwivi said:**
> How does filesystem affect compiling?Different distros use different directory structures.  If you compile it in one distro and move it to another, it may look for the dependencies in the wrong place.

---

### Post by Oxwivi on 2010-11-23
> **I'mGeorge said:**
> Another thing about compiling from sources it's that you have to keep your source folder, 'cause you need it if you wanna uninstall the compiled software later. If you don't keep it, uninstalling a compiled from source software can also be something really annoying as you would have to remove the program manually, and in linux this ain't something really practical.
Why would I need the source files to uninstall? Please elaborate.

---

### Post by Barrucadu on 2010-11-23
You need to keep the makefile (and possibly some other things) around so you can uninstall the software, as it wont be tracked by the package manager. Unless, of course, you built a package for it.

---

### Post by odiseo77 on 2010-11-23
To the OP: to avoid the need of keeping the sources directory (and for practical reasons), you can install checkinstall and execute ***checkinstall -D*** as root (instead of "make install"); it will generate a .deb package from the compiled program that you can cleanly and easily uninstall later with dpkg, aptitude, synaptic, or any other package manager.

---

### Post by Oxwivi on 2010-11-23
Thanks for the tip, odiseo77. But I'm looking to learn of all the issues concerning GNU/Linux in general, not just Ubuntu.

---

### Post by Paqman on 2010-11-23
Keep in mind that on a system with a package manager like Ubuntu's APT, compiling from source can sometimes be bad idea. This is because packages compiled from source disregard the complicated system of dependencies that the package manager maintains. This can lead to instability.

Generally speaking, it's better to stick to software from the repos unless something just isn't available. Even then PPAs or .deb files are a better option than compiling from source.

---

### Post by I'mGeorge on 2010-11-23
> **Oxwivi said:**
> Why would I need the source files to uninstall? Please elaborate.

so you could run the command 
```

make uninstall

```

if you don't keep it the usual OS package manager would not know how to uninstall it as it doesn't has the paths to where the software's several data files were installed. Of course for Debian/Ubuntu as already suggested you could use checkinstall -D instead of make install so synaptic would track your data. You could also make a deb (rpm)package out of a source dir, but that ain't really a practical thing to do, but if you want to find more about it cache this out [http://www.quietearth.us/articles/2006/08/16/Building-deb-package-from-source](http://www.quietearth.us/articles/2006/08/16/Building-deb-package-from-source)    

By the way don't give too much credit to those that say all the time compiled from source software works better. This it's only in theory in practice ain't that much of a big deal difference. But anyway I would still recommend the use of a compiled from source file manager, a lightweight one so it would perform as faster as it could being as compatible as it should :-)

---

### Post by sandyd on 2010-11-23
The only real good things about compiling from source are

a) add extra/weird options to the program that were not in the distribution's binaries

b) ensure library compatability

c) get newest software.

If your looking to get the newest software and expecting yourself to compile a lot of packages, go for Gentoo Linux.

---

### Post by forrestcupp on 2010-11-23
> **sandyd said:**
> The only real good things about compiling from source are

a) add extra/weird options to the program that were not in the distribution's binaries

b) ensure library compatability

c) get newest software.

If your looking to get the newest software and expecting yourself to compile a lot of packages, go for Gentoo Linux.
Good advice.  The only reason I think is good enough is for the very rare program you might find out there that doesn't have a package already built for it.  Most of the time, even for the newest software, there's someone out there putting out the package pretty quickly.

How's the baby and your husband/brother? :)

---

### Post by Oxwivi on 2010-11-24
Library compatibility? May ask for more details?

Oh, and forrestcupp, I think it's better for your sake and the one you're talking to, to keep personal matters in PM. :)

---

### Post by forrestcupp on 2010-11-24
> **Oxwivi said:**
> 
Oh, and forrestcupp, I think it's better for your sake and the one you're talking to, to keep personal matters in PM. :)

It was just a joke based on another discussion a while back. :)

---

### Post by Oxwivi on 2010-11-24
> **forrestcupp said:**
> It was just a joke based on another discussion a while back. :)
I know that, I remember you asking about something similar to sandyd in his/her thread, though I don't remember what the thread was about or your question.

---

### Post by Shining Arcanine on 2010-11-24
> **Oxwivi said:**
> Tell me everything about it.

I use Gentoo Linux. Take your pick:

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)
[http://www.gentoo.org/](http://www.gentoo.org/)
[http://www.slackware.com/](http://www.slackware.com/)

---

### Post by sandyd on 2010-11-24
> **forrestcupp said:**
> <snip>

How's the baby and your husband/brother? :)
great!
contrary to what my friends said, raising a baby is actually fun, even though she apparently won't let let either of us go further 1m away from her :P

and it turns out that one of the problems I was anticipating was actually not one at all (I was worried about my american eskimo, but it seems that teaching her to stay away from the baby was easier than I thought)

---

### Post by sandyd on 2010-11-24
> **Oxwivi said:**
> Library compatibility? May ask for more details?

**Oh, and forrestcupp, I think it's better for your sake and the one you're talking to, to keep personal matters in PM. :)**

it was announced publicly in my 'getting married' thread. I giggle like mad each time I hear it now :)

---

### Post by Oxwivi on 2010-12-05
May I ask again what is library compatibility?

---

