---
title: "SSH Private key password not being remembered"
date: 2010-08-17
forum: Security
---

### Post by 448191 on 2010-08-17
Before I reinstalled Ubuntu, the password for my private key file for remote SSH login would be remembered.

Now, it keeps asking for it. Do I have to add it to the keyring (how?) or something simlar?

---

### Post by FuturePilot on 2010-08-17
When you get prompted expand the Details: and check the box.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=164535&d=1280114067[/IMG]

---

### Post by 448191 on 2010-08-17
There is no checkbox, this is from CLI.

---

### Post by bodhi.zazen on 2010-08-17
From the command line I use ssh-add to add in keys.

```
ssh-add ~/.ssh/key_name
```

---

### Post by 448191 on 2010-08-17
That did the trick. Thanks.

---

### Post by 448191 on 2010-09-10
Actually, I have to re-execute that after every boot.

Should I just add it as a startup script?

---

