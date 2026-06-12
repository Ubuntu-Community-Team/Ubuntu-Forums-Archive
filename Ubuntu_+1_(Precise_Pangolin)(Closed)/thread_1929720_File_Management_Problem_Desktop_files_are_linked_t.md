---
title: "File Management Problem: Desktop files are linked to Home Folder"
date: 2012-02-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by naielstm on 2012-02-22
Hi!

I'm using Ubuntu 12.04 since two weeks. I had installed it first in German. But then I noticed that some notifications are still in English and I don't want a "bi-language" system.
Then I changed the language to English.
Now everything is in english and it works fine, except the fact that when I delete or create a file on my desktop it creates or deletes a new file in my home directory. 
My home directory is actually kinda linked to my home folder, meaning I don't have a desktop anymore because it is my home folder.

Can anyone please help me?

naielstm

---

### Post by forrestcupp on 2012-02-22
> **naielstm said:**
> Hi!

I'm using Ubuntu 12.04 since two weeks. I had installed it first in German. But then I noticed that some notifications are still in English and I don't want a "bi-language" system.
Then I changed the language to English.
Now everything is in english and it works fine, except the fact that when I delete or create a file on my desktop it creates or deletes a new file in my home directory. 
My home directory is actually kinda linked to my home folder, meaning I don't have a desktop anymore because it is my home folder.

Can anyone please help me?

naielstm
Well, you probably should ask this in the Ubuntu+1 development subforum.

But isn't that normal. Your desktop is actually a folder called Desktop that is a subfolder in /home. I think that's how it's supposed to work. Especially if you have it set for the file manager to handle the desktop.

If I'm misunderstanding, then maybe you could post a screen shot.

---

### Post by naielstm on 2012-02-22
The folders in english have the little icons with the picture frames or the notes for the music folder. The german ones haven't.
In the english folders weren't the files from the originally german folders, so I had to copy the files from the german to the english ones. Then I deleted the german files and folders.

Yes, you're right in my home directory is a file called "Arbeitsfläche". It's a german one, but hasn't got an own icon like the picture or the music folder. 
Normally the files in the "Desktop" or "Arbeitsfläche" folder should appear on the desktop, but they don't. On my desktop is exactly the content of my /home directory. 

When I open my desktop from the explorer it shows me the exact same content like in the /home folder. Creating a file on the desktop also creates a file in the /home folder. When deleting it's the same.

I tried to create a new folder and name it "Desktop" but it didn't work. 

Ubuntu asked me wether it should rename all the folders from german to english or leave them as they were.I said it should rename them and after that this happened. 


naielstm

---

### Post by nothingspecial on 2012-02-22
While in your home folder, press Ctrl-H to show the hidden files and directories. In your .config directory open the file user-dirs.dirs

Check that your Desktop is set as your Desktop. It should look like this

```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

If it doesn't, edit it so it does.

---

### Post by oldos2er on 2012-02-22
Thread moved to Ubuntu +1 (Precise Pangolin).

---

### Post by naielstm on 2012-02-23
> **nothingspecial said:**
> While in your home folder, press Ctrl-H to show the hidden files and directories. In your .config directory open the file user-dirs.dirs

Check that your Desktop is set as your Desktop. It should look like this

```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

If it doesn't, edit it so it does.

Yay it worked! :)

Thank you!

---

### Post by nothingspecial on 2012-02-23
You are welcome :)

---

