---
title: "[HOWTO] disable touchpad when external usb mouse is connected"
date: 2011-02-04
forum: Tutorials
---

### Post by raffamaiden on 2011-02-04
**-Introduction**

In this tutorial I will explain a simple way to disable the touchpad when an external mouse is connected to your computer. I have been inspired by [http://ubuntuforums.org/showthread.php?t=1629433](http://ubuntuforums.org/showthread.php?t=1629433)
but the tecnique showed here is simpler and should work with any kind of mouse of any producer, and not only for a specific mouse.

**-What we need**

To reach our goals we need halevt and synclient. Halevt is a daemon that can execute an action when HAL events occur. Connecting a mouse triggers a HAL event  Synclient is a program that let us set touchpad properties, like the enabled/disabled properties. Our goal is to call synclient when halevt intercept a mouse-inserted or mouse-removed event (these are just self-explanatory name invented by me, they are not used by halevt).

The halevt package shipped in ubuntu repositories currently is too old (0.1.5). We need to retrieve a new version (at least 0.1.6.2). This new version fix a bug that make halevt crash. If we use the ubuntu-repositories version, our application we won't work and crash.

**-Steps**

First off, we need to install synclient. we will do it with

```

sudo apt-get install xserver-xorg-input-synaptics

```We need to uninstall all previous halevt packages before compiling the new one. Do it with:

```

sudo apt-get purge halevt

```Then we retrieve the source of the new version of halevt. We will retrieve version 0.1.6.2 which is the latest version as I write this tutorial. You can search if a later version exist by clicking [here]("http://www.nongnu.org/halevt/")

```

wget http://savannah.nongnu.org/download/halevt/halevt-0.1.6.2.tar.gz

```Extract it with:

```

tar -xvf halevt-0.1.6.2.tar.gz

```Go into the extracted directory

```

cd halevt-0.1.6.2

```And the compile and install it

```

./configure && make && sudo make install

```Now we need to create the configuration file for halevt. We create it as a hidden file under the user home directory. We do it with

```

touch ~/.halevt.xml
gedit ~/.halevt.xml

```Copy and paste this into the file:

```

<?xml version="1.0" encoding="UTF-8"?>
<halevt:Configuration version="0.1" xmlns:halevt="http://www.environnement.ens.fr/perso/dumas/halevt.html">
    <halevt:Device match="hal.info.capabilities = input.mouse &amp;  hal.input.originating_device.hal.linux.subsystem = usb">
        <halevt:Insertion exec="synclient TouchpadOff=1"/>
        <halevt:Removal exec="synclient TouchpadOff=0"/>
    </halevt:Device>
</halevt:Configuration>

```And then save and close it. Now you can run halevt with:

```

halevt -c ~/.halevt.xml

```A message like this should appear:

> 
manager.c:357 (main) Using configuration file ~/.halevt.xml
Now try to insert and remove your external USB mouse. The touchpad should be enabled/disabled according.

**-Make the modification permanent**

Every time you log in you need to run the halevt command above for these to work properly.
To automatize this, we need to create two files under the same directory.

First we create disabletpd

```

gedit disabletpd

```And copy and paste that into it:
```

#!/bin/sh

### BEGIN INIT INFO
# Provides:          disabletpd
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Run halevt with ~/.halevt.xml configuration file
# Description:       Activate\deactivate touchpad when external USB mouse is connected
### END INIT INFO

case $1 in
start)
  synclient TouchpadOff=0
  start-stop-daemon --exec /usr/local/bin/halevt --start -- -c ~/.halevt.xml  ;;
stop)
  start-stop-daemon --exec /usr/local/bin/halevt --stop ;;
*)
  echo "Not a valid parameter";;
esac

```Save and exit. Then we create install_disabletpd.sh

```

gedit install_disabletpd.sh

```And copy and paste this into it:

```

#!/bin/bash

if [ $# != 1 ]; then
  echo "You have to pass only one option, which can be 'on' or 'off'"
  exit 1
fi

if [ $1 = 'on' ]; then
    sudo cp ./disabletpd /etc/init.d/disabletpd
    sudo update-rc.d disabletpd defaults
    /etc/init.d/disabletpd stop
    /etc/init.d/disabletpd start
    echo "Disabling touchpad installed"

elif [ $1 = 'off' ]; then
    /etc/init.d/disabletpd stop
    sudo rm /etc/init.d/disabletpd
    sudo update-rc.d -f disabletpd remove
    echo "Disabling touchpad uninstalled"

else
    echo "Invalid option"
    exit 1
fi

```Save and exit. It doesn't matter where you put disabletpd and install_disableptd.sh as long as they are in the same directory. Now, if you are not in the directory which contains the two files, cd into it:

```

cd /directory/in/which/you/have/the/files

```and run

```

./install_disabletpd.sh on

```This will make the halevt command run automatically at every startup

**-Reverse the change**

To reverse the last change, just run

```

./install_disabletpd.sh off

```This will prevent halevt running at next startup.

**-What with a non-USB mouse**

If you have a non-USB mouse (like a PS2 one), you can try using the following halevt.xml:

```

<?xml version="1.0" encoding="UTF-8"?>
<halevt:Configuration version="0.1" xmlns:halevt="http://www.environnement.ens.fr/perso/dumas/halevt.html">
    <halevt:Device match="hal.info.capabilities = input.mouse">
        <halevt:Insertion exec="synclient TouchpadOff=1"/>
        <halevt:Removal exec="synclient TouchpadOff=0"/>
    </halevt:Device>
</halevt:Configuration>

```Ask here if you should encounter any problem.

---

### Post by poitiers on 2011-02-23
Thanks for your effort, raffamaiden.

Indeed my dmesg showed halevt 0.1.5 segfaulting under maverick. For other newbies like myself let me add that in order to install the newer version (0.1.6.2), I had to add libxml-dev, boolstuff-dev, libdbus-glib-1-dev (+dependencies), libhal-dev.

And I was elated for several seconds, before the touchpad began to work again. I hate it SO much and can't find a way to permanently switch off the ** thing. Aparently some events reset the TouchpadOff back to 0. If I invoke "synclient TouchpadOff=1" several times in a row and if I'm lucky, the touchpad gets switched off. But then it comes back after a while anyway, as if from a keypress.

Any hints? I noticed that the [original tutorial]("http://ubuntuforums.org/showthread.php?t=1629433") used a different way of switching the touchpad off (not via synclient) and that it mentioned "a bug that re-enabled the touchpad immediately after disabling it".

Has anyone tried the way described here or am I the first to do that? Thanks.

---

### Post by timm625 on 2012-02-09
Thanks for this! Huge help for a super annoying problem. Only issue i ran into, and you may want to add a step in to fix, was setting the last .sh files to be executable

---

### Post by brallan on 2012-05-02
well, didn't work for me in 12.04, but these three commands did:

> [COLOR=red]sudo add-apt-repository ppa:atareao/atareao[/COLOR][COLOR=red]
sudo apt-get update[/COLOR][COLOR=red]
sudo apt-get install touchpad-indicator[/COLOR]

then just run touchpad-indicator from application launcher...
[COLOR=red][/COLOR]

---

### Post by brallan on 2012-05-02
removed.... see above

---

### Post by debashishone on 2012-05-09
> **brallan said:**
> well, didn't work for me in 12.04, but these three commands did:

> [COLOR=red]sudo add-apt-repository ppa:atareao/atareao[/COLOR][COLOR=red]
sudo apt-get update[/COLOR][COLOR=red]
sudo apt-get install touchpad-indicator[/COLOR]

then just run touchpad-indicator from application launcher...



Yeah, you're right I was about to post the same until I saw your reply. Thanks that you shared.

---

