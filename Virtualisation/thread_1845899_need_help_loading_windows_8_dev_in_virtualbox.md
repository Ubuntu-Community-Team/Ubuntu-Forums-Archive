---
title: "need help loading windows 8 dev in virtualbox"
date: 2011-09-18
forum: Virtualisation
---

### Post by nbrebol on 2011-09-18
So i just downloaded the windows 8 developer edition and am trying to get it to run in VB. I created a "new virtual machine", selected "other Windows" as the OS, allocated ~1200 mb for memory and did a 20 gb dynamic hard drive space.

the only problem i have is that i can't seem to get the windows-8-dev .iso file to mount in the cd drive. the virtual box tutorial i found on ubuntu forums has an older version that has a "cd/rom" tab in the settings and as far as i can tell, mine doesn't. Screenshot below. Thanks in advance for any help!

---

### Post by sikander3786 on 2011-09-18
Power on the machine and you might see a 'First Run Wizard' which would let you mount your ISO.

Or from the machine window (not VB main window), go to Devices > CD-ROM blah blah and mount your ISO from there.

---

### Post by jocko on 2011-09-18
The option to use a cd image is still where it has always been (just looks a bit different).
See [my screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=202393&stc=1&d=1316325811").

---

### Post by Megaptera on 2011-09-18
Full guide here may be useful:
[http://www.howtogeek.com/74515/how-to-test-drive-windows-8-in-virtualbox/](http://www.howtogeek.com/74515/how-to-test-drive-windows-8-in-virtualbox/)

---

### Post by texaswriter on 2011-09-18
If all else fails, you can just burn the cd and then pass it.

---

### Post by nbrebol on 2011-09-18
> **Megaptera said:**
> Full guide here may be useful:
[http://www.howtogeek.com/74515/how-to-test-drive-windows-8-in-virtualbox/](http://www.howtogeek.com/74515/how-to-test-drive-windows-8-in-virtualbox/)


This was helpful. Actually as soon as started the thread i went back and looked around more and ended up doing pretty close to what the tutorial said. I started the virtual machine and got an error message saying:

Failed to open a session for the virtual machine windows8dev.
Failed to load VMMR0.r0 (VERR_SUPLIB_OWNER_NOT_ROOT).
Unknown error creating VM (VERR_SUPLIB_OWNER_NOT_ROOT)

details:



Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {515e8e8d-f932-4d8e-9f32-79a52aead882}


I then went back and re-did the whole thing exactly as the how-to did and got the same thing. I am not an expert at ubuntu, but i am guessing the error has something to do with permissions or where the files are located?

thanks for all the replies, by the way. Is this something that is easily fixed? or should i go to another forum section and post the error message?

---

### Post by Megaptera on 2011-09-19
Sorry that didn't help completely, let's see if anyone else can help - bearing in mind the version of Windows 8 is still very much a work in progress ...

---

