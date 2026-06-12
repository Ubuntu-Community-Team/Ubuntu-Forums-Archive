---
title: "Advice on locking the screen."
date: 2009-09-02
forum: Security
---

### Post by Ladadadada on 2009-09-02
At work I use Ubuntu as my desktop.  I have it set to lock the screen and require a password to deactivate the screensaver however sometimes when I come back to the computer the screensaver is not active and no password is required to use it.

My guess is that the screensaver is crashing and dumping me back to the desktop.

Is there a more reliable solution for locking the computer than the screensaver ?

---

### Post by fela on 2009-09-02
> **Ladadadada said:**
> At work I use Ubuntu as my desktop.  I have it set to lock the screen and require a password to deactivate the screensaver however sometimes when I come back to the computer the screensaver is not active and no password is required to use it.

My guess is that the screensaver is crashing and dumping me back to the desktop.

Is there a more reliable solution for locking the computer than the screensaver ?

It means either that
a) you've found a serious security bug and you should report it at launchpad

or b) either you're not actually locking the screen or someone knows your password and unlocked it themselves.

I think it's most likely that you're not locking it properly.

---

### Post by Ladadadada on 2009-09-02
Is it anything more complicated than ctrl-alt-L ?

That's how I lock manually it and when I do that it requires a password to unlock.  But sometimes (usually after lunch) the screensaver is not running when I get back.

Even if I didn't lock it manually, the screensaver is set to activate after 10 minutes so after a lunch break it should be active.

No one knows my password.  I can be sure of that.

With b) ruled out (at least in my mind) I need to go about verifying a).

I have killed and restarted gnome-screensaver with the --debug option and the output going to a file.  Next time I see this issue I will check what's in the file and post it here or at launchpad depending on what I find.

---

### Post by fela on 2009-09-02
OK that's really strange. I think you should file a bug report.

---

### Post by cdenley on 2009-09-02
Did you verify your computer was running since before you locked it?
```

uptime

```
If someone has physical access, they could pull the plug and reboot, enable root, change your password, log you in, then change your password back. This does seem like an unlikely scenario, though.

---

### Post by cdenley on 2009-09-02
What version of ubuntu are you using? Have you installed all the available security updates? Apparently this type of bug is not uncommon.

[http://www.ubuntu.com/usn/USN-669-1](http://www.ubuntu.com/usn/USN-669-1)
[http://www.ubuntu.com/usn/usn-474-1](http://www.ubuntu.com/usn/usn-474-1)
[http://www.ubuntu.com/usn/usn-537-1](http://www.ubuntu.com/usn/usn-537-1)
[http://www.ubuntu.com/usn/usn-688-1](http://www.ubuntu.com/usn/usn-688-1)
[http://www.ubuntu.com/usn/usn-537-2](http://www.ubuntu.com/usn/usn-537-2)

I don't think there is a better method of locking your desktop besides actually logging out. If there were, ubuntu would use it by default.

---

### Post by scorp123 on 2009-09-03
> **Ladadadada said:**
>  My guess is that the screensaver is crashing and dumping me back to the desktop. I have seen this happen right in front of my nose!

Since then I only use the "Black screen" screensaver. That one just works as it has no fancy graphics or anything that might cause a crash.

I'd recommend you use that one?

BTW, nobody has mentioned option C)

Somebody logged in remotely and then gave the screensaver a **kill -9** ? If there is a SSH server running then it's a possibility.

But it's far more likely the stoopid screensaver killed itself, core dumped, segmentation faulted or something like that ...

---

