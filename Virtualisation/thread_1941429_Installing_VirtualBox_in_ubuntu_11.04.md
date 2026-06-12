---
title: "Installing VirtualBox in ubuntu 11.04?"
date: 2012-03-15
forum: Virtualisation
---

### Post by linktopower on 2012-03-15
Hello there, I was wondering...I have the [virtualbox-4.1_4.1.8-75467~Ubuntu~natty_i386.deb] File I was wondering is there a way to install it and all its dependencies at one time? If theres a way could someone tell me how or something?
 
Edit: I was thinking insted of running ubuntu in windows. What about doing the other way around ;)

---

### Post by howefield on 2012-03-15
I'm running the oneiric Virtualbox .deb package, seems to be running flawlessly.

There is a newer version than you have, by the way.

4.1.10 was released a couple of days ago.

---

### Post by linktopower on 2012-03-15
Oh so the vesion I have is out of date already?. 
 
The question is I have ubuntu 11.04 And when I go install it says there are dependencies missing. Is there a Command to install it and fetch the dependencies it needs?

---

### Post by howefield on 2012-03-15
There are fairly regular updates to Virtualbox, every 2 to 3 months. Might be worth downloading the newer natty version and trying again.

Try installing via the command line, probably give you a clue as to what is going wrong.

Open a terminal and type

```
sudo dpkg -i filename
```

Swap the real filename in the above.

---

### Post by linktopower on 2012-03-15
> **howefield said:**
> There are fairly regular updates to Virtualbox, every 2 to 3 months. Might be worth downloading the newer natty version and trying again.

Try installing via the command line, probably give you a clue as to what is going wrong.

Open a terminal and type

```
sudo dpkg -i filename
```Swap the real filename in the above.
Okay I've done that.

```
4.1.8-75467~Ubuntu~natty_i386.deb
Selecting previously deselected package virtualbox-4.1.
(Reading database ... 129818 files and directories currently installed.)
Unpacking virtualbox-4.1 (from virtualbox-4.1_4.1.8-75467~Ubuntu~natty_i386.deb) ...
dpkg: dependency problems prevent configuration of virtualbox-4.1:
 virtualbox-4.1 depends on libcurl3 (>= 7.16.2-1); however:
  Package libcurl3 is not installed.
 virtualbox-4.1 depends on libqt4-network (>= 4:4.5.3); however:
  Package libqt4-network is not installed.
 virtualbox-4.1 depends on libqt4-opengl (>= 4:4.7.0~rc1); however:
  Package libqt4-opengl is not installed.
 virtualbox-4.1 depends on libqtcore4 (>= 4:4.7.0~beta1); however:
  Package libqtcore4 is not installed.
 virtualbox-4.1 depends on libqtgui4 (>= 4:4.7.0~beta1); however:
  Package libqtgui4 is not installed.
dpkg: error processing virtualbox-4.1 (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for shared-mime-info ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Errors were encountered while processing:
 virtualbox-4.1

```See there is dependencies missing. Is there a way to install all the missing dependencies all at one go?
or do I have go download each one manually?

EDIT: Well never mind It seems ubuntu Software center is fixing the issue I guess I can call this solved

---

