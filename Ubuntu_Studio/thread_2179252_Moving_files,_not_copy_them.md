---
title: "Moving files, not copy them"
date: 2013-10-07
forum: Ubuntu Studio
---

### Post by Kanichiro on 2013-10-07
Since I reformatted, and updgraded to Ubuntu Studio 13.04, whenever I try to "move" a file into a folder, the system "copies" the file instead. 

I am moving these files into a folder on the same desktop/partician as the original file.

Is there a setting I can change to fix this? It's a real pain to copy a file into a folder, and then have to delete the original file.  Before the system would just move the file into the desired folder for me without creating a new copy.

Thanks!

---

### Post by TheFu on 2013-10-07
So typing ```
mv some-file-name ~/target/directory/
``` doesn't work?

---

### Post by Kanichiro on 2013-10-07
> **TheFu said:**
> So typing ```
mv some-file-name ~/target/directory/
``` doesn't work?

Thanks, but I use and prefer the "drag & drop" method over using commands.

 I was able to do this before, and did not have a problem until I updated to the new version of Ubuntu Studio.

---

### Post by TheFu on 2013-10-07
I can understand that, but we need to know which program you are using, right?  Also, it would help to know if the CLI method is broken on your machine too.  See the connection?  Troubleshooting 101.

Thunar, Nautilus, or some other program?  Also, the kernel could matter.  What do the logs show?

---

### Post by Morbius1 on 2013-10-07
Don't know if Ubuntu Studio changed how all this works but in 13.04 Ubuntu a drag and drop is a move not a copy. 

What happens when you do what we have to do in XFCE to do a move:

Select the file > Select the "Shift" key > then drag it to it's new location.

---

### Post by srikanthganta on 2013-10-07
You should have permission on the source folder and the destination.Try right click on the folder and are you able to do "cut" option on the folder?

---

### Post by Kanichiro on 2013-10-07
> **TheFu said:**
> I can understand that, but we need to know which program you are using, right?  Also, it would help to know if the CLI method is broken on your machine too.  See the connection?  Troubleshooting 101.

Thunar, Nautilus, or some other program?  Also, the kernel could matter.  What do the logs show?

I was able to move a file with a command line using the Terminal (mv 13223.jpg ~/Boats). 

Not being a command line person, I have no idea where it went, but it went somewhere. However, it's not in the Boats folder I have on my desktop!

---

### Post by Kanichiro on 2013-10-07
> **srikanthganta said:**
> You should have permission on the source folder and the destination.Try right click on the folder and are you able to do "cut" option on the folder?

Yes, I can select Cut. For some reason, I am not able to upload a screen shot of my right-click menu for you and it's tiny.

---

### Post by Kanichiro on 2013-10-07
> **Morbius1 said:**
> Don't know if Ubuntu Studio changed how all this works but in 13.04 Ubuntu a drag and drop is a move not a copy. 

What happens when you do what we have to do in XFCE to do a move:

Select the file > Select the "Shift" key > then drag it to it's new location.

Pressing the "Shift" key and dragging the file to a folder worked.  This is a start!

Why would I suddenly need to use the Shift key to move things?

Is there a way to "fix" my operating system so I can just drag a file/item to a folder without having to press Shift everytime?

---

### Post by Kanichiro on 2013-10-07
I want to thank everyone for their help with this.

Much appreciated!

---

### Post by michaelcranie on 2013-10-07
Thuner seems to be the file manager in studio 13.04. I dont know if you are able to remove it without removing xfce desktop . You could just cut and paste files if thats any better.I think  Studio12.10 LTS used nautilus so that migh be an option not sure what 13.10 is going to use.

---

