---
title: "Daily still Alpha after Beta 1 Freeze?"
date: 2017-03-02
forum: Ubuntu Development Version
---

### Post by corradoventu on 2017-03-02
I have installed the last daily ISO: Ubuntu 17.04 "Zesty Zapus" - Alpha amd64 (20170302)
I'm surprised to see 'Alpha' while i was expecting 'Beta' because from [https://wiki.ubuntu.com/ZestyZapus/ReleaseSchedule](https://wiki.ubuntu.com/ZestyZapus/ReleaseSchedule) the Beta freeze is already occurred.

---

### Post by ventrical on 2017-03-02
I most always see "Alpha" even after the Beta freeze. Perhaps it will get rolled over in a day or so.

Regards..

---

### Post by ajgreeny on 2017-03-02
It is the same always, or nearly so anyway, when a new development version appears and seems to tell you it is still the previous version when booting.
Certainly 17.04 still showed as 16.10 when it first appeared, but it is just a label; don't worry about it!

---

### Post by flocculant on 2017-03-02
If you're specifically talking about Ubuntu and not one of the flavours - you won't see anything but dailies until Final Beta regardless of any label

---

### Post by corradoventu on 2017-03-05
The string 'Ubuntu 17.04 "Zesty Zapus" - Alpha amd64 (20170302)' is written some part in the ISO. How can i verify BEFORE installing? I'm unable to find it starting the daily.

---

### Post by howefield on 2017-03-05
> **corradoventu said:**
> The string 'Ubuntu 17.04 "Zesty Zapus" - Alpha amd64 (20170302)' is written some part in the ISO. How can i verify BEFORE installing? I'm unable to find it starting the daily.

Possibly...

```
cat /media/$USER/Ubuntu\ 17.04\ amd64/.disk/info
```

---

### Post by corradoventu on 2017-03-05
corrado@corrado-z9:~$ cat /media/$USER/Ubuntu\ 17.04\ amd64/.disk/info
Ubuntu 17.04 "Zesty Zapus" - Alpha amd64 (20170305)
corrado@corrado-z9:~$ 
Thanks a lot

---

### Post by howefield on 2017-03-05
> **corradoventu said:**
> corrado@corrado-z9:~$ cat /media/$USER/Ubuntu\ 17.04\ amd64/.disk/info
Ubuntu 17.04 "Zesty Zapus" - Alpha amd64 (20170305)
corrado@corrado-z9:~$ 
Thanks a lot

Cool, you're welcome. Feel free to mark the thread as solved.

---

### Post by howefield on 2017-03-05
Just to add that if you haven't created the Live media it is possible to extract the information directly from the image. Double clicking on the image should open it up in the archive manager from where you can navigate to the info file and open it in a text editor.

---

