---
title: "configure keyboard shortcuts on citrix client (receiver) for linux"
date: 2013-05-28
forum: Virtualisation
---

### Post by cccc on 2013-05-28
Hi

I cannit minimize citrix virtual desktop running on Ubuntu with citrix client (receiver), version 12.1.0.
Knows someone howto configure citrix client to get Shift-F2 working like on Windows machines?

---

### Post by cccc on 2013-06-05
I still cannot find any solution.

---

### Post by handheld-penguin on 2013-06-07
Use Ctrl-F1 or Ctrl-F2 (I think). Double hitting them usually works.

---

### Post by cccc on 2013-06-07
> **handheld-penguin said:**
> Use Ctrl-F1 or Ctrl-F2 (I think). Double hitting them usually works.

I have tried, but still doesn't work.

---

### Post by dragonfly41 on 2013-06-09
Perhaps try installing autokey .. [http://code.google.com/p/autokey/](http://code.google.com/p/autokey/)   ?

---

### Post by Habitual on 2013-06-10
[CTX140219 - How to Enable or Disable Hotkeys within an ICA File (including Template.ica) - Citrix Knowledge Center]("http://support.citrix.com/article/CTX140219") ?

---

### Post by handheld-penguin on 2013-06-16
This seems like a change in the newest ubuntu. As I mentioned earlier this used to work well for me. But now for the life of me I cannot leave my fullscreen citrix session. I usually have to switch to a tty and kill the process there before switching back to my graphical desktop. Seems poor to me!

---

### Post by handheld-penguin on 2013-06-16
I think I managed to restore it! 
Add the following to both ~/.ICAClient/appsrv.ini and ~/.ICAClient/wfclient.ini (or either of these two if only one exists - I might have had one lying around from an old install). My wfclient.ini already had it but my appsrsv didn't. Adding to appsrv fixes.
Add the following just after [WFCClient]
```

Hotkey1Char=F1
Hotkey1Shift=Shift
Hotkey2Char=F3
Hotkey2Shift=Shift
Hotkey3Char=F2
Hotkey3Shift=Shift
Hotkey4Char=F1
Hotkey4Shift=Ctrl
Hotkey5Char=F2
Hotkey5Shift=Ctrl
Hotkey6Char=F2
Hotkey6Shift=Alt
Hotkey7Char=plus
Hotkey7Shift=Alt
Hotkey8Char=minus
Hotkey8Shift=Alt
Hotkey9Char=F3
HotKey9Shift=Ctrl
Hotkey10Char=F5
HotKey10Shift=Ctrl
Hotkey11Char=plus
Hotkey11Shift=Ctrl
Hotkey12Char=plus
Hotkey12Shift=Ctrl
Hotkey13Char=plus
Hotkey13Shift=Ctrl

```

And you should be good to go - this is based of info from Habituals update.

---

### Post by cccc on 2013-07-06
> **handheld-penguin said:**
> I think I managed to restore it! 
Add the following to both ~/.ICAClient/appsrv.ini and ~/.ICAClient/wfclient.ini (or either of these two if only one exists - I might have had one lying around from an old install). My wfclient.ini already had it but my appsrsv didn't. Adding to appsrv fixes.
Add the following just after [WFCClient]
```

Hotkey1Char=F1
Hotkey1Shift=Shift
Hotkey2Char=F3
Hotkey2Shift=Shift
Hotkey3Char=F2
Hotkey3Shift=Shift
Hotkey4Char=F1
Hotkey4Shift=Ctrl
Hotkey5Char=F2
Hotkey5Shift=Ctrl
Hotkey6Char=F2
Hotkey6Shift=Alt
Hotkey7Char=plus
Hotkey7Shift=Alt
Hotkey8Char=minus
Hotkey8Shift=Alt
Hotkey9Char=F3
HotKey9Shift=Ctrl
Hotkey10Char=F5
HotKey10Shift=Ctrl
Hotkey11Char=plus
Hotkey11Shift=Ctrl
Hotkey12Char=plus
Hotkey12Shift=Ctrl
Hotkey13Char=plus
Hotkey13Shift=Ctrl

```

And you should be good to go - this is based of info from Habituals update.

Thx, I've tried and still doesn't work.
BTW I'm using Citrix Desktop from XenServer 6.1.

---

### Post by plasticanet on 2013-09-20
In the host environment configure the shortcut to Minimise window: Start -> Keyboard -> Shortcuts -> Minimise window (i.e. I picked ALT+F9).
Then from the citrix receiver CTRL+F2 then ALT+F9 ... then click anywhere on the screen.

---

