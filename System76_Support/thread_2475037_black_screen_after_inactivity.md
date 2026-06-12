---
title: "black screen after inactivity"
date: 2022-05-14
forum: System76 Support
---

### Post by luizferw on 2022-05-14
Hello everyone, I have a problem that sometimes after I stay away from the computer for some time, a black screen appears, which follows the attached photo below. It doesn't always happen, but today was the second time, and when it happens I have to force the computer to shut down, but when it starts again it's completely normal.

[https://ubuntuforums.org/attachment.php?attachmentid=290450&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=290450&stc=1)

---

### Post by TheFu on 2022-05-14
That is a system crash.

When you reboot, run 
```
journalctl -b -1 -perr
```
 and look through the error messages from the **last boot**. The "-b -1" said 1 boot ago.  You can look through "-b -2" for 2 boots ago ... etc. Looks like there is a stack trace just above what the image captured.  That can provide information on the root cause by seeing which functions were being called.  With the bit shown, I'd guess that the GPU driver is at fault, so perhaps the wrong driver is being used or it didn't get properly re-linked after a kernel update.  You can reinstall it, which may force the re-link and solve the issue.  This is just a guess. The stack trace really will provide excellent hints for the problem.

To test, I'd think the problem is related to whatever screen saver is used, so just make the timeout for the screen saver shorter to cause the issue?

BTW, the numbers at the beginning of each line are timestamps. The journalctl will make those human readable.

If you are using Wayland with nVidia, I'd recommend changing to X11 instead. Also, which release and which DE are you running. That is very important.

---

