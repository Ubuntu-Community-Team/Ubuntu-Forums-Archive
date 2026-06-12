---
title: "How to make XP on Vbox autoload in Ubuntu?"
date: 2010-08-14
forum: Virtualisation
---

### Post by Copperred on 2010-08-14
.see below.

---

### Post by Copperred on 2010-08-15
Ok............ I have figured out how to make it AUTOLOAD......thank you Ubuntu Forums!

Second question remains:

2.)   assuming the XP machine is up and running, is there a way to associate   files on the Ubuntu system with programs resident on the XP machine?    (ie. I click a .doc file on Ubuntu and it loads up on MSWORD in the XP   machine)

---

### Post by JustinR on 2010-08-15
> **Copperred said:**
> Ok............ I have figured out how to make it AUTOLOAD......thank you Ubuntu Forums!

Second question remains:

2.)   assuming the XP machine is up and running, is there a way to associate   files on the Ubuntu system with programs resident on the XP machine?    (ie. I click a .doc file on Ubuntu and it loads up on MSWORD in the XP   machine)

System > Preferences > Startup Applications
```

VBoxManage start VM

```

2nd Question:
There isn't a native way of doing that as far as I know - you would probably have to script it.

---

### Post by Copperred on 2010-08-16
Can it be scripted?   Is it possible?      

I'd like to do 3 things:

1.) associate .doc, .ppt and .xls files that reside on the host Ubuntu to to the appropriate MS Office application (Word, PP, Excel) that resides on the virtual XP;

2.) associate email addresses in the Ubuntu OS (in Firefox, etc.) to MS Outlook residing on the virtual XP OS;

3.) associate http internet links in the virtual XP OS (in MS Office, etc) to Firefox residing on the Ubuntu OS host.

Any uber-uber-Scripters out there want to work with me on this?

The goal is clearly ubiquity....but the whole script package would go a LONG LONG way in bringing more and more windows people to Ubuntu.......would bring allot of corporate users too.

---

### Post by TheFu on 2010-08-16
> **Copperred said:**
> Can it be scripted?   Is it possible?      

I'd like to do 3 things:

1.) associate .doc, .ppt and .xls files that reside on the host Ubuntu to to the appropriate MS Office application (Word, PP, Excel) that resides on the virtual XP;

2.) associate email addresses in the Ubuntu OS (in Firefox, etc.) to MS Outlook residing on the virtual XP OS;

3.) associate http internet links in the virtual XP OS (in MS Office, etc) to Firefox residing on the Ubuntu OS host.

Any uber-uber-Scripters out there want to work with me on this?

The goal is clearly ubiquity....but the whole script package would go a LONG LONG way in bringing more and more windows people to Ubuntu.......would bring allot of corporate users too.

While scripting a startup for a VM may be possible, unless you are full of RAM, each instance would run a new VM, which is extremely heavy for 99.999% of us to consider.  Or you'll need to use inter-machine communication - which I've done before for commercial apps. When we did this, it took 2 full time C++ developers about 6 weeks to accomplish for 2 very specific apps to talk in about 10 EXTREMELY SPECIFIC use cases. We had the source code for 1 app and the other app (CAD) had remote control built-into it using named-pipes. I'm certain it is easier now, but still non-trivial.  I'd start with a named pipe available to both OSes via file system sharing or use Tk.

Instead, perhaps loading MS-Office into WINE under Ubuntu would make more sense, then the scripting becomes easier. I run Office 2003 under WINE and it mostly works. For me, it is faster than running under a native Win7 install too.

I could be an old foggy and perhaps some young coder can whip up a 2-way interface in a few hours. OTOH, don't underestimate the amount of effort that just a single OS goes thru to make what you want appear seamless.

---

### Post by Copperred on 2010-08-16
Thanks Fu for the idea....I was running Word 07 under Wine for a while..it had about 80% functionality......and none of the other Office apps worked at all...nada.  

What I have found is this (someone beat us to it ;) :

[http://plumnash.com/it/virtualbox-enhancement-for-opening-winxp-applications](http://plumnash.com/it/virtualbox-enhancement-for-opening-winxp-applications)[SIZE=3]
  
VirtualBox Enhancement for Opening WinXP Applications[/SIZE]  

This  guide explains how to open Microsoft Word Files from an Ubuntu host in  Microsoft Word using a Windows XP Virtual Machine. In fact, this  mechanism can be used to open lots of file types in seamlessly in any  Guest from any Host. This extensions builds upon the seamless  integration provided by VirtualBox to create a more convenient user  interface for using multiple operating systems in parallel.

---

