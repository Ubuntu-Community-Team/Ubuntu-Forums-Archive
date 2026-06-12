---
title: "manually hashing ssh_known_hosts"
date: 2010-02-16
forum: Security
---

### Post by greenmoss on 2010-02-16
Hey all,

Does anyone know the algorithm used for generating host-name hashes in /etc/ssh/ssh_known_hosts and ~/.ssh/ssh_known_hosts? I would like to script the creation of this file, and for various technical reasons "ssh-keygen -H" is unsuitable.

It looks like generating the hashed host names should be a simple algorithm. How would I do it in perl/python/PHP/Ruby/whatever?


So to re-iterate/clarify/exemplify, I'm looking to convert

myhost,1.2.3.4 ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAIEA1SlCaPlX31XP0ccAynX9x4wxoL/exJvPOvMJXhhZawQfBfdHUZm7l4WjBpvUkgtsOuWqBu3sfLesTzUcVgJbNySr88BqXVy3IfrdDKi1RIjuwqnXkxsfHc8iJTWmtppsxJwTC80gYvRE4aMg9LPdBpcqcEzEaebsYIPoEPXBsBc=

into something like

|1|f0gGjfb2sXP68qhAPt2NSsO+/p0=|s5A2sN16Qbi03bWWBxSXG+zTw/0= ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAIEA1SlCaPlX31XP0ccAynX9x4wxoL/exJvPOvMJXhhZawQfBfdHUZm7l4WjBpvUkgtsOuWqBu3sfLesTzUcVgJbNySr88BqXVy3IfrdDKi1RIjuwqnXkxsfHc8iJTWmtppsxJwTC80gYvRE4aMg9LPdBpcqcEzEaebsYIPoEPXBsBc=

*without* using "ssh-keygen -H"

---

### Post by helmar on 2010-02-17
I was also looking for a way to generate a hashed ssh_known_hosts file from an unhashed one *without modifying the unhashed one*. I didnt find a tool for that.

On [http://publications.csail.mit.edu/abstracts/abstracts05/jyjung/jyjung.html](http://publications.csail.mit.edu/abstracts/abstracts05/jyjung/jyjung.html) i found the descrition of a patch for OpenSSH 3.9 providing such a tool:

ssh-hostname-encoder -o <oldfile> -n <newfile>
 Converts your old known_host file to a new file with hashed hosts.

...but... "It is important to note that the hashing scheme we originally implemented is not compatible with that which has subsequently been included in OpenSSH 4.0."...

---

### Post by Agent ME on 2010-02-17
What's wrong with "ssh-keygen -H"? Do you not want to hash everything in the known_hosts file? It doesn't damage anything at all to do that, but if you really wanted to avoid hashing other stuff, you could move the key-to-be-hashed to its own known_hosts file, run "ssh-keygen -H" on it, and then place it back into the original known_hosts file.

---

