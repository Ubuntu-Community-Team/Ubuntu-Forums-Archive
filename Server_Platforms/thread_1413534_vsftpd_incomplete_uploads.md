---
title: "vsftpd incomplete uploads"
date: 2010-02-22
forum: Server Platforms
---

### Post by cdenley on 2010-02-22
I need to either find a reliable way for my script to determine if a file has not finished being uploaded yet, or I need to reliably determine what user was just connected to a non-listening instance of vsftpd started by the script. Any ideas?

---

### Post by cdenley on 2010-02-23
I decided to create a unique log file for each instance of vsftpd, then parse the log file when that instance exits to determine what files were uploaded during that session and by what user. Not the most elegant solution, but should be reliable enough.

---

