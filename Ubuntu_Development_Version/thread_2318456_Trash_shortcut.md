---
title: "Trash shortcut"
date: 2016-03-26
forum: Ubuntu Development Version
---

### Post by motang on 2016-03-26
I noticed that I cannot use Super key + t to launch the Trash anymore.  Was this removed? In the pop-up Keyboard Shortcuts, you can still see that it is listed, but when the Super key is held down 't' doesn't appear on top of the Trash icon.

---

### Post by grahammechanical on 2016-03-26
You are right. By design or a bug, I do not know.

Regards.

---

### Post by sammiev on 2016-03-26
Super key + t brings up the Terminal here.

I never noticed that before.

---

### Post by mc4man on 2016-03-26
Seems like a bug as still in the unity source, - 
```
tooltip_text = _("Trash");
  icon_name = "user-trash";
  position = Position::END;
  SetQuirk(Quirk::VISIBLE, true);
  SkipQuirkAnimation(Quirk::VISIBLE);
  SetShortcut('t');
```

But not implemented so super+t is the same as just  t
(- because it's not being used one could set the key binding in Keyboard > Shortcuts > Custom.. 
nautilus trash:///
kb of super+t

---

### Post by motang on 2016-03-28
> Super key + t brings up the Terminal here.

I never noticed that before. 
I think you might have set up a custom keyboard shortcut for that, Ctrl+Alt+T is is what Unit has for brining up Terminal.

---

### Post by motang on 2016-03-28
> But not implemented so super+t is the same as just t
(- because it's not being used one could set the key binding in Keyboard > Shortcuts > Custom..
nautilus trash:///
kb of super+t 
Seems like it, thanks.

---

### Post by mc4man on 2016-03-28
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1562847](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1562847)

---

### Post by PaulW2U on 2016-03-28
Bug confirmed in Launchpad and added to ISO testing tracker.

---

