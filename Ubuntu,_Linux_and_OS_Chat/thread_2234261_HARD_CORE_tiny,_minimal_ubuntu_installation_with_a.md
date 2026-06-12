---
title: "HARD CORE tiny, minimal ubuntu installation with any window manager"
date: 2014-07-13
forum: Ubuntu, Linux and OS Chat
---

### Post by patrikmellq on 2014-07-13
Pick a Ubuntu long time support server edition cd or iso file.
Then make the installation with out choosing any programs during the installation.

Now you get the basic minimal ubuntu system from scratch on your computer.
First you do is to enable UFW.

```

sudo ufw enable

```

After that you need to install Xorg to run a window manager.

```

sudo apt-get install xserver-xorg
sudo apt-get install xterm
sudo apt-get install xinit

```

Now you can pick any window manager you want.
For example fluxbox.

```

sudo apt-get install fluxbox

```

Now you have to write **startx** to run fluxbox.

If you want other window manager, for example Openbox.

```

sudo apt-get install openbox
sudo apt-get install opconf
sudo apt-get install obmenu

```

As you see you can pick any window manager you like as you have the minimal base system.

Now lets say you don't want to write **startx** each time to run your window manager.
Then you can install a minimum gui that will let you log in and automatic will run your window manager.

```

sudo apt-get install xdm

```

**Openbox** Main Page [http://openbox.org/](http://openbox.org/)

**Fluxbox** Main Page [http://fluxbox.org/](http://fluxbox.org/)

**Window Managers For X **Main Page [http://xwinman.org/](http://xwinman.org/)

---

### Post by patrikmellq on 2014-07-13
You need some light softwares to get started.
Here is one for internet with light gui.

[img]http://i44.tinypic.com/mrbevc.png[/img]

```

sudo apt-get install wicd

```

WICD [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by bapoumba on 2014-07-13
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by mastablasta on 2014-07-14
there is a minimal iso so you can just download that instead of server. saves some time and bandwidth. then...: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by ian-weisser on 2014-07-14
It would be slightly more minimal without ufw.
The firewall is provided by iptables, not ufw. And iptables is not difficult to use.

---

