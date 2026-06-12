---
title: "rsa-dsa"
date: 2010-01-10
forum: Security
---

### Post by tanvirmcc on 2010-01-10
Dear all,

  
[SIZE=3][FONT=Times New Roman]  I want to  configure SSH key-based authentication and SSH password Authentication in same  machine for different user . Can any one  please help me.[/FONT][/SIZE]




[SIZE=3][FONT=Times New Roman]Tanvir Ahamed
[/FONT][/SIZE]

---

### Post by CharlesA on 2010-01-10
You can create the key-pair by using the ssh-keygen program. Then add the public key to the authorized_users file.

---

