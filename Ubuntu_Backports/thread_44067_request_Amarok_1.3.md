---
title: "request: Amarok 1.3"
date: 2005-06-24
forum: Ubuntu Backports
---

### Post by dlpfmVfH on 2005-06-24
I want to know if it is possible to upgrade the amarok package, to 1.3 beta.
at the moment 1.2.4 is in ubp.
**Highlights in amaroK 1.3:**

   
[list]
[*] Wikipedia artist lookup, a revolutionary feature providing information from the free online encyclopedia.
[*] Redesigned sidebar, with improved look-and-feel.
[*] Automatic download of scripts and themes with KNewStuff.
[*] HelixPlayer engine.
[*] New Playlist Browser, powerful and easy to use.
[*] Cue file sheet support.
[*] Dynamic playlist mode.
[*] PostgreSQL database support.
[*] Much extended DCOP scripting interface.
[*] Multiple analyzer visualizations for the playlist window.
[*] Editable Smart Playlists. 
[/list] see :
[http://amarok.kde.org/content/view/55/66/](http://amarok.kde.org/content/view/55/66/)

thank you

---

### Post by Firetech on 2005-06-24
I don't think it's a good idea to backport a beta version (considering that the amaroK devs themselves consider beta1 to be of _alpha_ quality). AFAIK, beta 2 will be released this weekend, and it's not very hard to build and install manually for those people who want it.

Just extract the source package from amaroK's homepage. Open a terminal (Applications > System > Terminal in GNOME (ubuntu), K > System > Konsole in KDE (kubuntu). In the terminal, type "cd " followed by the directory you extracted the sources to and press Enter. Then run (type and press Enter) "./configure --help" and check for flags and functions you want/need or doesn't want/need. Then run "./configure [flags-here]" (my configuration is "./configure --disable-amazon --enable-mysql --enable-debug=full". The debug thingie at the end is recommended by the amaroK devs for them to track down bugs easier...)

When "./configure ..." is finished, run "make && sudo make install". (This takes 10-15 minutes on my 2.4 GHz Celeron with 256 MB of memory.)
When the compilation (make) is done start amaroK (or restart if you left it running) and you have a complete amaroK 1.3 beta (hopefully).

If you need to change your settings (the ./configure stuff), run "make clean" in the source package directory and refollow this little guide from the ./configure steps.

NOTE: You might want to uninstall the amaroK version from the repositories (the one from synaptic/kynaptic/apt-get) FIRST (!) so the files won't be overwritten or deleted upon upgrade of that package. If you do this, the menu item for amaroK will disappear, though. (It is not too hard adding one manually afterwards...)

---

### Post by Bob D. on 2005-06-24
Don't think you're going to get this backported.

The "Zeroth Law" (nice use of Asimov   :) ) of Backports is "Only packages currently in Ubuntu's development branches are eligible for backporting". The Breezy repos currently contain 1.2.4 as well.

For more info on the Backports requirements, see [here]("http://ubuntuforums.org/showthread.php?t=40291").

Bob

---

### Post by dlpfmVfH on 2005-06-25
ok thanks, forgot..the backport changes...

---

### Post by Bob D. on 2005-06-25
[QUOTE=aboe]ok thanks, forgot..the backport changes...[/QUOTE]No problem, you are most welcome. Got caught myself the other day by the changes when I requested a backport from another repository. Really all for the better I think.

Bob

---

### Post by jdong on 2005-06-25
Yeah, new policy. I've been wanting to do it for a while, too... It's not just official diplomacy or anything like that...

If Backports was newer than Breezy, upgrading from Hoary to Breezy would be an absolute nightmare.

---

### Post by manicka on 2005-06-25
[QUOTE=Firetech]

When "./configure ..." is finished, run "make && sudo make install". [/QUOTE]

I'd suggest using "sudo checkinstall" instead of "sudo make install". That way you end up with   nice deb package in your folder and the package is also easily removed using apt or synaptic if there is a problem with it.

---

### Post by metallikop on 2005-06-25
I have compiled and packaged up amarok 1.3beta1.  Grab it here: [http://www.metallikop.com/blog/?p=77](http://www.metallikop.com/blog/?p=77)

Edit: This will only work on breezy.  Sorry those of you stuck on Hoary.  Also, this is by no means an official build.

---

