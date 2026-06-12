---
title: "Max Memory for Virtual Box OSE"
date: 2012-03-02
forum: Virtualisation
---

### Post by lanzd on 2012-03-02
It seems by default the maximum amount of memory supported by Virtual Box OSE is 2560mb.  However I've read from various sites that the max amount of memory for Virtualbox is 16gbs (without using special modifications).  

I would like to set my allocated memory for my guest os to ~8gbs (I have 16 total for my machine).

Can anyone confirm either of these claims with experience?

Thanks, Dan

---

### Post by QIII on 2012-03-02
I have given as much as 4GB to virtual machines on a machine with 16GB -- but I don't use the OSE version.  I don't know if it would be different.

The limit in theory?  Don't know.  Certainly no more than what leaves enough of a share for your host to run.

Virtualbox.org may have some info.  

Why not use the version from virtualbox.org?  You can add their repo to your sources.list.

---

### Post by lanzd on 2012-03-03
All right Ill try that version, I was only using the OSE version because that is what was mostly suggested.  But the OSE version caps it at that amount for some reason.

Thank you.

---

### Post by lanzd on 2012-03-11
All right, I just got a chance to change versions.  I dropped the OSE version and got the one from virtualbox.org for lucid lynx.  Now on this version it seems the max memory you can allocate to a guest OS is 3584 mb.  I would like to use more, I plan to use this VM to play games on windows xp.  Is there a way to bypass this cap?

---

