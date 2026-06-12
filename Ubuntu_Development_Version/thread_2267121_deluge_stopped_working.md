---
title: "deluge stopped working"
date: 2015-02-27
forum: Ubuntu Development Version
---

### Post by zika on 2015-02-27
```
:~$ deluge

** (deluge:5004): WARNING **: couldn't make the type `gio.MemoryInputStream' ready


** (deluge:5004): WARNING **: couldn't make the type `gio.MemoryOutputStream' ready
TypeError: type 'gio.MemoryOutputStream' is not dynamically allocated but its base type '__main__.GPollableOutputStream' is dynamically allocated


** (deluge:5004): WARNING **: couldn't make the type `gio.unix.InputStream' ready


** (deluge:5004): WARNING **: couldn't make the type `gio.unix.OutputStream' ready
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:40: RuntimeWarning: tp_compare didn't return -1 or -2 for exception
  from gtk import _gtk
ImportError: could not import gio
ImportError: could not import gio
[ERROR   ] 18:16:04 ui:168 cannot import name Widget from gtk
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/deluge/ui/ui.py", line 149, in __init__
    from deluge.ui.gtkui.gtkui import GtkUI
  File "/usr/lib/python2.7/dist-packages/deluge/ui/gtkui/__init__.py", line 1, in <module>
    from gtkui import start
  File "/usr/lib/python2.7/dist-packages/deluge/ui/gtkui/gtkui.py", line 58, in <module>
    import gtk, gtk.glade
ImportError: cannot import name Widget from gtk
[ERROR   ] 18:16:04 ui:169 There was an error whilst launching the request UI: gtk
[ERROR   ] 18:16:04 ui:170 Look at the traceback above for more information.
```

---

### Post by mc4man on 2015-02-27
Ubuntu made some extensive changes to python2.7.9-1, guess they'll need to make some to deluge now. File a bug, don't hold breath

---

### Post by zika on 2015-02-27
> **mc4man said:**
> don't hold breathWhy would I? ;)
Update: Upgrade fixed it:```
:~$ deluge
/usr/lib/python2.7/dist-packages/deluge/ui/gtkui/queuedtorrents.py:60: Warning: The property GtkDialog:has-separator is deprecated and shouldn't be used anymore. It will be removed in a future version.
"glade/queuedtorrents.glade"))
[ERROR ] 22:00:56 component:118 [Failure instance: Traceback: <type 'exceptions.RuntimeError'>: Address family not supported by protocol
/usr/lib/python2.7/dist-packages/deluge/ui/client.py:432:__init__
/usr/lib/python2.7/dist-packages/deluge/core/daemon.py:161:__init__
/usr/lib/python2.7/dist-packages/deluge/component.py:296:start
/usr/lib/python2.7/dist-packages/deluge/component.py:124:_component_start
--- <exception caught here> ---
/usr/lib/python2.7/dist-packages/twisted/internet/defer.py:139:maybeDeferred
/usr/lib/python2.7/dist-packages/deluge/core/preferencesmanager.py:162:start
/usr/lib/python2.7/dist-packages/deluge/config.py:312:register_set_function
/usr/lib/python2.7/dist-packages/deluge/core/preferencesmanager.py:258:_on_set_listen_interface
/usr/lib/python2.7/dist-packages/deluge/core/preferencesmanager.py:276:_on_set_random_port
]
Unhandled error in Deferred:
Unhandled Error
Traceback (most recent call last):
File "/usr/lib/python2.7/dist-packages/deluge/ui/client.py", line 432, in __init__
self.__daemon = deluge.core.daemon.Daemon(classic=True)
File "/usr/lib/python2.7/dist-packages/deluge/core/daemon.py", line 161, in __init__
component.start("PreferencesManager")
File "/usr/lib/python2.7/dist-packages/deluge/component.py", line 296, in start
deferreds.append(self.components[name]._component_start())
File "/usr/lib/python2.7/dist-packages/deluge/component.py", line 124, in _component_start
d = maybeDeferred(self.start)
--- <exception caught here> ---
File "/usr/lib/python2.7/dist-packages/twisted/internet/defer.py", line 139, in maybeDeferred
result = f(*args, **kw)
File "/usr/lib/python2.7/dist-packages/deluge/core/preferencesmanager.py", line 162, in start
self._on_set_listen_interface)
File "/usr/lib/python2.7/dist-packages/deluge/config.py", line 312, in register_set_function
function(key, self.__config[key])
File "/usr/lib/python2.7/dist-packages/deluge/core/preferencesmanager.py", line 258, in _on_set_listen_interface
self._on_set_random_port("random_port", self.config["random_port"])
File "/usr/lib/python2.7/dist-packages/deluge/core/preferencesmanager.py", line 276, in _on_set_random_port
self.session.listen_on(listen_ports[0], listen_ports[1], str(self.config["listen_interface"]).strip())
exceptions.RuntimeError: Address family not supported by protocol
[ERROR ] 22:00:57 component:118 [Failure instance: Traceback: <type 'exceptions.RuntimeError'>: Address family not supported by protocol
/usr/lib/python2.7/dist-packages/twisted/internet/base.py:429:_continueFiring
/usr/lib/python2.7/dist-packages/deluge/ui/gtkui/gtkui.py:368:_on_reactor_start
/usr/lib/python2.7/dist-packages/deluge/component.py:296:start
/usr/lib/python2.7/dist-packages/deluge/component.py:124:_component_start
--- <exception caught here> ---
/usr/lib/python2.7/dist-packages/twisted/internet/defer.py:139:maybeDeferred
/usr/lib/python2.7/dist-packages/deluge/core/preferencesmanager.py:162:start
/usr/lib/python2.7/dist-packages/deluge/config.py:312:register_set_function
/usr/lib/python2.7/dist-packages/deluge/core/preferencesmanager.py:258:_on_set_listen_interface
/usr/lib/python2.7/dist-packages/deluge/core/preferencesmanager.py:276:_on_set_random_port
]
```Now it works... ;)

---

### Post by TheByteSmasher on 2015-02-28
> **zika said:**
> Why would I? ;)
Update: Upgrade fixed it:```
:~$ deluge
/usr/lib/python2.7/dist-packages/deluge/ui/gtkui/queuedtorrents.py:60: Warning: The property GtkDialog:has-separator is deprecated and shouldn't be used anymore. It will be removed in a future version.
"glade/queuedtorrents.glade"))
[ERROR ] 22:00:56 component:118 [Failure instance: Traceback: <type 'exceptions.RuntimeError'>: Address family not supported by protocol
/usr/lib/python2.7/dist-packages/deluge/ui/client.py:432:__init__
/usr/lib/python2.7/dist-packages/deluge/core/daemon.py:161:__init__
/usr/lib/python2.7/dist-packages/deluge/component.py:296:start
/usr/lib/python2.7/dist-packages/deluge/component.py:124:_component_start
--- <exception caught here> ---
/usr/lib/python2.7/dist-packages/twisted/internet/defer.py:139:maybeDeferred
/usr/lib/python2.7/dist-packages/deluge/core/preferencesmanager.py:162:start
/usr/lib/python2.7/dist-packages/deluge/config.py:312:register_set_function
/usr/lib/python2.7/dist-packages/deluge/core/preferencesmanager.py:258:_on_set_listen_interface
/usr/lib/python2.7/dist-packages/deluge/core/preferencesmanager.py:276:_on_set_random_port
]
Unhandled error in Deferred:
Unhandled Error
Traceback (most recent call last):
File "/usr/lib/python2.7/dist-packages/deluge/ui/client.py", line 432, in __init__
self.__daemon = deluge.core.daemon.Daemon(classic=True)
File "/usr/lib/python2.7/dist-packages/deluge/core/daemon.py", line 161, in __init__
component.start("PreferencesManager")
File "/usr/lib/python2.7/dist-packages/deluge/component.py", line 296, in start
deferreds.append(self.components[name]._component_start())
File "/usr/lib/python2.7/dist-packages/deluge/component.py", line 124, in _component_start
d = maybeDeferred(self.start)
--- <exception caught here> ---
File "/usr/lib/python2.7/dist-packages/twisted/internet/defer.py", line 139, in maybeDeferred
result = f(*args, **kw)
File "/usr/lib/python2.7/dist-packages/deluge/core/preferencesmanager.py", line 162, in start
self._on_set_listen_interface)
File "/usr/lib/python2.7/dist-packages/deluge/config.py", line 312, in register_set_function
function(key, self.__config[key])
File "/usr/lib/python2.7/dist-packages/deluge/core/preferencesmanager.py", line 258, in _on_set_listen_interface
self._on_set_random_port("random_port", self.config["random_port"])
File "/usr/lib/python2.7/dist-packages/deluge/core/preferencesmanager.py", line 276, in _on_set_random_port
self.session.listen_on(listen_ports[0], listen_ports[1], str(self.config["listen_interface"]).strip())
exceptions.RuntimeError: Address family not supported by protocol
[ERROR ] 22:00:57 component:118 [Failure instance: Traceback: <type 'exceptions.RuntimeError'>: Address family not supported by protocol
/usr/lib/python2.7/dist-packages/twisted/internet/base.py:429:_continueFiring
/usr/lib/python2.7/dist-packages/deluge/ui/gtkui/gtkui.py:368:_on_reactor_start
/usr/lib/python2.7/dist-packages/deluge/component.py:296:start
/usr/lib/python2.7/dist-packages/deluge/component.py:124:_component_start
--- <exception caught here> ---
/usr/lib/python2.7/dist-packages/twisted/internet/defer.py:139:maybeDeferred
/usr/lib/python2.7/dist-packages/deluge/core/preferencesmanager.py:162:start
/usr/lib/python2.7/dist-packages/deluge/config.py:312:register_set_function
/usr/lib/python2.7/dist-packages/deluge/core/preferencesmanager.py:258:_on_set_listen_interface
/usr/lib/python2.7/dist-packages/deluge/core/preferencesmanager.py:276:_on_set_random_port
]
```Now it works... ;)


BUT What did you do to fix it???

---

### Post by dino99 on 2015-02-28
> **TheByteSmasher said:**
> BUT What did you do to fix it???

some revert have been made to python2.7 to make it still compatible with all the python'sapps around.
so only update your archives, then upgrade python2.7; that 's it

---

### Post by zika on 2015-02-28
> **TheByteSmasher said:**
> BUT What did you do to fix it???
As I wrote:
> **zika said:**
> Upgrade fixed it

---

### Post by Yellow Pasque on 2015-03-03
Please mark thread solved if it's fixed.
[https://bugs.launchpad.net/ubuntu/+source/python2.7/+bug/1426294](https://bugs.launchpad.net/ubuntu/+source/python2.7/+bug/1426294)

---

### Post by zika on 2015-03-03
> **Temüjin said:**
> Please mark thread solved if it's fixed.
[https://bugs.launchpad.net/ubuntu/+source/python2.7/+bug/1426294](https://bugs.launchpad.net/ubuntu/+source/python2.7/+bug/1426294)Done.

---

