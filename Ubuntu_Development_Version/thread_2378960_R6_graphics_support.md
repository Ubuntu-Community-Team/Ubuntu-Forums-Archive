---
title: "R6 graphics support?"
date: 2017-11-29
forum: Ubuntu Development Version
---

### Post by exploder on 2017-11-29
I have an HP 17-g121-wm laptop and I am wondering if it's hardware will be supported under the new LTS when it arrives? Here are the specs [https://support.hp.com/us-en/document/c04773111](https://support.hp.com/us-en/document/c04773111)
The laptop is currently running Windows 10 and I would really like to run Ubuntu or Mint but 16.04 and other current releases will not run on this hardware. Sorry for being kind of vague with the question but I am sure some of you understand where I am coming from.

---

### Post by QIII on 2017-11-29
It doesn't look like the open source AMDGPU driver supports your GPU, but I would be surprised if the open source Radeon driver doesn't.  Have you actually tried?

Radeon with the VESA package should work very well, in fact.  It often outperforms AMDGPU plus AMDGPU-PRO.

---

### Post by exploder on 2017-11-29
Thanks for the response! I will have to grab the latest daily build when I get home from work tonight and see how it goes. I have tried 16.04 and 17.10 but the live dvd never makes it to the desktop no matter what I have tried...

---

