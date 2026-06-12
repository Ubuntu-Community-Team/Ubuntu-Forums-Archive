---
title: "Associate files with applications"
date: 2005-07-22
forum: Tutorials
---

### Post by scorpio2002 on 2005-07-22
Hi there! I'm writing this HOWTO because when I first approached Linux I had no idea how to associate my preferred apps with file formats. I was told that you were supposed to know all the gibberish about MIME types but I found a easier way to do that.

Let's immagine you want to change the default video player for .avi files. Well, that's  what you have to do (yes, just to easy steps :P ):

1) Right click on any avi file and go to Properties;
2) Then go to the "Open with" tab and just select the application you want to use for opening that type of file (i.e. avi). 

[IMG]http://scorpio2002.altervista.org/properties.gif[/IMG]

That's all. From now on, every .avi file will be opened using the application you chose.

#NOTE:
I don't know if this matter has already been dealt with, if that's the case I'm sorry for repeating it.

Bye,
Donato
Italy

---

### Post by aggiechemist on 2005-07-22
Good howto, it took me a while to find this myself. This would have helped. 

I would also add that this is the place to add file associations for programs you don't always use. For instance, I installed mplayer to my system for movies. Normally when you right click a file, it lists applications to choose from. But mplayer didn't get added to that list, so I always had to type it in. So going through this menu can fix that and you can add programs by hand that you might want to use to open files.

---

### Post by scorpio2002 on 2005-07-22
> Normally when you right click a file, it lists applications to choose from. But mplayer didn't get added to that list, so I always had to type it in. So going through this menu can fix that and you can add programs by hand that you might want to use to open files.

Oh yes, this is good ^_^
And, I like your signature too  ;-)

---

### Post by fresco on 2005-07-27
Yeah, that works! Earlier I have found that there's /usr/share/applications/defaults.list You can edit it as you like.

---

### Post by Cybe R. Wizard on 2005-11-18
scorpio2002, I assume that this tip uses Nautilus?  You should really include that bit of information for not everybody does use it.  The editing of /usr/share/applications/defaults.list, as fresco notes, is more universal.
But yours is /way/ easier.

---

### Post by SepheeBear on 2005-12-04
A better IMHO way is editing files in your home directory so that changes stay consistent if you switch systems or reinstall but keep your home dir intact.

to set the default "open with" app 
     **$HOME/.local/share/applications/defaults.list**

or to add an app to the list of "open with" apps for a certain mime-type
     **$HOME/.local/share/applications/mimeinfo.cache**

Both files have the same syntax:
mime/type=app.desktop

ex:     **text/xml=gvim.desktop**

---

### Post by winsetter on 2012-06-07
on ubuntu 12.04, the file to edit is /home/user_name/.local/share/applications/mimeapps.list

---

