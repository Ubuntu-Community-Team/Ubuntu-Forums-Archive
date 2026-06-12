---
title: "Copy a VMware image."
date: 2008-02-28
forum: Virtualisation
---

### Post by indianballer24 on 2008-02-28
Is there any way to copy a VMware Server virtual machine to another computer that only has VMware Player?

---

### Post by fjgaude on 2008-02-28
Sure, just do it. Player actually has more features than Server but I don't think it will matter.

With different hardware you might have to do a re-config of the vm.

---

### Post by imT on 2008-02-28
> **fjgaude said:**
> Sure, just do it. 
+1

---

### Post by indianballer24 on 2008-02-28
> **fjgaude said:**
> Sure, just do it. Player actually has more features than Server but I don't think it will matter.

With different hardware you might have to do a re-config of the vm.
One more question, How do I make a image in WMware Player?

---

### Post by HermanAB on 2008-02-28
The easiest way is to shut the VM down and make a tar ball of the VM directory.

---

### Post by fjgaude on 2008-02-28
> **indianballer24 said:**
> One more question, How do I make a image in WMware Player?

I usually just drag-and-drop from one computer to the next, if I'm on a fast link. But like said by HermanBB, a tarball makes the whole directory file smaller, much smaller, than the raw directory, whatever it was called by you on first install.

Let us know how you do.

---

### Post by indianballer24 on 2008-02-28
> **fjgaude said:**
> I usually just drag-and-drop from one computer to the next, if I'm on a fast link. But like said by HermanBB, a tarball makes the whole directory file smaller, much smaller, than the raw directory, whatever it was called by you on first install.

Let us know how you do.
What directory do I make a tarball of. Where do I copy it to. Are there any compatibility issues?

---

### Post by fjgaude on 2008-02-28
You can copy it to any directory and then when you open Player point to that directory. I put all mine in my /home/frank directory.

You make tarball, copy the entire folder that the Server made for the virtual machine. The default directory is /var/lib/vmware-server/Virtual Machines. The folder to tarball and copy to your Player is in Virtual Machines. It will have the name you gave to the vm.

Let us know how things are going.

---

### Post by iheartubuntu on 2008-03-22
Im trying to do this right now too, whether it be copy the directory that has the image file, or copying the file itself, I cant do this because I dont have the permission to because all the files are stored in root. How do I get around this? Im the only user on my system. Thanks

---

### Post by iheartubuntu on 2008-03-22
I figured it out. Here is what I did:

go into terminal, type in:

> sudo nautilus

Key in your password and this puts you as the root user, then go into your vmware folder... mine was in usr/lib/vmware-server/Virtual Machines/  then right click on the folder you want to copy and click properties, then permissions, then on all the file access, i changed the choices to "read and write". Make sure to click the "apply permission to enclosed files" before clicking OK.

I was then able to tar the directory and burn the tar to disc.

---

