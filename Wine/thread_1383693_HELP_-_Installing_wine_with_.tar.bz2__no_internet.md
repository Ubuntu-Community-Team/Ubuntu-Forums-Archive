---
title: "HELP - Installing wine with .tar.bz2 / no internet"
date: 2010-01-17
forum: Wine
---

### Post by Xog on 2010-01-17
How can i install wine with just the wine-1.1.35.tar.bz2 file? I have it on the computer via d/ling it on windows and saving to other partition..

I need wine to install the software for my wireless usb so i can connect to the internet

Im hoping theres a way to do it via software sources > other software and have it point to a specific directory? Can i do that? How?

Or can someone tell me where to extract the files? I can open the bz2 up and there's an extract button.. no install button :O

Also, would it be possible to install it while I'm on windows?

---

### Post by oedipuss on 2010-01-17
The tar.bz2 file must be the source package, and it needs to be compiled which can be somewhat complicated. There's no need to use it, instead try to get a deb of the version you want from : [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) matching your architecture (32 or 64 bit). Save that to a stick, and it can be installed from the ubuntu pc with a single click. (or maybe 2)


If on the other hand you absolutely have to use the tar file, there should be instructions inside it. Check for a README or INSTALL file. Generally, you extract it in a folder, and from a terminal cd to where it is extracted, run './configure' , 'make' , and 'make install' . There will be other packages needed to compile it, though, that's why it's generally considered complicated. And it kind of defeats the purpose here.

---

### Post by beastrace91 on 2010-01-17
To install form the source files (which is what is contained in the .gz folder) run the following as suggested above: ```
./configure
make
sudo make install
```

But note in order to configure/make you will need a pile of build depens (which can all be easily obtained via the internet with **sudo apt-get build-dep wine**.

Can I inquire as to why you do not have internet under Linux?

~Jeff

---

### Post by hikaricore on 2010-01-17
> **Xog said:**
> I need wine to install the software for my wireless usb so i can connect to the internet

Uhhmmm.... this probably isn't going to work.  WINE can not make use of windows based drivers and such.
Unless you're following a specific wireless driver guide for use with a wrapper this is bound for failure.

---

