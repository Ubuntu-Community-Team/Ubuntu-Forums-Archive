---
title: "PAM-script module doesn't work properly"
date: 2010-02-07
forum: Security
---

### Post by charliehorse55 on 2010-02-07
So I installed pam-script

made this script:

```

#!/bin/bash
RFID_AUTH_SUCCESS=0

#Read the card
tag=`'/etc/rfid/RFID-login'`

#check if the card id my card, if so, then authenticate, if not, disallow
if [ $tag == "2800a79557" ]; then 
RFID_AUTH_SUCCESS=1
else
RFID_AUTH_SUCCESS=0
fi
echo $RFID_AUTH_SUCCESS
exit $RFID_AUTH_SUCCESS;

```

and modified my common_auth to
```
# here are the per-package modules (the "Primary" block)
auth	sufficient			pam_script.so dir=/etc/pam-scripts/
auth	sufficient			pam_unix.so nullok_secure try_first_pass
```

But upon starting a terminal window and typing 
```

sudo test

```

It doesn't ask for my password and instantly authenticates as root!


if I run the above posted script manually, (cd into the dir and execute it), it works fine and produces the result 1 if positive and 0 if negative. 

What did I do wrong?

---

### Post by charliehorse55 on 2010-02-08
Solved it myself.

Silly, the pam-script package built and then I went sudo make install, which ran and outputted some stuff. However it failed to put pam_script.so into the /lib/security/ folder.

When it went make it also made the folder .libs, which had the script file inside. 

Why would a make command build a hidden folder?

---

