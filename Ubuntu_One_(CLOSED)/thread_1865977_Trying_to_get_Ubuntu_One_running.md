---
title: "Trying to get Ubuntu One running"
date: 2011-10-20
forum: Ubuntu One (CLOSED)
---

### Post by thnewguy on 2011-10-20
I have installed Ubuntu One and the process appeared to complete successfully. However, when I bring up the One control panel and click on the link "I have an existing account" nothing happens.

I've tried running the control panel from the command line and I'm getting the following output:

```

ERROR:dbus.connection:Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 214, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/logger.py", line 82, in inner
    res = f(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/gui/gtk/gui.py", line 1218, in on_replications_info_ready
    dependency=pkg, dependency_name=name)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/gui/gtk/gui.py", line 1071, in __init__
    self.dependency = InstallPackage(dependency, message)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/gui/gtk/gui.py", line 891, in __init__
    ControlPanelMixin.__init__(self, filename='install.ui')
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/gui/gtk/gui.py", line 160, in __init__
    builder.add_from_file(get_data_file(os.path.join('gtk', filename)))
GError: Failed to open file '/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/data/gtk/install.ui': No such file or directory

```


It appears I'm missing the file /usr/lib/python2.7/dist-packages/ubuntuone-control-panel/data/gtk/install.ui

Anyone know which package contains this file? Or how I might hunt it down? I'm running Kubuntu 11.10.

---

### Post by thnewguy on 2011-10-21
Okay, I finally got Ubuntu One up and running. If anyone else on Kubuntu 11.10 has this issue, this is my solution. Bear with me, it's a long one.

1. Remove all Ubuntu One packages. Use something like
apt-cache search ubuntuone
from the command line. Then remove every package that starts with "ubuntuone". You can probably do this with
sudo apt-get remove ubuntuone-client ubuntuone-installer ubuntuone-control-panel-gtk

2. Perform clean-up of packages on your system.
sudo apt-get autoremove
sudo apt-get clean

This gives us a clean place to start from.

3. Remove any single signon keys.
rm ~/.gnome2/keyrings/*


4. Re-install Ubuntu One
sudo apt-get install ubuntuone-installer
ubuntuone-installer 
(note this is run as your regular user, without "sudo")

5. You should be prompted to reboot. Restart the computer. Then run
u1sdtool -q

6. For some reason on my Kubuntu machine Ubuntu One's installer puts files in the wrong location. So we fix this using
sudo mkdir -p /usr/lib/python2.7/dist-packages/ubuntuone-control-panel/data
sudo cp -R /usr/share/ubuntuone-control-panel/* /usr/lib/python2.7/dist-packages/ubuntuone-control-panel/data

7. Run the command ubuntuone-control-panel-gtk

This should now allow you to create a new account or sign-in to an existing account.

This has worked for me so far.

---

### Post by ohadcn on 2012-02-24
i get this error on the 4th step:
```
 
[EMAIL="ohad@comp1:%7E/.gnome"]ohad@comp1:~/[/EMAIL]$ ubuntuone-installer 
 Traceback (most recent call last):
   File "/usr/bin/ubuntuone-installer", line 39, in <module>
     dialog = Window()
   File "/usr/lib/python2.7/dist-packages/ubuntuone-installer/ubuntuone/installer/gui.py", line 98, in __init__
     _(u'Install Ubuntu One')))
 UnicodeDecodeError: 'ascii' codec can't decode byte 0xd7 in position 0: ordinal not in range(128)

```
can someone solve that?

---

