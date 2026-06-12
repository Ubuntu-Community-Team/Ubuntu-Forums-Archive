---
title: "Bookmarks and Tomboy not syncing, 11.04"
date: 2011-05-21
forum: Ubuntu One (CLOSED)
---

### Post by jamesjenner on 2011-05-21
G'day all,

I've used Ubuntu one for file syncing on my work and home computer (started on 10.10 only recently upgraded to 11.04, work is XP) and while it seems a tad slow in syncing it worked okay. Though I've used alternatives because they seem more responsive.

Well I've recently upgraded to 11.04 on my comp at home and installed 11.04 on my lappy (new install). Both are 64-bit version of Ubuntu. Thought I'd start using the other sync features and see how it fairs.

Well files appear to be okay (though I haven't tested it thoroughly yet), but I cannot get firefox bookmarks or tomboy to sync at all. I've searched through the forums but it appears to be only comments about it not working, I've yet to see anyone with a solution.

Could someone please help?

Btw, I've checked out .cache/ubuntuone/log and all the syncdeamon exception logs are empty. I also just threw a file into the Ubuntu One folder and it synced damn fast. so it appears the only issues is with the bookmarks and notes.

---

### Post by ReelExterminator on 2011-05-23
I have the same problem with Tomboy. After choosing Ubuntu One as the sync service, I get the error '**Failed to synchronize** Could not synchronize notes. Check the details below and try again.' The details box is blank. Running Tomboy from a console reveals the following:
```

xxxx@xxxx-desktop:~$ tomboy 
[INFO 00:03:50.808] Initializing Mono.Addins
[ERROR 00:03:58.274] Synchronization failed with the following exception: Expected =, but found d [100]  Line 32, position 61.
  at Mono.Xml2.XmlTextReader.ExpectAfterWhitespace (Char c) [0x00000] in <filename unknown>:0 
  at Mono.Xml2.XmlTextReader.ReadAttributes (Boolean isXmlDecl) [0x00000] in <filename unknown>:0 
  at Mono.Xml2.XmlTextReader.ReadStartTag () [0x00000] in <filename unknown>:0 
  at Mono.Xml2.XmlTextReader.ReadContent () [0x00000] in <filename unknown>:0 
  at Mono.Xml2.XmlTextReader.Read () [0x00000] in <filename unknown>:0 
  at System.Xml.XmlTextReader.Read () [0x00000] in <filename unknown>:0 
  at Tomboy.Sync.NoteUpdate..ctor (System.String xmlContent, System.String title, System.String uuid, Int32 latestRevision) [0x00000] in <filename unknown>:0 
  at Tomboy.WebSync.WebSyncServer.GetNoteUpdatesSince (Int32 revision) [0x00000] in <filename unknown>:0 
  at Tomboy.Sync.SyncManager.SynchronizationThread () [0x00000] in <filename unknown>:0 

(Tomboy:27156): GLib-CRITICAL **: g_source_remove: assertion `tag > 0' failed
** (Tomboy:27156): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object
[ERROR 00:08:31.706] Synchronization failed with the following exception: Expected =, but found d [100]  Line 32, position 61.
  at Mono.Xml2.XmlTextReader.ExpectAfterWhitespace (Char c) [0x00000] in <filename unknown>:0 
  at Mono.Xml2.XmlTextReader.ReadAttributes (Boolean isXmlDecl) [0x00000] in <filename unknown>:0 
  at Mono.Xml2.XmlTextReader.ReadStartTag () [0x00000] in <filename unknown>:0 
  at Mono.Xml2.XmlTextReader.ReadContent () [0x00000] in <filename unknown>:0 
  at Mono.Xml2.XmlTextReader.Read () [0x00000] in <filename unknown>:0 
  at System.Xml.XmlTextReader.Read () [0x00000] in <filename unknown>:0 
  at Tomboy.Sync.NoteUpdate..ctor (System.String xmlContent, System.String title, System.String uuid, Int32 latestRevision) [0x00000] in <filename unknown>:0 
  at Tomboy.WebSync.WebSyncServer.GetNoteUpdatesSince (Int32 revision) [0x00000] in <filename unknown>:0 
  at Tomboy.Sync.SyncManager.SynchronizationThread () [0x00000] in <filename unknown>:0 

```

Not knowing anything about Mono, I have no idea in what file it's getting stuck at line 32.

---

### Post by davim on 2011-05-23
try this:

[https://bugs.launchpad.net/ubuntuone-servers/+bug/575937](https://bugs.launchpad.net/ubuntuone-servers/+bug/575937)

run this script:
[http://people.canonical.com/~roman.yepishev/ubuntuone-scripts/tomboy-recovery.py](http://people.canonical.com/~roman.yepishev/ubuntuone-scripts/tomboy-recovery.py)

---

### Post by jamesjenner on 2011-05-23
Anyone else have the problem with bookmarks in firefox?

---

