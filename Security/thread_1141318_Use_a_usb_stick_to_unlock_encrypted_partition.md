---
title: "Use a usb stick to unlock encrypted partition"
date: 2009-04-28
forum: Security
---

### Post by charlie22 on 2009-04-28
I've been looking for this but can not find an answer. I want to be able to encrypt my hard drive with truecrypt, but in order to unlock the drive the password would need to be retrieved from my plugged in USB stick. This is similar to basically starting your car with your keys where car=harddrive and keys=usb stick.

I want to run with that for a while and weigh it's advantages:
- allows incredibly long and complex passwords
- only one password attempt should be needed (unless usb stick is corrupted)
- adds depth to security

---

### Post by jkarcz on 2009-04-28
I think you can get truecrypt to fingerprint any file, meaning, you could, in theory, have truecrypt point to a file on your usb stick, which would only be accessable when the usb stick plugged in.

---

### Post by nukie77 on 2009-04-28
You can read about Truecrypt key-files here.  As long as you only keep one copy of your keyfile on your USB key, it should ask the way that you want.  Just don't lose it!

[http://www.truecrypt.org/docs/?s=keyfiles-technical-details](http://www.truecrypt.org/docs/?s=keyfiles-technical-details)

---

