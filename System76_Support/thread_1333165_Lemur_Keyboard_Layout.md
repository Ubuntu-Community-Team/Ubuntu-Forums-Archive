---
title: "Lemur Keyboard Layout"
date: 2009-11-21
forum: System76 Support
---

### Post by jjacobs2 on 2009-11-21
Hi,
I used remastersys to install my software and settings from my other laptop onto the Lemur but when I rebooted the keyboard layout wasn't quite right.  Does anyone know the default layout for the Lemur?
Thanks,
Josh

---

### Post by thomasaaron on 2009-11-23
The Lemur uses the "Generic 105-key (Intl)" Layout.

---

### Post by thomasaaron on 2009-11-23
Hmmmm... I don't see anything in Synaptic Package Manager that would allow that configuration.

I know, you can download a debian package to your home directory and manually install it to a custom directory by using the --install=dir flag. Here's the dpkg man page entry on it...

--instdir=dir
              Change default installation directory which refers to the
              directory  where packages are to be installed. instdir is
              also the directory passed  to  chroot(2)  before  running
              package's  installation  scripts,  which  means  that the
              scripts see instdir as a root directory.  (Defaults to /)

There is a "Set Internal Option" option selection in Synaptic's menu. Perhaps that is what it is for.

Sorry, I don't know a whole lot about that.

---

### Post by jjacobs2 on 2009-11-24
[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)
This is what I was referring to.  It backs up files and settings from another computer in the form of an installable ubuntu iso.  It seemed to work fine aside from the keyboard problem so perhaps there's a bad config file it carried over.

---

