---
title: "Lost sticky notes data after installed Feisty Fawn"
date: 2007-04-20
forum: The Cafe
---

### Post by khanhlnq on 2007-04-20
I just fresh-installed Feisty Fawn yesterday. I have a separate **/home** partition to keep my personal data.
After installed, everything works fine except I lost all my sticky notes although my profile still there.
Do you know where sticky notes store data or do you know a way to recover sticky notes data? I took notes so many important things that if I don't have sticky notes I will forget all.

---

### Post by qamelian on 2007-04-20
I'm not sure why your notes aren't showing up, but the data is stored in /home/your_username/.gnome2/stickynotes_applet . The text is stored in an xml file and is easily readable, so you should be able to just open this file in gedit and copy and paste the data into new notes.

---

### Post by khanhlnq on 2007-04-20
> **qamelian said:**
> I'm not sure why your notes aren't showing up, but the data is stored in /home/your_username/.gnome2/stickynotes_applet . The text is stored in an xml file and is easily readable, so you should be able to just open this file in gedit and copy and paste the data into new notes.
Last time I want to backup my sticky notes, I tried
```
locate stickynotes
```
and I found your mentioned folder. But the funny thing is the folder was not exist but my sticky notes still show so I didn't backup (I wonder why I did not copy/paste to gedit at that time :( )
Now after installed new Ubuntu version, the folder is not exist either, my old notes are all lost, my new notes can be added.

---

### Post by qamelian on 2007-04-20
The folder does exist but the dot (.) as the first character in a file or directory name makes the directory hidden. Just press ALt-F2 to get a command prompt and type in:

```
gedit ~/..gnome2/stickynotes_applet
``` and press the enter key. Gedit will open and display the contents of the file.

---

### Post by khanhlnq on 2007-04-20
> **qamelian said:**
> The folder does exist but the dot (.) as the first character in a file or directory name makes the directory hidden. Just press ALt-F2 to get a command prompt and type in:

```
gedit ~/..gnome2/stickynotes_applet
``` and press the enter key. Gedit will open and display the contents of the file.I found the file now, but it's the new content. My old notes was totally lost:(

---

