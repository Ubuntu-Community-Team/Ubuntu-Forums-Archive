---
title: "DeprecationWarning: the sha module is deprecated; use the hashlib module"
date: 2009-07-17
forum: Security
---

### Post by cccc on 2009-07-17
hi

I've done the Upgrade to karmic and have this python script to protect the start of thunderbird using password:```

#!/usr/bin/python

# Password protector
import os, sys, sha, getpass

# Read in hash
hash_file = open("/home/myuser/.password_protect", "r")
hash = hash_file.read()

# Get new hash
pwhash = ''
counter = 0
while pwhash != hash:
    pwhash = sha.sha(getpass.getpass("Password: ")).hexdigest()
    counter += 1
    if counter > 3:
        sys.exit()

os.system("/usr/bin/thunderbird")
```

but I'm getting this error message:```
 
/home/pw.py:4: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import os, sys, sha, getpass
```
howto solve this problem?

---

### Post by bodhi.zazen on 2009-07-17
Have you considered filing a bug report ?

---

### Post by Agent ME on 2009-07-17
Have you tried using [hashlib](http://docs.python.org/library/hashlib.html) like it says to?

Though usually I wouldn't expect a warning like that to completely stop the program from functioning.

Also, this script does no real protection. Anyone can just start up thunderbird on their own without that script. If you want to secure your email, you're better off encrypting the ~/.thunderbird folder.

---

### Post by cccc on 2009-07-17
> **Agent ME said:**
> Have you tried using [hashlib](http://docs.python.org/library/hashlib.html) like it says to?

Though usually I wouldn't expect a warning like that to completely stop the program from functioning.

Also, this script does no real protection. Anyone can just start up thunderbird on their own without that script. If you want to secure your email, you're better off encrypting the ~/.thunderbird folder.

I know, this is not a really protection, but howto install hashlib module and change this script to ask for a password without errors?

---

### Post by cccc on 2009-07-18
I changed the script and now it works well without warnings:```

#!/usr/bin/python

# Password protector
import os, sys, hashlib, getpass

# Read in hash
hash_file = open("/home/myuser/.password_protect", "r")
hash = hash_file.read()

# Get new hash
pwhash = ''
counter = 0
while pwhash != hash:
    pwhash = hashlib.sha1(getpass.getpass("Password: ")).hexdigest()
    counter += 1
    if counter > 3:
        sys.exit()

os.system("/usr/bin/thunderbird")
```

---

### Post by Yrrepperry on 2010-09-13
this problem seems to exist when using Google appengine too (where I gather it is using these modules, not me)
[B]DeprecationWarning: the sha module is deprecated; use the hashlib module

it still seems to work,but I wonder if I will always get this error.
[/B]

---

### Post by Bachstelze on 2010-09-13
> **Yrrepperry said:**
> 
it still seems to work,but I wonder if I will always get this error.

You will get it until either the script is fixed to use hashlib, or the sha module disappears altogether and the script stops working, whichever comes first.

---

