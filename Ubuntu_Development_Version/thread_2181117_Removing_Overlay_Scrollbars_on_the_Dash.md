---
title: "Removing Overlay Scrollbars on the Dash?"
date: 2013-10-16
forum: Ubuntu Development Version
---

### Post by buzzingrobot on 2013-10-16
Can the overlay scrollbars be removed from the Dash?

I've turned them off with Unity Tweak Tool and removed and purged the actual packages. 

But, tap the Windows key and, bang, there they are.

---

### Post by JRV on 2013-10-16
This worked for me:

```

   sudo apt-get remove overlay-scrollbar
   sudo echo "export LIBOVERLAY_SCROLLBAR=0" > /etc/X11/Xsession.d/80overlayscrollbars

```

The scroll bar is thin, and I don't know about the windows key. 
My original 1986 IBM PS2 keyboard doesn't have one.

---

### Post by buzzingrobot on 2013-10-16
> **JRV said:**
> This worked for me:

```

   sudo apt-get remove overlay-scrollbar
   sudo echo "export LIBOVERLAY_SCROLLBAR=0" > /etc/X11/Xsession.d/80overlayscrollbars

```

The scroll bar is thin, and I don't know about the windows key. 
My original 1986 IBM PS2 keyboard doesn't have one.

Didn't work  Rats. Got regular scrollbars everywhere but in the Dash.  Thanks, tho.

---

### Post by philinux on 2013-10-16
> **buzzingrobot said:**
> Didn't work  Rats. Got regular scrollbars everywhere but in the Dash.  Thanks, tho.

Sounds like it's hard coded. :eek:

---

### Post by JRV on 2013-10-17
philinux is probably right.  When I do a
```

sudo nautilus

```
I still get the overlay scrollbars.

philinux - Is your name Phil, or does the phi mean (1+sqrt(5))/2?

---

### Post by VMC on 2013-10-17
The above worked last time I tried it. Also, I removed them:
```
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0
```

I'll try this again to be sure.

---

### Post by VMC on 2013-10-17
I just tried this and using the command:
```
sudo sh -c 'echo "export LIBOVERLAY_SCROLLBAR=0" > /etc/X11/Xsession.d/80overlayscrollbars'
```
Then logout and back in again, it worked. I didn't have to remove anything.

---

