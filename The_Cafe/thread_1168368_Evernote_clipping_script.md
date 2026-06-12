---
title: "Evernote clipping script"
date: 2009-05-24
forum: The Cafe
---

### Post by ajy0852 on 2009-05-24
Hey,

I've been using the Evernote client in WINE for notetaking lately. This is a small script that uses Evernote's automatic file import feature to clip selected text into the client.

Basically, I select text and hit a key combination and the text appears as a new note in my default Evernote notebook.

1. Install xsel, a little utility that allows you to interact with the X selection.
```
sudo apt-get install xsel
```

2. Set up folders:
```
mkdir ~/Evernote
mkdir ~/.wine/drive_c/Evernote
ln -s ~/Evernote ~/.wine/drive_c/Evernote
```
This way, you can drop a file in ~/Evernote (more convenient for you) and 
the Evernote client will pick it up from ~/.wine/drive_c/Evernote (accessible to Evernote).

3. In the Evernote client, choose File -> Import -> File Import Wizard and go through the wizard.
- Source Folder: browse to the second folder you created above, it'll be in C:\Evernote
- On the second screen, make sure to choose "Watch folder for changes and import files automatically"
- I have it delete the file when it's done importing, this doesn't really matter.

4. Open a text editor and copy-paste:
```
#!/bin/bash
#evernote "clipper" - just takes the x selection and writes it to a text file that Evernote will import
#create a random filename so you can clip to your heart's content without losing anything
random_string=$(< /dev/urandom tr -dc _A-Z-a-z-0-9 | head -c8)
#this line writes the x selection to a file
xsel > ~/$random_string.txt
#if we write the file directly to the evernote folder,
#evernote will delete the file before it, well, exists
#and you'll get an empty note. So instead...
sleep 1
mv ~/$random_string.txt ~/Evernote/$random_string.txt
```
Go ahead and strip the comments if you want, it just tells you what's happening in the script.

Save the script (mine is "en-clipper") and make it executable. You can assign a keybinding to it. It doesn't require input, xsel takes care of all that. Just select text, execute the script, and notes will appear in Evernote.

Feel free to correct anything I did, I just blindly pieced together a bunch of stuff.

Have a good day!

---

### Post by meranaamjoker on 2009-09-22
Wow man! U r an unbelievable guy. This worked for me and thanks a lot again and again.

I desperately needed something like this.

---

### Post by RvdL on 2010-02-18
Works very nice! Unfortunately, ubuntu still lacks perfect Evernote support, but wine at least offers basic functionality. I missed the clipping function until now, but not any more :D!

---

### Post by jperode on 2010-07-23
ajy0852 may hence be called SuperClipperMan

---

### Post by jlawsonb on 2011-11-17
I found NixNote (formerly NeverNote) to be a decent approach as a native app.

---

### Post by Docaltmed on 2011-11-17
NixNote rocks! Between that and the Evernote extension for Firefox, I don't need anything else.

---

