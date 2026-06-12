---
title: "python bcrypt"
date: 2012-04-21
forum: Security
---

### Post by gameguy on 2012-04-21
I am trying to run a web server in python, and for that, I need to encrypt users passwords.

first I ran this:
```

sudo apt-get install python-bcrypt
python

```and then in the python interpreter
```

import bcrypt
bcrypt.gensalt()
#AttributeError: 'module' object has no attribute 'gensalt'
bcrypt.hashpw()
#AttributeError: 'module' object has no attribute 'hashpw'
dir(bcrypt)
#['__builtins__', '__doc__', '__file__', '__name__', '__package__', '__path__']

```basically, I want to use the bcrypt algorithm to encrypt the passwords, but I have no clue how to access them, since it doesn't seem to work like normal modules do.

---

