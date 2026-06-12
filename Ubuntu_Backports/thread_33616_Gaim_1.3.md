---
title: "Gaim 1.3"
date: 2005-05-11
forum: Ubuntu Backports
---

### Post by Chrysaor on 2005-05-11
GAIM 1.3 is released. Any chance on backport?

[http://gaim.sourceforge.net/downloads.php](http://gaim.sourceforge.net/downloads.php)
> version 1.3.0 (5/10/2005):
	* Removed parts of the font selection dialog that were not respected
	* Fix being invited to a multi user chat on MSN
	* Multiple SILC accounts should work now (Pekka Riikonen)
	* Fix times on jabber chat backlogs
	* Fix gevolution plugin to compile with e-d-s 1.0 or 1.2
	* Fix gevolution plugin to remember buddy name when someone added you
	  and you then add them
	* Formatting in jabber chats works
	* Fix to prevent MSN disconnecting if you change status while connecting
	* Fixes for two remotely exploitable crash bugs.  See
	  [http://gaim.sourceforge.net/security/](http://gaim.sourceforge.net/security/) for more information.

---

### Post by Zelut on 2005-05-11
I'm waiting on this too.  Someone please post if this becomes available..

---

### Post by jdong on 2005-05-11
I'm currently uploading this into hoary-backports-staging/main. Test & report back.

---

### Post by Zelut on 2005-05-11
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-backports/staging/binary-i386/Packages.gz](http://backports.ubuntuforums.org/backports/dists/hoary-backports/staging/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done

I must not have the right path in my sources.list.  Can someone please tell me the correct path to the backports-staging-main?  Thanks

---

### Post by rpgcyco on 2005-05-11
[QUOTE=jdong]I'm currently uploading this into hoary-backports-staging/main. Test & report back.[/QUOTE]

Working fine here (so far), thanks jdong. :)

- Rpg Cyco

---

### Post by Bob D. on 2005-05-11
[QUOTE=jdong]I'm currently uploading this into hoary-backports-staging/main. Test & report back.[/QUOTE] Ditto to the above. Seems to be working fine here.

Bob

---

### Post by Chrysaor on 2005-05-11
Working fine, thanks. :)

---

### Post by keyshawn on 2005-05-11
Wow jdong, Six hours - That must be a record ! :-)

I commend and thank you for doing so quickly. School must be winding down for you, eh ? 

regards,
skora. [high school senior]

---

### Post by psoleko on 2005-05-11
Hmm having some connection issues here with 1.3, after login buddies are not populated and I cannot send an IM. Time to see what's causing this.

-- Reinstalled then rebooted machine, connects albeit slow loading of buddy list info

---

### Post by jdong on 2005-05-13
[QUOTE=keyshawn]Wow jdong, Six hours - That must be a record ! :-)

I commend and thank you for doing so quickly. School must be winding down for you, eh ? 

regards,
skora. [high school senior][/QUOTE]

Oh, it was the first package to capture my attention that afternoon :)

---

### Post by SpEcIeS on 2005-05-27
[QUOTE=jdong]Oh, it was the first package to capture my attention that afternoon :)[/QUOTE]

Gaim 1.3.0 works well on my system...  thanks **jdong** :)

---

### Post by XeeleeUniversum on 2005-05-27
Hi,

firstly THX for the backport. :) But I've also a request for a plugin, I still using the gaim-encryption plugin very often but since update, Gaim still bothers me with this on every startup: "Plugin is compiled for an other version, U will experience some problems." (or something like that)

It is possible to backport this or/and other plugins too?

tbg alex

---

### Post by jdong on 2005-05-27
I'll see what I can do about that.

---

