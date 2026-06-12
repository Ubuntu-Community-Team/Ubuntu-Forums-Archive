---
title: "Metacity button layout"
date: 2012-11-30
forum: Ubuntu Development Version
---

### Post by paul_in_london on 2012-11-30
This is really just a note to self.

I recently needed to move the window buttons back to the left and I couldn't remember how to do it.

I think it was the third of these commands that did the trick for gnome classic (no effects) - i.e. metacity:

```
gsettings set org.gnome.shell.overrides button-layout 'close,minimize,maximize:'
gconftool --type string --set /desktop/gnome/shell/windows/button_layout "close,minimize,maximize:"
gsettings set org.gnome.desktop.wm.preferences button-layout close,minimize,maximize:
```

And for cinnamon:

```
gsettings set org.cinnamon.overrides button-layout 'close,minimize,maximize:'
```

---

### Post by serdotlinecho on 2012-11-30
Try  dconf-tools, navigate to this path > *org/gnome/desktop/wm/preferences*

[IMG]http://handytutorial.com/wp-content/uploads/2012/09/move-window-buttons-dconf-editor.png[/IMG]

---

### Post by paul_in_london on 2012-12-01
> **serdotlinecho said:**
> Try  dconf-tools, navigate to this path > *org/gnome/desktop/wm/preferences*

[IMG]http://handytutorial.com/wp-content/uploads/2012/09/move-window-buttons-dconf-editor.png[/IMG]

Thanks - yes, I think I did that at the time as well. :)

---

