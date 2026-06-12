---
title: "[SOLVED] XP error?"
date: 2008-11-09
forum: Virtualisation
---

### Post by Yezinki on 2008-11-09
Hello every one,

I am getting this error, the XP installation freezes wont go ahead?

Hoping to hear from you,

Regards,

Yezinki.

---

### Post by lisati on 2008-11-09
This is more of a warning than an error, it's ok to press "OK" - does the installation proceed if you do?

---

### Post by Yezinki on 2008-11-09
No it does not.

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-09
Its the retail XP DVD........Sony's OEM XP MCE Recovery DVD won't even run?

---

### Post by Yezinki on 2008-11-09
Still the same...... tried running again hangs here.....are these settings correct for XP/Vista in vbox?

Regards!

Yezinki.

---

### Post by linux23dragon on 2008-11-09
I've just installed VirtaulBox and now currently installing  Windows XP Corporate Edition.  This should confirm if Sony's OEM XP MCE Recovery DVD is the issue.

---

### Post by linux23dragon on 2008-11-09
> **linux23dragon said:**
> I've just installed VirtaulBox and now currently installing  Windows XP Corporate Edition.  This should confirm if Sony's OEM XP MCE Recovery DVD is the issue.

I'm using [_***[COLOR="Blue"]VirtualBox[/COLOR]***_]("http://www.virtualbox.org/wiki/Downloads") for Ubuntu-8.10 (64bit version).  Installing Windows XP Corporate edition seemed to work ok for me.  And I even have access to the external network as well.  Still need to fix the Audio and USB but otherwise all seems to be ok.


Are you using an older version of VirtualBox by any chance, or have you always had this issue with the OEM version of Windows XP?

Edit, is your video and system RAM settings setup correctly as well (in the *General setu*p settings)?

---

### Post by Yezinki on 2008-11-10
I shall edit video & system RAM settings.

Do you have to use the KB to toggle, after the OS is installed or can you use your machine's mouse?

Where are the Virtual drives created /home?

Can you connect your OS installed to the net?

It's a Open virtual box not Vmware.

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-10
[QUOTE=Yezinki]
Do you have to use the KB to toggle, after the OS is installed or can you use your machine's mouse?
[/quote]
I use the mouse to capture VirtualBox (with the host mouse pointer) and the right side ***Ctrl*** key to uncapture VirtualBox. 

[QUOTE=Yezinki]
Where are the Virtual drives created /home?
[/quote]

Correct it is hidden in your home directory (see attached file).  You can see this in the terminal with the following command :-

```
ls -la ~/.VirtualBox
```


[QUOTE=Yezinki]
Can you connect your OS installed to the net?[/quote]

Yes, it was already configured out of the box.


[QUOTE=Yezinki]
It's a Open virtual box not Vmware.
[/QUOTE]
I was using the closed source version of VirtalBox.

---

### Post by Yezinki on 2008-11-10
Hi **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUX KING![/COLOR][/SIZE][/FONT]**


1. Where did you download the closed version from.......heard that doesn't have usb support?

2. You used your internal optical drive to install the OS media?

3. What configuration parameters do you keep in settings?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-10
& lastly how are you able to use your machine's mouse........?

---

### Post by linux23dragon on 2008-11-10
> **Yezinki said:**
> 
1. Where did you download the closed version from.......heard that doesn't have usb support?


[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

> **Yezinki said:**
> 
2. You used your internal optical drive to install the OS media?


Correct

> **Yezinki said:**
> 
3. What configuration parameters do you keep in settings?


Please see the attached file.

---

### Post by linux23dragon on 2008-11-10
error post

---

