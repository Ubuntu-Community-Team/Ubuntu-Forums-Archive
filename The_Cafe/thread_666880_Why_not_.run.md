---
title: "Why not .run"
date: 2008-01-13
forum: The Cafe
---

### Post by swoll1980 on 2008-01-13
I just installed an enemy territory .run file and I don't think it could have gotten any easier than that. Everybody says Linux needs a universal installer. It doesn't seem 
like that big of an issue after using the .run installer. What are these people crying about

---

### Post by brennydoogles on 2008-01-13
I would say that you could potentially do really bad things with a poorly made .run file, whereas a .deb installer pretty much only adds files to your current configuration. Also, I would say that .run files would require that someone write a fairly complicated script (open up your .run for enemy territory in a text editor... you'll see what I mean), whereas a .deb or a .rpm can even be generated automatically by programs such as autodeb or checkinstall. Does that make any sense??

---

### Post by sumguy231 on 2008-01-13
The .run file is just a script that the software vendor made, not a packaging standard. I imagine having each software vendor write their own installer would both put too much effort on the vendor and make a mess of most systems.

---

### Post by ~LoKe on 2008-01-13
The .run file just **starts** the installer.

---

### Post by hhhhhx on 2008-01-13
i think if everyone starts using .run's then .run wil be the new .exe .  The main reason i use linux is that there are billions of options and you get to choose what you want. :)

---

### Post by Polygon on 2008-01-14
a run file is just a script, and a deb file is essentially a script, AND keeps track of where each file goes, so its can be easily upgraded, or removed.

---

### Post by swoll1980 on 2008-01-14
why can't all parts of a program be kept in the same folder?

---

### Post by ssam on 2008-01-14
> **bloor75 said:**
> why can't all parts of a program be kept in the same folder?

they can. try gobolinux

---

### Post by swoll1980 on 2008-01-14
gobolinux?

---

### Post by mali2297 on 2008-01-14
> **bloor75 said:**
> gobolinux?
An alternative distro...
[http://www.gobolinux.org/](http://www.gobolinux.org/)

> 
What is GoboLinux?

GoboLinux is a modular Linux distribution: it organizes the programs in your system in a new, logical way. Instead of having parts of a program thrown at /usr/bin, other parts at /etc and yet more parts thrown at /usr/share/something/or/another, each program gets its own directory tree, keeping them all neatly separated and allowing you to see everything that's installed in the system and which files belong to which programs in a simple and obvious way.


---

### Post by argie on 2008-01-14
Yes, it's a distro that does the things you want + manages to share the libraries. It also rearranges the file system hierarchy so you have folders like Programs, Libraries and stuff like that instead of /bin /lib though it does make symlinks to ensure that stuff that doesn't conform to the way they do things will still work.

Oh, and it also changes the root user to gobo instead of root.

EDIT: Nuts, too slow.

---

### Post by conehead77 on 2008-01-14
> **argie said:**
> Oh, and it also changes the root user to gobo instead of root.

Well, *thats* a feature :D

---

### Post by Polygon on 2008-01-14
> **bloor75 said:**
> why can't all parts of a program be kept in the same folder?

even mac programs have config files and other files that get strewn across the filesystem.

---

### Post by Mr. Picklesworth on 2008-01-14
Those script installers strikes me as a very bad idea, since they generally do not even have a means of uninstalling.

I think any alternative to .deb should be a standardized "easy" way of building from source involving a small configuration file and a special file type. Building from source is really a great way of doing things, and already fairly consistent thanks to the prevalent use of "make" and easy availability of build tools in modern distros. However, we currently lack an easy and consistent "one-click" way to do it for users who simply want to install a program.

As for placement of apps, I think the Filesystem Hierarchy Standard is fantastic for important system-level tools, servers and desktop environments. Anything that strives to be integrated. It is really just with less important software like games that we start to see a problem. Games are a nice example because they rarely borrow media from anywhere else for the sake of consistency. Similarly, since games also rarely borrow media from each other (exception being mods), it does not make sense for that stuff to be shared in /usr/share.

I think that is where /opt comes in. Apps under /opt can get away with that type of arrangement without getting in anything else's way. In addition, expansions and the like - tailored specifically to that one game - can easily find each other.

---

### Post by swoll1980 on 2008-01-14
Anyone try gobo yet?

---

### Post by lisati on 2008-01-14
> **bloor75 said:**
> why can't all parts of a program be kept in the same folder?

> **ssam said:**
> they can. try gobolinux

Kinda makes sense to keep things together, and not touching system folders if you don't have to. Doing so can make life a lot easier (and safer) if you need to clean up after a bad install or some other such problem.

---

### Post by forrestcupp on 2008-01-14
> **Mr. Picklesworth said:**
> Those script installers strikes me as a very bad idea, since they generally do not even have a means of uninstalling.
Usually programs installed from a .run file are just totally installed to a directory in /home.  So you can just delete the directory and not worry about it.

I kind of like it, myself.

---

### Post by swoll1980 on 2008-01-14
Thats what the enemy territory installer did

---

