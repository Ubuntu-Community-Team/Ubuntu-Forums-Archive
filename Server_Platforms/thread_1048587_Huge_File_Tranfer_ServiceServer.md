---
title: "Huge File Tranfer Service/Server"
date: 2009-01-23
forum: Server Platforms
---

### Post by olivesandtrees on 2009-01-23
I am looking for a cloud service or local server service (it can be open source or proprietary) that would allow users to easily and securely transfer video files larger than 2GB.

Almost everything I have looked at so far that would meet requirements can only transfer up to 2GB.

Thoughts and suggestions appreciated.

---

### Post by geforce123 on 2009-01-24
As far as I know, Linux on 32bit architecture (CPU) uses 32 bits integer for file locking&&access, which means youre limited to (2^31 - 1) bytes (2147483647 bytes == 2 GB).

To override this limit, you'll need LFS (Large File Support).

I've never really played with it thought, but this information may at least leads you to more revelant informations.

Honestly, I think a cloud is overkill for file transfer service.  A local FTP service on LFS storage would suit your needs.


Phil

---

### Post by olivesandtrees on 2009-01-24
Thanks for the reply.  I don't think just FTP will cut it for what it would need it to do.  It needs to allow editors and producers separated by geographical distance to collaboratively work on huge video projects.  They aren't the most computer tech savvy end user group.  Plus, security is a main concern because it would be very detrimental if these projects were leaked.  I know SFTP is an option, but still...

---

### Post by geforce123 on 2009-01-24
Still with LFS storage on the server, you could go with VPN and network shares, depending on the OSes, softwares, etc.

---

### Post by olivesandtrees on 2009-01-24
I like that idea... it would really simplify things for the end user.  Though, I have a feeling our network security engineer will not like as much - you know the paranoia and all.  Thanks for the input.

---

### Post by geforce123 on 2009-01-24
It's a perfectly defendable solution, I think.

With proper access control, autenthification, encryption, I don't see no reason why your network engineer wouldn't allow that.  It might even be usefull in a variety of situations you may face in the future (ressources sharing, etc)

---

