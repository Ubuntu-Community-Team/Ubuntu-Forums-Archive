---
title: "installing microsoft fonts on edgy"
date: 2007-02-12
forum: Repositories &amp; Backports
---

### Post by crackers8199 on 2007-02-12
how do i get this to work?  in googling i found that i need to enable the universal repository, but even after doing this i still haven't been able to get it working...

matt@matt-linux:~$ sudo aptitude install msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for msttcorefonts
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

---

### Post by bapoumba on 2007-02-12
PLease enable multiverse repositories :
```
~ $ aptitude show msttcorefonts
Package: msttcorefonts
State: installed
Automatically installed: no
Version: 1.2ubuntu3
Priority: optional
Section: multiverse/x11
```

---

### Post by crackers8199 on 2007-02-12
even after adding these two lines to the sources list...

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse

still get the same message...

---

### Post by highneko on 2007-02-12
I don't know if this counts but you could copy the font files from c:/fonts or maybe it's c:/windows/fonts into your ~/.fonts directory. That's if you have a windows partition and it's mounted.

---

### Post by rsambuca on 2007-02-12
If you search for msttcorefonts in synaptic, do they show up?  If not, you have the wrong repositories set up.

---

### Post by crackers8199 on 2007-02-12
> **highneko said:**
> I don't know if this counts but you could copy the font files from c:/fonts or maybe it's c:/windows/fonts into your ~/.fonts directory. That's if you have a windows partition and it's mounted.

OK, a few things...

1)  I was able to install the package when I used the add/remove applications...not sure why it wouldn't let me when I was trying to do it thru the terminal.

2)  As for copying the fonts to ~./fonts, I've been trying to do that and get the message that it's not a valid folder.  Why is this?  I'd like to copy over some other fonts, but haven't been able to get that to work...

---

### Post by highneko on 2007-02-12
> **crackers8199 said:**
> OK, a few things...

1)  I was able to install the package when I used the add/remove applications...not sure why it wouldn't let me when I was trying to do it thru the terminal.

2)  As for copying the fonts to ~./fonts, I've been trying to do that and get the message that it's not a valid folder.  Why is this?  I'd like to copy over some other fonts, but haven't been able to get that to work...
You gotta make the folder first. I should have mentioned it maybe. It would have been a long reply if I was gonna completely explain tho.
```

# First make the hidden folder named ".fonts" in the home directory:
mkdir ~/.fonts
# Copy the files. Replace the word "Example" with the mounted folder you choose for windows:
# The location of the windows fonts may be different for you. I have a mounted vista.
sudo cp /Example/Windows/Fonts/* ~/.fonts
# Then maybe you should change the permissions or ownership of the moved font files:
sudo chown $USER:$USER ~/.fonts/*
# Then the permissions to -rw-r--r--:
sudo chmod 644 ~/.fonts/*
```

That should do it. I didn't follow a tutorial when doing this. I just thought it would make sense and did it. It has been working fine and I have many new fonts for programs like gimp. Good luck.

---

