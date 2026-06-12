---
title: "UbuntuOne and Software Center Not Working"
date: 2013-07-11
forum: Ubuntu Development Version
---

### Post by ping-wu on 2013-07-11
Updated yesterday.  Ubuntu One and Software Center stopped working.  Message from Ubuntu One was "IPCError".  Software Center just won't run at all.

Anyone else having same problem?

---

### Post by dino99 on 2013-07-11
follow that howto: [http://rtg.in.ua/2012/04/17/fixing-ipcerror-in-ubuntu-one/](http://rtg.in.ua/2012/04/17/fixing-ipcerror-in-ubuntu-one/)

---

### Post by OrangeCrate on 2013-07-11
> **ping-wu said:**
> Updated yesterday.  Ubuntu One and **Software Center stopped working**.  Message from Ubuntu One was "IPCError".  Software Center just won't run at all.

**Anyone else having same problem?**

Checking, I see that it doesn't work here either (Xubuntu 13.10). At some point it will again...

Frankly, though I don't have anything specific against the Software Center, I use Synaptic and apt-get on a day-to-day basis.

---

### Post by P-I H on 2013-07-11
Software Center works in my installation, which only have ppa:s for Spotify, Wine and My-Weather-Indicator. Ubuntu one didn't work this morning, but after these updates it is OK.
```
Commit Log for Thu Jul 11 09:56:04 2013

Upgraded the following packages:
account-plugin-facebook (0.11+13.10.20130628-0ubuntu1) to 0.11+13.10.20130711-0ubuntu1
account-plugin-flickr (0.11+13.10.20130628-0ubuntu1) to 0.11+13.10.20130711-0ubuntu1
account-plugin-google (0.11+13.10.20130628-0ubuntu1) to 0.11+13.10.20130711-0ubuntu1
account-plugin-twitter (0.11+13.10.20130628-0ubuntu1) to 0.11+13.10.20130711-0ubuntu1
account-plugin-windows-live (0.11+13.10.20130628-0ubuntu1) to 0.11+13.10.20130711-0ubuntu1
gir1.2-dee-1.0 (1.2.5ubuntu1+13.10.20130630-0ubuntu1) to 1.2.5ubuntu1+13.10.20130711-0ubuntu1
gir1.2-goa-1.0 (3.8.2-1) to 3.8.2-1ubuntu1
gir1.2-networkmanager-1.0 (0.9.8.0-0ubuntu14) to 0.9.8.0-0ubuntu15
gnome-orca (3.9.3-0ubuntu1) to 3.9.4-0ubuntu1
libaccount-plugin-generic-oauth (0.11+13.10.20130628-0ubuntu1) to 0.11+13.10.20130711-0ubuntu1
libaccount-plugin-google (0.11+13.10.20130628-0ubuntu1) to 0.11+13.10.20130711-0ubuntu1
libdee-1.0-4 (1.2.5ubuntu1+13.10.20130630-0ubuntu1) to 1.2.5ubuntu1+13.10.20130711-0ubuntu1
libgoa-1.0-0 (3.8.2-1) to 3.8.2-1ubuntu1
libgoa-1.0-common (3.8.2-1) to 3.8.2-1ubuntu1
libnm-glib-vpn1 (0.9.8.0-0ubuntu14) to 0.9.8.0-0ubuntu15
libnm-glib4 (0.9.8.0-0ubuntu14) to 0.9.8.0-0ubuntu15
libnm-util2 (0.9.8.0-0ubuntu14) to 0.9.8.0-0ubuntu15
libqpdf10 (4.2.0-1) to 4.2.0-2
libvisio-0.0-0 (0.0.28-1) to 0.0.30-1
network-manager (0.9.8.0-0ubuntu14) to 0.9.8.0-0ubuntu15
python-configglue (1.1.1-0ubuntu1) to 1.1.1.is.really.1.0-0ubuntu1
qpdf (4.2.0-1) to 4.2.0-2
qtdeclarative5-ubuntu-ui-toolkit-plugin (0.1.46+13.10.20130710.1-0ubuntu1) to 0.1.46+13.10.20130711-0ubuntu1
ubuntu-ui-toolkit-theme (0.1.46+13.10.20130710.1-0ubuntu1) to 0.1.46+13.10.20130711-0ubuntu1
```

---

### Post by ping-wu on 2013-07-12
Most recent update solved both problems.

---

### Post by ping-wu on 2013-07-14
Ubuntu One has been fixed (knock on wood!!!).  Looks like Software-Center is still under construction.

---

### Post by ping-wu on 2013-07-19
Software-Center fixed with the most recent update.  Ubuntu One was already fixed.

Houston, Saucy is ready for taking off!

---

### Post by pnarciso on 2013-07-20
> **ping-wu said:**
> Software-Center fixed with the most recent update.  Ubuntu One was already fixed.

Houston, Saucy is ready for taking off!

No really, it give me this error for days, since I update from raring to saucy:

2013-07-20 12:28:42,338 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-07-20 12:28:42,369 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.Geoclue.Error.notAvailable: Geoclue master client has no usable Address providers'
2013-07-20 12:28:42,507 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-07-20 12:28:42,508 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-07-20 12:28:42,510 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-07-20 12:28:42,510 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-07-20 12:28:42,532 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
/usr/share/software-center/softwarecenter/db/update.py:872: UnicodeWarning: Unicode unequal comparison failed to convert both arguments to Unicode - interpreting them as being unequal
  if untranslated_value != translated_value:
Traceback (most recent call last):
  File "/usr/bin/software-center", line 183, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1375, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1313, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 150, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 140, in init_view
    SoftwarePane.init_view(self)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/softwarepane.py", line 138, in init_view
    self.icons, self.show_ratings)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/appview.py", line 71, in __init__
    self.helper = AppPropertiesHelper(db, cache, icons)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/models/appstore2.py", line 112, in __init__
    self.all_categories = cat_parser.parse_applications_menu()
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 294, in parse_applications_menu
    LOG.debug("%s %s %s" % (cat.name, cat.iconname, cat.query))
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 5: ordinal not in range(128)

---

