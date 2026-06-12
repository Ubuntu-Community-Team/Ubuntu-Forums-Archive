---
title: "Elisa 0.5.3 - Hardy .debs"
date: 2008-08-04
forum: The Cafe
---

### Post by b3n87 on 2008-08-04
If anyones interest, theres some unoffical debs for hardy made by the elisa community. Ive just done it and it works a treat.

[http://elisa.fluendo.com/forums/viewtopic.php?id=646]("http://elisa.fluendo.com/forums/viewtopic.php?id=646")

Enjoy

---

### Post by armageddon08 on 2008-08-04
Thanks....but can I install them with Synaptic the sources.list way.

---

### Post by b3n87 on 2008-08-04
No not yet, no one's made a repo for this version. THeres version 0.3.5 in the hardy repo's if thats any help.

The only thing missing I can see is access to pictures via F-Spot, the new version seems to be more polished and slighty faster.

---

### Post by armageddon08 on 2008-08-04
> **b3n87 said:**
> No not yet, no one's made a repo for this version. THeres version 0.3.5 in the hardy repo's if thats any help.

The only thing missing I can see is access to pictures via F-Spot, the new version seems to be more polished and slighty faster.

Well...the debs didn't work out for me. So I'm now currently downloading the source tarballs. One question will the plugins available at the Elisa official site for version 0.3.5 work in the version 0.5.3?

---

### Post by kostkon on 2008-08-04
In reality, there is a repo for Hardy, they even give you the key, nice:
[http://elisa.fluendo.com/packages/]("http://elisa.fluendo.com/packages/")

although I don't know what version it has currently.

---

### Post by armageddon08 on 2008-08-04
> **kostkon said:**
> In reality, there is a repo for Hardy, they even give you the key, nice:
[http://elisa.fluendo.com/packages/]("http://elisa.fluendo.com/packages/")

although I don't know what version it has currently.

Must be 0.3.5 'cause they haven't yet released .deb files of 0.5.3
[http://elisa.fluendo.com/download/]("http://elisa.fluendo.com/download/")

---

### Post by sensimilla on 2008-08-08
One of the developers posted the following link on the elisa forum:

[https://launchpad.net/~elisa-developers/+archive]("https://launchpad.net/~elisa-developers/+archive")

It contains the following apt sources.list entry

```
deb http://ppa.launchpad.net/elisa-developers/ubuntu hardy main
```

So that you can install the latest version of elisa via apt-get or synaptic.

It is currently working fine for me with 0.5.4 and 64-bit hardy.

(I couldn't get the above mentioned repo to work at all, maybe it will be updated at some point.)

---

### Post by pt123 on 2008-08-08
holy cow they went from .35 to .53 sounds like someone has been smoking a little too much.

---

### Post by armageddon08 on 2008-08-08
> **pt123 said:**
> holy cow they went from .35 to .53 sounds like someone has been smoking a little too much.

Actually, they had 0.5.1 and 0.5.2 and other versions also but they were for mostly for OSX or Windows.

---

### Post by meborc on 2008-08-08
> **sensimilla said:**
> One of the developers posted the following link on the elisa forum:

[https://launchpad.net/~elisa-developers/+archive]("https://launchpad.net/~elisa-developers/+archive")

It contains the following apt sources.list entry

```
deb http://ppa.launchpad.net/elisa-developers/ubuntu hardy main
```

So that you can install the latest version of elisa via apt-get or synaptic.

It is currently working fine for me with 0.5.4 and 64-bit hardy.

(I couldn't get the above mentioned repo to work at all, maybe it will be updated at some point.)


thanks, worked a treat... and 0.5.4 *IS* much more refined :)

---

### Post by Sealbhach on 2008-08-08
I can't get the Flickr plugin working.

Any ideas? Do I have to put something in the config file?


.

---

### Post by armageddon08 on 2008-08-08
> **Sealbhach said:**
> I can't get the Flickr plugin working.

Any ideas? Do I have to put something in the config file?


.

Yeah......I was also wondering abt that. Perhaps the plugins are not compatible as they are for the 0.3.5 version.

---

### Post by geoken on 2008-08-08
I forgot about Elisa when they started releasing multiple versions for Window's while not having the time to compile a single binary for any Linux distro. In July, they went through 4 version which were all packaged for Window's and all Linux users got were some hard to compile sources thrown at them.

I've since moved on to Boxee and I'm glad I did. The online media support in Boxee blows everything else out of the water.

If anyone wants to try out Boxee, head over to Phoronix. They have an article on Boxee and in the article their is a link to a thread on their forums where the site admin is handing out Boxee invites (or you can wait 'till September when it goes into public beta).

---

### Post by PryGuy on 2008-08-08
I've got no DVD playback :cry:

---

### Post by FuturePilot on 2008-08-08
It didn't even start for me :cry:

---

### Post by pexi on 2008-08-09
Hi, I have a macbook with Ubuntu hardy 64-bits installed, and Elisa doens't start. 
If I execute from a terminal I get this output:

```
pexi@macbook:~$ elisa
WARN  MainThread      plugin_registry             ago 09 17:23:33  plugin conflict Louie 1.1 (elisa/core/plugin_registry.py:220)
WARN  MainThread      plugin_registry             ago 09 17:23:33  plugin conflict elisa-plugin-coherence 0.1 (elisa/core/plugin_registry.py:220)
WARN  MainThread      gst_metadata_slave_process_protocol ago 09 17:23:33  Starting Slave-2 on unix:/tmp/elisa-metadata-6DS3SZ.socket launching elisa.plugins.gstreamer.amp_slave.run_slave
(Slave-2 stdout) (elisa/plugins/amp/master.py:54)
WARN  MainThread      gst_metadata_slave_process_protocol ago 09 17:23:34  /usr/lib/python2.5/site-packages/elisa/core/utils/classinit.py:34: UserWarning: ClassInitMeta class is deprecated
  warn("ClassInitMeta class is deprecated")
(Slave-2 stderr) (elisa/plugins/amp/master.py:57)
WARN  MainThread      resource_manager            ago 09 17:23:34  Creating wmd.wmd_resource:WMDResource failed. A full traceback can be found at /tmp/elisa_8fIDkX.txt (elisa/core/manager.py:83)
WARN  coherence                   ago 09 17:23:34  Coherence UPnP framework version 0.5.0 starting... (coherence/base.py:165)
WARN  webserver                   ago 09 17:23:34  WebServer on port 60205 ready (coherence/base.py:103)
WARN  MainThread      resource_manager            ago 09 17:23:34  Creating smbwin32.smbwin32_resource:SmbWin32Resource failed. A full traceback can be found at /tmp/elisa_EZ8tt0.txt (elisa/core/manager.py:83)
WARN  MainThread      service_manager             ago 09 17:23:34  Creating osso.osso_service:OssoService failed. A full traceback can be found at /tmp/elisa_Lsr3D6.txt (elisa/core/manager.py:83)
WARN  MainThread      input_manager               ago 09 17:23:34  Creating winremote.streamzap_input:StreamzapInput failed. A full traceback can be found at /tmp/elisa_KUE6zN.txt (elisa/core/manager.py:83)
WARN  MainThread      input_manager               ago 09 17:23:34  Creating lirc.lirc_input:LircInput failed. A full traceback can be found at /tmp/elisa_F3j2Fr.txt (elisa/core/manager.py:83)
WARN  MainThread      interface_controller        ago 09 17:23:34  creating frontend frontend1 failed. A full traceback can be found at [Failure instance: Traceback: <type 'exceptions.ImportError'>: No module named cssutils
/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py:216:simulate
/usr/lib/python2.5/site-packages/twisted/internet/base.py:561:runUntilCurrent
/usr/lib/python2.5/site-packages/twisted/internet/task.py:236:_tick
/usr/lib/python2.5/site-packages/elisa/core/interface_controller.py:104:load_frontends_iter
--- <exception caught here> ---
/usr/lib/python2.5/site-packages/elisa/core/plugin_registry.py:384:create_component
/usr/lib/python2.5/site-packages/twisted/python/reflect.py:357:namedAny
/usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py:19:<module>
/usr/lib/python2.5/site-packages/elisa/plugins/pigment/widgets/theme.py:18:<module>
] (elisa/core/interface_controller.py:88)
WARN  MainThread      interface_controller        ago 09 17:23:34  Could not load any frontend (elisa/core/interface_controller.py:123)
WARN  MainThread      twisted                     ago 09 17:23:34  A twisted traceback occurred. (twisted/internet/base.py:535)

Twisted traceback:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 175, in run
    self.__run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 114, in wrapper
    return real_cb(real_s, condition)
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 207, in callback
    self.simulate() # fire Twisted timers
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 216, in simulate
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 533, in runUntilCurrent
    f(*a, **kw)
  File "/usr/lib/python2.5/site-packages/elisa/core/bus.py", line 178, in _dispatch
    callback(message, sender)
  File "/usr/lib/python2.5/site-packages/elisa/plugins/gnome/gnome_screensaver_service.py", line 137, in _components_loaded
    frontend = frontends.values()[0]
exceptions.IndexError: list index out of range
```

I hope that someone could help us about this error.

---

### Post by georg_H on 2008-08-09
[LIST=1]
[*]Add this PPA repository ```
deb http://ppa.launchpad.net/elisa-developers/ubuntu hardy main
```
[*]The package elisa does not depend on two required packages: python-encutils and python-cssutils. After installing them (from the same repository), it should run.
[/LIST]

---

### Post by pexi on 2008-08-10
> **georg_H said:**
> [LIST=1]
[*]Add this PPA repository ```
deb http://ppa.launchpad.net/elisa-developers/ubuntu hardy main
```
[*]The package elisa does not depend on two required packages: python-encutils and python-cssutils. After installing them (from the same repository), it should run.
[/LIST]

I have installed from these repositories, but I get the error that I show in my last post.

---

### Post by slymi2005 on 2008-08-10
I get the same error after updating from 0.3.5 using the ppa repository.

---

### Post by FuturePilot on 2008-08-10
> **pexi said:**
> Hi, I have a macbook with Ubuntu hardy 64-bits installed, and Elisa doens't start. 
If I execute from a terminal I get this output:

```
pexi@macbook:~$ elisa
WARN  MainThread      plugin_registry             ago 09 17:23:33  plugin conflict Louie 1.1 (elisa/core/plugin_registry.py:220)
WARN  MainThread      plugin_registry             ago 09 17:23:33  plugin conflict elisa-plugin-coherence 0.1 (elisa/core/plugin_registry.py:220)
WARN  MainThread      gst_metadata_slave_process_protocol ago 09 17:23:33  Starting Slave-2 on unix:/tmp/elisa-metadata-6DS3SZ.socket launching elisa.plugins.gstreamer.amp_slave.run_slave
(Slave-2 stdout) (elisa/plugins/amp/master.py:54)
WARN  MainThread      gst_metadata_slave_process_protocol ago 09 17:23:34  /usr/lib/python2.5/site-packages/elisa/core/utils/classinit.py:34: UserWarning: ClassInitMeta class is deprecated
  warn("ClassInitMeta class is deprecated")
(Slave-2 stderr) (elisa/plugins/amp/master.py:57)
WARN  MainThread      resource_manager            ago 09 17:23:34  Creating wmd.wmd_resource:WMDResource failed. A full traceback can be found at /tmp/elisa_8fIDkX.txt (elisa/core/manager.py:83)
WARN  coherence                   ago 09 17:23:34  Coherence UPnP framework version 0.5.0 starting... (coherence/base.py:165)
WARN  webserver                   ago 09 17:23:34  WebServer on port 60205 ready (coherence/base.py:103)
WARN  MainThread      resource_manager            ago 09 17:23:34  Creating smbwin32.smbwin32_resource:SmbWin32Resource failed. A full traceback can be found at /tmp/elisa_EZ8tt0.txt (elisa/core/manager.py:83)
WARN  MainThread      service_manager             ago 09 17:23:34  Creating osso.osso_service:OssoService failed. A full traceback can be found at /tmp/elisa_Lsr3D6.txt (elisa/core/manager.py:83)
WARN  MainThread      input_manager               ago 09 17:23:34  Creating winremote.streamzap_input:StreamzapInput failed. A full traceback can be found at /tmp/elisa_KUE6zN.txt (elisa/core/manager.py:83)
WARN  MainThread      input_manager               ago 09 17:23:34  Creating lirc.lirc_input:LircInput failed. A full traceback can be found at /tmp/elisa_F3j2Fr.txt (elisa/core/manager.py:83)
WARN  MainThread      interface_controller        ago 09 17:23:34  creating frontend frontend1 failed. A full traceback can be found at [Failure instance: Traceback: <type 'exceptions.ImportError'>: No module named cssutils
/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py:216:simulate
/usr/lib/python2.5/site-packages/twisted/internet/base.py:561:runUntilCurrent
/usr/lib/python2.5/site-packages/twisted/internet/task.py:236:_tick
/usr/lib/python2.5/site-packages/elisa/core/interface_controller.py:104:load_frontends_iter
--- <exception caught here> ---
/usr/lib/python2.5/site-packages/elisa/core/plugin_registry.py:384:create_component
/usr/lib/python2.5/site-packages/twisted/python/reflect.py:357:namedAny
/usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py:19:<module>
/usr/lib/python2.5/site-packages/elisa/plugins/pigment/widgets/theme.py:18:<module>
] (elisa/core/interface_controller.py:88)
WARN  MainThread      interface_controller        ago 09 17:23:34  Could not load any frontend (elisa/core/interface_controller.py:123)
WARN  MainThread      twisted                     ago 09 17:23:34  A twisted traceback occurred. (twisted/internet/base.py:535)

Twisted traceback:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 175, in run
    self.__run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 114, in wrapper
    return real_cb(real_s, condition)
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 207, in callback
    self.simulate() # fire Twisted timers
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 216, in simulate
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 533, in runUntilCurrent
    f(*a, **kw)
  File "/usr/lib/python2.5/site-packages/elisa/core/bus.py", line 178, in _dispatch
    callback(message, sender)
  File "/usr/lib/python2.5/site-packages/elisa/plugins/gnome/gnome_screensaver_service.py", line 137, in _components_loaded
    frontend = frontends.values()[0]
exceptions.IndexError: list index out of range
```

I hope that someone could help us about this error.

Yep, that's the same error I got.

---

### Post by damoxc on 2008-08-11
can you post the output of:
```
python -c 'import cssutils'
```

If it's successfully installed there should be none.

---

### Post by MadsRH on 2008-08-14
Thanks, the "deb [http://ppa.launchpad.net/elisa-developers/ubuntu](http://ppa.launchpad.net/elisa-developers/ubuntu) hardy main" work perfect for me :)

---

### Post by PryGuy on 2008-08-16
So how about DVD support?

---

### Post by roundhay on 2008-08-17
I have follwed the instruction and installed from the developer repsoitory link but I get the following error:

WARN  MainThread      plugin_registry             Aug 17 17:26:41  plugin conflict elisa-plugin-coherence 0.1 (elisa/core/plugin_registry.py:220)
WARN  MainThread      gst_metadata_slave_process_protocol Aug 17 17:26:41  Starting Slave-2 on unix:/tmp/elisa-metadata-TTs_MM.socket launching elisa.plugins.gstreamer.amp_slave.run_slave
(Slave-2 stdout) (elisa/plugins/amp/master.py:54)
WARN  MainThread      gst_metadata_slave_process_protocol Aug 17 17:26:41  /usr/lib/python2.5/site-packages/elisa/core/utils/classinit.py:34: UserWarning: ClassInitMeta class is deprecated
  warn("ClassInitMeta class is deprecated")
(Slave-2 stderr) (elisa/plugins/amp/master.py:57)
WARN  MainThread      resource_manager            Aug 17 17:26:42  Creating wmd.wmd_resource:WMDResource failed. A full traceback can be found at /tmp/elisa_pUqdgP.txt (elisa/core/manager.py:83)
WARN  coherence                   Aug 17 17:26:42  Coherence UPnP framework version 0.5.8 starting... (coherence/base.py:251)
WARN  webserver                   Aug 17 17:26:42  WebServer on port 37535 ready (coherence/base.py:106)
WARN  MainThread      resource_manager            Aug 17 17:26:42  Creating smbwin32.smbwin32_resource:SmbWin32Resource failed. A full traceback can be found at /tmp/elisa_rPQdlg.txt (elisa/core/manager.py:83)
WARN  MainThread      service_manager             Aug 17 17:26:42  Creating osso.osso_service:OssoService failed. A full traceback can be found at /tmp/elisa_0mvDaK.txt (elisa/core/manager.py:83)
WARN  MainThread      input_manager               Aug 17 17:26:42  Creating winremote.streamzap_input:StreamzapInput failed. A full traceback can be found at /tmp/elisa_TU4vlD.txt (elisa/core/manager.py:83)
WARN  MainThread      input_manager               Aug 17 17:26:42  Creating lirc.lirc_input:LircInput failed. A full traceback can be found at /tmp/elisa_ZqAqf9.txt (elisa/core/manager.py:83)
WARN  MainThread      interface_controller        Aug 17 17:26:42  creating frontend frontend1 failed. A full traceback can be found at [Failure instance: Traceback: <type 'exceptions.ImportError'>: No module named encutils
/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py:216:simulate
/usr/lib/python2.5/site-packages/twisted/internet/base.py:561:runUntilCurrent
/usr/lib/python2.5/site-packages/twisted/internet/task.py:236:_tick
/usr/lib/python2.5/site-packages/elisa/core/interface_controller.py:104:load_frontends_iter
--- <exception caught here> ---
/usr/lib/python2.5/site-packages/elisa/core/plugin_registry.py:384:create_component
/usr/lib/python2.5/site-packages/twisted/python/reflect.py:357:namedAny
/usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py:19:<module>
/usr/lib/python2.5/site-packages/elisa/plugins/pigment/widgets/theme.py:18:<module>
/usr/lib/python2.5/site-packages/cssutils/__init__.py:81:<module>
/usr/lib/python2.5/site-packages/cssutils/util.py:16:<module>
] (elisa/core/interface_controller.py:88)
WARN  MainThread      interface_controller        Aug 17 17:26:42  Could not load any frontend (elisa/core/interface_controller.py:123)
WARN  MainThread      twisted                     Aug 17 17:26:42  A twisted traceback occurred. (twisted/internet/base.py:535)

Twisted traceback:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 175, in run
    self.__run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 114, in wrapper
    return real_cb(real_s, condition)
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 207, in callback
    self.simulate() # fire Twisted timers
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 216, in simulate
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 533, in runUntilCurrent
    f(*a, **kw)
  File "/usr/lib/python2.5/site-packages/elisa/core/bus.py", line 178, in _dispatch
    callback(message, sender)
  File "/usr/lib/python2.5/site-packages/elisa/plugins/gnome/gnome_screensaver_service.py", line 137, in _components_loaded
    frontend = frontends.values()[0]
exceptions.IndexError: list index out of range

This loom the same as a previous post in this thread, suggestions for a fix most welcome

---

### Post by roundhay on 2008-08-17
After running 

~$ python -c 'import cssutils'

I get the following output:

Traceback (most recent call last):
  File "<string>", line 1, in <module>
ImportError: No module named cssutils

This indicates that cssutils is not installed but according to synaptic is is? I get the same output if I remove cssutils using synaptic

Don't know why this is happening......

---

### Post by SomeGuyDude on 2008-08-17
Same as post 24. Doesn't open. Nice.

---

### Post by FuturePilot on 2008-08-17
> **SomeGuyDude said:**
> Same as post 24. Doesn't open. Nice.

Yes, 0.5.5 still will not run for me either. I see the splash screen and that's it, nothing ever opens. :(

---

### Post by emshains on 2008-08-17
> **b3n87 said:**
> If anyones interest, theres some unoffical debs for hardy made by the elisa community. Ive just done it and it works a treat.

[http://elisa.fluendo.com/forums/viewtopic.php?id=646]("http://elisa.fluendo.com/forums/viewtopic.php?id=646")

Enjoy

Dude, I just wish I saw youre post at the morning, because I was testing my new HDTV with my computer.

---

### Post by emshains on 2008-08-17
> **emshains said:**
> Dude, I just wish I saw youre post at the morning, because I was testing my new HDTV with my computer.

And it wouldnt give me any benefit, because it cant get past the "splash" screen.

---

### Post by zekopeko on 2008-08-17
try installing this packages

cssutils and python-enc

i'm not sure about the name but the packages have those words in them so just install them

---

### Post by ssam on 2008-08-28
the ppa is up to 0.5.7 now
[http://elisa.fluendo.com/news/13/](http://elisa.fluendo.com/news/13/)

I cant get the DVD player to work though (totem plays DVDs ok). i wonder if it needs newer gstreamer

---

### Post by ugm6hr on 2008-08-28
> **ssam said:**
> the ppa is up to 0.5.7 now
[http://elisa.fluendo.com/news/13/](http://elisa.fluendo.com/news/13/)

I cant get the DVD player to work though (totem plays DVDs ok). i wonder if it needs newer gstreamer

On Hardy 64-bit, it doesn't open (0.5.7).

Installed as per [http://elisa.fluendo.com/wiki/Distribution/LinuxPackages](http://elisa.fluendo.com/wiki/Distribution/LinuxPackages)

```
WARN  MainThread      plugin_registry             Aug 28 11:18:56  plugin conflict elisa-plugin-coherence 0.1 (elisa/core/plugin_registry.py:220)
WARN  MainThread      gst_metadata_slave_process_protocol Aug 28 11:18:57  Starting Slave-2 on unix:/tmp/elisa-metadata-9x2XXk.socket launching elisa.plugins.gstreamer.amp_slave.run_slave
(Slave-2 stdout) (elisa/plugins/amp/master.py:54)
WARN  MainThread      gst_metadata_slave_process_protocol Aug 28 11:18:57  /usr/lib/python2.5/site-packages/elisa/core/utils/classinit.py:34: UserWarning: ClassInitMeta class is deprecated
  warn("ClassInitMeta class is deprecated")
(Slave-2 stderr) (elisa/plugins/amp/master.py:57)
WARN  MainThread      resource_manager            Aug 28 11:18:57  Creating wmd.wmd_resource:WMDResource failed. A full traceback can be found at /tmp/elisa_UtLVC1.txt (elisa/core/manager.py:83)
WARN  coherence                   Aug 28 11:18:57  Coherence UPnP framework version 0.5.8 starting... (coherence/base.py:251)
WARN  webserver                   Aug 28 11:18:57  WebServer on port 44875 ready (coherence/base.py:106)
WARN  MainThread      resource_manager            Aug 28 11:18:57  Creating smbwin32.smbwin32_resource:SmbWin32Resource failed. A full traceback can be found at /tmp/elisa_SfEG1O.txt (elisa/core/manager.py:83)
WARN  MainThread      service_manager             Aug 28 11:18:57  Creating osso.osso_service:OssoService failed. A full traceback can be found at /tmp/elisa_xJrlSV.txt (elisa/core/manager.py:83)
WARN  MainThread      input_manager               Aug 28 11:18:57  Creating winremote.streamzap_input:StreamzapInput failed. A full traceback can be found at /tmp/elisa_LXFuGQ.txt (elisa/core/manager.py:83)
WARN  MainThread      input_manager               Aug 28 11:18:57  Creating lirc.lirc_input:LircInput failed. A full traceback can be found at /tmp/elisa_77l_VS.txt (elisa/core/manager.py:83)
WARN  MainThread      interface_controller        Aug 28 11:18:57  creating frontend frontend1 failed. A full traceback can be found at [Failure instance: Traceback: <type 'exceptions.ImportError'>: No module named cssutils
/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py:216:simulate
/usr/lib/python2.5/site-packages/twisted/internet/base.py:561:runUntilCurrent
/usr/lib/python2.5/site-packages/twisted/internet/task.py:236:_tick
/usr/lib/python2.5/site-packages/elisa/core/interface_controller.py:104:load_frontends_iter
--- <exception caught here> ---
/usr/lib/python2.5/site-packages/elisa/core/plugin_registry.py:384:create_component
/usr/lib/python2.5/site-packages/twisted/python/reflect.py:357:namedAny
/usr/lib/python2.5/site-packages/elisa/plugins/pigment/pigment_frontend.py:19:<module>
/usr/lib/python2.5/site-packages/elisa/plugins/pigment/widgets/theme.py:18:<module>
] (elisa/core/interface_controller.py:88)
WARN  MainThread      interface_controller        Aug 28 11:18:57  Could not load any frontend (elisa/core/interface_controller.py:123)
WARN  MainThread      twisted                     Aug 28 11:18:57  A twisted traceback occurred. (twisted/internet/base.py:535)

Twisted traceback:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 175, in run
    self.__run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 114, in wrapper
    return real_cb(real_s, condition)
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 207, in callback
    self.simulate() # fire Twisted timers
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 216, in simulate
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 533, in runUntilCurrent
    f(*a, **kw)
  File "/usr/lib/python2.5/site-packages/elisa/core/bus.py", line 178, in _dispatch
    callback(message, sender)
  File "/usr/lib/python2.5/site-packages/elisa/plugins/gnome/gnome_screensaver_service.py", line 137, in _components_loaded
    frontend = frontends.values()[0]
exceptions.IndexError: list index out of range

```

EDIT: I just installed python-cssutils with aptitude, and it works fine :)

---

### Post by bve on 2008-09-12
> **ssam said:**
> the ppa is up to 0.5.7 now
[http://elisa.fluendo.com/news/13/](http://elisa.fluendo.com/news/13/)

I cant get the DVD player to work though (totem plays DVDs ok). i wonder if it needs newer gstreamer


To get dvd playback ...

```

sudo ln -s /dev/scd0 /dev/dvd

```

Now does anyone have Elisa working with upnp?

---

### Post by psypher on 2008-10-26
I'm still getting the same errors after trying everything on this post and still Elisa only opens the slpash screen and then just black? Also my version is only 0.5.15 from that repo, why is everyone else on 0.5.3 and 4 ect.

Is boxee really the best? I've heard a few people mention it. XBMC has a lot of potential but very unstale, makes  my pc crash as soon as I play video.

---

### Post by ugm6hr on 2008-10-26
> **psypher said:**
> I'm still getting the same errors after trying everything on this post and still Elisa only opens the slpash screen and then just black? Also my version is only 0.5.15 from that repo, why is everyone else on 0.5.3 and 4 ect.

0.5.15 is newer than 0.5.3 (15>3).

Unfortunately, the last 2 revisions have been very poor - very slow and unstable on my system.

---

### Post by psypher on 2008-11-02
Upgraded to Intrepid x64.

Seems that 0.5.9 is now in the ubuntu repo's. Didn't have to add the repo. Still getting same problem though :( and i have tried the python pkgs:

```
 sudo apt-get install python-encutils python-cssutils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-encutils is already the newest version.
python-encutils set to manually installed.
python-cssutils is already the newest version.
python-cssutils set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by wolfe on 2008-11-04
I too am unable to get this to start, i get:

```
Traceback (most recent call last):
  File "/usr/bin/elisa", line 222, in <module>
    main()
  File "/usr/bin/elisa", line 200, in main
    if not options['headless']:
KeyError: 'headless'

```

---

