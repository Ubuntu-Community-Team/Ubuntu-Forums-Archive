---
title: "Show system menu icons"
date: 2010-09-28
forum: Sudan Team
---

### Post by zero-n on 2010-09-28
After installing Ubuntu you will notice that icons of system menu are missing to solve this issue run this command from your terminal as a normal user not as a root:
```

gconftool-2 --type Boolean --set /desktop/gnome/interface/menus_have_icons True

```

[source]("http://ubuntu-blog.com/show-viewsystem-menu-icons-visualize-karmic-koala")

---

