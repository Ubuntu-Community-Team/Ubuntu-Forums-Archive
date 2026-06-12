---
title: "ubuntu 14.10 can not mount iPhone5s"
date: 2014-09-01
forum: Ubuntu Development Version
---

### Post by KOSKERS on 2014-09-01
when i connect my iphone5s into my laptop with ubuntu 14.10.
it said that              Message did not receive a reply (timeout by message bus)
i have used PPA for upgrading the libmobileidevice lib version.
But also failed.


Can someone help me?

---

### Post by ThatBum on 2014-09-02
Try running [FONT=courier new]idevicepair unpair && idevicepair pair[/FONT] and reconnecting the iPhone.

E: Oh and install [FONT=courier new]libimobiledevice-utils[/FONT] if you haven't already since [FONT=courier new][/FONT][FONT=courier new]idevicepair[/FONT] is part of that package.[FONT=courier new][/FONT]

---

### Post by QIII on 2014-09-02
*Moved to **Ubuntu Development Version***

Please note that 14.10 is still under development and has not been released.

---

### Post by KOSKERS on 2014-09-02
Thanks for quick replying.

koskers@koskers-W35xSTQ-370ST:~$ idevicepair unpair && idevicepair pair
ERROR: Device 6ab139dd554ac7c536b97b3c50afaf6c7893d9a7 is not paired with this host

---

### Post by ThatBum on 2014-09-02
Ah, well use just [FONT=courier new][COLOR=#000000]idevicepair pair [/COLOR][/FONT]then.

If it's working, you should see two mountable volumes. One is "x's iPhone" and the other is "Documents on x's iPhone." The former is the [FONT=courier new]/Media[/FONT] directory in the [FONT=courier new]mobile[/FONT] user's home directory ([FONT=courier new]/private[/FONT][FONT=courier new]/var/mobile[/FONT]), and is what you want to mount to sync music and stuff. The latter is [FONT=courier new]/Documents[/FONT] in the same home directory, where some apps put their data in so as to make it more accessible for transfer to a computer.

This is assuming how it works hasn't changed since iOS 4, which is what I have on my iPhone 3G.

---

### Post by KOSKERS on 2014-09-03
koskers@koskers-W35xSTQ-370ST:~$ idevicepair pair
Segmentation fault

---

### Post by ThatBum on 2014-09-03
Oh, seems it needs to be run as root, use [FONT=courier new]sudo idevicepair pair[/FONT]&#8203;. Also unlock the phone first.

Other than that I don't know, it's not my forte. Maybe there's no support yet for the 5s or the version of iOS it's running, or it needs to be jailbroken to allow read-write permissions to the user partition.

---

### Post by KOSKERS on 2014-09-03
koskers@koskers-W35xSTQ-370ST:~$ sudo idevicepair pair
[sudo] password for koskers: 
koskers@koskers-W35xSTQ-370ST:~$ sudo idevicepair pair
koskers@koskers-W35xSTQ-370ST:~$ 


Sucessfully. :)
But i still can not see any iphone icon in ubuntu file manager

---

### Post by KOSKERS on 2014-09-03
koskers@koskers-W35xSTQ-370ST:~$ sudo idevicepair unpair
ERROR: Device 6ab139dd554ac7c536b97b3c50afaf6c7893d9a7 is not paired with this host

---

### Post by KOSKERS on 2014-09-03
i think it must be a bug in 14.10.
Because in 14.04... all things run right.

---

### Post by ThatBum on 2014-09-03
Odd, that command should have output, [FONT=courier new]SUCCESS: Paired with device [UUID][/FONT]

Try replugging the phone, and [FONT=courier new]sudo idevicepair verify[FONT=arial][/FONT][/FONT]

[FONT=courier new][FONT=arial][/FONT][/FONT]Also I read while researching this that iOS7 has some kind of on-phone verification when pairing with a new computer, like [this]("http://i.imgur.com/MekTUUX.jpg"). So hit that if it's asking.

---

### Post by KOSKERS on 2014-09-03
not found verify.
i use 
koskers@koskers-W35xSTQ-370ST:~$ sudo idevicepair validateERROR: Device 6ab139dd554ac7c536b97b3c50afaf6c7893d9a7 is not paired with this host


Thanks u very much indeed. u r warm-heart man

---

### Post by ThatBum on 2014-09-03
Thank you, I try.

I'm not really finding much else, aside from "Trust this computer" infinite loops, but this seems to be a different issue since it's not being recognized at all.

It works fine with my 3G after sorting out some issues with the music database, but it's quite an old phone and I bet it's been more thoroughly reverse-engineered than yours.

Anyone have anything else to add?

---

### Post by KOSKERS on 2014-09-03
No. Thx a lot.
I am w8ing ubuntu resolved this bug from 14.10

---

