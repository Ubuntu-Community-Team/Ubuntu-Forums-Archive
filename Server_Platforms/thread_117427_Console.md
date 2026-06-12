---
title: "Console"
date: 2006-01-14
forum: Server Platforms
---

### Post by Azion on 2006-01-14
Hey,
Just installed Ubuntu Server, but all I have is the terminal.
Is there anyway of installing gnome/kde or is it just terminal?

---

### Post by adwait on 2006-01-14
You can install whatever you want with
```
sudo apt-get install <program name>
```

In this case it would be either (for gnome)
```
sudo apt-get install ubuntu-desktop
```

or (for kde)
```
sudo apt-get install kubuntu-desktop
```

---

### Post by Azion on 2006-01-14
It says " Couldn't find package"

---

### Post by adwait on 2006-01-15
Is you /etc/apt/sources.list proper? Try running
```
sudo apt-get update
```

---

### Post by imagine on 2006-01-15
The main difference between the normal install and the server install is that the server has no X server/desktop environment. So instead of first picking the server install and then installing ubuntu-desktop you could have just used the normal install.

---

### Post by bobyang on 2006-01-15
you probably need to edit /etc/apt/source.list file, after installed ubuntu server, by default, the apt source is cdrom

---

### Post by Azion on 2006-01-16
Thing is imagine, I want to use it for a server!!!
Hence the forum!

Thanks for the suggestions guys I'll give them a shot

---

