---
title: "Ubuntu Keyring..."
date: 2010-08-06
forum: Security
---

### Post by Baldrick_NZ on 2010-08-06
So, how does one configure the keyring to initialise upon startup?

I find when I restart my PC, I need to enter my keyring password when I open Evolution, which can be a right pain. Any help to remedy this would be much appreciated.

Cheers,
Baldrick

---

### Post by kemra on 2010-08-06
Do you have GDM automatically log you in? If so you will still need to supply your password to open the keyring. If you dont have GDM log you in automatically then you shouldn't be prompted for a password.

But to answer your question more directly I'm not sure you can have the keyring supply passwords automatically ebfore you yourself have supplied your acocunt password. If there is a way I'm sure someone will step in.

---

### Post by FuturePilot on 2010-08-06
> **kemra said:**
> Do you have GDM automatically log you in? If so you will still need to supply your password to open the keyring. If you dont have GDM log you in automatically then you shouldn't be prompted for a password.

But to answer your question more directly I'm not sure you can have the keyring supply passwords automatically ebfore you yourself have supplied your acocunt password. If there is a way I'm sure someone will step in.

This is true. 

But if you do not have autologin enabled, make sure your login password is the same as the keyring password. Having them different will also cause you to be prompted.

---

### Post by Baldrick_NZ on 2010-08-06
> **FuturePilot said:**
> This is true. 

But if you do not have autologin enabled, make sure your login password is the same as the keyring password. Having them different will also cause you to be prompted.

So how does this noob get to autologin? Cheers.

---

### Post by Baldrick_NZ on 2010-08-10
Solved. Thanks guys.

---

