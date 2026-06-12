---
title: "errors running ubuntuzilla on gutsy 64"
date: 2007-11-02
forum: Ubuntuzilla
---

### Post by cybergalvez on 2007-11-02
when I run ubuntuzilla on gusty 64 I get the following errors:
LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/libunixprintplugin.so [/usr/lib/firefox/plugins/libunixprintplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so [/usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /home/jc/.mozilla/plugins/npwrapper.libflashplayer.so [/home/jc/.mozilla/plugins/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/libunixprintplugin.so [/usr/lib/firefox/plugins/libunixprintplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so [/usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /home/jc/.mozilla/plugins/npwrapper.libflashplayer.so [/home/jc/.mozilla/plugins/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]


What do they mean and more importantly how do I fix them - did I do something wrong when I installed ubuntuzilla?

Jose
Jose

---

### Post by cybergalvez on 2007-11-02
OK I get it now - I really need to read things better.  Ubuntuzilla installs the 32bit version of firefox because thats what modzilla puts out, ubuntu installs a 64bit version of firefox so my plugins git messed up.  I get it
Jose

---

