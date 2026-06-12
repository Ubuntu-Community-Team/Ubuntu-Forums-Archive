---
title: "Problems Mounting an FTP site"
date: 2007-08-04
forum: Server Platforms
---

### Post by etechship on 2007-08-04
I have install curlftpfs and all other things needed, i think. I used apt, and it installed a lot of other stuff, so I think it is okay.

when I run this command:
*user* and *pass* = my user and pass

```
curlftpfs ftp://ucstreaming.officewebsiteonline.com -o user="*user:pass*" /usr/lib/red5/webapps/oflaDemo/streams/
```

this what the outcome:
```
fusermount: failed to open /dev/fuse: Permission denied
```

any help would be greatly appreiated.

thanks

---

### Post by apetresc on 2007-08-04
I suggest you IMMEDIATELY edit your post to not include your FTP account's REAL username and password. I just checked, they are correct -- I was able to log on. I won't do anything, but not everybody will be so benign. If you read this, edit your post! (If a moderator reads this, edit his post!!)

---

### Post by etechship on 2007-08-04
ugg, thanks for that notice

---

### Post by apetresc on 2007-08-04
> **etechship said:**
> ugg, thanks for that notice
Hehe, no problem :) Good thing you responded quickly!
As for your actual problem, try running that same command with sudo. I think it's intentional that you can't mount FUSE systems as a regular user by default.

---

### Post by etechship on 2007-08-04
I'm running as root,and I tried sudo, but nothing differant.

---

### Post by apetresc on 2007-08-04
> **etechship said:**
> I'm running as root,and I tried sudo, but nothing differant.

Ah! Type this: ```
sudo chgrp fuse /dev/fuse
``` and then run it again.

I got this from googleing your error message, and going to the second hit here: [https://bugs.launchpad.net/ubuntu/+source/fuse/+bug/114212](https://bugs.launchpad.net/ubuntu/+source/fuse/+bug/114212)

---

### Post by etechship on 2007-08-04
```
ucsteaming:~# chgrp fuse /dev/fuse
ucsteaming:~# curlftpfs ftp://ucstreaming.officewebsiteonline.com -o user="*user:pass*" /usr/lib/red5/webapps/oflaDemo/streams/
fusermount: failed to open /dev/fuse: Permission denied
ucsteaming:~#

```

same thing. I will do some google searching, but ...

---

### Post by apetresc on 2007-08-04
Is the user you're doing this as in the 'fuse' group?

```
sudo adduser user fuse
```

---

### Post by etechship on 2007-08-04
I added myself to the fuse group, and did that 

> chgrp fuse /dev/fuse 

command, but nothing differant, even after I restarted

---

