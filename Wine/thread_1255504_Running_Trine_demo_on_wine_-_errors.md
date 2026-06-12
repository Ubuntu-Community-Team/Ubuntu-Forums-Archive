---
title: "Running Trine demo on wine - errors"
date: 2009-09-01
forum: Wine
---

### Post by themusicalduck on 2009-09-01
I'm trying to run the Trine demo on Wine. As soon as I run trine.exe, I get this output:

```
fixme:win:EnumDisplayDevicesW ((null),0,0x32f4dc,0x00000000), stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x2314c58, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x32f7c0)
fixme:wbemprox:DllCanUnloadNow 
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7bc45ab4

```

I can see a splash screen for half a second until it crashes, but that's it.

I have installed directx9 with winetricks and physx software as recommended in comments on appdb. I can't think of anything else to try and make it work :(

All my other wine programs are working fine.

I have wine 1.1.28 and Ubuntu 9.04 32 bit. Doing a google search on that error only brings up someone who had a problem running Eve, and they suspected it was related to using a 64 bit system.. but that doesn't apply to me.

---

### Post by castlefox on 2009-09-02
What graphics hardware are you using?

---

### Post by themusicalduck on 2009-09-02
Nvidia GTX 260

In addition, I tried installing it using a clean .wine directory and got the same result :/

---

### Post by themusicalduck on 2009-09-04
bump

---

