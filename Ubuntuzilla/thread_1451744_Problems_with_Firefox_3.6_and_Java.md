---
title: "Problems with Firefox 3.6 and Java"
date: 2010-04-10
forum: Ubuntuzilla
---

### Post by joelgsf on 2010-04-10
My system is Ubuntu-Jaunty amd64. I have java-6 installed from Ubuntu and installed Firefox 3.6 with Ubuntuzilla (amd64). At the end of a "successful" instalation I ran firefox and got the messages:
> 
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so [/usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/amd64/libnpjp2.so [/usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/amd64/libnpjp2.so: wrong ELF class: ELFCLASS64]
...
and many more.

I've looked at Ubuntuzilla Wiki and here in this forum, but all solutions proposed failed - "update-alternatives" and "setting manually" the links for the plugins.
What else can I do? It seems that there is some incompatibility with the 64-bits java (and others) plugins with Ubuntuzilla/Firefox 3.6. The plugins are there, where they are pointed at.
Any help will be extremely welcome.
Many thanks,

Joel Guilherme

---

### Post by nanotube on 2010-04-11
hi
yes, ubuntuzilla installs only 32bit versions, so you have to do some tinkering to get 32bit plugins.

for 64bit your best bet is to use the firefox-stable repository, rather than fiddling around with the old ubuntuzilla installer script.

here's a linky: [https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable)

---

### Post by joelgsf on 2010-04-11
Hello nanotube,

Thanks for the information but, it is really weird that Ubuntuzilla, itself, offers both options - 32 and 64 bits.
Thanks anyway. I'll stick to the official version, till Ubuntuzilla eventually comes to cover Firefox-64.

Joel Guilherme

---

