---
title: "Getting errors installing Lubuntu in VirtualBox"
date: 2015-10-25
forum: Virtualisation
---

### Post by cody27 on 2015-10-25
I'm trying to install Lubuntu in VirtualBox in Windows so I can use both at the same time. But I'm getting an error from VirtualBox. This could be from when I was trying to install OSX in VirtualBox, I was just messing around and didn't really understand what I was doing. But after messing with a bunch of the settings I'm still getting the error.

The error happens when I try to find the Lubuntu iso, I'm not even in the os yet.

The error is: 
```

Failed to open a session for the virtual machine Lubuntu 15.04.

The VM session was aborted.

Details:

Result Code: E_FAIL (0x80004005)
Component: SessionMachine
Interface: ISession {12f4dcdb-12b2-4ec1-b7cd-ddd9f6c5bf4d}

```

I've done some googling but I couldn't find any solutions for this. It could be due to my little experience though. 

Thanks for any help.

---

### Post by ajgreeny on 2015-10-25
have you followed all the instructions at [https://www.virtualbox.org/manual/ch01.html#gui-createvm?](https://www.virtualbox.org/manual/ch01.html#gui-createvm?)

I no longer run Windows except in VBox as a VM, so I am not sure if the instructions shown at the above link are the same as when I do this in a Linux host.  In particular see the paragraphs below which may help you:-
> If you have downloaded installation media from the Internet in the form of an ISO image file (most probably in the case of a Linux distribution), you would normally burn this file to an empty CD or DVD and proceed as just described. With VirtualBox however, you can skip this step and mount the ISO file directly. VirtualBox will then present this file as a CD or DVD-ROM drive to the virtual machine, much like it does with virtual hard disk images.

For this case, the wizard's drop-down list contains a list of installation media that were previously used with VirtualBox.

If your medium is not in the list (especially if you are using VirtualBox for the first time), select the small folder icon next to the drop-down list to bring up a standard file dialog, with which you can pick the image file on your host disks.

I see no reason why having tried to install OSX should have any effect on this problem, but I suppose it may depend on what exactly went wrong that time.

If this does not make sense come back again with more information and questions.

---

