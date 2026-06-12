---
title: "Ubuntu server slow"
date: 2010-07-29
forum: Server Platforms
---

### Post by csh on 2010-07-29
I am using VirtualBox to run Ubuntu Server 10.04.

Every time when I try to use 'cat' command to view a large log file like /var/log/messages, it will run very slow.

Is there any solution for the above problem?

And, after using 'cat' command to view a file, I cannot scroll up to view the content at the top of the file. Any solution for this also?

---

### Post by Wim Sturkenboom on 2010-07-29
Use 'less' instead of 'cat'; allows you to page through your files.

Don't know the answer to the slowness; might be normal for big files but not sure.

---

### Post by csh on 2010-07-29
> **Wim Sturkenboom said:**
> Use 'less' instead of 'cat'; allows you to page through your files.

Don't know the answer to the slowness; might be normal for big files but not sure.

In other OS like CentOS, this problem will not occur.

---

### Post by HermanAB on 2010-07-29
Howdy,

Use 'top' to see what junk you have running.

Use 'tail -n 1000 filename' or similar to view log files.

---

### Post by Bachstelze on 2010-07-29
The slowness is caused by the framebuffer.  Blacklist the fbcon and vga16fb kernel modules.

---

### Post by lisati on 2010-07-29
Moved to "Server Platforms"

---

