---
title: "Am I the only one who doesn't understand"
date: 2013-06-15
forum: The Cafe
---

### Post by jokerneophyte on 2013-06-15
why
 - are there device files? or /proc? Do they really make things cleaner?
 - is the directory structure the way it is? Wouldn't it be a __LOT__ cleaner to have /Applications/<name> with binary, config, everything?
 - do we need X11 or any display server? Wouldn't it be better if the desktop environment and the display server was one?

---

### Post by coldraven on 2013-06-16
Someone else has thought the same.
[http://lwn.net/Articles/67196/](http://lwn.net/Articles/67196/)

---

### Post by Copper Bezel on 2013-06-16
> **jokerneophyte said:**
> why
 - are there device files? or /proc? Do they really make things cleaner?
 - is the directory structure the way it is? Wouldn't it be a __LOT__ cleaner to have /Applications/<name> with binary, config, everything?
 - do we need X11 or any display server? Wouldn't it be better if the desktop environment and the display server was one?
Legacy code, backwards compatibility, and levels of abstraction, mostly. The first two are simpler answers, I think.
 
The "everything is a file" conceit has [a Wikipedia page]("http://en.wikipedia.org/wiki/Everything_is_a_file"). I think the purpose is less about keeping things "clean" and more about flexibility. It's a Unix / Posix trait that, I think, allows a variety of interfaces and system tools to access the system instead of requiring a bunch of crazy hooks and things built into the system. I think it's a necessity for (or at least, one method for) having a versatile kernel that various OSs can run on top of. If that stuff wasn't accessed through the filesystem, it'd have to be accessed through some other kind of hook into the kernel, wouldn't it? And that's okay for Windows, where there's only one environment ever run on top of that kernel. 

The [FSH directory structure]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") is pure legacy, I think, and was then set down as a standard for interoperability. There were real reasons to have /bin, /sbin, and /usr/bin as separate directories that may not all be mounted at boot time, and although I don't think most of those things apply to modern systems in typical use, the structure is still there and theoretically doesn't make much difference to end users. 

As for the abstraction between the display server and the desktop environment - well, step back a second there. There's the display server, like X, then there's the window manager, say, Compiz, and then there's the desktop environment, like Gnome. The desktop environment is the set of applications users normally interact with when using the computer, including not just Start menus and desktop wallpapers but file managers and settings screens and processes that apply themes and font rendering standards to applications and the whole bit. Individual processes within that desktop environment can sometimes be replaced with alternatives, and the window manager is really just one of those processes. 

The window manager itself is the process that composites the windows on the screen, draws title bars, and redirects user input (so that the system knows which window you're clicking on and what keyboard layout you're using, for instance, or which keystrokes to intercept for desktop environment purposes.) But both Gnome Shell and Unity bake a lot of the features of the desktop environment straight into the window manager, so that you can't, say, run Gnome with the Openbox window manager (something that was possible until Gnome 3.) Ubuntu uses the Gnome desktop environment but their modified Compiz window manager, and obviously it's a very different interface from the one comes by default with Gnome 3.

So the desktop environment isn't even a single process, anyway, but it's probably a good thing that the display server and the window manager aren't the same process. For instance, if you're using Ubuntu and Compiz crashes for some reason, it can restart itself without crashing all your applications and dropping you back to the login screen. It's also true that a single display server can run more than one window manager when the user wants to switch between them, and the display server provides tools that would be difficult to rebuild from scratch, so it made more sense for window managers and desktop environments to build on top of it.

The X window system itself is ancient and includes a lot of things that modern environments don't use while making a lot of very typical things difficult or clunky to implement, which is why Wayland and Mir are being proposed as alternatives. Mir is an Ubuntu project and written according to Ubuntu's goals, so I imagine it'll be tailored first and foremost to what Compiz / Unity needs while Unity is being written against it. That should improve performance and versatility (for Unity's purposes) while maintaining enough abstraction between the two processes to serve stability purposes. 

In a way, it's similar to how the OS or an application operates on top of the kernel. It can politely request things from the kernel, but can't force the kernel to do something it's not supposed to be doing, so that buggy application code or an unusual situation shouldn't crash the kernel. It's good to have the same kind of abstraction between the display server and an application running on top of it, even when that application is the primary interface to the desktop environment. 

But sticking with the standard still has a lot of advantages that even Ubuntu's developer base is going to have trouble doing without. Not only is it a huge coding task, it requires video drivers that will play nice with the new display server, and Ubuntu does not write those drivers. Some are provided directly by chip manufacturers, which means that either those manufacturers support Mir, or machines that use those chips won't run Mir. If Mir was built into Unity and Unity built into Ubuntu, then Ubuntu simply couldn't run on those machines. 

If you think of Android, which doesn't use a separate display server or the traditional Posix filesystem heirarchy, and then think of all the things that desktop Linux developers have to deal with that don't apply to Android, you more or less have your answer to why desktop Linuxes work the way they do. = )

---

### Post by 3Miro on 2013-06-16
> **jokerneophyte said:**
> why
 - are there device files? or /proc? Do they really make things cleaner?
 - is the directory structure the way it is? Wouldn't it be a __LOT__ cleaner to have /Applications/<name> with binary, config, everything?
 - do we need X11 or any display server? Wouldn't it be better if the desktop environment and the display server was one?

- in Unix based systems everything is a file, your CPU appears as a file in /dev/. This is just the way Unix works.
- in Linux you cannot have /Applications/<name> structure. An application in Linux consists of multiple components that interact with each other. Hence those components are placed in different places so that other applications can easily find them.
- making a display server is a very difficult thing. If every DE had its own server, then one environment wouldn't be able to run applications made for another, also every DE would ave to make their own drivers. Think if X11 as the the graphical kernel. There are ideas to move away from having just one server, but if another one came about then it must somehow allow for X11 applications to run on it.

---

### Post by prodigy_ on 2013-06-16
> **3Miro said:**
> - in Linux you cannot have /Applications/<name> structure.
That's not true. For example it could easily be implemented via symlinks without changing much of the code. The only reason why it doesn't exist is that nobody cares.

---

The directory structure in *NIX is awkward by modern standards. "Everything is a file" and "everything is a stream of bytes" abstractions on the other hand are very convenient especially when you work with CLI and try to automate things. In Windows everything is an object and writing advanced scripts for nontrivial tasks is pure hell.

---

### Post by 3Miro on 2013-06-16
> **prodigy_ said:**
> That's not true. For example it could easily be implemented via symlinks without changing much of the code. The only reason why it doesn't exist is that nobody cares.

---

The directory structure in *NIX is awkward by modern standards. "Everything is a file" and "everything is a stream of bytes" abstractions on the other hand are very convenient especially when you work with CLI and try to automate things. In Windows everything is an object and writing advanced scripts for nontrivial tasks is pure hell.

It is true that you can have another file tree that simply symlinks to the original one, however, many libraries cannot be associated with a single program and there will be a lot of ambiguity. People don't care to implement it because it would not be practical.

IIRC there was a distro that wanted to do just that, however, people weren't particularly excited about it and I don't know the current status of the project (or the name for that matter).

---

### Post by Copper Bezel on 2013-06-16
I remember that, too. I thought it was one of the Mac-alike distributions, and I remember that the filesystem was organized to more or less match OSX's, but it's not any of the obvious ones and I can't find anything about it now.

---

### Post by prodigy_ on 2013-06-16
> **3Miro said:**
> It is true that you can have another file tree that simply symlinks to the original one, however, many libraries cannot be associated with a single program and there will be a lot of ambiguity. People don't care to implement it because it would not be practical.
You don't really need symlinks to libs. They're binaries anyway so who cares what they are and where they are? The useful stuff in a hypothetical /applications/app_name folder would consist of links to the main executable, config files (both permanent and temporary), documentation and config examples - i.e. something you can run, read or edit. Right now it's all scattered between /bin, /usr (which is also a total mess), /etc and /var.

---

### Post by 3Miro on 2013-06-16
> **prodigy_ said:**
> You don't really need symlinks to libs. They're binaries anyway so who cares what they are and where they are? The useful stuff in a hypothetical /applications/app_name folder would consist of links to the main executable, config files (both permanent and temporary), documentation and config examples - i.e. something you can run, read or edit. Right now it's all scattered between /bin, /usr (which is also a total mess), /etc and /var.

Applications usually consist of a single executable file that links to a bunch of external libraries and documentation needs to be done in a way that can be accessed by a third party programs (i.e. man command).

The layout isn't a mess:

bin -> executable binaries
sbin -> executable binaries that should only be available to the system administrator
lib -> shared libraries
etc -> system settings
var -> system log files
home -> personal files and settings, even on windows the user specific settings are in a separate folder

dev and proc -> Unix file abstraction (i.e. devices and processes)

/bin, /sbin and /lib contain only the bare minimum needed to boot the system
/usr/bin, /usr/lib and /usr/sbin contain everything else, so that /usr folder can reside on a separate partition (I think this was a legacy thing)

---

### Post by prodigy_ on 2013-06-16
> **3Miro said:**
> bin -> executable binaries
sbin -> executable binaries that should only be available to the system administrator
lib -> shared libraries
etc -> system settings
var -> system log files
home -> personal files and settings, even on windows the user specific settings are in a separate folder

dev and proc -> Unix file abstraction (i.e. devices and processes)

/bin, /sbin and /lib contain only the bare minimum needed to boot the system
/usr/bin, /usr/lib and /usr/sbin contain everything else, so that /usr folder can reside on a separate partition (I think this was a legacy thing)
Yeah, it's a mess. Your post itself is a perfect illustration to my point.

Worse yet, just because permanent configs are in /etc it doesn't mean you can easily find the one you need. Try to write a script that would be portable at least between major Linux distros. Something networking related for example. Then you'll see what I'm talking about.

---

### Post by ssam on 2013-06-16
[Gobo Linux]("http://www.gobolinux.org/index.php") uses a filesystem layout similar to your proposal.

Fedora are moving all of /bin /lib /share into /usr to simplify things [https://fedoraproject.org/wiki/Features/UsrMove](https://fedoraproject.org/wiki/Features/UsrMove) (though some people complained loudly that they like to keep things separate for various reasons).

But for both of these, there are bunch of symlinks to keep compatibility.

---

### Post by Cheesemill on 2013-06-16
> **ssam said:**
> Fedora are moving all of /bin /lib /share into /usr to simplify things [https://fedoraproject.org/wiki/Features/UsrMove](https://fedoraproject.org/wiki/Features/UsrMove) (though some people complained loudly that they like to keep things separate for various reasons).

Arch have recently gone one step further by consolidating all executables into /usr/bin, the other binary folders (/bin, /usr/sbin and /sbin) are now just symlinks.
[https://mailman.archlinux.org/pipermail/arch-dev-public/2012-March/022625.html](https://mailman.archlinux.org/pipermail/arch-dev-public/2012-March/022625.html)

---

### Post by 3Miro on 2013-06-16
> **prodigy_ said:**
> Yeah, it's a mess. Your post itself is a perfect illustration to my point.

Worse yet, just because permanent configs are in /etc it doesn't mean you can easily find the one you need. Try to write a script that would be portable at least between major Linux distros. Something networking related for example. Then you'll see what I'm talking about.

Every single file has its own logical place, if you understand the logic, you immediately know where to look.

Different distributions use different configuration tools and files, what does this have to do with the Unix file tree.

---
The division between /bin and /usr/bin was done on old systems so /usr can be mounted after boot. On a modern system, there is no real need for that. Hence it makes sense to consolidate everything into either /bin or /usr/bin.

---

### Post by Mr. Picklesworth on 2013-06-16
> **3Miro said:**
> Applications usually consist of a single executable file that links to a bunch of external libraries and documentation needs to be done in a way that can be accessed by a third party programs (i.e. man command).

The layout isn't a mess:

bin -> executable binaries
sbin -> executable binaries that should only be available to the system administrator
lib -> shared libraries
etc -> system settings
var -> system log files
home -> personal files and settings, even on windows the user specific settings are in a separate folder

dev and proc -> Unix file abstraction (i.e. devices and processes)

/bin, /sbin and /lib contain only the bare minimum needed to boot the system
/usr/bin, /usr/lib and /usr/sbin contain everything else, so that /usr folder can reside on a separate partition (I think this was a legacy thing)

When we're talking about *applications*, it's more like this:

/opt/MyApp: your application's executable and data files go here
/usr/bin: or, if you want it on $PATH or something, your executable can go here
/usr/share/MyApp: you can also put your data files here (but you might want to pack them into your executable with [GResource]("https://developer.gnome.org/gio/2.32/gio-GResource.html"))

That was the slightly hairy bit.

/usr/share/applications: [application metadata / launchers]("http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html")
/usr/share/icons: [icons]("http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html")
/usr/share/mime: [mime types for files and directories]("http://standards.freedesktop.org/shared-mime-info-spec/shared-mime-info-spec-latest.html")
/etc/xdg/autostart: [application autostart entries]("http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html")

Those are pretty well all the things you might, on another system, have inside /Applications/MyApp - it's just we put them in the system folders, themselves, and we keep track of the files for each application by using a package system.

Of course, a weird and crazy application might come with a cron job (/etc/cron.d), or a boot script or an extra package repository, but those are uncommon. I think there are some movements afoot to package applications in a special kind of way (keeping in mind the specific sorts of hooks applications use), but at least when we think of it in terms of the specific standards (rather than giant folders that could contain all manner of things!) it's a bit easier to manage. We let the standards sort out amongst themselves what /etc and /usr mean.

---

### Post by Copper Bezel on 2013-06-17
Well, I think the four less hairy ones make sense with a top-down system like Linux, since they're all system-wide concerns. Individual apps shouldn't control the default handlers for filetypes, it makes sense to have the complete sets of launchers and autostart entries together, and theming means that icons in Linux are not defined exclusively by the apps. Now, you could certainly have a /Applications/Common or something to hold all of that, and that would make some sense, but an autostart entry wouldn't be under /Applications/MyApp.

Apps should certainly be in the $PATH, because having graphical apps readily accessible from the command line makes a lot of testing and scripting a lot more convenient than it would be otherwise. At first blush, a symlink from /usr/bin to a location in /opt seems to make the most sense - Google Chrome does this, apparently.

---

