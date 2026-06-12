---
title: "Problem editing grub"
date: 2014-04-15
forum: Ubuntu, Linux and OS Chat
---

### Post by meltdown2 on 2014-04-15
hi,
In the archive /etc/grub.d/05_debian_theme, I edited that:

set menu_color_normal=255,0,0/0,0,0
set menu_color_highlight=0,0,0/255,0,0

... but It doesn't work, ¿what's wrong? Thank you.

---

### Post by oldfred on 2014-04-15
Do you also have an image.
Not sure exactly how you edited it.

Details here:
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by grahammechanical on 2014-04-15
Have you run?

```
sudo update-grub
```

Regards.

---

### Post by meltdown2 on 2014-04-15
I edited grub with gedit and I don't have any Image. Yes I've already updated grub. If I edit this way It works:
[COLOR=#000000]
set menu_color_normal=red/black[/COLOR]
[COLOR=#000000]set menu_color_highlight=black/red

[/COLOR]... but I don't want this colors I want the color 255,0,0 . I've searched information in the forum and I see that: [http://ubuntuforums.org/showthread.php?t=1739412](http://ubuntuforums.org/showthread.php?t=1739412) in this thread says the html code #000000 works, and rgb too, but It doesn't works for me. ¿How I can fix It? Thank you very much :D

---

### Post by oldfred on 2014-04-15
You may need the quotes it shows in the examples?

> [h=4]6.2.1 Colors[/h]  Colors can be specified in several ways: 
 
[LIST]
[*] HTML-style &#8220;#RRGGBB&#8221; or &#8220;#RGB&#8221; format, where *R*, *G*, and *B* are hexadecimal digits (e.g., &#8220;#8899FF&#8221;)
[*] as comma-separated decimal RGB values (e.g., &#8220;128, 128, 255&#8221;)
[*] with &#8220;SVG 1.0 color names&#8221; (e.g., &#8220;cornflowerblue&#8221;) which must be specified in lowercase.
[/LIST]
  [h=4][/h]

---

### Post by meltdown2 on 2014-04-16
It does not work with quotes :(

---

