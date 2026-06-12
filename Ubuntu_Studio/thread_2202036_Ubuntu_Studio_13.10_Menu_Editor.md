---
title: "Ubuntu Studio 13.10 Menu Editor"
date: 2014-01-27
forum: Ubuntu Studio
---

### Post by royleith on 2014-01-27
I managed to install a new program in Wine, but it did not appear in the main menu. When I ran the Settings Manager/Main Menu editor, no changes could be made. Existing menu items could not be hidden or changed and new items and folders could not be added.

I could not find out the command for Main Menu and sudoed xfce4-settings-manager just in case it was a permissions thing and, of course, it did not show my user Main Menu editor.

New Linux programs are appearing in the menu, so I assume the menu files are created directly. I seem to remember .desktop files so I will investigate whether I can do the job, manually.

Has anyone else managed to edit anything in the 13.10 Main Menu editor?

---

### Post by ajgreeny on 2014-01-27
Ubuntu-studio uses XFCE as its desktop so I think the menu-editor is **alacarte**, unless things have changed since 12.04.

Try it in the Alt+F2 dialogue and hopefully it will open your menu-editor program, however, I don't know much about wine having hardly used it, so I'm not sure about menu items appearing for wine installed apps.

---

### Post by cub on 2014-01-27
> **ajgreeny said:**
> Ubuntu-studio uses XFCE as its desktop so I think the menu-editor is **alacarte**, unless things have changed since 12.04.

Try it in the Alt+F2 dialogue and hopefully it will open your menu-editor program, however, I don't know much about wine having hardly used it, so I'm not sure about menu items appearing for wine installed apps.
Alacarte is what opens with Settings Manager/Main Menu editor.

What happens when installed in Wine, I don't know though.

---

### Post by royleith on 2014-01-28
Thanks ajgreeny and cub,

The Alt-F2 trick is one I did not know about.

Anyway, alacarte is, as you say, the program for Main Menu editor. I ran it and tried to add a menu item without any luck. The program just will not permit any changes. I tried it with sudo in case there was a permissions problem and there is no change. For the moment, alacarte will not make edits.

BTW, adding a wine program is no problem. Any installed wine program can be run from Terminal, menu or from Thunar by using the path to /.wine/drive_c/Program Files (x86)/Program Folder/Program.exe. (BTW, that change to defaulting to Program Files (X86) for 32 bit programs (it's a Windows 7 trick) has caused me no end of problems.)

The only remaining difficulty is that 13.10 defaults to the Archive Manager for .exe programs instead of Wine Program Loader. Just use Mime Type Editor in Settings to assign 'application/x-ms-dos-executable' to Wine Windows Program Loader.

---

### Post by Sorinux on 2014-03-10
Quick info: running Ubuntustudio 14.04 beta and alacarte still not working. Can edit the entries that already exist, but can not add new ones.
Anybody has some solutions for this or just take out alacarte?

---

### Post by brianmc on 2014-03-13
I'm sitting here running Ubuntu Studio 13.10, and assumed menu editing was working correctly - it isn't.

Another way to get at the menu (to add to your collection) is: right-click on the panel containing your menu, select *Panel* -> *Panel Preferences...*, select the *Items* tab and find the '*Applications Menu*' item. Clicking on the Edit button takes you into [FONT=fixedsys]*alacarte*[/FONT], but all I've managed to do is disable items, delete items, or edit existing items.

What I do for my most-used applications is add a launcher to the panel, and list several applications under it.

Rather not dig into the guts of how Ubuntu Studio maintains the system-wide menu, but when I deleted all the 'Unused menu' items, then tried to delete the 'wine-wine' menu, [FONT=fixedsys]*alacarte*[/FONT] crashed.

This is just a minor annoyance, but hopefully it'll be addressed in 14.04.

---

