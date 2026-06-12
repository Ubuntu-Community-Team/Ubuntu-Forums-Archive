---
title: "Virtual Box error message"
date: 2013-09-21
forum: Virtualisation
---

### Post by ymurti2 on 2013-09-21
Please can someone help me? I tried to use VM but I got the attached error message.


I tried to use the terminal with the command "sudo /etc/init.d/vboxdrv setup" but I got the attached message:

---

### Post by ibjsb4 on 2013-09-21
Which dkms package did you install?  And did you install vBox from the software center?

---

### Post by ymurti2 on 2013-09-21
Dear [COLOR=#000000]ibjsb4,
[/COLOR]
I have installed from Software Center.  dkms, I do not know. Sorry.


> **ibjsb4 said:**
> Which dkms package did you install?  And did you install vBox from the software center?

---

### Post by ibjsb4 on 2013-09-21
I don't have very good luck when installing vBox form the software center, Im sure others do, but I just don't.  So i would recommend removing your current install and then installin from the site.
```
sudo apt-get remove --purge virtualbox
```

Then do a search in nautilus in your FileSystem for virtualbox and remove any leftovers.
```
gksudo nautilus
```

Then install dkms and build-essential
```
sudo apt-get install dkms build-essential
```

Then download per site instructions.
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Last step, install Extension Pack
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

And then the sucker should work :D

---

### Post by ymurti2 on 2013-09-22
Solved! Dear [COLOR=#000000]ibjsb4,   Thank You very much for your help.  [/COLOR]


> **ibjsb4 said:**
> I don't have very good luck when installing vBox form the software center, Im sure others do, but I just don't.  So i would recommend removing your current install and then installin from the site.
```
sudo apt-get remove --purge virtualbox
```

Then do a search in nautilus in your FileSystem for virtualbox and remove any leftovers.
```
gksudo nautilus
```

Then install dkms and build-essential
```
sudo apt-get install dkms build-essential
```

Then download per site instructions.
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Last step, install Extension Pack
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

And then the sucker should work :D

---

### Post by ibjsb4 on 2013-09-22
And welcome to the forums :)

---

