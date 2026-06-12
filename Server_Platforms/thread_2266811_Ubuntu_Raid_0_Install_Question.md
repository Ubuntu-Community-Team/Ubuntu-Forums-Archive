---
title: "Ubuntu Raid 0 Install Question"
date: 2015-02-25
forum: Server Platforms
---

### Post by Bonzai37 on 2015-02-25
I have installed Ubuntu-1410-utopic-64-minimal on mt server with 2   3TB HDDs in Raid 0. It's my first time setting up a Raid and I would like to know if it's correct. This is what shows in Webmin.

[http://gyazo.com/0136d4901627423d19e76d09c5c6851d](http://gyazo.com/0136d4901627423d19e76d09c5c6851d)
  [http://gyazo.com/64b607a6c4120ef4819d52c97c83f4d2](http://gyazo.com/64b607a6c4120ef4819d52c97c83f4d2)

Thank you and I fully understand and accept the risks of Raid 0.

---

### Post by Bonzai37 on 2015-02-25
I have installed Ubuntu-1410-utopic-64-minimal on mt server with 2   3TB   HDDs in Raid 0. It's my first time setting up a Raid and I would like   to know if it's correct. This is what shows in Webmin.

[http://gyazo.com/0136d4901627423d19e76d09c5c6851d](http://gyazo.com/0136d4901627423d19e76d09c5c6851d)
  [http://gyazo.com/64b607a6c4120ef4819d52c97c83f4d2](http://gyazo.com/64b607a6c4120ef4819d52c97c83f4d2)

Thank you and I fully understand and accept the risks of Raid 0.

---

### Post by nerdtron on 2015-02-26
I assume the RAID 1 in your screenshot is the /boot partition? From the screenshots, it looks good. But it's better to rely on the output of /proc/mdstat.

---

### Post by oldfred on 2015-02-26
Please do not post duplicate threads, merged.

---

