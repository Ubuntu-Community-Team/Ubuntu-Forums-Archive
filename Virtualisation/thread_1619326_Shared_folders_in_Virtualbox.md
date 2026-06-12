---
title: "Shared folders in Virtualbox"
date: 2010-11-11
forum: Virtualisation
---

### Post by rmcellig on 2010-11-11
Hw can I view my shared folders in Virtualbox. The Music folder I am trying to share is from a USB drive attached to my Ubuntu host.

---

### Post by kyphi on 2010-11-11
To set up a "shared folder" proceed this way:

1.  Create a folder in your Home directory and call it vboxshared.
2.  Type in Terminal: ```
VBoxManage sharedfolder add "Windows XP" -name vboxshared -hostpath /home/yourname/vboxshared
```
3.  Then in XP go to "Run" and type ```
cmd
```.
4.  Then type: ```
net use x: \\vboxsvr\vboxshared
```

The name "Windows XP" is the name I have in GRUB.
yourname= your home directory name.

Guest additions must be installed first.

You may have to put the contents of your USB stick into the shared folder.

---

### Post by rmcellig on 2010-11-11
I am having problems installing guest additions. What should I do?

---

### Post by lmarmisa on 2010-11-11
This is no error at all. This warning is very usual installing drivers in XP.

Simply, click on "Continue Anyway".

---

