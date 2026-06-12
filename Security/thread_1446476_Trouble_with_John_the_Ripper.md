---
title: "Trouble with John the Ripper"
date: 2010-04-04
forum: Security
---

### Post by lateralus01 on 2010-04-04
I'm using ubuntu 9.10 and I'm trying to crack my own password with John the Ripper.  I've been reading and working at this for a long time and I've not been able to crack my password.  I've added a "test" account on my machine with the password "password":

For my Unix Password:
```

mark@mark-laptop:~/John/john-1.7.3.4/run$ sudo ./unshadow /etc/passwd /etc/shadow > mypasswd
mark@mark-laptop:~/John/john-1.7.3.4/run$ sudo ./john mypasswd
No password hashes loaded

```

YES I have read the README and the FAQ and for this problem they give the following possible problems:
Q: Why doesn't John load my password file?  It says "No password hashes
loaded".
A: Your password file might be shadowed.  You need to get both
/etc/passwd and the shadow file (typically /etc/shadow), and combine
them into one file for use with John.
***I DID THIS AS YOU CAN SEE ABOVE
A: All of the password hashes found in the file (that John recognizes as
such) might be already cracked by previous invocations of John.
***THEY HAVEN'T, john --show mypasswd returns nothing and removing john.pot clears john's memory of previously cracked files
A: The file you're trying to run John on might in fact not be a password
file at all.
***IT OBVIOUSLY IS:
```

test:$6$.R/mk/Uv$7b.9w/5W4exX3kGRPR5gC63fPEqgzEKyBRXogMJ.WANpszWvcB4z..PHDL3M4FXnBjlzpQJYzHXw92HUtwm3Y0:1001:1001::/home/test:/bin/sh

```
^^Obviously I've trimmed out the other users :p
A: Your command line syntax might be wrong, resulting in John trying to
load a wrong file.
***IT'S NOT, THIS SYNTAX HAS BEEN USED IN EXAMPLES OVER AND OVER
A: Your password file format or hash type(s) might not be supported by
John, or at least by the version and build of John that you're using.
If you're positive that this is the case, you may want to check the
contributed resources list on John the Ripper homepage for a suitable
patch and, if unsuccessful with that, post a note to the mailing list
(see CONTACT) including a sample password file line that John does not
load (please make sure that the password is already changed by the time
you post).
***I'VE DOWNLOADED THE LATEST PATCH FOR MY VERSION OF JOHN AND RECOMPILED IT AND THAT HASN'T HELPED

Any ideas?

Thanks,
Lateralus01

---

### Post by cdenley on 2010-04-04
I don't think JTR supports SHA-512 hashes yet.
[http://www.openwall.com/john/doc/](http://www.openwall.com/john/doc/)
> Out of the box, John supports (and autodetects) the following Unix crypt(3) hash types: traditional and double-length DES-based, BSDI extended DES-based, FreeBSD MD5-based (now also used on Linux and in Cisco IOS), and OpenBSD Blowfish-based (now also used on some Linux distributions). Also supported out of the box are Kerberos/AFS and Windows LM (DES-based) hashes.

---

