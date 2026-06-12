---
title: "LUKS on Existing System"
date: 2009-01-27
forum: Security
---

### Post by Keymaster on 2009-01-27
When I initially configured my Linux machine I had a 40GB hdd in it.  I have a LUKS partition that is mounted for / and one for swap space.  The drive started to fail, so I cloned it using a live cd and the dd command to a 200GB drive.  Now I have all this extra space.  How can I turn the extra space into another LUKS encrypted volume?  Thanks

---

### Post by hyper_ch on 2009-01-28
have a look from at section V: [http://www.howtoforge.com/ubuntu_dm_crypt_luks](http://www.howtoforge.com/ubuntu_dm_crypt_luks)
and maybe also this here: [http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile](http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile)

---

### Post by Keymaster on 2009-03-11
Thanks.  I'll check it out.  Sorry it took so long for me to reply, but I've been quite busy.

---

