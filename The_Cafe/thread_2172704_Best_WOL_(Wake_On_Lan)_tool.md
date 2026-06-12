---
title: "Best WOL (Wake On Lan) tool?"
date: 2013-09-06
forum: The Cafe
---

### Post by ZarathustraDK on 2013-09-06
Hey. I was wondering if you guys have any recommendations in regards to WOL-software.

I'm looking for some kind setup where I can assign entire IP-ranges to be woken up, give them a designation and save them for later use. Any ideas?

---

### Post by TheFu on 2013-09-06
I use a perl script - **wake.pl**.
It can read all the machines to be sent WoL commands from a file.
Don't recall where I found the script - google found this: [http://www.cpan.org/authors/id/S/SR/SRAMKI/wol.pl](http://www.cpan.org/authors/id/S/SR/SRAMKI/wol.pl) at CPAN - THE place for perl stuff. I haven't used that script myself. This version is missing the all important - get-inputs-from-a-file.  

Next google result ... ah ... [http://www.han.de/~gero/netboot/archive/msg02524.html](http://www.han.de/~gero/netboot/archive/msg02524.html) is the one I've been using.

---

### Post by mamamia88 on 2013-09-06
> **ZarathustraDK said:**
> Hey. I was wondering if you guys have any recommendations in regards to WOL-software.

I'm looking for some kind setup where I can assign entire IP-ranges to be woken up, give them a designation and save them for later use. Any ideas?
you could switch your router to dd-wrt firmware then just put a checkmark next to whatever computer hostname you want to enable wake on lan for and then wake them up from the web interface.

---

### Post by CharlesA on 2013-09-06
Eh, I use a shell script based off of wakeonlan for that.

---

### Post by cariboo on 2013-09-06
I used the howto [here]("http://wiki.xbmc.org/index.php?title=How-to:Set_up_Wake-On-Lan_(Ubuntu)"), then use [gwakeonlan]("https://code.google.com/p/gwakeonlan/") to start the sleeping systems.

---

### Post by Pinoy Tux on 2013-09-10
> **CharlesA said:**
> Eh, I use a shell script based off of wakeonlan for that.
Ditto.

```
wakeonlan -f /path/to/list/of/mac-addresses
```

---

