---
title: "all files and folders are read only - HELP"
date: 2010-09-06
forum: Security
---

### Post by battle_bovine on 2010-09-06
I've recently upgraded to 10.04 and have noticed that all the files or folders I've been creating recently are read only.   I can manipulate the folders on my ubuntu system itself and create new entries, folderes, subfolders, and save files. IE a payment receipt in pdf format. However if I then try to move or copy any of these to my DROBO (data storage device) the file gets the LOCK Icon on it and becomes read only. If it is a subfolder I can no longer copy to it and if it's a regular file, say a pdf or flv I can't modify it.  Attempting to change the file permissions on either my ubuntu desktop or any other folder works but once it goes to the drobo I lose the ability to change it off of ---.   Again, this was all working fine before doing the upgrade to 10.04. Yes I did do a clean install to 10.04.     Any ideas??   moo

---

### Post by OpSecShellshock on 2010-09-06
Your external storage device is probably just mounting read-only by default or something. Certain drive formats do that.  I'm not sure about the Drobo devices themselves whether they have a proprietary or standard format. They don't seem to, so you might be able to create a mount point and then edit the fstab. However, I'm not absolutely sure about that when it concerns devices that are hooked in through a network connection. How's yours set up? Do you know the format?

---

### Post by an0dos on 2010-09-06
> **battle_bovine said:**
> I've recently upgraded to 10.04 and have noticed that all the files or folders I've been creating recently are read only.   I can manipulate the folders on my ubuntu system itself and create new entries, folderes, subfolders, and save files. IE a payment receipt in pdf format. However if I then try to move or copy any of these to my DROBO (data storage device) the file gets the LOCK Icon on it and becomes read only. If it is a subfolder I can no longer copy to it and if it's a regular file, say a pdf or flv I can't modify it.  Attempting to change the file permissions on either my ubuntu desktop or any other folder works but once it goes to the drobo I lose the ability to change it off of ---.   Again, this was all working fine before doing the upgrade to 10.04. Yes I did do a clean install to 10.04.     Any ideas??   moo

It soundls like a problem with the drobo. Have you tried turning off your drobo and pc? Then turn the pc on and connect the drobo once it is booted.

---

### Post by battle_bovine on 2010-09-06
Yes, the drobo's read/writes work fine in windows XP. I have restarted the drobo and my boxes.   I did map the drobo out differently this time around as the commands I used previously for ubuntu 9 weren't working. I modified my fs tab and here is the entry I'm using. This may very well be whats causing it but I'm not sure what I need to edit to work right.   # mount -t cifs -o uid=1000 //192.168.1.106/Drobo /media/drobo //192.168.1.106/Drobo    /media/drobo      cifs    username=XXXXXX,password=XXXXXXXXX    0       0  Works fine for simply creating a folder or an individual file but they immediately get slashed as read only and can't be modified further.

---

### Post by battle_bovine on 2010-09-07
Clarification because my last post was a little garbled.

mount -t cifs -o uid=1000 //192.168.1.106/Drobo /media/drobo

The above line is what I used in my fstab for ubuntu 9 and it worked fine. I can still use this command from Terminal with sudo and the drobo will mount normally and allows read/writes and file modifications. 

  //192.168.1.106/Drobo    /media/drobo      cifs     username=XXXXXX,password=XXXXXXXXX    0       0

This one is the new line I used after doing some googling to try and find a new way to mount the device since the original stopped working for some reason. I suppose I could just find a way to script a sudo command on bootup but that seems a bit pointless considering what the fstab is supposed to be doing.

Any ideas would be greatly appreciated. 


moo

---

### Post by battle_bovine on 2010-09-07
Okay so I've commented out both lines that I've tried using in fstab so that I can run "sudo mount -a" and get some sort of responses from ubuntu.

"//192.168.1.106/Drobo /media/drobo cifs rw,username=X,password=X     0       0"

As you can see here I've added "rw" to the mix in an attempt to get read and write permissions after being given the suggestion from #ubuntu on freenode. This didn't change anything as any new folders or files I tried to create ended up being locked for editing as soon as they were generated. 

"mount -t cifs -o uid=1000 //192.168.1.106/Drobo /media/drobo"

This entry works perfectly by itself if I simply run it from terminal with sudo. Also whats odd is the files previously that were locked are now no longer locked. If I do this line with fstab and mount -a I get told that the line it resides on is simply bad. 

Quite maddening because as far as I can tell it is NOT bad and shouldn't kick back a message as such. 

Ideas folks?

moo

---

### Post by battle_bovine on 2010-09-08
FIXED - apparently I was missing the uid=1000 from my  "//192.168.1.106/Drobo /media/drobo cifs rw,username=X,password=X 0 0"  command in fstab. I stuck it after rw and it now mounts perfectly.  This  still doesn't exactly explain why the mount command mysteriously quit  working. Perhaps it was never SUPPOSED to actually work in fstab?  Hopefully this will be useful to someone else in the future.

I hope this little trial helps some one in the future as this was driving me batty for a week and a half before I finally posted. 



moo

---

