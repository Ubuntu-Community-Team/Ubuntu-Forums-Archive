---
title: "how to increase wow fps?"
date: 2009-03-11
forum: Wine
---

### Post by uns3r on 2009-03-11
my wow fps is very low 
it goes in between 3-8 fps
how can i get my fps higher

i have tried  

1. Find this key HKEY_CURRENT_USER\Software\Wine\
2. Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder
3. Click right on the wine folder and select [NEW] then [KEY]
4. Replace the text New Key #1 with OpenGL
5. Click right in the right hand pane and select [NEW] then [String Value]
6. Replace New Value #1 with DisabledExtensions (Notice it's case sensitive!)
7. Then double click anywhere on the line, a dialog box will open.
8. In the value field type GL_ARB_vertex_buffer_object
(taken from [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft))

i have also tried launching it with /home/user.../Wow.exe -opengl and i get the same amount of fps as i do when i launch wow with the gnome launcher

edited part
right now i am getting 1-3 fps and its running horribly

---

### Post by cogadh on 2009-03-11
Are you running any desktop effects? If so, turn them off, using that breaks OpenGL functionaliuty as far as Wine is concerned.

---

### Post by uns3r on 2009-03-11
no desktop effects are turned off 
i am also running wow in open window mode

---

### Post by uns3r on 2009-03-11
and i am now getting a little black screen that pops up in the bottom left corner it just gives a quick flash

---

### Post by ozzyprv on 2009-03-12
> **uns3r said:**
> no desktop effects are turned off 
i am also running wow in open window mode


My Ubuntu (8.10) desktop effects are on and I get ~20 fps.
What are your machine specs?

---

### Post by uns3r on 2009-03-12
Machine Specs are
Toshiba Satellite
2G ram 
AMD 64 Athlon x2
ATI Radeon (not sure what one but i know its not the best out there)

i am not sure what to all put for computer specs

and in buildings i am getting about 17fps

---

### Post by ozzyprv on 2009-03-13
uns3r, have you had a look at this?
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154)

I implemented almost every single suggestion there.

Hope it helps!.

---

### Post by uns3r on 2009-03-15
okay i doubled to tripled my fps but now the mini map in the top left is white

---

### Post by ozzyprv on 2009-03-16
> **uns3r said:**
> okay i doubled to tripled my fps but now the mini map in the top left is white

interesting, I had that problem before implementing the tweaks.
Not sure what to tell you. 

O.

---

