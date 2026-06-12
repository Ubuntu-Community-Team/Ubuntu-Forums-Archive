---
title: "Cannot use mouse with Server 12.04 and Ubuntu-desktop GUI"
date: 2014-04-03
forum: Server Platforms
---

### Post by Eric_Snyder on 2014-04-03
This is a new issue. I have been using this combo for at least a year. My server just sits there and runs and the screen saver goes dark. At some point I need to do a little work using the keyboard/mouse and GUI. I go to use the keyboard/mouse directly (rather than SSH) it seems that either the screen won't wake up or it wakes up with the keyboard but the mouse is frozen.

Now what is happening is the screen wakes up and the mouse pointer moves with the mouse movements but the OS does not seem to be getting clicks. This leaves me with a non graphical GUI.

I have exchanged mice and the new mouse works the same as the old one - eliminating the mouse as the issue.

It also seems that the server hangs on shutdown waiting for processes to close.

I updated apt-get and reinstalled the desktop - no luck.

Not sure what the issue is. Any help would be appreciated.

---

### Post by houstonbofh on 2014-04-06
1) Is a KVM switch involved?  This can cause these issues...

2) Can you ssh in while it is doing this and look at the logs?

---

### Post by Eric_Snyder on 2014-04-06
No kvm switch. 

Yes. I can ssh in and look at logs. What logs do you suggest?

---

### Post by houstonbofh on 2014-04-28
Bring up a shell, and tail -f /var/log/syslog

Now open the screen and use the mouse with failure.  Unplug and reinsert the mouse.  See if the logs show anything obvious.

---

