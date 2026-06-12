---
title: "How to install Windows 7 in Vmware server"
date: 2011-09-15
forum: Virtualisation
---

### Post by halovivek on 2011-09-15
Hi
I have successfully installed the Vmware server in ubuntu 11.04.
I could not able to install the windows.
I do have the ISO image stored in a separate partition.
I have given the file path location, and error message comes file not found.
I could not able to map it to use the image for installation.
can you please help me ?

Note:- I do have the licensed version of Windows 7.  
please see the attachment for the problem

---

### Post by halovivek on 2011-09-15
Adding one more point.
i have given the file path to the location also.
/media/vivek/iso/<filename> 

its not taking and says file path not found.

I have mounted the disk also before giving the file path.

---

### Post by varunendra on 2011-09-16
Hello Vivek,

[LEFT]By location of the path you mentioned, I doubt if it is a valid path. It seems to me that perhaps you are trying to mount the iso first, then use its 'mount' path as the target in VM Server. Usually, the /media directory contains the mounted media, not a usual user-file.

So I'd like to know how did you get or create the iso file, and where have you kept it. Try to move it to your home directory and then use that path in VM server. For example, if the file is named "win7.iso", then after moving it to your home directory (say, /home/vivek), its path will be - **/home/vivek/win7.iso**.
[/LEFT]

---

### Post by dcstar on 2011-09-27
> **halovivek said:**
> Hi
I have successfully installed the Vmware server in ubuntu 11.04.
.........

Do you really want to use Server, it is basically an obsolete product now?

If you just want to use other OSs on your system, use VMWare Player.

---

### Post by HermanAB on 2011-09-27
Hrrmm...  I second the VMware Player suggestion.

VMware Server should not be lightly discarded.  It should the thrown, with great force.

---

### Post by CharlesA on 2011-09-27
> **HermanAB said:**
> Hrrmm...  I second the VMware Player suggestion.

VMware Server should not be lightly discarded.  It should the thrown, with great force.
+9000.

VMware Player blows VMware Server away.

---

### Post by maul9999 on 2011-09-27
> **halovivek said:**
> Hi
I have successfully installed the Vmware server in ubuntu 11.04.
I could not able to install the windows.
I do have the ISO image stored in a separate partition.
I have given the file path location, and error message comes file not found.
I could not able to map it to use the image for installation.
can you please help me ?

Note:- I do have the licensed version of Windows 7.  
please see the attachment for the problem
Try VirtualBox.  It should work.  It is good Virtual OS.  It will allow you to fully using DX 9 and over on GL Open.

---

### Post by halovivek on 2011-11-22
I left the Vmware player and now i am using Virutal box only. :D

---

### Post by dcstar on 2011-11-26
> **halovivek said:**
> I left the Vmware player and now i am using Virutal box only. :D

Then read below and MARK the thread.

---

### Post by CharlesA on 2011-11-26
> **dcstar said:**
> Then read below and MARK the thread.
Marked as solved.

---

