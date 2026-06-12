---
title: "Natty Narwhal 11.04 Clean Install Problems"
date: 2011-05-01
forum: System76 Support
---

### Post by jpelorat on 2011-05-01
Hi Every one,

I just finished a clean install of the Kubuntu 11.04 on my panp5. Every thing went smooth with the exception of the System76 Driver. 

After getting the app. from the repository (including key + sources.list) I proceeded to execute the application and this what I've got: 

[INDENT]bliss:~$ system76-driver 
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/sgonzale/.config/ibus/bus

(System76Driver.py:18741): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(System76Driver.py:18741): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(System76Driver.py:18741): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(System76Driver.py:18741): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(System76Driver.py:18741): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(System76Driver.py:18741): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(System76Driver.py:18741): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(System76Driver.py:18741): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(System76Driver.py:18741): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(System76Driver.py:18741): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(System76Driver.py:18741): libglade-WARNING **: unknown attribute `swapped' for <signal>.
Traceback (most recent call last):
  File "/opt/system76/system76-driver/src/System76Driver.py", line 277, in <module>
    supported(datadir)
  File "/opt/system76/system76-driver/src/System76Driver.py", line 137, in supported
    ui = System76Driver(datadir)
  File "/opt/system76/system76-driver/src/System76Driver.py", line 152, in __init__
    self.icon = gtk.gdk.pixbuf_new_from_file(os.path.join(WINDOW_ICON))
glib.G Error: Couldn't recognize the image file format for file '/opt/system76/system76-driver/src/images/76icon.svg'
sh: gksu: not found

[/INDENT]Also tried installing the gksu and the result was the same. No System76 Driver application running. I also tried this way:

[INDENT]bliss:~$ sudo system76-driver 
[sudo] password for sgonzale: 
Traceback (most recent call last):
  File "/usr/bin/system76-driver", line 50, in <module>
    main()
  File "/usr/bin/system76-driver", line 44, in main
    os.environ['GDMSESSION'] == 'default'
  File "/usr/lib/python2.7/UserDict.py", line 23, in __getitem__
    raise KeyError(key)
KeyError: 'GDMSESSION'

[/INDENT]Any suggestions or ideas?

Thanks in advance,
Ziggy :-)

---

### Post by isantop on 2011-05-02
Try purging and reinstalling the driver. Use these commands:

```
sudo apt-get remove --purge system76-driver
sudo apt-get update
sudo apt-get clean
sudo apt-get install system76-driver
```

---

### Post by jpelorat on 2011-05-02
Thanks isantop,

I did what you suggested but the problem persist. I even did a "rm -rf /opt/system76" and purged python-gconf, python-glade2, python-gnome2, python-gnomecanvas and python-pyorbit (the full dependencies) after purging system76-driver, just in case.

The fun thing is that in Kubuntu 10.10 the same version of system76-driver worked like a charm. I almost have the same list of packages installed.

Cheers,
Ziggy :-)

---

### Post by isantop on 2011-05-05
Can you try installing and using GDM to see if that helps it out? I can't see an issue with using KDM, but it will help to rule out all possibilities.

---

### Post by jpelorat on 2011-05-06
Hi,

No luck with GDM nor GDM + gksu and the new version of the driver released by System76.

Ziggy :-)

---

### Post by isantop on 2011-05-06
Have you run the driver without using sudo or gksu(do)? It will gain the needed permissions and prompt you for any required password itself, and running it with sudo will cause errors.

---

### Post by jpelorat on 2011-05-06
Hi,
[B]
It was the first thing I reported.[/B][INDENT]sgonzale@bliss:~$ system76-driver 
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/sgonzale/.config/ibus/bus

[/INDENT]**And the KDESUDO dialog appears. Then when I write my user password I get the rest of the message.**
[INDENT](System76Driver.py:15883): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(System76Driver.py:15883): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(System76Driver.py:15883): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(System76Driver.py:15883): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(System76Driver.py:15883): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(System76Driver.py:15883): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(System76Driver.py:15883): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(System76Driver.py:15883): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(System76Driver.py:15883): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(System76Driver.py:15883): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(System76Driver.py:15883): libglade-WARNING **: unknown attribute `swapped' for <signal>.
Traceback (most recent call last):
  File "/opt/system76/system76-driver/src/System76Driver.py", line 277, in <module>
    supported(datadir)
  File "/opt/system76/system76-driver/src/System76Driver.py", line 137, in supported
    ui = System76Driver(datadir)
  File "/opt/system76/system76-driver/src/System76Driver.py", line 152, in __init__
    self.icon = gtk.gdk.pixbuf_new_from_file(os.path.join(WINDOW_ICON))
glib.GError: Couldn't recognize the image file format for file '/opt/system76/system76-driver/src/images/76icon.svg'
sh: gksu: not found

[/INDENT][B]Then no System76 dialog and I get the console control back.

Regards,[/B] [B]
Ziggy :-)[/B]

---

### Post by jpelorat on 2011-06-02
Hi...

With the version 2.6.6 of the system76-driver everything is working fine.

Regards,
Sigi...

---

