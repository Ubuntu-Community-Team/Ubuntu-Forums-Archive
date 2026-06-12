---
title: "Can't download Ubuntu minimal install for Hardy"
date: 2009-07-21
forum: The Cafe
---

### Post by hellmet on 2009-07-21
Is it only me? I can download Jaunty. Not Intrepid or Hardy. I need the .iso for Hardy
Does anybody know of alternate locations?

---

### Post by Dragonbite on 2009-07-21
> **hellmet said:**
> Is it only me? I can download Jaunty. Not Intrepid or Hardy. I need the .iso for Hardy
Does anybody know of alternate locations?

When you go to the [[COLOR="Blue"]download page[/COLOR]]("http://www.ubuntu.com/getubuntu/download") there is an option to **Ubuntu 8.04 LTS Desktop** under the "Choose a version" heading.

Or is it that it isn't downloading Hardy? It isn't downloading correctly?

When I select 8.04 LTS Desktop and a random mirror, I see the link does go to *..8.04.3..* which is Hardy.  And there's a list of mirrors on the Download page.

So if these don't answer your question, can you be a little more specific as to what is not working?

---

### Post by hellmet on 2009-07-21
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
Try downloading Hardy or Intrepid. :(

---

### Post by Dragonbite on 2009-07-21
> **hellmet said:**
> [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
Try downloading Hardy or Intrepid. :(

I got the dialog box and it started downloading (32bit). I'm at work so I don't have any CDs to burn it on. Otherwise, the link that started downloading mini.iso is [[COLOR="Blue"]http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/installer-i386/current/images/netboot/mini.iso[/COLOR]]("http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/installer-i386/current/images/netboot/mini.iso")

If the issue is Firefox then from a terminal you could download it with```
wget http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/installer-i386/current/images/netboot/mini.iso
```

That way if there is an error you have a chance to see it.

I guess I'm not 100% sure where the problem is; downloading, burning, downloads incorrect versions, etc.?

Are you trying to download the 64 bit, PPC or 32 bit version?

---

### Post by hellmet on 2009-07-21
I was trying to download (32bit) from work and the download never started, even with wget. It is working alright from home now. Probably some issue with the Internet at work. Sorry for the extra thread...

---

### Post by Dragonbite on 2009-07-21
> **hellmet said:**
> I was trying to download (32bit) from work and the download never started, even with wget. It is working alright from home now. Probably some issue with the Internet at work. Sorry for the extra thread...

No problem.

That was going to be my next focus, was whether or not your ISP (or work, in your case) has that blocked somehow.

Glad to hear it's solved.

---

### Post by hellmet on 2009-07-21
Thanks for your support. Cheers!

---

