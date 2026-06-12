---
title: "Filesystem filename length limitations"
date: 2010-09-30
forum: Server Platforms
---

### Post by Bdobbs on 2010-09-30
Hi, I'm trying to store filenames that exceed 255 characters (I'm doing a backup of an S3 bucket that has such names, and there's no way to shorten them). I was under the impression that ReiserFS could handle much longer filenames than ext3, however trying to create a long filename on a ReiserFS volumes still fails:

```
# touch 123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345

``````
# touch 1234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456
touch: cannot touch `1234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456': File name too long

``````
# echo "test" > 1234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456
-bash: 1234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456: File name too long

```Is this a limit of bash and touch? Do I need to mount the volume with different parameters? Is there some sort of kernel support that needs to be enabled?

Does anyone have a different way of handling long-filenames? Thanks.

---

### Post by Bachstelze on 2010-09-30
According to Wikipedia, this is a Linux limitation, so you're pretty much out of luck. Linux is the only OS where ReiserFS is supported, and I don't know of any other filesystem that support filenames longer than 255 characters.

---

### Post by Bdobbs on 2010-09-30
Thanks for the info. I suppose I'll have to rename the files as they're downloaded and keep a lookup table for restoration.

Btw, where did you find that info on wikipedia? I see a reference to filepaths having a limit of 4k ([http://en.wikipedia.org/wiki/Comparison_of_file_systems#cite_note-note-12-9](http://en.wikipedia.org/wiki/Comparison_of_file_systems#cite_note-note-12-9)), but nothing about filenames.

---

### Post by Bachstelze on 2010-09-30
[http://en.wikipedia.org/wiki/ReiserFS](http://en.wikipedia.org/wiki/ReiserFS)

> Max filename length     4032 bytes, limited to 255 by Linux VFS

---

