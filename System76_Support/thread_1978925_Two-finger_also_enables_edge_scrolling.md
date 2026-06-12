---
title: "Two-finger also enables edge scrolling"
date: 2012-05-12
forum: System76 Support
---

### Post by brdmn on 2012-05-12
Not sure if this is a System76 specific issue, but I thought folks here might know the answer... in the touchpad settings for XFCE, there are three radio buttons for scrolling: No scrolling, Edge scrolling, and Two finger scrolling.  Selecting the last option also enables edge scrolling, in spite of the radio buttons which seem to imply otherwise.  Is there a way to have only two finger scrolling without enabling edge scrolling?

---

### Post by isantop on 2012-05-14
> **brdmn said:**
> Not sure if this is a System76 specific issue, but I thought folks here might know the answer... in the touchpad settings for XFCE, there are three radio buttons for scrolling: No scrolling, Edge scrolling, and Two finger scrolling.  Selecting the last option also enables edge scrolling, in spite of the radio buttons which seem to imply otherwise.  Is there a way to have only two finger scrolling without enabling edge scrolling?

Not sure about XFCE, but that's not the case in Gnome. Maybe if you check in your gconf-settings?

---

### Post by brdmn on 2012-05-14
I don't know why gconf-settings would be related to XFCE, but your post gave me an idea.  I ran xfce4-settings-editor (as opposed to the more friendly Settings Manager application) and reset the property "Two-Finger Scrolling" in the "Pointers/Synaptics" section.  This actually removed the key.  I'm not sure what exactly happened, but now two-finger scrolling works and edge-scrolling is disabled, just what I wanted.

I'll need to do some reading on XFCE to see if I can figure out what happened.  I don't really understand how things like gconf and xfconf work behind the scenes.

Update: After I selected the "Two-Finger Scrolling" option in the Settings Manager, the key is now back, but nothing looks different.  So the problem is solved, but I have no idea what really solved it!

Still nothing: So I still don't know how the problem got fixed, but I love the two-finger scrolling option!

---

