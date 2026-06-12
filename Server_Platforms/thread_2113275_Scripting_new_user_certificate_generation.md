---
title: "Scripting new user certificate generation"
date: 2013-02-06
forum: Server Platforms
---

### Post by lucas.robb on 2013-02-06
Hello All,

So I am trying to script a new user certificate issuing.  I have a script that looks something like this:
```

#!/bin/bash
# read out purpose of the script    
    echo ================================================================
    echo ""
    echo "This Script is to issue config files for new VPN Users"
    echo ""
    echo ================================================================
# get the name of the user
    read user
# generate the new keys
    source /etc/openvpn/easy-rsa/vars
    /etc/openvpn/easy-rsa/pkitool $user
# copy files over to new user folder
    mkdir /media/SMB-Share/files/$user
    cd /etc/openvpn/easy-rsa/keys/
    cp ca.crt $user.crt $user.csr $user.key ta.key /media/SMB-Share/files/$user
    cp /etc/openvpn/sample-client/client.conf /media/SMB-Share/files/$user/client.conf
# edit the client config for the new user
    sed -i "s/netbook/$user/" /media/SMB-Share/files/$user/client.conf
# edit permissions on folder
    chmod -R 777 /media/SMB-Share/files/$user

```
I was able to get this script working successful once, however I'm at a point now where when I run it, the source doesn't run properly and the rest fails after that.  Its not enough to run this script as Sudo I have only ever had success running sudo su prior to running the script.  Nonetheless, I'm only looking for help with lines 12-14, can anyone help me?

---

### Post by Habitual on 2013-02-07
echo quote "$variables"?
[http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)

---

