---
title: "Samba access OSX share from Ubuntu problem"
date: 2017-02-19
forum: Ubuntu/Debian BASED
---

### Post by SreckoMicic on 2017-02-19
I spent entire day trying to figure out why I can not access shared folder on OSX ElCap from KDE Neon....
I can access Win10 folders from Ubuntu without problems, I can access from OSX Ubuntu folders but I can not access OSX shares from Ubuntu.

I am getting this error with smbclient

```
NTLMSSP packet check failed due to short signature (0 bytes)!
BAD SIG NTLM2: wanted signature of
[0000] 01 00 00 00 19 FA C6 84   87 23 52 AE 00 00 00 00   ........ .#R.....
BAD SIG: got signature of
NTLMSSP NTLM2 packet check failed due to invalid signature!
GENSEC SPNEGO: failed to verify mechListMIC: NT_STATUS_ACCESS_DENIED
SPNEGO login failed: Access denied
session setup failed: NT_STATUS_ACCESS_DENIED

```

If I add  *client use spnego = no* in smb.conf  I am getting 

```
protocol negotiation failed: NT_STATUS_NOT_SUPPORTED
```

For the love of God what can be issue with this? Can anyone help?

---

### Post by howefield on 2017-02-19
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

