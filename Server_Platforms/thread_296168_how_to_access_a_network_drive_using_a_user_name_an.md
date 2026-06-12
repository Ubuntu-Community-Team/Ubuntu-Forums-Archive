---
title: "how to access a network drive using a user name and a pass?"
date: 2006-11-09
forum: Server Platforms
---

### Post by momotaro on 2006-11-09
I need to access to my network drive, which is using a user name and a password plz help

---

### Post by elst on 2006-11-09
If you are trying to connect from a Linux desktop to a Windows server, then select Places > Connect to Server... and select the "Windows share" connection type.

To connect from the command line, you can either use smbclient or mount the directory with the "cifs" type.

---

### Post by ciscosurfer on 2006-11-09
What are you using to connect?  Samba, NFS, VNC?  The answer to your question depends.

---

