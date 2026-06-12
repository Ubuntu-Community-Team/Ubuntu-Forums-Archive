---
title: "RR locking up."
date: 2012-11-02
forum: Ubuntu Development Version
---

### Post by sammiev on 2012-11-02
Testing is fun so far. :guitar:

Update Manager locks up after doing any updates whether they are any updates or not. ( as soon as you press OK to close the update window )

Updating RR from terminal does the same as above when you type exit to close the terminal window. 

FireFox will not close most times and RR locks up tight.

I have a few other programs that do much the same. I guess I need to wait for an update or two. :)

Testing RR on a Toshiba Intel(i5) based laptop.

---

### Post by sammiev on 2012-11-07
Just an update:

Still not useable even after all the updates at this time.

---

### Post by sammiev on 2012-11-08
After this evenings updates it seems things are a go again. Time to play until the next one. :)

---

### Post by sammiev on 2012-11-17
Well from marked as been solved is now as bad as it was or not worse after the updates over the last 24 hrs. Intel graphic cards are suffering more than ever.

---

### Post by ventrical on 2012-11-18
Works ok here. I have always had  better workability with Intel based graphics.

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

HP PY028AA-ABA-A1106N:

---

### Post by cariboo on 2012-11-18
I had a hard lockup watching a Youtube video last night, but that's the first time since upgrading to Raring. So far I can't upgrade to the 3.7 kernel, as the system won't even finish booting, so I'm still running the 3.5 kernel.

---

### Post by ronacc on 2012-11-18
I've been getting the lockups here too . I have found that they occur for me when I try to close the last window , as long as I keep 1 window open I get no lockups . This is with the 3.5.0-17 kernel , I haven't been able to get the 3.7 kernel to boot on my box yet .

---

### Post by BertN45 on 2012-11-18
My Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04) has a problem if I enable multi-threading on my Pentium 4. If I disable multi-threading everything works fine. I filed a bug-report: [https://bugs.launchpad.net/bugs/1080427](https://bugs.launchpad.net/bugs/1080427)

---

### Post by sammiev on 2012-11-18
> **ronacc said:**
> I've been getting the lockups here too . I have found that they occur for me when I try to close the last window , as long as I keep 1 window open I get no lockups . This is with the 3.5.0-17 kernel , I haven't been able to get the 3.7 kernel to boot on my box yet .

You are correct when you say trying to close the last window. I will have to follow that a little closer. 
Thanks and happy testing. :)

---

