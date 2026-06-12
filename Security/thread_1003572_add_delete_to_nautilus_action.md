---
title: "add delete to nautilus action"
date: 2008-12-06
forum: Security
---

### Post by mahmater on 2008-12-06
hi,

 I installed the secure-delete package but I couldn't add the delete function to Nautilus-action. will you help?

---

### Post by The Cog on 2008-12-06
I'm not familiar with secure delete, but the normal nautilus delete can be enabled from the nautilus menu Edit->Preferences, Behaviour (last line).

---

### Post by bp1509 on 2008-12-06
d

---

### Post by mahmater on 2008-12-07
well,I have no idea how to write scripts. before I formatted my PC I added the secure delete function to nautilus-action (I came across its parameter in a certain article which I could not remeber) and it worked like magic. now,I just forgot how i added it before ...

---

### Post by go_beep_yourself on 2008-12-12
Try using the shred command. Do man shred for more info.

To quickly open a terminal in the directory you are browsing in nautilus, use the nautilus-open-terminal package, and then right click anywhere in nautilus and open terminal. This is the best advice I can give you since I never used that script you are talking about before.

---

### Post by Rebootkid on 2010-03-02
They're talking about this: 
[http://www.gnome-look.org/content/show.php/shred_file?content=66603](http://www.gnome-look.org/content/show.php/shred_file?content=66603)

I've got the script, and it includes a screen shot of how to set the "action" when you download the tarball, but I'll be darned if I know how to create an "Action" in Nautilus. Still digging.

Ah-Ha!

First off, you've got to install the nautilus actions package.
"sudo apt-get install nautilus-actions"

Then, you have to set it up. Click System, Preferences, "Nautilus Actions"

Click the "Add" button

Assign a label. I called mine "Shred"
Give it a tool tip
Assign an icon
List off the path to the file. (Mine I set to ~/bin/shred_file
Give it the parameter %M

Note: All that info is in the screen shot from the above tarball

That's all it takes to set it up. Click the appropriate OK buttons, and log out, then back in. You should find the "shred" option available now.

---

