---
title: "Please please please let me keep my Tomboy notes"
date: 2013-02-04
forum: Ubuntu One (CLOSED)
---

### Post by Redsandro on 2013-02-04
Along the lines of _"[Please please please let me delete my tomboy notes!](http://ubuntuforums.org/showthread.php?t=1656198)"_, I have a problem where my notes **keep getting deleted** locally.

Something corrupted my notes (which were automatically synced to Ubuntu One) so I **[SIZE="1"](1)[/SIZE]** restored a local backup.

The local backup gets overwritten by the corrupted notes, so I **[SIZE="1"](1)[/SIZE]** _[removed all my notes from the server]("https://one.ubuntu.com/help/faq/how-can-i-delete-all-my-tomboy-notes-from-the-server/")_, **[SIZE="1"](2)[/SIZE]** restored a local backup, and **[SIZE="1"](3)[/SIZE]** synced my notes back to Ubuntu One. It sais all my 140 notes were uploaded to the server.

But when I sync a 2nd time, all my notes get removed locally again!

I tried increasing the <last-sync-date/>, <last-sync-rev/> and latest-revision values in manifest.xml, but still same behavior. Whatever I do, the first sync uploads everything to Ubuntu One, and the second sync removes everything locally.

Now all my computers are infected by this "virus", everywhere I use Tomboy, my notes keep getting removed.

What do I have to do to use my backup notes permanently again?
I don't want to recreate all 140 notes. Computers are supposed to make life easier. :P

```
$ python ubuntuone-couchdb-query  --http-method=DELETE notes
{"ok":true}
```

---

### Post by Redsandro on 2013-02-04
> **Redsandro said:**
> Along the lines of [U]"
```
$ python ubuntuone-couchdb-query  --http-method=DELETE notes
{"ok":true}
```

Found a validator. Tried again.
```
$ wget http://people.canonical.com/~roman.yepishev/us/tomboy-sync-validator.py
21K in 0.03s   
$ python tomboy-sync-validator.py 
CouchDB is at https://couchdb.one.ubuntu.com/[address]
API ref is at https://one.ubuntu.com/notes/api/1.0/user/, querying...
Notes are at https://one.ubuntu.com/notes/api/1.0/op/, querying...
Current sync GUID: 0
Latest sync revision: 1
Found 0 note
Done
```

Still a problem. :(

---

### Post by Redsandro on 2013-02-04
I have not verified this yet to see how my other machines behave, but just to keep you posted; I found that manifest revisions are irrelevant. We have to edit all the notes manually to make them appear as new as possible.

[list][*]Close Tomboy (obviously)
[*]Remove [~/.config/tomboy/manifest.xml](~/.config/tomboy/manifest.xml)
[*]Put backup notes back in [~/.local/share/tomboy/](~/.local/share/tomboy/)
[*]Regex ALL your notes in your favorite editor, and change dates to NOW:
[list][*]Pro Tip: Open all notes in Geany and use replace with regex and replace all notes in session. E.g.:
[*]Find:
[list][*]<last-change-date>.+</last-change-date>
[/list][*]Replace with:
[list][*]<last-change-date>2013-02-05T03:05:00.0000000+01:00</last-change-date>
[/list][*]Find:
[list][*]<last-metadata-change-date>.+</last-metadata-change-date>
[/list][*]Replace with:
[list][*]<last-metadata-change-date>2013-02-05T03:05:00.0000000+01:00</last-metadata-change-date>
[/list][*]Save All
[/list][*]I think this is not necessary, but you can remove all your notes [SIZE="1"](deleted notes are also stored as notes, marked as deleted)[/SIZE] from Ubuntu One using the method mentioned in the first post.
[*]Start Tomboy
[*]Sync once..
[list][*]Woohoo, everything is uploaded
[/list][*]Sync twice.. 
[list][*]Woohoo, nothing is deleted this time!
[/list][*]Fixed! (I hope)[/list]

Unfortunately, this causes ALL notes to be "last edited" *now* (or rather one minute ago), which for some reason is more inconvenient than it sounds.

---

### Post by Redsandro on 2013-02-05
NOOOOOOOOO!

All my notes are deleted again on my office computer. Put (new) backup (from home computer after editing the dates) back, and they get removed again.

:( Please help!

---

### Post by Redsandro on 2013-02-05
As newer notes should overwrite the older similar notes, but in stead both get removed, I think this is not very much what is supposed to happen. 

Bug report in. [https://bugs.launchpad.net/ubuntuone-servers/+bug/1116237](https://bugs.launchpad.net/ubuntuone-servers/+bug/1116237)

---

