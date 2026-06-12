---
title: "Please help me... Overwrited file... :(((("
date: 2007-02-11
forum: Server Platforms
---

### Post by Kika556 on 2007-02-11
Dear members.
I have Ubuntu server 6.06 and program I was using to edit one text file via FTP has overwrited it with another file. Now I have two same files, but not one I need. (file kept its original name).

I didn't do backup, don't have a backup of that file, it is VEEERY important to me.

Is there any chance I can get that file back?

Thank you in advance.

---

### Post by kidders on 2007-02-11
Hi there,

I'm afraid there is no way to recover your file, as far as I know. :-( There are a few circumstances where it *might* be possible to recover _some_ of it though:

[LIST]
[*]You overwrote a very large file with a very small one.
[*]Some running process loaded the original file into memory before you overwrote it.
[*]The file is plain text, and is sitting in a terminal scrollback buffer somewhere.
[*]If you accessed absolutely nothing else after overwriting the file, yanking out the hard disk immediately might save the file ... but may also destroy things & cause corruption.
[/LIST]

These are all very unlikely, but since your file is so important, I wanted to at least mention them.

---

