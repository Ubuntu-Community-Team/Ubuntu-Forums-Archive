---
title: "Tomboy crashes multiple times everyday and I have lost one note so far...."
date: 2011-12-07
forum: Ubuntu One (CLOSED)
---

### Post by krackersk on 2011-12-07
Hi All,

So I've been using ubuntu one for all my files sync (about 40Gb) and it's been working pretty good for a while now and I also use it to sync my notes using tomboy.

Tomboy was working well until I upgraded to 11.10 and then it started crashing multiple times everyday, so far haven't lost any data until just then when it crashed an one of my notes disappear (unfortunately a rather long and important one)

Yesterday I ran tomboy --debug from the commandline and I have attached the output log.

Any ideas on what is going on here?

---

### Post by Garland Fox on 2011-12-07
do not see the log attachment

---

### Post by krackersk on 2011-12-07
So I found the lost note, it was in ~/.local/share/tomboy and but it was appended with a ~ so tomboy wasn't seeing it

---

### Post by krackersk on 2011-12-07
It's not uploading so here is an expert from it:

** Running Mono with --debug    **
[DEBUG 20:30:56.191] NoteManager created with note path "/home/angus/.local/share/tomboy".
[INFO 20:30:56.771] Initializing Mono.Addins
[DEBUG 20:30:57.022] AddinManager.OnAddinLoaded: Tomboy.Tomboy
[DEBUG 20:30:57.024]            Name: Tomboy.Tomboy,0.10
[DEBUG 20:30:57.024]     Description: 
[DEBUG 20:30:57.024]       Namespace: Tomboy
[DEBUG 20:30:57.024]         Enabled: True
[DEBUG 20:30:57.024]            File: /usr/lib/tomboy/Tomboy.exe
[DEBUG 20:30:57.918] AddinManager.OnAddinLoaded: Tomboy.ExportToHtmlAddin
[DEBUG 20:30:57.918]            Name: Export to HTML
[DEBUG 20:30:57.918]     Description: Exports individual notes to HTML.
[DEBUG 20:30:57.918]       Namespace: Tomboy
[DEBUG 20:30:57.918]         Enabled: True
[DEBUG 20:30:57.918]            File: /usr/lib/tomboy/addins/ExportToHtml.dll
[DEBUG 20:30:57.921] AddinManager.OnAddinLoaded: Tomboy.WebDavSyncServiceAddin
[DEBUG 20:30:57.921]            Name: WebDav Sync Service Add-in
[DEBUG 20:30:57.921]     Description: Synchronize Tomboy Notes to a WebDav URL
[DEBUG 20:30:57.921]       Namespace: Tomboy
[DEBUG 20:30:57.921]         Enabled: True
[DEBUG 20:30:57.921]            File: /usr/lib/tomboy/addins/WebDavSyncService.dll
[DEBUG 20:30:57.924] Unable to locate 'gnomesu' in your PATH
[DEBUG 20:30:57.924] Using '/usr/bin/gksu' as GUI 'su' tool
[DEBUG 20:30:57.924] Successfully found all system tools
[DEBUG 20:30:57.924] Unable to locate 'wdfs' in your PATH
[DEBUG 20:30:57.924] AddinManager.OnAddinLoaded: Tomboy.WebSyncServiceAddin
[DEBUG 20:30:57.924]            Name: Web Sync Service Add-in
[DEBUG 20:30:57.924]     Description: Synchronize Tomboy Notes with Tomboy Online and other compatible web services
[DEBUG 20:30:57.924]       Namespace: Tomboy
[DEBUG 20:30:57.924]         Enabled: True
[DEBUG 20:30:57.924]            File: /usr/lib/tomboy/addins/WebSyncServiceAddin.dll
[DEBUG 20:30:57.925] AddinManager.OnAddinLoaded: Tomboy.FileSystemSyncServiceAddin
[DEBUG 20:30:57.926]            Name: Local Directory Sync Service Add-in
[DEBUG 20:30:57.926]     Description: Synchronize Tomboy Notes to a local file system path
[DEBUG 20:30:57.926]       Namespace: Tomboy
[DEBUG 20:30:57.926]         Enabled: True
[DEBUG 20:30:57.926]            File: /usr/lib/tomboy/addins/FileSystemSyncService.dll
[DEBUG 20:30:57.929] Loading notes
[DEBUG 20:30:58.696] AddinManager.OnAddinLoaded: Tomboy.PrintNotesAddin
[DEBUG 20:30:58.696]            Name: Printing Support
[DEBUG 20:30:58.696]     Description: Allows you to print a note.
[DEBUG 20:30:58.696]       Namespace: Tomboy
[DEBUG 20:30:58.696]         Enabled: True
[DEBUG 20:30:58.696]            File: /usr/lib/tomboy/addins/PrintNotes.dll
[DEBUG 20:30:58.697] AddinManager.OnAddinLoaded: Tomboy.BacklinksAddin
[DEBUG 20:30:58.697]            Name: Backlinks
[DEBUG 20:30:58.697]     Description: See which notes link to the one you're currently viewing.
[DEBUG 20:30:58.697]       Namespace: Tomboy
[DEBUG 20:30:58.697]         Enabled: True
[DEBUG 20:30:58.697]            File: /usr/lib/tomboy/addins/Backlinks.dll
[DEBUG 20:30:58.698] AddinManager.OnAddinLoaded: Tomboy.StickyNoteImportAddin
[DEBUG 20:30:58.698]            Name: Sticky Notes Importer
[DEBUG 20:30:58.698]     Description: Import your notes from the Sticky Notes applet.
[DEBUG 20:30:58.698]       Namespace: Tomboy
[DEBUG 20:30:58.698]         Enabled: True
[DEBUG 20:30:58.698]            File: /usr/lib/tomboy/addins/StickyNoteImport.dll
[DEBUG 20:30:58.699] StickyNoteImporter: Sticky Notes XML file does not exist or is invalid!
[DEBUG 20:30:58.699] AddinManager.OnAddinLoaded: Tomboy.EvolutionAddin
[DEBUG 20:30:58.699]            Name: Evolution Mail Integration
[DEBUG 20:30:58.699]     Description: Allows you to drag an email from Evolution into a Tomboy note.  The message subject is added as a link in the note with an envelope icon next to it.
[DEBUG 20:30:58.699]       Namespace: Tomboy
[DEBUG 20:30:58.699]         Enabled: True
[DEBUG 20:30:58.699]            File: /usr/lib/tomboy/addins/Evolution.dll
[DEBUG 20:30:58.755] AddinManager.OnAddinLoaded: Tomboy.FixedWidthAddin
[DEBUG 20:30:58.755]            Name: Fixed Width
[DEBUG 20:30:58.756]     Description: Adds fixed-width font style.
[DEBUG 20:30:58.756]       Namespace: Tomboy
[DEBUG 20:30:58.756]         Enabled: True
[DEBUG 20:30:58.756]            File: /usr/lib/tomboy/addins/FixedWidth.dll
[DEBUG 20:30:58.868] Unable to locate 'wdfs' in your PATH
[DEBUG 20:30:58.932] Autosync pref changed...restarting sync timer
[DEBUG 20:30:58.966] Tomboy remote control active.
[DEBUG 20:32:31.056] Loading notebooks
[DEBUG 20:32:39.845] Creating Buffer for 'SIRF Alarm system and Procedure'...
[DEBUG 20:32:40.001] SIRF Alarm system and Procedure tags:
[DEBUG 20:32:46.399] Saving 'SIRF Alarm system and Procedure'...
[DEBUG 20:32:54.922] Saving 'SIRF Alarm system and Procedure'...
[DEBUG 20:33:09.030] Creating Buffer for 'SIRF - Pilot Line'...
[DEBUG 20:33:09.072] SIRF - Pilot Line tags:
[DEBUG 20:33:13.134] Saving 'SIRF - Pilot Line'...
[DEBUG 20:33:23.034] Saving 'SIRF - Pilot Line'...
[DEBUG 20:33:31.173] Saving 'SIRF - Pilot Line'...
[DEBUG 20:33:46.960] Saving 'SIRF - Pilot Line'...
[DEBUG 20:34:52.556] Saving 'SIRF - Pilot Line'...
[DEBUG 20:35:02.382] Saving 'SIRF - Pilot Line'...
[DEBUG 20:35:13.348] Saving 'SIRF - Pilot Line'...
[DEBUG 20:35:52.474] Saving 'SIRF - Pilot Line'...
[DEBUG 20:36:29.083] Saving 'SIRF - Pilot Line'...
[DEBUG 20:37:07.915] Saving 'SIRF - Pilot Line'...
[DEBUG 20:37:38.296] Saving 'SIRF - Pilot Line'...
[DEBUG 20:38:05.386] Saving 'SIRF - Pilot Line'...
[DEBUG 20:38:36.709] Saving 'SIRF - Pilot Line'...
[DEBUG 20:39:17.265] Saving 'SIRF - Pilot Line'...
[DEBUG 20:40:01.607] Note edited...killing autosync timer until next save or delete event
[DEBUG 20:40:05.616] Saving 'SIRF - Pilot Line'...
[DEBUG 20:40:05.709] Note saved or deleted...restarting sync timer
[DEBUG 20:41:06.253] BackgroundSyncChecker: Checking server for updates
[DEBUG 20:41:06.257] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/](https://one.ubuntu.com/notes/api/1.0/)
[DEBUG 20:41:14.708] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/user/](https://one.ubuntu.com/notes/api/1.0/user/)
[DEBUG 20:41:16.806] BackgroundSyncChecker: Detected that sync would be a good idea now
[DEBUG 20:41:16.816] SyncThread using SyncServiceAddin: Tomboy Web
[DEBUG 20:41:16.817] SilentUI: SyncStateChanged: Connecting
[DEBUG 20:41:16.824] SilentUI: SyncStateChanged: AcquiringLock
[DEBUG 20:41:16.826] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/](https://one.ubuntu.com/notes/api/1.0/)
[DEBUG 20:41:17.381] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/user/](https://one.ubuntu.com/notes/api/1.0/user/)
[DEBUG 20:41:18.151] 8
[DEBUG 20:41:18.152] SilentUI: SyncStateChanged: PrepareDownload
[DEBUG 20:41:18.153] Sync: GetNoteUpdatesSince rev 502
[DEBUG 20:41:18.156] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/op/?include_notes=true&since=502](https://one.ubuntu.com/notes/api/1.0/op/?include_notes=true&since=502)
[DEBUG 20:41:18.922] Sync: 0 updates since rev 502
[DEBUG 20:41:18.926] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/op/](https://one.ubuntu.com/notes/api/1.0/op/)
[DEBUG 20:41:22.340] SilentUI: SyncStateChanged: PrepareUpload
[DEBUG 20:41:22.341] Saving 'SIRF - Pilot Line'...
[DEBUG 20:41:22.358] Saving 'SIRF Alarm system and Procedure'...
[DEBUG 20:41:22.341] Saving 'SIRF - Pilot Line'...
[DEBUG 20:41:22.375] SilentUI: NoteSynchronized, Title: SIRF - Pilot Line, Type: UploadModified
[DEBUG 20:41:22.375] Saving 'SIRF Alarm system and Procedure'...
[ERROR 20:41:22.382] Synchronization failed with the following exception: Collection was modified; enumeration operation may not execute.
  at System.Collections.Generic.List`1+Enumerator[Tomboy.Note].VerifyState () [0x00000] in <filename unknown>:0 
  at System.Collections.Generic.List`1+Enumerator[Tomboy.Note].MoveNext () [0x00000] in <filename unknown>:0 
  at Tomboy.NoteRecentChanges.UpdateResults () [0x00000] in <filename unknown>:0 
  at Tomboy.NoteRecentChanges.OnNoteSaved (Tomboy.Note note) [0x00000] in <filename unknown>:0 
  at (wrapper delegate-invoke) <Module>:invoke_void__this___Note (Tomboy.Note)
  at Tomboy.NoteManager.OnNoteSave (Tomboy.Note note) [0x00000] in <filename unknown>:0 
  at Tomboy.Note.Save () [0x00000] in <filename unknown>:0 
  at Tomboy.Sync.SyncManager.SynchronizationThread () [0x00000] in <filename unknown>:0 
[DEBUG 20:41:22.382] SilentUI: SyncStateChanged: Idle
[DEBUG 20:41:22.386] SilentUI: SyncStateChanged: Failed
[DEBUG 20:41:22.386] SilentUI: SyncStateChanged: Idle
[DEBUG 20:42:08.739] Saving 'SIRF - Pilot Line'...
[DEBUG 20:44:22.995] Saving 'SIRF - Pilot Line'...
[DEBUG 20:44:30.458] Saving 'SIRF - Pilot Line'...
[DEBUG 20:44:39.358] Saving 'SIRF - Pilot Line'...
[DEBUG 20:44:53.551] Saving 'SIRF - Pilot Line'...
[DEBUG 20:45:05.506] Saving 'SIRF - Pilot Line'...
[DEBUG 20:45:15.777] Saving 'SIRF - Pilot Line'...
[DEBUG 20:45:25.858] Saving 'SIRF - Pilot Line'...
[DEBUG 20:45:46.029] Saving 'SIRF - Pilot Line'...
[DEBUG 20:46:20.537] Saving 'SIRF - Pilot Line'...
[DEBUG 20:46:41.177] Saving 'SIRF - Pilot Line'...
[DEBUG 20:47:09.513] Saving 'SIRF - Pilot Line'...
[DEBUG 20:47:25.979] Saving 'SIRF - Pilot Line'...
[DEBUG 20:48:48.792] Saving 'SIRF - Pilot Line'...
[DEBUG 20:51:05.714] BackgroundSyncChecker: Checking server for updates
[DEBUG 20:51:05.714] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/](https://one.ubuntu.com/notes/api/1.0/)
[DEBUG 20:51:09.742] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/user/](https://one.ubuntu.com/notes/api/1.0/user/)
[DEBUG 20:51:12.196] BackgroundSyncChecker: Detected that sync would be a good idea now
[DEBUG 20:51:12.197] SyncThread using SyncServiceAddin: Tomboy Web
[DEBUG 20:51:12.198] SilentUI: SyncStateChanged: Connecting
[DEBUG 20:51:12.202] SilentUI: SyncStateChanged: AcquiringLock
[DEBUG 20:51:12.203] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/](https://one.ubuntu.com/notes/api/1.0/)
[DEBUG 20:51:12.796] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/user/](https://one.ubuntu.com/notes/api/1.0/user/)
[DEBUG 20:51:13.579] 8
[DEBUG 20:51:13.579] SilentUI: SyncStateChanged: PrepareDownload
[DEBUG 20:51:13.580] Sync: GetNoteUpdatesSince rev 502
[DEBUG 20:51:13.580] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/op/?include_notes=true&since=502](https://one.ubuntu.com/notes/api/1.0/op/?include_notes=true&since=502)
[DEBUG 20:51:14.283] Sync: 0 updates since rev 502
[DEBUG 20:51:14.284] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/op/](https://one.ubuntu.com/notes/api/1.0/op/)
[DEBUG 20:51:16.898] SilentUI: SyncStateChanged: PrepareUpload
[DEBUG 20:51:16.898] Saving 'SIRF - Pilot Line'...
[DEBUG 20:51:16.902] Saving 'SIRF - Pilot Line'...
[DEBUG 20:51:16.913] SilentUI: NoteSynchronized, Title: SIRF - Pilot Line, Type: UploadModified
[ERROR 20:51:16.913] Error while saving: System.InvalidOperationException: Collection was modified; enumeration operation may not execute.
  at System.Collections.Generic.List`1+Enumerator[Tomboy.Note].VerifyState () [0x00000] in <filename unknown>:0 
  at System.Collections.Generic.List`1+Enumerator[Tomboy.Note].MoveNext () [0x00000] in <filename unknown>:0 
  at Tomboy.NoteRecentChanges.UpdateResults () [0x00000] in <filename unknown>:0 
  at Tomboy.NoteRecentChanges.OnNoteSaved (Tomboy.Note note) [0x00000] in <filename unknown>:0 
  at (wrapper delegate-invoke) <Module>:invoke_void__this___Note (Tomboy.Note)
  at Tomboy.NoteManager.OnNoteSave (Tomboy.Note note) [0x00000] in <filename unknown>:0 
  at Tomboy.Note.Save () [0x00000] in <filename unknown>:0 
  at Tomboy.Note.SaveTimeout (System.Object sender, System.EventArgs args) [0x00000] in <filename unknown>:0 
[DEBUG 20:51:16.913] Saving 'SIRF Alarm system and Procedure'...
[DEBUG 20:51:16.914] Saving 'SIRF Alarm system and Procedure'...
[ERROR 20:51:16.915] Exception while saving note: System.IO.IOException: Sharing violation on path /home/angus/.local/share/tomboy/894bd4fb-f3b4-433c-acc2-1997205f513e.note.tmp
  at System.IO.FileStream..ctor (System.String path, FileMode mode, FileAccess access, FileShare share, Int32 bufferSize, Boolean anonymous, FileOptions options) [0x00000] in <filename unknown>:0 
  at System.IO.FileStream..ctor (System.String path, FileMode mode, FileAccess access, FileShare share) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.IO.FileStream:.ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare)
  at System.IO.StreamWriter..ctor (System.String path, Boolean append, System.Text.Encoding encoding, Int32 bufferSize) [0x00000] in <filename unknown>:0 
  at System.IO.StreamWriter..ctor (System.String path, Boolean append, System.Text.Encoding encoding) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.IO.StreamWriter:.ctor (string,bool,System.Text.Encoding)
  at System.Xml.XmlWriter.Create (System.String file, System.Xml.XmlWriterSettings settings) [0x00000] in <filename unknown>:0 
  at Tomboy.NoteArchiver.WriteFile (System.String write_file, Tomboy.NoteData note) [0x00000] in <filename unknown>:0 
  at Tomboy.NoteArchiver.Write (System.String write_file, Tomboy.NoteData note) [0x00000] in <filename unknown>:0 
  at Tomboy.Note.Save () [0x00000] in <filename unknown>:0 
[DEBUG 20:51:16.935] SilentUI: NoteSynchronized, Title: SIRF Alarm system and Procedure, Type: UploadModified
[DEBUG 20:51:16.935] Sync: Uploading 2 note updates
[DEBUG 20:51:16.935] SilentUI: SyncStateChanged: Uploading
[DEBUG 20:51:16.990] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/op/](https://one.ubuntu.com/notes/api/1.0/op/)
[DEBUG 20:51:19.717] SilentUI: SyncStateChanged: CommittingChanges
[DEBUG 20:51:19.732] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/op/](https://one.ubuntu.com/notes/api/1.0/op/)
[DEBUG 20:51:21.297] SilentUI: SyncStateChanged: Succeeded
[DEBUG 20:51:21.300] Sync: New revision: 503
[DEBUG 20:51:21.300] SilentUI: SyncStateChanged: Idle
[DEBUG 21:01:05.714] BackgroundSyncChecker: Checking server for updates
[DEBUG 21:01:05.714] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/](https://one.ubuntu.com/notes/api/1.0/)
[DEBUG 21:01:10.465] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/user/](https://one.ubuntu.com/notes/api/1.0/user/)
[DEBUG 21:11:05.714] BackgroundSyncChecker: Checking server for updates
[DEBUG 21:11:05.715] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/](https://one.ubuntu.com/notes/api/1.0/)
[DEBUG 21:11:07.887] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/user/](https://one.ubuntu.com/notes/api/1.0/user/)
[DEBUG 21:19:17.625] Saving 'SIRF - Pilot Line'...
[DEBUG 21:19:29.389] Saving 'SIRF - Pilot Line'...
[DEBUG 21:19:39.855] Saving 'SIRF - Pilot Line'...
[DEBUG 21:21:05.714] BackgroundSyncChecker: Checking server for updates
[DEBUG 21:21:05.714] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/](https://one.ubuntu.com/notes/api/1.0/)
[DEBUG 21:21:09.767] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/user/](https://one.ubuntu.com/notes/api/1.0/user/)
[DEBUG 21:31:05.715] BackgroundSyncChecker: Checking server for updates
[DEBUG 21:31:05.716] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/](https://one.ubuntu.com/notes/api/1.0/)
[ERROR 21:31:05.860] Caught exception. Message: Error: ConnectFailure (Network is unreachable)
[ERROR 21:31:05.860] Stack trace for previous exception:   at System.Net.HttpWebRequest.EndGetResponse (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0 
  at System.Net.HttpWebRequest.GetResponse () [0x00000] in <filename unknown>:0 
  at Tomboy.WebSync.Api.OAuth.MakeWebRequest (RequestMethod method, System.String url, System.Collections.Generic.List`1 parameters, System.String postData) [0x00000] in <filename unknown>:0 
[ERROR 21:31:05.862] Rest of stack trace for above exception:    at System.Environment.get_StackTrace()
   at Tomboy.WebSync.Api.OAuth.MakeWebRequest(RequestMethod method, System.String url, System.Collections.Generic.List`1 parameters, System.String postData)
   at Tomboy.WebSync.Api.OAuth.WebRequest(RequestMethod method, System.String url, System.String postData)
   at Tomboy.WebSync.Api.OAuth.Get(System.String uri, IDictionary`2 queryParameters)
   at Tomboy.WebSync.Api.RootInfo.GetRoot(System.String rootUri, IWebConnection connection)
   at Tomboy.WebSync.WebSyncServer.UpdatesAvailableSince(Int32 revision)
   at Tomboy.Sync.SyncManager.BackgroundSyncChecker()
   at Tomboy.Sync.SyncManager.<HandleNoteSavedOrDeleted>m__3C(System.Object o)
   at System.Threading.Timer+Scheduler.TimerCB(System.Object o)
[DEBUG 21:31:05.862] BackgroundSyncChecker: Error connecting to server
[DEBUG 21:41:05.712] BackgroundSyncChecker: Checking server for updates
[DEBUG 21:41:05.712] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/](https://one.ubuntu.com/notes/api/1.0/)
[ERROR 21:41:05.814] Caught exception. Message: Error: NameResolutionFailure
[ERROR 21:41:05.814] Stack trace for previous exception:   at System.Net.HttpWebRequest.EndGetResponse (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0 
  at System.Net.HttpWebRequest.GetResponse () [0x00000] in <filename unknown>:0 
  at Tomboy.WebSync.Api.OAuth.MakeWebRequest (RequestMethod method, System.String url, System.Collections.Generic.List`1 parameters, System.String postData) [0x00000] in <filename unknown>:0 
[ERROR 21:41:05.814] Rest of stack trace for above exception:    at System.Environment.get_StackTrace()
   at Tomboy.WebSync.Api.OAuth.MakeWebRequest(RequestMethod method, System.String url, System.Collections.Generic.List`1 parameters, System.String postData)
   at Tomboy.WebSync.Api.OAuth.WebRequest(RequestMethod method, System.String url, System.String postData)
   at Tomboy.WebSync.Api.OAuth.Get(System.String uri, IDictionary`2 queryParameters)
   at Tomboy.WebSync.Api.RootInfo.GetRoot(System.String rootUri, IWebConnection connection)
   at Tomboy.WebSync.WebSyncServer.UpdatesAvailableSince(Int32 revision)
   at Tomboy.Sync.SyncManager.BackgroundSyncChecker()
   at Tomboy.Sync.SyncManager.<HandleNoteSavedOrDeleted>m__3C(System.Object o)
   at System.Threading.Timer+Scheduler.TimerCB(System.Object o)
[DEBUG 21:41:05.814] BackgroundSyncChecker: Error connecting to server
[DEBUG 21:51:05.714] BackgroundSyncChecker: Checking server for updates
[DEBUG 21:51:05.714] Building web request for URL: [https://one.ubuntu.com/notes/api/1.0/](https://one.ubuntu.com/notes/api/1.0/)
[ERROR 21:51:05.805] Caught exception. Message: Error: NameResolutionFailure
[ERROR 21:51:05.806] Stack trace for previous exception:   at System.Net.HttpWebRequest.EndGetResponse (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0 
  at System.Net.HttpWebRequest.GetResponse () [0x00000] in <filename unknown>:0 
  at Tomboy.WebSync.Api.OAuth.MakeWebRequest (RequestMethod method, System.String url, System.Collections.Generic.List`1 parameters, System.String postData)

---

### Post by krackersk on 2011-12-21
Anybody got an idea? this is still happening

---

### Post by paulphillips on 2012-01-17
I'm getting the same behaviour.  It is very frustrating.
I've done some searching on bugs lists and it seems to be already raised as an issue, and seems to be linked with the syncing operation.

I've experienced this from the first time I've used tomboy.  I now tense up every time it greys out to sync as I'm never sure whether it will come back.

I've lost a couple of notes so far.  Not happy.

Today's lost note got corrupted, and I can't get it back...
I tried renaming it in ./local/share/tomboy to another name so tomboy wouldn't recognise it with the aim of resyncing from the server, but instead tomboy deleted it from the server!

Now it's lost forever :(

---

### Post by sailflorida on 2012-02-28
I too am experiencing sporadic crashes when running tomboy v1.8.0 under Ubuntu 11.10 oneiric. I have been running tomboy v1.6 under windows for many months, syncing to one.ubuntu.com with no problems. Previously, I ran tomboy under ubuntu 10.x with no problems.

I experience at least one, sometimes more crashes per day.

Several days ago, I backed up my notes files, uninstalled tomboy, deleted all pertinent folders, reinstalled tomboy. Still having tomboy crashes.

This is _incredibly_ frustrating.

Earlier today, tomboy.log claimed that there was a problem with a .note file. I used "more file.note", then copy / pasted from the terminal info a file to save the note, then copy / pasted the text back into a new tomboy note via the tomboy software gui.

Now I have a new crash, see tomboy.log contents below. For every crash, it seems like the cause as indicated by tomboy.log is different.

[email]watch3r@nb7:~/.config[/email]/tomboy$ cat tomboy.log 
2/28/2012 10:06:41 AM [INFO]: Initializing Mono.Addins
2/28/2012 10:32:27 AM [ERROR]: Synchronization failed with the following exception: Object reference not set to an instance of an object
  at (wrapper managed-to-native) Gtk.ListStore:gtk_list_store_set_value (intptr,intptr,int,intptr)
  at Gtk.ListStore.SetValue (TreeIter iter, Int32 column, Value value) [0x00000] in <filename unknown>:0 
  at Gtk.ListStore.AppendValues (System.Array values) [0x00000] in <filename unknown>:0 
  at Gtk.ListStore.AppendValues (System.Object[] values) [0x00000] in <filename unknown>:0 
  at Tomboy.NoteRecentChanges.UpdateResults () [0x00000] in <filename unknown>:0 
  at Tomboy.NoteRecentChanges.OnNoteSaved (Tomboy.Note note) [0x00000] in <filename unknown>:0 
  at (wrapper delegate-invoke) <Module>:invoke_void__this___Note (Tomboy.Note)
  at Tomboy.NoteManager.OnNoteSave (Tomboy.Note note) [0x00000] in <filename unknown>:0 
  at Tomboy.Note.Save () [0x00000] in <filename unknown>:0 
  at Tomboy.Sync.SyncManager.SynchronizationThread () [0x00000] in <filename unknown>:0

---

