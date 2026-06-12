---
title: "Not able to write a review (GLib error)"
date: 2015-04-18
forum: Ubuntu Development Version
---

### Post by enricobe on 2015-04-18
I can't write a new review on the Software Center. Xubuntu 15.04. I write here before open a new bug report on Launchpad because I don't know if this is expected in Xubuntu. I don't remeber to have done the login to my Ubuntu One account and no window appeared to let me do the login.

When I click on "Write a new review", nothing happens. Launching software-center from the terminal, the following error appears when I press the "Write a new review" button:
```
(software-center:5306): Gtk-WARNING **: Unable to show 'none': Operazione non supportata
2015-04-18 09:21:21,695 - softwarecenter.backend.spawn_helper - WARNING - exit code 1 from helper for '['/usr/share/software-center/submit_review_gtk3.py', '--pkgname', 'openshot', '--iconname', 'openshot', '--parent-xid', '', '--version', '1.4.3-1.1', '--origin', 'ubuntu', '--datadir', '/usr/share/software-center/', '--appname', 'OpenShot Video Editor']'
2015-04-18 09:21:21,695 - softwarecenter.backend.spawn_helper - WARNING - got error from helper: 'Traceback (most recent call last):
  File "/usr/share/software-center/submit_review_gtk3.py", line 117, in <module>
    version=options.version)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/review_gui_helper.py", line 595, in __init__
    BaseApp.__init__(self, datadir, "submit_review.ui")
  File "/usr/share/software-center/softwarecenter/ui/gtk3/review_gui_helper.py", line 382, in __init__
    self, os.path.join(datadir, "ui/gtk3", uifile), "software-center")
  File "/usr/share/software-center/softwarecenter/ui/gtk3/SimpleGtkbuilderApp.py", line 32, in __init__
    self.builder.add_from_file(path)
GLib.Error: gtk-builder-error-quark: Proprietà non valida: GtkGrid.n_rows alla riga 409 (11)
'
/usr/bin/software-center:184: Warning: Source ID 2536 was not found when attempting to remove it
  Gtk.main()
```

Should I report it in Launchpad?

---

### Post by dino99 on 2015-04-18
here is the error: (software-center:5306): Gtk-WARNING **: Unable to show 'none': Operazione non supportata

needs to be reported against software-center

---

### Post by enricobe on 2015-04-18
> **9d9 said:**
> here is the error: (software-center:5306): Gtk-WARNING **: Unable to show 'none': Operazione non supportata

needs to be reported against software-center

Thank you!

---

