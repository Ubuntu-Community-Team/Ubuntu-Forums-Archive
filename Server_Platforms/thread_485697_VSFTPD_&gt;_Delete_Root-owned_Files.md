---
title: "VSFTPD &gt; Delete Root-owned Files??"
date: 2007-06-27
forum: Server Platforms
---

### Post by Twikkistep on 2007-06-27
Hi there,

I don't know if this is custom, but I installed VSFTPD and chrooted the users to their local home directory. It all works great, but when I create a root-owned file in their home-directory, they are able to delete that file through FTP, while WU-FTPD for example doesn't pose this problem. Am I the only one here having this problem, or is it normal that VSFTPD works this way?

-- TS

---

### Post by Wim Sturkenboom on 2007-06-27
Same problem here on a Slackware box. I don't consider it normal. There might be a setting but I'm not sure.

---

### Post by umattu on 2007-06-27
Yeah I just tryed creating a root owned directory and was able to delete with an users account. I'm not liking that. Thanks for posting this, now we need to find the solution.;)

Same thing over my SSH connection as well!

Whew I feel better knowing that they can only delete root owned files in their home directory. I just tried it.

---

### Post by Mr. C. on 2007-06-29
A directory owner can delete entries in the directory.  It is the directory's permissions that control deletion of an object.  It is the directory that is modified to remove its reference to the file's inode; the inode's reference count is then decremented.

There are security risks involved with chrooting local users - you should learn about them.

MrC

---

