---
title: "Script read files - order issue"
date: 2011-12-02
forum: Server Platforms
---

### Post by Coder68 on 2011-12-02
I have created the following simple script to create MD5 hash output for a folder full of Rainbow Tables that I downloaded using wget. The script works, however it does not read the files in order so I have to either go and cut and paste to the correct spot, or reorder them in Excel. 

[PHP]#!/bin/bash

find -name \*.rti2 -exec md5sum "{}" + >downloadedMD5.txt 

exit 0[/PHP]If the order of the files in Nautilus is:

file_001.txt
file_002.txt
...
...
file_008.txt
file_009.txt
....
File_300.txt


Then what I get is something like this:
file_001.txt
file_002.txt
...
...
file_009.txt
file_010.txt
...
file_300.txt
file_292.txt

It seems that every 8th file can be found randomly in the output file. Only the last three digits at the end change in the file name. 

Any idea why this is or how to fix it?

Please keep in mind I am not a programmer or even a good script writer. :confused:

Once it is working correctly I want to add in the diff command so I can get a list of any files that I need to download again.

Thank you,

C68

---

### Post by papibe on 2011-12-02
Hi Coder68.

This may work:
```
find -name '*.rti2' | sort | xargs md5sum > downloadedMD5.txt 
```
But if you want to make extra careful (dirty characters in the file names). You can also try:
```
find -name '*.rti2' -print0 | sort -z | xargs -0 md5sum > downloadedMD5.txt 
```
Hope it helps,
Regards.

---

### Post by Coder68 on 2011-12-03
Thank you, I will give that a try later today when i get back home. 

I was able to look at all the options you listed via the man pages except one. What does the -print0 do?

Thank you,

C68

---

### Post by papibe on 2011-12-03
In Linux there are little restrictions on what character can be use to name file. As a result filenames can have spaces, newlines, etc. That is not necessarily your case, but I mentioned just in case.

Using the option -print0 prints (actually in this case passes it to the other program in the pipe) using a null character as a separator, thus keeping all dirty characters inside the filename.

When you use that option in a pipe, you need to use it in all other programs that are in it. That's the reason for the sorts' -z and the xargs' -0.

Hope it helps.
Regards.

---

