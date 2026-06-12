---
title: "dual boot security question"
date: 2011-01-23
forum: Security
---

### Post by luvinit on 2011-01-23
Hi,
I need a little reminding here. I had a computer stolen that I havent used for some time. It was dual booted from two hard drives, Hardy Heron and windows xp. Windows was password protected in grub. Now, assuming that the hard drives get taken out, there is a reasonable chance that the thief doesnt know linux in general and cant read the ubuntu drive and will just format over it. However, I cannot remember if it is the case that the windows XP drive can just be plugged in alone and booted from without problems, or is the boot sector on the windows drive altered that it wont boot without going through the Ubuntu drive first? I suspect the former is true.

---

### Post by bouncingwilf on 2011-01-23
Physical access = root access to anybody who has any idea what they're doing. Unless the Hardy partition was encrypted then I think it's safe to say that a live CD will expose the entire disk (including xp) to potential reading.


Bouncingwilf

---

### Post by CharlesA on 2011-01-23
Even if they can't boot XP, they can still read the data on it from a livecd.

---

### Post by luvinit on 2011-01-23
Hi,
yes, if they know what they are doing that is very true, but am I right that the windows drive can be plugged in alone and will quite simply boot as normal straight into windows?

---

### Post by CharlesA on 2011-01-23
Not if you set up GRUB on the other drive. It would say something like no bootable media found.

---

### Post by luvinit on 2011-01-23
Ok thanks. It is 2 years since I used the computer, that is why I have recollection problems.I think I can vaguely remember that one time I tried to boot from the windows drive alone and it didnt work, but I am getting old and my memory doesnt serve me well. The information on the windows drive was not so personal and important, but as I have literally never met anyone in person who knows anything other than windows the chances are that the thiefs interest will revolve more around the windows drive.

---

### Post by koenn on 2011-01-23
still, 
hook up that drive to a working Windows system, and it'll show up as a 2nd drive in Windows Explorer.

---

