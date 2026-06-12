---
title: "Virtualbox automatic starting of VM only partially works"
date: 2014-02-10
forum: Virtualisation
---

### Post by willebil on 2014-02-10
I am running Ubuntu 13.10 and Virtualbox 4.3.6. I have been struggling to get automatic starting of VM's working, this is what I have done. Created a user "tom" and a user "jerry". Before creating VM's on these user accounts, I have edit the default virtualbox configuration file and add the path to autostart database directory file and autostart configuration file to it.

[I][B]nano /etc/default/virtualbox
[/B][/I]
And added the following entries:
```
VBOXAUTOSTART_DB=/etc/vbox
VBOXAUTOSTART_CONFIG=/etc/vbox/vboxauto.conf

```
After this I specified the virtualbox user that is allowed to start VM.

***nano /etc/vbox/vboxauto.conf***

Add an entry for each user allowed to run autostart:
```

default_policy = deny
tom = {
allow = true
}
jerry = {
allow = true
}

```

In order vboxusers to write to the vbox directory, the permissions (and sticky bit) have been set.

```
chgrp vboxusers /etc/vbox
chmod 1775 /etc/vbox

```

Set the path to the autostart database directory for the user allowed above, command below have been repeated after logging into both accounts seperatly:

```
VBoxManage setproperty autostartdbpath /etc/vbox
Set VirtualBox to automatically start the VM (my-VM) when system starts up and poweroff it when system halts.
VBoxManage modifyvm my-VM –autostart-enabled on –autostop-type poweroff

```

After execution I have the **.start** and **.stop** files generated for both users, so far everyting is looking good. During booting I noticed that the startup script was aborted, to fix this you have to change the order over loading of the Virtualbox kernel modules, you do this as following:

```
[COLOR=#333333][FONT=Georgia]sudo update-rc.d -f vboxdrv remove[/FONT][/COLOR]
[COLOR=#333333][FONT=Georgia]sudo update-rc.d -f vboxdrv defaults 19[/FONT][/COLOR]
```

After the reboot I noticed that for the user "jerry" the VM's actially started automatically, but for the user "tom" nothing happened.

Manual execution of the startup script, either under the user account you have logged in or as super user (sudo) the script does actually do it's work for the "jerry" user, but for the user "tom" it only works when you execute the init script non-priveliged. So, when logged in as Tom the following commands do work:

```
[COLOR=#333333][FONT=Georgia]tom@system:$ /etc/init.d/vboxautostart-service start
[/FONT][/COLOR][COLOR=#333333][FONT=Georgia]tom@system:$ /etc/init.d/vboxautostart-service stop
[/FONT][/COLOR]
```[COLOR=#333333][FONT=Georgia]

but running them like this has no effect (and this behaviour is also preventing the VM to start during boot)
[/FONT][/COLOR]```
[COLOR=#333333][FONT=Georgia]tom@system:$ sudo /etc/init.d/vboxautostart-service start
[/FONT][/COLOR][COLOR=#333333][FONT=Georgia]tom@system:$ sudo /etc/init.d/vboxautostart-service stop[/FONT][/COLOR]
```

I am overlooking something, any ideas to fix this issue?

---

### Post by CharlesA on 2014-02-13
This would be a better question for the official virtualbox forums.

[http://forums.virtualbox.org/](http://forums.virtualbox.org/)

---

