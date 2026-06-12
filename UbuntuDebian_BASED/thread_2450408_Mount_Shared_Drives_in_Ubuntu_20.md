---
title: "Mount Shared Drives in Ubuntu 20"
date: 2020-09-13
forum: Ubuntu/Debian BASED
---

### Post by greatoffender on 2020-09-13
I'm a Linux idiot so I'll get that out of the way first. 

I have a Raspberry Pi V3 B+ that I dusted off and used for an NAS server. Wired into the network with 2 external drives attached. I can see the drives on my Linux machine but I am denied every time I try and mount them. "Failed to mount Windows share ..." and I believe the "windows share bit" is the problem but not familiar enough. How do I mount these to my Linux laptop? I have tried researching this for hours but as soon as I put Pi and Linux together in the search terms I am led down rabbit holes. Not an IT idiot just a Linux idiot.

I appreciate any and all help provided.

Thank you,

---

### Post by Morbius1 on 2020-09-13
** What operating system is on the Pi.
** Did you install Samba on the Pi.
** If you did how did you create the shares and how are they configured. Posting the output of the following commands will tell you that:
```
testparm -s
net usershare info --long
```
** What is the rest of the error message. "Failed to mount.." is not enough.

---

### Post by greatoffender on 2020-09-13
Raspbian - latest version
Yes, Samba is installed and shared drives are accessible to Windows clients.
Each share is the same except path.

Unable to mount location
Failed to mount Windows share: Permission denied

create mask = 0777
    directory mask = 0777
    path = /media/pi/My Book
    read only = No

---

### Post by QIII on 2020-09-13
Moved to **Ubuntu/Debian BASED**

---

### Post by Morbius1 on 2020-09-14
Change this:
> create mask = 0777
    directory mask = 0777
    path = /media/pi/My Book
    read only = No                 
To this:
> [QUOTE]create mask = 0777
    directory mask = 0777
    path = /media/pi/My Book
[COLOR=#ff0000]**force user = pi**[/COLOR]
    read only = No                 [/QUOTE]
Restart smbd:
```
sudo service smbd restart
```

---

### Post by greatoffender on 2020-09-16
Thanks for your help. I have been otherwise occupied by my "real" life and work but I have tried your suggestion and every other possible option I can find on the web. The difference now is that when I attempt to log in I no longer get an error about "unable to Mount" I just get pushed back to the log in screen with any and all options greyed out which requires me to cancel 2x to get the dialog box to go away. I haven't stopped trying and might even rebuild the Raspberry Pi over the weekend. The irony is not lost on me that every Windows machine in the house can log onto the NAS except the Linux machine. Windows did not like sharing a drive on my laptop (drive errors) and I finally just went all in and reformatted (new drive) to Ubuntu only.After experimenting with Linux for over 20 years I see that it has really never gotten easier but my patience has grown with age so we'll see. I do appreciate the help!

---

### Post by greatoffender on 2020-09-17
To the "Living Vampire" Morbius1 I thank you! Although I did not reach the Pi NAS server using your tips it did move me to explore more options and then rebuild the server. For no particular reason it now connects. It is no different now than when I first posed my dilemma but you were the only one to respond and you did push me to go the extra mile so once again, THANK YOU!
1

---

