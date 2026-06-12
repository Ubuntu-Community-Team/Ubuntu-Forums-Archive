---
title: "Ubuntu One ---what is it doing ? if anything ?"
date: 2011-05-13
forum: Ubuntu One (CLOSED)
---

### Post by MadMonkey1966 on 2011-05-13
I thought i would give Ubuntu One a try, even though i have used DropBox for ages.

I think it is all set up ok, yet the box is open and it says along the top:

 > Using 102.6 MB of 2.0 GB (5%)                                  File sync in progress......It has said that for 5 hours now.....is it actually doing anything ??

I have closed it a couple of times, and opened it, and it goes right back to the same thing.

What is more weird is there are no sent / receive lights flashing on my Modem either.

Am i missing something ?

Any help would be great, thanks in advance.

---

### Post by duanedesign on 2011-05-16
Sorry to hear you are having difficulties using Ubuntu One. Some thing you could try to determine if progress is being made is to start Ubuntu One and then open a Terminal. Then run this command in the Terminal.

```
u1sdtool --waiting
```

This will tell you the number of items waiting to sync. Check this every couple minute. If the number does not get smaller we will need to do some additional debugging.

One thing you can do is look in the file listed below and if it contains contents could you please post them in this thread. Run this command in a Terminal if the file is empty close it without saving it, If the file has contents please copy and paste the contents in this thread, The command to view the file is.

```
gksudo ~/.cache/ubuntuone/log/syncdaemon-exceptions.log
```

thank you,
duanedesign

---

