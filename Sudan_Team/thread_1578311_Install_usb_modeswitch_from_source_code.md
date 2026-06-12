---
title: "Install usb_modeswitch from source code"
date: 2010-09-20
forum: Sudan Team
---

### Post by zero-n on 2010-09-20
[B]Installing [usb_modeswitch]("http://www.draisberghof.de/usb_modeswitch/") from source code:
[/B] The latest version now is 1.4.4 for usb_modeswitch & the latest data package released 2010-08-26 , so check usb_modeswitch website for the latest release.

1- Install dependencies:
```

sudo aptitude install libusb-dev

```2- Download usb_modeswitch & extract:
```

wget http://www.draisberghof.de/usb_modeswitch/usb-modeswitch-1.1.4.tar.bz2
tar -xvf usb-modeswitch-1.1.4.tar.bz2 

```3- Install usb_modeswitch:
```

cd usb-modeswitch-1.1.4
sudo make install

```4- Download & extract usb_modeswitch-data:
```

wget http://www.draisberghof.de/usb_modeswitch/usb-modeswitch-data-20100826.tar.bz2
tar -xvf usb-modeswitch-data-20100826.tar.bz2

```5- Edit Make file:
```

cd usb-modeswitch-data-20100826
sudo gedit  Makefile

```add the following two lines after [COLOR=Red]**RULESDIR    = $(DESTDIR)/lib/udev/rules.d**[/COLOR] :
```

UDEVDIR     = $(DESTDIR)/lib/udev 
UDEVDIR     = $(DESTDIR)/etc/udev

```6- Install usb_modeswitch-data:
```

sudo make files-install

```

---

### Post by rockbaaska on 2011-10-24
baaska@ubuntu:~/usb-modeswitch-1.1.4$ cd usb-modeswitch-data-20111023
  baaska@ubuntu:~/usb-modeswitch-1.1.4/usb-modeswitch-data-20111023$ sudo gedit Makefile
  baaska@ubuntu:~/usb-modeswitch-1.1.4/usb-modeswitch-data-20111023$ sudo make files-install
  install -d /usr/share/usb_modeswitch
  install -d /etc/usb_modeswitch.d
  install -D --mode=644 40-usb_modeswitch.rules /lib/udev/rules.d/40-usb_modeswitch.rules


now how to run
[COLOR=#111111][FONT=&quot]mak@ubuntu:~$ sudo usb_modeswitch -I -c /etc/usb_modeswitch.d/0e8d:7109[/FONT][/COLOR][COLOR=#111111][FONT=&quot] [/FONT][/COLOR][COLOR=#111111][FONT=&quot]
 
 [/FONT][/COLOR]
 this is not running

---

