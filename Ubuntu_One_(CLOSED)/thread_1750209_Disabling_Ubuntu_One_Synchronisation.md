---
title: "Disabling Ubuntu One Synchronisation"
date: 2011-05-05
forum: Ubuntu One (CLOSED)
---

### Post by alexmidd on 2011-05-05
Since upgrading to Ubuntu 11.04, Ubuntu One insists on trying to synchronise every time I boot into Linux. When I want to log out or shut down I get the message that I can't because Ubuntu One is synchronising. The thing is, I don't use Ubuntu One and don't even have an account. But the control panel doesn't seem to let you change any settings without first signing up. So, how do I disable Ubuntu One from doing anything at all when I log into Linux?

Sorry if this has been asked already. I tried searching but it said that all my search terms were common words.

---

### Post by glendavee on 2011-05-05
Use Startup Applications to remove ubuntuone from list of programs (you find it in the applications folder)

---

### Post by alexmidd on 2011-05-05
Ah, brilliant, that has done the trick. Thank you.

---

### Post by brunolabs on 2011-05-11
I use Ubuntu One and would like it to synchronize only on command. I mean, _I don't want it to autoconnect when I boot the pc_, only when I need it. Is that possible? To stop the autoconnect.
Obviously the remove ubuntuone package solution doesn't fit me. :)


Thanks.


PS: I reused this thread so I didn't have to open another with the same question.

---

### Post by DAB4970 on 2011-05-16
I am guessing that unchecking the "File Synchronization" box in the Ubuntu One preferences window disables only the sync to the computer.  Am I correct on this?  I only want to sync to the Ubuntu One app on my iPhone 3GS.

---

### Post by duanedesign on 2011-05-16
Remove Ubuntu One from Start Up Applications. Then when you open/use Ubuntu One simply open it, this will start syncing. Or you could use the Terminal and issue the command:

```
u1sdtool -c
```

respectfully,
duanedeisn

---

### Post by brunolabs on 2011-05-22
> **DAB4970 said:**
> I am guessing that unchecking the "File Synchronization" box in the Ubuntu One preferences window disables only the sync to the computer.  Am I correct on this?

You are. Thanks!

---

