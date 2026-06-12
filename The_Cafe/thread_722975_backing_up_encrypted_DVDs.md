---
title: "backing up encrypted DVDs"
date: 2008-03-13
forum: The Cafe
---

### Post by DocForbin on 2008-03-13
I normally use dvd shrink under wine which works fine with a tweak or two, but dvd shrink alone cannot handle a recent title I'm trying to backup. Unfortunately, AnyDVD does not seem to work under wine. I tried k9copy, but it stalls part way through this title as well. Does anyone know a linux equivalent to AnyDVD or something that runs under wine?

---

### Post by tylerspaska on 2008-03-13
i use the free version of [dvdfab hd decrypter]("http://www.dvdfab.com/free.htm") and then use dvd shrink to make the folder fit a single layer dvd. i've only found one dvd that i can't back up. i'm not sure if it works with wine. dvd backup is one of the reasons i keep windows around.

---

### Post by scragar on 2008-03-13
you can always backup DVD's to an iso file using the command line, regardless of their protection:
```
dd if=/dev/**DVD-DEVICE** of=/home/**username**/dvdcopy.iso
```
replacing the bold bit's for the info you need.


and have you install the libdvdcss2 and the libdvdcss3 package? Those will provide the latest copy protection methods that you may need.

---

### Post by hhhhhx on 2008-03-13
thoggen :)

---

### Post by DocForbin on 2008-03-13
> **scragar said:**
> you can always backup DVD's to an iso file using the command line, regardless of their protection:
```
dd if=/dev/**DVD-DEVICE** of=/home/**username**/dvdcopy.iso
```
replacing the bold bit's for the info you need.


and have you install the libdvdcss2 and the libdvdcss3 package? Those will provide the latest copy protection methods that you may need.
Neat, but unfortunately on this title it dies shortly in just like dvd shrink.
```
dd: reading `/dev/scd1': Input/output error
```

I may have spoke too soon about k9copy, it hung for a while but finally did finish :)

I will check out thoggen and dvdfab, thanks for all the suggestions.

---

### Post by scragar on 2008-03-13
device, not partition. drop the 1. and be sure to unmount it first.

---

### Post by DocForbin on 2008-03-13
That is the device for my external burner. It runs for about 3 minutes before failing (made a 150 MB or so iso). I didn't unmount though.

---

