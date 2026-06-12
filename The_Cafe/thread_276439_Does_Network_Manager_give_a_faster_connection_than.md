---
title: "Does Network Manager give a faster connection than Knetworkmanager?"
date: 2006-10-12
forum: The Cafe
---

### Post by ComplexNumber on 2006-10-12
i've been doing some testing, and have set up another account on fedora that runs kde. i've connected to my wireless connection using knetworkmanager and used konqueror to browse to kde-look and ubuntuforums. then i logged out and logged into my gnome account. i noticed that the connection was equally slow in firefox and gnome.  then i rebooted and logged into my gnome account. i then connected using gnome's network manager.  my internet conection seemed to be faster. just to be sure, i logged out and logged into my kde account. the connection was just as fast as it was in gnome.

therefore, i noticed that the connection is noticably faster when i connect using network manager than when i connect using knetworkmanager. i repeated the test twice and got the same result. is there a reason for this? i can't see the logic.

---

### Post by wieman01 on 2006-10-13
This does not make sense indeed. Both Gnome NetworkManager & KDE NetworkManager as simply GUIs for the actual process/program called "NetworkManager" that runs in the background. So I don't see the point here. Must be something else.

---

### Post by ComplexNumber on 2006-10-13
> This does not make sense indeed.
thats what i thought. i can't see the reason why it should be so. i would have thought that the speed is hardware dependent. but i want to know the reason so that i can look into it.

---

### Post by wieman01 on 2006-10-13
So you have tried the same browser (e.g. Firefox) on both Window managers (KDE, GNOME)? Just to be able to compare.

---

### Post by ComplexNumber on 2006-10-13
> **wieman01 said:**
> So you have tried the same browser (e.g. Firefox) on both Window managers (KDE, GNOME)? Just to be able to compare.
i tried firefox on gnome and konqueror on kde. but the speeds were virtually the same, so i don't think its a browser issue. when i mean is, when i connected via knetwork manager, both were equally slower. when i connected using netwoek manager, bother were equally faster.

---

### Post by wieman01 on 2006-10-13
> **ComplexNumber said:**
> i tried firefox on gnome and konqueror on kde. but the speeds were virtually the same, so i don't think its a browser issue. when i mean is, when i connected via knetwork manager, both were equally slower. when i connected using netwoek manager, bother were equally faster.
Ok, beats me. Sorry... Not using NetworkManager anymore so I won't be much of help in that case.

---

### Post by ComplexNumber on 2006-10-13
> **wieman01 said:**
> Ok, beats me. Sorry... Not using NetworkManager anymore so I won't be much of help in that case.
ok, cheers anyway :). i guess it may turn out to be a simple reason afterall.

---

