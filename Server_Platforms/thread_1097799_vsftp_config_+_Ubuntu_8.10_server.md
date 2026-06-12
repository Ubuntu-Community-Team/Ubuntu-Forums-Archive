---
title: "vsftp config + Ubuntu 8.10 server"
date: 2009-03-16
forum: Server Platforms
---

### Post by daprofessor on 2009-03-16
I would like to deny anonymous ftp users from being able to browse the ftp directory.  The anonymous users will just download files from this server by direct link, I don't want them to be able to goto a browser and type [ftp://x.x.x.x](ftp://x.x.x.x) is there an option in the config that will do this?

I have tried to Google this.

I am running the latest version of vsftp and Ubuntu 8.10 Server.

---

### Post by daprofessor on 2009-03-16
I finally found the answer, you have to add this entry

dirlist_enable
    If set to NO, all directory list commands will give permission denied.

    Default: YES 

Set it to No.

---

