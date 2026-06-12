---
title: "Trouble with software center"
date: 2013-06-19
forum: Ubuntu Development Version
---

### Post by justynt on 2013-06-19
Is anyone else experiencing trouble with the software center not running. Currently running an fully updated 13.10

---

### Post by Toz on 2013-06-19
*Moved to the **Ubuntu+1** forum.*

Do you get any errors when you run it from the command line?

---

### Post by justynt on 2013-06-19
[http://pastebay.net/1241735](http://pastebay.net/1241735) there they are

---

### Post by justynt on 2013-06-19
note:
Ubuntu-one is not working either. Not working on guest session either.

---

### Post by Toz on 2013-06-19
Bug report [here]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1192315"). Apparently a duplicate of [this bug report]("https://bugs.launchpad.net/ubuntu/+source/dbus-python/+bug/1068680"). Comment #6 indicates that re-installing python-sip and python-qt4 solved the problem. Might be worth a try?

---

### Post by justynt on 2013-06-19
Not letting me install qt4 says "depends sip-api-9.2" however it has no installation candidate.

---

### Post by justynt on 2013-06-19
Fixed! installing sip (just sip) did it. Thank you very much.

---

### Post by Toz on 2013-06-19
Try running:
```
sudo apt-get update
```
...and try again.

Otherwise, you might need to wait until sip-api-9.2 becomes available. Since you are running the development release which I believe is still in alpha testing, you can expect breakage like this.

EDIT: Sorry, you ninja'd me with your last post. Glad it worked.

---

### Post by justynt on 2013-06-19
Haha well i appreciate you quick reply, hopefully this will help anyone else who has this bug.

---

### Post by Toz on 2013-06-19
Posted in the bug report about your solution. 

Can you mark this thread solved by:
1. Clicking "Edit" on your first post in this thread.
2. Click the "Go Advanced" button.
3. Change Prefix to "[SOLVED]"
4. Save.

Thanks

---

### Post by Document on 2013-06-19
So Software Center has suddenly decided to quit working. I have already tried re-installing it. Here is the error code I get when trying to boot from the terminal:

2013-06-19 18:37:48,921 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-06-19 18:37:49,161 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/proxies.py', 410, '_introspect_error_handler')'
2013-06-19 18:37:49,161 - dbus.proxies - ERROR - Introspect error on com.ubuntu.sso:/com/ubuntu/sso/credentials: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntu-sso-client/ubuntu-sso-login exited with status 1
Traceback (most recent call last):
  File "/usr/bin/software-center", line 130, in <module>
    app = SoftwareCenterAppGtk3(options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 338, in __init__
    self.icons)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/appmanager.py", line 66, in __init__
    self.oauth_token = helper.find_oauth_token_sync()
  File "/usr/share/software-center/softwarecenter/backend/ubuntusso.py", line 141, in find_oauth_token_sync
    sso.find_credentials()
  File "/usr/share/software-center/softwarecenter/backend/login_impl/login_sso.py", line 75, in find_credentials
    self.proxy.find_credentials(self.appname, self._get_params())
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntu-sso-client/ubuntu-sso-login exited with status 1



Thanks!

---

### Post by Toz on 2013-06-19
*Moving to **Ubuntu+1**.*

Have a look [here]("http://ubuntuforums.org/showthread.php?t=2155880").

---

### Post by Document on 2013-06-19
That solution seemed to have worked! Thank you!

---

### Post by cariboo on 2013-06-21
Merged two similar threads.

---

