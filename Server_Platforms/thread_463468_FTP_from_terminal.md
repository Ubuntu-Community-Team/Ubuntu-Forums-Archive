---
title: "FTP from terminal"
date: 2007-06-03
forum: Server Platforms
---

### Post by notquitehere188 on 2007-06-03
how can i copy files from an ftp server to my ubuntu computer using the terminal?

---

### Post by pbw on 2007-06-03
ncftp is a great userfriendly non-gui ftp client, try that it's my preference.

sudo apt-get install ncftp.

ncftp open site.com

use the -u (user) and -p (password) flags on login if it's not anonymous

get file

---

### Post by Wim Sturkenboom on 2007-06-03
Read *man ftp*

---

