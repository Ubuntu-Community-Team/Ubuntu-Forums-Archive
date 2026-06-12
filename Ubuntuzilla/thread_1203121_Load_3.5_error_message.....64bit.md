---
title: "Load 3.5 error message.....64bit"
date: 2009-07-03
forum: Ubuntuzilla
---

### Post by bishoptf on 2009-07-03
Ran the script and everything completed fine, I can continue to run the ubuntu version, but when I try to run 3.5 I get this error message:

/opt/firefox/firefox-bin: error while loading shared libraries: libdbus-glib-1.so.2: cannot open shared object file: No such file or directory


It appears to be a problem with the 32bit libs, found some ideas but no luck, running 64bit hardy...with nvidia display drivers.  Any suggestions would be great thanks, btw I had the ppa edition working fine just haven;t been able to get the ubuntuzilla 3.5 one to work....Thanks.

---

### Post by bollix47 on 2009-07-24
Is there a solution to this problem?

I just used ubuntuzilla to install firefox 3.5.1.  

The installation appeared to work fine but when I try to run firefox I get the same message concerning libdbus-glib-1.so.2.

---

### Post by nanotube on 2009-07-24
hmm, i don't have any 64bit system to try this on, so hard for me to figure out what's up. can you look around in synaptic for packages that seem related to glib and 32bit compatibility?

---

### Post by bollix47 on 2009-07-24
I was able to get it to start by:

```
:/opt/firefox$ sudo ln -s /usr/lib32/libglib-2.0.so.0 libdbus-glib-1.so.2

```

However, it would only start once.  After a close and restart the error message was:

```
/opt/firefox/firefox-bin: symbol lookup error: /opt/firefox/components/libdbusservice.so: undefined symbol: dbus_connection_setup_with_g_main
```

If I open up 3.0.12 firefox and then close it firefox 3.5.1 will again start 1 time only but all the plugins show errors:



```
LoadPlugin: failed to initialize shared library libXt.so [libXt.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library libXext.so [libXext.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/libnullplugin.so [/usr/lib/xulrunner-addons/plugins/libnullplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/libunixprintplugin.so [/usr/lib/xulrunner-addons/plugins/libunixprintplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-basic-plugin.so [/usr/lib/totem/gstreamer/libtotem-basic-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-complex-plugin.so [/usr/lib/totem/gstreamer/libtotem-complex-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-cone-plugin.so [/usr/lib/totem/gstreamer/libtotem-cone-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so [/usr/lib/totem/gstreamer/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-mully-plugin.so [/usr/lib/totem/gstreamer/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so [/usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so [/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so [/usr/lib/mozilla/plugins/mplayerplug-in-dvx.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/mplayerplug-in-qt.so [/usr/lib/mozilla/plugins/mplayerplug-in-qt.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/mplayerplug-in-rm.so [/usr/lib/mozilla/plugins/mplayerplug-in-rm.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so [/usr/lib/mozilla/plugins/mplayerplug-in-wmp.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/mplayerplug-in.so [/usr/lib/mozilla/plugins/mplayerplug-in.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so [/usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so [/usr/lib/mozilla/plugins/mplayerplug-in-dvx.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/mplayerplug-in-qt.so [/usr/lib/mozilla/plugins/mplayerplug-in-qt.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/mplayerplug-in-rm.so [/usr/lib/mozilla/plugins/mplayerplug-in-rm.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so [/usr/lib/mozilla/plugins/mplayerplug-in-wmp.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/mplayerplug-in.so [/usr/lib/mozilla/plugins/mplayerplug-in.so: wrong ELF class: ELFCLASS64]
/
```

Seems like it's trying to call 64-bit xulrunner/plugins which doesn't seem to work well on a 32-bit firefox.  ](*,)

So I guess the question is "Is this supposed to work on 64-bit ubuntu?".

---

### Post by bollix47 on 2009-07-24
I'm guessing not after seeing this post:

[http://ubuntuforums.org/showpost.php?p=7630889&postcount=26](http://ubuntuforums.org/showpost.php?p=7630889&postcount=26)

---

### Post by nanotube on 2009-07-24
> **bollix47 said:**
> I'm guessing not after seeing this post:

[http://ubuntuforums.org/showpost.php?p=7630889&postcount=26](http://ubuntuforums.org/showpost.php?p=7630889&postcount=26)

indeed, running the mozilla build on a 64bit system is a bit of a hack, but that's all we can do because mozilla doesn't make a 64bit build.

---

### Post by ThAixStYLe on 2009-09-21
This is very interesting.  I've just installed Ubuntuzilla on my 64 bit 9.04, so I'm running 32 bit FF and need 32 bit plugins.  Followed instructions on installing Flash and Java, but have now come to a dead end when it comes to the movie player (totem) plugin (needed for playing Windows Media content on some web pages) as well as some other plugins,  like moonlight.

Any idea how to get the 32 bit versions of these plugins and how to get them working?  The Ubuntuzilla FAQ has instructions for extracting the libflashplayer.so from the official Adobe package and there is a command for installing 32 bit JAVA from the terminal.  Anyone know how to choose which version (32 bit or 64 bit) of any other plugins we want to install?

Sorry for the noob question, just felt that it needs to be asked.

---

### Post by jsland on 2009-11-12
Please forgive this for being only a general answer.  I was having the same issue a few months back.  If my dim memory serves me you install/update flashplayer and the videos on websites, like reuters news clips, will work on a 64 bit machine.  Something about not all the parts of flashplayer being there in spite of going thru an initial install.

---

### Post by cooksw74 on 2010-03-28
bollix47,
 I had the same error message after creating the link you suggested (and opening firefox a second time).
 I was able to fix this problem by simply removing the file:
```
rm /usr/lib/firefox/components/libdbusservice.so
```

Apparently, firefox doesn't need this file to run (this may bite me in the butt later on, but it's working for now).

How this helps!;)

---

