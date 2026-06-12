---
title: "moving files between very deep directories"
date: 2019-12-23
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-12-23
"_very deep_" refers to a directory so deep that its full absolute path exceeds the allowed maximum path string permitted in regular Unix file system operation syscalls, requiring alternate methods of access.  this has been easy to overcome by changing directory one directory or a few directories at a time until the desired directory is reached then performing the operations locally.

"_extremely deep_" would be a more radical case where the full absolute path even exceeds the maximum string that can be passed as a _command line argument_. 

i now have a case where i need to move a file between two _very different_ _very deep_ directories.  this case cannot be an _extremely deep_ case since it gets the paths on a _command line_.  if i was doing this in [COLOR=#006400][FONT=courier new]**C**[/FONT][/COLOR] i could access each directory via a _file descriptor_ and call the new [COLOR=#800080][FONT=courier new]**renameat()**[/FONT][/COLOR] syscall which Linux implements (my case involves _Ubuntu_).  but i am doing this in a _bash script_ and am wondering if the [COLOR=#0000cd][FONT=courier new]**mv**[/FONT][/COLOR] command knows how to do this or if i need to work out another way to do this.

---

