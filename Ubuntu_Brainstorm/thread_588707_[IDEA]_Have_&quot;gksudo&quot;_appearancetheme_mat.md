---
title: "[IDEA] Have &quot;gksudo&quot; appearance/theme match those of those executing the programs"
date: 2007-10-23
forum: Ubuntu Brainstorm
---

### Post by botulismo on 2007-10-23
I know this is a small detail, but I do find it distracting when I am using a program that is functioning under gksudo and the theme/appearance/gtk/window settings/whatever exactly it is do not match. It's one of those small touches that, I think, would make Ubuntu look more professional if one's theme was seamlessly applied whether doing something as a super user or not.

To me, the only other option is manually enabling the root account just to match my current settings, at least, that is the only option that has worked for me previously. Is there a way to get that accomplished? I'm not a coder, I would not know, but it does seem bothersome to me. I'm including a screenshot of what it looks like, for example, when Synaptic opens.

Anyone else?

---

### Post by smartboyathome on 2007-10-23
> **botulismo said:**
> I know this is a small detail, but I do find it distracting when I am using a program that is functioning under gksudo and the theme/appearance/gtk/window settings/whatever exactly it is do not match. It's one of those small touches that, I think, would make Ubuntu look more professional if one's theme was seamlessly applied whether doing something as a super user or not.

To me, the only other option is manually enabling the root account just to match my current settings, at least, that is the only option that has worked for me previously. Is there a way to get that accomplished? I'm not a coder, I would not know, but it does seem bothersome to me. I'm including a screenshot of what it looks like, for example, when Synaptic opens.

Anyone else?

You can also use alt-f2 and type "gksudo gnome-appearance-properties %F". That way you can change your root theme and not have to log out.

---

### Post by aamukahvi on 2007-10-24
You need to have the theme in /usr/share/themes. If it's just in your ~/.themes the apps running with root privileges won't see it and thus use some default theme/no theme.

---

### Post by yabbadabbadont on 2007-10-24
I've posted this before somewhere.
```
sudo -i
ln -s /home/username/.icons
ln -s /home/username/.fonts
ln -s /home/username/.themes
ln -s /home/username/.gtkrc-1.2

```
That should take care of the issue.

---

### Post by r3m0t on 2007-10-24
> **aamukahvi said:**
> You need to have the theme in /usr/share/themes. If it's just in your ~/.themes the apps running with root privileges won't see it and thus use some default theme/no theme.

In that case, gksudo can copy the theme from your ~/.themes into /tmp/something and then make the child process use that theme. I don't know how, but it should be possible.

Some people use different themes deliberately to make sure they don't run something as root that they shouldn't - a bit like having different colours of bash prompts for different servers, and different accounts.

For most people, though, it's just a visual inconsistency that needs to be fixed.

---

