---
title: "VirtualBox issue adding vmdk file"
date: 2009-10-20
forum: Virtualisation
---

### Post by Rhetoric Camel on 2009-10-20
Hello everyone, sorry for this question, couldn't find an answer. I've been following this tutorial on setting up VirtualBox: [http://anderstornvig.dk/2008/06/03/running-existing-windows-in-virtualbox-on-ubuntu/](http://anderstornvig.dk/2008/06/03/running-existing-windows-in-virtualbox-on-ubuntu/)

I'm doing good until I get down to the section labeled "Create The Machine In VirtualBox"
I put in this code:
```
$ sudo chown [username] .VirtualBox/WindowsXP.vmdk .VirtualBox/WindowsXP-pt.vmdk

```
and it works because I see it when I go into VirtualBox add and open the WindowsXP.VMDK. But when I open it I get this error message

```
Failed to open the hard disk /home/rhetoriccamel/.VirtualBox/WindowsXP.vmdk.
Could not open the hard disk '/home/rhetoriccamel/.VirtualBox/WindowsXP.vmdk'.
VD: error opening image file '/home/rhetoriccamel/.VirtualBox/WindowsXP.vmdk' (VERR_ACCESS_DENIED).
```
and under the Details Tab:
```

Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
HardDisk
Interface: 
IHardDisk {62551115-83b8-4d20-925f-79e9d3c00f96}
Callee: 
IVirtualBox {3f4ab53a-199b-4526-a91a-93ff62e456b8}

```

I have no idea what this is... now earlier on in the tutorial it had me download and extract MerdgeIDE-tools and I downloaded, extracted then I clicked on the MerdgeIDE.bat file and it did what it had to do then the black box disappeared. Was I supposed to do anything with the .reg file also included in the zip? If so that's probably what I didn't do, and if I go back and I add that do I have to redo any of the steps I've done or just pick up where I left off?

Hopefully I didn't type this in a scatter brain fashion since I am a scatter brain and all. Thanks ahead of time for any help... hopefully.

---

### Post by Dedoimedo on 2009-10-21
Permissions ...?

Did you use this virtual machine in other OS or by other users?
Make sure you have the permission to access the directory and the files you want.

Make sure the directory is also readable and accessible, not just the files underneath.

Regards,
Dedoimedo

---

### Post by Rhetoric Camel on 2009-10-21
all this is is a copy of my windows that I used before I used linux, not password protected didn't see anything about permissions in the instructions I was following. Just did them to the T and then got stuck once I tried adding this to virtualbox.

---

### Post by Rhetoric Camel on 2009-10-23
was I supposed to copy something from windows after making a copy of my Hardware Profile? I copied the one that was in there and named the other one VirtualBox Boot, like the instructions said and after I booted right back into windows and went on with the instructions. Is something missing in this section? I'm completely lost.

---

