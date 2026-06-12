---
title: "Removing ubuntu-desktop and gnome-shell on Ubuntu Server 16.04."
date: 2017-01-07
forum: Server Platforms
---

### Post by sethanath2 on 2017-01-07
Hi,

I am a first timer using server, so I need a small desktop for now. I used the following commands for trying multiple desktop on the server.

 ```
$ sudo apt install --no-install-recommends gnome-shell
$ sudo apt install --no-install-recommends ubuntu-desktop
```

However, the following desktop is best for me.

```
$ sudo apt install --no-install-recommends ubuntu-gnome-desktop
```

I tried removing the first two DEs, but I am still be able to choose them from the login prompt. 

```
$ sudo apt remove gnome-shell
$ sudo apt remove ubuntu-desktop
```

I hope someone can help.

---

### Post by deadflowr on 2017-01-07
Not sure about gnome-shell, but ubuntu-desktop is only a meta-package which itself is needed to install the actual desktop environment packages for Ubuntu.
which is the unity interface and all the trimmings.
Removing that package only removes that package.
I believe if you run the autoremove command it should list all the related packages that the system would now deem unneeded.
which would consist of those packages the meta-package was used to install.
```
sudo apt-get autoremove
```
Be prepared as it should be a rather fat list.
And may or may not include packages you still want to use.
Review the list.
You always have the option to click n to abort the autoremove command before it starts actually removing anything.

---

### Post by sethanath2 on 2017-01-08
Thank you so much.

---

