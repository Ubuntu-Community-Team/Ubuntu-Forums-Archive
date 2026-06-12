---
title: "ubuntu , apache, imagettftext get path problem"
date: 2010-11-21
forum: Server Platforms
---

### Post by singying304 on 2010-11-21
when I use imagettftext function,

imagettftext($im, 20, 0, 11, 21, $grey, 'arial.ttf', $text);   don't work

imagettftext($im, 20, 0, 11, 21, $grey, './arial.ttf', $text); work

can I change it? can I change it to no need to type "./" then also can work?

because many people just type 'xxx.txt'.

thanks in advance.

---

### Post by Ryan Dwyer on 2010-11-21
I don't think you can. If the font filename is coming from an external source (such as user input) then you should add ./ or determine the full absolute path.

---

### Post by singying304 on 2010-11-21
> **Ryan Dwyer said:**
> I don't think you can. If the font filename is coming from an external source (such as user input) then you should add ./ or determine the full absolute path.
but the airal.ttf file is place in the same as the php file's folder.

---

### Post by Ryan Dwyer on 2010-11-21
That doesn't matter. The font filename must be either absolute or have a ./ at the start.

---

### Post by singying304 on 2010-11-21
> **Ryan Dwyer said:**
> That doesn't matter. The font filename must be either absolute or have a ./ at the start.
but this statement
imagettftext($im, 20, 0, 11, 21, $grey, 'arial.ttf', $text);
can work on other server, but can't work on mines.
I don't know why...

---

