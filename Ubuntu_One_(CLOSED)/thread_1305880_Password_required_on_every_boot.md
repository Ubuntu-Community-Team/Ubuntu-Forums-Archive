---
title: "Password required on every boot"
date: 2009-10-30
forum: Ubuntu One (CLOSED)
---

### Post by celticbhoy on 2009-10-30
Every time I boot into Karmic, I have to enter my password to access Ubuntu One. I have autologin set, how do I sort this?

---

### Post by joshuahoover on 2009-11-02
> **celticbhoy said:**
> Every time I boot into Karmic, I have to enter my password to access Ubuntu One. I have autologin set, how do I sort this?

Since you have auto-login set, you're going to get this prompt for a keyring password. The dangerous way to get rid of this prompt is to set your keyring password to blank. This will store all keyring passwords in clear text. The best way to solve this is to login to your computer and set the keyring password to be the same as your login password.

Thank you,

Joshua

---

