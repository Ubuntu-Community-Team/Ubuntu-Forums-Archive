---
title: "key based login how is there any ftp client which support key login"
date: 2010-05-17
forum: Server Platforms
---

### Post by tapas_mishra on 2010-05-17
I have disabled password logins to a server.I want to transfer some files to it using a client like FileZilla but there was no way I could give private key to filezilla is there an ftp client
which supports key based login?

---

### Post by NeddyDownUnder on 2010-05-17
Would you be able to tunnel it through ssh? i.e. 

ssh -fNL 5904:127.0.0.1:21 user@server (the 5904 is arbitrary... you can use any free local port)

Then point the ftp client to 127.0.0.1:5904 

I don't really know if it will work as I have not tested it with ftp, but I used to forward VNC and AFP like this just fine.

Good luck

---

