---
title: "IPCError on U1 at control panel"
date: 2012-11-14
forum: Ubuntu One (CLOSED)
---

### Post by oldos2er on 2012-11-14
Running Kubuntu 12.10, ubuntuone-control-panel-qt v4.0.0-0ubuntu1. Any mouse click on the control panel results in "IPCError" although the control panel appears to be functioning correctly after closing the error window.

Terminal output: ```
ann@ann-XPS-8100:~$ ubuntuone-control-panel-qt 
ERROR:root:Could not find any typelib for Unity
ERROR:root:Could not find any typelib for Unity
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
INFO:ubuntuone.controlpanel.backend:ControlBackend: instance started.
INFO:ubuntuone.controlpanel.backend:set_public_files_list_handler: args (<ubuntuone.controlpanel.backend.ControlBackend object at 0x17f2c10>, <bound method ShareLinksPanel._load_public_files of <ubuntuone.controlpanel.gui.qt.share_links.ShareLinksPanel object at 0x1960170>>), kwargs {}.
INFO:ubuntuone.controlpanel.backend:set_public_access_changed_handler: args (<ubuntuone.controlpanel.backend.ControlBackend object at 0x17f2c10>, <bound method ShareLinksPanel._file_shared of <ubuntuone.controlpanel.gui.qt.share_links.ShareLinksPanel object at 0x1960170>>), kwargs {}.
INFO:ubuntuone.controlpanel.backend:set_public_access_change_error_handler: args (<ubuntuone.controlpanel.backend.ControlBackend object at 0x17f2c10>, <function <lambda> at 0x1967140>), kwargs {}.
INFO:ubuntuone.controlpanel.qt.gui:Updates available? None
DEBUG:ubuntuone.credentials:find_credentials: args (<ubuntuone.platform.credentials.CredentialsManagementTool object at 0x17f2c90>,), kwargs {}.
DEBUG:ubuntuone.credentials:cleanup: removing signal match <<class 'dbus.connection.SignalMatch'> at 17b6590 "type='signal',sender='com.ubuntuone.Credentials',path='/credentials',interface='com.ubuntuone.CredentialsManagement',member='CredentialsFound'" on conn <dbus._dbus.SessionBus (session) at 0x17eb110>>
DEBUG:ubuntuone.credentials:cleanup: removing signal match <<class 'dbus.connection.SignalMatch'> at 17b6710 "type='signal',sender='com.ubuntuone.Credentials',path='/credentials',interface='com.ubuntuone.CredentialsManagement',member='CredentialsNotFound'" on conn <dbus._dbus.SessionBus (session) at 0x17eb110>>
DEBUG:ubuntuone.credentials:cleanup: removing signal match <<class 'dbus.connection.SignalMatch'> at 17b6890 "type='signal',sender='com.ubuntuone.Credentials',path='/credentials',interface='com.ubuntuone.CredentialsManagement',member='CredentialsError'" on conn <dbus._dbus.SessionBus (session) at 0x17eb110>>
INFO:ubuntuone.controlpanel.qt.wizard:initializePage: args (<ubuntuone.controlpanel.gui.qt.wizard.UbuntuOneWizard object at 0x196b950>, 1), kwargs {}.
INFO:ubuntuone.controlpanel.qt.wizard:UbuntuOneWizard.initializePage: new page is <ubuntuone.controlpanel.gui.qt.wizard.SignInPage object at 0x196eef0>, new button layout is [9, 4], new side widget stage is 1.
Unhandled error in Deferred:
Unhandled Error
Traceback (most recent call last):
Failure: ubuntuone.platform.tools.linux.IPCError: org.freedesktop.DBus.Error.Spawn.ChildExited: 
Unhandled error in Deferred:
Unhandled Error
Traceback (most recent call last):
Failure: ubuntuone.platform.tools.linux.IPCError: org.freedesktop.DBus.Error.Spawn.ChildExited: 
Unhandled error in Deferred:
Unhandled Error
Traceback (most recent call last):
Failure: ubuntuone.platform.tools.linux.IPCError: org.freedesktop.DBus.Error.Spawn.ChildExited: 
ERROR:ubuntuone.controlpanel.qt.folders:Error while invoking <bound method FoldersPanel.load of <ubuntuone.controlpanel.gui.qt.folders.FoldersPanel object at 0x194e4d0>> with args () and kwargs {}:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/gui/qt/__init__.py", line 196, in inner
    res = yield f(*args, **kwargs)
IPCError: org.freedesktop.DBus.Error.Spawn.ChildExited: 
INFO:ubuntuone.controlpanel.qt.folders:The warning dialog was shown and also closed (message was 'IPCError').
DEBUG:ubuntuone.credentials:login: args (<ubuntuone.platform.credentials.CredentialsManagementTool object at 0x17f2c90>,), kwargs {}.
DEBUG:ubuntuone.credentials:cleanup: removing signal match <<class 'dbus.connection.SignalMatch'> at 17b6590 "type='signal',sender='com.ubuntuone.Credentials',path='/credentials',interface='com.ubuntuone.CredentialsManagement',member='CredentialsFound'" on conn <dbus._dbus.SessionBus (session) at 0x17eb110>>
DEBUG:ubuntuone.credentials:cleanup: removing signal match <<class 'dbus.connection.SignalMatch'> at 17b6710 "type='signal',sender='com.ubuntuone.Credentials',path='/credentials',interface='com.ubuntuone.CredentialsManagement',member='CredentialsNotFound'" on conn <dbus._dbus.SessionBus (session) at 0x17eb110>>
DEBUG:ubuntuone.credentials:cleanup: removing signal match <<class 'dbus.connection.SignalMatch'> at 17b6890 "type='signal',sender='com.ubuntuone.Credentials',path='/credentials',interface='com.ubuntuone.CredentialsManagement',member='CredentialsError'" on conn <dbus._dbus.SessionBus (session) at 0x17eb110>>
DEBUG:ubuntuone.credentials:cleanup: removing signal match <<class 'dbus.connection.SignalMatch'> at 17b6950 "type='signal',sender='com.ubuntuone.Credentials',path='/credentials',interface='com.ubuntuone.CredentialsManagement',member='CredentialsFound'" on conn <dbus._dbus.SessionBus (session) at 0x17eb110>>
DEBUG:ubuntuone.credentials:cleanup: removing signal match <<class 'dbus.connection.SignalMatch'> at 17b6650 "type='signal',sender='com.ubuntuone.Credentials',path='/credentials',interface='com.ubuntuone.CredentialsManagement',member='AuthorizationDenied'" on conn <dbus._dbus.SessionBus (session) at 0x17eb110>>
DEBUG:ubuntuone.credentials:cleanup: removing signal match <<class 'dbus.connection.SignalMatch'> at 17b6b90 "type='signal',sender='com.ubuntuone.Credentials',path='/credentials',interface='com.ubuntuone.CredentialsManagement',member='CredentialsError'" on conn <dbus._dbus.SessionBus (session) at 0x17eb110>>
INFO:ubuntuone.controlpanel.qt.wizard:initializePage: args (<ubuntuone.controlpanel.gui.qt.wizard.UbuntuOneWizard object at 0x196b950>, 2), kwargs {}.
INFO:ubuntuone.controlpanel.qt.wizard:UbuntuOneWizard.initializePage: new page is <ubuntuone.controlpanel.gui.qt.wizard.CloudToComputerPage object at 0x1970170>, new button layout is [9, 1], new side widget stage is 2.
Unhandled error in Deferred:
Unhandled Error
Traceback (most recent call last):
Failure: ubuntuone.platform.tools.linux.IPCError: org.freedesktop.DBus.Error.Spawn.ChildExited: 
INFO:ubuntuone.controlpanel.qt.wizard:initializePage: args (<ubuntuone.controlpanel.gui.qt.wizard.UbuntuOneWizard object at 0x196b950>, 4), kwargs {}.
INFO:ubuntuone.controlpanel.qt.wizard:UbuntuOneWizard.initializePage: new page is <ubuntuone.controlpanel.gui.qt.wizard.ComputerToCloudPage object at 0x19727a0>, new button layout is [9, 0, 3], new side widget stage is 3.
ERROR:ubuntuone.controlpanel.qt.folders:Error while invoking <bound method LocalFoldersPanel.load of <ubuntuone.controlpanel.gui.qt.folders.LocalFoldersPanel object at 0x1972b90>> with args () and kwargs {}:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/gui/qt/__init__.py", line 196, in inner
    res = yield f(*args, **kwargs)
IPCError: org.freedesktop.DBus.Error.Spawn.ChildExited: 
INFO:ubuntuone.controlpanel.qt.folders:The warning dialog was shown and also closed (message was 'IPCError').
ERROR:ubuntuone.controlpanel.qt.addfolder:Error while invoking <function on_clicked at 0x1753de8> with args (<ubuntuone.controlpanel.gui.qt.addfolder.AddFolderButton object at 0x1972ef0>,) and kwargs {}:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/gui/qt/__init__.py", line 196, in inner
    res = yield f(*args, **kwargs)
IPCError: org.freedesktop.DBus.Error.Spawn.ChildExited: 
INFO:ubuntuone.controlpanel.qt.addfolder:The warning dialog was shown and also closed (message was 'IPCError').
ERROR:ubuntuone.controlpanel.qt.addfolder:Error while invoking <function on_clicked at 0x1753de8> with args (<ubuntuone.controlpanel.gui.qt.addfolder.AddFolderButton object at 0x1972ef0>,) and kwargs {}:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/gui/qt/__init__.py", line 196, in inner
    res = yield f(*args, **kwargs)
IPCError: org.freedesktop.DBus.Error.Spawn.ChildExited: 
INFO:ubuntuone.controlpanel.qt.addfolder:The warning dialog was shown and also closed (message was 'IPCError').
INFO:ubuntuone.controlpanel.qt.controlpanel:on_wizard_finished: args (<ubuntuone.controlpanel.gui.qt.controlpanel.ControlPanel object at 0x194c170>, 1), kwargs {}.
Unhandled error in Deferred:
Unhandled Error
Traceback (most recent call last):
Failure: ubuntuone.platform.tools.linux.IPCError: org.freedesktop.DBus.Error.Spawn.ChildExited: 
ERROR:ubuntuone.controlpanel.qt.folders:Error while invoking <bound method FoldersPanel.load of <ubuntuone.controlpanel.gui.qt.folders.FoldersPanel object at 0x194e4d0>> with args () and kwargs {}:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/gui/qt/__init__.py", line 196, in inner
    res = yield f(*args, **kwargs)
IPCError: org.freedesktop.DBus.Error.Spawn.ChildExited: 
Unhandled error in Deferred:
Unhandled Error
Traceback (most recent call last):
Failure: ubuntuone.platform.tools.linux.IPCError: org.freedesktop.DBus.Error.Spawn.ChildExited: 
INFO:ubuntuone.controlpanel.qt.folders:The warning dialog was shown and also closed (message was 'IPCError').
ERROR:ubuntuone.controlpanel.qt.preferences:Error while invoking <bound method PreferencesPanel.load of <ubuntuone.controlpanel.gui.qt.preferences.PreferencesPanel object at 0x1968830>> with args () and kwargs {}:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/gui/qt/__init__.py", line 196, in inner
    res = yield f(*args, **kwargs)
IPCError: org.freedesktop.DBus.Error.Spawn.ChildExited: 
INFO:ubuntuone.controlpanel.qt.preferences:The warning dialog was shown and also closed (message was 'IPCError').
INFO:ubuntuone.controlpanel.backend:change_file_sync_settings: args (<ubuntuone.controlpanel.backend.ControlBackend object at 0x17f2c10>, {u'autoconnect': False, u'max_download_speed': -1, u'share_autosubscribe': False, u'max_upload_speed': 49152, u'show_all_notifications': False, u'udf_autosubscribe': True}), kwargs {}.
Unhandled error in Deferred:
Unhandled Error
Traceback (most recent call last):
Failure: ubuntuone.platform.tools.linux.IPCError: org.freedesktop.DBus.Error.Spawn.ChildExited: 

```

---

### Post by vasiliscnisrok on 2012-12-12
this is bug [https://bugs.launchpad.net/ubuntuone-client/+bug/936942](https://bugs.launchpad.net/ubuntuone-client/+bug/936942)

sorry offtopic, but your may remove warning
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.

command in Terminal
mkdir -p ~/.config/fontconfig
mv ~/.fonts.conf ~/.config/fontconfig/fonts.conf

---

### Post by bra|10n on 2012-12-12
Perhaps this workaround [COLOR=Blue]
[http://rtg.in.ua/2012/04/17/fixing-ipcerror-in-ubuntu-one/](http://rtg.in.ua/2012/04/17/fixing-ipcerror-in-ubuntu-one/)[/COLOR]

Also in OT suggestions, simply deleting the offending line9 is also an option. If you are yet to try Infinality fonts, I strongly suggest giving them a shot...
[http://www.infinality.net/blog/](http://www.infinality.net/blog/)

---

