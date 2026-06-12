---
title: "TTF PHP5 Ubuntu 8.10 Issue!"
date: 2009-07-18
forum: Server Platforms
---

### Post by ubila on 2009-07-18
Hello good people :D

Im trying to make a security image validation and host it on my Ubuntu 8.10 server. The script works perfect when hosted on my off-shore hosting.

But when i try run it on my server, im getting errors :

**Warning**:  imagettftext() [function:imagettftext]: Could not find/open font in **/htdocs/security-image-inc.php** on line [B]81

[/B]The image is working, but the text it seems it cannot find the file. Yet it can fopen() the file and the permissions of the text file are sett to 755.

I THINK this is a ubuntu ttf support issue ? Any ideas? 

Thanks :D

---

### Post by ubila on 2009-07-19
Figured it out...
Incase anyone else hits this problem...It was a permissions problem. The ttf file and the folder that its contained in needs to be sett to 775.

---

