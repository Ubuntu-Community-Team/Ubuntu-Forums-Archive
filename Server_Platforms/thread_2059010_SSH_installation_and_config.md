---
title: "SSH installation and config"
date: 2012-09-17
forum: Server Platforms
---

### Post by hhaydoura on 2012-09-17
I really want to know how to install and configure ssh server and client, I am working on a virtual machine only command line no GUI, and i want to go to a client pc from the server using ssh, I hope someone could help me plz

---

### Post by codemaniac on 2012-09-17
> **hhaydoura said:**
> I really want to know how to install and configure ssh server and client, I am working on a virtual machine only command line no GUI, and i want to go to a client pc from the server using ssh, I hope someone could help me plz

Please follow the community documentation .

[https://help.ubuntu.com/12.04/serverguide/openssh-server.html](https://help.ubuntu.com/12.04/serverguide/openssh-server.html)

---

### Post by hhaydoura on 2012-09-17
well this is not what i am looking for already saw it, what i'm looking for is to ssh a client user "userA", what i need to know are the steps to make that possible

---

### Post by SlugSlug on 2012-09-17
install ssh server on client A's machine (sudo apt-get install ssh)

then ssh usera@IPofClientA

---

### Post by hhaydoura on 2012-09-17
it worked :)  thanks man :)

---

