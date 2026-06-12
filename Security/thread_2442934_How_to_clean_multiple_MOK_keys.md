---
title: "How to clean multiple MOK keys ?"
date: 2020-05-09
forum: Security
---

### Post by georgesgiralt on 2020-05-09
Hello,
I own a Dell G3 (3579) with which I had a lot of big problems. (Software and hardware).
In order to track them down, I was forced to redo the installation of Ubuntu 19.10 version WITH additional drivers installed during the installation process on 3 different disks. 
Now, my MOK database contains 10 keys, a lot of them being the various platform key created on my machine during install of the Nvidia proprietary driver. (which was one of the culprit for my problems)
For my sanity and further proper handling, I would like to clean the unused keys without destroying the good ones and retain the security boot.
I can't find a clear answer and procedure for this. So I kindly ask for help on that matter.
Many thanks in advance for your enlightenment !
Have a nice day and stay safe !

---

### Post by EuclideanCoffee on 2020-05-09
```

$ mokutil --export


```

Exports to list.

```

$ ls -1 MOK*

```

Shows all keys.

```

$ mokutil --list-enrolled

```

Shows you keys enrolled. 

```

$ mokutil --delete MOK-0001.der

```

Delete those not enrolled to maintain secure boot.

---

### Post by georgesgiralt on 2020-05-10
Thank you EuclidianCoffe for your answer !
Everything is fine except that the "**mokutil --list-enrolled**" command list all the 10 keys which are in my machine tables.
So I still can't find which  keys to delete. 
Is there a way to find the serial number from a .der file ? because I have the actual DER file my current Ubuntu is using, and the mokutil command gives me the serial of all the keys enrolled. 
So by comparison I would be able to build the list of the extra keys.
I'm not so keen in cryptography nor key handling, even if I look not so newbie ;-) 
Have a nice day and stay safe !

---

### Post by EuclideanCoffee on 2020-05-10
If you can't determine, maybe a simple reset could assist.

I would backup before doing anything final like a reset.

```

$ mokutil --export


```

---

### Post by georgesgiralt on 2020-05-10
OK. I'll give it a try ! 
But I would have preferred to check which key was which... 
Thanks anyway !

---

### Post by georgesgiralt on 2020-05-11
So, today it was raining hard. Very hard. So it was perfect to play with the computer ...
I did triple check the various key (and dates of the files in /var/lib/shim-signed/mok ) and determined all the keys I had to remove. 
Then I removed them one at a time (to be able to check if something went amiss and correct it easily).
So I did the following procedure eight times ...
```

$ sudo  mokutil --delete MOK-000<N>.der     # where N is the number of the key to remove.... In my case, it ran from 1 to 8.
<enter a password for the MOK UEFI utility>
<enter again the same password and keep in mind the keyboard in the UEFI utility would surely be a US one... >
$ sudo systemctl reboot

```
The machine reboots and the mok utility shows. Follow the instructions and then, **view the key to ensure it is the one you want to delete**... if it is, proceed.
Reboot the computer after removing the "quiet splash" stanza in the linux Grub line. This way, if something goes amiss, you'll catch the red fail message.
Login and do it again for the other key.
After this is complete, tap yourself on the back. 
Congratulation, you're done !
P.S. : each key has a validity date. Obviously, all keys valid BEFORE the creation date of the keys in /var/lib/shim-signed/mok are to be deleted. EXCEPT the one issued by MM Microsoft, your computer maker, and Ubuntu Central authority... 
P.P.S : It is important to say that saving the keys **BEFORE** doing anything leading to deletion is not a stupid thing to do. And doing one at a time, even if your BIOS allows for a more easy way to clean the lot is not a bad idea also. Kind of "belt and suspenders" here but.... Being locked out is no fun.

---

### Post by EuclideanCoffee on 2020-05-11
Congratulations, brilliant work. Please mark this as solved, so future users can follow your advice. Thanks for posting the results of your work.

---

