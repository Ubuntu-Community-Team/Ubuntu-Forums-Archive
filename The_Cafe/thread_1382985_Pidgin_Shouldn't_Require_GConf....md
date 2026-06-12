---
title: "Pidgin Shouldn't Require GConf..."
date: 2010-01-16
forum: The Cafe
---

### Post by Psumi on 2010-01-16
[[IMG]http://brainstorm.ubuntu.com/idea/23338/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/23338/)

Basically, proxy information is stored in gconf, and that's mainly why pidgin requires gconf to be installed for pidgin to be installed. Ayttm doesn't install gconf, so why should pidgin?

---

### Post by sliketymo on 2010-01-16
Not sure,but I think it has something to do with Evolution integration.

---

### Post by Keyper7 on 2010-01-16
Sounds strange, yeah. Specially since they don't use gnome-keyring under the argument of not wanting to tie Pidgin to an specific OS.

Does anyone know how such proxy info is stored in Windows and OSX?

---

### Post by Psumi on 2010-01-16
> **Keyper7 said:**
> Sounds strange, yeah. Specially since they don't use gnome-keyring under the argument of not wanting to tie Pidgin to an specific OS.

Does anyone know how such proxy info is stored in Windows and OSX?

According to a bug report, Windows stores proxy information within the registry, which is also not cross-DE.

---

### Post by juancarlospaco on 2010-01-16
GConf-Editor you mean, it doesnt store nothing on itself, its just a GUI Front-end.
:)

---

### Post by Psumi on 2010-01-16
> **juancarlospaco said:**
> GConf-Editor you mean, it doesnt store nothing on itself, its just a GUI Front-end.
:)

no, gconf is real: [http://en.wikipedia.org/wiki/GConf](http://en.wikipedia.org/wiki/GConf)

---

### Post by jpeddicord on 2010-01-16
> **Psumi said:**
> [[IMG]http://brainstorm.ubuntu.com/idea/23338/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/23338/)

Basically, proxy information is stored in gconf, and that's mainly why pidgin requires gconf to be installed for pidgin to be installed. Ayttm doesn't install gconf, so why should pidgin?

It's not that Pidgin stores proxy information in GConf, it's that Pidgin needs to poll proxy information from GNOME which does happen to be stored in the GConf database. So there is a reason for the dependency, it's not just a "let's decide to move these settings to gconf from flat files."

---

### Post by juancarlospaco on 2010-01-16
> **Psumi said:**
> no, gconf is real: [http://en.wikipedia.org/wiki/GConf](http://en.wikipedia.org/wiki/GConf)

I know, im not saying you are wrong, 
but it requires Gconf-Editor?, Gconf got a set of tools.

*"The application gconf-editor is provided to allow users to change settings manually"*

---

### Post by Mr. Picklesworth on 2010-01-16
Gconf is human-readable XML configuration files arranged in a predictable way, thus enabling easy maintenance for users and developers, the consistent creation of default settings, the locking of settings, etc.

It is not a heavy dependency. Pidgin at its heart still depends on GTK, glib, etc. and adding another configuration back-end simply adds unnecessary cruft to maintain.

On another note, as I understand it gconf is being refactored into something more dbusey, FD.org-ish and desktop agnostic, though I'm not following that very closely :)

---

### Post by jpeddicord on 2010-01-16
> **Mr. Picklesworth said:**
> On another note, as I understand it gconf is being refactored into something more dbusey, FD.org-ish and desktop agnostic, though I'm not following that very closely :)

Yeah, DConf & GSettings or something. At one point I heard it would be implemented directly into GLib, but who knows right now; the spec keeps changing.

---

### Post by falconindy on 2010-01-16
If you don't like having Gconf as a dependency of Pidgin, then rebuild pidgin yourself without gconf. When you get down to it, you can run Pidgin just fine even without libpurple (though you do need to compile against it).

---

### Post by 3rdalbum on 2010-01-16
Gconf is a predecessor to "CouchDB" and "DesktopCouch". It's a handy way to store and retrieve data with minimal fuss and no "reinventing-the-wheel". I fully support Pidgin's using Gconf.

---

### Post by Psumi on 2010-01-17
> **3rdalbum said:**
> Gconf is a predecessor to "CouchDB" and "DesktopCouch". It's a handy way to store and retrieve data with minimal fuss and no "reinventing-the-wheel". I fully support Pidgin's using Gconf.

So basically, because pidgin requires gconf, I can't have a pure xfce distro without relying on old software such as ayttm.

Similarly, gksu requires a bunch of gnome depends as well, even though it is only a gtk app.

---

### Post by Xbehave on 2010-01-17
> **Mr. Picklesworth said:**
> Gconf is human-readable XML configuration files arranged in a predictable way, thus enabling easy maintenance for users and developers, the consistent creation of default settings, the locking of settings, etc.
Actually is just the settings API, the only widespread backend is XML configuration but there are/were others such as sqlite backends.
> **Psumi said:**
> So basically, because pidgin requires gconf, I can't have a pure xfce distro without relying on old software such as ayttm.

Similarly, gksu requires a bunch of gnome depends as well, even though it is only a gtk app.
1) Why do you want a "pure xfce" distro?
2) what is wrong with having gnome dependencies, it's muuuch better than somebody reinventing the wheel every, especially if these are non-gui dependencies.

---

### Post by Psumi on 2010-01-17
> **falconindy said:**
> If you don't like having Gconf as a dependency of Pidgin, then rebuild pidgin yourself without gconf. When you get down to it, you can run Pidgin just fine even without libpurple (though you do need to compile against it).

Why would I do that? I'm not a builder or compiler for that matter, I'm an end-user.

---

### Post by cb951303 on 2010-01-17
I don't understand pidgin devs. They don't want to tie Pidgin to any specific DE and yet they include things like "fetching proxy settings from GNOME".

---

### Post by steeleyuk on 2010-01-17
> **cb951303 said:**
> I don't understand pidgin devs. They don't want to tie Pidgin to any specific DE and yet they include things like "fetching proxy settings from GNOME".

Well they have to, otherwise people would be complaining about not being able to connect when behind a proxy...

---

### Post by Psumi on 2010-01-17
> **steeleyuk said:**
> Well they have to, otherwise people would be complaining about not being able to connect when behind a proxy...

Which I don't do.

> **Xbehave said:**
> 1) Why do you want a "pure xfce" distro?
2) what is wrong with having gnome dependencies, it's muuuch better than somebody reinventing the wheel every, especially if these are non-gui dependencies.

Because Pidgin is the only real thing that has gnome depends when I install my system. I usually sudo from terminal anyway, so I often don't need gksu unless I need to find a specific package (which I can just search through packages.ubuntu.com anyway.)

I use parole instead of totem.

---

### Post by Xbehave on 2010-01-17
> **Psumi said:**
> Because Pidgin is the only real thing that has gnome depends when I install my system.
You still didn't answer the questions,
1) Why do you want a "pure XFCE" install?
2) Why should the pidgin devs reinvent the wheel instead of using a non-gui component from gnome

> I usually sudo from terminal anyway, so I often don't need gksu unless I need to find a specific package (which I can just search through packages.ubuntu.com anyway.)
Your not supposed to sudo a GUI program because sudo does not setup the environmental variables correctly and under certain circumstances it can result in you being unable to login ( I think it's because your sockets are owned by root so you can't touch your own files)

---

### Post by juancarlospaco on 2010-01-17
XFCE depends on GTK and dependencies of GTK.

---

### Post by jpeddicord on 2010-01-17
> **Psumi said:**
> Which I don't do.

Believe it or not, there are people who have preferences different from yours. ;)

---

### Post by Simian Man on 2010-01-17
> **Psumi said:**
> Why would I do that? I'm not a builder or compiler for that matter, I'm an end-user.
You are not really an "end-user" if you give a flip about a small non-GUI dependency being installed along with a chat client.  Xbehave is right, why do you care if you have a pure Xfce setup?  Did one of the Gnome developers wrong you in some way and you are boycotting their work or something?

> **Xbehave said:**
> Your not supposed to sudo a GUI program because sudo does not setup the environmental variables correctly and under certain circumstances it can result in you being unable to login ( I think it's because your sockets are owned by root so you can't touch your own files)
FYI If you unlock the root password, you can "su -" which will elevate you to a login root shell and GUI programs will work as expected.

---

### Post by cb951303 on 2010-01-17
> **steeleyuk said:**
> Well they have to, otherwise people would be complaining about not being able to connect when behind a proxy...

I don't see firefox users complaining. A custom proxy settings dialog is the solution.

---

### Post by Xbehave on 2010-01-17
> **Simian Man said:**
> FYI If you unlock the root password, you can "su -" which will elevate you to a login root shell and GUI programs will work as expected.
If "su -" is ok, then something like sudo -i
> The -i (simulate initial login) option runs the shell specified in the passwd(5) entry of the target user as a login shell.  This means that login-specific resource files such as .profile or .login will be read by the shell.  If a command is specified, it is passed to the shell for execution.  Otherwise, an interactive shell is executed.  sudo attempts to change to that user's home directory before running the shell.  It also initializes the environment, leaving DISPLAY and TERM unchanged, setting HOME, SHELL, USER, LOGNAME, and PATH, as well as the contents of /etc/environment on Linux and AIX systems.  All other environment variables are removed.
might also work? I dunno i always go with kdesudo/gksudo because I know they work, where as I know plain sudo can have unexpected results.

---

### Post by falconindy on 2010-01-17
> **Psumi said:**
> Why would I do that? I'm not a builder or compiler for that matter, I'm an end-user.
As an end user, I manually compile roughly a dozen packages to remove cruft and ridiculous dependencies.

You're obviously unhappy with the way Canonical has decided to package Pidgin -- if you want to obtain the results you desire, some effort is required on your part. Isn't this the reason people use Linux... so that they have this inherent ability to customize packages to their liking?

The cries of one will not outweigh the needs of many.

---

### Post by steeleyuk on 2010-01-17
> **cb951303 said:**
> I don't see firefox users complaining. A custom proxy settings dialog is the solution.

Just what everybody wants, to have to enter the same proxy information into several different apps...

It would be better if Firefox read the proxy information from gconf as well. Same goes for reading the information from KDE, XFCE, etc.

---

### Post by cb951303 on 2010-01-17
> **steeleyuk said:**
> Just what everybody wants, to have to enter the same proxy information into several different apps...
If you want an application to be truly DE and OS agnostic there are compromises to do. And make no mistake pidgin had always the goal of being DE agnostic.

> 
It would be better if Firefox read the proxy information from gconf as well. Same goes for reading the information from KDE, XFCE, etc.
Terrible idea. So you want Firefox, KDE and XFCE to depend on a GNOME library?

Note that KDE and XFCE have their own conf. libraries.

Maybe there could be a freedesktop standards or something about the conf. file specs so that every DE could read the information but it's a long term solution.

---

### Post by Xbehave on 2010-01-17
> **steeleyuk said:**
> It would be better if Firefox read the proxy information from gconf as well. Same goes for reading the information from KDE, XFCE, etc.
Firefox can/does
kde uses WPAD or environmental variables, it would be nice to have read gconf as an option but kde has it's own proxy configuration tool.

---

### Post by steeleyuk on 2010-01-17
> Terrible idea. So you want Firefox, KDE and XFCE to depend on a GNOME library?

I didn't say it should depend on them for every install. If I install Firefox on GNOME, it should check for the availabilty of Gconf and grab the proxy info from there, if its available. Same goes for KDE, XFCE, etc using their own configuration data.

> Firefox can/does

I see they've updated it now, I know when I used to connect through the proxy at Uni it would never work until I checked to auto-detect the settings. I was thinking it would be nice to have rid of the proxy dialog altogether however, and use Gconf (or other) data same as Totem does, Rhythmbox does, Empathy does, etc.

---

### Post by cb951303 on 2010-01-17
> **steeleyuk said:**
> I didn't say it should depend on them for every install. If I install Firefox on GNOME, it should check for the availabilty of Gconf and grab the proxy info from there, if its available. Same goes for KDE, XFCE, etc using their own configuration data.
.

unfortunately, programming-wise, that's not how it works. if you want to use gconf you need to compile your application against gconf libraries and that's what a dependency is.

I think what you mean is compile time flags: something like "./configure --enable-gnome-proxy" should do the trick but this way it's very easy to turn the source code to spaghetti.

I still think that the best solution for Pidgin is to include it's own proxy settings dialog. (BTW I don't use Pidgin, does it already include this?)

---

### Post by jpeddicord on 2010-01-17
> **cb951303 said:**
> unfortunately, programming-wise, that's not how it works. if you want to use gconf you need to compile your application against gconf libraries and that's what a dependency is.

Not entirely true. You can introduce a new run-time dependency without building against a library at all. See [dlopen]("http://en.wikipedia.org/wiki/Dlopen") for information. It's handy in Python, for example, when using a C library that doesn't have a Python counterpart. Wikipedian example: ```
void* sdl_library = dlopen("libSDL.so", RTLD_LAZY);
if(sdl_library == NULL) {
   // report error ...
} else {
   // use the result in a call to dlsym
}
```

So, technically, Pidgin, Firefox, or any other application could check for the existence of the GConf library, and if it exists, dlopen it and do what's needed. If it doesn't, they could fall back to something else.

---

### Post by del_diablo on 2010-01-17
> **Xbehave said:**
> 2) what is wrong with having gnome dependencies, it's muuuch better than somebody reinventing the wheel every, especially if these are non-gui dependencies.

GNOME is the bloatest thing ever for a normal working system.
But hey, lets hope all your favorite apps get tied down to BLOTGNOME and lags to death.

---

### Post by Xbehave on 2010-01-17
> **del_diablo said:**
> GNOME is the bloatest thing ever for a normal working system.
But hey, lets hope all your favorite apps get tied down to BLOTGNOME and lags to death.
A nice rational argument about why not to use gconf, because GNOME is "bloated". I could explain that the whole point of seperate libraries is that you can pull in parts of the functionality without the "bloat" of the rest of gnome, but I doubt you care as you probably consider everything that uses more than 64k "bloat".

---

### Post by falconindy on 2010-01-17
> **del_diablo said:**
> GNOME is the bloatest thing ever for a normal working system.
But hey, lets hope all your favorite apps get tied down to BLOTGNOME and lags to death.
So, what do you use? DWM? Rat Poison? XMonad? Screen? Did you post this from elinks?

---

### Post by phrostbyte on 2010-01-17
> **steeleyuk said:**
> Just what everybody wants, to have to enter the same proxy information into several different apps...

It would be better if Firefox read the proxy information from gconf as well. Same goes for reading the information from KDE, XFCE, etc.

I smell a new freedesktop.org standard.

---

