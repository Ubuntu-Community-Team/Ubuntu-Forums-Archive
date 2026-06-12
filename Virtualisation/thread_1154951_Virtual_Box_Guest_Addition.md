---
title: "Virtual Box Guest Addition"
date: 2009-05-10
forum: Virtualisation
---

### Post by elgoog on 2009-05-10
Is it possible to install all the features of the Guest Additions ISO in Windows XP Guest, except the video driver?

I like to have the resolution set at 1024x768, but the video driver from guest addition disable it to 800x600.

Using Jaunty as Host.

---

### Post by RedSingularity on 2009-05-10
The guest additions should allow you to enlarge the display!  It should not shrink it on you.

---

### Post by elgoog on 2009-05-10
> **Shadow121 said:**
> The guest additions should allow you to enlarge the display!  It should not shrink it on you.

It does. Check out the image. Only one resolution option works. The other one doesn't appear or is non-functional.

---

### Post by RedSingularity on 2009-05-10
You are using VirtualBox OSE?  That may be the problem.  Use the official version.  [HERE](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by bobince on 2009-05-10
Works fine with OSE for me. Independently of the Display Properties panel, resizing the host window should in any case cause the guest display to resize to match, which is clearly not happening in the screenshot.

Curious. Is everything appearing OK in the guest's Device Manager?

---

### Post by Nintendo01 on 2009-05-10
On mine sometimes I have to put it in seamless mode (Host key + L) then take it back out of seamless mode, and then it will let me change the display size on the Windows guest.

---

