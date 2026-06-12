---
title: "[SOLVED] Trouble following OpenSSL community help directions"
date: 2007-05-02
forum: Server Platforms
---

### Post by TennTux on 2007-05-02
I'm in the process of setting up Apache to use SSL so I got a copy of the community provided OpenSSL help ([https://help.ubuntu.com/community/OpenSSL]("https://help.ubuntu.com/community/OpenSSL")) . I am able to create a Certificate Authority. However, when I get to creating a server certificate I enter the following command.

```
openssl req -newkey rsa:1024 -keyout fas_tempkey.pem -keyform PEM -out fas_tempreq.pem -outform PEM
```

As expected I'm asked for a pass-phrase that I enter. And it finishes as expected except that I don't see the fas_tempreq.pem file. I wouldn't worry about this but a couple of steps later under the directions for signing the server certificate with my Certificate Authority I need to run the following command.

```
openssl ca -in fas_tempreq.pem -out server_crt.pem
```

However, this fails because fas_tempreq.pem does not exist...    ???

Am I missing something?

---

### Post by TennTux on 2007-05-02
Thanks for looking at this issue but I found the problem. I didn't see an error in the .cnf file. Fixed it and was able to move on.

---

