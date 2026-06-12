---
title: "Does vsftp have the proftpd hiddenstores feature"
date: 2007-06-06
forum: Server Platforms
---

### Post by Highway on 2007-06-06
Hi,
I am using proftp on a mandriva server that i need to replace. I was planning on replacing with an ubuntu LTS installation.

Proftpd does not seem to be in the main packages repository, and I don't want to use any software that requires enabling the universe or multiverse for future updates.
So i am looking at vsftp.  It seems fine except one feature that is indispensible in proftpd: hiddenstores.
This hides the file during upload and it only appears once it's fully uploaded. 

I am polling for large uploaded files regularly and without this feature my polling scripts were collecting partially uploaded files.   Yes, i know i could add some filesize checking, etc to my scripts, but I'm trying to avoid that now.

Vsftp would be fine if it had an equivalent of this.  Also, is there any commercial support available for vsftp?

Highway.

---

### Post by Mr. C. on 2007-06-06
vsftpd does not have such a feature.  About the best you can do is instead of polling the filesystem, is tail the end of the vsftpd.log or xferlog file.  Entries are written when transfer is complete (or partially transfered in case of abort).

MrC

---

