---
title: "Openbox autologin encrypted home"
date: 2018-05-11
forum: Security
---

### Post by muttleysys on 2018-05-11
Hello,

I've setup Lubuntu with Openbox and autologin with a non sudo user. That Lubuntu install is on a usb drive, and many copies are being used by users, booting it from USB. Autologin User is not capable to get any terminal or tool. He can just open a python application.

I need to encrypt user's home, containing my application, in order that wouldn't be possible to mount usb to another PC and steal application.

How can I achieve that? 
Would be great to unencrypt home only if system is booted up. And if just mounted, home must be encrypted.

---

### Post by TheFu on 2018-05-11
Don't think it is possible, since the password is used to decrypt the HOME. [https://help.ubuntu.com/community/EncryptedPrivateDirectory#Using_in_conjunction_with_Auto-login](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Using_in_conjunction_with_Auto-login) seems to confirm this.

BTW, in 18.04 and later, encrypted HOME dirs are deprecated for a number of reasons.  FDE is really the best method from a security standpoint, though it won't help your requirements.

And there isn't any way to prevent someone from "stealing" the application running on the local machine if they have a tiny bit of Unix knowledge.  If you want to prevent that, make them login to a server and lock down that connection to run only 1 compiled program.  Scripted programs can't really be locked down, since the user has to be able to "read" the file(s) to run them. There are techniques around changing userids or having a compiled program as the loader which can get around this back door.

I need to think about this a bit.  Might be able to come up with a way to automate the decryption using **expect**.  Expect is a little old-school and has the same security as python scripts - so it won't be real security, rather security by obscurity.  Sometimes that's the best we can do.

Thinking about it, I like the *other userid* method more.

---

