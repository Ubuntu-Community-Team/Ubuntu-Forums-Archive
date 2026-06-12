---
title: "freeRadius - running external Script"
date: 2014-06-11
forum: Server Platforms
---

### Post by daniel158 on 2014-06-11
Hello,

i'm using a freeRadius Server for 802.1X authenification with ntlm_auth. This works already fine. For dynamic vlan assignment I used the Tunnel-Private-Group-Id parameter in the post-auth section:

```

update reply {
               Tunnel-Type = "VLAN",
               Tunnel-Medium-Type = "IEEE-802"
               Tunnel-Private-Group-Id = 10
       }
```
This also works fine.
The problem is to run an external script which returns the ID which shoud be used as Tunnel-Private-Group-Id. This sounds simple and probably it is, but in hours of searching and trying exec Modul, I was not able to find an Documentation which I could understand.

Is there anybody who can help me?

regards,
Daniel

---

