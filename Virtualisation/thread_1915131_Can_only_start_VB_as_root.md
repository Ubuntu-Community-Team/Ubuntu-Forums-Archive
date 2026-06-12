---
title: "Can only start VB as root"
date: 2012-01-25
forum: Virtualisation
---

### Post by Julian David Pitt on 2012-01-25
When I start Virtual Box as myself I get this:

```
Failed to create the VirtualBox COM object.

The application will now terminate.



Start tag expected, '&lt;' not found.

Location: '/home/julian/.VirtualBox/VirtualBox.xml', line 1 (0), column 1.

/home/vbox/vbox-4.1.8/src/VBox/Main/src-server/VirtualBoxImpl.cpp[485] (nsresult VirtualBox::init()).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: VirtualBox
Interface: IVirtualBox {c28be65f-1a8f-43b4-81f1-eb60cb516e66}

```

Can anyone please tell me how this can be rectified please

---

### Post by carl4926 on 2012-01-25
Try deleting the xml file
/home/julian/.VirtualBox/VirtualBox.xml

And try it again

---

### Post by CharlesA on 2012-01-26
> **carl4926 said:**
> Try deleting the xml file
/home/julian/.VirtualBox/VirtualBox.xml

And try it again
That should fix it, but it might reset the list of VMs that are installed. Not sure.

---

### Post by Julian David Pitt on 2012-01-26
Hi Charles
That fixed it alright thanks mate, the only problem now is how to do get access to the VM's I previously created as root. Do you know if I can import them back in or will I get permission problems? Thanks again.

---

### Post by CharlesA on 2012-01-26
You would have to run vbox as root, export those VMs and import them under your normal user. After that is done you can delete them from the root user's home directory.

---

