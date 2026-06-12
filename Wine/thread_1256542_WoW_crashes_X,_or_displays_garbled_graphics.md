---
title: "WoW crashes X, or displays garbled graphics"
date: 2009-09-02
forum: Wine
---

### Post by techolous on 2009-09-02
I'm trying to run World of Warcraft 3.2.0 (installed on a 64 bit Windows 7 RC partition) on Ubuntu 9.04 64-bit. When I run it using DirectX it runs, but outputs garbled graphics (see attached screenshot). When I run it using OpenGL, X crashes.

graphics card is an integrated X1200 Radeon using the "radeon" XOrg driver (fglrx has discontinued support for my card)

EDIT:
I've tried Wine 1.0.1 (from the Ubuntu repositories) and 1.1.28 (from the WineHQ repository)

---

### Post by xxshifterxx on 2009-09-03
I have the same problem but except mine doesnt even launch..:D

---

### Post by jasonditz on 2009-09-03
> **techolous said:**
> I'm trying to run World of Warcraft 3.2.0 (installed on a 64 bit Windows 7 RC partition) on Ubuntu 9.04 64-bit. When I run it using DirectX it runs, but outputs garbled graphics (see attached screenshot). When I run it using OpenGL, X crashes.

graphics card is an integrated X1200 Radeon using the "radeon" XOrg driver (fglrx has discontinued support for my card)

EDIT:
I've tried Wine 1.0.1 (from the Ubuntu repositories) and 1.1.28 (from the WineHQ repository)

Try disabling the pixel shader in Wine configuration. That cleared it up for me.

---

### Post by techolous on 2009-09-03
> **jasonditz said:**
> Try disabling the pixel shader in Wine configuration. That cleared it up for me.

That worked, but now It is running at 2 fps (It won't run at all under Windows 7, due to insufficient memory). I'll dig around for solutions.

---

### Post by ackanao on 2009-09-03
Just a suggestion before you start digging - Wait for couple of hours and upgrade to 1.1.29 version of Wine.

---

### Post by techolous on 2009-09-03
> **ackanao said:**
> Just a suggestion before you start digging - Wait for couple of hours and upgrade to 1.1.29 version of Wine.

Will do.

(not using 1.1.29: )

It still crashes using OpenGL, but going through DirectX works.

Now, when I open a mailbox, the game crashes.

---

### Post by hikaricore on 2009-09-03
I don't understand what the issue is with ATI users.  Why don't you just manually install and older version of fglrx which supports your card?

---

### Post by techolous on 2009-09-03
> **hikaricore said:**
> I don't understand what the issue is with ATI users.  Why don't you just manually install and older version of fglrx which supports your card?

IIRC, the newer versions of XOrg are incompatible with the older versions of fglrx.

---

### Post by hikaricore on 2009-09-03
> **techolous said:**
> IIRC, the newer versions of XOrg are incompatible with the older versions of fglrx.

That's pretty retarded.  >.>
Sorry I wasn't aware of this, never had such issues with nvidia.   :(

---

