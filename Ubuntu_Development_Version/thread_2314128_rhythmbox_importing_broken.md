---
title: "rhythmbox importing broken"
date: 2016-02-18
forum: Ubuntu Development Version
---

### Post by ELD on 2016-02-18
Has anyone else noticed Rhythmbox totally crashes when you try to import music on 16.04?

---

### Post by mc4man on 2016-02-18
It doesn't crash here when importing from Music, however does from other locations (though the tracks are imported.
The crash here is in rhythmbox-metadata (- rhythmbox-metadata crashed with SIGSEGV in_int_malloc()

edit: could be only other locations if non music file types are also present..

---

### Post by ELD on 2016-02-18
Okay, I wasn't too clear, not exactly the actual import itself, but the bit before you important, so I guess the scanning?

```


(rhythmbox:5543): RhythmDB-CRITICAL **: rhythmdb_entry_get_entry_type: assertion 'entry != NULL' failed
Segmentation fault (core dumped)

```
That's what I get.

---

### Post by mc4man on 2016-02-18
> **ELD said:**
> Okay, I wasn't too clear, not exactly the actual import itself, but the bit before you important, so I guess the scanning?

```


(rhythmbox:5543): RhythmDB-CRITICAL **: rhythmdb_entry_get_entry_type: assertion 'entry != NULL' failed
Segmentation fault (core dumped)

```
That's what I get.
That I don't see at all. Are you fully updated? (3.3-1ubuntu4 for Rb
If so maybe try deleting ~/.local/rhythmbox & start over with importing, ect.

---

### Post by ELD on 2016-02-18
> **mc4man said:**
> That I don't see at all. Are you fully updated? (3.3-1ubuntu4 for Rb
If so maybe try deleting ~/.local/rhythmbox & start over with importing, ect.

Weird, works now after deleting the config folder as suggested, can close this then.

---

