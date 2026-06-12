---
title: "How to secure Transmission?"
date: 2010-05-10
forum: Security
---

### Post by dogdo on 2010-05-10
Hi  Is it possible at all to secure transmission?

---

### Post by Linuxforall on 2010-05-10
Yes you can make apparmor profiles for it.

---

### Post by dogdo on 2010-05-10
Ok im really not at all accomplished with ubuntu-is there somewhere i can find a ready made profile?

---

### Post by cariboo on 2010-05-10
Check out bodhi's Apparmor sticky at the top of the page, he has some pre-made scripts on his blog, that are linked to in the thread.

---

### Post by bodhi.zazen on 2010-05-10
[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.10/usr.bin.transmission](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.10/usr.bin.transmission)

Fairly similar to Ubuntu 10.04

I will try to upload my 10.04 profile as time allows.

---

### Post by rookcifer on 2010-05-10
Here's mine for 10.04.  Of course, if you have directories outside of /home that you wish for transmission to access, you will have to add it manually.  This profile, however, should be good enough to be operational and get you going.


```
# Last Modified: Mon May 10 17:48:58 2010
#include <tunables/global>

/usr/bin/transmission {
  #include <abstractions/base>
  #include <abstractions/evince>
  #include <abstractions/nameservice>
  #include <abstractions/private-files-strict>


  owner /home/*/** rwk,
  /proc/*/net/route r,
  /proc/filesystems r,  
  /usr/local/lib/lib*so* mr,

}
```

---

### Post by dogdo on 2010-05-16
> **rookcifer said:**
> Here's mine for 10.04.  Of course, if you have directories outside of /home that you wish for transmission to access, you will have to add it manually.  This profile, however, should be good enough to be operational and get you going.


```
# Last Modified: Mon May 10 17:48:58 2010
#include <tunables/global>

/usr/bin/transmission {
  #include <abstractions/base>
  #include <abstractions/evince>
  #include <abstractions/nameservice>
  #include <abstractions/private-files-strict>


  owner /home/*/** rwk,
  /proc/*/net/route r,
  /proc/filesystems r,  
  /usr/local/lib/lib*so* mr,

}
```

So what does this particular profile do-does it block access to the system files or home folder files?

---

### Post by bodhi.zazen on 2010-05-16
> **dogdo said:**
> So what does this particular profile do-does it block access to the system files or home folder files?

System files. Home is almost wide open ([FONT=monospace] [/FONT]owner /home/*/** rwk, )

If you are unfamiliar with apparmor, I suggest you start with the siticky in the security forums

**[B]Sticky:**[/B] 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Introduction to AppArmor]("http://ubuntuforums.org/showthread.php?t=1008906")

---

### Post by rookcifer on 2010-05-16
> **bodhi.zazen said:**
> System files. Home is almost wide open ([FONT=monospace] [/FONT]owner /home/*/** rwk, )

If you are unfamiliar with apparmor, I suggest you start with the siticky in the security forums



No, /home isn't wide-open.  As you can see I have included the "private-files-strict" abstraction which blocks access to all important /home files, including ssl, gpg keys and all *.rc files.

---

### Post by bodhi.zazen on 2010-05-16
> **rookcifer said:**
> No, /home isn't wide-open.  As you can see I have included the "private-files-strict" abstraction which blocks access to all important /home files, including ssl, gpg keys and all *.rc files.

Thank you for that clarificiation, but I think you mis read my post :

> **bodhi.zazen said:**
> System files. Home is **almost** wide open

---

