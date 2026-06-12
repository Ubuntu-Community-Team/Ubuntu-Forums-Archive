---
title: "Can not view notes via web and sync notes"
date: 2010-03-14
forum: Ubuntu One (CLOSED)
---

### Post by josephpei on 2010-03-14
I'm getting a "Server Error Something has gone wrong (500)" when i try to access the notes page for several days now. When will it be OK?

Bug report:
[https://bugs.launchpad.net/ubuntuone-servers/+bug/538354](https://bugs.launchpad.net/ubuntuone-servers/+bug/538354)

Just now:

Something has gone wrong (500)
This is a robot

We've recorded this problem and it will get investigated with the logs. If this problem is urgent, please file a bug report and include this number: OOPS-ID-1534appserver79128

---

### Post by joshuahoover on 2010-03-15
> **josephpei said:**
> I'm getting a "Server Error Something has gone wrong (500)" when i try to access the notes page for several days now. When will it be OK?

Bug report:
[https://bugs.launchpad.net/ubuntuone-servers/+bug/538354](https://bugs.launchpad.net/ubuntuone-servers/+bug/538354)

Just now:

Something has gone wrong (500)
This is a robot

We've recorded this problem and it will get investigated with the logs. If this problem is urgent, please file a bug report and include this number: OOPS-ID-1534appserver79128

Apologies for the inconvenience this may have caused you. You should be able to view your notes now. I tried this with a couple different accounts and didn't have any issues.

Thank you,

Joshua

---

### Post by josephpei on 2010-03-16
I still can't view my note via web.

2010 03 17 12:23 CST

Something has gone wrong (500)
This is a robot

We've recorded this problem and it will get investigated with the logs. If this problem is urgent, please file a bug report and include this number: OOPS-ID-1537appserver18628

---

### Post by mjuhasz on 2010-03-17
Same here: OOPS-ID-1537appserver77379
I can not view my notes on web and Tomboy sync is also failing.

---

### Post by joshuahoover on 2010-03-17
> **mjuhasz said:**
> Same here: OOPS-ID-1537appserver77379
I can not view my notes on web and Tomboy sync is also failing.

We were having system wide problems with our CouchDB servers earlier today. This has since been fixed. If you are still experiencing problems, please do the following:

[LIST=1]
[*]File a new bug at: [https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug](https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug)
[*]Quit Tomboy 
[*]Applications->Accessories->Terminal, and run: 

[LIST]
[*]tomboy --debug > ~/tomboy_debug.log 
[/LIST]
[*]Try to synchronize  and then attach ~/tomboy_debug.log to a bug report
[/LIST]
I realize the bug may not be directly related to synchronizing notes in Tomboy, but we'll likely get more detailed error information there that will give us further info as to what may be causing the issue.

Thank you,

Joshua

---

### Post by josephpei on 2010-03-17
Now I can sync note between tomboy and web server, but I still can't view notes via web.

View Web:

Something has gone wrong (500)
This is a robot

We've recorded this problem and it will get investigated with the logs. If this problem is urgent, please file a bug report and include this number: OOPS-ID-1538appserver15167


Tomboy debug:
** Running Mono with --debug    **
[DEBUG]: NoteManager created with note path "/home/rogerpei/.local/share/tomboy".
[DEBUG]: EnableDisable Called: enabling... True
[DEBUG]: Binding key '<Alt>F12' for '/apps/tomboy/global_keybindings/show_note_menu'
[DEBUG]: Binding key '<Alt>F11' for '/apps/tomboy/global_keybindings/open_start_here'
[INFO]: Initializing Mono.Addins
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.Tomboy
[DEBUG]: 	       Name: Tomboy.Tomboy,0.10
[DEBUG]: 	Description: 
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/Tomboy.exe
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.WebSyncServiceAddin
[DEBUG]: 	       Name: Web Sync Service Add-in
[DEBUG]: 	Description: Synchronize Tomboy Notes with Tomboy Online and other compatible web services
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/WebSyncServiceAddin.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.WebDavSyncServiceAddin
[DEBUG]: 	       Name: WebDav Sync Service Add-in
[DEBUG]: 	Description: Synchronize Tomboy Notes to a WebDav URL
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/WebDavSyncService.dll
[DEBUG]: Unable to locate 'gnomesu' in your PATH
[DEBUG]: Using '/usr/bin/gksu' as GUI 'su' tool
[DEBUG]: Successfully found all system tools
[DEBUG]: Unable to locate 'wdfs' in your PATH
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.FileSystemSyncServiceAddin
[DEBUG]: 	       Name: Local Directory Sync Service Add-in
[DEBUG]: 	Description: Synchronize Tomboy Notes to a local file system path
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/FileSystemSyncService.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.ExportToHtmlAddin
[DEBUG]: 	       Name: Export to HTML
[DEBUG]: 	Description: Exports individual notes to HTML.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/ExportToHtml.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.PrintNotesAddin
[DEBUG]: 	       Name: Printing Support
[DEBUG]: 	Description: Allows you to print a note.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/PrintNotes.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.BacklinksAddin
[DEBUG]: 	       Name: Backlinks
[DEBUG]: 	Description: See which notes link to the one you're currently viewing.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/Backlinks.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.EvolutionAddin
[DEBUG]: 	       Name: Evolution Mail Integration
[DEBUG]: 	Description: Allows you to drag an email from Evolution into a Tomboy note.  The message subject is added as a link in the note with an envelope icon next to it.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/Evolution.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.FixedWidthAddin
[DEBUG]: 	       Name: Fixed Width
[DEBUG]: 	Description: Adds fixed-width font style.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/FixedWidth.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.StickyNoteImportAddin
[DEBUG]: 	       Name: Sticky Notes Importer
[DEBUG]: 	Description: Import your notes from the Sticky Notes applet.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/StickyNoteImport.dll
[DEBUG]: StickyNoteImporter: Sticky Notes XML file does not exist or is invalid!
[DEBUG]: Unable to locate 'wdfs' in your PATH
[DEBUG]: Tomboy remote control active.
[DEBUG]: SyncThread using SyncServiceAddin: &#38339;&#22446;&#31512;&#32515;&#25120;&#29679;
[DEBUG]: Building web request for URL: [https://one.ubuntu.com/notes//api/1.0/](https://one.ubuntu.com/notes//api/1.0/)
[DEBUG]: Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/user/](https://one.ubuntu.com/notes/api/1.0/user/)
[DEBUG]: 8
[DEBUG]: Sync: GetNoteUpdatesSince rev 9
[DEBUG]: Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/op/?include_notes=true&since=9](https://one.ubuntu.com/notes/api/1.0/op/?include_notes=true&since=9)
[DEBUG]: Sync: 0 updates since rev 9
[DEBUG]: Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/op/](https://one.ubuntu.com/notes/api/1.0/op/)
[DEBUG]: Sync: Uploading 0 note updates
[DEBUG]: Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/op/](https://one.ubuntu.com/notes/api/1.0/op/)
[DEBUG]: Sync: New revision: 9

---

### Post by mjuhasz on 2010-03-18
> **joshuahoover said:**
> We were having system wide problems with our CouchDB servers earlier today. This has since been fixed. If you are still experiencing problems, please do the following:

[LIST=1]
[*]File a new bug at: [https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug](https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug)
[*]Quit Tomboy 
[*]Applications->Accessories->Terminal, and run: 

[LIST]
[*]tomboy --debug > ~/tomboy_debug.log 
[/LIST]
[*]Try to synchronize  and then attach ~/tomboy_debug.log to a bug report
[/LIST]
I realize the bug may not be directly related to synchronizing notes in Tomboy, but we'll likely get more detailed error information there that will give us further info as to what may be causing the issue.

Thank you,

Joshua

I have filed a bug as requested: [https://bugs.launchpad.net/ubuntuone-servers/+bug/540585](https://bugs.launchpad.net/ubuntuone-servers/+bug/540585)
I can view my notes on the web UI now but the Tomboy sync is still failing.

---

### Post by r_mano on 2011-07-11
Hmmm... I still have the two problems. Not able to sync tomboy notes, and not able to see them in the web browser... same "500" error.

---

### Post by duanedesign on 2011-07-12
To get more information about what may be causing this issue could you please try the following steps.

1. Quit Tomboy
2. Alt + f2, and run:

tomboy --debug > ~/tomboy_debug.log

3. Try to reproduce the bug (sync your notes) and then post the ~/tomboy_debug.log

If you do post the log please use the [ CODE ] tags. It is the Hash symbol in the Message Post Menu.

**Note:** that attaching the Tomboy debug log will show information about what you are attempting to sync with Ubuntu One. If you do not want this to be public you can send me the log as a PM.

---

