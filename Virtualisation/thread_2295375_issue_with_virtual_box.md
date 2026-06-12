---
title: "issue with virtual box"
date: 2015-09-18
forum: Virtualisation
---

### Post by hieu5 on 2015-09-18
Everything worked fine yesterday and now when I start it up I get this error message.
[ATTACH=CONFIG]264484[/ATTACH]

---

### Post by Bucky Ball on 2015-09-18
*Thread moved to **Virtualisation**.*

Welcome. Not related to ***Desktop Environments***. More luck here. :)

---

### Post by flocculant on 2015-09-18
so check the virtual manager - ctrl +d here

and see what it says :)

---

### Post by slickymaster on 2015-09-18
Hi hieu5, welcome to the forums

The message you're getting could be related to several issues, like the file system not being mounted or the file system being mounted as read-only or a corrupted virtualbox config file.

---

### Post by hieu5 on 2015-09-18
Gonna have to guide me through this cause I have no idea what's going on. There appears to be something wrong with the samsung galaxy disk 2 file.
[ATTACH=CONFIG]264485[/ATTACH]

---

### Post by flocculant on 2015-09-18
aah yes - I didn't notice in the first screeny - it says the file is inaccessible. 

The virt manager would likely say the same if you had it highlighted.

So - run back over what you did yesterday to that virtual machine. 

Check that the file actually does still exist where you expect it too.

---

### Post by hieu5 on 2015-09-18
I checked and it exists. I didn't really do anything differently yesterday than I did today, it just sort of happened.  Perhaps it's corrupted like slickymaster says?

---

### Post by slickymaster on 2015-09-18
Can you please post a screenshot of the Virtual Media Manager with the Samsung Galaxy disk 2 file selected?

---

### Post by hieu5 on 2015-09-18
Here you go
[ATTACH=CONFIG]264486[/ATTACH]

---

### Post by flocculant on 2015-09-18
> **hieu5 said:**
> Here you go
[ATTACH=CONFIG]264486[/ATTACH]

Can you fix that please ;)

---

### Post by hieu5 on 2015-09-18
That was weird. I uploaded the same way I did the other 2.
[ATTACH=CONFIG]264487[/ATTACH]

---

### Post by flocculant on 2015-09-18
You could also try to remove the virtual disk, then re-add it. If there is an issue you should get a warning - give the WHOLE thing to us here.

---

### Post by hieu5 on 2015-09-18
Can you tell me where to go to do that?

---

### Post by slickymaster on 2015-09-18
> **hieu5 said:**
> Can you tell me where to go to do that?

Before doing what flocculant suggested, which you might end up doing, try to release it. Just select the file in question and click the **Release** button.

---

### Post by hieu5 on 2015-09-18
Alright, I just released it. It's not attached to anything now.

---

### Post by hieu5 on 2015-09-18
So I just removed it and tried to re-add but then it says failed to open hard disk:

Failed to open the hard disk file **C:\Users\Titor\VirtualBox VMs\Samsung Galaxy S4 - 4.3 - API 18 - 1080x1920\Samsung Galaxy S4 - 4.3 - API 18 - 1080x1920-disk2.vmdk**.
Could not get the storage format of the medium **'C:\Users\Titor\VirtualBox VMs\Samsung Galaxy S4 - 4.3 - API 18 - 1080x1920\Samsung Galaxy S4 - 4.3 - API 18 - 1080x1920-disk2.vmdk'** (VERR_NOT_SUPPORTED).
[TABLE="width: 100%"]
[TR]
[TD]Result Code: [/TD]
[TD]VBOX_E_IPRT_ERROR (0x80BB0005)[/TD]
[/TR]
[TR]
[TD]Component: [/TD]
[TD]Medium[/TD]
[/TR]
[TR]
[TD]Interface: [/TD]
[TD]IMedium {05f2bbb6-a3a6-4fb9-9b49-6d0dda7142ac}[/TD]
[/TR]
[TR]
[TD]Callee: [/TD]
[TD]IVirtualBox {fafa4e17-1ee2-4905-a10e-fe7c18bf5554}[/TD]
[/TR]
[TR]
[TD]Callee RC: [/TD]
[TD]VBOX_E_OBJECT_NOT_FOUND (0x80BB0001)[/TD]
[/TR]
[/TABLE]

---

### Post by slickymaster on 2015-09-18
> **hieu5 said:**
> Alright, I just released it. It's not attached to anything now.
Create a new Virtual Machine and when it asks for a hard disk choose "Use an existing hard disk" and click on the "button with folder and green arrow image on the combo box right" which opens Virtual Media Manager, and then you can add the VMDK hard disk image and setup it for your virtual machine.

---

### Post by hieu5 on 2015-09-18
> **slickymaster said:**
> Create a new Virtual Machine and when it asks for a hard disk choose "Use an existing hard disk" and click on the "button with folder and green arrow image on the combo box right" which opens Virtual Media Manager, and then you can add the VMDK hard disk image and setup it for your virtual machine.
I tried to re-add it but an error message shows up that says the file is inacessible.

---

### Post by hieu5 on 2015-09-19
I figured it out. I looked in the virtual box folders and apparently their were 2 folders for the samsung and for some reason it switched folders for the disk 2 file.

---

