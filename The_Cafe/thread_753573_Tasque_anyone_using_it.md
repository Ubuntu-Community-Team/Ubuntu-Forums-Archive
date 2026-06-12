---
title: "Tasque anyone using it"
date: 2008-04-12
forum: The Cafe
---

### Post by pt123 on 2008-04-12
While trying to figure out how to get Tasks working in Tomboy, I stumbled across this powerful program called Tasque by Novell.

[http://live.gnome.org/Tasque](http://live.gnome.org/Tasque)

But sadly it doesn't seem to be in the Hardy repos, and I couldn't find searching the net. 

There is a video on it
[http://video.google.com/videoplay?docid=-3324975082418734422&pr=goog-sl](http://video.google.com/videoplay?docid=-3324975082418734422&pr=goog-sl)

It is able to download tasks lists from Remember the Milk. 
Can recognise tasks from Tomboy.
It also has a plugin to work with Gnome-Do.

So is anyone here using it, and if possible know a place where I can get a DEB for it. 

Another worry is that it uses Mono, I concerned  now that some of my must-need apps in Linux are using Mono : Tomboy, F-SPot & Gnome-Do.

---

### Post by pt123 on 2008-04-13
Bump anyone or are most here non-Task orientated users?

---

### Post by smartboyathome on 2008-04-13
The reason there isn't a deb is because it is still in development. I don't know where a deb is, but you can compile it (for every dependancy missing, make sure you have the -dev files installed in synaptic). Then type make, and sudo make install.

---

### Post by pt123 on 2008-04-14
> **smartboyathome said:**
> The reason there isn't a deb is because it is still in development. I don't know where a deb is, but you can compile it (for every dependancy missing, make sure you have the -dev files installed in synaptic). Then type make, and sudo make install.
If they did a deb all the enthusiasts can test it out. But it's a Novell product so they might not appreciate Ubuntu users.

Compile "make install" leaves an ugly mess. With debs its so easy to uninstall when you are finished with the program.

---

### Post by jbrockmeier on 2008-04-14
*But it's a Novell product so they might not appreciate Ubuntu users.*

You know what? We would appreciate Ubuntu users, or Fedora users, or users from any distro. We want it to be used by Linux users, not just SUSE/openSUSE users. Please package it for Ubuntu and enjoy using it! 

Joe 'Zonker' Brockmeier
openSUSE Community Manager

---

### Post by 50words on 2008-04-14
Looks like a fantastic tool! I have been meaning to try RTM, and I think this is the encouragement I needed. I'm going to give it a shot.

---

### Post by pt123 on 2008-04-14
> **jbrockmeier said:**
> *But it's a Novell product so they might not appreciate Ubuntu users.*

Joe 'Zonker' Brockmeier
openSUSE Community Manager



Whoa, you joined this  forum, just to post that. 

How did you know we were talking about it here?

------------

---

### Post by emid on 2008-04-22
I've been using it for a few weeks.  I like it quite a bit and will be keeping an eye out for new versions.

---

### Post by pt123 on 2008-04-23
^ How did you get it installed on Ubuntu,

here was a review of it by download Squad 
[http://www.downloadsquad.com/2008/04/18/flipping-the-linux-switch-forgetful-penguins-love-tasque/](http://www.downloadsquad.com/2008/04/18/flipping-the-linux-switch-forgetful-penguins-love-tasque/)

and they said they couldn't get it to work on Ubuntu

---

### Post by fnkps on 2008-04-23
I had to do some poking too, but you need to install both mono-gmcs and mono-tools-devel (at least, use sudo apt-get install mono-gmcs mono-tools-devel) before config, make, and make install.  After that it works just fine.  Or did for me.

Ken

---

### Post by StianH on 2008-04-27
I just saw the video on the RTM blog, and I really want to give it a go. I tried downloading the tarball from the wiki, but I do get an error running make.

I have installed mono-gmcs as required (./configure complained about that), and after reading what fnpks says I installed mono-tools-devel as well. However, the error still remains the same when running make (I've truncated all before the failing action):

```

Making all in po
make[1]: Entering directory `/home/stian/src/tasque-0.1.5/po'
file=`echo fi | sed 's,.*/,,'`.gmo \
	  && rm -f $file &&  -o $file fi.po
/bin/sh: -o: not found
make[1]: *** [fi.gmo] Error 127
make[1]: Leaving directory `/home/stian/src/tasque-0.1.5/po'
make: *** [all-recursive] Error 1

```

Anyone know anything about this?

I also tried building from svn using the instructions on the Wiki ( [http://live.gnome.org/Tasque/Building](http://live.gnome.org/Tasque/Building) ), but doing that I am told to install gnome-common from GNOME CVS:

```

stian@shuttlestar:~/src/tasque$ ./autogen.sh --prefix=/home/stian/stage/tasque --enable-backend-dummy --enable-backend-rtm --enable-backend-sqlite
You need to install gnome-common from the GNOME CVS

```

I am looking into this now, but sounds to me like something that might just have lots of other things needing to be buildt from GNOME CVS :P

---

### Post by castrojo on 2008-04-27
nixternal is packaging Tasque here: [https://edge.launchpad.net/~tasque-packagers/+archive](https://edge.launchpad.net/~tasque-packagers/+archive)

---

### Post by StianH on 2008-04-27
Hmm, I tried installing that, on my pretty much fresh Ubuntu 8.04 install, and it doesn't work. Either there are some missing dependencies, or something is wrong with the build (or even my computer), gonna try to submit a bug on that.

```

stian@shuttlestar:~$ tasque 
[Debug]: Tasque remote control active.

** (Tasque:8339): WARNING **: The following assembly referenced from /usr/lib/tasque/Tasque.exe could not be loaded:
     Assembly:   evolution-sharp    (assemblyref_index=13)
     Version:    3.0.0.0
     Public Key: 457eed85bd9370df
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/tasque/).


** (Tasque:8339): WARNING **: Could not load file or assembly 'evolution-sharp, Version=3.0.0.0, Culture=neutral, PublicKeyToken=457eed85bd9370df' or one of its dependencies.

** (Tasque:8339): WARNING **: Could not load file or assembly 'evolution-sharp, Version=3.0.0.0, Culture=neutral, PublicKeyToken=457eed85bd9370df' or one of its dependencies.
[Debug]: Exception is: System.Reflection.ReflectionTypeLoadException: The classes in the module cannot be loaded.
  at (wrapper managed-to-native) System.Reflection.Assembly:GetTypes (bool)
  at System.Reflection.Assembly.GetTypes () [0x00000] 
  at Tasque.Application.GetBackendsFromAssembly (System.Reflection.Assembly asm) [0x00000] 
  at Tasque.Application.LoadAvailableBackends () [0x00000] 
  at Tasque.Application.Init (System.String[] args) [0x00000] 
  at Tasque.Application..ctor (System.String[] args) [0x00000] 
  at Tasque.Application.GetApplicationWithArgs (System.String[] args) [0x00000] 
  at Tasque.Application.Main (System.String[] args) [0x00000] 

```

**UPDATE:** I figured out I needed to install libevolution3.0-cil as well. Now the pacakge from nixternal works just fine. Btw thanks for the link whiprush.

---

### Post by pt123 on 2008-04-27
> **whiprush said:**
> nixternal is packaging Tasque here: [https://edge.launchpad.net/~tasque-packagers/+archive](https://edge.launchpad.net/~tasque-packagers/+archive)


Thank you for posting this, and thanks to nixternal.

Just played around for 5mins, and really like the simple interface.

---

### Post by Mr. Picklesworth on 2008-04-27
Ooh, their little demo reminded me of Giver, too. Has Boyd Timothy ever made an imperfect app? He understands the concept of "simple, easy and integrated" to perfection.

---

### Post by andrewsomething on 2008-04-27
I have a sync from Debian unstable in my ppa:

[https://edge.launchpad.net/~andrewsomething/+archive](https://edge.launchpad.net/~andrewsomething/+archive)

As it is Debian now, an offical package should be in the next Ubuntu release, Intrepid.

---

### Post by SlappyPappy on 2008-05-08
> **whiprush said:**
> nixternal is packaging Tasque here: [https://edge.launchpad.net/~tasque-packagers/+archive](https://edge.launchpad.net/~tasque-packagers/+archive)

Brah, thanks for posting this. I tried to download it, configure, make, make install and it just kept refusing to work. After my failure I hit your link...

Did the deb and blammo I'm in. Very cool!  :)

---

### Post by flomar on 2008-05-13
Hi folks,

i've been looking for days to find a way to get Tasque running. the same day i found this thread i was amazed of Tasque, so thanks for posting and packaging ;) 

Already completely into Tasque i was curious about the Tomboy-Addin you can see in the Hackweek-Google-Video. I've been looking for days when yesterday [http://www.gnome.org/projects/tomboy/]("http://www.gnome.org/projects/tomboy/") announced that it has now been implemented into Tomboy 0.11.0 unstable. Of course there is only the source you have to compile.

Because this is my first (successful) try to compile and package a program i wanted to share this with you. :)
**[tomboy_0.11.0-1_i386.deb]("http://www.unet.univie.ac.at/~a0500643/upload/tomboy_0.11.0-1_i386.deb")**
I built this with ./configure && make && checkinstall on a Hardy machine.
What i did:
- remove tomboy
- download the [source]("http://www.gnome.org/projects/tomboy/download.html")
- sudo apt-get build-dep tomboy
- sudo apt-get install gnome-common intltool libgtk2.0-dev checkinstall
- install the created deb-package
- activate the tasque-addin in the preference-dialog 

## I dont have any experience in packaging, so dont consider this package as safe or for productivity use - at best for testing.

i hope this is of any use to you! 
flo

---

### Post by HammerHed on 2008-05-14
I have installed Tasque and cannot get it to open/run. 

Please help. I have installed all the required dependencies as far as I can see and don't seem to get any errors, but it just will not run. What am I missing here?

See my code below:

:~/Software_downloads/tasque-0.1.5$ tasque
[Debug]: Tasque remote control active.
[Debug]: Found Available Backend: Tasque.Backends.RtmBackend.RtmBackend
[Debug]: Tasque.exe location:  /usr/local/lib/tasque/Tasque.exe
[Info]: Searching for Backend DLLs in: /usr/local/lib/tasque
[Info]: 	Reading /usr/local/lib/tasque/RtmNet.dll
[Debug]: Storing 'Tasque.Backends.RtmBackend.RtmBackend' = 'Remember the Milk'
[Debug]: CurrentBackend specified in Preferences: 
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.DllNotFoundException: gdk-x11-2.0
  at (wrapper managed-to-native) Egg.TrayIcon:gdk_x11_display_get_xdisplay (intptr)
  at Egg.TrayIcon.OnRealized () [0x00000] 
  at Gtk.Widget.realized_cb (IntPtr widget) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.realized_cb(IntPtr widget)
   at Gtk.Widget.realized_cb(IntPtr )
   at Gtk.Widget.gtk_widget_show_all(IntPtr )
   at Gtk.Widget.gtk_widget_show_all(IntPtr )
   at Gtk.Widget.ShowAll()
   at Tasque.Application.SetupTrayIcon()
   at Tasque.Application.InitializeIdle()
   at GLib.Idle+IdleProxy.Handler()
   at GLib.Idle+IdleProxy.Handler()
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at Tasque.Application.StartMainLoop()
   at Tasque.Application.Main(System.String[] args)
grant@Demon:~/Software_downloads/tasque-0.1.5$ 


If I run: ./autogen.sh --prefix=/home/user/stage/tasque --enable-backend-dummy --enable-backend-rtm --enable-backend-sqlite

I get the following output:

grant@Demon:~/Software_downloads/tasque-0.1.5/tasque$ sudo ./autogen.sh --prefix=/home/user/stage/tasque --enable-backend-dummy --enable-backend-rtm --enable-backend-sqlite
[sudo] password for grant: 
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.9...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.26
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.16.3
checking for intltool >= 0.30...
  testing intltoolize... found 0.37.1
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
Checking for required M4 macros...
Checking for forbidden M4 macros...
Processing ./configure.ac
Running libtoolize...
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Putting files in AC_CONFIG_AUX_DIR, `..'.
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

Running intltoolize...
intltoolize: 'po/Makefile.in.in' is out of date: use '--force' to overwrite

---

### Post by flomar on 2008-05-14
hey,

i suppose you tried the packages bevor compiling it yourself?
-> [https://edge.launchpad.net/~tasque-packagers/+archive]("https://edge.launchpad.net/~tasque-packagers/+archive")

flo

---

### Post by HammerHed on 2008-05-14
Yes, I did but being a Ubuntu newb I could not figure out how to add [https://edge.launchpad.net/~tasque-packagers/+archive](https://edge.launchpad.net/~tasque-packagers/+archive) to my /etc/apt/sources.list

It gave me an error when I added it to the /etc/apt/sources.list.

How do I do that?

Sorry, this is basic stuff I know.

---

### Post by helliewm on 2008-05-14
Tasque is now a deb file on get deb see here:

[URL="http://www.getdeb.net/category.php?id=6"]http://www.getdeb.net/category
.php?id=6[/URL]

Helen

EDIT: It works perfectly too, looks excellent.

---

### Post by HammerHed on 2008-05-14
Thanks helliewm,

I installed the deb package and got it started, it asked me for the backend I changed it to Evolution and then it started with "loading Tasks" progress bar at the bottom.

Now it just hangs when I start it, I cannot get any preferences or anything, no menus just a blank Tasque window.

I have uninstalled it a few times and still the same.

What now?

---

### Post by monstermudder78 on 2008-05-14
> **HammerHed said:**
> Yes, I did but being a Ubuntu newb I could not figure out how to add [https://edge.launchpad.net/~tasque-packagers/+archive](https://edge.launchpad.net/~tasque-packagers/+archive) to my /etc/apt/sources.list

It gave me an error when I added it to the /etc/apt/sources.list.

How do I do that?

Sorry, this is basic stuff I know.

```
sudo gedit /etc/apt/sources.list
```

Then add these two lines to the bottom:
```
deb http://ppa.launchpad.net/tasque-packagers/ubuntu hardy main
deb-src http://ppa.launchpad.net/tasque-packagers/ubuntu hardy main
```

then:
```
sudo aptitude update
sudo aptitude safe-upgrade
```
(not sure if both of those are necessary but I always do both just to be sure)

finally:
```
sudo aptitude install tasque
```

I think that's how I just did it.

---

### Post by HammerHed on 2008-05-14
Thanks monstermudder78, I  did that and  installed as you mentioned but then get an error message:

Failed to execute child process "/usr/lib/tasque/Tasque.exe" (Permission denied)

If I run the following see the output, but tasque does not launch: 

grant@Demon:~/Software_downloads$ tasque
[Debug]: Tasque remote control active.
[Debug]: Found Available Backend: Tasque.Backends.RtmBackend.RtmBackend
[Debug]: Tasque.exe location:  /usr/local/lib/tasque/Tasque.exe
[Info]: Searching for Backend DLLs in: /usr/local/lib/tasque
[Info]: 	Reading /usr/local/lib/tasque/RtmNet.dll
[Debug]: Storing 'Tasque.Backends.RtmBackend.RtmBackend' = 'Remember the Milk'
[Debug]: CurrentBackend specified in Preferences: Tasque.Backends.EDS.EDSBackend
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.DllNotFoundException: gdk-x11-2.0
  at (wrapper managed-to-native) Egg.TrayIcon:gdk_x11_display_get_xdisplay (intptr)
  at Egg.TrayIcon.OnRealized () [0x00000] 
  at Gtk.Widget.realized_cb (IntPtr widget) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.realized_cb(IntPtr widget)
   at Gtk.Widget.realized_cb(IntPtr )
   at Gtk.Widget.gtk_widget_show_all(IntPtr )
   at Gtk.Widget.gtk_widget_show_all(IntPtr )
   at Gtk.Widget.ShowAll()
   at Tasque.Application.SetupTrayIcon()
   at Tasque.Application.InitializeIdle()
   at GLib.Idle+IdleProxy.Handler()
   at GLib.Idle+IdleProxy.Handler()
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at Tasque.Application.StartMainLoop()
   at Tasque.Application.Main(System.String[] args)
grant@Demon:~/Software_downloads$

---

### Post by monstermudder78 on 2008-05-14
HammerHed, are you using Hardy?

---

### Post by HammerHed on 2008-05-14
However if I run the download .deb package from the following link - [http://www.getdeb.net/category.php?id=6](http://www.getdeb.net/category.php?id=6) - I can get Tasque to load but now without any preferences options, it just hangs with a blank Tasque page.

---

### Post by HammerHed on 2008-05-14
Yeah Hardy.

---

### Post by monstermudder78 on 2008-05-14
Sorry, this may just be the blind leading the blind here, but where do u get the error when you install it the way I did?

---

### Post by monstermudder78 on 2008-05-14
Try installing this: libevolution3.0-cil

---

### Post by HammerHed on 2008-05-14
If I go to the Hardy desktop menu drop down: Aplications > Office > Tasque

Gives me the error: Failed to execute child process "/usr/lib/tasque/Tasque.exe" (Permission denied)

---

### Post by monstermudder78 on 2008-05-14
Hmmm... I think you will need someone more qualified than myself to fix that, sorry.

---

### Post by HammerHed on 2008-05-14
Seems as if my Hardy does not like that version of Tasque as I can get the version from: [http://www.getdeb.net/category.php?id=6](http://www.getdeb.net/category.php?id=6) to run, but with issues (it hangs) but at least it runs (sort of).

---

### Post by HammerHed on 2008-05-14
OK, finally  got somewhere.

This link has info on Hardy and Tasque: [http://www.downloadsquad.com/2008/04/18/flipping-the-linux-switch-forgetful-penguins-love-tasque/](http://www.downloadsquad.com/2008/04/18/flipping-the-linux-switch-forgetful-penguins-love-tasque/)

Also links to: [http://projects.dvwd.be//index2.php?page=1atatime&id=14](http://projects.dvwd.be//index2.php?page=1atatime&id=14)
for Ubuntu/Deb package updated Tasque.

Also require dependencies, see below:

 [http://projects.dvwd.be//index2.php?page=1atatime&id=14](http://projects.dvwd.be//index2.php?page=1atatime&id=14)

The program crashed until so I added notify-sharp from the PPA here: [https://launchpad.net/~banshee-team/+archive](https://launchpad.net/~banshee-team/+archive) (just the libnotify0.4-cil_0.4.0~r2998-1~hardy1_all.deb package)

Then followed the advice here: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=474666](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=474666) to install the libgtk2.0-dev package.

Yeah it sounds complex, but really it was just 2 minutes of Googling, and obviously jumping through these hoops was just a side effect of getting a dev version running.

See comments: instructions to get it sorted. Seems to run now.

At last.

Thanks for all your help!

---

### Post by r m h on 2009-02-22
I just ran across this thread serendipitously - I've been looking for a decent shareable todo list for a loooong time.

I'm running Ubuntu on my laptop and my desktop.  My wife uses a MacBook Pro laptop.

I installed Tasque and set up a Remember The Milk (RTM) account ([http://www.rememberthemilk.com](http://www.rememberthemilk.com)) primarily so I could have one set of todo lists accessible from both my laptop and my desktop.  But then I found that lists can be made public and or shareable.

So, my wife added the RTM gadget to her iGoogle and set up an RTM account of her own.  Within 10 minutes we had a shared ToDo list.

Tasque is installable via the Synaptic Package Manager.

There is a $25 per year iPhone app that allows managing RTM lists on it.

So far, I'm liking Tasque and it's RTM integration a whole lot.

---

### Post by Luggy on 2009-05-01
I installed Tasque the other day when checking out GnomeDo plugins and was easily available in the Jaunty repos.

I like it as an alternative to Tomboy because all I was really interested in was a ToDo list and not a list taking application.

It's nice, simple and clean. Just perfect.

---

### Post by argraff on 2009-07-16
Love this program - I have it hooked up to RTM, and RTM hooked up to Google Calendar and Evolution. Also hooked up Google Calendar to Evolution and I finally have a workable solution. It also syncs with my Palm Centro for bonus points. (Kinda sad that I need four apps to keep organized in two places, but hey...)

---

### Post by nelamvr6 on 2009-07-16
I was using this for a while, but it still doesn't support repeating tasks in RTM.  If a task repeats in RTM, Tasque will show it as a future task, but it will not be seen on the day it is due.

???  WTF?

So I found myself using the RTM web site all the time because I couldn't rely on Tasque showing me tasks due today.

Needless to say this severely limited Tasque's usefulness.  So now it has been completely deleted.

If the developers get this issue fixed I might give it another chance.

---

### Post by Cobalto on 2009-08-07
One of the developers has put up a new .deb for Jaunty with a patch to allow changing categories. It works perfectly and has made Tasque a lot more usable.

The bug report:
[http://bugzilla.gnome.org/show_bug.cgi?id=534749](http://bugzilla.gnome.org/show_bug.cgi?id=534749)

The .deb:
deb [http://ppa.launchpad.net/tobbe-ydo/ppa/ubuntu](http://ppa.launchpad.net/tobbe-ydo/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/tobbe-ydo/ppa/ubuntu](http://ppa.launchpad.net/tobbe-ydo/ppa/ubuntu) jaunty main

Really nicely done.

---

### Post by pt123 on 2009-08-07
I have moved over to using GTG Getting things Gn..
[http://gtg.fritalk.com/](http://gtg.fritalk.com/)

---

### Post by Jugney on 2010-02-10
Repeating tasks work just fine for me. I have to set them up in RTM, but then afterwards, I see in Tasque the next instance of that task. When I mark it completed, then the RTM backend re-generates the task on the next date it's due. This doesn't show up right away - only when I restart Tasque or refresh my tasks.

Tasque is awesome.

---

