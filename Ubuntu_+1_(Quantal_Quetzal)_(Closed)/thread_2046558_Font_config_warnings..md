---
title: "Font config warnings."
date: 2012-08-23
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Hreinsi on 2012-08-23
Get this error running from terminal

laptop@laptop:~$ sudo software-properties-gtk
[sudo] password for laptop: 
Fontconfig warning: "/etc/fonts/conf.d/65-droid-sans-fonts.conf", line 103: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/65-droid-sans-fonts.conf", line 138: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/69-language-selector-ja-jp.conf", line 141: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/69-language-selector-zh-tw.conf", line 79: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 26: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 31: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 40: Having multiple values in <test> isn't supported and may not works as expected
gpg: /tmp/tmpdodr9s/trustdb.gpg: trustdb created
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 103, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 180, in __init__
    self.show_drivers()
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 1280, in show_drivers
    widget = Gtk.Label("{}: {}".format(self.devices[device]['vendor'], self.devices[device]['model']))
KeyError: 'vendor'

---

### Post by philinux on 2012-08-23
Split to own thread.  Try running 

sudo fc-cache -f -v

I ended up deleting those fonts.

---

### Post by VinDSL on 2012-08-23
See [http://ubuntuforums.org/showpost.php?p=12159762&postcount=13](http://ubuntuforums.org/showpost.php?p=12159762&postcount=13)

---

### Post by philinux on 2012-08-23
+1 Vin but I'm reinstalling once the daily is sorted.

---

### Post by fjgaude on 2012-08-23
> **philinux said:**
> +1 Vin but I'm reinstalling once the daily is sorted.

Me too.

Boy but we see the progress being made to Unity working with just about any modern hardware!

---

### Post by Hreinsi on 2012-08-23
ok thx i will take a look later litle busy :)

---

