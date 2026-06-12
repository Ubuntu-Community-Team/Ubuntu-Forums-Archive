---
title: "Pidgin 2.1.0 Released!"
date: 2007-07-30
forum: The Cafe
---

### Post by Kosimo on 2007-07-30
Hi guys.
Good news.
Pidgin reaches the 2.1.0 version with more than 120 bugfixes.
Enjoy it!


[Pidgin Website]("http://pidgin.im/pidgin/home/")

---

### Post by Kosimo on 2007-07-30
By the way if someone doesn't know how to install from the source code:

Download the source
Extract pidgin folder
open the terminal and go inside that folder

then


> ./configure
make
sudo make install

---

### Post by jcrnan on 2007-07-30
I managed to install it, but when I try to add my msn account it complains about needing SSL support. What do I do?

---

### Post by ~LoKe on 2007-07-30
> loke@x04d:~/pidgin-2.1.0$ pidgin
pidgin: symbol lookup error: pidgin: undefined symbol: purple_core_ensure_single_instance
Great start.

---

### Post by Kosimo on 2007-07-30
Here is working with no issues.

How did you install it?

---

### Post by ubuntu27 on 2007-07-30
> **jcrnan said:**
> I managed to install it, but when I try to add my msn account it complains about needing SSL support. What do I do?

You need to install the following packages from the repositories (or compile from the offical tcl website to get the latest version)

openssl
tcltls
tk8.4
tcl8.4

```
sudo aptitude install openssl tk8.4 tcltls tcl8.4
```

Optional:

libsnack2

```
sudo aptitude install libsnack2
```

---

### Post by Dimitriid on 2007-07-30
I usually try to install source things with checkinstall so they are easy to find in synaptic, will synaptic take care of those libraries for me if I do it that way or do I still need to install em separately?

---

### Post by plun on 2007-07-30
> **~LoKe said:**
> Great start.

Got the same on Gutsy.....noticed this during configure

Pidgin will be installed in /usr/local/bin.
Warning: You have an old copy of Pidgin at /usr/bin/pidgin.

sudo apt-get remove pidgin

sudo make install again...:)

EDIT
Also got a little gstreamer error so maybe its better to discuss this i Gutsys forum.

---

### Post by jcrnan on 2007-07-30
Ubuntu27: I installed those packages and I still get the error when I try to enable the msn account.

---

### Post by walkerk on 2007-07-30
thanks for the heads up.. just compiled it :)

---

### Post by aeon on 2007-07-30
@jcrnan

install those and possibly also libgnutls and try to compile again, the errors should be gone now

---

### Post by Cyfr on 2007-07-30
Why am I getting 

bash: ./configure: No such file or directory

When I try and ./configure?

Im rather tired. Am I missing something? :p

---

### Post by cookieofdoom on 2007-07-30
libxss-dev is needed to support the "Report idle time based on keyboard or mouse use" option. libnss-dev libnspr-dev are (I believe) needed for supporting the protocols requiring SSL.

You can do ```
sudo apt-get install libxss-dev libnss-dev libnspr-dev
``` to get those packages installed.

@ Cyfr, are you in the right directory?

---

### Post by Cyfr on 2007-07-30
> **cookieofdoom said:**
> 

@ Cyfr, are you in the right directory?

I tried the directory that the extract gives and I tried the "pidgin"
 directory within that

---

### Post by migla on 2007-07-30
>  dpkg: error processing [...] trying to overwrite `/usr/bin/ld', which is also in package binutils

:(

---

### Post by Cyfr on 2007-07-30
Nevermind it didn't extract the files correctly for some reason. Fixed now :)

---

### Post by nrs on 2007-07-30
omgz you should be installing in /usr/local ! 

./configure --prefix=/usr/local

---

### Post by migla on 2007-07-30
My problem was caused by me using "sudo checkinstall -D" instead of "sudo make install". Found a solution in the [comments on some blog:]("http://jhcore.com/2007/06/04/install-pidgin-in-ubuntu/") "sudo checkinstall --exclude=/etc/gconf,/usr/bin,/usr/lib" (whatever that means, it worked for me) :)

---

### Post by WastingBody on 2007-07-30
Everything went well for me except there is no sound when someone sends a message. The console beeps and thats it.

---

### Post by Montsegur87 on 2007-07-30
config.status: error: cannot find input file: doc/Makefile.in

---

### Post by stmiller on 2007-07-30
Just do this to install all dependencies needed to compile:

```
sudo apt-get build-dep gaim

```

And no need to set the prefix. It defaults to /usr/local as you can see in the configure help.

---

### Post by apc15x on 2007-07-30
Well I downloaded pidgin 2.1.0 but I get an error:
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
Can anybody help.
Thank in advance :(

---

### Post by syxbit on 2007-07-30
where's the changelog?

---

### Post by Quillz on 2007-07-31
Cool, thanks for the news.

---

### Post by il-luzhin on 2007-07-31
E: Couldn't find package sibxss-dev

---

### Post by v8YKxgHe on 2007-07-31
I compiled Pidgin 2.1.0 first time and it works ... however I have no sound, all I get is a console beep - I've played with the settings but no luck - what could be going on?

---

### Post by Kosimo on 2007-07-31
How can I install the spelling plugin?

---

### Post by bubi on 2007-07-31
> **Kosimo said:**
> How can I install the spelling plugin?

You have to install the -dev package:
[INDENT]sudo apt-get install libgtkspell-dev[/INDENT]

---

### Post by Kosimo on 2007-07-31
> **bubi said:**
> You have to install the -dev package:
[INDENT]sudo apt-get install libgtkspell-dev[/INDENT]

Done.
But I'm still not getting the spelling corrector when typing in the chat window.
Do I maybe have to reinstall Pidgin from the source having this lib installed?

---

### Post by happy-and-lost on 2007-07-31
Will this release make it into the final release of Gutsy?

---

### Post by Kosimo on 2007-07-31
> **happy-and-lost said:**
> Will this release make it into the final release of Gutsy?


Gutsy will may have the 2.1.2 or 2.2.0 as you can see in pidgin's roadmap ([here]("http://developer.pidgin.im/roadmap"))

Acutally, in two weeks a new version 2.1.1 should be ready.
Then 2.1.2 in one month
and finally 2.2.0 will be ready in two months... Maybe not in time for Gutsy.

---

### Post by liamwithers on 2007-07-31
Heya, I've done configure and am on make but it's taking forever!

---

### Post by Kosimo on 2007-07-31
> **liamwithers said:**
> Heya, I've done configure and am on make but it's taking forever!

Wait... It takes long time (about 10 to 20 minutes) don't cancel it!

---

### Post by graabein on 2007-07-31
Looks pretty good based on the screenshot.

[IMG]http://img503.imageshack.us/img503/5148/contactwindowlq6.png[/IMG]

---

### Post by ThrobbingBrain66 on 2007-07-31
If you guys can wait a little while, getdeb.net will have 2.1 posted in a few days and you won't have to worry about compile errors and the like.

[www.getdeb.net](www.getdeb.net)

---

### Post by cookieofdoom on 2007-07-31
Sorry, my bad on the typo. It's:

sudo apt-get libxss-dev

I'll edit my post above, too.

---

### Post by Kosimo on 2007-07-31
> **ThrobbingBrain66 said:**
> If you guys can wait a little while, getdeb.net will have 2.1 posted in a few days and you won't have to worry about compile errors and the like.

[www.get-deb.net](www.get-deb.net)


[http://www.getdeb.net](http://www.getdeb.net)  ;)

---

### Post by ThrobbingBrain66 on 2007-07-31
> **Kosimo said:**
> [http://www.getdeb.net](http://www.getdeb.net)  ;)

Thanks, corrected. :)

---

### Post by AaronMT on 2007-07-31
```
[strike]configure: error:

You must have the GTK+ 2.0 development headers installed to compile Pidgin.
If you only want to build Finch then specify --disable-gtkui when running configure.
```

How can I fix this so I can compile?[/strike]

Solved.

---

### Post by Old Pink on 2007-07-31
There's nothing new anyway. 120 previously unnoticeable bugs have been fixed. Big deal. 

Might look into it when on getdeb, but studied the roadmap, etc for ages, and not only is it almost a month late, there's not a single new feature worth getting excited about.

Poor show.

---

### Post by DC@DR on 2007-07-31
Right, nothing new and astonishing :-(

---

### Post by Kosimo on 2007-07-31
> **DC@DR said:**
> Right, nothing new and astonishing :-(

Well guys... I see some important differences, specially in the new chat window.

And about the new versions... People is always complaining..  We're having every new version a most stable bugfree pidgin guys. 
At the moment Pidgin is ok for me (I would like to have P2P transfers between MSN users anyway). But,  for now, I don't need any new feature. I want a solid/rock Program. If you have a look to pidgin developer roadmap (see above) you'll notice about the many bugs with a ticket assigned already and still waiting to be fixed. I prefer to have all this bugs fixed than add some new feature that give us more and more bugs.

---

### Post by Kosimo on 2007-07-31
By the way...
If you want a super fashioning with much more features and videoconference program. Use aMSN.

---

### Post by Old Pink on 2007-07-31
aMSN is ugly as sin. And has no support for AIM, ICQ, Jabber/XMPP Yahoo!, Bonjour, Gadu-Gadu, IRC, Novell GroupWise Messenger, QQ, Lotus Sametime, SILC, SIMPLE, or Zephyr.

---

### Post by jcrnan on 2007-07-31
I find it hard to get a IM to be like I want it to. I wish I could have all the features and customizability of aMsn and the looks and stability of pidgin :)

---

### Post by Old Pink on 2007-07-31
Review, Roundup, What's New: [http://www.mbhoy.com/01-08-2007/pidgin-210](http://www.mbhoy.com/01-08-2007/pidgin-210)

Working well for me, quite nice, nothing to get excited about though.

---

### Post by syxbit on 2007-07-31
considering sean egan works for google, you'd think he could get all the googleTalk features working (voice etc..)

---

### Post by fyllekajan on 2007-07-31
Yawn.. any audio/video conferencing capabilities this year!? it's their own fault starting the hype years ago.. talking a lot of... on the other hand they are doing a good job on this program.. for what it is.

---

### Post by theonlyalterego on 2007-07-31
I get this
```

You must have libxml2 >= 2.6.0 development headers installed to build.

```

I can't seem to find a ubuntu package with 2.6.0 or greater, has anyone made one?

---

### Post by Jerr973 on 2007-08-01
Ok I have tried everything managed compile and it's installed, not will not start, so giving up but how do I remove it now?

---

### Post by ike on 2007-08-01
> **apc15x said:**
> Well I downloaded pidgin 2.1.0 but I get an error:
...
configure: error: C compiler cannot create executables
See `config.log' for more details.
Can anybody help.
Thank in advance :(

Start with these:
[http://forums.gentoo.org/viewtopic.php?t=27486](http://forums.gentoo.org/viewtopic.php?t=27486)
[http://www.binrev.com/forums/index.php?showtopic=18678](http://www.binrev.com/forums/index.php?showtopic=18678)
[http://www.linuxquestions.org/questions/showthread.php?threadid=386790](http://www.linuxquestions.org/questions/showthread.php?threadid=386790)

and if unlucky, try:
[http://www.google.com/search?hl=sv&q=%22C+compiler+cannot+create+executables%22+ubuntu&btnG=S%C3%B6k&lr=](http://www.google.com/search?hl=sv&q=%22C+compiler+cannot+create+executables%22+ubuntu&btnG=S%C3%B6k&lr=)


edit: Also check your config.log

---

### Post by oliverb4ss on 2007-08-01
I just got the following error after issuing the command "./configure" :

The msgfmt command is required to build libpurple.  If it is installed
on your system, ensure that it is in your path.  If it is not, install
GNU gettext to continue.

What can I do about that?

---

### Post by fakie_flip on 2007-08-01
I have Pidgin 2.0.2-1 compiled. How can I get off the record plugin to work for it?

---

### Post by crhylove on 2007-08-01
getdeb.net is down.  Any other place where I can get a 2.1.0 .deb?

---

### Post by Kosimo on 2007-08-01
> **crhylove said:**
> getdeb.net is down.  Any other place where I can get a 2.1.0 .deb?

Is on again...

(But Pidgin 2.1.0 is not available yet)  Why don't you just try to compile by yourself? Is really easy.

---

### Post by foureight84 on 2007-08-01
is it just me or is 2.10 missing the tray icon?

---

### Post by Kosimo on 2007-08-02
> **foureight84 said:**
> is it just me or is 2.10 missing the tray icon?

No issues here.

How did u install it?

---

### Post by happy-and-lost on 2007-08-02
How come it's in the Debian Sid repos but not the Ubuntu Gutsy ones?

---

### Post by PartisanEntity on 2007-08-02
Cool thanks for the heads up, just installed it and am happy to see that it loads much faster than version 2.0.0

---

### Post by BW~Merlin on 2007-08-02
I have been trying to compile this for the last several hours and know matter what I try I keep getting these errors and I don't know how to fix them.  

In file included from /usr/include/gtk-2.0/gtk/gtkwidget.h:32,
                 from /usr/include/gtk-2.0/gtk/gtkcontainer.h:33,
                 from /usr/include/gtk-2.0/gtk/gtkbin.h:32,
                 from /usr/include/gtk-2.0/gtk/gtkwindow.h:33,
                 from /usr/include/gtk-2.0/gtk/gtkdialog.h:32,
                 from /usr/include/gtk-2.0/gtk/gtkaboutdialog.h:28,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from ../../../pidgin/pidgin.h:33,
                 from gestures.c:22:
/usr/include/gtk-2.0/gtk/gtkobject.h:85: error: expected specifier-qualifier-list before 'GInitiallyUnowned'
/usr/include/gtk-2.0/gtk/gtkobject.h:97: error: expected specifier-qualifier-list before 'GInitiallyUnownedClass'

Can someone please help me.

---

### Post by Kosimo on 2007-08-02
> **BW~Merlin said:**
> I have been trying to compile this for the last several hours and know matter what I try I keep getting these errors and I don't know how to fix them.  

In file included from /usr/include/gtk-2.0/gtk/gtkwidget.h:32,
                 from /usr/include/gtk-2.0/gtk/gtkcontainer.h:33,
                 from /usr/include/gtk-2.0/gtk/gtkbin.h:32,
                 from /usr/include/gtk-2.0/gtk/gtkwindow.h:33,
                 from /usr/include/gtk-2.0/gtk/gtkdialog.h:32,
                 from /usr/include/gtk-2.0/gtk/gtkaboutdialog.h:28,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from ../../../pidgin/pidgin.h:33,
                 from gestures.c:22:
/usr/include/gtk-2.0/gtk/gtkobject.h:85: error: expected specifier-qualifier-list before 'GInitiallyUnowned'
/usr/include/gtk-2.0/gtk/gtkobject.h:97: error: expected specifier-qualifier-list before 'GInitiallyUnownedClass'

Can someone please help me.


I'm not really sure about it...
But could be a problem with some GTK library. You can install it by synaptic if I'm not mistaken.  Search for GTK engines

---

### Post by BW~Merlin on 2007-08-02
As far as I am aware I have all the gtk engines installed.  Is there some sort of check for error's and missing componets that might help narrow down what is wrong?

---

### Post by bokibre on 2007-08-02
here it is .deb package!!

[http://www.debuntu.org/pidgin-2.1.0-for-ubuntu-feisty](http://www.debuntu.org/pidgin-2.1.0-for-ubuntu-feisty)

---

### Post by J-Wreck on 2007-08-02
I don't like the way it gets rid of several of the icons in the IM window. It was better when their were individual buttons for things like bold, etc.

---

### Post by ThrobbingBrain66 on 2007-08-02
[quote=J-Wreck]I don't like the way it gets rid of several of the icons in the IM window. It was better when their were individual buttons for things like bold, etc.[/quote]
Quoted for truth.

The package just got pushed through on Gutsy Testing and the chat window is hideous now.  Making the chat window a normal size gives tons of empty space on the formatting toolbar.

---

### Post by Kosimo on 2007-08-02
Getdeb is also offering pidgin 2.1.0  

[http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by vishzilla on 2007-08-03
You can include SSL support by including the following lines

```
./configure --enable-gnutls=yes
make
sudo make install
```

---

### Post by matteusz on 2007-08-12
> **foureight84 said:**
> is it just me or is 2.10 missing the tray icon?

Try this:
Tools->Preferences->Show system tray icon->Always

---

### Post by cdecarlo on 2007-08-17
> **vishzilla said:**
> You can include SSL support by including the following lines

```
./configure --enable-gnutls=yes
make
sudo make install
```

Thank you!

---

