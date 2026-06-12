---
title: "Programmes and File System"
date: 2014-08-02
forum: Ubuntu, Linux and OS Chat
---

### Post by anon_private on 2014-08-02
How can I locate a programme in the file system.

For example, if I wanted to know where Libre Office  Writer is installed, how would I go about this?

Thanks

---

### Post by sudodus on 2014-08-02
```
which libreoffice
```

---

### Post by 3rdalbum on 2014-08-02
Why do you want to know?

You can find out where all the Libreoffice files are by using Synaptic Package Manager. Right-click the package in Synaptic, click Properties, and then click the "Installed Files" tab.

I find that people often ask that question in an attempt to solve a different problem (and the answer to the question doesn't actually help). If you tell us the problem you are actually having, you might get a better reply. One that will make things easier for you!

---

### Post by anon_private on 2014-08-02
> **sudodus said:**
> ```
which libreoffice
```

3

> **3rdalbum said:**
> Why do you want to know?

You can find out where all the Libreoffice files are by using Synaptic Package Manager. Right-click the package in Synaptic, click Properties, and then click the "Installed Files" tab.

I find that people often ask that question in an attempt to solve a different problem (and the answer to the question doesn't actually help). If you tell us the problem you are actually having, you might get a better reply. One that will make things easier for you!

I cannot see Synaptic Package Manager, but then I am using Ubuntu from a live pendrive.

I am not attemting to solve a probelm, but am trying to understand the system.

---

### Post by coffeecat on 2014-08-02
> **anon_private said:**
> 3

Sudodus wasn't asking you which version of LibreOffice you have. Sudodus' post was the terminal code that will answer the question in your first post.

---

### Post by anon_private on 2014-08-02
> **coffeecat said:**
> Sudodus wasn't asking you which version of LibreOffice you have. Sudodus' post was the terminal code that will answer the question in your first post.

Thank you for the clafication.

It does not seem to work for say document viewer, i.e, which document viewer; with or without quotes ( ' or ").

---

### Post by sudodus on 2014-08-02
Sorry for the misunderstanding. You can use ***which*** with a list of programs, that you want to find for example

```
[COLOR=#0000cd]which libreoffice ls tune2fs update-grub[/COLOR]      
/usr/bin/libreoffice
/bin/ls
/sbin/tune2fs
/usr/sbin/update-grub
```

where you see typical directories, where linux programs are stored.

---

### Post by sudodus on 2014-08-02
The document viewer has a system name, ***evince***

```
[COLOR=#0000cd]which evince[/COLOR]
/usr/bin/evince
```

---

### Post by anon_private on 2014-08-02
> **sudodus said:**
> Sorry for the misunderstanding. You can use ***which*** with a list of programs, that you want to find for example

```
[COLOR=#0000cd]which libreoffice ls tune2fs update-grub[/COLOR]      
/usr/bin/libreoffice
/bin/ls
/sbin/tune2fs
/usr/sbin/update-grub
```

where you see typical directories, where linux programs are stored.


My fault rather than yours

---

### Post by SeijiSensei on 2014-08-02
If you want to understand how things are arranged in the Linux file system, you might start with this: [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by SeijiSensei on 2014-08-02
If you want to understand how things are arranged in the Linux file system, you might start with this: [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

Most programs are stored in /usr/bin, but a few are in /bin, /sbin, and /usr/sbin.  The "**s**bin" directories contain programs used by the "**s**upervisor" or "root" user.

---

### Post by obake2 on 2014-08-03
It sounds like you want to learn more about Linux.
There is free class offered online that you could try :D

[http://arstechnica.com/information-technology/2014/03/2400-introduction-to-linux-course-will-be-free-and-online-this-summer/](http://arstechnica.com/information-technology/2014/03/2400-introduction-to-linux-course-will-be-free-and-online-this-summer/)

[https://www.edx.org/course/linuxfoundationx/linuxfoundationx-lfs101x-introduction-1621](https://www.edx.org/course/linuxfoundationx/linuxfoundationx-lfs101x-introduction-1621)

---

### Post by 3rdalbum on 2014-08-04
> **anon_private said:**
> I cannot see Synaptic Package Manager, but then I am using Ubuntu from a live pendrive.

I am not attemting to solve a probelm, but am trying to understand the system.

Synaptic is not on the ISO, you would have to install it. (From Ubuntu Software Center or "sudo apt-get install synaptic"). You can install it on the USB but it might not persist after reboot.

---

