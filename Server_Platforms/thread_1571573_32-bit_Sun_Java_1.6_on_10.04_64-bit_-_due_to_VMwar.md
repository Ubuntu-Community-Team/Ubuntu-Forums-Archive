---
title: "32-bit Sun Java 1.6 on 10.04 64-bit - due to VMware"
date: 2010-09-09
forum: Server Platforms
---

### Post by IQRules on 2010-09-09
Is there a proper way to install 32-bit Firefox 3.5.11 with Sun Java 1.6.0 on 64-bit Lucid 10.04 Ubuntu?

I want to run VMWare guest on Lucid and 64-bit Firefox 3.6.9 has issue with VMware.

Thanks

---

### Post by lovinglinux on 2010-09-10
Why do you want to run a 32bit Firefox on a 64 bit system?

What kind of issue you are experiencing with Firefox 3.6.9 on a VM? All versions work for me.

---

### Post by IQRules on 2010-09-10
> **lovinglinux said:**
> Why do you want to run a 32bit Firefox on a 64 bit system?

What kind of issue you are experiencing with Firefox 3.6.9 on a VM? All versions work for me.

Check this link,

[http://ubuntuforums.org/showthread.php?p=9389902&mode=linear#post9389902](http://ubuntuforums.org/showthread.php?p=9389902&mode=linear#post9389902)

Cannot access virtual machine console. Request timed out.
The attempt to acquire valid session ticket for "xxxxxx" took longer than expected. If this problem persists blah blah blah

Now I faced a new problem.

~/.mozilla/plugins$ firefox-old
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so [/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so: wrong ELF class: ELFCLASS64]


I like Ubuntu GUI. But CentOS 5.5 is easier on handling 32-bit FireFox on 64-bit box.

---

### Post by lovinglinux on 2010-09-12
> **IQRules said:**
> Now I faced a new problem.

~/.mozilla/plugins$ firefox-old
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so [/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so: wrong ELF class: ELFCLASS64]

That's the problem of using a 32bit version on 64 bit. It can't use the plugins. You need to download the plugins for 32 bit and put inside the ~/.mozilla/plugins folder. never tried tho.

---

