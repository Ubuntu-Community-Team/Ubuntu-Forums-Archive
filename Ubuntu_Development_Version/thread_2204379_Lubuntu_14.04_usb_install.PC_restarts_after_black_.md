---
title: "Lubuntu 14.04 usb install.PC restarts after black screen at boot"
date: 2014-02-08
forum: Ubuntu Development Version
---

### Post by e71067 on 2014-02-08
[IMG]http://ibin.co/1BcvDJ7qB5id[/IMG]
Im not using the windows usb partition.I only need it as backup iso.SWAP turned into unknown (why?)I install onto ext4. When Im installing I select encrypt Lubuntu installation for security and use LVM wtih the new Lubuntu installation.



all goes as it should so why wont it boot? (I just get black screen for few seconds and a reboot plz help)

Maybe logs might help?   /var/log/installer   logs 

_**casper.log**_
```
calling: test-builtin
error reading /lib/udev/hwdb.bin: No such file or directory
load module index
unload module index
Generating locales...
  en_US.UTF-8... done
Generation complete.
pwconv: failed to change the mode of /etc/passwd- to 0600
Using CD-ROM mount point /cdrom/
Identifying.. [b5bcadc1b4f19a53ce396974cfa9fe96-2]
Scanning disc for index files..
Found 4 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
Found label 'Lubuntu 14.04 _Trusty Tahr_ - Alpha amd64 (20140110)'
This disc is called: 
'Lubuntu 14.04 _Trusty Tahr_ - Alpha amd64 (20140110)'
Copying package lists...gpgv: Signature made Fri Jan 10 17:49:40 2014 UTC using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
 Reading Package Indexes... 0%  Reading Package Indexes... Done 
Writing new source list
Source list entries for this disc are:
deb cdrom:[Lubuntu 14.04 _Trusty Tahr_ - Alpha amd64 (20140110)]/ trusty main multiverse restricted universe
Repeat this process for the rest of the CDs in your set.
```

_**Debug**_
```
Ubiquity 2.17.3

(ubiquity:4668): Pango-WARNING **: error opening config file '/root/.config/pango/pangorc': Permission denied

/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:284: PyGTKDeprecationWarning: Using positional arguments with the GObject constructor has been deprecated. Please specify keywords for label or use a class specific constructor. See: [https://wiki.gnome.org/PyGObject/InitializerDeprecations](https://wiki.gnome.org/PyGObject/InitializerDeprecations)
  self.password_label = Gtk.Label('Password:')
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:288: PyGTKDeprecationWarning: Using positional arguments with the GObject constructor has been deprecated. Please specify keywords for label or use a class specific constructor. See: [https://wiki.gnome.org/PyGObject/InitializerDeprecations](https://wiki.gnome.org/PyGObject/InitializerDeprecations)
  self.display_password = Gtk.CheckButton('Display password')

(ubiquity:4668): Gtk-CRITICAL **: gtk_radio_button_set_group: assertion '!g_slist_find (group, radio_button)' failed

(ubiquity:4668): Gtk-CRITICAL **: gtk_radio_button_set_group: assertion '!g_slist_find (group, radio_button)' failed
/usr/lib/python3/dist-packages/gi/overrides/GLib.py:660: PyGIDeprecationWarning: Calling io_add_watch without priority as second argument is deprecated
  PyGIDeprecationWarning)
update_release_notes_label()
update_release_notes_label()

(ubiquity:4668): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed

(ubiquity:4668): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed

(ubiquity:4668): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed
/usr/lib/ubiquity/plugins/ubi-partman.py:893: PyGTKDeprecationWarning: Using positional arguments with the GObject constructor has been deprecated. Please specify keywords for label or use a class specific constructor. See: [https://wiki.gnome.org/PyGObject/InitializerDeprecations](https://wiki.gnome.org/PyGObject/InitializerDeprecations)
  new_item = Gtk.MenuItem(self.controller.get_string(widget))
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
No such schema 'org.gnome.settings-daemon.plugins.power'
Ubiquity 2.17.3

(ubiquity:9543): Pango-WARNING **: error opening config file '/root/.config/pango/pangorc': Permission denied

/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:284: PyGTKDeprecationWarning: Using positional arguments with the GObject constructor has been deprecated. Please specify keywords for label or use a class specific constructor. See: [https://wiki.gnome.org/PyGObject/InitializerDeprecations](https://wiki.gnome.org/PyGObject/InitializerDeprecations)
  self.password_label = Gtk.Label('Password:')
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:288: PyGTKDeprecationWarning: Using positional arguments with the GObject constructor has been deprecated. Please specify keywords for label or use a class specific constructor. See: [https://wiki.gnome.org/PyGObject/InitializerDeprecations](https://wiki.gnome.org/PyGObject/InitializerDeprecations)
  self.display_password = Gtk.CheckButton('Display password')

(ubiquity:9543): Gtk-CRITICAL **: gtk_radio_button_set_group: assertion '!g_slist_find (group, radio_button)' failed

(ubiquity:9543): Gtk-CRITICAL **: gtk_radio_button_set_group: assertion '!g_slist_find (group, radio_button)' failed
/usr/lib/python3/dist-packages/gi/overrides/GLib.py:660: PyGIDeprecationWarning: Calling io_add_watch without priority as second argument is deprecated
  PyGIDeprecationWarning)
update_release_notes_label()
update_release_notes_label()

(ubiquity:9543): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed

(ubiquity:9543): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed

(ubiquity:9543): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
No such schema 'org.gnome.settings-daemon.plugins.power'
Ubiquity 2.17.3

(ubiquity:13297): Pango-WARNING **: error opening config file '/root/.config/pango/pangorc': Permission denied

/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:284: PyGTKDeprecationWarning: Using positional arguments with the GObject constructor has been deprecated. Please specify keywords for label or use a class specific constructor. See: [https://wiki.gnome.org/PyGObject/InitializerDeprecations](https://wiki.gnome.org/PyGObject/InitializerDeprecations)
  self.password_label = Gtk.Label('Password:')
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:288: PyGTKDeprecationWarning: Using positional arguments with the GObject constructor has been deprecated. Please specify keywords for label or use a class specific constructor. See: [https://wiki.gnome.org/PyGObject/InitializerDeprecations](https://wiki.gnome.org/PyGObject/InitializerDeprecations)
  self.display_password = Gtk.CheckButton('Display password')

(ubiquity:13297): Gtk-CRITICAL **: gtk_radio_button_set_group: assertion '!g_slist_find (group, radio_button)' failed

(ubiquity:13297): Gtk-CRITICAL **: gtk_radio_button_set_group: assertion '!g_slist_find (group, radio_button)' failed
/usr/lib/python3/dist-packages/gi/overrides/GLib.py:660: PyGIDeprecationWarning: Calling io_add_watch without priority as second argument is deprecated
  PyGIDeprecationWarning)
update_release_notes_label()
update_release_notes_label()

(ubiquity:13297): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed

(ubiquity:13297): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed

(ubiquity:13297): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed

(ubiquity:13297): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed

(ubiquity:13297): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed

(ubiquity:13297): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed
/usr/lib/ubiquity/plugins/ubi-partman.py:893: PyGTKDeprecationWarning: Using positional arguments with the GObject constructor has been deprecated. Please specify keywords for label or use a class specific constructor. See: [https://wiki.gnome.org/PyGObject/InitializerDeprecations](https://wiki.gnome.org/PyGObject/InitializerDeprecations)
  new_item = Gtk.MenuItem(self.controller.get_string(widget))

(ubiquity:13297): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed

(ubiquity:13297): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed

(ubiquity:13297): Gtk-CRITICAL **: gtk_widget_set_allocation: assertion 'gtk_widget_get_visible (widget) || gtk_widget_is_toplevel (widget)' failed
No such schema 'com.canonical.indicator.session'
No such schema 'com.canonical.indicator.session'
No such schema 'com.canonical.indicator.session'
No such schema 'com.canonical.indicator.session'
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/keyboard_query.py:59: PyGTKDeprecationWarning: Stock items are deprecated. Please use: Gtk.Button.new_with_mnemonic(label)
  no = Gtk.Button(stock=Gtk.STOCK_NO)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/keyboard_query.py:60: PyGTKDeprecationWarning: Stock items are deprecated. Please use: Gtk.Button.new_with_mnemonic(label)
  yes = Gtk.Button(stock=Gtk.STOCK_YES)
/usr/lib/ubiquity/plugins/ubi-console-setup.py:116: Warning: Source ID 6426 was not found when attempting to remove it
  GLib.source_remove(self.keyboard_layout_timeout_id)
/usr/lib/ubiquity/plugins/ubi-console-setup.py:116: Warning: Source ID 7751 was not found when attempting to remove it
  GLib.source_remove(self.keyboard_layout_timeout_id)
/usr/lib/ubiquity/plugins/ubi-console-setup.py:138: Warning: Source ID 6429 was not found when attempting to remove it
  GLib.source_remove(self.keyboard_variant_timeout_id)
/usr/lib/ubiquity/plugins/ubi-console-setup.py:116: Warning: Source ID 7794 was not found when attempting to remove it
  GLib.source_remove(self.keyboard_layout_timeout_id)
/usr/lib/ubiquity/plugins/ubi-console-setup.py:116: Warning: Source ID 8739 was not found when attempting to remove it
  GLib.source_remove(self.keyboard_layout_timeout_id)
/usr/lib/ubiquity/plugins/ubi-console-setup.py:138: Warning: Source ID 7825 was not found when attempting to remove it
  GLib.source_remove(self.keyboard_variant_timeout_id)
/usr/lib/ubiquity/plugins/ubi-console-setup.py:72: Warning: Source ID 8843 was not found when attempting to remove it
  GLib.source_remove(self.keyboard_layout_timeout_id)
/usr/lib/ubiquity/plugins/ubi-console-setup.py:74: Warning: Source ID 8878 was not found when attempting to remove it
  GLib.source_remove(self.keyboard_variant_timeout_id)
/usr/lib/ubiquity/plugins/ubi-usersetup.py:408: Warning: Source ID 9742 was not found when attempting to remove it
  GLib.source_remove(self.hostname_timeout_id)
/usr/lib/ubiquity/plugins/ubi-usersetup.py:408: Warning: Source ID 9748 was not found when attempting to remove it
  GLib.source_remove(self.hostname_timeout_id)
/usr/lib/ubiquity/plugins/ubi-usersetup.py:408: Warning: Source ID 9759 was not found when attempting to remove it
  GLib.source_remove(self.hostname_timeout_id)

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

(ubiquity:13297): dconf-CRITICAL **: unable to create directory '/root/.cache/dconf': Not a directory.  dconf will not work properly.

```
[U][B]
media-info[/B][/U]
```
Lubuntu 14.04 "Trusty Tahr" - Alpha amd64 (20140110)
```

_**partman**_
```
/bin/partman: *******************************************************
/lib/partman/init.d/30parted: *******************************************************
parted_server: ======= Starting the server
parted_server: main_loop: iteration 1
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sda /dev/sda
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sda
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sda as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 2
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sdb /dev/sdb
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sdb
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sdb as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 3
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    65536-2052521983    2052456448    primary    fat16    /dev/sda1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 4
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: CLOSE =dev=sda
parted_server: Read command: CLOSE
parted_server: command_close()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 5
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 6
parted_server: Opening infifo
/lib/partman/init.d/35dump: *******************************************************
/lib/partman/init.d/35dump: IN: DUMP =dev=sdb
parted_server: Read command: DUMP
parted_server: command_dump()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 7
parted_server: Opening infifo
Device: yes
Model: Kingston DataTraveler 3.0
Path: /dev/sdb
Sector size: 512
Sectors: 31293440
Sectors/track: 63
Heads: 255
Cylinders: 1947
Partition table: yes
Type: msdos
Partitions: #    id    length    type    fs    path    name
(0,0,0)    (0,0,62)    -1    0-32255    32256    primary    label    /dev/sdb-1    
(0,1,0)    (481,113,53)    1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    
(481,113,54)    (481,127,27)    -1    3960032256-3960470527    438272    pri/log    free    /dev/sdb-1    
(481,127,28)    (1686,149,62)    2    3960470528-13872660479    9912189952    primary    extended    /dev/sdb2    
(481,127,28)    (481,127,29)    -1    3960470528-3960471551    1024    logical    label    /dev/sdb-1    
(481,127,30)    (1686,149,62)    5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    
(1686,150,0)    (1947,236,16)    -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    
Dump finished.
/lib/partman/init.d/50biosgrub: *******************************************************
/lib/partman/init.d/50biosgrub: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 8
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 32256-3960032255
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3960032255)
parted_server: Partition found (32256-3960032255)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 9
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 3960471552-13872660479
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3960471552-13872660479)
parted_server: Partition found (3960471552-13872660479)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 10
parted_server: Opening infifo
/lib/partman/init.d/50lvm: *******************************************************
/lib/partman/init.d/50lvm: *******************************************************
/lib/partman/init.d/50lvm: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 11
parted_server: Opening infifo
/lib/partman/init.d/50lvm: IN: GET_FLAGS =dev=sdb 32256-3960032255
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3960032255)
parted_server: Partition found (32256-3960032255)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 12
parted_server: Opening infifo
/lib/partman/init.d/50lvm: IN: GET_FLAGS =dev=sdb 3960471552-13872660479
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3960471552-13872660479)
parted_server: Partition found (3960471552-13872660479)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 13
parted_server: Opening infifo
/lib/partman/init.d/52crypto: *******************************************************
/lib/partman/init.d/52crypto: *******************************************************
/lib/partman/init.d/52crypto: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 14
parted_server: Opening infifo
/lib/partman/init.d/70update_partitions: *******************************************************
/lib/partman/init.d/70update_partitions: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 15
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 32256-3960032255
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3960032255)
parted_server: Partition found (32256-3960032255)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 16
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sdb 32256-3960032255
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 32256-3960032255
parted_server: partition_with_id(32256-3960032255)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7734437)
parted_server: no
parted_server: OUT: ntfs


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 17
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 32256-3960032255
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3960032255)
parted_server: Partition found (32256-3960032255)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 18
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 19
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 32256-3960032255
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3960032255)
parted_server: Partition found (32256-3960032255)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 20
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 21
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 22
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 3960471552-13872660479
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3960471552-13872660479)
parted_server: Partition found (3960471552-13872660479)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 23
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sdb 3960471552-13872660479
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7735296,27095039)
parted_server: no
parted_server: OUT: ext4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 24
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 3960471552-13872660479
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3960471552-13872660479)
parted_server: Partition found (3960471552-13872660479)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 25
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 26
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 3960471552-13872660479
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3960471552-13872660479)
parted_server: Partition found (3960471552-13872660479)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 27
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 28
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 29
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 30
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 31
parted_server: Opening infifo
/lib/partman/init.d/75auto_mountpoints: *******************************************************
/lib/partman/init.d/80autouse_swap: *******************************************************
/lib/partman/init.d/80autouse_swap: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 32
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    
parted_server: main_loop: iteration 33
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 34
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sdb
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 35
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: 1 primary partitions, 1 logical partitions
/lib/partman/automatically_partition/10resize_use_free/choices: filtered partition list:
/lib/partman/automatically_partition/10resize_use_free/choices: 1 32256-3960032255 3960000000 primary ntfs /dev/sdb1 
5 3960471552-13872660479 9912188928 logical ext4 /dev/sdb5 
-1 13872660480-16022241279 2149580800 pri/log free /dev/sdb-1 
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 32256-3960032255
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3960032255
parted_server: partition_with_id(32256-3960032255)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7734437)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 36
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 32256-3960032255
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3960032255)
parted_server: OUT: OK


parted_server: OUT: 512 3960000000 3960438272


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 37
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 3960471552-13872660479
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7735296,27095039)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 38
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 3960471552-13872660479
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: OUT: 512 9912188928 12061769728


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 39
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sdb', totalfree: '2149580800', diskfree: '6789713920', diskpart: '/var/lib/partman/devices/=dev=sdb//3960471552-13872660479', diskpath: '/dev/sdb5'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sdb//3960471552-13872660479' (/dev/sdb5) with 6789713920 bytes free
/lib/partman/automatically_partition/15reuse/choices: *******************************************************
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 40
parted_server: Opening infifo
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 41
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 42
parted_server: Opening infifo
/lib/partman/automatically_partition/60some_device_lvm/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: VIRTUAL =dev=sdb 3960471552-13872660479
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7735296,27095039)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 43
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 3960471552-13872660479
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: OUT: 512 9912188928 12061769728


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 44
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: PARTITION_INFO =dev=sdb 3960471552-13872660479
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 45
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 46
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 47
parted_server: Opening infifo
ubiquity: IN: PARTITION_INFO =dev=sdb 3960471552-13872660479
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 48
parted_server: Opening infifo
ubiquity: IN: PARTITION_INFO =dev=sdb 3960471552-13872660479
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 49
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    
parted_server: main_loop: iteration 50
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 51
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sdb
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 52
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: 1 primary partitions, 1 logical partitions
/lib/partman/automatically_partition/10resize_use_free/choices: filtered partition list:
/lib/partman/automatically_partition/10resize_use_free/choices: 1 32256-3960032255 3960000000 primary ntfs /dev/sdb1 
5 3960471552-13872660479 9912188928 logical ext4 /dev/sdb5 
-1 13872660480-16022241279 2149580800 pri/log free /dev/sdb-1 
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 32256-3960032255
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3960032255
parted_server: partition_with_id(32256-3960032255)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7734437)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 53
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 3960471552-13872660479
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7735296,27095039)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 54
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sdb', totalfree: '2149580800', diskfree: '6789713920', diskpart: '/var/lib/partman/devices/=dev=sdb//3960471552-13872660479', diskpath: '/dev/sdb5'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sdb//3960471552-13872660479' (/dev/sdb5) with 6789713920 bytes free
/lib/partman/automatically_partition/15reuse/choices: *******************************************************
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 55
parted_server: Opening infifo
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 56
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 57
parted_server: Opening infifo
/lib/partman/automatically_partition/60some_device_lvm/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/automatically_partition/20some_device/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    
parted_server: main_loop: iteration 58
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 59
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sdb
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 60
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: 1 primary partitions, 1 logical partitions
/lib/partman/automatically_partition/10resize_use_free/choices: filtered partition list:
/lib/partman/automatically_partition/10resize_use_free/choices: 1 32256-3960032255 3960000000 primary ntfs /dev/sdb1 
5 3960471552-13872660479 9912188928 logical ext4 /dev/sdb5 
-1 13872660480-16022241279 2149580800 pri/log free /dev/sdb-1 
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 32256-3960032255
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3960032255
parted_server: partition_with_id(32256-3960032255)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7734437)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 61
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 3960471552-13872660479
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7735296,27095039)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 62
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sdb', totalfree: '2149580800', diskfree: '6789713920', diskpart: '/var/lib/partman/devices/=dev=sdb//3960471552-13872660479', diskpath: '/dev/sdb5'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sdb//3960471552-13872660479' (/dev/sdb5) with 6789713920 bytes free
/lib/partman/automatically_partition/15reuse/choices: *******************************************************
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 63
parted_server: Opening infifo
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 64
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 65
parted_server: Opening infifo
/lib/partman/automatically_partition/60some_device_lvm/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/80custom/choices: *******************************************************
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 66
parted_server: Opening infifo
ubiquity: IN: PARTITION_INFO =dev=sdb 13872660480-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13872660480-16022241279
parted_server: partition_with_id(13872660480-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 67
parted_server: Opening infifo
ubiquity: IN: PARTITION_INFO =dev=sdb 3960471552-13872660479
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 68
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 69
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 70
parted_server: Opening infifo
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/30lvm/choices: paragraph: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/30lvm/choices: paragraph: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    
/lib/partman/choose_partition/30lvm/choices: paragraph: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    
parted_server: main_loop: iteration 71
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 32256-3960032255
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3960032255
parted_server: partition_with_id(32256-3960032255)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 72
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 32256-3960032255
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3960032255)
parted_server: OUT: OK


parted_server: Partition found (32256-3960032255)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 73
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 3960471552-13872660479
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 74
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 3960471552-13872660479
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: Partition found (3960471552-13872660479)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 75
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 13872660480-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13872660480-16022241279
parted_server: partition_with_id(13872660480-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 76
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 77
parted_server: Opening infifo
/lib/partman/choose_partition/35crypto/choices: *******************************************************
/lib/partman/choose_partition/35crypto/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/35crypto/choices: paragraph: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/35crypto/choices: paragraph: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    
/lib/partman/choose_partition/35crypto/choices: paragraph: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    
parted_server: main_loop: iteration 78
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    
/lib/partman/choose_partition/60partition_tree/choices: paragraph: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    
parted_server: main_loop: iteration 79
parted_server: Opening infifo
ubiquity: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 80
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 81
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 82
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sdb 3960471552-13872660479
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 83
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 84
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/46keysize/choices: *******************************************************
/lib/partman/active_partition/47ivalgorithm/choices: *******************************************************
/lib/partman/active_partition/48keytype/choices: *******************************************************
/lib/partman/active_partition/49keyhash/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sdb 3960471552-13872660479
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: Partition found (3960471552-13872660479)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 85
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sdb 3960471552-13872660479
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3960471552-13872660479)
parted_server: Partition found (3960471552-13872660479)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 86
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 87
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sdb 3960471552-13872660479
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 88
parted_server: Opening infifo
/lib/partman/active_partition/85erasepart/choices: *******************************************************
/lib/partman/active_partition/85erasepart/choices: IN: VIRTUAL =dev=sdb 3960471552-13872660479
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7735296,27095039)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 89
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 90
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sdb 3960471552-13872660479
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7735296,27095039)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 91
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sdb 3960471552-13872660479
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 92
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 93
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 94
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 95
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sdb 32256-3960032255
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3960032255
parted_server: partition_with_id(32256-3960032255)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 96
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 97
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/46keysize/choices: *******************************************************
/lib/partman/active_partition/47ivalgorithm/choices: *******************************************************
/lib/partman/active_partition/48keytype/choices: *******************************************************
/lib/partman/active_partition/49keyhash/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sdb 32256-3960032255
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3960032255)
parted_server: OUT: OK


parted_server: Partition found (32256-3960032255)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 98
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sdb 32256-3960032255
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3960032255)
parted_server: Partition found (32256-3960032255)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 99
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 100
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sdb 32256-3960032255
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3960032255
parted_server: partition_with_id(32256-3960032255)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 101
parted_server: Opening infifo
/lib/partman/active_partition/85erasepart/choices: *******************************************************
/lib/partman/active_partition/85erasepart/choices: IN: VIRTUAL =dev=sdb 32256-3960032255
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3960032255
parted_server: partition_with_id(32256-3960032255)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7734437)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 102
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 103
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sdb 32256-3960032255
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3960032255
parted_server: partition_with_id(32256-3960032255)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7734437)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 104
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sdb 32256-3960032255
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3960032255
parted_server: partition_with_id(32256-3960032255)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 105
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 106
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 107
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/30lvm/choices: paragraph: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/30lvm/choices: paragraph: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    
/lib/partman/choose_partition/30lvm/choices: paragraph: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    
parted_server: main_loop: iteration 108
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 32256-3960032255
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3960032255
parted_server: partition_with_id(32256-3960032255)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 109
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 32256-3960032255
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3960032255)
parted_server: OUT: OK


parted_server: Partition found (32256-3960032255)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 110
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 3960471552-13872660479
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 111
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 3960471552-13872660479
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: Partition found (3960471552-13872660479)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 112
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 13872660480-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13872660480-16022241279
parted_server: partition_with_id(13872660480-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 113
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 114
parted_server: Opening infifo
/lib/partman/choose_partition/35crypto/choices: *******************************************************
/lib/partman/choose_partition/35crypto/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/35crypto/choices: paragraph: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/35crypto/choices: paragraph: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    
/lib/partman/choose_partition/35crypto/choices: paragraph: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    
parted_server: main_loop: iteration 115
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 116
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 117
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 118
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 119
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 120
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 121
parted_server: Opening infifo
/lib/partman/storage_device/80label/do_option: *******************************************************
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/30lvm/choices: paragraph: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/30lvm/choices: paragraph: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    
/lib/partman/choose_partition/30lvm/choices: paragraph: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    
parted_server: main_loop: iteration 122
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 32256-3960032255
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3960032255
parted_server: partition_with_id(32256-3960032255)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 123
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 32256-3960032255
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3960032255)
parted_server: OUT: OK


parted_server: Partition found (32256-3960032255)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 124
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 3960471552-13872660479
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 125
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 3960471552-13872660479
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: Partition found (3960471552-13872660479)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 126
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 13872660480-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13872660480-16022241279
parted_server: partition_with_id(13872660480-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 127
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 128
parted_server: Opening infifo
/lib/partman/choose_partition/35crypto/choices: *******************************************************
/lib/partman/choose_partition/35crypto/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/35crypto/choices: paragraph: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/35crypto/choices: paragraph: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    
/lib/partman/choose_partition/35crypto/choices: paragraph: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    
parted_server: main_loop: iteration 129
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
/bin/partman: IN: QUIT
parted_server: Read command: QUIT
parted_server: Quitting
/bin/partman: *******************************************************
/lib/partman/init.d/30parted: *******************************************************
parted_server: ======= Starting the server
parted_server: main_loop: iteration 1
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sda /dev/sda
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sda
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sda as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 2
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sdb /dev/sdb
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sdb
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sdb as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 3
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    65536-2052521983    2052456448    primary    fat16    /dev/sda1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 4
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: CLOSE =dev=sda
parted_server: Read command: CLOSE
parted_server: command_close()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 5
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 6
parted_server: Opening infifo
/lib/partman/init.d/35dump: *******************************************************
/lib/partman/init.d/35dump: IN: DUMP =dev=sdb
parted_server: Read command: DUMP
parted_server: command_dump()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 7
parted_server: Opening infifo
Device: yes
Model: Kingston DataTraveler 3.0
Path: /dev/sdb
Sector size: 512
Sectors: 31293440
Sectors/track: 63
Heads: 255
Cylinders: 1947
Partition table: yes
Type: msdos
Partitions: #    id    length    type    fs    path    name
(0,0,0)    (0,0,62)    -1    0-32255    32256    primary    label    /dev/sdb-1    
(0,1,0)    (481,113,53)    1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    
(481,113,54)    (481,127,27)    -1    3960032256-3960470527    438272    pri/log    free    /dev/sdb-1    
(481,127,28)    (1686,149,62)    2    3960470528-13872660479    9912189952    primary    extended    /dev/sdb2    
(481,127,28)    (481,127,29)    -1    3960470528-3960471551    1024    logical    label    /dev/sdb-1    
(481,127,30)    (1686,149,62)    5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    
(1686,150,0)    (1947,236,16)    -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    
Dump finished.
/lib/partman/init.d/50biosgrub: *******************************************************
/lib/partman/init.d/50biosgrub: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 8
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 32256-3960032255
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3960032255)
parted_server: Partition found (32256-3960032255)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 9
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 3960471552-13872660479
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3960471552-13872660479)
parted_server: Partition found (3960471552-13872660479)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 10
parted_server: Opening infifo
/lib/partman/init.d/50lvm: *******************************************************
/lib/partman/init.d/50lvm: *******************************************************
/lib/partman/init.d/50lvm: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 11
parted_server: Opening infifo
/lib/partman/init.d/50lvm: IN: GET_FLAGS =dev=sdb 32256-3960032255
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3960032255)
parted_server: Partition found (32256-3960032255)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 12
parted_server: Opening infifo
/lib/partman/init.d/50lvm: IN: GET_FLAGS =dev=sdb 3960471552-13872660479
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3960471552-13872660479)
parted_server: Partition found (3960471552-13872660479)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 13
parted_server: Opening infifo
/lib/partman/init.d/52crypto: *******************************************************
/lib/partman/init.d/52crypto: *******************************************************
/lib/partman/init.d/52crypto: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 14
parted_server: Opening infifo
/lib/partman/init.d/70update_partitions: *******************************************************
/lib/partman/init.d/70update_partitions: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 15
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 32256-3960032255
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3960032255)
parted_server: Partition found (32256-3960032255)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 16
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sdb 32256-3960032255
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 32256-3960032255
parted_server: partition_with_id(32256-3960032255)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7734437)
parted_server: no
parted_server: OUT: ntfs


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 17
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 32256-3960032255
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3960032255)
parted_server: Partition found (32256-3960032255)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 18
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 19
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 32256-3960032255
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3960032255)
parted_server: Partition found (32256-3960032255)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 20
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 21
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 22
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 3960471552-13872660479
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3960471552-13872660479)
parted_server: Partition found (3960471552-13872660479)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 23
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sdb 3960471552-13872660479
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7735296,27095039)
parted_server: no
parted_server: OUT: ext4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 24
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 3960471552-13872660479
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3960471552-13872660479)
parted_server: Partition found (3960471552-13872660479)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 25
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 26
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 3960471552-13872660479
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3960471552-13872660479)
parted_server: Partition found (3960471552-13872660479)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 27
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 28
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 29
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 30
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 31
parted_server: Opening infifo
/lib/partman/init.d/75auto_mountpoints: *******************************************************
/lib/partman/init.d/80autouse_swap: *******************************************************
/lib/partman/init.d/80autouse_swap: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 32
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    
parted_server: main_loop: iteration 33
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 34
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sdb
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 35
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: 1 primary partitions, 1 logical partitions
/lib/partman/automatically_partition/10resize_use_free/choices: filtered partition list:
/lib/partman/automatically_partition/10resize_use_free/choices: 1 32256-3960032255 3960000000 primary ntfs /dev/sdb1 
5 3960471552-13872660479 9912188928 logical ext4 /dev/sdb5 
-1 13872660480-16022241279 2149580800 pri/log free /dev/sdb-1 
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 32256-3960032255
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3960032255
parted_server: partition_with_id(32256-3960032255)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7734437)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 36
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 32256-3960032255
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3960032255)
parted_server: OUT: OK


parted_server: OUT: 512 3960000000 3960438272


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 37
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 3960471552-13872660479
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7735296,27095039)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 38
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 3960471552-13872660479
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: OUT: 512 9912188928 12061769728


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 39
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sdb', totalfree: '2149580800', diskfree: '6789713920', diskpart: '/var/lib/partman/devices/=dev=sdb//3960471552-13872660479', diskpath: '/dev/sdb5'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sdb//3960471552-13872660479' (/dev/sdb5) with 6789713920 bytes free
/lib/partman/automatically_partition/15reuse/choices: *******************************************************
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 40
parted_server: Opening infifo
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 41
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 42
parted_server: Opening infifo
/lib/partman/automatically_partition/60some_device_lvm/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: VIRTUAL =dev=sdb 3960471552-13872660479
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7735296,27095039)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 43
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 3960471552-13872660479
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: OUT: 512 9912188928 12061769728


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 44
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: PARTITION_INFO =dev=sdb 3960471552-13872660479
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 45
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 46
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 47
parted_server: Opening infifo
ubiquity: IN: PARTITION_INFO =dev=sdb 3960471552-13872660479
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 48
parted_server: Opening infifo
ubiquity: IN: PARTITION_INFO =dev=sdb 3960471552-13872660479
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 49
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    
parted_server: main_loop: iteration 50
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 51
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sdb
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 52
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: 1 primary partitions, 1 logical partitions
/lib/partman/automatically_partition/10resize_use_free/choices: filtered partition list:
/lib/partman/automatically_partition/10resize_use_free/choices: 1 32256-3960032255 3960000000 primary ntfs /dev/sdb1 
5 3960471552-13872660479 9912188928 logical ext4 /dev/sdb5 
-1 13872660480-16022241279 2149580800 pri/log free /dev/sdb-1 
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 32256-3960032255
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3960032255
parted_server: partition_with_id(32256-3960032255)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7734437)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 53
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 3960471552-13872660479
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7735296,27095039)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 54
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sdb', totalfree: '2149580800', diskfree: '6789713920', diskpart: '/var/lib/partman/devices/=dev=sdb//3960471552-13872660479', diskpath: '/dev/sdb5'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sdb//3960471552-13872660479' (/dev/sdb5) with 6789713920 bytes free
/lib/partman/automatically_partition/15reuse/choices: *******************************************************
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 55
parted_server: Opening infifo
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 56
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 57
parted_server: Opening infifo
/lib/partman/automatically_partition/60some_device_lvm/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/automatically_partition/20some_device/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    
parted_server: main_loop: iteration 58
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 59
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sdb
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 60
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: 1 primary partitions, 1 logical partitions
/lib/partman/automatically_partition/10resize_use_free/choices: filtered partition list:
/lib/partman/automatically_partition/10resize_use_free/choices: 1 32256-3960032255 3960000000 primary ntfs /dev/sdb1 
5 3960471552-13872660479 9912188928 logical ext4 /dev/sdb5 
-1 13872660480-16022241279 2149580800 pri/log free /dev/sdb-1 
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 32256-3960032255
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3960032255
parted_server: partition_with_id(32256-3960032255)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7734437)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 61
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 3960471552-13872660479
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7735296,27095039)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 62
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sdb', totalfree: '2149580800', diskfree: '6789713920', diskpart: '/var/lib/partman/devices/=dev=sdb//3960471552-13872660479', diskpath: '/dev/sdb5'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sdb//3960471552-13872660479' (/dev/sdb5) with 6789713920 bytes free
/lib/partman/automatically_partition/15reuse/choices: *******************************************************
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 63
parted_server: Opening infifo
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 64
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 65
parted_server: Opening infifo
/lib/partman/automatically_partition/60some_device_lvm/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/80custom/choices: *******************************************************
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3960032255    3960000000    primary    ntfs    /dev/sdb1    


parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 66
parted_server: Opening infifo
ubiquity: IN: PARTITION_INFO =dev=sdb 13872660480-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13872660480-16022241279
parted_server: partition_with_id(13872660480-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: -1    13872660480-16022241279    2149580800    pri/log    free    /dev/sdb-1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 67
parted_server: Opening infifo
ubiquity: IN: PARTITION_INFO =dev=sdb 3960471552-13872660479
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3960471552-13872660479
parted_server: partition_with_id(3960471552-13872660479)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    3960471552-13872660479    9912188928    logical    ext4    /dev/sdb5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 68
parted_server: Opening infifo
/bin/partman: IN: QUIT
parted_server: Read command: QUIT
parted_server: Quitting
/bin/partman: *******************************************************
/lib/partman/init.d/30parted: *******************************************************
parted_server: ======= Starting the server
parted_server: main_loop: iteration 1
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sda /dev/sda
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sda
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sda as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 2
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sdb /dev/sdb
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sdb
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sdb as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 3
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    65536-2052521983    2052456448    primary    fat16    /dev/sda1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 4
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: CLOSE =dev=sda
parted_server: Read command: CLOSE
parted_server: command_close()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 5
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 6
parted_server: Opening infifo
/lib/partman/init.d/35dump: *******************************************************
/lib/partman/init.d/35dump: IN: DUMP =dev=sdb
parted_server: Read command: DUMP
parted_server: command_dump()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 7
parted_server: Opening infifo
Device: yes
Model: Kingston DataTraveler 3.0
Path: /dev/sdb
Sector size: 512
Sectors: 31293440
Sectors/track: 63
Heads: 255
Cylinders: 1947
Partition table: yes
Type: msdos
Partitions: #    id    length    type    fs    path    name
(0,0,0)    (0,0,62)    -1    0-32255    32256    primary    label    /dev/sdb-1    
(0,1,0)    (481,62,28)    1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
(481,62,29)    (1686,215,0)    2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    
(1686,215,1)    (1947,236,16)    3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    
Dump finished.
/lib/partman/init.d/50biosgrub: *******************************************************
/lib/partman/init.d/50biosgrub: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 8
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 9
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 3958374400-13874757631
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13874757631)
parted_server: Partition found (3958374400-13874757631)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 10
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 13874757632-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13874757632-16022241279)
parted_server: Partition found (13874757632-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 11
parted_server: Opening infifo
/lib/partman/init.d/50lvm: *******************************************************
/lib/partman/init.d/50lvm: *******************************************************
/lib/partman/init.d/50lvm: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 12
parted_server: Opening infifo
/lib/partman/init.d/50lvm: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 13
parted_server: Opening infifo
/lib/partman/init.d/50lvm: IN: GET_FLAGS =dev=sdb 3958374400-13874757631
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13874757631)
parted_server: Partition found (3958374400-13874757631)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 14
parted_server: Opening infifo
/lib/partman/init.d/50lvm: IN: GET_FLAGS =dev=sdb 13874757632-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13874757632-16022241279)
parted_server: Partition found (13874757632-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 15
parted_server: Opening infifo
/lib/partman/init.d/52crypto: *******************************************************
/lib/partman/init.d/52crypto: *******************************************************
/lib/partman/init.d/52crypto: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 16
parted_server: Opening infifo
/lib/partman/init.d/70update_partitions: *******************************************************
/lib/partman/init.d/70update_partitions: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 17
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 18
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sdb 32256-3958374399
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7731199)
parted_server: no
parted_server: OUT: ntfs


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 19
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 20
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 21
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 22
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 23
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 24
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 3958374400-13874757631
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13874757631)
parted_server: Partition found (3958374400-13874757631)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 25
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sdb 3958374400-13874757631
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 3958374400-13874757631
parted_server: partition_with_id(3958374400-13874757631)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27099135)
parted_server: no
parted_server: OUT: ext4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 26
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 3958374400-13874757631
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13874757631)
parted_server: Partition found (3958374400-13874757631)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 27
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 28
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 3958374400-13874757631
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13874757631)
parted_server: Partition found (3958374400-13874757631)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 29
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 30
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 31
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 13874757632-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13874757632-16022241279)
parted_server: Partition found (13874757632-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 32
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sdb 13874757632-16022241279
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 13874757632-16022241279
parted_server: partition_with_id(13874757632-16022241279)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,27099136,31293439)
parted_server: no
parted_server: OUT: linux-swap


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 33
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 13874757632-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13874757632-16022241279)
parted_server: Partition found (13874757632-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 34
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 35
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 13874757632-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13874757632-16022241279)
parted_server: Partition found (13874757632-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 36
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 37
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 38
parted_server: Opening infifo
/lib/partman/init.d/75auto_mountpoints: *******************************************************
/lib/partman/init.d/80autouse_swap: *******************************************************
/lib/partman/init.d/80autouse_swap: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 39
parted_server: Opening infifo
/lib/partman/init.d/80autouse_swap: IN: PARTITION_INFO =dev=sdb 13874757632-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13874757632-16022241279
parted_server: partition_with_id(13874757632-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 40
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 13874757632-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13874757632-16022241279)
parted_server: Partition found (13874757632-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 41
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 13874757632-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13874757632-16022241279)
parted_server: Partition found (13874757632-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 42
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 43
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 13874757632-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13874757632-16022241279)
parted_server: Partition found (13874757632-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 44
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/60swap: IN: CHANGE_FILE_SYSTEM =dev=sdb 13874757632-16022241279 linux-swap
parted_server: Read command: CHANGE_FILE_SYSTEM
parted_server: Opening outfifo
parted_server: command_change_file_system(13874757632-16022241279,linux-swap)
parted_server: partition_with_id(13874757632-16022241279)
parted_server: Already using filesystem linux-swap(v1)
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 45
parted_server: Opening infifo
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 46
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 47
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 48
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 49
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sdb
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 50
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: 3 primary partitions, 0 logical partitions
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 32256-3958374399
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7731199)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 51
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 32256-3958374399
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 512 3958342144 3958342144


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 52
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 3958374400-13874757631
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13874757631
parted_server: partition_with_id(3958374400-13874757631)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27099135)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 53
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 3958374400-13874757631
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13874757631)
parted_server: OUT: OK


parted_server: OUT: 512 9916383232 9916383232


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 54
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_RESIZE_RANGE =dev=sdb 13874757632-16022241279
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(13874757632-16022241279)
parted_server: named_partition_is_virtual(=dev=sdb,27099136,31293439)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 4096 2147483648 2147483136


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 55
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sdb', totalfree: '0', diskfree: '9604485120', diskpart: '/var/lib/partman/devices/=dev=sdb//3958374400-13874757631', diskpath: '/dev/sdb2'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sdb//3958374400-13874757631' (/dev/sdb2) with 9604485120 bytes free
/lib/partman/automatically_partition/15reuse/choices: *******************************************************
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 56
parted_server: Opening infifo
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 57
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 58
parted_server: Opening infifo
/lib/partman/automatically_partition/60some_device_lvm/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: VIRTUAL =dev=sdb 3958374400-13874757631
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13874757631
parted_server: partition_with_id(3958374400-13874757631)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27099135)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 59
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 3958374400-13874757631
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13874757631)
parted_server: OUT: OK


parted_server: OUT: 512 9916383232 9916383232


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 60
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: PARTITION_INFO =dev=sdb 3958374400-13874757631
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13874757631
parted_server: partition_with_id(3958374400-13874757631)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 61
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 62
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 63
parted_server: Opening infifo
ubiquity: IN: PARTITION_INFO =dev=sdb 3958374400-13874757631
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13874757631
parted_server: partition_with_id(3958374400-13874757631)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 64
parted_server: Opening infifo
ubiquity: IN: PARTITION_INFO =dev=sdb 3958374400-13874757631
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13874757631
parted_server: partition_with_id(3958374400-13874757631)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 65
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 66
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 67
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sdb
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 68
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: 3 primary partitions, 0 logical partitions
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 32256-3958374399
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7731199)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 69
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 3958374400-13874757631
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13874757631
parted_server: partition_with_id(3958374400-13874757631)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27099135)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 70
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_RESIZE_RANGE =dev=sdb 13874757632-16022241279
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(13874757632-16022241279)
parted_server: named_partition_is_virtual(=dev=sdb,27099136,31293439)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 4096 2147483648 2147483136


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 71
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sdb', totalfree: '0', diskfree: '9604485120', diskpart: '/var/lib/partman/devices/=dev=sdb//3958374400-13874757631', diskpath: '/dev/sdb2'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sdb//3958374400-13874757631' (/dev/sdb2) with 9604485120 bytes free
/lib/partman/automatically_partition/15reuse/choices: *******************************************************
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 72
parted_server: Opening infifo
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 73
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 74
parted_server: Opening infifo
/lib/partman/automatically_partition/60some_device_lvm/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/automatically_partition/20some_device/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 75
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 76
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sdb
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 77
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: 3 primary partitions, 0 logical partitions
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 32256-3958374399
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7731199)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 78
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 3958374400-13874757631
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13874757631
parted_server: partition_with_id(3958374400-13874757631)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27099135)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 79
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_RESIZE_RANGE =dev=sdb 13874757632-16022241279
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(13874757632-16022241279)
parted_server: named_partition_is_virtual(=dev=sdb,27099136,31293439)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 4096 2147483648 2147483136


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 80
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sdb', totalfree: '0', diskfree: '9604485120', diskpart: '/var/lib/partman/devices/=dev=sdb//3958374400-13874757631', diskpath: '/dev/sdb2'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sdb//3958374400-13874757631' (/dev/sdb2) with 9604485120 bytes free
/lib/partman/automatically_partition/15reuse/choices: *******************************************************
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 81
parted_server: Opening infifo
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 82
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 83
parted_server: Opening infifo
/lib/partman/automatically_partition/60some_device_lvm/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/80custom/choices: *******************************************************
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 84
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 85
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 86
parted_server: Opening infifo
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/30lvm/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/30lvm/choices: paragraph: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    
/lib/partman/choose_partition/30lvm/choices: paragraph: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 87
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 32256-3958374399
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 88
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: Partition found (32256-3958374399)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 89
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 3958374400-13874757631
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13874757631
parted_server: partition_with_id(3958374400-13874757631)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 90
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 3958374400-13874757631
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13874757631)
parted_server: OUT: OK


parted_server: Partition found (3958374400-13874757631)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 91
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 13874757632-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13874757632-16022241279
parted_server: partition_with_id(13874757632-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 92
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 13874757632-16022241279
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13874757632-16022241279)
parted_server: OUT: OK


parted_server: Partition found (13874757632-16022241279)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 93
parted_server: Opening infifo
/lib/partman/choose_partition/35crypto/choices: *******************************************************
/lib/partman/choose_partition/35crypto/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/35crypto/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/35crypto/choices: paragraph: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    
/lib/partman/choose_partition/35crypto/choices: paragraph: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 94
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 95
parted_server: Opening infifo
ubiquity: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 96
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 97
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 98
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sdb 13874757632-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13874757632-16022241279
parted_server: partition_with_id(13874757632-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 99
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 100
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/46keysize/choices: *******************************************************
/lib/partman/active_partition/47ivalgorithm/choices: *******************************************************
/lib/partman/active_partition/48keytype/choices: *******************************************************
/lib/partman/active_partition/49keyhash/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sdb 13874757632-16022241279
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13874757632-16022241279)
parted_server: OUT: OK


parted_server: Partition found (13874757632-16022241279)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 101
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sdb 13874757632-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13874757632-16022241279)
parted_server: Partition found (13874757632-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 102
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 103
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sdb 13874757632-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13874757632-16022241279
parted_server: partition_with_id(13874757632-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 104
parted_server: Opening infifo
/lib/partman/active_partition/85erasepart/choices: *******************************************************
/lib/partman/active_partition/85erasepart/choices: IN: VIRTUAL =dev=sdb 13874757632-16022241279
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 13874757632-16022241279
parted_server: partition_with_id(13874757632-16022241279)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,27099136,31293439)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 105
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 106
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sdb 13874757632-16022241279
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 13874757632-16022241279
parted_server: partition_with_id(13874757632-16022241279)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,27099136,31293439)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 107
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_RESIZE_RANGE =dev=sdb 13874757632-16022241279
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(13874757632-16022241279)
parted_server: named_partition_is_virtual(=dev=sdb,27099136,31293439)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 4096 2147483648 2147483136


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 108
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sdb 13874757632-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13874757632-16022241279
parted_server: partition_with_id(13874757632-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 109
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 110
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 111
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 112
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sdb 32256-3958374399
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 113
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 114
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/46keysize/choices: *******************************************************
/lib/partman/active_partition/47ivalgorithm/choices: *******************************************************
/lib/partman/active_partition/48keytype/choices: *******************************************************
/lib/partman/active_partition/49keyhash/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: Partition found (32256-3958374399)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 115
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 116
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 117
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sdb 32256-3958374399
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 118
parted_server: Opening infifo
/lib/partman/active_partition/85erasepart/choices: *******************************************************
/lib/partman/active_partition/85erasepart/choices: IN: VIRTUAL =dev=sdb 32256-3958374399
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7731199)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 119
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 120
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sdb 32256-3958374399
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7731199)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 121
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sdb 32256-3958374399
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 122
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 123
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 124
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 125
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sdb 3958374400-13874757631
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13874757631
parted_server: partition_with_id(3958374400-13874757631)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 126
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 127
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/46keysize/choices: *******************************************************
/lib/partman/active_partition/47ivalgorithm/choices: *******************************************************
/lib/partman/active_partition/48keytype/choices: *******************************************************
/lib/partman/active_partition/49keyhash/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sdb 3958374400-13874757631
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13874757631)
parted_server: OUT: OK


parted_server: Partition found (3958374400-13874757631)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 128
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sdb 3958374400-13874757631
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13874757631)
parted_server: Partition found (3958374400-13874757631)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 129
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 130
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sdb 3958374400-13874757631
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13874757631
parted_server: partition_with_id(3958374400-13874757631)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 131
parted_server: Opening infifo
/lib/partman/active_partition/85erasepart/choices: *******************************************************
/lib/partman/active_partition/85erasepart/choices: IN: VIRTUAL =dev=sdb 3958374400-13874757631
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13874757631
parted_server: partition_with_id(3958374400-13874757631)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27099135)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 132
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 133
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sdb 3958374400-13874757631
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13874757631
parted_server: partition_with_id(3958374400-13874757631)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27099135)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 134
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sdb 3958374400-13874757631
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13874757631
parted_server: partition_with_id(3958374400-13874757631)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 135
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 136
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 137
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/30lvm/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/30lvm/choices: paragraph: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    
/lib/partman/choose_partition/30lvm/choices: paragraph: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 138
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 32256-3958374399
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 139
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: Partition found (32256-3958374399)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 140
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 3958374400-13874757631
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13874757631
parted_server: partition_with_id(3958374400-13874757631)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 141
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 3958374400-13874757631
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13874757631)
parted_server: OUT: OK


parted_server: Partition found (3958374400-13874757631)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 142
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 13874757632-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13874757632-16022241279
parted_server: partition_with_id(13874757632-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 143
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 13874757632-16022241279
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13874757632-16022241279)
parted_server: OUT: OK


parted_server: Partition found (13874757632-16022241279)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 144
parted_server: Opening infifo
/lib/partman/choose_partition/35crypto/choices: *******************************************************
/lib/partman/choose_partition/35crypto/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/35crypto/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/35crypto/choices: paragraph: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    
/lib/partman/choose_partition/35crypto/choices: paragraph: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 145
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 146
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 147
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 148
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13874757631    9916383232    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13874757632-16022241279    2147483648    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 149
parted_server: Opening infifo
/bin/partman: IN: QUIT
parted_server: Read command: QUIT
parted_server: Quitting
/bin/partman: *******************************************************
/lib/partman/init.d/30parted: *******************************************************
parted_server: ======= Starting the server
parted_server: main_loop: iteration 1
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sda /dev/sda
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sda
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sda as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 2
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sdb /dev/sdb
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sdb
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sdb as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 3
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    65536-2052521983    2052456448    primary    fat16    /dev/sda1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 4
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: CLOSE =dev=sda
parted_server: Read command: CLOSE
parted_server: command_close()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 5
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 6
parted_server: Opening infifo
/lib/partman/init.d/35dump: *******************************************************
/lib/partman/init.d/35dump: IN: DUMP =dev=sdb
parted_server: Read command: DUMP
parted_server: command_dump()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 7
parted_server: Opening infifo
Device: yes
Model: Kingston DataTraveler 3.0
Path: /dev/sdb
Sector size: 512
Sectors: 31293440
Sectors/track: 63
Heads: 255
Cylinders: 1947
Partition table: yes
Type: msdos
Partitions: #    id    length    type    fs    path    name
(0,0,0)    (0,0,62)    -1    0-32255    32256    primary    label    /dev/sdb-1    
(0,1,0)    (481,62,28)    1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
(481,62,29)    (1686,182,31)    2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    
(1686,182,32)    (1947,236,16)    3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
Dump finished.
/lib/partman/init.d/50biosgrub: *******************************************************
/lib/partman/init.d/50biosgrub: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 8
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 9
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 10
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 11
parted_server: Opening infifo
/lib/partman/init.d/50lvm: *******************************************************
/lib/partman/init.d/50lvm: *******************************************************
/lib/partman/init.d/50lvm: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 12
parted_server: Opening infifo
/lib/partman/init.d/50lvm: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 13
parted_server: Opening infifo
/lib/partman/init.d/50lvm: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 14
parted_server: Opening infifo
/lib/partman/init.d/50lvm: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 15
parted_server: Opening infifo
/lib/partman/init.d/52crypto: *******************************************************
/lib/partman/init.d/52crypto: *******************************************************
/lib/partman/init.d/52crypto: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 16
parted_server: Opening infifo
/lib/partman/init.d/70update_partitions: *******************************************************
/lib/partman/init.d/70update_partitions: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 17
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 18
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sdb 32256-3958374399
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7731199)
parted_server: no
parted_server: OUT: ntfs


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 19
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 20
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 21
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 22
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 23
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 24
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 25
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27097087)
parted_server: no
parted_server: OUT: ext4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 26
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 27
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 28
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 29
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 30
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 31
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 32
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,27097088,31293439)
parted_server: no
parted_server: OUT: linux-swap


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 33
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 34
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 35
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 36
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 37
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 38
parted_server: Opening infifo
/lib/partman/init.d/75auto_mountpoints: *******************************************************
/lib/partman/init.d/80autouse_swap: *******************************************************
/lib/partman/init.d/80autouse_swap: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 39
parted_server: Opening infifo
/lib/partman/init.d/80autouse_swap: IN: PARTITION_INFO =dev=sdb 13873709056-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 40
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 41
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 42
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 43
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 44
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/60swap: IN: CHANGE_FILE_SYSTEM =dev=sdb 13873709056-16022241279 linux-swap
parted_server: Read command: CHANGE_FILE_SYSTEM
parted_server: Opening outfifo
parted_server: command_change_file_system(13873709056-16022241279,linux-swap)
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Already using filesystem linux-swap(v1)
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 45
parted_server: Opening infifo
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 46
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 47
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 48
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 49
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sdb
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 50
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: 3 primary partitions, 0 logical partitions
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 32256-3958374399
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7731199)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 51
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 32256-3958374399
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 512 3958342144 3958342144


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 52
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 3958374400-13873709055
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27097087)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 53
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 512 9915334656 9915334656


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 54
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_RESIZE_RANGE =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: named_partition_is_virtual(=dev=sdb,27097088,31293439)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 4096 2148532224 2148531712


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 55
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sdb', totalfree: '0', diskfree: '9603436544', diskpart: '/var/lib/partman/devices/=dev=sdb//3958374400-13873709055', diskpath: '/dev/sdb2'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sdb//3958374400-13873709055' (/dev/sdb2) with 9603436544 bytes free
/lib/partman/automatically_partition/15reuse/choices: *******************************************************
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 56
parted_server: Opening infifo
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 57
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 58
parted_server: Opening infifo
/lib/partman/automatically_partition/60some_device_lvm/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: VIRTUAL =dev=sdb 3958374400-13873709055
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27097087)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 59
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 512 9915334656 9915334656


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 60
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 61
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 62
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 63
parted_server: Opening infifo
ubiquity: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 64
parted_server: Opening infifo
ubiquity: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 65
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 66
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 67
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sdb
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 68
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: 3 primary partitions, 0 logical partitions
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 32256-3958374399
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7731199)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 69
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 3958374400-13873709055
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27097087)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 70
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_RESIZE_RANGE =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: named_partition_is_virtual(=dev=sdb,27097088,31293439)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 4096 2148532224 2148531712


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 71
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sdb', totalfree: '0', diskfree: '9603436544', diskpart: '/var/lib/partman/devices/=dev=sdb//3958374400-13873709055', diskpath: '/dev/sdb2'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sdb//3958374400-13873709055' (/dev/sdb2) with 9603436544 bytes free
/lib/partman/automatically_partition/15reuse/choices: *******************************************************
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 72
parted_server: Opening infifo
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 73
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 74
parted_server: Opening infifo
/lib/partman/automatically_partition/60some_device_lvm/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/automatically_partition/20some_device/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 75
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 76
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sdb
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 77
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: 3 primary partitions, 0 logical partitions
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 32256-3958374399
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7731199)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 78
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 3958374400-13873709055
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27097087)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 79
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_RESIZE_RANGE =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: named_partition_is_virtual(=dev=sdb,27097088,31293439)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 4096 2148532224 2148531712


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 80
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sdb', totalfree: '0', diskfree: '9603436544', diskpart: '/var/lib/partman/devices/=dev=sdb//3958374400-13873709055', diskpath: '/dev/sdb2'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sdb//3958374400-13873709055' (/dev/sdb2) with 9603436544 bytes free
/lib/partman/automatically_partition/15reuse/choices: *******************************************************
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 81
parted_server: Opening infifo
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 82
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 83
parted_server: Opening infifo
/lib/partman/automatically_partition/60some_device_lvm/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/80custom/choices: *******************************************************
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 84
parted_server: Opening infifo
/bin/partman: IN: QUIT
parted_server: Read command: QUIT
parted_server: Quitting
/bin/partman: *******************************************************
/lib/partman/init.d/30parted: *******************************************************
parted_server: ======= Starting the server
parted_server: main_loop: iteration 1
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sda /dev/sda
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sda
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sda as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 2
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sdb /dev/sdb
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sdb
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sdb as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 3
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    65536-2052521983    2052456448    primary    fat16    /dev/sda1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 4
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: CLOSE =dev=sda
parted_server: Read command: CLOSE
parted_server: command_close()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 5
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 6
parted_server: Opening infifo
/lib/partman/init.d/35dump: *******************************************************
/lib/partman/init.d/35dump: IN: DUMP =dev=sdb
parted_server: Read command: DUMP
parted_server: command_dump()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 7
parted_server: Opening infifo
Device: yes
Model: Kingston DataTraveler 3.0
Path: /dev/sdb
Sector size: 512
Sectors: 31293440
Sectors/track: 63
Heads: 255
Cylinders: 1947
Partition table: yes
Type: msdos
Partitions: #    id    length    type    fs    path    name
(0,0,0)    (0,0,62)    -1    0-32255    32256    primary    label    /dev/sdb-1    
(0,1,0)    (481,62,28)    1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
(481,62,29)    (1686,182,31)    2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    
(1686,182,32)    (1947,236,16)    3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
Dump finished.
/lib/partman/init.d/50biosgrub: *******************************************************
/lib/partman/init.d/50biosgrub: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 8
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 9
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 10
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 11
parted_server: Opening infifo
/lib/partman/init.d/50lvm: *******************************************************
/lib/partman/init.d/50lvm: *******************************************************
/lib/partman/init.d/50lvm: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 12
parted_server: Opening infifo
/lib/partman/init.d/50lvm: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 13
parted_server: Opening infifo
/lib/partman/init.d/50lvm: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 14
parted_server: Opening infifo
/lib/partman/init.d/50lvm: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 15
parted_server: Opening infifo
/lib/partman/init.d/52crypto: *******************************************************
/lib/partman/init.d/52crypto: *******************************************************
/lib/partman/init.d/52crypto: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 16
parted_server: Opening infifo
/lib/partman/init.d/70update_partitions: *******************************************************
/lib/partman/init.d/70update_partitions: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 17
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 18
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sdb 32256-3958374399
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7731199)
parted_server: no
parted_server: OUT: ntfs


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 19
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 20
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 21
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 22
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 23
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 24
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 25
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27097087)
parted_server: no
parted_server: OUT: ext4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 26
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 27
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 28
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 29
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 30
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 31
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 32
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,27097088,31293439)
parted_server: no
parted_server: OUT: linux-swap


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 33
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 34
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 35
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 36
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 37
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 38
parted_server: Opening infifo
/lib/partman/init.d/75auto_mountpoints: *******************************************************
/lib/partman/init.d/80autouse_swap: *******************************************************
/lib/partman/init.d/80autouse_swap: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 39
parted_server: Opening infifo
/lib/partman/init.d/80autouse_swap: IN: PARTITION_INFO =dev=sdb 13873709056-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 40
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 41
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 42
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 43
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 44
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/60swap: IN: CHANGE_FILE_SYSTEM =dev=sdb 13873709056-16022241279 linux-swap
parted_server: Read command: CHANGE_FILE_SYSTEM
parted_server: Opening outfifo
parted_server: command_change_file_system(13873709056-16022241279,linux-swap)
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Already using filesystem linux-swap(v1)
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 45
parted_server: Opening infifo
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 46
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 47
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 48
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 49
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sdb
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 50
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: 3 primary partitions, 0 logical partitions
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 32256-3958374399
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7731199)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 51
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 32256-3958374399
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 512 3958342144 3958342144


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 52
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 3958374400-13873709055
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27097087)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 53
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 512 9915334656 9915334656


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 54
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_RESIZE_RANGE =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: named_partition_is_virtual(=dev=sdb,27097088,31293439)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 4096 2148532224 2148531712


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 55
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sdb', totalfree: '0', diskfree: '9603436544', diskpart: '/var/lib/partman/devices/=dev=sdb//3958374400-13873709055', diskpath: '/dev/sdb2'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sdb//3958374400-13873709055' (/dev/sdb2) with 9603436544 bytes free
/lib/partman/automatically_partition/15reuse/choices: *******************************************************
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 56
parted_server: Opening infifo
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 57
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 58
parted_server: Opening infifo
/lib/partman/automatically_partition/60some_device_lvm/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: VIRTUAL =dev=sdb 3958374400-13873709055
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27097087)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 59
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 512 9915334656 9915334656


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 60
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 61
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 62
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 63
parted_server: Opening infifo
ubiquity: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 64
parted_server: Opening infifo
ubiquity: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 65
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 66
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 67
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sdb
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 68
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: 3 primary partitions, 0 logical partitions
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 32256-3958374399
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7731199)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 69
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 3958374400-13873709055
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27097087)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 70
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_RESIZE_RANGE =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: named_partition_is_virtual(=dev=sdb,27097088,31293439)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 4096 2148532224 2148531712


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 71
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sdb', totalfree: '0', diskfree: '9603436544', diskpart: '/var/lib/partman/devices/=dev=sdb//3958374400-13873709055', diskpath: '/dev/sdb2'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sdb//3958374400-13873709055' (/dev/sdb2) with 9603436544 bytes free
/lib/partman/automatically_partition/15reuse/choices: *******************************************************
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 72
parted_server: Opening infifo
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 73
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 74
parted_server: Opening infifo
/lib/partman/automatically_partition/60some_device_lvm/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/automatically_partition/20some_device/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 75
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 76
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sdb
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 77
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: 3 primary partitions, 0 logical partitions
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 32256-3958374399
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7731199)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 78
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 3958374400-13873709055
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27097087)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 79
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_RESIZE_RANGE =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: named_partition_is_virtual(=dev=sdb,27097088,31293439)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 4096 2148532224 2148531712


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 80
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sdb', totalfree: '0', diskfree: '9603436544', diskpart: '/var/lib/partman/devices/=dev=sdb//3958374400-13873709055', diskpath: '/dev/sdb2'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sdb//3958374400-13873709055' (/dev/sdb2) with 9603436544 bytes free
/lib/partman/automatically_partition/15reuse/choices: *******************************************************
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 81
parted_server: Opening infifo
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 82
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 83
parted_server: Opening infifo
/lib/partman/automatically_partition/60some_device_lvm/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/70some_device_crypto/choices: *******************************************************
/lib/partman/automatically_partition/80custom/choices: *******************************************************
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 84
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 85
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 86
parted_server: Opening infifo
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/30lvm/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/30lvm/choices: paragraph: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    
/lib/partman/choose_partition/30lvm/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 87
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 32256-3958374399
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 88
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: Partition found (32256-3958374399)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 89
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 90
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 91
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 13873709056-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 92
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 93
parted_server: Opening infifo
/lib/partman/choose_partition/35crypto/choices: *******************************************************
/lib/partman/choose_partition/35crypto/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/35crypto/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/35crypto/choices: paragraph: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    
/lib/partman/choose_partition/35crypto/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 94
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 95
parted_server: Opening infifo
ubiquity: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 96
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 97
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 98
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 99
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 100
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/46keysize/choices: *******************************************************
/lib/partman/active_partition/47ivalgorithm/choices: *******************************************************
/lib/partman/active_partition/48keytype/choices: *******************************************************
/lib/partman/active_partition/49keyhash/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 101
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 102
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 103
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 104
parted_server: Opening infifo
/lib/partman/active_partition/85erasepart/choices: *******************************************************
/lib/partman/active_partition/85erasepart/choices: IN: VIRTUAL =dev=sdb 3958374400-13873709055
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27097087)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 105
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 106
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sdb 3958374400-13873709055
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27097087)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 107
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 108
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 109
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 110
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 111
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sdb 32256-3958374399
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 112
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 113
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/46keysize/choices: *******************************************************
/lib/partman/active_partition/47ivalgorithm/choices: *******************************************************
/lib/partman/active_partition/48keytype/choices: *******************************************************
/lib/partman/active_partition/49keyhash/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: Partition found (32256-3958374399)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 114
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 115
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 116
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sdb 32256-3958374399
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 117
parted_server: Opening infifo
/lib/partman/active_partition/85erasepart/choices: *******************************************************
/lib/partman/active_partition/85erasepart/choices: IN: VIRTUAL =dev=sdb 32256-3958374399
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7731199)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 118
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 119
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sdb 32256-3958374399
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7731199)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 120
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sdb 32256-3958374399
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 121
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 122
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 123
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 124
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sdb 13873709056-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 125
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 126
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/46keysize/choices: *******************************************************
/lib/partman/active_partition/47ivalgorithm/choices: *******************************************************
/lib/partman/active_partition/48keytype/choices: *******************************************************
/lib/partman/active_partition/49keyhash/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 127
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 128
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 129
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sdb 13873709056-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 130
parted_server: Opening infifo
/lib/partman/active_partition/85erasepart/choices: *******************************************************
/lib/partman/active_partition/85erasepart/choices: IN: VIRTUAL =dev=sdb 13873709056-16022241279
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,27097088,31293439)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 131
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 132
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sdb 13873709056-16022241279
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,27097088,31293439)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 133
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_RESIZE_RANGE =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: named_partition_is_virtual(=dev=sdb,27097088,31293439)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 4096 2148532224 2148531712


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 134
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sdb 13873709056-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 135
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 136
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 137
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/30lvm/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/30lvm/choices: paragraph: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    
/lib/partman/choose_partition/30lvm/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 138
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 32256-3958374399
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 139
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: Partition found (32256-3958374399)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 140
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 141
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 142
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 13873709056-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 143
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 144
parted_server: Opening infifo
/lib/partman/choose_partition/35crypto/choices: *******************************************************
/lib/partman/choose_partition/35crypto/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/35crypto/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/35crypto/choices: paragraph: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    
/lib/partman/choose_partition/35crypto/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 145
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 146
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 147
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 148
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 149
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 150
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 151
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 152
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/46keysize/choices: *******************************************************
/lib/partman/active_partition/47ivalgorithm/choices: *******************************************************
/lib/partman/active_partition/48keytype/choices: *******************************************************
/lib/partman/active_partition/49keyhash/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 153
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 154
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 155
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 156
parted_server: Opening infifo
/lib/partman/active_partition/85erasepart/choices: *******************************************************
/lib/partman/active_partition/85erasepart/choices: IN: VIRTUAL =dev=sdb 3958374400-13873709055
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27097087)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 157
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 158
parted_server: Opening infifo
/lib/partman/active_partition/15method/do_option: *******************************************************
/lib/partman/choose_method/45biosgrub/choices: *******************************************************
/lib/partman/choose_method/45biosgrub/choices: IN: VALID_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 159
parted_server: Opening infifo
/lib/partman/choose_method/50crypto/choices: *******************************************************
/lib/partman/choose_method/50crypto/choices: *******************************************************
/lib/partman/choose_method/52lvm/choices: *******************************************************
/lib/partman/choose_method/52lvm/choices: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 160
parted_server: Opening infifo
/lib/partman/choose_method/52lvm/choices: IN: VALID_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 161
parted_server: Opening infifo
/lib/partman/choose_method/25filesystem/do_option: *******************************************************
/lib/partman/choose_method/25filesystem/do_option: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 162
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 163
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 164
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 165
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 166
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/50filesystems: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 167
parted_server: Opening infifo
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 168
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 169
parted_server: Opening infifo
/lib/partman/active_partition/15method/do_option: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 170
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 171
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 172
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 173
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 174
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/50filesystems: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 175
parted_server: Opening infifo
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 176
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 177
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 178
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/46keysize/choices: *******************************************************
/lib/partman/active_partition/47ivalgorithm/choices: *******************************************************
/lib/partman/active_partition/48keytype/choices: *******************************************************
/lib/partman/active_partition/49keyhash/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 179
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 180
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 181
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 182
parted_server: Opening infifo
/lib/partman/active_partition/85erasepart/choices: *******************************************************
/lib/partman/active_partition/85erasepart/choices: IN: VIRTUAL =dev=sdb 3958374400-13873709055
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27097087)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 183
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 184
parted_server: Opening infifo
/lib/partman/active_partition/45ext3/do_option: *******************************************************
/lib/partman/active_partition/45ext3/do_option: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 185
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 186
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 187
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 188
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 189
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/50filesystems: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 190
parted_server: Opening infifo
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 191
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 192
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 193
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/46keysize/choices: *******************************************************
/lib/partman/active_partition/47ivalgorithm/choices: *******************************************************
/lib/partman/active_partition/48keytype/choices: *******************************************************
/lib/partman/active_partition/49keyhash/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 194
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 195
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 196
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 197
parted_server: Opening infifo
/lib/partman/active_partition/85erasepart/choices: *******************************************************
/lib/partman/active_partition/85erasepart/choices: IN: VIRTUAL =dev=sdb 3958374400-13873709055
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27097087)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 198
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 199
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sdb 3958374400-13873709055
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27097087)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 200
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 512 9915334656 9915334656


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 201
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 202
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 203
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 204
parted_server: Opening infifo
/lib/partman/commit.d/01unmount_busy: *******************************************************
/lib/partman/commit.d/01unmount_busy: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 205
parted_server: Opening infifo
/lib/partman/commit.d/01unmount_busy: IN: IS_BUSY =dev=sdb 32256-3958374399
parted_server: Read command: IS_BUSY
parted_server: command_is_busy()
parted_server: Opening outfifo
parted_server: command_is_busy: busy check for id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 206
parted_server: Opening infifo
/lib/partman/commit.d/01unmount_busy: IN: IS_BUSY =dev=sdb 3958374400-13873709055
parted_server: Read command: IS_BUSY
parted_server: command_is_busy()
parted_server: Opening outfifo
parted_server: command_is_busy: busy check for id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 207
parted_server: Opening infifo
/lib/partman/commit.d/01unmount_busy: IN: IS_BUSY =dev=sdb 13873709056-16022241279
parted_server: Read command: IS_BUSY
parted_server: command_is_busy()
parted_server: Opening outfifo
parted_server: command_is_busy: busy check for id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 208
parted_server: Opening infifo
/lib/partman/commit.d/30parted: *******************************************************
/lib/partman/commit.d/30parted: IN: IS_CHANGED =dev=sdb
parted_server: Read command: IS_CHANGED
parted_server: command_is_changed(=dev=sdb)
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 209
parted_server: Opening infifo
/lib/partman/commit.d/45format_swap: *******************************************************
/lib/partman/commit.d/45format_swap: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 210
parted_server: Opening infifo
/lib/partman/commit.d/45format_swap: Try to format swap space in /var/lib/partman/devices/=dev=sdb/13873709056-16022241279
/lib/partman/commit.d/45format_swap: IN: PARTITION_INFO =dev=sdb 13873709056-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 211
parted_server: Opening infifo
/lib/partman/commit.d/45format_swap: IN: PARTITION_INFO =dev=sdb 13873709056-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 212
parted_server: Opening infifo
/lib/partman/commit.d/50format_basicfilesystems: *******************************************************
/lib/partman/commit.d/50format_basicfilesystems: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 213
parted_server: Opening infifo
/lib/partman/commit.d/50format_basicfilesystems: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 214
parted_server: Opening infifo
/lib/partman/commit.d/50format_btrfs: *******************************************************
/lib/partman/commit.d/50format_btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 215
parted_server: Opening infifo
/lib/partman/commit.d/50format_btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 216
parted_server: Opening infifo
/lib/partman/commit.d/50format_efi: *******************************************************
/lib/partman/commit.d/50format_efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 217
parted_server: Opening infifo
/lib/partman/commit.d/50format_efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 218
parted_server: Opening infifo
/lib/partman/commit.d/50format_ext3: *******************************************************
/lib/partman/commit.d/50format_ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 219
parted_server: Opening infifo
/lib/partman/commit.d/50format_ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 220
parted_server: Opening infifo
/lib/partman/commit.d/50format_jfs: *******************************************************
/lib/partman/commit.d/50format_jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 221
parted_server: Opening infifo
/lib/partman/commit.d/50format_jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 222
parted_server: Opening infifo
/lib/partman/commit.d/50format_xfs: *******************************************************
/lib/partman/commit.d/50format_xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 223
parted_server: Opening infifo
/lib/partman/commit.d/50format_xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 224
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 225
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 226
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27097087)
parted_server: no
parted_server: OUT: ext4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 227
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 228
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 229
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 3958374400-13873709055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873709055)
parted_server: Partition found (3958374400-13873709055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 230
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/50filesystems: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 231
parted_server: Opening infifo
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 232
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 233
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 234
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: COMMIT =dev=sdb
parted_server: Read command: COMMIT
parted_server: command_commit()
parted_server: Opening outfifo
parted_server: Note =dev=sdb as unchanged
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 235
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sdb 3958374400-13873709055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873709055    9915334656    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 236
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL_RESIZE_PARTITION =dev=sdb 3958374400-13873709055 9915000000
parted_server: Read command: VIRTUAL_RESIZE_PARTITION
parted_server: command_virtual_resize_partition()
parted_server: Note =dev=sdb as changed
parted_server: Opening outfifo
parted_server: Resizing partition with id 3958374400-13873709055
parted_server: partition_with_id(3958374400-13873709055)
parted_server: New size: 9915000000
parted_server: resize_partition(openfs=false)
parted_server: probed file system: yes
parted_server: try to check the file system for errors
parted_server: successfully checked
parted_server: resize_partition(openfs=false)
parted_server: probed file system: yes
parted_server: try to check the file system for errors
parted_server: successfully checked
parted_server: Note =dev=sdb as unchanged
parted_server: OUT: OK


parted_server: OUT: 3958374400-13873374719


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 237
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 238
parted_server: Opening infifo
/lib/partman/init.d/30parted: *******************************************************
/lib/partman/init.d/35dump: *******************************************************
/lib/partman/init.d/35dump: IN: DUMP =dev=sdb
parted_server: Read command: DUMP
parted_server: command_dump()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 239
parted_server: Opening infifo
Device: yes
Model: Kingston DataTraveler 3.0
Path: /dev/sdb
Sector size: 512
Sectors: 31293440
Sectors/track: 63
Heads: 255
Cylinders: 1947
Partition table: yes
Type: msdos
Partitions: #    id    length    type    fs    path    name
(0,0,0)    (0,0,62)    -1    0-32255    32256    primary    label    /dev/sdb-1    
(0,1,0)    (481,62,28)    1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
(481,62,29)    (1686,172,8)    2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    
(1686,172,9)    (1686,182,31)    -1    13873374720-13873709055    334336    pri/log    free    /dev/sdb-1    
(1686,182,32)    (1947,236,16)    3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
Dump finished.
/lib/partman/init.d/50biosgrub: *******************************************************
/lib/partman/init.d/50biosgrub: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 240
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 241
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 242
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 243
parted_server: Opening infifo
/lib/partman/init.d/50lvm: *******************************************************
/lib/partman/init.d/50lvm: *******************************************************
/lib/partman/init.d/50lvm: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 244
parted_server: Opening infifo
/lib/partman/init.d/50lvm: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 245
parted_server: Opening infifo
/lib/partman/init.d/50lvm: IN: GET_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 246
parted_server: Opening infifo
/lib/partman/init.d/50lvm: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 247
parted_server: Opening infifo
/lib/partman/init.d/52crypto: *******************************************************
/lib/partman/init.d/52crypto: *******************************************************
/lib/partman/init.d/52crypto: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 248
parted_server: Opening infifo
/lib/partman/init.d/70update_partitions: *******************************************************
/lib/partman/init.d/70update_partitions: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 249
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 250
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sdb 32256-3958374399
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7731199)
parted_server: no
parted_server: OUT: ntfs


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 251
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 252
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 253
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 254
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 255
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 256
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 257
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sdb 3958374400-13873374719
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27096434)
parted_server: no
parted_server: OUT: ext4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 258
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 259
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 260
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 261
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/50filesystems: IN: PARTITION_INFO =dev=sdb 3958374400-13873374719
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 262
parted_server: Opening infifo
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 263
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 264
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 265
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,27097088,31293439)
parted_server: no
parted_server: OUT: linux-swap


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 266
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 267
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 268
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 269
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/60swap: IN: CHANGE_FILE_SYSTEM =dev=sdb 13873709056-16022241279 linux-swap
parted_server: Read command: CHANGE_FILE_SYSTEM
parted_server: Opening outfifo
parted_server: command_change_file_system(13873709056-16022241279,linux-swap)
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Already using filesystem linux-swap(v1)
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 270
parted_server: Opening infifo
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 271
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 272
parted_server: Opening infifo
/lib/partman/init.d/80autouse_swap: *******************************************************
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/30lvm/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/30lvm/choices: paragraph: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    
/lib/partman/choose_partition/30lvm/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 273
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 32256-3958374399
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 274
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: Partition found (32256-3958374399)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 275
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 3958374400-13873374719
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 276
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 277
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 13873709056-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 278
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 279
parted_server: Opening infifo
/lib/partman/choose_partition/35crypto/choices: *******************************************************
/lib/partman/choose_partition/35crypto/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/35crypto/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/35crypto/choices: paragraph: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    
/lib/partman/choose_partition/35crypto/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 280
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 281
parted_server: Opening infifo
ubiquity: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 282
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 283
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 284
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sdb 32256-3958374399
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 285
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 286
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/46keysize/choices: *******************************************************
/lib/partman/active_partition/47ivalgorithm/choices: *******************************************************
/lib/partman/active_partition/48keytype/choices: *******************************************************
/lib/partman/active_partition/49keyhash/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: Partition found (32256-3958374399)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 287
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 288
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 289
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sdb 32256-3958374399
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 290
parted_server: Opening infifo
/lib/partman/active_partition/85erasepart/choices: *******************************************************
/lib/partman/active_partition/85erasepart/choices: IN: VIRTUAL =dev=sdb 32256-3958374399
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7731199)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 291
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 292
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sdb 32256-3958374399
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,63,7731199)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 293
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 32256-3958374399
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 512 3958342144 3958342144


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 294
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sdb 32256-3958374399
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 295
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 296
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 297
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 298
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sdb 3958374400-13873374719
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 299
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 300
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/46keysize/choices: *******************************************************
/lib/partman/active_partition/47ivalgorithm/choices: *******************************************************
/lib/partman/active_partition/48keytype/choices: *******************************************************
/lib/partman/active_partition/49keyhash/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 301
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 302
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 303
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sdb 3958374400-13873374719
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 304
parted_server: Opening infifo
/lib/partman/active_partition/85erasepart/choices: *******************************************************
/lib/partman/active_partition/85erasepart/choices: IN: VIRTUAL =dev=sdb 3958374400-13873374719
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27096434)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 305
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 306
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sdb 3958374400-13873374719
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27096434)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 307
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 3958374400-13873374719
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: OUT: 512 9915000320 9915334656


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 308
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sdb 3958374400-13873374719
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 309
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 310
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 311
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 312
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sdb 13873709056-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 313
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 314
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/46keysize/choices: *******************************************************
/lib/partman/active_partition/47ivalgorithm/choices: *******************************************************
/lib/partman/active_partition/48keytype/choices: *******************************************************
/lib/partman/active_partition/49keyhash/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 315
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 316
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 317
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sdb 13873709056-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 318
parted_server: Opening infifo
/lib/partman/active_partition/85erasepart/choices: *******************************************************
/lib/partman/active_partition/85erasepart/choices: IN: VIRTUAL =dev=sdb 13873709056-16022241279
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,27097088,31293439)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 319
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 320
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sdb 13873709056-16022241279
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,27097088,31293439)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 321
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_RESIZE_RANGE =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: named_partition_is_virtual(=dev=sdb,27097088,31293439)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 4096 2148532224 2148531712


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 322
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sdb 13873709056-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 323
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 324
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 325
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/30lvm/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/30lvm/choices: paragraph: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    
/lib/partman/choose_partition/30lvm/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 326
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 32256-3958374399
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 327
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: Partition found (32256-3958374399)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 328
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 3958374400-13873374719
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 329
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 330
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 13873709056-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 331
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 332
parted_server: Opening infifo
/lib/partman/choose_partition/35crypto/choices: *******************************************************
/lib/partman/choose_partition/35crypto/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/35crypto/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/35crypto/choices: paragraph: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    
/lib/partman/choose_partition/35crypto/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 333
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 334
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 335
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 336
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sdb 3958374400-13873374719
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 337
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 338
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/46keysize/choices: *******************************************************
/lib/partman/active_partition/47ivalgorithm/choices: *******************************************************
/lib/partman/active_partition/48keytype/choices: *******************************************************
/lib/partman/active_partition/49keyhash/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 339
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 340
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 341
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sdb 3958374400-13873374719
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 342
parted_server: Opening infifo
/lib/partman/active_partition/85erasepart/choices: *******************************************************
/lib/partman/active_partition/85erasepart/choices: IN: VIRTUAL =dev=sdb 3958374400-13873374719
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27096434)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 343
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 344
parted_server: Opening infifo
/lib/partman/active_partition/30format/do_option: *******************************************************
/lib/partman/active_partition/30format/do_option: IN: PARTITION_INFO =dev=sdb 3958374400-13873374719
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 345
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 346
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 347
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 348
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 349
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/50filesystems: IN: PARTITION_INFO =dev=sdb 3958374400-13873374719
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 350
parted_server: Opening infifo
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 351
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 352
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 353
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/46keysize/choices: *******************************************************
/lib/partman/active_partition/47ivalgorithm/choices: *******************************************************
/lib/partman/active_partition/48keytype/choices: *******************************************************
/lib/partman/active_partition/49keyhash/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 354
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 355
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 356
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sdb 3958374400-13873374719
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 357
parted_server: Opening infifo
/lib/partman/active_partition/85erasepart/choices: *******************************************************
/lib/partman/active_partition/85erasepart/choices: IN: VIRTUAL =dev=sdb 3958374400-13873374719
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27096434)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 358
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 359
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/30lvm/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/30lvm/choices: paragraph: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    
/lib/partman/choose_partition/30lvm/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 360
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 32256-3958374399
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 361
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: Partition found (32256-3958374399)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 362
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 3958374400-13873374719
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 363
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 364
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 13873709056-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 365
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 366
parted_server: Opening infifo
/lib/partman/choose_partition/35crypto/choices: *******************************************************
/lib/partman/choose_partition/35crypto/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/35crypto/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/35crypto/choices: paragraph: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    
/lib/partman/choose_partition/35crypto/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 367
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 368
parted_server: Opening infifo
ubiquity: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 369
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 370
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 371
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sdb 3958374400-13873374719
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 372
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 373
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/46keysize/choices: *******************************************************
/lib/partman/active_partition/47ivalgorithm/choices: *******************************************************
/lib/partman/active_partition/48keytype/choices: *******************************************************
/lib/partman/active_partition/49keyhash/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 374
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 375
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 376
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sdb 3958374400-13873374719
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 377
parted_server: Opening infifo
/lib/partman/active_partition/85erasepart/choices: *******************************************************
/lib/partman/active_partition/85erasepart/choices: IN: VIRTUAL =dev=sdb 3958374400-13873374719
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27096434)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 378
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 379
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sdb 3958374400-13873374719
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,7731200,27096434)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 380
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 3958374400-13873374719
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: OUT: 512 9915000320 9915334656


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 381
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sdb 3958374400-13873374719
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 382
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 383
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 384
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/30lvm/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/30lvm/choices: paragraph: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    
/lib/partman/choose_partition/30lvm/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 385
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 32256-3958374399
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 386
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: Partition found (32256-3958374399)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 387
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 3958374400-13873374719
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 388
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 389
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 13873709056-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 390
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 391
parted_server: Opening infifo
/lib/partman/choose_partition/35crypto/choices: *******************************************************
/lib/partman/choose_partition/35crypto/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/35crypto/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/35crypto/choices: paragraph: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    
/lib/partman/choose_partition/35crypto/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 392
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 393
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 394
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 395
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 396
parted_server: Opening infifo
/lib/partman/storage_device/80label/do_option: *******************************************************
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: *******************************************************
/lib/partman/choose_partition/30lvm/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/30lvm/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/30lvm/choices: paragraph: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    
/lib/partman/choose_partition/30lvm/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 397
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 32256-3958374399
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 398
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: Partition found (32256-3958374399)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 399
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 3958374400-13873374719
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 400
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 401
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: PARTITION_INFO =dev=sdb 13873709056-16022241279
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 402
parted_server: Opening infifo
/lib/partman/choose_partition/30lvm/choices: IN: VALID_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: lba


parted_server: OUT: palo


parted_server: OUT: prep


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 403
parted_server: Opening infifo
/lib/partman/choose_partition/35crypto/choices: *******************************************************
/lib/partman/choose_partition/35crypto/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/35crypto/choices: paragraph: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
/lib/partman/choose_partition/35crypto/choices: paragraph: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    
/lib/partman/choose_partition/35crypto/choices: paragraph: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
parted_server: main_loop: iteration 404
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
/lib/partman/check.d/03partition_too_small: *******************************************************
/lib/partman/check.d/03partition_too_small: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 405
parted_server: Opening infifo
/lib/partman/check.d/05duplicate_labels: *******************************************************
/lib/partman/check.d/05duplicate_labels: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 406
parted_server: Opening infifo
/lib/partman/check.d/05proper_mountpoints: *******************************************************
/lib/partman/fstab.d/basic: *******************************************************
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 407
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: *******************************************************
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 408
parted_server: Opening infifo
/lib/partman/fstab.d/efi: *******************************************************
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 409
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: *******************************************************
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 410
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: *******************************************************
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 411
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: *******************************************************
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 412
parted_server: Opening infifo
/lib/partman/fstab.d/basic: *******************************************************
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 413
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: *******************************************************
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 414
parted_server: Opening infifo
/lib/partman/fstab.d/efi: *******************************************************
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 415
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: *******************************************************
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 416
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: *******************************************************
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 417
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: *******************************************************
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 418
parted_server: Opening infifo
/lib/partman/fstab.d/basic: *******************************************************
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 419
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: *******************************************************
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 420
parted_server: Opening infifo
/lib/partman/fstab.d/efi: *******************************************************
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 421
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: *******************************************************
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 422
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: *******************************************************
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 423
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: *******************************************************
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 424
parted_server: Opening infifo
/lib/partman/check.d/07basic_method_only: *******************************************************
/lib/partman/check.d/07basic_method_only: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 425
parted_server: Opening infifo
/lib/partman/check.d/07crypto_check_mountpoints: *******************************************************
/lib/partman/check.d/07crypto_check_mountpoints: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 426
parted_server: Opening infifo
/lib/partman/check.d/07efi: *******************************************************
/lib/partman/check.d/07efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 427
parted_server: Opening infifo
/lib/partman/check.d/08biosgrub: *******************************************************
/lib/partman/check.d/08biosgrub: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 428
parted_server: Opening infifo
/lib/partman/check.d/08mountpoint_fat: *******************************************************
/lib/partman/check.d/08mountpoint_fat: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 429
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_basicfilesystems: *******************************************************
/lib/partman/check.d/09nomountpoint_basicfilesystems: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 430
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_btrfs: *******************************************************
/lib/partman/check.d/09nomountpoint_btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 431
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_ext3: *******************************************************
/lib/partman/check.d/09nomountpoint_ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 432
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_jfs: *******************************************************
/lib/partman/check.d/09nomountpoint_jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 433
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_xfs: *******************************************************
/lib/partman/check.d/09nomountpoint_xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 434
parted_server: Opening infifo
/lib/partman/check.d/10alignment_ext3: *******************************************************
/lib/partman/check.d/10alignment_ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 435
parted_server: Opening infifo
/lib/partman/check.d/10alignment_ext3: IN: ALIGNMENT_OFFSET =dev=sdb 3958374400-13873374719
parted_server: Read command: ALIGNMENT_OFFSET
parted_server: command_alignment_offset()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: OUT: 0


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 436
parted_server: Opening infifo
/lib/partman/check.d/10check_basicfilesystems: *******************************************************
/lib/partman/check.d/10check_basicfilesystems: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 437
parted_server: Opening infifo
/lib/partman/check.d/10check_swap: *******************************************************
/lib/partman/check.d/10check_swap: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 438
parted_server: Opening infifo
/lib/partman/check.d/11unsafe_swap: *******************************************************
/lib/partman/check.d/12system_partitions_formatted: *******************************************************
/lib/partman/check.d/12system_partitions_formatted: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 439
parted_server: Opening infifo
/lib/partman/check.d/13encrypted_home_present: *******************************************************
/lib/partman/check.d/13encrypted_home_present: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 440
parted_server: Opening infifo
/bin/partman: IN: IS_CHANGED =dev=sdb
parted_server: Read command: IS_CHANGED
parted_server: command_is_changed(=dev=sdb)
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 441
parted_server: Opening infifo
/bin/partman: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 442
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 443
parted_server: Opening infifo
/bin/partman-commit: *******************************************************
/lib/partman/init.d/30parted: *******************************************************
/lib/partman/init.d/35dump: *******************************************************
/lib/partman/init.d/35dump: IN: DUMP =dev=sdb
parted_server: Read command: DUMP
parted_server: command_dump()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 444
parted_server: Opening infifo
Device: yes
Model: Kingston DataTraveler 3.0
Path: /dev/sdb
Sector size: 512
Sectors: 31293440
Sectors/track: 63
Heads: 255
Cylinders: 1947
Partition table: yes
Type: msdos
Partitions: #    id    length    type    fs    path    name
(0,0,0)    (0,0,62)    -1    0-32255    32256    primary    label    /dev/sdb-1    
(0,1,0)    (481,62,28)    1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    
(481,62,29)    (1686,172,8)    2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    
(1686,172,9)    (1686,182,31)    -1    13873374720-13873709055    334336    pri/log    free    /dev/sdb-1    
(1686,182,32)    (1947,236,16)    3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    
Dump finished.
/lib/partman/init.d/50biosgrub: *******************************************************
/lib/partman/init.d/50biosgrub: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 445
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 446
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 447
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 448
parted_server: Opening infifo
/lib/partman/init.d/50lvm: *******************************************************
/lib/partman/init.d/50lvm: *******************************************************
/lib/partman/init.d/50lvm: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 449
parted_server: Opening infifo
/lib/partman/init.d/50lvm: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 450
parted_server: Opening infifo
/lib/partman/init.d/50lvm: IN: GET_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 451
parted_server: Opening infifo
/lib/partman/init.d/50lvm: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 452
parted_server: Opening infifo
/lib/partman/init.d/52crypto: *******************************************************
/lib/partman/init.d/52crypto: *******************************************************
/lib/partman/init.d/52crypto: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 453
parted_server: Opening infifo
/lib/partman/init.d/70update_partitions: *******************************************************
/lib/partman/init.d/70update_partitions: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 454
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 455
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 456
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 457
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 32256-3958374399
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-3958374399)
parted_server: Partition found (32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 458
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 459
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 460
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 461
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 462
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 463
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 3958374400-13873374719
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(3958374400-13873374719)
parted_server: Partition found (3958374400-13873374719)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 464
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/50filesystems: IN: PARTITION_INFO =dev=sdb 3958374400-13873374719
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 465
parted_server: Opening infifo
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 466
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 467
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 468
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 469
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: *******************************************************
/lib/partman/update.d/21lvm_sync_flag: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: msdos


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 470
parted_server: Opening infifo
/lib/partman/update.d/21lvm_sync_flag: IN: GET_FLAGS =dev=sdb 13873709056-16022241279
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Partition found (13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 471
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60lvm_visuals: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/60swap: IN: CHANGE_FILE_SYSTEM =dev=sdb 13873709056-16022241279 linux-swap
parted_server: Read command: CHANGE_FILE_SYSTEM
parted_server: Opening outfifo
parted_server: command_change_file_system(13873709056-16022241279,linux-swap)
parted_server: partition_with_id(13873709056-16022241279)
parted_server: Already using filesystem linux-swap(v1)
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 472
parted_server: Opening infifo
/lib/partman/update.d/61crypto_visuals: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 473
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 474
parted_server: Opening infifo
/lib/partman/init.d/80autouse_swap: *******************************************************
/lib/partman/commit.d/01unmount_busy: *******************************************************
/lib/partman/commit.d/01unmount_busy: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 475
parted_server: Opening infifo
/lib/partman/commit.d/01unmount_busy: IN: IS_BUSY =dev=sdb 32256-3958374399
parted_server: Read command: IS_BUSY
parted_server: command_is_busy()
parted_server: Opening outfifo
parted_server: command_is_busy: busy check for id 32256-3958374399
parted_server: partition_with_id(32256-3958374399)
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 476
parted_server: Opening infifo
/lib/partman/commit.d/01unmount_busy: IN: IS_BUSY =dev=sdb 3958374400-13873374719
parted_server: Read command: IS_BUSY
parted_server: command_is_busy()
parted_server: Opening outfifo
parted_server: command_is_busy: busy check for id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 477
parted_server: Opening infifo
/lib/partman/commit.d/01unmount_busy: IN: IS_BUSY =dev=sdb 13873709056-16022241279
parted_server: Read command: IS_BUSY
parted_server: command_is_busy()
parted_server: Opening outfifo
parted_server: command_is_busy: busy check for id 13873709056-16022241279
parted_server: partition_with_id(13873709056-16022241279)
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 478
parted_server: Opening infifo
/lib/partman/commit.d/30parted: *******************************************************
/lib/partman/commit.d/30parted: IN: IS_CHANGED =dev=sdb
parted_server: Read command: IS_CHANGED
parted_server: command_is_changed(=dev=sdb)
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 479
parted_server: Opening infifo
/lib/partman/commit.d/45format_swap: *******************************************************
/lib/partman/commit.d/45format_swap: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 480
parted_server: Opening infifo
/lib/partman/commit.d/50format_basicfilesystems: *******************************************************
/lib/partman/commit.d/50format_basicfilesystems: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 481
parted_server: Opening infifo
/lib/partman/commit.d/50format_basicfilesystems: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 482
parted_server: Opening infifo
/lib/partman/commit.d/50format_btrfs: *******************************************************
/lib/partman/commit.d/50format_btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 483
parted_server: Opening infifo
/lib/partman/commit.d/50format_btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 484
parted_server: Opening infifo
/lib/partman/commit.d/50format_efi: *******************************************************
/lib/partman/commit.d/50format_efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 485
parted_server: Opening infifo
/lib/partman/commit.d/50format_efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 486
parted_server: Opening infifo
/lib/partman/commit.d/50format_ext3: *******************************************************
/lib/partman/commit.d/50format_ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 487
parted_server: Opening infifo
/lib/partman/commit.d/50format_ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 488
parted_server: Opening infifo
/lib/partman/commit.d/50format_ext3: Try to create file system for /var/lib/partman/devices/=dev=sdb/3958374400-13873374719
/lib/partman/commit.d/50format_ext3: IN: PARTITION_INFO =dev=sdb 3958374400-13873374719
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 3958374400-13873374719
parted_server: partition_with_id(3958374400-13873374719)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 489
parted_server: Opening infifo
/lib/partman/commit.d/50format_jfs: *******************************************************
/lib/partman/commit.d/50format_jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 490
parted_server: Opening infifo
/lib/partman/commit.d/50format_jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 491
parted_server: Opening infifo
/lib/partman/commit.d/50format_xfs: *******************************************************
/lib/partman/commit.d/50format_xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 492
parted_server: Opening infifo
/lib/partman/commit.d/50format_xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 493
parted_server: Opening infifo
/lib/partman/finish.d/01apt_clone_save: *******************************************************
/lib/partman/finish.d/01apt_clone_save: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 494
parted_server: Opening infifo
/lib/partman/finish.d/10clear_partitions: *******************************************************
/lib/partman/finish.d/10clear_partitions: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 495
parted_server: Opening infifo
/lib/partman/finish.d/20mount_partitions: *******************************************************
/lib/partman/fstab.d/basic: *******************************************************
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 496
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: *******************************************************
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 497
parted_server: Opening infifo
/lib/partman/fstab.d/efi: *******************************************************
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 498
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: *******************************************************
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 499
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: *******************************************************
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 500
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: *******************************************************
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 501
parted_server: Opening infifo
/lib/partman/fstab.d/basic: *******************************************************
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 502
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: *******************************************************
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 503
parted_server: Opening infifo
/lib/partman/fstab.d/efi: *******************************************************
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 504
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: *******************************************************
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 505
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: *******************************************************
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 506
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: *******************************************************
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 507
parted_server: Opening infifo
/lib/partman/finish.d/55crypto_config: *******************************************************
/lib/partman/finish.d/70aptinstall_basicfilesystems: *******************************************************
/lib/partman/finish.d/70aptinstall_basicfilesystems: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 508
parted_server: Opening infifo
/lib/partman/finish.d/70aptinstall_btrfs: *******************************************************
/lib/partman/finish.d/70aptinstall_btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 509
parted_server: Opening infifo
/lib/partman/finish.d/70aptinstall_ext3: *******************************************************
/lib/partman/finish.d/70aptinstall_ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 510
parted_server: Opening infifo
/lib/partman/finish.d/70aptinstall_jfs: *******************************************************
/lib/partman/finish.d/70aptinstall_jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 511
parted_server: Opening infifo
/lib/partman/finish.d/70aptinstall_xfs: *******************************************************
/lib/partman/finish.d/70aptinstall_xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 512
parted_server: Opening infifo
/lib/partman/finish.d/70crypto_aptinstall: *******************************************************
/lib/partman/finish.d/70crypto_aptinstall: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 513
parted_server: Opening infifo
/lib/partman/finish.d/75reformat_after_restart: *******************************************************
/lib/partman/finish.d/75reformat_after_restart: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-3958374399    3958342144    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    3958374400-13873374719    9915000320    primary    ext4    /dev/sdb2    


parted_server: OUT: 3    13873709056-16022241279    2148532224    primary    linux-swap    /dev/sdb3    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 514
parted_server: Opening infifo
/lib/partman/finish.d/80parted: *******************************************************
/lib/partman/finish.d/80parted: IN: QUIT
parted_server: Read command: QUIT
parted_server: Quitting

```

```
Feb  8 07:04:42 lubuntu rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="1078" x-info="http://www.rsyslog.com"] start
Feb  8 07:04:42 lubuntu rsyslogd: rsyslogd's groupid changed to 104
Feb  8 07:04:42 lubuntu rsyslogd: rsyslogd's userid changed to 101
Feb  8 07:04:42 lubuntu rsyslogd-2039: Could no open output pipe '/dev/xconsole': No such file or directory [try http://www.rsyslog.com/e/2039 ]
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Initializing cgroup subsys cpuacct
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Linux version 3.13.0-1-generic (buildd@toyol) (gcc version 4.8.2 (Ubuntu/Linaro 4.8.2-12ubuntu2) ) #16-Ubuntu SMP Tue Jan 7 19:44:06 UTC 2014 (Ubuntu 3.13.0-1.16-generic 3.13.0-rc7)
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Command line: initrd=/ubninit file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash -- BOOT_IMAGE=/ubnkern 
Feb  8 07:04:42 lubuntu kernel: [    0.000000] KERNEL supported cpus:
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   Intel GenuineIntel
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   AMD AuthenticAMD
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   Centaur CentaurHauls
Feb  8 07:04:42 lubuntu kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Feb  8 07:04:42 lubuntu kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
Feb  8 07:04:42 lubuntu kernel: [    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
Feb  8 07:04:42 lubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Feb  8 07:04:42 lubuntu kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007ffcffff] usable
Feb  8 07:04:42 lubuntu kernel: [    0.000000] BIOS-e820: [mem 0x000000007ffd0000-0x000000007ffddfff] ACPI data
Feb  8 07:04:42 lubuntu kernel: [    0.000000] BIOS-e820: [mem 0x000000007ffde000-0x000000007fffffff] ACPI NVS
Feb  8 07:04:42 lubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Feb  8 07:04:42 lubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000fff80000-0x00000000ffffffff] reserved
Feb  8 07:04:42 lubuntu kernel: [    0.000000] NX (Execute Disable) protection: active
Feb  8 07:04:42 lubuntu kernel: [    0.000000] SMBIOS 2.3 present.
Feb  8 07:04:42 lubuntu kernel: [    0.000000] DMI: MSI MS-6702/MS-6702, BIOS 080011  02/24/2006
Feb  8 07:04:42 lubuntu kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Feb  8 07:04:42 lubuntu kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Feb  8 07:04:42 lubuntu kernel: [    0.000000] AGP bridge at 00:00:00
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Aperture from AGP @ e0000000 old size 32 MB
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Aperture from AGP @ e0000000 size 256 MB (APSIZE f00)
Feb  8 07:04:42 lubuntu kernel: [    0.000000] e820: last_pfn = 0x7ffd0 max_arch_pfn = 0x400000000
Feb  8 07:04:42 lubuntu kernel: [    0.000000] MTRR default type: uncachable
Feb  8 07:04:42 lubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   00000-9FFFF write-back
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   A0000-EFFFF uncachable
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   F0000-FFFFF write-protect
Feb  8 07:04:42 lubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   0 base 0000000000 mask FF80000000 write-back
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   1 disabled
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   2 disabled
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   3 disabled
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   4 disabled
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   5 disabled
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   6 disabled
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   7 disabled
Feb  8 07:04:42 lubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Feb  8 07:04:42 lubuntu kernel: [    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Scanning 1 areas for low memory corruption
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
Feb  8 07:04:42 lubuntu kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Feb  8 07:04:42 lubuntu kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Feb  8 07:04:42 lubuntu kernel: [    0.000000] BRK [0x01fda000, 0x01fdafff] PGTABLE
Feb  8 07:04:42 lubuntu kernel: [    0.000000] BRK [0x01fdb000, 0x01fdbfff] PGTABLE
Feb  8 07:04:42 lubuntu kernel: [    0.000000] BRK [0x01fdc000, 0x01fdcfff] PGTABLE
Feb  8 07:04:42 lubuntu kernel: [    0.000000] init_memory_mapping: [mem 0x7ea00000-0x7ebfffff]
Feb  8 07:04:42 lubuntu kernel: [    0.000000]  [mem 0x7ea00000-0x7ebfffff] page 2M
Feb  8 07:04:42 lubuntu kernel: [    0.000000] BRK [0x01fdd000, 0x01fddfff] PGTABLE
Feb  8 07:04:42 lubuntu kernel: [    0.000000] init_memory_mapping: [mem 0x7c000000-0x7e9fffff]
Feb  8 07:04:42 lubuntu kernel: [    0.000000]  [mem 0x7c000000-0x7e9fffff] page 2M
Feb  8 07:04:42 lubuntu kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0x7bffffff]
Feb  8 07:04:42 lubuntu kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Feb  8 07:04:42 lubuntu kernel: [    0.000000]  [mem 0x00200000-0x7bffffff] page 2M
Feb  8 07:04:42 lubuntu kernel: [    0.000000] init_memory_mapping: [mem 0x7ec00000-0x7ffcffff]
Feb  8 07:04:42 lubuntu kernel: [    0.000000]  [mem 0x7ec00000-0x7fdfffff] page 2M
Feb  8 07:04:42 lubuntu kernel: [    0.000000]  [mem 0x7fe00000-0x7ffcffff] page 4k
Feb  8 07:04:42 lubuntu kernel: [    0.000000] BRK [0x01fde000, 0x01fdefff] PGTABLE
Feb  8 07:04:42 lubuntu kernel: [    0.000000] RAMDISK: [mem 0x7ec82000-0x7ffcefff]
Feb  8 07:04:42 lubuntu kernel: [    0.000000] ACPI: RSDP 00000000000f7730 000014 (v00 ACPIAM)
Feb  8 07:04:42 lubuntu kernel: [    0.000000] ACPI: RSDT 000000007ffd0000 000030 (v01 A M I  OEMRSDT  02000624 MSFT 00000097)
Feb  8 07:04:42 lubuntu kernel: [    0.000000] ACPI: FACP 000000007ffd0200 000084 (v02 A M I  OEMFACP  02000624 MSFT 00000097)
Feb  8 07:04:42 lubuntu kernel: [    0.000000] ACPI: DSDT 000000007ffd03f0 003D81 (v01  1XXXX 1XXXX007 00000007 INTL 02002026)
Feb  8 07:04:42 lubuntu kernel: [    0.000000] ACPI: FACS 000000007ffde000 000040
Feb  8 07:04:42 lubuntu kernel: [    0.000000] ACPI: APIC 000000007ffd0390 000054 (v01 A M I  OEMAPIC  02000624 MSFT 00000097)
Feb  8 07:04:42 lubuntu kernel: [    0.000000] ACPI: OEMB 000000007ffde040 000046 (v01 A M I  AMI_OEM  02000624 MSFT 00000097)
Feb  8 07:04:42 lubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Feb  8 07:04:42 lubuntu kernel: [    0.000000] No NUMA configuration found
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000007ffcffff]
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x7ffcffff]
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   NODE_DATA [mem 0x7ec7d000-0x7ec81fff]
Feb  8 07:04:42 lubuntu kernel: [    0.000000]  [ffffea0000000000-ffffea0001ffffff] PMD -> [ffff88007c400000-ffff88007e3fffff] on node 0
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Zone ranges:
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   Normal   empty
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Movable zone start for each node
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Early memory node ranges
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   node   0: [mem 0x00001000-0x0009efff]
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   node   0: [mem 0x00100000-0x7ffcffff]
Feb  8 07:04:42 lubuntu kernel: [    0.000000] On node 0 totalpages: 524142
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   DMA zone: 21 pages reserved
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   DMA zone: 3998 pages, LIFO batch:0
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   DMA32 zone: 8128 pages used for memmap
Feb  8 07:04:42 lubuntu kernel: [    0.000000]   DMA32 zone: 520144 pages, LIFO batch:31
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Feb  8 07:04:42 lubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Feb  8 07:04:42 lubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb  8 07:04:42 lubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Feb  8 07:04:42 lubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Feb  8 07:04:42 lubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
Feb  8 07:04:42 lubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb  8 07:04:42 lubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Feb  8 07:04:42 lubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Feb  8 07:04:42 lubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Feb  8 07:04:42 lubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb  8 07:04:42 lubuntu kernel: [    0.000000] smpboot: Allowing 1 CPUs, 0 hotplug CPUs
Feb  8 07:04:42 lubuntu kernel: [    0.000000] nr_irqs_gsi: 40
Feb  8 07:04:42 lubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Feb  8 07:04:42 lubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Feb  8 07:04:42 lubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Feb  8 07:04:42 lubuntu kernel: [    0.000000] e820: [mem 0x80000000-0xfebfffff] available for PCI devices
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Feb  8 07:04:42 lubuntu kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:1 nr_node_ids:1
Feb  8 07:04:42 lubuntu kernel: [    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88007ea00000 s86400 r8192 d24192 u2097152
Feb  8 07:04:42 lubuntu kernel: [    0.000000] pcpu-alloc: s86400 r8192 d24192 u2097152 alloc=1*2097152
Feb  8 07:04:42 lubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 515929
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Policy zone: DMA32
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Kernel command line: initrd=/ubninit file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash -- BOOT_IMAGE=/ubnkern 
Feb  8 07:04:42 lubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Checking aperture...
Feb  8 07:04:42 lubuntu kernel: [    0.000000] AGP bridge at 00:00:00
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Aperture from AGP @ e0000000 old size 32 MB
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Aperture from AGP @ e0000000 size 256 MB (APSIZE f00)
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Node 0: aperture @ d0000000 size 256 MB
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Memory: 2027308K/2096568K available (7275K kernel code, 1135K rwdata, 3368K rodata, 1332K init, 1436K bss, 69260K reserved)
Feb  8 07:04:42 lubuntu kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Feb  8 07:04:42 lubuntu kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Feb  8 07:04:42 lubuntu kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=1.
Feb  8 07:04:42 lubuntu kernel: [    0.000000]     Offload RCU callbacks from all CPUs
Feb  8 07:04:42 lubuntu kernel: [    0.000000]     Offload RCU callbacks from CPUs: 0.
Feb  8 07:04:42 lubuntu kernel: [    0.000000] NR_IRQS:16640 nr_irqs:256 16
Feb  8 07:04:42 lubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
Feb  8 07:04:42 lubuntu kernel: [    0.000000] console [tty0] enabled
Feb  8 07:04:42 lubuntu kernel: [    0.000000] allocated 8388608 bytes of page_cgroup
Feb  8 07:04:42 lubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Feb  8 07:04:42 lubuntu kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Feb  8 07:04:42 lubuntu kernel: [    0.000000] tsc: Detected 2000.111 MHz processor
Feb  8 07:04:42 lubuntu kernel: [    0.008005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4000.22 BogoMIPS (lpj=8000444)
Feb  8 07:04:42 lubuntu kernel: [    0.008009] pid_max: default: 32768 minimum: 301
Feb  8 07:04:42 lubuntu kernel: [    0.008054] Security Framework initialized
Feb  8 07:04:42 lubuntu kernel: [    0.008090] AppArmor: AppArmor initialized
Feb  8 07:04:42 lubuntu kernel: [    0.008092] Yama: becoming mindful.
Feb  8 07:04:42 lubuntu kernel: [    0.008375] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Feb  8 07:04:42 lubuntu kernel: [    0.014089] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Feb  8 07:04:42 lubuntu kernel: [    0.015202] Mount-cache hash table entries: 256
Feb  8 07:04:42 lubuntu kernel: [    0.015611] Initializing cgroup subsys memory
Feb  8 07:04:42 lubuntu kernel: [    0.015625] Initializing cgroup subsys devices
Feb  8 07:04:42 lubuntu kernel: [    0.015628] Initializing cgroup subsys freezer
Feb  8 07:04:42 lubuntu kernel: [    0.015631] Initializing cgroup subsys blkio
Feb  8 07:04:42 lubuntu kernel: [    0.015633] Initializing cgroup subsys perf_event
Feb  8 07:04:42 lubuntu kernel: [    0.015637] Initializing cgroup subsys hugetlb
Feb  8 07:04:42 lubuntu kernel: [    0.015670] tseg: 0000000000
Feb  8 07:04:42 lubuntu kernel: [    0.015680] mce: CPU supports 5 MCE banks
Feb  8 07:04:42 lubuntu kernel: [    0.015697] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
Feb  8 07:04:42 lubuntu kernel: [    0.015697] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4
Feb  8 07:04:42 lubuntu kernel: [    0.015697] tlb_flushall_shift: 4
Feb  8 07:04:42 lubuntu kernel: [    0.025455] Freeing SMP alternatives memory: 28K (ffffffff81e6a000 - ffffffff81e71000)
Feb  8 07:04:42 lubuntu kernel: [    0.026693] ACPI: Core revision 20131115
Feb  8 07:04:42 lubuntu kernel: [    0.028939] ACPI: All ACPI Tables successfully acquired
Feb  8 07:04:42 lubuntu kernel: [    0.032012] ftrace: allocating 28199 entries in 111 pages
Feb  8 07:04:42 lubuntu kernel: [    0.045238] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
Feb  8 07:04:42 lubuntu kernel: [    0.086843] smpboot: CPU0: AMD Athlon(tm) 64 Processor 3000+ (fam: 0f, model: 0c, stepping: 00)
Feb  8 07:04:42 lubuntu kernel: [    0.088000] APIC calibration not consistent with PM-Timer: 136ms instead of 100ms
Feb  8 07:04:42 lubuntu kernel: [    0.088000] APIC delta adjusted to PM-Timer: 1250042 (1700154)
Feb  8 07:04:42 lubuntu kernel: [    0.088000] Performance Events: AMD PMU driver.
Feb  8 07:04:42 lubuntu kernel: [    0.088000] ... version:                0
Feb  8 07:04:42 lubuntu kernel: [    0.088000] ... bit width:              48
Feb  8 07:04:42 lubuntu kernel: [    0.088000] ... generic registers:      4
Feb  8 07:04:42 lubuntu kernel: [    0.088000] ... value mask:             0000ffffffffffff
Feb  8 07:04:42 lubuntu kernel: [    0.088000] ... max period:             00007fffffffffff
Feb  8 07:04:42 lubuntu kernel: [    0.088000] ... fixed-purpose events:   0
Feb  8 07:04:42 lubuntu kernel: [    0.088000] ... event mask:             000000000000000f
Feb  8 07:04:42 lubuntu kernel: [    0.089456] x86: Booted up 1 node, 1 CPUs
Feb  8 07:04:42 lubuntu kernel: [    0.089464] smpboot: Total of 1 processors activated (4000.22 BogoMIPS)
Feb  8 07:04:42 lubuntu kernel: [    0.089907] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Feb  8 07:04:42 lubuntu kernel: [    0.090202] devtmpfs: initialized
Feb  8 07:04:42 lubuntu kernel: [    0.095372] EVM: security.selinux
Feb  8 07:04:42 lubuntu kernel: [    0.095374] EVM: security.SMACK64
Feb  8 07:04:42 lubuntu kernel: [    0.095376] EVM: security.ima
Feb  8 07:04:42 lubuntu kernel: [    0.095377] EVM: security.capability
Feb  8 07:04:42 lubuntu kernel: [    0.095448] PM: Registering ACPI NVS region [mem 0x7ffde000-0x7fffffff] (139264 bytes)
Feb  8 07:04:42 lubuntu kernel: [    0.097129] pinctrl core: initialized pinctrl subsystem
Feb  8 07:04:42 lubuntu kernel: [    0.097244] regulator-dummy: no parameters
Feb  8 07:04:42 lubuntu kernel: [    0.097294] RTC time:  7:04:13, date: 02/08/14
Feb  8 07:04:42 lubuntu kernel: [    0.097357] NET: Registered protocol family 16
Feb  8 07:04:42 lubuntu kernel: [    0.097553] cpuidle: using governor ladder
Feb  8 07:04:42 lubuntu kernel: [    0.097555] cpuidle: using governor menu
Feb  8 07:04:42 lubuntu kernel: [    0.097563] node 0 link 0: io port [1000, ffffff]
Feb  8 07:04:42 lubuntu kernel: [    0.097567] TOM: 0000000080000000 aka 2048M
Feb  8 07:04:42 lubuntu kernel: [    0.097570] node 0 link 0: mmio [a0000, bffff]
Feb  8 07:04:42 lubuntu kernel: [    0.097574] node 0 link 0: mmio [80000000, ffffffff]
Feb  8 07:04:42 lubuntu kernel: [    0.097579] bus: [bus 00-ff] on node 0 link 0
Feb  8 07:04:42 lubuntu kernel: [    0.097581] bus: 00 [io  0x0000-0xffff]
Feb  8 07:04:42 lubuntu kernel: [    0.097582] bus: 00 [mem 0x000a0000-0x000bffff]
Feb  8 07:04:42 lubuntu kernel: [    0.097584] bus: 00 [mem 0x80000000-0xfcffffffff]
Feb  8 07:04:42 lubuntu kernel: [    0.097642] ACPI: bus type PCI registered
Feb  8 07:04:42 lubuntu kernel: [    0.097645] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Feb  8 07:04:42 lubuntu kernel: [    0.097726] PCI: Using configuration type 1 for base access
Feb  8 07:04:42 lubuntu kernel: [    0.099024] bio: create slab <bio-0> at 0
Feb  8 07:04:42 lubuntu kernel: [    0.099231] ACPI: Added _OSI(Module Device)
Feb  8 07:04:42 lubuntu kernel: [    0.099233] ACPI: Added _OSI(Processor Device)
Feb  8 07:04:42 lubuntu kernel: [    0.099235] ACPI: Added _OSI(3.0 _SCP Extensions)
Feb  8 07:04:42 lubuntu kernel: [    0.099237] ACPI: Added _OSI(Processor Aggregator Device)
Feb  8 07:04:42 lubuntu kernel: [    0.100790] ACPI: Executed 1 blocks of module-level executable AML code
Feb  8 07:04:42 lubuntu kernel: [    0.102601] ACPI: Interpreter enabled
Feb  8 07:04:42 lubuntu kernel: [    0.102613] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
Feb  8 07:04:42 lubuntu kernel: [    0.102618] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S3_] (20131115/hwxface-580)
Feb  8 07:04:42 lubuntu kernel: [    0.102630] ACPI: (supports S0 S1 S4 S5)
Feb  8 07:04:42 lubuntu kernel: [    0.102633] ACPI: Using IOAPIC for interrupt routing
Feb  8 07:04:42 lubuntu kernel: [    0.102669] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Feb  8 07:04:42 lubuntu kernel: [    0.102786] ACPI: No dock devices found.
Feb  8 07:04:42 lubuntu kernel: [    0.109571] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Feb  8 07:04:42 lubuntu kernel: [    0.109580] acpi PNP0A03:00: _OSC: OS supports [ASPM ClockPM Segments MSI]
Feb  8 07:04:42 lubuntu kernel: [    0.109587] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
Feb  8 07:04:42 lubuntu kernel: [    0.109702] acpi PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Feb  8 07:04:42 lubuntu kernel: [    0.109705] acpi PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
Feb  8 07:04:42 lubuntu kernel: [    0.109708] acpi PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Feb  8 07:04:42 lubuntu kernel: [    0.109711] acpi PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
Feb  8 07:04:42 lubuntu kernel: [    0.109714] acpi PNP0A03:00: host bridge window [mem 0x80000000-0xfff7ffff] (ignored)
Feb  8 07:04:42 lubuntu kernel: [    0.109717] PCI: root bus 00: hardware-probed resources
Feb  8 07:04:42 lubuntu kernel: [    0.109724] acpi PNP0A03:00: fail to add MMCONFIG information, can't access extended PCI configuration space under this bridge.
Feb  8 07:04:42 lubuntu kernel: [    0.109917] PCI host bridge to bus 0000:00
Feb  8 07:04:42 lubuntu kernel: [    0.109921] pci_bus 0000:00: root bus resource [bus 00-ff]
Feb  8 07:04:42 lubuntu kernel: [    0.109924] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
Feb  8 07:04:42 lubuntu kernel: [    0.109927] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Feb  8 07:04:42 lubuntu kernel: [    0.109930] pci_bus 0000:00: root bus resource [mem 0x80000000-0xfcffffffff]
Feb  8 07:04:42 lubuntu kernel: [    0.109946] pci 0000:00:00.0: [1106:3188] type 00 class 0x060000
Feb  8 07:04:42 lubuntu kernel: [    0.109958] pci 0000:00:00.0: reg 0x10: [mem 0xe0000000-0xefffffff pref]
Feb  8 07:04:42 lubuntu kernel: [    0.110096] pci 0000:00:01.0: [1106:b188] type 01 class 0x060400
Feb  8 07:04:42 lubuntu kernel: [    0.110133] pci 0000:00:01.0: supports D1
Feb  8 07:04:42 lubuntu kernel: [    0.110214] pci 0000:00:07.0: [13f6:0111] type 00 class 0x040100
Feb  8 07:04:42 lubuntu kernel: [    0.110228] pci 0000:00:07.0: reg 0x10: [io  0xe800-0xe8ff]
Feb  8 07:04:42 lubuntu kernel: [    0.110284] pci 0000:00:07.0: supports D1 D2
Feb  8 07:04:42 lubuntu kernel: [    0.110327] pci 0000:00:07.0: System wakeup disabled by ACPI
Feb  8 07:04:42 lubuntu kernel: [    0.110379] pci 0000:00:0b.0: [10ec:8169] type 00 class 0x020000
Feb  8 07:04:42 lubuntu kernel: [    0.110393] pci 0000:00:0b.0: reg 0x10: [io  0xe400-0xe4ff]
Feb  8 07:04:42 lubuntu kernel: [    0.110402] pci 0000:00:0b.0: reg 0x14: [mem 0xfebffc00-0xfebffcff]
Feb  8 07:04:42 lubuntu kernel: [    0.110432] pci 0000:00:0b.0: reg 0x30: [mem 0xfebc0000-0xfebdffff pref]
Feb  8 07:04:42 lubuntu kernel: [    0.110453] pci 0000:00:0b.0: supports D1 D2
Feb  8 07:04:42 lubuntu kernel: [    0.110456] pci 0000:00:0b.0: PME# supported from D1 D2 D3hot D3cold
Feb  8 07:04:42 lubuntu kernel: [    0.110541] pci 0000:00:10.0: [1106:3038] type 00 class 0x0c0300
Feb  8 07:04:42 lubuntu kernel: [    0.110575] pci 0000:00:10.0: reg 0x20: [io  0xec00-0xec1f]
Feb  8 07:04:42 lubuntu kernel: [    0.110607] pci 0000:00:10.0: supports D1 D2
Feb  8 07:04:42 lubuntu kernel: [    0.110610] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb  8 07:04:42 lubuntu kernel: [    0.110652] pci 0000:00:10.0: System wakeup disabled by ACPI
Feb  8 07:04:42 lubuntu kernel: [    0.110698] pci 0000:00:10.1: [1106:3038] type 00 class 0x0c0300
Feb  8 07:04:42 lubuntu kernel: [    0.110732] pci 0000:00:10.1: reg 0x20: [io  0xe000-0xe01f]
Feb  8 07:04:42 lubuntu kernel: [    0.110763] pci 0000:00:10.1: supports D1 D2
Feb  8 07:04:42 lubuntu kernel: [    0.110766] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
Feb  8 07:04:42 lubuntu kernel: [    0.110809] pci 0000:00:10.1: System wakeup disabled by ACPI
Feb  8 07:04:42 lubuntu kernel: [    0.110857] pci 0000:00:10.2: [1106:3038] type 00 class 0x0c0300
Feb  8 07:04:42 lubuntu kernel: [    0.110891] pci 0000:00:10.2: reg 0x20: [io  0xdc00-0xdc1f]
Feb  8 07:04:42 lubuntu kernel: [    0.110922] pci 0000:00:10.2: supports D1 D2
Feb  8 07:04:42 lubuntu kernel: [    0.110925] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
Feb  8 07:04:42 lubuntu kernel: [    0.110971] pci 0000:00:10.2: System wakeup disabled by ACPI
Feb  8 07:04:42 lubuntu kernel: [    0.111016] pci 0000:00:10.3: [1106:3038] type 00 class 0x0c0300
Feb  8 07:04:42 lubuntu kernel: [    0.111050] pci 0000:00:10.3: reg 0x20: [io  0xd800-0xd81f]
Feb  8 07:04:42 lubuntu kernel: [    0.111081] pci 0000:00:10.3: supports D1 D2
Feb  8 07:04:42 lubuntu kernel: [    0.111084] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
Feb  8 07:04:42 lubuntu kernel: [    0.111127] pci 0000:00:10.3: System wakeup disabled by ACPI
Feb  8 07:04:42 lubuntu kernel: [    0.111173] pci 0000:00:10.4: [1106:3104] type 00 class 0x0c0320
Feb  8 07:04:42 lubuntu kernel: [    0.111186] pci 0000:00:10.4: reg 0x10: [mem 0xfebff800-0xfebff8ff]
Feb  8 07:04:42 lubuntu kernel: [    0.111238] pci 0000:00:10.4: supports D1 D2
Feb  8 07:04:42 lubuntu kernel: [    0.111241] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
Feb  8 07:04:42 lubuntu kernel: [    0.111328] pci 0000:00:11.0: [1106:3227] type 00 class 0x060100
Feb  8 07:04:42 lubuntu kernel: [    0.111375] HPET not enabled in BIOS. You might try hpet=force boot option
Feb  8 07:04:42 lubuntu kernel: [    0.111479] pci 0000:00:18.0: [1022:1100] type 00 class 0x060000
Feb  8 07:04:42 lubuntu kernel: [    0.111557] pci 0000:00:18.1: [1022:1101] type 00 class 0x060000
Feb  8 07:04:42 lubuntu kernel: [    0.111632] pci 0000:00:18.2: [1022:1102] type 00 class 0x060000
Feb  8 07:04:42 lubuntu kernel: [    0.111707] pci 0000:00:18.3: [1022:1103] type 00 class 0x060000
Feb  8 07:04:42 lubuntu kernel: [    0.111825] pci 0000:01:00.0: [1002:4153] type 00 class 0x030000
Feb  8 07:04:42 lubuntu kernel: [    0.111836] pci 0000:01:00.0: reg 0x10: [mem 0xd0000000-0xd7ffffff pref]
Feb  8 07:04:42 lubuntu kernel: [    0.111842] pci 0000:01:00.0: reg 0x14: [io  0xc800-0xc8ff]
Feb  8 07:04:42 lubuntu kernel: [    0.111848] pci 0000:01:00.0: reg 0x18: [mem 0xfeaf0000-0xfeafffff]
Feb  8 07:04:42 lubuntu kernel: [    0.111863] pci 0000:01:00.0: reg 0x30: [mem 0xfeac0000-0xfeadffff pref]
Feb  8 07:04:42 lubuntu kernel: [    0.111881] pci 0000:01:00.0: supports D1 D2
Feb  8 07:04:42 lubuntu kernel: [    0.111928] pci 0000:01:00.1: [1002:4173] type 00 class 0x038000
Feb  8 07:04:42 lubuntu kernel: [    0.111937] pci 0000:01:00.1: reg 0x10: [mem 0xc8000000-0xcfffffff pref]
Feb  8 07:04:42 lubuntu kernel: [    0.111943] pci 0000:01:00.1: reg 0x14: [mem 0xfeae0000-0xfeaeffff]
Feb  8 07:04:42 lubuntu kernel: [    0.111972] pci 0000:01:00.1: supports D1 D2
Feb  8 07:04:42 lubuntu kernel: [    0.112034] pci 0000:00:01.0: PCI bridge to [bus 01]
Feb  8 07:04:42 lubuntu kernel: [    0.112039] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
Feb  8 07:04:42 lubuntu kernel: [    0.112043] pci 0000:00:01.0:   bridge window [mem 0xfea00000-0xfeafffff]
Feb  8 07:04:42 lubuntu kernel: [    0.112047] pci 0000:00:01.0:   bridge window [mem 0xbe900000-0xde8fffff pref]
Feb  8 07:04:42 lubuntu kernel: [    0.112899] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Feb  8 07:04:42 lubuntu kernel: [    0.112961] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Feb  8 07:04:42 lubuntu kernel: [    0.113020] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Feb  8 07:04:42 lubuntu kernel: [    0.113079] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Feb  8 07:04:42 lubuntu kernel: [    0.113138] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Feb  8 07:04:42 lubuntu kernel: [    0.113198] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Feb  8 07:04:42 lubuntu kernel: [    0.113257] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Feb  8 07:04:42 lubuntu kernel: [    0.113316] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Feb  8 07:04:42 lubuntu kernel: [    0.113396] ACPI: \_SB_.PCI0: notify handler is installed
Feb  8 07:04:42 lubuntu kernel: [    0.113432] Found 1 acpi root devices
Feb  8 07:04:42 lubuntu kernel: [    0.113622] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Feb  8 07:04:42 lubuntu kernel: [    0.113624] vgaarb: loaded
Feb  8 07:04:42 lubuntu kernel: [    0.113626] vgaarb: bridge control possible 0000:01:00.0
Feb  8 07:04:42 lubuntu kernel: [    0.113899] SCSI subsystem initialized
Feb  8 07:04:42 lubuntu kernel: [    0.113995] libata version 3.00 loaded.
Feb  8 07:04:42 lubuntu kernel: [    0.114023] ACPI: bus type USB registered
Feb  8 07:04:42 lubuntu kernel: [    0.114049] usbcore: registered new interface driver usbfs
Feb  8 07:04:42 lubuntu kernel: [    0.114061] usbcore: registered new interface driver hub
Feb  8 07:04:42 lubuntu kernel: [    0.114093] usbcore: registered new device driver usb
Feb  8 07:04:42 lubuntu kernel: [    0.114240] PCI: Using ACPI for IRQ routing
Feb  8 07:04:42 lubuntu kernel: [    0.114244] PCI: pci_cache_line_size set to 64 bytes
Feb  8 07:04:42 lubuntu kernel: [    0.114254] pci 0000:00:01.0: address space collision: [mem 0xbe900000-0xde8fffff pref] conflicts with GART [mem 0xd0000000-0xdfffffff]
Feb  8 07:04:42 lubuntu kernel: [    0.114262] pci 0000:01:00.0: no compatible bridge window for [mem 0xd0000000-0xd7ffffff pref]
Feb  8 07:04:42 lubuntu kernel: [    0.114267] pci 0000:01:00.1: no compatible bridge window for [mem 0xc8000000-0xcfffffff pref]
Feb  8 07:04:42 lubuntu kernel: [    0.114297] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
Feb  8 07:04:42 lubuntu kernel: [    0.114300] e820: reserve RAM buffer [mem 0x7ffd0000-0x7fffffff]
Feb  8 07:04:42 lubuntu kernel: [    0.114433] NetLabel: Initializing
Feb  8 07:04:42 lubuntu kernel: [    0.114435] NetLabel:  domain hash size = 128
Feb  8 07:04:42 lubuntu kernel: [    0.114436] NetLabel:  protocols = UNLABELED CIPSOv4
Feb  8 07:04:42 lubuntu kernel: [    0.114456] NetLabel:  unlabeled traffic allowed by default
Feb  8 07:04:42 lubuntu kernel: [    0.114599] Switched to clocksource refined-jiffies
Feb  8 07:04:42 lubuntu kernel: [    0.125376] AppArmor: AppArmor Filesystem Enabled
Feb  8 07:04:42 lubuntu kernel: [    0.125430] pnp: PnP ACPI init
Feb  8 07:04:42 lubuntu kernel: [    0.125452] ACPI: bus type PNP registered
Feb  8 07:04:42 lubuntu kernel: [    0.125515] pnp 00:00: [dma 4]
Feb  8 07:04:42 lubuntu kernel: [    0.125552] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
Feb  8 07:04:42 lubuntu kernel: [    0.125599] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
Feb  8 07:04:42 lubuntu kernel: [    0.125690] pnp 00:02: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
Feb  8 07:04:42 lubuntu kernel: [    0.125740] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
Feb  8 07:04:42 lubuntu kernel: [    0.125778] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
Feb  8 07:04:42 lubuntu kernel: [    0.126544] system 00:05: [io  0x0290-0x0291] has been reserved
Feb  8 07:04:42 lubuntu kernel: [    0.126548] system 00:05: [io  0x0a10-0x0a1f] has been reserved
Feb  8 07:04:42 lubuntu kernel: [    0.126551] system 00:05: [io  0x0a20-0x0a2f] has been reserved
Feb  8 07:04:42 lubuntu kernel: [    0.126554] system 00:05: [io  0x0a30-0x0a3f] has been reserved
Feb  8 07:04:42 lubuntu kernel: [    0.126559] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb  8 07:04:42 lubuntu kernel: [    0.126681] system 00:06: [io  0x03e0-0x03e7] has been reserved
Feb  8 07:04:42 lubuntu kernel: [    0.126685] system 00:06: [io  0x04d0-0x04d1] has been reserved
Feb  8 07:04:42 lubuntu kernel: [    0.126688] system 00:06: [io  0x0800-0x087f] has been reserved
Feb  8 07:04:42 lubuntu kernel: [    0.126691] system 00:06: [io  0x0400-0x041f] has been reserved
Feb  8 07:04:42 lubuntu kernel: [    0.126695] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb  8 07:04:42 lubuntu kernel: [    0.126775] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
Feb  8 07:04:42 lubuntu kernel: [    0.126779] system 00:07: [mem 0xfee00000-0xfee00fff] has been reserved
Feb  8 07:04:42 lubuntu kernel: [    0.126782] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb  8 07:04:42 lubuntu kernel: [    0.126975] pnp 00:08: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:01:00.0 BAR 0 [mem 0x00000000-0x07ffffff pref]
Feb  8 07:04:42 lubuntu kernel: [    0.126979] pnp 00:08: disabling [mem 0x000c0000-0x000cffff] because it overlaps 0000:01:00.0 BAR 0 [mem 0x00000000-0x07ffffff pref]
Feb  8 07:04:42 lubuntu kernel: [    0.126983] pnp 00:08: disabling [mem 0x000e0000-0x000fffff] because it overlaps 0000:01:00.0 BAR 0 [mem 0x00000000-0x07ffffff pref]
Feb  8 07:04:42 lubuntu kernel: [    0.126987] pnp 00:08: disabling [mem 0x00100000-0x7fffffff] because it overlaps 0000:01:00.0 BAR 0 [mem 0x00000000-0x07ffffff pref]
Feb  8 07:04:42 lubuntu kernel: [    0.126992] pnp 00:08: disabling [mem 0x00000000-0x0009ffff disabled] because it overlaps 0000:01:00.1 BAR 0 [mem 0x00000000-0x07ffffff pref]
Feb  8 07:04:42 lubuntu kernel: [    0.126996] pnp 00:08: disabling [mem 0x000c0000-0x000cffff disabled] because it overlaps 0000:01:00.1 BAR 0 [mem 0x00000000-0x07ffffff pref]
Feb  8 07:04:42 lubuntu kernel: [    0.127000] pnp 00:08: disabling [mem 0x000e0000-0x000fffff disabled] because it overlaps 0000:01:00.1 BAR 0 [mem 0x00000000-0x07ffffff pref]
Feb  8 07:04:42 lubuntu kernel: [    0.127004] pnp 00:08: disabling [mem 0x00100000-0x7fffffff disabled] because it overlaps 0000:01:00.1 BAR 0 [mem 0x00000000-0x07ffffff pref]
Feb  8 07:04:42 lubuntu kernel: [    0.127041] system 00:08: [mem 0xfff80000-0xffffffff] has been reserved
Feb  8 07:04:42 lubuntu kernel: [    0.127045] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
Feb  8 07:04:42 lubuntu kernel: [    0.127184] pnp: PnP ACPI: found 9 devices
Feb  8 07:04:42 lubuntu kernel: [    0.127186] ACPI: bus type PNP unregistered
Feb  8 07:04:42 lubuntu kernel: [    0.133674] Switched to clocksource acpi_pm
Feb  8 07:04:42 lubuntu kernel: [    0.133710] pci 0000:00:01.0: BAR 15: assigned [mem 0x80000000-0x8fffffff pref]
Feb  8 07:04:42 lubuntu kernel: [    0.133715] pci 0000:01:00.0: BAR 0: assigned [mem 0x80000000-0x87ffffff pref]
Feb  8 07:04:42 lubuntu kernel: [    0.133722] pci 0000:01:00.1: BAR 0: assigned [mem 0x88000000-0x8fffffff pref]
Feb  8 07:04:42 lubuntu kernel: [    0.133726] pci 0000:00:01.0: PCI bridge to [bus 01]
Feb  8 07:04:42 lubuntu kernel: [    0.133730] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
Feb  8 07:04:42 lubuntu kernel: [    0.133735] pci 0000:00:01.0:   bridge window [mem 0xfea00000-0xfeafffff]
Feb  8 07:04:42 lubuntu kernel: [    0.133739] pci 0000:00:01.0:   bridge window [mem 0x80000000-0x8fffffff pref]
Feb  8 07:04:42 lubuntu kernel: [    0.133745] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
Feb  8 07:04:42 lubuntu kernel: [    0.133748] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
Feb  8 07:04:42 lubuntu kernel: [    0.133751] pci_bus 0000:00: resource 6 [mem 0x80000000-0xfcffffffff]
Feb  8 07:04:42 lubuntu kernel: [    0.133754] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
Feb  8 07:04:42 lubuntu kernel: [    0.133757] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
Feb  8 07:04:42 lubuntu kernel: [    0.133760] pci_bus 0000:01: resource 2 [mem 0x80000000-0x8fffffff pref]
Feb  8 07:04:42 lubuntu kernel: [    0.133819] NET: Registered protocol family 2
Feb  8 07:04:42 lubuntu kernel: [    0.134091] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Feb  8 07:04:42 lubuntu kernel: [    0.134255] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
Feb  8 07:04:42 lubuntu kernel: [    0.134469] TCP: Hash tables configured (established 16384 bind 16384)
Feb  8 07:04:42 lubuntu kernel: [    0.134582] TCP: reno registered
Feb  8 07:04:42 lubuntu kernel: [    0.134591] UDP hash table entries: 1024 (order: 3, 32768 bytes)
Feb  8 07:04:42 lubuntu kernel: [    0.134627] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
Feb  8 07:04:42 lubuntu kernel: [    0.134793] NET: Registered protocol family 1
Feb  8 07:04:42 lubuntu kernel: [    0.134817] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
Feb  8 07:04:42 lubuntu kernel: [    0.135842] pci 0000:01:00.0: Boot video device
Feb  8 07:04:42 lubuntu kernel: [    0.135847] PCI: CLS 64 bytes, default 64
Feb  8 07:04:42 lubuntu kernel: [    0.135991] Trying to unpack rootfs image as initramfs...
Feb  8 07:04:42 lubuntu kernel: [    5.652507] Freeing initrd memory: 19764K (ffff88007ec82000 - ffff88007ffcf000)
Feb  8 07:04:42 lubuntu kernel: [    5.652583] agpgart-amd64 0000:00:00.0: AGP bridge [1106/3188]
Feb  8 07:04:42 lubuntu kernel: [    5.666476] agpgart-amd64 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Feb  8 07:04:42 lubuntu kernel: [    5.666629] Scanning for low memory corruption every 60 seconds
Feb  8 07:04:42 lubuntu kernel: [    5.666897] Initialise system trusted keyring
Feb  8 07:04:42 lubuntu kernel: [    5.666970] audit: initializing netlink socket (disabled)
Feb  8 07:04:42 lubuntu kernel: [    5.666987] type=2000 audit(1391843058.663:1): initialized
Feb  8 07:04:42 lubuntu kernel: [    5.703174] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Feb  8 07:04:42 lubuntu kernel: [    5.704835] zbud: loaded
Feb  8 07:04:42 lubuntu kernel: [    5.705021] VFS: Disk quotas dquot_6.5.2
Feb  8 07:04:42 lubuntu kernel: [    5.705088] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Feb  8 07:04:42 lubuntu kernel: [    5.705814] fuse init (API version 7.22)
Feb  8 07:04:42 lubuntu kernel: [    5.705904] msgmni has been set to 3998
Feb  8 07:04:42 lubuntu kernel: [    5.705981] Key type big_key registered
Feb  8 07:04:42 lubuntu kernel: [    5.706367] Key type asymmetric registered
Feb  8 07:04:42 lubuntu kernel: [    5.706370] Asymmetric key parser 'x509' registered
Feb  8 07:04:42 lubuntu kernel: [    5.706417] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Feb  8 07:04:42 lubuntu kernel: [    5.706455] io scheduler noop registered
Feb  8 07:04:42 lubuntu kernel: [    5.706457] io scheduler deadline registered (default)
Feb  8 07:04:42 lubuntu kernel: [    5.706496] io scheduler cfq registered
Feb  8 07:04:42 lubuntu kernel: [    5.706634] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb  8 07:04:42 lubuntu kernel: [    5.706653] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Feb  8 07:04:42 lubuntu kernel: [    5.706826] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
Feb  8 07:04:42 lubuntu kernel: [    5.706834] ACPI: Sleep Button [SLPB]
Feb  8 07:04:42 lubuntu kernel: [    5.706884] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Feb  8 07:04:42 lubuntu kernel: [    5.706886] ACPI: Power Button [PWRB]
Feb  8 07:04:42 lubuntu kernel: [    5.706934] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Feb  8 07:04:42 lubuntu kernel: [    5.706937] ACPI: Power Button [PWRF]
Feb  8 07:04:42 lubuntu kernel: [    5.707048] GHES: HEST is not enabled!
Feb  8 07:04:42 lubuntu kernel: [    5.707200] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Feb  8 07:04:42 lubuntu kernel: [    5.708841] Linux agpgart interface v0.103
Feb  8 07:04:42 lubuntu kernel: [    5.710650] brd: module loaded
Feb  8 07:04:42 lubuntu kernel: [    5.711687] loop: module loaded
Feb  8 07:04:42 lubuntu kernel: [    5.712276] libphy: Fixed MDIO Bus: probed
Feb  8 07:04:42 lubuntu kernel: [    5.712399] tun: Universal TUN/TAP device driver, 1.6
Feb  8 07:04:42 lubuntu kernel: [    5.712401] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Feb  8 07:04:42 lubuntu kernel: [    5.712457] PPP generic driver version 2.4.2
Feb  8 07:04:42 lubuntu kernel: [    5.712505] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Feb  8 07:04:42 lubuntu kernel: [    5.712511] ehci-pci: EHCI PCI platform driver
Feb  8 07:04:42 lubuntu kernel: [    5.712731] ehci-pci 0000:00:10.4: EHCI Host Controller
Feb  8 07:04:42 lubuntu kernel: [    5.712740] ehci-pci 0000:00:10.4: new USB bus registered, assigned bus number 1
Feb  8 07:04:42 lubuntu kernel: [    5.712825] ehci-pci 0000:00:10.4: irq 21, io mem 0xfebff800
Feb  8 07:04:42 lubuntu kernel: [    5.724014] ehci-pci 0000:00:10.4: USB 2.0 started, EHCI 1.00
Feb  8 07:04:42 lubuntu kernel: [    5.724112] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Feb  8 07:04:42 lubuntu kernel: [    5.724115] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Feb  8 07:04:42 lubuntu kernel: [    5.724118] usb usb1: Product: EHCI Host Controller
Feb  8 07:04:42 lubuntu kernel: [    5.724120] usb usb1: Manufacturer: Linux 3.13.0-1-generic ehci_hcd
Feb  8 07:04:42 lubuntu kernel: [    5.724123] usb usb1: SerialNumber: 0000:00:10.4
Feb  8 07:04:42 lubuntu kernel: [    5.724266] hub 1-0:1.0: USB hub found
Feb  8 07:04:42 lubuntu kernel: [    5.724279] hub 1-0:1.0: 8 ports detected
Feb  8 07:04:42 lubuntu kernel: [    5.724496] ehci-platform: EHCI generic platform driver
Feb  8 07:04:42 lubuntu kernel: [    5.724509] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Feb  8 07:04:42 lubuntu kernel: [    5.724511] ohci-pci: OHCI PCI platform driver
Feb  8 07:04:42 lubuntu kernel: [    5.724523] ohci-platform: OHCI generic platform driver
Feb  8 07:04:42 lubuntu kernel: [    5.724531] uhci_hcd: USB Universal Host Controller Interface driver
Feb  8 07:04:42 lubuntu kernel: [    5.724669] uhci_hcd 0000:00:10.0: UHCI Host Controller
Feb  8 07:04:42 lubuntu kernel: [    5.724677] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
Feb  8 07:04:42 lubuntu kernel: [    5.724701] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000ec00
Feb  8 07:04:42 lubuntu kernel: [    5.724768] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
Feb  8 07:04:42 lubuntu kernel: [    5.724771] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Feb  8 07:04:42 lubuntu kernel: [    5.724774] usb usb2: Product: UHCI Host Controller
Feb  8 07:04:42 lubuntu kernel: [    5.724777] usb usb2: Manufacturer: Linux 3.13.0-1-generic uhci_hcd
Feb  8 07:04:42 lubuntu kernel: [    5.724779] usb usb2: SerialNumber: 0000:00:10.0
Feb  8 07:04:42 lubuntu kernel: [    5.724894] hub 2-0:1.0: USB hub found
Feb  8 07:04:42 lubuntu kernel: [    5.724903] hub 2-0:1.0: 2 ports detected
Feb  8 07:04:42 lubuntu kernel: [    5.725103] uhci_hcd 0000:00:10.1: UHCI Host Controller
Feb  8 07:04:42 lubuntu kernel: [    5.725110] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
Feb  8 07:04:42 lubuntu kernel: [    5.725131] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000e000
Feb  8 07:04:42 lubuntu kernel: [    5.725196] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
Feb  8 07:04:42 lubuntu kernel: [    5.725199] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Feb  8 07:04:42 lubuntu kernel: [    5.725202] usb usb3: Product: UHCI Host Controller
Feb  8 07:04:42 lubuntu kernel: [    5.725205] usb usb3: Manufacturer: Linux 3.13.0-1-generic uhci_hcd
Feb  8 07:04:42 lubuntu kernel: [    5.725208] usb usb3: SerialNumber: 0000:00:10.1
Feb  8 07:04:42 lubuntu kernel: [    5.725310] hub 3-0:1.0: USB hub found
Feb  8 07:04:42 lubuntu kernel: [    5.725321] hub 3-0:1.0: 2 ports detected
Feb  8 07:04:42 lubuntu kernel: [    5.725530] uhci_hcd 0000:00:10.2: UHCI Host Controller
Feb  8 07:04:42 lubuntu kernel: [    5.725537] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
Feb  8 07:04:42 lubuntu kernel: [    5.725558] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000dc00
Feb  8 07:04:42 lubuntu kernel: [    5.725628] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Feb  8 07:04:42 lubuntu kernel: [    5.725632] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Feb  8 07:04:42 lubuntu kernel: [    5.725634] usb usb4: Product: UHCI Host Controller
Feb  8 07:04:42 lubuntu kernel: [    5.725637] usb usb4: Manufacturer: Linux 3.13.0-1-generic uhci_hcd
Feb  8 07:04:42 lubuntu kernel: [    5.725639] usb usb4: SerialNumber: 0000:00:10.2
Feb  8 07:04:42 lubuntu kernel: [    5.725739] hub 4-0:1.0: USB hub found
Feb  8 07:04:42 lubuntu kernel: [    5.725748] hub 4-0:1.0: 2 ports detected
Feb  8 07:04:42 lubuntu kernel: [    5.725944] uhci_hcd 0000:00:10.3: UHCI Host Controller
Feb  8 07:04:42 lubuntu kernel: [    5.725954] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
Feb  8 07:04:42 lubuntu kernel: [    5.725975] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000d800
Feb  8 07:04:42 lubuntu kernel: [    5.726040] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Feb  8 07:04:42 lubuntu kernel: [    5.726043] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Feb  8 07:04:42 lubuntu kernel: [    5.726046] usb usb5: Product: UHCI Host Controller
Feb  8 07:04:42 lubuntu kernel: [    5.726049] usb usb5: Manufacturer: Linux 3.13.0-1-generic uhci_hcd
Feb  8 07:04:42 lubuntu kernel: [    5.726051] usb usb5: SerialNumber: 0000:00:10.3
Feb  8 07:04:42 lubuntu kernel: [    5.726160] hub 5-0:1.0: USB hub found
Feb  8 07:04:42 lubuntu kernel: [    5.726169] hub 5-0:1.0: 2 ports detected
Feb  8 07:04:42 lubuntu kernel: [    5.726332] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Feb  8 07:04:42 lubuntu kernel: [    5.726334] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Feb  8 07:04:42 lubuntu kernel: [    5.726537] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb  8 07:04:42 lubuntu kernel: [    5.726689] mousedev: PS/2 mouse device common for all mice
Feb  8 07:04:42 lubuntu kernel: [    5.726855] rtc_cmos 00:01: RTC can wake from S4
Feb  8 07:04:42 lubuntu kernel: [    5.727048] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
Feb  8 07:04:42 lubuntu kernel: [    5.727101] rtc_cmos 00:01: alarms up to one year, y3k, 114 bytes nvram
Feb  8 07:04:42 lubuntu kernel: [    5.727199] device-mapper: uevent: version 1.0.3
Feb  8 07:04:42 lubuntu kernel: [    5.727267] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
Feb  8 07:04:42 lubuntu kernel: [    5.727277] ledtrig-cpu: registered to indicate activity on CPUs
Feb  8 07:04:42 lubuntu kernel: [    5.727421] TCP: cubic registered
Feb  8 07:04:42 lubuntu kernel: [    5.727552] NET: Registered protocol family 10
Feb  8 07:04:42 lubuntu kernel: [    5.727828] NET: Registered protocol family 17
Feb  8 07:04:42 lubuntu kernel: [    5.727845] Key type dns_resolver registered
Feb  8 07:04:42 lubuntu kernel: [    5.728150] Loading compiled-in X.509 certificates
Feb  8 07:04:42 lubuntu kernel: [    5.729586] Loaded X.509 cert 'Magrathea: Glacier signing key: 5540ab562236f3f8412351b228ac5d8a29add607'
Feb  8 07:04:42 lubuntu kernel: [    5.729608] registered taskstats version 1
Feb  8 07:04:42 lubuntu kernel: [    5.733537] Key type trusted registered
Feb  8 07:04:42 lubuntu kernel: [    5.737014] Key type encrypted registered
Feb  8 07:04:42 lubuntu kernel: [    5.740524] AppArmor: AppArmor sha1 policy hashing enabled
Feb  8 07:04:42 lubuntu kernel: [    5.740532] IMA: No TPM chip found, activating TPM-bypass!
Feb  8 07:04:42 lubuntu kernel: [    5.740802]   Magic number: 2:827:65
Feb  8 07:04:42 lubuntu kernel: [    5.740946] rtc_cmos 00:01: setting system clock to 2014-02-08 07:04:19 UTC (1391843059)
Feb  8 07:04:42 lubuntu kernel: [    5.744136] [Firmware Bug]: powernow-k8: No PSB or ACPI _PSS objects
Feb  8 07:04:42 lubuntu kernel: [    5.744139] powernow-k8: Make sure that your BIOS is up to date and Cool'N'Quiet support is enabled in BIOS setup
Feb  8 07:04:42 lubuntu kernel: [    5.744218] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Feb  8 07:04:42 lubuntu kernel: [    5.744220] EDD information not available.
Feb  8 07:04:42 lubuntu kernel: [    5.744257] PM: Hibernation image not present or could not be loaded.
Feb  8 07:04:42 lubuntu kernel: [    5.747001] Freeing unused kernel memory: 1332K (ffffffff81d1d000 - ffffffff81e6a000)
Feb  8 07:04:42 lubuntu kernel: [    5.747007] Write protecting the kernel read-only data: 12288k
Feb  8 07:04:42 lubuntu kernel: [    5.751231] Freeing unused kernel memory: 904K (ffff88000171e000 - ffff880001800000)
Feb  8 07:04:42 lubuntu kernel: [    5.754612] Freeing unused kernel memory: 728K (ffff880001b4a000 - ffff880001c00000)
Feb  8 07:04:42 lubuntu kernel: [    5.757696] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Feb  8 07:04:42 lubuntu kernel: [    5.843655] [drm] Initialized drm 1.1.0 20060810
Feb  8 07:04:42 lubuntu kernel: [    5.854930] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Feb  8 07:04:42 lubuntu kernel: [    5.855137] r8169 0000:00:0b.0: PCI: Disallowing DAC for device
Feb  8 07:04:42 lubuntu kernel: [    5.855152] r8169 0000:00:0b.0 (unregistered net_device): not PCI Express
Feb  8 07:04:42 lubuntu kernel: [    5.855475] r8169 0000:00:0b.0 eth0: RTL8110s at 0xffffc90000306c00, 00:11:09:8e:39:b3, XID 04000000 IRQ 16
Feb  8 07:04:42 lubuntu kernel: [    5.855479] r8169 0000:00:0b.0 eth0: jumbo features [frames: 7152 bytes, tx checksumming: ok]
Feb  8 07:04:42 lubuntu kernel: [    6.034264] [drm] radeon kernel modesetting enabled.
Feb  8 07:04:42 lubuntu kernel: [    6.036107] usb 1-3: new high-speed USB device number 2 using ehci-pci
Feb  8 07:04:42 lubuntu kernel: [    6.039518] [drm] initializing kernel modesetting (RV350 0x1002:0x4153 0x17AF:0x201C).
Feb  8 07:04:42 lubuntu kernel: [    6.039543] [drm] register mmio base: 0xFEAF0000
Feb  8 07:04:42 lubuntu kernel: [    6.039545] [drm] register mmio size: 65536
Feb  8 07:04:42 lubuntu kernel: [    6.040200] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
Feb  8 07:04:42 lubuntu kernel: [    6.040210] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
Feb  8 07:04:42 lubuntu kernel: [    6.040250] radeon 0000:01:00.0: putting AGP V3 device into 8x mode
Feb  8 07:04:42 lubuntu kernel: [    6.040256] radeon 0000:01:00.0: GTT: 256M 0xD0000000 - 0xDFFFFFFF
Feb  8 07:04:42 lubuntu kernel: [    6.040259] [drm] Generation 2 PCI interface, using max accessible memory
Feb  8 07:04:42 lubuntu kernel: [    6.040264] radeon 0000:01:00.0: VRAM: 128M 0x0000000080000000 - 0x0000000087FFFFFF (128M used)
Feb  8 07:04:42 lubuntu kernel: [    6.042157] [drm] Detected VRAM RAM=128M, BAR=128M
Feb  8 07:04:42 lubuntu kernel: [    6.042161] [drm] RAM width 128bits DDR
Feb  8 07:04:42 lubuntu kernel: [    6.043989] [TTM] Zone  kernel: Available graphics memory: 1025032 kiB
Feb  8 07:04:42 lubuntu kernel: [    6.043993] [TTM] Initializing pool allocator
Feb  8 07:04:42 lubuntu kernel: [    6.043999] [TTM] Initializing DMA pool allocator
Feb  8 07:04:42 lubuntu kernel: [    6.044100] [drm] radeon: 128M of VRAM memory ready
Feb  8 07:04:42 lubuntu kernel: [    6.044103] [drm] radeon: 256M of GTT memory ready.
Feb  8 07:04:42 lubuntu kernel: [    6.044146] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
Feb  8 07:04:42 lubuntu kernel: [    6.047988] radeon 0000:01:00.0: WB disabled
Feb  8 07:04:42 lubuntu kernel: [    6.047995] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x00000000d0000000 and cpu addr 0xffffc90000394000
Feb  8 07:04:42 lubuntu kernel: [    6.047998] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Feb  8 07:04:42 lubuntu kernel: [    6.047999] [drm] Driver supports precise vblank timestamp query.
Feb  8 07:04:42 lubuntu kernel: [    6.048092] [drm] radeon: irq initialized.
Feb  8 07:04:42 lubuntu kernel: [    6.048101] [drm] Loading R300 Microcode
Feb  8 07:04:42 lubuntu kernel: [    6.048391] [drm] radeon: ring at 0x00000000D0001000
Feb  8 07:04:42 lubuntu kernel: [    6.048413] [drm] ring test succeeded in 1 usecs
Feb  8 07:04:42 lubuntu kernel: [    6.052453] [drm] ib test succeeded in 0 usecs
Feb  8 07:04:42 lubuntu kernel: [    6.053061] [drm] Radeon Display Connectors
Feb  8 07:04:42 lubuntu kernel: [    6.053063] [drm] Connector 0:
Feb  8 07:04:42 lubuntu kernel: [    6.053065] [drm]   VGA-1
Feb  8 07:04:42 lubuntu kernel: [    6.053068] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
Feb  8 07:04:42 lubuntu kernel: [    6.053070] [drm]   Encoders:
Feb  8 07:04:42 lubuntu kernel: [    6.053072] [drm]     CRT1: INTERNAL_DAC1
Feb  8 07:04:42 lubuntu kernel: [    6.053073] [drm] Connector 1:
Feb  8 07:04:42 lubuntu kernel: [    6.053075] [drm]   DVI-I-1
Feb  8 07:04:42 lubuntu kernel: [    6.053076] [drm]   HPD1
Feb  8 07:04:42 lubuntu kernel: [    6.053079] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
Feb  8 07:04:42 lubuntu kernel: [    6.053080] [drm]   Encoders:
Feb  8 07:04:42 lubuntu kernel: [    6.053081] [drm]     CRT2: INTERNAL_DAC2
Feb  8 07:04:42 lubuntu kernel: [    6.053083] [drm]     DFP1: INTERNAL_TMDS1
Feb  8 07:04:42 lubuntu kernel: [    6.053084] [drm] Connector 2:
Feb  8 07:04:42 lubuntu kernel: [    6.053086] [drm]   SVIDEO-1
Feb  8 07:04:42 lubuntu kernel: [    6.053087] [drm]   Encoders:
Feb  8 07:04:42 lubuntu kernel: [    6.053089] [drm]     TV1: INTERNAL_DAC2
Feb  8 07:04:42 lubuntu kernel: [    6.166907] [drm] fb mappable at 0x80040000
Feb  8 07:04:42 lubuntu kernel: [    6.166909] [drm] vram apper at 0x80000000
Feb  8 07:04:42 lubuntu kernel: [    6.166910] [drm] size 4177920
Feb  8 07:04:42 lubuntu kernel: [    6.166912] [drm] fb depth is 24
Feb  8 07:04:42 lubuntu kernel: [    6.166913] [drm]    pitch is 5440
Feb  8 07:04:42 lubuntu kernel: [    6.167022] fbcon: radeondrmfb (fb0) is primary device
Feb  8 07:04:42 lubuntu kernel: [    6.280757] Console: switching to colour frame buffer device 170x48
Feb  8 07:04:42 lubuntu kernel: [    6.343572] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
Feb  8 07:04:42 lubuntu kernel: [    6.343574] radeon 0000:01:00.0: registered panic notifier
Feb  8 07:04:42 lubuntu kernel: [    6.343596] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:00.0 on minor 0
Feb  8 07:04:42 lubuntu kernel: [    6.469074] usb 1-3: New USB device found, idVendor=10d6, idProduct=1101
Feb  8 07:04:42 lubuntu kernel: [    6.469081] usb 1-3: New USB device strings: Mfr=0, Product=1, SerialNumber=2
Feb  8 07:04:42 lubuntu kernel: [    6.469084] usb 1-3: Product: USB 2.0(HS) Flash Disk 
Feb  8 07:04:42 lubuntu kernel: [    6.469087] usb 1-3: SerialNumber: A00000600001
Feb  8 07:04:42 lubuntu kernel: [    6.474373] usb-storage 1-3:1.0: USB Mass Storage device detected
Feb  8 07:04:42 lubuntu kernel: [    6.480024] scsi0 : usb-storage 1-3:1.0
Feb  8 07:04:42 lubuntu kernel: [    6.480434] usbcore: registered new interface driver usb-storage
Feb  8 07:04:42 lubuntu kernel: [    6.664023] tsc: Refined TSC clocksource calibration: 2000.070 MHz
Feb  8 07:04:42 lubuntu kernel: [    6.848078] usb 1-8: new high-speed USB device number 4 using ehci-pci
Feb  8 07:04:42 lubuntu kernel: [    6.989435] usb 1-8: New USB device found, idVendor=0951, idProduct=1666
Feb  8 07:04:42 lubuntu kernel: [    6.989442] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Feb  8 07:04:42 lubuntu kernel: [    6.989446] usb 1-8: Product: DataTraveler 3.0
Feb  8 07:04:42 lubuntu kernel: [    6.989448] usb 1-8: Manufacturer: Kingston
Feb  8 07:04:42 lubuntu kernel: [    6.989451] usb 1-8: SerialNumber: 08606E67F0A7BDC01703055A
Feb  8 07:04:42 lubuntu kernel: [    6.989988] usb-storage 1-8:1.0: USB Mass Storage device detected
Feb  8 07:04:42 lubuntu kernel: [    6.990113] scsi1 : usb-storage 1-8:1.0
Feb  8 07:04:42 lubuntu kernel: [    7.228023] usb 3-2: new full-speed USB device number 2 using uhci_hcd
Feb  8 07:04:42 lubuntu kernel: [    7.397920] usb 3-2: New USB device found, idVendor=045e, idProduct=0745
Feb  8 07:04:42 lubuntu kernel: [    7.397924] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Feb  8 07:04:42 lubuntu kernel: [    7.397927] usb 3-2: Product: Microsoft® Nano Transceiver v2.0
Feb  8 07:04:42 lubuntu kernel: [    7.397930] usb 3-2: Manufacturer: Microsoft
Feb  8 07:04:42 lubuntu kernel: [    7.413778] hidraw: raw HID events driver (C) Jiri Kosina
Feb  8 07:04:42 lubuntu kernel: [    7.441253] usbcore: registered new interface driver usbhid
Feb  8 07:04:42 lubuntu kernel: [    7.441259] usbhid: USB HID core driver
Feb  8 07:04:42 lubuntu kernel: [    7.447140] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.0/input/input4
Feb  8 07:04:42 lubuntu kernel: [    7.447793] hid-generic 0003:045E:0745.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:10.1-2/input0
Feb  8 07:04:42 lubuntu kernel: [    7.450116] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.1/input/input5
Feb  8 07:04:42 lubuntu kernel: [    7.451279] hid-generic 0003:045E:0745.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:10.1-2/input1
Feb  8 07:04:42 lubuntu kernel: [    7.470927] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.2/input/input6
Feb  8 07:04:42 lubuntu kernel: [    7.472078] hid-generic 0003:045E:0745.0003: input,hiddev0,hidraw2: USB HID v1.11 Device [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:10.1-2/input2
Feb  8 07:04:42 lubuntu kernel: [    7.484817] scsi scan: INQUIRY result too short (5), using 36
Feb  8 07:04:42 lubuntu kernel: [    7.484830] scsi 0:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
Feb  8 07:04:42 lubuntu kernel: [    7.485212] sd 0:0:0:0: Attached scsi generic sg0 type 0
Feb  8 07:04:42 lubuntu kernel: [    7.490926] sd 0:0:0:0: [sda] 4008881 512-byte logical blocks: (2.05 GB/1.91 GiB)
Feb  8 07:04:42 lubuntu kernel: [    7.491413] sd 0:0:0:0: [sda] Write Protect is off
Feb  8 07:04:42 lubuntu kernel: [    7.491418] sd 0:0:0:0: [sda] Mode Sense: 00 c0 00 00
Feb  8 07:04:42 lubuntu kernel: [    7.491915] sd 0:0:0:0: [sda] Write cache: disabled, read cache: disabled, doesn't support DPO or FUA
Feb  8 07:04:42 lubuntu kernel: [    7.497303]  sda: sda1
Feb  8 07:04:42 lubuntu kernel: [    7.500065] sd 0:0:0:0: [sda] Attached SCSI removable disk
Feb  8 07:04:42 lubuntu kernel: [    7.664087] Switched to clocksource tsc
Feb  8 07:04:42 lubuntu kernel: [    7.988671] scsi 1:0:0:0: Direct-Access     Kingston DataTraveler 3.0 PMAP PQ: 0 ANSI: 6
Feb  8 07:04:42 lubuntu kernel: [    7.990155] sd 1:0:0:0: Attached scsi generic sg1 type 0
Feb  8 07:04:42 lubuntu kernel: [    7.990786] sd 1:0:0:0: [sdb] 31293440 512-byte logical blocks: (16.0 GB/14.9 GiB)
Feb  8 07:04:42 lubuntu kernel: [    7.992530] sd 1:0:0:0: [sdb] Write Protect is off
Feb  8 07:04:42 lubuntu kernel: [    7.992538] sd 1:0:0:0: [sdb] Mode Sense: 2b 80 00 08
Feb  8 07:04:42 lubuntu kernel: [    7.994273] sd 1:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Feb  8 07:04:42 lubuntu kernel: [    8.244017]  sdb: sdb1 sdb2 < sdb5 sdb6 >
Feb  8 07:04:42 lubuntu kernel: [    8.254649] sd 1:0:0:0: [sdb] Attached SCSI removable disk
Feb  8 07:04:42 lubuntu kernel: [    8.631373] squashfs: version 4.0 (2009/01/31) Phillip Lougher
Feb  8 07:04:42 lubuntu kernel: [    9.472243] random: nonblocking pool is initialized
Feb  8 07:04:42 lubuntu kernel: [   27.264300] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb  8 07:04:42 lubuntu avahi-daemon[1084]: Found user 'avahi' (UID 107) and group 'avahi' (GID 115).
Feb  8 07:04:42 lubuntu avahi-daemon[1084]: Successfully dropped root privileges.
Feb  8 07:04:42 lubuntu avahi-daemon[1084]: avahi-daemon 0.6.31 starting up.
Feb  8 07:04:42 lubuntu kernel: [   28.918599] Bluetooth: Core ver 2.17
Feb  8 07:04:42 lubuntu avahi-daemon[1084]: WARNING: No NSS support for mDNS detected, consider installing nss-mdns!
Feb  8 07:04:42 lubuntu kernel: [   28.921255] NET: Registered protocol family 31
Feb  8 07:04:42 lubuntu kernel: [   28.921261] Bluetooth: HCI device and connection manager initialized
Feb  8 07:04:42 lubuntu kernel: [   28.921276] Bluetooth: HCI socket layer initialized
Feb  8 07:04:42 lubuntu kernel: [   28.921280] Bluetooth: L2CAP socket layer initialized
Feb  8 07:04:42 lubuntu kernel: [   28.921290] Bluetooth: SCO socket layer initialized
Feb  8 07:04:42 lubuntu bluetoothd[1065]: DIS cannot start: GATT is disabled
Feb  8 07:04:42 lubuntu bluetoothd[1065]: Failed to init deviceinfo plugin
Feb  8 07:04:42 lubuntu bluetoothd[1065]: Failed to init proximity plugin
Feb  8 07:04:42 lubuntu bluetoothd[1065]: Failed to init time plugin
Feb  8 07:04:42 lubuntu bluetoothd[1065]: Failed to init alert plugin
Feb  8 07:04:42 lubuntu bluetoothd[1065]: Failed to init thermometer plugin
Feb  8 07:04:42 lubuntu avahi-daemon[1084]: Successfully called chroot().
Feb  8 07:04:42 lubuntu avahi-daemon[1084]: Successfully dropped remaining capabilities.
Feb  8 07:04:42 lubuntu avahi-daemon[1084]: No service file found in /etc/avahi/services.
Feb  8 07:04:42 lubuntu avahi-daemon[1084]: Network interface enumeration completed.
Feb  8 07:04:42 lubuntu avahi-daemon[1084]: Registering HINFO record with values 'X86_64'/'LINUX'.
Feb  8 07:04:42 lubuntu avahi-daemon[1084]: Server startup complete. Host name is lubuntu.local. Local service cookie is 1222242128.
Feb  8 07:04:42 lubuntu kernel: [   29.003934] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Feb  8 07:04:42 lubuntu kernel: [   29.003942] Bluetooth: BNEP filters: protocol multicast
Feb  8 07:04:42 lubuntu kernel: [   29.003958] Bluetooth: BNEP socket layer initialized
Feb  8 07:04:42 lubuntu bluetoothd[1065]: Failed to init gatt_example plugin
Feb  8 07:04:42 lubuntu bluetoothd[1065]: Bluetooth Management interface initialized
Feb  8 07:04:42 lubuntu kernel: [   29.039473] Bluetooth: RFCOMM TTY layer initialized
Feb  8 07:04:42 lubuntu kernel: [   29.039496] Bluetooth: RFCOMM socket layer initialized
Feb  8 07:04:42 lubuntu kernel: [   29.039512] Bluetooth: RFCOMM ver 1.11
Feb  8 07:04:42 lubuntu kernel: [   29.141524] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Feb  8 07:04:42 lubuntu kernel: [   29.153756] lp: driver loaded but no devices found
Feb  8 07:04:42 lubuntu kernel: [   29.203485] ppdev: user-space parallel port driver
Feb  8 07:04:43 lubuntu kernel: [   29.381165] ACPI Warning: 0x0000000000000400-0x0000000000000407 SystemIO conflicts with Region \SMOV 1 (20131115/utaddress-251)
Feb  8 07:04:43 lubuntu kernel: [   29.381181] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Feb  8 07:04:43 lubuntu kernel: [   29.574458] MCE: In-kernel MCE decoding enabled.
Feb  8 07:04:43 lubuntu kernel: [   29.686681] EDAC MC: Ver: 3.0.0
Feb  8 07:04:43 lubuntu kernel: [   29.795038] AMD64 EDAC driver v3.4.0
Feb  8 07:04:43 lubuntu kernel: [   29.797370] EDAC amd64: DRAM ECC enabled.
Feb  8 07:04:43 lubuntu kernel: [   29.797381] EDAC amd64: K8 revE or earlier detected (node 0).
Feb  8 07:04:43 lubuntu kernel: [   29.797432] EDAC amd64: CS0: Double data rate SDRAM
Feb  8 07:04:43 lubuntu kernel: [   29.797434] EDAC amd64: CS1: Double data rate SDRAM
Feb  8 07:04:43 lubuntu kernel: [   29.797435] EDAC amd64: CS2: Double data rate SDRAM
Feb  8 07:04:43 lubuntu kernel: [   29.797437] EDAC amd64: CS3: Double data rate SDRAM
Feb  8 07:04:43 lubuntu kernel: [   29.797438] EDAC amd64: CS4: Double data rate SDRAM
Feb  8 07:04:43 lubuntu kernel: [   29.797440] EDAC amd64: CS5: Double data rate SDRAM
Feb  8 07:04:43 lubuntu kernel: [   29.801735] EDAC MC0: Giving out device to module amd64_edac controller K8: DEV 0000:00:18.2 (INTERRUPT)
Feb  8 07:04:43 lubuntu kernel: [   29.801810] EDAC PCI0: Giving out device to module amd64_edac controller EDAC PCI controller: DEV 0000:00:18.2 (POLLED)
Feb  8 07:04:43 lubuntu mtp-probe: checking bus 1, device 2: "/sys/devices/pci0000:00/0000:00:10.4/usb1/1-3"
Feb  8 07:04:43 lubuntu mtp-probe: checking bus 1, device 4: "/sys/devices/pci0000:00/0000:00:10.4/usb1/1-8"
Feb  8 07:04:43 lubuntu mtp-probe: bus: 1, device: 2 was not an MTP device
Feb  8 07:04:43 lubuntu mtp-probe: bus: 1, device: 4 was not an MTP device
Feb  8 07:04:43 lubuntu mtp-probe: checking bus 3, device 2: "/sys/devices/pci0000:00/0000:00:10.1/usb3/3-2"
Feb  8 07:04:43 lubuntu mtp-probe: bus: 3, device: 2 was not an MTP device
Feb  8 07:04:43 lubuntu kernel: [   29.925233] microcode: AMD CPU family 0xf not supported
Feb  8 07:04:43 lubuntu kernel: [   30.234257] device-mapper: multipath: version 1.6.0 loaded
Feb  8 07:04:44 lubuntu failsafe: Failsafe of 120 seconds reached.
Feb  8 07:04:45 lubuntu modem-manager[1281]: <info>  ModemManager (version 0.6.0.0) starting...
Feb  8 07:04:45 lubuntu modem-manager[1281]: <info>  Loaded plugin 'AnyData'
Feb  8 07:04:45 lubuntu modem-manager[1281]: <info>  Loaded plugin 'Gobi'
Feb  8 07:04:45 lubuntu modem-manager[1281]: <info>  Loaded plugin 'Option High-Speed'
Feb  8 07:04:45 lubuntu modem-manager[1281]: <info>  Loaded plugin 'Huawei'
Feb  8 07:04:45 lubuntu modem-manager[1281]: <info>  Loaded plugin 'Linktop'
Feb  8 07:04:45 lubuntu modem-manager[1281]: <info>  Loaded plugin 'Longcheer'
Feb  8 07:04:45 lubuntu modem-manager[1281]: <info>  Loaded plugin 'Ericsson MBM'
Feb  8 07:04:45 lubuntu modem-manager[1281]: <info>  Loaded plugin 'MotoC'
Feb  8 07:04:45 lubuntu modem-manager[1281]: <info>  Loaded plugin 'Nokia'
Feb  8 07:04:45 lubuntu modem-manager[1281]: <info>  Loaded plugin 'Novatel'
Feb  8 07:04:45 lubuntu modem-manager[1281]: <info>  Loaded plugin 'Option'
Feb  8 07:04:45 lubuntu modem-manager[1281]: <info>  Loaded plugin 'Samsung'
Feb  8 07:04:45 lubuntu modem-manager[1281]: <info>  Loaded plugin 'Sierra'
Feb  8 07:04:45 lubuntu modem-manager[1281]: <info>  Loaded plugin 'SimTech'
Feb  8 07:04:45 lubuntu modem-manager[1281]: <info>  Loaded plugin 'Wavecom'
Feb  8 07:04:45 lubuntu modem-manager[1281]: <info>  Loaded plugin 'X22X'
Feb  8 07:04:45 lubuntu modem-manager[1281]: <info>  Loaded plugin 'ZTE'
Feb  8 07:04:45 lubuntu modem-manager[1281]: <info>  Loaded plugin 'Cinterion'
Feb  8 07:04:45 lubuntu modem-manager[1281]: <info>  Loaded plugin 'Iridium'
Feb  8 07:04:45 lubuntu modem-manager[1281]: <info>  Loaded plugin 'Generic'
Feb  8 07:04:45 lubuntu modem-manager[1281]: <info>  Successfully loaded 20 plugins
Feb  8 07:04:45 lubuntu NetworkManager[1365]: <info> NetworkManager (version 0.9.8.4) is starting...
Feb  8 07:04:45 lubuntu NetworkManager[1365]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Feb  8 07:04:45 lubuntu NetworkManager[1365]: <info> WEXT support is enabled
Feb  8 07:04:46 lubuntu NetworkManager[1365]: <info> DNS: loaded plugin dnsmasq
Feb  8 07:04:46 lubuntu dbus[1026]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Feb  8 07:04:46 lubuntu polkitd[1389]: started daemon version 0.105 using authority implementation `local' version `0.105'
Feb  8 07:04:46 lubuntu dbus[1026]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Feb  8 07:04:46 lubuntu NetworkManager[1365]:    SCPlugin-Ifupdown: init!
Feb  8 07:04:46 lubuntu NetworkManager[1365]:    SCPlugin-Ifupdown: update_system_hostname
Feb  8 07:04:46 lubuntu NetworkManager[1365]:    SCPluginIfupdown: management mode: unmanaged
Feb  8 07:04:46 lubuntu NetworkManager[1365]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0b.0/net/eth0, iface: eth0)
Feb  8 07:04:46 lubuntu NetworkManager[1365]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0b.0/net/eth0, iface: eth0): no ifupdown configuration found.
Feb  8 07:04:46 lubuntu NetworkManager[1365]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Feb  8 07:04:46 lubuntu NetworkManager[1365]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Feb  8 07:04:46 lubuntu NetworkManager[1365]:    SCPlugin-Ifupdown: end _init.
Feb  8 07:04:46 lubuntu NetworkManager[1365]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Feb  8 07:04:46 lubuntu NetworkManager[1365]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Feb  8 07:04:46 lubuntu NetworkManager[1365]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Feb  8 07:04:46 lubuntu NetworkManager[1365]:    SCPlugin-Ofono: init!
Feb  8 07:04:46 lubuntu NetworkManager[1365]:    SCPlugin-Ofono: end _init.
Feb  8 07:04:46 lubuntu NetworkManager[1365]: <info> Loaded plugin (null): (null)
Feb  8 07:04:46 lubuntu NetworkManager[1365]:    Ifupdown: get unmanaged devices count: 0
Feb  8 07:04:46 lubuntu NetworkManager[1365]:    SCPlugin-Ifupdown: (19205904) ... get_connections.
Feb  8 07:04:46 lubuntu NetworkManager[1365]:    SCPlugin-Ifupdown: (19205904) ... get_connections (managed=false): return empty list.
Feb  8 07:04:46 lubuntu NetworkManager[1365]:    SCPlugin-Ofono: (19014240) ... get_connections.
Feb  8 07:04:46 lubuntu NetworkManager[1365]:    SCPlugin-Ofono: (19014240) connections count: 0
Feb  8 07:04:46 lubuntu NetworkManager[1365]:    Ifupdown: get unmanaged devices count: 0
Feb  8 07:04:46 lubuntu NetworkManager[1365]: <info> modem-manager is now available
Feb  8 07:04:46 lubuntu NetworkManager[1365]: <info> monitoring kernel firmware directory '/lib/firmware'.
Feb  8 07:04:46 lubuntu ntpd[1460]: ntpd 4.2.6p5@1.2349-o Wed Oct  9 19:08:06 UTC 2013 (1)
Feb  8 07:04:46 lubuntu NetworkManager[1365]: <info> WiFi hardware radio set enabled
Feb  8 07:04:46 lubuntu NetworkManager[1365]: <info> WiFi enabled by radio killswitch; enabled by state file
Feb  8 07:04:46 lubuntu NetworkManager[1365]: <info> WWAN enabled by radio killswitch; enabled by state file
Feb  8 07:04:46 lubuntu NetworkManager[1365]: <info> WiMAX enabled by radio killswitch; enabled by state file
Feb  8 07:04:46 lubuntu NetworkManager[1365]: <info> Networking is enabled by state file
Feb  8 07:04:46 lubuntu NetworkManager[1365]: <warn> failed to allocate link cache: (-12) Object not found
Feb  8 07:04:46 lubuntu NetworkManager[1365]: <info> (eth0): carrier is OFF
Feb  8 07:04:46 lubuntu ntpd[1496]: proto: precision = 0.264 usec
Feb  8 07:04:46 lubuntu NetworkManager[1365]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Feb  8 07:04:46 lubuntu NetworkManager[1365]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Feb  8 07:04:46 lubuntu NetworkManager[1365]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb  8 07:04:46 lubuntu NetworkManager[1365]: <info> (eth0): bringing up device.
Feb  8 07:04:46 lubuntu ntpd[1496]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Feb  8 07:04:46 lubuntu ntpd[1496]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Feb  8 07:04:47 lubuntu ntpd[1496]: Listen and drop on 1 v6wildcard :: UDP 123
Feb  8 07:04:47 lubuntu NetworkManager[1365]: <info> (eth0): preparing device.
Feb  8 07:04:47 lubuntu ntpd[1496]: Listen normally on 2 lo 127.0.0.1 UDP 123
Feb  8 07:04:47 lubuntu kernel: [   33.256736] r8169 0000:00:0b.0 eth0: link down
Feb  8 07:04:47 lubuntu kernel: [   33.256756] r8169 0000:00:0b.0 eth0: link down
Feb  8 07:04:47 lubuntu kernel: [   33.257571] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb  8 07:04:47 lubuntu ntpd[1496]: Listen normally on 3 lo ::1 UDP 123
Feb  8 07:04:47 lubuntu NetworkManager[1365]: <info> (eth0): deactivating device (reason 'managed') [2]
Feb  8 07:04:47 lubuntu kernel: [   33.265778] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb  8 07:04:47 lubuntu ntpd[1496]: peers refreshed
Feb  8 07:04:47 lubuntu ntpd[1496]: Listening on routing socket on fd #20 for interface updates
Feb  8 07:04:47 lubuntu NetworkManager[1365]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:0b.0/net/eth0
Feb  8 07:04:47 lubuntu NetworkManager[1365]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Feb  8 07:04:47 lubuntu ntpd[1496]: Deferring DNS for 0.ubuntu.pool.ntp.org 1
Feb  8 07:04:47 lubuntu ntpd[1496]: Deferring DNS for 1.ubuntu.pool.ntp.org 1
Feb  8 07:04:47 lubuntu ntpd[1496]: Deferring DNS for 2.ubuntu.pool.ntp.org 1
Feb  8 07:04:47 lubuntu ntpd[1496]: Deferring DNS for 3.ubuntu.pool.ntp.org 1
Feb  8 07:04:47 lubuntu ntpd[1496]: Deferring DNS for ntp.ubuntu.com 1
Feb  8 07:04:47 lubuntu ntpd[1528]: signal_no_reset: signal 17 had flags 4000000
Feb  8 07:04:47 lubuntu kernel: [   33.726386] zram: module is from the staging directory, the quality is unknown, you have been warned.
Feb  8 07:04:47 lubuntu kernel: [   33.740185] zram: Created 1 device(s) ...
Feb  8 07:04:47 lubuntu cron[1405]: (CRON) INFO (pidfile fd = 3)
Feb  8 07:04:47 lubuntu cron[1642]: (CRON) STARTUP (fork ok)
Feb  8 07:04:47 lubuntu cron[1642]: (CRON) INFO (Running @reboot jobs)
Feb  8 07:04:47 lubuntu kernel: [   34.063771] Adding 1025028k swap on /dev/zram0.  Priority:5 extents:1 across:1025028k SSFS
Feb  8 07:04:48 lubuntu kernel: [   34.818887] r8169 0000:00:0b.0 eth0: link up
Feb  8 07:04:48 lubuntu kernel: [   34.818905] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Feb  8 07:04:47 lubuntu NetworkManager[1365]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Feb  8 07:04:48 lubuntu NetworkManager[1365]: <info> (eth0): carrier now ON (device state 20)
Feb  8 07:04:48 lubuntu NetworkManager[1365]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Feb  8 07:04:48 lubuntu NetworkManager[1365]: <info> Auto-activating connection 'Wired connection 1'.
Feb  8 07:04:48 lubuntu NetworkManager[1365]: <info> Activation (eth0) starting connection 'Wired connection 1'
Feb  8 07:04:48 lubuntu NetworkManager[1365]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb  8 07:04:48 lubuntu NetworkManager[1365]: <info> NetworkManager state is now CONNECTING
Feb  8 07:04:48 lubuntu NetworkManager[1365]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Feb  8 07:04:48 lubuntu NetworkManager[1365]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Feb  8 07:04:48 lubuntu NetworkManager[1365]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Feb  8 07:04:48 lubuntu NetworkManager[1365]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Feb  8 07:04:48 lubuntu NetworkManager[1365]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Feb  8 07:04:48 lubuntu NetworkManager[1365]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Feb  8 07:04:48 lubuntu NetworkManager[1365]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Feb  8 07:04:48 lubuntu NetworkManager[1365]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Feb  8 07:04:48 lubuntu NetworkManager[1365]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Feb  8 07:04:48 lubuntu NetworkManager[1365]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Feb  8 07:04:48 lubuntu NetworkManager[1365]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Feb  8 07:04:48 lubuntu NetworkManager[1365]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Feb  8 07:04:48 lubuntu NetworkManager[1365]: <info> dhclient started with pid 1809
Feb  8 07:04:48 lubuntu NetworkManager[1365]: <info> Activation (eth0) Beginning IP6 addrconf.
Feb  8 07:04:48 lubuntu NetworkManager[1365]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Feb  8 07:04:48 lubuntu /usr/sbin/irqbalance: Balancing is ineffective on systems with a single cache domain.  Shutting down
Feb  8 07:04:48 lubuntu dbus[1026]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Feb  8 07:04:49 lubuntu dhclient: Internet Systems Consortium DHCP Client 4.2.4
Feb  8 07:04:49 lubuntu ntpd_intres[1528]: host name not found: 0.ubuntu.pool.ntp.org
Feb  8 07:04:49 lubuntu ntpd_intres[1528]: host name not found: 1.ubuntu.pool.ntp.org
Feb  8 07:04:49 lubuntu ntpd_intres[1528]: host name not found: 2.ubuntu.pool.ntp.org
Feb  8 07:04:49 lubuntu ntpd_intres[1528]: host name not found: 3.ubuntu.pool.ntp.org
Feb  8 07:04:49 lubuntu ntpd_intres[1528]: host name not found: ntp.ubuntu.com
Feb  8 07:04:49 lubuntu dhclient: Copyright 2004-2012 Internet Systems Consortium.
Feb  8 07:04:49 lubuntu dhclient: All rights reserved.
Feb  8 07:04:49 lubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Feb  8 07:04:49 lubuntu dhclient: 
Feb  8 07:04:49 lubuntu dhclient: Listening on LPF/eth0/00:11:09:8e:39:b3
Feb  8 07:04:49 lubuntu dhclient: Sending on   LPF/eth0/00:11:09:8e:39:b3
Feb  8 07:04:49 lubuntu dhclient: Sending on   Socket/fallback
Feb  8 07:04:49 lubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x5696d477)
Feb  8 07:04:49 lubuntu NetworkManager[1365]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Feb  8 07:04:49 lubuntu accounts-daemon[1891]: started daemon version 0.6.35
Feb  8 07:04:49 lubuntu dbus[1026]: [system] Successfully activated service 'org.freedesktop.Accounts'
Feb  8 07:04:49 lubuntu avahi-daemon[1084]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::211:9ff:fe8e:39b3.
Feb  8 07:04:49 lubuntu avahi-daemon[1084]: New relevant interface eth0.IPv6 for mDNS.
Feb  8 07:04:49 lubuntu avahi-daemon[1084]: Registering new address record for fe80::211:9ff:fe8e:39b3 on eth0.*.
Feb  8 07:04:51 lubuntu ntpd[1496]: ntpd exiting on signal 15
Feb  8 07:04:51 lubuntu ntpdate[2256]: Can't find host 0.ubuntu.pool.ntp.org: Name or service not known (-2)
Feb  8 07:04:51 lubuntu ntpdate[2256]: Can't find host 1.ubuntu.pool.ntp.org: Name or service not known (-2)
Feb  8 07:04:51 lubuntu ntpdate[2256]: Can't find host 2.ubuntu.pool.ntp.org: Name or service not known (-2)
Feb  8 07:04:51 lubuntu ntpdate[2256]: Can't find host 3.ubuntu.pool.ntp.org: Name or service not known (-2)
Feb  8 07:04:51 lubuntu ntpdate[2256]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Feb  8 07:04:51 lubuntu ntpdate[2256]: no servers can be used, exiting
Feb  8 07:04:51 lubuntu ntpd[2337]: ntpd 4.2.6p5@1.2349-o Wed Oct  9 19:08:06 UTC 2013 (1)
Feb  8 07:04:51 lubuntu ntpd[2341]: proto: precision = 0.276 usec
Feb  8 07:04:51 lubuntu ntpd[2341]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Feb  8 07:04:51 lubuntu ntpd[2341]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Feb  8 07:04:51 lubuntu ntpd[2341]: Listen and drop on 1 v6wildcard :: UDP 123
Feb  8 07:04:51 lubuntu ntpd[2341]: Listen normally on 2 lo 127.0.0.1 UDP 123
Feb  8 07:04:51 lubuntu ntpd[2341]: Listen normally on 3 lo ::1 UDP 123
Feb  8 07:04:51 lubuntu ntpd[2341]: Listen normally on 4 eth0 fe80::211:9ff:fe8e:39b3 UDP 123
Feb  8 07:04:51 lubuntu ntpd[2341]: peers refreshed
Feb  8 07:04:51 lubuntu ntpd[2341]: Listening on routing socket on fd #21 for interface updates
Feb  8 07:04:51 lubuntu ntpd[2341]: Deferring DNS for 0.ubuntu.pool.ntp.org 1
Feb  8 07:04:51 lubuntu ntpd[2341]: Deferring DNS for 1.ubuntu.pool.ntp.org 1
Feb  8 07:04:51 lubuntu ntpd[2341]: Deferring DNS for 2.ubuntu.pool.ntp.org 1
Feb  8 07:04:51 lubuntu ntpd[2341]: Deferring DNS for 3.ubuntu.pool.ntp.org 1
Feb  8 07:04:51 lubuntu ntpd[2341]: Deferring DNS for ntp.ubuntu.com 1
Feb  8 07:04:51 lubuntu ntpd[2349]: signal_no_reset: signal 17 had flags 4000000
Feb  8 07:04:51 lubuntu dhclient: DHCPREQUEST of 172.16.1.105 on eth0 to 255.255.255.255 port 67 (xid=0x5696d477)
Feb  8 07:04:51 lubuntu dhclient: DHCPOFFER of 172.16.1.105 from 172.16.1.1
Feb  8 07:04:51 lubuntu dhclient: DHCPACK of 172.16.1.105 from 172.16.1.1
Feb  8 07:04:51 lubuntu NetworkManager[1365]: <info> (eth0): DHCPv4 state changed preinit -> bound
Feb  8 07:04:51 lubuntu NetworkManager[1365]: <info>   address 172.16.1.105
Feb  8 07:04:51 lubuntu NetworkManager[1365]: <info>   prefix 24 (255.255.255.0)
Feb  8 07:04:51 lubuntu NetworkManager[1365]: <info>   gateway 172.16.1.1
Feb  8 07:04:51 lubuntu NetworkManager[1365]: <info>   hostname 'lubuntu'
Feb  8 07:04:51 lubuntu NetworkManager[1365]: <info>   nameserver '172.16.1.1'
Feb  8 07:04:51 lubuntu NetworkManager[1365]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Feb  8 07:04:51 lubuntu NetworkManager[1365]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Feb  8 07:04:51 lubuntu avahi-daemon[1084]: Joining mDNS multicast group on interface eth0.IPv4 with address 172.16.1.105.
Feb  8 07:04:51 lubuntu avahi-daemon[1084]: New relevant interface eth0.IPv4 for mDNS.
Feb  8 07:04:51 lubuntu avahi-daemon[1084]: Registering new address record for 172.16.1.105 on eth0.IPv4.
Feb  8 07:04:51 lubuntu dhclient: bound to 172.16.1.105 -- renewal in 1541 seconds.
Feb  8 07:04:52 lubuntu NetworkManager[1365]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Feb  8 07:04:52 lubuntu NetworkManager[1365]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Feb  8 07:04:52 lubuntu NetworkManager[1365]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Feb  8 07:04:52 lubuntu NetworkManager[1365]: <info> NetworkManager state is now CONNECTED_GLOBAL
Feb  8 07:04:52 lubuntu NetworkManager[1365]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Feb  8 07:04:52 lubuntu NetworkManager[1365]: <info> DNS: starting dnsmasq...
Feb  8 07:04:52 lubuntu NetworkManager[1365]: <warn> dnsmasq not available on the bus, can't update servers.
Feb  8 07:04:52 lubuntu NetworkManager[1365]: <error> [1391843092.576882] [nm-dns-dnsmasq.c:400] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Feb  8 07:04:52 lubuntu NetworkManager[1365]: <warn> DNS: plugin dnsmasq update failed
Feb  8 07:04:52 lubuntu NetworkManager[1365]: <info> Writing DNS information to /sbin/resolvconf
Feb  8 07:04:52 lubuntu dnsmasq[2402]: started, version 2.68 cache disabled
Feb  8 07:04:52 lubuntu dnsmasq[2402]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Feb  8 07:04:52 lubuntu dnsmasq[2402]: DBus support enabled: connected to system bus
Feb  8 07:04:52 lubuntu dnsmasq[2402]: warning: no upstream servers configured
Feb  8 07:04:53 lubuntu ntpd_intres[2349]: DNS 0.ubuntu.pool.ntp.org -> 217.153.128.243
Feb  8 07:04:53 lubuntu NetworkManager[1365]: <info> Activation (eth0) successful, device activated.
Feb  8 07:04:53 lubuntu dbus[1026]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Feb  8 07:04:53 lubuntu NetworkManager[1365]: <warn> dnsmasq appeared on DBus: :1.20
Feb  8 07:04:53 lubuntu NetworkManager[1365]: <info> Writing DNS information to /sbin/resolvconf
Feb  8 07:04:53 lubuntu dnsmasq[2402]: setting upstream servers from DBus
Feb  8 07:04:53 lubuntu dnsmasq[2402]: using nameserver 172.16.1.1#53
Feb  8 07:04:53 lubuntu ntpd_intres[2349]: DNS 1.ubuntu.pool.ntp.org -> 46.250.172.2
Feb  8 07:04:53 lubuntu ntpd_intres[2349]: DNS 2.ubuntu.pool.ntp.org -> 193.106.216.30
Feb  8 07:04:53 lubuntu dbus[1026]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb  8 07:04:53 lubuntu ntpd_intres[2349]: DNS 3.ubuntu.pool.ntp.org -> 217.153.128.244
Feb  8 07:04:53 lubuntu ntpd_intres[2349]: DNS ntp.ubuntu.com -> 91.189.89.199
Feb  8 07:04:53 lubuntu ntpd[2341]: ntpd exiting on signal 15
Feb  8 07:04:59 lubuntu dbus[1026]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Feb  8 07:04:59 lubuntu udisksd[2714]: udisks daemon version 2.1.1 starting
Feb  8 07:04:59 lubuntu dbus[1026]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Feb  8 07:04:59 lubuntu udisksd[2714]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Feb  8 07:05:02 lubuntu ntpdate[2545]: step time server 217.153.128.243 offset -0.612688 sec
Feb  8 07:05:02 lubuntu ntpd[2789]: ntpd 4.2.6p5@1.2349-o Wed Oct  9 19:08:06 UTC 2013 (1)
Feb  8 07:05:02 lubuntu ntpd[2790]: proto: precision = 0.278 usec
Feb  8 07:05:02 lubuntu ntpd[2790]: ntp_io: estimated max descriptors: 2144, initial socket boundary: 16
Feb  8 07:05:02 lubuntu ntpd[2790]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Feb  8 07:05:03 lubuntu ntpd[2790]: Listen and drop on 1 v6wildcard :: UDP 123
Feb  8 07:05:03 lubuntu ntpd[2790]: Listen normally on 2 lo 127.0.0.1 UDP 123
Feb  8 07:05:03 lubuntu ntpd[2790]: Listen normally on 3 eth0 172.16.1.105 UDP 123
Feb  8 07:05:03 lubuntu ntpd[2790]: Listen normally on 4 lo ::1 UDP 123
Feb  8 07:05:03 lubuntu ntpd[2790]: Listen normally on 5 eth0 fe80::211:9ff:fe8e:39b3 UDP 123
Feb  8 07:05:03 lubuntu ntpd[2790]: peers refreshed
Feb  8 07:05:03 lubuntu ntpd[2790]: Listening on routing socket on fd #22 for interface updates
Feb  8 07:05:06 lubuntu kernel: [   53.680510] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)
Feb  8 07:05:06 lubuntu udisksd[2714]: Mounted /dev/sdb5 at /media/lubuntu/edfa1d4b-0fcd-40d4-8619-ffa08cc9eb45 on behalf of uid 999
Feb  8 07:05:07 lubuntu udisksd[2714]: Mounted /dev/sdb1 at /media/lubuntu/Windows USB on behalf of uid 999
Feb  8 07:05:07 lubuntu ntfs-3g[2812]: Version 2013.1.13AR.1 external FUSE 29
Feb  8 07:05:07 lubuntu ntfs-3g[2812]: Mounted /dev/sdb1 (Read-Write, label "Windows USB", NTFS 3.1)
Feb  8 07:05:07 lubuntu ntfs-3g[2812]: Cmdline options: rw,nosuid,nodev,uhelper=udisks2,uid=999,gid=999,dmask=0077,fmask=0177
Feb  8 07:05:07 lubuntu ntfs-3g[2812]: Mount options: rw,nosuid,nodev,uhelper=udisks2,allow_other,nonempty,relatime,default_permissions,fsname=/dev/sdb1,blkdev,blksize=4096
Feb  8 07:05:07 lubuntu ntfs-3g[2812]: Global ownership and permissions enforced, configuration type 7
Feb  8 07:05:08 lubuntu NetworkManager[1365]: <info> (eth0): IP6 addrconf timed out or failed.
Feb  8 07:05:08 lubuntu NetworkManager[1365]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Feb  8 07:05:08 lubuntu NetworkManager[1365]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Feb  8 07:05:08 lubuntu NetworkManager[1365]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Feb  8 07:05:18 lubuntu ntpd_intres[1528]: parent died before we finished, exiting
Feb  8 07:05:59 lubuntu udisksd[2714]: Cleaning up mount point /media/lubuntu/edfa1d4b-0fcd-40d4-8619-ffa08cc9eb45 (device 8:21 is not mounted)
Feb  8 07:06:02 lubuntu udisksd[2714]: Cleaning up mount point /media/lubuntu/Windows USB (device 8:17 is not mounted)
Feb  8 07:06:02 lubuntu ntfs-3g[2812]: Unmounting /dev/sdb1 (Windows USB)
Feb  8 07:06:41 lubuntu kernel: [  148.612050] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)
Feb  8 07:06:41 lubuntu udisksd[2714]: Mounted /dev/sdb5 at /media/lubuntu/edfa1d4b-0fcd-40d4-8619-ffa08cc9eb45 on behalf of uid 999
Feb  8 07:14:02 lubuntu dbus[1026]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Feb  8 07:14:02 lubuntu dbus[1026]: [system] Successfully activated service 'org.freedesktop.UPower'
Feb  8 07:17:01 lubuntu CRON[3308]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb  8 07:18:06 lubuntu udisksd[2714]: Cleaning up mount point /media/lubuntu/edfa1d4b-0fcd-40d4-8619-ffa08cc9eb45 (device 8:21 is not mounted)
Feb  8 07:18:07 lubuntu udisksd[2714]: Unmounted /dev/sdb5 on behalf of uid 999
Feb  8 07:30:02 lubuntu CRON[3403]: (root) CMD (start -q anacron || :)
Feb  8 07:30:32 lubuntu dhclient: DHCPREQUEST of 172.16.1.105 on eth0 to 172.16.1.1 port 67 (xid=0x5696d477)
Feb  8 07:30:32 lubuntu dhclient: DHCPACK of 172.16.1.105 from 172.16.1.1
Feb  8 07:30:32 lubuntu dhclient: bound to 172.16.1.105 -- renewal in 1621 seconds.
Feb  8 07:30:32 lubuntu NetworkManager[1365]: <info> (eth0): DHCPv4 state changed bound -> renew
Feb  8 07:30:32 lubuntu NetworkManager[1365]: <info>   address 172.16.1.105
Feb  8 07:30:32 lubuntu NetworkManager[1365]: <info>   prefix 24 (255.255.255.0)
Feb  8 07:30:32 lubuntu NetworkManager[1365]: <info>   gateway 172.16.1.1
Feb  8 07:30:32 lubuntu NetworkManager[1365]: <info>   hostname 'lubuntu'
Feb  8 07:30:32 lubuntu NetworkManager[1365]: <info>   nameserver '172.16.1.1'
Feb  8 07:30:32 lubuntu dbus[1026]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Feb  8 07:30:33 lubuntu dbus[1026]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb  8 07:39:37 lubuntu dbus[1026]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Feb  8 07:39:38 lubuntu dbus[1026]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Feb  8 07:39:38 lubuntu dbus[1026]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Feb  8 07:39:38 lubuntu dbus[1026]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Feb  8 07:42:44 lubuntu udisksd[2714]: Mounted /dev/sdb5 at /media/lubuntu/edfa1d4b-0fcd-40d4-8619-ffa08cc9eb45 on behalf of uid 999
Feb  8 07:42:44 lubuntu kernel: [ 2311.455163] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)
Feb  8 07:42:52 lubuntu udisksd[2714]: Cleaning up mount point /media/lubuntu/edfa1d4b-0fcd-40d4-8619-ffa08cc9eb45 (device 8:21 is not mounted)
Feb  8 07:42:52 lubuntu udisksd[2714]: Unmounted /dev/sdb5 on behalf of uid 999
Feb  8 07:47:33 lubuntu dbus[1026]: [system] Activating service name='com.ubuntu.SoftwareProperties' (using servicehelper)
Feb  8 07:47:34 lubuntu dbus[1026]: [system] Successfully activated service 'com.ubuntu.SoftwareProperties'
Feb  8 07:49:14 lubuntu dbus[1026]: [system] Activating service name='org.debian.apt' (using servicehelper)
Feb  8 07:49:15 lubuntu AptDaemon: INFO: Initializing daemon
Feb  8 07:49:15 lubuntu dbus[1026]: [system] Successfully activated service 'org.debian.apt'
Feb  8 07:49:15 lubuntu AptDaemon: INFO: UpdateCache() was called
Feb  8 07:49:15 lubuntu AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/6c5c4323dd1a42e09336db92e8089463
Feb  8 07:49:15 lubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/6c5c4323dd1a42e09336db92e8089463
Feb  8 07:49:15 lubuntu AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/6c5c4323dd1a42e09336db92e8089463
Feb  8 07:49:16 lubuntu AptDaemon.Worker: INFO: Updating cache
Feb  8 07:49:41 lubuntu dbus[1026]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Feb  8 07:49:41 lubuntu dbus[1026]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Feb  8 07:49:45 lubuntu AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/6c5c4323dd1a42e09336db92e8089463
Feb  8 07:51:14 lubuntu AptDaemon: INFO: UpdateCache() was called
Feb  8 07:51:14 lubuntu AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/e1bd8dfc00734e92ab97c9140cde1890
Feb  8 07:51:14 lubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/e1bd8dfc00734e92ab97c9140cde1890
Feb  8 07:51:14 lubuntu AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/e1bd8dfc00734e92ab97c9140cde1890
Feb  8 07:51:15 lubuntu AptDaemon.Worker: INFO: Updating cache
Feb  8 07:51:17 lubuntu AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/e1bd8dfc00734e92ab97c9140cde1890
Feb  8 07:57:16 lubuntu AptDaemon: INFO: Quitting due to inactivity
Feb  8 07:57:16 lubuntu AptDaemon: INFO: Quitting was requested
Feb  8 07:57:34 lubuntu dhclient: DHCPREQUEST of 172.16.1.105 on eth0 to 172.16.1.1 port 67 (xid=0x5696d477)
Feb  8 07:57:34 lubuntu dhclient: DHCPACK of 172.16.1.105 from 172.16.1.1
Feb  8 07:57:34 lubuntu NetworkManager[1365]: <info> (eth0): DHCPv4 state changed renew -> renew
Feb  8 07:57:34 lubuntu NetworkManager[1365]: <info>   address 172.16.1.105
Feb  8 07:57:34 lubuntu NetworkManager[1365]: <info>   prefix 24 (255.255.255.0)
Feb  8 07:57:34 lubuntu NetworkManager[1365]: <info>   gateway 172.16.1.1
Feb  8 07:57:34 lubuntu NetworkManager[1365]: <info>   hostname 'lubuntu'
Feb  8 07:57:34 lubuntu NetworkManager[1365]: <info>   nameserver '172.16.1.1'
Feb  8 07:57:34 lubuntu dbus[1026]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Feb  8 07:57:34 lubuntu dhclient: bound to 172.16.1.105 -- renewal in 1682 seconds.
Feb  8 07:57:34 lubuntu dbus[1026]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb  8 08:17:01 lubuntu CRON[4649]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb  8 08:25:36 lubuntu dhclient: DHCPREQUEST of 172.16.1.105 on eth0 to 172.16.1.1 port 67 (xid=0x5696d477)
Feb  8 08:25:36 lubuntu dhclient: DHCPACK of 172.16.1.105 from 172.16.1.1
Feb  8 08:25:36 lubuntu dhclient: bound to 172.16.1.105 -- renewal in 1520 seconds.
Feb  8 08:25:36 lubuntu NetworkManager[1365]: <info> (eth0): DHCPv4 state changed renew -> renew
Feb  8 08:25:36 lubuntu NetworkManager[1365]: <info>   address 172.16.1.105
Feb  8 08:25:36 lubuntu NetworkManager[1365]: <info>   prefix 24 (255.255.255.0)
Feb  8 08:25:36 lubuntu NetworkManager[1365]: <info>   gateway 172.16.1.1
Feb  8 08:25:36 lubuntu NetworkManager[1365]: <info>   hostname 'lubuntu'
Feb  8 08:25:36 lubuntu NetworkManager[1365]: <info>   nameserver '172.16.1.1'
Feb  8 08:25:36 lubuntu dbus[1026]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Feb  8 08:25:36 lubuntu dbus[1026]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb  8 08:28:52 lubuntu ubiquity[4668]: Ubiquity 2.17.3
Feb  8 08:28:54 lubuntu ubiquity[4668]: log-output -t ubiquity laptop-detect
Feb  8 08:28:59 lubuntu ubiquity[4668]: switched to page language
Feb  8 08:29:13 lubuntu localechooser: info: Language = 'en'
Feb  8 08:29:13 lubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
Feb  8 08:29:13 lubuntu localechooser: info: Set debian-installer/language = 'en'
Feb  8 08:29:13 lubuntu localechooser: info: Default country = 'US'
Feb  8 08:29:13 lubuntu localechooser: info: Default locale = 'en_US.UTF-8'
Feb  8 08:29:13 lubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Feb  8 08:29:13 lubuntu localechooser: info: Set debian-installer/country = 'US'
Feb  8 08:29:13 lubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Feb  8 08:29:13 lubuntu localechooser: info: System locale (debian-installer/locale) = 'en_US.UTF-8'
Feb  8 08:29:01 lubuntu ubiquity[4668]: switched to page language
Feb  8 08:29:15 lubuntu ubiquity[4668]: debconffilter_done: ubi-language (current: ubi-language)
Feb  8 08:29:15 lubuntu ubiquity[4668]: Step_before = stepLanguage
Feb  8 08:29:15 lubuntu ubiquity[4668]: Step_before = stepLanguage
Feb  8 08:29:16 lubuntu ubiquity[4668]: switched to page prepare
Feb  8 08:31:37 lubuntu ubiquity[4668]: debconffilter_done: ubi-prepare (current: ubi-prepare)
Feb  8 08:31:37 lubuntu ubiquity[4668]: Step_before = stepPrepare
Feb  8 08:31:37 lubuntu activate-dmraid: No Serial ATA RAID disks detected
Feb  8 08:31:37 lubuntu kernel: [ 5244.486683] xor: measuring software checksum speed
Feb  8 08:31:37 lubuntu kernel: [ 5244.524005]    prefetch64-sse:  6145.000 MB/sec
Feb  8 08:31:37 lubuntu kernel: [ 5244.564003]    generic_sse:  6257.000 MB/sec
Feb  8 08:31:37 lubuntu kernel: [ 5244.564006] xor: using function: generic_sse (6257.000 MB/sec)
Feb  8 08:31:37 lubuntu kernel: [ 5244.688012] raid6: sse2x1     477 MB/s
Feb  8 08:31:37 lubuntu kernel: [ 5244.756061] raid6: sse2x2     883 MB/s
Feb  8 08:31:37 lubuntu kernel: [ 5244.824033] raid6: sse2x4    1467 MB/s
Feb  8 08:31:37 lubuntu kernel: [ 5244.824036] raid6: using algorithm sse2x4 (1467 MB/s)
Feb  8 08:31:37 lubuntu kernel: [ 5244.824038] raid6: using intx1 recovery algorithm
Feb  8 08:31:38 lubuntu kernel: [ 5244.983319] bio: create slab <bio-1> at 1
Feb  8 08:31:38 lubuntu kernel: [ 5244.993155] Btrfs loaded
Feb  8 08:31:38 lubuntu kernel: [ 5245.094789] JFS: nTxBlock = 8192, nTxLock = 65536
Feb  8 08:31:38 lubuntu kernel: [ 5245.258911] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Feb  8 08:31:38 lubuntu partman:   No matching physical volumes found
Feb  8 08:31:38 lubuntu partman:   Reading all physical volumes.  This may take a while...
Feb  8 08:31:38 lubuntu partman:   
Feb  8 08:31:38 lubuntu partman: No volume groups found
Feb  8 08:31:38 lubuntu partman: 
Feb  8 08:31:38 lubuntu partman-lvm:   
Feb  8 08:31:38 lubuntu partman-lvm: No volume groups found
Feb  8 08:31:38 lubuntu partman-lvm: 
Feb  8 08:31:39 lubuntu ntfsresize: ntfsresize v2013.1.13AR.1 (libntfs-3g)
Feb  8 08:31:39 lubuntu ntfsresize: Device name        : /dev/sdb1
Feb  8 08:31:39 lubuntu ntfsresize: NTFS volume version: 3.1
Feb  8 08:31:39 lubuntu ntfsresize: Cluster size       : 4096 bytes
Feb  8 08:31:39 lubuntu ntfsresize: Current volume size: 3959992832 bytes (3960 MB)
Feb  8 08:31:39 lubuntu ntfsresize: Current device size: 3960000000 bytes (3960 MB)
Feb  8 08:31:39 lubuntu ntfsresize: Checking filesystem consistency ...
Feb  8 08:31:39 lubuntu ntfsresize: Accounting clusters ...
Feb  8 08:31:39 lubuntu ntfsresize: Space in use       : 3957 MB (99.9%)
Feb  8 08:31:39 lubuntu ntfsresize: Collecting resizing constraints ...
Feb  8 08:31:39 lubuntu ntfsresize: You might resize at 3956678656 bytes or 3957 MB (freeing 3 MB).
Feb  8 08:31:39 lubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Feb  8 08:31:42 lubuntu kernel: [ 5249.277953] NTFS driver 2.1.30 [Flags: R/O MODULE].
Feb  8 08:31:42 lubuntu kernel: [ 5249.388533] QNX4 filesystem 0.2.3 registered.
Feb  8 08:31:42 lubuntu os-prober:   
Feb  8 08:31:42 lubuntu os-prober: No volume groups found
Feb  8 08:31:42 lubuntu os-prober: 
Feb  8 08:31:42 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/05efi on mounted /dev/sda1
Feb  8 08:31:42 lubuntu 05efi: debug: Not on UEFI platform
Feb  8 08:31:42 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda1
Feb  8 08:31:42 lubuntu 10freedos: debug: /dev/sda1 is a FAT32 partition
Feb  8 08:31:42 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda1
Feb  8 08:31:42 lubuntu 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Feb  8 08:31:42 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda1
Feb  8 08:31:42 lubuntu macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Feb  8 08:31:42 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda1
Feb  8 08:31:42 lubuntu 20microsoft: debug: /dev/sda1 is a FAT32 partition
Feb  8 08:31:42 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda1
Feb  8 08:31:42 lubuntu 30utility: debug: /dev/sda1 is a FAT32 partition
Feb  8 08:31:42 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda1
Feb  8 08:31:42 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda1
Feb  8 08:31:42 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda1
Feb  8 08:31:42 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/83haiku on mounted /dev/sda1
Feb  8 08:31:42 lubuntu 83haiku: debug: /dev/sda1 is not a BeFS partition: exiting
Feb  8 08:31:42 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda1
Feb  8 08:31:42 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda1
Feb  8 08:31:42 lubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sdb1
Feb  8 08:31:43 lubuntu 50mounted-tests: debug: mounted using GRUB ntfs filesystem driver
Feb  8 08:31:43 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/05efi
Feb  8 08:31:43 lubuntu 05efi: debug: Not on UEFI platform
Feb  8 08:31:43 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Feb  8 08:31:43 lubuntu 10freedos: debug: /dev/sdb1 is not a FAT partition: exiting
Feb  8 08:31:43 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Feb  8 08:31:43 lubuntu 10qnx: debug: /dev/sdb1 is not a QNX4 partition: exiting
Feb  8 08:31:43 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Feb  8 08:31:43 lubuntu macosx-prober: debug: /dev/sdb1 is not an HFS+ partition: exiting
Feb  8 08:31:43 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Feb  8 08:31:43 lubuntu 20microsoft: debug: /dev/sdb1 is a NTFS partition
Feb  8 08:31:43 lubuntu 20microsoft: result: /dev/sdb1:Windows Recovery Environment (loader):Windows:chain
Feb  8 08:31:43 lubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
Feb  8 08:31:43 lubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Feb  8 08:31:43 lubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sdb2
Feb  8 08:31:43 lubuntu 50mounted-tests: debug: /dev/sdb2 type not recognised; skipping
Feb  8 08:31:43 lubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Feb  8 08:31:43 lubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sdb5
Feb  8 08:31:43 lubuntu 50mounted-tests: debug: mounted using GRUB ext2 filesystem driver
Feb  8 08:31:43 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/05efi
Feb  8 08:31:43 lubuntu 05efi: debug: Not on UEFI platform
Feb  8 08:31:43 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Feb  8 08:31:43 lubuntu 10freedos: debug: /dev/sdb5 is not a FAT partition: exiting
Feb  8 08:31:43 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Feb  8 08:31:43 lubuntu 10qnx: debug: /dev/sdb5 is not a QNX4 partition: exiting
Feb  8 08:31:43 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Feb  8 08:31:43 lubuntu macosx-prober: debug: /dev/sdb5 is not an HFS+ partition: exiting
Feb  8 08:31:43 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Feb  8 08:31:43 lubuntu 20microsoft: debug: /dev/sdb5 is not a MS partition: exiting
Feb  8 08:31:43 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Feb  8 08:31:43 lubuntu 30utility: debug: /dev/sdb5 is not a FAT partition: exiting
Feb  8 08:31:43 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Feb  8 08:31:43 lubuntu 40lsb: result: /dev/sdb5:Ubuntu Trusty Tahr (development branch) (14.04):Ubuntu:linux
Feb  8 08:31:43 lubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/40lsb
Feb  8 08:31:43 lubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Feb  8 08:31:43 lubuntu ubiquity[4668]: Device free not found in os-prober output
Feb  8 08:31:43 lubuntu ubiquity[4668]: switched to page partman
Feb  8 08:33:12 lubuntu ubiquity[4668]: message repeated 4 times: [ switched to page partman]
Feb  8 08:33:14 lubuntu ubiquity[4668]: debconffilter_done: ubi-partman (current: ubi-partman)
Feb  8 08:33:14 lubuntu activate-dmraid: No Serial ATA RAID disks detected
Feb  8 08:33:14 lubuntu partman:   No matching physical volumes found
Feb  8 08:33:14 lubuntu partman:   Reading all physical volumes.  This may take a while...
Feb  8 08:33:14 lubuntu partman:   
Feb  8 08:33:14 lubuntu partman: No volume groups found
Feb  8 08:33:14 lubuntu partman: 
Feb  8 08:33:14 lubuntu partman-lvm:   
Feb  8 08:33:14 lubuntu partman-lvm: No volume groups found
Feb  8 08:33:14 lubuntu partman-lvm: 
Feb  8 08:33:16 lubuntu ntfsresize: ntfsresize v2013.1.13AR.1 (libntfs-3g)
Feb  8 08:33:16 lubuntu ntfsresize: Device name        : /dev/sdb1
Feb  8 08:33:16 lubuntu ntfsresize: NTFS volume version: 3.1
Feb  8 08:33:16 lubuntu ntfsresize: Cluster size       : 4096 bytes
Feb  8 08:33:16 lubuntu ntfsresize: Current volume size: 3959992832 bytes (3960 MB)
Feb  8 08:33:16 lubuntu ntfsresize: Current device size: 3960000000 bytes (3960 MB)
Feb  8 08:33:16 lubuntu ntfsresize: Checking filesystem consistency ...
Feb  8 08:33:16 lubuntu ntfsresize: Accounting clusters ...
Feb  8 08:33:16 lubuntu ntfsresize: Space in use       : 3957 MB (99.9%)
Feb  8 08:33:16 lubuntu ntfsresize: Collecting resizing constraints ...
Feb  8 08:33:16 lubuntu ntfsresize: You might resize at 3956678656 bytes or 3957 MB (freeing 3 MB).
Feb  8 08:33:16 lubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Feb  8 08:33:18 lubuntu ubiquity[4668]: Device free not found in os-prober output
Feb  8 08:33:18 lubuntu ubiquity[4668]: switched to page partman
Feb  8 08:33:33 lubuntu ubiquity[4668]: debconffilter_done: ubi-partman (current: ubi-partman)
Feb  8 08:33:35 lubuntu ubiquity: Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49.
Feb  8 08:33:35 lubuntu ubiquity: Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 51.
Feb  8 08:33:35 lubuntu ubiquity: Use of uninitialized value in sysopen at /usr/share/perl5/Debconf/DbDriver/File.pm line 53.
Feb  8 08:33:35 lubuntu ubiquity: Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 53.
Feb  8 08:33:35 lubuntu ubiquity: debconf: DbDriver "targetdb": could not open 
Feb  8 08:33:35 lubuntu ubiquity[4668]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^oem-config/ --config=Name:targetdb --config=Driver:File --config=Mode:0644 --config=Filename:/target/var/cache/debconf/config.dat
Feb  8 08:33:35 lubuntu ubiquity: Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49.
Feb  8 08:33:35 lubuntu ubiquity: Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 51.
Feb  8 08:33:35 lubuntu ubiquity: Use of uninitialized value in sysopen at /usr/share/perl5/Debconf/DbDriver/File.pm line 53.
Feb  8 08:33:35 lubuntu ubiquity: Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 53.
Feb  8 08:33:35 lubuntu ubiquity: debconf: DbDriver "targetdb": could not open 
Feb  8 08:33:35 lubuntu ubiquity[4668]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^keyboard-configuration/ --config=Name:targetdb --config=Driver:File --config=Mode:0644 --config=Filename:/target/var/cache/debconf/config.dat
Feb  8 08:33:35 lubuntu ubiquity: Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49.
Feb  8 08:33:35 lubuntu ubiquity: Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 51.
Feb  8 08:33:35 lubuntu ubiquity: Use of uninitialized value in sysopen at /usr/share/perl5/Debconf/DbDriver/File.pm line 53.
Feb  8 08:33:35 lubuntu ubiquity: Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 53.
Feb  8 08:33:35 lubuntu ubiquity: debconf: DbDriver "targetdb": could not open 
Feb  8 08:33:35 lubuntu ubiquity[4668]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^console-setup/ --config=Name:targetdb --config=Driver:File --config=Mode:0644 --config=Filename:/target/var/cache/debconf/config.dat
Feb  8 08:50:56 lubuntu dhclient: DHCPREQUEST of 172.16.1.105 on eth0 to 172.16.1.1 port 67 (xid=0x5696d477)
Feb  8 08:50:56 lubuntu dhclient: DHCPACK of 172.16.1.105 from 172.16.1.1
Feb  8 08:50:56 lubuntu dhclient: bound to 172.16.1.105 -- renewal in 1329 seconds.
Feb  8 08:50:56 lubuntu NetworkManager[1365]: <info> (eth0): DHCPv4 state changed renew -> renew
Feb  8 08:50:56 lubuntu NetworkManager[1365]: <info>   address 172.16.1.105
Feb  8 08:50:56 lubuntu NetworkManager[1365]: <info>   prefix 24 (255.255.255.0)
Feb  8 08:50:56 lubuntu NetworkManager[1365]: <info>   gateway 172.16.1.1
Feb  8 08:50:56 lubuntu NetworkManager[1365]: <info>   hostname 'lubuntu'
Feb  8 08:50:56 lubuntu NetworkManager[1365]: <info>   nameserver '172.16.1.1'
Feb  8 08:50:56 lubuntu dbus[1026]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Feb  8 08:50:56 lubuntu dbus[1026]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb  8 09:13:05 lubuntu dhclient: DHCPREQUEST of 172.16.1.105 on eth0 to 172.16.1.1 port 67 (xid=0x5696d477)
Feb  8 09:13:06 lubuntu dhclient: DHCPACK of 172.16.1.105 from 172.16.1.1
Feb  8 09:13:06 lubuntu NetworkManager[1365]: <info> (eth0): DHCPv4 state changed renew -> renew
Feb  8 09:13:06 lubuntu NetworkManager[1365]: <info>   address 172.16.1.105
Feb  8 09:13:06 lubuntu NetworkManager[1365]: <info>   prefix 24 (255.255.255.0)
Feb  8 09:13:06 lubuntu NetworkManager[1365]: <info>   gateway 172.16.1.1
Feb  8 09:13:06 lubuntu NetworkManager[1365]: <info>   hostname 'lubuntu'
Feb  8 09:13:06 lubuntu NetworkManager[1365]: <info>   nameserver '172.16.1.1'
Feb  8 09:13:06 lubuntu dbus[1026]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Feb  8 09:13:06 lubuntu dhclient: bound to 172.16.1.105 -- renewal in 1487 seconds.
Feb  8 09:13:06 lubuntu dbus[1026]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb  8 09:17:01 lubuntu CRON[9416]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb  8 09:21:56 lubuntu dbus[1026]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Feb  8 09:21:56 lubuntu polkitd[9532]: started daemon version 0.105 using authority implementation `local' version `0.105'
Feb  8 09:21:56 lubuntu dbus[1026]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Feb  8 09:21:57 lubuntu ubiquity[9543]: Ubiquity 2.17.3
Feb  8 09:21:58 lubuntu ubiquity[9543]: log-output -t ubiquity laptop-detect
Feb  8 09:22:02 lubuntu ubiquity[9543]: switched to page language
Feb  8 09:22:04 lubuntu localechooser: info: debian-installer/language preseeded to 'en' (seen: false)
Feb  8 09:22:04 lubuntu localechooser: info: debian-installer/country preseeded to 'US' (seen: false)
Feb  8 09:22:04 lubuntu localechooser: info: debian-installer/locale preseeded to 'en_US.UTF-8' (seen: false)
Feb  8 09:22:04 lubuntu localechooser: info: Preseeded language ignored: unknown language code
Feb  8 09:22:17 lubuntu localechooser: info: Language = 'en'
Feb  8 09:22:17 lubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
Feb  8 09:22:17 lubuntu localechooser: info: Set debian-installer/language = 'en'
Feb  8 09:22:17 lubuntu localechooser: info: Default country = 'US'
Feb  8 09:22:17 lubuntu localechooser: info: Default locale = 'en_US.UTF-8'
Feb  8 09:22:17 lubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Feb  8 09:22:17 lubuntu localechooser: info: Set debian-installer/country = 'US'
Feb  8 09:22:17 lubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Feb  8 09:22:17 lubuntu localechooser: info: System locale (debian-installer/locale) = 'en_US.UTF-8'
Feb  8 09:22:04 lubuntu ubiquity[9543]: switched to page language
Feb  8 09:22:19 lubuntu ubiquity[9543]: debconffilter_done: ubi-language (current: ubi-language)
Feb  8 09:22:20 lubuntu ubiquity[9543]: Step_before = stepLanguage
Feb  8 09:22:20 lubuntu ubiquity[9543]: Step_before = stepLanguage
Feb  8 09:22:21 lubuntu ubiquity[9543]: switched to page prepare
Feb  8 09:22:23 lubuntu ubiquity[9543]: debconffilter_done: ubi-prepare (current: ubi-prepare)
Feb  8 09:22:23 lubuntu ubiquity[9543]: Step_before = stepPrepare
Feb  8 09:22:23 lubuntu activate-dmraid: No Serial ATA RAID disks detected
Feb  8 09:22:23 lubuntu partman:   No matching physical volumes found
Feb  8 09:22:23 lubuntu partman:   Reading all physical volumes.  This may take a while...
Feb  8 09:22:23 lubuntu partman:   
Feb  8 09:22:23 lubuntu partman: No volume groups found
Feb  8 09:22:23 lubuntu partman: 
Feb  8 09:22:23 lubuntu partman-lvm:   
Feb  8 09:22:23 lubuntu partman-lvm: No volume groups found
Feb  8 09:22:23 lubuntu partman-lvm: 
Feb  8 09:22:25 lubuntu ntfsresize: ntfsresize v2013.1.13AR.1 (libntfs-3g)
Feb  8 09:22:25 lubuntu ntfsresize: Device name        : /dev/sdb1
Feb  8 09:22:25 lubuntu ntfsresize: NTFS volume version: 3.1
Feb  8 09:22:25 lubuntu ntfsresize: Cluster size       : 4096 bytes
Feb  8 09:22:25 lubuntu ntfsresize: Current volume size: 3958338048 bytes (3959 MB)
Feb  8 09:22:25 lubuntu ntfsresize: Current device size: 3958342144 bytes (3959 MB)
Feb  8 09:22:25 lubuntu ntfsresize: Checking filesystem consistency ...
Feb  8 09:22:25 lubuntu ntfsresize: Accounting clusters ...
Feb  8 09:22:25 lubuntu ntfsresize: Space in use       : 3957 MB (100.0%)
Feb  8 09:22:25 lubuntu ntfsresize: Collecting resizing constraints ...
Feb  8 09:22:25 lubuntu ntfsresize: You might resize at 3956678656 bytes or 3957 MB (freeing 2 MB).
Feb  8 09:22:25 lubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Feb  8 09:22:27 lubuntu os-prober:   
Feb  8 09:22:27 lubuntu os-prober: No volume groups found
Feb  8 09:22:27 lubuntu os-prober: 
Feb  8 09:22:27 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/05efi on mounted /dev/sda1
Feb  8 09:22:27 lubuntu 05efi: debug: Not on UEFI platform
Feb  8 09:22:27 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda1
Feb  8 09:22:27 lubuntu 10freedos: debug: /dev/sda1 is a FAT32 partition
Feb  8 09:22:27 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda1
Feb  8 09:22:27 lubuntu 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Feb  8 09:22:27 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda1
Feb  8 09:22:27 lubuntu macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Feb  8 09:22:27 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda1
Feb  8 09:22:27 lubuntu 20microsoft: debug: /dev/sda1 is a FAT32 partition
Feb  8 09:22:27 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda1
Feb  8 09:22:27 lubuntu 30utility: debug: /dev/sda1 is a FAT32 partition
Feb  8 09:22:27 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda1
Feb  8 09:22:27 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda1
Feb  8 09:22:27 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda1
Feb  8 09:22:27 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/83haiku on mounted /dev/sda1
Feb  8 09:22:27 lubuntu 83haiku: debug: /dev/sda1 is not a BeFS partition: exiting
Feb  8 09:22:27 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda1
Feb  8 09:22:27 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda1
Feb  8 09:22:27 lubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sdb1
Feb  8 09:22:27 lubuntu 50mounted-tests: debug: mounted using GRUB ntfs filesystem driver
Feb  8 09:22:27 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/05efi
Feb  8 09:22:27 lubuntu 05efi: debug: Not on UEFI platform
Feb  8 09:22:27 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Feb  8 09:22:27 lubuntu 10freedos: debug: /dev/sdb1 is not a FAT partition: exiting
Feb  8 09:22:27 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Feb  8 09:22:27 lubuntu 10qnx: debug: /dev/sdb1 is not a QNX4 partition: exiting
Feb  8 09:22:27 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Feb  8 09:22:27 lubuntu macosx-prober: debug: /dev/sdb1 is not an HFS+ partition: exiting
Feb  8 09:22:27 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Feb  8 09:22:27 lubuntu 20microsoft: debug: /dev/sdb1 is a NTFS partition
Feb  8 09:22:27 lubuntu 20microsoft: result: /dev/sdb1:Windows Recovery Environment (loader):Windows:chain
Feb  8 09:22:27 lubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
Feb  8 09:22:27 lubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Feb  8 09:22:27 lubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sdb2
Feb  8 09:22:27 lubuntu 50mounted-tests: debug: mounted using GRUB ext2 filesystem driver
Feb  8 09:22:27 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/05efi
Feb  8 09:22:27 lubuntu 05efi: debug: Not on UEFI platform
Feb  8 09:22:27 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Feb  8 09:22:27 lubuntu 10freedos: debug: /dev/sdb2 is not a FAT partition: exiting
Feb  8 09:22:27 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Feb  8 09:22:27 lubuntu 10qnx: debug: /dev/sdb2 is not a QNX4 partition: exiting
Feb  8 09:22:27 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Feb  8 09:22:27 lubuntu macosx-prober: debug: /dev/sdb2 is not an HFS+ partition: exiting
Feb  8 09:22:27 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Feb  8 09:22:27 lubuntu 20microsoft: debug: /dev/sdb2 is not a MS partition: exiting
Feb  8 09:22:27 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Feb  8 09:22:27 lubuntu 30utility: debug: /dev/sdb2 is not a FAT partition: exiting
Feb  8 09:22:27 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Feb  8 09:22:27 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Feb  8 09:22:27 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Feb  8 09:22:27 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
Feb  8 09:22:27 lubuntu 83haiku: debug: /dev/sdb2 is not a BeFS partition: exiting
Feb  8 09:22:27 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Feb  8 09:22:27 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Feb  8 09:22:27 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/efi
Feb  8 09:22:27 lubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sdb3
Feb  8 09:22:27 lubuntu 50mounted-tests: debug: /dev/sdb3 is a swap partition; skipping
Feb  8 09:22:27 lubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Feb  8 09:22:27 lubuntu ubiquity[9543]: Device /dev/sdb2 not found in os-prober output
Feb  8 09:22:27 lubuntu ubiquity[9543]: Device /dev/sdb3 not found in os-prober output
Feb  8 09:22:27 lubuntu ubiquity[9543]: switched to page partman
Feb  8 09:22:50 lubuntu ubiquity[9543]: message repeated 3 times: [ switched to page partman]
Feb  8 09:23:53 lubuntu ubiquity[9543]: debconffilter_done: ubi-partman (current: ubi-partman)
Feb  8 09:23:54 lubuntu ubiquity: Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49.
Feb  8 09:23:54 lubuntu ubiquity: Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 51.
Feb  8 09:23:54 lubuntu ubiquity: Use of uninitialized value in sysopen at /usr/share/perl5/Debconf/DbDriver/File.pm line 53.
Feb  8 09:23:54 lubuntu ubiquity: Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 53.
Feb  8 09:23:54 lubuntu ubiquity: debconf: DbDriver "targetdb": could not open 
Feb  8 09:23:54 lubuntu ubiquity[9543]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^oem-config/ --config=Name:targetdb --config=Driver:File --config=Mode:0644 --config=Filename:/target/var/cache/debconf/config.dat
Feb  8 09:23:54 lubuntu ubiquity: Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49.
Feb  8 09:23:54 lubuntu ubiquity: Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 51.
Feb  8 09:23:54 lubuntu ubiquity: Use of uninitialized value in sysopen at /usr/share/perl5/Debconf/DbDriver/File.pm line 53.
Feb  8 09:23:54 lubuntu ubiquity: Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 53.
Feb  8 09:23:54 lubuntu ubiquity: debconf: DbDriver "targetdb": could not open 
Feb  8 09:23:54 lubuntu ubiquity[9543]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^keyboard-configuration/ --config=Name:targetdb --config=Driver:File --config=Mode:0644 --config=Filename:/target/var/cache/debconf/config.dat
Feb  8 09:23:54 lubuntu ubiquity: Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49.
Feb  8 09:23:54 lubuntu ubiquity: Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 51.
Feb  8 09:23:54 lubuntu ubiquity: Use of uninitialized value in sysopen at /usr/share/perl5/Debconf/DbDriver/File.pm line 53.
Feb  8 09:23:54 lubuntu ubiquity: Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 53.
Feb  8 09:23:54 lubuntu ubiquity: debconf: DbDriver "targetdb": could not open 
Feb  8 09:23:55 lubuntu ubiquity[9543]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^console-setup/ --config=Name:targetdb --config=Driver:File --config=Mode:0644 --config=Filename:/target/var/cache/debconf/config.dat
Feb  8 09:33:01 lubuntu dbus[1026]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Feb  8 09:33:01 lubuntu polkitd[13286]: started daemon version 0.105 using authority implementation `local' version `0.105'
Feb  8 09:33:01 lubuntu dbus[1026]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Feb  8 09:33:02 lubuntu ubiquity[13297]: Ubiquity 2.17.3
Feb  8 09:33:04 lubuntu ubiquity[13297]: log-output -t ubiquity laptop-detect
Feb  8 09:33:07 lubuntu ubiquity[13297]: switched to page language
Feb  8 09:33:09 lubuntu localechooser: info: debian-installer/language preseeded to 'en' (seen: false)
Feb  8 09:33:09 lubuntu localechooser: info: debian-installer/country preseeded to 'US' (seen: false)
Feb  8 09:33:09 lubuntu localechooser: info: debian-installer/locale preseeded to 'en_US.UTF-8' (seen: false)
Feb  8 09:33:09 lubuntu localechooser: info: Preseeded language ignored: unknown language code
Feb  8 09:33:11 lubuntu localechooser: info: Language = 'en'
Feb  8 09:33:11 lubuntu localechooser: info: line=en;0;US;UTF-8;en_US.UTF-8;;console-setup
Feb  8 09:33:11 lubuntu localechooser: info: Set debian-installer/language = 'en'
Feb  8 09:33:11 lubuntu localechooser: info: Default country = 'US'
Feb  8 09:33:11 lubuntu localechooser: info: Default locale = 'en_US.UTF-8'
Feb  8 09:33:11 lubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Feb  8 09:33:11 lubuntu localechooser: info: Set debian-installer/country = 'US'
Feb  8 09:33:11 lubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Feb  8 09:33:11 lubuntu localechooser: info: System locale (debian-installer/locale) = 'en_US.UTF-8'
Feb  8 09:33:09 lubuntu ubiquity[13297]: switched to page language
Feb  8 09:33:14 lubuntu ubiquity[13297]: debconffilter_done: ubi-language (current: ubi-language)
Feb  8 09:33:14 lubuntu ubiquity[13297]: Step_before = stepLanguage
Feb  8 09:33:14 lubuntu ubiquity[13297]: Step_before = stepLanguage
Feb  8 09:33:15 lubuntu ubiquity[13297]: switched to page prepare
Feb  8 09:33:17 lubuntu ubiquity[13297]: debconffilter_done: ubi-prepare (current: ubi-prepare)
Feb  8 09:33:17 lubuntu ubiquity[13297]: Step_before = stepPrepare
Feb  8 09:33:17 lubuntu activate-dmraid: No Serial ATA RAID disks detected
Feb  8 09:33:17 lubuntu partman:   No matching physical volumes found
Feb  8 09:33:17 lubuntu partman:   Reading all physical volumes.  This may take a while...
Feb  8 09:33:17 lubuntu partman:   
Feb  8 09:33:17 lubuntu partman: No volume groups found
Feb  8 09:33:17 lubuntu partman: 
Feb  8 09:33:17 lubuntu partman-lvm:   
Feb  8 09:33:17 lubuntu partman-lvm: No volume groups found
Feb  8 09:33:17 lubuntu partman-lvm: 
Feb  8 09:33:18 lubuntu ntfsresize: ntfsresize v2013.1.13AR.1 (libntfs-3g)
Feb  8 09:33:18 lubuntu ntfsresize: Device name        : /dev/sdb1
Feb  8 09:33:18 lubuntu ntfsresize: NTFS volume version: 3.1
Feb  8 09:33:18 lubuntu ntfsresize: Cluster size       : 4096 bytes
Feb  8 09:33:18 lubuntu ntfsresize: Current volume size: 3958338048 bytes (3959 MB)
Feb  8 09:33:18 lubuntu ntfsresize: Current device size: 3958342144 bytes (3959 MB)
Feb  8 09:33:18 lubuntu ntfsresize: Checking filesystem consistency ...
Feb  8 09:33:18 lubuntu ntfsresize: Accounting clusters ...
Feb  8 09:33:18 lubuntu ntfsresize: Space in use       : 3957 MB (100.0%)
Feb  8 09:33:18 lubuntu ntfsresize: Collecting resizing constraints ...
Feb  8 09:33:18 lubuntu ntfsresize: You might resize at 3956678656 bytes or 3957 MB (freeing 2 MB).
Feb  8 09:33:18 lubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Feb  8 09:33:20 lubuntu os-prober:   
Feb  8 09:33:20 lubuntu os-prober: No volume groups found
Feb  8 09:33:20 lubuntu os-prober: 
Feb  8 09:33:20 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/05efi on mounted /dev/sda1
Feb  8 09:33:20 lubuntu 05efi: debug: Not on UEFI platform
Feb  8 09:33:20 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda1
Feb  8 09:33:20 lubuntu 10freedos: debug: /dev/sda1 is a FAT32 partition
Feb  8 09:33:20 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda1
Feb  8 09:33:20 lubuntu 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Feb  8 09:33:20 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda1
Feb  8 09:33:20 lubuntu macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Feb  8 09:33:20 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda1
Feb  8 09:33:20 lubuntu 20microsoft: debug: /dev/sda1 is a FAT32 partition
Feb  8 09:33:20 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda1
Feb  8 09:33:20 lubuntu 30utility: debug: /dev/sda1 is a FAT32 partition
Feb  8 09:33:20 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda1
Feb  8 09:33:20 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda1
Feb  8 09:33:20 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda1
Feb  8 09:33:20 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/83haiku on mounted /dev/sda1
Feb  8 09:33:20 lubuntu 83haiku: debug: /dev/sda1 is not a BeFS partition: exiting
Feb  8 09:33:20 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda1
Feb  8 09:33:20 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda1
Feb  8 09:33:20 lubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sdb1
Feb  8 09:33:21 lubuntu 50mounted-tests: debug: mounted using GRUB ntfs filesystem driver
Feb  8 09:33:21 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/05efi
Feb  8 09:33:21 lubuntu 05efi: debug: Not on UEFI platform
Feb  8 09:33:21 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Feb  8 09:33:21 lubuntu 10freedos: debug: /dev/sdb1 is not a FAT partition: exiting
Feb  8 09:33:21 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Feb  8 09:33:21 lubuntu 10qnx: debug: /dev/sdb1 is not a QNX4 partition: exiting
Feb  8 09:33:21 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Feb  8 09:33:21 lubuntu macosx-prober: debug: /dev/sdb1 is not an HFS+ partition: exiting
Feb  8 09:33:21 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Feb  8 09:33:21 lubuntu 20microsoft: debug: /dev/sdb1 is a NTFS partition
Feb  8 09:33:21 lubuntu 20microsoft: result: /dev/sdb1:Windows Recovery Environment (loader):Windows:chain
Feb  8 09:33:21 lubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
Feb  8 09:33:21 lubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Feb  8 09:33:21 lubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sdb2
Feb  8 09:33:21 lubuntu 50mounted-tests: debug: mounted using GRUB ext2 filesystem driver
Feb  8 09:33:21 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/05efi
Feb  8 09:33:21 lubuntu 05efi: debug: Not on UEFI platform
Feb  8 09:33:21 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Feb  8 09:33:21 lubuntu 10freedos: debug: /dev/sdb2 is not a FAT partition: exiting
Feb  8 09:33:21 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Feb  8 09:33:21 lubuntu 10qnx: debug: /dev/sdb2 is not a QNX4 partition: exiting
Feb  8 09:33:21 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Feb  8 09:33:21 lubuntu macosx-prober: debug: /dev/sdb2 is not an HFS+ partition: exiting
Feb  8 09:33:21 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Feb  8 09:33:21 lubuntu 20microsoft: debug: /dev/sdb2 is not a MS partition: exiting
Feb  8 09:33:21 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Feb  8 09:33:21 lubuntu 30utility: debug: /dev/sdb2 is not a FAT partition: exiting
Feb  8 09:33:21 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Feb  8 09:33:21 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Feb  8 09:33:21 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Feb  8 09:33:21 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
Feb  8 09:33:21 lubuntu 83haiku: debug: /dev/sdb2 is not a BeFS partition: exiting
Feb  8 09:33:21 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Feb  8 09:33:21 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Feb  8 09:33:21 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/efi
Feb  8 09:33:21 lubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sdb3
Feb  8 09:33:21 lubuntu 50mounted-tests: debug: /dev/sdb3 is a swap partition; skipping
Feb  8 09:33:21 lubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Feb  8 09:33:21 lubuntu ubiquity[13297]: Device /dev/sdb2 not found in os-prober output
Feb  8 09:33:21 lubuntu ubiquity[13297]: Device /dev/sdb3 not found in os-prober output
Feb  8 09:33:21 lubuntu ubiquity[13297]: switched to page partman
Feb  8 09:33:22 lubuntu ubiquity[13297]: debconffilter_done: ubi-partman (current: ubi-partman)
Feb  8 09:33:22 lubuntu ubiquity[13297]: switched to page prepare
Feb  8 09:33:38 lubuntu ubiquity[13297]: debconffilter_done: ubi-prepare (current: ubi-prepare)
Feb  8 09:33:38 lubuntu ubiquity[13297]: Step_before = stepPrepare
Feb  8 09:33:38 lubuntu activate-dmraid: No Serial ATA RAID disks detected
Feb  8 09:33:38 lubuntu partman:   No matching physical volumes found
Feb  8 09:33:38 lubuntu partman:   Reading all physical volumes.  This may take a while...
Feb  8 09:33:38 lubuntu partman:   
Feb  8 09:33:38 lubuntu partman: No volume groups found
Feb  8 09:33:38 lubuntu partman: 
Feb  8 09:33:38 lubuntu partman-lvm:   
Feb  8 09:33:38 lubuntu partman-lvm: No volume groups found
Feb  8 09:33:38 lubuntu partman-lvm: 
Feb  8 09:33:39 lubuntu ntfsresize: ntfsresize v2013.1.13AR.1 (libntfs-3g)
Feb  8 09:33:39 lubuntu ntfsresize: Device name        : /dev/sdb1
Feb  8 09:33:39 lubuntu ntfsresize: NTFS volume version: 3.1
Feb  8 09:33:39 lubuntu ntfsresize: Cluster size       : 4096 bytes
Feb  8 09:33:39 lubuntu ntfsresize: Current volume size: 3958338048 bytes (3959 MB)
Feb  8 09:33:39 lubuntu ntfsresize: Current device size: 3958342144 bytes (3959 MB)
Feb  8 09:33:39 lubuntu ntfsresize: Checking filesystem consistency ...
Feb  8 09:33:39 lubuntu ntfsresize: Accounting clusters ...
Feb  8 09:33:39 lubuntu ntfsresize: Space in use       : 3957 MB (100.0%)
Feb  8 09:33:39 lubuntu ntfsresize: Collecting resizing constraints ...
Feb  8 09:33:39 lubuntu ntfsresize: You might resize at 3956678656 bytes or 3957 MB (freeing 2 MB).
Feb  8 09:33:39 lubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Feb  8 09:33:41 lubuntu ubiquity[13297]: Device /dev/sdb2 not found in os-prober output
Feb  8 09:33:41 lubuntu ubiquity[13297]: Device /dev/sdb3 not found in os-prober output
Feb  8 09:33:41 lubuntu ubiquity[13297]: switched to page partman
Feb  8 09:36:44 lubuntu kernel: [ 9151.487991] Adding 2098172k swap on /dev/sdb3.  Priority:-1 extents:1 across:2098172k FS
Feb  8 09:36:45 lubuntu ubiquity: /dev/sdb2: 11/606208 files (0.0% non-contiguous), 76147/2420736 blocks
Feb  8 09:36:45 lubuntu ubiquity: resize2fs 1.42.9 (28-Dec-2013)
Feb  8 09:36:45 lubuntu ubiquity: Resizing the filesystem on /dev/sdb2 to 2420654 (4k) blocks.
Feb  8 09:36:45 lubuntu ubiquity: The filesystem on /dev/sdb2 is now 2420654 blocks long.
Feb  8 09:36:45 lubuntu ubiquity: 
Feb  8 09:36:46 lubuntu ubiquity: resize2fs 1.42.9 (28-Dec-2013)
Feb  8 09:36:46 lubuntu ubiquity: The filesystem is already 2420654 blocks long.  Nothing to do!
Feb  8 09:36:46 lubuntu ubiquity: 
Feb  8 09:36:47 lubuntu ntfsresize: ntfsresize v2013.1.13AR.1 (libntfs-3g)
Feb  8 09:36:47 lubuntu ntfsresize: Device name        : /dev/sdb1
Feb  8 09:36:47 lubuntu ntfsresize: NTFS volume version: 3.1
Feb  8 09:36:47 lubuntu ntfsresize: Cluster size       : 4096 bytes
Feb  8 09:36:47 lubuntu ntfsresize: Current volume size: 3958338048 bytes (3959 MB)
Feb  8 09:36:47 lubuntu ntfsresize: Current device size: 3958342144 bytes (3959 MB)
Feb  8 09:36:47 lubuntu ntfsresize: Checking filesystem consistency ...
Feb  8 09:36:47 lubuntu ntfsresize: Accounting clusters ...
Feb  8 09:36:47 lubuntu ntfsresize: Space in use       : 3957 MB (100.0%)
Feb  8 09:36:47 lubuntu ntfsresize: Collecting resizing constraints ...
Feb  8 09:36:47 lubuntu ntfsresize: You might resize at 3956678656 bytes or 3957 MB (freeing 2 MB).
Feb  8 09:36:47 lubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Feb  8 09:36:56 lubuntu dbus[1026]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Feb  8 09:36:56 lubuntu polkitd[20543]: started daemon version 0.105 using authority implementation `local' version `0.105'
Feb  8 09:36:56 lubuntu dbus[1026]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Feb  8 09:37:53 lubuntu dhclient: DHCPREQUEST of 172.16.1.105 on eth0 to 172.16.1.1 port 67 (xid=0x5696d477)
Feb  8 09:37:54 lubuntu dhclient: DHCPACK of 172.16.1.105 from 172.16.1.1
Feb  8 09:37:54 lubuntu dhclient: bound to 172.16.1.105 -- renewal in 1402 seconds.
Feb  8 09:37:54 lubuntu NetworkManager[1365]: <info> (eth0): DHCPv4 state changed renew -> renew
Feb  8 09:37:54 lubuntu NetworkManager[1365]: <info>   address 172.16.1.105
Feb  8 09:37:54 lubuntu NetworkManager[1365]: <info>   prefix 24 (255.255.255.0)
Feb  8 09:37:54 lubuntu NetworkManager[1365]: <info>   gateway 172.16.1.1
Feb  8 09:37:54 lubuntu NetworkManager[1365]: <info>   hostname 'lubuntu'
Feb  8 09:37:54 lubuntu NetworkManager[1365]: <info>   nameserver '172.16.1.1'
Feb  8 09:37:54 lubuntu dbus[1026]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Feb  8 09:37:54 lubuntu dbus[1026]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb  8 09:43:38 lubuntu ubiquity[13297]: message repeated 9 times: [ switched to page partman]
Feb  8 09:43:41 lubuntu ubiquity[13297]: debconffilter_done: ubi-partman (current: ubi-partman)
Feb  8 09:43:41 lubuntu ubiquity[13297]: Step_before = stepPartAdvanced
Feb  8 09:43:41 lubuntu clock-setup: rdate called using NTP server ntp.ubuntu.com.
Feb  8 09:43:41 lubuntu clock-setup: Sat Feb  8 09:43:41 UTC 2014
Feb  8 09:43:41 lubuntu clock-setup: rdate: adjust local clock by 0.013752 seconds
Feb  8 09:43:42 lubuntu ubiquity[13297]: switched to page timezone
Feb  8 09:43:43 lubuntu kernel: [ 9570.198314] Adding 2098172k swap on /dev/sdb3.  Priority:-1 extents:1 across:2098172k FS
Feb  8 09:43:43 lubuntu partman: mke2fs 1.42.9 (28-Dec-2013)
Feb  8 09:43:44 lubuntu ubiquity[13297]: debconffilter_done: ubi-timezone (current: ubi-timezone)
Feb  8 09:43:44 lubuntu ubiquity[13297]: Step_before = stepLocation
Feb  8 09:43:46 lubuntu ubiquity[13297]: switched to page console_setup
Feb  8 09:43:47 lubuntu ubiquity[13297]: log-output -t ubiquity setxkbmap -model pc105 -layout pl -option  -option lv3:ralt_switch
Feb  8 09:43:53 lubuntu kernel: [ 9579.942877] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: errors=remount-ro
Feb  8 09:43:53 lubuntu ubiquity[13297]: debconffilter_done: ubiquity.components.partman_commit (current: ubi-console-setup)
Feb  8 09:43:54 lubuntu /install.py: keeping packages due to preseeding: 
Feb  8 09:43:54 lubuntu /install.py: keeping language packs for: en_US.UTF-8
Feb  8 09:44:10 lubuntu dbus[1026]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Feb  8 09:44:10 lubuntu dbus[1026]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Feb  8 09:47:30 lubuntu ubiquity[13297]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
Feb  8 09:47:31 lubuntu ubiquity[13297]: switched to page console_setup
Feb  8 09:47:32 lubuntu ubiquity[13297]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
Feb  8 09:47:39 lubuntu ubiquity[13297]: switched to page console_setup
Feb  8 09:47:40 lubuntu ubiquity[13297]: log-output -t ubiquity setxkbmap -model pc105 -layout pl -option  -option lv3:ralt_switch
Feb  8 09:48:24 lubuntu ubiquity: Your console font configuration will be updated the next time your system
Feb  8 09:48:24 lubuntu ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
Feb  8 09:48:24 lubuntu ubiquity[13297]: log-output -t ubiquity setxkbmap -model pc105 -layout pl -option 
Feb  8 09:48:24 lubuntu ubiquity[13297]: debconffilter_done: ubi-console-setup (current: ubi-console-setup)
Feb  8 09:48:24 lubuntu ubiquity[13297]: Step_before = stepKeyboardConf
Feb  8 09:48:26 lubuntu ubiquity[13297]: switched to page usersetup
Feb  8 09:49:02 lubuntu ubiquity: 13297
Feb  8 09:49:04 lubuntu ubiquity: WARNING: [/dev/zram0] is a RAM device, skipping.
Feb  8 09:49:05 lubuntu ubiquity: INFO: Setting up swap: [/dev/sdb3]
Feb  8 09:49:05 lubuntu ubiquity: WARNING: Commented out your unencrypted swap from /etc/fstab
Feb  8 09:49:05 lubuntu ubiquity: INFO: Successfully setup encrypted swap!
Feb  8 09:56:30 lubuntu ubiquity:  * Starting crypto disk...
Feb  8 09:56:31 lubuntu ubiquity:  * cryptswap1 (starting)..
Feb  8 09:56:32 lubuntu kernel: [10338.910676] bio: create slab <bio-2> at 2
Feb  8 09:56:33 lubuntu ubiquity:  * cryptswap1 (started)...
Feb  8 09:56:33 lubuntu ubiquity:    ...done.
Feb  8 09:56:33 lubuntu kernel: [10340.592652] Adding 2098172k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:2098172k FS
Feb  8 09:56:34 lubuntu ubiquity[13297]: debconffilter_done: ubi-usersetup (current: ubi-usersetup)
Feb  8 09:56:34 lubuntu ubiquity[13297]: Step_before = stepUserInfo
Feb  8 09:56:44 lubuntu /install.py: Terminated ubiquity update process.
Feb  8 09:56:45 lubuntu ubiquity[13297]: debconffilter_done: ubiquity.components.install (current: None)
Feb  8 09:56:55 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target python2.7 /usr/lib/python2.7/py_compile.py
Feb  8 09:56:55 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target python2.7 /usr/lib/python2.7/py_compile.py
Feb  8 09:56:56 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target python3.3 /usr/lib/python3.3/py_compile.py
Feb  8 09:56:57 lubuntu ubiquity: Listing /usr/share/python/ ...
Feb  8 09:56:57 lubuntu ubiquity: Listing /usr/share/python/debpython ...
Feb  8 09:56:57 lubuntu ubiquity: Compiling /usr/share/python/debpython/__init__.py ...
Feb  8 09:56:57 lubuntu ubiquity: Compiling /usr/share/python/debpython/debhelper.py ...
Feb  8 09:56:57 lubuntu ubiquity: Compiling /usr/share/python/debpython/depends.py ...
Feb  8 09:56:57 lubuntu ubiquity: Compiling /usr/share/python/debpython/files.py ...
Feb  8 09:56:57 lubuntu ubiquity: Compiling /usr/share/python/debpython/namespace.py ...
Feb  8 09:56:57 lubuntu ubiquity: Compiling /usr/share/python/debpython/option.py ...
Feb  8 09:56:57 lubuntu ubiquity: Compiling /usr/share/python/debpython/pydist.py ...
Feb  8 09:56:57 lubuntu ubiquity: Compiling /usr/share/python/debpython/tools.py ...
Feb  8 09:56:57 lubuntu ubiquity: Compiling /usr/share/python/debpython/version.py ...
Feb  8 09:56:57 lubuntu ubiquity: Compiling /usr/share/python/pyversions.py ...
Feb  8 09:56:57 lubuntu ubiquity: Listing /usr/share/python/runtime.d ...
Feb  8 09:56:56 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target python3.3 /usr/lib/python3.3/py_compile.py
Feb  8 09:56:57 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target python2.7 -m compileall /usr/share/python/
Feb  8 09:56:58 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target py3compile -p python3 /usr/share/python3/
Feb  8 09:56:58 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target mount -t proc proc /proc
Feb  8 09:56:58 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Feb  8 09:56:58 lubuntu /plugininstall.py: log-output -t ubiquity mount --bind /dev /target/dev
Feb  8 09:56:58 lubuntu /plugininstall.py: log-output -t ubiquity mount --bind /run /target/run
Feb  8 09:57:00 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/public_modules.rtinstall rtinstall python2.7  2.7.6-4ubuntu1
Feb  8 09:57:01 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/gdebi-core.rtupdate pre-rtupdate python2.7 python2.7
Feb  8 09:57:01 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/libgda-5.0-common.rtupdate pre-rtupdate python2.7 python2.7
Feb  8 09:57:01 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/apport.rtupdate pre-rtupdate python2.7 python2.7
Feb  8 09:57:01 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/ibus.rtupdate pre-rtupdate python2.7 python2.7
Feb  8 09:57:01 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/gdebi.rtupdate pre-rtupdate python2.7 python2.7
Feb  8 09:57:01 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/gdebi-core.rtupdate rtupdate python2.7 python2.7
Feb  8 09:57:38 lubuntu kernel: [10404.944065] usb 1-8: reset high-speed USB device number 4 using ehci-pci
Feb  8 09:57:39 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/libgda-5.0-common.rtupdate rtupdate python2.7 python2.7
Feb  8 09:57:43 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/apport.rtupdate rtupdate python2.7 python2.7
Feb  8 09:57:44 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/ibus.rtupdate rtupdate python2.7 python2.7
Feb  8 09:57:44 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/gdebi.rtupdate rtupdate python2.7 python2.7
Feb  8 09:57:44 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/gdebi-core.rtupdate post-rtupdate python2.7 python2.7
Feb  8 09:57:44 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/libgda-5.0-common.rtupdate post-rtupdate python2.7 python2.7
Feb  8 09:57:44 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/apport.rtupdate post-rtupdate python2.7 python2.7
Feb  8 09:57:44 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/ibus.rtupdate post-rtupdate python2.7 python2.7
Feb  8 09:57:44 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python/runtime.d/gdebi.rtupdate post-rtupdate python2.7 python2.7
Feb  8 09:57:48 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python3/runtime.d/public_modules.rtinstall rtinstall python3.3  3.3.3-5ubuntu2
Feb  8 09:57:48 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python3/runtime.d/dh-python.rtupdate pre-rtupdate python3.3 python3.3
Feb  8 09:57:48 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python3/runtime.d/ubiquity.rtupdate pre-rtupdate python3.3 python3.3
Feb  8 09:57:48 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python3/runtime.d/ubuntu-drivers-common.rtupdate pre-rtupdate python3.3 python3.3
Feb  8 09:57:48 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python3/runtime.d/ubiquity-frontend-gtk.rtupdate pre-rtupdate python3.3 python3.3
Feb  8 09:57:48 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python3/runtime.d/dh-python.rtupdate rtupdate python3.3 python3.3
Feb  8 09:57:50 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python3/runtime.d/ubiquity.rtupdate rtupdate python3.3 python3.3
Feb  8 09:57:51 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python3/runtime.d/ubuntu-drivers-common.rtupdate rtupdate python3.3 python3.3
Feb  8 09:57:52 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python3/runtime.d/ubiquity-frontend-gtk.rtupdate rtupdate python3.3 python3.3
Feb  8 09:57:52 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python3/runtime.d/dh-python.rtupdate post-rtupdate python3.3 python3.3
Feb  8 09:57:52 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python3/runtime.d/ubiquity.rtupdate post-rtupdate python3.3 python3.3
Feb  8 09:57:52 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python3/runtime.d/ubuntu-drivers-common.rtupdate post-rtupdate python3.3 python3.3
Feb  8 09:57:52 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /usr/share/python3/runtime.d/ubiquity-frontend-gtk.rtupdate post-rtupdate python3.3 python3.3
Feb  8 09:57:52 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /sys
Feb  8 09:57:52 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /proc
Feb  8 09:57:52 lubuntu /plugininstall.py: log-output -t ubiquity umount /target/run
Feb  8 09:57:52 lubuntu /plugininstall.py: log-output -t ubiquity umount /target/dev
Feb  8 09:57:54 lubuntu localechooser: Generating locales...
Feb  8 09:57:54 lubuntu localechooser:   pl_PL.UTF-8... 
Feb  8 09:57:56 lubuntu localechooser: done
Feb  8 09:57:56 lubuntu localechooser: Generation complete.
Feb  8 09:57:57 lubuntu localechooser: Adding /usr/lib/locale/pl_PL.utf8
Feb  8 09:57:57 lubuntu localechooser: locale 'pl_PL.utf8' already exists
Feb  8 09:57:57 lubuntu localechooser: 
Feb  8 09:57:57 lubuntu localechooser: Generating locales...
Feb  8 09:57:57 lubuntu localechooser:   en_US.UTF-8... 
Feb  8 09:57:59 lubuntu localechooser: done
Feb  8 09:57:59 lubuntu localechooser: Generation complete.
Feb  8 09:58:00 lubuntu localechooser: Adding /usr/lib/locale/en_US.utf8
Feb  8 09:58:00 lubuntu localechooser: locale 'en_US.utf8' already exists
Feb  8 09:58:00 lubuntu localechooser: 
Feb  8 09:58:00 lubuntu ubiquity: umount: /target/cdrom: not found
Feb  8 09:58:00 lubuntu ubiquity: 
Feb  8 09:58:00 lubuntu /plugininstall.py: log-output -t ubiquity umount /target/cdrom
Feb  8 09:58:00 lubuntu ubiquity: mount: warning: /target/cdrom seems to be mounted read-only.
Feb  8 09:58:00 lubuntu /plugininstall.py: log-output -t ubiquity mount --bind /cdrom /target/cdrom
Feb  8 09:58:00 lubuntu ubiquity: /usr/lib/ubiquity/apt-setup/generators/01setup: 9: /usr/lib/ubiquity/apt-setup/generators/01setup: 
Feb  8 09:58:00 lubuntu ubiquity: cannot open /target/etc/apt/sources.list: No such file
Feb  8 09:58:00 lubuntu ubiquity: 
Feb  8 09:58:03 lubuntu dbus[1026]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Feb  8 09:58:03 lubuntu dbus[1026]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Feb  8 09:58:03 lubuntu in-target: Reading package lists...
Feb  8 09:58:03 lubuntu in-target: 
Feb  8 09:58:04 lubuntu apt-setup: Using CD-ROM mount point /cdrom/
Feb  8 09:58:04 lubuntu apt-setup: Identifying.. 
Feb  8 09:58:04 lubuntu apt-setup: [b5bcadc1b4f19a53ce396974cfa9fe96-2]
Feb  8 09:58:04 lubuntu apt-setup: Scanning disc for index files..
Feb  8 09:58:04 lubuntu apt-setup: Found 8 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
Feb  8 09:58:04 lubuntu apt-setup: Found label 'Lubuntu 14.04 _Trusty Tahr_ - Alpha amd64 (20140110)'
Feb  8 09:58:04 lubuntu apt-setup: This disc is called: 
Feb  8 09:58:04 lubuntu apt-setup: 'Lubuntu 14.04 _Trusty Tahr_ - Alpha amd64 (20140110)'
Feb  8 09:58:04 lubuntu apt-setup: Copying package lists...
Feb  8 09:58:04 lubuntu apt-setup: gpgv: 
Feb  8 09:58:04 lubuntu apt-setup: Signature made pi&#261;, 10 sty 2014, 18:49:40 CET using DSA key ID FBB75451
Feb  8 09:58:04 lubuntu apt-setup: gpgv: 
Feb  8 09:58:04 lubuntu apt-setup: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Feb  8 09:58:04 lubuntu apt-setup: 
Feb  8 09:58:05 lubuntu apt-setup: #015Reading Package Indexes... 0%#015
Feb  8 09:58:05 lubuntu apt-setup: #015Reading Package Indexes... Done#015
Feb  8 09:58:05 lubuntu apt-setup: 
Feb  8 09:58:05 lubuntu apt-setup: Writing new source list
Feb  8 09:58:05 lubuntu apt-setup: Source list entries for this disc are:
Feb  8 09:58:05 lubuntu apt-setup: deb cdrom:[Lubuntu 14.04 _Trusty Tahr_ - Alpha amd64 (20140110)]/ trusty main multiverse restricted universe
Feb  8 09:58:05 lubuntu apt-setup: Repeat this process for the rest of the CDs in your set.
Feb  8 09:58:07 lubuntu in-target: Ign cdrom://Lubuntu 14.04 _Trusty Tahr_ - Alpha amd64 (20140110) trusty InRelease
Feb  8 09:58:07 lubuntu in-target: Ign cdrom://Lubuntu 14.04 _Trusty Tahr_ - Alpha amd64 (20140110) trusty/main Translation-en_US
Feb  8 09:58:07 lubuntu in-target: Ign cdrom://Lubuntu 14.04 _Trusty Tahr_ - Alpha amd64 (20140110) trusty/main Translation-en
Feb  8 09:58:07 lubuntu in-target: Ign cdrom://Lubuntu 14.04 _Trusty Tahr_ - Alpha amd64 (20140110) trusty/multiverse Translation-en_US
Feb  8 09:58:07 lubuntu in-target: Ign cdrom://Lubuntu 14.04 _Trusty Tahr_ - Alpha amd64 (20140110) trusty/multiverse Translation-en
Feb  8 09:58:07 lubuntu in-target: Ign cdrom://Lubuntu 14.04 _Trusty Tahr_ - Alpha amd64 (20140110) trusty/restricted Translation-en_US
Feb  8 09:58:07 lubuntu in-target: Ign cdrom://Lubuntu 14.04 _Trusty Tahr_ - Alpha amd64 (20140110) trusty/restricted Translation-en
Feb  8 09:58:07 lubuntu in-target: Ign cdrom://Lubuntu 14.04 _Trusty Tahr_ - Alpha amd64 (20140110) trusty/universe Translation-en_US
Feb  8 09:58:07 lubuntu in-target: Ign cdrom://Lubuntu 14.04 _Trusty Tahr_ - Alpha amd64 (20140110) trusty/universe Translation-en
Feb  8 09:58:07 lubuntu in-target: Reading package lists...
Feb  8 09:58:08 lubuntu in-target: 
Feb  8 09:58:09 lubuntu choose-mirror[24601]: INFO: base system installable from CD; skipping mirror check
Feb  8 09:58:09 lubuntu choose-mirror[24601]: INFO: base system installable from CD; skipping architecture check
Feb  8 09:58:11 lubuntu in-target: Ign http://pl.archive.ubuntu.com trusty InRelease
Feb  8 09:58:11 lubuntu in-target: Ign http://pl.archive.ubuntu.com trusty-updates InRelease
Feb  8 09:58:11 lubuntu in-target: Ign http://pl.archive.ubuntu.com trusty-backports InRelease
Feb  8 09:58:11 lubuntu in-target: Get:1 http://pl.archive.ubuntu.com trusty Release.gpg [933 B]
Feb  8 09:58:11 lubuntu in-target: Get:2 http://pl.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Feb  8 09:58:11 lubuntu in-target: Get:3 http://pl.archive.ubuntu.com trusty-backports Release.gpg [933 B]
Feb  8 09:58:11 lubuntu in-target: Get:4 http://pl.archive.ubuntu.com trusty Release [58,5 kB]
Feb  8 09:58:11 lubuntu in-target: Get:5 http://pl.archive.ubuntu.com trusty-updates Release [58,5 kB]
Feb  8 09:58:11 lubuntu in-target: Get:6 http://pl.archive.ubuntu.com trusty-backports Release [58,6 kB]
Feb  8 09:58:11 lubuntu in-target: Get:7 http://pl.archive.ubuntu.com trusty/main Sources [1057 kB]
Feb  8 09:58:12 lubuntu in-target: Get:8 http://pl.archive.ubuntu.com trusty/restricted Sources [5380 B]
Feb  8 09:58:12 lubuntu in-target: Get:9 http://pl.archive.ubuntu.com trusty/universe Sources [6412 kB]
Feb  8 09:58:26 lubuntu in-target: Get:10 http://pl.archive.ubuntu.com trusty/multiverse Sources [177 kB]
Feb  8 09:58:26 lubuntu in-target: Get:11 http://pl.archive.ubuntu.com trusty/main amd64 Packages [1313 kB]
Feb  8 09:58:28 lubuntu in-target: Get:12 http://pl.archive.ubuntu.com trusty/restricted amd64 Packages [11,7 kB]
Feb  8 09:58:28 lubuntu in-target: Get:13 http://pl.archive.ubuntu.com trusty/universe amd64 Packages [5875 kB]
Feb  8 09:58:36 lubuntu in-target: Get:14 http://pl.archive.ubuntu.com trusty/multiverse amd64 Packages [133 kB]
Feb  8 09:58:36 lubuntu in-target: Get:15 http://pl.archive.ubuntu.com trusty/main i386 Packages [1311 kB]
Feb  8 09:58:38 lubuntu in-target: Get:16 http://pl.archive.ubuntu.com trusty/restricted i386 Packages [12,1 kB]
Feb  8 09:58:38 lubuntu in-target: Get:17 http://pl.archive.ubuntu.com trusty/universe i386 Packages [5883 kB]
Feb  8 09:58:46 lubuntu in-target: Get:18 http://pl.archive.ubuntu.com trusty/multiverse i386 Packages [135 kB]
Feb  8 09:58:46 lubuntu in-target: Get:19 http://pl.archive.ubuntu.com trusty/main Translation-en [753 kB]
Feb  8 09:58:47 lubuntu in-target: Get:20 http://pl.archive.ubuntu.com trusty/multiverse Translation-en [102 kB]
Feb  8 09:58:47 lubuntu in-target: Get:21 http://pl.archive.ubuntu.com trusty/restricted Translation-en [3457 B]
Feb  8 09:58:47 lubuntu in-target: Get:22 http://pl.archive.ubuntu.com trusty/universe Translation-en [4053 kB]
Feb  8 09:58:54 lubuntu in-target: Get:23 http://pl.archive.ubuntu.com trusty-updates/main Sources [14 B]
Feb  8 09:58:55 lubuntu in-target: Get:24 http://pl.archive.ubuntu.com trusty-updates/restricted Sources [14 B]
Feb  8 09:58:59 lubuntu in-target: Get:25 http://pl.archive.ubuntu.com trusty-updates/universe Sources [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:26 http://pl.archive.ubuntu.com trusty-updates/multiverse Sources [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:27 http://pl.archive.ubuntu.com trusty-updates/main amd64 Packages [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:28 http://pl.archive.ubuntu.com trusty-updates/restricted amd64 Packages [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:29 http://pl.archive.ubuntu.com trusty-updates/universe amd64 Packages [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:30 http://pl.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:31 http://pl.archive.ubuntu.com trusty-updates/main i386 Packages [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:32 http://pl.archive.ubuntu.com trusty-updates/restricted i386 Packages [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:33 http://pl.archive.ubuntu.com trusty-updates/universe i386 Packages [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:34 http://pl.archive.ubuntu.com trusty-updates/multiverse i386 Packages [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:35 http://pl.archive.ubuntu.com trusty-updates/main Translation-en [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:36 http://pl.archive.ubuntu.com trusty-updates/multiverse Translation-en [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:37 http://pl.archive.ubuntu.com trusty-updates/restricted Translation-en [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:38 http://pl.archive.ubuntu.com trusty-updates/universe Translation-en [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:39 http://pl.archive.ubuntu.com trusty-backports/main Sources [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:40 http://pl.archive.ubuntu.com trusty-backports/restricted Sources [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:41 http://pl.archive.ubuntu.com trusty-backports/universe Sources [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:42 http://pl.archive.ubuntu.com trusty-backports/multiverse Sources [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:43 http://pl.archive.ubuntu.com trusty-backports/main amd64 Packages [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:44 http://pl.archive.ubuntu.com trusty-backports/restricted amd64 Packages [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:45 http://pl.archive.ubuntu.com trusty-backports/universe amd64 Packages [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:46 http://pl.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:47 http://pl.archive.ubuntu.com trusty-backports/main i386 Packages [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:48 http://pl.archive.ubuntu.com trusty-backports/restricted i386 Packages [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:49 http://pl.archive.ubuntu.com trusty-backports/universe i386 Packages [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:50 http://pl.archive.ubuntu.com trusty-backports/multiverse i386 Packages [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:51 http://pl.archive.ubuntu.com trusty-backports/main Translation-en [14 B]
Feb  8 09:59:01 lubuntu in-target: Get:52 http://pl.archive.ubuntu.com trusty-backports/multiverse Translation-en [14 B]
Feb  8 09:59:02 lubuntu in-target: Get:53 http://pl.archive.ubuntu.com trusty-backports/restricted Translation-en [14 B]
Feb  8 09:59:08 lubuntu in-target: Get:54 http://pl.archive.ubuntu.com trusty-backports/universe Translation-en [14 B]
Feb  8 09:59:08 lubuntu in-target: Ign http://pl.archive.ubuntu.com trusty/main Translation-en_US
Feb  8 09:59:08 lubuntu in-target: Ign http://pl.archive.ubuntu.com trusty/multiverse Translation-en_US
Feb  8 09:59:08 lubuntu in-target: Ign http://pl.archive.ubuntu.com trusty/restricted Translation-en_US
Feb  8 09:59:08 lubuntu in-target: Ign http://pl.archive.ubuntu.com trusty/universe Translation-en_US
Feb  8 09:59:08 lubuntu in-target: Ign http://pl.archive.ubuntu.com trusty-updates/main Translation-en_US
Feb  8 09:59:08 lubuntu in-target: Ign http://pl.archive.ubuntu.com trusty-updates/multiverse Translation-en_US
Feb  8 09:59:08 lubuntu in-target: Ign http://pl.archive.ubuntu.com trusty-updates/restricted Translation-en_US
Feb  8 09:59:08 lubuntu in-target: Ign http://pl.archive.ubuntu.com trusty-updates/universe Translation-en_US
Feb  8 09:59:08 lubuntu in-target: Ign http://pl.archive.ubuntu.com trusty-backports/main Translation-en_US
Feb  8 09:59:08 lubuntu in-target: Ign http://pl.archive.ubuntu.com trusty-backports/multiverse Translation-en_US
Feb  8 09:59:08 lubuntu in-target: Ign http://pl.archive.ubuntu.com trusty-backports/restricted Translation-en_US
Feb  8 09:59:08 lubuntu in-target: Ign http://pl.archive.ubuntu.com trusty-backports/universe Translation-en_US
Feb  8 09:59:09 lubuntu in-target: Fetched 27,4 MB in 57s (473 kB/s)
Feb  8 09:59:09 lubuntu in-target: Reading package lists...
Feb  8 09:59:32 lubuntu in-target: 
Feb  8 09:59:34 lubuntu in-target: Reading package lists...
Feb  8 09:59:36 lubuntu in-target: 
Feb  8 09:59:38 lubuntu in-target: Reading package lists...
Feb  8 09:59:38 lubuntu in-target: 
Feb  8 09:59:41 lubuntu in-target: Ign http://security.ubuntu.com trusty-security InRelease
Feb  8 09:59:41 lubuntu in-target: Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Feb  8 09:59:41 lubuntu in-target: Get:2 http://security.ubuntu.com trusty-security Release [58,5 kB]
Feb  8 09:59:42 lubuntu in-target: Get:3 http://security.ubuntu.com trusty-security/main Sources [14 B]
Feb  8 09:59:42 lubuntu in-target: Get:4 http://security.ubuntu.com trusty-security/restricted Sources [14 B]
Feb  8 09:59:42 lubuntu in-target: Get:5 http://security.ubuntu.com trusty-security/universe Sources [14 B]
Feb  8 09:59:42 lubuntu in-target: Get:6 http://security.ubuntu.com trusty-security/multiverse Sources [14 B]
Feb  8 09:59:42 lubuntu in-target: Get:7 http://security.ubuntu.com trusty-security/main amd64 Packages [14 B]
Feb  8 09:59:42 lubuntu in-target: Get:8 http://security.ubuntu.com trusty-security/restricted amd64 Packages [14 B]
Feb  8 09:59:42 lubuntu in-target: Get:9 http://security.ubuntu.com trusty-security/universe amd64 Packages [14 B]
Feb  8 09:59:43 lubuntu in-target: Get:10 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [14 B]
Feb  8 09:59:43 lubuntu in-target: Get:11 http://security.ubuntu.com trusty-security/main i386 Packages [14 B]
Feb  8 09:59:43 lubuntu in-target: Get:12 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Feb  8 09:59:43 lubuntu in-target: Get:13 http://security.ubuntu.com trusty-security/universe i386 Packages [14 B]
Feb  8 09:59:43 lubuntu in-target: Get:14 http://security.ubuntu.com trusty-security/multiverse i386 Packages [14 B]
Feb  8 09:59:43 lubuntu in-target: Get:15 http://security.ubuntu.com trusty-security/main Translation-en [14 B]
Feb  8 09:59:43 lubuntu in-target: Get:16 http://security.ubuntu.com trusty-security/multiverse Translation-en [14 B]
Feb  8 09:59:44 lubuntu in-target: Get:17 http://security.ubuntu.com trusty-security/restricted Translation-en [14 B]
Feb  8 09:59:44 lubuntu in-target: Get:18 http://security.ubuntu.com trusty-security/universe Translation-en [14 B]
Feb  8 09:59:46 lubuntu in-target: Ign http://security.ubuntu.com trusty-security/main Translation-en_US
Feb  8 09:59:46 lubuntu in-target: Ign http://security.ubuntu.com trusty-security/multiverse Translation-en_US
Feb  8 09:59:46 lubuntu in-target: Ign http://security.ubuntu.com trusty-security/restricted Translation-en_US
Feb  8 09:59:46 lubuntu in-target: Ign http://security.ubuntu.com trusty-security/universe Translation-en_US
Feb  8 09:59:46 lubuntu in-target: Fetched 59,7 kB in 5s (10,2 kB/s)
Feb  8 09:59:46 lubuntu in-target: Reading package lists...
Feb  8 09:59:46 lubuntu in-target: 
Feb  8 09:59:49 lubuntu in-target: Reading package lists...
Feb  8 09:59:49 lubuntu in-target: 
Feb  8 09:59:52 lubuntu in-target: Ign http://extras.ubuntu.com trusty InRelease
Feb  8 09:59:52 lubuntu in-target: Get:1 http://extras.ubuntu.com trusty Release.gpg [72 B]
Feb  8 09:59:52 lubuntu in-target: Get:2 http://extras.ubuntu.com trusty Release [11,9 kB]
Feb  8 09:59:52 lubuntu in-target: Get:3 http://extras.ubuntu.com trusty/main Sources [14 B]
Feb  8 09:59:52 lubuntu in-target: Get:4 http://extras.ubuntu.com trusty/main amd64 Packages [14 B]
Feb  8 09:59:52 lubuntu in-target: Get:5 http://extras.ubuntu.com trusty/main i386 Packages [14 B]
Feb  8 09:59:53 lubuntu in-target: Ign http://extras.ubuntu.com trusty/main Translation-en_US
Feb  8 09:59:53 lubuntu in-target: Ign http://extras.ubuntu.com trusty/main Translation-en
Feb  8 09:59:53 lubuntu in-target: Fetched 12,0 kB in 0s (14,4 kB/s)
Feb  8 09:59:53 lubuntu in-target: Reading package lists...
Feb  8 09:59:53 lubuntu in-target: 
Feb  8 09:59:54 lubuntu clock-setup: hwclock from util-linux 2.20.1
Feb  8 09:59:54 lubuntu clock-setup: Using /dev interface to clock.
Feb  8 09:59:54 lubuntu clock-setup: Assuming hardware clock is kept in local time.
Feb  8 09:59:54 lubuntu clock-setup: Time elapsed since reference time has been 0.907990 seconds.
Feb  8 09:59:54 lubuntu clock-setup: Delaying further to reach the new time.
Feb  8 09:59:54 lubuntu clock-setup: Setting Hardware Clock to 10:59:54 = 1391853594 seconds since 1969
Feb  8 09:59:54 lubuntu clock-setup: ioctl(RTC_SET_TIME) was successful.
Feb  8 09:59:56 lubuntu user-setup: pwconv: failed to change the mode of /etc/passwd- to 0600
Feb  8 09:59:56 lubuntu user-setup: Shadow passwords are now on.
Feb  8 09:59:57 lubuntu user-setup: Adding user `euphoria' ...
Feb  8 09:59:57 lubuntu user-setup: Adding new group `euphoria' (1000) ...
Feb  8 09:59:57 lubuntu user-setup: Adding new user `euphoria' (1000) with group `euphoria' ...
Feb  8 09:59:57 lubuntu user-setup: Creating home directory `/home/euphoria' ...
Feb  8 09:59:57 lubuntu user-setup: Setting up encryption ...
Feb  8 09:59:57 lubuntu user-setup: stty: 
Feb  8 09:59:57 lubuntu user-setup: standard input
Feb  8 09:59:57 lubuntu user-setup: : Inappropriate ioctl for device
Feb  8 09:59:57 lubuntu user-setup: 
Feb  8 09:59:57 lubuntu user-setup: 
Feb  8 09:59:57 lubuntu user-setup: ************************************************************************
Feb  8 09:59:57 lubuntu user-setup: YOU SHOULD RECORD YOUR MOUNT PASSPHRASE AND STORE IT IN A SAFE LOCATION.
Feb  8 09:59:57 lubuntu user-setup:   ecryptfs-unwrap-passphrase ~/.ecryptfs/wrapped-passphrase
Feb  8 09:59:57 lubuntu user-setup: THIS WILL BE REQUIRED IF YOU NEED TO RECOVER YOUR DATA AT A LATER TIME.
Feb  8 09:59:57 lubuntu user-setup: ************************************************************************
Feb  8 09:59:57 lubuntu user-setup: 
Feb  8 09:59:58 lubuntu user-setup: 
Feb  8 09:59:58 lubuntu user-setup: Done configuring.
Feb  8 09:59:58 lubuntu user-setup: 
Feb  8 09:59:58 lubuntu user-setup: Copying files from `/etc/skel' ...
Feb  8 09:59:59 lubuntu user-setup: addgroup: 
Feb  8 09:59:59 lubuntu user-setup: The group `lpadmin' already exists as a system group. Exiting.
Feb  8 09:59:59 lubuntu user-setup: Adding group `sambashare' (GID 119) ...
Feb  8 10:00:02 lubuntu user-setup: Done.
Feb  8 10:00:02 lubuntu user-setup: Adding user `euphoria' to group `adm' ...
Feb  8 10:00:02 lubuntu user-setup: Adding user euphoria to group adm
Feb  8 10:00:02 lubuntu user-setup: Done.
Feb  8 10:00:02 lubuntu user-setup: Adding user `euphoria' to group `cdrom' ...
Feb  8 10:00:02 lubuntu user-setup: Adding user euphoria to group cdrom
Feb  8 10:00:02 lubuntu user-setup: Done.
Feb  8 10:00:02 lubuntu user-setup: Adding user `euphoria' to group `dip' ...
Feb  8 10:00:02 lubuntu user-setup: Adding user euphoria to group dip
Feb  8 10:00:02 lubuntu user-setup: Done.
Feb  8 10:00:02 lubuntu user-setup: Adding user `euphoria' to group `lpadmin' ...
Feb  8 10:00:03 lubuntu user-setup: Adding user euphoria to group lpadmin
Feb  8 10:00:03 lubuntu user-setup: Done.
Feb  8 10:00:03 lubuntu user-setup: Adding user `euphoria' to group `plugdev' ...
Feb  8 10:00:03 lubuntu user-setup: Adding user euphoria to group plugdev
Feb  8 10:00:03 lubuntu user-setup: Done.
Feb  8 10:00:03 lubuntu user-setup: Adding user `euphoria' to group `sambashare' ...
Feb  8 10:00:03 lubuntu user-setup: Adding user euphoria to group sambashare
Feb  8 10:00:03 lubuntu user-setup: Done.
Feb  8 10:00:03 lubuntu user-setup: adduser: The group `debian-tor' does not exist.
Feb  8 10:00:03 lubuntu user-setup: Adding user `euphoria' to group `sudo' ...
Feb  8 10:00:03 lubuntu user-setup: Adding user euphoria to group sudo
Feb  8 10:00:03 lubuntu user-setup: Done.
Feb  8 10:00:04 lubuntu ubiquity: sudo: unable to resolve host lubuntu
Feb  8 10:00:04 lubuntu ubiquity: open: Permission denied
Feb  8 10:00:04 lubuntu ubiquity: Error locking counter
Feb  8 10:00:04 lubuntu ubiquity: open: Permission denied
Feb  8 10:00:04 lubuntu ubiquity: Error locking counter
Feb  8 10:00:04 lubuntu ubiquity: sudo: unable to resolve host lubuntu
Feb  8 10:00:04 lubuntu ubiquity: open: Permission denied
Feb  8 10:00:04 lubuntu ubiquity: Error locking counter
Feb  8 10:00:04 lubuntu ubiquity: open: Permission denied
Feb  8 10:00:04 lubuntu ubiquity: Error locking counter
Feb  8 10:00:04 lubuntu /plugininstall.py: running /usr/lib/ubiquity/target-config/20xconfig
Feb  8 10:00:04 lubuntu /plugininstall.py: running /usr/lib/ubiquity/target-config/22gnome_panel_data
Feb  8 10:00:04 lubuntu /plugininstall.py: running /usr/lib/ubiquity/target-config/25modules
Feb  8 10:00:04 lubuntu /plugininstall.py: running /usr/lib/ubiquity/target-config/30accessibility
Feb  8 10:00:04 lubuntu /plugininstall.py: running /usr/lib/ubiquity/target-config/31ubuntu_driver_packages
Feb  8 10:00:04 lubuntu /plugininstall.py: running /usr/lib/ubiquity/target-config/32gnome_power_manager
Feb  8 10:00:04 lubuntu ubiquity: /usr/bin/casper-reconfigure: package 'gnome-power-manager' is not installed
Feb  8 10:00:04 lubuntu /plugininstall.py: running /usr/lib/ubiquity/target-config/40install_driver_updates
Feb  8 10:00:04 lubuntu /plugininstall.py: running /usr/lib/ubiquity/target-config/45jackd2
Feb  8 10:00:04 lubuntu /plugininstall.py: running /usr/lib/ubiquity/target-config/49kubuntu_gnome_icon_cache
Feb  8 10:00:04 lubuntu /plugininstall.py: running /usr/lib/ubiquity/target-config/50gkd-caps
Feb  8 10:00:04 lubuntu ubiquity: Setting capabilities for gnome-keyring-daemon using Linux Capabilities failed.
Feb  8 10:00:17 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target mount -t proc proc /proc
Feb  8 10:00:17 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Feb  8 10:00:17 lubuntu /plugininstall.py: log-output -t ubiquity mount --bind /dev /target/dev
Feb  8 10:00:17 lubuntu /plugininstall.py: log-output -t ubiquity mount --bind /run /target/run
Feb  8 10:00:17 lubuntu ubiquity: #0150% [Working]                                                                    
Feb  8 10:00:17 lubuntu ubiquity: #0150% [Connecting to pl.archive.ubuntu.com]                                        
Feb  8 10:00:17 lubuntu ubiquity: #0150% [Connecting to pl.archive.ubuntu.com (153.19.251.225)]                       
Feb  8 10:00:17 lubuntu ubiquity: #0150% [Waiting for headers]                                                        
Feb  8 10:00:17 lubuntu ubiquity: #015Get:1 http://pl.archive.ubuntu.com/ubuntu/ trusty/main hunspell-en-us all 20070829-4ubuntu3 [248 kB]
Feb  8 10:00:17 lubuntu ubiquity: #0150% [1 hunspell-en-us 1188 B/248 kB 0%]                                          
Feb  8 10:00:18 lubuntu ubiquity: #01517% [Working]                                                                   
Feb  8 10:00:18 lubuntu ubiquity: #01517% [Waiting for headers]                                                       
Feb  8 10:00:18 lubuntu ubiquity: #015Get:2 http://pl.archive.ubuntu.com/ubuntu/ trusty/universe sylpheed-i18n all 3.4.0~beta5-1ubuntu3 [672 kB]
Feb  8 10:00:18 lubuntu ubiquity: #01517% [2 sylpheed-i18n 0 B/672 kB 0%]                                             
Feb  8 10:00:18 lubuntu ubiquity: #01545% [2 sylpheed-i18n 408 kB/672 kB 60%]                                         
Feb  8 10:00:18 lubuntu ubiquity: #01563% [Working]                                                                   
Feb  8 10:00:18 lubuntu ubiquity: #01563% [Waiting for headers]                                                       
Feb  8 10:00:18 lubuntu ubiquity: #015Get:3 http://pl.archive.ubuntu.com/ubuntu/ trusty/main wamerican all 7.1-1 [269 kB]
Feb  8 10:00:18 lubuntu ubiquity: #01563% [3 wamerican 0 B/269 kB 0%]                                                 
Feb  8 10:00:19 lubuntu ubiquity: #01581% [Working]                                                                   
Feb  8 10:00:19 lubuntu ubiquity: #01581% [Waiting for headers]                                                       
Feb  8 10:00:19 lubuntu ubiquity: #015Get:4 http://pl.archive.ubuntu.com/ubuntu/ trusty/main wbritish all 7.1-1 [269 kB]
Feb  8 10:00:19 lubuntu ubiquity: #01581% [4 wbritish 0 B/269 kB 0%]                                                  
Feb  8 10:00:19 lubuntu ubiquity: #015100% [Working]                                                                  
Feb  8 10:00:19 lubuntu /plugininstall.py: Verifying downloads ...
Feb  8 10:00:20 lubuntu /plugininstall.py: Downloads verified successfully
Feb  8 10:00:21 lubuntu ubiquity: (Reading database ... 
Feb  8 10:00:21 lubuntu ubiquity: 132790 files and directories currently installed.)
Feb  8 10:00:21 lubuntu ubiquity: Preparing to replace language-pack-en 1:14.04+20140109 (using .../language-pack-en_1%3a14.04+20140206_all.deb) ...
Feb  8 10:00:21 lubuntu ubiquity: Unpacking replacement language-pack-en ...
Feb  8 10:00:21 lubuntu ubiquity: Replacing files in old package language-pack-en-base ...
Feb  8 10:00:23 lubuntu ubiquity: Preparing to replace language-pack-gnome-en 1:14.04+20140109 (using .../language-pack-gnome-en_1%3a14.04+20140206_all.deb) ...
Feb  8 10:00:23 lubuntu ubiquity: Unpacking replacement language-pack-gnome-en ...
Feb  8 10:00:23 lubuntu ubiquity: Replacing files in old package language-pack-gnome-en-base ...
Feb  8 10:00:25 lubuntu ubiquity: Preparing to replace sylpheed-plugins 3.4.0~beta5-1ubuntu1 (using .../sylpheed-plugins_3.4.0~beta5-1ubuntu3_amd64.deb) ...
Feb  8 10:00:25 lubuntu ubiquity: Unpacking replacement sylpheed-plugins ...
Feb  8 10:00:25 lubuntu ubiquity: Preparing to replace sylpheed 3.4.0~beta5-1ubuntu1 (using .../sylpheed_3.4.0~beta5-1ubuntu3_amd64.deb) ...
Feb  8 10:00:25 lubuntu ubiquity: Unpacking replacement sylpheed ...
Feb  8 10:00:26 lubuntu ubiquity: Selecting previously unselected package hunspell-en-us.
Feb  8 10:00:26 lubuntu ubiquity: Unpacking hunspell-en-us (from .../hunspell-en-us_20070829-4ubuntu3_all.deb) ...
Feb  8 10:00:27 lubuntu ubiquity: Preparing to replace sylpheed-i18n 3.4.0~beta5-1ubuntu1 (using .../sylpheed-i18n_3.4.0~beta5-1ubuntu3_all.deb) ...
Feb  8 10:00:27 lubuntu ubiquity: Unpacking replacement sylpheed-i18n ...
Feb  8 10:00:28 lubuntu ubiquity: Selecting previously unselected package wamerican.
Feb  8 10:00:28 lubuntu ubiquity: Unpacking wamerican (from .../wamerican_7.1-1_all.deb) ...
Feb  8 10:00:28 lubuntu ubiquity: Selecting previously unselected package wbritish.
Feb  8 10:00:28 lubuntu ubiquity: Unpacking wbritish (from .../wbritish_7.1-1_all.deb) ...
Feb  8 10:00:28 lubuntu ubiquity: Processing triggers for desktop-file-utils ...
Feb  8 10:00:29 lubuntu ubiquity: Processing triggers for mime-support ...
Feb  8 10:00:29 lubuntu ubiquity: Processing triggers for man-db ...
Feb  8 10:00:34 lubuntu ubiquity: Processing triggers for hicolor-icon-theme ...
Feb  8 10:00:49 lubuntu ubiquity: Setting up language-pack-en (1:14.04+20140206) ...
Feb  8 10:00:50 lubuntu ubiquity: Setting up language-pack-gnome-en (1:14.04+20140206) ...
Feb  8 10:00:50 lubuntu ubiquity: Setting up sylpheed (3.4.0~beta5-1ubuntu3) ...
Feb  8 10:00:50 lubuntu ubiquity: Setting up sylpheed-plugins (3.4.0~beta5-1ubuntu3) ...
Feb  8 10:00:50 lubuntu ubiquity: Setting up hunspell-en-us (20070829-4ubuntu3) ...
Feb  8 10:00:50 lubuntu ubiquity: Setting up sylpheed-i18n (3.4.0~beta5-1ubuntu3) ...
Feb  8 10:00:50 lubuntu ubiquity: Setting up wamerican (7.1-1) ...
Feb  8 10:00:55 lubuntu ubiquity: Setting up wbritish (7.1-1) ...
Feb  8 10:00:58 lubuntu ubiquity: Processing triggers for libc-bin ...
Feb  8 10:01:02 lubuntu ubiquity: Processing triggers for dictionaries-common ...
Feb  8 10:01:16 lubuntu dhclient: DHCPREQUEST of 172.16.1.105 on eth0 to 172.16.1.1 port 67 (xid=0x5696d477)
Feb  8 10:01:16 lubuntu dhclient: DHCPACK of 172.16.1.105 from 172.16.1.1
Feb  8 10:01:16 lubuntu NetworkManager[1365]: <info> (eth0): DHCPv4 state changed renew -> renew
Feb  8 10:01:16 lubuntu NetworkManager[1365]: <info>   address 172.16.1.105
Feb  8 10:01:16 lubuntu NetworkManager[1365]: <info>   prefix 24 (255.255.255.0)
Feb  8 10:01:16 lubuntu NetworkManager[1365]: <info>   gateway 172.16.1.1
Feb  8 10:01:16 lubuntu NetworkManager[1365]: <info>   hostname 'lubuntu'
Feb  8 10:01:16 lubuntu NetworkManager[1365]: <info>   nameserver '172.16.1.1'
Feb  8 10:01:16 lubuntu dbus[1026]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Feb  8 10:01:16 lubuntu dhclient: bound to 172.16.1.105 -- renewal in 1297 seconds.
Feb  8 10:01:16 lubuntu dbus[1026]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb  8 10:01:26 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /sys
Feb  8 10:01:26 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /proc
Feb  8 10:01:26 lubuntu /plugininstall.py: log-output -t ubiquity umount /target/run
Feb  8 10:01:26 lubuntu /plugininstall.py: log-output -t ubiquity umount /target/dev
Feb  8 10:01:29 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target mount -t proc proc /proc
Feb  8 10:01:29 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Feb  8 10:01:30 lubuntu /plugininstall.py: log-output -t ubiquity mount --bind /dev /target/dev
Feb  8 10:01:30 lubuntu /plugininstall.py: log-output -t ubiquity mount --bind /run /target/run
Feb  8 10:01:33 lubuntu check-missing-firmware: /dev/.udev/firmware-missing does not exist, skipping
Feb  8 10:01:33 lubuntu check-missing-firmware: /run/udev/firmware-missing does not exist, skipping
Feb  8 10:01:33 lubuntu check-missing-firmware: no missing firmware in /dev/.udev/firmware-missing /run/udev/firmware-missing
Feb  8 10:01:33 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /sys
Feb  8 10:01:33 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /proc
Feb  8 10:01:33 lubuntu /plugininstall.py: log-output -t ubiquity umount /target/run
Feb  8 10:01:33 lubuntu /plugininstall.py: log-output -t ubiquity umount /target/dev
Feb  8 10:01:33 lubuntu /plugininstall.py: log-output -t ubiquity /usr/lib/ubiquity/debian-installer-utils/register-module.post-base-installer
Feb  8 10:01:36 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target mount -t proc proc /proc
Feb  8 10:01:36 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Feb  8 10:01:36 lubuntu /plugininstall.py: log-output -t ubiquity mount --bind /dev /target/dev
Feb  8 10:01:36 lubuntu /plugininstall.py: log-output -t ubiquity mount --bind /run /target/run
Feb  8 10:01:36 lubuntu /plugininstall.py: log-output -t ubiquity mount --bind /tmp/.X11-unix /target/tmp/.X11-unix
Feb  8 10:01:36 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target dpkg-divert --package ubiquity --rename --quiet --add /usr/sbin/update-initramfs
Feb  8 10:01:40 lubuntu ubiquity: Running depmod.
Feb  8 10:01:40 lubuntu ubiquity: Failed to symbolic-link boot/initrd.img-3.13.0-1-generic to initrd.img:File exists at /var/lib/dpkg/info/linux-image-3.13.0-1-generic.postinst line 629.
Feb  8 10:01:46 lubuntu ubiquity: 
Feb  8 10:01:46 lubuntu ubiquity: Creating config file /etc/papersize with new version
Feb  8 10:01:47 lubuntu ubiquity: Processing triggers for libc-bin ...
Feb  8 10:01:53 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target dpkg-divert --package ubiquity --rename --quiet --remove /usr/sbin/update-initramfs
Feb  8 10:01:53 lubuntu ubiquity: update-initramfs: Generating /boot/initrd.img-3.13.0-1-generic
Feb  8 10:02:09 lubuntu ubiquity: cryptsetup: WARNING: target cryptswap1 has a random key, skipped
Feb  8 10:02:11 lubuntu ubiquity: W: Possible missing firmware /lib/firmware/radeon/HAWAII_smc.bin for module radeon
Feb  8 10:02:11 lubuntu ubiquity: W: Possible missing firmware /lib/firmware/radeon/HAWAII_sdma.bin for module radeon
Feb  8 10:02:11 lubuntu ubiquity: W: Possible missing firmware /lib/firmware/radeon/HAWAII_rlc.bin for module radeon
Feb  8 10:02:11 lubuntu ubiquity: W: Possible missing firmware /lib/firmware/radeon/HAWAII_mc.bin for module radeon
Feb  8 10:02:11 lubuntu ubiquity: W: Possible missing firmware /lib/firmware/radeon/HAWAII_mec.bin for module radeon
Feb  8 10:02:11 lubuntu ubiquity: W: Possible missing firmware /lib/firmware/radeon/HAWAII_ce.bin for module radeon
Feb  8 10:02:11 lubuntu ubiquity: W: Possible missing firmware /lib/firmware/radeon/HAWAII_me.bin for module radeon
Feb  8 10:02:11 lubuntu ubiquity: W: Possible missing firmware /lib/firmware/radeon/HAWAII_pfp.bin for module radeon
Feb  8 10:02:44 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target update-initramfs -c -k 3.13.0-1-generic
Feb  8 10:02:44 lubuntu /plugininstall.py: log-output -t ubiquity umount /target/tmp/.X11-unix
Feb  8 10:02:44 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /sys
Feb  8 10:02:44 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /proc
Feb  8 10:02:44 lubuntu /plugininstall.py: log-output -t ubiquity umount /target/run
Feb  8 10:02:44 lubuntu /plugininstall.py: log-output -t ubiquity umount /target/dev
Feb  8 10:02:47 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target mount -t proc proc /proc
Feb  8 10:02:47 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Feb  8 10:02:47 lubuntu /plugininstall.py: log-output -t ubiquity mount --bind /dev /target/dev
Feb  8 10:02:47 lubuntu /plugininstall.py: log-output -t ubiquity mount --bind /run /target/run
Feb  8 10:02:47 lubuntu /plugininstall.py: Verifying downloads ...
Feb  8 10:02:47 lubuntu /plugininstall.py: Downloads verified successfully
Feb  8 10:02:49 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /sys
Feb  8 10:02:49 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /proc
Feb  8 10:02:49 lubuntu /plugininstall.py: log-output -t ubiquity umount /target/run
Feb  8 10:02:49 lubuntu /plugininstall.py: log-output -t ubiquity umount /target/dev
Feb  8 10:02:49 lubuntu /plugininstall.py: log-output -t ubiquity mount --bind /proc /target/proc
Feb  8 10:02:49 lubuntu /plugininstall.py: log-output -t ubiquity mount --bind /sys /target/sys
Feb  8 10:02:49 lubuntu /plugininstall.py: log-output -t ubiquity mount --bind /dev /target/dev
Feb  8 10:02:49 lubuntu /plugininstall.py: log-output -t ubiquity mount --bind /run /target/run
Feb  8 10:02:49 lubuntu grub-installer: info: architecture: amd64/generic
Feb  8 10:02:50 lubuntu ubiquity: File descriptor 3 (pipe:[1323455]) leaked on lvdisplay invocation.
Feb  8 10:02:50 lubuntu ubiquity:  Parent PID 2804: /bin/sh
Feb  8 10:02:50 lubuntu ubiquity:   
Feb  8 10:02:50 lubuntu ubiquity: Volume group "sdb" not found
Feb  8 10:02:50 lubuntu ubiquity: 
Feb  8 10:02:50 lubuntu ubiquity:   
Feb  8 10:02:50 lubuntu ubiquity: Skipping volume group sdb
Feb  8 10:02:50 lubuntu ubiquity: 
Feb  8 10:02:50 lubuntu grub-installer: info: Identified partition label for /dev/sdb2: msdos
Feb  8 10:02:55 lubuntu grub-installer: dpkg: warning: ignoring request to remove grub which isn't installed
Feb  8 10:02:55 lubuntu grub-installer: dpkg: warning: ignoring request to remove grub-legacy which isn't installed
Feb  8 10:02:55 lubuntu grub-installer: dpkg: warning: ignoring request to remove grub-efi which isn't installed
Feb  8 10:02:55 lubuntu grub-installer: dpkg: warning: ignoring request to remove grub-efi-amd64-bin which isn't installed
Feb  8 10:02:55 lubuntu grub-installer: dpkg: warning: ignoring request to remove grub-efi-amd64 which isn't installed
Feb  8 10:02:55 lubuntu grub-installer: dpkg: warning: ignoring request to remove grub-efi-amd64-signed which isn't installed
Feb  8 10:02:55 lubuntu grub-installer: dpkg: warning: ignoring request to remove grub-efi-ia32-bin which isn't installed
Feb  8 10:02:55 lubuntu grub-installer: dpkg: warning: ignoring request to remove grub-efi-ia32 which isn't installed
Feb  8 10:02:55 lubuntu os-prober: File descriptor 3 (pipe:[1323455]) leaked on lvs invocation.
Feb  8 10:02:55 lubuntu os-prober:  Parent PID 2929: log-output
Feb  8 10:02:55 lubuntu os-prober:   
Feb  8 10:02:55 lubuntu os-prober: No volume groups found
Feb  8 10:02:55 lubuntu os-prober: 
Feb  8 10:02:55 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/05efi on mounted /dev/sda1
Feb  8 10:02:55 lubuntu 05efi: debug: Not on UEFI platform
Feb  8 10:02:55 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda1
Feb  8 10:02:55 lubuntu 10freedos: debug: /dev/sda1 is a FAT32 partition
Feb  8 10:02:55 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda1
Feb  8 10:02:55 lubuntu 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Feb  8 10:02:55 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda1
Feb  8 10:02:55 lubuntu macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Feb  8 10:02:55 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda1
Feb  8 10:02:55 lubuntu 20microsoft: debug: /dev/sda1 is a FAT32 partition
Feb  8 10:02:55 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda1
Feb  8 10:02:55 lubuntu 30utility: debug: /dev/sda1 is a FAT32 partition
Feb  8 10:02:56 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda1
Feb  8 10:02:56 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda1
Feb  8 10:02:56 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda1
Feb  8 10:02:56 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/83haiku on mounted /dev/sda1
Feb  8 10:02:56 lubuntu 83haiku: debug: /dev/sda1 is not a BeFS partition: exiting
Feb  8 10:02:56 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda1
Feb  8 10:02:56 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda1
Feb  8 10:02:56 lubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sdb1
Feb  8 10:02:56 lubuntu 50mounted-tests: debug: mounted using GRUB ntfs filesystem driver
Feb  8 10:02:56 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/05efi
Feb  8 10:02:56 lubuntu 05efi: debug: Not on UEFI platform
Feb  8 10:02:56 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Feb  8 10:02:56 lubuntu 10freedos: debug: /dev/sdb1 is not a FAT partition: exiting
Feb  8 10:02:56 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Feb  8 10:02:56 lubuntu 10qnx: debug: /dev/sdb1 is not a QNX4 partition: exiting
Feb  8 10:02:56 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Feb  8 10:02:56 lubuntu macosx-prober: debug: /dev/sdb1 is not an HFS+ partition: exiting
Feb  8 10:02:56 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Feb  8 10:02:56 lubuntu 20microsoft: debug: /dev/sdb1 is a NTFS partition
Feb  8 10:02:56 lubuntu 20microsoft: result: /dev/sdb1:Windows Recovery Environment (loader):Windows:chain
Feb  8 10:02:56 lubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
Feb  8 10:02:57 lubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Feb  8 10:02:57 lubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sdb3
Feb  8 10:02:57 lubuntu 50mounted-tests: debug: /dev/sdb3 type not recognised; skipping
Feb  8 10:02:57 lubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Feb  8 10:02:57 lubuntu grub-installer: info: Installing grub on '/dev/sdb'
Feb  8 10:02:58 lubuntu grub-installer: info: grub-install does not support --no-floppy
Feb  8 10:02:58 lubuntu grub-installer: info: Running chroot /target grub-install  --force "/dev/sdb"
Feb  8 10:03:00 lubuntu grub-installer: Installation finished. No error reported.
Feb  8 10:03:00 lubuntu grub-installer: 
Feb  8 10:03:00 lubuntu grub-installer: info: grub-install ran successfully
Feb  8 10:03:01 lubuntu ubiquity: Setting partition 2 of /dev/sdb to active... done.
Feb  8 10:03:10 lubuntu os-prober: File descriptor 3 (pipe:[1323455]) leaked on lvs invocation.
Feb  8 10:03:10 lubuntu os-prober:  Parent PID 4655: log-output
Feb  8 10:03:10 lubuntu os-prober:   
Feb  8 10:03:10 lubuntu os-prober: No volume groups found
Feb  8 10:03:10 lubuntu os-prober: 
Feb  8 10:03:11 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/05efi on mounted /dev/sda1
Feb  8 10:03:11 lubuntu 05efi: debug: Not on UEFI platform
Feb  8 10:03:11 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda1
Feb  8 10:03:11 lubuntu 10freedos: debug: /dev/sda1 is a FAT32 partition
Feb  8 10:03:11 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda1
Feb  8 10:03:11 lubuntu 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Feb  8 10:03:11 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda1
Feb  8 10:03:11 lubuntu macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Feb  8 10:03:11 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda1
Feb  8 10:03:11 lubuntu 20microsoft: debug: /dev/sda1 is a FAT32 partition
Feb  8 10:03:11 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda1
Feb  8 10:03:11 lubuntu 30utility: debug: /dev/sda1 is a FAT32 partition
Feb  8 10:03:11 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda1
Feb  8 10:03:11 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda1
Feb  8 10:03:11 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda1
Feb  8 10:03:11 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/83haiku on mounted /dev/sda1
Feb  8 10:03:11 lubuntu 83haiku: debug: /dev/sda1 is not a BeFS partition: exiting
Feb  8 10:03:11 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda1
Feb  8 10:03:11 lubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda1
Feb  8 10:03:11 lubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sdb1
Feb  8 10:03:11 lubuntu 50mounted-tests: debug: mounted using GRUB ntfs filesystem driver
Feb  8 10:03:11 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/05efi
Feb  8 10:03:11 lubuntu 05efi: debug: Not on UEFI platform
Feb  8 10:03:11 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Feb  8 10:03:11 lubuntu 10freedos: debug: /dev/sdb1 is not a FAT partition: exiting
Feb  8 10:03:11 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Feb  8 10:03:11 lubuntu 10qnx: debug: /dev/sdb1 is not a QNX4 partition: exiting
Feb  8 10:03:11 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Feb  8 10:03:11 lubuntu macosx-prober: debug: /dev/sdb1 is not an HFS+ partition: exiting
Feb  8 10:03:11 lubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Feb  8 10:03:11 lubuntu 20microsoft: debug: /dev/sdb1 is a NTFS partition
Feb  8 10:03:11 lubuntu 20microsoft: result: /dev/sdb1:Windows Recovery Environment (loader):Windows:chain
Feb  8 10:03:11 lubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
Feb  8 10:03:11 lubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Feb  8 10:03:11 lubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sdb3
Feb  8 10:03:11 lubuntu 50mounted-tests: debug: /dev/sdb3 type not recognised; skipping
Feb  8 10:03:11 lubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Feb  8 10:03:17 lubuntu /plugininstall.py: log-output -t ubiquity umount -f /target/proc
Feb  8 10:03:17 lubuntu /plugininstall.py: log-output -t ubiquity umount -f /target/sys
Feb  8 10:03:17 lubuntu /plugininstall.py: log-output -t ubiquity umount -f /target/dev
Feb  8 10:03:17 lubuntu /plugininstall.py: log-output -t ubiquity umount -f /target/run
Feb  8 10:03:58 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target mount -t proc proc /proc
Feb  8 10:03:59 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Feb  8 10:03:59 lubuntu /plugininstall.py: log-output -t ubiquity mount --bind /dev /target/dev
Feb  8 10:03:59 lubuntu /plugininstall.py: log-output -t ubiquity mount --bind /run /target/run
Feb  8 10:03:59 lubuntu ubiquity: (Reading database ... 
Feb  8 10:03:59 lubuntu ubiquity: 132811 files and directories currently installed.)
Feb  8 10:03:59 lubuntu ubiquity: Removing b43-fwcutter ...
Feb  8 10:03:59 lubuntu ubiquity: Purging configuration files for b43-fwcutter ...
Feb  8 10:04:03 lubuntu ubiquity: Removing pptp-linux ...
Feb  8 10:04:03 lubuntu ubiquity: Purging configuration files for pptp-linux ...
Feb  8 10:04:03 lubuntu ubiquity: Removing binutils ...
Feb  8 10:04:03 lubuntu ubiquity: Purging configuration files for binutils ...
Feb  8 10:04:04 lubuntu ubiquity: Removing lupin-casper ...
Feb  8 10:04:04 lubuntu ubiquity: Removing casper ...
Feb  8 10:04:04 lubuntu ubiquity: Purging configuration files for casper ...
Feb  8 10:04:04 lubuntu ubiquity: Removing cifs-utils ...
Feb  8 10:04:04 lubuntu ubiquity: Purging configuration files for cifs-utils ...
Feb  8 10:04:04 lubuntu ubiquity: Removing dmraid ...
Feb  8 10:04:05 lubuntu ubiquity: update-initramfs: deferring update (trigger activated)
Feb  8 10:04:05 lubuntu ubiquity: Purging configuration files for dmraid ...
Feb  8 10:04:05 lubuntu ubiquity: update-initramfs: deferring update (trigger activated)
Feb  8 10:04:05 lubuntu ubiquity: Removing feh ...
Feb  8 10:04:05 lubuntu ubiquity: Purging configuration files for feh ...
Feb  8 10:04:05 lubuntu ubiquity: Removing firefox-locale-bn ...
Feb  8 10:04:05 lubuntu ubiquity: Removing firefox-locale-cs ...
Feb  8 10:04:06 lubuntu ubiquity: Removing firefox-locale-de ...
Feb  8 10:04:06 lubuntu ubiquity: Removing firefox-locale-es ...
Feb  8 10:04:06 lubuntu ubiquity: Removing firefox-locale-fr ...
Feb  8 10:04:06 lubuntu ubiquity: Removing firefox-locale-hu ...
Feb  8 10:04:06 lubuntu ubiquity: Removing firefox-locale-it ...
Feb  8 10:04:06 lubuntu ubiquity: Removing firefox-locale-ja ...
Feb  8 10:04:07 lubuntu ubiquity: Removing firefox-locale-nl ...
Feb  8 10:04:07 lubuntu ubiquity: Removing firefox-locale-pl ...
Feb  8 10:04:07 lubuntu ubiquity: Removing firefox-locale-pt ...
Feb  8 10:04:07 lubuntu ubiquity: Removing firefox-locale-ru ...
Feb  8 10:04:07 lubuntu ubiquity: Removing firefox-locale-zh-hans ...
Feb  8 10:04:08 lubuntu ubiquity: Removing gparted ...
Feb  8 10:04:08 lubuntu ubiquity: Purging configuration files for gparted ...
Feb  8 10:04:08 lubuntu ubiquity: Removing kpartx-boot ...
Feb  8 10:04:08 lubuntu ubiquity: update-initramfs: deferring update (trigger activated)
Feb  8 10:04:08 lubuntu ubiquity: Purging configuration files for kpartx-boot ...
Feb  8 10:04:08 lubuntu ubiquity: Removing kpartx ...
Feb  8 10:04:10 lubuntu ubiquity: Removing libgtkmm-2.4-1c2a:amd64 ...
Feb  8 10:04:10 lubuntu ubiquity: Purging configuration files for libgtkmm-2.4-1c2a:amd64 ...
Feb  8 10:04:10 lubuntu ubiquity: Removing libatkmm-1.6-1:amd64 ...
Feb  8 10:04:10 lubuntu ubiquity: Purging configuration files for libatkmm-1.6-1:amd64 ...
Feb  8 10:04:10 lubuntu ubiquity: Removing libatm1:amd64 ...
Feb  8 10:04:10 lubuntu ubiquity: Purging configuration files for libatm1:amd64 ...
Feb  8 10:04:10 lubuntu ubiquity: Removing libpangomm-1.4-1:amd64 ...
Feb  8 10:04:11 lubuntu ubiquity: Purging configuration files for libpangomm-1.4-1:amd64 ...
Feb  8 10:04:11 lubuntu ubiquity: Removing libcairomm-1.0-1:amd64 ...
Feb  8 10:04:11 lubuntu ubiquity: Purging configuration files for libcairomm-1.0-1:amd64 ...
Feb  8 10:04:11 lubuntu ubiquity: Removing lvm2 ...
Feb  8 10:04:11 lubuntu ubiquity: Purging configuration files for lvm2 ...
Feb  8 10:04:12 lubuntu ubiquity: Removing libdevmapper-event1.02.1:amd64 ...
Feb  8 10:04:12 lubuntu ubiquity: Purging configuration files for libdevmapper-event1.02.1:amd64 ...
Feb  8 10:04:12 lubuntu ubiquity: Removing libdmraid1.0.0.rc16 ...
Feb  8 10:04:12 lubuntu ubiquity: Purging configuration files for libdmraid1.0.0.rc16 ...
Feb  8 10:04:12 lubuntu ubiquity: Removing libglibmm-2.4-1c2a:amd64 ...
Feb  8 10:04:12 lubuntu ubiquity: Purging configuration files for libglibmm-2.4-1c2a:amd64 ...
Feb  8 10:04:12 lubuntu ubiquity: Removing libjpeg-progs ...
Feb  8 10:04:13 lubuntu ubiquity: Removing libjpeg-turbo-progs ...
Feb  8 10:04:13 lubuntu ubiquity: Removing libsigc++-2.0-0c2a:amd64 ...
Feb  8 10:04:13 lubuntu ubiquity: Purging configuration files for libsigc++-2.0-0c2a:amd64 ...
Feb  8 10:04:13 lubuntu ubiquity: Removing linux-wlan-ng ...
Feb  8 10:04:13 lubuntu ubiquity: Purging configuration files for linux-wlan-ng ...
Feb  8 10:04:14 lubuntu ubiquity: Removing linux-wlan-ng-doc ...
Feb  8 10:04:14 lubuntu ubiquity: Removing localechooser-data ...
Feb  8 10:04:14 lubuntu ubiquity: Removing samba-common ...
Feb  8 10:04:14 lubuntu ubiquity: Purging configuration files for samba-common ...
Feb  8 10:04:26 lubuntu ubiquity: Removing setserial ...
Feb  8 10:04:27 lubuntu ubiquity: Purging configuration files for setserial ...
Feb  8 10:04:32 lubuntu ubiquity: Removing ubiquity-slideshow-lubuntu ...
Feb  8 10:04:32 lubuntu ubiquity: Removing user-setup ...
Feb  8 10:04:32 lubuntu ubiquity: Purging configuration files for user-setup ...
Feb  8 10:04:35 lubuntu ubiquity: Removing watershed ...
Feb  8 10:04:35 lubuntu ubiquity: Removing zram-config ...
Feb  8 10:04:35 lubuntu ubiquity: invoke-rc.d: policy-rc.d denied execution of stop.
Feb  8 10:04:35 lubuntu ubiquity: 
Feb  8 10:04:35 lubuntu ubiquity: Warning: Fake initctl called, doing nothing.
Feb  8 10:04:35 lubuntu ubiquity: Purging configuration files for zram-config ...
Feb  8 10:04:42 lubuntu ubiquity: Removing language-pack-gnome-bn-base ...
Feb  8 10:04:42 lubuntu ubiquity: Purging configuration files for language-pack-gnome-bn-base ...
Feb  8 10:04:42 lubuntu ubiquity: Removing language-pack-bn-base ...
Feb  8 10:04:42 lubuntu ubiquity: Purging configuration files for language-pack-bn-base ...
Feb  8 10:04:42 lubuntu ubiquity: Removing language-pack-gnome-cs-base ...
Feb  8 10:04:43 lubuntu ubiquity: Purging configuration files for language-pack-gnome-cs-base ...
Feb  8 10:04:43 lubuntu ubiquity: Removing language-pack-cs-base ...
Feb  8 10:04:43 lubuntu ubiquity: Purging configuration files for language-pack-cs-base ...
Feb  8 10:04:44 lubuntu ubiquity: Removing language-pack-gnome-de-base ...
Feb  8 10:04:44 lubuntu ubiquity: Purging configuration files for language-pack-gnome-de-base ...
Feb  8 10:04:44 lubuntu ubiquity: Removing language-pack-de-base ...
Feb  8 10:04:45 lubuntu ubiquity: Purging configuration files for language-pack-de-base ...
Feb  8 10:04:45 lubuntu ubiquity: Removing language-pack-gnome-es-base ...
Feb  8 10:04:45 lubuntu ubiquity: Purging configuration files for language-pack-gnome-es-base ...
Feb  8 10:04:45 lubuntu ubiquity: Removing language-pack-es-base ...
Feb  8 10:04:46 lubuntu ubiquity: Purging configuration files for language-pack-es-base ...
Feb  8 10:04:46 lubuntu ubiquity: Removing language-pack-gnome-fr-base ...
Feb  8 10:04:46 lubuntu ubiquity: Purging configuration files for language-pack-gnome-fr-base ...
Feb  8 10:04:46 lubuntu ubiquity: Removing language-pack-fr-base ...
Feb  8 10:04:47 lubuntu ubiquity: Purging configuration files for language-pack-fr-base ...
Feb  8 10:04:47 lubuntu ubiquity: Removing language-pack-gnome-hu-base ...
Feb  8 10:04:47 lubuntu ubiquity: Purging configuration files for language-pack-gnome-hu-base ...
Feb  8 10:04:47 lubuntu ubiquity: Removing language-pack-gnome-it-base ...
Feb  8 10:04:48 lubuntu ubiquity: Purging configuration files for language-pack-gnome-it-base ...
Feb  8 10:04:48 lubuntu ubiquity: Removing language-pack-gnome-ja-base ...
Feb  8 10:04:48 lubuntu ubiquity: Purging configuration files for language-pack-gnome-ja-base ...
Feb  8 10:04:48 lubuntu ubiquity: Removing language-pack-gnome-nl-base ...
Feb  8 10:04:48 lubuntu ubiquity: Purging configuration files for language-pack-gnome-nl-base ...
Feb  8 10:04:48 lubuntu ubiquity: Removing language-pack-gnome-pl-base ...
Feb  8 10:04:49 lubuntu ubiquity: Purging configuration files for language-pack-gnome-pl-base ...
Feb  8 10:04:49 lubuntu ubiquity: Removing language-pack-gnome-pt-base ...
Feb  8 10:04:49 lubuntu ubiquity: Purging configuration files for language-pack-gnome-pt-base ...
Feb  8 10:04:49 lubuntu ubiquity: Removing language-pack-gnome-ru-base ...
Feb  8 10:04:49 lubuntu ubiquity: Purging configuration files for language-pack-gnome-ru-base ...
Feb  8 10:04:49 lubuntu ubiquity: Removing language-pack-gnome-xh-base ...
Feb  8 10:04:50 lubuntu ubiquity: Purging configuration files for language-pack-gnome-xh-base ...
Feb  8 10:04:50 lubuntu ubiquity: Removing language-pack-gnome-zh-hans-base ...
Feb  8 10:04:50 lubuntu ubiquity: Purging configuration files for language-pack-gnome-zh-hans-base ...
Feb  8 10:04:50 lubuntu ubiquity: Removing language-pack-hu-base ...
Feb  8 10:04:51 lubuntu ubiquity: Purging configuration files for language-pack-hu-base ...
Feb  8 10:04:51 lubuntu ubiquity: Removing language-pack-it-base ...
Feb  8 10:04:51 lubuntu ubiquity: Purging configuration files for language-pack-it-base ...
Feb  8 10:04:51 lubuntu ubiquity: Removing language-pack-ja-base ...
Feb  8 10:04:51 lubuntu ubiquity: Purging configuration files for language-pack-ja-base ...
Feb  8 10:04:52 lubuntu ubiquity: Removing language-pack-nl-base ...
Feb  8 10:04:52 lubuntu ubiquity: Purging configuration files for language-pack-nl-base ...
Feb  8 10:04:52 lubuntu ubiquity: Removing language-pack-pl-base ...
Feb  8 10:04:52 lubuntu ubiquity: Purging configuration files for language-pack-pl-base ...
Feb  8 10:04:52 lubuntu ubiquity: Removing language-pack-pt-base ...
Feb  8 10:04:53 lubuntu ubiquity: Purging configuration files for language-pack-pt-base ...
Feb  8 10:04:53 lubuntu ubiquity: Removing language-pack-ru-base ...
Feb  8 10:04:53 lubuntu ubiquity: Purging configuration files for language-pack-ru-base ...
Feb  8 10:04:53 lubuntu ubiquity: Removing language-pack-xh-base ...
Feb  8 10:04:53 lubuntu ubiquity: Purging configuration files for language-pack-xh-base ...
Feb  8 10:04:54 lubuntu ubiquity: Removing language-pack-zh-hans-base ...
Feb  8 10:04:54 lubuntu ubiquity: Purging configuration files for language-pack-zh-hans-base ...
Feb  8 10:04:54 lubuntu ubiquity: Removing language-pack-gnome-bn ...
Feb  8 10:04:55 lubuntu ubiquity: Removing language-pack-bn ...
Feb  8 10:04:55 lubuntu ubiquity: Removing language-pack-gnome-cs ...
Feb  8 10:04:55 lubuntu ubiquity: Removing language-pack-cs ...
Feb  8 10:04:55 lubuntu ubiquity: Removing language-pack-gnome-de ...
Feb  8 10:04:55 lubuntu ubiquity: Removing language-pack-de ...
Feb  8 10:05:03 lubuntu ubiquity: Removing language-pack-gnome-es ...
Feb  8 10:05:04 lubuntu ubiquity: Removing language-pack-es ...
Feb  8 10:05:04 lubuntu ubiquity: Removing language-pack-gnome-fr ...
Feb  8 10:05:04 lubuntu ubiquity: Removing language-pack-fr ...
Feb  8 10:05:04 lubuntu ubiquity: Removing language-pack-gnome-hu ...
Feb  8 10:05:04 lubuntu ubiquity: Removing language-pack-gnome-it ...
Feb  8 10:05:05 lubuntu ubiquity: Removing language-pack-gnome-ja ...
Feb  8 10:05:05 lubuntu ubiquity: Removing language-pack-gnome-nl ...
Feb  8 10:05:05 lubuntu ubiquity: Removing language-pack-gnome-pl ...
Feb  8 10:05:05 lubuntu ubiquity: Removing language-pack-gnome-pt ...
Feb  8 10:05:08 lubuntu ubiquity: Removing language-pack-gnome-ru ...
Feb  8 10:05:08 lubuntu ubiquity: Removing language-pack-gnome-xh ...
Feb  8 10:05:08 lubuntu ubiquity: Removing language-pack-gnome-zh-hans ...
Feb  8 10:05:08 lubuntu ubiquity: Removing language-pack-hu ...
Feb  8 10:05:09 lubuntu ubiquity: Removing language-pack-it ...
Feb  8 10:05:09 lubuntu ubiquity: Removing language-pack-ja ...
Feb  8 10:05:09 lubuntu ubiquity: Removing language-pack-nl ...
Feb  8 10:05:09 lubuntu ubiquity: Removing language-pack-pl ...
Feb  8 10:05:09 lubuntu ubiquity: Removing language-pack-pt ...
Feb  8 10:05:10 lubuntu ubiquity: Removing language-pack-ru ...
Feb  8 10:05:10 lubuntu ubiquity: Removing language-pack-xh ...
Feb  8 10:05:10 lubuntu ubiquity: Removing language-pack-zh-hans ...
Feb  8 10:05:11 lubuntu ubiquity: Removing ubiquity ...
Feb  8 10:05:11 lubuntu ubiquity: Purging configuration files for ubiquity ...
Feb  8 10:05:14 lubuntu ubiquity: Removing ubiquity-frontend-gtk ...
Feb  8 10:05:15 lubuntu ubiquity: Purging configuration files for ubiquity-frontend-gtk ...
Feb  8 10:05:15 lubuntu ubiquity: Removing apt-clone ...
Feb  8 10:05:15 lubuntu ubiquity: Removing archdetect-deb ...
Feb  8 10:05:15 lubuntu ubiquity: Removing dpkg-repack ...
Feb  8 10:05:16 lubuntu ubiquity: Removing gir1.2-appindicator3-0.1 ...
Feb  8 10:05:16 lubuntu ubiquity: Removing gir1.2-timezonemap-1.0 ...
Feb  8 10:05:16 lubuntu ubiquity: Removing gir1.2-json-1.0 ...
Feb  8 10:05:16 lubuntu ubiquity: Removing gir1.2-xkl-1.0 ...
Feb  8 10:05:16 lubuntu ubiquity: Removing ubiquity-casper ...
Feb  8 10:05:17 lubuntu ubiquity: Removing laptop-detect ...
Feb  8 10:05:17 lubuntu ubiquity: Removing libdebian-installer4:amd64 ...
Feb  8 10:05:17 lubuntu ubiquity: Purging configuration files for libdebian-installer4:amd64 ...
Feb  8 10:05:17 lubuntu ubiquity: Removing libido3-0.1-0:amd64 ...
Feb  8 10:05:17 lubuntu ubiquity: Purging configuration files for libido3-0.1-0:amd64 ...
Feb  8 10:05:17 lubuntu ubiquity: Removing python3-gi-cairo ...
Feb  8 10:05:18 lubuntu ubiquity: Purging configuration files for python3-gi-cairo ...
Feb  8 10:05:18 lubuntu ubiquity: Removing python3-cairo ...
Feb  8 10:05:18 lubuntu ubiquity: Removing libpython3.4:amd64 ...
Feb  8 10:05:18 lubuntu ubiquity: Purging configuration files for libpython3.4:amd64 ...
Feb  8 10:05:18 lubuntu ubiquity: Removing libpython3.4-stdlib:amd64 ...
Feb  8 10:05:19 lubuntu ubiquity: dpkg-query: no packages found matching pkgname
Feb  8 10:05:19 lubuntu ubiquity: Removing libmpdec2:amd64 ...
Feb  8 10:05:19 lubuntu ubiquity: Purging configuration files for libmpdec2:amd64 ...
Feb  8 10:05:19 lubuntu ubiquity: Removing libpython3.3:amd64 ...
Feb  8 10:05:20 lubuntu ubiquity: Purging configuration files for libpython3.3:amd64 ...
Feb  8 10:05:20 lubuntu ubiquity: Removing libpython3.4-minimal:amd64 ...
Feb  8 10:05:20 lubuntu ubiquity: dpkg-query: no packages found matching pkgname
Feb  8 10:05:20 lubuntu ubiquity: Purging configuration files for libpython3.4-minimal:amd64 ...
Feb  8 10:05:20 lubuntu ubiquity: dpkg-query: no packages found matching pkgname
Feb  8 10:05:20 lubuntu ubiquity: Removing libtimezonemap1 ...
Feb  8 10:05:20 lubuntu ubiquity: Purging configuration files for libtimezonemap1 ...
Feb  8 10:05:21 lubuntu ubiquity: Removing python3-icu ...
Feb  8 10:05:21 lubuntu ubiquity: Removing python3-pam ...
Feb  8 10:05:21 lubuntu ubiquity: Removing rdate ...
Feb  8 10:05:21 lubuntu ubiquity: Removing sbsigntool ...
Feb  8 10:05:22 lubuntu ubiquity: Removing ubiquity-ubuntu-artwork ...
Feb  8 10:05:22 lubuntu ubiquity: Processing triggers for libc-bin ...
Feb  8 10:05:22 lubuntu ubiquity: Processing triggers for initramfs-tools ...
Feb  8 10:05:22 lubuntu ubiquity: update-initramfs: Generating /boot/initrd.img-3.13.0-1-generic
Feb  8 10:05:39 lubuntu ubiquity: cryptsetup: WARNING: target cryptswap1 has a random key, skipped
Feb  8 10:05:40 lubuntu ubiquity: W: Possible missing firmware /lib/firmware/radeon/HAWAII_smc.bin for module radeon
Feb  8 10:05:40 lubuntu ubiquity: W: Possible missing firmware /lib/firmware/radeon/HAWAII_sdma.bin for module radeon
Feb  8 10:05:40 lubuntu ubiquity: W: Possible missing firmware /lib/firmware/radeon/HAWAII_rlc.bin for module radeon
Feb  8 10:05:40 lubuntu ubiquity: W: Possible missing firmware /lib/firmware/radeon/HAWAII_mc.bin for module radeon
Feb  8 10:05:40 lubuntu ubiquity: W: Possible missing firmware /lib/firmware/radeon/HAWAII_mec.bin for module radeon
Feb  8 10:05:40 lubuntu ubiquity: W: Possible missing firmware /lib/firmware/radeon/HAWAII_ce.bin for module radeon
Feb  8 10:05:40 lubuntu ubiquity: W: Possible missing firmware /lib/firmware/radeon/HAWAII_me.bin for module radeon
Feb  8 10:05:40 lubuntu ubiquity: W: Possible missing firmware /lib/firmware/radeon/HAWAII_pfp.bin for module radeon
Feb  8 10:06:59 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /sys
Feb  8 10:06:59 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /proc
Feb  8 10:06:59 lubuntu /plugininstall.py: log-output -t ubiquity umount /target/run
Feb  8 10:06:59 lubuntu /plugininstall.py: log-output -t ubiquity umount /target/dev
Feb  8 10:07:01 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target mount -t proc proc /proc
Feb  8 10:07:01 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Feb  8 10:07:01 lubuntu /plugininstall.py: log-output -t ubiquity mount --bind /dev /target/dev
Feb  8 10:07:01 lubuntu /plugininstall.py: log-output -t ubiquity mount --bind /run /target/run
Feb  8 10:07:09 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /sys
Feb  8 10:07:10 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /proc
Feb  8 10:07:10 lubuntu /plugininstall.py: log-output -t ubiquity umount /target/run
Feb  8 10:07:10 lubuntu /plugininstall.py: log-output -t ubiquity umount /target/dev
Feb  8 10:07:13 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target mount -t proc proc /proc
Feb  8 10:07:13 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Feb  8 10:07:13 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target mount -t securityfs securityfs /sys/kernel/security
Feb  8 10:07:13 lubuntu ubiquity:  * Recaching AppArmor profiles
Feb  8 10:07:14 lubuntu ubiquity: Warning from /etc/apparmor.d/lightdm-guest-session (/etc/apparmor.d/lightdm-guest-session line 13): profile /usr/lib/lightdm/lightdm-guest-session dbus rules not enforced
Feb  8 10:07:14 lubuntu ubiquity: Warning from /etc/apparmor.d/lightdm-guest-session (/etc/apparmor.d/lightdm-guest-session line 13): profile chromium_browser dbus rules not enforced
Feb  8 10:07:14 lubuntu ubiquity: Warning from /etc/apparmor.d/lightdm-guest-session (/etc/apparmor.d/lightdm-guest-session line 13): profile /usr/lib/lightdm/lightdm-guest-session network rules not enforced
Feb  8 10:07:14 lubuntu ubiquity: Warning from /etc/apparmor.d/lightdm-guest-session (/etc/apparmor.d/lightdm-guest-session line 13): profile chromium_browser network rules not enforced
Feb  8 10:07:15 lubuntu ubiquity: Warning from /etc/apparmor.d/sbin.dhclient (/etc/apparmor.d/sbin.dhclient line 79): profile /usr/lib/NetworkManager/nm-dhcp-client.action dbus rules not enforced
Feb  8 10:07:15 lubuntu ubiquity: Warning from /etc/apparmor.d/sbin.dhclient (/etc/apparmor.d/sbin.dhclient line 79): profile /usr/lib/connman/scripts/dhclient-script dbus rules not enforced
Feb  8 10:07:15 lubuntu ubiquity: Warning from /etc/apparmor.d/sbin.dhclient (/etc/apparmor.d/sbin.dhclient line 79): profile /sbin/dhclient network rules not enforced
Feb  8 10:07:32 lubuntu ubiquity: Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 169): profile /usr/bin/evince dbus rules not enforced
Feb  8 10:07:32 lubuntu ubiquity: Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 169): profile sanitized_helper dbus rules not enforced
Feb  8 10:07:32 lubuntu ubiquity: Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 169): profile /usr/bin/evince-previewer dbus rules not enforced
Feb  8 10:07:32 lubuntu ubiquity: Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 169): profile sanitized_helper dbus rules not enforced
Feb  8 10:07:32 lubuntu ubiquity: Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 169): profile /usr/bin/evince-thumbnailer dbus rules not enforced
Feb  8 10:07:32 lubuntu ubiquity: Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 169): profile sanitized_helper dbus rules not enforced
Feb  8 10:07:32 lubuntu ubiquity: Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 169): profile /usr/bin/evince network rules not enforced
Feb  8 10:07:32 lubuntu ubiquity: Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 169): profile sanitized_helper network rules not enforced
Feb  8 10:07:32 lubuntu ubiquity: Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 169): profile /usr/bin/evince-previewer network rules not enforced
Feb  8 10:07:32 lubuntu ubiquity: Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 169): profile sanitized_helper network rules not enforced
Feb  8 10:07:32 lubuntu ubiquity: Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 169): profile /usr/bin/evince-thumbnailer network rules not enforced
Feb  8 10:07:32 lubuntu ubiquity: Warning from /etc/apparmor.d/usr.bin.evince (/etc/apparmor.d/usr.bin.evince line 169): profile sanitized_helper network rules not enforced
Feb  8 10:07:32 lubuntu ubiquity: Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Feb  8 10:07:34 lubuntu ubiquity: Warning from /etc/apparmor.d/usr.sbin.cupsd (/etc/apparmor.d/usr.sbin.cupsd line 180): profile /usr/sbin/cupsd dbus rules not enforced
Feb  8 10:07:34 lubuntu ubiquity: Warning from /etc/apparmor.d/usr.sbin.cupsd (/etc/apparmor.d/usr.sbin.cupsd line 180): profile /usr/lib/cups/backend/cups-pdf network rules not enforced
Feb  8 10:07:34 lubuntu ubiquity: Warning from /etc/apparmor.d/usr.sbin.cupsd (/etc/apparmor.d/usr.sbin.cupsd line 180): profile /usr/sbin/cupsd network rules not enforced
Feb  8 10:07:34 lubuntu ubiquity: Warning from /etc/apparmor.d/usr.sbin.ntpd (/etc/apparmor.d/usr.sbin.ntpd line 82): profile /usr/sbin/ntpd network rules not enforced
Feb  8 10:07:34 lubuntu ubiquity: Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
Feb  8 10:07:35 lubuntu ubiquity: Warning from /etc/apparmor.d/usr.sbin.tcpdump (/etc/apparmor.d/usr.sbin.tcpdump line 64): profile /usr/sbin/tcpdump network rules not enforced
Feb  8 10:07:35 lubuntu ubiquity:    ...done.
Feb  8 10:07:35 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target /etc/init.d/apparmor recache
Feb  8 10:07:35 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /proc
Feb  8 10:07:35 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /sys/kernel/security
Feb  8 10:07:35 lubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /sys


```
**_Version_**
```
ubiquity 2.17.3
```

---

### Post by sudodus on 2014-02-08
Welcome to the Ubuntu Forums :-)

Lubuntu 14.04 has two more months of development until it will be released. You can expect many things to break during this interval. You can help the developers make it work with your hardware, if you report your results at the testing tracker

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds)

and write a bug report at Launchpad

[https://launchpad.net/](https://launchpad.net/)

-o-

If you need a working system, I suggest that you install the current released version, Lubuntu 13.10.

---

### Post by Elfy on 2014-02-08
*Thread moved to **Ubuntu +1**.*

---

### Post by e71067 on 2014-02-08
Im eager to be a part of free open source software so im willing to report all bugs i encounter for the win! :D

however i dont know exactly how to use launchpad to do that, ive tried the openid button but it loads forever


any help with the install?

---

### Post by sudodus on 2014-02-08
You need to create a user id at Launchpad

[https://help.launchpad.net/YourAccount/NewAccount](https://help.launchpad.net/YourAccount/NewAccount)

Good luck :-D

---

### Post by e71067 on 2014-02-08
ok i just did and there is no eror reporting for lubuntu. only for its artwork.

so where do i submit (plz post link url if you can)

---

### Post by grahammechanical on 2014-02-08
Please describe what you mean by 'wont boot.' Describe what appears on the screen.

I see many posts in different sections of this forum that basically say the same thing. "I installed. It went successfully. On reboot it did not boot." This happens on different versions of Ubuntu and not just Trusty Tahr.

It could be a standard buggy proprietary video driver problem. I never install and tick "install third party software." That brings in a proprietary video driver. In my opinion proprietary video drivers should not be installed with other third party software. Then we would not see problems like this.

As a tester you now have an opportunity to become familiar with Recovery Mode. It is under the Advanced Options sub-menu. Select Resume and if that gets you to a desktop then experiment with different video drivers.

When using the development branch then a combination of upgraded Linux kernel, Xserver and video driver can (and sometimes does) break the boot process. We sometimes have to use an earlier kernel. They are again under Advanced Options.

We can use Recovery mode + Network + Root to update/upgrade. The other month doing that for a few days fixed a buggy library (pixbuf) that broke the loading process on one of my Trusty Tahr installs.

The boot process can break at different points. Is it Grub? Is it Xserver? Is it LightDM? Is it Compiz? Is it Unity? Or in your case, is it something specific to LXDE?

Insufficient information.

Regards.

---

