---
title: "subpixel font rendering?"
date: 2009-01-03
forum: Wine
---

### Post by pt123 on 2009-01-03
In the latest Wine release it says there is support for 
subpixel font rendering
[http://winehq.org/announce/1.1.12](http://winehq.org/announce/1.1.12)

When I open applications through Wine subpixel font rendering is not being applied. I could not a find an option winecfg too.

Note I am running 1.1.12

---

### Post by oudalrich on 2009-01-04
Look [here]("http://bugs.winehq.org/show_bug.cgi?id=16729#c4"). Worked for me. Though Wine now seems to use a somewhat smaller font size.

---

### Post by pt123 on 2009-01-04
Thanks for that but I am finding certain parts of the applications using it and other parts not.
As you can see from this screenshot of Ant Movie Catalog.

Note I have set the DPI to 120 and used these font settings in the ~/.wine/drive_c/windows/win.ini
```

[Desktop]
MenuFontSize=12
MessageFontSize=12
StatusFontSize=12
IconTitleSize=12
MenuFont="Bitstream Vera Sans"
MessageFont="Bitstream Vera Sans"
StatusFont="Bitstream Vera Sans"
IconTitleFaceName="Bitstream Vera Sans"

```
as shown in this page
[http://www.justlinux.com/forum/showthread.php?t=141123](http://www.justlinux.com/forum/showthread.php?t=141123)

---

