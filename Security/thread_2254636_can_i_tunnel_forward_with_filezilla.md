---
title: "can i tunnel forward with filezilla"
date: 2014-11-28
forum: Security
---

### Post by dilbert_one on 2014-11-28
can i tunnel forward with filezilla ? 

does this work?

---

### Post by CharlesA on 2014-11-29
Like create an ssh tunnel? I do not believe so as it would call the sftp-subsystem and that has a limited amount of capabilities.

---

### Post by bashiergui on 2014-11-29
Why wouldn't this work?
[https://support.terranetwork.net/web/knowledgebase/139/FTP-over-SSL-and-SSH-with-FileZilla.html](https://support.terranetwork.net/web/knowledgebase/139/FTP-over-SSL-and-SSH-with-FileZilla.html)

Or you could just use an encrypted protocol to begin with like scp or sftp.

---

