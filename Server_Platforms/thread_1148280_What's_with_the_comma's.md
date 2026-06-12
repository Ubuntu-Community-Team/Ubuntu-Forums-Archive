---
title: "What's with the comma's ?"
date: 2009-05-04
forum: Server Platforms
---

### Post by moonpup on 2009-05-04
I just installed 9.04 Server and maybe never noticed this on earlier versions, but what are the 3 commas after my username in the /etc/passwd file? Empty variable fields like full name, phone, etc?

user:x:1000:1000:user,,,:/home/user:/bin/bash

---

### Post by Ateles on 2009-05-04
Yes, you're right - those are the GECOS fields (for name, phone, etc.).

---

### Post by bab1 on 2009-05-04
> **moonpup said:**
> ... what are the 3 commas after my username in the /etc/passwd file? Empty variable fields like full name, phone, etc?

user:x:1000:1000:user,,,:/home/user:/bin/bash

As **Ateles** said, it's for GECOS fields.  These are  also known as comments.  The utility ***finger*** will retrieve the comments from the CLI

---

