---
title: "getting public keys for apt fails because of firewall"
date: 2009-06-06
forum: Security
---

### Post by anystupidname on 2009-06-06
At home I add keys via this script:
```
#!/bin/bash

sudo gpg --keyserver subkeys.pgp.net --recv-keys $1
sudo gpg --armor --export $1 | sudo apt-key add -
```

At work they block port 11371 so I've just been ignoring the authentication warnings when I use apt but this bothers me. ](*,) Could anybody please offer suggestions for an alternate semi-automated method of adding keys when 11371 is blocked? Please and thanks!

---

### Post by sgerrand on 2009-08-07
using an ssh tunnel and port forwarding through it helps immeasurably in those situations. 

i.e., ```
ssh -f -L 11371:KEY_SERVER_NAME:11371 SSH_HOST_NAME -N
```

using this method, you would connect to localhost instead of the normal hostname. to use the hostname you posted as an example:

```

#!/bin/bash

KEYHOST=localhost

sudo gpg --keyserver $KEYHOST --recv-keys $1
sudo gpg --armor --export $1 | sudo apt-key add -

```

ssh is a lifesaver in the land of corporates, so long as you have the ability to get out on port 22 at least.

---

