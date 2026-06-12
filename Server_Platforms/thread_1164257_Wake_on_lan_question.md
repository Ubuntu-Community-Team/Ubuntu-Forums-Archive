---
title: "Wake on lan question"
date: 2009-05-19
forum: Server Platforms
---

### Post by audio_uphoria on 2009-05-19
Wasn't sure if this would go better in the server section or the networking section but basically I have a server set up using ubuntu 8.04 server edition. I noticed the bios of the server has wake on lan feature and I was wondering if I could use this feature on the server. If so how? Thanks.

---

### Post by cdenley on 2009-05-19
In order to turn the server on with wol, you must send a "magic packet" from another computer on the LAN with the MAC address of your server.
```

sudo apt-get install wakeonlan
man wakeonlan

```

---

### Post by Cheesemill on 2009-05-19
Yep, you sure can.

If you enable Wake-On LAN in your servers BIOS you can then power it up just by sending it a magic packet.

This can be done by using the wakeonlan program which is in the repo's.

Cheesemill

---

### Post by audio_uphoria on 2009-05-19
So in order to use wol I can only do it from another computer on the same lan and not over the internet, is what your saying?

---

### Post by cdenley on 2009-05-19
> **audio_uphoria said:**
> So in order to use wol I can only do it from another computer on the same lan and not over the internet, is what your saying?

That is correct. The magic packet does not use the IP protocol, and cannot be routed across the internet. You need a second computer running to send the magic packet.

---

### Post by audio_uphoria on 2009-05-19
Ok thanks. My server is set up like 5 miles from where I live so I wish there was a way to turn it on and off from my home pc over the internet. I guess I can still shut it down using command line in putty. Thanks for the info.

---

