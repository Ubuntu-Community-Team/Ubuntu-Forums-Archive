---
title: "FTP wrong passwd error"
date: 2010-09-12
forum: Server Platforms
---

### Post by darms21 on 2010-09-12
FileZilla keeps giving me 
Response:    331 Password required for USERNAME
Command:    PASS *********
Response:    530 Login incorrect.
Error:    Critical error
Error:    Could not connect to server



The password is 100% right... Any1 have any ideas? 
Could you please detail how I can change my proFTP passwd on the Linux side.
I am using sudo passwd FTP_USER_NAME.

Thanks so much guys!!!

---

### Post by darms21 on 2010-09-12
I found the solution. It turns out that I needed to user my system's login name and password and not the username + password that I thought I created for use w/ this FTP client. Can any1 explain why this is the case?

---

