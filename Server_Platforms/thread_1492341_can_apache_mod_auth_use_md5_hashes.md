---
title: "can apache mod_auth use md5 hashes?"
date: 2010-05-24
forum: Server Platforms
---

### Post by r.lopez.negrete on 2010-05-24
Hi all,

I'm trying to figure out if I can force apache's mod_auth to use md5 hashed passwords. Is this possible and if so, how is this set up?

Thanks,
 Rodrigo

---

### Post by lisati on 2010-05-24
Moved to "Server Platforms"

---

### Post by lisati on 2010-05-24
I notice that this thread is marked "Solved". I'm curious as to why......

---

### Post by cdenley on 2010-05-25
It should work just fine with an MD5 hash generated with crypt. I use PHP to generate a password file which apache uses with mod_auth.
[PHP]
$fh=fopen('/path/to/password/file','a');
fwrite($fh,$user.':'.crypt($pass)."\n");
fclose($fh);
[/PHP]

---

