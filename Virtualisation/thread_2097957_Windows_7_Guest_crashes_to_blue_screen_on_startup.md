---
title: "Windows 7 Guest crashes to blue screen on startup"
date: 2012-12-25
forum: Virtualisation
---

### Post by aboud on 2012-12-25
host: ubuntu 12.10, 64-bit
Guest: Windows 7, 64-bit
platform: Virtualbox.

I copied a working virtual machine from windows to Linux, but it never started. it crashes to blue screen after the windows logo. 

do you know any known issues that can cause that  ? 


i7 3612qm with VT-x enabled.

Thanks

---

### Post by carl4926 on 2012-12-25
I think BSOD is something quite common

I do know I never bother with _64 in VM's but it should work... obviously

Have you got The Extension Pack installed?

---

### Post by aboud on 2012-12-25
I never got to the windows7 desktop to install the geust addition.

---

### Post by haqking on 2012-12-25
boot into safe mode and read the logs in event viewer

---

### Post by aboud on 2012-12-26
It crashed before it get to the safe mode. 

I delete it and installed new windows 7. the new installation is working so far. 

Thanks every body!

---

### Post by haqking on 2012-12-26
> **aboud said:**
> It crashed before it get to the safe mode. 

I delete it and installed new windows 7. the new installation is working so far. 

Thanks every body!

for future reference press f8 upon boot to access safe mode menu.

---

### Post by aboud on 2012-12-26
That what I did, but it crashed on the logo.

---

### Post by PJs Ronin on 2012-12-26
I had the BSOD about a week or so ago after I resized (reduced) my (fixed size) W7 image to save HD space.   Didn't have a clue what I was doing and issued a command like:

"VBoxManage modifyhd my.vdi –compact"

to free up space.   The command went well, no errors, but when I tried to run W7 all I got was a BSOD.   No amount of F8, esc, del key tapping would fix the problem.   I pulled a backup copy of the w7.vdi from removable storage and voila, all is good.   But that got me to wondering what I did wrong.

Seems you need to do some cleanup within the guest first with a program called zerofree that sets unused disk space within the guest to 'zeros' so that the '--compact' option has something to chew on.   Pretty sure I'm not explaining this right so check out this page: [http://dantwining.co.uk/2011/07/18/how-to-shrink-a-dynamically-expanding-guest-virtualbox-image/](http://dantwining.co.uk/2011/07/18/how-to-shrink-a-dynamically-expanding-guest-virtualbox-image/)

Fixed size images are a real pain... stick with dynamic imo.

---

