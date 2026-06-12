---
title: "how to sset wine to its default settings"
date: 2011-04-03
forum: Wine
---

### Post by kolmad on 2011-04-03
here is the code for if you want you can make it brand new!

rm -rf $HOME/.wine

rm -f $HOME/.config/menus/applications-merged/wine*

rm -rf $HOME/.local/share/applications/wine

rm -f $HOME/.local/share/desktop-directories/wine*

rm -f $HOME/.local/share/icons/????_*.xpm

Do each line separate.

Add sudo apt-get delete wine to delete it completetly.

Hope this helps!:)

---

