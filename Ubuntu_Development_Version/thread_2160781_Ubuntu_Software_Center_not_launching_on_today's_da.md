---
title: "Ubuntu Software Center not launching on today's daily build"
date: 2013-07-08
forum: Ubuntu Development Version
---

### Post by slickymaster on 2013-07-08
Wondering if anyone could try to reproduce a strange issue I'm facing in today's daily build. I've tried to launch the software center from the applications menu, from the Xfce bottom panel and from the terminal but it fails in any of the ways attempted.
There are no crash reports either in **/var/crash** either in **/var/log**

Here's the specs:```
~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Saucy Salamander (development branch)
Release:    13.10
Codename:    saucy
3.10.0-2-generic

```

---

### Post by pqwoerituytrueiwoq on 2013-07-08
when I run it in the terminal i get this, this is not a clean install from today, BTW the command is [FONT=courier new]software-center[/FONT] or [FONT=courier new]software-center-gtk3[/FONT] they both do the same thing here
```
** (software-center:1937): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-7WsocSVGdP: Connection refused
2013-07-08 10:45:14,424 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 130, in <module>
    app = SoftwareCenterAppGtk3(options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 429, in __init__
    self.useful_cache = UsefulnessCache(True)
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 91, in __init__
    self._retrieve_votes_from_server()
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 105, in _retrieve_votes_from_server
    user = get_person_from_config()
  File "/usr/share/software-center/softwarecenter/utils.py", line 638, in get_person_from_config
    cfg = get_config()
  File "/usr/share/software-center/softwarecenter/config.py", line 180, in get_config
    _software_center_config = SoftwareCenterConfig(filename)
  File "/usr/share/software-center/softwarecenter/config.py", line 38, in __init__
    super(SoftwareCenterConfig, self).__init__()
TypeError: must be type, not classobj
```
if you have not figured it out yet it is not working here either in my virtualbox

---

### Post by slickymaster on 2013-07-08
Hi, pqwoerituytrueiwoq.

Thanks for taking the time to look into it, I appreciate it.

I'm testing it also in my virtual box and also that's the output I get when I tried to launch it from the terminal:```
slickymaster@slickymaster-VirtualBox:~$ software-center

** (software-center:2245): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-9MkGPjK2Cx: Connection refused
2013-07-08 15:52:40,828 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-07-08 15:52:42,138 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Geoclue.Master was not provided by any .service files'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 130, in <module>
    app = SoftwareCenterAppGtk3(options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 429, in __init__
    self.useful_cache = UsefulnessCache(True)
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 91, in __init__
    self._retrieve_votes_from_server()
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 105, in _retrieve_votes_from_server
    user = get_person_from_config()
  File "/usr/share/software-center/softwarecenter/utils.py", line 638, in get_person_from_config
    cfg = get_config()
  File "/usr/share/software-center/softwarecenter/config.py", line 180, in get_config
    _software_center_config = SoftwareCenterConfig(filename)
  File "/usr/share/software-center/softwarecenter/config.py", line 38, in __init__
    super(SoftwareCenterConfig, self).__init__()
TypeError: must be type, not classobj
```

So far, I wasn't able to figure it out, but already filed a bug at Launchpad: [Bug #1198898 - Ubuntu Software Center not launching]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1198898")

---

### Post by dino99 on 2013-07-08
Dont waste time to report against that package: its too buggy to get fixed
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bugs?orderby=-date_last_updated&start=0](https://bugs.launchpad.net/ubuntu/+source/software-center/+bugs?orderby=-date_last_updated&start=0)

---

### Post by slickymaster on 2013-07-08
> **dino99 said:**
> Dont waste time to report against that package: its too buggy to get fixed
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bugs?orderby=-date_last_updated&start=0](https://bugs.launchpad.net/ubuntu/+source/software-center/+bugs?orderby=-date_last_updated&start=0)

:shock: Yeah, I see what you mean, 824 of them. Thanks for the heads up.

Besides reporting against the package, do you have any suggestions where to report it?

---

### Post by dino99 on 2013-07-08
Simply ignore it, and use the well proofed apt-get/synaptic

---

### Post by slickymaster on 2013-07-08
> **dino99 said:**
> Simply ignore it, and use the well proofed apt-get/synaptic

It's not a matter of personal use. Thing is that I'm testing for [Ubuntu ISO Testing]("http://iso.qa.ubuntu.com/") and we're supposed to report any bugs along the way.

---

### Post by pqwoerituytrueiwoq on 2013-07-08
well i marked it as affects me also

---

### Post by slickymaster on 2013-07-08
Thanks, pqwoerituytrueiwoq.

I think I'll close this thread, as it achieved it's purpose.

---

