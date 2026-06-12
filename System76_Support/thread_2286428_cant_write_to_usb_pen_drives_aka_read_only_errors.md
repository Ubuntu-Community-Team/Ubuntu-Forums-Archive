---
title: "cant write to usb pen drives/ aka read only errors"
date: 2015-07-12
forum: System76 Support
---

### Post by lizbeth3 on 2015-07-12
I have a meerkat running ubuntu and after formatting it either with mintstcik or gparted i can not cut and paste files to it.  I have tried to chown it many times and ran the browser with admin privileges to change read and write permission but the default file manager will not allow me to change them.  Im well familiar with write permissions and how to use a terminal but it seems to be something specific with your file manager.  I know this is a fact because on a whim i installed thunar and was able to write to my pen drive with that.  WTFO? ):P

---

### Post by Geoffrey_Arndt on 2015-07-12
Do you have gksu installed?   Try running "sudo gksu nautilus" and see if you can change permissions on the Mintstick (aka usb flash-stick with Mint on it???).

---

### Post by lizbeth3 on 2015-07-12
Again, no. Every time i switch to create and delete files it switches back to access files while root - just like my first post said.

---

### Post by Vladlenin5000 on 2015-07-12
And have you changed permissions as suggested?

---

### Post by coffeecat on 2015-07-13
I've removed a few posts. Let's keep it civil, please.

@lizbeth3, I think you need to give more details. What file manager are you using? How are you mounting the devices you are trying to write to? What error messages do you get? It might be helpful to post the exact chown or chmod commands you use.

Also - can you confirm what "meerkat running ubuntu" means. Is that the name of the System76 machine? There will be people who could help who are not familiar with system76 hardware.

[quote=lizbeth3]your file manager. [/quote]

Not ours. We're all volunteers here.

---

### Post by sudodus on 2015-07-13
Is the problem only with files on a pendrive? Is the file system FAT32 or NTFS? Linux cannot manage the ownership and permissions of files in Windows file systems individually. Instead, the ownership and permissions are set when mounting the partition, and will be 'inherited' by all directories and files. So the solution is to set the permissions correctly when mounting.

Another problem might be that a pendrive is failing. A first stage of that is ['gridlock'](http://ubuntuforums.org/showthread.php?t=2178075&p=12805426#post12805426), which renders it read-only.

***Edit:*** At a second reading, I see that Thunar works for you. Fine, use tools that work for you :-) and maybe later find out why another tool does not work.

---

### Post by Geoffrey_Arndt on 2015-07-13
It is curious though, why Thunar will allow for file modification (write, delete, etc.) and Nautilus (presumably) doesn't.   So, the usb-flash-stick was formatted with a Linux file system (which?).   "gksu nautilus" will work from a gui interface, but is just a temporary work-around vs changing ownership of the flash-stick which seems a better option (perhaps her chown code is off? . . )

---

### Post by sudodus on 2015-07-13
Yes. There are important things we don't now about this system, and we can only help if lizbeth3 gives us more details.

---

