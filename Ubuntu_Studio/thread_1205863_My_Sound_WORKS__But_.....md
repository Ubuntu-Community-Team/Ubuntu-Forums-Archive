---
title: "My Sound WORKS  But ...."
date: 2009-07-06
forum: Ubuntu Studio
---

### Post by kibster on 2009-07-06
But the recording doesnt, I have tried what seems to be everything...nothing seems to work

I have a  Dynex sound card 5.1  works fine in the machine  but sound recorder doesnt see it..or is looking someplace for it and cant get it to reconinze it... I am trying to sound recorder

I would appreciate some help from the forum guru's''

Thx Russ

---

### Post by igorzwx on 2009-07-06
Step 1: Enable recording in your Alsa Mixer

Step 2: Create a folder

Step 3: Open terminal in this folder

Step 4: Type this command:

arecord -f S16_LE -c1 -r44100 -t wav mumu.wav

Step 5: Stop recordind with Ctrl+C

---

### Post by igorzwx on 2009-07-06
To may life easy you can install this magic tool:

nautilus-open-terminal

You can install it with Synaptic, or from terminal

sudo apt-get install nautilus-open-terminal

Then right click on the Desktop -> Create folder

Then right click on this folder and select "Open in Terminal" from
the drop-down menu

Now you need to copy-and-paste the command "arecord ..."
to the Terminal (paste with Ctrl+V), then ENTER.

Stop recording with Ctrl+C. 
The wave will be in the folder.

You can open it with Audacity.

It is much easy then to make that recorder work.

---

