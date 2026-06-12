---
title: "How do I change the function definitons for the keyboard?"
date: 2014-10-28
forum: System76 Support
---

### Post by sgrizzard on 2014-10-28
Specifically, I want to map [fn][rarrow] to the "next song" media button.

---

### Post by tgalati4 on 2014-10-28
Open your control center->Keyboard Shortcuts->Sound (Next Track).  Click on it with the mouse so it is highlighted.  Hit the desired key combination (Function Next Arrow).  If it shows up as a keycode, then it should work.  If it does not show up, then you need to do some homework.  Close the box and test in various music players.

Sometimes your Function keys are controlled by the BIOS and are not available to the operating system.  Other times, you can trick it by using *setkeycodes* to assign a key scan code to an actual, unused keycode, then assign that keycode to XFAudioNext using *xmodmap*.  This is tedious, but if the simple keyboard shortcut works, then you are done.

---

