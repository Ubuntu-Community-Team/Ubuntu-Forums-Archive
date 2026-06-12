---
title: "samba in intrepid server"
date: 2009-02-06
forum: Server Platforms
---

### Post by fahd on 2009-02-06
I installed samba server(version 3.2.3, it functions well. Nevertheless, I often get the next message whenever I issue the command *smbstatus*:
 Failed to initialise messages database:Permission denied
messaging_tdb_init failed: NT_STATUS_ACCESS_DENIED.

Thanks a lot.

Fahd
090206

---

### Post by Formaldehyde on 2009-02-10
use sudo

---

### Post by cb951303 on 2009-02-10
are you in samba group?

---

### Post by fahd on 2009-02-10
Thanks the replies. Anyway I am a member of the admin group. In the previous ubuntu version (hardy including samba server ver. 3.0.28a) I could give the command smbstatus as a member of admin group. However the same thing does not happen in intrepid server (samba ver. is 3.2.3).I login as linuxuser; where linuxuser is the member of admin group (groups linuxuser). As I mentioned above, this functioned well in hardy. It is very weird, is not it? Thanks again the clue.

Fahd
090210

---

