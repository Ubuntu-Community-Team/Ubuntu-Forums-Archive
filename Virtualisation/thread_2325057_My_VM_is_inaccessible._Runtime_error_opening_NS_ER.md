---
title: "My VM is inaccessible. Runtime error opening NS_ERROR_FAILURE (0x80004005)"
date: 2016-05-18
forum: Virtualisation
---

### Post by PCManiac on 2016-05-18
[COLOR=#111111][FONT=Ubuntu]Hi, guys. I  tried to ask this on Ask Ubuntu and nobody seems to answer this problem. So, I'm going to tell here the problem.
 
I was trying to start up my VM, when suddenly I closed VirtualBox and opened it, it appeared this:

The selected virtual machine is *inaccessible*. Please inspect the error message shown below and press the **Refresh** button if you want to repeat the accessibility check:

Runtime error opening 
'/scra/home/davidbmelo/VirtualBox/VDI/Windows XP/Windows XP.vbox' for reading: -102 (File not found.).

/build/virtualbox-FD2cpk/virtualbox-4.1.44-dfsg/src/VBox/Main/src-server/MachineImpl.cpp[708] (nsresult Machine::registeredInit()).
Result Code:  NS_ERROR_FAILURE (0x80004005)
Component: VirtualBox
Interface: IVirtualBox {c28be65f-1a8f-43b4-81f1-eb60cb516e66}

Can someone tell me how do I fix this problem please?
BTW, the version I'm using on VirtualBox is 4.1.44.
[/FONT][/COLOR]

---

### Post by QIII on 2016-05-18
Hello!

Can you navigate to the directory/filename indicated and see if the file exists or not?

---

### Post by PCManiac on 2016-05-18
> **QIII said:**
> Hello!

Can you navigate to the directory/filename indicated and see if the file exists or not?

You mean like this? (see image in the Attached Thumbnails)

---

