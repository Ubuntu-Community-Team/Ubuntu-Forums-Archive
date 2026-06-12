---
title: "Ubuntu file server + AD integration"
date: 2012-09-05
forum: Server Platforms
---

### Post by Tutigan on 2012-09-05
I have scoured the web, valiantly trying to find a solution, and just gotten severly confused...

I have a samba file server running Ubuntu Server 12.04, joined to my active directory domain. I have been able to allow domain users to access the file shares on the ubuntu server, and even grant logon/sudo access to the domain admins. What I want to do is a little more complicated:
When I create a new user in active directory, I want to be able to have their home drive automatically created on the linux server.
Is this even possible? It works with windows file servers, why not linux?

~tutigan

---

### Post by fang0654 on 2012-09-05
It is possible, and pretty easy.  You just need a script to create the drive when it is first accessed.

In your smb.conf, under the [homes] directive, you should place the following:

root preexec = /path/to/script/you/want/to/run %D %U

You can use something as simple as this as your create script:

```
#!/bin/bash
#smb-mkhomedir.sh

DHOME="/home"
USERS_GID="1000"
SKEL="/etc/skel"

# Reads config file (will override defaults above)
[ -r /etc/adduser.conf ] && . /etc/adduser.conf


if [ -z $1 ]; then
        echo "Usage: $0 username" 1>&2
        exit 1
fi

if [ ! -e $DHOME/$1 ]; then
        mkdir -m $DIR_MODE -p $DHOME/$1
        cp -R $SKEL/* $DHOME/$1
        chown -R $1:$USERS_GID $DHOME/$1
fi

exit 0
```

(Pulled from [http://www.debian-administration.org/article/403/Giving_users_a_home_directory_automatically]("http://www.debian-administration.org/article/403/Giving_users_a_home_directory_automatically"))

You will still get an error from AD when you create the user, but the first time the user goes to connect it'll create the folder.

---

