---
title: "Add New Keyboard Layouts"
date: 2013-04-26
forum: Ubuntu Translations
---

### Post by uKashi on 2013-04-26
Hello Guys, I have a question, I am new with Ubuntu (Linux)
When I choose Mongolian standard keyboard on Ubuntu it's old traditional letters (*as old Russian type-machine*) and it's different than new qwerty keyboard.
I wanted to change this to QWERTY, and edited file in:

/usr/share/X11/xkb/symbols/mn

 then it's not saving on **Ubuntu 12.10**. when I put "gksudo nautilus" and paste my file I got ERROR after restart: **Error activating XKB configuration**.
What should I do? how to fix it? Please help me. Otherwise to type on Ubuntu it requiring me to glue old letters on my keyboard.
Thank you.

Standard (Traditional) keyboard on Ubuntu:
 A=&#1049;
O=&#1198;
T=&#1069;
K=&#1054;
M=&#1058; etc (*I don't wanna glue those letters on my keyboard*)

QWERTY letters:
A=A
O=&#1054;
T=&#1058;
K=&#1050;
M=&#1052;
U=&#1059;
E=&#1069;
Z=&#1047; etc, much easier.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2013-05-15
Editing a keyboard layout was made pretty complicated in the X environment. The error message you're gettnling is because of the keyboard file's ownership permissions. Before you edit it, it is owned by root, but when you edit and saveit, its permissions are changed. You can check the other keyboard layout files' permission in the same folder and set your edited file's permission accordingly, that should make it work, provided that your changes are valid.

---

