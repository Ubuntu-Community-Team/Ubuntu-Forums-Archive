---
title: "virtual box error"
date: 2008-05-28
forum: Virtualisation
---

### Post by nhovan on 2008-05-28
so everytime i try to open my vbox it gives me the error:
Virtual box driver cannot be opened
VBox status code: -1911 (VERR_VM_DRIVER_OPEN_ERROR).


it was working fine until i upgraded to 8.04. any help anyone? and i made sure i gave myself permissions to it and all that.

---

### Post by Drakkor on 2008-05-28
Are you in vboxusers group in Users and Groups,and I had to give permission in /dev/vboxdrv to add me as owner. Hope this helps.

---

### Post by nhovan on 2008-05-28
where did you get to that screen at? i am in thevboxusers group but i dont have those options that you had in your attachment

---

### Post by Jose Catre-Vandis on 2008-05-28
> **nhovan said:**
> where did you get to that screen at? i am in thevboxusers group but i dont have those options that you had in your attachment

Open nautilus and browse to Filesystem/dev you will find vboxdrv there. Right click on it and choose properties.

If you do this as root you can change permissions

---

### Post by nhovan on 2008-05-28
ok i got to that part and it says root is the owner. i checked in system>admin>usergroups and I am under the vboxusers permissions as well as the root permissions

---

### Post by Drakkor on 2008-05-28
In terminal ```
sudo nautilus
```
Then go to filesystem, in the dev folder you will find the vboxdrv file,
right click it and select properties then permissions,and make your username the owner.

---

### Post by hyperair on 2008-05-28
You may have an outdated vboxdrv kernel module. Try ```
sudo /etc/init.d/vboxdrv setup
``` Then try again.

---

### Post by nhovan on 2008-05-28
ya. sorry for the long delay. but i tried both these things and put my name in as an owner and still doesnt work. i do get this error in terminal:

Initializing nautilus-share extension
seahorse nautilus module initialized
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:13614): WARNING **: Unable to add monitor: Not supported

---

### Post by Drakkor on 2008-05-28
I also got the terminal error,but it still will go to the root nautlus filesystem . I finally got mine working by using an old version 1.5.4 . and does you User/Group permissions look like this ? You might want to follow my thread at : [http://ubuntuforums.org/showthread.php?t=809645](http://ubuntuforums.org/showthread.php?t=809645)

---

### Post by hyperair on 2008-05-29
Sounds like a nautilus-share error. Regarding that, Samba isn't configured properly for usershares. That has nothing to do with Virtualbox though. The simplest way to fix the nautilus-share error is to override your /etc/samba/smb.conf file with /usr/share/doc/nautilus-share/examples/smb.conf. Or at least merge the data inside, if you know how.

---

### Post by TDFZ on 2009-03-29
I had the same error.  I fixed it by completely unintsalling it with Synaptics, downloading the .deb from VBOX website and installing it.  Thats it.  It worked.

---

