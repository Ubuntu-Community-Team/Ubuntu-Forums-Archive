---
title: "control master volume with shortcuts"
date: 2008-06-10
forum: System76 Support
---

### Post by 982000971 on 2008-06-10
I use shortcuts to easily control the volume on my serval laptop. Specifically Ctrl+Up / Ctrl+Dwn. But with the latest Ubuntu update my shortcuts now control the Microphone Volume (which is useless). How do I get it back to controlling the Master Volume?

---

### Post by thomasaaron on 2008-06-10
Have you tried going to System > Preferences > Keyboard Shortcuts and resetting those shortcuts?

---

### Post by 982000971 on 2008-06-10
Yup. No dice! :confused:

---

### Post by issih on 2008-06-10
What audio track does the volume control in the notification tray now change?, if that too is the microphone, then you just need to reset the default track to be the master control, (its in the menus somewhere :s) and you should be back to normal. 

Odd thing to have happened if that is it...

---

### Post by 982000971 on 2008-06-10
Hmm, nope. My tray icon still controls the Master Volume. It's only my shortcut...

---

### Post by thomasaaron on 2008-06-11
I'm a little confused. I don't think Ctrl-Up and Ctrl-Down is the default way to adjust volume on the Serval. It is Fn-F7 and Fn-F8.

What did you use to assign Ctrl-Up and Ctrl-Down to adjust the volume. If this is just a matter of semantics, and you meant to specify the function key combinations, than you can change what the function key combinations do in System > Preferences > Sound. Just highlight the device you want them to control down at the bottom of the window.

If you re-assigned the ctrl-up and ctrl-down keys, you need to provide us with information as to how you did that.

---

### Post by 982000971 on 2008-06-11
Yeah, all my keyboard shortcuts are custom. I don't use the default ones. So I assigned Ctrl+Up and Ctrl+Dwn using System > Preferences > Keyboard Shortcuts. I have many assigned shortcuts, but the volume control is the only one that seems to have changed with the latest upgrade.

As a side note, Fn+F7 and Fn+F8 are not controlling Master Volume (or any volume) either. I'm not sure when that would have started though because I never use it.

----- Hmm, and get this. I had tried assigning different keys to adjust volume before I made my original post but they would all control the Microphone Volume. But I just tried assigning Fn+F7 and Fn+F8 and for some reason that enabled it to control Master Volume. So then I tried reassigning my Ctrl+Up and Ctrl+Dwn setup... and it stuck. It now controls the Master Volume again.

This may have been what you meant by resetting the shortcuts in your first post. By manually restoring the defaults. I didn't even remember the defaults, I had just tried clearing the assigned shortcuts...

Well. Works now. Thanks.

---

