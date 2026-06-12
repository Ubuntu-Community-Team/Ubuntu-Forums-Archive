---
title: "VirtualBox window disappears"
date: 2021-09-07
forum: Virtualisation
---

### Post by satimis on 2021-09-07
I follow
Method 2: Install VirtualBox from the Oracle Repositories
[https://linuxhint.com/install-virtualbox-linux/](https://linuxhint.com/install-virtualbox-linux/)

performing following steps to install VirtualBox

$ wget -q [https://www.virtualbox.org/download/oracle_vbox_2016.asc](https://www.virtualbox.org/download/oracle_vbox_2016.asc) -O- | sudo apt-key add -

$ sudo add-apt-repository "deb [arch=amd64] [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) $(lsb_release -cs) contrib"

$ sudo apt update

$ sudo add-apt-repository "deb [arch=amd64] [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) $(lsb_release -cs) contrib"

$ sudo apt install virtualbox-6.1

Installation went through without problem.

On -> Activities -> VirtualBox
VirtualBox starts but its window disappears

On Terminal run
$ which virtualbox```

/usr/bin/virtualbox

```

Please help.  Thanks

Regards

---

### Post by scorp123 on 2021-09-08
What happens if you open a terminal and try to launch Virtualbox from in there? Do any error messages get printed into the terminal?

So you'd open a terminal and type in:
```
/usr/bin/virtualbox

```

And let's see what happens, e.g. error messages should get printed there into the terminal. This might give clues about what's happening...

---

### Post by satimis on 2021-09-08
> **scorp123 said:**
> What happens if you open a terminal and try to launch Virtualbox from in there? Do any error messages get printed into the terminal?

So you'd open a terminal and type in:
```
/usr/bin/virtualbox

```

And let's see what happens, e.g. error messages should get printed there into the terminal. This might give clues about what's happening...
Thanks for your advice.

The PC is connected to 2 displays :-
Display-1  Samsung 24" display 1920x1080 resolution, HDMI connection
Display-2  Dell 32" 4K display, Display port connection.

Display-1 was not switched on during installing VirtualBox but its window disappeared after starting VirtualBox Manager gui.  After pulling out the HDMI cable of Display-1 its window popup on the screen.  I couldn't explain WHY?

Regards

---

