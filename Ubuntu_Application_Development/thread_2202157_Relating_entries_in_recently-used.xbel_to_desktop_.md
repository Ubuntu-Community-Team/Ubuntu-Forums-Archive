---
title: "Relating entries in recently-used.xbel to desktop files"
date: 2014-01-27
forum: Ubuntu Application Development
---

### Post by mike134 on 2014-01-27
I am trying to write a script for Lubuntu 13.10 to show recent items on the menu with their application icon, but the name field in ~/.local/share/recently-used.xbel does not match the Name field in the desktop files in /usr/share/applications.
For example, in recently-used.xbel I have

          <bookmark:application name="File Roller" exec="&apos;file-roller&apos;" modified="2014-01-27T12:13:17Z" count="1"/>
          <bookmark:application name="Gnumeric Spreadsheet" exec="&apos;gnumeric %u&apos;" modified="2014-01-27T15:14:16Z" count="2"/>
          <bookmark:application name="abiword" exec="&apos;abiword %u&apos;" modified="2014-01-27T19:08:52Z" count="1"/>
          <bookmark:application name="Document Viewer" exec="&apos;evince %u&apos;" modified="2014-01-27T19:10:19Z" count="1"/>


 
But in /usr/share/applications I have:[INDENT]abiword.desktop:Exec=abiword %U[/INDENT]
[INDENT]abiword.desktop:Name=AbiWord[/INDENT]
[INDENT]gnumeric.desktop:Name=Gnumeric[/INDENT]
[INDENT]gnumeric.desktop:Exec=gnumeric %U[/INDENT]
[INDENT]evince.desktop:Name=Document Viewer[/INDENT]
[INDENT]evince.desktop:Exec=evince %U[/INDENT]
[INDENT]file-roller.desktop:Name=Archive Manager[/INDENT]
[INDENT]file-roller.desktop:Exec=file-roller %U
[/INDENT]

So you can see here that the name fields in recently-used.xbel do not match the filenames or Name fields in the desktop files, so I can only think to link using the Exec field (abiword, gnumeric, evince, file-roller) , but this may not always work, so is there is an easier to way - I would have thought I should be able to use name field.

Thanks

Mike

---

