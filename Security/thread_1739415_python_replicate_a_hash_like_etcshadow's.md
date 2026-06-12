---
title: "python replicate a hash like /etc/shadow's"
date: 2011-04-25
forum: Security
---

### Post by d3v1150m471c on 2011-04-25
I've been working on a security tool and a feature I'd like to implement is the ability to hash a password identical to the way /etc/shadow's hashes are created so that these passwords can be tested for weakness and improved accordingly. The program is written in python and I'd like to keep it that way. So far all I've been able to find is:

```

python -c "import crypt, getpass, pwd; print crypt.crypt('password', '\$6\$SALTsalt\$')"

```I found that on [http://ubuntuforums.org/showthread.php?t=1169551](http://ubuntuforums.org/showthread.php?t=1169551)

So far it looks useful but the problem I'm running into is it doesn't create the same hash, I'm assuming this is due to the salt. Is there a default salt used by "/etc/shadow"? I would assume so because when you enter your password it probably compares the hash to /etc/shadow. Any help on this or pointing me in the right direction would be greatly appreciated.

---

### Post by sisco311 on 2011-04-26
> **d3v1150m471c said:**
> Is there a default salt used by "/etc/shadow"?

Nope, that would defeat the whole purpose of the salt.

You can use the spwd module to get the encrypted password of a user:
```

#!/usr/bin/env python

import crypt, getpass, spwd

name = 'username'
spwd.getspnam(name)[1]

```

The encrypted password is in the following format:
$id$salt$encrypted

Where id identifies  the  encryption method  used, salt is the salt and the encrypted part of the password string is the actual computed  password.

Check out **man 3 crypt** and [http://docs.python.org/library/unix.html](http://docs.python.org/library/unix.html)

---

### Post by d3v1150m471c on 2011-04-26
Thanks sisco, I owe you one. I'm gonna give this a whirl and see what I can come up with.

---

### Post by d3v1150m471c on 2011-04-26
I like these modules, but here's the trouble I'm running into. That first python string I referenced, say my /etc/shadow hash was this:
```

$6$jcGfgT$FruNTWTNgs9sELgRfgUT9LFdXogITyE7icwbdiKPLR9DTgmQDa.

```Now, I would assume $6$jcGfgT would be the encryption method and the salt, sha-512 $6$jcGfgT, but when using that method and salt it returns a completely different hash. So is that not the actual salt? I can't imagine the privileges or a login would work on Linux if they're unable to use a known salt stored somewhere when it runs a password input through an algorithm. So now I can get a hash with straight python, but using the above modules i'm unable to compare them with the result of weak passwords because the salt or something is off... meh lol

---

### Post by d3v1150m471c on 2011-04-27
okay i fixed this...somewhat. the problem was that i was using special characters in my password so i simply need to find a way to make sure they're being properly escaped. otherwise the original python code above works perfectly. thanks again, sisco :)

---

