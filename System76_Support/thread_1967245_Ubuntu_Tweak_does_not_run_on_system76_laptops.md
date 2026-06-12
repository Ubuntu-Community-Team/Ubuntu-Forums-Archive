---
title: "Ubuntu Tweak does not run on system76 laptops??"
date: 2012-04-27
forum: System76 Support
---

### Post by Arioch on 2012-04-27
Just filed in a bug in launchpad.
I have one Dell XPS1530 running Ubuntu 12.04, after installing Ubuntu-tweak it works perfectly.

On my second machine, a Gazelle (gazp6) System76 laptop running the latest system76 driver 2.7.4 Ubuntu tweak crashes upon launching. I am pasting the terminal output from Ubuntu-tweak -d ([COLOR="Red"]please note last line on the trace output[/COLOR])

[Launcher][DEBUG] Distribution: Ubuntu 12.04 precise
Application: Ubuntu Tweak 0.7.0-1~precise4
Desktop:ubuntu (ubuntu-tweak:68)
[gtk][DEBUG] <function post_ui at 0x1c64b18>: (debug.py:179)
[gtk][DEBUG] 	args-1: <function on_find_object at 0x1ee8d70> (debug.py:181)
[gtk][DEBUG] <function post_ui at 0x1c64b18>: (debug.py:179)
[gtk][DEBUG] 	args-1: <function on_scan_finished at 0x1ee8ed8> (debug.py:181)
[gtk][DEBUG] <function post_ui at 0x1c64b18>: (debug.py:179)
[gtk][DEBUG] 	args-1: <function on_scan_error at 0x1ee9050> (debug.py:181)
[gtk][DEBUG] <function post_ui at 0x1c64b18>: (debug.py:179)
[gtk][DEBUG] 	args-1: <function on_plugin_object_cleaned at 0x1ee9320> (debug.py:181)

(ubuntu-tweak:11391): GConf-WARNING **: : You can't use a GConfEngine that has an active GConfClient wrapper object. Use GConfClient API instead.

(ubuntu-tweak:11391): GConf-WARNING **: : You can't use a GConfEngine that has an active GConfClient wrapper object. Use GConfClient API instead.
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
[gtk][DEBUG] <function post_ui at 0x1c64b18>: (debug.py:179)
[gtk][DEBUG] 	args-1: <function _load_module at 0x208dc08> (debug.py:181)
Traceback (most recent call last):
  File "/usr/bin/ubuntu-tweak", line 124, in <module>
    window = UbuntuTweakWindow(feature=options.feature, module=options.module, splash_window=splash_window)
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/main.py", line 305, in __init__
    tweaks_page = FeaturePage('tweaks')
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/main.py", line 166, in __init__
    self._setting = GSetting('com.ubuntu-tweak.tweak.%s' % feature_name)
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/settings/gsettings.py", line 19, in __init__
    self.schema_default = self.default or Schema.load_schema(self.schema_id, self.key)
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/settings/common.py", line 105, in load_schema
    cls.load_override()
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/settings/common.py", line 96, in load_override
    cs = RawConfigSetting(override)
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/settings/common.py", line 17, in __init__
    self.init_configparser()
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/settings/common.py", line 48, in init_configparser
    self._configparser.read(self._path)
  File "/usr/lib/python2.7/ConfigParser.py", line 305, in read
    self._read(fp, filename)
  File "/usr/lib/python2.7/ConfigParser.py", line 546, in _read
    raise e
[COLOR="Red"]ConfigParser.ParsingError: File contains parsing errors: /usr/share/glib-2.0/schemas/system76-touchpad.gschema.override[/COLOR]
	[line  2]: '  horiz-scroll-enabled=true\n'
	[line  3]: '  scroll-method="two-finger-scrolling"\n'


Hope between the system76 folks and Ubuntu-tweak folks in launchpad this can be fixed soon.

Thanks

---

### Post by Arioch on 2012-04-28
Here is the launchpad link. There seems to be some formating issue on the system76 config file according to Ubuntu-tweak devs, but they will fix it in the next maintenance version.

[https://bugs.launchpad.net/ubuntu-tweak/+bug/990270](https://bugs.launchpad.net/ubuntu-tweak/+bug/990270)

---

### Post by kkaldroma on 2012-05-07
As the solution was not painfully obvious and us 76rs need to look out for the youngins, here is how to fix this issue.

Go to the file
 /usr/share/glib-2.0/schemas/system76-touchpad.gschema.override

Open it using Gedit, vim, vi, nano (whatever). [terminal $ gedit /usr/share/glib-2.0/schemas/system76-touchpad.gschema.override]

Then delete all of the spaces in front of all of the lines of text.
"      horiz-scroll-enabled=true" 
should become
"horiz-scroll-enabled=true"

and so on....

Done.

---

### Post by Arioch on 2012-05-07
Yeap, that is correct. The Ubuntu-tweak folks were really helpful and fast in finding a fix for that bug...although System76's did not seem to care at all that their driver brings conflicts with other mainstream applications in ubuntu.

Like the ugly oversized ubuntu logo at start up. Out of 3 machines with Nvidia cards running ubuntu 12.04, the sys76 is the only one with the ugly logo (low resolution) whereas the other two show a nifty well defined logo. The 3 of them use propietary nvidia drivers. After installing 12.04 on the 76 machine the logo was fine, but after restoring the sys76 driver the logo went back to the ugly low res mode.

not saying sys76 driver is the ultimate cause, i dont know, chances are high since i did nothing more on that machine to get that behavior.

---

