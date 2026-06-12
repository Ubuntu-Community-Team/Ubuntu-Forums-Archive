---
title: "Can't install things."
date: 2012-06-05
forum: Server Platforms
---

### Post by needik on 2012-06-05
Hello.

Some time ago my friend gave me VPS server with ubuntu. I was using it for while and noticed today that I can't install anything.

For example:

apt-get install vlc
```
http://pastebin.com/aGs7ggaa
```
apt-get -f install
```
http://pastebin.com/nrcFyjkA
```

I was looking at google for this problem and found this is something with old kernel or something but I'm kinda novice for this and don't know what to do exactly now. Could you guys try to help me?
I think reinstall would be good for this one but I don't have access to server panel...

---

### Post by needik on 2012-06-07
anyone?

---

### Post by sandyd on 2012-06-07
> **needik said:**
> Hello.

Some time ago my friend gave me VPS server with ubuntu. I was using it for while and noticed today that I can't install anything.

For example:

apt-get install vlc
```
http://pastebin.com/aGs7ggaa
```
apt-get -f install
```
http://pastebin.com/nrcFyjkA
```

I was looking at google for this problem and found this is something with old kernel or something but I'm kinda novice for this and don't know what to do exactly now. Could you guys try to help me?
I think reinstall would be good for this one but I don't have access to server panel...

Looks like it is half-upgraded, the glibc versions do not match. Since dpkg is broken, best thing to do would be to reinstall

---

### Post by Cheesehead on 2012-06-08
Looks like you had a failed LTS upgrade from Lucid to Precise.

Look through your /var/log/apt/term.log to see if you can find the upgrade and failure. If so, post it here.

You can also try running the upgrade again.

If you cannot pinpoint the failure, and cannot complete the upgrade, then your best choice is indeed to reinstall. (Don't forget to backup all your data first!)

---

### Post by needik on 2012-06-08
I think that's it:

```
http://pastebin.com/1nc0JDQd
```

I can't really reinstall that vps right now because I don't have access to server panel. My friend gave me just ssh access to it...

---

