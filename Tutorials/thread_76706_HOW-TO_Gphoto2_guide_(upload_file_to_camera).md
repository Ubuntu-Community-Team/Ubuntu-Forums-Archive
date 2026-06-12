---
title: "HOW-TO: Gphoto2 guide (upload file to camera)"
date: 2005-10-15
forum: Tutorials
---

### Post by humanity_to_others on 2005-10-15
Gphoto2 is a command line tool for digital cameras in linux. Main Page: [http://www.gphoto.org/](http://www.gphoto.org/)There are some guis based on gphoto2. Like Digikam, Gtkkam. You can apt-get them with synaptic. 

_Some hints about using gphoto2:_ 

Viewing digital camera's abilities:
```
gphoto2 -a
```
Listing folders:
```
gphoto2 -l
```
Downloading all files in camera:
```
gphoto2 -P
```

Upload a file to cam (We must specify an upload folder in camera)
```
gphoto2 -u a.jpg --folder /store_00010001/
```

Additional help, type: 
```
man gphoto2
```

---

### Post by afrodeity on 2012-08-15
something not right with the way the camera is mounted, I have a fujifilm JX370

```
gphoto2 -l
An error occurred in the io-library ('Could not lock the device'): Camera is already in use.
*** Error (-60: 'Could not lock the device') ***      
```

---

