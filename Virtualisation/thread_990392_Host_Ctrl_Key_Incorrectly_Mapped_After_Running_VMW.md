---
title: "Host Ctrl Key Incorrectly Mapped After Running VMWare 1.08 on Ubuntu 8.10"
date: 2008-11-22
forum: Virtualisation
---

### Post by DaveTRG on 2008-11-22
I was having trouble with keymappings inside my Backtrack VM on vmware so I created a config file using the following command:

```
echo 'xkeymap.nokeycodeMap = true' > ~/.vmware/config
```

This fixed the problem but has left me with another (bigger) issue.  Now, after starting the vmware client and even after I close it, both ctrl keys in my HOST machine do not function.  Restarting X fixes the issue.

Also, I noticed that if choose to map the CAPS key to Ctrl in the Keyboard settings under System | Preferences, that will function as a (bad) workaround for the issue.

The machine I'm running on is a Dell Inspiron 1420 laptop.

Can anyone help?  Thanks in advance.

---

### Post by DaveTRG on 2008-11-22
this only happens after i put the vm as fullscreen and then exit it.  also, it affects my shift and caps lock keys as well, hence the lack of caps in my post...

---

### Post by PilotJLR on 2008-12-03
Try instead using the info in my post here:
[http://ubuntuforums.org/showthread.php?t=971593&page=2](http://ubuntuforums.org/showthread.php?t=971593&page=2)

I don't know if that will solve your problem, but it will at least get Unity working.  :-)

---

