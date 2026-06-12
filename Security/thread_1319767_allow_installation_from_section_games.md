---
title: "allow installation from section games"
date: 2009-11-08
forum: Security
---

### Post by hudo on 2009-11-08
Hi,

I'd like to allow my kids to install software ONLY from the games section.

Is this possible ?

---

### Post by ianhaycox on 2009-11-21
Did you get anywhere with this ?

I have a similar requirement - my kids have non-privileged accounts, but I'd like to give them the ability to install software from the repositories (maybe just games) but not full sudo access.

Is there anyway to configure this ?

Ideas welcome

---

### Post by slakkie on 2009-11-21
You should be able to do it. Write a script like something below, and make sure that your kids can only run this script with sudo.

```

#!/usr/bin/env bash

for i in $@ ; do
    apt-cache show $i | grep -iq "Section: games"
    if [ $? -eq 0 ] ; then
        aptitude install $i
    else
        echo "$i is not a game, not installing it"
    fi
done

```

---

### Post by ianhaycox on 2009-11-22
That is one alternative, but I was reluctant to add the kids to sudoers.

I looked at System->Administation->Authorizations (is that policykit ?) and there are options to allow non-priv users to mount/shutdown etc. but nothing for installing software.

Is there is something I can add to Authorizations to allow non-priv users install packages ?

---

