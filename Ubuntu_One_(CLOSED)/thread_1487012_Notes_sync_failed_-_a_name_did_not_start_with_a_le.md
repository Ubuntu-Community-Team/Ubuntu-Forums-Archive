---
title: "Notes sync failed - a name did not start with a legal character"
date: 2010-05-18
forum: Ubuntu One (CLOSED)
---

### Post by hartl_vienna on 2010-05-18
The sync with Tomboy doesn't work. If I start the sync I get the following error. Could anyone help me with that?


```
[ERROR 07:28:21.014] Synchronization failed with the following exception: a name did not start with a legal character 123 ({) Line 13, position 2.
  at Mono.Xml2.XmlTextReader.ReadName (System.String& prefix, System.String& localName) [0x00000]
  at Mono.Xml2.XmlTextReader.ReadStartTag () [0x00000]
  at Mono.Xml2.XmlTextReader.ReadContent () [0x00000]
  at Mono.Xml2.XmlTextReader.Read () [0x00000]
  at System.Xml.XmlTextReader.Read () [0x00000]
  at Tomboy.Sync.NoteUpdate..ctor (System.String xmlContent, System.String title, System.String uuid, Int32 latestRevision) [0x00000]
  at Tomboy.WebSync.WebSyncServer.GetNoteUpdatesSince (Int32 revision) [0x00000]
  at Tomboy.Sync.SyncManager.SynchronizationThread () [0x00000]

(tomboy:2010): GLib-CRITICAL **: g_source_remove: assertion `tag > 0' failed
```

---

