---
title: "Ubuntu 18.04 no longer accepts Active Directory credentials"
date: 2023-12-11
forum: Security
---

### Post by smg-it on 2023-12-11
I have this old 18.04 VM that was connected to our AD domain some four or five years ago. Can't tell how long it's been a thing but it does not appear to be accepting my AD credentials any longer.

I did some checks described here:

[https://ubuntu.com/server/docs/service-sssd-ad](https://ubuntu.com/server/docs/service-sssd-ad)

I can get the correct results from: 

```
getent passwd john@ad1.example.com

```
And

```
groups john@ad1.example.com
```

But when I do "sudo login", I get a local prompt "myserver login" instead of the expected "ad-client login"

Needless to say the machine itself only allows me to log into it using the local admin creds.

I was thinking I could try leaving the domain and rejoining like I would on a Windows box but I'm not sure if that wouldn't break it even more. The box runs a fairly valuable instance of Microsoft SQL server.

---

