---
title: "Any Ubuntu users running Portage?"
date: 2006-05-01
forum: The Cafe
---

### Post by BoyOfDestiny on 2006-05-01
I'm wondering if anyone here has tried to run portage on Ubuntu, as described here
[Installing portage on other distros, easier than ever]("http://forums.gentoo.org/viewtopic.php?t=125553")

Ideally I'd put it on both my dapper 32 and 64 installs... I want to make it clear I don't want it to do OS core updates (no messing with the kernel, gcc, etc). The only reason I want access to portage is for more apps/plugins. 

RANT:
There are already some apps I build from source under ubuntu:

pan-0.94, advancemame-0.104.0, scummvm-0.8.2, advancemenu-2.4.13, dosbox-0.65, libbinio-1.4, uade-2.02, audacious-1.0.0, vice-1.19, checkinstall-1.6.0       ,mednafen-0.5.2. 
For cvs version of zsnes and svn version of audacious, I have scripts to automate checkout and building... 

For the stuff I listed, it's either not included in the dapper repos, out of date, an issue with the repo package (i.e. vice not having the c64 kernals, [yes with an 'a' in this case] and out of date too...)

So for that stuff, had to go the page, download, uncompress, get all the dependencies, build, checkinstall, repeat... 

Anyway, works great, but it would be nice to be able to update these automatically if it wouldn't be too disastrous...

P.S. I'm not ready to even think of switching distros. I enjoy Ubuntu (and Dapper especially) way too much. Not to mention the community we have going here :)

---

### Post by htinn on 2006-05-01
Pan is now 0.95 by the way. :)

---

### Post by hollywoodb on 2006-05-01
The immediate problems I see:

1) /etc/portage/package.mask is going to need to be huge.

2) You'll proabably spend a lot of time writing or modifying ebuilds.  Many ebuilds have different dependencies or cascading dependencies that aren't going to coincide with what libraries and such present on an Ubuntu system.

3) Many ebuilds are going to break due to /etc/portage/package.mask

4) I'm not sure how you would make portage aware of currently installed packages.  For example, you install app-1.2.3 which depends on foo-1.2.3... Portage installs foo-1.2.3 while you already had foo-1.2.2 from the repos installed.  Files get overwritten or install to a different location, either way it s a problem.  This is where the huge package.mask comes in.

5) If you were able to make portage aware of installed packages, you'd have to get all your package-dev or package-devel packages installed for compiles (emerge) to complete and not complain about missing files as early as the configure script for package 1.

That's just off the top of my head, if some of these issues are resolvable I'd like to know as well ;)

---

### Post by BoyOfDestiny on 2006-05-01
Man those are a lot of barriers... Oh well... I guess I'll just keep doing what I've been doing... At least it's pretty streamlined once all the dependencies are installed... :)

Also, thanks htinn, got pan .95 running now :)

---

### Post by Specialsauce on 2006-05-01
meh, the way i see it, if you want portage, use gentoo.

---

### Post by ssam on 2006-05-02
are the apps in gentoo really more up to date?

---

### Post by Sheinar on 2006-05-02
[QUOTE=ssam]are the apps in gentoo really more up to date?[/QUOTE]
Not really. Not unless they've changed how they release packages since I last used Gentoo. Gentoo is pretty out of date unless you enable the testing repository.

---

### Post by bonzodog on 2006-05-02
Ubuntu does have it's own version of portage; Apt-build. This will pull a src package from the src repos and build it according to the dpkg info file inside the package.

---

### Post by -Rick- on 2006-05-02
If you're bored you could also try [pkgsrc]("http://www.netbsd.org/Documentation/software/packages.html")

---

