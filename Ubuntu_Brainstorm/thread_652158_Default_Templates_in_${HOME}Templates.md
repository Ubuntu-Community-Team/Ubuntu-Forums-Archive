---
title: "Default Templates in ${HOME}/Templates"
date: 2007-12-28
forum: Ubuntu Brainstorm
---

### Post by benanzo on 2007-12-28
I suggested for Gutsy that there be some default items in the right-click Create Document-> menu.  However, the only thing that happened was the Templates directory was created by default, but was still left empty.  The normal user has no idea that they need to create blank documents of frequently created filetypes and place them in this dir in order to see them in the Create Document-> menu.

Ubuntu comes with a wealth of great software that creates common filetypes.  Would it be unreasonable to add a couple defaults in this directory so it's easier for users to quickly and easily create the files they need right from the desktop?

I'm thinking specifically of adding:

TextFile.txt
OpenDocument.odt
MSWord.doc (uggh, but maybe)
Spreadsheet.ods
Presentation.odp

etc etc

This would be great for a first impression of usablity and completeness.

---

### Post by AlKhatib on 2007-12-28
I agree about the open document formats. But text files are already create using "empty file" template.

---

### Post by lexen on 2007-12-28
I was one of those users that had no idea about the change.  I am on board.  Frankly, this seems like such an easy thing to do, it makes me wonder why it wasn't done up until now.

     About the .doc, I think we should stick to open source media for now.

---

### Post by Merk42 on 2007-12-30
So THAT'S what the Templates folder is for.  I thought it had to do with the added Pictures/Movies/Music/Documents folders

---

### Post by Technophobia on 2007-12-30
I hear its because empty documents take up too much space on the cd.

---

### Post by steeleyuk on 2008-01-12
Empty documents take up too much space on the CD?!

Empty Calc file = 5.7KB
Empty Impress File = 8.4KB
Empty Writer File = 6.4KB

Add a few more kilobytes for any other file types and you'll still end up under 100KB.

(BTW, this isn't aimed at you Technophobia, its at whoever said it takes up too much space...)

---

### Post by Curtisc on 2008-01-12
Can't you just right click -> create blank file and then change the extension to be whatever you like?  I don't really see why the Templates thing is necessary - if I want an openoffice document, I can just type in "Document.odt".

However, I suppose if everyone wants the Templates folder to exist, it does make more sense to have something in it.  I too had no idea what it was doing there, and I immediately deleted it (along with "Music", "Movies", etc - I want to organize things my way without extra folders kicking around).

---

### Post by steeleyuk on 2008-01-12
Thats the problem, its empty by default so alot of people wonder what its for. Its one of those, either utilise it or lose it. If the choice is to keep it, having a default set of templates in there just adds to the polish of the distro.

---

### Post by benanzo on 2008-01-14
> Can't you just right click -> create blank file and then change the extension to be whatever you like? I don't really see why the Templates thing is necessary - if I want an openoffice document, I can just type in "Document.odt".

Doesn't quite work like that.  If you create and 'Empty File' and just rename to 'Document.odt' it's still just an empty text file.  In fact, opening from nautilus will cause this error:

> 
**Cannot open newFile.odt**
The filename "newFile.odt" indicates that this file is of type "ODT document". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.


Which will cause further confusion for the user.  You must actually save out an empty .odt file from within OpenOffice so it writes some basic xml info to the file in order for the mimetype to properly register.

---

### Post by Curtisc on 2008-01-16
> **benanzo said:**
> Doesn't quite work like that.  If you create and 'Empty File' and just rename to 'Document.odt' it's still just an empty text file.  In fact, opening from nautilus will cause this error:

Which will cause further confusion for the user.  You must actually save out an empty .odt file from within OpenOffice so it writes some basic xml info to the file in order for the mimetype to properly register.

Ah, thanks for that.  I should have checked before I said anything I guess - I've only ever done it with text documents (i.e. NewFile.tex, NewFile.py, etc) so I assumed it would work with others.

---

### Post by xlinuks on 2008-01-17
> **benanzo said:**
> I suggested for Gutsy that there be some default items in the right-click Create Document-> menu.  However, the only thing that happened was the Templates directory was created by default, but was still left empty.  The normal user has no idea that they need to create blank documents of frequently created filetypes and place them in this dir in order to see them in the Create Document-> menu.

Ubuntu comes with a wealth of great software that creates common filetypes.  Would it be unreasonable to add a couple defaults in this directory so it's easier for users to quickly and easily create the files they need right from the desktop?

I'm thinking specifically of adding:

TextFile.txt
OpenDocument.odt
MSWord.doc (uggh, but maybe)
Spreadsheet.ods
Presentation.odp

etc etc

This would be great for a first impression of usablity and completeness.

I totally agree with you.

---

### Post by benanzo on 2008-01-17
> **Curtisc said:**
> Ah, thanks for that.  I should have checked before I said anything I guess - I've only ever done it with text documents (i.e. NewFile.tex, NewFile.py, etc) so I assumed it would work with others.

Yeah it's not really apparent that this is how it works though, which adds more confusion for new users who want a quick and easy way to create new documents.  Even if they did know to add files to the Templates dir they still might just assume exactly what you did that an empty file with a .odt extension is sufficient to make it work, which isn't the case.  We really need to do this for them since there's no indication, not even a README file in the Templates dir that explains what they should do.

And also, this is likely a Gnome problem and not specific to Ubuntu, but why is the Templates dir in the ${HOME} directory?  Why isn't it in ~/.gnome2/Templates like the nautilus scripts etc.  I really don't like adding needless clutter to my home directory and the Templates dir only serves one purpose and no one should need to access it's contents very often.  This is a settings/config directory, not a useful user dir like Music or Documents.  Maybe I'll send a bug into Gnome.

---

### Post by steeleyuk on 2008-01-17
That directory probably should be moved like you say.

If you want to do it yourself now though, you can edit the user-dirs.dirs file in .config

---

### Post by Sam on 2008-01-18
+1 for hidding the templates folders by default (mine is set to ~/.templates). It can be easily opened with Nautilus, menu Go, Templates without having to show the hidden files.

---

### Post by phoenix81000 on 2008-01-18
stupid idea.. i freaking hate those things glad to red of that windows junk

---

### Post by steeleyuk on 2008-01-19
> **phoenix81000 said:**
> stupid idea.. i freaking hate those things glad to red of that windows junk

Want to elaborate a bit more?

---

### Post by MaX on 2008-01-19
I guess he's refering to the simple fact of Templates... if you want a new document, open the respective program and create it.

I think the template folder should be in ~/.config/templates but that's just me...

---

### Post by junglist313 on 2008-02-18
OK I was one of those people that deleted it and now I want it back. I have created a folder called Templates in the Home directory, I have a empty OpenOffice file named OpenOfficeDocument.doc and I still have nothing in my right click menu. Help?

---

### Post by steeleyuk on 2008-02-19
Go to your home folder. Press CTRL+H to show hidden files.

Then go to the .config folder and open the file user-dirs.dirs file. You'll then need to edit that file to map to the templates folder. For example, see mine...

> # This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"

---

### Post by junglist313 on 2008-02-21
Thank you steeleyuk! :)

---

