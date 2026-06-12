---
title: "Runing a custom script during MAAs deployment"
date: 2019-05-14
forum: Server Platforms
---

### Post by abdelkader-1 on 2019-05-14
Hello,

Can someone help me to run a custom script during the installation ob Ubuntu with MAAS server please, i did:
1 - Prepared an example script:
```
#!/bin/bash

mkdir /tmp/TMP
cd /tmp/TMP
wget http://mirrors.kernel.org/ubuntu/pool/universe/i/ipmitool/ipmitool_1.8.18-5build1_amd64.deb 

```
2- Get the system id on the target machine:
```
maas  $PROFILE machines read | jq '.[] | .hostname, .system_id'
```
3- Deploy Ubuntu machine with custom script:
```
maas $PROFILE  machine deploy $SYSTEM_ID  [EMAIL="user_data@=/opt/test.sh"]user_data@=/opt/test.sh[/EMAIL]
Success
....
```
  
But after installation i don't find anything under /tmp folder, i'm missing something ?

---

