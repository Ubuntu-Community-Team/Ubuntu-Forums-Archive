---
title: "P7 - Suspend crashes X and halts networking"
date: 2012-08-14
forum: System76 Support
---

### Post by wwillard on 2012-08-14
I have been experiencing a problem with suspend for the last two months.  Approximately every 3-4 times that I shut my laptop lid, I notice that my machine fails to suspend.  When I open the laptop, X has crashed, and I am at the login screen.  When I login, I am no longer able to connect to my wireless router.

I am running Ubuntu 12.04 with kernel 3.2.0-29-generic, and I have installed the proprietary ATI drivers.  As others have reported, I was unable to install the updates for the drivers.

One other glitch is that even when I am able to suspend correctly, sometimes I do not see the login dialog upon resume.  I can type in my password anyway, and login at that point, even if I do not see the dialog prompt, however.

---

### Post by isantop on 2012-08-14
> **wwillard said:**
> I have been experiencing a problem with suspend for the last two months.  Approximately every 3-4 times that I shut my laptop lid, I notice that my machine fails to suspend.  When I open the laptop, X has crashed, and I am at the login screen.  When I login, I am no longer able to connect to my wireless router.

I am running Ubuntu 12.04 with kernel 3.2.0-29-generic, and I have installed the proprietary ATI drivers.  As others have reported, I was unable to install the updates for the drivers.

One other glitch is that even when I am able to suspend correctly, sometimes I do not see the login dialog upon resume.  I can type in my password anyway, and login at that point, even if I do not see the dialog prompt, however.

Does the problem occur if you use the Fn+F4 hotkey to suspend the system? I also own a PanP7 personally, and I haven't had any issues. The only differences between my setup and yours are that I haven't installed the proprietary drivers, and I always suspend with Fn+F4.

---

### Post by wwillard on 2012-08-14
I'll try using Fn+F4.  I have always used either the Suspend menu item, or just shut the laptop.

I was also having this issue before I installed the proprietary drivers.

One more piece of data:  I am running xfce as my window manager. I don't know if that matters or not.

---

### Post by tstavely on 2012-08-27
> **wwillard said:**
> I'll try using Fn+F4.  I have always used either the Suspend menu item, or just shut the laptop.

I was also having this issue before I installed the proprietary drivers.

One more piece of data:  I am running xfce as my window manager. I don't know if that matters or not.

I have no proprietary drivers and run an unmodified Unity desktop, etc. Suspend often to always fails if I close the lid of my Thinkpad T420s but always succeeds if I use Fn-F4 to activate it. This is strange and bothersome behavior. Is a solution known?

Tony

---

### Post by isantop on 2012-08-28
> **tstavely said:**
> I have no proprietary drivers and run an unmodified Unity desktop, etc. Suspend often to always fails if I close the lid of my Thinkpad T420s but always succeeds if I use Fn-F4 to activate it. This is strange and bothersome behavior. Is a solution known?

Tony

No, not at this time. However, it seems to be common to all systems on 12.04, so it should be fixed soon.

---

